---
title: 'Capítulo 4: Descripción de los servicios de host de USBX'
description: Obtenga información sobre los servicios de host de USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6cbeff83d8e3812f13aa3f8f66d4013b70490d556911939186b4b43840aac50d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790690"
---
# <a name="chapter-4---description-of-usbx-host-services"></a>Capítulo 4: Descripción de los servicios de host de USBX

## <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

Inicializa USBX para la operación del host.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a>Descripción

Esta función inicializará la pila de host USB. El área de memoria suministrada se configurará para su uso interno en USBX. Si se devuelve UX_SUCCESS, USBX está listo para la controladora de host y el registro de clases.

### <a name="input-parameter"></a>Parámetro de entrada

- **system_change_function** Puntero a la rutina de devolución de llamada opcional para notificar a la aplicación de los cambios en el dispositivo.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00) Inicialización correcta.
- **UX_MEMORY_INSUFFICIENT** (0x12) Error en una asignación de memoria.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

Anula todas las transacciones vinculadas a una solicitud de transferencia para un punto de conexión.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Descripción

Esta función cancela todas las transacciones activas o pendientes para una solicitud de transferencia específica vinculada a un punto de conexión. La solicitud de transferencia tiene una función de devolución de llamada vinculada, a la que se llamará con el estado UX_TRANSACTION_ABORTED.

### <a name="input-parameter"></a>Parámetro de entrada

- **endpoint** Puntero a un punto de conexión.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00) No hay errores.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) El identificador del punto de conexión no es válido.

### <a name="example"></a>Ejemplo

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a>ux_host_stack_class_get

Obtiene el puntero a un contenedor de clases.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a>Descripción

Esta función devuelve un puntero al contenedor de clases. Una clase debe obtener su contenedor de la pila USB para buscar instancias cuando una clase o una aplicación desea abrir un dispositivo.

> [!NOTE]
> La cadena C de class_name debe terminar en NULL y la longitud (sin tener en cuenta el terminador NULL) no debe ser mayor que UX_MAX_CLASS_NAME_LENGTH.

### <a name="parameters"></a>Parámetros

- **class_name** Puntero al nombre de la clase.
- **class** Un puntero actualizado por la llamada de función que incluye el contenedor de clases para el nombre de la clase.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00) No hay errores; en la devolución, el campo de clase se registra con el puntero al contenedor de clases.
- **UX_HOST_CLASS_UNKNOWN** (0x59) La pila no conoce la clase.

### <a name="example"></a>Ejemplo

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a>ux_host_stack_class_register

Registra una clase USB en la pila USB.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a>Descripción

Esta función registra una clase USB en la pila USB. La clase debe especificar un punto de entrada para que la pila USB envíe comandos como el siguiente.

- **UX_HOST_CLASS_COMMAND_QUERY**
- **UX_HOST_CLASS_COMMAND_ACTIVATE**
- **UX_HOST_CLASS_COMMAND_DESTROY**

> [!NOTE]
> La cadena C de *class_name* debe terminar en NULL y la longitud (sin tener en cuenta el terminador NULL) no debe ser mayor que **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parámetros

- **class_name** Puntero al nombre de la clase; las entradas válidas se encuentran en el archivo ux_system_initialize.c en las clases USB de USBX.
- **class_entry_address** Dirección de la función de entrada de la clase.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00) La clase se ha instalado correctamente.
- **UX_MEMORY_ARRAY_FULL** (0x1a) No hay más memoria para almacenar esta clase.
- **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) La clase de host ya está instalada.

### <a name="example"></a>Ejemplo:

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a>ux_host_stack_class_instance_create

Crea una instancia de clase para un contenedor de clases.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Descripción

Esta función crea una instancia de clase para un contenedor de clases. La instancia de una clase no se incluye en el código de clase para reducir la complejidad de la clase. En su lugar, cada instancia de clase se vincula al contenedor de clases ubicado en la pila principal.

### <a name="parameters"></a>Parámetros

- **class** Puntero al contenedor de clases.
- **class_instance** Puntero a la instancia de clase que se va a crear.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00) La instancia de clase se ha vinculado al contenedor de clases.

### <a name="example"></a>Ejemplo

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a>ux_host_stack_class_instance_destroy

Destruye una instancia de clase para un contenedor de clases.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Descripción

