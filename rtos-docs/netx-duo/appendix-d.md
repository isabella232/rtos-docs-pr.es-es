---
title: 'Apéndice D: API de socket compatible con BSD de Azure RTOS NetX Duo'
description: Obtenga información sobre la API de socket compatible con BSD para IPv4 e IPv6.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd43c3efa18dd76f6eb996c84091024f48ad65aa5839958066161080dc02127e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789755"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a>Apéndice D: API de socket compatible con BSD de Azure RTOS NetX Duo

## <a name="bsd-compatible-socket-api"></a>API de socket compatible con BSD 
La API de socket compatible con BSD admite un subconjunto de las llamadas de API de sockets de BSD (con algunas limitaciones) mediante la utilización de primitivas subyacentes de NetX Duo&reg;. Se admiten los protocolos IPv6 e IPv4 y el direccionamiento de red. Esta capa de API de sockets compatible con BSD debe funcionar igual de rápido o ligeramente más rápido que las implementaciones de BSD típicas porque esta API emplea primitivas de NetX Duo internas y omite la innecesaria comprobación de errores de NetX.  

Las opciones configurables permiten que la aplicación host defina el número máximo de sockets, el tamaño máximo de la ventana de TCP y la profundidad de la cola de escucha.

Debido a las restricciones de rendimiento y arquitectura, esta API de sockets compatible con BSD no admite todas las llamadas de sockets de BSD. Además, no todas las opciones de BSD están disponibles para los servicios de BSD, específicamente las siguientes:

  - La función ***select** _ solo funciona con fd_set \_readfds; no se admiten otros argumentos en esta llamada, como writefds o exceptfds.
  - El argumento "int flags" no se admite para las llamadas ***send** _, _*_recv_*_, _*_sendto_*_ y _ *_recvfrom_**. 
  - La API de socket compatible con BSD solo admite un conjunto limitado de llamadas de sockets de BSD.

El código fuente está diseñado para simplificar y solo consta de dos archivos: ***nxd_bsd.c** _ y _*_nxd_bsd.h_*_. La instalación requiere la adición de estos dos archivos al proyecto de compilación (no la biblioteca de NetX) y la creación de la aplicación host que usará las llamadas de servicio de socket de BSD. El archivo _ *_nxd_bsd.h_** también se debe incluir en el código fuente de la aplicación. Los archivos de demostración de ejemplo para las aplicaciones basadas en IPv4 e IPv6 se incluyen con la distribución, que está disponible de forma gratuita con NetX Duo. Puede encontrar más información en los archivos de ayuda y Léame que se incluyen con el paquete de la API de sockets compatible con BSD.

La API de sockets compatible con BSD admite las siguientes llamadas a la API de sockets de BSD:

```c
INT     bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool, CHAR
        *bsd_memory_not_used);
```
```c
INT     getpeername( INT sockID, struct sockaddr *remoteAddress, INT
        *addressLength);
```
```c
INT     getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);
```
```c
INT     recvfrom(INT sockID, CHAR *buffer, INT buffersize, INT flags,struct sockaddr
        *fromAddr, INT *fromAddrLen);
```
```c        
INT     recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);
```
```c
INT     sendto(INT sockID, CHAR *msg, INT msgLength, INT flags, struct sockaddr
        *destAddr, INT destAddrLen);
```
```c        
INT     send(INT sockID, const CHAR *msg, INT msgLength, INT flags);
```
```c
INT     accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);
```
```c
INT     listen(INT sockID, INT backlog);
```
```c
INT     bind (INT sockID, struct sockaddr *localAddress, INT addressLength);
```
```c
INT     connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);
```
```c
INT     socket( INT protocolFamily, INT type, INT protocol);
```
```c
INT     soc_close ( INT sockID);
```
```c
INT     select(INT nfds, fd_set *readfds, fd_set *writefds, fd_set *exceptfds, struct
        timeval *timeout);
```
```c
VOID    FD_SET(INT fd, fd_set *fdset);
```
```c
VOID    FD_CLR(INT fd, fd_set *fdset);
```
```c
INT     FD_ISSET(INT fd, fd_set *fdset);
```
```c
VOID    FD_ZERO(fd_set *fdset);
```