---
title: 'Capítulo 2: Consideraciones acerca de la clase del dispositivo USBX'
description: La clase RNDIS del dispositivo USB permite que un sistema host de USB se comunique con el dispositivo como un dispositivo Ethernet. Esta clase se basa en la implementación de propiedad de Microsoft y es específica de las plataformas de Windows.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 035492644a911eba3b1c62a79572bc7d4c55f6dd
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082224"
---
# <a name="chapter-2---usbx-device-class-considerations"></a>Capítulo 2: Consideraciones acerca de la clase del dispositivo USBX

## <a name="usb-device-rndis-class"></a>Clase RNDIS del dispositivo USB

La clase RNDIS del dispositivo USB permite que un sistema host de USB se comunique con el dispositivo como un dispositivo Ethernet. Esta clase se basa en la implementación de propiedad de Microsoft y es específica de las plataformas de Windows.

Un marco de dispositivos compatible con RNDIS debe declararse en la pila de dispositivos. A continuación se muestra un ejemplo.

```C
unsigned char device_framework_full_speed[] = {
    /* VID: 0x04b4
    PID: 0x1127
    */

    /* Device Descriptor */
    0x12, /* bLength */
    0x01, /* bDescriptorType */
    0x10, 0x01, /* bcdUSB */
    0x02, /* bDeviceClass - CDC */
    0x00, /* bDeviceSubClass */
    0x00, /* bDeviceProtocol */
    0x40, /* bMaxPacketSize0 */
    0xb4, 0x04, /* idVendor */
    0x27, 0x11, /* idProduct */
    0x00, 0x01, /* bcdDevice */
    0x01, /* iManufacturer */
    0x02, /* iProduct */
    0x03, /* iSerialNumber */
    0x01, /* bNumConfigurations */

    /* Configuration Descriptor */
    0x09, /* bLength */
    0x02, /* bDescriptorType */
    0x38, 0x00, /* wTotalLength */
    0x02, /* bNumInterfaces */
    0x01, /* bConfigurationValue */
    0x00, /* iConfiguration */
    0x40, /* bmAttributes - Self-powered */
    0x00, /* bMaxPower */

    /* Interface Association Descriptor */
    0x08, /* bLength */
    0x0b, /* bDescriptorType */
    0x00, /* bFirstInterface */
    0x02, /* bInterfaceCount */
    0x02, /* bFunctionClass - CDC - Communication */
    0xff, /* bFunctionSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bFunctionProtocol - No class specific protocol required */
    0x00, /* iFunction */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x00, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x01, /* bNumEndpoints */
    0x02, /* bInterfaceClass - CDC - Communication */
    0xff, /* bInterfaceSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x83, /* bEndpointAddress */
    0x03, /* bmAttributes - Interrupt */
    0x08, 0x00, /* wMaxPacketSize */
    0xff, /* bInterval */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x01, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x02, /* bNumEndpoints */
    0x0a, /* bInterfaceClass - CDC - Data */
    0x00, /* bInterfaceSubClass - Should be 0x00 */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x02, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x81, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */
};
```

La clase RNDIS usa un enfoque de descriptor de dispositivos muy similar para CDC-ACM y CDC-ECM, y también requiere un descriptor IAD. Consulte la clase CDC-ACM para obtener la definición y los requisitos del descriptor de dispositivos.

La activación de la clase RNDIS se realiza tal como se indica a continuación.

```C
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/

parameter.ux_slave_class_rndis_instance_activate = UX_NULL;
parameter.ux_slave_class_rndis_instance_deactivate = UX_NULL;

/* Define a local NODE ID. */

parameter.ux_slave_class_rndis_parameter_local_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_local_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_local_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_local_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_local_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */

parameter.ux_slave_class_rndis_parameter_remote_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_remote_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_remote_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_remote_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_remote_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_remote_node_id[5] = 0x79;

/* Set extra parameters used by the RNDIS query command with certain OIDs. */

parameter.ux_slave_class_rndis_parameter_vendor_id = 0x04b4 ;
parameter.ux_slave_class_rndis_parameter_driver_version = 0x1127;
ux_utility_memory_copy(parameter.ux_slave_class_rndis_parameter_vendor_description,
    "ELOGIC RNDIS", 12);

/* Initialize the device rndis class. This class owns both interfaces. */
status = ux_device_stack_class_register(_ux_system_slave_class_rndis_name,
    ux_device_class_rndis_entry, 1,0, &parameter);
```

Como en el caso de CDC-ECM, la clase RNDIS requiere 2 nodos, uno local y otro remoto, pero no hay ningún requisito para obtener un descriptor de cadena que describa el nodo remoto.

Sin embargo, debido al mecanismo de mensajería de propiedad de Microsoft, se necesitan algunos parámetros adicionales. En primer lugar, debe pasar el id. de proveedor. Lo mismo sucede con la versión del controlador de RNDIS. También se debe proporcionar una cadena de proveedor.

La clase RNDIS tiene API integradas para transferir datos de ambas maneras, pero están ocultas en la aplicación, ya que la aplicación de usuario se comunicará con el dispositivo USB Ethernet a través de NetX.

La clase USBX RNDIS está estrechamente relacionada con la pila de red NetX de Azure RTOS. Una aplicación que use las clases NetX y USBX RNDIS activará la pila de red de NetX de la manera habitual, pero además necesitará activar la pila de red USB tal como se indica a continuación.

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

La pila de red USB debe activarse una sola vez y no es específica de RNDIS, pero es necesaria para cualquier clase USB que requiera los servicios de NetX.

Tenga en cuenta que los hosts de MAC OS y Linux no reconocerán la clase RNDIS, ya que es específica de los sistemas operativos de Microsoft. En las plataformas de Windows, un archivo .inf debe estar presente en el host que coincide con el descriptor del dispositivo. Asimismo, Microsoft proporciona una plantilla para la clase RNDIS que se puede encontrar en el directorio usbx_windows_host_files. Para obtener una versión más reciente de Windows, debe usar el archivo RNDIS_Template.inf. Este archivo debe modificarse para reflejar el valor de PID/VID que usa el dispositivo. El valor PID/VID será específico para el cliente final cuando la empresa y el producto se registren mediante el valor USB-IF. En el archivo .inf, los campos que se van a modificar se encuentran aquí.

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

En el marco del dispositivo RNDIS, el valor PID/VID se almacena en el descriptor del dispositivo (consulte el descriptor de dispositivo que se declaró anteriormente).

Cuando un sistema host de USB detecta el dispositivo USB RNDIS, monta una interfaz de red, y el dispositivo se puede usar con la pila del protocolo de red. Consulte el sistema operativo host como referencia.

