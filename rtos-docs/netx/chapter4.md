---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios de Azure RTOS NetX en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814481"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a>Capítulo 4: Descripción de los servicios de Azure RTOS NetX

Este capítulo contiene una descripción de todos los servicios de Azure RTOS NetX en orden alfabético. Los nombres de los servicios están diseñados de modo que todos los servicios similares están agrupados. Por ejemplo, todos los servicios ARP se encuentran al principio de este capítulo.

> [!NOTE]
> *Tenga en cuenta que una API de socket compatible con BSD está disponible para el código de aplicación heredado que no puede sacar el máximo partido de la API NetX de alto rendimiento. Consulte el Apéndice D para obtener más información sobre la API de socket compatible con BSD.*

En la sección "Valores devueltos" de cada descripción, los valores en **NEGRITA** no se ven afectados por la opción NX_DISABLE_ERROR_CHECKING que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están deshabilitados por completo. Las secciones "Permitido desde" indican desde donde se puede llamar a cada servicio de NetX.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

Invalida todas las entradas dinámicas en la memoria caché de ARP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio invalida todas las entradas de ARP dinámicas que se encuentran actualmente en la memoria caché de ARP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la caché de ARP se invalidó correctamente.
- **NX_NOT_ENABLED**: (0x14) ARP no está habilitado.
- **NX_PTR_ERROR**: (0x07) la dirección IP no es válida.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

Establece la entrada de ARP dinámica.

### <a name="prototype"></a>Prototipo

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Descripción

Este servicio asigna una entrada dinámica de la memoria caché de ARP y configura la dirección IP especificada a la asignación de la dirección física. Si no se especifica ninguna dirección física, se envía una solicitud de ARP real a la red para que se resuelva dicha dirección. Tenga en cuenta también que esta entrada se quitará si está activa la caducidad de ARP o si se ha agotado la memoria caché de ARP y se trata de la entrada de ARP usada menos recientemente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP que se va a asignar.
- **physical_msw**: los 16 bits superiores (47-32) de la dirección física.
- **physical_lsw**: los 32 bits inferiores (31-0) de la dirección física.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la entrada dinámica de ARP se estableció correctamente.
- **NX_NO_MORE_ENTRIES**: (0X17) no hay más entradas de ARP disponibles en la memoria caché de ARP.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.
- **NX_PTR_ERROR**: (0x07) el puntero de instancia de IP no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate, nx_arp_enable,
- nx_arp_gratuitous_send, nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_enable"></a>nx_arp_enable

Habilita el protocolo de resolución de direcciones (ARP).

### <a name="prototype"></a>Prototipo

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a>Descripción

Este servicio inicializa el componente ARP de NetX para la instancia de IP específica. La inicialización de ARP incluye la configuración de la caché de ARP y varias rutinas de procesamiento de ARP necesarias para enviar y recibir mensajes de ARP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **arp_cache_memory**: puntero al área de memoria para colocar la caché de ARP.
- **arp_cache_size**: cada entrada de ARP tiene 52 bytes. Por lo tanto el número total de entradas de ARP es el tamaño dividido entre 52.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) ARP se habilitó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de memoria caché o la IP no son válidos.
- **NX_SIZE_ERROR**: (0x09) la memoria caché de ARP proporcionada por el usuario es demasiado pequeña.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_ALREADY_ENABLED**: (0X15) este componente ya se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_gratuitous_send, nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

Envía una solicitud de ARP innecesaria.

### <a name="prototype"></a>Prototipo

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Descripción

Este servicio recorre todas las interfaces físicas para transmitir solicitudes de ARP innecesarias, siempre y cuando la dirección IP de la interfaz sea válida. Si posteriormente se recibe una respuesta de ARP, se llama al controlador de respuesta proporcionado para procesar la respuesta al ARP innecesario.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **response_handler**: puntero a la función de control de respuesta. Si se proporciona NX_NULL, se omiten las respuestas.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se realizó correctamente el envío de ARP innecesario.
- **NX_NO_PACKET**: (0X01) no hay ningún paquete disponible.
- **NX_NOT_ENABLED**: (0x14) ARP no está habilitado.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP actual no es válida.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

Buscar la dirección de hardware físico dada una dirección IP

### <a name="prototype"></a>Prototipo

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a>Descripción

Este servicio intenta encontrar una dirección de hardware físico en la memoria caché de ARP que está asociada con la dirección IP proporcionada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP que se buscará.
- **physical_msw**: puntero a la variable para devolver los 16 bits superiores (47-32) de la dirección física.
- **physical_lsw**: puntero a la variable para devolver los 32 bits inferiores (31-0) de la dirección física.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se encontró la dirección de hardware de ARP correctamente.
- **NX_ENTRY_NOT_FOUND**: (0x16) no se encontró la asignación en la memoria caché de ARP.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.
- **NX_PTR_ERROR** (0x07) Puntero de memoria o IP no válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_info_get"></a>nx_arp_info_get

Recupera información acerca de las actividades de ARP.

### <a name="prototype"></a>Prototipo

```C
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

*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de la llamada.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **arp_requests_sent**: puntero al destino para el total de solicitudes de ARP enviadas desde esta instancia de IP.
- **arp_requests_received**: puntero al destino para el total de solicitudes de ARP recibidas de la red.
- **arp_responses_sent**: puntero al destino para el total de respuestas de ARP enviadas desde esta instancia de IP.
- **arp_responses_received**: puntero al destino para el total de respuestas de ARP recibidas de la red.
- **arp_dynamic_entries**: puntero al destino para el número actual de entradas de ARP dinámicas.
- **arp_static_entries**: puntero al destino para el número actual de entradas de ARP estáticas.
- **arp_aged_entries**: puntero al destino del número total de entradas de ARP que han vencido y han dejado de ser válidas.
- **arp_invalid_messages**: puntero al destino del total de mensajes de ARP no válidos recibidos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la información de ARP se recuperó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
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

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_ip_address_find,
- nx_arp_static_entries_delete, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

Busca la dirección IP según una dirección física.

### <a name="prototype"></a>Prototipo

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a>Descripción

Este servicio intenta buscar una dirección IP en la memoria caché de ARP que está asociada con la dirección física proporcionada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: puntero para devolver la dirección IP, si se encuentra una que se ha asignado.
- **physical_msw**: los 16 bits superiores (47-32) de la dirección física que se buscará.
- **physical_lsw**: los 32 bits inferiores (31-0) de la dirección física que se buscará.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se encontró la dirección IP de ARP correctamente.
- **NX_ENTRY_NOT_FOUND**: (0x16) no se encontró la asignación en la memoria caché de ARP.
- **NX_PTR_ERROR** (0x07) Puntero de memoria o IP no válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.
- **NX_INVALID_PARAMETERS**: (0x4D) los elementos Physical_msw y physical_lsw son 0.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_static_entries_delete,nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

Elimina todas las entradas de ARP estáticas.

### <a name="prototype"></a>Prototipo

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina todas las entradas estáticas en la caché de ARP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se eliminan las entradas estáticas.
- **NX_PTR_ERROR** (0x07) Puntero ip_ptr no válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

Crea una dirección IP estática para la asignación de hardware en la caché de ARP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Descripción

Este servicio crea una asignación estática de la dirección IP a la dirección física en la caché de ARP para la instancia de IP especificada. Las entradas de ARP estáticas no están sujetas a actualizaciones periódicas de ARP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP que se va a asignar.
- **physical_msw**: los 16 bits superiores (47-32) de la dirección física que se va a asignar.
- **physical_lsw**: los 32 bits inferiores (31-0) de la dirección física que se va a asignar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la entrada estática de ARP se creó correctamente.
- **NX_NO_MORE_ENTRIES**: (0X17) no hay más entradas de ARP disponibles en la memoria caché de ARP.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.
- **NX_INVALID_PARAMETERS**: (0x4D) los elementos Physical_msw y physical_lsw son 0.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

Elimina una dirección IP estática para la asignación de hardware en la caché de ARP.


### <a name="prototype"></a>Prototipo

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Descripción

Este servicio busca y elimina una asignación estática de dirección IP a dirección física creada anteriormente en la caché de ARP para la instancia de IP especificada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: la dirección IP se asignó estáticamente.
- **physical_msw**: los 16 bits superiores (47-32) de la dirección física asignada estáticamente.
- **physical_lsw**: los 32 bits inferiores (31-0) de la dirección física asignada estáticamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la entrada estática de ARP se eliminó correctamente.
- **NX_ENTRY_NOT_FOUND**: (0x16) no se encontró la entrada de ARP estática en la caché de ARP.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.
- **NX_INVALID_PARAMETERS**: (0x4D) los elementos Physical_msw y physical_lsw son 0.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a>Consulte también

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create

## <a name="nx_icmp_enable"></a>nx_icmp_enable

Habilita el Protocolo de mensajes de control de Internet (ICMP).

### <a name="prototype"></a>Prototipo

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita el componente ICMP para la instancia de IP especificada.
El componente ICMP es responsable de controlar los mensajes de error de Internet y las solicitudes y respuestas de ping.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) ICMP se habilitó correctamente.
- **NX_ALREADY_ENABLED**: (0x15) ICMP ya está habilitado.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a>Consulte también

- nx_icmp_info_get, nx_icmp_ping

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get

Recupera información acerca de las actividades de ICMP.

### <a name="prototype"></a>Prototipo

```C
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

*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de la llamada.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **pings_sent**: puntero al destino para el número total de pings enviados.
- **ping_timeouts**: puntero al destino para el número total de tiempos de espera de ping.
- **ping_threads_suspended**: puntero al destino del número total de subprocesos suspendidos en solicitudes de ping.
- **ping_responses_received**: puntero al destino del número total de respuestas de ping recibidas.
- **icmp_checksum_errors**: puntero al destino del número total de errores de suma de comprobación de ICMP.
- **icmp_unhandled_messages**: puntero al destino del número total de mensajes de ICMP no administrados.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la información de ICMP se recuperó correctamente.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_icmp_enable, nx_icmp_ping

## <a name="nx_icmp_ping"></a>nx_icmp_ping

Envía una solicitud de ping a la dirección IP especificada.

### <a name="prototype"></a>Prototipo

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía una solicitud de ping a la dirección IP especificada y espera un mensaje de respuesta de ping durante el período de tiempo especificado. Si no se recibe ninguna respuesta, se devuelve un error. De lo contrario, se devuelve el mensaje de respuesta completo en la variable a la que apunta el elemento response_ptr.

*Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido cuando ya no se necesite.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP, en orden de bytes del host, a la que se va a hacer ping. Puntero de datos al área de datos para el mensaje de ping.
- **data_size**: número de bytes en los datos de ping
- **response_ptr**: puntero al puntero de paquete en el que se devuelve el mensaje de respuesta de ping.
- **wait_option**: define cuánto tiempo se debe esperar una respuesta de ping. Las opciones de espera se definen de la siguiente forma:

  - NX_NO_WAIT (0x00000000)
  - NX_WAIT_FOREVER (0xFFFFFFFF)
  - Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el ping se hizo correctamente. El puntero del mensaje de respuesta se ha colocado en la variable a la que apunta el elemento response_ptr.
- **NX_NO_PACKET**: (0X01) no se pudo asignar un paquete de solicitud de ping.
- **NX_OVERFLOW**: (0x03) el área de datos especificada supera el tamaño de paquete predeterminado para esta instancia de IP.
- **NX_NO_RESPONSE**: (0x29) la IP solicitada no ha respondido.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.
- **NX_PTR_ERROR** (0x07) Puntero de respuesta o IP no válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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

- nx_icmp_enable, nx_icmp_info_get

## <a name="nx_igmp_enable"></a>nx_igmp_enable

