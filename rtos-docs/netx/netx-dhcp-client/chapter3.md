---
title: 'Capítulo 3: Descripción de los servicios de cliente DHCP de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios DHCP de Azure RTOS NetX (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815250"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a>Capítulo 3: Descripción de los servicios de cliente DHCP de Azure RTOS NetX

Este capítulo contiene una descripción de todos los servicios DHCP de Azure RTOS NetX (enumerados a continuación) en orden alfabético.

En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nx_dhcp_create**: *crea una instancia de DHCP*.

- **nx_dhcp_clear_broadcast_flag**: borra la marca de difusión en mensajes de cliente.

- **nx_dhcp_delete**: *elimina una instancia de DHCP*.

- **nx_dhcp_decline**: envía un *mensaje de rechazo al servidor*.

- **nx_dhcp_force_renew**: *envía un mensaje para forzar la renovación*.

- **nx_dhcp_packet_pool_set**: *establece el grupo de paquetes de cliente DHCP*.

- **nx_dhcp_release**: envía un *mensaje de liberación al servidor*.

- **nx_dhcp_reinitialize**: *borra los parámetros de red de cliente DHCP*.

- **nx_dhcp_request_client_ip**: *especifica una dirección IP concreta*.

- **nx_dhcp_send_request**: *envía un mensaje DHCP al servidor*.

- **nx_dhcp_server_address_get**: *recupera la dirección del servidor DHCP del cliente DHCP*.

- **nx_dhcp_set_interface_index**: *especifica la interfaz de red de cliente*.

- **nx_dhcp_start**: *inicia el procesamiento de DHCP*.

- **nx_dhcp_state_change_notify**: *notifica a la aplicación el cambio de estado de DHCP*.

- **nx_dhcp_stop**: *detiene el procesamiento de DHCP*.

- **nx_dhcp_user_option_retrieve**: *recupera la opción DHCP*.

- **nx_dhcp_user_option_convert**: *convierte cuatro bytes a ULONG*.

Servicios de cliente DHCP específicos de la interfaz:

- **nx_dhcp_interface_clear_broadcast_flag**: *borra la marca de difusión en mensajes de cliente en la interfaz especificada*.

- **nx_dhcp_interface_enable**: *habilita la interfaz para ejecutar DHCP en la interfaz especificada*.

- **nx_dhcp_interface_disable**: *deshabilita la interfaz para ejecutar DHCP en la interfaz especificada*.

- **nx_dhcp_interface_decline**: *envía un mensaje de rechazo al servidor en la interfaz especificada*.

- **nx_dhcp_interface_force_renew**: *envía un mensaje para forzar la renovación en la interfaz especificada*.

- **nx_dhcp_interface_reinitialize**: *borra parámetros de red de cliente DHCP en la interfaz especificada*.

- **nx_dhcp_interface_release**: *envía un mensaje de liberación al servidor en la interfaz especificada*.

- **nx_dhcp_interface_request_client_ip**: *especifica una dirección IP concreta en la interfaz especificada*.

- **nx_dhcp_interface_send_request**: *envía un mensaje DHCP al servidor en la interfaz especificada*.

- **nx_dhcp_interface_server_address_get**: *obtiene la dirección IP del servidor DHCP en la interfaz especificada*.

- **nx_dhcp_interface_start**: *inicia el procesamiento de cliente DHCP en la interfaz especificada*.

- **nx_dhcp_interface_stop**: *detiene el procesamiento de cliente DHCP en la interfaz especificada*.

- **nx_dhcp_interface_state_change_notify**: *establece la función de devolución de llamada cuando el estado de DHCP cambia en la interfaz especificada*.

- **nx_dhcp_interface_user_option_retrieve**: *recupera la opción DHCP especificada en la interfaz especificada*.

Servicios de cliente DHCP si se define NX_DHCP_CLIENT_RESORE_STATE:

- **nx_dhcp_resume**: *reanuda el estado del cliente DHCP previamente establecido*.

- **nx_dhcp_suspend**: *suspende el procesamiento del estado del cliente DHCP*.

- **nx_dhcp_client_get_record**: *crea un registro del estado del cliente DHCP*.

