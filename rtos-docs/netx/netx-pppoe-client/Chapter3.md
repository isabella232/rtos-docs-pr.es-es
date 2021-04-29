---
title: 'Capítulo 3: Descripción de los servicios del cliente PPPoE de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios del cliente PPPoE de Azure RTOS NetX (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 246115fc97d7597246f7fd5b4fb88cb615baab33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814446"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a>Capítulo 3: Descripción de los servicios del cliente PPPoE de Azure RTOS NetX

Este capítulo contiene una descripción de todos los servicios del cliente PPPoE de Azure RTOS NetX (enumerados a continuación) en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nx_pppoe_client_create** *Crear una instancia de cliente PPPoE*
- **nx_pppoe_client_delete** *Eliminar una instancia de cliente PPPoE*
- **nx_pppoe_client_host_uniq_set** *Establecer el host único para el cliente PPPoE*
- **nx_pppoe_client_host_uniq_set_extended** *Establecer el host único para el cliente PPPoE*
- **nx_pppoe_client_service_name_set** *Establecer el nombre del servicio para el cliente PPPoE*
- **nx_pppoe_client_service_name_set_extended** *Establecer el nombre del servicio para el cliente PPPoE*
- **nx_pppoe_client_session_connect** *Conectar la sesión de cliente PPPoE al servidor de PPPoE*
- **nx_pppoe_client_session_packet_send** *Enviar paquete de sesión de PPPoE*
- **nx_pppoe_client_session_terminate** *Finalizar la sesión de PPPoE*
- **nx_pppoe_client_session_get** *Obtener el inf de sesión de PPPoE especificado*

## <a name="nx_pppoe_client_create"></a>nx_pppoe_client_create

Crear una instancia de cliente PPPoE

### <a name="prototype"></a>Prototipo

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a>Descripción

Este servicio crea una instancia del cliente PPPoE con el controlador de vínculo proporcionado por el usuario para la instancia de IP de NetX especificada. Si el controlador de vínculo no se ha inicializado y está habilitado, el software del cliente PPPoE es responsable de inicializar el controlador de vínculo.

Además, la aplicación debe proporcionar un grupo de paquetes creado previamente para la instancia de IP que se va a utilizar para la asignación interna de paquetes.

> [!NOTE]
> Por lo general, es una buena idea crear el subproceso de IP de NetX con una prioridad más alta que la de los subprocesos del cliente PPPoE. Consulte el servicio *nx_ip_create* para obtener más información sobre cómo especificar la prioridad del subproceso de IP.

### <a name="input-parameters"></a>Parámetros de entrada

 - **pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.
 - **name** Nombre de esta instancia de cliente PPPoE.
 - **ip_ptr** Puntero al bloque de control de la instancia de IP.
 - **interface_index** Índice de la interfaz.
 - **pool_ptr** Puntero al grupo de paquetes.
 - **stack_ptr** Puntero al inicio del área de la pila del subproceso del cliente PPPoE.
 - **stack_size** Tamaño en bytes de la pila del subproceso.
 - **priority** Prioridad de los subprocesos de cliente PPPoE internos (1-31).
 - **pppoe_link_driver** Controlador del vínculo proporcionado por el usuario.
 - **pppoe_packet_receive** Función de recepción de paquetes proporcionada por el usuario.

### <a name="return-values"></a>Valores devueltos

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Creación correcta del cliente PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de pila, grupo de paquetes, IP o cliente PPPoE no válido.
 - NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Interfaz no válida.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Tamaño de carga no válido del grupo de paquetes.
 - NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Tamaño de memoria no válido.
 - NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Prioridad no válida del subproceso del cliente PPPoE.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a>nx_pppoe_client_delete

Eliminar una instancia de cliente PPPoE

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina la instancia del cliente PPPoE creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

 - **pppoe_client_ptr** Puntero al bloque de control de cliente PPPoE.

### <a name="return-values"></a>Valores devueltos

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Eliminación correcta del cliente PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a>nx_pppoe_client_host_uniq_set

Establecer host único de cliente PPPoE

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a>Descripción

Este servicio establece un host de cliente PPPoE único. Un host usa Host-Uniq para asociar de forma única un concentrador de acceso a una solicitud de host determinada.
Pueden ser datos binarios de cualquier valor y longitud que elija el host.

> [!NOTE]
> El host único debe ser una cadena terminada en NULL.

> [!NOTE]
> Este servicio está en desuso. Se recomienda a los desarrolladores que migren a *nx_pppoe_client_host_uniq_set_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.
 - **host_uniq** Puntero a un host único. El host único debe ser una cadena terminada en NULL.

### <a name="return-values"></a>Valores devueltos

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Configuración correcta del host único del cliente PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a>nx_pppoe_client_host_uniq_set_extended

Establecer host único de cliente PPPoE

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a>Descripción

