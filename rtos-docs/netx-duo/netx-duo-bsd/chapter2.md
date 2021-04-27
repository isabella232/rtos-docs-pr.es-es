---
title: 'Capítulo 2: Instalación y uso de BSD de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente BSD de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 582661bc66c51341fc098de9ff7b6fa2a7d746de
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814822"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a>Capítulo 2: Instalación y uso de BSD de Azure RTOS NetX Duo

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente BSD de Azure RTOS NetX Duo.

## <a name="product-distribution"></a>Distribución del producto

BSD de Azure RTOS NetX Duo se puede obtener desde nuestro repositorio de código fuente público en [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/). El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:

- **nxd_bsd.h**: archivo de encabezado para BSD de NetX Duo
- **nxd_bsd.c**: archivo de código fuente para BSD de NetX Duo
- **nxd_bsd.pdf**: manual de usuario de BSD de NetX Duo

Archivos de demostración:

- **bsd_demo_udp.c**
- **bsd_demo_tcp.c**
- **bsd_demo_raw.c**

## <a name="netx-duo-bsd-installation"></a>Instalación de BSD de NetX Duo

Para usar BSD de NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo. Por ejemplo, si NetX Duo está instalado en el directorio " *\threadx\arm7\green*", los archivos *nxd_bsd.h* y *nxd_bsd.c* deben copiarse en ese mismo directorio.

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a>Compilación de los componentes ThreadX y NetX Duo de una aplicación BSD

### <a name="threadx"></a>ThreadX

La biblioteca de ThreadX debe definir `bsd_errno` en el almacenamiento local para el subproceso. Se recomienda el siguiente procedimiento:

1. En *tx_port.h*, establezca una de las macros TX_THREAD_EXTENSION como se indica a continuación:
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. Recompile la biblioteca de ThreadX.

> [!NOTE]
> Si TX_THREAD_EXTENSION_3 ya está en uso, el usuario puede utilizar una de las otras macros TX_THREAD_EXTENSION.

### <a name="netx-duo"></a>NetX Duo

Antes de usar los servicios de BSD de NetX Duo, debe compilarse la biblioteca de NetX Duo con NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definido. De forma predeterminada, no está definido. Si se van a utilizar los sockets BSD sin formato, la biblioteca de NetX Duo debe compilarse con NX_ENABLE_IP_RAW_PACKET_FILTER definido.

## <a name="using-netx-duo-bsd"></a>Uso de BSD de NetX Duo

Un proyecto de aplicación BSD de NetX Duo debe incluir *nxd_bsd.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar los servicios de BSD especificados más adelante en este manual. La aplicación también debe incluir *nxd_bsd.c* en el proceso de compilación. Este archivo se debe compilar de la misma manera que otros archivos de la aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar BSD de NetX Duo.

Para poder usar los servicios de BSD de NetX Duo, la aplicación debe crear una instancia de IP, crear un grupo de paquetes para la capa BSD desde la que asignar paquetes, asignar espacio de memoria para la pila de subprocesos BSD internos y especificar la prioridad del subproceso BSD interno. La capa BSD se inicializa llamando a *bsd_initialize* y pasando los parámetros. Esto se muestra en los pequeños ejemplos que se incluyen más adelante en este documento, pero el prototipo se muestra a continuación:

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

default_ip es la instancia de IP en la que opera la capa BSD. Los servicios de BSD usan el parámetro default_pool como origen para asignar paquetes. Los dos parámetros siguientes, bsd_thread_stack_area y bsd_thread_stack_size, definen el área de pila usada por el subproceso BSD interno y el último parámetro, bsd_thread_priority, establece la prioridad del subproceso.

## <a name="netx-duo-bsd-raw-socket-support"></a>Compatibilidad con sockets sin formato de BSD de NetX Duo