- **nx_dhcp_client_restore_record**: *restaura un registro guardado previamente en el cliente DHCP*.

- **nx_dhcp_client_update_time_remaining**: *actualiza el tiempo restante en el estado actual de DHCP*.

Servicios de cliente DHCP si se define NX_DHCP_CLIENT_RESORE_STATE:

- **nx_dhcp_client_interface_get_record**: *crea un registro del estado del cliente DHCP en la interfaz especificada*.

- **nx_dhcp_client_interface_restore_record**: *crea un registro guardado previamente del estado del cliente DHCP en la interfaz especificada*.

- **nx_dhcp_client_interface_update_time_remaining**: *actualiza el tiempo restante en el estado DHCP actual en la interfaz especificada*.

## <a name="nx_dhcp_create"></a>nx_dhcp_create

Crea una instancia de DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de DHCP para la instancia de IP creada anteriormente. De forma predeterminada, la interfaz principal está habilitada para ejecutar DHCP. La entrada del nombre, aunque no se usa en la implementación de cliente DHCP de NetX, debe seguir los criterios de la RFC 1035 para los nombres de hosts. La longitud total no debe superar los 255 caracteres, las etiquetas separadas por puntos deben comenzar con una letra y terminar con una letra o un número, y pueden contener guiones pero no otros caracteres no alfanuméricos.

Si la aplicación desea ejecutar otra interfaz de DHCP registrada con la instancia de IP (mediante *nx_ip_interface_attach*), puede llamar a *nx_dhcp_set_interface_index* para ejecutar DHCP solo en esa interfaz o *nx_dhcp_interface_enable* para ejecutar DHCP también en esa interfaz. Consulte la descripción de estos servicios para obtener más información.

> [!NOTE]
> La aplicación debe asegurarse de que la carga del grupo de paquetes del cliente DHCP pueda admitir el tamaño mínimo del mensaje DHCP especificado en la sección 2 de la RFC 2131 (548 bytes de datos de mensajes DHCP más UDP, IP y los encabezados de trama de la red física).

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.  
- **ip_ptr** Puntero a la instancia de IP creada anteriormente.  
- **name_ptr** Puntero al nombre de host de la instancia de DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) DHCP creado correctamente.

- **NX_DHCP_INVALID_NAME** (0xA8) Nombre de host no válido.

- **NX_DHCP_INVALID_PAYLOAD** (0x9C) Carga demasiado pequeña para el mensaje DHCP.

- NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.

### <a name="allowed-from"></a>Permitido desde

**Subprocesos,** inicialización

### <a name="example"></a>Ejemplo

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a>nx_dhcp_interface_enable

Habilita la interfaz especificada para ejecutar DHCP 

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio permite que la interfaz especificada ejecute DHCP. De forma predeterminada, la interfaz principal está habilitada para el cliente DHCP. En este punto, se puede iniciar DHCP en esta interfaz llamando a *nx_dhcp_interface_start* o hacerlo en todas las interfaces habilitadas con *nx_dhcp_start*.

Tenga en cuenta que la aplicación debe registrar primero esta interfaz con la instancia de IP mediante *nx_ip_interface_attach.*

Además, debe haber un “registro” de interfaz de cliente DHCP disponible para agregar esta interfaz a la lista de interfaces habilitadas. De forma predeterminada NX_DHCP_CLIENT_MAX_RECORDS se define como 1. Establezca esta opción en el número máximo de interfaces que se espera que ejecute el cliente DHCP simultáneamente. Normalmente NX_DHCP_CLIENT_MAX_RECORDS será igual a NX_MAX_PHYSICAL_INTERFACES; sin embargo, si un dispositivo tiene más interfaces físicas de las que espera ejecutar el cliente DHCP, puede ahorrar memoria si establece NX_DHCP_CLIENT_MAX_RECORDS en un valor inferior a ese número. No hay una asignación uno a uno de las interfaces físicas con los registros de la interfaz de cliente DHCP.

La diferencia entre este servicio y *nx_dhcp_set_interface_index* es que el segundo establece una única interfaz para ejecutar DHCP, mientras que este servicio simplemente agrega la interfaz especificada a la lista de interfaces de cliente habilitadas para DHCP.