## <a name="usb-device-dfu-class"></a>Clase DFU del dispositivo USB

La clase DFU del dispositivo USB permite que un sistema host USB actualice el firmware del dispositivo en función de una aplicación host. La clase DFU es una clase estándar de tipo USB-IF.

La clase USBX DFU es relativamente sencilla. El descriptor de dispositivos de TI no requiere ningún punto de conexión de control. La mayoría de las veces, esta clase se insertará en un dispositivo compuesto USB. El dispositivo puede ser cualquier cosa, como un dispositivo de almacenamiento o un dispositivo COMM, y la interfaz DFU agregada puede informar al host de que el dispositivo puede actualizar su firmware sobre la marcha.

La clase DFU funciona en tres pasos. En primer lugar, el dispositivo se monta de forma normal mediante la clase exportada. Una aplicación en el host (Windows o Linux) ejecutará la clase DFU y enviará una solicitud para restablecer el dispositivo en el modo DFU. El dispositivo desaparecerá del bus durante un breve período de tiempo (el suficiente para que el host y el dispositivo detecten una secuencia de restablecimiento) y, al reiniciarse, el dispositivo estará exclusivamente en modo DFU, en espera de que la aplicación host envíe una actualización de firmware. Una vez completada la actualización del firmware, la aplicación host restablece el dispositivo y, tras la reenumeración, el dispositivo volverá a su funcionamiento normal con el nuevo firmware.

Una plataforma de dispositivos DFU tendrá el siguiente aspecto.

```C
UCHAR device_framework_full_speed[] = {

    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x40,
    0x99, 0x99, 0x00, 0x00, 0x00, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x1b, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor for DFU. */
    0x09, 0x04, 0x00, 0x00, 0x00, 0xFE, 0x01, 0x01, 0x00,

    /* Functional descriptor for DFU. */
    0x09, 0x21, 0x0f, 0xE8, 0x03, 0x40, 0x00, 0x00,
    0x01,

};
```

En este ejemplo, el descriptor DFU no está asociado a ninguna otra clase. Tiene un descriptor de interfaz simple y no hay ningún otro punto de conexión asociado a él. Hay un descriptor funcional que describe los detalles de las capacidades de DFU del dispositivo.

La descripción de las capacidades de DFU es la siguiente.

| Nombre             | Offset  | Size | type      | Descripción |
|------------------|----------|------|-----------|------------|
| bmAttributes  | 2     | 1   | Campo de bit | Bit 3: el dispositivo realizará una secuencia de asociación y desasociación del bus al recibir una solicitud de DFU_DETACH. El host no debe emitir un restablecimiento de USB. (bitWillDetach) 0 = no 1 = sí; bit 2: el dispositivo puede comunicarse a través de USB después de realizar la fase de manifiesto. (bitManifestationTolerant) 0 = no, debe ver el reinicio del bus 1 = sí bit 1: carga compatible (bitCanUpload) 0 = no 1 = sí; bit 0: descarga compatible (bitCanDnload) 0 = no 1 = sí  |
| wDetachTimeOut  | 3      | 2  | number    | Es el tiempo, en milisegundos, que el dispositivo esperará después de la recepción de la solicitud de DFU_DETACH. Si este tiempo transcurre sin un restablecimiento de USB, el dispositivo finalizará la fase de reconfiguración y volverá al funcionamiento normal. Representa el tiempo máximo que el dispositivo puede esperar (dependiendo de sus temporizadores, etc.). USBX establece este valor en 1000 ms.  |
| wTransferSize  | 5      | 2  | number    | Número máximo de bytes que el dispositivo puede aceptar por operación de escritura de control \-. USBX establece este valor en 64 bytes. |

La declaración de la clase DFU es la siguiente:

```C
/* Store the DFU parameters. */

dfu_parameter.ux_slave_class_dfu_parameter_instance_activate =
    tx_demo_thread_dfu_activate;

dfu_parameter.ux_slave_class_dfu_parameter_instance_deactivate =
    tx_demo_thread_dfu_deactivate;

dfu_parameter.ux_slave_class_dfu_parameter_read =
    tx_demo_thread_dfu_read;

dfu_parameter.ux_slave_class_dfu_parameter_write =
    tx_demo_thread_dfu_write;

dfu_parameter.ux_slave_class_dfu_parameter_get_status =
    tx_demo_thread_dfu_get_status;

dfu_parameter.ux_slave_class_dfu_parameter_notify =
    tx_demo_thread_dfu_notify;

dfu_parameter.ux_slave_class_dfu_parameter_framework =
    device_framework_dfu;

dfu_parameter.ux_slave_class_dfu_parameter_framework_length =
    DEVICE_FRAMEWORK_LENGTH_DFU;

/* Initialize the device dfu class. The class is connected with interface
1 on configuration 1. */
status = ux_device_stack_class_register(_ux_system_slave_class_dfu_name,
    ux_device_class_dfu_entry, 1, 0,
    (VOID *)&dfu_parameter);

if (status!=UX_SUCCESS) return;
```

La clase DFU debe trabajar con una aplicación de firmware de dispositivo específica del destino. Por lo tanto, define varias devoluciones de llamada para leer y escribir en bloques de firmware y para obtener el estado de la aplicación de actualización de firmware. La clase DFU también tiene una función de devolución de llamadas de notificaciones para informar a la aplicación cuando se produce un inicio y un final de la transferencia del firmware.

A continuación se proporciona la descripción de un flujo de la aplicación del DFU típico.

![Flujo de la aplicación DFU](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

El principal desafío de la clase DFU es obtener la aplicación correcta en el host para realizar la descarga del firmware. No hay ninguna aplicación que haya proporcionado Microsoft o USB-IF. Existen algunas opciones de shareware y funcionan razonablemente bien en Linux, pero en un menor grado en Windows.

En Linux, puede usar las utilidades DFU para encontrarlas aquí: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util); también se puede encontrar mucha información sobre las utilidades DFU en este vínculo: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend).

La implementación de Linux de DFU realiza correctamente la secuencia de restablecimiento entre el host y el dispositivo, por lo que no es necesario que el dispositivo lo haga. Linux puede aceptar que el elemento bmAttributes *bitWillDetach* sea 0. Por otro lado, Windows requiere que el dispositivo realice el restablecimiento.

En Windows, el registro USB debe ser capaz de asociar el dispositivo USB al PID/VID y a la biblioteca USB que, a su vez, usará la aplicación DFU. Esto puede hacerse fácilmente con la utilidad gratuita Zadig, que se puede encontrar aquí: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).

Al ejecutar Zadig por primera vez, se mostrará esta pantalla:

![Ejecución de Zadig por primera vez](./media/usbx-device-stack-supplemental/zadig.png)

