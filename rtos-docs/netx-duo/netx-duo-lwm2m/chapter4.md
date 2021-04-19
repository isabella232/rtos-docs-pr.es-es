---
title: 'Capítulo 4: Descripción de los servicios del cliente LWM2M'
description: Este capítulo contiene una descripción de todos los servicios del cliente LWM2M en orden alfabético.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814673"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a>Capítulo 4: Descripción de los servicios del cliente LWM2M

Este capítulo contiene una descripción de todos los servicios del cliente LWM2M siguientes en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.

**Administración de clientes de LWM2M:**

- nx_lwm2m_client_create: *crear cliente LWM2M*

- nx_lwm2m_client_delete: *eliminar cliente LWM2M*

- nx_lwm2m_client_lock: *bloquear cliente LWM2M*

- nx_lwm2m_client_unlock: *desbloquear cliente LWM2M*

**Administración de sesiones de clientes LWM2M:**

- nx_lwm2m_client_session_create: *crear sesión de cliente LWM2M*

- nx_lwm2m_client_session_delete: *eliminar sesión de cliente LWM2M*

- nx_lwm2m_client_session_bootstrap: *iniciar una sesión con un servidor de arranque*

- nx_lwm2m_client_session_bootstrap_dtls: *iniciar una sesión segura con un servidor de arranque*

- nx_lwm2m_client_session_register_info_get: *obtener información de registro del servidor de LWM2M*

- nx_lwm2m_client_session_register: *iniciar una sesión con un servidor de LWM2M*

- nx_lwm2m_client_session_register_dtls: *iniciar una sesión segura con un servidor LWM2M*

- nx_lwm2m_client_session_update: *actualizar una sesión con un servidor LWM2M*

- nx_lwm2m_client_session_deregister: *finalizar una sesión con un servidor LWM2M*

- nx_lwm2m_client_session_error_get: *obtener el último error de una sesión*

**Implementación de objetos de dispositivo:**

- nx_lwm2m_client_device_callbacks_set: *establecer devoluciones de llamada de aplicaciones de objetos de dispositivo*

- nx_lwm2m_client_device_error_push: *agregar un código de error a un objeto de dispositivo*

- nx_lwm2m_client_device_error_reset: *restablecer códigos de error de un objeto de dispositivo*

- nx_lwm2m_client_device_resource_changed: *cambio de señal de un recurso de objeto de dispositivo*

**Implementación de objetos de actualización de firmware:**

- nx_lwm2m_firmware_create: *crear un objeto de actualización de firmware*

- nx_lwm2m_firmware_package_info_set: *establecer la información de paquetes de actualización de firmware*

- nx_lwm2m_firmware_result_set: *establecer el resultado de la actualización de firmware*

- nx_lwm2m_firmware_state_set: *establecer el estado de la actualización de firmware*

**Implementación de objetos personalizados:**

- nx_lwm2m_client_object_add: *agregar implementación de objeto al cliente LWM2M*

- nx_lwm2m_client_object_remove: *quitar implementación de objeto del cliente LWM2M*

- nx_lwm2m_client_object_instance_add: *agregar instancia de objeto al cliente LWM2M*

- nx_lwm2m_client_object_instance_remove: *quitar instancia de objeto del cliente LWM2M*

- nx_lwm2m_object_resource_changed: *cambio de señal del valor de un recurso de una instancia de objeto*

**Administración de dispositivos locales:**

- nx_lwm2m_client_object_create: *crear una nueva instancia de objeto*

- nx_lwm2m_client_object_delete: *eliminar una instancia de objeto*

- nx_lwm2m_client_object_discover: *detectar recursos de una instancia de objeto*

- nx_lwm2m_client_object_execute: *ejecutar el recurso de una instancia de objeto*

- nx_lwm2m_client_object_next_get: *obtener la lista de objetos implementados por el cliente LWM2M*

- nx_lwm2m_client_object_instance_next_get: *obtener la lista de instancias de un objeto*

- nx_lwm2m_client_object_read: *leer los valores de los recursos de una instancia de objeto*

- nx_lwm2m_client_object_write: *cambiar los valores de los recursos de una instancia de objeto*

**Configuración de valores e información de recursos:**

- nx_lwm2m_client_resource_info_set: *establecer la información de los recursos*

- nx_lwm2m_client_resource_string_set: *establecer el valor del recurso como una cadena*

