---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios de Azure RTOS NetX Duo en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 85617aadab7f484a4f4e467fd13f815f4d8b5609
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815417"
---
# <a name="chapter-4---description-of-azure-rtos-netx-duo-services"></a>Capítulo 4: Descripción de los servicios de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios de Azure RTOS NetX Duo en orden alfabético. Los nombres de los servicios están diseñados de modo que todos los servicios similares estén agrupados. Por ejemplo, todos los servicios de ARP se encuentran al principio de este capítulo. 

Se han incorporado numerosos servicios nuevos en NetX Duo para admitir operaciones y protocolos basados en IPv6. Los servicios habilitados para IPv6 de NetX Duo tienen el prefijo ***nxd**,* que indica que están diseñados para la operación de la pila dual IPv4 e IPv6.

Los servicios existentes en NetX son totalmente compatibles con NetX Duo. Las aplicaciones de NetX se pueden migrar a NetX Duo con un esfuerzo mínimo de portabilidad.

> [!NOTE]
> *Tenga en cuenta que está disponible una API de sockets compatible con BSD para el código de aplicación heredado que no puede sacar el máximo partido de la API de alto rendimiento de NetX Duo. Consulte el Apéndice D para más información sobre la API de sockets compatible con BSD*.

En la sección "Valores devueltos" de cada descripción, los valores en **NEGRITA** no se ven afectados por la opción NX_DISABLE_ERROR_CHECKING que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados. Las secciones "Permitido desde" indican desde dónde se puede llamar a cada servicio de NetX.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate   
Invalidar todas las entradas dinámicas de la memoria caché de ARP

### <a name="prototype"></a>Prototipo     

```c
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción   
Este servicio invalida todas las entradas de ARP dinámicas que se encuentran actualmente en la memoria caché de ARP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) memoria caché de ARP invalidada correctamente.
- **NX_NOT_ENABLED**: (0x14) ARP no está habilitado.
- **NX_PTR_ERROR**: (0x07) Dirección IP no válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde   
Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible    
No

### <a name="example"></a>Ejemplo

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);

/* If status is NX_SUCCESS the dynamic ARP entries were
   successfully invalidated. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set  
Establecer entrada de ARP dinámica

### <a name="prototype"></a>Prototipo  

```c
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);  
```

### <a name="description"></a>Descripción    
Este servicio asigna una entrada dinámica de la memoria caché de ARP y configura la dirección IP especificada para la asignación de la dirección física. Si se especifica una dirección física establecida en cero, se envía una solicitud de ARP real a la red para que se resuelva la dirección física. Tenga en cuenta también que esta entrada se quitará si está activa la caducidad de ARP o si se ha agotado la memoria caché de ARP y se trata de la entrada de ARP usada menos recientemente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP que se va a asignar.
- **physical_msw**: 16 bits superiores (del 47 al 32) de la dirección física.
- **physical_lsw**: 32 bits inferiores (del 31 al 0) de la dirección física.

### <a name="return-values"></a>Valores devueltos    

- **NX_SUCCESS**: (0x00) Entrada dinámica de ARP establecida correctamente.
- **NX_NO_MORE_ENTRIES**: (0x17) No hay más entradas de ARP disponibles en la memoria caché de ARP.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.
- **NX_PTR_ERROR**: (0x07) Puntero a la instancia de IP no válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde    
Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible    
No

### <a name="example"></a>Ejemplo

```c
/* Setup a dynamic ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
                                  0x1022, 0x1234);

/* If status is NX_SUCCESS, there is now a dynamic mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   10:22:00:00:12:34. */
```
### <a name="see-also"></a>Consulte también 

- nx_arp_dynamic_entries_invalidate
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_enable"></a>nx_arp_enable  
Habilitar el protocolo de resolución de direcciones (ARP)

### <a name="prototype"></a>Prototipo    

```c
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory,
    ULONG arp_cache_size);
```

### <a name="description"></a>Descripción

Este servicio inicializa el componente de ARP de NetX para la instancia de IP específica. La inicialización de ARP incluye la configuración de la memoria caché de ARP y varias rutinas de procesamiento de ARP necesarias para enviar y recibir mensajes de ARP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **arp_cache_memory**: puntero al área de memoria en la que se va a colocar la memoria caché de ARP.
- **arp_cache_size**: cada entrada de ARP tiene 52 bytes; el número total de entradas de ARP es, por lo tanto, el tamaño dividido entre 52.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) ARP habilitado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de memoria de caché o IP no válidos.
- **NX_SIZE_ERROR**: (0x09) La memoria caché de ARP proporcionada por el usuario es demasiado pequeña.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_ALREADY_ENABLED**: (0x15) Este componente ya se ha habilitado.

### <a name="allowed-from"></a>Permitido desde   
Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible  
No

### <a name="example"></a>Ejemplo

```c
/* Enable ARP and supply 1024 bytes of ARP cache memory for
   previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);

/* If status is NX_SUCCESS, ARP was successfully enabled for this IP
instance.*/
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_entry_delete"></a>nx_arp_entry_delete   
Eliminar una entrada de ARP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_arp_entry_delete(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>Descripción

Este servicio quita una entrada de ARP para un dirección IP determinada de su tabla de ARP interna de IP.

### <a name="parameters"></a>Parámetros  

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: se debe eliminar la entrada de ARP con la dirección IP especificada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) ARP habilitado correctamente.
- **NX_ENTRY_NOT_FOUND**: (0x16) No se puede encontrar ninguna entrada con la dirección IP especificada.
- **NX_PTR_ERROR** (0x07) Puntero de memoria de caché o IP no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_IP_ADDRESS_ERROR**: (0x21) La dirección IP especificada no es válida.

### <a name="allowed-from"></a>Permitido desde  
Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible  
No

### <a name="example"></a>Ejemplo

```c
/* Delete the ARP entry with the IP address 1.2.3.4. */
status = nx_arp_entry_delete(&ip_0, IP_ADDRESS(1, 2, 3, 4));

/* If status is NX_SUCCESS, ARP entry with the specified IP address
   is deleted.*/
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send   
Enviar solicitud ARP gratuita

### <a name="prototype"></a>Prototipo  

```c
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler)(NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```                               
### <a name="description"></a>Descripción

Este servicio recorre todas las interfaces físicas para transmitir solicitudes ARP gratuitas, siempre y cuando la dirección IP de la interfaz sea válida. Si posteriormente se recibe una respuesta de ARP, se llama al controlador de respuesta proporcionado para procesar la respuesta a la solicitud ARP gratuita.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **response_handler**: puntero a la función de control de la respuesta. Si se proporciona NX_NULL, se omiten las respuestas.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Envío correcto de solicitud ARP gratuita.
- **NX_NO_PACKET**: (0x01) No hay ningún paquete disponible.
- **NX_NOT_ENABLED**: (0x14) ARP no está habilitado.
- **NX_IP_ADDRESS_ERROR**: (0x21) La dirección IP actual no es válida.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully
   sent. */
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find
Buscar la dirección de hardware física para una dirección IP determinada

### <a name="prototype"></a>Prototipo  

```c
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG *physical_msw,
    ULONG *physical_lsw);
```
### <a name="description"></a>Descripción

Este servicio intenta encontrar una dirección de hardware física en la memoria caché de ARP que está asociada con la dirección IP proporcionada.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP que se va a buscar.
- **physical_msw**: puntero a la variable para devolver los 16 bits superiores (del 47 al 32) de la dirección física.
- **physical_lsw**: puntero a la variable para devolver los 32 bits inferiores (del 31 al 0) de la dirección física.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se encontró correctamente la dirección de hardware de ARP.
- **NX_ENTRY_NOT_FOUND**: (0x16) No se encontró la asignación en la memoria caché de ARP.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.
- **NX_PTR_ERROR**: (0x07) Puntero de memoria o IP no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Search for the hardware address associated with the IP address of
   1.2.3.4 in the ARP cache of the previously created IP
   Instance 0. */
status = nx_arp_hardware_address_find(&ip_0, IP_ADDRESS(1,2,3,4),
                                      &physical_msw,
                                      &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
   physical_lsw contain the hardware address.*/
```   
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_info_get"></a>nx_arp_info_get
Recuperar información acerca de las actividades de ARP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de ARP de la instancia de IP asociada.

> [!NOTE]
> *Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **arp_requests_sent**: puntero al destino para el total de solicitudes de ARP enviadas desde esta instancia de IP.
- **arp_requests_received**: puntero al destino para el total de solicitudes de ARP recibidas de la red.
- **arp_responses_sent**: puntero al destino para el total de respuestas de ARP enviadas desde esta instancia de IP.
- **arp_responses_received**: puntero al destino para el total de respuestas de ARP recibidas de la red.
- **arp_dynamic_entries**: puntero al destino para el número actual de entradas de ARP dinámicas.
- **arp_static_entries**: puntero al destino para el número actual de entradas de ARP estáticas.
- **arp_aged_entries**: puntero al destino del número total de entradas de ARP que han vencido y han quedado no válidas.
- **arp_invalid_messages**: puntero al destino del total de mensajes de ARP no válidos recibidos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Recuperación correcta de la información de ARP.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(&ip_0, &arp_requests_sent,
                         &arp_requests_received,
                         &arp_responses_sent,
                         &arp_responses_received,
                         &arp_dynamic_entries,
                         &arp_static_entries,
                         &arp_aged_entries,
                         &arp_invalid_messages);

/* If status is NX_SUCCESS, the ARP information has been stored in
   the supplied variables. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find
Buscar la dirección IP dada una dirección física

### <a name="prototype"></a>Prototipo  

```c
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```
### <a name="description"></a>Descripción

Este servicio intenta encontrar una dirección IP en la memoria caché de ARP que está asociada con la dirección física proporcionada.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: puntero para devolver la dirección IP, si se encuentra una que se ha asignado.
- **physical_msw**: 16 bits superiores (del 47 al 32) de la dirección física que se va a buscar.
- **physical_lsw**: 32 bits inferiores (del 31 al 0) de la dirección física que se va a buscar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se encontró correctamente la dirección IP de ARP. 
- **NX_ENTRY_NOT_FOUND**: (0x16) No se encontró la asignación en la memoria caché de ARP.
- **NX_PTR_ERROR**: (0x07) Puntero de memoria o IP no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.
- **NX_INVALID_PARAMETERS**: (0x4D) physical_msw y physical_lsw son ambos 0.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Search for the IP address associated with the hardware address of
   0x0:0x01234 in the ARP cache of the previously created IP
   Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
   associated IP address. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete
Eliminar todas las entradas de ARP estáticas

### <a name="prototype"></a>Prototipo  

```c
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina todas las entradas estáticas de la memoria caché de ARP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se han eliminado las entradas estáticas.
- **NX_PTR_ERROR**: (0x07) Puntero ip_ptr no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Delete all the static ARP entries for IP Instance 0, assuming
   "ip_0" is the NX_IP structure for IP Instance 0. */
status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
   have been deleted. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create
Crear una dirección IP estática para la asignación de hardware en la memoria caché de ARP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```
### <a name="description"></a>Descripción

Este servicio crea una asignación de dirección IP estática a física en la memoria caché de ARP para la instancia de IP especificada. Las entradas de ARP estáticas no están sujetas a actualizaciones periódicas de ARP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP que se va a asignar.
- **physical_msw**: 16 bits superiores (del 47 al 32) de la dirección física que se va a asignar.
- **physical_lsw**: 32 bits inferiores (del 31 al 0) de la dirección física que se va a asignar.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Creación correcta de la entrada estática de ARP.
- **NX_NO_MORE_ENTRIES**: (0x17) No hay más entradas de ARP disponibles en la memoria caché de ARP.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.
- **NX_INVALID_PARAMETERS**: (0x4D) physical_msw y physical_lsw son ambos 0.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Create a static ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   0x00:0x1234. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete 
Eliminar una asignación de dirección IP estática a hardware en la memoria caché de ARP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```
### <a name="description"></a>Descripción

Este servicio busca y elimina una asignación de dirección IP estática a física creada anteriormente en la memoria caché de ARP para la instancia de IP especificada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP asignada estáticamente.
- **physical_msw**: 16 bits superiores (del 47 al **32) de la dirección física asignada estáticamente.
- **physical_lsw**: 32 bits inferiores (del 31 al **0) de la dirección física asignada estáticamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Eliminación correcta de la entrada estática de ARP.
- **NX_ENTRY_NOT_FOUND**: (0x16) No se encontró la entrada de ARP estática en la memoria caché de ARP.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.
- **NX_INVALID_PARAMETERS**: (0x4D) physical_msw y physical_lsw son ambos 0.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Delete a static ARP entry on the previously created IP
   instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, the previously created static ARP entry
   was successfully deleted. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_icmp_enable"></a>nx_icmp_enable
Habilitar el protocolo de mensajes de control de Internet (ICMP)

### <a name="prototype"></a>Prototipo  

```c
UINT nx_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita el componente de ICMP para la instancia de IP especificada. El componente de ICMP es responsable de controlar los mensajes de error de Internet y las solicitudes y respuestas de ping. 

> [!IMPORTANT]  
> *Este servicio solo habilita ICMP para el servicio IPv4. Para habilitar ICMPv4 e ICMPv6, las aplicaciones deben usar el servicio **nxd_icmp_enable***.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) ICMP habilitado correctamente.
- **NX_ALREADY_ENABLED**: (0x15) ICMP ya está habilitado.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```
### <a name="see-also"></a>Consulte también

- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get
Recuperar información acerca de las actividades de ICMP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```
### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de ICMP de la instancia de IP especificada.

> [!NOTE]  
> *Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **pings_sent**: puntero al destino para el número total de pings enviados.
- **ping_timeouts**: puntero al destino para el número total de tiempos de espera de ping.
- **ping_threads_suspended**: puntero al destino del número total de subprocesos suspendidos en solicitudes de ping.
- **ping_responses_received**: puntero al destino del número total de respuestas de ping recibidas.
- **icmp_checksum_errors**: puntero al destino del número total de errores de suma de comprobación de ICMP.
- **icmp_unhandled_messages**: puntero al destino del número total de mensajes de ICMP no controlados.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Recuperación correcta de la información de ICMP.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Retrieve ICMP information from previously created IP
   instance ip_0. */
status = nx_icmp_info_get(&ip_0, &pings_sent, &ping_timeouts,
                          &ping_threads_suspended,
                          &ping_responses_received,
                          &icmp_checksum_errors,
                          &icmp_unhandled_messages);
/* If status is NX_SUCCESS, ICMP information was retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_icmp_enable
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_ping"></a>nx_icmp_ping  
Enviar solicitud de ping a la dirección IP especificada

### <a name="prototype"></a>Prototipo  

```c
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio envía una solicitud de ping a la dirección IP especificada y espera un mensaje de respuesta de ping durante la cantidad de tiempo especificada. Si no se recibe ninguna respuesta, se devuelve un error. De lo contrario, se devuelve el mensaje de respuesta completo en la variable a la que apunta response_ptr. 

Para enviar una solicitud de ping a un destino IPv6, las aplicaciones deben usar el servicio ***nxd_icmp_ping** _ o _ *_nxd_icmp_source_ping_**.

> [!WARNING]  
> *Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP, en orden de bytes del host, a la que se va a hacer ping.
- **data**: puntero al área de datos para el mensaje de ping.
- **data_size**: número de bytes de los datos de ping.
- **response_ptr**: puntero al puntero de paquete en el que se va a devolver el mensaje de respuesta de ping.
- **wait_option**: define el número de tics del temporizador de ThreadX que se va a esperar una respuesta de ping. Las opciones de espera se definen de la siguiente forma:

| Opción de espera            | Value                           |
| -----------------------|---------------------------------|
| NX_NO_WAIT             | (0x00000000)                    |
| valor del tiempo de espera en tics | (0x00000001 a 0xFFFFFFFE) |
| NX_WAIT_FOREVER        | 0xFFFFFFFF                      |

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Ping correcto. El puntero al mensaje de respuesta se ha colocado en la variable a la que apunta response_ptr.
- **NX_NO_PACKET**: (0x01) No se ha podido asignar un paquete de solicitud de ping.
- **NX_OVERFLOW**: (0x03) El área de datos especificada supera el tamaño de paquete predeterminado para esta instancia de IP.
- **NX_NO_RESPONSE** (0x29) La dirección IP solicitada no ha respondido.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.
- **NX_PTR_ERROR**: (0x07) Puntero de respuesta o dirección IP no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
   Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
                      &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
   address 1.2.3.5 and the response packet is contained in the
   packet pointed to by response_ptr. It should have the same "abcd"
   four bytes of data. */
```
### <a name="see-also"></a>Consulte también

- nx_icmp_enable
- nx_icmp_info_get
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_igmp_enable"></a>nx_igmp_enable
Habilitar el protocolo de administración de grupos de Internet (IGMP)

### <a name="prototype"></a>Prototipo  

```c
UINT nx_igmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita el componente de IGMP en la instancia de IP especificada. El componente de IGMP es responsable de proporcionar compatibilidad con las operaciones de administración de grupos de multidifusión IP.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) IGMP habilitado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_ALREADY_ENABLED**: (0x15) Este componente ya se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get
Recuperar información acerca de las actividades de IGMP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```
### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de IGMP de la instancia de IP especificada.

> [!IMPORTANT]  
> *Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **igmp_reports_sent**: puntero al destino para el número total de informes de IGMP enviados.
- **igmp_queries_received**: puntero al destino para el número total de consultas recibidas por el enrutador de multidifusión.
- **igmp_checksum_errors**: puntero al destino del número total de errores de suma de comprobación de IGMP en los paquetes recibidos.
- **current_groups_joined**: puntero al destino del número actual de grupos unidos mediante esta instancia de IP.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Recuperación correcta de la información de IGMP.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Retrieve IGMP information from previously created IP Instance ip_0. */
status = nx_igmp_info_get(&ip_0, &igmp_reports_sent,
                          &igmp_queries_received,
                          &igmp_checksum_errors,
                          &current_groups_joined);

/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable
Deshabilitar el bucle invertido de IGMP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio deshabilita el bucle invertido de IGMP para todos los grupos de multidifusión unidos posteriormente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Bucle invertido de IGMP deshabilitado correctamente.
- **NX_NOT_ENABLED**: (0x14) IGMP no está habilitado.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada no es un subproceso ni una inicialización.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Disable IGMP loopback for all subsequent multicast groups
   joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable
Habilitar el bucle invertido de IGMP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita el bucle invertido de IGMP para todos los grupos de multidifusión unidos posteriormente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Bucle invertido de IGMP deshabilitado correctamente.
- **NX_NOT_ENABLED**: (0x14) IGMP no está habilitado.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada no es un subproceso ni una inicialización.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable IGMP loopback for all subsequent multicast
   groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join
Unir la instancia de IP al grupo de multidifusión especificado mediante una interfaz

### <a name="prototype"></a>Prototipo  

```c
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Descripción

Este servicio une una instancia de IP al grupo de multidifusión especificado mediante una interfaz de red especificada. Se mantiene un contador interno para realizar un seguimiento del número de veces que se ha unido el mismo grupo. Después de unirse al grupo de multidifusión, el componente de IGMP permitirá la recepción de paquetes IP con esta dirección de grupo mediante la interfaz de red especificada y también notificará a los enrutadores que esta instancia de IP es miembro de este grupo de multidifusión. Los mensajes de unión, informe y abandono de la pertenencia de IGMP también se envían mediante la interfaz de red especificada. Para unirse a un grupo de multidifusión IPv4 sin enviar el informe de pertenencia al grupo de IGMP, la aplicación debe usar el servicio ***nx_ipv4_multicast_interface_join***.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **group_address**: dirección del grupo de multidifusión IP de clase D que se va a unir en el orden de bytes del host.
- **interface_index**: índice de la interfaz asociada a la instancia de NetX Duo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Unión correcta al grupo de multidifusión.
- **NX_NO_MORE_ENTRIES**: (0x17) No es posible unirse a más grupos de multidifusión; se ha superado el máximo.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_INVALID_INTERFACE**: (0x4C) El índice del dispositivo apunta a una interfaz de red no válida.
- **NX_IP_ADDRESS_ERROR**: (0x21) La dirección del grupo de multidifusión proporcionada no es una dirección de clase D válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) La compatibilidad con la multidifusión IP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Previously created IP Instance joins the multicast group
   244.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
                                 (&ip IP_ADDRESS(244,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```   
### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_leave"></a>nx_igmp_multicast_interface_leave
Salir del grupo de multidifusión especificado mediante una interfaz

### <a name="prototype"></a>Prototipo  

```c
UINT nx_igmp_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Descripción

Este servicio sale del grupo de multidifusión especificado mediante la interfaz de red especificada. Se mantiene un contador interno para realizar un seguimiento del número de veces que ha sido miembro el mismo grupo. Después de salir del grupo de multidifusión, el componente de IGMP enviará un informe de pertenencia adecuado y puede salir del grupo si no hay ningún miembro de este nodo. Para salir de un grupo de multidifusión IPv4 sin enviar el informe de pertenencia al grupo de IGMP, la aplicación debe usar el servicio ***nx_ipv4_multicast_interface_leave***.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **group_address**: dirección del grupo de multidifusión IP de clase D del que se va a salir. La dirección IP está en el orden de bytes del host.
- **interface_index**: índice de la interfaz asociada a la instancia de NetX Duo.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Unión correcta al grupo de multidifusión.
- **NX_ENTRY_NOT_FOUND**: (0x16) no se encuentra la dirección del grupo de multidifusión especificado en la tabla de multidifusión local.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_INVALID_INTERFACE**: (0x4C) El índice del dispositivo apunta a una interfaz de red no válida.
- **NX_IP_ADDRESS_ERROR**: (0x21) La dirección del grupo de multidifusión proporcionada no es una dirección de clase D válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) La compatibilidad con la multidifusión IP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Leave the multicast group 244.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_leave
                                (&ip IP_ADDRESS(244,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join
Unir la instancia de IP al grupo de multidifusión especificado

### <a name="prototype"></a>Prototipo  

```c
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>Descripción

Este servicio une una instancia de IP al grupo de multidifusión especificado. Se mantiene un contador interno para realizar un seguimiento del número de veces que se ha unido el mismo grupo. Si se trata de la primera vez que se solicita la unión en la red, el controlador recibe la orden de enviar un informe de IGMP que indique la intención del host de unirse al grupo. Después de unirse, el componente de IGMP permitirá la recepción de paquetes IP con esta dirección de grupo y notificará a los enrutadores que esta instancia de IP es miembro de este grupo de multidifusión. Para unirse a un grupo de multidifusión IPv4 sin enviar el informe de pertenencia al grupo de IGMP, la aplicación debe usar el servicio ***nx_ipv4_multicast_interface_join***.

> [!NOTE]  
> *Para unirse a un grupo de multidifusión en un dispositivo no primario, use el servicio **nx_igmp_multicast_interface_join.***

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **group_address**: dirección del grupo de multidifusión IP de clase D que se va a unir.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Unión correcta al grupo de multidifusión.
- **NX_NO_MORE_ENTRIES**: (0x17) No es posible unirse a más grupos de multidifusión; se ha superado el máximo.
- **NX_INVALID_INTERFACE**: (0x4C) El índice del dispositivo apunta a una interfaz de red no válida.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección de grupo IP no válida.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Previously created IP Instance ip_0 joins the multicast group
   224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully
   joined the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave
Hacer que la instancia de IP salga del grupo de multidifusión especificado

### <a name="prototype"></a>Prototipo  

```c
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>Descripción

Este servicio hace que una instancia de IP salga del grupo de multidifusión especificado si el número de solicitudes para salir coincide con el número de solicitudes para unirse. De lo contrario, solo se reduce el contador de uniones interno. Para salir de un grupo de multidifusión IPv4 sin enviar el informe de pertenencia al grupo de IGMP, la aplicación debe usar el servicio ***nx_ipv4_multicast_interface_leave***.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **group_address**: grupo de multidifusión que se va a abandonar.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Unión correcta al grupo de multidifusión.
- **NX_ENTRY_NOT_FOUND**: (0x16) No se ha encontrado la solicitud de unión anterior.
- **NX_INVALID_INTERFACE**: (0x4C) El índice del dispositivo apunta a una interfaz de red no válida.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección de grupo IP no válida.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
   the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy
Notificar a la aplicación si cambia la dirección IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *, VOID *),
    VOID *additional_info);
```
### <a name="description"></a>Descripción

Este servicio registra una función de notificación a la aplicación a la que se llama cada vez que cambie la dirección IPv4.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **change_notify**: puntero a la función de notificación de cambio de IP. Si este parámetro es NX_NULL, se deshabilita la notificación de cambio de dirección IP.
- **additional_info**: puntero a información adicional opcional que también se proporciona a la función de notificación cuando cambia la dirección IP.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Notificación correcta de cambio de dirección IP.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Register the function "my_ip_changed" to be called whenever the
   IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed,
                                      NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
   called whenever the IP address changes. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_get"></a>nx_ip_address_get
Recuperar la dirección IPv4 y la máscara de red

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>Descripción

Este servicio recupera la dirección IPv4 y la máscara de subred de la interfaz de red principal.

> [!IMPORTANT]   
> *Para obtener información del dispositivo secundario, use el servicio **nx_ip_interface_address_get***.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: puntero al destino de la dirección IP.
- **network_mask**: puntero al destino de la máscara de red.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) La dirección IP se ha obtenido correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero a la variable de devolución o a la instancia de IP no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Get the IP address and network mask from the previously created
   IP Instance ip_0. */
status = nx_ip_address_get(&ip_0, &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
   network_mask contain the IP and network mask respectively. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_set"></a>nx_ip_address_set
Establecer la dirección IPv4 y la máscara de red

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>Descripción

Este servicio establece la dirección IPv4 y la máscara de red de la interfaz de red principal.

> [!IMPORTANT]  
> *Para establecer la dirección IP y la máscara de red del dispositivo secundario, use el servicio **nx_ip_interface_address_set***.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: nueva dirección IP.
- **network_mask**: nueva máscara de red.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Dirección IP establecida correctamente.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00 for
   the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4),
                           0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address of
   1.2.3.4 and a network mask of 0xFFFFFF00. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_auxiliary_packet_pool_set"></a>nx_ip_auxiliary_packet_pool_set
Configurar un grupo de paquetes auxiliar

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_auxiliary_packet_pool_set(
    NX_IP *ip_ptr,
    NX_PACKET_POOL *aux_pool);
```
### <a name="description"></a>Descripción

Este servicio configura un grupo de paquetes auxiliar en la instancia de IP. Para un sistema con restricción de memoria, el usuario puede aumentar la eficacia de la memoria al crear el grupo de paquetes predeterminado con el tamaño de paquete de la MTU y crear un grupo de paquetes auxiliar con un tamaño de paquete más pequeño para que el subproceso de IP transmita pequeños paquetes con él. El tamaño de paquete recomendado para el grupo auxiliar es de 256 bytes, suponiendo que IPv6 e IPsec están habilitados.

De manera predeterminada, la instancia de IP no acepta el grupo de paquetes auxiliar. Para habilitar esta característica, se debe definir *NX_DUAL_PACKET_POOL_ENABLE* al compilar la biblioteca de NetX Duo.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **aux_pool**: grupo de paquetes auxiliar que se va a configurar para la instancia de IP.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Dirección IP establecida correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) No se ha compilado en la biblioteca la característica de grupo de paquetes dual.
- **NX_PTR_ERROR**: (0x07) Puntero de IP o puntero de grupo no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible  