En la lista de dispositivos, busque el dispositivo y asócielo al controlador libusb de Windows. Esto enlazará el PID/VID del dispositivo con la biblioteca USB de Windows que usan las utilidades DFU.

Para usar el comando DFU, simplemente desempaquete las utilidades DFU comprimidas en un directorio, y asegúrese de que el archivo dll de libusb también está presente en el mismo directorio. Las utilidades DFU se deben ejecutar desde un cuadro de DOS en la línea de comandos.

En primer lugar, escriba el comando **dfu-util –l** para determinar si el dispositivo aparece en la lista. Si no es así, ejecute Zadig para asegurarse de que el dispositivo aparece y está asociado a la biblioteca USB. Debería ver una pantalla como la que se muestra a continuación:

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

El siguiente paso será preparar el archivo que se va a descargar. La clase USBX DFU no realiza ninguna comprobación en este archivo y es independiente de su formato interno. Este archivo de firmware es específico del destino, pero no de DFU ni de USBX.

A continuación, se puede indicar a la utilidad DFU que envíe el archivo; para ello escriba el siguiente comando:

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

Asimismo, la utilidad DFU debe mostrar el proceso de descarga del archivo hasta que el firmware se haya descargado por completo.

## <a name="usb-device-pima-class-ptp-responder"></a>Clase PIMA del dispositivo USB (respondedor PTP)

La clase PIMA del dispositivo USB permite que un sistema host USB (iniciador) se conecte a un:

Dispositivo PIMA (respondedor) para transferir archivos multimedia. La clase USBX PIMA se ajusta a la clase USB-IF PIMA 15740, también conocida como clase PTP (para el protocolo de transferencia de imágenes).

La clase PIMA del lado del dispositivo USBX admite las siguientes operaciones.

| Código de operación                                    | Value | Descripción                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO    | 0x1001  | Permite obtener las operaciones y los eventos que admite el dispositivo.                                                         |
| UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION        | 0x1002  | Permite abrir una sesión entre el host y el dispositivo.                                                            |
| UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION       | 0x1003  | Permite cerrar una sesión entre el host y el dispositivo.                                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS    | 0x1004  | Permite devolver el id. de almacenamiento del dispositivo. USBX PIMA solo usa un id. de almacenamiento. |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO   | 0x1005  | Permite devolver información sobre el objeto de almacenamiento, como la capacidad máxima y el espacio disponible.                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS    | 0x1006  | Permite devolver el número de objetos contenidos en el dispositivo de almacenamiento.                                              |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES | 0x1007  | Permite devolver una matriz de manipuladores de los objetos en el dispositivo de almacenamiento.                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO    | 0x1008  | Permite devolver información acerca de un objeto, como el nombre de este, la fecha de creación y la fecha de modificación. |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT          | 0x1009  | Permite devolver los datos que pertenecen a un objeto específico.                                                         |
| UX_DEVICE_CLASS_PIMA_OC_GET_THUMB           | 0x100a  | Permite enviar la miniatura si está disponible sobre un objeto.                                                           |
| UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT       | 0x100B  | Permite eliminar un objeto en el contenido multimedia.                                                                             |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO   | 0x100C  | Permite enviar al dispositivo la información sobre un objeto para su creación en el contenido multimedia.                              |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT         | 0x100D  | Permite enviar los datos de un objeto al dispositivo.                                                                     |
| UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE        | 0x100F  | Permite limpiar los elementos multimedia del dispositivo.                                                                                    |
| UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE        | 0x0110  | Permite restablecer el dispositivo de destino.                                                                                   |

| Código de la operación                                         | Value | Descripción |
|--------------------------------------------------------|-------|-----------------------------------------|
| UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION       | 0x4001  | Permite cancelar la transacción actual.                                                 |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED             | 0x4002  | Se ha agregado un objeto a los elementos multimedia del dispositivo y el host puede recuperarlo. |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED           | 0x4003  | Se ha eliminado un objeto de los elementos multimedia del dispositivo.                                |
| UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED              | 0x4004  | Se ha agregado un elemento multimedia al dispositivo.                                            |
| UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED            | 0x4005  | Se ha eliminado un elemento multimedia del dispositivo.                                        |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED     | 0x4006  | Las propiedades del elemento han cambiado.                                                  |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED     | 0x4007  | Ha cambiado la información de un objeto.                                               |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE      | 0x4008  | Un dispositivo ha cambiado.                                                            |
| UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER | 0x4009  | El dispositivo solicita la transferencia de un objeto desde el host.                     |
| UX_DEVICE_CLASS_PIMA_EC_STORE_FULL               | 0x400A  | El dispositivo indica que está al completo de elementos multimedia.                                                |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET             | 0x400B  | El dispositivo indica que se ha restablecido.                                                     |
| UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED    | 0x400C  | La información de almacenamiento ha cambiado en el dispositivo.                                   |
| UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE         | 0x400D  | La captura se ha completado.                                                            |

La clase de dispositivo USBX PIMA usa un subproceso TX para escuchar los comandos PIMA del host.

Un comando PIMA se compone de un bloque de comandos, un bloque de datos y una fase de estado.

La función ux_device_class_pima_thread envía una solicitud a la pila para recibir un comando PIMA del lado del host. El comando PIMA se descodifica y se comprueba su contenido. Si el bloque de comandos es válido, este se bifurca en el controlador de comandos adecuado.

La mayoría de comandos PIMA solo se pueden ejecutar cuando el host ha abierto una sesión. La única excepción es el comando **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**. Con la implementación USBX PIMA, solo se puede abrir una sesión entre un iniciador y un respondedor en cualquier momento. Todas las transacciones de la sesión única están bloqueadas y no se puede iniciar una nueva transacción antes de que se complete la anterior.

Las transacciones PIMA se componen de tres fases: una fase de comandos, una fase de datos opcional y una fase de respuesta. Si hay una fase de datos, solo puede estar en una dirección.

El iniciador siempre determina el flujo de las operaciones PIMA, pero el respondedor puede iniciar los eventos de vuelta al iniciador para informar de los cambios de estado que se produjeron durante una sesión.

En el diagrama siguiente se muestra la transferencia de un objeto de datos entre el host y la clase de dispositivo PIMA.

