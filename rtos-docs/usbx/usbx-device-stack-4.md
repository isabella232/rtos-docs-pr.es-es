---
title: 'Capítulo 4: Descripción de los servicios del dispositivo USBX'
description: Obtenga información sobre los servicios del dispositivo USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9d88d9bd177a251a00fec6757fc1f1494b56bab9655a55f973481f273f0683ee
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797558"
---
# <a name="description-of-usbx-device-services"></a>Descripción de los servicios del dispositivo USBX

### <a name="ux_device_stack_alternate_setting_get"></a>ux_device_stack_alternate_setting_get

Obtención del valor alternativo actual de un valor de interfaz.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a>Descripción

El host USB usa esta función para obtener la configuración alternativa actual de un valor de interfaz específico. El driver del controlador lo llama cuando se recibe una solicitud de **GET_INTERFACE**.

### <a name="input-parameter"></a>Parámetro de entrada

- **Interface_value**: valor de interfaz para el que se consulta la configuración alternativa actual

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.
- **UX_ERROR** (0xFF): valor de interfaz incorrecto.

### <a name="example"></a>Ejemplo

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a>ux_device_stack_alternate_setting_set

Obtención del valor alternativo actual de un valor de interfaz.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Descripción

El host USB usa esta función para establecer la configuración alternativa actual de un valor de interfaz específico. El driver del controlador lo llama cuando se recibe una solicitud de **SET_INTERFACE**. Una vez finalizada **SET_INTERFACE**, los valores de la configuración alternativa se aplican a la clase.

La pila de dispositivos emitirá **UX_SLAVE_CLASS_COMMAND_CHANGE** a la clase a la que pertenece esta interfaz para reflejar el cambio de la configuración alternativa.

### <a name="parameters"></a>Parámetros

- **interface_value**: valor de interfaz para el que se establece la configuración alternativa actual.
- **alternate_setting_value**: nuevo valor de configuración alternativo.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52): no hay ninguna interfaz asociada.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54): el dispositivo no está configurado.
- **UX_ERROR** (0xFF): valor de interfaz incorrecto.

### <a name="example"></a>Ejemplo

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

Registro de una nueva clase de dispositivo USB.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a>Descripción

La aplicación usa esta función para registrar una nueva clase de dispositivo USB. Este registro inicia un contenedor de clases y no una instancia de la clase. La clase debe tener un subproceso activo y asociarse a una interfaz específica.

Algunas clases esperan un parámetro o una lista de parámetros. Por ejemplo, la clase de almacenamiento de dispositivo esperaría la geometría del dispositivo de almacenamiento que está intentando emular. Por lo tanto, el campo de parámetro depende del requisito de la clase y puede ser un valor o un puntero que señala a una estructura rellena con los valores de clase.

> [!NOTE]
> La cadena C de class_name debe terminar en NULL y la longitud (sin tener en cuenta el terminador NULL) no debe ser mayor que **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parámetros

- **class_name**: nombre de clase
- **class_entry_function**: función de entrada de la clase.
- **configuration_number**: número de configuración al que está asociada esta clase.
- **interface_number**: número de la interfaz a la que está asociada esta clase.
- **parameter**: puntero que señala a una lista de parámetros específica de la clase.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00): se ha registrado la clase.
- **UX_MEMORY_INSUFFICIENT** (0x12): no quedan entradas en la tabla de clases.
- **UX_THREAD_ERROR** (0x16): no se puede crear un subproceso de clase.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a>ux_device_stack_class_unregister

Anulación del registro de una clase de dispositivo USB.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a>Descripción

La aplicación usa esta función para anular el registro de una clase de dispositivo USB.

> [!NOTE]
> La cadena C de class_name debe terminar en NULL y la longitud (sin tener en cuenta el terminador NULL) no debe ser mayor que **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parámetros

- **class_name**: nombre de clase.
- **class_entry_function**: función de entrada de la clase.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): se ha anulado el registro de la clase.
- **UX_NO_CLASS_MATCH** (0x57): la clase no está registrada.

### <a name="example"></a>Ejemplo

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a>ux_device_stack_configuration_get

Obtención de la configuración actual.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a>Descripción

El host usa esta función para obtener la configuración actual que se ejecuta en el dispositivo.

