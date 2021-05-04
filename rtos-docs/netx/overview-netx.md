---
title: Descripción de Azure RTOS NetX
description: Azure RTOS NetX es una implementación de alto rendimiento de los estándares del protocolo TCP/IP, totalmente integrada con Azure RTOS ThreadX y disponible para todos los procesadores compatibles.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 7c864c23f019e4841ddb3096fde663c8039baf44
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171325"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="f59e1-103">Introducción a Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="f59e1-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="f59e1-104">Azure RTOS NetX es una pila de red insertada en IPv4 TCP/IP y de nivel industrial diseñada específicamente para aplicaciones de IoT, en tiempo real y profundamente insertadas.</span><span class="sxs-lookup"><span data-stu-id="f59e1-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="f59e1-105">Azure RTOS NetX es la pila de red IPv4 original de Microsoft y es esencialmente un subconjunto de Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="f59e1-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="f59e1-106">NetX proporciona aplicaciones insertadas con los principales protocolos de red, como IPv4, TCP y UDP, así como un conjunto completo de protocolos adicionales de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="f59e1-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="f59e1-107">Una pequeña superficie, una ejecución rápida y una facilidad de uso superior hacen que Azure RTOS NetX sea una opción ideal para las aplicaciones de IoT integradas más exigentes.</span><span class="sxs-lookup"><span data-stu-id="f59e1-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="f59e1-108">Protocolos de API</span><span class="sxs-lookup"><span data-stu-id="f59e1-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="f59e1-109">TELNET</span><span class="sxs-lookup"><span data-stu-id="f59e1-109">TELNET</span></span>

* <span data-ttu-id="f59e1-110">Superficie de memoria RAM mínima 0,5 KB y 0,3 KB.</span><span class="sxs-lookup"><span data-stu-id="f59e1-110">Minimal 0.5 KB and 0.3 KB RAM footprint.</span></span>
* <span data-ttu-id="f59e1-111">Compatibilidad con cliente y servidor.</span><span class="sxs-lookup"><span data-stu-id="f59e1-111">Client and server support.</span></span>

### <a name="auto-ip"></a><span data-ttu-id="f59e1-112">IP automática</span><span class="sxs-lookup"><span data-stu-id="f59e1-112">Auto IP</span></span>