Para deshabilitar una interfaz de DHCP, la aplicación puede llamar al servicio *nx_dhcp_interface_disable*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.  

- **interface_index** Índice de interfaz para habilitar DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) DHCP habilitado correctamente.

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No hay ningún registro disponible para poder habilitar otra interfaz para DHCP.

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interfaz habilitada para DHCP.

- NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a>nx_dhcp_interface_disable

Deshabilita la interfaz especificada para ejecutar DHCP 

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio impide que la interfaz especificada ejecute DHCP. Reinicializa el cliente DHCP en esta interfaz.

Para reiniciar el cliente DHCP, la aplicación debe volver a habilitar la interfaz mediante *nx_dhcp_interface_enable* y reiniciar DHCP llamando a *nx_dhcp_interface_start*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.  

- **interface_index** Índice de interfaz para deshabilitar DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) DHCP creado correctamente.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.

- NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a>nx_dhcp_clear_broadcast_flag

Establece la marca de difusión de DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a>Descripción

Este servicio establece o borra la marca de difusión del encabezado del mensaje DHCP de todas las interfaces habilitadas para DHCP. En el caso de algunos mensajes DHCP (por ejemplo, DISCOVER), la marca de difusión se establece en “difundir” porque el cliente no tiene una dirección IP.

__clear_flag__


- **NX_TRUE** La marca de difusión se borra (solicitud de respuesta de unidifusión).

- **NX_TRUE** La marca de difusión se establece (solicitud de respuesta de unidifusión).

Este servicio está dirigido a los clientes DHCP que deben pasar por un enrutador para llegar al servidor DHCP, donde el enrutador rechaza el reenvío de mensajes de difusión.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.  

- **clear_flag** Valor en el que se va a establecer la marca de difusión.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Marca de difusión actualizada correctamente.

- NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a>nx_dhcp_interface_clear_broadcast_flag

Establece o borra la marca de difusión en la interfaz especificada

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a>Descripción

Este servicio permite que la aplicación host de cliente DHCP establezca o borre la marca de difusión en los mensajes de cliente DHCP en el servidor DHCP de la interfaz especificada. Para obtener más información, consulte **nx_dhcp_clear_broadcast_flag**.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.

- **interface_index** Índice de la interfaz para establecer la marca de difusión.  

- **clear_flag** Valor en el que se va a establecer la marca de difusión.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Marca de difusión actualizada correctamente.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.

- NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a>nx_dhcp_delete

Elimina una instancia de DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente DHCP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) DHCP eliminado correctamente.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a>nx_dhcp_ force_renew

Envía un mensaje para forzar la renovación 

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Descripción

Este servicio permite que la aplicación host envíe un mensaje para forzar la renovación en todas las interfaces habilitadas para DHCP. El cliente DHCP debe estar en un estado ENLAZADO. Esta función establece el estado en RENOVAR, de modo que el cliente DHCP intente renovar antes de que venza el tiempo de espera de T1.

Si quiere enviar un mensaje para forzar la renovación en una interfaz específica cuando hay varias interfaces habilitadas para DHCP, use *nx_dhcp_interface_force_renew*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje para forzar la renovación enviado correctamente.  

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a>nx_dhcp_interface_force_renew

Envía un mensaje para forzar la renovación en la interfaz especificada

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio permite que la aplicación host envíe un mensaje para forzar la renovación en la interfaz de entrada, siempre y cuando esa interfaz se haya habilitado para DHCP (consulte *nx_dhcp_interface_enable*). El cliente DHCP de la interfaz especificada debe estar en un estado ENLAZADO. Esta función establece el estado en RENOVAR, de modo que el cliente DHCP intente renovar antes de que venza el tiempo de espera de T1.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje para forzar la renovación enviado correctamente.  

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.

- NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a>nx_dhcp_packet_pool_set

Establece el grupo de paquetes del cliente DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Descripción