Esta función destruye una instancia de clase para un contenedor de clases.

### <a name="parameters"></a>Parámetros

- **class** Puntero al contenedor de clases.
- **class_instance** Puntero a la instancia que se va a destruir.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00) Se destruyó la instancia de clase.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) La instancia de clase no está vinculada al contenedor de clases.

### <a name="example"></a>Ejemplo

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a>ux_host_stack_class_instance_get

Obtiene un puntero de instancia de clase para una clase específica.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a>Descripción

Esta función devuelve un puntero de instancia de clase para una clase específica. La instancia de una clase no se incluye en el código de clase para reducir la complejidad de la clase. En su lugar, cada instancia de clase se vincula al contenedor de clases. Esta función se usa para buscar instancias de clase dentro de un contenedor de clases.

### <a name="parameters"></a>Parámetros

- **class** Puntero al contenedor de clases.
- **class_index** Índice que la llamada de función usará en la lista de clases vinculadas al contenedor.
- **class_instance** Puntero a la instancia que la llamada de función devolverá.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00) Se encontró la instancia de clase.

- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) No hay más instancias de clase vinculadas a este contenedor de clases.

### <a name="example"></a>Ejemplo

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

Obtiene un puntero a un contenedor de configuración.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Descripción

Esta función devuelve un contenedor de configuración basado en un identificador de dispositivo y en un índice de configuración.

### <a name="parameters"></a>Parámetros

- **device** Puntero al contenedor de dispositivos que posee la configuración solicitada.
- **configuration_index** Índice de la configuración que se va a buscar.
- **configuration** Dirección del puntero al contenedor de configuración que se va a devolver.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00) Se encontró la configuración.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) El contenedor de dispositivos no existe.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) El identificador de configuración para el índice no existe.

### <a name="example"></a>Ejemplo

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

Selecciona una configuración específica para un dispositivo.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Descripción

Esta función selecciona una configuración específica para un dispositivo. Cuando esta configuración se establece en el dispositivo, de forma predeterminada, cada interfaz del dispositivo y su valor alternativo asociado 0 se activan en el dispositivo. Si la clase device o interface desea cambiar la configuración de una interfaz determinada, debe emitir una llamada de servicio **ux_host_stack_interface_setting_select**.

### <a name="parameters"></a>Parámetros

- **configuration** Puntero al contenedor de configuración que se va a habilitar para este dispositivo.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00) La configuración se ha seleccionado correctamente.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) El identificador de configuración no existe.
- **UX_OVER_CURRENT_CONDITION** (0X43) Existe una condición de exceso de corriente en el bus para esta configuración.

### <a name="example"></a>Ejemplo

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

Obtiene un puntero a un contenedor de dispositivos.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a>Descripción

Esta función devuelve un contenedor de dispositivos basado en su índice. El índice del dispositivo empieza por 0. Tenga en cuenta que el índice es un tipo ULONG porque podríamos tener varios controladores, y un índice de bytes podría no ser suficiente. El índice del dispositivo no se debe confundir con la dirección del dispositivo, ya que esta es específica del bus.

### <a name="parameters"></a>Parámetros

- **device_index** Índice del dispositivo.
- **device** Dirección del puntero para el contenedor de dispositivos que se va a devolver.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00) El contenedor de dispositivos existe y se devuelve.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) Dispositivo desconocido.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a>ux_host_stack_interface_endpoint_get

Obtiene un contenedor de puntos de conexión.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Descripción

Esta función devuelve un contenedor de puntos de conexión basado en el identificador de la interfaz y un índice de punto de conexión. Se supone que se ha seleccionado la configuración alternativa de la interfaz o que se usa la configuración predeterminada antes de los puntos de conexión buscados.

### <a name="parameters"></a>Parámetros

- **interface** Puntero al contenedor de la interfaz que contiene el punto de conexión solicitado.
- **endpoint_index** Índice del punto de conexión de esta interfaz.
- **endpoint** Dirección del contenedor de puntos de conexión que se va a devolver.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00) El contenedor de puntos de conexión existe y se devuelve.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) La interfaz especificada no existe.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) El índice de punto de conexión no existe.

### <a name="example"></a>Ejemplo

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

Registra una controladora USB en la pila USB.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a>Descripción

