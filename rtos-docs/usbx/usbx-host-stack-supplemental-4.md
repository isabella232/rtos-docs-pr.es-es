---
title: Implementación de USBX PictBridge
description: USBX admite la implementación completa de PictBridge tanto en el host como en el dispositivo. PictBridge se encuentra en la parte superior de la clase PIMA de USBX, en ambos lados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ce291f794cbc458d402cbefa3fd81dcc6f371b57
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816078"
---
# <a name="chapter-4-usbx-pictbridge-implementation"></a><span data-ttu-id="29439-104">Capítulo 4: Implementación de USBX PictBridge</span><span class="sxs-lookup"><span data-stu-id="29439-104">Chapter 4: USBX Pictbridge implementation</span></span>

<span data-ttu-id="29439-105">USBX admite la implementación completa de PictBridge tanto en el host como en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="29439-105">UBSX supports the full Pictbridge implementation both on the host and the device.</span></span> <span data-ttu-id="29439-106">PictBridge se encuentra en la parte superior de la clase PIMA de USBX, en ambos lados.</span><span class="sxs-lookup"><span data-stu-id="29439-106">Pictbridge sits on top of USBX PIMA class on both sides.</span></span> 

<span data-ttu-id="29439-107">Los estándares de PictBridge permite la conexión de una cámara fija digital o un smartphone directamente a una impresora sin un PC, lo que permite la impresión directa en algunas impresoras compatibles con PictBridge.</span><span class="sxs-lookup"><span data-stu-id="29439-107">The PictBridge standards allows the connection of a digital still camera or a smart phone directly to a printer without a PC, enabling direct printing to certain Pictbridge aware printers.</span></span>

<span data-ttu-id="29439-108">Cuando se conecta una cámara o un teléfono a una impresora, esta es el host USB y la cámara es el dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="29439-108">When a camera or phone is connected to a printer, the printer is the USB host and the camera is the USB device.</span></span> <span data-ttu-id="29439-109">Pero, con PictBridge, la cámara aparecerá como el host y esta controlará los comandos.</span><span class="sxs-lookup"><span data-stu-id="29439-109">However, with Pictbridge, the camera will appear as being the host and commands are driven from the camera.</span></span> <span data-ttu-id="29439-110">La cámara es el servidor de almacenamiento y la impresora, el cliente de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="29439-110">The camera is the storage server, the printer the storage client.</span></span> <span data-ttu-id="29439-111">La cámara es el cliente de impresión y la impresora es el servidor de impresión.</span><span class="sxs-lookup"><span data-stu-id="29439-111">The camera is the print client and the printer is, of course, the print server.</span></span>

<span data-ttu-id="29439-112">PictBridge usa USB como capa de transporte, pero se basa en PTP (Protocolo de transferencia de imágenes) para el protocolo de comunicación.</span><span class="sxs-lookup"><span data-stu-id="29439-112">Pictbridge uses USB as a transport layer but relies on PTP (Picture Transfer Protocol) for the communication protocol.</span></span>

<span data-ttu-id="29439-113">A continuación se presenta un diagrama de los comandos y las respuestas entre el cliente de DPS y el servidor de DPS cuando se produce un trabajo de impresión.</span><span class="sxs-lookup"><span data-stu-id="29439-113">The following is a diagram of the commands/responses between the DPS client and the DPS server when a print job occurs.</span></span>