No

### <a name="example"></a>Ejemplo

```c
#define SMALL_PAYLOAD_SIZE 256
NX_PACKET small_pool;

nx_packet_pool_create(&small_pool, "small pool", SMALL_PAYLOAD_SIZE,
                       small_pool_memory_ptr, small_pool_size);

/* Add the small packet pool to the IP instance. */
status = nx_ip_auxiliary_packet_pool_set(&ip_0, &small_pool);

/* If status is NX_SUCCESS, the IP instance now is able to use the
   small pool for transmitting small datagram. */
```
### <a name="see-also"></a>Consulte también

- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_ip_create"></a>nx_ip_create
Crear una instancia de IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```
### <a name="description"></a>Descripción

Este servicio crea una instancia de IP con la dirección IP y el controlador de red proporcionados por el usuario. Además, la aplicación debe proporcionar un grupo de paquetes creado previamente para la instancia de IP que se va a utilizar para la asignación interna de paquetes. Tenga en cuenta que no se llama al controlador de red proporcionado por la aplicación hasta que se ejecuta este subproceso de IP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control para crear una nueva instancia de IP.
- **name**: nombre de esta nueva instancia de IP.
- **ip_address**: dirección IP de esta nueva instancia de IP.
- **network_mask**: máscara para delimitar la parte de la red de la dirección IP para los usos de subredes y superredes.
- **default_pool**: puntero al bloque de control del grupo de paquetes de NetX Duo creado previamente.
- **ip_network_driver**: controlador de red proporcionado por el usuario que se usa para enviar y recibir paquetes IP.
- **memory_ptr**: puntero al área de memoria para el área de pila del subproceso auxiliar de IP.
- **memory_size**: número de bytes del área de memoria para la pila del subproceso auxiliar de IP.
- **priority**: prioridad del subproceso auxiliar de IP.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Creación correcta de la instancia de IP.
- **NX_NOT_IMPLEMENTED**: (0x4A) La biblioteca de NetX Duo no está configurada correctamente.
- **NX_PTR_ERROR**: (0X07) instancia de IP, puntero a la función del controlador de red, grupo de paquetes o puntero a la memoria no válidos.
- **NX_SIZE_ERROR**: (0X09) El tamaño de pila proporcionado es demasiado pequeño.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_IP_ADDRESS_ERROR**: (0x21) La dirección IP proporcionada no es válida.
- **NX_OPTION_ERROR**: (0x21) La prioridad del subproceso de IP proporcionada no es válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Create an IP instance with an IP address of 1.2.3.4 and a network
   mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
   point of the application specific network driver and the
   "stack_memory_ptr" specifies the start of a 1024 byte memory
   area that is used for this IP instance’s helper thread. */
status = nx_ip_create(&ip_0, "NetX IP Instance ip_0",
                      IP_ADDRESS(1, 2, 3, 4),
                      0xFFFFFF00UL, &pool_0, ethernet_driver,
                      stack_memory_ptr, 1024, 1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_delete"></a>nx_ip_delete
Eliminar una instancia de IP creada anteriormente

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_delete(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio elimina una instancia de IP creada anteriormente y libera todos los recursos del sistema que pertenecen a la instancia de IP.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Instancia de IP eliminada correctamente.
- **NX_SOCKETS_BOUND**: (0x28) Esta instancia de IP todavía tiene sockets UDP o TCP enlazados a ella. Se deben desenlazar y eliminar todos los sockets antes de eliminar la instancia de IP.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>Consulte también 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command
Emitir un comando al controlador de red

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_driver_direct_command
    (NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```
### <a name="description"></a>Descripción

Este servicio proporciona una interfaz directa al controlador de la interfaz de red principal de la aplicación especificado durante la llamada a ***nx_ip_create***. Se pueden usar comandos específicos de la aplicación siempre que su valor numérico sea mayor o igual que NX_LINK_USER_COMMAND.

> [!IMPORTANT]  
> *Para emitir un comando para el dispositivo secundario, use el servicio **nx_ip_driver_interface_direct_command***.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **command**: código numérico del comando. Los comandos estándar se definen de la siguiente manera:
    - NX_LINK_GET_STATUS (10)
    - NX_LINK_GET_SPEED (11)
    - NX_LINK_GET_DUPLEX_TYPE (12)
    - NX_LINK_GET_ERROR_COUNT (13)
    - NX_LINK_GET_RX_COUNT (14)
    - NX_LINK_GET_TX_COUNT (15)
    - NX_LINK_GET_ALLOC_ERRORS (16)
    - NX_LINK_USER_COMMAND (50)
- **return_value_ptr**: puntero a la variable de devolución del autor de llamada.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Comando directo del controlador de red ejecutado correctamente.
- **NX_UNHANDLED_COMMAND**: (0X44) Comando del controlador de red no controlado o no implementado.
- **NX_PTR_ERROR**: (0X07) IP o puntero de valor devuelto no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) Índice de interfaz no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Make a direct call to the application-specific network driver
   for the previously created IP instance. For this example, the
   network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(&ip_0, NX_LINK_GET_STATUS,
                                     &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
   NX_TRUE or NX_FALSE value representing the status of the
   physical link. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command
Emitir un comando al controlador de red

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```
### <a name="description"></a>Descripción

Este servicio proporciona un comando directo al controlador del dispositivo de red de la aplicación en la instancia de IP. Se pueden usar comandos específicos de la aplicación siempre que su valor numérico sea mayor o igual que *NX_LINK_USER_COMMAND*.

### <a name="parameters"></a>Parámetros  

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **command**: código numérico del comando. Los comandos estándar se definen de la siguiente manera:
    - NX_LINK_GET_STATUS (10)
    - NX_LINK_GET_SPEED (11)
    - NX_LINK_GET_DUPLEX_TYPE (12)
    - NX_LINK_GET_ERROR_COUNT (13)
    - NX_LINK_GET_RX_COUNT (14)
    - NX_LINK_GET_TX_COUNT (15)
    - NX_LINK_GET_ALLOC_ERRORS (16)
    - NX_LINK_USER_COMMAND (50)
- **interface_index**: índice de la interfaz de red a la que se debe enviar el comando.
- **return_value_ptr**: puntero a la variable de devolución del autor de llamada.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Comando directo del controlador de red ejecutado correctamente.
- **NX_UNHANDLED_COMMAND**: (0X44) Comando del controlador de red no controlado o no implementado.
- **NX_INVALID_INTERFACE**: (0x4C) Índice de interfaz no válido.
- **NX_PTR_ERROR**: (0X07) IP o puntero de valor devuelto no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Make a direct call to the application-specific network driver
   for the previously created IP instance. For this example, the
   network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;

status = nx_ip_driver_interface_direct_command(&ip_0,
                                               NX_LINK_GET_STATUS,
                                               interface_index,
                                               &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
   NX_TRUE or NX_FALSE value representing the status of the
   physical link. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable  
Deshabilitar el reenvío de paquetes IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio deshabilita el reenvío de paquetes IP dentro del componente de IP de NetX Duo. Al crear la tarea de IP, este servicio se deshabilita automáticamente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) El reenvío de paquetes IP se ha deshabilitado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible  

No

### <a name="example"></a>Ejemplo

```c
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>Consulte también  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable
Habilitar el reenvío de paquetes IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita el reenvío de paquetes IP dentro del componente de IP de NetX Duo. Al crear la tarea de IP, este servicio se deshabilita automáticamente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) El reenvío de paquetes IP se ha habilitado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>Consulte también 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable
Deshabilitar la fragmentación de paquetes IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio deshabilita la funcionalidad de fragmentación y reensamblado de paquetes IPv4 e IPv6. En el caso de los paquetes que esperan reensamblado, este servicio libera estos paquetes. Al crear la tarea de IP, este servicio se deshabilita automáticamente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0X00) Se ha deshabilitado correctamente la fragmentación de paquetes IP.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) La fragmentación de IP no está habilitada en la instancia de IP.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
   previously created IP instance. */
```

### <a name="see-also"></a>Consulte también  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable
Habilitar la fragmentación de paquetes IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita la funcionalidad de fragmentación y reensamblado de paquetes IPv4 e IPv6. Al crear la tarea de IP, este servicio se deshabilita automáticamente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) La fragmentación de IP se ha habilitado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Las características de fragmentación de IP no se han compilado en NetX Duo.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>Consulte también  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_gateway_address_clear"></a>nx_ip_gateway_address_clear
Borrar la dirección de la puerta de enlace IPv4

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_gateway_address_clear(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio borra la dirección de la puerta de enlace IPv4 configurada en la instancia. Para borrar un valor predeterminado externo de IPv6 de la instancia de IP, las aplicaciones deben usar el servicio ***nxd_ipv6_default_router_delete.***

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha borrado correctamente la dirección de la puerta de enlace IP.
- **NX_PTR_ERROR**: (0x07) Bloque de control de IP no válido.
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Clear the gateway address of IP instance. */
status = nx_ip_gateway_address_clear(&ip_0);

/* If status == NX_SUCCESS, the gateway address was successfully
   cleared from the IP instance. */
```
### <a name="see-also"></a>Consulte también

