---
title: 'Capítulo 5: Consideraciones acerca de la clase del dispositivo USBX'
description: Obtenga información sobre las consideraciones de la clase de dispositivo USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 84f215ad990a2fe185a08f3876276528787ef8bc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815081"
---
# <a name="chapter-5---usbx-device-class-considerations"></a>Capítulo 5: Consideraciones acerca de la clase del dispositivo USBX

## <a name="device-class-registration"></a>Registro de clase de dispositivo

Todas las clases de dispositivos siguen el mismo principio para el registro. Se pasa una estructura que contiene los parámetros específicos de clase a la función de inicialización de clase.

```c
/* Set the parameters for callback when insertion/extraction of a HID device. */

hid_parameter.ux_slave_class_hid_instance_activate = tx_demo_hid_instance_activate;

hid_parameter.ux_slave_class_hid_instance_deactivate = tx_demo_hid_instance_deactivate;

/* Initialize the hid class parameters for the device. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_device_report;

hid_parameter.ux_device_class_hid_parameter_report_length = HID_DEVICE_REPORT_LENGTH;

hid_parameter.ux_device_class_hid_parameter_report_id = UX_TRUE;
hid_parameter.ux_device_class_hid_parameter_callback = demo_thread_hid_callback;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry,1,0, (VOID *)&hid_parameter);
```

Cada clase puede registrar, opcionalmente, una función de devolución de llamada cuando se activa una instancia de la clase. La pila del dispositivo llama a la devolución de llamada para informar a la aplicación de que se ha creado una instancia.

La aplicación tendrá en su cuerpo las dos funciones correspondientes a la activación y desactivación, como se muestra en el ejemplo siguiente.

```c
VOID tx_demo_hid_instance_activate(VOID *hid_instance)
{
    /* Save the HID instance. */
    hid_slave = (UX_SLAVE_CLASS_HID *) hid_instance;
}

VOID tx_demo_hid_instance_deactivate(VOID *hid_instance)
{
    /* Reset the HID instance. */
    hid_slave = UX_NULL;
}
```

No se recomienda hacer nada en estas funciones, tan solo memorizar la instancia de la clase y sincronizar con el resto de la aplicación.

## <a name="usb-device-storage-class"></a>Clase de almacenamiento de dispositivo USB

La clase de almacenamiento de dispositivo USB permite que un dispositivo de almacenamiento insertado en el sistema sea visible para un host USB.

La clase de almacenamiento de dispositivo USB no proporciona por sí misma una solución de almacenamiento. Simplemente acepta e interpreta las solicitudes SCSI procedentes del host. Cuando una de estas solicitudes es un comando de lectura o escritura, invocará una devolución de llamada predefinida a un controlador de dispositivo de almacenamiento real, como un controlador de dispositivo ATA o un controlador de dispositivo Flash.

Al inicializar la clase de almacenamiento de dispositivo, se asigna una estructura de puntero a la clase que contiene toda la información necesaria. A continuación encontrará un ejemplo.

```c
/* Initialize the storage class parameters to customize vendor strings. */

storage_parameter.ux_slave_class_storage_parameter_vendor_id
    = demo_ux_system_slave_class_storage_vendor_id;

storage_parameter.ux_slave_class_storage_parameter_product_id
    = demo_ux_system_slave_class_storage_product_id;

storage_parameter.ux_slave_class_storage_parameter_product_rev
    = demo_ux_system_slave_class_storage_product_rev;

storage_parameter.ux_slave_class_storage_parameter_product_serial
    = demo_ux_system_slave_class_storage_product_serial;

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read_only_flag
    = UX_FALSE;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read
    = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write
    = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status
    = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,
    ux_device_class_storage_entry, ux_device_class_storage_thread, 0, (VOID *)&storage_parameter);
```

En este ejemplo, las cadenas de almacenamiento del controlador se personalizan asignando punteros de cadena al parámetro correspondiente. Si uno de los punteros de cadena se deja en UX_NULL, se usa la cadena predeterminada de Azure RTOS.

En este ejemplo, se proporciona la dirección del último bloque o LBA de la unidad, así como el tamaño del sector lógico. La LBA es el número de sectores disponibles en el medio: 1. La longitud del bloque se establece en 512 en medios de almacenamiento normales. Se puede establecer en 2048 para las unidades ópticas.

La aplicación debe pasar tres punteros de función de devolución de llamada para permitir que la clase de almacenamiento lea, escriba y obtenga el estado del medio.

En el ejemplo siguiente se muestran los prototipos de las funciones de lectura y escritura.

```c
UINT media_read( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);

UINT media_write( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);
```