Habilita el protocolo de administración de grupos de Internet (IGMP).

### <a name="prototype"></a>Prototipo

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita el componente IGMP en la instancia de IP especificada.
El componente IGMP es responsable de proporcionar compatibilidad con las operaciones de administración de grupos de multidifusión de IP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) IGMP se habilitó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_ALREADY_ENABLED**: (0X15) este componente ya se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a>Consulte también

- nx_igmp_info_get,nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get

Recupera información acerca de las actividades de IGMP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de IGMP de la instancia de IP especificada.

*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de la llamada.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **igmp_reports_sent**: puntero al destino para el número total de informes de ICMP enviados.
- **igmp_queries_received**: puntero al destino para el número total de consultas recibidas por el enrutador de multidifusión.
- **igmp_checksum_errors**: puntero al destino del número total de errores de suma de comprobación de IGMP en paquetes recibidos.
- **current_groups_joined**: puntero al destino del número actual de grupos unidos a través de esta instancia de IP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la información de IGMP se recuperó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_igmp_enable, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

Deshabilita el bucle invertido de IGMP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita el bucle invertido de IGMP para todos los grupos de multidifusión posteriores combinados.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) el bucle invertido de IGMP se deshabilitó correctamente.
- **NX_NOT_ENABLED** (0x14) IGMP no está habilitado.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso ni una inicialización.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a>Consulte también

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

Habilita el bucle invertido de IGMP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita el bucle invertido de IGMP para todos los grupos de multidifusión posteriores combinados.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) el bucle invertido de IGMP se deshabilitó correctamente.
- **NX_NOT_ENABLED** (0x14) IGMP no está habilitado.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso ni una inicialización.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a>Consulte también

- nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join

Conecta la instancia de IP al grupo de multidifusión especificado a través de una interfaz.

### <a name="prototype"></a>Prototipo

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio conecta una instancia de IP al grupo de multidifusión especificado a través de una interfaz de red especificada. Se mantiene un contador interno para realizar un seguimiento del número de veces que se ha unido el mismo grupo. Después de unirse al grupo de multidifusión, el componente IGMP permitirá la recepción de paquetes IP con esta dirección de grupo a través de la interfaz de red especificada y también notificará a los enrutadores que esta IP forma parte de este grupo de multidifusión. Los mensajes de unión, informe y abandono de la pertenencia a IGMP también se envían a través de la interfaz de red especificada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **group_address**: dirección del grupo de multidifusión IP de la clase D que se unirá en el orden de bytes del host.
- **interface_index**: índice de la interfaz asociada a la instancia de NetX.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el grupo de multidifusión se unió correctamente.
- **NX_NO_MORE_ENTRIES**: (0X17) no se pueden unir más grupos de multidifusión; se superó el máximo.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) el índice del dispositivo apunta a una interfaz de red no válida.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección del grupo de multidifusión proporcionada no es una dirección de clase D válida.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) la compatibilidad con la multidifusión IP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a>Consulte también

- nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

Conecta la instancia de IP al grupo de multidifusión especificado.

### <a name="prototype"></a>Prototipo

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Descripción

Este servicio une una instancia de IP al grupo de multidifusión especificado. Se mantiene un contador interno para realizar un seguimiento del número de veces que se ha conectado el mismo grupo. El controlador recibe la orden de enviar un informe de IGMP si se trata de la primera vez que se solicita la unión en la red que indica la intención del host para unirse al grupo. Una vez unido, el componente IGMP permitirá la recepción de paquetes IP con esta dirección de grupo y notificará a los enrutadores que esta dirección IP forma parte de este grupo de multidifusión.

> [!NOTE]
> *Para unirse a un grupo de multidifusión en un dispositivo no primario, use el servicio **nx_igmp_multicast_interface_join.***

- **Parámetros**

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **group_address**: dirección del grupo de multidifusión IP de la clase D que se unirá.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el grupo de multidifusión se unió correctamente.
- **NX_NO_MORE_ENTRIES**: (0X17) no se pueden unir más grupos de multidifusión; se superó el máximo.
- **NX_INVALID_INTERFACE**: (0x4C) el índice del dispositivo apunta a una interfaz de red no válida.
- **NX_IP_ADDRESS_ERROR** (0x21) Dirección de grupo IP no válida.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a>Consulte también

- nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

Hace que la instancia de IP salga del grupo de multidifusión especificado.

### <a name="prototype"></a>Prototipo

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Descripción

Este servicio hace que una instancia de IP salga del grupo de multidifusión especificado si el número de solicitudes para salir coincide con el número de solicitudes para unirse. De lo contrario, el recuento de uniones interno simplemente se reduce.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **group_address**: grupo de multidifusión que va a salir.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el grupo de multidifusión se unió correctamente.
- **NX_ENTRY_NOT_FOUND**: (0x16) no se encontró la solicitud anterior para unirse.
- **NX_INVALID_INTERFACE**: (0x4C) el índice del dispositivo apunta a una interfaz de red no válida.
- **NX_IP_ADDRESS_ERROR** (0x21) Dirección de grupo IP no válida.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Consulte también

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy

Envía una notificación a la aplicación si cambia la dirección IP.


### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a>Descripción

Este servicio registra una función de notificación de la aplicación a la que se llama cada vez que se cambia la dirección IP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **change_notify**: puntero a la función de notificación de cambio de IP. Si este parámetro es NX_NULL, se deshabilita la notificación de cambio de dirección IP.
- **additional_info**: puntero a información adicional opcional que también se proporciona a la función de notificación cuando se cambia la dirección IP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el cambio de dirección IP se notificó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,
- nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_address_get"></a>nx_ip_address_get

Recupera la dirección IP y la máscara de red.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Descripción

Este servicio recupera la dirección IP y la máscara de subred de la interfaz de red principal.

*Para obtener información del dispositivo secundario, use el servicio siguiente:
- **nx_ip_interface_address_get**.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: puntero al destino de la dirección IP.
- **network_mask**: puntero al destino de la máscara de red.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la dirección IP se obtuvo correctamente.
- **NX_PTR_ERROR**: (0X07) la IP o el puntero de variable devuelto no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_address_set"></a>nx_ip_address_set

Establece la dirección IP y la máscara de red.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Descripción

Este servicio establece la dirección IP y la máscara de red para la interfaz de red principal.

*Para establecer la dirección IP y la máscara de red para el dispositivo secundario, use el servicio **nx_ip_interface_address_set**.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: nueva dirección IP.
- **network_mask**: nueva máscara de red.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la dirección IP se estableció correctamente.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_create"></a>nx_ip_create

Crea una instancia de IP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de IP con la dirección IP y el controlador de red que proporcionó el usuario. Además, la aplicación debe proporcionar un grupo de paquetes creado previamente para la instancia de IP que se va a utilizar para la asignación interna de paquetes. Tenga en cuenta que no se llama al controlador de red de aplicación proporcionado hasta que se ejecuta este subproceso de IP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero al bloque de control para crear una nueva instancia de IP.
- **name**: nombre de esta nueva instancia de IP.
- **ip_address**: dirección IP de esta nueva instancia de IP.
- **network_mask**: máscara para delimitar la parte de la red de la dirección IP para los usos de subredes y superredes.
- **default_pool**: puntero al bloque de control del grupo de paquetes NetX creado previamente.
- **ip_network_driver**: controlador de red proporcionado por el usuario que se usa para enviar y recibir paquetes IP.
- **memory_ptr**: puntero al área de memoria del área de pila del subproceso del asistente de IP.
- **memory_size** Número de bytes en el área de memoria para la pila del subproceso del asistente de IP.
- **priority**: prioridad del subproceso del asistente de IP.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) la instancia de IP se creó correctamente.
- **NX_NOT_IMPLEMENTED**: (0x4A) la biblioteca NetX se configuro incorrectamente.
- **NX_PTR_ERROR**: (0X07) la IP, el puntero de función del controlador de red, el grupo de paquetes o el puntero de memoria no son válidos.
- **NX_SIZE_ERROR**: (0X09) el tamaño de pila proporcionado es demasiado pequeño.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_IP_ADDRESS_ERROR**: (0X21) la dirección IP proporcionada no es válida.
- **NX_OPTION_ERROR**: (0X21) la prioridad del subproceso de IP proporcionada no es válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_delete"></a>nx_ip_delete

Elimina la instancia de IP creada anteriormente.


### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de IP creada anteriormente y libera todos los recursos del sistema que pertenecen a la instancia de IP.

### <a name="parameters"></a>Parámetros
- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la dirección IP se eliminó correctamente.
- **NX_SOCKETS_BOUND**: (0X28) esta instancia de IP todavía tiene sockets UDP o TCP enlazados. Todos los sockets se deben desenlazar y eliminar antes de eliminar la instancia de IP.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

Emite el comando para el controlador de red.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Descripción

Este servicio proporciona una interfaz directa al controlador de la interfaz de red principal de la aplicación especificado durante la llamada ***nx_ip_create***.

Los comandos específicos de la aplicación se pueden usar siempre que su valor numérico sea mayor o igual que NX_LINK_USER_COMMAND.

*Para emitir el comando para el dispositivo secundario, use el servicio **nx_ip_driver_interface_direct_command**.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **command**: código de comando numérico. Los comandos estándar se definen de la siguiente manera:

- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)

- **return_value_ptr**: puntero a la variable devuelta en el autor de llamada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) comando directo de controlador de red correcto.
- **NX_UNHANDLED_COMMAND**: (0X44) comando de controlador de red no controlado o no implementado.
- **NX_PTR_ERROR**: (0X07) la IP o el puntero de valor devuelto no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) el índice de la interfaz no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

- **Adelantamiento posible**

No

### <a name="example"></a>Ejemplo

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command

Emite el comando para el controlador de red.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Descripción

Este servicio proporciona un comando directo al controlador de dispositivo de red de la aplicación en la instancia de IP. Los comandos específicos de la aplicación se pueden usar siempre que su valor numérico sea mayor o igual que *NX_LINK_USER_COMMAND*.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **command**: código de comando numérico. Los comandos estándar se definen de la siguiente manera:
- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)
- **interface_index**: índice de la interfaz de red a la que debe enviarse el comando.
- **return_value_ptr**: puntero a la variable devuelta en el autor de llamada.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) comando directo de controlador de red correcto.
- **NX_UNHANDLED_COMMAND**: (0X44) comando de controlador de red no controlado o no implementado.
- **NX_INVALID_INTERFACE**: (0x4C) el índice de interfaz no es válido.
- **NX_PTR_ERROR**: (0X07) la IP o el puntero de valor devuelto no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

Deshabilita el reenvío de paquetes IP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita el reenvío de paquetes IP dentro del componente IP de NetX. Al crear la tarea IP, este servicio se deshabilita automáticamente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el reenvío de IP se deshabilitó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

Habilita el reenvío de paquetes IP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita el reenvío de paquetes IP dentro del componente IP de NetX. Al crear la tarea IP, este servicio se deshabilita automáticamente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) el reenvío de IP se habilitó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

Deshabilita la fragmentación de paquetes IP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita la funcionalidad de fragmentación y reensamblado de paquetes IP. En el caso de los paquetes que esperan el reensamblado, este servicio los libera. Al crear la tarea de IP, este servicio se deshabilita automáticamente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0X00) el fragmento de IP se deshabilitó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) la fragmentación de IP no está habilitada en la instancia de IP.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

Habilita la fragmentación de paquetes IP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita la funcionalidad de fragmentación y reensamblado de paquetes IP. Al crear la tarea de IP, este servicio se deshabilita automáticamente.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0X00) el fragmento de IP se habilitó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) las características de fragmentación de IP no se compilan en NetX.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

Establece la dirección IP de la puerta de enlace.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a>Descripción