-nx_ip_gateway_address_get -nx_ip_gateway_address_set -nx_ip_info_get -nx_ip_static_route_add -nx_ip_static_route_delete -nxd_ipv6_default_router_add -nxd_ipv6_default_router_delete -nxd_ipv6_default_router_entry_get -nxd_ipv6_default_router_get -nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_get"></a>nx_ip_gateway_address_get
Obtener la dirección de la puerta de enlace IPv4

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_gateway_address_get(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>Descripción

Este servicio recupera la dirección de la puerta de enlace IPv4 configurada en la instancia de IP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **ip_address**: puntero a la memoria en la que se almacena la dirección de la puerta de enlace.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha obtenido correctamente. 
- **NX_PTR_ERROR**: (0x07) Puntero de bloque de control de IP o puntero de dirección IP no válidos.
- **NX_NOT_FOUND**: (0x4E) No se ha encontrado la dirección de la puerta de enlace.
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
ULONG ip_address;

/* Get the gateway address of IP instance. */
status = nx_ip_gateway_address_get(&ip_0, &ip_address);

/* If status == NX_SUCCESS, the gateway address was successfully
   got. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set
Establecer la dirección IP de la puerta de enlace

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>Descripción

Este servicio establece la dirección IP de la puerta de enlace IPv4. Todo el tráfico destinado fuera de la red se enruta a esta puerta de enlace para su transmisión. La puerta de enlace debe ser accesible directamente mediante una de las interfaces de red. Para configurar la dirección de la puerta de enlace IPv6, use el servicio ***nxd_ipv6_default_router_add***. 

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP de la puerta de enlace.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Dirección IP de la puerta de enlace establecida correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero a la instancia de IP no válido.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subproceso

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Setup the Gateway address for previously created IP
   Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99);

/* If status is NX_SUCCESS, all out-of-network send requests are
   routed to 1.2.3.99. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_info_get"></a>nx_ip_info_get
Recuperar información acerca de las actividades de IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```
### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de IP de la instancia de IP especificada.

> [!NOTE]  
> *Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_total_packets_sent**: puntero al destino para el número total de paquetes IP enviados.
- **ip_total_bytes_sent**: puntero al destino para el número total de bytes enviados.
- **ip_total_packets_received**: puntero al destino para el número total de paquetes IP recibidos.
- **ip_total_bytes_received**: puntero al destino para el número total de bytes de IP recibidos.
- **ip_invalid_packets**: puntero al destino para el número total de paquetes IP no válidos.
- **ip_receive_packets_dropped**: puntero al destino para el número total de paquetes recibidos eliminados.
- **ip_receive_checksum_errors**: puntero al destino para el número total de errores de suma de comprobación en paquetes recibidos.
- **ip_send_packets_dropped**: puntero al destino para el número total de paquetes enviados eliminados.
- **ip_total_fragments_sent**: puntero al destino para el número total de fragmentos enviados.
- **ip_total_fragments_received**: puntero al destino para el número total de fragmentos recibidos.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Recuperación correcta de la información de IP.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Retrieve IP information from previously created IP
   Instance 0. */
status = nx_ip_info_get(&ip_0,
                        &ip_total_packets_sent,
                        &ip_total_bytes_sent,
                        &ip_total_packets_received,
                        &ip_total_bytes_received,
                        &ip_invalid_packets,
                        &ip_receive_packets_dropped,
                        &ip_receive_checksum_errors,
                        &ip_send_packets_dropped,
                        &ip_total_fragments_sent,
                        &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get
Recuperar la dirección IP de la interfaz

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>Descripción

Este servicio recupera la dirección IPv4 de una interfaz de red especificada. Para recuperar la dirección IPv6, la aplicación debe usar el servicio ***nxd_ipv6_address_get***.

> [!CAUTION]  
> *Si no es el dispositivo primario, el dispositivo especificado debe estar conectado previamente a la instancia de IP.*

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_index**: índice de la interfaz, el mismo valor que el índice de la interfaz de red asociada a la instancia de IP.
- **ip_address**: puntero al destino de la dirección IP de la interfaz del dispositivo.
- **network_mask**: puntero al destino de la máscara de red de la interfaz del dispositivo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La dirección IP se ha obtenido correctamente.
- **NX_INVALID_INTERFACE**: (0x4C) La interfaz de red especificada no es válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define INTERFACE_INDEX 1

/* Get device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
                                     &ip_address,
                                     &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
   retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_mapping_configure"></a>nx_ip_interface_address_mapping_configure
Configurar si es necesaria la asignación de direcciones

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_address_mapping_configure(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT mapping_needed);
```
### <a name="description"></a>Descripción

Este servicio configura si es necesaria la asignación de dirección IP a dirección MAC para la interfaz de red especificada. Normalmente se llama a este servicio desde el controlador de dispositivo de la interfaz para notificar a la pila de IP si la interfaz subyacente requiere asignación de la dirección IP a una dirección de capa dos (MAC).

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **interface_index**: índice de la interfaz de red.
- **mapping_needed**: NX_TRUE si se necesita asignación de direcciones y NX_FALSE si no es necesaria.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Configuración correcta.
- **NX_INVALID_INTERFACE**: (0x4C) Índice de dispositivo no válido.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Thread

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0
UCHAR mapping_needed = NX_TRUE;

/* Configure address mapping needed specified interface. */
status = nx_ip_interface_address_mapping_configure(&ip_0,
                                             PRIMARY_INTERFACE,
                                             mapping_needed);

/* If status == NX_SUCCESS, the address mapping needed was
   successfully configured. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set
Establecer la dirección IP y la máscara de red de la interfaz

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>Descripción

Este servicio establece la dirección IPv4 y la máscara de red de la interfaz IP especificada. Para configurar la dirección de la interfaz IPv6, la aplicación debe usar el servicio ***nxd_ipv6_address_set***. 
 
> [!WARNING]  
> *La interfaz especificada se debe asociar previamente a la instancia de IP*. 

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_index**: índice de la interfaz asociada a la instancia de NetX Duo.
- **ip_address**: nueva dirección IP de la interfaz de red.
- **network_mask**: nueva máscara de red de la interfaz.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Dirección IP establecida correctamente.
- **NX_INVALID_INTERFACE**: (0x4C) La interfaz de red especificada no es válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) Punteros no válidos.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define INTERFACE_INDEX 1

/* Set device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
                                     ip_address,
                                     network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
   successfully set. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach
Conectar la interfaz de red a la instancia de IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)(struct NX_IP_DRIVER_STRUCT *));
```
### <a name="description"></a>Descripción

Este servicio agrega una interfaz de red física a la interfaz IP. Tenga en cuenta que la instancia de IP se crea con la interfaz principal, por lo que cada interfaz adicional es secundaria para la interfaz principal. El número total de interfaces de red conectadas a la instancia de IP (incluida la interfaz principal) no puede superar **NX_MAX_PHYSICAL_INTERFACES**.

Si el subproceso de IP todavía no se ha ejecutado, las interfaces secundarias se inicializarán como parte del proceso de inicio del subproceso de IP que inicializa todas las interfaces físicas.

Si el subproceso de IP aún no se está ejecutando, la interfaz secundaria se inicializa como parte del servicio ***nx_ip_interface_attach***.

> [!WARNING]  
> *ip_ptr debe apuntar a una estructura IP de NetX Duo válida. **NX_MAX_PHYSICAL_INTERFACES** se debe configurar para el número de interfaces de red de la instancia de IP. El valor predeterminado es uno*.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_name**: puntero a la cadena del nombre de la interfaz.
- **ip_address**: dirección IP del dispositivo en el orden de bytes del host.
- **network_mask**: máscara de red del dispositivo en el orden de bytes del host.
- **ip_link_driver**: controlador Ethernet de la interfaz.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) La entrada se ha agregado a la tabla de enrutamiento estático.
- **NX_NO_MORE_ENTRIES**: (0x17) Número máximo de interfaces. Se ha superado NX_MAX_PHYSICAL_INTERFACES. Si IPv6 está habilitado, este error también puede indicar que es posible que el controlador no tenga suficientes recursos para administrar las operaciones de multidifusión IPv6.
- **NX_DUPLICATED_ENTRY**: (0x52) La dirección IP suministrada ya está en uso en esta instancia de IP.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) Entrada de puntero no válida.
- **NX_IP_ADDRESS_ERROR**: (0x21) Entrada de dirección IP no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Attach secondary device for device IP address 192.168.1.68 with
   the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
                                IP_ADDRESS(192,168,1,68),
                                0xFFFFFF00UL,
                                nx_etherDriver);

/* If status is NX_SUCCESS the interface was successfully added to
   the IP instance interface table. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_get"></a>nx_ip_interface_capability_get
Obtener las funcionalidades del hardware de la interfaz

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_capability_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *interface_capability_flag);
```
### <a name="description"></a>Descripción

Este servicio recupera la marca de funcionalidades de la interfaz de red especificada. Para usar este servicio, se debe compilar la biblioteca de NetX Duo con la opción ***NX_ENABLE_INTERFACE_CAPABILITY*** habilitada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **interface_index**: índice de la interfaz de red.
- **interface_capability_flag**: puntero al espacio de memoria de la marca de funcionalidades.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se obtuvo correctamente la información de funcionalidades de la interfaz.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de funcionalidades de la interfaz no se admite en esta compilación.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido o puntero de marca de funcionalidades no válido.
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0
ULONG       capability_flag;

/* Get the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_get(&ip_0,
                                        PRIMARY_INTERFACE,
                                        &capability_flag);

/* If status == NX_SUCCESS, the capability flag from the primary
   interface was successfully retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_set"></a>nx_ip_interface_capability_set
Establecer la marca de funcionalidades del hardware

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_capability_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG interface_capability_flag);
```                           
### <a name="description"></a>Descripción

El controlador del dispositivo de red usa este servicio para configurar la marca de funcionalidades de una interfaz de red especificada. Para usar este servicio, se debe compilar la biblioteca de NetX Duo con la opción ***NX_ENABLE_INTERFACE_CAPABILITY*** definida.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **interface_index**: índice de la interfaz de red.
- **interface_capability_flag**: marca de funcionalidades para la salida.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha establecido correctamente la marca de funcionalidades del hardware de la interfaz.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de funcionalidades de la interfaz no se admite en esta compilación.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido. 
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido. 
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0
ULONG capability_flag = \
                 NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM |\
                 NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM;
UINT device_index = 0;

/* Set the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_set(&ip_0,
                                        PRIMARY_INTERFACE,
                                        capability_flag);

/* If status == NX_SUCCESS, the hardware capability flag was
   successfully set. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_detach"></a>nx_ip_interface_detach
Desconectar la interfaz especificada de la instancia de IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr, 
    UINT index);
```
### <a name="description"></a>Descripción

Este servicio desconecta la interfaz IP especificada de la instancia de IP. Una vez desconectada una interfaz, se cierran todos los sockets TCP conectados y se quitan las entradas de la memoria caché de ND y ARP de esta interfaz de las tablas respectivas. Se quitan las pertenencias de IGMP de esta interfaz.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **index**: índice de la interfaz que se va a quitar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha quitado correctamente una interfaz física.
- **NX_INVALID_INTERFACE**: (0x4C) La interfaz de red especificada no es válida.
- **NX_PTR_ERROR**: (0x07) Punteros no válidos.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define INTERFACE_INDEX 1

/* Detach interface 1. */
status = nx_ip_interface_detach(&IP_0, INTERFACE_INDEX);

/* If status is NX_SUCCESS the interface is successfully detached
   from the IP instance. */
```

### <a name="see-also"></a>Consulte también  

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get
Recuperar los parámetros de la interfaz de red

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```
### <a name="description"></a>Descripción

Este servicio recupera información de los parámetros de red de la interfaz de red especificada. Todos los datos se recuperan en el orden de bytes del host. 

> [!WARNING]  
> *ip_ptr debe apuntar a una estructura IP de NetX Duo válida. La interfaz especificada, si no es la interfaz principal, se debe conectar previamente a la instancia de IP.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_index**: índice que especifica la interfaz de red.
- **interface_name**: puntero al búfer que contiene el nombre de la interfaz de red.
- **ip_address**: puntero al destino de la dirección IP de la interfaz.
- **network_mask**: puntero al destino de la máscara de red.
- **mtu_size**: puntero al destino de la unidad de transferencia máxima de esta interfaz.
- **physical_address_msw**: puntero al destino de los 16 bits superiores de la dirección MAC del dispositivo.
- **physical_address_lsw**: puntero al destino de los 32 bits inferiores de la dirección MAC del dispositivo.

### <a name="return-values"></a>Valores devueltos   

- **NX_SUCCESS**: (0x00) Se ha obtenido la información de la interfaz.
- **NX_PTR_ERROR**: (0x07) Entrada de puntero no válida.
- **NX_INVALID_INTERFACE**: (0x4C) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Retrieve interface parameters for the specified interface (index
   1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1
status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
                                  &name_ptr, &ip_address,
                                  &network_mask,
                                  &mtu_size,
                                  &physical_address_msw,
                                  &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
   successfully retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_mtu_set"></a>nx_ip_interface_mtu_set
Establecer el valor de MTU de una interfaz de red

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_mtu_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG mtu_size);
```
### <a name="description"></a>Descripción

El controlador del dispositivo usa este servicio para configurar el valor de MTU de IP de la interfaz de red especificada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **interface_index**: índice de la interfaz de red.
- **mtu_size**: tamaño de MTU de IP.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha establecido correctamente el valor de MTU.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0
ULONG       mtu_size = 1500;

/* Set the MTU size of specified interface. */
status = nx_ip_interface_mtu_set(&ip_0,
                                 PRIMARY_INTERFACE, mtu_size);

/* If status == NX_SUCCESS, the MTU size was successfully set. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_get"></a>nx_ip_interface_physical_address_get
Obtener la dirección física de un dispositivo de red

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_physical_address_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *physical_msw,
    ULONG *physical_lsw);
```
### <a name="description"></a>Descripción

Este servicio recupera la dirección física de una interfaz de red desde la instancia de IP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **interface_index**: índice de la interfaz de red.
- **physical_msw**: puntero al destino de los 16 bits superiores de la dirección MAC del dispositivo.
- **physical_lsw**: puntero al destino de los 32 bits inferiores de la dirección MAC del dispositivo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha obtenido correctamente.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero de bloque de control de IP o puntero a la dirección física no válidos.
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0
ULONG   physical_msw;
ULONG   physical_lsw;

/* Get the physical address of specified interface. */
status = nx_ip_interface_physical_address_get(&ip_0,
                                              PRIMARY_INTERFACE,
                                              &physical_msw,
                                              &physical_lsw);

/* If status == NX_SUCCESS, the physical address was successfully
   retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_set"></a>nx_ip_interface_physical_address_set
Establecer la dirección física de una interfaz de red especificada

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_physical_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT update_driver);
```
### <a name="description"></a>Descripción

Este servicio lo usan la aplicación o un controlador de dispositivo para configurar la dirección física de la dirección MAC de la interfaz de red especificada. La nueva dirección MAC se aplica al bloque de control de la estructura de la interfaz. Si se establece la marca ***update_driver***, se emite un comando de nivel de controlador para que el controlador del dispositivo pueda actualizar su dirección MAC programada en el controlador Ethernet.

En una situación típica, se llama a este servicio desde el controlador de dispositivo de la interfaz durante la fase de inicialización para notificar a la pila IP su dirección MAC. En este caso, no se debe establecer la marca ***update_driver***.

También se puede llamar a esta rutina desde la aplicación de usuario para volver a configurar la dirección MAC de la interfaz en tiempo de ejecución. En este caso de uso, se debe establecer la marca ***update_driver*** para que se pueda aplicar la nueva dirección MAC al controlador del dispositivo.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **interface_index**: índice de la interfaz de red.
- **physical_msw**: puntero al destino de los 16 bits superiores de la dirección MAC del dispositivo.
- **physical_lsw**: puntero al destino de los 32 bits inferiores de la dirección MAC del dispositivo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha establecido correctamente
- **NX_UNHANDLED_COMMAND**: (0x4B) Comando no reconocido por el controlador.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0
ULONG       physical_msw = 0x00CF;
ULONG       physical_lsw = 0x01020304;

/* Set the physical address of specified device. */
status = nx_ip_interface_physical_address_set(&ip_0,
                                              PRIMARY_INTERFACE,
                                              physical_msw,
                                              physical_lsw,
                                              NX_TRUE);

/* If status == NX_SUCCESS, the physical address was successfully
   set. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check
Comprobar el estado de una instancia de IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio comprueba y, de manera opcional, espera el estado especificado de la interfaz de red de una instancia de IP creada anteriormente.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_index**: número de índice de la interfaz. needed_status: estado de IP solicitado, definido en formato de mapa de bits de la siguiente manera:
  - **NX_IP_INITIALIZE_DONE**: (0x0001)
  - **NX_IP_ADDRESS_RESOLVED**: (0x0002)
  - **NX_IP_LINK_ENABLED**: (0x0004)
  - **NX_IP_ARP_ENABLED**: (0x0008)
  - **NX_IP_UDP_ENABLED**: (0x0010)
  - **NX_IP_TCP_ENABLED**: (0x0020)
  - **NX_IP_IGMP_ENABLED**: (0x0040)
  - **NX_IP_RARP_COMPLETE**: (0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED**: (0x0100)
- **actual_status**: puntero al destino del conjunto de bits real. wait_option define cómo se comporta el servicio si los bits de estado solicitados no están disponibles. Las opciones de espera se definen de la siguiente forma:
  - **NX_NO_WAIT**: (0x00000000)
  - **valor de tiempo de espera**: (de 0x00000001 a 0xFFFFFFFE)
  - **NX_WAIT_FOREVER**: (0xFFFFFFFF)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Comprobación de estado de IP correcta.
- **NX_NOT_SUCCESSFUL**: (0x43) La solicitud de estado no se ha satisfecho dentro del tiempo de espera especificado.
- **NX_PTR_ERROR**: (0x07) El puntero IP no es o ha dejado de ser válido o el puntero de estado real no es válido.
- **NX_OPTION_ERROR**: (0x0a) Opción de estado necesario no válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz está fuera del intervalo o la interfaz no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
                                      &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
   instance is up. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set
Establecer la función de devolución de llamada de notificación de cambio de estado del vínculo

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID(*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```
### <a name="description"></a>Descripción

Este servicio configura la función de devolución de llamada de notificación de cambio de estado del vínculo. La rutina *link_status_change_notify* proporcionada por el usuario se invoca cuando cambia el estado de la interfaz principal o secundaria (por ejemplo, se cambia la dirección IP). Si *link_status_change_notify* es NULL, se deshabilita la característica de devolución de llamada de notificación de cambio de estado del vínculo.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **link_status_change_notify**: función de devolución de llamada proporcionada por el usuario a la que se llamará cuando cambie la interfaz física.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha establecido correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido o nuevo puntero de dirección física.
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Configure a callback function to be used when the physical
   interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0,
                                             my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
   is set. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check

## <a name="nx_ip_max_payload_size_find"></a>nx_ip_max_payload_size_find
Calcular la carga máxima de datos del paquete

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_max_payload_size_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *dest_address,
    UINT if_index,
    UINT src_port,
    UINT dest_port,
    ULONG protocol,
    ULONG *start_offset_ptr,
    ULONG *payload_length_ptr);
```
### <a name="description"></a>Descripción

Este servicio encuentra el tamaño máximo de carga de aplicación que no requerirá fragmentación IP para alcanzar el destino; por ejemplo, la carga es o está por debajo del tamaño de MTU de la interfaz local. (o el valor de MTU de ruta obtenido mediante la detección de MTU de la ruta IPv6). El encabezado IP y el tamaño del encabezado de aplicación superior (TCP o UDP) se restan de la carga total. Si se aplica la directiva de seguridad de IPsec de NetX Duo a este punto de conexión, los encabezados IPsec (ESP/AH) y la sobrecarga asociada, como el vector inicial, también se restan de la MTU. Este servicio es aplicable a los paquetes IPv4 e IPv6.

El parámetro *if_index* especifica la interfaz que se va a utilizar para enviar el paquete. En el caso de un sistema de host múltiple, el autor de llamada debe especificar el parámetro *if_index* si el destino es una difusión (solo IPv4), multidifusión o una dirección local de vínculo IPv6.

Este servicio devuelve dos valores al autor de llamada:

1) start_offset_ptr: esta es la ubicación después de los encabezados TCP/UDP/IP/IPsec.
2) payload_length_ptr: cantidad de datos que la aplicación puede transferir sin superar la MTU.

No hay ningún servicio de NetX equivalente.

### <a name="restrictions"></a>Restricciones 

La instancia de IP se debe crear previamente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP.
- **dest_address**: puntero a la dirección de destino del paquete.
- **if_index**: indica el índice de la interfaz que se va a usar.
- **src_port**: número de puerto de origen.
- **dest_port**: número de puerto de destino.
- **protocol**: protocolo de nivel superior que se va a usar.
- **start_offset_ptr**: puntero al inicio de los datos para la carga máxima del paquete.
- **payload_length_ptr**: puntero al tamaño de la carga excluyendo los encabezados.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Carga calculada correctamente.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido o la interfaz no es válida.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido o dirección de destino no válida.
- **NX_IP_ADDRESS_ERROR**: (0x21) Se ha proporcionado una dirección no válida. 
- **NX_NOT_SUPPORTED**: (0x4B) Protocolo no válido (no es UDP ni TCP).
- **NX_CALLER_ERROR**: (0x11) No se ha llamado al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* The following example determines the maximum payload for UDP
   packet to remote host. */
#define PRIMARY_INTERFACE 0
status = nx_ip_max_payload_size_find(&ip_0,
                                     &dest_ipv6_address,
                                     PRIMARY_INTERFACE,
                                     source_port,
                                     dest_port, NX_PROTOCOL_UDP,
                                     &start_offset,
                                     &payload_length);

/* A return value of NX_SUCCESS indicates the packet payload
   payload_length starting at the offset start_offset is
   successfully computed. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable
Deshabilitar el envío y la recepción de paquetes sin formato

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio deshabilita la transmisión y recepción de paquetes IP sin formato para esta instancia de IP. Si el servicio de paquetes sin formato se ha habilitado previamente y hay paquetes sin formato en la cola de recepción, este servicio liberará cualquier paquete sin formato recibido.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Deshabilitación correcta de paquetes de IP sin formato.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);
/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been disabled for the previously created IP instance. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable
Habilitar el procesamiento de paquetes sin formato

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita la transmisión y recepción de paquetes IP sin formato para esta instancia de IP. Los paquetes TCP, UDP, ICMP e IGMP entrantes se siguen procesando en NetX Duo. Los paquetes con tipos de protocolo de nivel superior desconocidos los procesa la rutina de recepción de paquetes sin formato.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Habilitación correcta de paquetes IP sin formato.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been enabled for the previously created IP instance. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_filter_set"></a>nx_ip_raw_packet_filter_set
Establecer el filtro de paquetes IP sin formato

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_raw_packet_filter_set(
    NX_IP *ip_ptr,
    UINT (*raw_packet_filter)(NX_IP *, ULONG, NX_PACKET *));
```
### <a name="description"></a>Descripción

Este servicio configura el filtro de paquetes IP sin formato. La función de filtro de paquetes sin formato, implementada por la aplicación de usuario, permite a una aplicación recibir paquetes sin formato en función de los criterios proporcionados por el usuario. Tenga en cuenta que la capa de contenedor BSD de NetX Duo usa la característica de filtro de paquetes sin formato para controlar el socket sin formato en la capa BSD. Para usar este servicio, se debe compilar la biblioteca de NetX Duo con la opción ***NX_ENABLE_IP_RAW_PACKET_FILTER*** definida.

### <a name="parameters"></a>Parámetros  

- **ip_ptr**: puntero al bloque de control de IP.
- **raw_packet_filter**: puntero a la función del filtro de paquetes sin formato.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha establecido correctamente la rutina de filtro de paquetes sin formato.
- **NX_NOT_SUPPORT** (0x4B) No está disponible la compatibilidad con paquetes sin formato.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
UINT raw_packet_filter(NX_IP *ip_ptr, ULONG protocol,
                       NX_PACKET *packet_ptr)
{

/* Simply filter protocol. */
if(protocol == NX_IP_RAW)
   return NX_SUCCESS;
else
   return NX_NOT_SUCCESSFUL;
}

void raw_packet_thread_entry(ULONG id)
{

/* Set the raw packet filter of IP instance. */
status = nx_ip_raw_packet_filter_set(&ip_0,
                                     raw_packet_filter);

/* If status == NX_SUCCESS, the raw packet filter of IP instance
   was successfully set. */
}
```
### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive
Recibir paquete IP sin formato

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio recibe un paquete IP sin formato de la instancia de IP especificada. Si hay paquetes IP en la cola de recepción de paquetes sin formato, el primer paquete (más antiguo) se devuelve al autor de llamada. De lo contrario, si no hay paquetes disponibles, el autor de llamada puede suspender según lo especificado por la opción de espera.

> [!CAUTION]   
> *Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **packet_ptr**: puntero al puntero para colocar el paquete IP sin formato recibido.
- **wait_option**: define cómo se comporta el servicio si no hay ningún paquete disponible. Las opciones de espera se definen de la siguiente forma:
   - **NX_NO_WAIT**: (0x00000000)
   - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
   - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Recepción correcta del paquete IP sin formato.
- **NX_NO_PACKET** (0x01) No hay ningún paquete disponible.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.
- **NX_PTR_ERROR**: (0x07) IP o puntero de paquete devuelto no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Receive a raw IP packet for this IP instance, wait for a maximum
   of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
   variable packet_ptr. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send
Enviar paquete IP sin formato

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```
### <a name="description"></a>Descripción

Este servicio envía un paquete IPv4 sin formato a la dirección IP de destino. Tenga en cuenta que esta rutina vuelve inmediatamente y, por lo tanto, no se conoce si se ha enviado realmente el paquete IP. El controlador de red será responsable de liberar el paquete cuando se complete la transmisión.

En el caso de un sistema de host múltiple, NetX Duo usa la dirección IP de destino para encontrar una interfaz de red adecuada y usa la dirección IP de la interfaz como dirección de origen. Si la dirección IP de destino es de difusión o de multidifusión, se usa la primera interfaz válida. En este caso, las aplicaciones usan ***nx_ip_raw_packet_source_send***.

Para enviar un paquete IPv6 sin formato, la aplicación debe usar el servicio ***nxd_ip_raw_packet_send** _ o _ *_nxd_ip_raw_packet_source_send._**

> [!WARNING]  
> *A menos que se devuelva un error, la aplicación no debe liberar el paquete después de esta llamada. Si lo hace, se producirán resultados imprevisibles, ya que el controlador de red liberará el paquete después de la transmisión.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **packet_ptr**: puntero al paquete IP sin formato que se va a enviar.
- **destination_ip**: dirección IP de destino, que puede ser una dirección IP de host específica, una difusión de red, un bucle interno o una dirección de multidifusión.
- **type_of_service**: define el tipo de servicio para la transmisión. Los valores válidos son los siguientes:
    - **NX_IP_NORMAL**: (0x00000000)
    - **NX_IP_MIN_DELAY**: (0x00100000)
    - **NX_IP_MAX_DATA**: (0x00080000)
    - **NX_IP_MAX_RELIABLE**: (0x00040000)
    - **NX_IP_MIN_COST**: (0x00020000)

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha iniciado correctamente el envío del paquete IP sin formato.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.
- **NX_NOT_ENABLED**: (0x14) La característica de paquete IP sin formato no está habilitada.
- **NX_OPTION_ERROR**: (0x0A) Tipo de servicio no válido.
- **NX_UNDERFLOW**: (0x02) No hay espacio suficiente para anteponer un encabezado IP al paquete.
- **NX_OVERFLOW**: (0x03) El puntero para anexar paquetes no es válido.
- **NX_PTR_ERROR**: (0x07) IP o puntero de paquete no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
                               IP_ADDRESS(1,2,3,5),
                               NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
   packet_ptr has been sent. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_source_send"></a>nx_ip_raw_packet_source_send
Enviar un paquete IP sin formato mediante la interfaz de red especificada

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```
### <a name="description"></a>Descripción

Este servicio envía un paquete IP sin formato a la dirección IP de destino usando la dirección IPv4 local especificada como dirección de origen y mediante la interfaz de red asociada. Tenga en cuenta que esta rutina vuelve inmediatamente y, por lo tanto, no se conoce si se ha enviado realmente el paquete IP. El controlador de red será responsable de liberar el paquete cuando se complete la transmisión. Este servicio difiere de otros servicios, ya que no hay ninguna manera de saber si el paquete se ha enviado realmente. Podría perderse en Internet.

> [!CAUTION]  
> *Tenga en cuenta que debe estar habilitado el procesamiento de paquetes IP sin formato*.

> [!WARNING]  
> *Este servicio es similar a **nx_ip_raw_packet_send**, salvo que este servicio permite a una aplicación enviar paquetes IPv4 sin formato desde una interfaz física especificada*.

### <a name="parameters"></a>Parámetros  

- **ip_ptr**: puntero a la tarea de IP creada anteriormente.
- **packet_ptr**: puntero al paquete que se va a transmitir.
- **destination_ip**: dirección IP a la que se va a enviar el paquete.
- **address_index**: índice de la dirección de la interfaz por la que se va a enviar el paquete.
- **type_of_service**: tipo de servicio del paquete.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha transmitido correctamente el paquete.
- **NX_IP_ADDRESS_ERROR**: (0x21) No hay ninguna interfaz de salida adecuada disponible.
- **NX_NOT_ENABLED** (0x14) No se ha habilitado el procesamiento de paquetes IP sin formato.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) Entrada de puntero no válida.
- **NX_OPTION_ERROR**: (0x0A) Tipo de servicio especificado no válido.
- **NX_OVERFLOW**: (0x03) Puntero de anteposición de paquetes no válido.
- **NX_UNDERFLOW**: (0x02) Puntero de anteposición de paquetes no válido.
- **NX_INVALID_INTERFACE**: (0x4C) Índice de interfaz especificado no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define ADDRESS_IDNEX 1

/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_source_send(ip_ptr, packet_ptr,
                                      destination_ip,
                                      ADDRESS_INDEX,
                                      NX_IP_NORMAL);

/* If status is NX_SUCCESS the packet was successfully
   transmitted. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_receive_queue_max_set"></a>nx_ip_raw_receive_queue_max_set
Establecer el tamaño máximo de la cola de recepción sin formato

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_raw_receive_queue_max_set(
    NX_IP *ip_ptr, 
    ULONG queue_max);
```
### <a name="description"></a>Descripción

Este servicio configura la profundidad máxima de la cola de recepción de paquetes IP sin formato. Tenga en cuenta que la cola de recepción de paquetes IP sin formato se comparte para los paquetes IPv4 e IPv6. Cuando la cola de recepción de paquetes sin formato alcanza la profundidad máxima configurada por el usuario, se quitan los paquetes sin formato recién recibidos. La profundidad predeterminada de la cola de recepción de paquetes IP sin formato es 20.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **queue_max**: nuevo valor para el tamaño de la cola.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha establecido correctamente la profundidad máxima de la cola de recepción sin formato.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
ULONG queue_max = 10;

/* Set the maximum size of the IP raw packet receive queue. */
status = nx_ip_raw_receive_queue_max_set (&ip_0,
                                          queue_max);

/* If status == NX_SUCCESS, the maximum size of the IP raw packet
   receive queue was successfully set. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add
Agregar una ruta estática a la tabla de enrutamiento

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```
### <a name="description"></a>Descripción

Este servicio agrega una entrada a la tabla de enrutamiento estático. Tenga en cuenta que la dirección de *next_hop* debe ser accesible directamente desde uno de los dispositivos de red local.

> [!CAUTION]  
> *Tenga en cuenta que ip_ptr debe apuntar a una estructura IP de NetX Duo válida y que la biblioteca de NetX Duo se debe compilar con NX_ENABLE_IP_STATIC_ROUTING definido para usar este servicio. De manera predeterminada, NetX Duo se compila sin NX_ENABLE_IP_STATIC_ROUTING definido*.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **network_address**: dirección de red de destino, en el orden de bytes del host. 
- **net_mask**: máscara de red de destino, en el orden de bytes del host.
- **next_hop**: dirección del próximo salto para la red de destino, en el orden de bytes del host.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) La entrada se ha agregado a la tabla de enrutamiento estático.
- **NX_OVERFLOW**: (0x03) La tabla de enrutamiento estático está llena.
- **NX_NOT_SUPPORTED**: (0x4B) Esta característica no se ha compilado.
- **NX_IP_ADDRESS_ERROR**: (0x21) El próximo salto no es directamente accesible mediante las interfaces locales.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero ip_ptr no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Specify the next hop for 192.168.1.68 through the gateway
   192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,1,0),
                                0xFFFFFF00UL,
                                IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
   static routing table. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete
Eliminar una ruta estática de la tabla de enrutamiento

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask);
```
### <a name="description"></a>Descripción

Este servicio elimina una entrada de la tabla de enrutamiento estático.

> [!WARNING]  
> *Tenga en cuenta que ip_ptr debe apuntar a una estructura IP de NetX Duo válida y que la biblioteca de NetX Duo se debe compilar con NX_ENABLE_IP_STATIC_ROUTING definido para usar este servicio. De manera predeterminada, NetX Duo se compila sin NX_ENABLE_IP_STATIC_ROUTING definido*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **network_address**: dirección de red de destino, en el orden de bytes del host.
- **net_mask**: máscara de red de destino, en el orden de bytes del host.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha eliminado correctamente de la tabla de enrutamiento estático.
- **NX_NOT_SUCCESSFUL**: (0x43) No se ha encontrado la entrada en la tabla de enrutamiento.
- **NX_NOT_SUPPORTED**: (0x4B) Esta característica no se ha compilado.
- **NX_PTR_ERROR**: (0x07) Puntero ip_ptr no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Remove the static route for 192.168.1.68 from the routing
   table.*/
status = nx_ip_static_route_delete(ip_ptr,
                                   IP_ADDRESS(192,168,1,0),
                                   0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
   the static routing table. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_status_check"></a>nx_ip_status_check
Comprobar el estado de una instancia de IP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio comprueba y, de manera opcional, espera el estado especificado de la interfaz de red primaria de una instancia de IP creada anteriormente. Para obtener el estado de las interfaces secundarias, las aplicaciones deben usar el servicio ***nx_ip_interface_status_check.***

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **needed_status**: estado de IP solicitado, definido en formato de mapa de bits de la siguiente manera:
  - **NX_IP_INITIALIZE_DONE**: (0x0001)
  - **NX_IP_ADDRESS_RESOLVED**: (0x0002)
  - **NX_IP_LINK_ENABLED**: (0x0004)
  - **NX_IP_ARP_ENABLED**: (0x0008)
  - **NX_IP_UDP_ENABLED**: (0x0010)
  - **NX_IP_TCP_ENABLED**: (0x0020)
  - **NX_IP_IGMP_ENABLED**: (0x0040)
  - **NX_IP_RARP_COMPLETE**: (0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED**: (0x0100)
- **actual_status**: puntero al destino del conjunto de bits real.
- **wait_option**: define cómo se comporta el servicio si los bits de estado solicitados no están disponibles. Las opciones de espera se definen de la siguiente forma:
  - **NX_NO_WAIT**: (0x00000000)
  - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)
  - **NX_WAIT_FOREVER**: (0xFFFFFFFF)

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Comprobación de estado de IP correcta.
- **NX_NOT_SUCCESSFUL**: (0x43) La solicitud de estado no se ha satisfecho dentro del tiempo de espera especificado.
- **NX_PTR_ERROR**: (0x07) El puntero IP no es o ha dejado de ser válido o el puntero de estado real no es válido.
- **NX_OPTION_ERROR**: (0x0a) Opción de estado necesario no válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
                            &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
   is up. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ipv4_multicast_interface_join"></a>nx_ipv4_multicast_interface_join
Unir la instancia de IP al grupo de multidifusión especificado mediante una interfaz

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ipv4_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Descripción

Este servicio une una instancia de IP al grupo de multidifusión especificado mediante una interfaz de red especificada. Una vez que la instancia de IP se une a un grupo de multidifusión, la lógica de recepción de IP comienza a reenviar paquetes de datos del grupo de multidifusión a la capa superior. Tenga en cuenta que este servicio se une a un grupo de multidifusión sin enviar informes de IGMP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **group_address**: dirección del grupo de multidifusión IP de clase D que se va a unir en el orden de bytes del host.
- **interface_index**: índice de la interfaz asociada a la instancia de NetX Duo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Unión correcta al grupo de multidifusión.
- **NX_NO_MORE_ENTRIES**: (0x17) No es posible unirse a más grupos de multidifusión; se ha superado el máximo.
- **NX_PTR_ERROR**: (0x07) Puntero no válido a la instancia de IP o la instancia de IP no es válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_EANABLED** (0x14) IGMP no está habilitado en esta instancia de IP.
- **NX_IP_ADDRESS_ERROR**: (0x21) La dirección del grupo de multidifusión proporcionada no es una dirección de clase D válida.
- **NX_INVALID_INTERFACE**: (0x4C) El índice del dispositivo apunta a una interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Previously created IP Instance joins the multicast group
   224.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_join
                                 (&ip IP_ADDRESS(224,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ipv4_multicast_interface_leave"></a>nx_ipv4_multicast_interface_leave
Salir del grupo de multidifusión especificado mediante una interfaz

### <a name="prototype"></a>Prototipo  

```c
UINT nx_ipv4_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Descripción

Este servicio sale del grupo de multidifusión especificado mediante la interfaz de red especificada. Después de cerrar el grupo, este servicio no desencadena la generación de mensajes de IGMP.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **group_address**: dirección del grupo de multidifusión IP de clase D del que se va a salir. La dirección IP está en el orden de bytes del host.
- **interface_index**: índice de la interfaz asociada a la instancia de NetX Duo.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Unión correcta al grupo de multidifusión.
- **NX_ENTRY_NOT_FOUND**: (0x16) no se encuentra la dirección del grupo de multidifusión especificado en la tabla de multidifusión local.
- **NX_INVALID_INTERFACE**: (0x4C) El índice del dispositivo apunta a una interfaz de red no válida.
- **NX_IP_ADDRESS_ERROR**: (0x21) La dirección del grupo de multidifusión proporcionada no es una dirección de clase D válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero no válido a la instancia de IP o la instancia de IP no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Leave the multicast group 224.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_leave
                                (&ip, IP_ADDRESS(224,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_packet_allocate"></a>nx_packet_allocate
Asignar un paquete del grupo especificado

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio asigna un paquete del grupo especificado y ajusta el puntero antepuesto en el paquete según el tipo de paquete especificado. Si no hay ningún paquete disponible, el servicio se suspende según la opción de espera proporcionada.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un grupo de paquetes creado previamente.
- **packet_ptr**: puntero al puntero del puntero del paquete asignado.
- **packet_type**: define el tipo de paquete solicitado. Consulte "Grupos de paquetes" en la página 63 del Capítulo 3 para obtener una lista de los tipos de paquetes admitidos.
- **wait_option**: define el tiempo de espera en tics si no hay paquetes disponibles en el grupo de paquetes. Las opciones de espera se definen de la siguiente forma:
  - **NX_NO_WAIT**: (0x00000000)
  - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
  - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Asignación correcta del paquete.
- **NX_NO_PACKET**: (0x01) No hay ningún paquete disponible.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_INVALID_PARAMETERS**: (0x4D) El tamaño de paquete no admite el protocolo.
- **NX_OPTION_ERROR**: (0x0A) Tipo de paquete no válido.
- **NX_PTR_ERROR**: (0x07) Grupo o puntero de devolución del paquete no válidos.
- **NX_CALLER_ERROR**: (0x11) Opción de espera no válida desde algo que no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR (controladores de red de la aplicación). La opción de espera debe ser *NX_NO_WAIT* cuando se usa en ISR o en el contexto del temporizador.

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Allocate a new UDP packet from the previously created packet pool
   and suspend for a maximum of 5 timer ticks if the pool is
   empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr,
                            NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
   found in the variable packet_ptr. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy
Copiar paquete

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio copia la información del paquete proporcionado en uno o varios paquetes nuevos que se asignan desde el grupo de paquetes proporcionado. Si se realiza correctamente, se devuelve el puntero al nuevo paquete en el destino al que apunta **new_packet_ptr**.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete de origen.
- **new_packet_ptr**: puntero al destino en el que se va a devolver el puntero a la nueva copia del paquete.
- **pool_ptr**: puntero al grupo de paquetes creado anteriormente que se utiliza para asignar uno o varios paquetes para la copia.
- **wait_option**: define cómo espera el servicio si no hay ningún paquete disponible. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Copia correcta de paquetes.
- **NX_NO_PACKET**: (0x01) El paquete no está disponible para la copia.
- **NX_INVALID_PACKET**: (0x12) Error en la copia o el paquete de origen está vacío.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_INVALID_PARAMETERS**: (0x4D) El tamaño de paquete no admite el protocolo.
- **NX_PTR_ERROR**: (0x07) Grupo, paquete o puntero de destino no válidos.
- **NX_UNDERFLOW**: (0x02) Puntero de anteposición de paquetes no válido.
- **NX_OVERFLOW**: (0x03) Puntero de anexión de paquetes no válido.
- **NX_CALLER_ERROR**: (0x11) Se especificó una opción de espera en la inicialización o en una ISR.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
   previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append
Anexar datos al final del paquete

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio anexa datos al final del paquete especificado. El área de datos proporcionada se copia en el paquete. Si no hay suficiente memoria disponible y la característica de paquetes encadenados está habilitada, se asignarán uno o varios paquetes para satisfacer la solicitud. Si la característica de paquetes encadenados no está habilitada, se devuelve *NX_SIZE_ERROR*.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete.
- **data_start**: puntero al inicio del área de datos del usuario que se va a anexar al paquete.
- **data_size**: tamaño del área de datos del usuario.
- **pool_ptr**: puntero al grupo de paquetes desde el que se va a asignar otro paquete si no hay suficiente espacio en el paquete actual.
- **wait_option**: define cómo se comporta el servicio si no hay ningún paquete disponible. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Paquete anexados correctamente.
- **NX_NO_PACKET**: (0x01) No hay ningún paquete disponible.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_INVALID_PARAMETERS**: (0x4D) El tamaño de paquete no admite el protocolo.
- **NX_UNDERFLOW**: (0x02) El puntero antepuesto es menor que el inicio de la carga.
- **NX_OVERFLOW**: (0x03) El puntero anexado es mayor que el final de la carga.
- **NX_PTR_ERROR**: (0x07) Grupo, paquete o puntero de datos no válidos.
- **NX_SIZE_ERROR**: (0x09) Tamaño de datos no válido.
- **NX_CALLER_ERROR**: (0x11) Opción de espera no válida desde algo que no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR (controladores de red de la aplicación)

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
   been appended to the packet. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release


## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset
Extraer datos de un paquete mediante un desplazamiento

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```
### <a name="description"></a>Descripción

Este servicio copia los datos de un paquete de NetX Duo (o cadena de paquetes) a partir del desplazamiento especificado desde el puntero antepuesto del paquete con el tamaño especificado en bytes en el búfer especificado. El número de bytes realmente copiados se devuelve en *bytes_copied*. Este servicio no quita los datos del paquete ni ajusta el puntero antepuesto u otra información de estado interno.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete que se va a extraer.
- **offset**: desplazamiento desde el puntero antepuesto actual.
- **buffer_start**: puntero al inicio del búfer de guardado.
- **buffer_length**: número de bytes que se van a copiar.
- **bytes_copied**: número de bytes copiados realmente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Copia correcta del paquete.
- **NX_PACKET_OFFSET_ERROR**: (0x53) Se ha proporcionado un valor de desplazamiento no válido.
- **NX_PTR_ERROR** (0x07) Puntero de paquete o puntero de búfer no válidos.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

```c
/* Extract 10 bytes from the start of the received packet buffer
   into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
                                       &bytes_copied) ;
/* If status is NX_SUCCESS, 10 bytes were successfully copied into
   the data buffer. */
```
### <a name="see-also"></a>Vea también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve
Recuperar datos de un paquete

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start,
    ULONG *bytes_copied);
```
### <a name="description"></a>Descripción

Este servicio copia los datos del paquete proporcionado en el búfer proporcionado. El número real de bytes copiados se devuelve en el destino al que apunta **bytes_copied**.

Tenga en cuenta que este servicio no cambia el estado interno del paquete. Los datos que se recuperan siguen estando disponibles en el paquete. 

> [!CAUTION]  
> *El búfer de destino debe ser lo suficientemente grande como para contener el contenido del paquete. Si no es así, se dañará la memoria, lo que provocará resultados imprevisibles*.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete de origen.
- **buffer_start**: puntero al inicio del área del búfer.
- **bytes_copied**: puntero al destino para el número de bytes copiados.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Datos del paquete recuperados correctamente.
- **NX_INVALID_PACKET**: (0x12) Paquete no válido.
- **NX_PTR_ERROR**: (0x07) Paquete, inicio de búfer o puntero de bytes copiados no válidos.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
UCHAR                 buffer[512];
ULONG                 bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
   packet, the size of which is contained in "bytes_copied." */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get
Obtener la longitud de los datos de un paquete

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```
### <a name="description"></a>Descripción

Este servicio obtiene la longitud de los datos del paquete especificado.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete.
- **length**: destino de la longitud del paquete.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha obtenido correctamente la longitud del paquete.
- **NX_PTR_ERROR**: (0x07) Puntero de paquete no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create
Crear un grupo de paquetes en el área de memoria especificada

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```
### <a name="description"></a>Descripción

Este servicio crea un grupo de paquetes del tamaño de paquete especificado en el área de memoria proporcionada por el usuario.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero al bloque de control del grupo de paquetes.
- **name**: puntero al nombre de la aplicación para el grupo de paquetes.
- **payload_size**: número de bytes de cada paquete del grupo. Este valor debe ser de al menos 40 bytes y también debe ser divisible por 4.
- **memory_ptr**: puntero al área de memoria en la que se va a colocar el grupo de paquetes. El puntero se debe alinear en un límite ULONG.
- **memory_size**: tamaño del área de memoria del grupo.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Grupo de paquetes creado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero de memoria o grupo no válidos.
- **NX_SIZE_ERROR**: (0x09) Tamaño de memoria o bloque no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Create a packet pool of 32000 bytes starting at physical
   address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
                               (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
   created. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete
Eliminar un grupo de paquetes creado anteriormente

### <a name="prototype"></a>Prototipo  

```c
UINT  nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Descripción

Este servicio elimina un grupo de paquetes creado anteriormente. NetX Duo comprueba si hay subprocesos suspendidos actualmente en los paquetes del grupo de paquetes y borra la suspensión.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero al bloque de control del grupo de paquetes.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Grupo de paquetes eliminado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de grupo no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
   deleted. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get
Recuperar información acerca de un grupo de paquetes

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```
### <a name="description"></a>Descripción

Este servicio recupera información sobre el grupo de paquetes especificado.

> [!IMPORTANT]  
> *Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada*.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un grupo de paquetes creado previamente.
- **total_packets**: puntero al destino para el número total de paquetes del grupo.
- **free_packets**: puntero al destino para el número total de paquetes libres actualmente.
- **empty_pool_requests**: puntero al destino del número total de solicitudes de asignación cuando el grupo estaba vacío.
- **empty_pool_suspensions**: puntero al destino del número total de suspensiones del grupo vacío.
- **invalid_packet_releases**: puntero al destino del número total de liberaciones de paquetes no válidas.

### <a name="return-values"></a>Valores devueltos 

- **TX_SUCCESS**: (0x00) Información del grupo de paquetes recuperada correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
                                 &total_packets,
                                 &free_packets,
                                 &empty_pool_requests,
                                 &empty_pool_suspensions,
                                 &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
   retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_low_watermark_set"></a>nx_packet_pool_low_watermark_set
Establecer la referencia inferior del grupo de paquetes

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_pool_low_watermark_set(
    NX_PACKET_POOL *pool_ptr,
    ULONG low_watermark);
```
### <a name="description"></a>Descripción

Este servicio configura la referencia inferior del grupo de paquetes especificado. Una vez establecido el valor de la referencia inferior, TCP o UDP no pondrán en cola los paquetes recibidos si el número de paquetes disponibles en el grupo de paquetes es menor que la referencia inferior del grupo de paquetes, lo que impide que el grupo de paquetes se quede sin paquetes. Este servicio está disponible si la biblioteca de NetX Duo se compila con la opción ***NX_ENABLE_LOW_WATERMARK*** definida.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero al bloque de control del grupo de paquetes.
- **low_watermark**: valor de la referencia inferior que se va a configurar.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Se ha establecido correctamente el valor de la referencia inferior.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de referencia inferior no se ha compilado en NetX Duo.
- **NX_PTR_ERROR** (0x07) Puntero de grupo no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Set pool_0 low watermark value to 2. */
status = nx_packet_pool_create(&pool_0, 2);

/* If status is NX_SUCCESS, the low watermark value is set for
   pool_0.*/
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release
Liberar un paquete previamente asignado

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>Descripción

Este servicio libera un paquete, incluidos los paquetes adicionales encadenados al paquete especificado. Si otro subproceso está bloqueado en la asignación de paquetes, se le proporciona el paquete y se reanuda.

> [!NOTE]  
> *La aplicación debe impedir que se libere un paquete más de una vez, ya que si lo hace se producirán resultados imprevisibles*.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Paquete liberado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero de paquete no válido.
- **NX_UNDERFLOW**: (0x02) El puntero antepuesto es menor que el inicio de la carga.
- **NX_OVERFLOW**: (0x03) El puntero anexado es mayor que el final de la carga.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR (controladores de red de la aplicación)

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
   packet pool it was allocated from. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release
Liberar un paquete transmitido

### <a name="prototype"></a>Prototipo  

```c
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>Descripción

En el caso de los paquetes que no son TCP, este servicio libera un paquete transmitido, incluidos los paquetes adicionales encadenados al paquete especificado. Si otro subproceso está bloqueado en la asignación de paquetes, se le proporciona el paquete y se reanuda. En el caso de un paquete TCP transmitido, el paquete se marca como transmitido, pero no se libera hasta que se confirma el paquete. Normalmente, se llama a este servicio desde el controlador de red de la aplicación después de que se transmite un paquete.

> [!WARNING] 
> *El controlador de red debe quitar el encabezado del soporte físico y ajustar la longitud del paquete antes de llamar a este servicio*.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Paquete transmitido liberado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero de paquete no válido.
- **NX_UNDERFLOW**: (0x02) El puntero antepuesto es menor que el inicio de la carga.
- **NX_OVERFLOW**: (0x03) El puntero anexado es mayor que el final de la carga.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores y controladores de red de la aplicación (incluidos ISR)

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
/* Release a previously allocated packet that was just transmitted
   from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
   returned to the packet pool it was allocated from. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable
Deshabilitar el protocolo de resolución de direcciones inversa (RARP)

### <a name="prototype"></a>Prototipo  

```c
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita el componente de RARP de NetX Duo para la instancia de IP especificada. En el caso de un sistema de host múltiple, este servicio deshabilita RARP en todas las interfaces.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) RARP deshabilitado correctamente.
- **NX_NOT_ENABLED**: (0x14) RARP no estaba habilitado.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```
### <a name="see-also"></a>Consulte también

- nx_rarp_enable
- nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable
Habilitar el protocolo de resolución de direcciones inversa (RARP)

### <a name="prototype"></a>Prototipo  

```c
UINT nx_rarp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita el componente de RARP de NetX Duo para la instancia de IP especificada. Los componentes de RARP buscan una dirección IP establecida en cero en todas las interfaces de red asociadas. Una dirección IP establecida en cero indica que la interfaz todavía no tiene asignación de dirección IP. RARP intenta resolver la dirección IP mediante la habilitación del proceso de RARP en esa interfaz.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) RARP habilitado correctamente.
- **NX_IP_ADDRESS_ERROR**: (0x21) La dirección IP ya es válida.
- **NX_ALREADY_ENABLED**: (0x15) RARP ya estaba habilitado.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
   resolve this IP instance’s address by querying the network. */
```
### <a name="see-also"></a>Consulte también

- nx_rarp_disable
- nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get
Recuperar información acerca de las actividades de RARP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```
### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de RARP de la instancia de IP especificada.

> [!IMPORTANT]  
> *Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **rarp_requests_sent**: puntero al destino para el número total de solicitudes RARP enviadas.
- **rarp_responses_received**: puntero al destino para el número total de respuestas de RARP recibidas.
- **rarp_invalid_messages**: puntero al destino para el número total de mensajes no válidos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Recuperación correcta de la información de RARP.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Retrieve RARP information from previously created IP
   Instance 0. */
status = nx_rarp_info_get(&ip_0,
                          &rarp_requests_sent,
                          &rarp_responses_received,
                          &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_rarp_disable
- nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize
Inicializar el sistema de NetX Duo

### <a name="prototype"></a>Prototipo  

```c
VOID nx_system_initialize(VOID);
```
### <a name="description"></a>Descripción

Este servicio inicializa los recursos básicos del sistema de NetX Duo como preparación para su uso. La aplicación debe llamarlo durante la inicialización y antes de que se realice cualquier otra llamada a NetX Duo.

### <a name="parameters"></a>Parámetros

Ninguno

### <a name="return-values"></a>Valores devueltos

Ninguno

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

Administración del sistema

### <a name="example"></a>Ejemplo

```c
/* Initialize NetX Duo for operation. */
nx_system_initialize();

/* At this point, NetX Duo is ready for IP creation and all
   subsequent network operations. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind
Enlazar el socket TCP de cliente al puerto TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio enlaza el socket de cliente TCP creado previamente al puerto TCP especificado. El intervalo de sockets TCP válidos va de 0 a 0xFFFF. Si el puerto TCP especificado no está disponible, el servicio se suspende según la opción de espera proporcionada.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket TCP creada anteriormente.
- **port**: número de puerto que se va a enlazar (de 1 a 0xFFFF). Si el número de puerto es NX_ANY_PORT (0x0000), la instancia de IP buscará el siguiente puerto libre y lo utilizará para el enlace.
- **wait_option**: define cómo se comporta el servicio si el puerto ya está enlazado a otro socket. Las opciones de espera se definen de la siguiente forma:
- **NX_NO_WAIT**: (0x00000000)
- **NX_WAIT_FOREVER**: (0xFFFFFFFF)
- **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Socket enlazado correctamente.
- **NX_ALREADY_BOUND**: (0x22) Este socket ya está enlazado a otro puerto TCP.
- **NX_PORT_UNAVAILABLE**: (0x23) El puerto ya está enlazado a otro socket.
- **NX_NO_FREE_PORTS**: (0x45) No hay ningún puerto libre.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_INVALID_PORT**: (0x46) Puerto no válido.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Bind a previously created client socket to port 12 and wait for 7
   timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
   bound to port 12 on the associated IP instance. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect
Conectar socket TCP de cliente

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio conecta el socket de cliente TCP creado y enlazado previamente al puerto del servidor especificado. Los puertos de servidor TCP válidos oscilan entre 0 y 0xFFFF. Si la conexión no se completa inmediatamente, el servicio se suspende según la opción de espera proporcionada.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket TCP creada anteriormente.
- **server_ip**: dirección IP del servidor.
- **server_port**: número de puerto del servidor al que conectarse (de 1 a 0xFFFF).
- **wait_option**: define cómo se comporta el servicio mientras se establece la conexión. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Socket conectado correctamente.
- **NX_NOT_BOUND**: (0x24) El socket no está enlazado.
- **NX_NOT_CLOSED**: (0x35) El socket no está en estado cerrado.
- **NX_IN_PROGRESS**: (0x37) No se ha especificado ninguna espera, el intento de conexión está en curso.
- **NX_INVALID_INTERFACE**: (0x4C) Interfaz proporcionada no válida.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP del servidor no válida.
- **NX_INVALID_PORT**: (0x46) Puerto no válido.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Initiate a TCP connection from a previously created and bound
   client socket. The connection requested in this example is to
   port 12 on the server with the IP address of 1.2.3.5. This
   service will wait 300 timer ticks for the connection to take
   place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
                                      IP_ADDRESS(1,2,3,5),
                                      12, 300);

/* If status is NX_SUCCESS, the previously created and bound
   client_socket is connected to port 12 on IP 1.2.3.5. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get
Obtener el número de puerto enlazado al socket TCP de cliente

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>Descripción

Este servicio recupera el número de puerto asociado al socket, lo que resulta útil para encontrar el puerto asignado por NetX Duo en situaciones en las que se especificó NX_ANY_PORT en el momento en que se enlazó el socket.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket TCP creada anteriormente.
- **port_ptr**: puntero al destino del número de puerto devuelto. Los números de puerto válidos son del 1 al 0xFFFF.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Socket enlazado correctamente.
- **NX_NOT_BOUND**: (0x24) Este socket no está enlazado a un puerto.
- **NX_PTR_ERROR**: (0x07) Puntero de socket o puntero de devolución de puerto no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Get the port number of previously created and bound client
   socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind
Desenlazar el socket de cliente TCP del puerto TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descripción

Este servicio libera el enlace entre el socket de cliente TCP y un puerto TCP. Si hay otros subprocesos en espera de enlazar otro socket al mismo número de puerto, el primer subproceso suspendido se enlaza a este puerto.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket TCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Socket desenlazado correctamente.
- **NX_NOT_BOUND**: (0x24) El socket no estaba enlazado a ningún puerto.
- **NX_NOT_CLOSED**: (0x35) El socket no se ha desconectado.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
   bound. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_enable"></a>nx_tcp_enable
Habilitar el componente de TCP de NetX Duo

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita el componente del protocolo de control de transmisión (TCP) de NetX Duo. Una vez habilitado, la aplicación puede establecer conexiones TCP.

### <a name="parameters"></a>Parámetros  

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) TCP habilitado correctamente.
- **NX_ALREADY_ENABLED**: (0x15) TCP ya está habilitado.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find
Buscar el siguiente puerto TCP disponible

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>Descripción

Este servicio intenta buscar un puerto TCP libre (sin enlazar) a partir del puerto proporcionado por la aplicación. La lógica de búsqueda volverá a empezar si la búsqueda alcanza el valor máximo de puerto de 0xFFFF. Si la búsqueda tiene éxito, se devuelve el puerto libre en la variable a la que apunta *free_port_ptr*.

> [!WARNING]  
> *Se puede llamar a este servicio desde otro subproceso y hacer que se devuelva el mismo puerto. Para evitar esta condición de carrera, es posible que la aplicación desee colocar este servicio y el enlace del socket de cliente real bajo la protección de una exclusión mutua*.

### <a name="parameters"></a>Parámetros  

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **port**: número de puerto en el que se va a iniciar la búsqueda (de 1 a 0xFFFF).
- **free_port_ptr**: puntero al valor devuelto del puerto libre de destino.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha encontrado un puerto libre.
- **NX_NO_FREE_PORTS**: (0x45) No se ha encontrado ningún puerto libre.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.
- **NX_INVALID_PORT**: (0x46) El número de puerto especificado no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Locate a free TCP port, starting at port 12, on a previously
   created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
   on the IP instance. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get
Recuperar información acerca de las actividades de TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```
### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de TCP de la instancia de IP especificada.

> [!IMPORTANT]  
> *Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **tcp_packets_sent**: puntero al destino para el número total de paquetes TCP enviados.
- **tcp_bytes_sent**: puntero al destino para el número total de bytes TCP enviados.
- **tcp_packets_received**: puntero al destino del número total de paquetes TCP recibidos.
- **tcp_bytes_received**: puntero al destino del número total de bytes TCP recibidos.
- **tcp_invalid_packets**: puntero al destino del número total de paquetes TCP no válidos.
- **tcp_receive_packets_dropped**: puntero al destino del número total de paquetes TCP recibidos eliminados.
- **tcp_checksum_errors**: puntero al destino del número total de paquetes TCP con errores de suma de comprobación.
- **tcp_connections**: puntero al destino del número total de conexiones TCP.
- **tcp_disconnections**: puntero al destino del número total de desconexiones TCP.
- **tcp_connections_dropped**: puntero al destino del número total de conexiones TCP eliminadas.
- **tcp_retransmit_packets**: puntero al destino del número total de paquetes TCP retransmitidos.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Recuperación correcta de la información de TCP.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Retrieve TCP information from previously created IP Instance
   ip_0. */
status = nx_tcp_info_get(&ip_0,
                         &tcp_packets_sent,
                         &tcp_bytes_sent,
                         &tcp_packets_received,
                         &tcp_bytes_received,
                         &tcp_invalid_packets,
                         &tcp_receive_packets_dropped,
                         &tcp_checksum_errors,
                         &tcp_connections,
                         &tcp_disconnections
                         &tcp_connections_dropped,
                         &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept
Aceptar conexión TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio acepta (o se prepara para aceptar) una solicitud de conexión de socket de cliente TCP para un puerto que se configuró previamente para la escucha. Este servicio se puede llamar inmediatamente después de que la aplicación llame al servicio de escucha o de reescucha, o después de que se llame a la rutina de devolución de llamada de escucha cuando la conexión de cliente esté realmente presente. Si no se puede establecer una conexión de inmediato, el servicio se suspende según la opción de espera proporcionada.

> [!WARNING]  
> *La aplicación debe llamar a **nx_tcp_server_socket_unaccept** cuando ya no se necesite la conexión para quitar el enlace del socket de servidor al puerto del servidor*.

> [!IMPORTANT]  
> *Se llama a las rutinas de devolución de llamada de la aplicación desde el subproceso auxiliar de IP.*

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al bloque de control del socket de servidor TCP.
- **wait_option**: define cómo se comporta el servicio mientras se establece la conexión. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Aceptación correcta del socket de servidor TCP (conexión pasiva).
- **NX_NOT_LISTEN_STATE**: (0x36) El socket de servidor proporcionado no está en estado de escucha.
- **NX_IN_PROGRESS**: (0x37) No se ha especificado ninguna espera, el intento de conexión está en curso.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_PTR_ERROR**: (0x07) Error de puntero de socket.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
       example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
NX_PACKET *my_packet;
UINT status, i;
    /* Assuming that:
       "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
                         "Port 12 Server Socket",
                          NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                          NX_IP_TIME_TO_LIVE, 100,
                          NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                port_12_connect_request);

    /* Loop to process 5 server connections, sending
       "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {

        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
           complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {

            /* Allocate a packet for the "Hello_and_Goodbye"
               message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                         NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                  sizeof("Hello_and_Goodbye"),
                                  &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
               /* Error, release the packet. */
               nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
         }

         /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
            again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }

     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen
Habilitar la escucha para la conexión de cliente en el puerto TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```
### <a name="description"></a>Descripción

Este servicio habilita la escucha de una solicitud de conexión de cliente en el puerto TCP especificado. Cuando se recibe una solicitud de conexión de cliente, el socket de servidor proporcionado se enlaza al puerto especificado y se llama a la función de devolución de llamada de escucha proporcionada.

El procesamiento de la rutina de devolución de llamada de escucha depende completamente de la aplicación. Puede contener lógica para reactivar un subproceso de la aplicación que posteriormente realiza una operación de aceptación. Si la aplicación ya tiene un subproceso suspendido en el procesamiento de aceptación para este socket, es posible que la rutina de devolución de llamada de escucha no sea necesaria.

Si la aplicación desea controlar conexiones de cliente adicionales en el mismo puerto, se debe llamar a ***nx_tcp_server_socket_relisten*** con un socket disponible (un socket en estado CLOSED) para la conexión siguiente. Hasta que se llame al servicio de reescucha, las conexiones de cliente adicionales se ponen en cola. Cuando se supera la profundidad máxima de la cola, se elimina la solicitud de conexión más antigua para poner en cola la nueva solicitud de conexión. Este servicio especifica la profundidad máxima de la cola.

> [!IMPORTANT]  
> *Se llama a las rutinas de devolución de llamada de la aplicación desde el subproceso auxiliar de IP.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **port**: número de puerto en el que se va a escuchar (de 1 a 0xFFFF).
- **socket_ptr**: puntero al socket que se va a utilizar para la conexión.
- **listen_queue_size**: número de solicitudes de conexión de cliente que se pueden poner en cola.
- **listen_callback**: función de la aplicación a la que se llamará cuando se reciba la conexión. Si se especifica un valor NULL, se deshabilita la característica de devolución de llamada de escucha.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Escucha de puerto TCP habilitada correctamente.
- **NX_MAX_LISTEN**: (0x33) No hay más estructuras de solicitud de escucha disponibles. La constante NX_MAX_LISTEN_REQUESTS del archivo **_nx_api.h_** define el número de solicitudes de escucha activas posibles.
- **NX_NOT_CLOSED**: (0x35) El socket de servidor proporcionado no está en estado cerrado.
- **NX_ALREADY_BOUND**: (0x22) El socket de servidor proporcionado ya está enlazado a un puerto.
- **NX_DUPLICATE_LISTEN**: (0x34) Ya existe una solicitud de escucha activa para este puerto.
- **NX_INVALID_PORT**: (0x46) Puerto especificado no válido.
- **NX_PTR_ERROR**: (0x07) IP o puntero de socket no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
   /* Simply set the semaphore to wake up the server thread.*/
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket.
   This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
NX_PACKET *my_packet;
UINT status, i;
   /* Assuming that:
      "port_12_semaphore" has already been created with an
      initial count of 0 "my_ip" has already been created
      and the link is enabled "my_pool" packet pool has already
      been created.
   */

   /* Create the server socket. */
   nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
                        Socket",
                        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                        NX_IP_TIME_TO_LIVE, 100,
                        NX_NULL, port_12_disconnect_request);

   /* Setup server listening on port 12. */
   nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                               port_12_connect_request);

   /* Loop to process 5 server connections, sending
      "Hello_and_Goodbye" to
      each client and then disconnecting. */
   for (i = 0; i < 5; i++)
   {

        /* Get the semaphore that indicates a client connection
           request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection
           to complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
           if (status == NX_SUCCESS)
        {

              /* Allocate a packet for the "Hello_and_Goodbye"
                 message. */
              nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                 NX_WAIT_FOREVER);

              /* Place "Hello_and_Goodbye" in the packet. */
              nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                    sizeof("Hello_and_Goodbye"),
                                    &my_pool,
                                    NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
         }
         /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
         again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }
     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);
     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten
Reescuchar la conexión de cliente en el puerto TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descripción

Se llama a este servicio después de que se haya recibido una conexión en un puerto que se configuró anteriormente para la escucha. El propósito principal de este servicio es proporcionar un nuevo socket de servidor para la siguiente conexión de cliente. Si una solicitud de conexión se pone en cola, la conexión se procesará inmediatamente durante esta llamada al servicio.

> [!IMPORTANT]  
> *También se llama a la misma rutina de devolución de llamada especificada por la solicitud de escucha original cuando existe una conexión para este nuevo socket de servidor*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **port**: número de puerto en el que se va a reescuchar (de 1 a 0xFFFF).
- **socket_ptr**: socket que se va a usar para la siguiente conexión de cliente.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Reescucha de puerto TCP correcta.
- **NX_NOT_CLOSED**: (0x35) El socket de servidor proporcionado no está en estado cerrado.
- **NX_ALREADY_BOUND**: (0x22) El socket de servidor proporcionado ya está enlazado a un puerto.
- **NX_INVALID_RELISTEN**: (0x47) Ya hay un puntero de socket válido para este puerto o el puerto especificado no tiene una solicitud de escucha activa.
- **NX_CONNECTION_PENDING**: (0x48) Igual que NX_SUCCESS, salvo que había una solicitud de conexión en cola y se procesó durante esta llamada.
- **NX_INVALID_PORT**: (0x46) Puerto especificado no válido.
- **NX_PTR_ERROR**: (0x07) Dirección IP o puntero de devolución de llamada de escucha no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

   /* Simply set the semaphore to wake up the server thread.*/
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket. This
      example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET *my_packet;
UINT status, i;

   /* Assuming that:
     "port_12_semaphore" has already been created with an initial
     count of 0.
    "my_ip" has already been created and the link is enabled.
    "my_pool" packet pool has already been created. */

   /* Create the server socket. */
   nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
                                 NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                 NX_IP_TIME_TO_LIVE, 100,
                                 NX_NULL, port_12_disconnect_request);

   /* Setup server listening on port 12. */
   nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                               port_12_connect_request);

   /* Loop to process 5 server connections, sending
      "Hello_and_Goodbye" to each client then disconnecting. */
   for (i = 0; i < 5; i++)
   {

       /* Get the semaphore that indicates a client connection
          request is present. */
       tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

       /* Wait for 200 ticks for the client socket connection to
          complete. */
       status = nx_tcp_server_socket_accept(&server_socket, 200);

       /* Check for a successful connection. */
          if (status == NX_SUCCESS)
       {

             /* Allocate a packet for the "Hello_and_Goodbye"
                message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                   sizeof("Hello_and_Goodbye"),
                                   &my_pool, NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
         }

         /* Unaccept the server socket. Note that unaccept is
            called even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
            again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }

     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept
Quitar la asociación de un socket con el puerto de escucha

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descripción

Este servicio quita la asociación entre este socket de servidor y el puerto del servidor especificado. La aplicación debe llamar a este servicio después de una desconexión o después de una llamada de aceptación incorrecta.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket de servidor configurado previamente.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Finalización correcta de la aceptación del socket de servidor.
- **NX_NOT_LISTEN_STATE**: (0x36) El socket de servidor está en un estado inadecuado y probablemente no esté desconectado.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NX_PACKET_POOL        my_pool;
NX_IP                 my_ip;
NX_TCP_SOCKET         server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

   /* Simply set the semaphore to wake up the server thread. */
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket. This example
   doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET  *my_packet;
UINT       status, i;

   /* Assuming that:
     "port_12_semaphore" has already been created with an initial count
      of 0 "my_ip" has already been created and the link is enabled
     "my_pool" packet pool has already been created
   */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
                         Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                         NX_IP_TIME_TO_LIVE, 100,NX_NULL,
                         port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
       to
       each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {

        /* Get the semaphore that indicates a client connection request
           is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
           complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

       /* Check for a successful connection. */
          if (status == NX_SUCCESS)
       {
             /* Allocate a packet for the "Hello_and_Goodbye" message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet,
                      "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                      &my_pool, NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
       }

       /* Unaccept the server socket. Note that unaccept is called even
          if disconnect or accept fails. */
       nx_tcp_server_socket_unaccept(&server_socket);

      /* Setup server socket for listening with this socket again. */
      nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten
Deshabilitar la escucha para la conexión de cliente en el puerto TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_server_socket_unlisten(
    NX_IP *ip_ptr, 
    UINT port);
```
### <a name="description"></a>Descripción

Este servicio deshabilita la escucha de una solicitud de conexión de cliente en el puerto TCP especificado.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **port**: número de puerto en el que se va a deshabilitar la escucha (de 0 a 0xFFFF).

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Escucha de puerto TCP deshabilitada correctamente.
- **NX_ENTRY_NOT_FOUND**: (0x16) La escucha no estaba habilitada para el puerto especificado.
- **NX_INVALID_PORT**: (0x46) Puerto especificado no válido.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NX_PACKET_POOL       my_pool;
NX_IP                my_ip;
NX_TCP_SOCKET        server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

     /* Simply set the semaphore to wake up the server thread. */
     tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{

     /* The client has initiated a disconnect on this socket. This example
        doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET *my_packet;
UINT status, i;

     /* Assuming that:
       "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
       "my_pool" packet pool has already been created
     */

     /* Create the server socket. */
     nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
                          NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                          NX_IP_TIME_TO_LIVE, 100,
                          NX_NULL, port_12_disconnect_request);

     /* Setup server listening on port 12. */
     nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                 port_12_connect_request);

     /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
     for (i = 0; i < 5; i++)
     {

         /* Get the semaphore that indicates a client connection request is
            present. */
         tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

         /* Wait for 200 ticks for the client socket connection to complete.*/
         status = nx_tcp_server_socket_accept(&server_socket, 200);

         /* Check for a successful connection. */
         if (status == NX_SUCCESS)
         {

             /* Allocate a packet for the "Hello_and_Goodbye" message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                   sizeof("Hello_and_Goodbye"), &my_pool,
                                   NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
          }

          /* Unaccept the server socket. Note that unaccept is called even if
             disconnect or accept fails. */
          nx_tcp_server_socket_unaccept(&server_socket);

          /* Setup server socket for listening with this socket again. */
          nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }
  
     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available
Recuperar el número de bytes disponibles para su recuperación

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```
### <a name="description"></a>Descripción

Este servicio obtiene el número de bytes disponibles para su recuperación en el socket TCP especificado. Tenga en cuenta que el socket TCP ya debe estar conectado.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket TCP creado y conectado anteriormente.
- **bytes_available**: puntero al destino para los bytes disponibles.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) El servicio se ejecuta correctamente. Se devuelve el número de bytes disponibles para la lectura al autor de llamada.
- **NX_NOT_CONNECTED**: (0x38) El socket no está en estado conectado.
- **NX_PTR_ERROR**: (0x07) Punteros no válidos.
- **NX_NOT_ENABLED**: (0x14) TCP no está habilitado.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,&bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
   bytes_available. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create
Crear un cliente TCP o un socket de servidor

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, 
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descripción

Este servicio crea un cliente TCP o un socket de servidor para la instancia de IP especificada.

> [!NOTE]  
> *Se llama a las rutinas de devolución de llamada de la aplicación desde el subproceso asociado a esta instancia de IP.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **socket_ptr**: puntero al bloque de control del nuevo socket TCP.
- **name**: nombre de la aplicación para este socket TCP.
- **type_of_service**: define el tipo de servicio para la transmisión. Los valores válidos son los siguientes:
    - **NX_IP_NORMAL**: (0x00000000)
    - **NX_IP_MIN_DELAY**: (0x00100000)
    - **NX_IP_MAX_DATA**: (0x00080000)
    - **NX_IP_MAX_RELIABLE**: (0x00040000)
    - **NX_IP_MIN_COST**: (0x00020000)
- **fragment**: especifica si se permite o no la fragmentación de IP. Si se especifica NX_FRAGMENT_OKAY** (0x0), se permite la fragmentación de IP. Si se especifica NX_DONT_FRAGMENT (0x4000), se deshabilita la fragmentación de IP.
- **time_to_live**: especifica el valor de 8 bits que define el número de enrutadores que puede pasar este paquete antes de que se descarte. NX_IP_TIME_TO_LIVE especifica el valor predeterminado.
- **window_size**: define el número máximo de bytes permitidos en la cola de recepción de este socket.
- **urgent_data_callback**: función de la aplicación a la que se llama cada vez que se detectan datos urgentes en el flujo de recepción. Si este valor es NX_NULL, se omiten los datos urgentes.
- **disconnect_callback**: función de la aplicación a la que se llama siempre que el socket emite una desconexión en el otro extremo de la conexión. Si este valor es NX_NULL, se deshabilita la función de devolución de llamada de desconexión.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Socket de cliente TCP creado correctamente.
- **NX_OPTION_ERROR**: (0x0A) Tipo de servicio, fragmento, tamaño de ventana u opción de período de vida no válidos.
- **NX_PTR_ERROR**: (0x07) IP o puntero de socket no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Create a TCP client socket on the previously created IP instance,
   with normal delivery, IP fragmentation enabled, 0x80 time to
   live, a 200-byte receive window, no urgent callback routine, and
   the "client_disconnect" routine to handle disconnection initiated
   from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
                             "Client Socket",
                             NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                             0x80, 200, NX_NULL
                             client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
   to be bound. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete
Eliminar un socket TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina un socket TCP creado anteriormente. Si el socket sigue enlazado o conectado, el servicio devuelve un código de error.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: socket TCP creado previamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Socket eliminado correctamente.
- **NX_NOT_CREATED**: (0x27) No se ha creado el socket.
- **NX_STILL_BOUND**: (0x42) El socket sigue estando enlazado.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect
Desconectar las conexiones de socket de cliente y servidor

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio desconecta una conexión de socket de servidor o cliente establecida. Una desconexión de un socket de servidor debe ir seguida de una solicitud de desaceptación, mientras que un socket de cliente que se desconecta se deja en un estado listo para otra solicitud de conexión. Si el proceso de desconexión no puede finalizar inmediatamente, el servicio se suspende según la opción de espera proporcionada.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.
- **wait_option**: define cómo se comporta el servicio mientras la desconexión está en curso. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Socket desconectado correctamente.
- **NX_NOT_CONNECTED**: (0x38) El socket especificado no está conectado.
- **NX_IN_PROGRESS**: (0x37) La desconexión está en curso, no se especificó ninguna espera.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí 

### <a name="example"></a>Ejemplo 

```c
/* Disconnect from a previously established connection and wait a
   maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
   as a result of the client socket connect or the server accept) is
   disconnected. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify
Instalar la función de devolución de llamada de notificación de finalización de la desconexión TCP
 
### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada que se invoca después de que se complete una operación de desconexión del socket. La función de devolución de llamada de finalización de la desconexión del socket TCP está disponible si NetX Duo se compila con la opción ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definida.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.
- **tcp_disconnect_complete_notify**: función de devolución de llamada que se va a instalar.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) La función de devolución de llamada se ha registrado correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de notificación extendida no se ha compilado en la biblioteca de NetX Duo. NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) La característica de TCP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
                                                  callback);
```
### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_setnx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify
Establecer la función de devolución de llamada de notificación de establecimiento de TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada a la que se llama después de que un socket TCP realice una conexión. La función de devolución de llamada de establecimiento de socket TCP está disponible si se compila NetX Duo con la opción ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definida.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.
- **tcp_establish_notify**: función de devolución de llamada invocada después de establecer una conexión TCP.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) La función de notificación se ha establecido correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de notificación extendida no se ha compilado en la biblioteca de NetX Duo. 
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) La aplicación no ha habilitado TCP.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Set the function pointer "callback" as the notify function NetX
   Duo will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```
### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get
Recuperar información acerca de las actividades del socket TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```
### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de socket TCP de la instancia de socket TCP especificada.

> [!NOTE]  
> *Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada*.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket TCP creada anteriormente.
- **tcp_packets_sent**: puntero al destino para el número total de paquetes TCP enviados en el socket.
- **tcp_bytes_sent**: puntero al destino para el número total de bytes TCP enviados en el socket.
- **tcp_packets_received**: puntero al destino del número total de paquetes TCP recibidos en el socket.
- **tcp_bytes_received**: puntero al destino del número total de bytes TCP recibidos en el socket.
- **tcp_retransmit_packets**: puntero al destino del número total de retransmisiones de paquetes TCP.
- **tcp_packets_queued**: puntero al destino del número total de paquetes TCP en cola en el socket.
- **tcp_checksum_errors**: puntero al destino del número total de paquetes TCP con errores de suma de comprobación en el socket.
- **tcp_socket_state**: puntero al destino del estado actual del socket.
- **tcp_transmit_queue_depth**: puntero al destino del número total de paquetes transmitidos que están en la cola en espera de confirmación.
- **tcp_transmit_window**: puntero al destino del tamaño de la ventana de transmisión actual.
- **tcp_receive_window**: puntero al destino del tamaño de la ventana de recepción actual.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Recuperación correcta de la información del socket TCP.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido. 
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Retrieve TCP socket information from previously created
   socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
                                &tcp_packets_sent,
                                &tcp_bytes_sent,
                                &tcp_packets_received,
                                &tcp_bytes_received,
                                &tcp_retransmit_packets,
                                &tcp_packets_queued,
                                &tcp_checksum_errors,
                                &tcp_socket_state,
                                &tcp_transmit_queue_depth,
                                &tcp_transmit_window,
                                &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get
Obtener MSS del socket

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```
### <a name="description"></a>Descripción

Este servicio recupera el tamaño máximo de segmento (MSS) local del socket especificado.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket creado anteriormente.
- **mss**: destino para el valor de MSS devuelto.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) MSS obtenido correctamente.
- **NX_PTR_ERROR**: (0x07) Socket o puntero de destino del valor de MSS no válidos.
- **NX_NOT_ENABLED**: (0x14) TCP no está habilitado.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada no es un subproceso ni una inicialización.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket's current MSS value. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get
Obtener MSS del socket TCP del nodo del mismo nivel

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *mss);
```
### <a name="description"></a>Descripción

Este servicio recupera el tamaño máximo de segmento (MSS) anunciado por el socket del nodo del mismo nivel.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket creado y conectado anteriormente.
- **mss**: destino para devolver el valor de MSS.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) MSS del nodo del mismo nivel obtenido correctamente.
- **NX_PTR_ERROR**: (0x07) Socket o puntero de destino del valor de MSS no válidos.
- **NX_NOT_ENABLED**: (0x14) TCP no está habilitado.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada no es un subproceso ni una inicialización.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket peer’s advertised MSS value. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set
Establecer MSS del socket

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```
### <a name="description"></a>Descripción

Este servicio establece el tamaño máximo de segmento (MSS) del socket especificado. Tenga en cuenta que el valor de MSS debe estar dentro de la MTU de IP de la interfaz de red, lo que permite espacio para los encabezados IP y TCP.

Se debe usar este servicio antes de que un socket TCP inicie el proceso de conexión. Si se usa el servicio después de establecer una conexión TCP, el nuevo valor no tiene ningún efecto en la conexión.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket creado anteriormente.
- **mss**: valor de MSS que se va a establecer.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) MSS establecido correctamente.
- **NX_SIZE_ERROR**: (0x09) El valor de MSS especificado es demasiado grande.
- **NX_NOT_CONNECTED**: (0x38) No se ha establecido la conexión TCP. 
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_NOT_ENABLED**: (0x14) TCP no está habilitado.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada no es un subproceso ni una inicialización.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get
Recuperar información sobre el socket TCP del nodo del mismo nivel

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>Descripción

Este servicio recupera la información de puerto y dirección IP del nodo del mismo nivel para el socket TCP conectado mediante la red IPv4. El servicio equivalente que también admite una red IPv6 es ***nxd_tcp_socket_peer_info_get***.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.
- **peer_ip_address**: puntero al destino de la dirección IP del nodo del mismo nivel, en el orden de bytes del host.
- **peer_port**: puntero al destino del número de puerto del nodo del mismo nivel, en el orden de bytes del host.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) El servicio se ejecuta correctamente. El número de puerto y la dirección IP del nodo del mismo nivel se devuelven al autor de llamada.
- **NX_NOT_CONNECTED**: (0x38) El socket no está en estado conectado.
- **NX_PTR_ERROR**: (0x07) Punteros no válidos.
- **NX_NOT_ENABLED**: (0x14) TCP no está habilitado.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
                                     &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_queue_depth_notify_set"></a>nx_tcp_socket_queue_depth_notify_set
Establecer la función de notificación de la cola de transmisión de TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_queue_depth_notify_set(
              NX_TCP_SOCKET *socket_ptr,
              VOID(*tcp_socket_queue_depth_notify)(NX_TCP_SOCKET *));
```
### <a name="description"></a>Descripción

Este servicio establece la función de notificación de la actualización de la profundidad de la cola de transmisión especificada por la aplicación, a la que se llama cada vez que el socket especificado determina que ha liberado paquetes de la cola de transmisión, de modo que la profundidad de la cola ya no supera su límite. Si una aplicación estuviera bloqueada en la transmisión debido a la profundidad de la cola, la función de devolución de llamada sirve como una notificación a la aplicación de que puede iniciar la transmisión de nuevo. Este servicio solo está disponible si se compila la biblioteca de NetX Duo con la opción ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY*** definida.

### <a name="parameters"></a>Parámetros 

- **socket_ptr**: puntero a la estructura del socket. 
- **tcp_socket_queue_depth_notify**: función de notificación que se va a instalar.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Se ha instalado correctamente la función de notificación.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de notificación de la profundidad de la cola del socket TCP no se ha compilado en la biblioteca de NetX Duo.
- **NX_PTR_ERROR**: (0x07) Puntero no válido al bloque de control del socket o a la función de notificación.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) La característica de TCP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
VOID tcp_socket_queue_depth_notify(NX_TCP_SOCKET *socket_ptr)
{
   /* Notify the application to resume sending. */

}
/* Install the TCP transmit queue notify function .*/
status = nxd_tcp_socket_queue_depth_notify_set(&tcp_socket,
                                  tcp_socket_queue_depth_notify);

