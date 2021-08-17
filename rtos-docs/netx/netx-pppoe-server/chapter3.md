---
title: 'Capítulo 3: Descripción de los servicios del servidor PPPoE de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios del servicio PPPoE de Azure RTOS NetX (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d184fc3c5e6ed74ef25045561b1613e280672f77385fbb13b8e84bccf051b301
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782819"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a>Capítulo 3: Descripción de los servicios del servidor PPPoE de Azure RTOS NetX

Este capítulo contiene una descripción de todos los servicios del servicio PPPoE de Azure RTOS NetX (enumerados a continuación) en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nx_pppoe_server_create**: *crea una instancia del servidor PPPoE*.

- **nx_pppoe_server_ac_name_set**: *establece el nombre del concentrador de acceso*.

- **nx_pppoe_server_delete**: *elimina una instancia del servidor PPPoE*.

- **nx_pppoe_server_enable**: *habilita servicios del servidor PPPoE*.

- **nx_pppoe_server_disable**: *deshabilita los servicios del servidor PPPoE*.

- **nx_pppoe_server_callback_notify_set**: *establece funciones de notificación de devolución de llamada del servidor PPPoE*.

- **nx_pppoe_server_service_name_set**: *establece el nombre del servicio del servidor PPPoE*.

- **nx_pppoe_server_session_send**: *envía datos del servidor PPPoE a la sesión especificada*.

- **nx_pppoe_server_session_packet_send**: *envía un paquete del servidor PPPoE a la sesión especificada*.

- **nx_pppoe_server_session_terminate**: *finaliza la sesión PPPoE especificada*.

- **nx_pppoe_server_session_get**: *obtiene la información de sesión especificada*.

## <a name="nx_pppoe_server_create"></a>nx_pppoe_server_create

Crea una instancia del servidor PPPoE.

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia del servidor PPPoE con el controlador de vínculo proporcionado por el usuario para la instancia de IP NetX especificada. Si el controlador de vínculo no se ha inicializado y está habilitado, el software del servidor PPPoE es responsable de inicializar el controlador de vínculo.

Además, la aplicación debe proporcionar un grupo de paquetes creado previamente para la instancia del servidor PPPoE que se va a utilizar para la asignación interna de paquetes.

Tenga en cuenta que, por lo general, se recomienda crear el subproceso de IP de NetX con una prioridad más alta que la prioridad de subproceso del servidor PPPoE. Consulte el servicio *nx_ip_create* para obtener más información sobre cómo especificar la prioridad del subproceso de IP.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.
- **nombre**: nombre de esta instancia del servidor PPPoE.
- **ip_ptr**: puntero al bloque de control de la instancia de IP.
- **interface_index**: índice de interfaz.
- **pppoe_link_driver**: controlador de vínculo proporcionado por el usuario.
- **pool_ptr**: puntero al grupo de paquetes.
- **stack_ptr**: puntero al inicio del área de pila del subproceso del servidor PPPoE.
- **stack_size**: tamaño en bytes de la pila del subproceso.
- **prioridad**: prioridad de los subprocesos de servidor PPPoE internos (1-31).

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) creación correcta del servidor PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) servidor PPPoE no válido, IP, grupo de paquetes o puntero de pila.
- NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) interfaz no válida.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) tamaño de carga no válido del grupo de paquetes.
- NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) tamaño de memoria no válido.
- NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) prioridad no válida del subproceso del servidor PPPoE.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a>nx_pppoe_server_delete

Elimina una instancia del servidor PPPoE.

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina la instancia del servidor PPPoE creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a>nx_pppoe_server_enable

Habilita el servicio del servidor PPPoE.

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita los servicios del servidor PPPoE.

> [!NOTE]
> Se debe llamar a esta función después de *nx_pppoe_server_create* y *nx_pppoe_server_callback_notify_set*.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a>nx_pppoe_server_disable

Deshabilita el servicio del servidor PPPoE.

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita los servicios del servidor PPPoE.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a>nx_pppoe_server_callback_notify_set

Establece funciones de notificación de devolución de llamada del servidor PPPoE. 

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a>Descripción

Este servicio establece las funciones de notificación de devolución de llamada del servidor PPPoE.