Donde:

- *storage* es la instancia de la clase de almacenamiento.
- *lun* es el LUN al que se dirige el comando.
- *data_pointer* es la dirección del búfer que se va a usar para la lectura o escritura.
- *number_blocks* es el número de sectores para lectura y escritura.
- *lba* es la dirección del sector que se va a leer.
- *media_status* se debe rellenar exactamente como el valor devuelto de la devolución de llamada del estado del medio.

El valor devuelto puede tener el valor UX_SUCCESS o UX_ERROR que indica una operación correcta o incorrecta. Estas operaciones no necesitan devolver ningún otro código de error. Si hay un error en alguna operación, la clase de almacenamiento invocará la función de devolución de llamada de estado.

Esta función tiene el siguiente prototipo.

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

El parámetro de llamada media_id no se usa actualmente y siempre debe ser 0. En el futuro, podrá usarse para distinguir varios dispositivos de almacenamiento o dispositivos de almacenamiento con varios LUN SCSI. Esta versión de la clase de almacenamiento no admite varias instancias de la clase de almacenamiento o dispositivos de almacenamiento con varios LUN SCSI.

El valor devuelto es un código de error SCSI que puede tener el formato siguiente.

- **Bits de 0 a 7** Clave de detección
- **Bits de 8 a 15** Código de detección adicional (ASC)
- **Bits de 16 a 23** Código de detección adicional (ASCQ)

En la tabla siguiente se proporcionan las combinaciones posibles Sense/ASC/ASCQ.

| Clave de detección | ASC | ASCQ | Descripción                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| 00        | 00  | 00   | SIN DETECCIÓN                                          |
| 01        | 17  | 01   | DATOS RECUPERADOS CON REINTENTOS                       |
| 01        | 18  | 00   | DATOS RECUPERADOS CON ECC                           |
| 02        | 04  | 01   | UNIDAD LÓGICA NO PREPARADA: PREPARÁNDOSE          |
| 02        | 04  | 02   | UNIDAD LÓGICA NO PREPARADA: SE REQUIERE INICIALIZACIÓN |
| 02        | 04  | 04   | UNIDAD LÓGICA NO PREPARADA: FORMATO EN CURSO       |
| 02        | 04  | FF   | UNIDAD LÓGICA NO PREPARADA: EL DISPOSITIVO ESTÁ OCUPADO          |
| 02        | 06  | 00   | NO SE ENCONTRÓ NINGUNA POSICIÓN DE REFERENCIA                       |
| 02        | 08  | 00   | ERROR DE COMUNICACIÓN DE UNIDAD LÓGICA                |
| 02        | 08  | 01   | TIEMPO DE ESPERA DE COMUNICACIÓN DE UNIDAD LÓGICA               |
| 02        | 08  | 80   | SATURACIÓN DE COMUNICACIÓN DE UNIDAD LÓGICA                |
| 02        | 3A  | 00   | MEDIO NO PRESENTE                                |
| 02        | 54  | 00   | ERROR DE INTERFAZ DEL SISTEMA DE USB A HOST              |
| 02        | 80  | 00   | INSUFICIENTES RECURSOS                            |
| 02        | FF  | FF   | ERROR DESCONOCIDO                                     |
| 03        | 02  | 00   | NO SE COMPLETÓ LA BÚSQUEDA                                  |
| 03        | 03  | 00   | ERROR DE ESCRITURA                                       |
| 03        | 10  | 00   | ERROR CRC DE ID.                                      |
| 03        | 11  | 00   | ERROR DE LECTURA NO RECUPERADO                            |
| 03        | 12  | 00   | NO SE ENCONTRÓ LA MARCA DE DIRECCIÓN PARA EL CAMPO DE ID.               |
| 03        | 13  | 00   | NO SE ENCONTRÓ LA MARCA DE DIRECCIÓN PARA EL CAMPO DE DATOS             |
| 03        | 14  | 00   | NO SE ENCONTRÓ LA ENTIDAD REGISTRADA                         |
| 03        | 30  | 01   | NO SE PUEDE LEER EL MEDIO: FORMATO DESCONOCIDO               |
| 03        | 31  | 01   | ERROR DEL COMANDO DE FORMATO                             |
| 04        | 40  | NN   | ERROR DE DIAGNÓSTICO EN EL COMPONENTE NN (80H-FFH)      |
| 05        | 1A  | 00   | ERROR DE LONGITUD DE LA LISTA DE PARÁMETROS                       |
| 05        | 20  | 00   | CÓDIGO DE OPERACIÓN DE COMANDO NO VÁLIDO                    |
| 05        | 21  | 00   | DIRECCIÓN DE BLOQUE LÓGICO FUERA DEL INTERVALO                |
| 05        | 24  | 00   | CAMPO NO VÁLIDO EN EL PAQUETE DE COMANDOS                   |
| 05        | 25  | 00   | UNIDAD LÓGICA NO ADMITIDA                        |
| 05        | 26  | 00   | CAMPO NO VÁLIDO EN LA LISTA DE PARÁMETROS                   |
| 05        | 26  | 01   | PARÁMETRO NO ADMITIDO                           |
| 05        | 26  | 02   | VALOR DE PARÁMETRO NO VÁLIDO                           |
| 05        | 39  | 00   | NO SE ADMITE GUARDAR PARÁMETROS                     |
| 06        | 28  | 00   | TRANSICIÓN DE NO PREPARADO A PREPARADO: SE CAMBIÓ EL MEDIO     |
| 06        | 29  | 00   | SE HA PRODUCIDO UN RESTABLECIMIENTO DE ENCENDIDO O DE DISPOSITIVO DE BUS       |
| 06        | 2F  | 00   | COMANDOS DESACTIVADOS POR OTRO INICIADOR             |
| 07        | 27  | 00   | MEDIO PROTEGIDO CONTRA ESCRITURA                             |
| 0B        | 4E  | 00   | SE INTENTÓ UN COMANDO SUPERPUESTO                      |