/* If status == NX_SUCCESS, the callback function is successfully
   installed. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive
Recibir datos de un socket TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio recibe datos TCP del socket especificado. Si no hay datos en cola en el socket especificado, el autor de llamada se suspende en función de la opción de espera proporcionada.

> [!CAUTION]  
> *Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite*.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket TCP creada anteriormente.
- **packet_ptr**: puntero al puntero del paquete TCP.
- **wait_option**: define cómo se comporta el servicio si no hay ningún dato en la cola actualmente en este socket. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Datos del socket recibidos correctamente.
- **NX_NOT_BOUND**: (0x24) El socket todavía no está enlazado.
- **NX_NO_PACKET**: (0x01) No se ha recibido ningún dato.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_NOT_CONNECTED**: (0x38) El socket ya no está conectado.
- **NX_PTR_ERROR**: (0x07) Socket o puntero de paquete devuelto no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Receive a packet from the previously created and connected TCP
   client socket. If no packet is available, wait for 200 timer
   ticks before giving up. */
status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* If status is NX_SUCCESS, the received packet is pointed to by
   "packet_ptr". */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify
Notificar a la aplicación sobre los paquetes recibidos

### <a name="prototype"></a>Prototipo   

```c
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr, 
    VOID (*tcp_receive_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descripción 

Este servicio configura el puntero de la función de notificación de recepción con la función de devolución de llamada especificada por la aplicación. A continuación, se llama a esta función de devolución de llamada siempre que se reciban uno o varios paquetes en el socket. Si se proporciona un puntero NX_NULL, la función de notificación se deshabilita.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket TCP.
- **tcp_receive_notify**: puntero a la función de devolución de llamada de la aplicación a la que se llama cuando se reciben uno o varios paquetes en el socket.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Notificación correcta de recepción en el socket.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) La característica de TCP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Setup a receive packet callback function for the "client_socket"
   socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever one or more packets are received for
   "client_socket". */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send
Enviar datos mediante un socket TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio envía datos TCP mediante un socket TCP previamente conectado. Si el último tamaño de ventana anunciado del receptor es menor que esta solicitud, el servicio se suspende opcionalmente en función de la opción de espera especificada. Este servicio garantiza que no se envíen datos de paquetes mayores que el valor de MSS a la capa IP. 

> [!WARNING]  
> *A menos que se devuelva un error, la aplicación no debe liberar el paquete después de esta llamada. Si lo hace, se producirán resultados imprevisibles, ya que el controlador de red también intentará liberar el paquete después de la transmisión*.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket TCP conectada anteriormente.
- **packet_ptr**: puntero al paquete de datos TCP.
- **wait_option**: define cómo se comporta el servicio si la solicitud es mayor que el tamaño de la ventana del receptor. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Envío correcto del socket.
- **NX_NOT_BOUND**: (0x24) El socket no estaba enlazado a ningún puerto.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) No se ha encontrado ninguna interfaz de salida adecuada.
- **NX_NOT_CONNECTED**: (0x38) El socket ya no está conectado.
- **NX_WINDOW_OVERFLOW**: (0x39) La solicitud es mayor que el tamaño en bytes anunciado de la ventana del receptor.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_INVALID_PACKET**: (0x12) No se ha asignado el paquete.
- **NX_TX_QUEUE_DEPTH**: (0x49) Se ha alcanzado la profundidad máxima de la cola de transmisión.
- **NX_OVERFLOW**: (0x03) El puntero para anexar paquetes no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.
- **NX_UNDERFLOW**: (0x02) El puntero de anteposición del paquete no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Send a packet out on the previously created and connected TCP
   socket. If the receive window on the other side of the connection
   is less than the packet size, wait 200 timer ticks before giving
   up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait
Esperar a que el socket TCP entre en un estado específico

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio espera a que el socket entre en el estado deseado. Si el socket no está en el estado deseado, el servicio se suspende según la opción de espera proporcionada.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket TCP conectada anteriormente.
- **desired_state**: estado TCP deseado. Los estados de socket TCP válidos se definen de la siguiente manera:
    - **NX_TCP_CLOSED** (0x01)
    - **NX_TCP_LISTEN_STATE** (0x02)
    - **NX_TCP_SYN_SENT** (0x03)
    - **NX_TCP_SYN_RECEIVED** (0x04)
    - **NX_TCP_ESTABLISHED** (0x05)
    - **NX_TCP_CLOSE_WAIT** (0x06)
    - **NX_TCP_FIN_WAIT_1** (0x07)
    - **NX_TCP_FIN_WAIT_2** (0x08)
    - **NX_TCP_CLOSING** (0x09)
    - **NX_TCP_TIMED_WAIT** (0x0A)
    - **NX_TCP_LAST_ACK** (0x0B)
- **wait_option**: define cómo se comporta el servicio si el estado solicitado no está presente. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFF)

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Espera de estado correcta.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_NOT_SUCCESSFUL**: (0x43) El estado no está presente en el tiempo de espera especificado.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.
- **NX_OPTION_ERROR**: (0X0A) El estado del socket deseado no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Wait 300 timer ticks for the previously created socket to enter
   the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
                                  NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
   state! */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback
Instalar una devolución de llamada para el estado de tiempo de espera

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada que se invoca cuando el socket TCP está en estado de tiempo de espera. Para usar este servicio, se debe compilar la biblioteca de NetX Duo con la opción ***NX_ENABLE_EXTENDED_NOTIFY*** definida.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.
- **tcp_timed_wait_callback**: función de devolución de llamada de tiempo de espera.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) El socket de la función de devolución de llamada se ha registrado correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) La biblioteca de NetX Duo se ha compilado sin la característica de notificación extendida habilitada.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) La característica de TCP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure
Configurar los parámetros de transmisión del socket

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```
### <a name="description"></a>Descripción