![Diagrama de los comandos y las respuestas entre el cliente de DPS y el servidor de DPS cuando se produce un trabajo de impresión.](./media/usbx-host-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a><span data-ttu-id="29439-115">Implementación del cliente PictBridge</span><span class="sxs-lookup"><span data-stu-id="29439-115">Pictbridge client implementation</span></span>

<span data-ttu-id="29439-116">El PictBridge en el cliente requiere que la pila del dispositivo USBX y la clase PIMA se ejecuten en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="29439-116">The Pictbridge on the client requires the USBX device stack and the PIMA class to be running first.</span></span>

<span data-ttu-id="29439-117">Un marco de dispositivo describe la clase PIMA de la siguiente manera.</span><span class="sxs-lookup"><span data-stu-id="29439-117">A device framework describes the PIMA class in the following way.</span></span>

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

<span data-ttu-id="29439-118">La clase PIMA usa el campo de identificador 0x06, su subclase es 0x01 para la imagen fija y el protocolo es 0x01 para la clase PIMA 15740.</span><span class="sxs-lookup"><span data-stu-id="29439-118">The Pima class is using the ID field 0x06 and has its subclass is 0x01 for Still Image and the protocol is 0x01 for PIMA 15740.</span></span>

<span data-ttu-id="29439-119">En esta clase se definen 3 puntos de conexión, 2 en masa para enviar y recibir datos y uno para interrumpir los eventos.</span><span class="sxs-lookup"><span data-stu-id="29439-119">3 endpoints are defined in this class, 2 bulks for sending/receiving data and one interrupt for events.</span></span>

<span data-ttu-id="29439-120">A diferencia de otras implementaciones de dispositivos USBX, la aplicación PictBridge no necesita definir una clase en sí.</span><span class="sxs-lookup"><span data-stu-id="29439-120">Unlike other USBX device implementations, the Pictbridge application does not need to define a class itself.</span></span> <span data-ttu-id="29439-121">En su lugar, invoca la función ***ux_pictbridge_dpsclient_start***.</span><span class="sxs-lookup"><span data-stu-id="29439-121">Rather it invokes the function ***ux_pictbridge_dpsclient_start***.</span></span> <span data-ttu-id="29439-122">A continuación se muestra un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="29439-122">An example is below:</span></span>

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "Azure RTOS",10);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.
    ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="29439-123">Los parámetros que se pasan al cliente de PictBridge son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="29439-123">The parameters passed to the pictbridge client are as follows:</span></span>

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no,
    : String of serial number pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version pictbridge.ux_pictbridge_dpslocal. ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

<span data-ttu-id="29439-124">El siguiente paso es la sincronización del dispositivo y el host para que estén listos para intercambiar información.</span><span class="sxs-lookup"><span data-stu-id="29439-124">The next step is for the device and the host to synchronize and be ready to exchange information.</span></span>

<span data-ttu-id="29439-125">Esto se hace esperando a una marca de evento de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="29439-125">This is done by waiting on an event flag as follows:</span></span>

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get
    (&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR, &actual_flags,
    UX_PICTBRIDGE_EVENT_TIMEOUT);
```

<span data-ttu-id="29439-126">Si la máquina de estados está en el estado **DISCOVERY_COMPLETE**, el lado de la cámara (el cliente de DPS) recopilará la información relacionada con la impresora y sus capacidades.</span><span class="sxs-lookup"><span data-stu-id="29439-126">If the state machine is in the **DISCOVERY_COMPLETE** state, the camera side (the DPS client) will gather information regarding the printer and its capabilities.</span></span>

<span data-ttu-id="29439-127">Si el cliente de DPS está listo para aceptar un trabajo de impresión, su estado se establecerá en **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="29439-127">If the DPS client is ready to accept a print job, its status will be set to **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span></span> <span data-ttu-id="29439-128">Se puede comprobar de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="29439-128">It can be checked below:</span></span>

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)

    /* We can print something … */
```

<span data-ttu-id="29439-129">A continuación, se deben rellenar los descriptores de trabajos de impresión como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="29439-129">Next some print joib descriptors need to be filled as follows:</span></span>

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo ->ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo ->ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo ->ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo ->ux_pictbridge_jobinfo_object_data_read =
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
object ->ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object ->ux_device_class_pima_object_compressed_size = IMAGE_LEN; object ->ux_device_class_pima_object_offset = 0;
object ->ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object ->ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

<span data-ttu-id="29439-130">El cliente PictBridge tiene ahora un trabajo de impresión para realizar y capturará los bloques de imagen desde la aplicación mediante la devolución de llamada definida en el campo.</span><span class="sxs-lookup"><span data-stu-id="29439-130">The Pictbridge client now has a print job to do and will fetch the image blocks at a time from the application through the callback defined in the field.</span></span>

```C
jobinfo ->ux_pictbridge_jobinfo_object_data_read
```

<span data-ttu-id="29439-131">El prototipo de esa función se define como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="29439-131">The prototype of that function is defined as follows.</span></span>

## <a name="ux_pictbridge_jobinfo_object_data_read"></a><span data-ttu-id="29439-132">ux_pictbridge_jobinfo_object_data_read</span><span class="sxs-lookup"><span data-stu-id="29439-132">ux_pictbridge_jobinfo_object_data_read</span></span>

