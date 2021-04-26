---
title: 'Apéndice D: API de socket compatible con BSD de Azure RTOS NetX Duo'
description: Obtenga información sobre la API de socket compatible con BSD para IPv4 e IPv6.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 82439184d9facb6ddcc08ce81bc51182d7f34429
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814874"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a><span data-ttu-id="50ecb-103">Apéndice D: API de socket compatible con BSD de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="50ecb-103">Appendix D - Azure RTOS NetX Duo BSD-Compatible Socket API</span></span>

## <a name="bsd-compatible-socket-api"></a><span data-ttu-id="50ecb-104">API de socket compatible con BSD</span><span class="sxs-lookup"><span data-stu-id="50ecb-104">BSD-Compatible Socket API</span></span> 
<span data-ttu-id="50ecb-105">La API de socket compatible con BSD admite un subconjunto de las llamadas de API de sockets de BSD (con algunas limitaciones) mediante la utilización de primitivas subyacentes de NetX Duo&reg;.</span><span class="sxs-lookup"><span data-stu-id="50ecb-105">The BSD-Compatible Socket API supports a subset of the BSD Sockets API calls (with some limitations) by utilizing NetX Duo&reg; primitives underneath.</span></span> <span data-ttu-id="50ecb-106">Se admiten los protocolos IPv6 e IPv4 y el direccionamiento de red.</span><span class="sxs-lookup"><span data-stu-id="50ecb-106">Both IPv6 and IPv4 protocols and network addressing are supported.</span></span> <span data-ttu-id="50ecb-107">Esta capa de API de sockets compatible con BSD debe funcionar igual de rápido o ligeramente más rápido que las implementaciones de BSD típicas porque esta API emplea primitivas de NetX Duo internas y omite la innecesaria comprobación de errores de NetX.</span><span class="sxs-lookup"><span data-stu-id="50ecb-107">This BSD-Compatible Sockets API layer should perform as fast or slightly faster than typical BSD implementations because this API utilizes internal NetX Duo primitives and bypasses unnecessary NetX error checking.</span></span>  

<span data-ttu-id="50ecb-108">Las opciones configurables permiten que la aplicación host defina el número máximo de sockets, el tamaño máximo de la ventana de TCP y la profundidad de la cola de escucha.</span><span class="sxs-lookup"><span data-stu-id="50ecb-108">Configurable options allow the host application to define the maximum number of sockets, TCP maximum window size, and depth of listen queue.</span></span>

<span data-ttu-id="50ecb-109">Debido a las restricciones de rendimiento y arquitectura, esta API de sockets compatible con BSD no admite todas las llamadas de sockets de BSD.</span><span class="sxs-lookup"><span data-stu-id="50ecb-109">Due to performance and architecture constraints, this BSD-Compatible Sockets API does not support all BSD Sockets calls.</span></span> <span data-ttu-id="50ecb-110">Además, no todas las opciones de BSD están disponibles para los servicios de BSD, específicamente las siguientes:</span><span class="sxs-lookup"><span data-stu-id="50ecb-110">In addition, not all BSD options are available for the BSD services, specifically the following:</span></span>

  - <span data-ttu-id="50ecb-111">La función \***select** _ solo funciona con fd_set \_readfds; no se admiten otros argumentos en esta llamada, como writefds o exceptfds.</span><span class="sxs-lookup"><span data-stu-id="50ecb-111">\***select** _ call works with only fd_set \_readfds, other arguments in this call e.g., writefds, exceptfds are not supported.</span></span>
  - <span data-ttu-id="50ecb-112">El argumento "int flags" no se admite para las llamadas ***send** _, _*_recv_*_, _*_sendto_\*_ y _ \*_recvfrom_\*\*.</span><span class="sxs-lookup"><span data-stu-id="50ecb-112">The "int flags" argument is not supported for ***send** _, _*_recv_*_, _*_sendto,_*_ and _ *_recvfrom_** calls.</span></span> 
  - <span data-ttu-id="50ecb-113">La API de socket compatible con BSD solo admite un conjunto limitado de llamadas de sockets de BSD.</span><span class="sxs-lookup"><span data-stu-id="50ecb-113">The BSD-Compatible Socket API supports only limited set of BSD Sockets calls.</span></span>

<span data-ttu-id="50ecb-114">El código fuente está diseñado para simplificar y solo consta de dos archivos: ***nxd_bsd.c** _ y _*_nxd_bsd.h_\*_.</span><span class="sxs-lookup"><span data-stu-id="50ecb-114">The source code is designed for simplicity and is comprised of only two files, ***nxd_bsd.c** _ and _*_nxd_bsd.h_\*_.</span></span> <span data-ttu-id="50ecb-115">La instalación requiere la adición de estos dos archivos al proyecto de compilación (no la biblioteca de NetX) y la creación de la aplicación host que usará las llamadas de servicio de socket de BSD.</span><span class="sxs-lookup"><span data-stu-id="50ecb-115">Installation requires adding these two files to the build project (not the NetX library) and creating the host application which will use BSD Socket service calls.</span></span> <span data-ttu-id="50ecb-116">El archivo _ *_nxd_bsd.h_*\* también se debe incluir en el código fuente de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="50ecb-116">The _ *_nxd_bsd.h_*\* file must also be included in your application source.</span></span> <span data-ttu-id="50ecb-117">Los archivos de demostración de ejemplo para las aplicaciones basadas en IPv4 e IPv6 se incluyen con la distribución, que está disponible de forma gratuita con NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="50ecb-117">Sample demo files for both IPv4 and IPv6  based applications are included with the distribution which is freely available with NetX Duo.</span></span> <span data-ttu-id="50ecb-118">Puede encontrar más información en los archivos de ayuda y Léame que se incluyen con el paquete de la API de sockets compatible con BSD.</span><span class="sxs-lookup"><span data-stu-id="50ecb-118">Further details are available in the help and Readme files bundled with the BSDCompatible Socket API package.</span></span>

<span data-ttu-id="50ecb-119">La API de sockets compatible con BSD admite las siguientes llamadas a la API de sockets de BSD:</span><span class="sxs-lookup"><span data-stu-id="50ecb-119">The BSD-Compatible Sockets API supports the following BSD Sockets API calls:</span></span>

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