BSD de NetX Duo también admite sockets sin formato. Para usar sockets sin formato en BSD de NetX Duo, la biblioteca de NetX Duo se debe compilar con NX_ENABLE_IP_RAW_PACKET_FILTER definido. De forma predeterminada, no está definido. A continuación, la aplicación debe habilitar el procesamiento de sockets sin formato para una instancia de IP creada anteriormente mediante una llamada a *nx_ip_raw_packet_enable.*

Para crear un socket sin formato en BSD de NetX Duo, la aplicación usa el servicio *socket* de creación de sockets y especifica la familia de protocolos, el tipo de socket y el protocolo:

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

protocolFamily es AF_INET para sockets IPv4 o AF_INET6 para sockets IPv6, suponiendo que IPv6 está habilitado en la instancia de IP. El parámetro socket_type debe establecerse en SOCK_RAW. El parámetro protocol es específico de la aplicación.

Para enviar y recibir paquetes sin formato, así como cerrar un socket sin formato, la aplicación usa normalmente los mismos servicios de BSD que para UDP, por ejemplo, *sendto, recvfrom, select* y *soc_close*. Los sockets sin formato no admiten los servicios *accept* ni *listen* de BSD.

- De forma predeterminada, los datos sin procesar de IPv4 recibidos incluyen el encabezado IPv4.  Por el contrario, los datos sin procesar IPv6 recibidos no incluyen el encabezado IPv6.

- De forma predeterminada, al enviar paquetes IPv6 o IPv4 sin formato, la capa de contenedor de BSD agrega el encabezado IPv6 o IPv4 antes de enviar los datos.

BSD de NetX Duo es compatible con opciones adicionales de sockets sin formato, como IP_RAW_RX_NO_HEADER, IP_HDRINCL e IP_RAW_IPV6_HDRINCL.

Si se establece IP_RAW_RX_NO_HEADER, se quita el encabezado IPv4 para que los datos recibidos no lo incluyan y la longitud del mensaje notificado no incluye el encabezado IPv4.  En el caso de los sockets IPv6, de forma predeterminada, la recepción de sockets sin formato no incluye el encabezado IPv6, lo que equivale a tener establecida la opción IP_RAW_RX_NO_HEADER. La aplicación puede usar el servicio *setsockopt* para desactivar la opción IP_RAW_RX_NO_HEADER. Una vez desactivada esta opción, los datos de IPv6 sin formato recibidos incluirían el encabezado IPv6 y en la longitud del mensaje indicado se incluirá este encabezado.

Esta opción no tiene ningún efecto en los datos transmitidos de IPv4 o IPv6.

Si se establece IP_HDRINCL, la aplicación incluye el encabezado IPv4 al enviar datos.  Esta opción no tiene ningún efecto en la transmisión IPv6 y no está definida de forma predeterminada. Si se establece IP_RAW_IPV6_HDRINCL, la aplicación incluye el encabezado IPv6 al enviar datos.  Esta opción no tiene ningún efecto en la transmisión IPv4 y no está definida de forma predeterminada.

IP_HDRINCL e IP_RAW_IPV6_HDRINCL no tienen ningún efecto en la recepción de IPv4 o IPv6.

> [!NOTE]
> La especificación de sockets de BSD 4.3 indica que el kernel debe copiar el paquete sin formato en cada búfer de recepción del socket. Sin embargo, en BSD de NetX Duo, si se crean varios sockets que comparten el mismo protocolo, no se define el comportamiento.

## <a name="netx-duo-bsd-raw-packet-support"></a>Compatibilidad con paquetes sin formato de BSD de NetX Duo

Para habilitar la compatibilidad con paquetes sin formato para PPPoE, se debe crear un contenedor de BSD de NetX Duo con NX_BSD_RAW_PPPOE_SUPPORT habilitado.

El siguiente comando crea un socket BSD para administrar paquetes de PPPoE sin formato:

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

La implementación de BSD actual solo admite dos tipos de protocolo de la familia AF_PACKET:

- `ETHERTYPE_PPPOE_DISC`: paquetes de detección de PPPoE. En la trama de datos MAC, los paquetes de detección tienen el tipo de trama Ethernet 0x8863.

