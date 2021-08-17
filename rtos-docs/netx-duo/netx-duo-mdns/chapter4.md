---
title: 'Capítulo 4: Descripción de los servicios mDNS'
description: Este capítulo contiene una descripción de todos los servicios mDNS de NetX.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6e37698ac6023b4cff6cb4fc05330a73b678ef3d2a813a706c9b821381e123db
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797575"
---
# <a name="chapter-4---description-of-mdns-services"></a>Capítulo 4: Descripción de los servicios mDNS

Este capítulo contiene una descripción de todos los servicios mDNS de NetX (se enumeran a continuación).

> [!NOTE]
> En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

## <a name="nx_mdns_create"></a>nx_mdns_create

Crear una instancia de mDNS

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de mDNS en la instancia de IP específica y los recursos asociados. También se crea un subproceso para controlar los mensajes de mDNS entrantes, para responder a las consultas y para transmitir periódicamente mensajes de consulta.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **ip_ptr** Puntero a la instancia de IP asociada.
- **packet_pool** Puntero a un grupo de paquetes válido.
- **priority** Prioridad del subproceso de mDNS.
- **stack_ptr** Puntero al área de pila del subproceso de mDNS.
- **stack_size** Tamaño del área de pila.
- **host_name** Nombre de host asignado a este nodo.
- **local_service_cache** Espacio de almacenamiento para servicios registrados locales.
- **local_service_cache_size** Tamaño de la caché de servicios local.
- **peer_service_cache** Espacio de almacenamiento para la información de servicio recibida.
- **peer_service_cache_size** Tamaño de la caché de servicio del mismo nivel.
- **probing_notify** Función de devolución de llamada opcional invocada al final de la operación de sondeo. Notifica a la aplicación si el nombre de host (cuando se habilita mDNS en una interfaz local) o el nombre del servicio (después de registrar un servicio) es único.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se creó correctamente la instancia de mDNS.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a>nx_mdns_delete

Eliminar una instancia de mDNS

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina la instancia de mDNS y libera sus recursos.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se eliminó correctamente la instancia de mDNS.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a>nx_mdns_enable

Iniciar el servicio mDNS

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Descripción

Esta API habilita el servicio mDNS en una interfaz física específica. Una vez habilitado el servicio, el módulo mDNS sondea primero todos sus nombres de servicio únicos en la red antes de responder a las consultas recibidas en la interfaz.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de instancia de mDNS.
- **interface_index** Índice de la interfaz en la que se va a habilitar el servicio.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se habilitó correctamente el servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a>nx_mdns_disable

Deshabilitar el servicio mDNS

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Descripción

Esta API deshabilita el servicio mDNS en la interfaz física específica. Una vez deshabilitado el servicio, mDNS envía mensajes de despedida para cada servicio local a la red que está conectado a la interfaz, para notificarlo a los nodos vecinos.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **interface_index** Índice de la interfaz en la que se va a deshabilitar el servicio.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se habilitó correctamente el servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a>nx_mdns_cache_notify_set

Instalar la función de notificación completa de la caché de mDNS

### <a name="prototype"></a>Prototipo

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a>Descripción

Este servicio instala una función de devolución de llamada proporcionada por el usuario, que se invoca cuando la caché de servicio local o la caché de servicio del mismo nivel se llenan. Cuando la caché de servicio está llena, no se pueden agregar más registros de recursos de mDNS. Tenga en cuenta que la caché de servicio puede llenarse como resultado de la fragmentación interna, cuando se agregan y quitan servicios con distintas longitudes de cadena. Al recibir una notificación de caché llena en la caché de servicio del mismo nivel, la aplicación puede usar el servicio "*nx_mdns_service_cache_clear"* para borrar todas las entradas de dicha caché.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se instaló correctamente la función de devolución de llamada de notificación de la caché de mDNS.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a>nx_mdns_cache_notify_clear

Borrar la función de notificación completa de la caché del servicio mDNS

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Descripción