Este servicio configura varios parámetros de transmisión del socket TCP especificado.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket TCP.
- **max_queue_depth**: número máximo de paquetes que se pueden poner en cola para su transmisión.
- **timeout**: número de tics del temporizador de ThreadX que se espera una confirmación antes de que se vuelva a enviar el paquete.
- **max_retries**: número máximo de reintentos permitidos.
- **timeout_shift**: valor para desplazar el tiempo de espera de cada reintento subsiguiente. Un valor de 0 da como resultado el mismo tiempo de espera entre reintentos sucesivos. Un valor de 1 duplica el tiempo de espera entre reintentos.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Socket de transmisión configurado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_OPTION_ERROR**: (0x0a) Opción de profundidad de la cola no válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) La característica de TCP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Configure the "client_socket" for a maximum transmit queue depth of
   12, 100 tick timeouts, a maximum of 20 retries, and a timeout double
   on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,12,100,20,1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
   configured. */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set
Notificar a la aplicación las actualizaciones de tamaño de la ventana

### <a name="prototype"></a>Prototipo  

```c
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_window_update_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descripción

Este servicio instala una rutina de devolución de llamada de actualización de la ventana del socket. Se llama a esta rutina automáticamente cada vez que el socket especificado recibe un paquete que indica un aumento en el tamaño de la ventana del host remoto.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket TCP creado anteriormente.
- **tcp_window_update_notify**: rutina de devolución de llamada a la que se llamará cuando cambie el tamaño de la ventana. Un valor NULL deshabilita la actualización de cambios de la ventana.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) La rutina de devolución de llamada se ha instalado en el socket.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) Punteros no válidos.
- **NX_NOT_ENABLED**: (0x14) La característica de TCP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Set the function pointer to the windows update callback after creating the
   socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
                                                my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(&data_socket)
{

/* Process update on increase TCP transmit socket window size. */
   return;
}
```
### <a name="see-also"></a>Consulte también

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable
Habilitar el componente de UDP de NetX Duo

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita el componente del protocolo de datagramas de usuario (UDP) de NetX Duo. Una vez habilitado, la aplicación puede enviar y recibir datagramas UDP.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) UDP habilitado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_ALREADY_ENABLED**: (0x15) Este componente ya se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
   instance. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find