- nx_lwm2m_client_resource_integer32_set: *establecer el valor del recurso como un entero de 32 bits*

- nx_lwm2m_client_resource_integer64_set: *establecer el valor del recurso como un entero de 64 bits*

- nx_lwm2m_client_resource_float32_set: *establecer el recurso en un valor flotante de 32 bits*

- nx_lwm2m_client_resource_float64_set: *establecer el recurso en un valor flotante de 64 bits*

- nx_lwm2m_client_resource_boolean_set: *establecer el recurso en un valor booleano*

- nx_lwm2m_client_resource_objlnk_set: *establecer el valor del recurso como un vínculo de objeto*

- nx_lwm2m_client_resource_opaque_set: *establecer el valor del recurso como opaco*

- nx_lwm2m_client_resource_instance_set: *establecer el valor del recurso como una instancia para varios recursos*
-
- nx_lwm2m_client_resource_dim_set: *establecer la dimensión del recurso para varios recursos.*

**Obtención de valores e información de recursos:**

- nx_lwm2m_client_resource_info_get: *obtener la información de los recursos*

- nx_lwm2m_client_resource_string_get: *obtener el valor de un recurso string*

- nx_lwm2m_client_resource_integer32_get: *obtener el valor de un recurso integer de 32 bits*

- nx_lwm2m_client_resource_integer64_get: *obtener el valor de un recurso integer de 64 bits*

- nx_lwm2m_client_resource_float32_get: *obtener el valor de un recurso flotante de 32 bits*

- nx_lwm2m_client_resource_float64_get: *obtener el valor de un recurso flotante de 64 bits*

- nx_lwm2m_client_resource_boolean_get: *obtener el valor de un recurso boolean*

- nx_lwm2m_client_resource_objlnk_get: *obtener el valor de un recurso de vínculo de objeto*

- nx_lwm2m_client_resource_opaque_get: *obtener el valor de un recurso opaque*

- nx_lwm2m_client_resource_instance_get: *obtener la instancia de recurso para varios recursos*

- nx_lwm2m_client_resource_dim_get: *obtener la dimensión de recurso para varios recursos.*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Crea un cliente LWM2M.

### <a name="prototype"></a>Prototipo

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de cliente LWM2M que se ejecuta en el contexto de su propio subproceso ThreadX.

El cliente LWM2M implementa los siguientes objetos OMA LWM2M: Security (0), Server (1), Access Control (2) y Device (3). La aplicación debe agregar las implementaciones de otros objetos.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **packet_pool_ptr**: puntero al grupo de paquetes predeterminado para este cliente LWM2M.
- **name_ptr**: puntero al nombre de punto de conexión del cliente LWM2M.
- **name_length**: longitud del nombre del punto de conexión del cliente LWM2M.
- **msisdn_ptr**: puntero a MSISDN, donde se puede acceder al cliente LWM2M para su uso con el enlace SMS; puede ser NULL si no se admite el enlace SMS.
- **msisdn_length**: longitud del número MSISDN.
- **binding_modes**: el enlace y los modos admitidos que admite el cliente LWM2M, deben ser una combinación de las marcas NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S y NX_LWM2M_BINDING_SQ.
- **stack_ptr**: puntero al área de la pila de subprocesos del cliente LWM2M.
- **stack_size**: tamaño de la pila de subprocesos del cliente de LWM2M.
- **priority**: prioridad del cliente LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: el cliente LWM2M se creó correctamente.
- **NX_LWM2M_CLIENT_ERROR**: error al crear el cliente LWM2M.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE**: el puerto no está disponible.
- **NX_PTR_ERROR**: puntero no válido.
- **NX_SIZE_ERROR**: tamaño de pila no válido.
- **NX_OPTION_ERROR**: prioridad no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Elimina un cliente LWM2M.

### <a name="prototype"></a>Prototipo

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente LWM2M creada anteriormente.

Esta llamada también elimina todas las sesiones asociadas actualmente al cliente.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: el cliente LWM2M se eliminó correctamente.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a>nx_lwm2m_client_device_callbacks_set

Establece la devolución de llamada de la aplicación de un objeto de dispositivo.

### <a name="prototype"></a>Prototipo

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a>Descripción

Este servicio instala la devolución de llamada de la aplicación para implementar operaciones en los recursos de objeto de dispositivo de LWM2M que no controla el cliente LWM2M.