Este servicio establece la dirección IP de la puerta de enlace de IP. Todo el tráfico fuera de red se enruta a esta puerta de enlace para su transmisión. La puerta de enlace debe ser accesible directamente a través de una de las interfaces de red.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_address**: dirección IP de la puerta de enlace.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la dirección IP de la puerta de enlace se estableció correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de instancia de IP no es válido.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subproceso

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a>Consulte también

- nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete

## <a name="nx_ip_info_get"></a>nx_ip_info_get

Recupera información acerca de las actividades de la IP.

### <a name="prototype"></a>Prototipo

```C
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

Este servicio recupera información sobre las actividades de la IP de la instancia de IP especificada.

*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **ip_total_packets_sent**: puntero al destino para el número total de paquetes IP enviados.
- **ip_total_bytes_sent**: puntero al destino para el número total de bytes enviados.
- **ip_total_packets_received**: puntero al destino del número total de paquetes de recepción IP.
- **ip_total_bytes_received**: puntero al destino del número total de bytes de IP recibidos.
- **ip_invalid_packets**: puntero al destino del número total de paquetes IP no válidos.
- **ip_receive_packets_dropped**: puntero al destino del número total de paquetes recibidos anulados.
- **ip_receive_checksum_errors**: puntero al destino del número total de errores de suma de comprobación en paquetes recibidos.
- **ip_send_packets_dropped**: puntero al destino del número total de paquetes enviados anulados.
- **ip_total_fragments_sent**: puntero al destino del número total de fragmentos enviados.
- **ip_total_fragments_received**: puntero al destino del número total de fragmentos recibidos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la información de IP se recuperó correctamente.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get

Recupera la dirección IP de la interfaz.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Descripción

Este servicio recupera la dirección IP de una interfaz de red especificada.

*El dispositivo especificado, si no es el dispositivo primario, debe estar conectado previamente a la instancia de IP.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_index**: índice de la interfaz; el mismo valor que el índice de la interfaz de red asociada a la instancia de IP.
- **ip_address**: puntero al destino de la dirección IP de la interfaz del dispositivo.
- **network_mask**: puntero al destino de la máscara de red de la interfaz del dispositivo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la dirección IP se obtuvo correctamente.
- **NX_INVALID_INTERFACE**: (0x4C) la interfaz de red especificada no es válida.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_set, nx_ip_interface_attach,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set

Establece la dirección IP de la interfaz y la máscara de red.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Descripción

Este servicio establece la dirección IP y la máscara de red para la interfaz IP especificada.

*La interfaz especificada se debe conectar previamente a la instancia de IP.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_index**: índice de la interfaz asociada a la instancia de NetX.
- **ip_address**: nueva dirección IP de la interfaz de red.
- **network_mask**: nueva máscara de red de la interfaz.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la dirección IP se estableció correctamente.
- **NX_INVALID_INTERFACE**: (0x4C) la interfaz de red especificada no es válida.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) los punteros no son válidos.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get, nx_ip_interface_attach,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach

Conecta la interfaz de red a la instancia de IP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a>Descripción

Este servicio agrega una interfaz de red física a la interfaz IP. Tenga en cuenta que la instancia de IP se crea con la interfaz principal, por lo que cada interfaz adicional es secundaria para la interfaz principal. El número total de interfaces de red conectadas a la instancia de IP (incluida la interfaz principal) no puede superar el recuento de **NX_MAX_PHYSICAL_INTERFACES**.

Si el subproceso de IP todavía no se ha ejecutado, las interfaces secundarias se inicializarán como parte del proceso de inicio del subproceso de IP que inicializa todas las interfaces físicas.

Si el subproceso de IP aún no se está ejecutando, la interfaz secundaria se inicializa como parte del servicio ***nx_ip_interface_attach***.

*ip_ptr debe apuntar a una estructura IP de NetX válida.*

- ***NX_MAX_PHYSICAL_INTERFACES** debe configurarse para el número de interfaces de red de la instancia de IP. El valor predeterminado es uno.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_name**: puntero a la cadena de nombre de interfaz.
- **ip_address**: dirección IP del dispositivo en el orden de bytes del host.
- **network_mask**: máscara de red del dispositivo en el orden de bytes del host.
- **ip_link_driver**: controlador Ethernet para la interfaz.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la entrada se agrega a la tabla de enrutamiento estática.
- **NX_NO_MORE_ENTRIES**: (0x17) número máximo de interfaces.
- **NX_MAX_PHYSICAL_INTERFACES**: se superó el número máximo.
- **NX_DUPLICATED_ENTRY**: (0X52) la dirección IP suministrada ya se usa en esta instancia de IP.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) la entrada del puntero no es válida.
- **NX_IP_ADDRESS_ERROR**: (0x21) la entrada de la dirección IP no es válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

Recupera parámetros de la interfaz de red.


### <a name="prototype"></a>Prototipo

```C
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

*ip_ptr debe apuntar a una estructura IP de NetX válida. La interfaz especificada, si no es la principal, se debe conectar previamente a la instancia de IP.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **interface_index**: índice que especifica la interfaz de red.
- **interface_name**: puntero al búfer que contiene el nombre de la interfaz de red.
- **ip_address**: puntero al destino de la dirección IP de la interfaz.
- **network_mask**: puntero al destino de la máscara de red.
- **mtu_size**: puntero al destino de la unidad de transferencia máxima de esta interfaz.
- **physical_address_msw**: puntero al destino para los 16 bits superiores de la dirección MAC del dispositivo.
- **physical_address_lsw**: puntero al destino para los 32 bits inferiores de la dirección MAC del dispositivo.


### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) se obtuvo la información de la interfaz.
- **NX_PTR_ERROR**: (0x07) la entrada del puntero no es válida.
- **NX_INVALID_INTERFACE**: (0x4C) el puntero de la IP no es válido.
- **NX_CALLER_ERROR**: (0x11) no se llama al servicio desde el contexto de la inicialización del sistema o del subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check

Comprobar el estado de una instancia de IP


### <a name="prototype"></a>Prototipo

```C
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
- **interface_index**: número de índice de interfaz
- **needed_status** Estado de IP solicitado, definido en el formato de mapa de bits de la siguiente manera:
    - NX_IP_INITIALIZE_DONE (0x0001)
    - NX_IP_ADDRESS_RESOLVED (0x0002)
    - NX_IP_LINK_ENABLED (0x0004)
    - NX_IP_ARP_ENABLED (0x0008)
    - NX_IP_UDP_ENABLED (0x0010)
    - NX_IP_TCP_ENABLED (0x0020)
    - NX_IP_IGMP_ENABLED (0x0040)
    - NX_IP_RARP_COMPLETE (0x0080)
    - NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **actual_status** Puntero al destino del conjunto de bits real.
- **wait_option** Define cómo se comporta el servicio si los bits de estado solicitados no están disponibles. Las opciones de espera se definen de la siguiente forma:
    - NX_NO_WAIT (0x00000000)
    - NX_WAIT_FOREVER (0xFFFFFFFF)
    - Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) Comprobación de estado de IP correcta.
- **NX_NOT_SUCCESSFUL** (0X43) La solicitud de estado no se ha satisfecho dentro del tiempo de espera especificado.
- **NX_PTR_ERROR** (0x07) El puntero IP no es o ha dejado de ser válido o el puntero de estado real no es válido.
- **NX_OPTION_ERROR** (0x0a) Opción de estado necesario no válida.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) el valor de interface_index está fuera del intervalo. o la interfaz no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_info_get,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set

Establece la función de devolución de llamada de notificación de cambio de estado de vínculo.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a>Descripción

Este servicio configura la función de devolución de llamada de notificación de cambio del estado del vínculo. La rutina de *link_status_change_notify* proporcionada por el usuario se invoca cuando se cambia el estado de la interfaz principal o secundaria (por ejemplo, se cambia la dirección IP). Si *link_status_change_notify* es NULL, se deshabilita la característica de devolución de llamada de notificación de cambio del estado del vínculo.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero de bloque de control IP.
- **link_status_change_notify**: función de devolución de llamada proporcionada por el usuario a la que se llamará cuando se cambie la interfaz física.


### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se estableció correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de bloque de control de IP o el nuevo puntero de dirección física no son válidos.
- **NX_CALLER_ERROR**: (0x11) no se llama al servicio desde el contexto de la inicialización del sistema o del subproceso.


### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_info_get,
- nx_ip_interface_status_check

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

Deshabilita el envío o recepción de paquetes sin formato.


### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita la transmisión y recepción de paquetes IP sin formato para esta instancia de IP. Si el servicio de paquetes sin formato se habilitó previamente y hay paquetes sin formato en la cola de recepción, este servicio liberará cualquier paquete sin formato recibido.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) los paquetes de IP sin formato se deshabilitaron correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

Habilita el procesamiento de paquetes sin formato.


### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita la transmisión y recepción de paquetes IP sin formato para esta instancia de IP. Los paquetes TCP, UDP, ICMP e IGMP entrantes se siguen procesando en NetX. Los paquetes con tipos de protocolo de capa superior desconocidos se procesan mediante la rutina de recepción de paquetes sin formato.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) los paquetes de IP sin formato se habilitaron correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_interface_send"></a>nx_ip_raw_packet_interface_send

Envía un paquete de Raw IP a través de la interfaz de red especificada.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a>Descripción

Este servicio envía un paquete de Raw IP a la dirección IP de destino mediante la dirección IP local especificada como dirección de origen y a través de la interfaz de red asociada. Tenga en cuenta que esta rutina se devuelve inmediatamente y, por lo tanto, no se conoce si se ha enviado realmente el paquete IP. El controlador de red será responsable de liberar el paquete cuando se complete la transmisión. Este servicio difiere de otros, ya que no hay ninguna manera de saber si el paquete se envió realmente. Podría perderse en Internet.

*Tenga en cuenta que el procesamiento Raw IP debe estar habilitado.*

*Este servicio es similar a **nx_ip_raw_packet_send**, salvo en el hecho de que permite a una aplicación enviar paquetes de Raw IP desde una interfaz física especificada.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la tarea de IP creada anteriormente.
- **packet_ptr**: puntero al paquete que se va a transmitir.
- **destination_ip**: dirección IP para enviar el paquete.
- **address_index**: índice de la dirección de la interfaz en la que se va a enviar el paquete.
- **type_of_service**: tipo de servicio para el paquete.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se transmitió correctamente el paquete.
- **NX_IP_ADDRESS_ERROR**: (0X21) no hay ninguna interfaz de salida adecuada disponible.
- **NX_NOT_ENABLED**: (0x14) no se ha habilitado el procesamiento de paquetes Raw IP.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) la entrada del puntero no es válida.
- **NX_OPTION_ERROR**: (0x0A) el tipo de servicio especificado no es válido.
- **NX_OVERFLOW**: (0x03) el puntero de anteposición de paquetes no es válido.
- **NX_UNDERFLOW**: (0x02) el puntero de anteposición de paquetes no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) el índice de interfaz especificado no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

Recibe un paquete de Raw IP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio recibe un paquete de Raw IP de la instancia de IP especificada. Si hay paquetes IP en la cola de recepción de paquetes sin procesar, el primer paquete (más antiguo) se devuelve al autor de llamada. De lo contrario, si no hay paquetes disponibles, el autor de llamada puede suspenderse según lo especifique la opción de espera.

*Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido cuando ya no se necesite.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **packet_ptr**: puntero al puntero para colocar el paquete de Raw IP recibido.
- **wait_option**: define cómo se comporta el servicio si no hay ningún paquete de Raw IP disponible. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) los paquetes de Raw IP se recibieron correctamente.
- **NX_NO_PACKET**: (0X01) no hay ningún paquete disponible.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.
- **NX_PTR_ERROR**: (0X07) la IP o el puntero de paquete devuelto no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

Envía un paquete de Raw IP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a>Descripción

Este servicio envía un paquete de Raw IP a la dirección IP de destino. Tenga en cuenta que esta rutina se devuelve inmediatamente y, por lo tanto, no se conoce si se ha enviado realmente el paquete IP. El controlador de red será responsable de liberar el paquete cuando se complete la transmisión.

En el caso de un sistema de host múltiple, NetX usa la dirección IP de destino para encontrar una interfaz de red adecuada y la dirección IP de la interfaz como dirección de origen. Si la dirección IP de destino es de difusión o multidifusión, se usa la primera interfaz válida. En este caso, las aplicaciones usan el elemento ***nx_ip_raw_packet_interface_send***.

*A menos que se devuelva un error, la aplicación no debe liberar el paquete después de esta llamada. Si lo hace, se producirán resultados imprevisibles, ya que el controlador de red liberará el paquete después de la transmisión.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **packet_ptr**: puntero al paquete de Raw IP que se va a enviar.
- **destination_ip**: dirección IP de destino, que puede ser una dirección IP de host específica, una difusión de red, un bucle invertido interno o una dirección de multidifusión.
- **type_of_service**: define el tipo de servicio para la transmisión. Los valores válidos son los siguientes:
- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)


### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se inició el envío correcto de paquetes de Raw IP.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.
- **NX_NOT_ENABLED**: (0x14) la característica de Raw IP no está habilitada.
- **NX_OPTION_ERROR**: (0x0A) el tipo de servicio no es válido.
- **NX_UNDERFLOW**: (0X02) no dispone de espacio suficiente para anteponer un encabezado IP en el paquete.
- **NX_OVERFLOW**: (0x03) el puntero para anexar paquetes no es válido.
- **NX_PTR_ERROR**: (0X07) la IP o el puntero del paquete no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send,
- nx_ip_raw_packet_interface_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

Agrega una ruta predeterminada a la tabla de enrutamiento.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a>Descripción

Este servicio agrega una entrada a la tabla de enrutamiento estático. Tenga en cuenta que la dirección *next_hop* debe ser accesible directamente desde uno de los dispositivos de red local.

*Tenga en cuenta que el elemento ip_ptr debe apuntar a una estructura IP de NetX válida y la biblioteca NetX debe compilarse con NX_ENABLE_IP_STATIC_ROUTING definido para usar este servicio. De forma predeterminada, NetX se compila sin el elemento NX_ENABLE_IP_STATIC_ROUTING definido.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **network_address**: dirección de red de destino, en el orden de bytes del host.
- **net_mask**: máscara de red de destino, en el orden de bytes del host.
- **next_hop**: dirección del próximo salto para la red de destino, en el orden de bytes del host.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la entrada se agrega a la tabla de enrutamiento estática.
- **NX_OVERFLOW**: (0x03) la tabla de enrutamiento estática está llena.
- **NX_NOT_SUPPORTED**: (0X4B) esta característica no está compilada.
- **NX_IP_ADDRESS_ERROR**: (0x21) el próximo salto no es accesible directamente a través de interfaces locales.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR** (0x07) Puntero ip_ptr no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

Elimina una ruta estática de la tabla de enrutamiento.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a>Descripción

Este servicio elimina una entrada de la tabla de enrutamiento estática.

*Tenga en cuenta que el elemento ip_ptr debe apuntar a una estructura IP de NetX válida y la biblioteca NetX debe compilarse con NX_ENABLE_IP_STATIC_ROUTING definido para usar este servicio. De forma predeterminada, NetX se compila sin el elemento NX_ENABLE_IP_STATIC_ROUTING definido.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **network_address**: dirección de red de destino, en el orden de bytes del host.
- **net_mask**: máscara de red de destino, en el orden de bytes del host.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add

## <a name="nx_ip_status_check"></a>nx_ip_status_check

Comprobar el estado de una instancia de IP

### <a name="prototype"></a>Prototipo

```C
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
- **needed_status** Estado de IP solicitado, definido en el formato de mapa de bits de la siguiente manera:
- NX_IP_INITIALIZE_DONE (0x0001)
- NX_IP_ADDRESS_RESOLVED (0x0002)
- NX_IP_LINK_ENABLED (0x0004)
- NX_IP_ARP_ENABLED (0x0008)
- NX_IP_UDP_ENABLED (0x0010)
- NX_IP_TCP_ENABLED (0x0020)
- NX_IP_IGMP_ENABLED (0x0040)
- NX_IP_RARP_COMPLETE (0x0080)
- NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **actual_status** Puntero al destino del conjunto de bits real.
- **wait_option** Define cómo se comporta el servicio si los bits de estado solicitados no están disponibles. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) Comprobación de estado de IP correcta.
- **NX_NOT_SUCCESSFUL** (0X43) La solicitud de estado no se ha satisfecho dentro del tiempo de espera especificado.
- **NX_PTR_ERROR** (0x07) El puntero IP no es o ha dejado de ser válido o el puntero de estado real no es válido.
- **NX_OPTION_ERROR** (0x0a) Opción de estado necesario no válida.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize

## <a name="nx_packet_allocate"></a>nx_packet_allocate

Asigna un paquete del grupo especificado.

### <a name="prototype"></a>Prototipo

```C
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
- **packet_ptr**: puntero al puntero del puntero de paquete asignado.
- **packet_type**: define el tipo de paquete solicitado. Consulte "Grupos de paquetes" en la página 49 del capítulo 3 para obtener una lista de los tipos de paquetes admitidos.
- **wait_option**: define el tiempo de espera en tics si no hay paquetes disponibles en el grupo de paquetes. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) los paquetes se asignaron correctamente.
- **NX_NO_PACKET**: (0X01) no hay ningún paquete disponible.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_INVALID_PARAMETERS** (0x4D) El tamaño de paquete no admite el protocolo.
- **NX_OPTION_ERROR**: (0X0a) el tipo de paquete no es válido.
- **NX_PTR_ERROR**: (0x07) el grupo o el puntero de devolución de paquetes no son válidos.
- **NX_CALLER_ERROR**: (0x11) la opción de espera de un elemento distinto de un subproceso no es válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR (controladores de red de la aplicación). La opción de espera debe ser NX_NO_WAIT cuando se usa en ISR o en el contexto del temporizador.

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a>Consulte también

- nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy

Copia el paquete.

### <a name="prototype"></a>Prototipo

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio copia la información del paquete proporcionado en uno o varios paquetes nuevos que se asignan desde el grupo de paquetes proporcionado. Si se completa correctamente, se devuelve el puntero al nuevo paquete en el destino al que apunta el elemento **new_packet_ptr**.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete de origen.
- **new_packet_ptr**: puntero al destino en el que se va a devolver el puntero a la nueva copia del paquete.
- **pool_ptr**: puntero al grupo de paquetes creado anteriormente que se utiliza para asignar uno o varios paquetes para la copia.
- **wait_option**: define cómo espera el servicio si no hay ningún paquete disponible. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) los paquetes se copiaron correctamente.
- **NX_NO_PACKET**: (0x01) el paquete no está disponible para la copia.
- **NX_INVALID_PACKET**: (0X12) error en la copia o el paquete de origen está vacío.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_INVALID_PARAMETERS**: (0x4D) el tamaño de paquete no admite el protocolo.
- **NX_PTR_ERROR**: (0x07) el grupo, el paquete o el puntero de destino no son válidos.
- **NX_UNDERFLOW**: (0x02) el puntero de anteposición de paquetes no es válido.
- **NX_OVERFLOW**: (0x03) el puntero para anexar paquetes no es válido.
- **NX_CALLER_ERROR**: (0x11) se especificó una opción de espera en la inicialización o en una ISR.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a>Consulte también

- nx_packet_allocate, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append

Anexa datos al final del paquete.

### <a name="prototype"></a>Prototipo

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio anexa datos al final del paquete especificado. El área de datos proporcionada se copia en el paquete. Si no hay suficiente memoria disponible y la característica de paquetes encadenados está habilitada, se asignarán uno o varios paquetes para satisfacer la solicitud. Si la característica de paquetes encadenados no está habilitada, se devuelve *NX_SIZE_ERROR*.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero de paquete.
- **data_start**: puntero al inicio del área de datos del usuario que se va a anexar al paquete.
- **data_size**: tamaño del área de datos del usuario.
- **pool_ptr**: puntero al grupo de paquetes desde el que se va a asignar otro paquete si no hay suficiente espacio en el paquete actual.
- **wait_option**: define cómo se comporta el servicio si no hay ningún paquete disponible. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el paquete se anexó correctamente.
- **NX_NO_PACKET**: (0X01) no hay ningún paquete disponible.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a *tx_thread_wait_abort* ha anulado la suspensión solicitada.
- **NX_INVALID_PARAMETERS**: (0x4D) el tamaño de paquete no admite el protocolo.
- **NX_UNDERFLOW**: (0x02) el puntero antepuesto es menor que el inicio de carga.
- **NX_OVERFLOW**: (0x03) el puntero anexado es mayor que el final de la carga.
- **NX_PTR_ERROR**: (0x07): el grupo, el paquete o el puntero de datos no son válidos.
- **NX_SIZE_ERROR**: (0x09) el tamaño de datos no es válido.
- **NX_CALLER_ERROR**: (0x11) la opción de espera de un elemento distinto de un subproceso no es válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR (controladores de red de la aplicación)

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a>Consulte también

- nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset

Extrae datos del paquete mediante un desplazamiento.

### <a name="prototype"></a>Prototipo

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a>Descripción

Este servicio copia los datos de un paquete de NetX (o cadena de paquetes) a partir del desplazamiento especificado desde el puntero antepuesto del paquete del tamaño especificado en bytes en el búfer especificado. El número de bytes que se copian realmente se devuelve en *bytes_copied.* Este servicio no quita los datos del paquete ni ajusta el puntero antepuesto u otra información de estado interno.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete que se va a extraer.
- **offset**: desplazamiento desde el puntero antepuesto actual.
- **buffer_start**: puntero al principio del búfer de almacenamiento.
- **buffer_length**: número de bytes que se van a copiar.
- **bytes_copied**: número de bytes copiados realmente

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) los paquetes se copiaron correctamente.
- **NX_PACKET_OFFSET_ERROR**: (0x53) se proporcionó un valor de desplazamiento no válido.
- **NX_PTR_ERROR**: (0X07) el puntero de paquete o de búfer no son válidos.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a>Consulte también

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

Recupera datos de un paquete.

### <a name="prototype"></a>Prototipo

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a>Descripción

Este servicio copia los datos del paquete proporcionado en el búfer especificado. El número real de bytes copiados se devuelve en el destino al que apunta **bytes_copied**.

Tenga en cuenta que este servicio no cambia el estado interno del paquete. Los datos que se están recuperando siguen estando disponibles en el paquete.

*El búfer de destino debe ser lo suficientemente grande como para incluir el contenido del paquete. Si no es así, se dañará la memoria, lo que dará lugar a resultados imprevisibles.*

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete de origen.
- **buffer_start**: puntero al principio del área del búfer.
- **bytes_copied**: puntero al destino para el número de bytes copiados.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) los datos de los paquetes se recuperaron correctamente.
- **NX_INVALID_PACKET**: (0X12) el paquete no es válido.
- **NX_PTR_ERROR**: (0x07) el paquete, el inicio del búfer o el puntero de bytes copiados no son válidos.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a>Consulte también

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_length_get,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get

Obtiene la longitud de los datos de un paquete.

### <a name="prototype"></a>Prototipo

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a>Descripción

Este servicio obtiene la longitud de los datos en el paquete especificado.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete.
- **length**: destino de la longitud del paquete.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a>Consulte también

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create

Crea un grupo de paquetes en el área de memoria especificada.

### <a name="prototype"></a>Prototipo

```C
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
- **payload_size**: número de bytes en cada paquete del grupo. Este valor debe ser de al menos 40 bytes y también debe ser divisible por 4.
- **memory_ptr**: puntero al área de memoria en la que se va a colocar el grupo de paquetes. El puntero se debe alinear en un límite ULONG.
- **memory_size**: tamaño del área de memoria del grupo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el grupo de paquetes se creó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de memoria o el grupo no son válidos.
- **NX_SIZE_ERROR**: (0x09) el tamaño de memoria o el bloque no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a>Consulte también

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

