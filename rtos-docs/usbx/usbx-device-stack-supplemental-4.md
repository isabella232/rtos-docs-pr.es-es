---
title: 'Capítulo 4: Implementación de USBX PictBridge'
description: USBX admite la implementación completa de PictBridge tanto en el dispositivo como en el host. PictBridge se encuentra en la parte superior de la clase PIMA de USBX, en ambos lados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4fdf1e46a7123c10d17e11d09c1b16c2f68f4a31
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550242"
---
# <a name="chapter-4---usbx-pictbridge-implementation"></a>Capítulo 4: Implementación de USBX PictBridge

USBX admite la implementación completa de PictBridge tanto en el host como en el dispositivo. PictBridge se encuentra en la parte superior de la clase PIMA de USBX, en ambos lados.

Los estándares de PictBridge permite la conexión de una cámara fija digital o un smartphone directamente a una impresora sin un PC, lo que permite la impresión directa en algunas impresoras compatibles con PictBridge.

Cuando se conecta una cámara o un teléfono a una impresora, esta es el host USB y la cámara es el dispositivo USB. Pero, con PictBridge, la cámara aparecerá como el host y esta controlará los comandos. La cámara es el servidor de almacenamiento y la impresora, el cliente de almacenamiento. La cámara es el cliente de impresión y la impresora es el servidor de impresión.

PictBridge usa USB como capa de transporte, pero se basa en PTP (Protocolo de transferencia de imágenes) para el protocolo de comunicación.

A continuación se presenta un diagrama de los comandos y las respuestas entre el cliente de DPS y el servidor de DPS cuando se produce un trabajo de impresión:

![Comandos de DPS y respuestas](./media/usbx-device-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a>Implementación del cliente PictBridge

El PictBridge en el cliente requiere que la pila del dispositivo USBX y la clase PIMA se ejecuten en primer lugar.

Un marco de dispositivo describe la clase PIMA de la siguiente manera.

```C
UCHAR device_framework_full_speed[] =
{
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x20,
    0xA9, 0x04, 0xB6, 0x30, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,
    /* Configuration descriptor */
    0x09, 0x02, 0x27, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,
    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x03, 0x06, 0x01, 0x01, 0x00,
    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x60
};
```

La clase PIMA usa el campo de identificador 0x06, su subclase es 0x01 para la imagen fija y el protocolo es 0x01 para la clase PIMA 15740.

En esta clase se definen tres puntos de conexión, dos en masa para enviar y recibir datos y uno para interrumpir los eventos.

A diferencia de otras implementaciones de dispositivos USBX, la aplicación PictBridge no necesita definir una clase en sí. En su lugar, invoca la función ***ux_pictbridge_dpsclient_start***. A continuación se muestra un ejemplo:

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "ExpressLogic",13);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

Los parámetros que se pasan al cliente de PictBridge son los siguientes:

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no
    : String of serial number
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

El siguiente paso es la sincronización del dispositivo y el host para que estén listos para intercambiar información.

Esto se hace esperando a una marca de evento de la siguiente manera:

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get(&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR,
    &actual_flags, UX_PICTBRIDGE_EVENT_TIMEOUT);
```

Si la máquina de estados está en el estado **DISCOVERY_COMPLETE**, el lado de la cámara (el cliente de DPS) recopilará la información relacionada con la impresora y sus capacidades.

Si el cliente de DPS está listo para aceptar un trabajo de impresión, su estado se establecerá en **UX_PICTBRIDGE_NEW_JOB_TRUE**. Se puede comprobar de la siguiente manera:

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)
/* We can print something … */
```

Después, se deben rellenar los descriptores de trabajos de impresión como se indica a continuación:

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo -> ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo -> ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo -> ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo -> ux_pictbridge_jobinfo_object_data_read =
    ux_demo_object_data_copy;

/* This is a demo, the fileID is hardwired (1 and 2 for scripts, 3 for photo to be printed. */
printinfo.ux_pictbridge_printinfo_fileid =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_filename,
    "Pictbridge demo file", 20);
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_date, "01/01/2008",
    10);