El cliente LWM2M implementa los siguientes recursos: Error Code (11), Reset Error Code (12) y Supported Binding and Modes (16); las operaciones con los demás recursos se redirigen a la aplicación.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **operation_callback**: devolución de llamada de operación de lectura, detección, escritura y ejecución.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: la devolución de llamada de la operación se estableció correctamente.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push
Agrega un código de error a un objeto de dispositivo.

### <a name="prototype"></a>Prototipo

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a>Descripción

Este servicio agrega una nueva instancia al recurso Error Code (11) del dispositivo de objeto.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **code**: nuevo código de error.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**

Se alcanzó el número máximo de códigos de error

almacenados.

NX_PTR_ERROR: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Restablece los códigos de error del objeto de dispositivo.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina todas las instancias de recursos de código de error del objeto de dispositivo. Esto es equivalente a la ejecución del recurso Reset Error Code (12).

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Indica un cambio en un recurso de objeto de dispositivo.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a>Descripción

La aplicación usa el servicio para indicar al cliente LWM2M que un recurso del dispositivo de objeto ha cambiado. El cliente LWM2M enviará una notificación si un servidor LWM2M observa el recurso.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **resource**: puntero a la estructura que describe el recurso que ha cambiado.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a>nx_lwm2m_client_firmware_create

Cree un objeto de firmware de cliente LWM2M. 

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a>Descripción

La aplicación usa el servicio para crear el objeto de firmware.

### <a name="parameters"></a>Parámetros

- **firmware_ptr**: puntero al objeto de firmware de cliente LWM2M.
- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **protocols**: protocolos admitidos.
- **package_callback**: devolución de llamada del paquete.
- **package_uri_callback**: devolución de llamada del URI del paquete.
- **update_callback**: devolución de llamada de actualización.

### <a name="return-values"></a>Valores devueltos

**NX_SUCCESS**: operación correcta.
**NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a>nx_lwm2m_client_firmware_package_info_set

Establece la información de paquetes de firmware del cliente LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a>Descripción

La aplicación usa el servicio para establecer los recursos de información de paquetes del objeto de actualización de firmware.

### <a name="parameters"></a>Parámetros

- **firmware_ptr**: puntero al objeto de firmware de cliente LWM2M.
- **name**: nombre del paquete de firmware.
- **name_length**: longitud del nombre.
- **version**: versión del paquete de firmware.
- **version_length**: longitud de la versión.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a>nx_lwm2m_client_firmware_result_set

Establece el recurso de resultado de la actualización del objeto de actualización de firmware.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Descripción

La aplicación usa el servicio para establecer el recurso de resultado de la actualización del objeto de actualización de firmware.

### <a name="parameters"></a>Parámetros

- **firmware_ptr**: puntero al objeto de firmware de cliente LWM2M.
- **result**: resultado de la actualización.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a>nx_lwm2m_client_firmware_state_set

Establece el recurso de resultado de la actualización del objeto de actualización de firmware.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Descripción

La aplicación usa el servicio para establecer el estado del objeto de actualización de firmware.

### <a name="parameters"></a>Parámetros

- **firmware_ptr**: puntero al objeto de firmware de cliente LWM2M.
- **state**: estado del objeto de firmware.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Bloquea el cliente LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio bloquea el cliente LWM2M para impedir el acceso simultáneo a los objetos LWM2M desde los servidores o desde otro subproceso de aplicación.

Si el cliente LWM2M está bloqueado actualmente por otro subproceso, la función se bloqueará hasta que dicho cliente se desbloquee.

Las llamadas a pares ***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** se pueden anidar.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Agrega una implementación de objeto al cliente LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a>Descripción

Este servicio agrega una nueva implementación de objeto al cliente LWM2M.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **object_ptr**: puntero a la estructura que define la implementación del objeto.
- **object_id**: identificador del objeto.
- **object_operation**: función de devolución de llamada de la operación de objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_ALREADY_EXIST**: el id. de objeto ya existe.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Crea una nueva instancia de objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de creación en un objeto del cliente LWM2M para crear una nueva instancia de objeto.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **object_id**: identificador del objeto.
- **instance_id_ptr**: puntero al identificador de la nueva instancia, puede ser **NULL** si el cliente LWM2M debe asignar un id. de instancia. Si el identificador es el valor reservado 65535, el cliente LWM2M asignará un id. de instancia. Si no es NULL, el identificador asignado se devuelve después de la llamada.
- **num_values**: número de valores que se van a establecer.
- **values_ptr**: puntero a una matriz de valores de recursos para inicializar la nueva instancia de objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_ClIENT_ALREADY_EXIST**: el id. de instancia de objeto ya existe.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED**: el objeto no admite la creación de instancias.
- **NX_LWM2M_CLIENT_NO_MEMORY**: no se puede asignar memoria para almacenar la nueva instancia.
- **NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto no existe.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Elimina una instancia de objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de eliminación en una instancia de objeto del cliente LWM2M.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **object_id**: identificador del objeto.
- **instance_id**: identificador de la instancia de objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED**: el objeto no admite la eliminación de instancias.
- **NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto o el id. de instancia de objeto no existen.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Detecta recursos de una instancia de objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a>Descripción