Buscar el siguiente puerto UDP disponible

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>Descripción

Este servicio busca un puerto UDP libre (sin enlazar) a partir del número de puerto proporcionado por la aplicación. La lógica de búsqueda volverá a empezar si la búsqueda alcanza el valor máximo de puerto de 0xFFFF. Si la búsqueda tiene éxito, se devuelve el puerto libre en la variable a la que apunta free_port_ptr.

> [!WARNING]  
> *Se puede llamar a este servicio desde otro subproceso y puede hacer que se devuelva el mismo puerto. Para evitar esta condición de carrera, es posible que la aplicación desee colocar este servicio y el enlace de socket real bajo la protección de una exclusión mutua*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **port**: número de puerto para iniciar la búsqueda (de 1 a 0xFFFF).
- **free_port_ptr**: puntero a la variable de devolución del puerto libre de destino.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha encontrado un puerto libre.
- **NX_NO_FREE_PORTS**: (0x45) No se ha encontrado ningún puerto libre.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.
- **NX_INVALID_PORT**: (0x46) El número de puerto especificado no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Locate a free UDP port, starting at port 12, on a previously
   created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
   free UDP port on the IP instance. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get
Recuperar información acerca de las actividades de UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```
### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de UDP de la instancia de IP especificada.

> [!IMPORTANT]  
> *Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **udp_packets_sent**: puntero al destino para el número total de paquetes UDP enviados.
- **udp_bytes_sent**: puntero al destino para el número total de bytes UDP enviados.
- **udp_packets_received**: puntero al destino del número total de paquetes UDP recibidos.
- **udp_bytes_received**: puntero al destino del número total de bytes UDP recibidos.
- **udp_invalid_packets**: puntero al destino del número total de paquetes UDP no válidos.
- **udp_receive_packets_dropped**: puntero al destino del número total de paquetes UDP recibidos eliminados.
- **udp_checksum_errors**: puntero al destino del número total de paquetes UDP con errores de suma de comprobación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Recuperación correcta de la información de UDP.
- **NX_PTR_ERROR**: (0x07) Puntero IP no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Retrieve UDP information from previously created IP Instance
   ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
                         &udp_bytes_sent,
                         &udp_packets_received,
                         &udp_bytes_received,
                         &udp_invalid_packets,
                         &udp_receive_packets_dropped,
                         &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract
Extraer parámetros de red de un paquete UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>Descripción

Este servicio extrae los parámetros de red, como la dirección IPv4, el número de puerto del nodo del mismo nivel y el tipo de protocolo (este servicio siempre devuelve el tipo UDP) de un paquete recibido en una interfaz de entrada. Para obtener información sobre un paquete procedente de una red IPv4 o IPv6, la aplicación debe usar el servicio ***nxd_udp_packet_info_extract***.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete.
- **ip_address**: puntero a la dirección IP del emisor.
- **protocolo**: puntero al protocolo (UDP).
- **port**: puntero al número de puerto del emisor.
- **interface_index**: puntero al índice de la interfaz de recepción.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Datos de la interfaz de paquetes extraídos correctamente.
- **NX_INVALID_PACKET**: (0x12) El paquete no contiene una trama IPv4.
- **NX_PTR_ERROR**: (0x07) Entrada de puntero no válida.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract(packet_ptr, &ip_address,
                                     &protocol, &port,
                                     &interface_index);

/* If status is NX_SUCCESS packet data was successfully
   retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind
Enlazar un socket UDP a un puerto UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio enlaza el socket UDP creado previamente al puerto UDP especificado. El intervalo de sockets UDP válidos es de 0 a 0xFFFF. Si el número de puerto solicitado está enlazado a otro socket, este servicio espera durante el período de tiempo especificado para que el socket se desenlace del número de puerto.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket UDP creada anteriormente.
- **port**: número de puerto al que se va a enlazar** (de 1 a 0xFFFF). Si el número de puerto es NX_ANY_PORT** (0x0000), la instancia de IP buscará el siguiente puerto libre y lo utilizará para el enlace.
- **wait_option**: define cómo se comporta el servicio si el puerto ya está enlazado a otro socket. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Socket enlazado correctamente.
- **NX_ALREADY_BOUND**: (0x22) Este socket ya está enlazado a otro puerto.
- **NX_PORT_UNAVAILABLE**: (0x23) El puerto ya está enlazado a otro socket.
- **NX_NO_FREE_PORTS**: (0x45) No hay ningún puerto libre.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_INVALID_PORT**: (0x46) Puerto especificado no válido.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Bind the previously created UDP socket to port 12 on the
   previously created IP instance. If the port is already bound,
   wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
   port 12.*/
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available
Recuperar el número de bytes disponibles para su recuperación

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```
### <a name="description"></a>Descripción

Este servicio recupera el número de bytes disponibles para su recepción en el socket UDP especificado.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket UDP creada anteriormente.
- **bytes_available**: puntero al destino para los bytes disponibles.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Bytes disponibles recuperados correctamente.
- **NX_NOT_SUCCESSFUL**: (0x43) Socket no enlazado a ningún puerto.
- **NX_PTR_ERROR**: (0x07) Punteros no válidos.
- **NX_NOT_ENABLED**: (0x14) La característica de UDP no está habilitada.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket,
                                       &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
   retrieved.*/
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable
Deshabilitar la suma de comprobación para un socket UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descripción

Este servicio deshabilita la lógica de la suma de comprobación para enviar y recibir paquetes en el socket UDP especificado. Cuando se deshabilita la lógica de la suma de comprobación, se carga un valor de cero en el campo de suma de comprobación del encabezado UDP para todos los paquetes enviados mediante este socket. Un valor de suma de comprobación establecido en cero en el encabezado UDP indica al receptor que no se ha procesado la suma de comprobación para este paquete.

Tenga en cuenta también que esto no tiene ningún efecto si **NX_DISABLE_UDP_RX_CHECKSUM** y **NX_DISABLE_UDP_TX_CHECKSUM** se definen al recibir y enviar paquetes UDP, respectivamente.

Tenga en cuenta que este servicio no tiene ningún efecto en los paquetes de la red IPv6, ya que la suma de comprobación UDP es obligatoria para IPv6.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket UDP creada anteriormente.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Suma de comprobación de socket deshabilitada correctamente.
- **NX_NOT_BOUND**: (0x24) El socket no está enlazado.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizador

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
   calculated. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable
Habilitar la suma de comprobación para un socket UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita la lógica de la suma de comprobación para enviar y recibir paquetes en el socket UDP especificado. La suma de comprobación abarca todo el área de datos UDP y un encabezado pseudo IP.

Tenga en cuenta también que esto no tiene ningún efecto si **NX_DISABLE_UDP_RX_CHECKSUM** y **NX_DISABLE_UDP_TX_CHECKSUM** se definen al recibir y enviar paquetes UDP, respectivamente.

Tenga en cuenta que este servicio no tiene ningún efecto en los paquetes de la red IPv6. La suma de comprobación de UDP es obligatoria en IPv6.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket UDP creada anteriormente.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Suma de comprobación de socket habilitada correctamente.
- **NX_NOT_BOUND**: (0x24) El socket no está enlazado.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizador

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
   calculated. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create
Crear un socket UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, 
    CHAR *name,
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG queue_maximum);
```
### <a name="description"></a>Descripción

Este servicio crea un socket UDP para la instancia de IP especificada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **socket_ptr**: puntero al bloque de control del nuevo socket UDP.
- **name**: nombre de la aplicación para este socket UDP.
- **type_of_service**: define el tipo de servicio para la transmisión. Los valores válidos son los siguientes:
    - **NX_IP_NORMAL**: (0x00000000)
    - **NX_IP_MIN_DELAY**: (0x00100000)
    - **NX_IP_MAX_DATA**: (0x00080000)
    - **NX_IP_MAX_RELIABLE**: (0x00040000)
    - **NX_IP_MIN_COST**: (0x00020000)
- **fragment**: especifica si se permite o no la fragmentación de IP. Si se especifica NX_FRAGMENT_OKAY (0x0), se permite la fragmentación de IP. Si se especifica NX_DONT_FRAGMENT (0x4000), se deshabilita la fragmentación de IP.
- **time_to_live**: especifica el valor de 8 bits que define el número de enrutadores que puede pasar este paquete antes de que se descarte. NX_IP_TIME_TO_LIVE especifica el valor predeterminado.
- **queue_maximum**: define el número máximo de datagramas UDP que se pueden poner en cola para este socket. Una vez alcanzado el límite de la cola, se libera el paquete UDP más antiguo para cada paquete nuevo recibido.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Socket UDP creado correctamente.
- **NX_OPTION_ERROR**: (0x0A) Tipo de servicio, fragmento u opción de período de vida no válidos.
- **NX_PTR_ERROR**: (0x07) IP o puntero de socket no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
                              NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80,
                              30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
   is ready for binding. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete
Eliminar un socket UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descripción

Este servicio elimina un socket UDP creado anteriormente. Si el socket se ha enlazado a un puerto, primero se debe desenlazar el socket.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket UDP creada anteriormente.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Socket eliminado correctamente.
- **NX_STILL_BOUND**: (0x42) El socket sigue estando enlazado.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
   been deleted. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get
Recuperar información acerca de las actividades del socket UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```
### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de socket UDP de la instancia de socket UDP especificada.

> [!IMPORTANT]  
> *Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada*.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket UDP creada anteriormente.
- **udp_packets_sent**: puntero al destino para el número total de paquetes UDP enviados en el socket.
- **udp_bytes_sent**: puntero al destino para el número total de bytes UDP enviados en el socket.
- **udp_packets_received**: puntero al destino del número total de paquetes UDP recibidos en el socket.
- **udp_bytes_received**: puntero al destino del número total de bytes UDP recibidos en el socket.
- **udp_packets_queued**: puntero al destino del número total de paquetes UDP en cola en el socket.
- **udp_receive_packets_dropped**: puntero al destino del número total de paquetes de recepción UDP descartados para el socket debido a que se superó el tamaño de la cola.
- **udp_checksum_errors**: puntero al destino del número total de paquetes UDP con errores de suma de comprobación en el socket.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Recuperación correcta de la información del socket UDP.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
                                &udp_packets_sent,
                                &udp_bytes_sent,
                                &udp_packets_received,
                                &udp_bytes_received,
                                &udp_queued_packets,
                                &udp_receive_packets_dropped,
                                &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get
Recuperar el número de puerto enlazado a un socket UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_port_get(
    NX_UDP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>Descripción

Este servicio recupera el número de puerto asociado al socket, lo que resulta útil para encontrar el puerto asignado por NetX Duo en situaciones en las que se especificó NX_ANY_PORT en el momento en que se enlazó el socket.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket UDP creada anteriormente.
- **port_ptr**: puntero al destino del número de puerto devuelto. Los números de puerto válidos son (1 a 0xFFFF).

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Socket enlazado correctamente.
- **NX_NOT_BOUND**: (0x24) Este socket no está enlazado a un puerto.
- **NX_PTR_ERROR**: (0x07) Puntero de socket o puntero de devolución de puerto no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive
Recibir un datagrama de un socket UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio recibe un datagrama UDP del socket especificado. Si no hay ningún datagrama en cola en el socket especificado, el autor de llamada se suspende en función de la opción de espera proporcionada.

> [!CAUTION]  
> *Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite*.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket UDP creada anteriormente.
- **packet_ptr**: puntero al puntero del paquete del datagrama UDP.
- **wait_option**: define cómo se comporta el servicio si no hay ningún datagrama en la cola actualmente en este socket. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Recepción correcta en el socket.
- **NX_NOT_BOUND**: (0x24) El socket no estaba enlazado a ningún puerto.
- **NX_NO_PACKET**: (0x01) No había ningún datagrama UDP para recibir.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_PTR_ERROR**: (0x07) Socket o puntero de devolución del paquete no válidos.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Receive a packet from a previously created and bound UDP socket.
   If no packets are currently available, wait for 500 timer ticks
   before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
   packet_ptr. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify
Notificar cada paquete recibido a la aplicación

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)(NX_UDP_SOCKET *socket_ptr));
```
### <a name="description"></a>Descripción 

Este servicio establece el puntero de la función de notificación de recepción en la función de devolución de llamada especificada por la aplicación. A continuación, se llama a esta función de devolución de llamada siempre que se recibe un paquete en el socket. Si se proporciona un puntero NX_NULL, la función de notificación de recepción se deshabilita.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket UDP.
- **udp_receive_notify**: puntero a la función de devolución de llamada de la aplicación a la que se llama cuando se recibe un paquete en el socket.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) La función de notificación de recepción del socket se ha establecido correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Setup a receive packet callback function for the "udp_socket"
   socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever a packet is received for
   "udp_socket". */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send
Enviar un datagrama UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address, 
    UINT port);
```
### <a name="description"></a>Descripción

Este servicio envía un datagrama UDP mediante un socket UDP previamente creado y enlazado para redes IPv4. NetX Duo encuentra una dirección IP local adecuada como dirección de origen en función de la dirección IP de destino. Para especificar una interfaz y una dirección IP de origen específicas, la aplicación debe usar el servicio **nxd_udp_socket_source_send**.

Tenga en cuenta que este servicio vuelve inmediatamente, independientemente de si el datagrama UDP se ha enviado correctamente. El servicio equivalente de NetX Duo (IPv4 e IPv6) es ***nxd_udp_socket_send***.

El socket debe estar enlazado a un puerto local.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.
- **packet_ptr**: puntero al paquete del datagrama UDP.
- **ip_address**: dirección IPv4 de destino.
- **port**: número de puerto de destino válido (entre 1 y 0xFFFF), en el orden de bytes del host.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Envío correcto desde el socket UDP.
- **NX_NOT_BOUND**: (0x24) Socket no enlazado a ningún puerto.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) No se ha podido encontrar ninguna interfaz de salida adecuada.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP del servidor no válida.
- **NX_UNDERFLOW**: (0x02) No hay suficiente espacio para el encabezado UDP en el paquete.
- **NX_OVERFLOW**: (0x03) El puntero de anexión del paquete no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) No se ha habilitado UDP.
- **NX_INVALID_PORT**: (0x46) El número de puerto no está dentro de un intervalo válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
                            server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
   the packet out the UDP socket to its peer. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_source_send"></a>nx_udp_socket_source_send
Enviar un datagrama mediante el socket UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```
### <a name="description"></a>Descripción

Este servicio envía un datagrama UDP mediante un socket UDP previamente creado y enlazado mediante la interfaz de red con la dirección IP especificada como dirección de origen. Tenga en cuenta que el servicio vuelve inmediatamente, independientemente de si el datagrama UDP se ha enviado correctamente o no. ***nxd_udp_socket_source_send*** funciona para redes IPv4 e IPv6.

### <a name="parameters"></a>Parámetros 

- **socket_ptr**: socket en el que se va a transmitir el paquete.
- **packet_ptr**: puntero al paquete que se va a transmitir.
- **ip_address**: dirección IP de destino a la que se va a enviar el paquete.
- **port**: puerto de destino.
- **address_index**: índice de la dirección asociada a la interfaz en la que se va a enviar el paquete.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) El paquete se ha enviado correctamente.
- **NX_NOT_BOUND**: (0x24) Socket no enlazado a ningún puerto.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IP no válida.
- **NX_NOT_ENABLED**: (0x14) El procesamiento de UDP no está habilitado.
- **NX_PTR_ERROR**: (0x07) Puntero no válido.
- **NX_OVERFLOW**: (0x03) Puntero de anexión de paquetes no válido.
- **NX_UNDERFLOW**: (0x02) Puntero de anteposición de paquetes no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) Índice de dirección no válido.
- **NX_INVALID_PORT**: (0x46) El número de puerto supera el número de puerto máximo.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
   interface at index 1 in the IP task interface list. */
status = nx_udp_socket_source_send(socket_ptr, packet_ptr,
                                   destination_ip, 80,
                                   ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind
Desenlazar un socket UDP del puerto UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Descripción

Este servicio libera el enlace entre el socket UDP y un puerto UDP. Los paquetes recibidos almacenados en la cola de recepción se liberan como parte de la operación de desenlazado.

Si hay otros subprocesos en espera de enlazar otro socket al puerto desenlazado, el primer subproceso suspendido se enlaza al puerto recién desenlazado.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia del socket UDP creada anteriormente.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Socket desenlazado correctamente.
- **NX_NOT_BOUND**: (0x24) El socket no estaba enlazado a ningún puerto.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR**: (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) Este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
   unbound. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract
Extraer la dirección IP y el puerto de envío de un datagrama UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, 
    UINT *port);
```
### <a name="description"></a>Descripción

Este servicio extrae el número de puerto y la dirección IP del emisor de los encabezados IP y UDP del datagrama UDP proporcionado. Tenga en cuenta que el servicio ***nxd_udp_source_extract*** funciona con paquetes de una red IPv4 o IPv6.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete del datagrama UDP.
- **ip_address**: puntero válido a la variable de devolución de la dirección IP.
- **port**: puntero válido a la variable de devolución del puerto.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Extracción correcta del puerto y la dirección IP de origen.
- **NX_INVALID_PACKET**: (0x12) El paquete proporcionado no es válido.
- **NX_PTR_ERROR**: (0x07) Paquete, dirección IP o puerto de destino no válidos.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Extract the IP and port information from the sender of the UPD packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address, &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has been stored
   in sender_ip_address and sender_port respectively.*/
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_icmp_enable"></a>nxd_icmp_enable
Habilitar los servicios de ICMPv4 e ICMPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita los servicios ICMPv4 e ICMPv6 y solo se puede llamar después de que se haya creado la instancia de IP. El servicio se puede habilitar antes o después de habilitar IPv6 (consulte *nxd_ipv6_enable*). Los servicios de ICMPv4 incluyen la solicitud y respuesta de eco. Entre los servicios ICMPv6 se incluyen la solicitud y respuesta de eco, la detección de vecinos, la detección de direcciones duplicadas, la detección de enrutadores y la configuración automática de direcciones sin estado. El equivalente para IPv4 en NetX es *nx_icmp_enable*.

> [!NOTE] 
> *Si la dirección IPv6 se configura manualmente antes de habilitar ICMPv6, la dirección IPv6 configurada manualmente no está sujeta al proceso de detección de direcciones duplicadas*.

*nx_icmp_enable* inicia los servicios de ICMP solo para operaciones IPv4. Las aplicaciones que utilizan los servicios de ICMPv6 deben usar *nxd_icmp_enable* en lugar de *nx_icmp_enable*.