![Transacciones PIMA](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a>Inicialización de la clase de dispositivo PIMA

La clase de dispositivo PIMA necesita algunos parámetros que proporciona la aplicación durante la inicialización.

Los parámetros siguientes describen la información del dispositivo y del almacenamiento.

- `ux_device_class_pima_manufacturer`
- `ux_device_class_pima_model`
- `ux_device_class_pima_device_version`
- `ux_device_class_pima_serial_number`
- `ux_device_class_pima_storage_id`
- `ux_device_class_pima_storage_type`
- `ux_device_class_pima_storage_file_system_type`
- `ux_device_class_pima_storage_access_capability`
- `ux_device_class_pima_storage_max_capacity_low`
- `ux_device_class_pima_storage_max_capacity_high`
- `ux_device_class_pima_storage_free_space_low`
- `ux_device_class_pima_storage_free_space_high`
- `ux_device_class_pima_storage_free_space_image`
- `ux_device_class_pima_storage_description`
- `ux_device_class_pima_storage_volume_label`

La clase PIMA también requiere que realice el registro de la devolución de llamada en la aplicación para informar a la aplicación de determinados eventos o para recuperar o almacenar datos en el medio local. Las devoluciones de llamada son tal como se muestra a continuación.

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

En el ejemplo siguiente se muestra cómo inicializar el lado cliente de PIMA. En este ejemplo se usa PictBridge como cliente para PIMA.

```C
/* Initialize the first XML object valid in the pictbridge instance.

Initialize the handle, type and file name.

The storage handle and the object handle have a fixed value of 1 in our implementation. */

object_info = pictbridge -> ux_pictbridge_object_client;

object_info -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_SCRIPT;
object_info -> ux_device_class_pima_object_storage_id = 1;
object_info -> ux_device_class_pima_object_handle_id = 2;

ux_utility_string_to_unicode(_ux_pictbridge_ddiscovery_name,
    object_info -> ux_device_class_pima_object_filename);

/* Initialize the head and tail of the notification round robin buffers.
   At first, the head and tail are pointing to the beginning of the array.
*/

pictbridge -> ux_pictbridge_event_array_head =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_tail =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_end =
    pictbridge -> ux_pictbridge_event_array +
    UX_PICTBRIDGE_MAX_EVENT_NUMBER;

/* Initialialize the pima device parameter. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_manufacturer =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_model =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_serial_number =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_id = 1;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_type =
    UX_DEVICE_CLASS_PIMA_STC_FIXED_RAM;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_file_system_type =
    UX_DEVICE_CLASS_PIMA_FSTC_GENERIC_FLAT;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_access_capability =
    UX_DEVICE_CLASS_PIMA_AC_READ_WRITE;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_image = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_description =
    _ux_pictbridge_volume_description;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_volume_label =
    _ux_pictbridge_volume_label;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_number_get =
    ux_pictbridge_dpsclient_object_number_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_handles_get =
    ux_pictbridge_dpsclient_object_handles_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_get =
    ux_pictbridge_dpsclient_object_info_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_get =
    ux_pictbridge_dpsclient_object_data_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_send =
    ux_pictbridge_dpsclient_object_info_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_send =
    ux_pictbridge_dpsclient_object_data_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_delete =
    ux_pictbridge_dpsclient_object_delete;

/* Store the instance owner. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_application =
    (VOID *) pictbridge;

/* Initialize the device pima class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_pima_name,
    ux_device_class_pima_entry, 1, 0, (VOID *)&pictbridge -> ux_pictbridge_pima_parameter);

/* Check status. */
if (status != UX_SUCCESS)
```

## <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

Permite agregar un objeto y enviar el evento al host

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando la clase PIMA necesita agregar un objeto e informar al host.

### <a name="parameters"></a>Parámetros

- **pima**: puntero a la instancia de la clase pima.
- **object_handle**: identificador del objeto.

### <a name="example"></a>Ejemplo

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a>ux_device_class_pima_object_number_get

Permite obtener el número de objeto de la aplicación.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando la clase PIMA necesita recuperar el número de objetos en el sistema local y enviarlo de nuevo al host.

### <a name="parameters"></a>Parámetros

- **pima**: puntero a la instancia de la clase pima.
- **object_number**: dirección del número de objetos que se van a devolver.

### <a name="example"></a>Ejemplo

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a>ux_device_class_pima_object_handles_get

Permite devolver la matriz de identificadores de objetos.

### <a name="prototype"></a>Prototipo

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando la clase PIMA necesita recuperar el número de objetos en el sistema local y enviarlo de nuevo al host.

### <a name="parameters"></a>Parámetros

- **pima**: puntero a la instancia de la clase pima.
- **object_handles_format_code**: código de formato para los identificadores.
- **object_handles_association**: código de asociación de objetos.
- **object_handle_array**: dirección en la que se almacenan los identificadores.
- **object_handles_max_number**: número máximo de identificadores de la matriz.

### <a name="example"></a>Ejemplo

```C
UINT ux_pictbridge_dpsclient_object_handles_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *) pima -> ux_device_class_pima_application;

    /* Set the pima pointer to the pictbridge instance. */
    pictbridge -> ux_pictbridge_pima = (VOID *) pima;

    /* We say we have one object but the caller might specify different format code and associations. */
    object_info = pictbridge -> ux_pictbridge_object_client;

    /* Insert in the array the number of found handles so far: 0. */
    ux_utility_long_put((UCHAR *)object_handles_array, 0);

    /* Check the type demanded. */

    if (object_handles_format_code == 0 || object_handles_format_code ==
        0xFFFFFFFF || object_info -> ux_device_class_pima_object_format ==
        object_handles_format_code)
    {
        /* Insert in the array the number of found handles. This handle is for the client XML script. */
        ux_utility_long_put((UCHAR *)object_handles_array, 1);

        /* Adjust the array to point after the number of elements. */
        object_handles_array++;

        /* We have a candicate. Store the handle. */
        ux_utility_long_put((UCHAR *)object_handles_array, object_info ->
            ux_device_class_pima_object_handle_id);
    }

    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_info_get"></a>ux_device_class_pima_object_info_get

Permite devolver la información del objeto.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando la clase PIMA necesita recuperar el número de objetos en el sistema local y enviarlo de nuevo al host.

### <a name="parameters"></a>Parámetros

- **pima**: puntero a la instancia de la clase pima.
- **object_handle**: identificador del objeto.
- **object**: dirección del puntero del objeto.

### <a name="example"></a>Ejemplo

```C
UINT ux_pictbridge_dpsclient_object_info_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UX_SLAVE_CLASS_PIMA_OBJECT **object)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST)) {

        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge -> ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;
    } else
        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;
    /* Return the pointer to this object. */
    *object = object_info;

    /* We are done. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

Permite devolver los datos del objeto.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando la clase PIMA necesita recuperar los datos de los objetos en el sistema local y enviarlo de nuevo al host.

### <a name="parameters"></a>Parámetros

- **pima**: puntero a la instancia de la clase pima.
- **object_handle**: identificador del objeto.
- **object_buffer**: dirección del búfer del objeto.
- **object_length_requested**: longitud de datos de objetos que ha solicitado el cliente a la aplicación.
- **object_actual_length**: longitud de datos de objeto de devuelve la aplicación.

### <a name="example"></a>Ejemplo

```C
UINT ux_pictbridge_dpsclient_object_data_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UCHAR *object_buffer, ULONG object_offset,
    ULONG object_length_requested, ULONG *object_actual_length)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    UCHAR *pima_object_buffer;
    ULONG actual_length;
    UINT status;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST))
    {
        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;

       /* Is this the corrent handle ? */
       if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
       {
           /* Get the pointer to the object buffer. */
           pima_object_buffer = object_info -> ux_device_class_pima_object_buffer;

           /* Copy the demanded object data portion. */
           ux_utility_memory_copy(object_buffer, pima_object_buffer +
               object_offset, object_length_requested);

           /* Update the length requested. for a demo, we do not do any checking. */
           *object_actual_length = object_length_requested;

           /* What cycle are we in ? */
           if (pictbridge -> ux_pictbridge_host_client_state_machine &
               UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST)
            {
                /* Check if we are blocking for a client request. */
                if (pictbridge -> ux_pictbridge_host_client_state_machine &
                    UX_PICTBRIDGE_STATE_MACHINE_CLIENT_REQUEST_PENDING)

                    /* Yes we are pending, send an event to release the pending request. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_STATE_MACHINE_READY, TX_OR);

               /* Since we are in host request, this indicates we are done with the cycle. */
               pictbridge -> ux_pictbridge_host_client_state_machine =
                   UX_PICTBRIDGE_STATE_MACHINE_IDLE;

            }

            /* We have copied the requested data. Return OK. */
            return(UX_SUCCESS);

        }
    }
    else
    {

        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;

        /* Obtain the data from the application jobinfo callback. */
        status = pictbridge -> ux_pictbridge_jobinfo.
            ux_pictbridge_jobinfo_object_data_read(pictbridge, object_buffer, object_offset,
            object_length_requested, &actual_length);

        /* Save the length returned. */
        *object_actual_length = actual_length;

        /* Return the application status. */
        return(status);

    }

    /* Could not find the handle. */

    return(UX_DEVICE_CLASS_PIMA_RC_INVALID_OBJECT_HANDLE);
}
```

## <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

El host envía la información del objeto.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando la clase PIMA necesita recibir la información del objeto en el sistema local para el almacenamiento futuro.

### <a name="parameters"></a>Parámetros

- **pima**: puntero a la instancia de la clase pima.
- **object**: puntero al objeto.
- **object_handle**: identificador del objeto.

### <a name="example"></a>Ejemplo

```C
UINT ux_pictbridge_dpsclient_object_info_send(UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, ULONG *object_handle)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info; UCHAR
    string_discovery_name[UX_PICTBRIDGE_MAX_FILE_NAME_SIZE];

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* We only have one object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Copy the demanded object info set. */
    ux_utility_memory_copy(object_info, object,
        UX_SLAVE_CLASS_PIMA_OBJECT_DATA_LENGTH);

    /* Store the object handle. In Pictbridge we only receive XML scripts so the handle is hardwired to 1. */
    object_info -> ux_device_class_pima_object_handle_id = 1;
    *object_handle = 1;

    /* Check state machine. If we are in discovery pending mode, check file name of this object. */
    if (pictbridge -> ux_pictbridge_discovery_state ==
        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_PENDING)
    {
        /* We are in the discovery mode. Check for file name. It must match
           HDISCVRY.DPS in Unicode mode. */

        /* Check if this is a script. */
        if (object_info -> ux_device_class_pima_object_format ==
            UX_DEVICE_CLASS_PIMA_OFC_SCRIPT)
        {

            /* Yes this is a script. We need to search for the HDISCVRY.DPS file name. Get the file name in a ascii format. */
            ux_utility_unicode_to_string(object_info ->
                ux_device_class_pima_object_filename,
                string_discovery_name);

            /* Now, compare it to the HDISCVRY.DPS file name. Check length first. */
            if (ux_utility_string_length_get(_ux_pictbridge_hdiscovery_name)
                == ux_utility_string_length_get(string_discovery_name))
            {

                /* So far, the length of name of the files are the same. Compare names now. */
                if(ux_utility_memory_compare(_ux_pictbridge_hdiscovery_name,
                    string_discovery_name,
                    ux_utility_string_length_get(string_discovery_name)) == UX_SUCCESS)
                {
                    /* We are done with discovery of the printer. We can now send notifications when the camera wants to print an object. */
                    pictbridge -> ux_pictbridge_discovery_state =
                        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_COMPLETE;

                    /* Set an event flag if the application is listening. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY, TX_OR);

                    /* There is no object during th discovery cycle. */
                    return(UX_SUCCESS);
                }
            }
        }
    }
    /* What cycle are we in ? */
    if (pictbridge -> ux_pictbridge_host_client_state_machine ==
        UX_PICTBRIDGE_STATE_MACHINE_IDLE)

        /* Since we are in idle state, we must have received a request from the host. */
        pictbridge -> ux_pictbridge_host_client_state_machine =
            UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