* <span data-ttu-id="f59e1-113">Asignación automática de direcciones IPv4.</span><span class="sxs-lookup"><span data-stu-id="f59e1-113">Automatic IPv4 address assignment.</span></span>
* <span data-ttu-id="f59e1-114">Mínimo 1,2 KB; 300 bytes de RAM.</span><span class="sxs-lookup"><span data-stu-id="f59e1-114">Minimal 1.2 KB, 300 bytes of RAM.</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="f59e1-115">HTTP - Protocolo de transferencia de hipertexto (HTTP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-115">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="f59e1-116">Memoria flash mínima de 2,8 KB a 4,8 KB; superficie de memoria RAM de 0,4 KB a 1,0 KB.</span><span class="sxs-lookup"><span data-stu-id="f59e1-116">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint.</span></span>
* <span data-ttu-id="f59e1-117">Compatibilidad con cliente y servidor.</span><span class="sxs-lookup"><span data-stu-id="f59e1-117">Client and server support.</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="f59e1-118">SMTP - Protocolo simple de transferencia de correo (SMTP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-118">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="f59e1-119">Mínimo 4,1 KB y una superficie de RAM de 0,6 KB</span><span class="sxs-lookup"><span data-stu-id="f59e1-119">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="f59e1-120">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="f59e1-120">Client support</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="f59e1-121">DHCP - Protocolo de configuración dinámica de host (DHCP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-121">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="f59e1-122">Memoria flash mínima de 3,6 KB a 4,6 KB, superficie de RAM de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="f59e1-122">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="f59e1-123">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="f59e1-123">Client and server support</span></span>
* <span data-ttu-id="f59e1-124">Compatibilidad con IPv4</span><span class="sxs-lookup"><span data-stu-id="f59e1-124">IPv4 support</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="f59e1-125">P0P3: Protocolo de oficina de correos, versión 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="f59e1-125">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="f59e1-126">Mínimo 8,1 KB y una superficie de RAM de 1,4 KB</span><span class="sxs-lookup"><span data-stu-id="f59e1-126">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="f59e1-127">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="f59e1-127">Client support</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="f59e1-128">SNMP - Protocolo simple de administración de redes (SNMP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-128">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="f59e1-129">Mínimo 10,9 KB y una superficie de RAM de 2,6 KB</span><span class="sxs-lookup"><span data-stu-id="f59e1-129">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="f59e1-130">Compatibilidad del agente con V1, V2 y V3</span><span class="sxs-lookup"><span data-stu-id="f59e1-130">Agent support for VI, V2, and V3</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="f59e1-131">FTP, TFTP - Protocolo de transferencia de archivos (FTP), Protocolo trivial de transferencia de archivos (TFTP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-131">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="f59e1-132">FTP: memoria flash mínima de 1,8 KB a 7,2 KB y superficie de RAM de 0,6 KB a 2,1 KB</span><span class="sxs-lookup"><span data-stu-id="f59e1-132">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="f59e1-133">TFTP: memoria flash mínima de 1,7 KB a 2,4 KB y superficie de RAM de 0,3 KB a 1,8 KB</span><span class="sxs-lookup"><span data-stu-id="f59e1-133">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="f59e1-134">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="f59e1-134">Client and server support</span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="f59e1-135">PPP - Protocolo punto a punto (PPP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-135">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="f59e1-136">Mínimo 7,1 KB y una superficie de RAM de 3,8 KB</span><span class="sxs-lookup"><span data-stu-id="f59e1-136">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="f59e1-137">Confiable.</span><span class="sxs-lookup"><span data-stu-id="f59e1-137">Dependable and reliable.</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="f59e1-138">SNTP-Protocolo simple de tiempo de red (SNTP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-138">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="f59e1-139">Mínimo 4 KB y una superficie de RAM de 0,5 KB</span><span class="sxs-lookup"><span data-stu-id="f59e1-139">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="f59e1-140">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="f59e1-140">Client support</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="f59e1-141">API de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="f59e1-141">Azure RTOS NetX API</span></span>

* <span data-ttu-id="f59e1-142">Implementación rápida de la API sin copia</span><span class="sxs-lookup"><span data-stu-id="f59e1-142">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="f59e1-143">Capa de BSD opcional para la portabilidad de código de sockets heredado</span><span class="sxs-lookup"><span data-stu-id="f59e1-143">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="f59e1-144">IGMP - Protocolo de administración de grupos de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-144">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="f59e1-145">Memoria flash mínima de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="f59e1-145">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="f59e1-146">Compatibilidad con grupos de multidifusión IPv4</span><span class="sxs-lookup"><span data-stu-id="f59e1-146">IPv4 multicast group support</span></span>
* <span data-ttu-id="f59e1-147">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="f59e1-147">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="f59e1-148">Estadísticas de IGMP opcionales</span><span class="sxs-lookup"><span data-stu-id="f59e1-148">Optional IGMP statistics</span></span>
* <span data-ttu-id="f59e1-149">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="f59e1-149">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="f59e1-150">UDP - Protocolo de datagramas de usuario (UDP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-150">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="f59e1-151">Memoria flash mínima de 2,5 KB, 124 bytes de RAM por socket</span><span class="sxs-lookup"><span data-stu-id="f59e1-151">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="f59e1-152">Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:</span><span class="sxs-lookup"><span data-stu-id="f59e1-152">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="f59e1-153">RX: 95 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 14 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="f59e1-153">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="f59e1-154">TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 10 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="f59e1-154">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="f59e1-155">Tecnología UDP Fast Path™</span><span class="sxs-lookup"><span data-stu-id="f59e1-155">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="f59e1-156">No hay límites en el número de UDP.</span><span class="sxs-lookup"><span data-stu-id="f59e1-156">No limits on the number of UDP</span></span>
* <span data-ttu-id="f59e1-157">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="f59e1-157">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="f59e1-158">Suspensión opcional en la recepción de sockets</span><span class="sxs-lookup"><span data-stu-id="f59e1-158">Optional suspension on socket receive</span></span>
* <span data-ttu-id="f59e1-159">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="f59e1-159">Optional timeout on all suspension</span></span>
* <span data-ttu-id="f59e1-160">Estadísticas de UDP opcionales</span><span class="sxs-lookup"><span data-stu-id="f59e1-160">Optional UDP statistics</span></span>
* <span data-ttu-id="f59e1-161">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="f59e1-161">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="f59e1-162">TCP - Protocolo de control de transmisión (TCP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-162">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="f59e1-163">Memoria flash mínima de 10,5 KB a 12,5 KB, 280 bytes de RAM por socket</span><span class="sxs-lookup"><span data-stu-id="f59e1-163">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="f59e1-164">Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:</span><span class="sxs-lookup"><span data-stu-id="f59e1-164">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="f59e1-165">RX: 93 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 20 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="f59e1-165">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="f59e1-166">TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 27 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="f59e1-166">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="f59e1-167">Conexión confiable</span><span class="sxs-lookup"><span data-stu-id="f59e1-167">Reliable connection</span></span>
* <span data-ttu-id="f59e1-168">No hay límites en el número de sockets de TCP</span><span class="sxs-lookup"><span data-stu-id="f59e1-168">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="f59e1-169">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="f59e1-169">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="f59e1-170">Suspensión opcional en la recepción y transmisión de sockets</span><span class="sxs-lookup"><span data-stu-id="f59e1-170">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="f59e1-171">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="f59e1-171">Optional timeout on all suspension</span></span>
* <span data-ttu-id="f59e1-172">Estadísticas de TCP opcionales</span><span class="sxs-lookup"><span data-stu-id="f59e1-172">Optional TCP statistics</span></span>
* <span data-ttu-id="f59e1-173">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="f59e1-173">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="f59e1-174">ICMP - Protocolo de mensajes de control de Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-174">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="f59e1-175">Memoria flash mínima de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="f59e1-175">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="f59e1-176">Compatibilidad con IPv4</span><span class="sxs-lookup"><span data-stu-id="f59e1-176">IPv4 support</span></span>
* <span data-ttu-id="f59e1-177">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="f59e1-177">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="f59e1-178">Solicitud de ping y respuesta de ping</span><span class="sxs-lookup"><span data-stu-id="f59e1-178">Ping request and ping response</span></span>
* <span data-ttu-id="f59e1-179">Suspensión de subprocesos opcional en solicitudes de ping</span><span class="sxs-lookup"><span data-stu-id="f59e1-179">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="f59e1-180">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="f59e1-180">Optional timeout on all suspension</span></span>
* <span data-ttu-id="f59e1-181">Estadísticas de ICMP opcionales</span><span class="sxs-lookup"><span data-stu-id="f59e1-181">Optional ICMP statistics</span></span>
* <span data-ttu-id="f59e1-182">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="f59e1-182">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="f59e1-183">IPv4 - Protocolo de Internet (IP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-183">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="f59e1-184">Memoria flash mínima de 3,5 KB a 8,5 KB; superficie de memoria RAM de 2 KB a 3 KB.</span><span class="sxs-lookup"><span data-stu-id="f59e1-184">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint.</span></span>
* <span data-ttu-id="f59e1-185">Arquitectura Piconet™.</span><span class="sxs-lookup"><span data-stu-id="f59e1-185">Piconet™ Architecture.</span></span>
* <span data-ttu-id="f59e1-186">Rendimiento rápido, casi a velocidad de cable.</span><span class="sxs-lookup"><span data-stu-id="f59e1-186">Fast, near wirespeed performance.</span></span>
* <span data-ttu-id="f59e1-187">Compatibilidad con varias interfaces.</span><span class="sxs-lookup"><span data-stu-id="f59e1-187">Multiple interface support.</span></span>
* <span data-ttu-id="f59e1-188">Compatibilidad con hosts múltiples.</span><span class="sxs-lookup"><span data-stu-id="f59e1-188">Multi-homed support.</span></span>
* <span data-ttu-id="f59e1-189">Compatibilidad con enrutamiento estático.</span><span class="sxs-lookup"><span data-stu-id="f59e1-189">Static routing support.</span></span>
* <span data-ttu-id="f59e1-190">Compatibilidad con el reensamblado y la fragmentación IP.</span><span class="sxs-lookup"><span data-stu-id="f59e1-190">IP fragmentation/reassembly support.</span></span>
* <span data-ttu-id="f59e1-191">Compatibilidad con IPv4.</span><span class="sxs-lookup"><span data-stu-id="f59e1-191">IPv4 Support.</span></span>
* <span data-ttu-id="f59e1-192">Validado por IxANVL de IXIA.</span><span class="sxs-lookup"><span data-stu-id="f59e1-192">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="f59e1-193">Certificación de logotipo Preparado para fase II.</span><span class="sxs-lookup"><span data-stu-id="f59e1-193">Phase II Ready Logo Certification.</span></span>
* <span data-ttu-id="f59e1-194">Estadísticas de IP opcionales.</span><span class="sxs-lookup"><span data-stu-id="f59e1-194">Optional IP statistics.</span></span>
* <span data-ttu-id="f59e1-195">Interfaz del controlador de la capa física intuitiva y bien definida.</span><span class="sxs-lookup"><span data-stu-id="f59e1-195">Well defined, intuitive physical layer driver interface.</span></span>
* <span data-ttu-id="f59e1-196">Seguimiento de nivel de sistema mediante Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="f59e1-196">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="f59e1-197">ARP/RARP - Protocolo de resolución de direcciones (ARP), Protocolo de resolución inversa de direcciones (RARP)</span><span class="sxs-lookup"><span data-stu-id="f59e1-197">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="f59e1-198">Memoria flash mínima de 1,7 KB, tamaño de RAM.</span><span class="sxs-lookup"><span data-stu-id="f59e1-198">Minimal 1.7 KB FLASH, RAM size.</span></span>
* <span data-ttu-id="f59e1-199">Resolución dinámica de direcciones MAC de 32 bits IPv4 y 48 bits.</span><span class="sxs-lookup"><span data-stu-id="f59e1-199">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses.</span></span>
* <span data-ttu-id="f59e1-200">Validado por IxANVL de IXIA.</span><span class="sxs-lookup"><span data-stu-id="f59e1-200">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="f59e1-201">Caché de ARP flexible y definida por el usuario.</span><span class="sxs-lookup"><span data-stu-id="f59e1-201">Flexible, user-defined ARP cache.</span></span>
* <span data-ttu-id="f59e1-202">Compatibilidad con ARP gratuita.</span><span class="sxs-lookup"><span data-stu-id="f59e1-202">Gratuitous ARP support.</span></span>
* <span data-ttu-id="f59e1-203">Estadísticas de ARP/RARP opcionales determinadas por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f59e1-203">Optional ARP/RARP statistics determined by application.</span></span>
* <span data-ttu-id="f59e1-204">Seguimiento de nivel de sistema mediante Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="f59e1-204">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="f59e1-205">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span><span class="sxs-lookup"><span data-stu-id="f59e1-205">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="f59e1-206">Comprobación de interoperabilidad</span><span class="sxs-lookup"><span data-stu-id="f59e1-206">Interoperability verification</span></span>

<span data-ttu-id="f59e1-207">Azure RTOS NetX se ajusta a los estándares RFC y ofrece una interoperabilidad completa con los dispositivos de la mayoría de los proveedores.</span><span class="sxs-lookup"><span data-stu-id="f59e1-207">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="f59e1-208">Azure RTOS NetX también emplea el estándar del sector IxANVL (Biblioteca de validación de red automatizada) para la implementación del protocolo TCP/IP principal de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="f59e1-208">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="f59e1-209">Tecnología avanzada</span><span class="sxs-lookup"><span data-stu-id="f59e1-209">Advanced technology</span></span>

<span data-ttu-id="f59e1-210">Azure RTOS NetX es una tecnología avanzada que incluye los elementos siguientes.</span><span class="sxs-lookup"><span data-stu-id="f59e1-210">Azure RTOS NetX is advanced technology that includes the following.</span></span>
* <span data-ttu-id="f59e1-211">Arquitectura Piconet™.</span><span class="sxs-lookup"><span data-stu-id="f59e1-211">Piconet™ architecture.</span></span>
* <span data-ttu-id="f59e1-212">Escalado automático.</span><span class="sxs-lookup"><span data-stu-id="f59e1-212">Automatic scaling.</span></span>
* <span data-ttu-id="f59e1-213">Tecnología UDP Fast-Path™.</span><span class="sxs-lookup"><span data-stu-id="f59e1-213">UDP Fast-Path Technology™.</span></span>
* <span data-ttu-id="f59e1-214">Administración de paquetes flexible.</span><span class="sxs-lookup"><span data-stu-id="f59e1-214">Flexible packet management.</span></span>
* <span data-ttu-id="f59e1-215">Implementación y API sin copia.</span><span class="sxs-lookup"><span data-stu-id="f59e1-215">Zero-copy API and implementation.</span></span>
* <span data-ttu-id="f59e1-216">Compatibilidad con hosts múltiples.</span><span class="sxs-lookup"><span data-stu-id="f59e1-216">Multi-homed support.</span></span>
* <span data-ttu-id="f59e1-217">Tiempo de espera opcional en todas las suspensiones.</span><span class="sxs-lookup"><span data-stu-id="f59e1-217">Optional timeout on all suspension.</span></span>
* <span data-ttu-id="f59e1-218">Compatibilidad con enrutamiento estático.</span><span class="sxs-lookup"><span data-stu-id="f59e1-218">Static routing support.</span></span>
* <span data-ttu-id="f59e1-219">Compatibilidad con el análisis del sistema de Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="f59e1-219">Azure RTOS TraceX system analysis support.</span></span>