Para usar la solicitud de enrutador IPv6 y la configuración de dirección automática IPv6 sin estado, se debe habilitar ICMPv6.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Los servicios de ICMP de se han habilitado correctamente.
- **NX_PTR_ERROR**: (0x07) Puntero a la instancia de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Enable ICMP on the IP instance. */
status = nxd_icmp_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for ICMP services. */
```
### <a name="see-also"></a>Consulte también

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_ping"></a>nxd_icmp_ping
Realizar solicitudes de eco ICMPv4 o ICMPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_icmp_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr, 
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio envía un paquete de solicitud de eco ICMP mediante una interfaz física adecuada y espera una respuesta de eco del host de destino. NetX Duo determina la interfaz adecuada en función de la dirección de destino para enviar el mensaje de ping. Las aplicaciones deben usar el servicio ***nxd_icmp_source_ping*** para especificar la interfaz física y la dirección IP de origen precisas que se usarán para la transmisión de paquetes.

Se debe haber creado la instancia de IP y los servicios ICMPv4 e ICMPv6 deben estar habilitados (consulte ***nxd_icmp_enable***).

> [!WARNING]  
> Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP.
- **ip_address**: dirección IP de destino a la que se va a hacer ping, en el orden de bytes del host.
- **data_ptr**: puntero al área de datos del paquete de ping.
- **data_size**: número de bytes de datos de ping.
- **response_ptr**: puntero al puntero del paquete de respuesta.
- **wait_option**: tiempo de espera para una respuesta. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **valor de tiempo de espera en tics**: (0x00000001 a 
    - **NX_WAIT_FOREVER** 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Ping enviado y recibido correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) IPv6 no está habilitado.
- **NX_OVERFLOW**: (0x03) Los datos de ping superan la carga del paquete.
- **NX_NO_RESPONSE**: (0x29) El host de destino no ha respondido.
- **NX_WAIT_ABORTED**: (0x1A) tx_thread_wait_abort ha cancelado la suspensión solicitada.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) No se ha podido encontrar ninguna interfaz de salida adecuada.
- **NX_PTR_ERROR**: (0x07) Puntero de respuesta o dirección IP no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) IP o el componente de ICMP no están habilitados.
- **NX_IP_ADDRESS_ERROR**: (0x21) La dirección IP de entrada no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* The following two examples illustrate how to use this API to send
   ping packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   2001:1234:5678::1 */
   
/* Declare variable address to hold the destination address. */
NXD_ADDRESS ip_address;

char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0x20011234;
ip_address.nxd_ip_address.v6[1]    = 0x56780000;
ip_address.nxd_ip_address.v6[2]    = 0;
ip_address.nxd_ip_address.v6[3]    = 1;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr,
                       NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been
   received from IP address 2001:1234:5678::1 and the response
   packet is contained in the packet pointed to by response_ptr.It
   should have the same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4[0]    = 0x01020304;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr, 10);

/* A return value of NX_SUCCESS indicates a ping reply was received
   from IP address 1.2.3.4 and the response packet is contained in
   the packet pointed to by response_ptr. It should have the same
   “abcd” four bytes of data. */
```
### <a name="see-also"></a>Consulte también

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_source_ping"></a>nxd_icmp_source_ping
Realizar solicitudes de eco ICMPv4 o ICMPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_icmp_source_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    UINT address_index,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio envía un paquete de solicitud de eco ICMP con el índice especificado de una dirección IPv4 o IPv6, y mediante la interfaz de red a la que está asociada la dirección de origen y espera una respuesta de eco del host de destino. Este servicio funciona con direcciones IPv4 e IPv6. El parámetro *address_index* indica la dirección IPv4 o IPv6 de origen que se va a usar. Para una dirección IPv4, *address_index* es el mismo índice de la interfaz de red conectada. En el caso de IPv6, *address_index* indica la entrada de la tabla de direcciones IPv6.

Se debe haber creado la instancia de IP y los servicios ICMPv4 e ICMPv6 deben estar habilitados (consulte *nxd_icmp_enable*).

> [!CAUTION] 
> *Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP.
- **ip_address**: dirección IP de destino a la que se va a hacer ping, en el orden de bytes del host.
- **address_index**: indica la dirección IP que se va a usar como dirección de origen.
- **data_ptr**: puntero al área de datos del paquete de ping.
- **data_size**: número de bytes de datos de ping.
- **response_ptr**: puntero al puntero del paquete de respuesta.
- **wait_option**: tiempo de espera para una respuesta. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE
    - **NX_WAIT_FOREVER** 0xFFFFFFFF)

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Ping enviado y recibido correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) IPv6 no está habilitado.
- **NX_OVERFLOW**: (0x03) Los datos de ping superan la carga del paquete.
- **NX_NO_RESPONSE**: (0x29) El host de destino no ha respondido.
- **NX_WAIT_ABORTED**: (0x1A) tx_thread_wait_abort ha cancelado la suspensión solicitada.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) No se ha podido encontrar ninguna interfaz de salida adecuada.
- **NX_PTR_ERROR**: (0x07) Puntero de respuesta o dirección IP no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) IP o el componente de ICMP no están habilitados.
- **NX_IP_ADDRESS_ERROR**: (0x21) La dirección IP de entrada no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* The following two examples illustrate how to use this API to send ping
   packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   FE80::411:7B23:40dc:f181 */

/* Declare variable address to hold the destination address. */

#define PRIMARY_INTERFACE 0
#define GLOBAL_IPv6_ADDRESS 1

NXD_ADDRESS ip_address;
char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0xFE800000;
ip_address.nxd_ip_address.v6[1]    = 0x00000000;
ip_address.nxd_ip_address.v6[2]    = 0x04117B23;
ip_address.nxd_ip_address.v6[3]    = 0x40DCF181;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              GLOBAL_IPv6_ADDRESS,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been received
   from IP address FE80::411:7B23:40dc:f181 and the response packet is
   contained in the packet pointed to by response_ptr. It should have the
   same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4       = 0x01020304;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              PRIMARY_INTERFACE,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply was received from
   IP address 1.2.3.4 and the response packet is contained in the packet
   pointed to by response_ptr. It should have the same “abcd” four bytes
   of data. */
```

### <a name="see-also"></a>Consulte también

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmpv6_ra_flag_callback_set"></a>nxd_icmpv6_ra_flag_callback_set
Establecer la función de devolución de llamada de cambio de marca de RA de ICMPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_icmpv6_ra_flag_callback_set(
    NX_IP *ip_ptr, 
    VOID(*ra_callback)(NX_IP*ip_ptr, UINT ra_flag));
```
### <a name="description"></a>Descripción

Este servicio establece la función de devolución de llamada de cambio de marca de anuncio de enrutador de ICMPv6. La función de devolución de llamada proporcionada por el usuario se invoca cuando NetX Duo recibe un mensaje de anuncio de enrutador.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP.
- **ra_callback**: función de devolución de llamada proporcionada por el usuario.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha establecido correctamente la función de devolución de llamada de marca de RA.
- **NX_NOT_SUPPORTED**: (0x4B) IPv6 no está habilitado.
- **NX_PTR_ERROR**: (0x07) Instancia de IP no válida.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
VOID icmpv6_ra_flag_callback(NX_IP *ip_ptr, UINT ra_flag)
{
   /* RA flag has changed. The updated value is passed in via the
      ra_flag parameter. */
}

/* Configure the user-defined ICMPv6 RA flag change callback
   function. */
status = nxd_icmpv6_ra_flag_callback_set(&ip_0,
                                         icmpv6_ra_flag_callback);

/* A status return of NX_SUCCESS indicates the callback function has
   been successfully configured. */
```
### <a name="see-also"></a>Consulte también

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping

## <a name="nxd_ip_raw_packet_send"></a>nxd_ip_raw_packet_send
Enviar un paquete IP sin formato

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ip_raw_packet_send(
    NX_IP *ip_ptr, 
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination
    ULONG protocol, 
    UINT ttl, 
    ULONG tos);
```
### <a name="description"></a>Descripción

Este servicio envía un paquete IPv4 o IPv6 sin formato (sin encabezados de protocolo de capa de transporte). En un sistema de host múltiple, si el sistema no puede determinar una interfaz adecuada (por ejemplo, si la dirección IP de destino es de difusión IPv4, multidifusión o una dirección de multidifusión IPv6), se selecciona el dispositivo primario. Se puede utilizar el servicio ***nxd_ip_raw_packet_source_send** _ para especificar una interfaz de salida. El equivalente en NetX es _ *_nx_ip_raw_packet_send_.* *

La instancia de IP se debe haber creado previamente y se debe habilitar el control de paquetes IP sin formato mediante el servicio ***nx_ip_raw_packet_enable***.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **packet_ptr**: puntero al paquete que se va a transmitir.
- **destination_ip**: puntero a la dirección de destino.
- **protocol**: protocolo del paquete almacenado en el encabezado IP.
- **ttl**: valor de TTL o límite de saltos.
- **tos**: valor de TOS o clase de tráfico y etiqueta de flujo.

### <a name="return-value"></a>Valor devuelto 

- **NX_SUCCESS**: (0x00) El paquete IP sin formato se ha enviado correctamente.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) No se ha podido encontrar ninguna interfaz de salida adecuada.
- **NX_NOT_ENABLED**: (0x14) No se ha habilitado el control de paquetes IP sin formato.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IPv4 o IPv6 no válida.
- **NX_UNDERFLOW**: (0x02) No hay suficiente espacio para el encabezado IPv4 o IPv6 en el paquete.
- **NX_OVERFLOW**: (0x03) El puntero de anexión del paquete no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero de IP o puntero de paquete no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_INVALID_PARAMETERS**: (0x4D) Entrada de dirección IPv6 no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS dest_address;

/* Set the destination address,in this case an IPv6 address. */
dest_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
dest_address.nxd_ip_address.v6[0]    = 0x20011234;
dest_address.nxd_ip_address.v6[1]    = 0x56780000;
dest_address.nxd_ip_address.v6[2]    = 0;
dest_address.nxd_ip_address.v6[3]    = 1;

UINT ttl, tos;

ttl = 128;

tos = 0;

/* Enable RAW IP handling on the previously created IP instance.*/
status = nx_raw_ip_packet_enable(&ip_0);

/* Allocate a packet pointed to by packet_ptr from the IP packet
   pool. */
/* Then transmit the packet to the destination address. */

status = nxd_ip_raw_packet_send(&ip_0, packet_ptr, dest_address,
                                NX_PROTOCOL_UDP, ttl, tos);

/* A status return of NX_SUCCESS indicates the packet was
   successfully transmitted. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_source_send

## <a name="nxd_ip_raw_packet_source_send"></a>nxd_ip_raw_packet_source_send
Enviar un paquete sin formato con la dirección de origen especificada

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination_ip,
    UINT address_index,
    ULONG protocol,
    UINT ttl,
    ULONG tos);
```
### <a name="description"></a>Descripción

Este servicio envía un paquete IPv4 o IPv6 sin formato mediante la dirección IPv4 o IPv6 especificada como dirección de origen. Este servicio se utiliza normalmente en un sistema de host múltiple, si el sistema no puede determinar una interfaz adecuada (por ejemplo, si la dirección IP de destino es de difusión IPv4, multidifusión o una dirección de multidifusión IPv6). El parámetro *address_index* permite a la aplicación especificar la dirección de origen que se va a usar al enviar este paquete sin formato.

La instancia de IP se debe haber creado previamente y se debe habilitar el control de paquetes IP sin formato mediante el servicio ***nx_ip_raw_packet_enable***.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP.
- **packet_ptr**: puntero al paquete que se va a enviar.
- **destination_ip**: dirección IP de destino.
- **address_index**: índice de las direcciones IPv4 o IPv6 que se usarán como dirección de origen.
- **protocol**: valor del campo de protocolo.
- **ttl**: valor de TTL o límite de saltos.
- **tos**: valor de TOS o clase de tráfico y etiqueta de flujo.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) El paquete se ha enviado correctamente.
- **NX_UNDERFLOW**: (0x02) No hay suficiente espacio para el encabezado IPv4 o IPv6 en el paquete.
- **NX_OVERFLOW**: (0x03) El puntero de anexión del paquete no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero no válido al bloque de control de IP, al paquete o a destination_ip.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) El procesamiento de paquetes sin formato no está habilitado.
- **NX_IP_ADDRESS_ERROR**: (0x21) Error de dirección.
- **NX_INVALID_INTERFACE**: (0x4C) Índice de interfaz no válido.
- **NX_INVALID_PARAMETERS**: (0x4D) Entrada de dirección IPv6 no válida.

### <a name="allowed-from"></a>Permitido desde

Thread

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define SOURCE_ADDRESS_INDEX 2

/* Send a raw packet from specified interface. */
status = nxd_ip_raw_packet_source_send(&ip_0, packet_ptr,
                                       dest_ip,
                                       SOURCE_ADDRESS_INDEX,
                                       NX_IP_RAW,
                                       NX_IP_TIME_TO_LIVE,
                                       NX_IP_NORMAL);

/* If status == NX_SUCCESS, raw packet has been sent out on the
   specified interface. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send

## <a name="nxd_ipv6_address_change_notify"></a>nxd_ipv6_address_change_notify
Establecer la notificación de cambio de dirección IPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_address_change_notify(
    NX_IP *ip_ptr,
    VOID (*ip_address_change_notify)(NX_IP *, UINT, UINT, UINT, ULONG *));
```
### <a name="description"></a>Descripción

Este servicio registra una rutina de devolución de llamada de la aplicación a la que NetX Duo llama cada vez que cambia la dirección IPv6.

Este servicio está disponible si se ha compilado la biblioteca de NetX Duo con la opción ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY*** definida.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero al bloque de control de IP.
- **ip_address_change_notify**: función de devolución de llamada de la aplicación.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha establecido correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de notificación de cambio de dirección IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) No se ha compilado la notificación de cambio de dirección IPv6.

### <a name="allowed-from"></a>Permitido desde

Thread

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
VOID ip_address_change_notify(NX_IP *ip_ptr, UINT status,
                              UINT interface_index,
                              UINT address_index,
                              ULONG *ip_address)
{

   /* Do something when ip address changed. */
}

void ip_address_thread_entry(ULONG id)
{

   /* Set the ip address change notify of IP instance. */
   status = nxd_ipv6_address_change_notify (&ip_0, ip_address_change_notify);

/* If status == NX_SUCCESS, the ip address change notify of IP
   instance was successfully set. */
}
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_delete"></a>nxd_ipv6_address_delete
Eliminar una dirección IPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_address_delete(
    NX_IP *ip_ptr, 
    UINT address_index);
```
### <a name="description"></a>Descripción

Este servicio elimina la dirección IPv6 del índice especificado de la tabla de direcciones IPv6 de la instancia de IP especificada. No hay equivalente en NetX.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **address_index**: índice de la tabla de direcciones IPv6 de la instancia de IP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La dirección se ha eliminado correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) No se ha podido encontrar ninguna interfaz de salida adecuada.
- **NX_PTR_ERROR**: (0x07) Puntero a la instancia de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS ip_address;
UINT        address_index;

/* Delete the IPv6 address at the specified address table index. */
address_index = 1;
status = nxd_ipv6_address_delete(&ip_0, address_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully deleted. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_get"></a>nxd_ipv6_address_get
Recuperar la dirección IPv6 y el prefijo

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_address_get(
    NX_IP *ip_ptr, 
    UINT address_index, 
    NXD_ADDRESS *ip_address,
    ULONG *prefix_length,
    UINT *interface_index);
```
### <a name="description"></a>Descripción

Este servicio recupera la dirección IPv6 y el prefijo del índice especificado de la tabla de direcciones de la instancia de IP especificada. El índice de la interfaz física a la que está asociada la dirección IPv6 se devuelve en el puntero *interface_index*. Los servicios equivalentes de NetX son ***nx_ip_address_get** _ y _*_nx_ip_interface_address_get_**.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **address_index**: índice de la tabla de direcciones de la instancia de IP.
- **ip_address**: puntero a la dirección que se va a establecer.
- **prefix_length**: longitud del prefijo de dirección (máscara de subred).
- **interface_index**: puntero al índice de la interfaz.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) IPv6 está habilitado correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) No hay ninguna dirección de interfaz o índice de dirección no válido.
- **NX_PTR_ERROR**: (0x07) Puntero a la instancia de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS ip_address;
UINT        address_index;
ULONG       prefix_length;
UINT        interface_index;

/* Get the IPv6 address at the specified address table index. If
   found, the address network interface is returned in the
   interface_index input, as well as the address prefix in the
   prefix_length input. */