Este servicio permite que la aplicación cree el grupo de paquetes de cliente DHCP pasando un puntero a un grupo de paquetes creado previamente en esta llamada de servicio. Para usar esta característica, la aplicación host debe definir NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL. Una vez definido el parámetro, el servicio *nx_dhcp_create* no creará el grupo de paquetes de cliente. Tenga en cuenta que se recomienda que la aplicación use los valores predeterminados para la carga del grupo de paquetes de cliente DHCP, definido como NX_DHCP_PACKET_PAYLOAD en *nx_dhcp.h* al crear el grupo de paquetes.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.  

- **packet_pool_ptr** Puntero al grupo de paquetes creado previamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Grupo de paquetes del cliente DHCP establecido.

- **NX_NOT_ENABLED** (0x14) El servicio no está habilitado.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_DHCP_INVALID_PAYLOAD (0x9C) La carga es demasiado pequeña.

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a>nx_dhcp_request_client_ip

Establece la dirección IP solicitada para la instancia de DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a>Descripción

Este servicio establece la dirección IP que el cliente DHCP debe solicitar al servidor DHCP en la primera interfaz habilitada para DHCP en el registro del cliente DHCP. Si se establece la marca *skip_discover_message*, el cliente DHCP omite el mensaje de detección y envía un mensaje de solicitud.

Para establecer la solicitud de una dirección IP específica para mensajes DHCP en una interfaz concreta, use el servicio *nx_dhcp_interface_request_client_ip*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.  

- **client_ip_address** Dirección IP que se va a solicitar del servidor DHCP.

- **skip_discover_message** Si es verdadero, el cliente DHCP envía un mensaje de solicitud.  
Si es falso, envía el mensaje de detección.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) La dirección IP solicitada se ha establecido.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.

- NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.
 
### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a>nx_dhcp_interface_request_client_ip

Establece la dirección IP solicitada para la instancia de DHCP en la interfaz especificada

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a>Descripción

Este servicio establece la dirección IP que el cliente DHCP debe solicitar al servidor DHCP en la interfaz especificada, si dicha interfaz está habilitada para DHCP (consulte *nx_dhcp_interface_enable*). Si se establece la marca *skip_discover_message*, el cliente DHCP omite el mensaje de detección y envía un mensaje de solicitud.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.

- **Interface_index** Índice de la interfaz en la que se va a solicitar la dirección IP.

- **client_ip_address** Dirección IP que se va a solicitar del servidor DHCP.

- **skip_discover_message** Si es verdadero, el cliente DHCP envía el mensaje de solicitud; de lo contrario, envía el mensaje de detección.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) La dirección IP solicitada se ha establecido.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.

- NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.


### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a>nx_dhcp_reinitialize

Borra los parámetros de red del cliente DHCP 

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Descripción

Este servicio borra los parámetros de red de la aplicación host (dirección IP, dirección de red y máscara de red) y borra el estado del cliente DHCP en todas las interfaces habilitadas para DHCP. Se usa en combinación con *nx_dhcp_stop* y *nx_dhcp_start* para “reiniciar” la máquina de estados de DHCP: 

nx_dhcp_stop(&my_dhcp);  
nx_dhcp_reinitialize(&my_dhcp);  
nx_dhcp_start(&my_dhcp);


Para reinicializar el cliente DHCP en una interfaz específica cuando hay varias interfaces habilitadas para DHCP, use el servicio *nx_dhcp_interface_reinitialize*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) DHCP reinicializado correctamente. 

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a>nx_dhcp_interface_reinitialize

Borra los parámetros de red del cliente DHCP en la interfaz especificada 

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio borra los parámetros de red (dirección IP, dirección de red y máscara de red) en la interfaz especificada si dicha interfaz está habilitada para DHCP (consulte *nx_dhcp_interface_enable*). Consulte *nx_dhcp_reinitialize* para obtener más información.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

- **interface_index** Índice de interfaz para reinicializar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Interfaz reinicializada correctamente.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a>nx_dhcp_release

Libera la dirección IP concedida

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Descripción

Este servicio libera la dirección IP obtenida de un servidor DHCP mediante el envío del mensaje RELEASE a dicho servidor. Seguidamente, reinicializa el cliente DHCP. Este servicio se aplica a todas las interfaces habilitadas para DHCP.

La aplicación puede reiniciar el cliente DHCP llamando a *nx_dhcp_start*.