Hay dos devoluciones de llamada adicionales opcionales que la aplicación puede implementar; una es para responder a un comando **GET_STATUS_NOTIFICATION** y la otra es para responder al comando **SYNCHRONIZE_CACHE**.

Si la aplicación desea controlar el comando GET_STATUS_NOTIFICATION desde el host, debe implementar una devolución de llamada con el siguiente prototipo.

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

Donde:

- *storage* es la instancia de la clase de almacenamiento.
- *media_id* no se usa actualmente. notification_class especifica la clase de notificación.
- La aplicación debe establecer *media_notification* en el búfer que contiene la respuesta de la notificación.
- La aplicación debe establecer *media_notification_length* para que contenga la longitud del búfer de respuesta.

El valor devuelto indica si el comando se ha ejecutado correctamente o no; debe ser **UX_SUCCESS** o **UX_ERROR**.

Si la aplicación no implementa esta devolución de llamada, al recibir el comando **GET_STATUS_NOTIFICATION**, USBX notificará al host que el comando no está implementado.

El comando **SYNCHRONIZE_CACHE** debe procesarse si la aplicación usa una caché para las escrituras desde el host. Un host puede enviar este comando si sabe que el dispositivo de almacenamiento está a punto de desconectarse, por ejemplo, en Windows, si hace clic con el botón secundario en el icono de una unidad flash de la barra de herramientas y selecciona "Expulsar \[nombre del dispositivo de almacenamiento\]", Windows emitirá el comando **SYNCHRONIZE_CACHE** a ese dispositivo.

Si la aplicación quiere procesar el comando **GET_STATUS_NOTIFICATION** desde el host, debe implementar una devolución de llamada con el siguiente prototipo.

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

Donde:

- *storage* es la instancia de la clase de almacenamiento.
- *lun* es un parámetro que especifica a qué LUN se dirige el comando.
- *number_blocks* especifica el número de bloques que se van a sincronizar.
- *lba* es la dirección del sector del primer bloque que se va a sincronizar.
- *media_status* se debe rellenar exactamente como el valor devuelto de la devolución de llamada del estado del medio.

El valor devuelto indica si el comando se ha ejecutado correctamente o no; debe ser **UX_SUCCESS** o **UX_ERROR**.

### <a name="multiple-scsi-lun"></a>LUN SCSI múltiple

La clase de almacenamiento de dispositivo USBX admite varios LUN. Por lo tanto, es posible crear un dispositivo de almacenamiento que actúe como un CD-ROM y un disco Flash al mismo tiempo. En tal caso, la inicialización sería ligeramente diferente. A continuación, se muestra un ejemplo de un disco Flash y un CD-ROM:

```c
/* Store the number of LUN in this device storage instance. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 2;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x7bbff;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the storage class LUN parameters for reading/writing to the CD-ROM. */

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_last_lba = 0x04caaf;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_block_length = 2048;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_type = 5;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_read = tx_demo_thread_cdrom_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_write = tx_demo_thread_cdrom_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_status = tx_demo_thread_cdrom_media_status;

/* Initialize the device storage class for a Flash disk and CD-ROM. The class is connected with interface 0 */ status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *) &storage_parameter);
```