Este servicio borra una función de devolución de llamada de notificación de la caché de servicio proporcionada por el usuario.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se borró correctamente la función de devolución de llamada de notificación de la caché del servicio mDNS.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a>nx_mdns_domain_name_set

Establecer el nombre de dominio

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a>Descripción

Este servicio configura el nombre de dominio local predeterminado. Cuando se crea la instancia de mDNS, el nombre de dominio local predeterminado se establece en "local". Esta API permite a una aplicación sobrescribir el nombre de dominio local predeterminado.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **domain_name** Nombre de dominio que se va a usar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se configuró correctamente el dominio local.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a>nx_mdns_service_announcement_timing_set

Establece los parámetros de tiempo de los mensajes de anuncio de servicio.

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a>Descripción

Este servicio reconfigura los parámetros de tiempo empleados por mDNS al enviar los anuncios de servicio. El período de publicación comienza a partir de *t* tics y se puede ampliar de manera telescópica con 2 elevado a la potencia del factor *k*. El número de repeticiones por anuncio es *p*, el intervalo entre cada anuncio repetido es *intervalo* tics y el número de períodos de anuncio es max_time. De forma predeterminada, el período inicial se establece en 1 segundo, con k = 1 (el período se duplica cada vez), *p = 1* (sin repetición), retrans_interval = 0 (sin intervalo de tiempo), period_interval = 0xFFFFFFFF (intervalo de período máximo) y max_time = 3 (número de anuncios).

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **t** Número de tics del período inicial. El valor predeterminado es 100 tics para 1 segundo.
- **p** Número de repeticiones. El valor predeterminado es 1.
- **k** Factor telescópico. El valor predeterminado es 1.
- **retrans_interval** Número de tics que hay que esperar antes de enviar mensajes de anuncio repetidos. El valor predeterminado es 0.
- **period_interval** Número de tics entre dos períodos de anuncio. El valor predeterminado es 0xFFFFFFFF.
- **max_time** Número de períodos de anuncio que se van a usar para el anuncio. Después de los períodos de anuncio de *max_time*, no se envían más mensajes de anuncio. El valor predeterminado es 3.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Establece correctamente los valores de tiempo.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a>nx_mdns_service_add

Agregar un servicio local

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a>Descripción

Esta API registra un servicio ofrecido por la aplicación. Si se establece la marca *is_unique*, mDNS sondea el nombre del servicio para asegurarse de que es único en la red local antes de empezar a anunciar el servicio en la red. *Instance* es la parte de instancia del nombre del servicio. *service* es la parte de servicio del nombre del servicio. Por ejemplo, "_http._tcp" es un servicio. Para describir un servicio con subtipo, el autor de llamada debe usar el parámetro *subtype*. Por ejemplo, si el servicio deseado es "_printer._sub._http._tcp", el campo de servicio es "_http._tcp:" y el campo de subtipo es "_printer".

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **instance** Puntero al nombre de instancia del servicio.
- **service** Puntero al tipo de servicio mDNS, excluida la información del subtipo.
- **subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.
- **priority** Prioridad del servicio.
- **weight** Peso del servicio.
- **port** Número de puerto TCP o UDP que usa el servicio
- **text** Información de texto adicional.
- **is_unique** Marca booleana que indica si el servicio es compartido o único. En el caso de los servicios registrados como únicos, mDNS debe sondear el servicio en la red antes de iniciar su oferta.
- **Interface_index** Interfaz física mediante la que se ofrece el servicio. Con los servicios que se ofrecen mediante cualquiera de los servicios asociados, se usa el valor *NX_MDNS_ALL_INTERFACES*.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se registró correctamente el servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a>nx_mdns_service_delete

Quitar un servicio registrado anterior

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a>Descripción

Esta API elimina un servicio registrado anterior. Cuando se elimina el servicio, se envían mensajes de despedida a la red local para notificarlo a los nodos vecinos.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **instance** Puntero al nombre de instancia del servicio.
- **service** Puntero al tipo de servicio mDNS, excluida la información del subtipo.
- **subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se eliminó correctamente el servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a>nx_mdns_service_one_shot_query