Esta función registra una controladora USB en la pila USB. Principalmente asigna la memoria usada por este controlador y pasa el comando de inicialización al controlador.

### <a name="parameters"></a>Parámetros

- **hcd_name** Nombre de la controladora de host.
- **hcd_function** Función de la controladora de host responsable de la inicialización.
- **hcd_param1** El recurso de E/S o de memoria utilizado por HCD.
- **hcd_param2** La IRQ utilizada por la controladora de host.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00) La controladora se inicializó correctamente.
- **UX_MEMORY_INSUFFICIENT** (0X12) No hay suficiente memoria para esta controladora.
- **UX_PORT_RESET_FAILED** (0x31) No se pudo restablecer la controladora.
- **UX_CONTROLLER_INIT_FAILED** (0x32) La controladora no se pudo inicializar correctamente.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a>ux_host_stack_configuration_interface_get

Obtiene un puntero de contenedor de interfaz.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a>Descripción

Esta función devuelve un contenedor de interfaz basado en un identificador de configuración, un índice de interfaz y un índice de configuración alternativo.

### <a name="parameters"></a>Parámetros

- **configuration** Puntero al contenedor de configuración que posee la interfaz.
- **interface_index** Índice de interfaz que se va a buscar.
- **alternate_setting_index** Configuración alternativa dentro de la interfaz que se va a buscar.
- **interface** Dirección del puntero de contenedor de la interfaz que se va a devolver.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00) El contenedor de interfaz para el índice de interfaz y la configuración alternativa se encontraron y devolvieron.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) La configuración no existe.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) La interfaz no existe.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

Selecciona una configuración alternativa para una interfaz.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a>Descripción

Esta función selecciona una configuración alternativa específica para una interfaz determinada que pertenece a la configuración seleccionada. Esta función se usa para cambiar de la configuración alternativa predeterminada a una nueva configuración o para volver a la configuración alternativa predeterminada. Cuando se selecciona una nueva configuración alternativa, las características del punto de conexión anterior no son válidas y se deben volver a cargar.

### <a name="input-parameter"></a>Parámetro de entrada

- **interface** Puntero al contenedor de interfaz cuya configuración alternativa se va a seleccionar.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00) La configuración alternativa de esta interfaz se ha seleccionado correctamente.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) La interfaz no existe.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a>ux_host_stack_transfer_request_abort

Anula una solicitud de transferencia pendiente.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Descripción

Esta función anula una solicitud de transferencia pendiente que se ha enviado previamente. Esta función solo cancela una solicitud de transferencia concreta. La devolución de llamada a la función tendrá el estado UX_TRANSFER REQUEST_STATUS_ABORT.

### <a name="parameters"></a>Parámetros

- **transfer request** Puntero a la solicitud de transferencia que se va a anular.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00) Se canceló la transferencia USB para esta solicitud de transferencia.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

Solicita una transferencia USB.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Descripción

Esta función realiza una transacción USB. En la entrada, la solicitud de transferencia proporciona la canalización del punto de conexión seleccionada para esta transacción y los parámetros asociados a la transferencia (carga de datos y longitud de la transacción). En el caso de la canalización de control, la transacción se bloquea y solo se devolverá cuando se hayan completado las tres fases de la transferencia de control o si se ha producido un error anterior. En el caso de otras canalizaciones, la pila USB programará la transacción en la unidad USB, pero no esperará a que se complete. Cada solicitud de transferencia para canalizaciones sin bloqueo tiene que especificar un controlador de rutina de finalización.

Cuando se devuelve la llamada de función, se debe examinar el estado de la solicitud de transferencia, ya que contiene el resultado de la transacción.

### <a name="input-parameter"></a>Parámetro de entrada

- **transfer_request** Puntero a la solicitud de transferencia. La solicitud de transferencia contiene toda la información necesaria para la transferencia.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00) Se canceló la transferencia USB para esta solicitud de transferencia. El código de estado de la solicitud de transferencia debe examinarse cuando se complete la solicitud de transferencia.
- **UX_MEMORY_INSUFFICIENT** (0X12) No hay suficiente memoria para asignar los recursos de controlador necesarios.
- **UX_TRANSFER_NOT_READY** (0x25) El dispositivo estaba en un estado no válido; debe estar en los estados ATTACHED, ADDRESSED o CONFIGURED.

### <a name="example"></a>Ejemplo:

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