> [!NOTE]
> Se debe llamar a esta función antes de *nx_pppoe_server_enable*, y se debe establecer el puntero de función pppoe_data_receive_notify, si no es así, *nx_pppoe_server_enable* producirá un error.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.
- **pppoe_discover_initiation_notify**: función de aplicación a la que se llama cada vez que se recibe el mensaje de inicio de la detección de PPPoE. Si este valor es NULL, la función de devolución de llamada de detección de inicio está deshabilitada.
- **pppoe_discover_request_notify**: función de aplicación a la que se llama cada vez que se recibe el mensaje de solicitud de detección de PPPoE. Si este valor es NULL, la función de devolución de llamada de solicitud de detección está deshabilitada.
- **pppoe_discover_terminate_notify**: función de aplicación a la que se llama siempre que se recibe el mensaje de finalización de la detección de PPPoE. Si este valor es NULL, se deshabilita la función de devolución de llamada de finalización.
- **pppoe_discover_terminate_confirm**: función de aplicación a la que se llama cada vez que se envía un mensaje de finalización de la detección de PPPoE. Si este valor es NULL, se deshabilita la función de devolución de llamada de finalización.
- **pppoe_data_receive_notify**: función de aplicación a la que se llama cada vez que se recibe un mensaje de datos de PPPoE. Este valor no se debe cambiar.
- **pppoe_data_send_notify**: función de aplicación a la que se llama cada vez que se envía un mensaje de datos de PPPoE. Si este valor es NULL, la función de devolución de llamada de envío de datos está deshabilitada.

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero del servidor PPPoE o puntero de función no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a>nx_pppoe_server_ac_name_set

Establece el nombre del concentrador de acceso.

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a>Descripción

Esta función establece la llamada de función de nombre de concentrador de acceso.

> [!NOTE]
> La cadena de ac_name debe terminar en NULL y la longitud de ac_name coincide con la longitud especificada en la lista de argumentos.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.
- **ac_name**: nombre del concentrador de acceso.
- **ac_name_length**: longitud de ac_ame.

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) conjunto de servidores PPPoE correctos.
- **NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) servidor PPPoE no válido, IP, grupo de paquetes o puntero de pila.
- **NX_SIZE_ERROR**: (0x09) error de comprobación de name_length.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a>nx_pppoe_server_service_name_set

Establece el nombre de servicio del servidor PPPoE.

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a>Descripción

Este servicio establece el nombre del servicio de servidor PPPoE.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a>nx_pppoe_server_session_send

Envía datos del servidor PPPoE a la sesión especificada.

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a>Descripción

Este servicio envía un marco PPPoE mediante el identificador de sesión especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.
- **session_index**: índice de la sesión.
- **data_ptr**: puntero al inicio de la trama de datos del servidor PPPoE.
- **Data_length**: longitud de la trama de datos del servidor PPPoE.

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.
- NX_PPPOE_SERVER_NOT_ENABLED: el servicio del servidor PPPoE de (0xC6) no está habilitado.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) índice de sesión PPPoE no válido.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) no se ha establecido la sesión PPPoE.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a>nx_pppoe_server_session_packet_send

Envía paquete del servidor PPPoE a la sesión especificada.

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía un paquete de PPPoE mediante el identificador de sesión especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.
- **session_index**: índice de la sesión.
- **packet_ptr**: puntero al paquete PPPoE.

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) paquete del servidor PPPoE no válido.
- NX_PPPOE_SERVER_NOT_ENABLED: el servicio del servidor PPPoE de (0xC6) no está habilitado.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) índice de sesión PPPoE no válido.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) no se ha establecido la sesión PPPoE.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a>nx_pppoe_server_session_terminate

Finaliza la sesión de PPPoE especificada.

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a>Descripción

Este servicio finaliza la sesión de PPPoE especificada.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.
- **session_index**: índice de la sesión.

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.
- NX_PPPOE_SERVER_NOT_ENABLED: el servicio del servidor PPPoE de (0xC6) no está habilitado.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) índice de sesión PPPoE no válido.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) no se ha establecido la sesión PPPoE.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a>nx_pppoe_server_session_get

Obtiene la información de sesión de PPPoE especificada.

### <a name="prototype"></a>Prototipo

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Descripción

Este servicio obtiene la información de sesión de PPPoE especificada, la dirección física del cliente y el identificador de sesión.

### <a name="input-parameters"></a>Parámetros de entrada

- **pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.
- **session_index**: índice de la sesión.
- **client_mac_msw**: puntero MSW de dirección física del cliente.
- **client_mac_lsw**: puntero MSW de dirección física del cliente.
- **session_id**: puntero de identificador de sesión.

### <a name="return-values"></a>Valores devueltos

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) índice de sesión PPPoE no válido.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) no se ha establecido la sesión PPPoE.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a>PppInitInd

Configura el nombre de servicio predeterminado.

### <a name="prototype"></a>Prototipo

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a>Descripción