Este servicio establece un host de cliente PPPoE único. Un host usa Host-Uniq para asociar de forma única un concentrador de acceso a una solicitud de host determinada.
Pueden ser datos binarios de cualquier valor y longitud que elija el host.

> [!NOTE]
> El host único debe ser una cadena terminada en NULL.

> [!NOTE]
> Este servicio reemplaza a *nx_pppoe_client_host_uniq_set()* . Esta versión proporciona información de longitud adicional al servicio.

### <a name="input-parameters"></a>Parámetros de entrada

 - **pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.
 - **host_uniq** Puntero a un host único. El host único debe ser una cadena terminada en NULL.
 - **host_uniq_length** Longitud de host_uniq.

### <a name="return-values"></a>Valores devueltos

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Configuración correcta del host único del cliente PPPoE.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Puntero de cliente PPPoE no válido.
 - **NX_SIZE_ERROR** (0x09) Error en la comprobación de host_uniq_length.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a>nx_pppoe_client_service_name_set

Establecer el nombre del servicio del cliente PPPoE

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a>Descripción

Este servicio establece el nombre del servicio del cliente PPPoE. Service-Name que indica el servicio que el host está solicitando. Si no se establece Service-Name, indica que el host aceptará cualquier número de servicios.

> [!NOTE]
> El nombre del servicio debe ser una cadena terminada en NULL.

> [!NOTE]
> Este servicio está en desuso. Se recomienda a los desarrolladores que migren a *nx_pppoe_client_service_name_set_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.
 - **SERVICE_NAME** Puntero a un nombre de servicio. El nombre del servicio debe ser una cadena terminada en NULL.

### <a name="return-values"></a>Valores devueltos

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Configuración correcta del nombre del servicio del cliente PPPoE.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Puntero de cliente PPPoE no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a>nx_pppoe_client_service_name_set_extended

Establecer el nombre del servicio del cliente PPPoE

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a>Descripción

Este servicio establece el nombre del servicio del cliente PPPoE. Service-Name que indica el servicio que el host está solicitando. Si no se establece Service-Name, indica que el host aceptará cualquier número de servicios.

> [!NOTE]
> El nombre del servicio debe ser una cadena terminada en NULL.

> [!NOTE]
> Este servicio reemplaza a *nx_pppoe_client_service_name_set()* . Esta versión proporciona a la función información adicional sobre la longitud del nombre del servicio.

### <a name="input-parameters"></a>Parámetros de entrada

 - **pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.
 - **SERVICE_NAME** Puntero a un nombre de servicio. El nombre del servicio debe ser una cadena terminada en NULL.
 - **service_name_length** Longitud de service_name.

### <a name="return-values"></a>Valores devueltos

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Configuración correcta del nombre del servicio del cliente PPPoE.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Puntero de cliente PPPoE no válido.
 - **NX_SIZE_ERROR** (0x09) Error de comprobación de service_name_length.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a>nx_pppoe_client_session_connect

Conectar sesión de cliente PPPoE

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio realiza la conexión de la sesión de PPPoE utilizando un cliente PPPoE previamente creado al servidor de PPPoE especificado.

> [!NOTE]
> Se debe llamar a esta función después de *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* y *nx_pppoe_client_service_name_set*.

### <a name="input-parameters"></a>Parámetros de entrada

 - **pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.
 - **wait_option** Opción de espera mientras se establece la conexión.

### <a name="return-values"></a>Valores devueltos

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Conexión correcta de la sesión del cliente PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a>nx_pppoe_client_session_packet_send

Enviar paquete de cliente PPPoE a la sesión especificada

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía un paquete de PPPoE mediante el identificador de sesión especificado.

### <a name="input-parameters"></a>Parámetros de entrada

 - **pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.
 - **packet_ptr** Puntero a paquete de PPPoE.

### <a name="return-values"></a>Valores devueltos

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Envío correcto del paquete del cliente PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Paquete de cliente PPPoE no válido.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) Sesión de PPPoE no establecida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a>nx_pppoe_client_session_terminate

Finalizar sesión de cliente PPPoE

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Descripción

Este servicio finaliza la sesión de PPPoE especificada.

### <a name="input-parameters"></a>Parámetros de entrada

 - **pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.

### <a name="return-values"></a>Valores devueltos

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Finalización correcta de la sesión del cliente PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a>nx_pppoe_client_session_get

Obtener la información de sesión de PPPoE especificada

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Descripción

Este servicio obtiene la información de sesión de PPPoE especificada, la dirección física del servidor y el identificador de sesión.

### <a name="input-parameters"></a>Parámetros de entrada

 - **pppoe_server_ptr** Puntero al bloque de control de cliente PPPoE.
 - **server_mac_msw** Puntero MSW de dirección física del servidor.
 - **server_mac_lsw** Puntero MSW de dirección física del servidor.
 - **session_id** Puntero de identificador de sesión.

### <a name="return-values"></a>Valores devueltos

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Obtención correcta de la sesión del cliente PPPoE.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) Sesión de PPPoE no establecida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