/* Fill in the object info to be printed. First get the pointer to the object container in the job info structure. */
object = (UX_SLAVE_CLASS_PIMA_OBJECT *) jobinfo ->
    ux_pictbridge_jobinfo_object;

/* Store the object format: JPEG picture. */
object -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object -> ux_device_class_pima_object_compressed_size = IMAGE_LEN;
object -> ux_device_class_pima_object_offset = 0;
object -> ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object -> ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

El cliente PictBridge tiene ahora un trabajo de impresión para realizar y capturará los bloques de imagen desde la aplicación mediante la devolución de llamada definida en el campo.

```C
jobinfo -> ux_pictbridge_jobinfo_object_data_read
```

El prototipo de esa función se define como se indica a continuación.

## <a name="ux_pictbridge_jobinfo_object_data_read"></a>ux_pictbridge_jobinfo_object_data_read

Copia de un bloque de datos del espacio de usuario para imprimirlos

### <a name="prototype"></a>Prototipo

```C
UINT ux_pictbridge_jobinfo_object_data_read( 
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,  
    ULONG object_offset,  
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a>Descripción

Se llama a esta función cuando el cliente de DPS necesita recuperar un bloque de datos para imprimirlo en la impresora PictBridge de destino.

### <a name="parameters"></a>Parámetros

- **pictbridge**: señalador a la instancia de clase pictbridge.
- **object_buffer**: señalador al búfer del objeto
- **object_offset**: lugar donde se empieza a leer el bloque de datos
- **object_length**: longitud que se va a devolver
- **actual_length**: longitud real devuelta

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00): esta operación se realizó correctamente.
- **UX_ERROR** (0x01): la aplicación no pudo recuperar los datos.

### <a name="example"></a>Ejemplo

```C
/* Copy the object data. */
UINT ux_demo_object_data_copy(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
{
    /* Copy the demanded object data portion. */
    ux_utility_memory_copy(object_buffer, image + object_offset,
        object_length);
    /* Update the actual length. */
    *actual_length = object_length;
    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="pictbridge-host-implementation"></a>Implementación del host PictBridge

La implementación del host de PictBridge es diferente a la del cliente.

Lo primero que hay que hacer en un entorno de host PictBridge es registrar la clase PIMA como se muestra en el ejemplo siguiente:

```C
status = ux_host_stack_class_register(_ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

Esta clase es la capa de PTP genérica que se encuentra entre la pila USB y la capa PictBridge.

El siguiente paso consiste en inicializar los valores predeterminados de PictBridge para los servicios de impresión como se indica a continuación:

| Campo de PictBridge       | Value                                  |
|------------------------|----------------------------------------|
| DpsVersion[0]          | 0x00010000                             |
| DpsVersion[1]          | 0x00010001                             |
| DpsVersion[2]          | 0x00000000                             |
| VendorSpecificVersion  | 0x00010000                             |
| PrintServiceAvailable  | 0x30010000                             |
| Qualities[0]           | UX_PICTBRIDGE_QUALITIES_DEFAULT        |
| Qualities[1]           | UX_PICTBRIDGE_QUALITIES_NORMAL         |
| Qualities[2]           | UX_PICTBRIDGE_QUALITIES_DRAFT          |
| Qualities[3]           | UX_PICTBRIDGE_QUALITIES_FINE           |
| PaperSizes[0]          | UX_PICTBRIDGE_PAPER_SIZES_DEFAULT      |
| PaperSizes[1]          | UX_PICTBRIDGE_PAPER_SIZES_4IX6I        |
| PaperSizes[2]          | UX_PICTBRIDGE_PAPER_SIZES_L            |
| PaperSizes[3]          | UX_PICTBRIDGE_PAPER_SIZES_2L           |
| PaperSizes[4]          | UX_PICTBRIDGE_PAPER_SIZES_LETTER       |
| PaperTypes[0]          | UX_PICTBRIDGE_PAPER_TYPES_DEFAULT      |
| PaperTypes[1]          | UX_PICTBRIDGE_PAPER_TYPES_PLAIN        |
| PaperTypes[2           | UX_PICTBRIDGE_PAPER_TYPES_PHOTO        |
| FileTypes[0]           | UX_PICTBRIDGE_FILE_TYPES_DEFAULT       |
| FileTypes[1]           | UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG     |
| FileTypes[2]           | UX_PICTBRIDGE_FILE_TYPES_JFIF          |
| FileTypes[3]           | UX_PICTBRIDGE_FILE_TYPES_DPOF          |
| DatePrints[0]          | UX_PICTBRIDGE_DATE_PRINTS_DEFAULT      |
| DatePrints[1]          | UX_PICTBRIDGE_DATE_PRINTS_OFF          |
| DatePrints[2]          | UX_PICTBRIDGE_DATE_PRINTS_ON           |
| FileNamePrints[0]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT |
| FileNamePrints[1]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF     |
| FileNamePrints[2]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_ON      |
| ImageOptimizes[0]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT  |
| ImageOptimizes[1]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF      |
| ImageOptimizes[2]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON       |
| Layouts[0]             | UX_PICTBRIDGE_LAYOUTS_DEFAULT          |
| Layouts[1]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER      |
| Layouts[2]             | UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT      |
| Layouts[3]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS  |
| FixedSizes[0]          | UX_PICTBRIDGE_FIXED_SIZE_DEFAULT       |
| FixedSizes[1]          | UX_PICTBRIDGE_FIXED_SIZE_35IX5I        |
| FixedSizes[2]          | UX_PICTBRIDGE_FIXED_SIZE_4IX6I         |
| FixedSizes[3]          | UX_PICTBRIDGE_FIXED_SIZE_5IX7I         |
| FixedSizes[4]          | UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM      |
| FixedSizes[5]          | UX_PICTBRIDGE_FIXED_SIZE_LETTER        |
| FixedSizes[6]          | UX_PICTBRIDGE_FIXED_SIZE_A4            |
| Croppings[0]           | UX_PICTBRIDGE_CROPPINGS_DEFAULT        |
| Croppings[1]           | UX_PICTBRIDGE_CROPPINGS_OFF            |
| Croppings[2]           | UX_PICTBRIDGE_CROPPINGS_ON             |

La máquina de estados del host de DPS se establecerá en Idle (Inactivo) y estará lista para aceptar un nuevo trabajo de impresión.

La parte del host de PictBridge ahora puede iniciarse como se muestra en el ejemplo siguiente:

```C
/* Activate the pictbridge dpshost. */
status = ux_pictbridge_dpshost_start(&pictbridge, pima);

if (status != UX_SUCCESS)
    return;
```

La función de host de PictBridge requiere una devolución de llamada cuando los datos están listos para imprimirse. Esto se logra pasando un señalador de función en la estructura de host de PictBridge como se indica a continuación:

```C
/* Set a callback when an object is being received. */
pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

Esta función tiene las propiedades siguientes.

## <a name="ux_pictbridge_application_object_data_write"></a>ux_pictbridge_application_object_data_write

Escritura de un bloque de datos para imprimirlo.

### <a name="prototype"></a>Prototipo

```C
UINT ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge, 
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando el servidor de DPS necesita recuperar un bloque de datos del cliente de DPS para imprimir en la impresora local.

### <a name="parameters"></a>Parámetros

- **pictbridge**: señalador a la instancia de clase pictbridge.
- **object_buffer**: señalador al búfer del objeto
- **object_offset**: lugar donde se empieza a leer el bloque de datos
- **total_length**: longitud total del objeto
- **length**: longitud de este búfer

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00): esta operación se realizó correctamente.
- **UX_ERROR** (0x01): La aplicación no pudo imprimir los datos.

### <a name="example"></a>Ejemplo

```C
/* Copy the object data. */
UINT tx_demo_object_data_write(UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer, ULONG offset, ULONG total_length, ULONG length);
{
    UINT status;
    /* Send the data to the local printer. */
    status = local_printer_data_send(object_buffer, length);

    /* We have printed the requested data. Return status. */
    return(status);
}
```