Elimina un grupo de paquetes creado anteriormente.

### <a name="prototype"></a>Prototipo

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina un grupo de paquetes creado anteriormente. NetX comprueba si hay subprocesos suspendidos en los paquetes del grupo de paquetes y borra la suspensión.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero del bloque de control del grupo de paquetes.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el grupo de paquetes se eliminó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero del grupo no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a>Consulte también

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

Recupera información acerca de un grupo de paquetes

### <a name="prototype"></a>Prototipo

```C
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

*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un grupo de paquetes creado previamente.
- **total_packets**: puntero al destino para el número total de paquetes en el grupo.
- **free_packets**: puntero al destino para el número total de paquetes actualmente disponibles.
- **empty_pool_requests**: puntero al destino del número total de solicitudes de asignación cuando el grupo estaba vacío.
- **empty_pool_suspensions**: puntero al destino del número total de suspensiones del grupo vacío.
- **invalid_packet_releases**: puntero al destino del número total de versiones de paquetes no válidas.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS**: (0x00) la información del grupo de paquetes se recuperó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release

Libera el paquete previamente asignado.

### <a name="prototype"></a>Prototipo

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descripción

Este servicio libera un paquete, incluidos los paquetes adicionales encadenados al paquete especificado. Si otro subproceso está bloqueado en la asignación de paquetes, se le proporciona el paquete y se reanuda.

*La aplicación debe impedir que se libere un paquete más de una vez, ya que, si lo hace, se producirán resultados imprevisibles.*

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero de paquete.


### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) los paquetes se liberaron correctamente.
- **NX_PTR_ERROR**: (0X07) el puntero del paquete no es válido.
- **NX_UNDERFLOW**: (0x02) el puntero antepuesto es menor que el inicio de carga.
- **NX_OVERFLOW**: (0x03) el puntero anexado es mayor que el final de la carga.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR (controladores de red de la aplicación)

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a>Consulte también

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

Libera un paquete transmitido.

### <a name="prototype"></a>Prototipo

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descripción

En el caso de los paquetes que no son de TCP, este servicio libera un paquete transmitido, incluidos los paquetes adicionales encadenados al paquete especificado. Si otro subproceso está bloqueado en la asignación de paquetes, se le proporciona el paquete y se reanuda. En el caso de un paquete de TCP transmitido, este se marca como transmitido, pero no se libera hasta que se confirma. Normalmente, se llama a este servicio desde el controlador de red de la aplicación después de que se transmita un paquete.

*El controlador de red debe quitar el encabezado de medios físicos y ajustar la longitud del paquete antes de llamar a este servicio.*

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero de paquete.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Paquetes transmitidos liberados correctamente.
- **NX_PTR_ERROR**: (0X07) el puntero del paquete no es válido.
- **NX_UNDERFLOW**: (0x02) el puntero antepuesto es menor que el inicio de carga.
- **NX_OVERFLOW**: (0x03) el puntero anexado es mayor que el final de la carga.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores y controladores de red de la aplicación (incluidos ISR)

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a>Consulte también

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable

Deshabilita Reverse Address Resolution Protocol (RARP).

### <a name="prototype"></a>Prototipo

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita el componente RARP de NetX para la instancia de IP específica. En el caso de un sistema de host múltiple, este servicio deshabilita RARP en todas las interfaces.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) RARP se deshabilitó correctamente.
- **NX_NOT_ENABLED**: (0X14) RARP no se habilitó.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a>Consulte también

- nx_rarp_enable, nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable

Habilita Reverse Address Resolution Protocol (RARP).

### <a name="prototype"></a>Prototipo

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita el componente RARP de NetX para la instancia de IP específica. Los componentes RARP buscan una dirección IP cero en todas las interfaces de red asociadas. Una dirección IP cero indica que la interfaz todavía no tiene ninguna asignación de dirección IP. RARP intenta resolver la dirección IP mediante la habilitación del proceso RARP en esa interfaz.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) RARP se habilitó correctamente.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP ya es válida.
- **NX_ALREADY_ENABLED**: (0x15) RARP ya estaba habilitado.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a>Consulte también

- nx_rarp_disable, nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get

Recupera información acerca de las actividades de RARP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre las actividades de RARP de la instancia de IP especificada.

*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **rarp_requests_sent**: puntero al destino para el número total de solicitudes de RARP enviadas.
- **rarp_responses_received**: puntero al destino para el número total de respuestas de RARP recibidas.
- **rarp_invalid_messages**: puntero al destino del número total de mensajes no válidos.


### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) la información de RARP se recuperó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_rarp_disable, nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize

Inicializa el sistema NetX.

### <a name="prototype"></a>Prototipo

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a>Descripción

Este servicio inicializa los recursos básicos del sistema NetX como preparación para su uso. La aplicación debe llamarlo durante la inicialización y antes de que se realice cualquier otra llamada a NetX.

### <a name="parameters"></a>Parámetros

Ninguno

### <a name="return-values"></a>Valores devueltos

Ninguno

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a>Consulte también

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

Enlazar el socket TCP del cliente al puerto TCP

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio enlaza el socket de cliente TCP creado previamente al puerto TCP especificado. El intervalo de sockets TCP válidos es de 0 a 0xFFFF. Si el puerto TCP especificado no está disponible, el servicio se suspende según la opción de espera proporcionada.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.
- **port**: número de puerto que se va a enlazar (de 1 a 0xFFFF). Si el número de puerto es NX_ANY_PORT (0x0000), la instancia de IP buscará el siguiente puerto disponible y lo utilizará para el enlace.
- **wait_option**: define cómo se comporta el servicio si el puerto ya está enlazado a otro socket. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se enlazó correctamente.
- **NX_ALREADY_BOUND**: (0X22) este socket ya está enlazado a otro puerto TCP.
- **NX_PORT_UNAVAILABLE**: (0x23) el puerto ya está enlazado a otro socket.
- **NX_NO_FREE_PORTS**: (0X45) no hay ningún puerto disponible.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a *tx_thread_wait_abort* ha anulado la suspensión solicitada.
- **NX_INVALID_PORT**: (0x46) el puerto no es válido.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

Conecta el socket TCP del cliente.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio conecta el socket de cliente TCP creado y enlazado previamente al puerto del servidor especificado. Los puertos de servidor TCP válidos oscilan entre 0 y 0xFFFF. Si la conexión no se completa inmediatamente, el servicio se suspende según la opción de espera proporcionada.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.
- **server_IP**: dirección IP del servidor.
- **server_port**: número de puerto del servidor al que conectarse (de 1 a 0xFFFF).
- **wait_option**: define cómo se comporta el servicio mientras se establece la conexión. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se conectó correctamente.
- **NX_NOT_BOUND**: (0x24) el socket no está enlazado.
- **NX_NOT_CLOSED**: (0x35) el socket no está en un estado cerrado.
- **NX_IN_PROGRESS**: (0X37) no se especificó ninguna espera. El intento de conexión está en curso.
- **NX_INVALID_INTERFACE**: (0x4C) la interfaz proporcionada no es válida.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP del servidor no es válida.
- **NX_INVALID_PORT**: (0x46) el puerto no es válido.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

Obtiene el número de puerto enlazado al socket TCP del cliente.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el número de puerto asociado al socket, lo que resulta útil para buscar el puerto asignado por NetX en situaciones en las que se especificó el elemento NX_ANY_PORT cuando se enlazó el socket.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.
- **port_ptr**: puntero al destino del número de puerto de devolución. Los números de puerto válidos oscilan entre 1 y 0xFFFF.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se enlazó correctamente.
- **NX_NOT_BOUND** (0X24) este socket no está enlazado a ningún puerto.
- **NX_PTR_ERROR**: (0x07) el puntero de socket o de devolución de puerto no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

Desenlaza el socket de cliente TCP del puerto TCP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descripción

Este servicio libera el enlace entre el socket de cliente TCP y un puerto TCP. Si hay otros subprocesos en espera de enlazar otro socket al mismo número de puerto, el primer subproceso suspendido se enlaza a este puerto.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se desenlazó correctamente.
- **NX_NOT_BOUND**: (0x24) el socket no estaba enlazado a ningún puerto.
- **NX_NOT_CLOSED**: (0x35) el socket no se desconectó.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_enable"></a>nx_tcp_enable

Habilita el componente TCP de NetX.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita el componente de Protocolo de control de transmisión (TCP) de NetX. Una vez habilitado, la aplicación puede establecer conexiones TCP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) TCP se habilitó correctamente.
- **NX_ALREADY_ENABLED**: (0x15) TCP ya está habilitado.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

Busca el siguiente puerto TCP disponible.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a>Descripción

Este servicio intenta localizar un puerto TCP disponible (sin enlazar) a partir del puerto proporcionado por la aplicación. La lógica de búsqueda se ajustará si la búsqueda alcanza el valor de puerto máximo de 0xFFFF. Si la búsqueda se realiza correctamente, se devuelve el puerto disponible en la variable a la que apunta *free_port_ptr*.

*Se puede llamar a este servicio desde otro subproceso y hacer que se devuelva el mismo puerto. Para evitar esta condición de carrera, es posible que la aplicación quiera proteger este servicio y el enlace de socket de cliente real mediante una exclusión mutua.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **port**: número de puerto en el que debe iniciarse la búsqueda (de 1 a 0xFFFF).
- **free_port_ptr**: puntero al valor devuelto del puerto disponible de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se encontró un puerto disponible.
- **NX_NO_FREE_PORTS**: (0X45) no se encontró ningún puerto disponible.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.
- **NX_INVALID_PORT**: (0X46) el número de puerto especificado no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get

Recupera información acerca de las actividades de TCP.

### <a name="prototype"></a>Prototipo

```C
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

*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **tcp_packets_sent**: puntero al destino para el número total de paquetes TCP enviados.
- **tcp_bytes_sent**: puntero al destino para el número total de bytes TCP enviados.
- **tcp_packets_received**: puntero al destino del número total de paquetes TCP recibidos.
- **tcp_bytes_received**: puntero al destino del número total de bytes TCP recibidos.
- **tcp_invalid_packets**: puntero al destino del número total de paquetes TCP no válidos.
- **tcp_receive_packets_dropped**: puntero al destino del número total de paquetes TCP recibidos anulados.
- **tcp_checksum_errors**: puntero al destino del número total de paquetes TCP con errores de suma de comprobación.
- **tcp_connections**: puntero al destino del número total de conexiones TCP.
- **tcp_disconnections**: puntero al destino del número total de desconexiones TCP.
- **tcp_connections_dropped**: puntero al destino del número total de conexiones TCP anuladas.
- **tcp_retransmit_packets**: puntero al destino del número total de paquetes TCP retransmitidos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la información de TCP se recuperó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

Acepta la conexión TCP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio acepta (o se prepara para aceptar) una solicitud de conexión de socket de cliente TCP para un puerto que se configuró previamente para la escucha. Este servicio se puede llamar inmediatamente después de que la aplicación llame al servicio de escucha o de reescucha, o después de que se llame a la rutina de devolución de llamada de escucha cuando la conexión de cliente existe realmente. Si no se puede establecer una conexión de inmediato, el servicio se suspende según la opción de espera proporcionada.