Este servicio realiza una operación de detección en una instancia de objeto del cliente LWM2M, que devuelve la lista de recursos implementados por el objeto.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **object_id**: identificador del objeto.
- **instance_id**: identificador de la instancia de objeto.
- **num_resources**: en la entrada, el tamaño del búfer de destino; en la salida, el número de elementos escritos en el búfer.
- **resources**: puntero al búfer de destino.

### <a name="return-values"></a>Valores devueltos

- *NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**: el búfer de recursos es demasiado pequeño para almacenar la lista de recursos.
- **NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto o el id. de instancia de objeto no existen.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Realiza una operación de ejecución en un recurso de una instancia de objeto.

### <a name="prototype"></a>Prototipo

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de ejecución en un recurso de una instancia de objeto del cliente LWM2M.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **object_id**: identificador del objeto.
- **instance_id**: identificador de la instancia de objeto.
- **resource_id**: identificador del recurso.
- **arguments_ptr**: puntero a los argumentos de la operación de ejecución. Puede ser NULL si arguments_length es cero.
- **arguments_length**: longitud de los argumentos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**: el búfer de recursos es demasiado pequeño para almacenar la lista de recursos.
- **NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto o el id. de instancia de objeto no existen.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a>nx_lwm2m_client_object_instance_add

Agrega una implementación de instancia de objeto a un objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Descripción

Este servicio agrega una nueva implementación de instancia de objeto al cliente LWM2M. Si el valor de instance_id_ptr es **NX_LWM2M_CLIENT_RESERVED_ID**, el cliente LWM2M asignará automáticamente un id. de instancia no utilizado; de lo contrario, el cliente LWM2M usará el valor de la aplicación establecido. Después de agregar la nueva instancia correctamente, el campo instance_id se rellenará en instance_id_ptr para volver a la aplicación.

### <a name="parameters"></a>Parámetros

- **object_ptr**: puntero a la estructura que define la implementación del objeto.
- **instance_ptr**: puntero a la estructura que define la implementación de la instancia de objeto.
- **instance_id_ptr**: puntero al id. de instancia de objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_CLIENT_LWM2M_ALREADY_EXIST**: el id. de objeto ya existe.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a>nx_lwm2m_client_object_instance_next_get

Obtiene la siguiente instancia de un objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Descripción

Este servicio devuelve el identificador de la siguiente instancia de objeto del objeto especificado. Si el id. de instancia actual se establece en NX_LWM2M_RESERVED_ID (65535), se devuelve el identificador de la primera instancia.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **object_id**: identificador del objeto.
- **instance_id_ptr**: puntero al id. de instancia de objeto actual. En la devolución, contiene el id. de instancia siguiente del objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_CLIENT_LWM2M_NOT_FOUND**: el id. de instancia proporcionado es el último del objeto, o bien el id. de objeto no está implementado.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a>nx_lwm2m_client_object_instance_remove

Quita una implementación de instancia de objeto de un objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a>Descripción

Este servicio quita una instancia de objeto de un objeto.

### <a name="parameters"></a>Parámetros

- ***object_ptr***: puntero a la estructura que define la implementación del objeto.
- **instance_ptr**: puntero a la estructura que define la implementación de la instancia de objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_ALREADY_EXIST**: el id. de objeto ya existe.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a>nx_lwm2m_client_object_next_get

Obtiene el siguiente objeto del cliente LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a>Descripción