El host envía los datos del objeto.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando la clase PIMA necesita recibir la información del objeto en el sistema local para el almacenamiento.

### <a name="parameters"></a>Parámetros

- **pima**: puntero a la instancia de la clase pima.
- **object_handle**: identificador del objeto.
- **phase**: fase de la transferencia (activa o completa).
- **object_buffer**: dirección del búfer del objeto.
- **object_offset**: dirección de los datos.
- **object_length**: longitud de datos del objeto que ha enviado la aplicación.

### <a name="example"></a>Ejemplo

```C
UINT ux_pictbridge_dpsclient_object_data_send(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    ULONG phase,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length)
{
    UINT status;
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    ULONG event_flag;
    UCHAR *pima_object_buffer;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Get the pointer to the pima object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Is this the corrent handle ? */
    if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
    {
        /* Get the pointer to the object buffer. */
        pima_object_buffer = object_info ->
            ux_device_class_pima_object_buffer;

        /* Check the phase. We should wait for the object to be completed and the response sent back before parsing the object. */
        if (phase == UX_DEVICE_CLASS_PIMA_OBJECT_TRANSFER_PHASE_ACTIVE)
        {
            /* Copy the demanded object data portion. */
            ux_utility_memory_copy(pima_object_buffer + object_offset,
                object_buffer, object_length);

            /* Save the length of this object. */
            object_info -> ux_device_class_pima_object_length = object_length;

            /* We are not done yet. */
            return(UX_SUCCESS);
        }
        else
        {
            /* Completion of transfer. We are done. */
            return(UX_SUCCESS);
        }
    }
}
```