Para volver a liberar una dirección en el servidor DHCP en una interfaz específica, use el servicio *nx_dhcp_interface_release*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) DHCP liberado correctamente.  

- **NX_DHCP_NOT_BOUND** (0x94) No se ha concedido la dirección IP, por lo que no se puede liberar.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a>nx_dhcp_interface_release

Libera la dirección IP en la interfaz especificada

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio libera la dirección IP obtenida de un servidor DHCP en la interfaz especificada y reinicializa el cliente DHCP. El cliente DHCP puede reiniciarse mediante una llamada a *nx_dhcp_start*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) DHCP liberado correctamente.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.

- **NX_DHCP_NOT_BOUND** (0x94) No se ha concedido la dirección IP, por lo que no se puede liberar.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a>nx_dhcp_decline

Rechaza la dirección IP del servidor DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Descripción

Este servicio rechaza una dirección IP concedida desde el servidor DHCP en todas las interfaces habilitadas para DHCP. Si se define NX_DHCP_CLIENT_ SEND_ ARP_PROBE, el cliente DHCP enviará un mensaje de rechazo si detecta que la dirección IP ya está en uso. Consulte **Sondeos ARP** en el capítulo 1 para obtener más información sobre la configuración de sondeo ARP en el cliente DHCP de NetX.

La aplicación puede usar este servicio para rechazar su dirección IP si detecta que la dirección se está usando por otros medios.

Este servicio reinicializa el cliente DHCP para que se pueda reiniciar mediante una llamada a *nx_dhcp_start*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Rechazo enviado correctamente.  

- **NX_DHCP_NOT_STARTED** (0x96) No se ha iniciado la instancia de DHCP.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a>nx_dhcp_interface_decline

Rechaza la dirección IP del servidor DHCP en la interfaz especificada

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio envía el mensaje DECLINE al servidor para rechazar una dirección IP asignada por el servidor DHCP. También reinicializa el cliente DHCP. Consulte *nx_dhcp_decline* para obtener más información.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

- **Interface_index** Índice de la interfaz para rechazar la dirección IP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de rechazo de DHCP enviado.  

- **NX_DHCP_NOT_BOUND** (0x94) Cliente DHCP no enlazado.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a>nx_dhcp_send_request

Envía un mensaje DHCP al servidor

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a>Descripción

Este servicio envía el mensaje DHCP especificado al servidor DHCP en la primera interfaz habilitada para DHCP que se encuentra en el registro del cliente DHCP. Para enviar un mensaje RELEASE o DECLINE, la aplicación debe utilizar los servicios *nx_dhcp [_interface] _release*() o *nx_dhcp_interface_decline ()* , respectivamente.

El cliente DHCP debe iniciarse para usar este servicio, salvo para enviar el tipo de mensaje INFORM_REQUEST.

> [!NOTE] 
> Este servicio no está destinado a que la aplicación host “impulse” la máquina de estados del cliente DHCP.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.  

- **dhcp_message_type** Solicitud de mensaje (definida en *nx_dhcp.h*)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje DHCP enviado.  

- **NX_DHCP_NOT_STARTED** (0x96) Índice de interfaz no válido.

- **NX_DHCP_INVALID_MESSAGE** (0x9B) Tipo de mensaje no válido para enviar.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a>nx_dhcp_interface_send_request

Envía un mensaje DHCP al servidor en una interfaz específica

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a>Descripción

Este servicio envía un mensaje al servidor DHCP en la interfaz especificada si esa interfaz está habilitada para DHCP. Para enviar un mensaje RELEASE o DECLINE, la aplicación debe utilizar los servicios *nx_dhcp [_interface] _release*() o *nx_dhcp_interface_decline ()* , respectivamente.

El cliente DHCP debe iniciarse para usar este servicio, salvo para enviar el tipo de mensaje INFORM_REQUEST.

Este servicio no está destinado a que la aplicación host “impulse” la máquina de estados del cliente DHCP.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.

- **Interface_index** Índice de la interfaz a la que se va a enviar el mensaje.  

- **dhcp_message_type** Solicitud de mensaje (definida en *nx_dhcp.h*).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje DHCP enviado.  