address_index = 1;
status = nxd_ipv6_address_get(&ip_0, address_index, &ip_address,
                              &prefix_length, &interface_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_set"></a>nxd_ipv6_address_set
Establecer la dirección IPv6 y el prefijo

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_address_set(
    NX_IP *ip_ptr, 
    UINT interface_index,
    NXD_ADDRESS *ip_address,
    ULONG prefix_length,
    UINT *address_index);
```
### <a name="description"></a>Descripción

Este servicio establece la dirección IPv6 y el prefijo proporcionados en la instancia de IP especificada. Si el argumento *address_index* no es NULL, se devuelve el índice de la tabla de direcciones IPv6 donde se ha insertado la dirección. Los servicios equivalentes de NetX son ***nx_ip_address_set** _ y _*_nx_ip_interface_address_set_**.

### <a name="parameters"></a>Parámetros  

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_index**: índice de la interfaz a la que está asociada la dirección IPv6.
- **ip_address**: puntero a la dirección que se va a establecer.
- **prefix_length**: longitud del prefijo de dirección (máscara de subred).
- **address_index**: puntero al índice en la tabla de direcciones en la que se ha insertado la dirección.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) IPv6 está habilitado correctamente.
- **NX_NO_MORE_ENTRIES**: (0x15) La tabla de direcciones IP está llena.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_DUPLICATED_ENTRY**: (0x52) La dirección IP suministrada ya está en uso en esta instancia de IP.
- **NX_PTR_ERROR**: (0x07) Puntero a la instancia de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IPv6 no válida.
- **NX_INVALID_INTERFACE**: (0x4C) La interfaz apunta a una interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS ip_address;
UINT        address_index;
UINT        interface_index;

ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                     IP_ADDRESS(1,2,3,4),
                     0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                     pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* Set the IPv6 address (a global address as indicated by the 64 bit
   prefix) using the IPv6 address just created on the primary device
   (index zero). The index into the address table is returned in
   address_index. */
interface_index = 0;
status = nxd_ipv6_address_set(&ip_0, interface_index, &ip_address,
                              64,&address_index);

/* A status return of NX_SUCCESS indicates that the IPv6 address is
   successfully assigned to the primary interface (interface 0). */
```

### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add
Agregar un enrutador IPv6 a la tabla de enrutadores predeterminados

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_default_router_add(
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address,
    ULONG router_lifetime,
    UINT index_index);
```
### <a name="description"></a>Descripción

Este servicio agrega un enrutador predeterminado IPv6 en la interfaz física especificada a la tabla de enrutadores predeterminados. El servicio IPv4 de NetX equivalente es ***nx_ip_gateway_address_set***.

*router_address* debe apuntar a una dirección IPv6 válida y el enrutador debe ser accesible directamente desde la interfaz física especificada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **router_address**: puntero a la dirección del enrutador predeterminado, en el orden de bytes del host.
- **router_lifetime**: tiempo de vida del enrutador predeterminado en segundos. Los valores válidos son:
    - **0xFFFF:** Sin tiempo de espera.
    - **0-0xFFFE:** valor de tiempo de espera en segundos.
- **index_index**: puntero a la ubicación de memoria válida del índice de red mediante el cual se puede llegar al enrutador.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) El enrutador predeterminado se ha agregado correctamente.
- **NX_NO_MORE_ENTRIES**: (0x17) No hay más entradas disponibles en la tabla de enrutadores predeterminados.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IPv6 no válida.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_INVALID_PARAMETERS**: (0x4D) Entrada de dirección IPv6 no válida.
- **NX_PTR_ERROR**: (0x07) Espacio de almacenamiento o instancia de IP no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) Índice de interfaz del enrutador no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* This example adds a default router for the primary interface at
   fe80::1219:B9FF:FE37:ac to the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;

/* Set the router address version to IPv6 */
router_address.nxd_ip_version   = NX_IP_VERSION_V6;

/* Set the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Set IPv6 default router. */
status = nxd_ipv6_default_router_add(ip_ptr, &router_address,
                                     0xFFFF, PRIMARY_INTERFACE);

/* Unless invalid pointer input is detected by the error checking
   Service, status return is always NX_SUCCESS. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete
Eliminar un enrutador IPv6 de la tabla de enrutadores predeterminados

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_default_router_delete (
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address);
```
### <a name="description"></a>Descripción

Este servicio elimina un enrutador predeterminado IPv6 de la tabla de enrutadores predeterminados. El servicio IPv4 de NetX equivalente es ***nx_ip_gateway_address_clear***.

### <a name="restrictions"></a>Restricciones

Se ha creado la instancia de IP. *router_address* debe apuntar a información válida.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a una instancia de IP creada anteriormente.
- **router_address**: puntero a la dirección de la puerta de enlace predeterminada de IPv6.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Enrutador eliminado correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_NOT_FOUND**: (0x4E) No se encuentra la entrada del enrutador.
- **NX_PTR_ERROR**: (0x07) Espacio de almacenamiento o instancia de IP no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_INVALID_PARAMETERS**: (0x82) Entrada que no es de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/*This example removes a default router:fe80::1219:B9FF:FE37:ac */

NXD_ADDRESS router_address;

/* Set the router_address version to IPv6 */
router_address.nxd_ip_version = NX_IP_VERSION_V6;

/* Program the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Delete the IPv6 default router. */
nxd_ipv6_default_router_delete(ip_ptr, &router_address);
```
### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_clearnx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_getnx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_entry_get"></a>nxd_ipv6_default_router_entry_get
Obtener una entrada de enrutador predeterminado

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_default_router_entry_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT entry_index,
    NXD_ADDRESS *router_addr,
    ULONG *router_lifetime,
    ULONG *prefix_length,
    ULONG *configuration_method);
```
### <a name="description"></a>Descripción

Este servicio recupera una entrada de enrutador de la tabla de enrutamiento de IPv6 predeterminada que está conectada a un dispositivo de red especificado.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **interface_index**: índice de la interfaz de red.
- **entry_index**: índice de la entrada.
- **router_addr**: dirección IPv6 del enrutador.
- **router_lifetime**: puntero al tiempo de vigencia del enrutador.
- **prefix_length**: puntero a la longitud del prefijo.
- **configuration_method**: puntero a la información sobre cómo se configuró la entrada.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha obtenido correctamente.
- **NX_NOT_FOUND**: (0x4E) No se ha encontrado la entrada del enrutador.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0
NXD_ADDRESS            router_addr;
ULONG                  router_lifetime;
ULONG                  prefix_length;
ULONG                  configuration_method;

/* Get the router entry of specified interface. */
status = nxd_ipv6_default_router_entry_get (&ip_0,
                                            PRIMARY_INTERFACE,
                                            entry_index,
                                            &router_addr,
                                            &router_lifetime,
                                            &prefix_length,
                                            &configuration_method);

/* If status == NX_SUCCESS, the router entry was successfully
   got. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_get"></a>nxd_ipv6_default_router_get
Recuperar un enrutador IPv6 de la tabla de enrutadores predeterminados

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_default_router_get(
    NX_IP *ip_ptr, 
    UINT interface_index
    NXD_ADDRESS *router_address,
    ULONG *router_lifetime,
    ULONG *prefix_length);
```
### <a name="description"></a>Descripción

Este servicio recupera una dirección de enrutador IPv6 predeterminado, el tiempo de vigencia y la longitud del prefijo en la interfaz física especificada de la tabla de enrutadores predeterminados. El servicio IPv4 de NetX equivalente es ***nx_ip_gateway_address_get***.

*router_address* debe apuntar a una estructura NXD_ADDRESS válida para que este servicio puede rellenar la dirección IPv6 del enrutador predeterminado.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_index**: índice de la interfaz de red mediante la cual se puede acceder al enrutador.
- **router_address**: puntero al espacio de almacenamiento para el valor devuelto de la dirección del enrutador predeterminado, en el orden de bytes del host.
- **router_lifetime**: puntero al tiempo de vigencia del enrutador.
- **prefix_length**: puntero a la longitud del prefijo de la dirección del enrutador.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) El enrutador predeterminado se ha agregado correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_NOT_FOUND**: (0x4E) No se encuentra el enrutador predeterminado.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) Índice de interfaz del enrutador no válido.
- **NX_PTR_ERROR**: (0x07) Espacio de almacenamiento o instancia de IP no válidos.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* This example retrieves a default router for the primary device
   from the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;
ULONG       router_lifetime;
ULONG       prefix_length;

/* Get IPv6 default router. */
status = nxd_ipv6_default_router_get(ip_ptr, PRIMARY_INTERFACE,
                                     &router_address,
                                     &router_lifetime,
                                     &prefix_length);

/* If status returns NX_SUCCESS, the router address and related
   information is returned successfully. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_number_of_entries_get"></a>nxd_ipv6_default_router_number_of_entries_get
Obtener el número de enrutadores IPv6 predeterminados

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_default_router_number_of_entries_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT *num_entries);
```
### <a name="description"></a>Descripción

Este servicio recupera el número de enrutadores IPv6 predeterminados configurados en una interfaz de red determinada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control de IP.
- **interface_index**: índice de la interfaz de red.
- **num_entries**: destino para el número de enrutadores IPv6 en un dispositivo de red especificado.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Se ha obtenido correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_INVALID_INTERFACE**: (0x4C) El valor del índice de dispositivo no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero del bloque de control de IP o puntero de número de entradas no válidos.

### <a name="allowed-from"></a>Permitido desde

Thread

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0
UINT                   num_entries;

/* Get the router entries of specified interface. */
status = nxd_ipv6_default_router_number_of_entries_get(&ip_0,
                                                       PRIMARY_INTERFACE,
                                                       &num_entries);

/* If status == NX_SUCCESS, the router entries was successfully
   retrieved. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get

## <a name="nxd_ipv6_disable"></a>nxd_ipv6_disable
Deshabilitar la característica de IPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio deshabilita IPv6 para la instancia de IP especificada. También borra la tabla de enrutadores predeterminados, la memoria caché de ND y la tabla de direcciones IPv6, sale de todos los grupos de multidifusión y restablece las variables de solicitud de enrutador. Este servicio no tiene ningún efecto si IPv6 no está habilitado.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Deshabilitación correcta.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_NOT_SUPPORT**: (0x4B) No se ha compilado del módulo de IPv6.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Disable IPv6 feature on this IP instance. */
status = nxd_ipv6_disable(&ip_0);

/* If status == NX_SUCCESS, disables IPv6 feature on IP instance.*/
```
### <a name="see-also"></a>Consulte también 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable
Habilitación de los servicios de IPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio habilita los servicios de IPv6. Cuando los servicios de IPv6 están habilitados, la instancia de IP se une al grupo de multidifusión de todos los nodos (FF02:: 1). Este servicio no establece la dirección del vínculo local ni la dirección global. Las aplicaciones deben usar *nxd_ipv6_address_set* para configurar las direcciones de red del dispositivo. No hay equivalente en NetX.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) IPv6 está habilitado correctamente.
- **NX_ALREADY_ENABLED**: (0x15) IPv6 ya está habilitado.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_PTR_ERROR**: (0x07) Puntero a la instancia de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                      IP_ADDRESS(1,2,3,4),
                      0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                      pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for IPv6 services. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_multicast_interface_join"></a>nxd_ipv6_multicast_interface_join
Unirse a un grupo de multidifusión IPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_multicast_interface_join(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio permite a una aplicación unirse a una dirección de multidifusión IPv6 específica en una interfaz de red específica. Se notifica al controlador del vínculo que agregue la dirección de multidifusión. Este servicio está disponible si se compila la biblioteca de NetX Duo con la opción ***NX_ENABLE_IPV6_MULTICAST*** definida.

### <a name="parameters"></a>Parámetros  

- **ip_ptr**: puntero a la instancia de IP.
- **group_address**: dirección IPv6 de multidifusión.
- **interface_index**: índice de la interfaz de red asociada al grupo de multidifusión.

### <a name="return-values"></a>Valores devueltos  

- **NX_SUCCESS**: (0x00) Se ha habilitado correctamente la recepción en la dirección IPv6 de multidifusión.
- **NX_NO_MORE_ENTRIES**: (0x17) No hay más entradas en la tabla de multidifusión de IPv6.
- **NX_OVERFLOW**: (0x03) No hay más direcciones de grupo disponibles en el controlador del dispositivo.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 o la característica de multidifusión de IPv6 no se han compilado en la biblioteca de NetX Duo.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IPv6 no válida.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0

/* Join multicast group on this IP instance. */
status = nxd_ipv6_multicast_interface_join(&ip_0,
                                           &group_address,
                                           PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, interface of index on IP instance
   has joined the multicast group. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_leave

## <a name="nxd_ipv6_multicast_interface_leave"></a>nxd_ipv6_multicast_interface_leave
Salir de un grupo de multidifusión IPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_multicast_interface_leave(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```
### <a name="description"></a>Descripción

Este servicio quita la dirección de multidifusión IPv6 específica del dispositivo de red específico. También se notifica al controlador de vínculo la eliminación de la dirección IPv6 de multidifusión. Este servicio está disponible si se compila la biblioteca de NetX Duo con la opción ***NX_ENABLE_IPV6_MULTICAST*** definida.

### <a name="parameters"></a>Parámetros  

- **ip_ptr**: puntero a la instancia de IP.
- **group_address**: dirección IPv6 de multidifusión.
- **interface_index**: índice de la interfaz de red asociada al grupo.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Salida correcta del grupo de multidifusión.
- **NX_ENTRY_NOT_FOUND**: (0x16) No se encontró la entrada.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 o la característica de multidifusión de IPv6 no se han compilado en la biblioteca de NetX Duo.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IPv6 no válida.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0

/* Leave multicast address on this IP instance. */
status = nxd_ipv6_multicast_interface_leave(&ip_0,
                                            &group_address,
                                            primary_interface);

/* If status == NX_SUCCESS, interface of index on IP instance
   has left the multicast group. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join

## <a name="nxd_ipv6_stateless_address_autoconfig_disable"></a>nxd_ipv6_stateless_address_autoconfig_disable
Deshabilitar la configuración automática de direcciones sin estado

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_stateless_address_autoconfig_disable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>Descripción

Este servicio deshabilita la característica de configuración automática de direcciones IPv6 sin estado en un dispositivo de red especificado. No tiene ningún efecto si se ha configurado la dirección IPv6.

Este servicio está disponible si se compila la biblioteca de NetX Duo con la opción ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL*** definida.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP.
- **interface_index**: índice de la interfaz de red en el que se debe deshabilitar la configuración automática de direcciones IPv6 sin estado.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Se ha deshabilitado correctamente la característica de configuración automática de direcciones sin estado.
- **NX_NOT_SUPPORTED**: (0X4B) La característica de IPv6 o la característica de control de configuración automática de direcciones IPv6 sin estado no se han compilado en la biblioteca de NetX Duo.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE 0

/* Disable stateless address auto configuration on this IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_disable(&ip_0,
                                                       PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, disables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>Consulte también 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_stateless_address_autoconfig_enable"></a>nxd_ipv6_stateless_address_autoconfig_enable
Habilitar la configuración automática de direcciones sin estado

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_ipv6_stateless_address_autoconfig_enable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>Descripción

Este servicio habilita la característica de configuración automática de direcciones IPv6 sin estado en un dispositivo de red especificado.

Este servicio está disponible si se compila la biblioteca de NetX Duo con la opción ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL*** definida.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP.
- **interface_index**: índice de la interfaz de red en el que se debe habilitar la configuración automática de direcciones IPv6 sin estado.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Se ha habilitado correctamente la característica de configuración automática de direcciones sin estado.
- **NX_ALREADY_ENABLED**: (0x15) Ya está habilitado.
- **NX_NOT_SUPPORTED**: (0X4B) La característica de IPv6 o la característica de control de configuración automática de direcciones IPv6 sin estado no se han compilado en la biblioteca de NetX Duo.
- **NX_INVALID_INTERFACE**: (0x4C) El índice de la interfaz no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero al bloque de control de IP no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
#define PRIMARY_INTERFACE

/* Enable stateless address auto configuration on this
   IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_enable(&ip_0,
                                                      PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, enables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>Consulte también 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable

## <a name="nxd_nd_cache_entry_delete"></a>nxd_nd_cache_entry_delete
Eliminar la entrada de la dirección IPv6 de la memoria caché de vecinos

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_nd_cache_entry_delete(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>Descripción

Este servicio elimina una entrada de la memoria caché de detección de vecinos de IPv6 para la dirección IP proporcionada. La función IPv4 de NetX equivalente es ***nx_arp_static_entry_delete***.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: puntero a la dirección IPv6 que se va a eliminar, en el orden de bytes del host.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha eliminado correctamente la dirección.
- **NX_ENTRY_NOT_FOUND**: (0x16) No se encontró la dirección en la memoria caché de vecinos de IPv6.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_PTR_ERROR**: (0x07) Espacio de almacenamiento o instancia de IP no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* This example deletes an entry from the neighbor cache table. */

NXD_ADDRESS ip_address;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Delete an entry in the neighbor cache table with the specified IPv6
   address and hardware address. */
status = nxd_nd_cache_entry_delete(&ip_0,
                                   &ip_address.nxd_ip_address.v6[0]);

/* If status == NX_SUCCESS, the entry was deleted from the neighbor cache
   table. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set
Agregar una dirección IPv6 y una asignación de MAC a la memoria caché de vecinos

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_nd_cache_entry_set(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *dest_ip,
    UINT interface_index, 
    char *mac);
```

### <a name="description"></a>Descripción

Este servicio agrega una entrada a la memoria caché de detección de vecinos para la dirección IP especificada *ip_address* asignada a la dirección MAC de hardware en el índice de interfaz de red especificado (interface_index). El servicio IPv4 de NetX equivalente es ***nx_arp_static_entry_create***.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **dest_ip**: puntero a la instancia de dirección IPv6.
- **interface_index**: índice que especifica la interfaz de red física mediante la que se puede tener acceso a la dirección IPv6 de destino. 
- **mac**: puntero a la dirección de hardware.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Entrada agregada correctamente.
- **NX_NOT_SUCCESSFUL**: (0x43) Memoria caché no válida o no hay entradas disponibles en la memoria caché de vecinos.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_PTR_ERROR**: (0x07) Espacio de almacenamiento o instancia de IP no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) Valor del índice de interfaz no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* This example adds an entry on the primary network interface to
   the neighbor cache table. */

#define PRIMARY_INTEFACE 0

NXD_ADDRESS ip_address;
UCHAR hw_address[6] = {0x0, 0xcf,0x01,0x02, 0x03, 0x04};
CHAR  *mac;

mac = (CHAR *)&hw_address[0];

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Create an entry in the neighbor cache table with the specified
   IPv6 address and hardware address. */
status = nxd_nd_cache_entry_set(&ip_0,
                                &ip_address.nxd_ip_address.v6[0],
                                PRIMARY_INTERFACE, mac);

/* If status == NX_SUCCESS, the entry was added to the neighbor
   cache table. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_hardware_address_find"></a>nxd_nd_cache_hardware_address_find
Buscar la dirección de hardware de una dirección IPv6

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_nd_cache_hardware_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG *physical_msw,
    ULONG *physical_lsw
    UINT *interface_index);
```
### <a name="description"></a>Descripción

Este servicio intenta encontrar una dirección de hardware física en la memoria caché de detección de vecinos de IPv6 que está asociada con la dirección IPv6 proporcionada. También se devuelve el índice de la interfaz de red mediante la cual se puede llegar al vecino en el parámetro *interface_index*. El servicio IPv4 de NetX equivalente es ***nx_arp_hardware_address_find***.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: puntero a la dirección IP que se va a buscar, en el orden de bytes del host.
- **physical_msw**: puntero a los 16 bits superiores (del 47 al 32) de la dirección física, en el orden de bytes del host. 
- **physical_lsw**: puntero a los 32 bits inferiores (del 31 al 0) de la dirección física, en el orden de bytes del host.
- **interface_index**: puntero a la ubicación de memoria válida para el índice de interfaz que especifica el dispositivo de red en el que se puede acceder a la dirección IPv6.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha encontrado correctamente la dirección.
- **NX_ENTRY_NOT_FOUND**: (0x16) La asignación no está en la memoria caché de vecinos.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_INVALID_PARAMETERS**: (0x4D) La dirección IP proporcionada no es de la versión 6.
- **NX_PTR_ERROR**: (0x07) Espacio de almacenamiento o instancia de IP no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* This example inputs an IP address on the primary network in order
   to obtain the hardware address it is mapped to in the neighbor
   cache able. */

NXD_ADDRESS  ip_address;
ULONG physical_msw, physical_lsw;
UINT  interface_index;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Obtain the hardware address mapped to the supplied global IPv6
   address. */
status = nxd_nd_cache_hardware_address_find(&ip_0, &ip_address,
                                            &physical_msw,
                                            &physical_lsw
                                            &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the hardware address returned in
   variables physical_msw and physical_lsw, the index of the network
   interface through which the neighbor can be reached is stored in
   interface_index. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate
Invalidar la memoria caché de detección de vecinos

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_nd_cache_invalidate(NX_IP *ip_ptr);
```
### <a name="description"></a>Descripción

Este servicio invalida toda la memoria caché de detección de vecinos de IPv6. Este servicio se puede invocar antes o después de que se haya habilitado ICMPv6. Este servicio no es aplicable a la conectividad IPv4, por lo que no hay ningún servicio equivalente en NetX.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Memoria caché invalidada correctamente.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_PTR_ERROR**: (0x07) Instancia de IP no válida.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* This example invalidates the host neighbor cache table. */

/* Invalidate the cache table bound to the IP instance. */
status = nxd_nd_cache_invalidate (&ip_0);

/* If status == NX_SUCCESS, all entries in the neighbor cache table
   are invalidated. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find
Recuperar la dirección IPv6 de una dirección física

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_nd_cache_ip_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT *interface_index);
```
### <a name="description"></a>Descripción

Este servicio intenta encontrar una dirección IPv6 en la memoria caché de detección de vecinos de IPv6 que está asociada con la dirección física proporcionada. También se devuelve el índice de la interfaz de red mediante la cual se puede llegar al vecino. El servicio IPv4 de NetX equivalente es ***nx_arp_ip_address_find***.

### <a name="parameters"></a>Parámetros 

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: puntero a una estructura NXD_ADDRESS válida.
- **physical_msw**: 16 bits superiores (del 47 al 32) de la dirección física que se va a buscar, en orden de bytes del host.
- **physical_lsw**: 32 bits inferiores (del 31 al 0) de la dirección física que se va a buscar, en orden de bytes del host.
- **interface_index**: puntero al índice del dispositivo de red mediante el cual se puede acceder a la dirección IPv6.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha encontrado correctamente la dirección.
- **NX_ENTRY_NOT_FOUND**: (0x16) No se encontró la dirección física en la memoria caché de vecinos.
- **NX_NOT_SUPPORTED**: (0x4B) La característica de IPv6 no se ha compilado en la biblioteca de NetX Duo.
- **NX_PTR_ERROR**: (0x07) Espacio de almacenamiento o instancia de IP no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido. 
- **NX_INVALID_PARAMETERS**: (0x4D) La dirección MAC es cero.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* This example inputs a hardware address to search on for the
   matching IPv6 global address in the neighbor cache table. */

NXD_ADDRESS ip_address;
ULONG physical_msw = 0xcf;
ULONG physical_lsw = 0x01020304;
UINT  interface_index;

/* Obtain the IPv6 address mapped to the supplied hardware
   Address on the primary device. */
status = nxd_nd_cache_ip_address_find(&ip_0, &ip_address,
                                      physical_msw, physical_lsw,
                                      &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the global IPv6 address returned in
   variable ip_address. */
```
### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate

## <a name="nxd_tcp_client_socket_connect"></a>nxd_tcp_client_socket_connect
Establecer una conexión TCP

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr
    NXD_ADDRESSS *server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio realiza una conexión TCP con un socket de cliente TCP creado previamente en el puerto del servidor especificado. Este servicio funciona en redes IPv4 o IPv6. Los puertos de servidor TCP válidos oscilan entre 0 y 0xFFFF. NetX Duo determina la interfaz física adecuada en función de la dirección IP del servidor. El equivalente IPv4 de NetX es ***nx_tcp_client_socket_connect***.

El socket debe estar enlazado a un puerto local.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket TCP creado anteriormente.
- **server_IP**: puntero a la dirección de destino IPv4 o IPv6, en el orden de bytes del host.
- **server_port**: número de puerto del servidor al que conectarse (de 1 a 0xFFFF), en el orden de bytes del host.
- **wait_option**: opción de espera mientras se establece la conexión. Las opciones de espera se definen de la siguiente forma:
    - **NX_NO_WAIT**: (0x00000000)
    - **NX_WAIT_FOREVER**: (0xFFFFFFFF)
    - **valor de tiempo de espera en tics**: (0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Socket conectado correctamente.
- **NX_WAIT_ABORTED**: (0x1A) Una llamada a tx_thread_wait_abort ha cancelado la suspensión solicitada.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IPv4 o IPv6 del servidor no válida.
- **NX_NOT_BOUND**: (0x24) El socket no está enlazado.
- **NX_NOT_CLOSED**: (0x35) El socket no está en estado cerrado.
- **NX_IN_PROGRESS**: (0x37) No se ha especificado ninguna espera, el intento de conexión está en curso.
- **NX_INVALID_INTERFACE**: (0x4C) Índice de interfaz no válido.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) La interfaz de red no tiene una dirección IPv6 válida.
- **NX_NOT_ENABLED**: (0x14) TCP no está habilitado.
- **NX_INVALID_PORT**: (0x46) Puerto no válido.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_CONNECTED**: (0x38) Error en la conexión.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS peer_ip_address;
ULONG       peer_port;

/* Set Peer IPv6 address */
peer_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
peer_ip_address.nxd_ip_address.v6[0] = 0x20010000;
peer_ip_address.nxd_ip_address.v6[1] = 0;
peer_ip_address.nxd_ip_address.v6[2] = 0;
peer_ip_address.nxd_ip_address.v6[3] = 0x101;

/* Set peer port number */
peer_port = 2563;

/* Connect to the peer */
status = nxd_tcp_client_socket_connect(socket_ptr,
                                       &peer_ip_address,
                                       peer_port, NX_WAIT_FOREVER);
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_socket_peer_info_get

## <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get
Recuperar la dirección IP y el número de puerto del socket TCP del nodo del mismo nivel

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_tcp_socket_peer_info_get
    (NX_TCP_SOCKET *socket_ptr,
    NXD_ADDRESS *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>Descripción

Este servicio recupera la información de puerto y dirección IP del nodo del mismo nivel para el socket TCP conectado mediante la red IPv4 o IPv6. El servicio IPv4 de NetX equivalente es ***nx_tcp_socket_peer_info_get***.

Tenga en cuenta que *socket_ptr* debe apuntar a un socket TCP que ya esté en estado conectado.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket TCP conectado al host del nodo del mismo nivel.
- **peer_ip_address**: puntero a la dirección IPv4 o IPv6 del nodo del mismo nivel. La dirección IP devuelta está en el orden de bytes del host.
- **peer_port**: puntero al número de puerto del nodo del mismo nivel. El número de puerto devuelto está en el orden de bytes del host.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Información del socket recuperada correctamente.
- **NX_NOT_CONNECTED**: (0x38) Socket no conectado al nodo del mismo nivel.
- **NX_NOT_ENABLED**: (0x14) TCP no está habilitado.
- **NX_PTR_ERROR**: (0x07) Entrada de puntero no válida.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS  peer_ip_address;
ULONG        peer_port;

/* Get TCP socket information. */
status = nxd_tcp_socket_peer_info_get(socket_ptr, &peer_ip_address,
                                      &peer_port);

/* If status == NX_SUCCESS, the service returns valid peer info: */
if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V4)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v4 */

if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V6)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v6 */
```
### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect

## <a name="nxd_udp_packet_info_extract"></a>nxd_udp_packet_info_extract
Extraer parámetros de red de un paquete UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>Descripción

Este servicio extrae los parámetros de red de un paquete recibido en redes UDP IPv4 o IPv6. El servicio equivalente de NetX es ***nx_udp_packet_info_extract***.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete.
- **ip_address**: puntero a la dirección IP del emisor.
- **protocol**: puntero al protocolo que se va a devolver.
- **port**: puntero al número de puerto del emisor.
- **interface_index**: puntero al índice de la interfaz de red desde la que se recibe este paquete.

### <a name="return-values"></a>Valores devueltos 

- **NX_SUCCESS**: (0x00) Datos de la interfaz de paquetes extraídos correctamente.
- **NX_INVALID_PACKET**: (0x12) El paquete no es IPv4 ni IPv6.
- **NX_PTR_ERROR**: (0x07) Entrada de puntero no válida.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Extract network data from UDP packet interface.*/
status = nxd_udp_packet_info_extract(packet_ptr, &ip_address,
                                    &protocol, &port,
                                    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved.*/
```
### <a name="see-also"></a>Consulte también 

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send
Enviar un datagrama UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port);
```
### <a name="description"></a>Descripción

Este servicio envía un datagrama UDP mediante un socket UDP previamente creado y enlazado para redes IPv4 o IPv6. NetX Duo encuentra una dirección IP local adecuada como dirección de origen en función de la dirección IP de destino. Para especificar una interfaz y una dirección IP de origen específicas, la aplicación debe usar el servicio ***nxd_udp_socket_source_send***.

Tenga en cuenta que este servicio vuelve inmediatamente, independientemente de si el datagrama UDP se ha enviado correctamente. El servicio equivalente de NetX (IPv4) es ***nx_udp_socket_send***.

El socket debe estar enlazado a un puerto local.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.
- **packet_ptr**: puntero al paquete del datagrama UDP.
- **ip_address**: puntero a la dirección IPv4 o IPv6 de destino.
- **port**: número de puerto de destino válido (entre 1 y 0xFFFF), en el orden de bytes del host.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Envío correcto desde el socket UDP.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IPv4 o IPv6 del servidor no válida.
- **NX_NOT_BOUND**: (0x24) Socket no enlazado a ningún puerto.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) No se ha podido encontrar ninguna interfaz de salida adecuada.
- **NX_UNDERFLOW**: (0x02) No hay suficiente espacio para el encabezado UDP en el paquete.
- **NX_OVERFLOW**: (0x03) El puntero de anexión del paquete no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero de socket, puntero de dirección o puntero de paquete no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) No se ha habilitado UDP.
- **NX_INVALID_PORT**: (0x46) El número de puerto no está dentro de un intervalo válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS ip_address, server_address;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the
   IPv6 address just created on the primary device (index 0). We
   don’t need the index into the address table, so the last argument
   is set to null. */

interface_index = 0;
status = nxd_ipv6_address_set(&client_ip, interface_index,
                              &ip_address, 64, NX_NULL);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_send(&client_socket, packet_ptr,
                             &server_address, 12);

/* If status == NX_SUCCESS, the UDP host successfully transmitted
   the packet out the UDP socket to the server. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_source_send"></a>nxd_udp_socket_source_send
Enviar un datagrama UDP

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port, 
    UINT address_index);
```
### <a name="description"></a>Descripción

Este servicio envía un datagrama UDP mediante un socket UDP previamente creado y enlazado para redes IPv4 o IPv6. El parámetro *address_index* especifica la dirección IP de origen que se va a utilizar para el paquete saliente. Tenga en cuenta que la función vuelve inmediatamente, independientemente de si el datagrama UDP se ha enviado correctamente.

El socket debe estar enlazado a un puerto local.

El servicio equivalente de NetX (IPv4) es ***nx_udp_socket_source_send***.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.
- **packet_ptr**: puntero al paquete del datagrama UDP.
- **ip_address**: puntero a la dirección IPv4 o IPv6 de destino. port: número de puerto de destino válido (entre 1 y 0xFFFF), en orden de bytes del host.
- **address_index**: índice que especifica la dirección de origen que se va a utilizar para el paquete.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Envío correcto desde el socket UDP.
- **NX_IP_ADDRESS_ERROR**: (0x21) Dirección IPv4 o IPv6 del servidor no válida.
- **NX_NOT_BOUND**: (0x24) Socket no enlazado a ningún puerto.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) No se ha podido encontrar ninguna interfaz de salida adecuada.
- **NX_NOT_FOUND**: (0x4E) No se puede encontrar ninguna interfaz adecuada.
- **NX_PTR_ERROR**: (0x07) Puntero de socket, dirección o puntero de paquete no válidos.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) No se ha habilitado UDP.
- **NX_INVALID_PORT**: (0x46) El número de puerto no está dentro del intervalo válido.
- **NX_INVALID_INTERFACE**: (0x4C) La interfaz de red especificada no es válida.
- **NX_UNDERFLOW**: (0x02) No hay suficiente espacio para el encabezado UDP en el paquete.
- **NX_OVERFLOW**: (0x03) El puntero de anexión del paquete no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS ip_address, server_address;
UINT address_index;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the IPv6
   address just created on the primary device (index 0). The address index
   is needed for nxd_udp_socket_source_send. */

status = nxd_ipv6_address_set(&client_ip, 0,
                              &ip_address, 64, &address_index);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_source_send(&client_socket, packet_ptr,
                                    &server_address, 12, address_index);

/* If status == NX_SUCCESS, the UDP host successfully transmitted the
   packet out the UDP socket to the server. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_source_extract

## <a name="nxd_udp_source_extract"></a>nxd_udp_source_extract
Recuperar la información de origen del paquete UPD

### <a name="prototype"></a>Prototipo  

```c
UINT nxd_udp_source_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address, 
    UINT *port);
```
### <a name="description"></a>Descripción

Este servicio extrae la dirección IP y el número de puerto de origen de un paquete UDP recibido mediante el socket UDP del host. El equivalente de NetX (IPv4) es ***nx_udp_source_extract***.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete UDP recibido.
- **ip_address**: puntero a la estructura NXD_ADDRESS que va a almacenar la dirección IP de origen del paquete.
- **port**: puntero al número de puerto del socket UDP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Extracción correcta del origen.
- **NX_INVALID_PACKET**: (0x12) El paquete no es válido.
- **NX_PTR_ERROR**: (0x07) Puntero de socket no válido.
- **NX_CALLER_ERROR** (0x11) El autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS ip_address;
UINT         port;

/* Create the UDP socket client_socket and
   allocate the packet pointed to by packet_ptr (not shown). */

/* Extract the IP address and port of the packet received on the UDP
   socket specified in the packet interface. */
status = nxd_udp_source_extract(&packet_ptr, &ip_address, &port);

/* If status == NX_SUCCESS, the source IP address and port of the
   packet received on the UDP socket was successfully extracted. */
```
### <a name="see-also"></a>Consulte también

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send