## <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

Permite eliminar un objeto local.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando la clase PIMA necesita eliminar un objeto en el almacenamiento local.

### <a name="parameters"></a>Parámetros

- **pima**: puntero a la instancia de la clase pima.
- **object_handle**: identificador del objeto.

### <a name="example"></a>Ejemplo

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a>Clase de audio del dispositivo USB

La clase de audio del dispositivo USB permite que un sistema host de USB se comunique con el dispositivo como un dispositivo de audio. Esta clase se basa en el estándar USB y la clase de audio USB 1.0 o 2.0 estándar.

Un marco de dispositivos compatible con el audio USB debe declararse en la pila de dispositivos. A continuación, se muestra un ejemplo de un altavoz de audio 2.0:

```C
unsigned char device_framework_high_speed[] = {

    /* --- Device Descriptor 18 bytes
    0x00 bDeviceClass: Refer to interface
    0x00 bDeviceSubclass: Refer to interface
    0x00 bDeviceProtocol: Refer to interface

    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    /* 0 bLength, bDescriptorType */ 18, 0x01,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00, 0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 0x08,
    /* 8 idVendor, idProduct */ 0x84, 0x84, 0x03, 0x00,
    /* 12 bcdDevice */ 0x00, 0x02,
    /* 14 iManufacturer, iProduct, iSerialNumber */ 0, 0, 0,
    /* 17 bNumConfigurations */ 1,
    /* ---------------- Device Qualifier Descriptor */
    /* 0 bLength, bDescriptorType */ 10, 0x06,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00,0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 8,
    /* 8 bNumConfigurations */ 1,
    /* 9 bReserved */ 0,
    /* --- Configuration Descriptor (9+8+73+55=145, 0x91) */
    /* 0 bLength, bDescriptorType */ 9, 0x02,
    /* 2 wTotalLength */ 145, 0,
    /* 4 bNumInterfaces, bConfigurationValue */ 2, 1,
    /* 6 iConfiguration */ 0,
    /* 7 bmAttributes, bMaxPower */ 0x80, 50,
    /* ----------- Interface Association Descriptor */
    /* 0 bLength, bDescriptorType */ 8, 0x0B,
    /* 2 bFirstInterface, bInterfaceCount */ 0, 2,
    /* 4 bFunctionClass : 0x01 (Audio) */ 0x01,
    /* 5 bFunctionSubClass : 0x00 (UNDEFINED) */ 0x00,
    /* 6 bFunctionProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 7 iFunction */ 0,
    /* --- Interface Descriptor #0: Control (9+64=73) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 0, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioControl) */ 0x01,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* --- Audio 2.0 AC Interface Header Descriptor (9+8+17+18+12=64, 0x40) */
    /* 0 bLength */ 9,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bcdADC */ 0x00, 0x02,
    /* 5 bCategory : 0x08 (IO Box) */ 0x08,
    /* 6 wTotalLength */ 64, 0,
    /* 8 bmControls */ 0x00,
    /* -------- Audio 2.0 AC Clock Source Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x0A,
    /* 3 bClockID */ 0x10,
    /* 4 bmAttributes : 0x05 (Sync|InternalFixedClk) */ 0x05,
    /* 5 bmControls : 0x01 (FreqReadOnly) */ 0x01,
    /* 6 bAssocTerminal, iClockSource */ 0x00, 0,
    /* ------ Audio 2.0 AC Input Terminal Descriptor */
    /* 0 bLength */ 17,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02, /* 3 bTerminalID */ 0x04,
    /* 4 wTerminalType : 0x0101 (USB Streaming) */ 0x01, 0x01,
    /* 6 bAssocTerminal, bCSourceID */ 0x00, 0x10,
    /* 8 bNrChannels */ 2,
    /* 9 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 13 iChannelNames, bmControls, iTerminal */ 0, 0x00, 0x00, 0,
    /* -------- Audio 2.0 AC Feature Unit Descriptor */
    /* 0 bLength */ 18,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x06,
    /* 3 bUnitID, bSourceID */ 0x05, 0x04,
    /* 5 bmaControls(0) : 0x0F (VolumeRW|MuteRW) */ 0x0F, 0x00, 0x00, 0x00,
    /* 9 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* 13 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* . iFeature */ 0,
    /* ----- Audio 2.0 AC Output Terminal Descriptor */
    /* 0 bLength */ 12,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x03, /* 3 bTerminalID */ 0x06,
    /* 4 wTerminalType : 0x0301 (Speaker) */ 0x01, 0x03,
    /* 6 bAssocTerminal, bSourceID, bCSourceID */ 0x00, 0x05, 0x10,
    /* 9 bmControls, iTerminal */ 0x00, 0x00, 0,
    /* --- Interface Descriptor #1: Stream OUT (9+9+16+6+7+8=55) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------------------- Interface Descriptor */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 1,
    /* 4 bNumEndpoints */ 1,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------- Audio 2.0 AS Interface Descriptor */
    /* 0 bLength */ 16,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bTerminalLink, bmControls */ 0x04, 0x00,
    /* 5 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 6 bmFormats : 0x000000001 (PCM) */ 0x01, 0x00, 0x00, 0x00, /* 10 bNrChannels */ 2,
    /* 11 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 15 iChannelNames */ 0, /* --------- Audio 2.0 AS Format Type Descriptor */
    /* 0 bLength */ 6,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02,
    /* 3 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 4 bSubslotSize, bBitResolution */ 2, 16,
    /* ------------------------- Endpoint Descriptor */
    /* 0 bLength, bDescriptorType */ 7, 0x05,
    /* 2 bEndpointAddress */ 0x02,
    /* 3 bmAttributes : 0x0D (Sync|ISO) */ 0x0D,
    /* 4 wMaxPacketSize : 0x0100 (256) */ 0x00, 0x01,
    /* 6 bInterval : 0x04 (1ms) */ 4,
    /* - Audio 2.0 AS ISO Audio Data Endpoint Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x25, 0x01,
    /* 3 bmAttributes, bmControls */ 0x00, 0x00,
    /* 5 bLockDelayUnits, wLockDelay */ 0x00, 0x00, 0x00,
};
```

La clase de audio utiliza un marco de dispositivo compuesto para agrupar interfaces (control y streaming). Como resultado, debe tener cuidado al definir el descriptor de dispositivo. USBX se basa en el descriptor IAD para saber internamente cómo enlazar interfaces. El descriptor IAD debe declararse antes que las interfaces (una interfaz de AudioControl seguida de una o varias interfaces de AudioStreaming) y contener la primera interfaz de la clase de audio (la interfaz de AudioControl) y el número de interfaces que están asociadas.