- **NX_DHCP_NOT_STARTED** (0x96) Índice de interfaz no válido.

- **NX_DHCP_INVALID_MESSAGE** (0x9B) Tipo de mensaje no válido para enviar.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a>nx_dhcp_server_address_get

Obtiene la dirección IP del servidor DHCP del cliente DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a>Descripción

Este servicio recupera la dirección IP del servidor DHCP del cliente DHCP en la primera interfaz habilitada para DHCP que se encuentra en el registro del cliente DHCP. El autor de la llamada solo puede utilizar este servicio después de que el cliente DHCP se haya enlazado a una dirección IP asignada por el servidor DHCP. La aplicación host puede usar el servicio *nx_ip_status_check* para comprobar que la dirección IP está establecida o usar *nx_dhcp_state_change_notify* y consultar si el estado del cliente DHCP es NX_DHCP_STATE_BOUND. Consulte *nx_dhcp_state_change_notify* para obtener información sobre cómo establecer la función de devolución de llamada de cambio de estado.

Para buscar el servidor DHCP en una interfaz específica cuando hay varias interfaces habilitadas para el cliente DHCP, use el servicio *nx_dhcp_interface_server_address_get*

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.

- **server_address** Puntero a la dirección IP del servidor.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Dirección del servidor DHCP devuelta.

- NX_PTR_ERROR (0x16) El puntero de entrada no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a>nx_dhcp_interface_server_address_get

Obtiene la dirección IP del servidor DHCP del cliente DHCP en la interfaz especificada

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a>Descripción

Este servicio recupera la dirección IP del servidor DHCP del cliente DHCP en la interfaz especificada si dicha interfaz está habilitada para DHCP. El cliente DHCP debe estar en un estado ENLAZADO. Después de iniciar el cliente DHCP en esa interfaz, la aplicación host puede usar el servicio *nx_ip_status_check* para comprobar que la dirección IP está establecida o bien usar la devolución de llamada de cambio de estado del cliente DHCP y consultar si el estado del cliente DHCP es NX_DHCP_STATE_BOUND. Consulte *nx_dhcp_state_change_notify* para obtener más información sobre cómo establecer la función de devolución de llamada de cambio de estado.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.

- **Interface_index** Índice de la interfaz para obtener la dirección IP.  

- **server_address** Puntero a la dirección IP del servidor.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Dirección del servidor DHCP devuelta.

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No hay interfaces habilitadas para DHCP.

- **NX_DHCP_NOT_BOUND** (0x94) Cliente DHCP no enlazado.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a>nx_dhcp_set_interface_index

Establece la interfaz de red para la instancia de DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a>Descripción

Este servicio establece la interfaz de red para que la instancia de DHCP se conecte al servidor DHCP cuando se ejecuta el cliente DHCP configurado para una sola interfaz de red.

De forma predeterminada, el cliente DHCP se ejecuta en la interfaz principal. Para ejecutar DHCP en un servicio secundario, use este servicio para establecer la interfaz secundaria como la interfaz de cliente DHCP. La aplicación debe registrar previamente la interfaz especificada en la instancia de IP mediante el servicio de *nx_ip_interface_attach*.

Tenga en cuenta que este servicio está pensado para las aplicaciones que tienen previsto ejecutar el cliente DHCP en una sola interfaz. Para ejecutar DHCP en varias interfaces, consulte *nx_dhcp_interface_enable* para obtener más información.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero al bloque de control de DHCP.  

- **index** Índice de la interfaz de red del dispositivo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) La interfaz se ha establecido correctamente.

- **NX_INVALID_INTERFACE** (0x4C) Interfaz de red no válida.

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interfaz habilitada para DHCP.

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No hay ningún registro disponible para otro.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a>nx_dhcp_start

Inicia el procesamiento de DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia el procesamiento de DHCP en todas las interfaces habilitadas para DHCP. De forma predeterminada, la interfaz principal se habilita para DHCP cuando la aplicación llama a *nx_dhcp_create.*

Para comprobar si la instancia de IP está enlazada a una dirección IP en la interfaz de cliente DHCP, use *nx_ip_status_check* para ver la confirmación de que la dirección IP es válida.

