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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="f86f8-103">Capítulo 2: Instalación y uso de BSD de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f86f8-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="f86f8-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente BSD de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="f86f8-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="f86f8-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="f86f8-105">Product Distribution</span></span>

<span data-ttu-id="f86f8-106">BSD de Azure RTOS NetX Duo se puede obtener desde nuestro repositorio de código fuente público en [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span><span class="sxs-lookup"><span data-stu-id="f86f8-106">Azure RTOS NetX Duo BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="f86f8-107">El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="f86f8-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="f86f8-108">**nxd_bsd.h**: archivo de encabezado para BSD de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f86f8-108">**nxd_bsd.h**: Header file for NetX Duo BSD</span></span>
- <span data-ttu-id="f86f8-109">**nxd_bsd.c**: archivo de código fuente para BSD de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f86f8-109">**nxd_bsd.c**: C Source file for NetX Duo BSD</span></span>
- <span data-ttu-id="f86f8-110">**nxd_bsd.pdf**: manual de usuario de BSD de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f86f8-110">**nxd_bsd.pdf**: User Guide for NetX Duo BSD</span></span>

<span data-ttu-id="f86f8-111">Archivos de demostración:</span><span class="sxs-lookup"><span data-stu-id="f86f8-111">Demo files:</span></span>

- <span data-ttu-id="f86f8-112">**bsd_demo_udp.c**</span><span class="sxs-lookup"><span data-stu-id="f86f8-112">**bsd_demo_udp.c**</span></span>
- <span data-ttu-id="f86f8-113">**bsd_demo_tcp.c**</span><span class="sxs-lookup"><span data-stu-id="f86f8-113">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="f86f8-114">**bsd_demo_raw.c**</span><span class="sxs-lookup"><span data-stu-id="f86f8-114">**bsd_demo_raw.c**</span></span>

## <a name="netx-duo-bsd-installation"></a><span data-ttu-id="f86f8-115">Instalación de BSD de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f86f8-115">NetX Duo BSD Installation</span></span>

<span data-ttu-id="f86f8-116">Para usar BSD de NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="f86f8-116">In order to use NetX Duo BSD the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="f86f8-117">Por ejemplo, si NetX Duo está instalado en el directorio " *\threadx\arm7\green*", los archivos *nxd_bsd.h* y *nxd_bsd.c* deben copiarse en ese mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="f86f8-117">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_bsd.h* and *nxd_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a><span data-ttu-id="f86f8-118">Compilación de los componentes ThreadX y NetX Duo de una aplicación BSD</span><span class="sxs-lookup"><span data-stu-id="f86f8-118">Building the ThreadX and NetX Duo components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="f86f8-119">ThreadX</span><span class="sxs-lookup"><span data-stu-id="f86f8-119">ThreadX</span></span>

<span data-ttu-id="f86f8-120">La biblioteca de ThreadX debe definir `bsd_errno` en el almacenamiento local para el subproceso.</span><span class="sxs-lookup"><span data-stu-id="f86f8-120">The ThreadX library must define `bsd_errno` in the thread local storage.</span></span> <span data-ttu-id="f86f8-121">Se recomienda el siguiente procedimiento:</span><span class="sxs-lookup"><span data-stu-id="f86f8-121">We recommend the following procedure:</span></span>

1. <span data-ttu-id="f86f8-122">En *tx_port.h*, establezca una de las macros TX_THREAD_EXTENSION como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="f86f8-122">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. <span data-ttu-id="f86f8-123">Recompile la biblioteca de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="f86f8-123">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="f86f8-124">Si TX_THREAD_EXTENSION_3 ya está en uso, el usuario puede utilizar una de las otras macros TX_THREAD_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="f86f8-124">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx-duo"></a><span data-ttu-id="f86f8-125">NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f86f8-125">NetX Duo</span></span>

<span data-ttu-id="f86f8-126">Antes de usar los servicios de BSD de NetX Duo, debe compilarse la biblioteca de NetX Duo con NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definido.</span><span class="sxs-lookup"><span data-stu-id="f86f8-126">Before using NetX Duo BSD Services, the NetX Duo library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined.</span></span> <span data-ttu-id="f86f8-127">De forma predeterminada, no está definido.</span><span class="sxs-lookup"><span data-stu-id="f86f8-127">By default it is not defined.</span></span> <span data-ttu-id="f86f8-128">Si se van a utilizar los sockets BSD sin formato, la biblioteca de NetX Duo debe compilarse con NX_ENABLE_IP_RAW_PACKET_FILTER definido.</span><span class="sxs-lookup"><span data-stu-id="f86f8-128">If the BSD raw sockets are to be used, the NetX Duo library must be built with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span>

## <a name="using-netx-duo-bsd"></a><span data-ttu-id="f86f8-129">Uso de BSD de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f86f8-129">Using NetX Duo BSD</span></span>

<span data-ttu-id="f86f8-130">Un proyecto de aplicación BSD de NetX Duo debe incluir *nxd_bsd.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar los servicios de BSD especificados más adelante en este manual.</span><span class="sxs-lookup"><span data-stu-id="f86f8-130">A NetX Duo BSD application project must include *nxd_bsd.h* after it includes *tx_api.h* and *nx_api.h* to be able to use BSD services specified later in this guide.</span></span> <span data-ttu-id="f86f8-131">La aplicación también debe incluir *nxd_bsd.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="f86f8-131">The application must also include *nxd_bsd.c* in the build process.</span></span> <span data-ttu-id="f86f8-132">Este archivo se debe compilar de la misma manera que otros archivos de la aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f86f8-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="f86f8-133">Esto es todo lo que se necesita para usar BSD de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="f86f8-133">This is all that is required to use NetX Duo BSD.</span></span>

<span data-ttu-id="f86f8-134">Para poder usar los servicios de BSD de NetX Duo, la aplicación debe crear una instancia de IP, crear un grupo de paquetes para la capa BSD desde la que asignar paquetes, asignar espacio de memoria para la pila de subprocesos BSD internos y especificar la prioridad del subproceso BSD interno.</span><span class="sxs-lookup"><span data-stu-id="f86f8-134">To utilize NetX Duo BSD services, the application must create an IP instance, create a packet pool for the BSD layer to allocate packets from, allocate memory space for the internal BSD thread stack, and specify the priority of the internal BSD thread.</span></span> <span data-ttu-id="f86f8-135">La capa BSD se inicializa llamando a *bsd_initialize* y pasando los parámetros.</span><span class="sxs-lookup"><span data-stu-id="f86f8-135">The BSD layer is initialized by calling *bsd_initialize* and passing in the parameters.</span></span> <span data-ttu-id="f86f8-136">Esto se muestra en los pequeños ejemplos que se incluyen más adelante en este documento, pero el prototipo se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="f86f8-136">This is demonstrated in the "Small Examples" later in this document but the prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

<span data-ttu-id="f86f8-137">default_ip es la instancia de IP en la que opera la capa BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-137">The default_ip is the IP instance the BSD layer operates on.</span></span> <span data-ttu-id="f86f8-138">Los servicios de BSD usan el parámetro default_pool como origen para asignar paquetes.</span><span class="sxs-lookup"><span data-stu-id="f86f8-138">The default_pool is used by the BSD services to allocate packets from.</span></span> <span data-ttu-id="f86f8-139">Los dos parámetros siguientes, bsd_thread_stack_area y bsd_thread_stack_size, definen el área de pila usada por el subproceso BSD interno y el último parámetro, bsd_thread_priority, establece la prioridad del subproceso.</span><span class="sxs-lookup"><span data-stu-id="f86f8-139">The next two parameters: bsd_thread_stack_area, bsd_thread_stack_size defines the stack area used by the internal BSD thread, and the last parameter, bsd_thread_priority, sets the priority of the thread.</span></span>

## <a name="netx-duo-bsd-raw-socket-support"></a><span data-ttu-id="f86f8-140">Compatibilidad con sockets sin formato de BSD de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f86f8-140">NetX Duo BSD Raw Socket Support</span></span>

<span data-ttu-id="f86f8-141">BSD de NetX Duo también admite sockets sin formato.</span><span class="sxs-lookup"><span data-stu-id="f86f8-141">NetX Duo BSD also supports raw sockets.</span></span> <span data-ttu-id="f86f8-142">Para usar sockets sin formato en BSD de NetX Duo, la biblioteca de NetX Duo se debe compilar con NX_ENABLE_IP_RAW_PACKET_FILTER definido.</span><span class="sxs-lookup"><span data-stu-id="f86f8-142">To use raw sockets in NetX Duo BSD, the NetX Duo library must be compiled with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span> <span data-ttu-id="f86f8-143">De forma predeterminada, no está definido.</span><span class="sxs-lookup"><span data-stu-id="f86f8-143">By default it is not defined.</span></span> <span data-ttu-id="f86f8-144">A continuación, la aplicación debe habilitar el procesamiento de sockets sin formato para una instancia de IP creada anteriormente mediante una llamada a *nx_ip_raw_packet_enable.*</span><span class="sxs-lookup"><span data-stu-id="f86f8-144">The application must then enable raw socket processing for a previously created IP instance by calling *nx_ip_raw_packet_enable.*</span></span>

<span data-ttu-id="f86f8-145">Para crear un socket sin formato en BSD de NetX Duo, la aplicación usa el servicio *socket* de creación de sockets y especifica la familia de protocolos, el tipo de socket y el protocolo:</span><span class="sxs-lookup"><span data-stu-id="f86f8-145">To create a raw socket in NetX Duo BSD, the application uses the socket create service *socket* and specifies the protocol family, socket type and protocol:</span></span>

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

<span data-ttu-id="f86f8-146">protocolFamily es AF_INET para sockets IPv4 o AF_INET6 para sockets IPv6, suponiendo que IPv6 está habilitado en la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-146">protocolFamily is AF_INET for IPv4 sockets, or AF_INET6 for IPv6 sockets, assuming IPv6 is enabled on the IP instance.</span></span> <span data-ttu-id="f86f8-147">El parámetro socket_type debe establecerse en SOCK_RAW.</span><span class="sxs-lookup"><span data-stu-id="f86f8-147">The socket_type must be set to SOCK_RAW.</span></span> <span data-ttu-id="f86f8-148">El parámetro protocol es específico de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f86f8-148">protocol is application specific.</span></span>

<span data-ttu-id="f86f8-149">Para enviar y recibir paquetes sin formato, así como cerrar un socket sin formato, la aplicación usa normalmente los mismos servicios de BSD que para UDP, por ejemplo, *sendto, recvfrom, select* y *soc_close*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-149">To send and receive raw packets as well as close a raw socket, the application typically uses the same BSD services as for UDP e.g. *sendto, recvfrom, select* and *soc_close*.</span></span> <span data-ttu-id="f86f8-150">Los sockets sin formato no admiten los servicios *accept* ni *listen* de BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-150">Raw sockets do not support either *accept* or *listen* BSD services.</span></span>

- <span data-ttu-id="f86f8-151">De forma predeterminada, los datos sin procesar de IPv4 recibidos incluyen el encabezado IPv4.</span><span class="sxs-lookup"><span data-stu-id="f86f8-151">By default, received IPv4 raw data includes the IPv4 header.</span></span>  <span data-ttu-id="f86f8-152">Por el contrario, los datos sin procesar IPv6 recibidos no incluyen el encabezado IPv6.</span><span class="sxs-lookup"><span data-stu-id="f86f8-152">Conversely, received IPv6 raw data does not include the IPv6 header.</span></span>

- <span data-ttu-id="f86f8-153">De forma predeterminada, al enviar paquetes IPv6 o IPv4 sin formato, la capa de contenedor de BSD agrega el encabezado IPv6 o IPv4 antes de enviar los datos.</span><span class="sxs-lookup"><span data-stu-id="f86f8-153">By default, when sending either raw IPv6 or IPv4 packets, the BSD wrapper layer adds the IPv6 or IPv4 header before sending the data.</span></span>

<span data-ttu-id="f86f8-154">BSD de NetX Duo es compatible con opciones adicionales de sockets sin formato, como IP_RAW_RX_NO_HEADER, IP_HDRINCL e IP_RAW_IPV6_HDRINCL.</span><span class="sxs-lookup"><span data-stu-id="f86f8-154">NetX Duo BSD supports additional raw socket options, including IP_RAW_RX_NO_HEADER, IP_HDRINCL and IP_RAW_IPV6_HDRINCL.</span></span>

<span data-ttu-id="f86f8-155">Si se establece IP_RAW_RX_NO_HEADER, se quita el encabezado IPv4 para que los datos recibidos no lo incluyan y la longitud del mensaje notificado no incluye el encabezado IPv4.</span><span class="sxs-lookup"><span data-stu-id="f86f8-155">If IP_RAW_RX_NO_HEADER is set, the IPv4 header is removed so that the received data does not contain the IPv4 header, and the reported message length does not include the IPv4 header.</span></span>  <span data-ttu-id="f86f8-156">En el caso de los sockets IPv6, de forma predeterminada, la recepción de sockets sin formato no incluye el encabezado IPv6, lo que equivale a tener establecida la opción IP_RAW_RX_NO_HEADER.</span><span class="sxs-lookup"><span data-stu-id="f86f8-156">For IPv6 sockets, by default the raw socket receive does not include IPv6 header, equivalent to having the IP_RAW_RX_NO_HEADER option set.</span></span> <span data-ttu-id="f86f8-157">La aplicación puede usar el servicio *setsockopt* para desactivar la opción IP_RAW_RX_NO_HEADER. Una vez desactivada esta opción, los datos de IPv6 sin formato recibidos incluirían el encabezado IPv6 y en la longitud del mensaje indicado se incluirá este encabezado.</span><span class="sxs-lookup"><span data-stu-id="f86f8-157">Application may use the *setsockopt* service to clear the IP_RAW_RX_NO_HEADER option, Once the IP_RAW_RX_NO_HEADER option is cleared, the received IPv6 raw data would include the IPv6 header, and the reported message length includes the IPv6 header.</span></span>

<span data-ttu-id="f86f8-158">Esta opción no tiene ningún efecto en los datos transmitidos de IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="f86f8-158">This option has no effect on IPv4 or IPv6 transmitted data.</span></span>

<span data-ttu-id="f86f8-159">Si se establece IP_HDRINCL, la aplicación incluye el encabezado IPv4 al enviar datos.</span><span class="sxs-lookup"><span data-stu-id="f86f8-159">If IP_HDRINCL is set, the application includes the IPv4 header when sending data.</span></span>  <span data-ttu-id="f86f8-160">Esta opción no tiene ningún efecto en la transmisión IPv6 y no está definida de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="f86f8-160">This option has no effect on IPv6 transmission and is not defined by default.</span></span> <span data-ttu-id="f86f8-161">Si se establece IP_RAW_IPV6_HDRINCL, la aplicación incluye el encabezado IPv6 al enviar datos.</span><span class="sxs-lookup"><span data-stu-id="f86f8-161">If IP_RAW_IPV6_HDRINCL is set, the application includes the IPv6 header when sending data.</span></span>  <span data-ttu-id="f86f8-162">Esta opción no tiene ningún efecto en la transmisión IPv4 y no está definida de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="f86f8-162">This option has no effect on IPv4 transmission and is not defined by default.</span></span>

<span data-ttu-id="f86f8-163">IP_HDRINCL e IP_RAW_IPV6_HDRINCL no tienen ningún efecto en la recepción de IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="f86f8-163">IP_HDRINCL and IP_RAW_IPV6_HDRINCL have no effect on IPv4 or IPv6 reception.</span></span>

> [!NOTE]
> <span data-ttu-id="f86f8-164">La especificación de sockets de BSD 4.3 indica que el kernel debe copiar el paquete sin formato en cada búfer de recepción del socket.</span><span class="sxs-lookup"><span data-stu-id="f86f8-164">The BSD 4.3 Socket specification specifies that the kernel must copy the raw packet to each socket receive buffer.</span></span> <span data-ttu-id="f86f8-165">Sin embargo, en BSD de NetX Duo, si se crean varios sockets que comparten el mismo protocolo, no se define el comportamiento.</span><span class="sxs-lookup"><span data-stu-id="f86f8-165">However in NetX Duo BSD, if multiple sockets are created sharing the same protocol, the behavior is undefined.</span></span>

## <a name="netx-duo-bsd-raw-packet-support"></a><span data-ttu-id="f86f8-166">Compatibilidad con paquetes sin formato de BSD de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f86f8-166">NetX Duo BSD Raw Packet Support</span></span>

<span data-ttu-id="f86f8-167">Para habilitar la compatibilidad con paquetes sin formato para PPPoE, se debe crear un contenedor de BSD de NetX Duo con NX_BSD_RAW_PPPOE_SUPPORT habilitado.</span><span class="sxs-lookup"><span data-stu-id="f86f8-167">To enable the raw packet support for PPPoE, NetX Duo BSD wrapper needs to be built with NX_BSD_RAW_PPPOE_SUPPORT enabled.</span></span>

<span data-ttu-id="f86f8-168">El siguiente comando crea un socket BSD para administrar paquetes de PPPoE sin formato:</span><span class="sxs-lookup"><span data-stu-id="f86f8-168">The following command creates a BSD socket to handle PPPoE raw packets:</span></span>

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

<span data-ttu-id="f86f8-169">La implementación de BSD actual solo admite dos tipos de protocolo de la familia AF_PACKET:</span><span class="sxs-lookup"><span data-stu-id="f86f8-169">The current BSD implementation only supports two protocol types in AF_PACKET family</span></span>

- <span data-ttu-id="f86f8-170">`ETHERTYPE_PPPOE_DISC`: paquetes de detección de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="f86f8-170">`ETHERTYPE_PPPOE_DISC`: PPPoE Discovery packets.</span></span> <span data-ttu-id="f86f8-171">En la trama de datos MAC, los paquetes de detección tienen el tipo de trama Ethernet 0x8863.</span><span class="sxs-lookup"><span data-stu-id="f86f8-171">In the MAC data frame, the Discovery packets have the Ethernet frame type 0x8863.</span></span>

- <span data-ttu-id="f86f8-172">`ETHERTYPE_PPPOE_SESS`: paquetes de sesión PPP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-172">`ETHERTYPE_PPPOE_SESS`: PPP Session packets.</span></span> <span data-ttu-id="f86f8-173">En la trama de datos MAC, los paquetes de sesión tienen el tipo de trama Ethernet 0x8864.</span><span class="sxs-lookup"><span data-stu-id="f86f8-173">In the MAC data frame, the Session packets have the Ethernet frame type 0x8864.</span></span>

<span data-ttu-id="f86f8-174">La estructura `sockaddr_ll` se usa para especificar los parámetros al enviar o recibir marcos PPPoE.</span><span class="sxs-lookup"><span data-stu-id="f86f8-174">The structure `sockaddr_ll` is used to specify parameters when sending or receiving PPPoE frames.</span></span>

<span data-ttu-id="f86f8-175">`struct sockaddr_ll` se declara como:</span><span class="sxs-lookup"><span data-stu-id="f86f8-175">`struct sockaddr_ll` is declared as:</span></span>

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
> <span data-ttu-id="f86f8-176">`sendto()` o `recvfrom()` no utilizan todos los campos de la estructura.</span><span class="sxs-lookup"><span data-stu-id="f86f8-176">Not every field in the structure is used by `sendto()` or `recvfrom()`.</span></span> <span data-ttu-id="f86f8-177">Consulte la descripción siguiente sobre cómo configurar `sockaddr_ll` para el envío y la recepción de paquetes PPPoE.</span><span class="sxs-lookup"><span data-stu-id="f86f8-177">See the description below on how to set up the `sockaddr_ll` for sending and receiving PPPoE packets.</span></span>

<span data-ttu-id="f86f8-178">El socket creado en la familia AF_PACKET se puede usar para enviar tanto paquetes de detección de PPPoE o paquetes de sesión de PPP, independientemente del protocolo especificado.</span><span class="sxs-lookup"><span data-stu-id="f86f8-178">Socket created in the AF_PACKET family can be used to send either PPPoE Discovery packets or PPP session packets, regardless of the protocol specified.</span></span> <span data-ttu-id="f86f8-179">Al transmitir un paquete PPPoE, la aplicación debe preparar el búfer que incluye el marco PPPoE con el formato correcto, incluidos los encabezados MAC (dirección MAC de destino, dirección MAC de origen y tipo de marco). El tamaño del búfer incluye el encabezado Ethernet de 14 bytes.</span><span class="sxs-lookup"><span data-stu-id="f86f8-179">When transmitting a PPPoE packet, application must prepare the buffer that includes properly formatted PPPoE frame, including the MAC headers (Destination MAC address, source MAC address, and frame type.) The size of the buffer includes the 14-byte Ethernet header.</span></span>

<span data-ttu-id="f86f8-180">En la estructura `sockaddr_ll`, `sll_ifindex` se usa para indicar la interfaz física que se va a utilizar para enviar este paquete.</span><span class="sxs-lookup"><span data-stu-id="f86f8-180">The `sockaddr_ll` struct, the `sll_ifindex` is used to indicate the physical interface to be used for sending this packet.</span></span> <span data-ttu-id="f86f8-181">El resto de los campos de la estructura no se utiliza.</span><span class="sxs-lookup"><span data-stu-id="f86f8-181">The rest of the fields in the structure are not used.</span></span> <span data-ttu-id="f86f8-182">El proceso interno de BSD omite los valores establecidos en los campos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="f86f8-182">Values set to the unused fields are ignored by the BSD internal process.</span></span>

<span data-ttu-id="f86f8-183">En el siguiente bloque de código se muestra cómo transmitir un paquete PPPoE:</span><span class="sxs-lookup"><span data-stu-id="f86f8-183">The following code block illustrates how to transmit a PPPoE packet:</span></span>

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

<span data-ttu-id="f86f8-184">El valor devuelto indica el número de bytes transmitidos.</span><span class="sxs-lookup"><span data-stu-id="f86f8-184">The return value indicates the number of bytes transmitted.</span></span> <span data-ttu-id="f86f8-185">Dado que los paquetes PPPoE están basados en mensajes, en una transmisión correcta, el número de bytes enviados coincide con el tamaño del paquete, incluido el encabezado Ethernet de 14 bytes.</span><span class="sxs-lookup"><span data-stu-id="f86f8-185">Since PPPoE packets are message-based, on a successful transmission, the number of bytes sent matches the size of the packet, including the 14-byte Ethernet header.</span></span>

<span data-ttu-id="f86f8-186">Los paquetes PPPoE se pueden recibir mediante `recvfrom()`.</span><span class="sxs-lookup"><span data-stu-id="f86f8-186">PPPoE packets can be received using `recvfrom()`.</span></span> <span data-ttu-id="f86f8-187">El búfer de recepción debe ser lo suficientemente grande como para incluir un mensaje con el tamaño de MTU de Ethernet.</span><span class="sxs-lookup"><span data-stu-id="f86f8-187">The receive buffer must be big enough to accommodate message of Ethernet MTU size.</span></span> <span data-ttu-id="f86f8-188">El paquete PPPoE recibido incluye el encabezado Ethernet de 14 bytes.</span><span class="sxs-lookup"><span data-stu-id="f86f8-188">The received PPPoE packet includes 14-byte Ethernet header.</span></span> <span data-ttu-id="f86f8-189">Al recibir paquetes PPPoE, los paquetes de detección de PPPoE solo los puede recibir un socket creado con el protocolo `ETHERTYPE_PPPOE_DISC`.</span><span class="sxs-lookup"><span data-stu-id="f86f8-189">On receiving PPPoE packets, PPPoE Discovery packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_DISC`.</span></span> <span data-ttu-id="f86f8-190">Del mismo modo, los paquetes de sesión PPP solo los puede recibir un socket creado con el protocolo `ETHERTYPE_PPPOE_SESS`.</span><span class="sxs-lookup"><span data-stu-id="f86f8-190">Similarly, PPP session packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_SESS`.</span></span> <span data-ttu-id="f86f8-191">Si se crean varios sockets para el mismo tipo de protocolo, los paquetes PPPoE que llegan se reenvían al socket que se creó en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="f86f8-191">If multiple sockets are created for the same protocol type, arriving PPPoE packets are forwarded to the socket created first.</span></span> <span data-ttu-id="f86f8-192">Si el primer socket creado para el protocolo está cerrado, se usa el siguiente socket por orden de creación para recibir estos paquetes.</span><span class="sxs-lookup"><span data-stu-id="f86f8-192">If the first socket created for the protocol is closed, the next socket in the order of creation is used for receiving these packets.</span></span>

<span data-ttu-id="f86f8-193">Después de recibir un paquete PPPoE, los siguientes campos de la estructura`sockaddr_ll` son válidos:</span><span class="sxs-lookup"><span data-stu-id="f86f8-193">After a PPPoE packet is received, the following fields in the `sockaddr_ll` struct are valid:</span></span>
- <span data-ttu-id="f86f8-194">**sll_family**: establecido en AF_PACKET por el proceso interno de BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-194">**sll_family**: Set by the BSD internal to be AF_PACKET</span></span>
- <span data-ttu-id="f86f8-195">**sll_ifindex**: indica la interfaz desde la que se recibe el paquete.</span><span class="sxs-lookup"><span data-stu-id="f86f8-195">**sll_ifindex**: Indicates the interface from which the packet is received</span></span>
- <span data-ttu-id="f86f8-196">**sll_protocol**: se establece en el tipo de paquete recibido: `ETHERTYPE_PPPOE_DISC` o `ETHERTYPE_PPPOE_SESS`.</span><span class="sxs-lookup"><span data-stu-id="f86f8-196">**sll_protocol**: Set to the type of packet received: `ETHERTYPE_PPPOE_DISC` or `ETHERTYPE_PPPOE_SESS`</span></span>

## <a name="eliminating-internal-bsd-thread"></a><span data-ttu-id="f86f8-197">Eliminación de subprocesos BSD internos</span><span class="sxs-lookup"><span data-stu-id="f86f8-197">Eliminating Internal BSD Thread</span></span>

<span data-ttu-id="f86f8-198">De manera predeterminada, BSD emplea un subproceso interno para realizar parte de su procesamiento.</span><span class="sxs-lookup"><span data-stu-id="f86f8-198">By default, BSD utilizes an internal thread to perform some of its processing.</span></span> <span data-ttu-id="f86f8-199">En sistemas con restricciones de memoria estrictas, se puede compilar BSD con NX_BSD_TIMEOUT_PROCESS_IN_TIMER definido, lo que elimina el subproceso de BSD interno y, en su lugar, utiliza un temporizador interno para realizar el mismo procesamiento.</span><span class="sxs-lookup"><span data-stu-id="f86f8-199">In systems with tight memory constraints, BSD can be built with NX_BSD_TIMEOUT_PROCESS_IN_TIMER defined, which eliminates the internal BSD thread and instead uses an internal timer to perform the same processing.</span></span> <span data-ttu-id="f86f8-200">Esto elimina la memoria necesaria para el bloque de control y la pila de subprocesos BSD internos.</span><span class="sxs-lookup"><span data-stu-id="f86f8-200">This eliminates the memory required for the internal BSD thread control block and stack.</span></span> <span data-ttu-id="f86f8-201">Sin embargo, el procesamiento general del temporizador se incrementa significativamente y el procesamiento de BSD también puede ejecutarse con una prioridad más alta de la necesaria.</span><span class="sxs-lookup"><span data-stu-id="f86f8-201">However, overall timer processing is significantly increased and the BSD processing may also execute at a higher priority than needed.</span></span>

<span data-ttu-id="f86f8-202">Para configurar los sockets BSD de modo que se ejecuten en el contexto del temporizador de ThreadX, defina NX_BSD_TIMEOUT_PROCESS_IN_TIMER en *nxd_bsd.h*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-202">To configure BSD sockets to run in the ThreadX timer context, define NX_BSD_TIMEOUT_PROCESS_IN_TIMER in *nxd_bsd.h*.</span></span> <span data-ttu-id="f86f8-203">Si la capa BSD está configurada para ejecutar las tareas de BSD en el contexto del temporizador, en la llamada a *bsd_initialize* se omiten los tres parámetros siguientes, que se deben establecer en NULL:</span><span class="sxs-lookup"><span data-stu-id="f86f8-203">If the BSD layer is configured to execute the BSD tasks in the timer context, in the call to *bsd_initialize*, the following three parameters are ignored, and should be set to NULL:</span></span>

- <span data-ttu-id="f86f8-204">**bsd_thread_stack_area**</span><span class="sxs-lookup"><span data-stu-id="f86f8-204">**bsd_thread_stack_area**</span></span>
- <span data-ttu-id="f86f8-205">**bsd_thread_stack_size**</span><span class="sxs-lookup"><span data-stu-id="f86f8-205">**bsd_thread_stack_size**</span></span>
- <span data-ttu-id="f86f8-206">**bsd_thread_priority**</span><span class="sxs-lookup"><span data-stu-id="f86f8-206">**bsd_thread_priority**</span></span>

## <a name="netx-duo-bsd-with-dns-support"></a><span data-ttu-id="f86f8-207">Compatibilidad de BSD de NetX Duo con DNS</span><span class="sxs-lookup"><span data-stu-id="f86f8-207">NetX Duo BSD with DNS Support</span></span>

<span data-ttu-id="f86f8-208">Si se define NX_BSD_ENABLE_DNS, BSD de NetX Duo puede enviar consultas de DNS para obtener la información de la IP o el nombre del host.</span><span class="sxs-lookup"><span data-stu-id="f86f8-208">If NX_BSD_ENABLE_DNS is defined, NetX Duo BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="f86f8-209">Esta característica requiere que se cree previamente un cliente DNS de NetX con el servicio *nx_dns_create*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-209">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="f86f8-210">Con la instancia de DNS, deben registrarse una o varias direcciones IP de servidor DNS conocidas mediante el servicio *nx_dns_server_add* para agregar direcciones de servidor IPv4 o mediante el servicio *nxd_dns_server_add* para agregar direcciones de servidor IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="f86f8-210">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* service for adding IPv4 server addresses, or using the *nxd_dns_server_add* service for adding either IPv4 or IPv6 server addresses.</span></span>

<span data-ttu-id="f86f8-211">Los servicios DNS y la asignación de memoria se usan en los servicios *getaddrinfo* y *getnameinfo*:</span><span class="sxs-lookup"><span data-stu-id="f86f8-211">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="f86f8-212">Cuando la aplicación BSD llama a *getaddrinfo* con un nombre de host, BSD de NetX llamará a cualquiera de los servicios siguientes para obtener la dirección IP:</span><span class="sxs-lookup"><span data-stu-id="f86f8-212">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="f86f8-213">**nx_dns_ipv4_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="f86f8-213">**nx_dns_ipv4_address_by_name_get**</span></span>
- <span data-ttu-id="f86f8-214">**nxd_dns_ipv6_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="f86f8-214">**nxd_dns_ipv6_address_by_name_get**</span></span>
- <span data-ttu-id="f86f8-215">**nx_dns_cname_get**</span><span class="sxs-lookup"><span data-stu-id="f86f8-215">**nx_dns_cname_get**</span></span>

<span data-ttu-id="f86f8-216">Para *nx_dns_ipv4_address_by_name_get* y *nxd_dns_ipv6_address_by_name_get*, BSD de NetX usa las áreas de memoria ipv4_addr_buffer e ipv6_addr_buffer, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f86f8-216">For *nx_dns_ipv4_address_by_name_get* and *nxd_dns_ipv6_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer and ipv6_addr_buffer memory areas respectively.</span></span> <span data-ttu-id="f86f8-217">El tamaño de estos búferes se define mediante (NX_BSD_IPV4_ADDR_PER_HOST \* 4) y (NX_BSD_IPV6_ADDR_PER_HOST \* 16), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f86f8-217">The size of these buffers are defined by (NX_BSD_IPV4_ADDR_PER_HOST \* 4) and (NX_BSD_IPV6_ADDR_PER_HOST \* 16) respectively.</span></span>

<span data-ttu-id="f86f8-218">Para devolver información de dirección de *getaddrinfo*, BSD de NetX usa la tabla de memoria de bloques de ThreadX nx_bsd_addrinfo_pool_memory, cuya área de memoria está definida por otro conjunto de opciones configurables, NX_BSD_IPV4_ADDR_MAX_NUM y NX_BSD_IPV6_ADDR_MAX_NUM.</span><span class="sxs-lookup"><span data-stu-id="f86f8-218">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table nx_bsd_addrinfo_pool_memory, whose memory area is defined by another set of configurable options, NX_BSD_IPV4_ADDR_MAX_NUM and NX_BSD_IPV6_ADDR_MAX_NUM.</span></span>

<span data-ttu-id="f86f8-219">Consulte **Opciones de configuración general** para obtener más detalles sobre las opciones de configuración anteriores.</span><span class="sxs-lookup"><span data-stu-id="f86f8-219">See **General Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="f86f8-220">Además, si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES y la entrada del host es un nombre canónico, BSD de NetX Duo asignará dinámicamente la memoria de un grupo de bloques \`_nx_bsd_cname_block_pool creado previamente</span><span class="sxs-lookup"><span data-stu-id="f86f8-220">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX Duo BSD will allocate memory dynamically from a previously created block pool \`_nx_bsd_cname_block_pool</span></span>

> [!NOTE]
> <span data-ttu-id="f86f8-221">Después de llamar a *getaddrinfo*, la aplicación BSD es responsable de liberar la memoria a la que apunta el argumento res de vuelta a la tabla de bloques mediante el servicio *freeaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-221">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="netx-duo-bsd-limitations"></a><span data-ttu-id="f86f8-222">Limitaciones de BSD de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f86f8-222">NetX Duo BSD Limitations</span></span>

<span data-ttu-id="f86f8-223">Debido a problemas de rendimiento y arquitectura, BSD de NetX Duo no admite todas las características de los sockets BSD 4.3:</span><span class="sxs-lookup"><span data-stu-id="f86f8-223">Due to performance and architecture issues, NetX Duo BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="f86f8-224">Las marcas INT no se admiten para las llamadas a *send, recv, sendto* y *recvfrom*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-224">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="general-configuration-options"></a><span data-ttu-id="f86f8-225">Opciones de configuración general</span><span class="sxs-lookup"><span data-stu-id="f86f8-225">General Configuration Options</span></span>

<span data-ttu-id="f86f8-226">Las opciones configurables por el usuario en *nxd_bsd.h* permiten a la aplicación ajustar los sockets BSD de NetX Duo a sus requisitos de la aplicación concretos.</span><span class="sxs-lookup"><span data-stu-id="f86f8-226">User configurable options in *nxd_bsd.h* allow the application to fine tune NetX Duo BSD sockets for its particular application requirements.</span></span>

<span data-ttu-id="f86f8-227">A continuación se muestra la lista de opciones configurables que se establecen en tiempo de compilación:</span><span class="sxs-lookup"><span data-stu-id="f86f8-227">The following is the list of configurable options that are set at compile time:</span></span>

- <span data-ttu-id="f86f8-228">**NX_BSD_TCP_WINDOW**: se usa en llamadas de creación de sockets TCP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-228">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="f86f8-229">64 k es el tamaño de ventana típico para Ethernet de 100 Mb.</span><span class="sxs-lookup"><span data-stu-id="f86f8-229">64k is typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="f86f8-230">El valor predeterminado es 65535.</span><span class="sxs-lookup"><span data-stu-id="f86f8-230">The default value is 65535.</span></span>

- <span data-ttu-id="f86f8-231">**NX_BSD_SOCKFD_START**: este es el índice lógico del valor de inicio del descriptor de archivo de socket BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-231">**NX_BSD_SOCKFD_START**: This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="f86f8-232">De forma predeterminada, esta opción es 32.</span><span class="sxs-lookup"><span data-stu-id="f86f8-232">By default this option is 32.</span></span>

- <span data-ttu-id="f86f8-233">**NX_BSD_MAX_SOCKETS**: especifica el número máximo de sockets totales disponibles en la capa BSD y debe ser un múltiplo de 32.</span><span class="sxs-lookup"><span data-stu-id="f86f8-233">**NX_BSD_MAX_SOCKETS**: Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.</span></span> <span data-ttu-id="f86f8-234">El valor predeterminado es 32.</span><span class="sxs-lookup"><span data-stu-id="f86f8-234">The value is defaulted to 32.</span></span>

- <span data-ttu-id="f86f8-235">**NX_BSD_SOCKET_QUEUE_MAX**: especifica el número máximo de paquetes UDP almacenados en la cola de sockets de recepción.</span><span class="sxs-lookup"><span data-stu-id="f86f8-235">**NX_BSD_SOCKET_QUEUE_MAX**: Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="f86f8-236">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="f86f8-236">The value is defaulted to 5.</span></span>

- <span data-ttu-id="f86f8-237">**NX_BSD_MAX_LISTEN_BACKLOG**: especifica el tamaño de la cola de escucha ("trabajo pendiente") para los sockets TCP de BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-237">**NX_BSD_MAX_LISTEN_BACKLOG**: This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="f86f8-238">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="f86f8-238">The default value is 5.</span></span>

- <span data-ttu-id="f86f8-239">**NX_MICROSECOND_PER_CPU_TICK**: especifica el número de microsegundos por cada tic del temporizador del programador.</span><span class="sxs-lookup"><span data-stu-id="f86f8-239">**NX_MICROSECOND_PER_CPU_TICK**: Specifies the number of microseconds per scheduler timer tick.</span></span>

- <span data-ttu-id="f86f8-240">**NX_BSD_TIMEOUT**: especifica el tiempo de espera en tics de temporizador requerido por BSD en las llamadas internas de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="f86f8-240">**NX_BSD_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo internal calls required by BSD.</span></span> <span data-ttu-id="f86f8-241">El valor predeterminado es (20 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="f86f8-241">The default value is (20 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="f86f8-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: especifica el tiempo de espera en tics de temporizador en la llamada de desconexión de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="f86f8-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo disconnect call.</span></span> <span data-ttu-id="f86f8-243">El valor predeterminado es 1.</span><span class="sxs-lookup"><span data-stu-id="f86f8-243">The default value is 1.</span></span>

- <span data-ttu-id="f86f8-244">**NX_BSD_PRINT_ERRORS**: si se establece, el valor devuelto de estado de error de una función BSD es un número de línea y un tipo de error, por ejemplo NX_SOC_ERROR, donde se produce el error.</span><span class="sxs-lookup"><span data-stu-id="f86f8-244">**NX_BSD_PRINT_ERRORS**: If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="f86f8-245">Esto requiere que el desarrollador de la aplicación defina la salida de la depuración.</span><span class="sxs-lookup"><span data-stu-id="f86f8-245">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="f86f8-246">La configuración predeterminada está deshabilitada y no se especifica ninguna salida de depuración en *nxd_bsd.h*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-246">The default setting is disabled and no debug output is specified in *nxd_bsd.h*.</span></span>

- <span data-ttu-id="f86f8-247">**NX_BSD_TIMER_RATE**: intervalo después del cual se ejecuta la tarea de temporizador periódica de BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-247">**NX_BSD_TIMER_RATE**: Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="f86f8-248">El valor predeterminado es 1 segundo (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="f86f8-248">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="f86f8-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: si se establece, esta opción permite que el proceso de tiempo de espera de BSD se ejecute en el contexto del temporizador del sistema.</span><span class="sxs-lookup"><span data-stu-id="f86f8-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="f86f8-250">De forma predeterminada está desactivado.</span><span class="sxs-lookup"><span data-stu-id="f86f8-250">The default behavior is disabled.</span></span> <span data-ttu-id="f86f8-251">Esta característica se describe con más detalle en el capítulo 2 "Instalación y uso de BSD de NetX Duo".</span><span class="sxs-lookup"><span data-stu-id="f86f8-251">This feature is described in more detail in Chapter 2 "Installation and Use of NetX Duo BSD".</span></span>

- <span data-ttu-id="f86f8-252">**NX_BSD_RAW_PPPOE_SUPPORT**: habilita la compatibilidad con paquetes sin formato de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="f86f8-252">**NX_BSD_RAW_PPPOE_SUPPORT**: Enable PPPoE raw packet support.</span></span> <span data-ttu-id="f86f8-253">De forma predeterminada, esta opción no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="f86f8-253">By default this option is not enabled.</span></span>

- <span data-ttu-id="f86f8-254">**NX_BSD_ENABLE_DNS**: si esta opción está habilitada, BSD de NetX Duo enviará una consulta de DNS de un nombre o una dirección IP de host.</span><span class="sxs-lookup"><span data-stu-id="f86f8-254">**NX_BSD_ENABLE_DNS**: If enabled, NetX Duo BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="f86f8-255">Requiere que se cree e inicie previamente una instancia de cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="f86f8-255">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="f86f8-256">De forma predeterminada, no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="f86f8-256">By default it is not enabled.</span></span>

- <span data-ttu-id="f86f8-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: define el tamaño de la tabla de sockets sin formato.</span><span class="sxs-lookup"><span data-stu-id="f86f8-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Defines the size of the raw socket table.</span></span> <span data-ttu-id="f86f8-258">El valor debe ser una potencia de dos.</span><span class="sxs-lookup"><span data-stu-id="f86f8-258">The value must be a power of two.</span></span> <span data-ttu-id="f86f8-259">BSD de NetX crea una matriz de sockets de tipo NX_BSD_SOCKETS para enviar y recibir paquetes sin formato.</span><span class="sxs-lookup"><span data-stu-id="f86f8-259">NetX BSD creates an array of sockets of type NX_BSD_SOCKETS for sending and receiving raw packets.</span></span> <span data-ttu-id="f86f8-260">NX_ENABLE_IP_RAW_PACKET_FILTER debe estar habilitado.</span><span class="sxs-lookup"><span data-stu-id="f86f8-260">NX_ENABLE_IP_RAW_PACKET_FILTER must be enabled.</span></span> <span data-ttu-id="f86f8-261">El valor predeterminado es 32.</span><span class="sxs-lookup"><span data-stu-id="f86f8-261">By default it is 32.</span></span>

- <span data-ttu-id="f86f8-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: número máximo de direcciones IPv4 devueltas por *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="f86f8-263">Esto, junto con NX_BSD_IPV6_ADDR_MAX_NUM, define el tamaño del grupo de bloques nx_bsd_addrinfo_block_pool de BSD de NetX para asignar memoria de forma dinámica para el almacenamiento de información de direcciones en *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-263">This along with NX_BSD_IPV6_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="f86f8-264">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="f86f8-264">The default value is 5.</span></span>

- <span data-ttu-id="f86f8-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: número máximo de direcciones IPv6 devueltas por *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: Maximum number of IPv6 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="f86f8-266">Esto, junto con NX_BSD_IPV4_ADDR_MAX_NUM, define el tamaño del grupo de bloques nx_bsd_addrinfo_block_pool de BSD de NetX para asignar memoria de forma dinámica para el almacenamiento de información de direcciones en *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-266">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span>

- <span data-ttu-id="f86f8-267">**NX_BSD_IPV4_ADDR_PER_HOST**: define el número máximo de direcciones IPv4 almacenadas por consulta de DNS.</span><span class="sxs-lookup"><span data-stu-id="f86f8-267">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="f86f8-268">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="f86f8-268">The default value is 5.</span></span>

- <span data-ttu-id="f86f8-269">**NX_BSD_IPV6_ADDR_PER_HOST**: define el número máximo de direcciones IPv6 almacenadas por consulta de DNS.</span><span class="sxs-lookup"><span data-stu-id="f86f8-269">**NX_BSD_IPV6_ADDR_PER_HOST**: Defines maximum IPv6 addresses stored per DNS query.</span></span> <span data-ttu-id="f86f8-270">El valor predeterminado es 2.</span><span class="sxs-lookup"><span data-stu-id="f86f8-270">The default value is 2.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="f86f8-271">Opciones de socket BSD</span><span class="sxs-lookup"><span data-stu-id="f86f8-271">BSD Socket Options</span></span>

<span data-ttu-id="f86f8-272">La siguiente lista de opciones de socket BSD de NetX Duo se puede habilitar (o deshabilitar) en tiempo de ejecución en cada socket mediante el servicio *setsockopt*:</span><span class="sxs-lookup"><span data-stu-id="f86f8-272">The following list of NetX Duo BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

<span data-ttu-id="f86f8-273">Hay dos configuraciones diferentes para option_level.</span><span class="sxs-lookup"><span data-stu-id="f86f8-273">There are two different settings for option_level.</span></span>

<span data-ttu-id="f86f8-274">El primer tipo de opciones de socket de tiempo de ejecución es SOL_SOCKET para las opciones de nivel de socket.</span><span class="sxs-lookup"><span data-stu-id="f86f8-274">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="f86f8-275">Para habilitar una opción de nivel de socket, llame a *setsockopt* con option_level establecido en SOL_SOCKET y option_name establecido en la opción específica, por ejemplo, SO_BROADCAST *.*</span><span class="sxs-lookup"><span data-stu-id="f86f8-275">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST *.*</span></span> <span data-ttu-id="f86f8-276">Para recuperar una configuración de opción, llame a *getsockopt* para option_name con option_level de nuevo establecido en SOL_SOCKET.</span><span class="sxs-lookup"><span data-stu-id="f86f8-276">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="f86f8-277">A continuación se muestra la lista de opciones de nivel de socket en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="f86f8-277">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="f86f8-278">**SO_BROADCAST**: si se establece, habilita el envío y la recepción de paquetes de difusión de sockets NetX.</span><span class="sxs-lookup"><span data-stu-id="f86f8-278">**SO_BROADCAST**:  If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="f86f8-279">Este es el comportamiento predeterminado para NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="f86f8-279">This is the default behavior for NetX Duo.</span></span> <span data-ttu-id="f86f8-280">Todos los sockets tienen esta capacidad.</span><span class="sxs-lookup"><span data-stu-id="f86f8-280">All sockets have this capability.</span></span>

- <span data-ttu-id="f86f8-281">**SO_ERROR**: se usa para obtener el estado del socket en la operación de socket anterior del socket especificado, mediante el servicio *getsockopt*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-281">**SO_ERROR**:  Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="f86f8-282">Todos los sockets tienen esta capacidad.</span><span class="sxs-lookup"><span data-stu-id="f86f8-282">All sockets have this capability.</span></span>

- <span data-ttu-id="f86f8-283">**SO_KEEPALIVE**: si se establece, habilita la característica de mantenimiento de conexión de TCP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-283">**SO_KEEPALIVE**:  If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="f86f8-284">Esto requiere que la biblioteca de NetX Duo se compile con NX_TCP_ENABLE_KEEPALIVE definido en *nx_user.h*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-284">This requires the NetX Duo library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="f86f8-285">Esta característica está deshabilitada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="f86f8-285">By default this feature is disabled.</span></span>

- <span data-ttu-id="f86f8-286">**SO_RCVTIMEO**: establece la opción de espera en segundos para recibir paquetes en sockets BSD de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="f86f8-286">**SO_RCVTIMEO**:  This sets the wait option in seconds for receiving packets on NetX Duo BSD sockets.</span></span> <span data-ttu-id="f86f8-287">El valor predeterminado es NX_WAIT_FOREVER (0xFFFFFFFF) o, si está habilitada la opción sin bloqueo, NX_NO_WAIT (0x0).</span><span class="sxs-lookup"><span data-stu-id="f86f8-287">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>

- <span data-ttu-id="f86f8-288">**SO_RCVBUF**: establece el tamaño de la ventana del socket TCP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-288">**SO_RCVBUF**:  This sets the window size of the TCP socket.</span></span> <span data-ttu-id="f86f8-289">El valor predeterminado, NX_BSD_TCP_WINDOW, se establece en 64 k para sockets TCP de BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-289">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="f86f8-290">Para establecer un tamaño superior a 65535, es necesario que la biblioteca de NetX Duo se compile con NX_TCP_ENABLE_WINDOW_SCALING definido.</span><span class="sxs-lookup"><span data-stu-id="f86f8-290">To set the size over 65535 requires the NetX Duo library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>

- <span data-ttu-id="f86f8-291">**SO_REUSEADDR**: si se establece, permite asignar varios sockets a un puerto.</span><span class="sxs-lookup"><span data-stu-id="f86f8-291">**SO_REUSEADDR**:  If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="f86f8-292">Por lo general se usa en el socket de servidor TCP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-292">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="f86f8-293">Este es el comportamiento predeterminado de los sockets de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="f86f8-293">This is the default behavior of NetX Duo sockets.</span></span>

<span data-ttu-id="f86f8-294">El segundo tipo de opciones de socket en tiempo de ejecución es el nivel de opción de IP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-294">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="f86f8-295">Para habilitar una opción de nivel de IP, llame a *setsockopt* con option_level establecido en IP_PROTO y option_name establecido en la opción, por ejemplo, IP_MULTICAST_TTL *.*</span><span class="sxs-lookup"><span data-stu-id="f86f8-295">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL *.*</span></span> <span data-ttu-id="f86f8-296">Para recuperar un valor de opción, llame a *getsockopt* para option_name con option_level de nuevo establecido en IP_PROTO.</span><span class="sxs-lookup"><span data-stu-id="f86f8-296">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="f86f8-297">A continuación se muestra la lista de opciones de nivel de IP en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="f86f8-297">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="f86f8-298">**IP_MULTICAST_TTL**: establece el período de vida de los sockets UDP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-298">**IP_MULTICAST_TTL**:  This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="f86f8-299">El valor predeterminado es NX_IP_TIME_TO_LIVE (0x80) cuando se crea el socket.</span><span class="sxs-lookup"><span data-stu-id="f86f8-299">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="f86f8-300">Este valor se puede invalidar mediante una llamada a *setsockopt* con esta opción de socket.</span><span class="sxs-lookup"><span data-stu-id="f86f8-300">This value can be overridden by calling *setsockopt* with this socket option.</span></span>

- <span data-ttu-id="f86f8-301">**IP_RAW_IPV6_HDRINCL**: si se establece esta opción, la aplicación que realiza la llamada debe anexar un encabezado IPv6 y, opcionalmente, encabezados de aplicación a los datos que se transmiten en sockets IPv6 sin formato creados por BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-301">**IP_RAW_IPV6_HDRINCL**:  If this option is set, the calling application must append an IPv6 header and optionally application headers to data being transmitted on raw IPv6 sockets created by BSD.</span></span> <span data-ttu-id="f86f8-302">Para usar esta opción, el procesamiento de sockets sin formato debe estar habilitado en la tarea de IP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-302">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="f86f8-303">**IP_ADD_MEMBERSHIP**: si se establece, esta opción permite que el socket BSD (se aplica solo a los sockets UDP) se una al grupo de IGMP especificado.</span><span class="sxs-lookup"><span data-stu-id="f86f8-303">**IP_ADD_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>

- <span data-ttu-id="f86f8-304">**IP_DROP_MEMBERSHIP**: si se establece, esta opción permite que el socket BSD (se aplica solo a los sockets UDP) abandone el grupo de IGMP especificado.</span><span class="sxs-lookup"><span data-stu-id="f86f8-304">**IP_DROP_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

- <span data-ttu-id="f86f8-305">**IP_HDRINCL**: si se establece esta opción, la aplicación que realiza la llamada debe anexar el encabezado IP y, opcionalmente, encabezados de aplicación a los datos que se transmiten en sockets IPv4 sin formato creados en BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-305">**IP_HDRINCL**:  If this option is set, the calling application must append the IP header and optionally application headers to data being transmitted on raw IPv4 sockets created in BSD.</span></span> <span data-ttu-id="f86f8-306">Para usar esta opción, el procesamiento de sockets sin formato debe estar habilitado en la tarea de IP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-306">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="f86f8-307">**IP_RAW_RX_NO_HEADER**: si se desactiva, el encabezado IPv6 se incluye con los datos recibidos para los sockets IPv6 sin formato creados en BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-307">**IP_RAW_RX_NO_HEADER**:  If cleared, the IPv6 header is included with the received data for raw IPv6 sockets created in BSD.</span></span> <span data-ttu-id="f86f8-308">Los encabezados IPv6 se quitan de forma predeterminada en los sockets IPv6 sin formato de BSD y la longitud del paquete no incluye el encabezado IPv6.</span><span class="sxs-lookup"><span data-stu-id="f86f8-308">IPv6 headers are removed by default in BSD raw IPv6 sockets, and the packet length does not include the IPv6 header.</span></span>

<span data-ttu-id="f86f8-309">Si se establece, el encabezado IPv4 se quita de los datos recibidos en sockets sin formato de BSD de tipo IPv4.</span><span class="sxs-lookup"><span data-stu-id="f86f8-309">If set, the IPv4 header is removed from received data on BSD raw sockets of type IPv4.</span></span> <span data-ttu-id="f86f8-310">Los encabezados IPv4 se incluyen de forma predeterminada en los sockets IPv4 sin formato de BSD y la longitud de los paquetes incluye el encabezado IPv4.</span><span class="sxs-lookup"><span data-stu-id="f86f8-310">IPv4 headers are included by default in BSD raw IPv4 sockets and packet length includes the IPv4 header.</span></span>

<span data-ttu-id="f86f8-311">Esta opción no tiene ningún efecto en los datos de transmisión de IPv4 ni de IPv6.</span><span class="sxs-lookup"><span data-stu-id="f86f8-311">This option has no effect on either IPv4 or IPv6 transmission data.</span></span>

## <a name="small-ipv4-example"></a><span data-ttu-id="f86f8-312">Ejemplo de IPv4 pequeño</span><span class="sxs-lookup"><span data-stu-id="f86f8-312">Small IPv4 Example</span></span>

<span data-ttu-id="f86f8-313">A continuación se describe un ejemplo de cómo usar los servicios de BSD de NetX Duo para redes IPv4.</span><span class="sxs-lookup"><span data-stu-id="f86f8-313">An example of how to use NetX Duo BSD services for IPv4 networks is described below.</span></span> <span data-ttu-id="f86f8-314">En este ejemplo, el archivo de inclusión *nxd_bsd.h* se agrega en la línea 8.</span><span class="sxs-lookup"><span data-stu-id="f86f8-314">In this example, the include file *nxd_bsd.h* is brought in at line 8.</span></span> <span data-ttu-id="f86f8-315">A continuación, la instancia de IP *bsd_ip* y el grupo de paquetes *bsd_pool* se crean como variables globales en las líneas 20 y 21.</span><span class="sxs-lookup"><span data-stu-id="f86f8-315">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="f86f8-316">Tenga en cuenta que en esta demostración se usa un controlador de red de RAM (virtual) *, _nx_ram_network_driver*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-316">Note that this demo uses a ram (virtual) network driver *, _nx_ram_network_driver*.</span></span> <span data-ttu-id="f86f8-317">En este ejemplo, el cliente y el servidor compartirán la misma dirección IP de una instancia de IP única.</span><span class="sxs-lookup"><span data-stu-id="f86f8-317">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="f86f8-318">Los subprocesos de cliente y servidor se crean en las líneas 62 y 68.</span><span class="sxs-lookup"><span data-stu-id="f86f8-318">The client and server threads are created on lines 62 and 68.</span></span> <span data-ttu-id="f86f8-319">El grupo de paquetes BSD para transmitir paquetes se crea en la línea 78 y se usa en la creación de la instancia de IP en la línea 87.</span><span class="sxs-lookup"><span data-stu-id="f86f8-319">The BSD packet pool for transmitting packets is created on line 78 and used in the IP instance creation on line 87.</span></span> <span data-ttu-id="f86f8-320">Observe que se asigna la prioridad 1 a la tarea del subproceso de IP en la llamada a *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-320">Note that the IP thread task is given priority 1 in the *nx_ip_create* call.</span></span> <span data-ttu-id="f86f8-321">Para un rendimiento óptimo de NetX, este subproceso debe ser la tarea de prioridad más alta definida en el programa.</span><span class="sxs-lookup"><span data-stu-id="f86f8-321">This thread should be the highest priority task defined in the program for optimal NetX performance.</span></span>

<span data-ttu-id="f86f8-322">La instancia de IP se habilita para los servicios ARP y TCP en las líneas 88 y 110, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f86f8-322">The IP instance is enabled for ARP and TCP services on lines 88 and 110 respectively.</span></span> <span data-ttu-id="f86f8-323">El último requisito antes de poder usar los servicios de BSD es llamar a *bsd_initialize* en la línea 120 para configurar todas las estructuras de datos y los recursos de NetX y ThreadX necesarios para BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-323">The last requirement before BSD services can be used is to call *bsd_initialize* on line 120 to set up all data structures and NetX and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="f86f8-324">A continuación se define la función de entrada del subproceso de servidor.</span><span class="sxs-lookup"><span data-stu-id="f86f8-324">The server thread entry function is defined next.</span></span> <span data-ttu-id="f86f8-325">El socket TCP de BSD se crea en la línea 149.</span><span class="sxs-lookup"><span data-stu-id="f86f8-325">The BSD TCP socket is created on line 149.</span></span> <span data-ttu-id="f86f8-326">La dirección IP y el puerto del servidor se establecen en las líneas 160 a 163.</span><span class="sxs-lookup"><span data-stu-id="f86f8-326">The server IP address and port are set on lines 160-163.</span></span> <span data-ttu-id="f86f8-327">Observe el uso de las macros de orden de bytes de host a red *htonl* y *htons* aplicadas a la dirección IP y al puerto.</span><span class="sxs-lookup"><span data-stu-id="f86f8-327">Note the use of host to network byte order macros *htonl* and *htons* applied to the IP address and port.</span></span> <span data-ttu-id="f86f8-328">Esto cumple con la especificación de sockets BSD por la que los datos de varios bytes se envían a los servicios de BSD en el orden de bytes de la red.</span><span class="sxs-lookup"><span data-stu-id="f86f8-328">This is in compliance with BSD socket specification that multi byte data is submitted to the BSD services in network byte order.</span></span>

<span data-ttu-id="f86f8-329">Después, el socket del servidor maestro se enlaza al puerto mediante el servicio *bind* en la línea 166.</span><span class="sxs-lookup"><span data-stu-id="f86f8-329">Next, the master server socket is bound to the port using the *bind* service on line 166.</span></span> <span data-ttu-id="f86f8-330">Este es el socket de escucha para las solicitudes de conexión TCP que usan el servicio *listen* en la línea 180.</span><span class="sxs-lookup"><span data-stu-id="f86f8-330">This is the listening socket for TCP connection requests using the *listen* service on line 180.</span></span> <span data-ttu-id="f86f8-331">Desde aquí, la función de subproceso de servidor, *thread_server_entry*, se repite en bucle para comprobar si hay eventos de recepción mediante la llamada a *select* en la línea 202.</span><span class="sxs-lookup"><span data-stu-id="f86f8-331">From here the server thread function, *thread_server_entry*, loops to check for receive events using the *select* call on line 202.</span></span> <span data-ttu-id="f86f8-332">Si un evento de recepción es una solicitud de conexión, lo que se determina comparando la lista preparada para lectura, llama a *accept* en la línea 213.</span><span class="sxs-lookup"><span data-stu-id="f86f8-332">If a receive event is a connection request, which is determined by comparing the read ready list, it calls *accept* on line 213.</span></span> <span data-ttu-id="f86f8-333">Se asigna un socket de servidor secundario para controlar la solicitud de conexión y se agrega a la lista maestra de sockets de servidor TCP conectados a un cliente en la línea 223.</span><span class="sxs-lookup"><span data-stu-id="f86f8-333">A child server socket is assigned to handle the connection request and added to the master list of TCP server sockets connected to a Client on line 223.</span></span> <span data-ttu-id="f86f8-334">Si no hay ninguna solicitud de conexión nueva, el subproceso de servidor comprueba en todos los sockets conectados actualmente si hay eventos de recepción con el bucle For que empieza en la línea 236.</span><span class="sxs-lookup"><span data-stu-id="f86f8-334">If there are no new connection requests, the server thread then checks all the currently connected sockets for receive events in the for loop starting on line 236.</span></span> <span data-ttu-id="f86f8-335">Cuando se detecta un evento de recepción en espera, llama a *send* y a *recv* en ese socket hasta que no se reciben datos (la conexión se cierra en el otro lado) y el socket se cierra con el servicio *soc_close* en la línea 277.</span><span class="sxs-lookup"><span data-stu-id="f86f8-335">When a receive event waiting is detected, it calls *send* and *recv* on that socket until no data is received (connection closed on the other side) and the socket is closed using the *soc_close* service on line 277.</span></span>

<span data-ttu-id="f86f8-336">Una vez que se configura el subproceso de servidor, la función de entrada de subprocesos del cliente, *thread_client_entry*, crea un socket en la línea 326 y lo conecta con el socket de servidor TCP mediante la llamada a *connect* en la línea 337.</span><span class="sxs-lookup"><span data-stu-id="f86f8-336">After the server thread sets up, the Client thread entry function, *thread_client_entry,* creates a socket on line 326 and connects with the TCP server socket using the *connect* call on line 337.</span></span> <span data-ttu-id="f86f8-337">A continuación, se ejecuta en bucle para enviar y recibir paquetes mediante los servicios *send* y *recv*, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f86f8-337">It then loops to send and receive packets using the *send* and *recv* services respectively.</span></span> <span data-ttu-id="f86f8-338">Cuando no se reciben más datos, cierra el socket en la línea 398 con el servicio *soc_close*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-338">When no more data is received, it closes the socket on line 398 using the *soc_close* service.</span></span> <span data-ttu-id="f86f8-339">Después de la desconexión, la función de entrada del subproceso del cliente crea un nuevo socket TCP y realiza otra solicitud de conexión en el bucle While iniciado en la línea 321.</span><span class="sxs-lookup"><span data-stu-id="f86f8-339">After disconnection, the client thread entry function creates a new TCP socket and makes another connection request in the while loop started on line 321.</span></span>

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

## <a name="small-ipv6-example-system"></a><span data-ttu-id="f86f8-340">Sistema de ejemplo de IPv6 pequeño</span><span class="sxs-lookup"><span data-stu-id="f86f8-340">Small IPv6 Example System</span></span>

<span data-ttu-id="f86f8-341">En el siguiente programa se describe un ejemplo de cómo usar los servicios de BSD de NetX Duo para redes IPv6.</span><span class="sxs-lookup"><span data-stu-id="f86f8-341">An example of how to use NetX Duo BSD services for IPv6 networks is described in the program below.</span></span> <span data-ttu-id="f86f8-342">Este ejemplo es muy similar al programa de demostración de IPv4 descrito anteriormente con algunas diferencias importantes.</span><span class="sxs-lookup"><span data-stu-id="f86f8-342">This example is very similar to the IPv4 demo program previously described with a few important differences.</span></span>

<span data-ttu-id="f86f8-343">Los subprocesos de cliente y de servidor, el grupo de paquetes de BSD, la instancia de IP y la inicialización de BSD se producen igual que para los sockets BSD IPv4.</span><span class="sxs-lookup"><span data-stu-id="f86f8-343">The client and server threads, BSD packet pool, IP instance and BSD initialization happens as it does for IPv4 BSD sockets.</span></span>

<span data-ttu-id="f86f8-344">En la función de entrada del subproceso de servidor, *thread_server_entry*, define un par de variables IPv6 usando los tipos de datos *sockaddr_in6* y *NXD_ADDRESS* en las líneas 145 a 148.</span><span class="sxs-lookup"><span data-stu-id="f86f8-344">In the server thread entry function, *thread_server_entry*, defines a couple IPv6 variables using *sockaddr_in6* and *NXD_ADDRESS* data types on lines 145-148.</span></span> <span data-ttu-id="f86f8-345">En realidad, el tipo de datos NXD_ADDRESS puede almacenar tanto tipos de direcciones IPv4 como IPv6.</span><span class="sxs-lookup"><span data-stu-id="f86f8-345">The NXD_ADDRESS data type can actually store both IPv4 and IPv6 address types.</span></span>

<span data-ttu-id="f86f8-346">A continuación, el subproceso de servidor habilita IPv6 e ICMPv6 en la instancia de IP mediante los servicios *nxd_ipv6_enable* y *nxd_icmpv6_enable*, respectivamente, en las líneas 161 y 169.</span><span class="sxs-lookup"><span data-stu-id="f86f8-346">Next, the server thread enables IPv6 and ICMPv6 on the IP instance using the *nxd_ipv6_enable* and *nxd_icmpv6_enable* service respectively on line 161 and 169.</span></span> <span data-ttu-id="f86f8-347">A continuación, las direcciones IP locales y globales del vínculo se registran con la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-347">Next, the link local and global IP addresses are registered with the IP instance.</span></span> <span data-ttu-id="f86f8-348">Esto se hace mediante el servicio *nxd_ipv6_address_set* en las líneas 180 y 195.</span><span class="sxs-lookup"><span data-stu-id="f86f8-348">This is done using the *nxd_ipv6_address_set* service on lines 180 and 195.</span></span> <span data-ttu-id="f86f8-349">Después, se suspende el tiempo suficiente como para que la tarea de subproceso de IP complete el protocolo de detección de direcciones duplicadas y registre estas direcciones como direcciones válidas en la llamada a *tx_thread_sleep* en la línea 201.</span><span class="sxs-lookup"><span data-stu-id="f86f8-349">It then sleeps long enough for the IP thread task to complete the Duplicate Address Detection protocol and register these addresses as valid addresses on the *tx_thread_sleep* call on line 201.</span></span>

<span data-ttu-id="f86f8-350">A continuación, el socket de servidor TCP se crea con el argumento de entrada de tipo de socket AF_INET6 en la línea 204.</span><span class="sxs-lookup"><span data-stu-id="f86f8-350">Next, the TCP server socket is created with the AF_INET6 socket type input argument on line 204.</span></span> <span data-ttu-id="f86f8-351">El puerto y la dirección IPv6 del socket se establecen en las líneas 216 a 221, de nuevo con el uso de las macros *htonl* y *htons* para incluir los datos en el orden de bytes de la red para los servicios de socket BSD.</span><span class="sxs-lookup"><span data-stu-id="f86f8-351">The socket IPv6 address and port are set on lines 216-221, again noting the use of *htonl* and *htons* macros to put data in network byte order for BSD socket services.</span></span> <span data-ttu-id="f86f8-352">Desde aquí, la función de entrada del subproceso de servidor es prácticamente idéntica al ejemplo de IPv4.</span><span class="sxs-lookup"><span data-stu-id="f86f8-352">From here on, the server thread entry function is virtually identical to the IPv4 example.</span></span>

<span data-ttu-id="f86f8-353">A continuación, se define la función de entrada del subproceso de cliente, *thread_client_entry*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-353">The client thread entry function, *thread_client_entry*, is defined next.</span></span> <span data-ttu-id="f86f8-354">Tenga en cuenta que, dado que el cliente de TCP en este ejemplo comparte la misma instancia de IP y dirección IPv6 que el servidor TCP, no es necesario habilitar los servicios IPv6 o ICMPv6 en la instancia de IP de nuevo.</span><span class="sxs-lookup"><span data-stu-id="f86f8-354">Note that because the TCP client in this example shares the same IP instance and IPv6 address as the TCP server, we do not need to enable IPv6 or ICMPv6 services on the IP instance again.</span></span> <span data-ttu-id="f86f8-355">Además, la dirección IPv6 ya está registrada con la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-355">Further, the IPv6 address is also already registered with the IP instance.</span></span> <span data-ttu-id="f86f8-356">En su lugar, la función de entrada del subproceso de cliente simplemente espera en la línea 368 a que se configure el servidor.</span><span class="sxs-lookup"><span data-stu-id="f86f8-356">Instead, the client thread entry function simply waits on line 368 for the server to set up.</span></span> <span data-ttu-id="f86f8-357">Se establecen la dirección y el puerto del servidor mediante las macros de orden de bytes del host a la red en las líneas 387 a 392 y, a continuación, el cliente puede conectarse con el servidor TCP en la línea 412.</span><span class="sxs-lookup"><span data-stu-id="f86f8-357">The server address and port are set, using the host to network byte order macros on lines 387-392, and then the Client can connect with the TCP server on line 412.</span></span> <span data-ttu-id="f86f8-358">Tenga en cuenta que los tipos de datos de dirección IP local en las líneas 378 a 383 solo se usan para mostrar los servicios *getsockname* y *getpeername* en las líneas 425 y 434, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f86f8-358">Note that the local IP address data types in lines 378-383 are used only to demonstrate the *getsockname* and *getpeername* services on lines 425 and 434 respectively.</span></span> <span data-ttu-id="f86f8-359">Dado que los datos proceden de la red, en las líneas 378 a 383 se usan las macros de orden de bytes de red a host.</span><span class="sxs-lookup"><span data-stu-id="f86f8-359">Because the data is coming from the network, the network to host byte order macros as used in lines 378-383.</span></span>

<span data-ttu-id="f86f8-360">Después, la función de entrada de subproceso de cliente se repite para crear un socket TCP, realiza una conexión TCP y envía y recibe datos con el servidor TCP hasta que no se reciben más datos; prácticamente igual que el ejemplo de IPv4.</span><span class="sxs-lookup"><span data-stu-id="f86f8-360">Next the client thread entry function enters a loop in which it creates a TCP socket, makes a TCP connection and sends and receives data with the TCP server until no more data is received virtually the same as the IPv4 example.</span></span> <span data-ttu-id="f86f8-361">A continuación, cierra el socket en la línea 483, se pausa brevemente, crea otro socket TCP y solicita una conexión con el servidor TCP.</span><span class="sxs-lookup"><span data-stu-id="f86f8-361">It then closes the socket on line 483, pauses briefly and creates another TCP socket and requests a TCP server connection.</span></span>

<span data-ttu-id="f86f8-362">Una diferencia importante con el ejemplo de IPv4 es que las llamadas a *socket* especifican un socket IPv6 mediante el argumento de entrada AF_INET6.</span><span class="sxs-lookup"><span data-stu-id="f86f8-362">One important difference with the IPv4 example is the *socket* calls specify an IPv6 socket using the AF_INET6 input argument.</span></span> <span data-ttu-id="f86f8-363">Otra diferencia importante es que la llamada a *connect* del cliente TCP toma un tipo de datos *sockaddr_in6* y un argumento de longitud establecido en el tamaño del tipo de datos *sockaddr_in6*.</span><span class="sxs-lookup"><span data-stu-id="f86f8-363">Another important difference is that the TCP Client *connect* call takes an *sockaddr_in6* data type and a length argument set to the size of the *sockaddr_in6* data type.</span></span>

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