- `ETHERTYPE_PPPOE_SESS`: paquetes de sesión PPP. En la trama de datos MAC, los paquetes de sesión tienen el tipo de trama Ethernet 0x8864.

La estructura `sockaddr_ll` se usa para especificar los parámetros al enviar o recibir marcos PPPoE.

`struct sockaddr_ll` se declara como:

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> `sendto()` o `recvfrom()` no utilizan todos los campos de la estructura. Consulte la descripción siguiente sobre cómo configurar `sockaddr_ll` para el envío y la recepción de paquetes PPPoE.

El socket creado en la familia AF_PACKET se puede usar para enviar tanto paquetes de detección de PPPoE o paquetes de sesión de PPP, independientemente del protocolo especificado. Al transmitir un paquete PPPoE, la aplicación debe preparar el búfer que incluye el marco PPPoE con el formato correcto, incluidos los encabezados MAC (dirección MAC de destino, dirección MAC de origen y tipo de marco). El tamaño del búfer incluye el encabezado Ethernet de 14 bytes.

En la estructura `sockaddr_ll`, `sll_ifindex` se usa para indicar la interfaz física que se va a utilizar para enviar este paquete. El resto de los campos de la estructura no se utiliza. El proceso interno de BSD omite los valores establecidos en los campos no utilizados.

En el siguiente bloque de código se muestra cómo transmitir un paquete PPPoE:

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

El valor devuelto indica el número de bytes transmitidos. Dado que los paquetes PPPoE están basados en mensajes, en una transmisión correcta, el número de bytes enviados coincide con el tamaño del paquete, incluido el encabezado Ethernet de 14 bytes.

Los paquetes PPPoE se pueden recibir mediante `recvfrom()`. El búfer de recepción debe ser lo suficientemente grande como para incluir un mensaje con el tamaño de MTU de Ethernet. El paquete PPPoE recibido incluye el encabezado Ethernet de 14 bytes. Al recibir paquetes PPPoE, los paquetes de detección de PPPoE solo los puede recibir un socket creado con el protocolo `ETHERTYPE_PPPOE_DISC`. Del mismo modo, los paquetes de sesión PPP solo los puede recibir un socket creado con el protocolo `ETHERTYPE_PPPOE_SESS`. Si se crean varios sockets para el mismo tipo de protocolo, los paquetes PPPoE que llegan se reenvían al socket que se creó en primer lugar. Si el primer socket creado para el protocolo está cerrado, se usa el siguiente socket por orden de creación para recibir estos paquetes.

Después de recibir un paquete PPPoE, los siguientes campos de la estructura`sockaddr_ll` son válidos:
- **sll_family**: establecido en AF_PACKET por el proceso interno de BSD.
- **sll_ifindex**: indica la interfaz desde la que se recibe el paquete.
- **sll_protocol**: se establece en el tipo de paquete recibido: `ETHERTYPE_PPPOE_DISC` o `ETHERTYPE_PPPOE_SESS`.

## <a name="eliminating-internal-bsd-thread"></a>Eliminación de subprocesos BSD internos

De manera predeterminada, BSD emplea un subproceso interno para realizar parte de su procesamiento. En sistemas con restricciones de memoria estrictas, se puede compilar BSD con NX_BSD_TIMEOUT_PROCESS_IN_TIMER definido, lo que elimina el subproceso de BSD interno y, en su lugar, utiliza un temporizador interno para realizar el mismo procesamiento. Esto elimina la memoria necesaria para el bloque de control y la pila de subprocesos BSD internos. Sin embargo, el procesamiento general del temporizador se incrementa significativamente y el procesamiento de BSD también puede ejecutarse con una prioridad más alta de la necesaria.

Para configurar los sockets BSD de modo que se ejecuten en el contexto del temporizador de ThreadX, defina NX_BSD_TIMEOUT_PROCESS_IN_TIMER en *nxd_bsd.h*. Si la capa BSD está configurada para ejecutar las tareas de BSD en el contexto del temporizador, en la llamada a *bsd_initialize* se omiten los tres parámetros siguientes, que se deben establecer en NULL:

- **bsd_thread_stack_area**
- **bsd_thread_stack_size**
- **bsd_thread_priority**

## <a name="netx-duo-bsd-with-dns-support"></a>Compatibilidad de BSD de NetX Duo con DNS

Si se define NX_BSD_ENABLE_DNS, BSD de NetX Duo puede enviar consultas de DNS para obtener la información de la IP o el nombre del host. Esta característica requiere que se cree previamente un cliente DNS de NetX con el servicio *nx_dns_create*. Con la instancia de DNS, deben registrarse una o varias direcciones IP de servidor DNS conocidas mediante el servicio *nx_dns_server_add* para agregar direcciones de servidor IPv4 o mediante el servicio *nxd_dns_server_add* para agregar direcciones de servidor IPv4 o IPv6.

Los servicios DNS y la asignación de memoria se usan en los servicios *getaddrinfo* y *getnameinfo*:

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

Cuando la aplicación BSD llama a *getaddrinfo* con un nombre de host, BSD de NetX llamará a cualquiera de los servicios siguientes para obtener la dirección IP:

- **nx_dns_ipv4_address_by_name_get**
- **nxd_dns_ipv6_address_by_name_get**
- **nx_dns_cname_get**

Para *nx_dns_ipv4_address_by_name_get* y *nxd_dns_ipv6_address_by_name_get*, BSD de NetX usa las áreas de memoria ipv4_addr_buffer e ipv6_addr_buffer, respectivamente. El tamaño de estos búferes se define mediante (NX_BSD_IPV4_ADDR_PER_HOST * 4) y (NX_BSD_IPV6_ADDR_PER_HOST * 16), respectivamente.

Para devolver información de dirección de *getaddrinfo*, BSD de NetX usa la tabla de memoria de bloques de ThreadX nx_bsd_addrinfo_pool_memory, cuya área de memoria está definida por otro conjunto de opciones configurables, NX_BSD_IPV4_ADDR_MAX_NUM y NX_BSD_IPV6_ADDR_MAX_NUM.

Consulte **Opciones de configuración general** para obtener más detalles sobre las opciones de configuración anteriores.