<span data-ttu-id="29439-133">Copia de un bloque de datos del espacio de usuario para imprimirlos.</span><span class="sxs-lookup"><span data-stu-id="29439-133">Copying a block of data from user space for printing.</span></span>

### <a name="prototype"></a><span data-ttu-id="29439-134">Prototipo</span><span class="sxs-lookup"><span data-stu-id="29439-134">Prototype</span></span>

```C
UINT **ux_pictbridge_jobinfo_object_data_read(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="29439-135">Descripción</span><span class="sxs-lookup"><span data-stu-id="29439-135">Description</span></span>

<span data-ttu-id="29439-136">Se llama a esta función cuando el cliente de DPS necesita recuperar un bloque de datos para imprimirlo en la impresora PictBridge de destino.</span><span class="sxs-lookup"><span data-stu-id="29439-136">This function is called when the DPS client needs to retrieve a data block to print to the target Pictbridge printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="29439-137">Parámetros</span><span class="sxs-lookup"><span data-stu-id="29439-137">Parameters</span></span>

- <span data-ttu-id="29439-138">**pictbridge**: puntero que señala a la instancia de clase pictbridge.</span><span class="sxs-lookup"><span data-stu-id="29439-138">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="29439-139">**object_buffer**: puntero que señala al búfer del objeto</span><span class="sxs-lookup"><span data-stu-id="29439-139">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="29439-140">**object_offset**: lugar donde se empieza a leer el bloque de datos</span><span class="sxs-lookup"><span data-stu-id="29439-140">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="29439-141">**object_length**: longitud que se va a devolver</span><span class="sxs-lookup"><span data-stu-id="29439-141">**object_length**: Length to be returned</span></span>
- <span data-ttu-id="29439-142">**actual_length**: longitud real devuelta</span><span class="sxs-lookup"><span data-stu-id="29439-142">**actual_length**: Actual length returned</span></span>

### <a name="return-value"></a><span data-ttu-id="29439-143">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="29439-143">Return Value</span></span>

- <span data-ttu-id="29439-144">**UX_SUCCESS**: (0x00) La operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="29439-144">**UX_SUCCESS**: (0x00) This operation was successful.</span></span>
- <span data-ttu-id="29439-145">**UX_ERROR**: (0x01) La aplicación no pudo recuperar los datos.</span><span class="sxs-lookup"><span data-stu-id="29439-145">**UX_ERROR**: (0x01) The application could not retrieve data.</span></span>

### <a name="example"></a><span data-ttu-id="29439-146">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="29439-146">Example</span></span>

```C
/* Copy the object data. */

UINT ux_demo_object_data_copy(UX_PICTBRIDGE *pictbridge,UCHAR *object_buffer,
    ULONG object_offset, ULONG object_length, ULONG *actual_length)
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

## <a name="pictbridge-host-implementation"></a><span data-ttu-id="29439-147">Implementación del host PictBridge</span><span class="sxs-lookup"><span data-stu-id="29439-147">Pictbridge host implementation</span></span>

<span data-ttu-id="29439-148">La implementación del host de PictBridge es diferente a la del cliente.</span><span class="sxs-lookup"><span data-stu-id="29439-148">The host implementation of Pictbridge is different from the client.</span></span>

<span data-ttu-id="29439-149">Lo primero que hay que hacer en un entorno de host PictBridge es registrar la clase PIMA como se muestra en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="29439-149">The first thing to do in a Pictbridge host environment is to register the Pima class as the example below shows:</span></span>