Este servicio devuelve el identificador del siguiente objeto implementado por el cliente LWM2M. Si el id. de objeto actual se establece en NX_LWM2M_RESERVED_ID (65535), se devuelve el primer id. de objeto.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **object_id_ptr**: puntero al id. de objeto actual. En la devolución, contiene el siguiente id. de objeto implementado por el cliente LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto especificado es el último de la base de datos.
**NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Lee los valores de los recursos de una instancia de objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de lectura en una instancia de objeto del cliente LWM2M.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **object_id**: identificador del objeto.
- **instance_id**: identificador de la instancia de objeto.
- **num_values**: número de recursos que se van a leer.
- **values_ptr**: puntero a una matriz de NX_LWM2M_RESOURCE que contiene los identificadores de los recursos que se van a leer. En la devolución, la matriz se rellena con los tipos y valores correspondientes.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED**: un recurso no admite la operación de lectura.
- **NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto, el id. de instancia de objeto o un id. de recursos no existen.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a>nx_lwm2m_client_object_remove

Quita una implementación de instancia de objeto de un objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a>Descripción

Este servicio quita un objeto del cliente LWM2M.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **object_ptr**: puntero a la estructura que define la implementación del objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_ALREADY_EXIST**: el id. de objeto ya existe.
- **NX_PTR_ERROR**: puntero no válido.
- **NX_LWM2M_CLIENT_FORBIDDEN**: se prohíbe eliminar un objeto interno.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a>nx_lwm2m_client_object_resource_changed

Indica un cambio de un recurso de objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Descripción

La aplicación usa el servicio para indicar al cliente LWM2M que un recurso del objeto ha cambiado. El cliente LWM2M enviará una notificación si un servidor LWM2M observa el recurso.

### <a name="parameters"></a>Parámetros

- **object_ptr**: puntero a la estructura que define la implementación del objeto.
- ***instance_ptr***: puntero a la estructura que define la implementación de la instancia de objeto.
- **resource**: puntero a la estructura que describe el recurso que ha cambiado.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Cambia los valores de los recursos de una instancia de objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de escritura en una instancia de objeto del cliente LWM2M.

Se pueden especificar las siguientes operaciones de escritura en el parámetro *write_op*.

| Value | Operación&nbsp;de escritura | Descripción |
| --- | ---| --- |
| 0 | Actualización parcial | Agrega o actualiza los recursos proporcionados en el nuevo valor y deja sin modificar otros recursos existentes. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Reemplazo de instancia | Reemplaza la instancia de objeto por los nuevos valores de recursos proporcionados. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** | Reemplazo de recurso | Reemplaza los recursos por los nuevos valores de recursos proporcionados (usados para reemplazar varios recursos). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Escritura de arranque | Indica una llamada desde una secuencia de arranque. |

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.
- **object_id**: identificador del objeto.
- **instance_id**: identificador de la instancia de objeto.
- **num_values**: número de recursos que se van a escribir.
- **values_ptr**: puntero a una matriz de NX_LWM2M_RESOURCE que contiene los identificadores de los recursos, los tipos y los valores que se van a escribir.
- **write_op**: tipo de operación de escritura.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: El tipo de un recurso no es válido.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**: la longitud de un valor es demasiado grande para almacenarse en la instancia.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED**: un recurso no admite la operación de escritura.
- **NX_LWM2M_CLIENT_NO_MEMORY**: no se puede asignar memoria para almacenar un valor de recurso.
- **NX_LWM2M_CLIENT_NOT_ACCEPTABLE**: el valor de un recurso no es válido.
- **NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto, el id. de instancia de objeto o un id. de recursos no existen.
- **NX_OPTION_ERROR**: tipo de operación de escritura no válido. 
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a>nx_lwm2m_client_resource_boolean_get

Obtiene el valor de un recurso boolean.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Descripción

El servicio recupera el valor de un recurso boolean.

### <a name="parameters"></a>Parámetros

- **resource**: puntero a la descripción del valor de recurso.
- **bool_ptr**: puntero al valor booleano de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es booleano.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a>nx_lwm2m_client_resource_boolean_set

Establece el valor de un recurso boolean.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a>Descripción

El servicio establece el valor de un recurso boolean.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **bool_data**: datos booleanos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a>nx_lwm2m_client_resource_dim_get

Obtiene la dimensión de recurso para varios recursos.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a>Descripción

El servicio recupera la dimensión de recurso para varios recursos.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **dim**: puntero a la dimensión de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es booleano.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a>nx_lwm2m_client_resource_dim_set

Establece la dimensión de recurso para varios recursos.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a>Descripción