### <a name="input-parameter"></a>Parámetro de entrada

Ninguno

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

Establecimiento de la configuración actual.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a>Descripción

El host usa esta función para establecer la configuración actual que se ejecuta en el dispositivo. Tras recibir este comando, la pila de dispositivos USB activará la configuración alternativa 0 de cada interfaz conectada a esta configuración.

### <a name="input-parameter"></a>Parámetro de entrada

- **configuration_value**: el valor de configuración seleccionado por el host.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00): la configuración se ha establecido correctamente.

### <a name="example"></a>Ejemplo

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

Envío de un descriptor al host.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a>Descripción

El lado del dispositivo usa esta función para devolver un descriptor al host. Este descriptor puede ser un descriptor de dispositivo, un descriptor de configuración o un descriptor de cadena.

### <a name="parameters"></a>Parámetros

- **descriptor_type**: tipo de descriptor. Debe ser uno de los siguientes valores:
  - **UX_DEVICE_DESCRIPTOR_ITEM**
  - **UX_CONFIGURATION_DESCRIPTOR_ITEM**
  - **UX_STRING_DESCRIPTOR_ITEM**
  - **UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**
  - **UX_OTHER_SPEED_DESCRIPTOR_ITEM**
- **request_index**: índice del descriptor.
- **host_length**: longitud requerida por el host.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.
- **UX_ERROR** (0xFF): no se ha completado la transferencia.

### <a name="example"></a>Ejemplo

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

Desconexión de la pila de dispositivos.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a>Descripción

El administrador de VBUS llama a esta función cuando se produce una desconexión del dispositivo. La pila de dispositivos informará a todas las clases registradas en este dispositivo y, a partir de ese momento, liberará todos los recursos del dispositivo.

### <a name="input-parameter"></a>Parámetro de entrada

Ninguno

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00): se ha desconectado el dispositivo.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

Solicitud de la condición Stall del punto de conexión.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a>Descripción

La clase de dispositivo USB llama a esta función cuando un punto de conexión debe devolver una condición Stall al host.

### <a name="input-parameter"></a>Parámetro de entrada

- **endpoint**: punto de conexión donde se solicita la condición Stall.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00): la operación se realizó correctamente.
- **UX_ERROR** (0xFF): el dispositivo está en un estado no válido.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

Reactivación del host.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando el dispositivo quiere reactivar el host. Este comando solo es válido cuando el dispositivo está en modo de suspensión. Depende de la aplicación del dispositivo decidir si quiere reactivar el host USB. Por ejemplo, un módem USB puede reactivar un host cuando detecta una señal de timbre en la línea telefónica.

### <a name="input-parameter"></a>Parámetro de entrada

Ninguno

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): la llamada se ha realizado correctamente.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54): error en la llamada (es probable que el dispositivo no estuviera en el modo de suspensión).

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

Inicialización de la pila de dispositivos USB.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a>Descripción

La aplicación llama a esta función para inicializar la pila del dispositivo USB. No inicializa ninguna clase ni controlador. Esto se debe hacer con llamadas de función independientes. Esta llamada proporciona principalmente la pila con el marco de dispositivo para la función USB. Admite velocidades altas y completas con la posibilidad de tener un marco de dispositivo totalmente independiente para cada velocidad. Se admiten el marco de cadena y varios lenguajes.

### <a name="parameters"></a>Parámetros

- **device_framework_high_speed**: puntero que señala al marco de alta velocidad.
- **device_framework_length_high_speed**: longitud del marco de alta velocidad.
- **device_framework_full_speed**: puntero que señala al marco de velocidad máxima.
- **device_framework_length_full_speed**: longitud del marco de velocidad máxima.
- **string_framework**: puntero que señala al marco de cadena.
- **string_framework_length**: longitud del marco de cadena.
- **language_id_framework**: puntero que señala al marco de lenguaje de cadena.
- **language_id_framework_length**: longitud del marco de lenguaje de cadena.
- **ux_system_slave_change_function**: función a la que se llamará cuando cambie el estado del dispositivo.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): la operación se ha realizado correctamente.
- **UX_MEMORY_INSUFFICIENT** (0x12): no hay suficiente memoria para inicializar la pila.
- **UX_DESCRIPTOR_CORRUPTED** (0x42): el descriptor no es válido.