La forma en que funciona la clase de audio depende de si el dispositivo está enviando o recibiendo audio, pero ambos casos usan un FIFO para almacenar búferes de tramas de audio: si el dispositivo está enviando audio al host, la aplicación agrega búferes de tramas de audio al FIFO que USBX envía posteriormente al host; si por el contrario el dispositivo está recibiendo audio desde el host, USBX agrega los búferes de tramas de audio recibidos del host al FIFO, que posteriormente lee la aplicación. Cada flujo de audio tiene su propio FIFO y cada búfer de trama de audio consta de varios ejemplos.

La inicialización de la clase de audio espera las siguientes partes.

1. La clase de audio espera los siguientes parámetros de streaming:

   ```C
   /* Set the parameters for Audio streams. */
   /* Set the application-defined callback that is invoked when the
      host requests a change to the alternate setting. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_change = demo_audio_read_change;

   /* Set the application-defined callback that is invoked whenever
      a USB packet (audio frame) is sent to or received from the host. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_frame_done = demo_audio_read_done;

   /* Set the number of audio frame buffers in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_nb = UX_DEMO_FRAME_BUFFER_NB;

   /* Set the maximum size of each audio frame buffer in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_size = UX_DEMO_MAX_FRAME_SIZE;

   /* Set the internally-defined audio processing thread entry pointer. If the application wishes to receive audio from the host
      (which is the case in this example), ux_device_class_audio_read_thread_entry should be used;
      if the application wishes to send data to the host, ux_device_class_audio_write_thread_entry should be used. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry = ux_device_class_audio_read_thread_entry;
   ```