El servicio establece la dimensión de recurso para varios recursos.

### <a name="parameters"></a>Parámetros

- **value**: puntero a la descripción del valor de recurso.
- **dim**: valor de dimensión.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a>nx_lwm2m_client_resource_float32_get

Establece el valor de un recurso **float** de 32 bits.

### <a name="prototype"></a>Prototipo

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Descripción

El servicio recupera el valor de un recurso **float** de 32 bits.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **float32_ptr**: puntero al valor **float** de 32 bits de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es booleano.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a>nx_lwm2m_client_resource_float32_set

Establece el valor de un recurso **float** de 32 bits.

### <a name="prototype"></a>Prototipo

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a>Descripción

El servicio establece el valor de un recurso **float** de 32 bits.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **float32_data**: datos de valor **float** de 32 bits.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a>nx_lwm2m_client_resource_float64_get

Obtiene el valor de un recurso float de 64 bits.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Descripción

El servicio recupera el valor de un recurso **float** de 64 bits.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **float64_ptr**: puntero al valor **float** de 64 bits de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es flotante.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a>nx_lwm2m_client_resource_float64_set

Establece el valor de un recurso **float** de 64 bits.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Descripción

El servicio establece el valor de un recurso **float** de 64 bits.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **float64_data**: datos de valor **float** de 64 bits.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a>nx_lwm2m_client_resource_info_get

Obtiene la información del recurso.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a>Descripción

El servicio recupera la información del recurso.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **resource_id**: puntero al identificador del recurso de destino.
- **operation**: puntero a la operación de recurso de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a>nx_lwm2m_client_resource_info_set

Establece la información del recurso.

### <a name="prototype"></a>Prototipo

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Descripción

El servicio establece la información del recurso.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **resource_id**: identificador del recurso.
- **operation**: operación del recurso.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a>nx_lwm2m_client_resource_instances_get

Obtiene la instancia de varios recursos.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a>Descripción

El servicio recupera la información del recurso.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **resource_instances**: puntero al identificador del recurso de destino.
- **count**: puntero al recuento.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es booleano.
- **NX_LWM2M_CLIENT_NO_MEMORY**: sin memoria para rellenar las instancias.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a>nx_lwm2m_client_resource_instances_set

Establece las instancias del recurso.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a>Descripción

El servicio establece las instancias de recurso para varios recursos.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **resource_instance**: puntero a las instancias de recurso.
- **count**: recuento de instancias de recurso.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a>nx_lwm2m_client_resource_integer32_get

Obtiene el valor de un recurso integer de 32 bits.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a>Descripción

El servicio recupera el valor de un recurso integer de 32 bits.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **integer32_ptr**: puntero al valor entero de 32 bits.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es entero.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a>nx_lwm2m_client_resource_integer32_set

Establece el valor de un recurso integer de 32 bits.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a>Descripción

El servicio establece el valor de un recurso integer de 32 bits.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **integer32_data**: datos de entero de 32 bits.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a>nx_lwm2m_client_resource_integer64_get

Obtiene el valor de un recurso integer de 64 bits.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a>Descripción

El servicio recupera el valor de un recurso integer de 64 bits.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **integer64_ptr**: puntero al valor entero de 64 bits.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es un entero de 64 bits.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a>nx_lwm2m_client_resource_integer64_set

## <a name="set-the-value-of-a-64-bit-integer-resource"></a>Establece el valor de un recurso integer de 64 bits.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a>Descripción

El servicio establece el valor de un recurso integer de 64 bits.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **integer64_data**: entero 64 bits.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a>nx_lwm2m_client_resource_objlnk_get

Obtiene el valor de un recurso de vínculo de objeto.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a>Descripción

El servicio recupera el valor de un vínculo de objeto.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **object_id**: puntero al id. de objeto.
- **instance_id**: puntero al id. de instancia de objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: El valor del recurso no es un valor de vínculo de objeto.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a>nx_lwm2m_client_resource_objlnk_set

Establece las instancias del recurso.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Descripción

El servicio establece el valor del recurso de vínculo de objeto.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **object_id**: identificador del objeto.
- **instance_id**: identificador de la instancia de objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a>nx_lwm2m_client_resource_opaque_get

Obtiene el valor de un recurso opaque.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a>Descripción