## <a name="usb-device-cdc-acm-class"></a>Clase CDC-ACM de dispositivo USB

La clase CDC-ACM de dispositivo host USB permite que un sistema host USB se comunique con el dispositivo como un dispositivo serie. Esta clase se basa en el estándar USB y es un subconjunto del estándar CDC.

Un marco de dispositivos compatible con CDC-ACM debe declararse en la pila de dispositivos. A continuación, se muestra un ejemplo.

```c
unsigned char device_framework_full_speed[] = {

    /*
    Device descriptor 18 bytes
    0x02 bDeviceClass: CDC class code
    0x00 bDeviceSubclass: CDC class sub code 0x00 bDeviceProtocol: CDC Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    0x12, 0x01, 0x10, 0x01,
    0xEF, 0x02, 0x01, 0x08,
    0x84, 0x84, 0x00, 0x00,
    0x00, 0x01, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration 1 descriptor 9 bytes */
    0x09, 0x02, 0x4b, 0x00, 0x02, 0x01, 0x00,0x40, 0x00,

    /* Interface association descriptor. 8 bytes. */
    0x08, 0x0b, 0x00,
    0x02, 0x02, 0x02, 0x00, 0x00,

    /* Communication Class Interface Descriptor Requirement. 9 bytes. */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x02, 0x01, 0x00,

    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00,0x10, 0x01,

    /* ACM Functional Descriptor 4 bytes */
    0x04, 0x24, 0x02,0x0f,

    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,

    /* Master interface */
    0x01, /* Slave interface */

    /* Call Management Functional Descriptor 5 bytes */
    0x05, 0x24, 0x01,0x03, 0x01, /* Data interface */

    /* Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x83, 0x03,0x08, 0x00, 0xFF,

    /* Data Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x02,0x0A, 0x00, 0x00, 0x00,

    /* First alternate setting Endpoint 1 descriptor 7 bytes*/
    0x07, 0x05, 0x02,0x02,0x40, 0x00,0x00,

    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81,0x02,0x40, 0x00, 0x00,

};
```

La clase CDC-ACM usa un marco de dispositivo compuesto para agrupar interfaces (control y datos). Como resultado, debe tener cuidado al definir el descriptor de dispositivo. USBX se basa en el descriptor IAD para saber internamente cómo enlazar interfaces. El descriptor IAD debe declararse antes de las interfaces y contener la primera interfaz de la clase CDC-ACM y el número de interfaces asociadas.

La clase CDC-ACM también usa un descriptor funcional de unión que realiza la misma función que el descriptor IAD más reciente. Aunque debe declararse un descriptor funcional de unión por motivos históricos y por compatibilidad con el lado host, USBX no lo usa.

La inicialización de la clase CDC-ACM espera los siguientes parámetros.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

Los dos parámetros definidos son punteros de devolución de llamada a las aplicaciones de usuario a las que se llamará cuando la pila active o desactive esta clase.

El tercer parámetro definido es un puntero de devolución de llamada a la aplicación de usuario a la que se llamará cuando se produzca un cambio de parámetro de código de línea o de estado de línea. Por ejemplo, cuando hay una solicitud del host para cambiar el estado DTR a **TRUE**, se invoca la devolución de llamada, en ella la aplicación de usuario puede comprobar los estados de línea a través de la función IOCTL para saber si el host está preparado para la comunicación.

CDC-ACM se basa en un estándar USB-IF y se reconoce de forma automática por los sistemas operativos MAC y Linux. En las plataformas de Windows, esta clase requiere un archivo. inf para la versión de Windows anterior a la versión 10. Windows 10 no requiere ningún archivo. inf. Asimismo, proporcionamos una plantilla para la clase CDC-ACM que se puede encontrar en el directorio ***usbx_windows_host_files***. Para obtener una versión más reciente de Windows, se debe usar el archivo CDC_ACM_Template_Win7_64bit.inf (excepto Win10). Este archivo debe modificarse para reflejar el valor de PID/VID que usa el dispositivo. El valor PID/VID será específico para el cliente final cuando la empresa y el producto se registren mediante el valor USB-IF. En el archivo .inf, los campos que se van a modificar se encuentran aquí.

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

En el marco del dispositivo CDC-ACM, el valor PID/VID se almacena en el descriptor del dispositivo (consulte el descriptor de dispositivo que se declaró anteriormente).

Cuando un sistema host USB detecta el dispositivo USB CDC-ACM, monta una clase serie y el dispositivo se puede usar con cualquier programa de terminal serie. Consulte el sistema operativo host como referencia.