Si hay otras interfaces que ya ejecutan DHCP, no se verán afectadas por este servicio.

Para iniciar DHCP en una interfaz específica cuando hay varias interfaces habilitadas, utilice el servicio *nx_dhcp_interface_start*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) DHCP iniciado correctamente.  

- **NX_DHCP_ALREADY_STARTED** (0x93) DHCP ya se ha iniciado.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a>nx_dhcp_interface_start

Inicia el procesamiento de DHCP en la interfaz especificada

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio inicia el procesamiento de DHCP en la interfaz especificada si dicha interfaz está habilitada para DHCP. Consulte *nx_dhcp_interface_enable*() para obtener más información sobre cómo habilitar una interfaz para DHCP. De forma predeterminada, la interfaz principal se habilita para DHCP cuando la aplicación llama a *nx_dhcp_create.*

Si no hay otras interfaces que ejecuten el cliente DHCP, este servicio iniciará o reanudará el subproceso del cliente DHCP y (re)activará el temporizador del cliente DHCP.  
  
La aplicación debe usar *nx_ip_status_check* para comprobar si se obtiene una dirección IP.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

- **Interface_index** Índice en el que se va a iniciar el cliente DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) DHCP iniciado correctamente.  

- **NX_DHCP_ALREADY_STARTED** (0x93) Ya se ha iniciado la instancia de DHCP.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a>nx_dhcp_state_change_notify

Establece la función de devolución de llamada de cambio de estado de DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a>Descripción

Este servicio registra la función de devolución de llamada especificada “dhcp_state_change_notify” para notificar a una aplicación los cambios de estado de DHCP. La función de devolución de llamada proporciona el estado al que ha pasado el cliente DHCP.

A continuación se indican los valores asociados a los distintos estados de DHCP:

| Estado                             | Value |
|-----------------------------------|-------|
| NX\_DHCP\_STATE\_BOOT             | 1     |
| NX\_DHCP\_STATE\_INIT             | 2     |
| NX\_DHCP\_STATE\_SELECTING        | 3     |
| NX\_DHCP\_STATE\_REQUESTING       | 4     |
| NX\_DHCP\_STATE\_BOUND            | 5     |
| NX\_DHCP\_STATE\_RENEWING         | 6     |
| NX\_DHCP\_STATE\_REBINDING        | 7     |
| NX_DHCP_STATE_FORCERENEW          | 8     |
| NX\_DHCP\_STATE\_ADDRESS\_PROBING | 9     |


### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

- **dhcp_state_change_notify** Puntero de función de devolución de llamada de cambio de estado

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.  

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a>nx_dhcp_interface_state_change_notify

Establece la función de devolución de llamada de cambio de estado DHCP en la interfaz especificada

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a>Descripción

Este servicio registra la función de devolución de llamada especificada para notificar a una aplicación los cambios de estado de DHCP. Los argumentos de entrada de la función de devolución de llamada son el índice de interfaz y el estado al que el cliente DHCP ha pasado en esa interfaz.

Para obtener más información sobre las funciones de cambio de estado, consulte *nx_dhcp_state_change_notify*().

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

- **dhcp_interface_state_change_notify** Puntero de función de devolución de llamada de la aplicación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.  

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a>nx_dhcp_stop

Detiene el procesamiento de DHCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene el procesamiento de DHCP en todas las interfaces que han iniciado el procesamiento de DHCP. Si no hay ninguna interfaz que procese DHCP, este servicio suspenderá el subproceso de cliente DHCP e inactivará el temporizador de cliente DHCP.

Para detener DHCP en una interfaz específica si hay varias interfaces habilitadas para DHCP, use el servicio *nx_dhcp_interface_stop*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) DHCP detenido correctamente.

- **NX_DHCP_NOT_STARTED** (0x96) No se ha iniciado la instancia de DHCP.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a>nx_dhcp_interface_stop

Detiene el procesamiento de DHCP en la interfaz especificada

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio detiene el procesamiento de DHCP en la interfaz especificada si DHCP ya está iniciado. Si no hay ninguna otra interfaz que ejecute DHCP, se suspenden el subproceso y el temporizador de DHCP.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

