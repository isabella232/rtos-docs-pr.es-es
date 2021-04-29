---
title: 'Apéndice D: API de socket compatible con BSD de Azure RTOS NetX'
description: Obtenga información sobre la API de socket compatible con BSD para IPv4.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9062e27d8f447ac8d36e7a09afee5ac14f86f8c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815318"
---
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a><span data-ttu-id="587b0-103">Apéndice D: API de socket compatible con BSD de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="587b0-103">Appendix D - Azure RTOS NetX BSD-Compatible Socket API</span></span>

## <a name="bsd-compatible-socket-api"></a><span data-ttu-id="587b0-104">API de socket compatible con BSD</span><span class="sxs-lookup"><span data-stu-id="587b0-104">BSD-Compatible Socket API</span></span>

<span data-ttu-id="587b0-105">La API de socket compatible con BSD admite un subconjunto de las llamadas de API de sockets de BSD (con algunas limitaciones) mediante la utilización de primitivas subyacentes de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="587b0-105">The BSD-Compatible Socket API supports a subset of the BSD Sockets API calls (with some limitations) by utilizing Azure RTOS NetX primitives underneath.</span></span> <span data-ttu-id="587b0-106">Se admiten los protocolos IPv4 y el direccionamiento de red.</span><span class="sxs-lookup"><span data-stu-id="587b0-106">IPv4 protocols and network addressing are supported.</span></span> <span data-ttu-id="587b0-107">Esta capa de API de sockets compatible con BSD debe funcionar igual de rápido o ligeramente más rápido que las implementaciones de BSD típicas porque esta API emplea primitivas de NetX internas y omite la innecesaria comprobación de errores de NetX.</span><span class="sxs-lookup"><span data-stu-id="587b0-107">This BSD-Compatible Sockets API layer should perform as fast or slightly faster than typical BSD implementations because this API utilizes internal NetX primitives and bypasses unnecessary NetX error checking.</span></span>

<span data-ttu-id="587b0-108">Las opciones configurables permiten que la aplicación host defina el número máximo de sockets, el tamaño máximo de la ventana de TCP y la profundidad de la cola de escucha.</span><span class="sxs-lookup"><span data-stu-id="587b0-108">Configurable options allow the host application to define the maximum number of sockets, TCP maximum window size, and depth of listen queue.</span></span>

<span data-ttu-id="587b0-109">Debido a las restricciones de rendimiento y arquitectura, esta API de sockets compatible con BSD no admite todas las llamadas de sockets de BSD.</span><span class="sxs-lookup"><span data-stu-id="587b0-109">Due to performance and architecture constraints, this BSD-Compatible Sockets API does not support all BSD Sockets calls.</span></span> <span data-ttu-id="587b0-110">Además, no todas las opciones de BSD están disponibles para los servicios de BSD, específicamente las siguientes:</span><span class="sxs-lookup"><span data-stu-id="587b0-110">In addition, not all BSD options are available for the BSD services, specifically the following:</span></span>

- <span data-ttu-id="587b0-111">La función ***select** _ solo funciona con _fd_set \*readfds*, no se admiten otros argumentos en esta llamada, por ejemplo, *writefds* o *exceptfds*.</span><span class="sxs-lookup"><span data-stu-id="587b0-111">The ***select** _ function works with only _fd_set \*readfds*, other arguments in this call e.g., *writefds*, *exceptfds* are not supported.</span></span>
- <span data-ttu-id="587b0-112">El argumento *int flags* no se admite para las funciones ***send** _, _*_recv_*_, _*_sendto_\*_ y _ *_recvfrom_* \*.</span><span class="sxs-lookup"><span data-stu-id="587b0-112">The *int flags* argument is not supported for the ***send** _, _*_recv_*_, _*_sendto,_*_ and _ *_recvfrom_** functions.</span></span> <span data-ttu-id="587b0-113">La API de socket compatible con BSD solo admite un conjunto limitado de llamadas de sockets de BSD.</span><span class="sxs-lookup"><span data-stu-id="587b0-113">The BSD-Compatible Socket API supports only limited set of BSD Sockets calls.</span></span>

<span data-ttu-id="587b0-114">El código fuente está diseñado para simplificar y solo consta de dos archivos: ***nx_bsd.c** _ y _*_nx_bsd.h_\*_.</span><span class="sxs-lookup"><span data-stu-id="587b0-114">The source code is designed for simplicity and is comprised of only two files,***nx_bsd.c** _ and _*_nx_bsd.h_\*_.</span></span> <span data-ttu-id="587b0-115">La instalación requiere la adición de estos dos archivos al proyecto de compilación (no la biblioteca de NetX) y la creación de la aplicación host que usará las llamadas de servicio de socket de BSD.</span><span class="sxs-lookup"><span data-stu-id="587b0-115">Installation requires adding these two files to the build project (not the NetX library) and creating the host application which will use BSD Socket service calls.</span></span> <span data-ttu-id="587b0-116">El archivo _ *_nx_bsd.h_*\* también se debe incluir en el código fuente de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="587b0-116">The _ *_nx_bsd.h_*\* file must also be included in your application source.</span></span> <span data-ttu-id="587b0-117">Los archivos de demostración de ejemplo se incluyen con la distribución que está disponible gratuitamente con NetX.</span><span class="sxs-lookup"><span data-stu-id="587b0-117">Sample demo files are included with the distribution which is freely available with NetX.</span></span> <span data-ttu-id="587b0-118">Puede encontrar más información en los archivos de ayuda **417** y el archivo Léame de la API de socket compatible con BSD que se incluyen con el paquete de la API de socket compatible con BSD.</span><span class="sxs-lookup"><span data-stu-id="587b0-118">Further details are available in the help BSD-Compatible Socket API **417** and Readme files bundled with the BSD-Compatible Socket API package.</span></span>

<span data-ttu-id="587b0-119">La API de sockets compatible con BSD admite las siguientes llamadas a la API de sockets de BSD:</span><span class="sxs-lookup"><span data-stu-id="587b0-119">The BSD-Compatible Sockets API supports the following BSD Sockets API calls:</span></span>

```C
*INT bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool,
    CHAR *bsd_memory_not_used);*

*INT getpeername( INT sockID, struct sockaddr *remoteAddress, INT *addressLength);*

*INT getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);*

*INT recvfrom(INT sockID, CHAR *buffer, INT buffersize,
    INT flags,struct sockaddr *fromAddr, INT *fromAddrLen);*

*INT recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);*

*INT sendto(INT sockID, CHAR *msg, INT msgLength, INT flags,
    struct sockaddr *destAddr, INT destAddrLen);*

*INT send(INT sockID, const CHAR *msg, INT msgLength, INT flags);*

 *INT accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);*

*INT listen(INT sockID, INT backlog);*

*INT bind (INT sockID, struct sockaddr *localAddress, INT addressLength);*

*INT connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);*

*INT socket( INT protocolFamily, INT type, INT protocol);*

*INT soc_close ( INT sockID);*

*INT select(INT nfds, fd_set *readfds, fd_set *writefds,
    fd_set *exceptfds, struct timeval *timeout);*

*VOID FD_SET(INT fd, fd_set *fdset);*

*VOID FD_CLR(INT fd, fd_set *fdset);*

*INT FD_ISSET(INT fd, fd_set *fdset);*

*VOID FD_ZERO(fd_set *fdset);*

```