Además, si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES y la entrada del host es un nombre canónico, BSD de NetX Duo asignará dinámicamente la memoria de un grupo de bloques `_nx_bsd_cname_block_pool creado previamente

> [!NOTE]
> Después de llamar a *getaddrinfo*, la aplicación BSD es responsable de liberar la memoria a la que apunta el argumento res de vuelta a la tabla de bloques mediante el servicio *freeaddrinfo*.

## <a name="netx-duo-bsd-limitations"></a>Limitaciones de BSD de NetX Duo

Debido a problemas de rendimiento y arquitectura, BSD de NetX Duo no admite todas las características de los sockets BSD 4.3:

Las marcas INT no se admiten para las llamadas a *send, recv, sendto* y *recvfrom*.

## <a name="general-configuration-options"></a>Opciones de configuración general

Las opciones configurables por el usuario en *nxd_bsd.h* permiten a la aplicación ajustar los sockets BSD de NetX Duo a sus requisitos de la aplicación concretos.

A continuación se muestra la lista de opciones configurables que se establecen en tiempo de compilación:

- **NX_BSD_TCP_WINDOW**: se usa en llamadas de creación de sockets TCP. 64 k es el tamaño de ventana típico para Ethernet de 100 Mb. El valor predeterminado es 65535.

- **NX_BSD_SOCKFD_START**: este es el índice lógico del valor de inicio del descriptor de archivo de socket BSD. De forma predeterminada, esta opción es 32.

- **NX_BSD_MAX_SOCKETS**: especifica el número máximo de sockets totales disponibles en la capa BSD y debe ser un múltiplo de 32. El valor predeterminado es 32.

- **NX_BSD_SOCKET_QUEUE_MAX**: especifica el número máximo de paquetes UDP almacenados en la cola de sockets de recepción. El valor predeterminado es 5.

- **NX_BSD_MAX_LISTEN_BACKLOG**: especifica el tamaño de la cola de escucha ("trabajo pendiente") para los sockets TCP de BSD. El valor predeterminado es 5.

- **NX_MICROSECOND_PER_CPU_TICK**: especifica el número de microsegundos por cada tic del temporizador del programador.

- **NX_BSD_TIMEOUT**: especifica el tiempo de espera en tics de temporizador requerido por BSD en las llamadas internas de NetX Duo. El valor predeterminado es (20 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: especifica el tiempo de espera en tics de temporizador en la llamada de desconexión de NetX Duo. El valor predeterminado es 1.

- **NX_BSD_PRINT_ERRORS**: si se establece, el valor devuelto de estado de error de una función BSD es un número de línea y un tipo de error, por ejemplo NX_SOC_ERROR, donde se produce el error. Esto requiere que el desarrollador de la aplicación defina la salida de la depuración. La configuración predeterminada está deshabilitada y no se especifica ninguna salida de depuración en *nxd_bsd.h*.

- **NX_BSD_TIMER_RATE**: intervalo después del cual se ejecuta la tarea de temporizador periódica de BSD. El valor predeterminado es 1 segundo (1 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: si se establece, esta opción permite que el proceso de tiempo de espera de BSD se ejecute en el contexto del temporizador del sistema. De forma predeterminada está desactivado. Esta característica se describe con más detalle en el capítulo 2 "Instalación y uso de BSD de NetX Duo".

- **NX_BSD_RAW_PPPOE_SUPPORT**: habilita la compatibilidad con paquetes sin formato de PPPoE. De forma predeterminada, esta opción no está habilitada.

- **NX_BSD_ENABLE_DNS**: si esta opción está habilitada, BSD de NetX Duo enviará una consulta de DNS de un nombre o una dirección IP de host. Requiere que se cree e inicie previamente una instancia de cliente DNS. De forma predeterminada, no está habilitada.

- **NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: define el tamaño de la tabla de sockets sin formato. El valor debe ser una potencia de dos. BSD de NetX crea una matriz de sockets de tipo NX_BSD_SOCKETS para enviar y recibir paquetes sin formato. NX_ENABLE_IP_RAW_PACKET_FILTER debe estar habilitado. El valor predeterminado es 32.

- **NX_BSD_IPV4_ADDR_MAX_NUM**: número máximo de direcciones IPv4 devueltas por *getaddrinfo*. Esto, junto con NX_BSD_IPV6_ADDR_MAX_NUM, define el tamaño del grupo de bloques nx_bsd_addrinfo_block_pool de BSD de NetX para asignar memoria de forma dinámica para el almacenamiento de información de direcciones en *getaddrinfo*. El valor predeterminado es 5.

- **NX_BSD_IPV6_ADDR_MAX_NUM**: número máximo de direcciones IPv6 devueltas por *getaddrinfo*. Esto, junto con NX_BSD_IPV4_ADDR_MAX_NUM, define el tamaño del grupo de bloques nx_bsd_addrinfo_block_pool de BSD de NetX para asignar memoria de forma dinámica para el almacenamiento de información de direcciones en *getaddrinfo*.

- **NX_BSD_IPV4_ADDR_PER_HOST**: define el número máximo de direcciones IPv4 almacenadas por consulta de DNS. El valor predeterminado es 5.

- **NX_BSD_IPV6_ADDR_PER_HOST**: define el número máximo de direcciones IPv6 almacenadas por consulta de DNS. El valor predeterminado es 2.

## <a name="bsd-socket-options"></a>Opciones de socket BSD

La siguiente lista de opciones de socket BSD de NetX Duo se puede habilitar (o deshabilitar) en tiempo de ejecución en cada socket mediante el servicio *setsockopt*:

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

Hay dos configuraciones diferentes para option_level.

El primer tipo de opciones de socket de tiempo de ejecución es SOL_SOCKET para las opciones de nivel de socket. Para habilitar una opción de nivel de socket, llame a *setsockopt* con option_level establecido en SOL_SOCKET y option_name establecido en la opción específica, por ejemplo, SO_BROADCAST *.* Para recuperar una configuración de opción, llame a *getsockopt* para option_name con option_level de nuevo establecido en SOL_SOCKET.

A continuación se muestra la lista de opciones de nivel de socket en tiempo de ejecución.

- **SO_BROADCAST**: si se establece, habilita el envío y la recepción de paquetes de difusión de sockets NetX. Este es el comportamiento predeterminado para NetX Duo. Todos los sockets tienen esta capacidad.

- **SO_ERROR**: se usa para obtener el estado del socket en la operación de socket anterior del socket especificado, mediante el servicio *getsockopt*. Todos los sockets tienen esta capacidad.

- **SO_KEEPALIVE**: si se establece, habilita la característica de mantenimiento de conexión de TCP. Esto requiere que la biblioteca de NetX Duo se compile con NX_TCP_ENABLE_KEEPALIVE definido en *nx_user.h*. Esta característica está deshabilitada de forma predeterminada.

- **SO_RCVTIMEO**: establece la opción de espera en segundos para recibir paquetes en sockets BSD de NetX Duo. El valor predeterminado es NX_WAIT_FOREVER (0xFFFFFFFF) o, si está habilitada la opción sin bloqueo, NX_NO_WAIT (0x0).

- **SO_RCVBUF**: establece el tamaño de la ventana del socket TCP. El valor predeterminado, NX_BSD_TCP_WINDOW, se establece en 64 k para sockets TCP de BSD. Para establecer un tamaño superior a 65535, es necesario que la biblioteca de NetX Duo se compile con NX_TCP_ENABLE_WINDOW_SCALING definido.

- **SO_REUSEADDR**: si se establece, permite asignar varios sockets a un puerto. Por lo general se usa en el socket de servidor TCP. Este es el comportamiento predeterminado de los sockets de NetX Duo.

El segundo tipo de opciones de socket en tiempo de ejecución es el nivel de opción de IP. Para habilitar una opción de nivel de IP, llame a *setsockopt* con option_level establecido en IP_PROTO y option_name establecido en la opción, por ejemplo, IP_MULTICAST_TTL *.* Para recuperar un valor de opción, llame a *getsockopt* para option_name con option_level de nuevo establecido en IP_PROTO.

A continuación se muestra la lista de opciones de nivel de IP en tiempo de ejecución.

- **IP_MULTICAST_TTL**: establece el período de vida de los sockets UDP. El valor predeterminado es NX_IP_TIME_TO_LIVE (0x80) cuando se crea el socket. Este valor se puede invalidar mediante una llamada a *setsockopt* con esta opción de socket.

- **IP_RAW_IPV6_HDRINCL**: si se establece esta opción, la aplicación que realiza la llamada debe anexar un encabezado IPv6 y, opcionalmente, encabezados de aplicación a los datos que se transmiten en sockets IPv6 sin formato creados por BSD. Para usar esta opción, el procesamiento de sockets sin formato debe estar habilitado en la tarea de IP.

- **IP_ADD_MEMBERSHIP**: si se establece, esta opción permite que el socket BSD (se aplica solo a los sockets UDP) se una al grupo de IGMP especificado.

- **IP_DROP_MEMBERSHIP**: si se establece, esta opción permite que el socket BSD (se aplica solo a los sockets UDP) abandone el grupo de IGMP especificado.

- **IP_HDRINCL**: si se establece esta opción, la aplicación que realiza la llamada debe anexar el encabezado IP y, opcionalmente, encabezados de aplicación a los datos que se transmiten en sockets IPv4 sin formato creados en BSD. Para usar esta opción, el procesamiento de sockets sin formato debe estar habilitado en la tarea de IP.

- **IP_RAW_RX_NO_HEADER**: si se desactiva, el encabezado IPv6 se incluye con los datos recibidos para los sockets IPv6 sin formato creados en BSD. Los encabezados IPv6 se quitan de forma predeterminada en los sockets IPv6 sin formato de BSD y la longitud del paquete no incluye el encabezado IPv6.

Si se establece, el encabezado IPv4 se quita de los datos recibidos en sockets sin formato de BSD de tipo IPv4. Los encabezados IPv4 se incluyen de forma predeterminada en los sockets IPv4 sin formato de BSD y la longitud de los paquetes incluye el encabezado IPv4.

Esta opción no tiene ningún efecto en los datos de transmisión de IPv4 ni de IPv6.

## <a name="small-ipv4-example"></a>Ejemplo de IPv4 pequeño

A continuación se describe un ejemplo de cómo usar los servicios de BSD de NetX Duo para redes IPv4. En este ejemplo, el archivo de inclusión *nxd_bsd.h* se agrega en la línea 8. A continuación, la instancia de IP *bsd_ip* y el grupo de paquetes *bsd_pool* se crean como variables globales en las líneas 20 y 21. Tenga en cuenta que en esta demostración se usa un controlador de red de RAM (virtual) *, _nx_ram_network_driver*. En este ejemplo, el cliente y el servidor compartirán la misma dirección IP de una instancia de IP única.

Los subprocesos de cliente y servidor se crean en las líneas 62 y 68. El grupo de paquetes BSD para transmitir paquetes se crea en la línea 78 y se usa en la creación de la instancia de IP en la línea 87. Observe que se asigna la prioridad 1 a la tarea del subproceso de IP en la llamada a *nx_ip_create*. Para un rendimiento óptimo de NetX, este subproceso debe ser la tarea de prioridad más alta definida en el programa.

La instancia de IP se habilita para los servicios ARP y TCP en las líneas 88 y 110, respectivamente. El último requisito antes de poder usar los servicios de BSD es llamar a *bsd_initialize* en la línea 120 para configurar todas las estructuras de datos y los recursos de NetX y ThreadX necesarios para BSD.

A continuación se define la función de entrada del subproceso de servidor. El socket TCP de BSD se crea en la línea 149. La dirección IP y el puerto del servidor se establecen en las líneas 160 a 163. Observe el uso de las macros de orden de bytes de host a red *htonl* y *htons* aplicadas a la dirección IP y al puerto. Esto cumple con la especificación de sockets BSD por la que los datos de varios bytes se envían a los servicios de BSD en el orden de bytes de la red.

Después, el socket del servidor maestro se enlaza al puerto mediante el servicio *bind* en la línea 166. Este es el socket de escucha para las solicitudes de conexión TCP que usan el servicio *listen* en la línea 180. Desde aquí, la función de subproceso de servidor, *thread_server_entry*, se repite en bucle para comprobar si hay eventos de recepción mediante la llamada a *select* en la línea 202. Si un evento de recepción es una solicitud de conexión, lo que se determina comparando la lista preparada para lectura, llama a *accept* en la línea 213. Se asigna un socket de servidor secundario para controlar la solicitud de conexión y se agrega a la lista maestra de sockets de servidor TCP conectados a un cliente en la línea 223. Si no hay ninguna solicitud de conexión nueva, el subproceso de servidor comprueba en todos los sockets conectados actualmente si hay eventos de recepción con el bucle For que empieza en la línea 236. Cuando se detecta un evento de recepción en espera, llama a *send* y a *recv* en ese socket hasta que no se reciben datos (la conexión se cierra en el otro lado) y el socket se cierra con el servicio *soc_close* en la línea 277.

Una vez que se configura el subproceso de servidor, la función de entrada de subprocesos del cliente, *thread_client_entry*, crea un socket en la línea 326 y lo conecta con el socket de servidor TCP mediante la llamada a *connect* en la línea 337. A continuación, se ejecuta en bucle para enviar y recibir paquetes mediante los servicios *send* y *recv*, respectivamente. Cuando no se reciben más datos, cierra el socket en la línea 398 con el servicio *soc_close*. Después de la desconexión, la función de entrada del subproceso del cliente crea un nuevo socket TCP y realiza otra solicitud de conexión en el bucle While iniciado en la línea 321.

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a>Sistema de ejemplo de IPv6 pequeño

En el siguiente programa se describe un ejemplo de cómo usar los servicios de BSD de NetX Duo para redes IPv6. Este ejemplo es muy similar al programa de demostración de IPv4 descrito anteriormente con algunas diferencias importantes.

Los subprocesos de cliente y de servidor, el grupo de paquetes de BSD, la instancia de IP y la inicialización de BSD se producen igual que para los sockets BSD IPv4.

En la función de entrada del subproceso de servidor, *thread_server_entry*, define un par de variables IPv6 usando los tipos de datos *sockaddr_in6* y *NXD_ADDRESS* en las líneas 145 a 148. En realidad, el tipo de datos NXD_ADDRESS puede almacenar tanto tipos de direcciones IPv4 como IPv6.

A continuación, el subproceso de servidor habilita IPv6 e ICMPv6 en la instancia de IP mediante los servicios *nxd_ipv6_enable* y *nxd_icmpv6_enable*, respectivamente, en las líneas 161 y 169. A continuación, las direcciones IP locales y globales del vínculo se registran con la instancia de IP. Esto se hace mediante el servicio *nxd_ipv6_address_set* en las líneas 180 y 195. Después, se suspende el tiempo suficiente como para que la tarea de subproceso de IP complete el protocolo de detección de direcciones duplicadas y registre estas direcciones como direcciones válidas en la llamada a *tx_thread_sleep* en la línea 201.

A continuación, el socket de servidor TCP se crea con el argumento de entrada de tipo de socket AF_INET6 en la línea 204. El puerto y la dirección IPv6 del socket se establecen en las líneas 216 a 221, de nuevo con el uso de las macros *htonl* y *htons* para incluir los datos en el orden de bytes de la red para los servicios de socket BSD. Desde aquí, la función de entrada del subproceso de servidor es prácticamente idéntica al ejemplo de IPv4.

A continuación, se define la función de entrada del subproceso de cliente, *thread_client_entry*. Tenga en cuenta que, dado que el cliente de TCP en este ejemplo comparte la misma instancia de IP y dirección IPv6 que el servidor TCP, no es necesario habilitar los servicios IPv6 o ICMPv6 en la instancia de IP de nuevo. Además, la dirección IPv6 ya está registrada con la instancia de IP. En su lugar, la función de entrada del subproceso de cliente simplemente espera en la línea 368 a que se configure el servidor. Se establecen la dirección y el puerto del servidor mediante las macros de orden de bytes del host a la red en las líneas 387 a 392 y, a continuación, el cliente puede conectarse con el servidor TCP en la línea 412. Tenga en cuenta que los tipos de datos de dirección IP local en las líneas 378 a 383 solo se usan para mostrar los servicios *getsockname* y *getpeername* en las líneas 425 y 434, respectivamente. Dado que los datos proceden de la red, en las líneas 378 a 383 se usan las macros de orden de bytes de red a host.

Después, la función de entrada de subproceso de cliente se repite para crear un socket TCP, realiza una conexión TCP y envía y recibe datos con el servidor TCP hasta que no se reciben más datos; prácticamente igual que el ejemplo de IPv4. A continuación, cierra el socket en la línea 483, se pausa brevemente, crea otro socket TCP y solicita una conexión con el servidor TCP.

Una diferencia importante con el ejemplo de IPv4 es que las llamadas a *socket* especifican un socket IPv6 mediante el argumento de entrada AF_INET6. Otra diferencia importante es que la llamada a *connect* del cliente TCP toma un tipo de datos *sockaddr_in6* y un argumento de longitud establecido en el tamaño del tipo de datos *sockaddr_in6*.

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