Iniciar la detección de servicios una sola vez

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio realiza una consulta de mDNS una sola vez. Si el servicio especificado se encuentra en la caché de servicio del mismo nivel, se devuelve la primera instancia. Si no se encuentra ningún servicio en la caché de servicio del mismo nivel local, el módulo mDNS emite un comando de consulta y espera la respuesta. El servicio se bloquea hasta que se recibe la primera respuesta o se agota el tiempo de espera de la consulta.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **instance** Puntero al nombre de instancia del servicio, si procede.
- **service** Puntero al tipo de servicio mDNS, excluida la información del subtipo. La aplicación debe especificar el tipo de servicio.
- **subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.
- **service_ptr** Puntero proporcionado por el usuario a la estructura NX_MDNS_SERVICE que almacena los resultados de la consulta.
- **WAIT_OPTION** Cantidad de tiempo de espera, en tics, para obtener una respuesta.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se obtuvo correctamente la información del servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a>nx_mdns_service_continuous_query

Iniciar la detección continua de servicios

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Descripción

Este servicio inicia una consulta continua. Tenga en cuenta que el servicio se devuelve inmediatamente. Después de emitir una consulta continua, la aplicación puede recuperar el registro del servicio mediante la API *nx_mdns_service_lookup*. Para detener la consulta continua, la aplicación puede usar la API *nx_mdns_service_query_stop*.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **instance** Puntero al nombre de instancia del servicio, si procede.
- **service** Puntero al tipo de servicio mDNS, excluida la información de subtipo, si procede.
- **subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se inició correctamente la consulta.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a>nx_mdns_service_query_stop

Cesar una detección continua de servicios emitida previamente

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Descripción

Esta API finaliza una detección continua de servicios emitida anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **instance** Puntero al nombre de instancia del servicio.
- **service** Puntero a la información de subtipo del tipo de servicio mDNS.
- **subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se detuvo correctamente la consulta.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a>nx_mdns_service_lookup

Recupera el servicio de la caché de servicio del mismo nivel local.

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a>Descripción

Este servicio busca servicios que coincidan con el nombre de instancia (si se proporciona) y con el tipo de servicio en la caché de servicio del mismo nivel local. La aplicación iniciará la búsqueda de servicio con *instance_index* establecido en cero con respecto al primer servicio de la caché que coincida con la descripción. La aplicación mantendrá el uso de este servicio con un aumento del valor de *instance_index* para los servicios adicionales que se encuentran en la caché, hasta que el servicio devuelva *NX_NO_MORE_ENTRIES*, que indica el final de esta.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **instance** Puntero al nombre de instancia del servicio, si procede.
- **service** Puntero al tipo de servicio mDNS, excluida la información de subtipo, si procede.
- **subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.
- **Instance_index** Número de índice de la instancia que se va a devolver.
- **service_ptr** Puntero proporcionado por el usuario a la estructura NX_MDNS_SERVICE que almacena los resultados de la búsqueda.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se recuperó correctamente el servicio.
- **NX_NO_MORE_ENTRIES** (0X17) No se encuentra ninguna entrada de servicio en el número de índice especificado. Este código de error indica el final de la búsqueda.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a>nx_mdns_service_ignore_set

Configurar un conjunto de omisiones de servicios

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a>Descripción

Esta API configura una máscara para omitir los servicios especificados por la máscara de bits *service_mask*. Opcionalmente, el usuario puede usar el parámetro service_mask para seleccionar los tipos de servicio que no desee almacenar en caché. En la tabla *nx_mdns_service_types* de *nxd_mdns.c.* , se define una lista de servicios. La máscara correspondiente del primer tipo de servicio de nx_mdns_service_types[] es 0x00000001, la máscara del segundo tipo de servicio es 0x00000002, etc.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **service_mask** Tipos de servicio definidos por el usuario que se van a omitir. La máscara es un tipo ULONG de 32 bits. Cada bit representa una entrada en la matriz *nx_mdns_service_types* definida por el usuario. Si se establece un bit, el tipo de servicio correspondiente especificado en la matriz *nx_mdns_service_type* no se almacenará en la caché de servicio del mismo nivel.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Establece correctamente la máscara de omisión del servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a>nx_mdns_service_notify_set

Configurar una función de devolución de llamada de notificación de cambio de servicio

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a>Descripción

Esta API configura una función de devolución de llamada de notificación de cambio de servicio. Esta función de devolución de llamada se invoca cuando se agrega, cambia o deja de estar disponible un servicio ofrecido por otros nodos de la red. Opcionalmente, el usuario puede usar el parámetro service_mask para seleccionar los tipos de servicio que quiere supervisar. En la tabla *nx_mdns_service_types* de *nxd_mdns. c.* , hay una lista de servicios en proceso de supervisión que están codificados de forma rígida.

La máscara correspondiente del primer tipo de servicio de nx_mdns_service_types[] es 0x00000001, la máscara del segundo tipo de servicio es 0x00000002, etc.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **service_mask** Tipos de servicio definidos por el usuario que se van a supervisar. La máscara es un tipo ULONG de 32 bits. Cada bit representa una entrada en la matriz de *nx_mdns_service_types*.
- **service_change_notify** Función de devolución de llamada que se invoca cuando cambia el servicio especificado. La información detallada del servicio se devuelve en la memoria a la que apunta *service_ptr*. Tenga en cuenta que el contenido de la memoria no es válido después de volver de la función de devolución de llamada de notificación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se instaló correctamente la función de devolución de llamada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a>nx_mdns_service_notify_clear

Borrar la función de devolución de llamada de notificación de cambio de servicio

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Descripción

Esta API borra la función de devolución de llamada de notificación de cambio de servicio.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se borró correctamente la función de devolución de llamada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a>nx_mdns_host_address_get

Obtener la dirección de host

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio realiza una consulta mDNS en las direcciones IPv4 e IPv6 del host. Si la dirección del nombre de host especificado se encuentra en la caché de servicio del mismo nivel, se devuelve la dirección. Si no se encuentra ninguna dirección en esta caché, el módulo mDNS emite consultas de tipo A y AAAA y espera la respuesta. Esta API se bloquea hasta que se recibe una respuesta o se agota el tiempo de espera de la consulta.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.
- **host_name** Puntero al nombre de host.
- **ipv4_address** Puntero a una dirección alineada de 4 bytes para el espacio de almacenamiento de direcciones IPv4. El usuario debe asignar 4 bytes de espacio para la dirección IPv4. La dirección de NX_NULL se puede pasar a esta API si la aplicación no necesita recuperar la dirección IPv4.
- **ipv6_address** Puntero a la dirección alineada de 4 bytes para el espacio de almacenamiento de direcciones IPv6. El usuario debe asignar 16 bytes de espacio para la dirección IPv6. La dirección de NX_NULL se puede pasar a esta API si la aplicación no necesita recuperar la dirección IPv6.
- **WAIT_OPTION** Cantidad de tiempo de espera, en tics, para obtener una respuesta.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se obtuvo correctamente la dirección del host.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a>nx_mdns_local_cache_clear

Borrar todos los servicios locales

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Descripción

Este servicio borra todas las entradas de la caché del servicio local después de enviar el mensaje de despedida.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se borraron correctamente todas las entradas de la caché.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a>nx_mdns_peer_cache_clear

Borrar todos los servicios detectados

### <a name="prototype"></a>Prototipo

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Descripción

Este servicio borra todas las entradas de la caché de servicio del mismo nivel.

### <a name="input-parameters"></a>Parámetros de entrada

- **mdns_ptr** Puntero al bloque de control de mDNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se borraron correctamente todas las entradas de la caché.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