El servicio recupera el valor de un recurso opaque. Un valor de recurso opaque está formado por un puntero a un búfer y una longitud.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **opaque_ptr**: puntero a los datos opacos.
- **opaque_length**: puntero a la longitud de los datos opacos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es un recurso opaque.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a>nx_lwm2m_client_resource_opaque_set

Establece el valor de un recurso opaque.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a>Descripción

El servicio establece el valor de un recurso opaque.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **opaque_ptr**: puntero a los datos opacos.
- **opaque_length**: longitud de los datos opacos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a>nx_lwm2m_client_resource_string_get

Obtiene el valor de un recurso string.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a>Descripción

El servicio recupera el valor de un recurso string.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **string_ptr**: puntero al puntero de la cadena de destino.
- **string_length**: puntero a la longitud de la cadena de destino. Puede ser **NULL** si la cadena termina en NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es de cadena.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a>nx_lwm2m_client_resource_string_set

Establece el valor de un recurso string.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a>Descripción

El servicio establece el valor de un recurso integer de 64 bits.

### <a name="parameters"></a>Parámetros

- **resource**: puntero al recurso.
- **string_ptr**: puntero a la cadena.
- **string_length**: longitud de la cadena.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Inicia una sesión con un servidor de arranque.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a>Descripción

Este servicio inicia una sesión con un servidor de arranque. El servidor debe tener una instancia de seguridad correspondiente en el objeto de seguridad.

Si el recurso "Hold Off" es distinto de cero en la instancia de seguridad asociada a este servidor, la sesión esperará a un arranque iniciado por el servidor; si el servidor no inicia ningún arranque después de este período de tiempo, se llevará a cabo un arranque iniciado por el cliente.

Esta llamada anula cualquier sesión activa actual, que se reemplaza por la nueva sesión del servidor de arranque.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.
- **security_id**: id. de instancia de seguridad del servidor de arranque; debe establecerse en NX_LWM2M_RESERVED_ID (65535) si el servidor de arranque no tiene definida ninguna instancia de seguridad.
- **ip_address**: dirección IP del servidor.
- **port**: puerto UDP del servidor.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_ERROR**: error de arranque.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE**: el puerto no está disponible.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Inicia una sesión segura con un servidor de arranque.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia una sesión con un servidor de arranque mediante una conexión DTLS segura. El servidor debe tener una instancia de seguridad correspondiente en el objeto de seguridad.

La sesión DTLS se debe haber configurado con los conjuntos de cifrado y el material de clave adecuados antes de llamar a esta función. **NX_SECURE_ENABLE_DTLS** debe definirse.

Si el recurso "Hold Off" es distinto de cero en la instancia de seguridad asociada a este servidor, la sesión esperará a un arranque iniciado por el servidor; si el servidor no inicia ningún arranque después de este período de tiempo, se llevará a cabo un arranque iniciado por el cliente. 

Esta llamada anula cualquier sesión activa actual, que se reemplaza por la nueva sesión del servidor de arranque.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.
- **security_id**: id. de instancia de seguridad del servidor de arranque; debe establecerse en **NX_LWM2M_RESERVED_ID** (65535) si el servidor de arranque no tiene definida ninguna instancia de seguridad.
- **ip_address**: dirección IP del servidor.
- **port**: puerto UDP del servidor.
- **dtls_session_ptr**: sesión DTLS que se va a usar para la sesión de arranque.
- **dtls_local_port**: puerto UDP local usado para la sesión DTLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_ERROR**: error de arranque.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE**: el puerto no está disponible.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Crea una sesión de cliente LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Descripción

Este servicio crea una nueva sesión de cliente LWM2M asociada a un cliente LWM2M existente. El cliente LWM2M usa la sesión para comunicarse con un servidor de arranque o un servidor LWM2M. 

La aplicación debe proporcionar una función de devolución de llamada a la que se llamará cuando se actualice el estado de la sesión.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.
- **client_ptr**: puntero al cliente LWM2M creado anteriormente.
- **state_callback**: devolución de llamada de la aplicación a la que se llama cuando el estado de la sesión ha cambiado.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Elimina una sesión de cliente LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una sesión de cliente LWM2M.