A continuación, se definen las funciones de API de clase CDC-ACM.

### <a name="ux_device_class_cdc_acm_ioctl"></a>ux_device_class_cdc_acm_ioctl

Ejecutar IOCTL en la interfaz CDC-ACM

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita realizar varias llamadas IOCTL a la interfaz CDC-ACM.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **ioctl_function**: función IOCTL que se va a realizar.
- **parameter**: puntero a un parámetro específico de la llamada IOCTL.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a>Funciones IOCTL:

| Función                                        | Value |
| ----------------------------------------------- | - |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING    | 1 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING    | 2 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE     | 3 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE         | 4 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE     | 5 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START | 6 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP  | 7 |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING

Ejecutar el establecimiento de codificación de línea de IOCTL en la interfaz CDC-AC M

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita establecer los parámetros de codificación de línea.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- **parámetro**: puntero a una estructura de parámetros de línea:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>Valor devuelto

**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.

### <a name="example"></a>Ejemplo

```c
/* Change the line coding values. */

line_coding.ux_slave_class_cdc_acm_line_coding_dter = 9600;
line_coding.ux_slave_class_cdc_acm_line_coding_stop_bit =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_STOP_BIT_15;

line_coding.ux_slave_class_cdc_acm_line_coding_parity =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_PARITY_EVEN;

line_coding.ux_slave_class_cdc_acm_line_coding_data_bits = 5;

status = _ux_slave_class_cdc_acm_ioctl(cdc_acm,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING, &line_coding);

if (status != UX_SUCCESS)
    break;
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING

Ejecutar la obtención de la codificación de línea de IOCTL en la interfaz CDC-ACM

### <a name="prototype"></a>Prototipo

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita obtener los parámetros de codificación de línea.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING
- **parámetro**: puntero a una estructura de parámetros de línea:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.

### <a name="example"></a>Ejemplo

```c
/* This is to retrieve BAUD rate. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, &line_coding);

/* Any error ? */
if (status == UX_SUCCESS)
{
    /* Decode BAUD rate. */
    switch (line_coding.ux_slave_class_cdc_acm_parameter_baudrate)
    {
        case 1200 :
            status = tx_demo_thread_slave_cdc_acm_response("1200", 4);
            break;
        case 2400 :
            status = tx_demo_thread_slave_cdc_acm_response("2400", 4);
            break;
        case 4800 :
            status = tx_demo_thread_slave_cdc_acm_response("4800", 4);
            break;
        case 9600 :
            status = tx_demo_thread_slave_cdc_acm_response("9600", 4);
            break;
        case 115200 :
            status = tx_demo_thread_slave_cdc_acm_response("115200", 6);
            break;
    }
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE

Ejecutar la obtención de estado de línea de IOCTL en la interfaz CDC-ACM

## <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita obtener los parámetros de estado de línea.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE
- **parámetro**: puntero a una estructura de parámetros de línea:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.

### <a name="example"></a>Ejemplo

```c
/* This is to retrieve RTS state. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE, &line_state);

/* Any error ? */
if (status == UX_SUCCESS)
{
/* Check state. */
    if (line_state.ux_slave_class_cdc_acm_parameter_rts == UX_TRUE)
        /* State is ON. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS ON", 6);
    else
        /* State is OFF. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS OFF", 7);
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE

Ejecutar el establecimiento de estado de línea de IOCTL en la interfaz CDC-ACM

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita obtener los parámetros de estado de línea.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- **parámetro**: puntero a una estructura de parámetros de línea:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.

### <a name="example"></a>Ejemplo

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE

Ejecutar ABORT PIPE de IOCTL en la interfaz CDC-ACM

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita anular una canalización. Por ejemplo, para anular una escritura en curso, se debe pasar UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT como parámetro.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE
- **parámetro**: la dirección de la canalización:

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Dirección de canalización no válida.

### <a name="example"></a>Ejemplo

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START

Ejecutar el inicio de la transmisión de IOCTL en la interfaz CDC-ACM

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación desea usar la transmisión con devolución de llamada.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START
- **parámetro**: puntero a la estructura del parámetro de inicio de transmisión:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.
- **UX_ERROR** (0xFF) La transmisión ya se ha iniciado.
- **UX_MEMORY_INSUFFICIENT** (0x12) Error en una asignación de memoria.

### <a name="example"></a>Ejemplo

```c
/* Set the callback parameter. */

callback.ux_device_class_cdc_acm_parameter_write_callback
    = tx_demo_thread_slave_write_callback;

callback.ux_device_class_cdc_acm_parameter_read_callback
    = tx_demo_thread_slave_read_callback;

/* Program the start of transmission. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP

Ejecutar la detención de la transmisión de IOCTL en la interfaz CDC-ACM

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación desea dejar de usar la transmisión con devolución de llamada.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP
- **parameter**: no se usa.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.
- **UX_ERROR** (0xFF) no hay ninguna transmisión en curso.

### <a name="example"></a>Ejemplo

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a>ux_device_class_cdc_acm_read

Leer la canalización CDC-ACM

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita leer la canalización de datos OUT (OUT desde el host, IN desde el dispositivo). Está bloqueando.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **bufer**: dirección del búfer donde se almacenarán los datos.
- **requested_length**: la longitud máxima que se espera.
- **actual_length**: la longitud devuelta en el búfer.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) El dispositivo ya no está en el estado configurado.
- **UX_TRANSFER_NO_ANSWER** (0x22) No hay respuesta del dispositivo. Es probable que el dispositivo se desconectase mientras estaba pendiente la transferencia.

### <a name="example"></a>Ejemplo

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a>ux_device_class_cdc_acm_write

Escribir en una canalización CDC-ACM

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita escribir en la canalización de datos IN (IN desde el host, OUT desde el dispositivo). Está bloqueando.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **bufer**: dirección del búfer donde se almacenan los datos.
- **requested_length**: la longitud del búfer que se va a escribir.
- **actual_length**: la longitud devuelta en el búfer después de realizar la escritura.

### <a name="return-value"></a>Valor devuelto
- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) El dispositivo ya no está en el estado configurado.
- **UX_TRANSFER_NO_ANSWER** (0x22) No hay respuesta del dispositivo. Es probable que el dispositivo se desconectase mientras estaba pendiente la transferencia.

### <a name="example"></a>Ejemplo

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a>ux_device_class_cdc_acm_write_with_callback

Escribir en una canalización CDC-ACM con devolución de llamada

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita escribir en la canalización de datos IN (IN desde el host, OUT desde el dispositivo). Esta función no es de bloqueo y la finalización se realizará a través de una devolución de llamada establecida en UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase CDC.
- **bufer**: dirección del búfer donde se almacenan los datos.
- **requested_length**: la longitud del búfer que se va a escribir.
- **actual_length**: la longitud devuelta en el búfer después de realizar la escritura.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) El dispositivo ya no está en el estado configurado.
- **UX_TRANSFER_NO_ANSWER** (0x22) No hay respuesta del dispositivo. Es probable que el dispositivo se desconectase mientras estaba pendiente la transferencia.

### <a name="example"></a>Ejemplo

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a>Clase CDC-ECM de dispositivo USB

La clase CDC-ECM del dispositivo USB permite que un sistema host USB se comunique con el dispositivo como un dispositivo Ethernet. Esta clase se basa en el estándar USB y es un subconjunto del estándar CDC.

Un marco de dispositivos compatible con CDC-ACM debe declararse en la pila de dispositivos. A continuación, se muestra un ejemplo.

```c
unsigned char device_framework_full_speed[] = {

    /* Device descriptor 18 bytes
    0x02 bDeviceClass: CDC_ECM class code
    0x06 bDeviceSubclass: CDC_ECM class sub code
    0x00 bDeviceProtocol: CDC_ECM Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    0x3939 idVendor: Azure RTOS test.
    */
    
    0x12, 0x01, 0x10, 0x01,
    0x02, 0x00, 0x00, 0x08,
    0x39, 0x39, 0x08, 0x08, 0x00, 0x01, 0x01, 0x02, 03,0x01,
    
    /* Configuration 1 descriptor 9 bytes. */
    0x09, 0x02, 0x58, 0x00,0x02, 0x01, 0x00,0x40, 0x00,
    
    /* Interface association descriptor. 8 bytes. */
    
    0x08, 0x0b, 0x00, 0x02, 0x02, 0x06, 0x00, 0x00,
    
    /* Communication Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x06, 0x00, 0x00,
    
    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00, 0x10, 0x01,
    
    /* ECM Functional Descriptor 13 bytes */
    0x0D, 0x24, 0x0F, 0x04,0x00, 0x00, 0x00, 0x00, 0xEA, 0x05, 0x00,
    0x00,0x00,
    
    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,0x01,
    
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x08,
    
    /* Data Class Interface Descriptor Alternate Setting 0, 0 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x00, 0x0A, 0x00, 0x00, 0x00,
    
    /* Data Class Interface Descriptor Alternate Setting 1, 2 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x01, 0x02, 0x0A, 0x00, 0x00,0x00,
    
    /* First alternate setting Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x02, 0x02, 0x40, 0x00, 0x00,
    
    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81, 0x02, 0x40, 0x00,0x00

};
```

La clase CDC-ECM usa un enfoque de descriptor de dispositivos muy similar para CDC-ACM, y también requiere un descriptor IAD. Vea la clase CDC-ACM para la definición.

Además del marco normal del dispositivos, CDC-ECM requiere descriptores de cadena especiales. A continuación encontrará un ejemplo.

```c
unsigned char string_framework[] = {
    /* Manufacturer string descriptor: Index 1 - "Azure RTOS" */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,
    
    /* Product string descriptor: Index 2 - "EL CDCECM Device" */
    0x09, 0x04, 0x02, 0x10,
    0x45, 0x4c, 0x20, 0x43, 0x44, 0x43, 0x45, 0x43,
    0x4d, 0x20, 0x44, 0x65, 0x76, 0x69, 0x63, 0x64,
    
    /* Serial Number string descriptor: Index 3 - "0001" */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31,
    
    /* MAC Address string descriptor: Index 4 - "001E5841B879" */
    0x09, 0x04, 0x04, 0x0C,
    0x30, 0x30, 0x31, 0x45, 0x35, 0x38,
    0x34, 0x31, 0x42, 0x38, 0x37, 0x39

};
```

La clase CDC-ECM usa el descriptor de cadena de dirección MAC para responder a las consultas de host de en qué dirección MAC responde el dispositivo en el protocolo TCP/IP. Se puede establecer en la elección del dispositivo, pero debe definirse aquí.

La inicialización de la clase CDC-ECM es como se indica a continuación.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_activate = UX_NULL;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_deactivate = UX_NULL;

/* Define a NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[5] = 0x79;

/* Initialize the device cdc_ecm class. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_ecm_name,
    ux_device_class_cdc_ecm_entry, 1,0,&cdc_ecm_parameter);
```