*La aplicación debe llamar a **nx_tcp_server_socket_unaccept** cuando ya no se necesite la conexión para quitar el enlace del socket de servidor al puerto del servidor.*

*Se llama a las rutinas de devolución de llamada de la aplicación desde el subproceso auxiliar de IP.*

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al bloque de control del socket de servidor TCP.
- **wait_option**: define cómo se comporta el servicio mientras se establece la conexión. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)


### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) el socket de servidor TCP (conexión pasiva) se aceptó correctamente.
- **NX_NOT_LISTEN_STATE**: (0X36) el socket de servidor proporcionado no está en un estado de escucha.
- **NX_IN_PROGRESS**: (0X37) no se especificó ninguna espera. El intento de conexión está en curso.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a *tx_thread_wait_abort* ha anulado la suspensión solicitada.
- **NX_PTR_ERROR**: (0x07) error del puntero de socket.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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
        created */

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

Habilita la escucha para la conexión de cliente en el puerto TCP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a>Descripción

Este servicio habilita la escucha de una solicitud de conexión de cliente en el puerto TCP especificado. Cuando se recibe una solicitud de conexión de cliente, el socket del servidor proporcionado se enlaza al puerto especificado y se llama a la función de devolución de llamada de escucha proporcionada.

El procesamiento de la rutina de devolución de llamada de escucha depende completamente de la aplicación. Puede contener lógica para reactivar un subproceso de aplicación que posteriormente realiza una operación de aceptación. Si la aplicación ya tiene un subproceso suspendido en el procesamiento de aceptación para este socket, es posible que la rutina de devolución de llamada de escucha no sea necesaria.

Si la aplicación quiere controlar conexiones de cliente adicionales en el mismo puerto, se debe llamar a ***nx_tcp_server_socket_relisten*** con un socket disponible (un socket en estado CLOSED) para la conexión siguiente. Hasta que se llame al servicio de reescucha, las conexiones de cliente adicionales se ponen en cola. Cuando se supera la profundidad máxima de la cola, se anula la solicitud de conexión más antigua para poner en cola la nueva solicitud de conexión. Este servicio especifica la profundidad máxima de la cola.

*Se llama a las rutinas de devolución de llamada de la aplicación desde el subproceso auxiliar de IP.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **port**: número de puerto en el que se realiza la escucha (de 1 a 0xFFFF).
- **socket_ptr**: puntero al socket que se va a utilizar para la conexión.
- **listen_queue_size**: número de solicitudes de conexión de cliente que se pueden poner en cola.
- **listen_callback**: función de aplicación a la que se llamará cuando se reciba la conexión. Si se especifica un valor NULL, la característica de devolución de llamada de escucha se deshabilita.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la escucha del puerto TCP se habilitó correctamente.
- **NX_MAX_LISTEN**: (0X33) no hay más estructuras de solicitud de escucha disponibles. La constante NX_MAX_LISTEN_REQUESTS en nx_api.h define el número de solicitudes de escucha activas posibles.
- **NX_NOT_CLOSED**: (0X35) el socket de servidor proporcionado no está en estado cerrado.
- **NX_ALREADY_BOUND**: (0X22) el socket de servidor proporcionado ya está enlazado a un puerto.
- **NX_DUPLICATE_LISTEN**: (0x34) ya existe una solicitud de escucha activa para este puerto.
- **NX_INVALID_PORT**: (0x46) el puerto especificado no es válido.
- **NX_PTR_ERROR**: (0X07) la IP o el puntero de socket no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

Reescucha la conexión de cliente en el puerto TCP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descripción

Se llama a este servicio después de que se haya recibido una conexión en un puerto que se configuró anteriormente para la escucha. La finalidad principal de este servicio es proporcionar un nuevo socket de servidor para la siguiente conexión de cliente. Si una solicitud de conexión se pone en cola, la conexión se procesará inmediatamente durante esta llamada de servicio.

*También se llama a la misma rutina de devolución de llamada especificada por la solicitud de escucha original cuando existe una conexión para este nuevo socket de servidor.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **port**: número de puerto en el que se realiza la reescucha (de 1 a 0xFFFF).
- **socket_ptr**: socket que se va a usar para la siguiente conexión de cliente.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) la reescucha del puerto TCP se realizó correctamente.
- **NX_NOT_CLOSED**: (0X35) el socket de servidor proporcionado no está en estado cerrado.
- **NX_ALREADY_BOUND**: (0X22) el socket de servidor proporcionado ya está enlazado a un puerto.
- **NX_INVALID_RELISTEN**: (0x47) ya hay un puntero de socket válido para este puerto o el puerto especificado no tiene ninguna solicitud de escucha activa.
- **NX_CONNECTION_PENDING**: (0X48) igual que NX_SUCCESS, salvo que había una solicitud de conexión en cola y se procesó durante esta llamada.
- **NX_INVALID_PORT**: (0x46) el puerto especificado no es válido.
- **NX_PTR_ERROR** (0x07) Dirección IP o puntero de devolución de llamada de escucha no válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

Quita la asociación de un socket con el puerto de escucha.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descripción

Este servicio quita la asociación entre este socket de servidor y el puerto del servidor especificado. La aplicación debe llamar a este servicio después de una desconexión o después de una llamada de aceptación incorrecta.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de servidor de configuración anterior.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la operación de no aceptación del socket de servidor se completó correctamente.
- **NX_NOT_LISTEN_STATE**: (0x36) el socket del servidor está en un estado inadecuado y probablemente no esté desconectado.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
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
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

Deshabilita la escucha para la conexión de cliente en el puerto TCP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a>Descripción

Este servicio deshabilita la escucha de una solicitud de conexión de cliente en el puerto TCP especificado.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **port**: número de puerto para deshabilitar la escucha (de 0 a 0xFFFF).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la escucha de puerto TCP se deshabilitó correctamente.
- **NX_ENTRY_NOT_FOUND**: (0x16) no se ha habilitó la escucha para el puerto especificado.
- **NX_INVALID_PORT**: (0x46) el puerto especificado no es válido.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

Recupera el número de bytes disponibles para la recuperación

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Descripción

Este servicio obtiene el número de bytes disponibles para la recuperación en el socket TCP especificado. Tenga en cuenta que el socket TCP ya debe estar conectado.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket TCP creado y conectado anteriormente.
- **bytes_available**: puntero al destino para los bytes disponibles.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el servicio se ejecuta correctamente. El número de bytes disponibles para la lectura se devuelve al autor de la llamada.
- **NX_NOT_CONNECTED**: (0x38) el socket no está en estado conectado.
- **NX_PTR_ERROR**: (0x07) los punteros no son válidos.
- **NX_NOT_ENABLED**: (0x14) el TCP no está habilitado.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

Crea un cliente TCP o un socket de servidor

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descripción

Este servicio crea un cliente TCP o un socket de servidor para la instancia de IP especificada.

*Se llama a las rutinas de devolución de llamada de aplicación desde el subproceso asociado con esta instancia de IP.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **socket_ptr**: puntero al nuevo bloque de control de socket TCP.
- **name**: nombre de la aplicación para este socket TCP.
- **type_of_service**: define el tipo de servicio para la transmisión. Los valores válidos son los siguientes:

- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)

- **fragment**: especifica si se permite o no la fragmentación de IP. Si se especifica NX_FRAGMENT_OKAY (0X0), se permite la fragmentación de IP. Si se especifica NX_DONT_FRAGMENT (0x4000), se deshabilita la fragmentación de IP.
- **time_to_live**: especifica el valor de 8 bits que define el número de enrutadores que puede autorizar este paquete antes de que desaparezca. El elemento NX_IP_TIME_TO_LIVE especifica el valor predeterminado.
- **window_size**: define el número máximo de bytes permitidos en la cola de recepción de este socket.
- **urgent_data_callback**: función de aplicación a la que se llama cada vez que se detectan datos urgentes en el flujo de recepción. Si este valor es NX_NULL, se omiten los datos urgentes.
- **disconnect_callback**: función de aplicación a la que se llama siempre que el socket emite una desconexión en el otro extremo de la conexión. Si este valor es NX_NULL, la función de devolución de llamada de desconexión se deshabilita.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) el socket de cliente TCP se creó correctamente.
- **NX_OPTION_ERROR**: (0x0A) el tipo de servicio, el fragmento, el tamaño de la ventana o la opción de período de vida no son válidos.
- **NX_PTR_ERROR**: (0X07) la IP o el puntero de socket no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

Elimina un socket TCP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina un socket TCP creado anteriormente. Si el socket sigue enlazado o conectado, el servicio devuelve un código de error.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: socket TCP creado previamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se eliminó correctamente.
- **NX_NOT_CREATED**: (0x27) no se creó el socket.
- **NX_STILL_BOUND**: (0x42) el socket sigue estando enlazado.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

Desconecta conexiones de socket de cliente y servidor.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio desconecta una conexión de socket de servidor o cliente establecida. Una desconexión de un socket de servidor debe ir seguida de una solicitud de desaceptación, mientras que un socket de cliente que está desconectado se deja en un estado listo para otra solicitud de conexión. Si el proceso de desconexión no puede finalizar inmediatamente, el servicio se suspende según la opción de espera proporcionada.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.
- **wait_option**: define cómo se comporta el servicio mientras la desconexión está en curso. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se desconectó correctamente.
- **NX_NOT_CONNECTED**: (0x38) el socket especificado no está conectado.
- **NX_IN_PROGRESS**: (0x37) la desconexión está en curso; no se especificó ninguna espera.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify

Instala la función de devolución de llamada de notificación de realización de la desconexión de TCP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada que se invoca después de que se complete una operación de desconexión de socket. La función de devolución de llamada de realización de la desconexión de socket TCP está disponible si NetX se crea con la opción siguiente definida:

- ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT***

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.
- **tcp_disconnect_complete_notify**: función de devolución de llamada que se va a instalar.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) la función de devolución de llamada se ha registrado correctamente.
- **NX_NOT_SUPPORTED**: (0X4B) la característica de notificación extendida no está integrada en la biblioteca de NetX
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) la característica de TCP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,
- nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify

Define la función de devolución de llamada de notificación de establecimiento de TCP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada a la que se llama después de que un socket TCP establezca una conexión. La función de devolución de llamada de establecimiento de socket TCP está disponible si NetX se crea con la opción ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definida.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.
- **tcp_establish_notify**: función de devolución de llamada invocada después de establecer una conexión TCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la función de notificación se definió correctamente.
- **NX_NOT_SUPPORTED**: (0X4B) la característica de notificación extendida no está integrada en la biblioteca de NetX
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) la aplicación no ha habilitado TCP.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

Recupera información acerca de las actividades de socket TCP.

### <a name="prototype"></a>Prototipo

```C
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

*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.
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

- **NX_SUCCESS**: (0x00) la información del socket TCP se recuperó correctamente.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="return-values"></a>Valores devueltos

```C
/* Retrieve TCP socket information from previously created socket_0.*/
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

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Retrieve TCP socket information from previously created socket_0.*/
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

Obtiene MSS del socket.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Descripción

Este servicio recupera el tamaño de segmento máximo local (MSS) del socket especificado.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket creado anteriormente.
- **mss**: destino para el valor de MSS devuelto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el valor de MSS se obtuvo correctamente.
- **NX_PTR_ERROR**: (0x07) el socket o el puntero de destino de MSS no son válidos.
- **NX_NOT_ENABLED**: (0x14) el TCP no está habilitado.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso ni una inicialización.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

Obtiene el valor de MSS del socket TCP del mismo nivel.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Descripción