```C
status = ux_host_stack_class_register(ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="29439-150">Esta clase es la capa de PTP genérica que se encuentra entre la pila de host USB y la capa PictBridge.</span><span class="sxs-lookup"><span data-stu-id="29439-150">This class is the generic PTP layer sitting between the USB host stack and the Pictbridge layer.</span></span>

<span data-ttu-id="29439-151">El siguiente paso consiste en inicializar los valores predeterminados de PictBridge para los servicios de impresión como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="29439-151">The next step is to initialize the Pictbridge default values for print services as follows.</span></span>

| <span data-ttu-id="29439-152">Campo de PictBridge</span><span class="sxs-lookup"><span data-stu-id="29439-152">Pictbridge field</span></span>       | <span data-ttu-id="29439-153">Value</span><span class="sxs-lookup"><span data-stu-id="29439-153">Value</span></span>                                  |
|------------------------|----------------------------------------|
| <span data-ttu-id="29439-154">DpsVersion[0]</span><span class="sxs-lookup"><span data-stu-id="29439-154">DpsVersion[0]</span></span>          | <span data-ttu-id="29439-155">0x00010000</span><span class="sxs-lookup"><span data-stu-id="29439-155">0x00010000</span></span>                             |
| <span data-ttu-id="29439-156">DpsVersion[1]</span><span class="sxs-lookup"><span data-stu-id="29439-156">DpsVersion[1]</span></span>          | <span data-ttu-id="29439-157">0x00010001</span><span class="sxs-lookup"><span data-stu-id="29439-157">0x00010001</span></span>                             |
| <span data-ttu-id="29439-158">DpsVersion[2]</span><span class="sxs-lookup"><span data-stu-id="29439-158">DpsVersion[2]</span></span>          | <span data-ttu-id="29439-159">0x00000000</span><span class="sxs-lookup"><span data-stu-id="29439-159">0x00000000</span></span>                             |
| <span data-ttu-id="29439-160">VendorSpecificVersion</span><span class="sxs-lookup"><span data-stu-id="29439-160">VendorSpecificVersion</span></span>  | <span data-ttu-id="29439-161">0x00010000</span><span class="sxs-lookup"><span data-stu-id="29439-161">0x00010000</span></span>                             |
| <span data-ttu-id="29439-162">PrintServiceAvailable</span><span class="sxs-lookup"><span data-stu-id="29439-162">PrintServiceAvailable</span></span>  | <span data-ttu-id="29439-163">0x30010000</span><span class="sxs-lookup"><span data-stu-id="29439-163">0x30010000</span></span>                             |
| <span data-ttu-id="29439-164">Qualities[0]</span><span class="sxs-lookup"><span data-stu-id="29439-164">Qualities[0]</span></span>           | <span data-ttu-id="29439-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="29439-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span></span>        |
| <span data-ttu-id="29439-166">Qualities[1]</span><span class="sxs-lookup"><span data-stu-id="29439-166">Qualities[1]</span></span>           | <span data-ttu-id="29439-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span><span class="sxs-lookup"><span data-stu-id="29439-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span></span>         |
| <span data-ttu-id="29439-168">Qualities[2]</span><span class="sxs-lookup"><span data-stu-id="29439-168">Qualities[2]</span></span>           | <span data-ttu-id="29439-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span><span class="sxs-lookup"><span data-stu-id="29439-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span></span>          |
| <span data-ttu-id="29439-170">Qualities[3]</span><span class="sxs-lookup"><span data-stu-id="29439-170">Qualities[3]</span></span>           | <span data-ttu-id="29439-171">UX_PICTBRIDGE_QUALITIES_FINE</span><span class="sxs-lookup"><span data-stu-id="29439-171">UX_PICTBRIDGE_QUALITIES_FINE</span></span>           |
| <span data-ttu-id="29439-172">PaperSizes[0]</span><span class="sxs-lookup"><span data-stu-id="29439-172">PaperSizes[0]</span></span>          | <span data-ttu-id="29439-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="29439-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span></span>      |
| <span data-ttu-id="29439-174">PaperSizes[1]</span><span class="sxs-lookup"><span data-stu-id="29439-174">PaperSizes[1]</span></span>          | <span data-ttu-id="29439-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span><span class="sxs-lookup"><span data-stu-id="29439-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span></span>        |
| <span data-ttu-id="29439-176">PaperSizes[2]</span><span class="sxs-lookup"><span data-stu-id="29439-176">PaperSizes[2]</span></span>          | <span data-ttu-id="29439-177">UX_PICTBRIDGE_PAPER_SIZES_L</span><span class="sxs-lookup"><span data-stu-id="29439-177">UX_PICTBRIDGE_PAPER_SIZES_L</span></span>            |
| <span data-ttu-id="29439-178">PaperSizes[3]</span><span class="sxs-lookup"><span data-stu-id="29439-178">PaperSizes[3]</span></span>          | <span data-ttu-id="29439-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span><span class="sxs-lookup"><span data-stu-id="29439-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span></span>           |
| <span data-ttu-id="29439-180">PaperSizes[4]</span><span class="sxs-lookup"><span data-stu-id="29439-180">PaperSizes[4]</span></span>          | <span data-ttu-id="29439-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span><span class="sxs-lookup"><span data-stu-id="29439-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span></span>       |
| <span data-ttu-id="29439-182">PaperTypes[0]</span><span class="sxs-lookup"><span data-stu-id="29439-182">PaperTypes[0]</span></span>          | <span data-ttu-id="29439-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="29439-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span></span>      |
| <span data-ttu-id="29439-184">PaperTypes[1]</span><span class="sxs-lookup"><span data-stu-id="29439-184">PaperTypes[1]</span></span>          | <span data-ttu-id="29439-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span><span class="sxs-lookup"><span data-stu-id="29439-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span></span>        |
| <span data-ttu-id="29439-186">PaperTypes[2]</span><span class="sxs-lookup"><span data-stu-id="29439-186">PaperTypes[2]</span></span>          | <span data-ttu-id="29439-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span><span class="sxs-lookup"><span data-stu-id="29439-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span></span>        |
| <span data-ttu-id="29439-188">FileTypes[0]</span><span class="sxs-lookup"><span data-stu-id="29439-188">FileTypes[0]</span></span>           | <span data-ttu-id="29439-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="29439-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span></span>       |
| <span data-ttu-id="29439-190">FileTypes[1]</span><span class="sxs-lookup"><span data-stu-id="29439-190">FileTypes[1]</span></span>           | <span data-ttu-id="29439-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="29439-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span></span>     |
| <span data-ttu-id="29439-192">FileTypes[2]</span><span class="sxs-lookup"><span data-stu-id="29439-192">FileTypes[2]</span></span>           | <span data-ttu-id="29439-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span><span class="sxs-lookup"><span data-stu-id="29439-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span></span>          |
| <span data-ttu-id="29439-194">FileTypes[3]</span><span class="sxs-lookup"><span data-stu-id="29439-194">FileTypes[3]</span></span>           | <span data-ttu-id="29439-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span><span class="sxs-lookup"><span data-stu-id="29439-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span></span>          |
| <span data-ttu-id="29439-196">DatePrints[0]</span><span class="sxs-lookup"><span data-stu-id="29439-196">DatePrints[0]</span></span>          | <span data-ttu-id="29439-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="29439-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span></span>      |
| <span data-ttu-id="29439-198">DatePrints[1]</span><span class="sxs-lookup"><span data-stu-id="29439-198">DatePrints[1]</span></span>          | <span data-ttu-id="29439-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="29439-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span></span>          |
| <span data-ttu-id="29439-200">DatePrints[2]</span><span class="sxs-lookup"><span data-stu-id="29439-200">DatePrints[2]</span></span>          | <span data-ttu-id="29439-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="29439-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span></span>           |
| <span data-ttu-id="29439-202">FileNamePrints[0]</span><span class="sxs-lookup"><span data-stu-id="29439-202">FileNamePrints[0]</span></span>      | <span data-ttu-id="29439-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="29439-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span></span> |
| <span data-ttu-id="29439-204">FileNamePrints[1]</span><span class="sxs-lookup"><span data-stu-id="29439-204">FileNamePrints[1]</span></span>      | <span data-ttu-id="29439-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="29439-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span></span>     |
| <span data-ttu-id="29439-206">FileNamePrints[2]</span><span class="sxs-lookup"><span data-stu-id="29439-206">FileNamePrints[2]</span></span>      | <span data-ttu-id="29439-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="29439-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span></span>      |
| <span data-ttu-id="29439-208">ImageOptimizes[0]</span><span class="sxs-lookup"><span data-stu-id="29439-208">ImageOptimizes[0]</span></span>      | <span data-ttu-id="29439-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="29439-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span></span>  |
| <span data-ttu-id="29439-210">ImageOptimizes[1]</span><span class="sxs-lookup"><span data-stu-id="29439-210">ImageOptimizes[1]</span></span>      | <span data-ttu-id="29439-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span><span class="sxs-lookup"><span data-stu-id="29439-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span></span>      |
| <span data-ttu-id="29439-212">ImageOptimizes[2]</span><span class="sxs-lookup"><span data-stu-id="29439-212">ImageOptimizes[2]</span></span>      | <span data-ttu-id="29439-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span><span class="sxs-lookup"><span data-stu-id="29439-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span></span>       |
| <span data-ttu-id="29439-214">Layouts[0]</span><span class="sxs-lookup"><span data-stu-id="29439-214">Layouts[0]</span></span>             | <span data-ttu-id="29439-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="29439-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span></span>          |
| <span data-ttu-id="29439-216">Layouts[1]</span><span class="sxs-lookup"><span data-stu-id="29439-216">Layouts[1]</span></span>             | <span data-ttu-id="29439-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span><span class="sxs-lookup"><span data-stu-id="29439-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span></span>      |
| <span data-ttu-id="29439-218">Layouts[2]</span><span class="sxs-lookup"><span data-stu-id="29439-218">Layouts[2]</span></span>             | <span data-ttu-id="29439-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span><span class="sxs-lookup"><span data-stu-id="29439-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span></span>      |
| <span data-ttu-id="29439-220">Layouts[3]</span><span class="sxs-lookup"><span data-stu-id="29439-220">Layouts[3]</span></span>             | <span data-ttu-id="29439-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span><span class="sxs-lookup"><span data-stu-id="29439-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span></span>  |
| <span data-ttu-id="29439-222">FixedSizes[0]</span><span class="sxs-lookup"><span data-stu-id="29439-222">FixedSizes[0]</span></span>          | <span data-ttu-id="29439-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="29439-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span></span>       |
| <span data-ttu-id="29439-224">FixedSizes[1]</span><span class="sxs-lookup"><span data-stu-id="29439-224">FixedSizes[1]</span></span>          | <span data-ttu-id="29439-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span><span class="sxs-lookup"><span data-stu-id="29439-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span></span>        |
| <span data-ttu-id="29439-226">FixedSizes[2]</span><span class="sxs-lookup"><span data-stu-id="29439-226">FixedSizes[2]</span></span>          | <span data-ttu-id="29439-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span><span class="sxs-lookup"><span data-stu-id="29439-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span></span>         |
| <span data-ttu-id="29439-228">FixedSizes[3]</span><span class="sxs-lookup"><span data-stu-id="29439-228">FixedSizes[3]</span></span>          | <span data-ttu-id="29439-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span><span class="sxs-lookup"><span data-stu-id="29439-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span></span>         |
| <span data-ttu-id="29439-230">FixedSizes[4]</span><span class="sxs-lookup"><span data-stu-id="29439-230">FixedSizes[4]</span></span>          | <span data-ttu-id="29439-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span><span class="sxs-lookup"><span data-stu-id="29439-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span></span>      |
| <span data-ttu-id="29439-232">FixedSizes[5]</span><span class="sxs-lookup"><span data-stu-id="29439-232">FixedSizes[5]</span></span>          | <span data-ttu-id="29439-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span><span class="sxs-lookup"><span data-stu-id="29439-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span></span>        |
| <span data-ttu-id="29439-234">FixedSizes[6]</span><span class="sxs-lookup"><span data-stu-id="29439-234">FixedSizes[6]</span></span>          | <span data-ttu-id="29439-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span><span class="sxs-lookup"><span data-stu-id="29439-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span></span>            |
| <span data-ttu-id="29439-236">Croppings[0]</span><span class="sxs-lookup"><span data-stu-id="29439-236">Croppings[0]</span></span>           | <span data-ttu-id="29439-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="29439-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span></span>        |
| <span data-ttu-id="29439-238">Croppings[1]</span><span class="sxs-lookup"><span data-stu-id="29439-238">Croppings[1]</span></span>           | <span data-ttu-id="29439-239">UX_PICTBRIDGE_CROPPINGS_OFF</span><span class="sxs-lookup"><span data-stu-id="29439-239">UX_PICTBRIDGE_CROPPINGS_OFF</span></span>            |
| <span data-ttu-id="29439-240">Croppings[2]</span><span class="sxs-lookup"><span data-stu-id="29439-240">Croppings[2]</span></span>           | <span data-ttu-id="29439-241">UX_PICTBRIDGE_CROPPINGS_ON</span><span class="sxs-lookup"><span data-stu-id="29439-241">UX_PICTBRIDGE_CROPPINGS_ON</span></span>             |

<span data-ttu-id="29439-242">La máquina de estados del host de DPS se establecerá en Idle (Inactivo) y estará lista para aceptar un nuevo trabajo de impresión.</span><span class="sxs-lookup"><span data-stu-id="29439-242">The state machine of the DPS host will be set to Idle and ready to accept a new print job.</span></span>

<span data-ttu-id="29439-243">La parte del host de PictBridge ahora puede iniciarse como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="29439-243">The host portion of Pictbridge can now be started as the example below shows.</span></span>

```C
/* Activate the pictbridge dpshost. */

