---
title: 'Capítulo 3: Descripción de la caché de servicio interna'
description: 'El módulo mDNS de NetX Duo administra dos cachés de servicio internas: la caché de servicio local y la caché de servicio del mismo nivel.'
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 007f1080a076730cfbcdedc9f063ac0c427a414c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814662"
---
# <a name="chapter-3---description-of-internal-service-cache"></a>Capítulo 3: Descripción de la caché de servicio interna

El módulo mDNS de NetX Duo administra dos cachés de servicio internas: la caché de servicio local y la caché de servicio del mismo nivel. La caché del servicio local almacena los registros de recursos relacionados con los servicios que ofrecen las aplicaciones que se ejecutan en el nodo. En el caso de las consultas entrantes, si la pregunta coincide con el servicio ofrecido, mDNS responde con las respuestas almacenadas en la caché del servicio local. Las aplicaciones registran servicios mediante la llamada a la API *nx_mdns_service_add()* . Para quitar servicios y aplicaciones, use la API *nx_mdns_service_delete()* , que, a su vez, enviará mensajes de despedida antes de quitar las entradas correspondientes de la caché del servicio local.

Cuando se agrega un servicio, mDNS mantiene al menos 3 registros de recursos en la caché del servicio local: SRV, PTR y TXT. Se puede agregar un registro de recursos PTR adicional si el tipo de servicio incluye el subtipo. Por ejemplo, una aplicación registra un servicio:

```
*name*._*subtype*._sub._*type*._tcp.local,
```

dos registros de recursos PTR se agregan a la caché de servicio local, uno para

```
“*_subtype._*sub*._type._*tcp.local *PTR name.type._*tcp*.*local”
```

y el otro para

```
*“_type._*tcp*.*local *PTR name.type._*tcp*.*local”.
```

La caché de servicio del mismo nivel contiene registros de recursos mDNS recibidos de los nodos vecinos. El módulo mDNS recopila registros de recursos anunciados por otros nodos de la red y almacena la información recibida en la caché de servicio del mismo nivel. Cuando la aplicación consulta información, como direcciones IPv4 o IPv6 del host, mDNS busca en la caché de servicio del mismo nivel las respuestas almacenadas en caché localmente. Cuando la aplicación consulta los servicios ofrecidos por los nodos del mismo nivel, mDNS busca en la caché los registros de direcciones PTR, SRV, TXT y IPv4/IPv6 relacionados. La caché de servicio del mismo nivel también almacena las consultas enviadas al nodo. Por ejemplo, una aplicación puede solicitar un servicio determinado mediante la llamada a *nx_mdns_service_one_shot_query.* Si el servicio no se encuentra en la caché de servicio del mismo nivel, mDNS crea preguntas de consulta (PTR, SRV y TXT) en dicha caché. Estas preguntas de consulta se enviarán a la red de forma periódica hasta que se resuelva el servicio o se agote el tiempo de espera. De igual forma, la aplicación puede usar la API *nx_mdns_service_continous_query()* para solicitar un servicio determinado durante un largo período de tiempo (la aplicación cancela una consulta continua emitida anteriormente mediante la API *nx_mdns_service_query_stop de API()* ). Para buscar un servicio determinado en la caché de servicio del mismo nivel sin enviar consultas a la red, las aplicaciones pueden utilizar la API *nx_mdns_serivce_lookup().* Esta API solo busca los registros de recursos en la caché de servicio del mismo nivel.

Cada registro de recursos se almacena en una estructura de datos *NX_MDNS_RR* en las cachés de servicio. Las cadenas de los registros de recursos son de longitud variable, por lo que no se almacenan en la estructura *NX_MDNS_RR*. El registro de recursos contiene un puntero a la ubicación de memoria real donde se almacena la cadena. La tabla de cadenas y los registros de recursos comparten la caché de servicio. Los registros de recursos se almacenan desde el principio de la caché de servicio y crecen hasta que se llena la caché. La tabla de cadenas comienza desde el final de la caché de servicio y crece hasta el principio de la caché. Cada cadena de la tabla de cadenas tiene un campo de longitud y un campo de contador. Cuando se agrega una cadena a la tabla de cadenas, si la misma cadena ya está presente en la tabla, el valor del contador se incrementa y no se asigna memoria a la cadena. La caché de servicio se considera llena si no se pueden agregar más registros de recursos ni cadenas nuevas a la caché de servicio.

Hay dos maneras de que una aplicación encuentre los servicios ofrecidos en la red local. Se puede emitir una búsqueda de un servicio específico mediante una consulta de una sola vez, o bien se puede iniciar una consulta continua para "supervisar" las actividades de la red. En el escenario de consulta única, la aplicación debe especificar el tipo de servicio. mDNS busca en la caché de servicio local y en la caché de servicio del mismo nivel. Si se encuentra una instancia de servicio, la consulta única devuelve la información encontrada en los registros de recursos. Si no hay ningún registro en la caché de servicio local ni en la caché de servicio del mismo nivel, mDNS envía mensajes de consulta. Si se especifica el nombre de la instancia, se envía a la red local un tipo *ANY* (consultar el tipo SRV y TXT) con el nombre de instancia específico, con el formato "name.type.local". Si no se especifica el nombre de instancia, se envía un tipo PTR de consulta a la red local. El primer servicio completo recibido se devuelve al autor de la llamada.

La consulta continua funciona de forma diferente. El caso de uso típico de una consulta continua es supervisar la red local en busca de un servicio específico (por ejemplo, para buscar constantemente servicios de impresión en la red local). En este caso, la aplicación emite una consulta de búsqueda (a través de la API *nx_mdns_service_continious_* query) de ciertos tipos de servicios. Normalmente, el autor de llamada no espera una respuesta determinada. En el caso de las consultas enviadas como consultas continuas, el módulo mDNS transmite las consultas periódicamente con intervalos que aumentan exponencialmente. Para detener la consulta, la aplicación debe usar la API *nx_mdns_service_query_stop* para detener el temporizador interno de estas consultas. El tipo de consulta puede ser NULL, en cuyo caso el tipo de consulta se establece en el tipo PTR especial "_services._dns-sd._udp.local". Este tipo de servicio se define mediante mDNS como una manera de detectar todos los servicios disponibles en la red local. Si se proporciona el nombre de instancia, se envía a la red local un tipo ANY (consultar el tipo SRV y TXT) con el nombre de instancia específico "name.type.local". Si el nombre de instancia es NULL, se envía un tipo PTR de consulta a la red local.

Todas las respuestas, incluidas las que proceden de las consultas no solicitadas, se registran en la caché de servicio del mismo nivel. Posteriormente, la aplicación utiliza la API *nx_mdns_service_lookup* para recuperar un servicio específico de la caché de servicio del mismo nivel.

Nota especial sobre la fragmentación: cada estructura *NX_MDNS_RR* tiene un tamaño fijo y, por lo tanto, no está sujeta a la fragmentación, ya que mDNS agrega y elimina los registros de recursos. Sin embargo, las cadenas son de longitud variable. Una vez que se elimina una cadena, el espacio está disponible y se puede usar para la nueva cadena si cabe. Sin embargo, esta operación hace que la memoria se fragmente. A medida que se agregan y quitan servicios, la tabla de cadenas se puede fragmentar hasta el punto de no poderse agregar cadenas nuevas aunque la caché de servicio contenga suficientes bytes no utilizados para la cadena. Las aplicaciones locales suelen ser más estables y predecibles. Por lo tanto, es menos probable que la caché de servicio local sufra fragmentación. La caché de servicio del mismo nivel, por otro lado, agrega constantemente registros de recursos a medida que los servicios están disponibles, o bien los quita cuando los nodos de la red eliminan los servicios. Los servicios de la red van y vienen, lo que provoca operaciones de asignación/eliminación más frecuentes en la tabla de cadenas. Con el tiempo, es posible que la tabla de cadenas se fragmente. Cuando se produce esta situación, una solución sencilla es vaciar toda la caché de servicio del mismo nivel. Para ello, puede llamar a la API *nx_mdns_peer_cache_clear()* . Tenga en cuenta que esta API finaliza automáticamente las consultas continuas pendientes.