### <a name="example"></a>Ejemplo

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

La aplicación puede solicitar una devolución de llamada cuando el controlador cambia su estado. Los dos estados principales del controlador son:

- **UX_DEVICE_SUSPENDED**
- **UX_DEVICE_RESUMED**

Si la aplicación no necesita señales de suspensión/reanudación, proporciona una función UX_NULL.

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

Eliminación de una interfaz de pila.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando se debe quitar una interfaz. Una interfaz se quita cuando se extrae un dispositivo o después de un restablecimiento de bus, o cuando hay un nuevo valor alternativo.

### <a name="input-parameter"></a>Parámetro de entrada

- **interface**: puntero que señala a la interfaz que se va a quitar.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

Obtención del valor de la interfaz actual.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando el host consulta la interfaz actual. El dispositivo devuelve el valor de la interfaz actual.

> [!NOTE]
> Esta función es desusada. Está disponible para software heredado, pero el nuevo software debe usar la función ***ux_device_stack_alternate_setting_get*** en su lugar.

### <a name="input-parameter"></a>Parámetro de entrada

- **interface_value** Valor de interfaz que se va a devolver.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): la operación se ha realizado correctamente.
- **UX_ERROR** (0xFF): no existe ninguna interfaz.

### <a name="example"></a>Ejemplo

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

Cambio de la configuración alternativa de la interfaz.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando el host solicita un cambio de la configuración alternativa de la interfaz.

### <a name="parameters"></a>Parámetros

- **device_framework**: dirección del marco de dispositivo para esta interfaz.
- **device_framework_length**: longitud de la plataforma del dispositivo.
- **alternate_setting_value**: valor de configuración alternativo que va a usar esta interfaz.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): la operación se ha realizado correctamente.
- **UX_ERROR** (0xFF): no existe ninguna interfaz.

### <a name="example"></a>Ejemplo

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a>ux_device_stack_interface_start

Inicio de la búsqueda de una clase para que sea propietaria de una instancia de interfaz.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando el host selecciona una interfaz y la pila de dispositivos necesita buscar una clase de dispositivo para que sea propietaria de esta instancia de la interfaz.

### <a name="input-parameter"></a>Parámetro de entrada

- **interface**: puntero que señala a la interfaz que se ha creado.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): la operación se ha realizado correctamente.
- **UX_NO_CLASS_MATCH** (0x57): no existe ninguna clase para esta interfaz.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

Solicitud de la transferencia de datos al host.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una clase o la pila quiere transferir datos al host. El host siempre sondea el dispositivo, pero el dispositivo puede preparar los datos de antemano.

### <a name="parameters"></a>Parámetros

- **transfer_request**: puntero que señala a la solicitud de transferencia.
- **slave_length**: longitud que el dispositivo quiere devolver.
- **host_length**: longitud solicitada por el host.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): la operación se ha realizado correctamente.
- **UX_TRANSFER_NOT_READY** (0x25): el dispositivo está en un estado no válido; debe estar en los estados **ATTACHED** (adjunto), **CONFIGURED** (configurado) o **ADDRESSED** (solucionado).
- **UX_ERROR** (0xFF): error de transporte.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

Cancelación de una solicitud de transferencia

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita cancelar una solicitud de transferencia o cuando la pila necesita anular una solicitud de transferencia asociada a un punto de conexión.

### <a name="parameters"></a>Parámetros

- **transfer_request**: puntero que señala a la solicitud de transferencia.
- **completion_code**: código de error que se devolverá a la clase en espera de que se complete la solicitud de transferencia.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Esta operación se realizó correctamente.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a>ux_device_stack_uninitialize

Detención de la inicialización de la pila.

### <a name="prototype"></a>Prototipo

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a>Descripción

Se llama a esta función cuando una aplicación necesita detener la inicialización de la pila de dispositivos USBX y se liberan todos los recursos de la pila del dispositivo. Se debe llamar a este método una vez que se ha anulado el registro de todas las clases mediante ux_device_stack_class_unregister.

### <a name="parameters"></a>Parámetros

Ninguno

### <a name="return-value"></a>Valor devuelto

**UX_SUCCESS** (0x00): la operación se ha realizado correctamente.