La inicialización de esta clase espera la misma devolución de llamada de función para la activación y la desactivación, aunque aquí se establece en NULL para que no se realice ninguna devolución de llamada.

Los parámetros siguientes son para la definición de los id. de nodo. Son necesarios dos nodos para CDC-ECM, un nodo local y un nodo remoto. El nodo local especifica la dirección MAC del dispositivo, mientras que el nodo remoto especifica la dirección MAC del host. El nodo remoto debe ser el mismo que el declarado en el descriptor de cadena del marco de dispositivo.

La clase CDC-ECM tiene API integradas para transferir datos de ambas maneras, pero están ocultas en la aplicación, ya que la aplicación de usuario se comunicará con el dispositivo USB Ethernet a través de NetX.

La clase USBX CDC-ECM está estrechamente relacionada con la pila de red NetX de Azure RTOS. Una aplicación que use las clases NetX y USBX CDC-ECM activará la pila de red de NetX de la manera habitual, pero además necesitará activar la pila de red USB tal como se indica a continuación.

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

La pila de red USB debe activarse una sola vez y no es específica de CDCECM, pero es necesaria para cualquier clase USB que requiera los servicios de NetX.

Los hosts de MAC OS y Linux reconocerán la clase CDC-ECM. Pero no hay ningún controlador proporcionado por Microsoft Windows para reconocer CDC-ECM de forma nativa. Algunos productos comerciales existen para las plataformas de Windows y suministran su propio archivo .inf. Este archivo deberá modificarse de la misma forma que la plantilla inf de CDC-ACM para que coincida con el PID/VID del dispositivo de red USB.