Este servicio recupera el tamaño máximo de segmento (MSS) anunciado por el socket del mismo nivel.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket creado y conectado anteriormente.
- **mss**: destino para devolver el valor de MSS.


### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el valor de MSS del mismo nivel se obtuvo correctamente.
- **NX_PTR_ERROR**: (0x07) el socket o el puntero de destino de MSS no son válidos.
- **NX_NOT_ENABLED**: (0x14) el TCP no está habilitado.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso ni una inicialización.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

Define el valor de MSS del socket.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a>Descripción

Este servicio establece el tamaño máximo de segmento (MSS) del socket especificado. Tenga en cuenta que el valor de MSS debe estar dentro de la MTU de IP de la interfaz de red De este modo, hay espacio para los encabezados IP y TCP.

Este servicio debe usarse antes de que un socket TCP inicie el proceso de conexión. Si se usa el servicio después de establecer una conexión TCP, el nuevo valor no tiene ningún efecto en la conexión.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket creado anteriormente.
- **mss**: valor de MSS que se va a establecer.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el valor de MSS se estableció correctamente.
- **NX_SIZE_ERROR**: (0x09) el valor de MSS especificado es demasiado grande.
- **NX_NOT_CONNECTED**: (0x38) no se estableció la conexión TCP
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_NOT_ENABLED**: (0x14) el TCP no está habilitado.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso ni una inicialización.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

Recupera información sobre el socket TCP del mismo nivel.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a>Descripción

Este servicio recupera información del puerto y la dirección IP del mismo nivel para el socket TCP conectado a través de la red IP.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.
- **peer_ip_address**: puntero al destino de la dirección IP del mismo nivel, en el orden de bytes del host.
- **peer_port**: puntero al destino del número de puerto del mismo nivel, en el orden de bytes del host.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el servicio se ejecuta correctamente. El número de puerto y de dirección IP del mismo nivel se devuelven al autor de la llamada.
- **NX_NOT_CONNECTED**: (0x38) el socket no está en estado conectado.
- **NX_PTR_ERROR**: (0x07) los punteros no son válidos.
- **NX_NOT_ENABLED**: (0x14) el TCP no está habilitado.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

Recupera datos de un socket TCP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio recibe datos TCP del socket especificado. Si no hay datos en cola en el socket especificado, el autor de llamada se suspende en función de la opción de espera proporcionada.

*Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite.*

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.
- **packet_ptr**: puntero al puntero de paquete TCP.
- **wait_option**: define cómo se comporta el servicio si no hay ningún dato en la cola de este socket actualmente. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) los datos del socket se recibieron correctamente.
- **NX_NOT_BOUND**: (0x24) el socket todavía no está enlazado.
- **NX_NO_PACKET**: (0X01) no se recibió ningún dato.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_NOT_CONNECTED**: (0X38) el socket ya no está conectado.
- **NX_PTR_ERROR**: (0X07) el socker o el puntero de paquete devuelto no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

/* Recibe un paquete del socket de cliente TCP creado y conectado anteriormente. Si no hay ningún paquete disponible, espera hasta 200 tics del temporizador antes de abandonarlo. */ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* Si el estado es NX_SUCCESS, el paquete recibido apunta a "packet_ptr". */

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

Notifica a la aplicación los paquetes recibidos.


### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descripción

Este servicio configura el puntero de la función de notificación de recepción con la función de devolución de llamada especificada por la aplicación. A continuación, se llama a esta función de devolución de llamada siempre que se reciban uno o varios paquetes en el socket. Si se proporciona un puntero NX_NULL, la función de notificación se deshabilita.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket TCP.
- **tcp_receive_notify**: puntero de función de devolución de llamada de la aplicación al que se llama cuando se reciben uno o varios paquetes en el socket.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la recepción del socket se notificó correctamente.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) la característica de TCP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

Envía datos a través de un socket TCP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía datos TCP a través de un socket TCP previamente conectado. Si el último tamaño de la ventana anunciado del receptor es menor que esta solicitud, el servicio se suspende opcionalmente en función de la opción de espera especificada. Este servicio garantiza que no se envíen datos de paquetes mayores que el valor de MSS a la capa de IP.

*A menos que se devuelva un error, la aplicación no debe liberar el paquete después de esta llamada. Si lo hace, se producirán resultados imprevisibles, ya que el controlador de red también intentará liberar el paquete después de la transmisión.*

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de TCP conectada anteriormente.
- **packet_ptr**: puntero del paquete de datos de TCP.
- **wait_option**: define cómo se comporta el servicio si la solicitud es mayor que el tamaño de la ventana del receptor. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se envió correctamente.
- **NX_NOT_BOUND**: (0x24) el socket no estaba enlazado a ningún puerto.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) no se encontró ninguna interfaz de salida adecuada.
- **NX_NOT_CONNECTED**: (0X38) el socket ya no está conectado.
- **NX_WINDOW_OVERFLOW**: (0x39) la solicitud es mayor que el tamaño de la ventana anunciado del receptor en bytes.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_INVALID_PACKET**: (0X12) no se asignó el paquete.
- **NX_TX_QUEUE_DEPTH**: (0x49) se alcanzó la profundidad máxima de la cola de transmisión.
- **NX_OVERFLOW**: (0x03) el puntero para anexar paquetes no es válido.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.
- **NX_UNDERFLOW**: (0x02) el puntero de anteposición de paquetes no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait

### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

Espera a que el socket TCP entre en un estado específico.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a>Descripción

Este servicio espera a que el socket entre en el estado deseado. Si el socket no se encuentra en el estado deseado, el servicio se suspende según la opción de espera proporcionada.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de TCP conectada anteriormente.
- **desired_state**: estado de TCP deseado. Los estados de socket de TCP válidos se definen de la siguiente manera:
- NX_TCP_CLOSED (0x01)
- NX_TCP_LISTEN_STATE (0x02)
- NX_TCP_SYN_SENT (0x03)
- NX_TCP_SYN_RECEIVED (0x04)
- NX_TCP_ESTABLISHED (0x05)
- NX_TCP_CLOSE_WAIT (0x06)
- NX_TCP_FIN_WAIT_1 (0x07)
- NX_TCP_FIN_WAIT_2 (0x08)
- NX_TCP_CLOSING (0x09)
- NX_TCP_TIMED_WAIT (0x0A)
- NX_TCP_LAST_ACK (0x0B)
- **wait_option**: define cómo se comporta el servicio si el estado solicitado no existe. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) la espera del estado se completó correctamente.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_NOT_SUCCESSFUL**: (0X43) el estado no existe en el tiempo de espera especificado.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.
- **NX_OPTION_ERROR**: (0X0a) el estado del socket deseado no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback

Instala la devolución de llamada para el estado de tiempo de espera.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada que se invoca cuando el socket TCP está en estado de tiempo de espera. Para usar este servicio, la biblioteca NetX debe compilarse con la opción ***NX_ENABLE_EXTENDED_NOTIFY*** definida.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.
- **tcp_timed_wait_callback**: función de devolución de llamada de espera programada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket de la función de devolución de llamada se registró correctamente.
- **NX_NOT_SUPPORTED**: (0X4B) la biblioteca de NetX se genera sin la característica de notificación extendida habilitada.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) la característica de TCP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

Configura parámetros de transmisión del socket.

### <a name="prototype"></a>Prototipo

```C
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
- **timeout**: número de tics de temporizador de ThreadX; se espera una confirmación antes de que se vuelva a enviar el paquete.
- **max_retries**: número máximo de reintentos permitidos.
- **timeout_shift**: valor para desplazar el tiempo de espera de cada reintento subsiguiente. Un valor de 0, da como resultado el mismo tiempo de espera entre reintentos sucesivos. Un valor de 1, duplica el tiempo de espera entre reintentos.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) el socket de transmisión se configuró correctamente.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_OPTION_ERROR**: (0x0a) la opción de profundidad de la cola no es válida.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) la característica de TCP no está habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set

Notifica a la aplicación la actualizaciones del tamaño de la ventana.

### <a name="prototype"></a>Prototipo

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descripción

Este servicio instala una rutina de devolución de llamada de actualizaciones de la ventana del socket. Se llama a esta rutina automáticamente cada vez que el socket especificado recibe un paquete que indica un aumento en el tamaño de la ventana del host remoto.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.
- **tcp_window_update_notify**: rutina de devolución de llamada a la que se llamará cuando cambie el tamaño de la ventana. Un valor NULL deshabilita la actualización de cambios de la ventana.

### <a name="return-values"></a>Valores devueltos
- **NX_SUCCESS**: (0x00) la rutina de devolución de llamada se instala en el socket.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_PTR_ERROR**: (0x07) los punteros no son válidos.
- **NX_NOT_ENABLED**: (0x14) la característica de TCP no está habilitada.


### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a>Consulte también

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable

Habilita el componente UDP de NetX.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita el componente de Protocolo de datagramas de usuario (UDP) de NetX. Una vez habilitado, la aplicación puede enviar y recibir datagramas UDP.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) UDP se habilitó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_ALREADY_ENABLED**: (0X15) este componente ya se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

Busca el siguiente puerto UDP disponible.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a>Descripción

Este servicio busca un puerto UDP disponible (sin enlazar) a partir del número de puerto proporcionado por la aplicación. La lógica de búsqueda se ajustará si la búsqueda alcanza el valor de puerto máximo de 0xFFFF. Si la búsqueda se realiza correctamente, se devuelve el puerto disponible en la variable a la que apunta *free_port_ptr*.

*Se puede llamar a este servicio desde otro subproceso y hacer que se devuelva el mismo puerto. Para evitar esta condición de carrera, es posible que la aplicación quiera proteger este servicio y el enlace de socket real mediante una exclusión mutua.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **port**: número de puerto para iniciar la búsqueda (de 1 a 0xFFFF).
- **free_port_ptr**: puntero a la variable devuelta del puerto disponible de destino.


### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se encontró un puerto disponible.
- **NX_NO_FREE_PORTS**: (0X45) no se encontró ningún puerto disponible.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.
- **NX_INVALID_PORT**: (0X46) el número de puerto especificado no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get

Recupera información acerca de las actividades UDP.

### <a name="prototype"></a>Prototipo

```C
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

Este servicio recupera información sobre las actividades UDP de la instancia de IP especificada.

*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **udp_packets_sent**: puntero al destino para el número total de paquetes UDP enviados.
- **udp_bytes_sent**: puntero al destino para el número total de bytes UDP enviados.
- **udp_packets_received**: puntero al destino del número total de paquetes UDP recibidos.
- **udp_bytes_received**: puntero al destino del número total de bytes UDP recibidos.
- **udp_invalid_packets**: puntero al destino del número total de paquetes UDP no válidos.
- **udp_receive_packets_dropped**: puntero al destino del número total de paquetes UDP recibidos anulados.
- **udp_checksum_errors**: puntero al destino del número total de paquetes UDP con errores de suma de comprobación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la información de UDP se recuperó correctamente.
- **NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.


### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract

Extrae parámetros de la red de un paquete UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a>Descripción

Este servicio extrae los parámetros de red, como la dirección IP, el número de puerto del mismo nivel y el tipo de protocolo (este servicio siempre devuelve el tipo UDP) de un paquete recibido en una interfaz entrante.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero al paquete.
- **ip_address**: puntero a la dirección IP del emisor.
- **protocolo**: puntero al protocolo (UDP).
- **port**: puntero al número de puerto del emisor.
- **interface_index**: puntero al índice de la interfaz de recepción.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) los datos de la interfaz del paquetes se extrajeron correctamente.
- **NX_INVALID_PACKET**: (0X12) el paquete no contiene el marco de IP.
- **NX_PTR_ERROR**: (0x07) la entrada del puntero no es válida.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