Cuando se elimina un cliente LWM2M mediante una llamada a nx_lwm2m_client_delete también se eliminan todas las sesiones asociadas al cliente.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Finaliza una sesión con un servidor LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de anulación de registro en un servidor LWM2M.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_NOT_REGISTERED**: el cliente no está registrado en el servidor.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Obtiene el último error de una sesión.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio devuelve el código de error de la sesión cuando la sesión se encuentra en estado de error.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: la sesión no está en estado de error.
- **NX_LWM2M_CLIENT_ADDRESS_ERROR**: dirección del servidor no válida.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**: la carga de la solicitud no cabe en el búfer de red.
- **NX_LWM2M_CLIENT_DTLS_ERROR**: no se pudo establecer una conexión segura con el servidor.
- **NX_LWM2M_CLIENT_ERROR**: error no especificado.
- **NX_LWM2M_CLIENT_FORBIDDEN**: el servidor rechazó el registro.
- **NX_LWM2M_CLIENT_NOT_FOUND**: el servidor no encontró el cliente al actualizar o eliminar el registro.
- **NX_LWM2M_CLIENT_SERVER_INSTANCE_DELETED**: se eliminó la instancia de objeto de servidor correspondiente a la sesión.
- **NX_LWM2M_CLIENT_TIMED_OUT**: el servidor no devolvió ninguna respuesta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Inicia una sesión con un servidor LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a>Descripción

Este servicio realiza una operación de registro en un servidor LWM2M. El servidor debe tener una instancia de servidor correspondiente en el objeto de servidor.

Si el registro se realiza correctamente, el cliente LWM2M procesará más operaciones desde el servidor y enviará periódicamente mensajes de actualización hasta que se elimine el registro del cliente.

Esta llamada anula cualquier sesión activa actual, que se reemplaza por la nueva sesión del servidor LWM2M.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.
- **server_id**: id. de servidor corto del servidor LWM2M.
- **ip_address**: dirección IP del servidor.
- **port**: puerto UDP del servidor.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_ERROR**: error de arranque.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE**: el puerto no está disponible.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Inicia una sesión segura con un servidor LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de registro en un servidor LWM2M mediante una conexión DTLS segura. El servidor debe tener una instancia de servidor correspondiente en el objeto de servidor.

La sesión DTLS se debe haber configurado con los conjuntos de cifrado y el material de clave adecuados antes de llamar a esta función. **NX_SECURE_ENABLE_DTLS** debe definirse.

Si el registro se realiza correctamente, el cliente LWM2M procesará más operaciones desde el servidor y enviará periódicamente mensajes de actualización hasta que se elimine el registro del cliente.

Esta llamada anula cualquier sesión activa actual, que se reemplaza por la nueva sesión del servidor LWM2M.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.
- **server_id**: id. de servidor corto del servidor LWM2M.
- **ip_address**: dirección IP del servidor.
- **port**: puerto UDP del servidor.
- **dtls_session_ptr**: sesión DTLS que se va a usar para la sesión de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_ERROR**: error de arranque.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE**: el puerto no está disponible.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a>nx_lwm2m_client_session_register_info_get

Inicia una sesión segura con un servidor LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a>Descripción

Una vez establecida una sesión de comunicación con un servidor de arranque. La aplicación puede llamar a esta API para obtener el servidor y la información de seguridad para el siguiente paso de registro.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.
- **security_instance_id**: identificador de la instancia de seguridad.
- **server_id**: puntero al identificador del servidor de destino.
- **server_uri**: puntero al URI del servidor de destino.
- **server_uri_len**: puntero a la longitud del URI del servidor de destino.
- **security_mode**: puntero al modo de seguridad de destino.
- **pub_key_or_id**: puntero a la identidad o la clave pública de destino.
- **pub_key_or_id_len**: puntero a la longitud de la identidad o la clave pública de destino.
- **server_pub_key**: puntero a la clave pública del servidor de destino.
- **server_pub_key_len**: puntero a la longitud de la clave pública del servidor de destino.
- **secret_key**: puntero a la clave secreta de destino.
- **secret_key_len**: puntero a la longitud de la clave secreta de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_NOT_FOUND**: no hay ninguna instancia de objeto de seguridad.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Actualiza una sesión con un servidor LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de actualización en un servidor LWM2M.

### <a name="parameters"></a>Parámetros

- **session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_LWM2M_CLIENT_NOT_REGISTERED**: el cliente no está registrado en el servidor.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Desbloquea un cliente LWM2M.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio desbloquea el cliente LWM2M previamente bloqueado mediante una llamada a ***nx_lwm2m_client_unlock***.

### <a name="parameters"></a>Parámetros

- **client_ptr**: puntero al bloque de control del cliente LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: operación correcta.
- **NX_PTR_ERROR**: puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```