## <a name="usb-device-hid-class"></a>Clase HID del dispositivo USB

La clase HID del dispositivo USB permite que un sistema host USB se conecte a un dispositivo HID con capacidades específicas del cliente HID.

La clase de dispositivo USBX HID es relativamente sencilla en comparación con el lado host. Está estrechamente vinculada al comportamiento del dispositivo y su descriptor HID.

Cualquier cliente HID requiere en primer lugar definir un marco de dispositivo HID como en el ejemplo siguiente.

```c
UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0x81, 0x0A, 0x01, 0x01, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x22, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x01, 0x03, 0x00, 0x00, 0x00,

    /* HID descriptor */
    0x09, 0x21, 0x10, 0x01, 0x21, 0x01, 0x22, 0x3f, 0x00,

    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x81, 0x03, 0x08, 0x00, 0x08

};
```

El marco HID contiene un descriptor de interfaz que describe la clase HID y la subclase de dispositivo HID. La interfaz HID puede ser una clase independiente o parte de un dispositivo compuesto.

Actualmente, la clase USBX HID no admite varios id. de informe, ya que la mayoría de las aplicaciones solo requieren un id. (id. cero). Si le interesa la característica de varios id. de informe, póngase en contacto con nosotros.

La inicialización de la clase HID es como sigue, empleando un teclado USB como ejemplo.