status = ux_pictbridge_dpshost_start(&pictbridge, pima);
if (status != UX_SUCCESS)
    return;
```

<span data-ttu-id="29439-244">La función de host de PictBridge requiere una devolución de llamada cuando los datos están listos para imprimirse.</span><span class="sxs-lookup"><span data-stu-id="29439-244">The Pictbridge host function requires a callback when data is ready to be printed.</span></span> <span data-ttu-id="29439-245">Esto se logra pasando un puntero de función en la estructura de host de PictBridge como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="29439-245">This is accomplished by passing a function pointer in the pictbridge host structure as follows.</span></span>

```C
/* Set a callback when an object is being received. */

pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

<span data-ttu-id="29439-246">Esta función tiene las propiedades siguientes:</span><span class="sxs-lookup"><span data-stu-id="29439-246">This function has the following properties:</span></span>

## <a name="ux_pictbridge_application_object_data_write"></a><span data-ttu-id="29439-247">ux_pictbridge_application_object_data_write</span><span class="sxs-lookup"><span data-stu-id="29439-247">ux_pictbridge_application_object_data_write</span></span>

<span data-ttu-id="29439-248">Escritura de un bloque de datos para imprimirlo.</span><span class="sxs-lookup"><span data-stu-id="29439-248">Writing a block of data for printing.</span></span>