- **Interface_index** Interfaz en la que se va a detener el procesamiento de DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) DHCP detenido correctamente.

- **NX_DHCP_NOT_STARTED** (0x96) No se ha iniciado DHCP.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a>nx_dhcp_user_option_retrieve

Recupera una opción DHCP de la última respuesta del servidor

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Descripción

Este servicio recupera la opción DHCP especificada del búfer de opciones DHCP de la primera interfaz habilitada para DHCP encontrada en el registro del cliente DHCP. Si se realiza correctamente, los datos de la opción se copian en el búfer especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.  

- **request_option** Opción DHCP, tal y como se especifica en las RFC. Consulte la opción NX_DHCP_OPTION en *nx_dhcp.h*.

- **destination_ptr** Puntero al destino de la cadena de respuesta.  

- **destination_size** Puntero al tamaño del destino y, en la devolución, al destino para colocar el número de bytes devueltos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Opción recuperada correctamente.  

- **NX_DHCP_NOT_BOUND** (0x94) Cliente DHCP no enlazado.

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No hay interfaces habilitadas para DHCP.

- **NX_DHCP_DEST_TO_SMALL** (0x95) El destino es demasiado pequeño para mantener la respuesta.

- **NX_DHCP_PARSE_ERROR** (0x97) No se encontró la opción DHCP en la respuesta del servidor.

- NX_PTR_ERROR (0x16) El puntero de entrada no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a>nx_dhcp_interface_user_option_retrieve

Recupera una opción de DHCP de la última respuesta del servidor en la interfaz especificada

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Descripción

Este servicio recupera la opción DHCP especificada del búfer de opciones DHCP en la interfaz especificada, si dicha interfaz está habilitada para DHCP. Si se realiza correctamente, los datos de la opción se copian en el búfer especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

- **Interface_index** Índice en el que se va a recuperar la opción especificada.  

- **request_option** Opción DHCP, tal y como se especifica en las RFC. Consulte la opción NX_DHCP_OPTION en *nx_dhcp.h*.  

- **destination_ptr** Puntero al destino de la cadena de respuesta.  

- **destination_size** Puntero al tamaño del destino y, en la devolución, al destino para colocar el número de bytes devueltos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Opción recuperada correctamente.  

- **NX_DHCP_NOT_BOUND** (0x94) Dirección IP no asignada.

- **NX_DHCP_DEST_TO_SMALL** (0x95) El búfer es demasiado pequeño.

- **NX_DHCP_PARSE_ERROR** (0x97) No se encontró la opción DHCP en la respuesta del servidor.

- NX_PTR_ERROR (0x16) El puntero DHCP no es válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.

- NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a>nx_dhcp_user_option_convert

Convierte cuatro bytes en ULONG

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a>Descripción

Este servicio convierte los cuatro caracteres a los que apunta “option_string_ptr” en un valor Long sin signo. Es especialmente útil cuando hay presentes direcciones IP.

### <a name="input-parameters"></a>Parámetros de entrada

- **option_string_ptr** Puntero a la cadena de opción recuperada previamente.

### <a name="return-values"></a>Valores devueltos

- **Value** Valor de los primeros cuatro bytes.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a>nx_dhcp_user_option_add_callback_set

Establece la función de devolución de llamada para agregar opciones proporcionadas por el usuario

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a>Descripción

Este servicio registra la función de devolución de llamada especificada para agregar las opciones proporcionadas por el usuario.

Si se especifica la función de devolución de llamada, las aplicaciones pueden agregar al paquete opciones proporcionadas por el usuario mediante iface_index y message_type.

> [!NOTE]
> En la rutina del usuario. Las aplicaciones deben seguir el formato de las opciones de DHCP cuando se agregan opciones proporcionadas por el usuario. El tamaño total de las opciones de usuario debe ser menor o igual que user_option_length y actualizar user_option_length como la longitud de las opciones reales. Devuelve NX_TRUE si se agregan opciones correctamente; de lo contrario, devuelve NX_FALSE.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.

- **dhcp_user_option_add** Puntero a la opción Agregar función de usuario.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.

- NX_PTR_ERROR (0x16) Puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