```c
/* Initialize the hid class parameters for a keyboard. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_keyboard_report;
hid_parameter.ux_device_class_hid_parameter_report_length = HID_KEYBOARD_REPORT_LENGTH;
hid_parameter.ux_device_class_hid_parameter_callback = tx_demo_thread_hid_callback;
hid_parameter.ux_device_class_hid_parameter_report_id = 0;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry, 1,0,(VOID *)&hid_parameter);
if (status!=UX_SUCCESS)
    return;
```

La aplicación debe pasar a la clase HID un descriptor de informe HID y su longitud. El descriptor de informe es una colección de elementos que describen el dispositivo. Para más información sobre la gramática de HID, consulte la especificación de la clase HID USB.

Además del descriptor de informe, la aplicación pasa una devolución de llamada cuando se produce un evento de HID.

La clase USBX HID admite los siguientes comandos HID estándar desde el host.

| Nombre de comando                             | Value | Descripción                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT   | 0x01  | Obtención de un informe del dispositivo                     |
| UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE     | 0x02  | Obtención de la frecuencia de inactividad del punto de conexión de interrupción |
| UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL | 0x03  | Obtención del protocolo que se ejecuta en el dispositivo           |
| UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT   | 0x09  | Establecimiento de un informe en el dispositivo                       |
| UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE     | 0x0a  | Establecimiento de la frecuencia de inactividad del punto de conexión de interrupción |
| UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL | 0x0b  | Obtención del protocolo que se ejecuta en el dispositivo           |

Los comandos de obtención y establecimiento de informes son los que HID usa más para transferir datos entre el host y el dispositivo. Normalmente, el host envía datos en el punto de conexión de control, pero puede recibir datos en el punto de conexión de interrupción o mediante la emisión de un comando GET_REPORT para capturar los datos del punto de conexión de control.

La clase HID puede devolver datos al host en el punto de conexión de interrupción mediante el uso de la función ux_device_class_hid_event_set.

### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

Establecimiento de un evento en la clase HID

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita enviar un evento de HID de nuevo al host. La función no es de bloqueo, simplemente coloca el informe en una cola circular y vuelve a la aplicación.

### <a name="parameters"></a>Parámetros

- **hid** puntero a la instancia de la clase HID.
- **hid_event**: puntero a la estructura del evento de HID.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.
- **UX_ERROR** (0xFF) Error de no hay espacio disponible en la cola circular.

### <a name="example"></a>Ejemplo

```c
/* Insert a key into the keyboard event. Length is fixed to 8. */
hid_event.ux_device_class_hid_event_length = 8;

/* First byte is a modifier byte. */
hid_event.ux_device_class_hid_event_buffer[0] = 0;

/* Second byte is reserved. */
hid_event.ux_device_class_hid_event_buffer[1] = 0;

/* The 6 next bytes are keys. We only have one key here. */
hid_event.ux_device_class_hid_event_buffer[2] = key;

/* Set the keyboard event. */
ux_device_class_hid_event_set(hid, &hid_event);
```

La devolución de llamada definida en la inicialización de la clase HID realiza lo opuesto al envío de un evento. Obtiene como entrada el evento enviado por el host. El prototipo de la devolución de llamada es como sigue.

### <a name="hid_callback"></a>hid_callback

Obtener un evento de la clase HID

### <a name="prototype"></a>Prototipo

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando el host envía un informe HID a la aplicación.

### <a name="parameters"></a>Parámetros

- **hid** puntero a la instancia de la clase HID.
- **hid_event**: puntero a la estructura del evento de HID.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo interpretar un evento para un teclado HID:

```c
UINT tx_demo_thread_hid_callback(UX_SLAVE_CLASS_HID *hid, UX_SLAVE_CLASS_HID_EVENT *hid_event
{
/* There was an event. Analyze it. Is it NUM LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_NUM_LOCK_MASK)
    /* Set the Num lock flag. */
    num_lock_flag = UX_TRUE;
else
    /* Reset the Num lock flag. */
    num_lock_flag = UX_FALSE;

/* There was an event. Analyze it. Is it CAPS LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_CAPS_LOCK_MASK)
    /* Set the Caps lock flag. */
    caps_lock_flag = UX_TRUE;
else
    /* Reset the Caps lock flag. */
    caps_lock_flag = UX_FALSE;
}
```