### <a name="prototype"></a><span data-ttu-id="29439-249">Prototipo</span><span class="sxs-lookup"><span data-stu-id="29439-249">Prototype</span></span>

```C
UINT **ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="29439-250">Descripción</span><span class="sxs-lookup"><span data-stu-id="29439-250">Description</span></span>

<span data-ttu-id="29439-251">Se llama a esta función cuando el servidor de DPS necesita recuperar un bloque de datos del cliente de DPS para imprimir en la impresora local.</span><span class="sxs-lookup"><span data-stu-id="29439-251">This function is called when the DPS server needs to retrieve a data block from the DPS client to print to the local printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="29439-252">Parámetros</span><span class="sxs-lookup"><span data-stu-id="29439-252">Parameters</span></span>

- <span data-ttu-id="29439-253">**pictbridge**: puntero que señala a la instancia de clase pictbridge.</span><span class="sxs-lookup"><span data-stu-id="29439-253">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="29439-254">**object_buffer**: puntero que señala al búfer del objeto</span><span class="sxs-lookup"><span data-stu-id="29439-254">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="29439-255">**object_offset**: lugar donde se empieza a leer el bloque de datos</span><span class="sxs-lookup"><span data-stu-id="29439-255">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="29439-256">**total_length**: longitud total del objeto</span><span class="sxs-lookup"><span data-stu-id="29439-256">**total_length**: Entire length of object</span></span>
- <span data-ttu-id="29439-257">**length**: longitud de este búfer</span><span class="sxs-lookup"><span data-stu-id="29439-257">**length**: Length of this buffer</span></span>

### <a name="return-value"></a><span data-ttu-id="29439-258">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="29439-258">Return Value</span></span>

- <span data-ttu-id="29439-259">**UX_SUCCESS**: (0x00): la operación se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="29439-259">**UX_SUCCESS**: (0x00) This operation was successful.</span></span>
- <span data-ttu-id="29439-260">**UX_ERROR**: (0x01): la aplicación no ha podido imprimir los datos.</span><span class="sxs-lookup"><span data-stu-id="29439-260">**UX_ERROR**: (0x01) The application could not print data.</span></span>

### <a name="example"></a><span data-ttu-id="29439-261">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="29439-261">Example</span></span>

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