El software de PPPoE expondrá esta función para permitir que el software de TTP configure el "nombre de servicio predeterminado" que debe usar PPPoE para filtrar las solicitudes de PADI entrantes. El software de PPPoE debe recordar esta información y, si se recibe un paquete PADI que contiene un nombre de servicio que coincide con, debe llamar a PppDiscoverReq.

### <a name="input-parameters"></a>Parámetros de entrada

- **length**: longitud del nombre de servicio predeterminado.
- **aData**: nombre de servicio predeterminado.

### <a name="return-values"></a>Valores devueltos

**None**

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a>PppDiscoverCnf

Define el campo de nombre de servicio del paquete PADO.

### <a name="prototype"></a>Prototipo

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a>Descripción

El software de PPPoE expondrá esta función para permitir que el software de TTP defina el campo de nombre de servicio del paquete PADO. El software de PPPoE no debe enviar el paquete PADO hasta que se llame a PppDiscoverCnf.

El paquete PADO debe contener un nombre de concentrador de acceso (con el identificador de etiqueta 0x0102, tal y como se define en RFC2516), definido en la inicialización del software de PPPoE.

Se pueden pasar varios nombres de servicio en aData, y cada nombre debe terminar en NULL.

El carácter NULL se usa como separador para proporcionar la máxima flexibilidad en caso de que otros comandos deban pasarse como parte del nombre del servicio.

### <a name="input-parameters"></a>Parámetros de entrada

- **length**: longitud del nombre de servicio predeterminado.
- **aData**: nombre de servicio predeterminado.
- **interfaceHandle**: identificador de interfaz.

### <a name="return-values"></a>Valores devueltos

**None**

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a>PppOpenCnf

Acepta o rechaza la sesión PPPoE.

### <a name="prototype"></a>Prototipo

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a>Descripción

El software de PPPoE expondrá esta función para permitir que el software de TTP acepte o rechace la sesión de PPPoE.  En respuesta a esta pila de PPPoE, se debe aceptar la conexión y asignar un número de Session_ID PPPoE único asociado a interfaceHandle.

### <a name="input-parameters"></a>Parámetros de entrada

- **Aceptar**: NX_TRUE si se va a aceptar la conexión.
- **interfaceHandle**: identificador de interfaz.

### <a name="return-values"></a>Valores devueltos

**None**

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a>PppCloseInd

Cierra una sesión de PPPoE.

### <a name="prototype"></a>Prototipo

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a>Descripción

El software de PPPoE expondrá esta función para permitir que el software de TTP cierre una sesión de PPPoE.

El software de PPPoE indicará la cadena de código de causa de la etiqueta de Generic-Error (0x0203) en el mensaje PADT.

### <a name="input-parameters"></a>Parámetros de entrada

- **interfaceHandle**: identificador de interfaz.
- **causeCode**: cadena terminada en NULL para enviar información sobre la razón por la que se cierra la conexión desde el servidor PPPoE.

### <a name="return-values"></a>Valores devueltos

**None**

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a>PppCloseCnf

Confirma que se ha liberado el identificador.

### <a name="prototype"></a>Prototipo

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a>Descripción

El software de PPPoE expondrá esta función para permitir que el software de TTP confirme que el identificador se ha liberado.

### <a name="input-parameters"></a>Parámetros de entrada

- **interfaceHandle**: identificador de interfaz.

### <a name="return-values"></a>Valores devueltos

**None**

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a>PppTransmitDataCnf

Permite la confirmación de los datos de PPP anteriores.

### <a name="prototype"></a>Prototipo

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a>Descripción

El software de PPPoE expondrá esta función para permitir que se confirme un PppTransmitDataReq anterior.  Implica que el software de TTP está listo para una nueva trama PPP de PPPoE.

### <a name="input-parameters"></a>Parámetros de entrada

- **interfaceHandle**: identificador de interfaz.
- **aData**: puntero el búfer de datos de PPP que se ha aceptado.
- **Packet_id**: identificador de paquete.

### <a name="return-values"></a>Valores devueltos

**None**

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a>PppReceiveDataInd

Recibe datos de la transmisión a través de Ethernet.

### <a name="prototype"></a>Prototipo

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a>Descripción

El software de PPPoE expondrá esta función para recibir datos de transmisión a través de Ethernet.

### <a name="input-parameters"></a>Parámetros de entrada

- **interfaceHandle**: identificador de interfaz.
- **length**: el número de bytes en aData.
- **aData**: búfer de datos que contiene el marco de datos de PPP.

### <a name="return-values"></a>Valores devueltos

**None**

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```