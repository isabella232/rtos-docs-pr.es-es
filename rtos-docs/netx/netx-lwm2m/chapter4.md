---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS NetX LWM2M'
description: Este capítulo contiene una descripción de todos los servicios Azure RTOS NetX LWM2M (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815169"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a>Capítulo 4: Descripción de los servicios de Azure RTOS NetX LWM2M

Este capítulo contiene una descripción de todos los servicios Azure RTOS NetX LWM2M (enumerados a continuación) en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.

### <a name="lwm2m-client-management"></a>Administración de clientes de LWM2M

- **nx_lwm2m_client_create**: *Crear cliente de LWM2M*
- **nx_lwm2m_client_delete**: *Eliminar cliente de LWM2M*
- **nx_lwm2m_client_lock**: *Bloquear cliente de LWM2M*
- **nx_lwm2m_client_object_add**: *Agregar implementación de objeto al cliente de LWM2M*
- **nx_lwm2m_client_unlock**: *Desbloquear cliente de LWM2M*

### <a name="lwm2m-client-session-management"></a>Administración de sesiones de clientes de LWM2M

- **nx_lwm2m_client_session_bootstrap**: *Iniciar sesión con un servidor de arranque*
- **nx_lwm2m_client_session_bootstrap_dtls**: *Iniciar una sesión segura con un servidor de arranque*
- **nx_lwm2m_client_session_create**: *Crear sesión de cliente de LWM2M*
- **nx_lwm2m_client_session_delete**: *Eliminación de sesión de cliente de LWM2M*
- **nx_lwm2m_client_session_deregister**: *Finalizar una sesión con un servidor LWM2M*
- **nx_lwm2m_client_session_error_get**: *Obtener el último error de una sesión*
- **nx_lwm2m_client_session_register**: *Iniciar una sesión con un servidor LWM2M*
- **nx_lwm2m_client_session_register_dtls**: *Iniciar una sesión segura con un servidor LWM2M*
- **nx_lwm2m_client_session_update**: *Actualizar una sesión con un servidor LWM2M*

### <a name="security-object-implementation"></a>Implementación de objetos de seguridad

- **nx_lwm2m_client_security_key_callbacks_set**: *Establecer devoluciones de llamada de administración de claves de seguridad*

### <a name="device-object-implementation"></a>Implementación de objetos de dispositivo

- **nx_lwm2m_client_device_callbacks_set**: *Establecer devoluciones de llamada de aplicaciones de objetos de dispositivo*
- **nx_lwm2m_client_device_error_push**: *Agregar un código de error a un objeto de dispositivo*
- **nx_lwm2m_client_device_error_reset**: *Restablecer códigos de error del objeto de dispositivo*
- **nx_lwm2m_client_device_resource_changed**: *Cambio de señal del recurso de objeto de dispositivo*

### <a name="custom-objects-implementation"></a>Implementación de objetos personalizados

- **nx_lwm2m_object_resource_changed**: *Cambio de señal de un valor de recursos de una instancia de objeto*

### <a name="local-device-management"></a>Administración de dispositivos locales

- **nx_lwm2m_client_object_create**: *Crear una nueva instancia de objeto*
- **nx_lwm2m_client_object_delete**: *Eliminar una instancia de objeto*
- **nx_lwm2m_client_object_discover**: *Detectar recursos de una instancia de objeto*
- **nx_lwm2m_client_object_execute**: *Ejecutar el recurso de una instancia de objeto*
- **nx_lwm2m_client_object_get_next**: *Obtener la lista de objetos implementados por el cliente de LWM2M*
- **nx_lwm2m_client_object_instance_get_next**: *Obtener la lista de instancias de un objeto*
- **nx_lwm2m_client_object_read**: *Leer los valores de los recursos de una instancia de objeto*
- **nx_lwm2m_client_object_write**: *Cambiar los valores de los recursos de una instancia de objeto*

### <a name="resources-values-decoding"></a>Descodificación de valores de recursos

- **nx_lwm2m_resource_get_boolean**: *Obtener el valor de un recurso booleano*
- **nx_lwm2m_resource_get_float32**: *Obtener el valor de un recurso de punto flotante de 32 bits*
- **nx_lwm2m_resource_get_float64**: *Obtener el valor de un recurso de punto flotante de 64 bits*
- **nx_lwm2m_resource_get_integer32**: *Obtener el valor de un recurso entero de 32 bits*
- **nx_lwm2m_resource_get_integer64**: *Obtener el valor de un recurso entero de 64 bits*
- **nx_lwm2m_resource_get_objlnk**: *Obtener el valor de un recurso de vínculo de objeto*
- **nx_lwm2m_resource_get_opaque**: *Obtener el valor de un recurso opaco*
- **nx_lwm2m_resource_get_string**: *Obtener el valor de un recurso de cadena*
- **nx_lwm2m_resource_multiple_get_boolean**: *Obtener el valor de una instancia de recurso booleano en un recurso múltiple*
- **nx_lwm2m_resource_multiple_get_float32**: *Obtener el valor de una instancia de recurso de punto flotante de 32 bits en un recurso múltiple*
- **nx_lwm2m_resource_multiple_get_float64**: *Obtener el valor de un punto flotante de 64 bits en una instancia de múltiples recursos*
- **nx_lwm2m_resource_multiple_get_integer32**: *Obtener el valor de una instancia de recurso entero de 32 bits de un recurso múltiple*
- **nx_lwm2m_resource_multiple_get_integer64**: *Obtener el valor de una instancia de recurso entero de 64 bits de un recurso múltiple*
- **nx_lwm2m_resource_multiple_get_objlnk**: *Obtener el valor de una instancia de recurso de enlace de objeto de un recurso múltiple*
- **nx_lwm2m_resource_multiple_get_opaque**: *Obtener el valor de una instancia de recurso opaco de un recurso múltiple*
- **nx_lwm2m_resource_multiple_get_string**: *Obtener el valor de una instancia de cadena de un recurso múltiple*

### <a name="firmware-update-object"></a>objeto de actualización de firmware

- **nx_lwm2m_firmware_create**: *Crear el objeto de actualización de firmware*
- **nx_lwm2m_firmware_package_info_set**: *Establecer la información de paquetes de actualización de firmware*
- **nx_lwm2m_firmware_result_set**: *Establecer el resultado de la actualización de firmware*
- **nx_lwm2m_firmware_state_set**: *Establecer el estado de la actualización de firmware*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Creación de cliente de LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de cliente de LWM2M que se ejecuta en el contexto de su propio subproceso ThreadX.

El cliente de LWM2M implementa los siguientes objetos OMA LWM2M: Security (0), Server (1), Access Control (2) y Device (3). La aplicación debe agregar las implementaciones de otros objetos.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **ip_ptr**: Puntero a la instancia de IP creada anteriormente.
- **packet_pool_ptr**: Puntero al grupo de paquetes predeterminado para este cliente de LWM2M.
- **local_port**: Puerto UDP local que se usa para la comunicación no segura.
- **name_ptr**: Puntero al nombre de punto de conexión del cliente de LWM2M.
- **msisdn_ptr**: Puntero a MSISDN, donde se puede acceder al cliente de LWM2M para su uso con el enlace SMS; puede ser NULL si no se admite el enlace SMS.
- **binding_modes**: El enlace y los modos admitidos por el cliente de LWM2M, deben ser una combinación de las marcas NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S y NX_LWM2M_BINDING_SQ.
- **stack_ptr**: Puntero al área de la pila de subprocesos del cliente de LWM2M.
- **stack_size**: Tamaño de la pila de subprocesos del cliente de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: El cliente de LWM2M se ha creado correctamente.
- **NX_LWM2M_ERROR**: Error al crear el cliente de LWM2M.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Eliminación de clientes de LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente de LWM2M creada anteriormente.

Esta llamada también elimina todas las sesiones asociadas actualmente al cliente.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: El cliente de LWM2M se ha eliminado correctamente.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_device_callbacks_set"></a>nx_lwm2m_client_device_callbacks_set

Definición de devoluciones de llamada de aplicaciones de objetos de dispositivo

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a>Descripción

Este servicio instala las devoluciones de llamada de la aplicación para implementar operaciones en los recursos de objeto de dispositivo de LWM2M que no son controlados por el cliente de LWM2M.

El cliente de LWM2M implementa los siguientes recursos: Error Code (11), Reset Error Code (12) and Supported Binding y Modes (16); las operaciones con los demás recursos se redirigen a la aplicación.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **read_callback**: Devolución de llamada del método de lectura.
- **discover_callback**: Devolución de llamada del método de descubrimiento.
- **write_callback**: Devolución de llamada del método de escritura.
- **execute_callback**: Devolución de llamada del método de ejecución.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push

Adición de un código de error a un objeto de dispositivo

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a>Descripción

Este servicio agrega una nueva instancia al recurso Error Code (11) del dispositivo de objeto.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **code**: Nuevo código de error.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BUFFER_TOO_SMALL**: Se ha alcanzado el número máximo de códigos de error almacenados.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Restablecimiento de códigos de error del objeto de dispositivo

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina todas las instancias de recursos de código de error del objeto de dispositivo. Esto es equivalente a la ejecución del código del recurso Reset Error Code (12).

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Cambio de señal del recurso de objeto de dispositivo

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Descripción

La aplicación usa el servicio para indicar al cliente de LWM2M que un recurso del objeto de dispositivo ha cambiado. El cliente de LWM2M enviará una notificación si un servidor LWM2M observa el recurso.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **resource**: Puntero a la estructura que describe el recurso que ha cambiado.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Bloqueo del cliente de LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio bloquea al cliente de LWM2M para impedir el acceso simultáneo a los objetos LWM2M desde los servidores o desde otro subproceso de aplicación.

Si el cliente de LWM2M está bloqueado actualmente por otro subproceso, la función se bloqueará hasta que se desbloquee el cliente de LWM2M.

Las llamadas a pares nx_lwm2m_client_lock nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() se pueden anidar.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Adición de implementación de objeto al cliente de LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a>Descripción

Este servicio agrega una nueva implementación de objeto al cliente de LWM2M.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **object_ptr**: Puntero a la estructura que define la implementación del objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_ALREADY_EXIST**: El id. de objeto ya existe.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Creación de una nueva instancia de objeto

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de creación en un objeto del cliente de LWM2M para crear una nueva instancia de objeto.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **object_id**: Id. de objeto.
- **instance_id_ptr**: Puntero al id. de la nueva instancia, puede ser NULL si el cliente de LWM2M debe asignar un id. de instancia. Si el id. es el valor reservado 65535, el cliente de LWM2M asignará un id. de instancia. Si no es NULL, el id. asignado se devuelve después de la llamada.
- **num_values**: Número de valores que se van a definir.
- **values_ptr**: Puntero a una matriz de valores de recursos para inicializar la nueva instancia de objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_ALREADY_EXIST**: El id. de instancia de objeto ya existe.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: El objeto no admite la creación de instancias.
- **NX_LWM2M_NO_MEMORY**: No se puede asignar memoria para almacenar la nueva instancia.
- **NX_LWM2M_NOT_FOUND**: El id. de objeto no existe.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Eliminación de una instancia de objeto

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de eliminación en una instancia de objeto del cliente de LWM2M.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **object_id**: Id. de objeto.
- **instance_id**: Id. de instancia de objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: El objeto no admite la eliminación de instancias.
- **NX_LWM2M_NOT_FOUND**: El id. de objeto o el id. de instancia de objeto no existen.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Detección de recursos de una instancia de objeto

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de descubrimiento en una instancia de objeto del cliente de LWM2M, lo que devuelve la lista de recursos implementados por el objeto.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **object_id**: Id. de objeto.
- **instance_id**: Id. de instancia de objeto.
- **num_resources_ptr**: En la entrada, el tamaño del búfer de destino, en la salida, el número de elementos escritos en el búfer.
- **resources_ptr**: Puntero al búfer de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BUFFER_TOO_SMALL**: El búfer de recursos es demasiado pequeño para almacenar la lista de recursos.
- **NX_LWM2M_NOT_FOUND**: El id. de objeto o el id. de instancia de objeto no existen.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Ejecución del recurso de una instancia de objeto

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de ejecución en una instancia de objeto del cliente de LWM2M.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **object_id**: Id. de objeto.
- **instance_id**: Id. de instancia de objeto.
- **resource_id**: Id. de recursos.
- **arguments_ptr**: Puntero a los argumentos de la operación de ejecución. Puede ser NULL si arguments_length es cero.
- **arguments_length**: Longitud de los argumentos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: El recurso no admite la operación de ejecución.
- **NX_LWM2M_NOT_FOUND**: El id. de objeto, el id. de instancia de objeto o el id. de recurso no existen.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_object_get_next"></a>nx_lwm2m_client_object_get_next

Obtención de la lista de objetos implementados por el cliente de LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a>Descripción

Este servicio devuelve el id. del siguiente objeto implementado por el cliente de LWM2M. Si el id. de objeto actual se establece en NX_LWM2M_RESERVED_ID (65535), se devuelve el primer id. de objeto.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **object_id_ptr**: Puntero al id. de objeto actual. En la devolución, contiene el siguiente id. de objeto implementado por el cliente de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_NOT_FOUND**: El id. de objeto especificado es el último de la base de datos.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_object_instance_get_next"></a>nx_lwm2m_client_object_instance_get_next

Obtención de la lista de instancias de un objeto

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Descripción

Este servicio devuelve el id. de la siguiente instancia de objeto del objeto especificado. Si el id. de instancia actual se establece en NX_LWM2M_RESERVED_ID (65535), se devuelve el id. de la primera instancia.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **object_id**: Id. de objeto.
- **instance_id_ptr**: Puntero al id. de instancia de objeto actual. En la devolución, contiene el id. de instancia siguiente del objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_NOT_FOUND**: El id. de instancia proporcionado es el último del objeto o el id. de objeto no está implementado.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Lectura de los valores de los recursos de una instancia de objeto

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de lectura en una instancia de objeto del cliente de LWM2M.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **object_id**: Id. de objeto.
- **instance_id**: Id. de instancia de objeto.
- **num_values**: El número de recursos que se van a leer.
- **values_ptr**: Puntero a una matriz de NX_LWM2M_RESOURCE que contiene los id. de los recursos que se van a leer. En la devolución, la matriz se rellena con los tipos y valores correspondientes.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: Un recurso no admite la operación de lectura.
- **NX_LWM2M_NOT_FOUND**: El id. de objeto, el id. de instancia de objeto o un id. de recursos no existen.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Modificación de los valores de los recursos de una instancia de objeto

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de escritura en una instancia de objeto del cliente de LWM2M.

Se pueden especificar las siguientes operaciones de escritura en el parámetro *write_op*:

- **0** &mdash; Partial Update: Agrega o actualiza los recursos proporcionados en el nuevo valor y deja sin modificar otros recursos existentes.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: Reemplaza la instancia de objeto con los nuevos valores de recursos proporcionados.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: Reemplaza los recursos con los nuevos valores de recursos proporcionados (usados para reemplazar recursos múltiples).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: Indica una llamada desde una secuencia de arranque.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **object_id**: Id. de objeto.
- **instance_id**: Id. de instancia de objeto.
- **num_values**: Número de recursos que se van a escribir.
- **values_ptr**: Puntero a una matriz de NX_LWM2M_RESOURCE que contiene los id. de los recursos, los tipos y los valores que se van a escribir.
- **write_op**: Tipo de operación de escritura.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_ENCODING**: El tipo de un recurso no es válido.
- **NX_LWM2M_BUFFER_TOO_SMALL**: La longitud de un valor es demasiado grande para almacenarse en la instancia.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: Un recurso no admite la operación de escritura.
- **NX_LWM2M_NO_MEMORY**: No se puede asignar memoria para almacenar un valor de recurso.
- **NX_LWM2M_NOT_ACCEPTABLE**: El valor de un recurso no es válido.
- **NX_LWM2M_NOT_FOUND**: El id. de objeto, el id. de instancia de objeto o un id. de recursos no existen.
- NX_OPTION_ERROR: Tipo no válido de operación de escritura.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a>nx_lwm2m_client_security_key_callbacks_set

Definición de devoluciones de llamada de administración de claves de objetos de seguridad

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a>Descripción

Este servicio instala las devoluciones de llamada de la aplicación para implementar operaciones en los recursos del objeto de seguridad de LWM2M relacionados con las claves de seguridad.

El cliente de LWM2M delega la administración de claves de seguridad en la aplicación durante las sesiones de arranque, se llamará a las devoluciones de llamada cuando el servidor de arranque escriba o elimine los siguientes recursos en una instancia de objeto de seguridad: Public Key o Identity (3), Server Public Key (4), Secret Key (5).

La aplicación es responsable del almacenamiento de los datos de claves y de la configuración de las sesiones DTLS usadas por el cliente de LWM2M.

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.
- **write_callback**: Devolución de llamada del método de clave de escritura.
- **delete_callback**: Devolución de llamada del método de clave de eliminación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Inicio de una sesión con un servidor de arranque

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Descripción

Este servicio inicia una sesión con un servidor de arranque. El servidor debe tener una instancia de seguridad correspondiente en el objeto de seguridad.

Si el recurso de espera es distinto de cero en la instancia de seguridad asociada a este servidor, la sesión esperará a un arranque iniciado por el servidor, si el servidor no inicia ningún arranque después de este período de tiempo, se llevará a cabo un arranque iniciado por el cliente.

Esta llamada anula cualquier sesión activa actual y se reemplaza por la nueva sesión del servidor de arranque.

### <a name="parameters"></a>Parámetros

- **session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.
- **security_id**: Id. de instancia de seguridad del servidor de arranque; debe establecerse en NX_LWM2M_RESERVED_ID (65535) si el servidor de arranque no tiene definida ninguna instancia de seguridad.
- **ip_address**: Dirección IP del servidor.
- **port**: Puerto UDP del servidor.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_NOT_FOUND**: No hay ninguna instancia de objeto de seguridad correspondiente al id. de instancia de seguridad.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Inicio de una sesión segura con un servidor de arranque

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Descripción

Este servicio inicia una sesión con un servidor de arranque mediante una conexión DTLS segura. El servidor debe tener una instancia de seguridad correspondiente en el objeto de seguridad.

La sesión DTLS se debe haber configurado con los conjuntos de cifrado y el material de clave adecuados antes de llamar a esta función. NX_SECURE_ENABLE_DTLS debe definirse.

Si el recurso de espera es distinto de cero en la instancia de seguridad asociada a este servidor, la sesión esperará a un arranque iniciado por el servidor, si el servidor no inicia ningún arranque después de este período de tiempo, se llevará a cabo un arranque iniciado por el cliente.

Esta llamada anula cualquier sesión activa actual y se reemplaza por la nueva sesión del servidor de arranque.

### <a name="parameters"></a>Parámetros

- **session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.
- **security_id**: Id. de instancia de seguridad del servidor de arranque; debe establecerse en NX_LWM2M_RESERVED_ID (65535) si el servidor de arranque no tiene definida ninguna instancia de seguridad.
- **ip_address**: Dirección IP del servidor.
- **port**: Puerto UDP del servidor.
- **dtls_session_ptr**: Sesión DTLS que se va a usar para la sesión de arranque.
- **dtls_local_port**: Puerto UDP local usado para la sesión DTLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_NOT_FOUND**: No hay ninguna instancia de objeto de seguridad correspondiente al id. de instancia de seguridad.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Creación de una sesión de cliente de LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Descripción

Este servicio crea una nueva sesión de cliente de LWM2M asociada a un cliente de LWM2M existente. El cliente de LWM2M usa la sesión para comunicarse con un servidor de arranque o un servidor LWM2M.

La aplicación debe proporcionar una función de devolución de llamada a la que se llamará cuando se actualice el estado de la sesión.

### <a name="parameters"></a>Parámetros

- **session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.
- **client_ptr**: Puntero al cliente de LWM2M creado anteriormente.
- **state_callback**: Devolución de llamada de la aplicación a la que se llama cuando el estado de la sesión ha cambiado.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Eliminación de una sesión de cliente de LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una sesión de cliente de LWM2M.

Cuando se elimina un cliente de LWM2M mediante una llamada a nx_lwm2m_client_delete también se eliminan todas las sesiones asociadas al cliente.

### <a name="parameters"></a>Parámetros

- **session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Finalización de una sesión con un servidor LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de anulación de registro en un servidor LWM2M.

### <a name="parameters"></a>Parámetros

- **session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_NOT_REGISTERED**: El cliente no está registrado en el servidor.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Obtención del último error de una sesión

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio devuelve el código de error de la sesión cuando la sesión se encuentra en estado de error.

### <a name="parameters"></a>Parámetros

- **session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: La sesión no está en estado de error.
- **NX_LWM2M_ADDRESS_ERROR**: Dirección de servidor no válida.
- **NX_LWM2M_BUFFER_TOO_SMALL**: la carga de la solicitud no cabe en el búfer de red.
- **NX_LWM2M_DTLS_ERROR**: No se pudo establecer una conexión segura con el servidor.
- **NX_LWM2M_ERROR**: Error no especificado.
- **NX_LWM2M_FORBIDDEN**: Registro rechazado por el servidor.
- **NX_LWM2M_NOT_FOUND**: El servidor no encontró al cliente al actualizar/eliminar el registro.
- **NX_LWM2M_SERVER_INSTANCE_DELETED**: Se ha eliminado la instancia de objeto de servidor correspondiente a la sesión.
- **NX_LWM2M_TIMED_OUT**: No hay respuesta del servidor.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Inicio de una sesión con un servidor LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de registro en un servidor LWM2M. El servidor debe tener una instancia de servidor correspondiente en el objeto de servidor.

Si el registro se realiza correctamente, el cliente de LWM2M procesará más operaciones desde el servidor y enviará periódicamente mensajes de actualización hasta que se elimine el registro del cliente.

Esta llamada anula cualquier sesión activa actual y se reemplaza por la nueva sesión del servidor LWM2M.

### <a name="parameters"></a>Parámetros

- **session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.
- **server_id**: Id. de servidor corto del servidor LWM2M.
- **ip_address**: Dirección IP del servidor.
- **port**: Puerto UDP del servidor.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_NOT_FOUND**: No hay ninguna instancia de objeto de servidor correspondiente al id. de servidor corto.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Inicio de una sesión segura con un servidor LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de registro en un servidor LWM2M mediante una conexión DTLS segura. El servidor debe tener una instancia de servidor correspondiente en el objeto de servidor.

La sesión DTLS se debe haber configurado con los conjuntos de cifrado y el material de clave adecuados antes de llamar a esta función. NX_SECURE_ENABLE_DTLS debe definirse.

Cada sesión DTLS usa su propio socket UDP para la comunicación, por lo que el puerto local dtls_local_port debe ser diferente para cada sesión si la aplicación crea varias sesiones seguras.

Si el registro se realiza correctamente, el cliente de LWM2M procesará más operaciones desde el servidor y enviará periódicamente mensajes de actualización hasta que se elimine el registro del cliente.

Esta llamada anula cualquier sesión activa actual y se reemplaza por la nueva sesión del servidor LWM2M.

### <a name="parameters"></a>Parámetros

- **session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.
- **server_id**: Id. de servidor corto del servidor LWM2M.
- **ip_address**: Dirección IP del servidor.
- **port**: Puerto UDP del servidor.
- **dtls_session_ptr**: Sesión DTLS que se va a usar para la sesión de LWM2M.
- **dtls_local_port**: Puerto UDP local usado para la sesión DTLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_NOT_FOUND**: No hay ninguna instancia de objeto de servidor correspondiente al id. de servidor corto.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Actualización de una sesión con un servidor LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descripción

Este servicio realiza una operación de actualización en un servidor LWM2M.

### <a name="parameters"></a>Parámetros

- **session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_NOT_REGISTERED**: El cliente no está registrado en el servidor.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Desbloqueo del cliente de LWM2M

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio desbloquea al cliente de LWM2M previamente bloqueado por una llamada a nx_lwm2m_client_unlock().

### <a name="parameters"></a>Parámetros

- **client_ptr**: Puntero al bloque de control del cliente de LWM2M.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_firmware_create"></a>nx_lwm2m_firmware_create

Creación de un objeto de actualización de firmware

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a>Descripción

Este servicio inicializa un objeto de actualización de firmware y agrega el objeto a un cliente de LWM2M creado anteriormente. El objeto de actualización de firmware implementa los recursos para comunicarse con un servidor LWM2M, pero la aplicación debe proporcionar devoluciones de llamada para implementar las operaciones reales en el firmware (descarga, almacenamiento y actualización de firmware).

El parámetro protocols indica qué protocolos son compatibles con la aplicación para recuperar el firmware con el recurso "Package URI"; se definen las marcas siguientes:

NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.

### <a name="parameters"></a>Parámetros

- **firmware_ptr**: Puntero al bloque de control del objeto de firmware.
- **client_ptr**: Puntero al cliente de LWM2M creado anteriormente.
- **protocolos**: Marcas que indican qué protocolos admite el recurso URI del paquete.
- **package_callback**: Debe ser NULL [por determinar].
- **package_uri_callback**: Devolución de llamada usada para implementar el recurso URI del paquete.
- **update_callback**: Devolución de llamada usada para implementar el recurso de Actualización.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_firmware_package_info_set"></a>nx_lwm2m_firmware_package_info_set

Definición de información de paquete de actualización de firmware

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a>Descripción

Este servicio cambia los valores de los recursos "PkgName" (6) y "PkgVersion" (7) del objeto de actualización de firmware.

### <a name="parameters"></a>Parámetros

- **firmware_ptr**: Puntero al objeto de actualización de firmware.
- **name**: Nuevo valor del Nombre del paquete.
- **versión**: Nuevo valor de la Versión del paquete.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_firmware_result_set"></a>nx_lwm2m_firmware_result_set

Definición del resultado de la actualización de firmware

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a>Descripción

Este servicio cambia el valor del recurso "Update result" (5) del objeto de actualización de firmware.

### <a name="parameters"></a>Parámetros

- **firmware_ptr**: Puntero al objeto de actualización de firmware.
- **result**: El nuevo valor del recurso de Resultado de actualización.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_firmware_state_set"></a>nx_lwm2m_firmware_state_set

Definición del estado de actualización del firmware

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a>Descripción

Este servicio cambia el valor del recurso "State" (3) del objeto de actualización de firmware.

### <a name="parameters"></a>Parámetros

- **firmware_ptr**: Puntero al objeto de actualización de firmware.
- **state**: Nuevo valor del recurso de Estado.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_object_resource_changed"></a>nx_lwm2m_object_resource_changed

Modificación de señal de un valor de recurso de una instancia de objeto

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Descripción

La implementación de un objeto usa este servicio para indicar al cliente de LWM2M que uno de sus valores de recurso ha cambiado. El cliente de LWM2M enviará una notificación si un servidor LWM2M observa el recurso.

### <a name="parameters"></a>Parámetros

- **object_ptr**: Puntero a la implementación del objeto.
- **instance_ptr**: Puntero a la instancia de objeto.
- **resource**: Puntero a la estructura que describe el recurso que ha cambiado.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- NX_PTR_ERROR: Puntero no válido.

## <a name="nx_lwm2m_resource_get_boolean"></a>nx_lwm2m_resource_get_boolean

Obtención del valor de un recurso booleano

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de un recurso booleano.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso.
- **bool_ptr**: Puntero al valor booleano de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor booleano.

## <a name="nx_lwm2m_resource_get_float32"></a>nx_lwm2m_resource_get_float32

Obtención del valor de un recurso de punto flotante de 32 bits

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de un recurso de punto flotante de 32 bits.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso.
- **float32_ptr**: Puntero al valor de punto flotante de 32 bits de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor de punto flotante.

## <a name="nx_lwm2m_resource_get_float64"></a>nx_lwm2m_resource_get_float64

Obtención del valor de un recurso de punto flotante de 64 bits

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de un recurso de punto flotante de 64 bits.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso.
- **float64_ptr**: Puntero al valor de punto flotante de 64 bits de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor de punto flotante.

## <a name="nx_lwm2m_resource_get_integer32"></a>nx_lwm2m_resource_get_integer32

Obtención del valor de un recurso entero de 32 bits.

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de un recurso entero de 32 bits.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso.
- **int32_ptr**: Puntero al valor Entero de 32 bits de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor Entero o el valor Entero no cabe en un número de 32 bits.

## <a name="nx_lwm2m_resource_get_integer64"></a>nx_lwm2m_resource_get_integer64

Obtención del valor de un recurso entero de 64 bits

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de un recurso entero de 64 bits.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso.
- **int64_ptr**: Puntero al valor Entero de 64 bits de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor Entero.

## <a name="nx_lwm2m_resource_get_objlnk"></a>nx_lwm2m_resource_get_objlnk

Obtención del valor de un recurso de vínculo de objeto

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de un recurso de vínculo de objeto.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso.
- **objlnk_ptr**: Puntero al valor de Vínculo del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor de Vínculo de objeto.

## <a name="nx_lwm2m_resource_get_opaque"></a>nx_lwm2m_resource_get_opaque

Obtención del valor de un recurso opaco

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de un recurso opaco.

Un valor de recurso opaco está formado por un puntero a un búfer y una longitud.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso.
- **opaque_ptr_ptr**: Puntero al puntero de búfer opaco de destino.
- **opaque_length_ptr**: Puntero a la longitud de búfer opaco de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor Opaco.

## <a name="nx_lwm2m_resource_get_string"></a>nx_lwm2m_resource_get_string

Obtención del valor de un recurso de cadena

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de un recurso de cadena.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso.
- **string_ptr_ptr**: Puntero al puntero de la cadena de destino.
- **string_length_ptr**: Puntero a la longitud de la cadena de destino. Puede ser NULL si la cadena termina en cero.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor de Cadena.

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a>nx_lwm2m_resource_multiple_get_boolean

Obtención del valor de una instancia de recurso booleano en un recurso múltiple

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de una instancia de recurso booleano de un recurso múltiple.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso múltiple.
- **index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.
- **instance_id_ptr**: Puntero al id. de instancia de destino.
- **bool_ptr**: Puntero al valor booleano de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.
- **NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor booleano.

## <a name="nx_lwm2m_resource_multiple_get_float32"></a>nx_lwm2m_resource_multiple_get_float32

Obtención del valor de una instancia de recurso de punto flotante de 32 bits en un recurso múltiple

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de una instancia de recurso de punto flotante de 32 bits de un recurso múltiple.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso múltiple.
- **index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.
- **instance_id_ptr**: Puntero al id. de instancia de destino.
- **float32_ptr**: Puntero al valor de punto flotante de 32 bits de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.
- **NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor de punto flotante.

## <a name="nx_lwm2m_resource_multiple_get_float64"></a>nx_lwm2m_resource_multiple_get_float64

Obtención del valor de una instancia de recurso de punto flotante de 64 bits de un recurso múltiple

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de una instancia de recurso de punto flotante de 64 bits de un recurso múltiple.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso múltiple.
- **index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.
- **instance_id_ptr**: Puntero al id. de instancia de destino.
- **float64_ptr**: Puntero al valor de punto flotante de 64 bits de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.
- **NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor de punto flotante.

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a>nx_lwm2m_resource_multiple_get_integer32

Obtención del valor de una instancia de recurso entero de 32 bits de un recurso múltiple

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de una instancia de recurso entero de 32 bits de un recurso múltiple.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso múltiple.
- **index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.
- **instance_id_ptr**: Puntero al id. de instancia de destino.
- **int32_ptr**: Puntero al valor Entero de 32 bits de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.
- **NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor entero o el valor entero no cabe en un número de 32 bits.

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a>nx_lwm2m_resource_multiple_get_integer64

Obtención del valor de una instancia de recurso entero de 64 bits de un recurso múltiple

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de una instancia de recurso entero de 64 bits de un recurso múltiple.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso múltiple.
- **index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.
- **instance_id_ptr**: Puntero al id. de instancia de destino.
- **int64_ptr**: Puntero al valor Entero de 64 bits de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.
- **NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor Entero.

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a>nx_lwm2m_resource_multiple_get_objlnk

Obtención del valor de una instancia de recurso de enlace de objeto de un recurso múltiple

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de una instancia de recurso de enlace de objeto de un recurso múltiple.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso múltiple.
- **index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.
- **instance_id_ptr**: Puntero al id. de instancia de destino.
- **objlnk_ptr**: Puntero al valor de Vínculo del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.
- **NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor de vínculo de objeto.

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a>nx_lwm2m_resource_multiple_get_opaque

Obtención del valor de una instancia de recurso opaco de un recurso múltiple

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de una instancia de recurso opaco de un recurso múltiple.

Un valor de recurso opaco está formado por un puntero a un búfer y una longitud.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso múltiple.
- **index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.
- **instance_id_ptr**: Puntero al id. de instancia de destino.
- **opaque_ptr_ptr**: Puntero al puntero de búfer opaco de destino.
- **opaque_length_ptr**: Puntero a la longitud de búfer opaco de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.
- **NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor Opaco.

## <a name="nx_lwm2m_resource_multiple_get_string"></a>nx_lwm2m_resource_multiple_get_string

Obtención del valor de una instancia de cadena de un recurso múltiple

### <a name="prototype"></a>Prototipo

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el valor de una instancia de recurso de cadena de un recurso múltiple.

### <a name="parameters"></a>Parámetros

- **value**: Puntero a la descripción del valor de recurso múltiple.
- **index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.
- **instance_id_ptr**: Puntero al id. de instancia de destino.
- **string_ptr_ptr**: Puntero al puntero de la cadena de destino.
- **string_length_ptr**: Puntero a la longitud de la cadena de destino. Puede ser NULL si la cadena termina en cero.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: Operación correcta.
- **NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.
- **NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor de instancia no es un valor de cadena.