Enlaza el socket UDP al puerto UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio enlaza el socket UDP creado previamente al puerto UDP especificado. El intervalo de sockets UDP válidos es de 0 a 0xFFFF. Si el número de puerto solicitado está enlazado a otro socket, este servicio espera durante el período de tiempo especificado para que el socket se desenlace del número de puerto.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.
- **port**: número de puerto al que se va a enlazar (de 1 a 0xFFFF). Si el número de puerto es NX_ANY_PORT (0x0000), la instancia de IP buscará el siguiente puerto disponible y lo utilizará para el enlace.
- **wait_option**: define cómo se comporta el servicio si el puerto ya está enlazado a otro socket. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se enlazó correctamente.
- **NX_ALREADY_BOUND**: (0X22) este socket ya está enlazado a otro puerto.
- **NX_PORT_UNAVAILABLE**: (0x23) el puerto ya está enlazado a otro socket.
- **NX_NO_FREE_PORTS**: (0X45) no hay ningún puerto disponible.
- **NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.
- **NX_INVALID_PORT**: (0x46) el puerto especificado no es válido.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

Recupera el número de bytes disponibles para la recuperación

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Descripción

Este servicio recupera el número de bytes disponibles para la recepción en el socket UDP especificado.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.
- **bytes_available**: puntero al destino para los bytes disponibles.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) los bytes disponibles se recuperaron correctamente.
- **NX_NOT_SUCCESSFUL**: (0X43) el socket no se enlazó a ningún puerto.
- **NX_PTR_ERROR**: (0x07) los punteros no son válidos.
- **NX_NOT_ENABLED**: (0x14) la característica de UDP no está habilitada.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

Deshabilita la suma de comprobación para el socket UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita la lógica de suma de comprobación para enviar y recibir paquetes en el socket UDP especificado. Cuando se deshabilita la lógica de suma de comprobación, se carga un valor de cero en el campo de suma de comprobación del encabezado UDP para todos los paquetes enviados a través de este socket. Un valor de suma de comprobación de cero en el encabezado UDP indica al receptor que la suma de comprobación no se procesa para este paquete.

Tenga en cuenta también que esto no tiene ningún efecto si se definen los elementos ***NX_DISABLE_UDP_RX_CHECKSUM** _ y _ *_NX_DISABLE_UDP_TX_CHECKSUM_** al recibir y enviar paquetes UDP, respectivamente.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la suma de comprobación de socket se deshabilitó correctamente.
- **NX_NOT_BOUND**: (0x24) el socket no está enlazado.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizador

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

Habilita la suma de comprobación para el socket UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita la lógica de suma de comprobación para enviar y recibir paquetes en el socket UDP especificado. La suma de comprobación abarca todo el área de datos UDP y un seudoencabezado de IP.

Tenga en cuenta también que esto no tiene ningún efecto si **NX_DISABLE_UDP_RX_CHECKSUM** y **NX_DISABLE_UDP_TX_CHECKSUM** se definen al recibir y enviar paquetes UDP, respectivamente.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la suma de comprobación de socket se habilitó correctamente.
- **NX_NOT_BOUND**: (0x24) el socket no está enlazado.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizador

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create

Crea un socket UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a>Descripción

Este servicio crea un socket UDP para la instancia de IP especificada.

### <a name="parameters"></a>Parámetros

- **ip_ptr**: puntero a la instancia de IP creada anteriormente.
- **socket_ptr**: puntero al nuevo bloque de control de socket UDP.
- **name**: nombre de la aplicación para este socket UDP.
- **type_of_service**: define el tipo de servicio para la transmisión. Los valores válidos son los siguientes:
    - NX_IP_NORMAL (0x00000000)
    - NX_IP_MIN_DELAY (0x00100000)
    - NX_IP_MAX_DATA (0x00080000)
    - NX_IP_MAX_RELIABLE (0x00040000)
    - NX_IP_MIN_COST (0x00020000)
- **fragment**: especifica si se permite o no la fragmentación de IP. Si se especifica NX_FRAGMENT_OKAY (0X0), se permite la fragmentación de IP. Si se especifica NX_DONT_FRAGMENT (0x4000), se deshabilita la fragmentación de IP.
- **time_to_live**: especifica el valor de 8 bits que define el número de enrutadores que puede autorizar este paquete antes de que desaparezca. El elemento NX_IP_TIME_TO_LIVE especifica el valor predeterminado.
- **queue_maximum**: define el número máximo de datagramas UDP que se pueden poner en cola para este socket. Una vez alcanzado el límite de la cola, se libera el paquete UDP más antiguo para cada paquete nuevo recibido.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket UDP se creó correctamente.
- **NX_OPTION_ERROR**: (0x0a) el tipo de servicio, el fragmento o la opción de período de vida no son válidos.
- **NX_PTR_ERROR**: (0X07) la IP o el puntero de socket no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_delete,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete

Elimina el socket UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina un socket UDP creado anteriormente. Si el socket se ha enlazado a un puerto, primero se debe desenlazar.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se eliminó correctamente.
- **NX_STILL_BOUND**: (0x42) el socket sigue estando enlazado.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get

Recupera información acerca de las actividades del socket UDP.

### <a name="prototype"></a>Prototipo

```C
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

Este servicio recupera información sobre las actividades del socket UDP de la instancia de socket UDP especificada.

*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.
- **udp_packets_sent**: puntero al destino para el número total de paquetes UDP enviados en el socket.
- **udp_bytes_sent**: puntero al destino para el número total de bytes UDP enviados en el socket.
- **udp_packets_received**: puntero al destino del número total de paquetes UDP recibidos en el socket.
- **udp_bytes_received**: puntero al destino del número total de bytes UDP recibidos en el socket.
- **udp_packets_queued**: puntero al destino del número total de paquetes UDP en cola en el socket.
- **udp_receive_packets_dropped**: puntero al destino del número total de paquetes de recepción UDP anulados para el socket debido a que se superó el tamaño de la cola.
- **udp_checksum_errors**: puntero al destino del número total de paquetes UDP con errores de suma de comprobación en el socket.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la información del socket UDP se recuperó correctamente.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

Recoge el número de puerto enlazado al socket UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el número de puerto asociado al socket, lo que resulta útil para buscar el puerto asignado por NetX en situaciones en las que se especificó el elemento NX_ANY_PORT cuando se enlazó el socket.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.
- **port_ptr**: puntero al destino del número de puerto de devolución. Los números de puerto válidos son (1- 0XFFFF).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se enlazó correctamente.
- **NX_NOT_BOUND** (0X24) este socket no está enlazado a ningún puerto.
- **NX_PTR_ERROR**: (0x07) el puntero de socket o de devolución de puerto no son válidos.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

Recibe el datagrama del socket UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio recibe un datagrama UDP del socket especificado. Si no hay ningún datagrama en cola en el socket especificado, el autor de llamada se suspende en función de la opción de espera proporcionada.

*Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite.*

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.
- **packet_ptr**: puntero al puntero de paquete de datagrama UDP.
- **wait_option**: define cómo se comporta el servicio si no hay ningún datagrama en la cola de este socket actualmente. Las opciones de espera se definen de la siguiente forma:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

Notifica a la aplicación cada paquete recibido.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a>Descripción

Este servicio define el puntero de función de notificación de recepción a la función de devolución de llamada especificada por la aplicación. A continuación, se llama a esta función de devolución de llamada siempre que se recibe un paquete en el socket. Si se proporciona un puntero NX_NULL, la función de notificación de recepción se deshabilita.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero al socket UDP.
- **udp_receive_notify**: puntero de función de devolución de llamada de aplicación al que se llama cuando se recibe un paquete en el socket.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send

Envía un datagrama UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a>Descripción

Este servicio envía un datagrama UDP a través de un socket UDP previamente creado y enlazado. NetX encuentra una dirección IP local adecuada como dirección de origen según la dirección IP de destino. Para especificar una interfaz específica y una dirección IP de origen, la aplicación debe usar el servicio **nx_udp_socket_interface_send**.

Tenga en cuenta que este servicio se devuelve de manera inmediata, independientemente de si el datagrama UDP se envió correctamente.

El socket debe estar enlazado a un puerto local.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.
- **packet_ptr**: puntero de paquete de datagrama UDP.
- **ip_address**: dirección IP de destino.
- **port**: número de puerto de destino válido entre 1 y 0xFFFF, en el orden de bytes del host.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket UDP se envió correctamente.
- **NX_NOT_BOUND**: (0x24) el socket no se enlazó a ningún puerto.
- **NX_NO_INTERFACE_ADDRESS**: (0x50) no se pudo encontrar ninguna interfaz de salida adecuada.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP del servidor no es válida.
- **NX_UNDERFLOW**: (0X02) no hay suficiente espacio para el encabezado UDP en el paquete.
- **NX_OVERFLOW**: (0x03) el puntero para anexar paquetes no es válido.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0x14) no se habilitó UDP.
- **NX_INVALID_PORT**: (0x46) el número de puerto no está dentro de un intervalo válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_interface_send"></a>nx_udp_socket_interface_send

Envía un datagrama a través de un socket UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a>Descripción

Este servicio envía un datagrama UDP a través de un socket UDP creado y enlazado previamente a través de la interfaz de red con la dirección IP especificada como dirección de origen. Tenga en cuenta que el servicio se devuelve de manera inmediata, independientemente de si el datagrama UDP se envió correctamente o no.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: socket en el que se va a transmitir el paquete.
- **packet_ptr**: puntero al paquete que se va a transmitir.
- **ip_address**: dirección IP de destino a la que se enviará el paquete.
- **port**: puerto de destino.
- **address_index**: índice de la dirección asociada con la interfaz en la que se va a enviar el paquete.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se envió correctamente el paquete.
- **NX_NOT_BOUND**: (0x24) el socket no se enlazó a ningún puerto.
- **NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.
- **NX_NOT_ENABLED**: (0x14) el procesamiento de UDP no está habilitado.
- **NX_PTR_ERROR**: (0x07) el puntero no es válido.
- **NX_OVERFLOW**: (0x03) el puntero para anexar paquetes no es válido.
- **NX_UNDERFLOW**: (0x02) el puntero de anteposición de paquetes no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_INVALID_INTERFACE**: (0x4C) el índice de dirección no es válido.
- **NX_INVALID_PORT**: (0x46) el número de puerto supera el número de puerto máximo.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_unbind

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

Desenlaza el socket UDP de un puerto UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Descripción

Este servicio libera el enlace entre el socket UDP y un puerto UDP. Los paquetes recibidos almacenados en la cola de recepción se liberan como parte de la operación de desenlace.

Si hay otros subprocesos en espera de enlazar otro socket al puerto desenlazado, el primer subproceso suspendido se enlaza al nuevo puerto desenlazado.

### <a name="parameters"></a>Parámetros

- **socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el socket se desenlazó correctamente.
- **NX_NOT_BOUND**: (0x24) el socket no estaba enlazado a ningún puerto.
- **NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.
- **NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.
- **NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract

Extrae la IP y el puerto de envío del datagrama UDP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a>Descripción

Este servicio extrae el número de puerto y la dirección IP del emisor de los encabezados IP y UDP del datagrama UDP proporcionado.

### <a name="parameters"></a>Parámetros

- **packet_ptr**: puntero de paquete de datagrama UDP.
- **ip_address**: puntero válido a la variable de dirección IP devuelta.
- **port**: puntero válido a la variable de puerto devuelto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el puerto o la IP de origen se extrajeron correctamente.
- **NX_INVALID_PACKET**: (0X12) el paquete proporcionado no es válido.
- **NX_PTR_ERROR**: (0x07) el paquete, la IP o el puerto de destino no son válidos.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a>Consulte también

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind