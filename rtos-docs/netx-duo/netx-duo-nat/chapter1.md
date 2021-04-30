---
title: 'Capítulo 1: Introducción a la traducción de direcciones de red'
description: La traducción de direcciones de red (NAT) IP se desarrolló originalmente para solucionar el problema de un número limitado de direcciones IPv4 de Internet.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3d01aa6f68e21ea82f65a59a19c4f5c7958a6b92
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814633"
---
# <a name="chapter-1---an-introduction-to-network-address-translation"></a>Capítulo 1: Introducción a la traducción de direcciones de red

## <a name="the-need-for-network-address-translation"></a>Necesidad de la traducción de direcciones de red

La traducción de direcciones de red (NAT) IP se desarrolló originalmente para solucionar el problema de un número limitado de direcciones IPv4 de Internet. La necesidad de NAT se produce cuando varios dispositivos necesitan tener acceso a Internet, pero el proveedor de servicios Internet (ISP) solo asigna una dirección de Internet IPv4.

También hay otras ventajas en el uso de NAT. La topología de red fuera del dominio local puede cambiar de muchas maneras. Los clientes pueden cambiar los proveedores, las redes troncales de la empresa se pueden reorganizar o los proveedores pueden combinarlos o dividirlos. Siempre que cambie la topología externa, las asignaciones de direcciones para los hosts dentro del dominio local también deben cambiar para reflejar estos cambios externos. Los cambios de este tipo se pueden ocultar a los usuarios dentro del dominio centralizando los cambios en un único enrutador de traducción de direcciones. NAT permite el acceso de los hosts locales a la red pública de Internet y los protege del acceso directo desde el exterior. Las organizaciones con una configuración de red principalmente para uso interno, con una necesidad de acceso externo ocasional, son buenos candidatos para este esquema.

## <a name="basic-nat-and-network-address-port-translation"></a>Traducción básica de puertos de direcciones de red y NAT

Un enrutador habilitado para NAT se instala entre la red pública y la red privada. La función del enrutador habilitado para NAT consiste en traducir entre las direcciones IPv4 privadas internas y la dirección IPv4 pública asignada, por lo que todos los dispositivos de la red privada pueden compartir la misma dirección IPv4 pública.

En la implementación básica de NAT, el enrutador NAT "posee" una o más direcciones IP registradas globalmente diferentes de su propia dirección IP. Estas direcciones globales están disponibles para asignarlas a los hosts de su red privada de forma estática o dinámica. NAPT, o traducción de puertos de dirección de red, es una variación de NAT básico, donde la traducción de direcciones de red se amplía para incluir un identificador de "transporte". Normalmente, es el número de puerto de los paquetes TCP y UDP, y el identificador de consulta de los paquetes ICMP.

Normalmente, las conexiones a través del límite de NAT se inician mediante los hosts de la red privada que envían paquetes salientes a un host externo. Con este fin, a estos hosts se les asignan habitualmente direcciones IP *dinámicas* (temporales). Sin embargo, también es posible que las conexiones se inicien en la dirección opuesta si la red privada tiene "servidores", por ejemplo, servidores HTTP o FTP que aceptarán solicitudes de cliente de la red externa. Normalmente, NAT asignará a estos hosts locales una dirección IP *estática* (permanente): puerto.

## <a name="how-network-address-translation-works"></a>Funcionamiento de la traducción de direcciones de red

En la figura 1 se muestra una configuración de red típica con un enrutador habilitado para NAT.

![Configuración de red típica con un enrutador habilitado para NAT](media/image2.png)

**Figura 1: Configuración de red típica con un enrutador habilitado para NAT**

Un enrutador habilitado para NAT normalmente tiene dos interfaces de red. Una interfaz está conectada a la red pública de Internet y la otra está conectada a la red privada. Un enrutador típico en esta configuración es responsable de enrutar los datagramas IP entre la red privada y la red pública en función de la dirección IP de destino. Un enrutador habilitado para NAT realiza la traducción de direcciones antes de enrutar un datagrama IPv4 entre la interfaz pública y la privada. Se establece una traducción para cada sesión TCP o UDP, en función de la dirección de origen interna, el número de puerto de origen, la dirección de destino externa y el número de puerto de destino. En el caso de la solicitud de eco ICMP y el datagrama de respuesta, se usa el identificador de consulta ICMP en lugar del número de puerto.

Para ilustrar una implementación típica de la traducción de direcciones de red, supongamos que tenemos en cuenta una configuración de red en la figura 2.

![Implementación típica de la traducción de direcciones de red](media/image3.png)

**Figura 2: Implementación típica de la traducción de direcciones de red**

En este escenario, el enrutador NAT conecta la red privada a la izquierda y la red pública a la derecha. Supongamos que en el lado de la red pública, la dirección IP de la interfaz del enrutador NAT es 202.151.25.14 y que en la interfaz de red privada, el enrutador NAT usa la dirección IP 192.168.1.254. Un nodo de la red privada inicia una conexión TCP con un servidor web en Internet.

En la figura 3 se muestra una vista general del proceso de traducción de direcciones de red.

![Vista general del proceso de traducción de direcciones de red](media/image4.png)

**Figura 3: Vista general del proceso de traducción de direcciones de red**

1. El cliente transmite un mensaje SYN de TCP al servidor web. La dirección del remitente es 192.168.1.15 y el número de puerto 6732; la dirección de destino es 128.15.54.3 y el número de puerto 80.
1. El enrutador NAT recibe el paquete del cliente en la interfaz de red privada. La regla de tráfico saliente se aplica al paquete: la dirección del remitente (cliente) se traduce a la dirección IP pública del enrutador NAT 202.15.25.14 y el número de puerto de origen del remitente (cliente) se traduce al número de puerto TCP 2015 en la interfaz pública.
1. A continuación, el paquete se transmite a través de Internet y, finalmente, llega a su host de destino 128.15.54.3. Observe que en el lado de recepción, en función de la dirección de origen y el número de puerto de la capa TCP, el paquete parece haberse originado en 202.151.24.14, número de puerto 2015.
   La figura 4 muestra el proceso NAT en la ruta de acceso de devolución.

   ![Proceso NAT en la ruta de acceso de devolución](media/image5.png)

   **Figura 4: Proceso NAT en la ruta de acceso de devolución**
1. En este escenario, el host de Internet 128.15.54.3 envía un paquete de respuesta con la dirección de Internet del enrutador NAT como destino.
1. El paquete alcanza el enrutador NAT. Dado que se trata de un paquete entrante, se aplican las reglas de traducción de entrada: la dirección de destino se vuelve a cambiar a la dirección IP del remitente (cliente) original: 192.168.1.15, número de puerto de destino 6732.
1. A continuación, el paquete se reenvía al cliente mediante la interfaz que está conectada a la red interna.

De esta manera, la dirección de red de Internet y el número de puerto del remitente no se exponen a otros hosts de la red pública de Internet.

## <a name="netx-duo-nat-features"></a>Características de NAT en NetX Duo

Cuando se crea la instancia de NAT mediante la llamada a *nx_nat_create*, se crea la tabla de traducción NAT.

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

Para realizar un seguimiento de las traducciones de direcciones de red de todas las conexiones activas entre las redes locales y externas, el enrutador habilitado para NAT de Net Duo mantiene una tabla de traducción con información sobre cada conexión de host privado que incluye la dirección IP de origen y de destino y el número de puerto.

La ubicación de esta tabla de traducción ("caché") se establece con el puntero dynamic_cache_memory. Esta área debe ser un espacio de búfer alineado de 4 bytes. El tamaño de la tabla (o el número de entradas) se determina dividiendo el tamaño de caché dynamic_cache_size por el tamaño de una entrada de la tabla NAT. La tabla debe ser lo suficientemente grande para el número mínimo de entradas especificado por **NX_NAT_MIN_ENTRY_COUNT que se define en *nx_nat.h*. El valor predeterminado es 3.**

El tiempo de espera de todas las entradas dinámicas de la tabla de traducción NAT de NetX Duo se inicializa en NX_NAT_ENTRY_RESPONSE_TIMEOUT, que se define en *nx_nat. h*. El valor predeterminado es 4 minutos (240 tics del sistema en el caso de un procesador de 100 mHz), según se recomienda en el documento RFC 2663. Cada vez que NAT de NetX Duo recibe o envía un paquete que coincide con una entrada dinámica de la tabla, restablece el tiempo de espera de la entrada en NX_NAT_ENTRY_RESPONSE_TIMEOUT. Al buscar en la tabla, NAT de NetX Duo también buscará en la tabla las entradas expiradas y las eliminará.

Para crear entradas entrantes como estáticas en la tabla, por ejemplo, para los servidores de la red local, NAT de NetX Duo proporciona el servicio *nx_nat_inbound_entry_create*. Si una entrada de la tabla define la conexión del host local como estática, nunca expira.

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr,
    ULONG local_ip_address, USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

Este servicio se describe con más detalle en [Capítulo 4: Descripción de los servicios](chapter4.md).

Durante el tiempo de ejecución, si la tabla de traducción está llena y no se pueden agregar más entradas, NAT de NetX Duo lo notificará a la aplicación NAT con una devolución de llamada de caché completa si se registra una con la instancia de NAT. Para ello se usa el servicio *nx_nat_cache_notify_set*.

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)(NX_NAT_DEVICE *nat_ptr));
```

Consulte [Capítulo 4: Descripción de los servicios](chapter4.md) para más información sobre este servicio.

## <a name="nat-packet-processing-in-netx-duo"></a>Procesamiento de paquetes NAT en NetX Duo

El uso de NAT de NetX Duo va dirigido a los enrutadores IPv4. Para que NAT funcione, NetX Duo debe estar configurado para reenviar paquetes al servidor NAT. Consulte el capítulo 2 sobre la instalación de NAT de NetX Duo para saber cómo hacerlo. El servidor NAT indica entonces si "consume" (intenta reenviar) el paquete a un host de cualquiera de sus redes. Si no se consume el paquete, este se "devuelve" a NetX Duo para procesarlo de la manera habitual.

Cuando el servidor NAT recibe un paquete para reenviar desde NetX Duo, determina si el paquete es entrante o saliente.

En el caso de los paquetes salientes, el servidor NAT comprueba la dirección de origen y el puerto del encabezado IP del paquete. Si la tabla de traducción no contiene una entrada para un paquete enviado previamente por este host para el mismo destino, NAT creará una nueva entrada que contendrá una dirección IP de origen global única para la conexión-puerto y modificará los encabezados de paquete con esta nueva dirección IP-puerto antes de enviarlo a la red externa.

En el caso de los paquetes entrantes, el servidor NAT busca una entrada anterior en su tabla de traducción con una dirección IP externa-puerto que coincida con la dirección IP de destino del paquete-puerto. Si no se encuentra ninguna coincidencia, descartará el paquete a menos que la dirección de destino-puerto sea la dirección externa del servidor en la red local. Si encuentra una coincidencia, reemplazará la dirección IP de destino externa del encabezado del paquete-puerto por la dirección IP privada-puerto y enviará el paquete en la red local al host privado previsto.

NAT de NetX Duo emplea una serie de puertos de traducción TCP, UDP e ICMP para crear conexiones únicas de dirección local-puerto para los hosts locales que se conectan a hosts externos. Las siguientes opciones configurables por el usuario, definidas en *nx_nat.h* definen el intervalo de cada protocolo:

```C
NX_NAT_START_TCP_PORT

NX_NAT_END_TCP_PORT

NX_NAT_START_UDP_PORT

NX_NAT_END_UDP_PORT

NX_NAT_START_ICMP_QUERY_ID

NX_NAT_END_ICMP_QUERY_ID
```

## <a name="nat-requirements-and-constraints"></a>Requisitos y restricciones de NAT

NAT de NetX Duo requiere NetX Duo 5.8 o posterior. La aplicación NAT requiere la creación de una única instancia IP y una interfaz a la red física interna y externa.

Restricciones:

- NAT de NetX Duo es compatible con TCP, UDP e ICMP. IGMP no es compatible.
- NAT de NetX Duo no admite direccionamiento IPv6.
- NAT de NetX Duo no incluye los servicios DNS o DHCP, aunque puede integrar esos servicios con sus operaciones NAT.

## <a name="rfcs-supported-by-netx-duo-nat"></a>Documentos RFC que cumple NAT de NetX Duo

La implementación de NAT de NetX Duo se basa en la información que se presenta en los siguientes documentos RFC:

- RFC 2663: Terminología y consideraciones del traductor de direcciones IP de red (NAT)
- RFC 3022: Traductor de direcciones de red IP tradicionales (NAT tradicional)
- RFC 4787: Requisitos de comportamiento de la traducción de direcciones de red (NAT) para UDP de unidifusión