2. La clase de audio espera los siguientes parámetros de función.

   ```C
   /* Set the parameters for Audio device. */

   /* Set the number of streams. */
   audio_parameter.ux_device_class_audio_parameter_streams_nb = 1;

   /* Set the pointer to the first audio stream parameter.
      Note that we initialized this parameter in the previous section.
      Also note that for more than one streams, this should be an array. */
   audio_parameter.ux_device_class_audio_parameter_streams = audio_stream_parameter;

   /* Set the application-defined callback that is invoked when the audio class
      is activated i.e. device is connected to host. */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_activate = demo_audio_instance_activate;

   /* Set the application-defined callback that is invoked when the audio class
      is deactivated i.e. device is disconnected from host. */

   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_deactivate = demo_audio_instance_deactivate;

   /* Set the application-defined callback that is invoked when the stack receives a control request from the host.
      See below for more details.
   */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_device_class_audio_control_process = demo_audio20_request_process;

   /* Initialize the device Audio class. This class owns interfaces starting with 0. */
   status = ux_device_stack_class_register(_ux_system_slave_class_audio_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   La devolución de llamada de la solicitud de control que define la aplicación (***ux_device_class_audio_control_process***; establecida en el ejemplo anterior) se invoca cuando la pila recibe una solicitud de control del host. Si la solicitud se acepta y se controla (se confirma o se detiene), la devolución de llamada debe devolver un resultado correcto; de lo contrario, debe devolver un error.

   El proceso de solicitud de control específico de la clase se define como una devolución de llamada que define la aplicación porque las solicitudes de control son muy diferentes entre las versiones de audio USB, y una gran parte del proceso de solicitud se relaciona con el marco de trabajo del dispositivo. La aplicación debe controlar las solicitudes correctamente para que el dispositivo funcione.

   Puesto que para un dispositivo de audio, el volumen, el silencio y la frecuencia de muestreo son solicitudes de control comunes, las devoluciones de llamada simples y definidas internamente para diferentes versiones de audio USB se introducen en secciones posteriores para que las usen las aplicaciones. Consulte ***ux_device_class_audio10_control_process** _ y _ *_ux_device_class_audio_control_request_** para obtener más detalles.

En el marco del dispositivo de audio, el valor PID/VID se almacena en el descriptor del dispositivo (consulte el descriptor de dispositivo que se declaró anteriormente).

Cuando un sistema host USB detecta el dispositivo de audio USB y monta la clase de audio, el dispositivo puede usarse con cualquier reproductor o grabadora de audio (según el marco de trabajo). Consulte el sistema operativo host como referencia.

A continuación se definen las API de la clase de audio.

## <a name="ux_device_class_audio_read_thread_entry"></a>ux_device_class_audio_read_thread_entry

Entrada de subproceso para leer los datos de la función de audio.

### <a name="prototype"></a>Prototipo

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Descripción

Esta función se pasa al parámetro de inicialización de la secuencia de audio si quiere leer el audio del host. Internamente, se crea un subproceso con esta función como su función de entrada; el propio subproceso lee los datos de audio a través del punto de conexión isocróno OUT en la función Audio.

### <a name="parameters"></a>Parámetros

- **audio_stream**: puntero a la instancia de la secuencia de audio.

### <a name="example"></a>Ejemplo

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a>ux_device_class_audio_write_thread_entry

Entrada de subproceso para leer los datos de la función Audio.

### <a name="prototype"></a>Prototipo

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Descripción

Esta función se pasa al parámetro de inicialización de la secuencia de audio si quiere escribir en el audio del host. Internamente, se crea un subproceso con esta función como su función de entrada; el propio subproceso escribe los datos de audio a través del punto de conexión isocróno IN en la función Audio.

### <a name="parameters"></a>Parámetros

- **audio_stream**: puntero a la instancia de la secuencia de audio.

### <a name="example"></a>Ejemplo

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a>ux_device_class_audio_stream_get

Permite obtener una instancia de flujo específica para la función Audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a>Descripción

Esta función se usa para obtener una instancia de secuencia de la clase de audio.

### <a name="parameters"></a>Parámetros

- **audio**: puntero a la instancia de audio.
- **stream_index**: índice de instancia de la secuencia basado en 0.
- **stream**: puntero al búfer para almacenar el puntero de la instancia de la secuencia de audio.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) esta operación se realizó correctamente.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a>ux_device_class_audio_reception_start

Permite iniciar la recepción de datos de audio para la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Descripción

Esta función se usa para iniciar la lectura de datos de audio en secuencias de audio.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO está lleno.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a>ux_device_class_audio_sample_read8

Permite leer la muestra de 8 bits de la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a>Descripción

Esta función lee los datos de la muestra de audio de 8 bits de la secuencia especificada.

En concreto, lee los datos de muestra del búfer de la trama de audio actual en el FIFO. Tras leer la última muestra en una trama de audio, esta se liberará automáticamente para que se pueda usar para aceptar más datos del host.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.
- **buffer**: puntero al búfer para guardar la muestra de bytes.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a>ux_device_class_audio_sample_read16

Permite leer la muestra de 16 bits de la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a>Descripción

Esta función lee los datos de la muestra de audio de 16 bits de la secuencia especificada.

En concreto, lee los datos de muestra del búfer de la trama de audio actual en el FIFO. Tras leer la última muestra en una trama de audio, esta se liberará automáticamente para que se pueda usar para aceptar más datos del host.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.
- **buffer**: puntero al búfer para guardar la muestra de 16 bits.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a>ux_device_class_audio_sample_read24

Permite leer la muestra de 24 bits de la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Descripción

Esta función lee los datos de la muestra de audio de 24 bits de la secuencia especificada.

En concreto, lee los datos de muestra del búfer de la trama de audio actual en el FIFO. Tras leer la última muestra en una trama de audio, esta se liberará automáticamente para que se pueda usar para aceptar más datos del host.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.
- **buffer**: puntero al búfer para guardar la muestra de 3 bytes.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a>ux_device_class_audio_sample_read32

Permite leer la muestra de 32 bits de la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Descripción

Esta función lee los datos de la muestra de audio de 32 bits de la secuencia especificada.

En concreto, lee los datos de muestra del búfer de la trama de audio actual en el FIFO. Tras leer la última muestra en una trama de audio, esta se liberará automáticamente para que se pueda usar para aceptar más datos del host.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.
- **buffer**: puntero al búfer para guardar la muestra de 4 bytes.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a>ux_device_class_audio_read_frame_get

Permite obtener acceso a la trama de audio en la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Descripción

Esta función devuelve el primer búfer de la trama de audio y su longitud en el FIFO de la secuencia especificada. Cuando la aplicación termina de procesar los datos, se debe usar ux_device_class_audio_read_frame_free para liberar el búfer de la trama en el FIFO.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.
- **frame_data**: puntero para el puntero de datos en el que se va a devolver el puntero de datos.
- **frame_length**: puntero al búfer para guardar la longitud de la trama en número de bytes.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a>ux_device_class_audio_read_frame_free

Permite liberar un búfer de la trama de audio en la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Descripción

Esta función libera el búfer de la trama de audio situado al principio del FIFO de la secuencia especificada para que pueda recibir datos del host.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a>ux_device_class_audio_transmission_start

Permite iniciar la transmisión de datos de audio para la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Descripción

Esta función se usa para empezar a enviar datos de audio escritos en el FIFO en la clase de audio.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a>ux_device_class_audio_frame_write

Permite escribir una trama de audio en la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a>Descripción

Esta función escribe una trama en el FIFO de la secuencia de audio. Los datos de la trama se copian en el búfer disponible en el FIFO para que se pueda enviar al host.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.
- **frame**: puntero a los datos de la trama.
- **frame_length**: longitud de la trama en número de bytes.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO está lleno.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a>ux_device_class_audio_write_frame_get

Permite obtener acceso a la trama de audio en la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Descripción

Esta función recupera la dirección del último búfer de trama de audio del FIFO; también recupera la longitud del búfer de la trama de audio. Una vez que la aplicación rellena el búfer de la trama de audio con los datos deseados, ***ux_device_class_audio_write_frame_commit*** debe usarse para agregar o confirmar el búfer de la trama en el FIFO.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.
- **frame_data**: puntero para el puntero de datos de la trama en el que se va a devolver el puntero de datos de la trama.
- **frame_length**: puntero al búfer para guardar la longitud de la trama en número de bytes.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO está lleno.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a>ux_device_class_audio_write_frame_get

Permite liberar un búfer de la trama de audio en la secuencia de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a>Descripción

Esta función agrega o confirma el último búfer de la trama de audio en el FIFO, por lo que el búfer está listo para transferirse al host; tenga en cuenta que el último búfer de la trama de audio debe haberse rellenado a través de ux_device_class_write_frame_get.

### <a name="parameters"></a>Parámetros

- **stream**: puntero a la instancia de la secuencia de audio.
- **length**: número de bytes listos en el búfer.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.
- **UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO está lleno.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a>ux_device_class_audio10_control_process

Permite procesar solicitudes de control de audio USB 1.0

### <a name="prototype"></a>Prototipo

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a>Descripción

Esta función administra las solicitudes básicas que envían el host en el punto de conexión de control con un tipo específico 1.0 de audio USB.

Las características de audio 1.0 de las solicitudes de volumen y silenciar se procesan en la función. Al procesar las solicitudes, los datos predefinidos que pasa el último parámetro (grupo) se usan para responder a las solicitudes y almacenar los cambios del control.

### <a name="parameters"></a>Parámetros

- **audio**: puntero a la instancia de audio.
- **transfer**: puntero a la instancia de la solicitud de transferencia.
- **group**: grupo de datos para el proceso de solicitud.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Initialize audio 1.0 control values. */

audio_control[0].ux_device_class_audio10_control_fu_id = 2;
audio_control[0].ux_device_class_audio10_control_mute[0] = 0;
audio_control[0].ux_device_class_audio10_control_volume[0] = 0;
audio_control[1].ux_device_class_audio10_control_fu_id = 5;
audio_control[1].ux_device_class_audio10_control_mute[0] = 0;
audio_control[1].ux_device_class_audio10_control_volume[0] = 0;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio10_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio10_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```

## <a name="ux_device_class_audio20_control_process"></a>ux_device_class_audio20_control_process

Permite procesar solicitudes de control de audio USB 1.0

### <a name="prototype"></a>Prototipo
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a>Descripción

Esta función administra las solicitudes básicas que envían el host en el punto de conexión de control con un tipo específico de audio USB 2.0.

La velocidad de muestreo de audio 2.0 (se supone una frecuencia de un solo fijo), las características de las solicitudes de volumen y silenciar se procesan en la función. Al procesar las solicitudes, los datos predefinidos que pasa el último parámetro (grupo) se usan para responder a las solicitudes y almacenar los cambios del control.

### <a name="parameters"></a>Parámetros

- **audio**: puntero a la instancia de audio.
- **transfer**: puntero a la instancia de la solicitud de transferencia.
- **group**: grupo de datos para el proceso de solicitud.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) Esta operación se realizó correctamente.
- **UX_ERROR** (0xFF) Error de la función.

### <a name="example"></a>Ejemplo

```C
/* Initialize audio 2.0 control values. */

audio_control[0].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[0].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[0].ux_device_class_audio20_control_fu_id = 2;
audio_control[0].ux_device_class_audio20_control_mute[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[0].ux_device_class_audio20_control_volume[0] = 50;
audio_control[1].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[1].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[1].ux_device_class_audio20_control_fu_id = 5;
audio_control[1].ux_device_class_audio20_control_mute[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[1].ux_device_class_audio20_control_volume[0] = 50;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio20_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio20_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```
