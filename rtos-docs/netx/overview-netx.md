---
title: Descripción de Azure RTOS NetX
description: Azure RTOS NetX es una implementación de alto rendimiento de los estándares del protocolo TCP/IP, totalmente integrada con Azure RTOS ThreadX y disponible para todos los procesadores compatibles.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 029f73b755d5c40279125fb010ec35baaaf7f38d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814442"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="14f69-103">Introducción a Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="14f69-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="14f69-104">Azure RTOS NetX es una pila de red insertada en IPv4 TCP/IP y de nivel industrial diseñada específicamente para aplicaciones de IoT, en tiempo real y profundamente insertadas.</span><span class="sxs-lookup"><span data-stu-id="14f69-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="14f69-105">Azure RTOS NetX es la pila de red IPv4 original de Microsoft y es esencialmente un subconjunto de Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="14f69-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="14f69-106">NetX proporciona aplicaciones insertadas con los principales protocolos de red, como IPv4, TCP y UDP, así como un conjunto completo de protocolos adicionales de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="14f69-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="14f69-107">Una pequeña superficie, una ejecución rápida y una facilidad de uso superior hacen que Azure RTOS NetX sea una opción ideal para las aplicaciones de IoT integradas más exigentes.</span><span class="sxs-lookup"><span data-stu-id="14f69-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="14f69-108">Protocolos de API</span><span class="sxs-lookup"><span data-stu-id="14f69-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="14f69-109">TELNET</span><span class="sxs-lookup"><span data-stu-id="14f69-109">TELNET</span></span>

* <span data-ttu-id="14f69-110">Mínimo 0,5 KB y una superficie de RAM de 0,3 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-110">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="14f69-111">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="14f69-111">Client and server support</span></span>
* <span data-ttu-id="14f69-112">API de Telnet intuitivas: *nx_telnet_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-112">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="auto-ip"></a><span data-ttu-id="14f69-113">IP automática</span><span class="sxs-lookup"><span data-stu-id="14f69-113">Auto IP</span></span>

* <span data-ttu-id="14f69-114">Asignación automática de direcciones IPv4</span><span class="sxs-lookup"><span data-stu-id="14f69-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="14f69-115">Mínimo 1,2 KB, 300 bytes de RAM</span><span class="sxs-lookup"><span data-stu-id="14f69-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="14f69-116">API de IP automática intuitivas: *nx_autoip_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="14f69-117">HTTP - Protocolo de transferencia de hipertexto (HTTP)</span><span class="sxs-lookup"><span data-stu-id="14f69-117">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="14f69-118">Memoria flash mínima 2,8 KB a 4,8 KB, superficie de RAM de 0,4 KB a 1,0 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-118">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint</span></span>
* <span data-ttu-id="14f69-119">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="14f69-119">Client and server support</span></span>
* <span data-ttu-id="14f69-120">API de HTTP intuitivas: *nx_http_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-120">Intuitive HTTP APIs: *nx_http_\**</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="14f69-121">SMTP - Protocolo simple de transferencia de correo (SMTP)</span><span class="sxs-lookup"><span data-stu-id="14f69-121">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="14f69-122">Mínimo 4,1 KB y una superficie de RAM de 0,6 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-122">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="14f69-123">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="14f69-123">Client support</span></span>
* <span data-ttu-id="14f69-124">API de SMTP intuitivas: *nx_smtp_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-124">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="14f69-125">DHCP - Protocolo de configuración dinámica de host (DHCP)</span><span class="sxs-lookup"><span data-stu-id="14f69-125">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="14f69-126">Memoria flash mínima de 3,6 KB a 4,6 KB, superficie de RAM de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-126">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="14f69-127">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="14f69-127">Client and server support</span></span>
* <span data-ttu-id="14f69-128">Compatibilidad con IPv4</span><span class="sxs-lookup"><span data-stu-id="14f69-128">IPv4 support</span></span>
* <span data-ttu-id="14f69-129">API de DHCP intuitiva: *nx_dhcp_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-129">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="14f69-130">P0P3: Protocolo de oficina de correos, versión 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="14f69-130">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="14f69-131">Mínimo 8,1 KB y una superficie de RAM de 1,4 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-131">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="14f69-132">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="14f69-132">Client support</span></span>
* <span data-ttu-id="14f69-133">API de POP3 intuitivas: *nx_pop3_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-133">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="14f69-134">SNMP - Protocolo simple de administración de redes (SNMP)</span><span class="sxs-lookup"><span data-stu-id="14f69-134">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="14f69-135">Mínimo 10,9 KB y una superficie de RAM de 2,6 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-135">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="14f69-136">Compatibilidad del agente con V1, V2 y V3</span><span class="sxs-lookup"><span data-stu-id="14f69-136">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="14f69-137">API de SNMP intuitivas: *nx_snmp_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-137">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="14f69-138">FTP, TFTP - Protocolo de transferencia de archivos (FTP), Protocolo trivial de transferencia de archivos (TFTP)</span><span class="sxs-lookup"><span data-stu-id="14f69-138">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="14f69-139">FTP: memoria flash mínima de 1,8 KB a 7,2 KB y superficie de RAM de 0,6 KB a 2,1 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-139">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="14f69-140">TFTP: memoria flash mínima de 1,7 KB a 2,4 KB y superficie de RAM de 0,3 KB a 1,8 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-140">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="14f69-141">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="14f69-141">Client and server support</span></span>
* <span data-ttu-id="14f69-142">API intuitivas de FTP y TFTP: <i>nx_ftp_ *</i> o <i>nx_tftp_* </i></span><span class="sxs-lookup"><span data-stu-id="14f69-142">Intuitive FTP and TFTP APIs: <i>nx_ftp_ *</i> or <i>nx_tftp_*</i></span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="14f69-143">PPP - Protocolo punto a punto (PPP)</span><span class="sxs-lookup"><span data-stu-id="14f69-143">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="14f69-144">Mínimo 7,1 KB y una superficie de RAM de 3,8 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-144">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="14f69-145">API de PPP intuitivas: *nx_ppp_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-145">Intuitive PPP APIs: *nx_ppp_\**</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="14f69-146">SNTP-Protocolo simple de tiempo de red (SNTP)</span><span class="sxs-lookup"><span data-stu-id="14f69-146">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="14f69-147">Mínimo 4 KB y una superficie de RAM de 0,5 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-147">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="14f69-148">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="14f69-148">Client support</span></span>
* <span data-ttu-id="14f69-149">API de SNTP intuitivas: *nx_sntp_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-149">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="14f69-150">API de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="14f69-150">Azure RTOS NetX API</span></span>

* <span data-ttu-id="14f69-151">API intuitivas y coherentes</span><span class="sxs-lookup"><span data-stu-id="14f69-151">Intuitive and consistent API</span></span>
* <span data-ttu-id="14f69-152">Convención de nomenclatura sustantivo-verbo</span><span class="sxs-lookup"><span data-stu-id="14f69-152">Noun-verb naming convention</span></span>
* <span data-ttu-id="14f69-153">Implementación rápida de la API sin copia</span><span class="sxs-lookup"><span data-stu-id="14f69-153">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="14f69-154">Todas las funciones de la API comienzan por <i>nx_\*</i> para identificarlas fácilmente como pertenecientes a Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="14f69-154">All API functions have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="14f69-155">Tiempo de espera de subproceso opcional para las funciones de la API de bloqueo</span><span class="sxs-lookup"><span data-stu-id="14f69-155">Blocking API functions have an optional thread timeout</span></span>
* <span data-ttu-id="14f69-156">Capa de BSD opcional para la portabilidad de código de sockets heredado</span><span class="sxs-lookup"><span data-stu-id="14f69-156">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="14f69-157">IGMP - Protocolo de administración de grupos de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="14f69-157">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="14f69-158">Memoria flash mínima de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-158">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="14f69-159">Compatibilidad con grupos de multidifusión IPv4</span><span class="sxs-lookup"><span data-stu-id="14f69-159">IPv4 multicast group support</span></span>
* <span data-ttu-id="14f69-160">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="14f69-160">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="14f69-161">Estadísticas de IGMP opcionales</span><span class="sxs-lookup"><span data-stu-id="14f69-161">Optional IGMP statistics</span></span>
* <span data-ttu-id="14f69-162">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="14f69-162">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="14f69-163">API de IGMP intuitivas: *nx_igmp_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-163">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="14f69-164">UDP - Protocolo de datagramas de usuario (UDP)</span><span class="sxs-lookup"><span data-stu-id="14f69-164">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="14f69-165">Memoria flash mínima de 2,5 KB, 124 bytes de RAM por socket</span><span class="sxs-lookup"><span data-stu-id="14f69-165">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="14f69-166">Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:</span><span class="sxs-lookup"><span data-stu-id="14f69-166">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="14f69-167">RX: 95 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 14 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="14f69-167">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="14f69-168">TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 10 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="14f69-168">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="14f69-169">Tecnología UDP Fast Path™</span><span class="sxs-lookup"><span data-stu-id="14f69-169">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="14f69-170">No hay límites en el número de UDP.</span><span class="sxs-lookup"><span data-stu-id="14f69-170">No limits on the number of UDP</span></span>
* <span data-ttu-id="14f69-171">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="14f69-171">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="14f69-172">Suspensión opcional en la recepción de sockets</span><span class="sxs-lookup"><span data-stu-id="14f69-172">Optional suspension on socket receive</span></span>
* <span data-ttu-id="14f69-173">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="14f69-173">Optional timeout on all suspension</span></span>
* <span data-ttu-id="14f69-174">Estadísticas de UDP opcionales</span><span class="sxs-lookup"><span data-stu-id="14f69-174">Optional UDP statistics</span></span>
* <span data-ttu-id="14f69-175">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="14f69-175">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="14f69-176">API de UDP intuitivas: *nx_udp_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-176">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="14f69-177">TCP - Protocolo de control de transmisión (TCP)</span><span class="sxs-lookup"><span data-stu-id="14f69-177">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="14f69-178">Memoria flash mínima de 10,5 KB a 12,5 KB, 280 bytes de RAM por socket</span><span class="sxs-lookup"><span data-stu-id="14f69-178">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="14f69-179">Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:</span><span class="sxs-lookup"><span data-stu-id="14f69-179">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="14f69-180">RX: 93 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 20 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="14f69-180">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="14f69-181">TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 27 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="14f69-181">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="14f69-182">Conexión confiable</span><span class="sxs-lookup"><span data-stu-id="14f69-182">Reliable connection</span></span>
* <span data-ttu-id="14f69-183">No hay límites en el número de sockets de TCP</span><span class="sxs-lookup"><span data-stu-id="14f69-183">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="14f69-184">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="14f69-184">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="14f69-185">Suspensión opcional en la recepción y transmisión de sockets</span><span class="sxs-lookup"><span data-stu-id="14f69-185">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="14f69-186">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="14f69-186">Optional timeout on all suspension</span></span>
* <span data-ttu-id="14f69-187">Estadísticas de TCP opcionales</span><span class="sxs-lookup"><span data-stu-id="14f69-187">Optional TCP statistics</span></span>
* <span data-ttu-id="14f69-188">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="14f69-188">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="14f69-189">API de TCP intuitivas: *nx_tcp_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-189">Intuitive TCP APIs:  *nx_tcp_\**</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="14f69-190">ICMP - Protocolo de mensajes de control de Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="14f69-190">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="14f69-191">Memoria flash mínima de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-191">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="14f69-192">Compatibilidad con IPv4</span><span class="sxs-lookup"><span data-stu-id="14f69-192">IPv4 support</span></span>
* <span data-ttu-id="14f69-193">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="14f69-193">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="14f69-194">Solicitud de ping y respuesta de ping</span><span class="sxs-lookup"><span data-stu-id="14f69-194">Ping request and ping response</span></span>
* <span data-ttu-id="14f69-195">Suspensión de subprocesos opcional en solicitudes de ping</span><span class="sxs-lookup"><span data-stu-id="14f69-195">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="14f69-196">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="14f69-196">Optional timeout on all suspension</span></span>
* <span data-ttu-id="14f69-197">Estadísticas de ICMP opcionales</span><span class="sxs-lookup"><span data-stu-id="14f69-197">Optional ICMP statistics</span></span>
* <span data-ttu-id="14f69-198">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="14f69-198">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="14f69-199">API de ICMP intuitivas: *nx_icmp_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-199">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="14f69-200">IPv4 - Protocolo de Internet (IP)</span><span class="sxs-lookup"><span data-stu-id="14f69-200">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="14f69-201">Memoria flash mínima de 3,5 KB a 8,5 KB y superficie de RAM de 2 KB a 3 KB</span><span class="sxs-lookup"><span data-stu-id="14f69-201">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="14f69-202">Arquitectura Piconet™</span><span class="sxs-lookup"><span data-stu-id="14f69-202">Piconet™ Architecture</span></span>
* <span data-ttu-id="14f69-203">Rendimiento rápido, casi a la velocidad del cableado</span><span class="sxs-lookup"><span data-stu-id="14f69-203">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="14f69-204">Compatibilidad con varias interfaces</span><span class="sxs-lookup"><span data-stu-id="14f69-204">Multiple interface support</span></span>
* <span data-ttu-id="14f69-205">Compatibilidad con host múltiple</span><span class="sxs-lookup"><span data-stu-id="14f69-205">Multihomed support</span></span>
* <span data-ttu-id="14f69-206">Compatibilidad con enrutamiento estático</span><span class="sxs-lookup"><span data-stu-id="14f69-206">Static routing support</span></span>
* <span data-ttu-id="14f69-207">Compatibilidad con la fragmentación IP y el reensamblado</span><span class="sxs-lookup"><span data-stu-id="14f69-207">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="14f69-208">Compatibilidad con IPv4</span><span class="sxs-lookup"><span data-stu-id="14f69-208">IPv4 Support</span></span>
* <span data-ttu-id="14f69-209">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="14f69-209">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="14f69-210">Certificación de logotipo preparado para fase II</span><span class="sxs-lookup"><span data-stu-id="14f69-210">Phase II Ready Logo Certification</span></span>
* <span data-ttu-id="14f69-211">Estadísticas de IP opcionales</span><span class="sxs-lookup"><span data-stu-id="14f69-211">Optional IP statistics</span></span>
* <span data-ttu-id="14f69-212">Interfaz del controlador de la capa física bien definida e intuitiva</span><span class="sxs-lookup"><span data-stu-id="14f69-212">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="14f69-213">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="14f69-213">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="14f69-214">API de capa de IP intuitivas: *nx_ip_\** , *nxd_ip_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-214">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**</span></span>
* <span data-ttu-id="14f69-215">Certificado previamente por TUV y UL para CEI 61508 SIL 4, CEI 62304 clase C, ISO 26262 ASIL D y EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="14f69-215">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="14f69-216">ARP/RARP - Protocolo de resolución de direcciones (ARP), Protocolo de resolución inversa de direcciones (RARP)</span><span class="sxs-lookup"><span data-stu-id="14f69-216">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="14f69-217">Memoria flash mínima de 1,7 KB, tamaño de RAM</span><span class="sxs-lookup"><span data-stu-id="14f69-217">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="14f69-218">Resolución dinámica de direcciones MAC de 32 bits IPv4 y 48 bits</span><span class="sxs-lookup"><span data-stu-id="14f69-218">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="14f69-219">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="14f69-219">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="14f69-220">Memoria caché de ARP flexible y definida por el usuario</span><span class="sxs-lookup"><span data-stu-id="14f69-220">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="14f69-221">Compatibilidad con ARP gratuito</span><span class="sxs-lookup"><span data-stu-id="14f69-221">Gratuitous ARP support</span></span>
* <span data-ttu-id="14f69-222">Estadísticas de ARP/RARP opcionales determinadas por la aplicación</span><span class="sxs-lookup"><span data-stu-id="14f69-222">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="14f69-223">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="14f69-223">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="14f69-224">API de ARP/RARP intuitivas: *nx_arp_\** , *nx_rarp_\**</span><span class="sxs-lookup"><span data-stu-id="14f69-224">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="14f69-225">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span><span class="sxs-lookup"><span data-stu-id="14f69-225">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="small-footprint"></a><span data-ttu-id="14f69-226">Superficie pequeña</span><span class="sxs-lookup"><span data-stu-id="14f69-226">Small-footprint</span></span>

<span data-ttu-id="14f69-227">Azure RTOS NetX tiene una superficie notablemente pequeña, de 9 KB a 15 KB, para la compatibilidad básica con IP y UDP.</span><span class="sxs-lookup"><span data-stu-id="14f69-227">Azure RTOS NetX has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="14f69-228">Se necesita una memoria de área de instrucciones adicional de 10 KB a 13 KB para la funcionalidad de TCP.</span><span class="sxs-lookup"><span data-stu-id="14f69-228">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="14f69-229">El uso de RAM de Azure RTOS NetX suele oscilar entre 2,6 KB y 3,6 KB más la memoria del grupo de paquetes, definida por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="14f69-229">Azure RTOS NetX RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="14f69-230">Al igual que Azure RTOS ThreadX, el tamaño de Azure RTOS NetX se escala automáticamente en función de los servicios que usa la aplicación.</span><span class="sxs-lookup"><span data-stu-id="14f69-230">Like Azure RTOS ThreadX, the size of Azure RTOS NetX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="14f69-231">Esto elimina prácticamente la necesidad de configuraciones y parámetros de compilación complicados, lo que facilita el trabajo del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="14f69-231">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="14f69-232">Ejecución rápida</span><span class="sxs-lookup"><span data-stu-id="14f69-232">Fast execution</span></span>

<span data-ttu-id="14f69-233">Azure RTOS NetX proporciona una implementación de envío y recepción de paquetes sin copia, y está muy integrada con Azure RTOS ThreadX, para lograr el rendimiento más rápido posible.</span><span class="sxs-lookup"><span data-stu-id="14f69-233">Azure RTOS NetX provides a zero-copy packet send/receive implementation and is highly integrated with Azure RTOS ThreadX to achieve the fastest possible performance.</span></span> <span data-ttu-id="14f69-234">Por ejemplo, Azure RTOS NetX normalmente puede lograr transferencias de datos cercanas a la velocidad del cableado en un procesador de 80 MHz (o menos), en tanto que se usa un pequeño porcentaje de ciclos del procesador.</span><span class="sxs-lookup"><span data-stu-id="14f69-234">For example, Azure RTOS NetX can typically achieve near wirespeed data transfers on an 80-MHz processor (or less), while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="14f69-235">Simple y fácil de usar</span><span class="sxs-lookup"><span data-stu-id="14f69-235">Simple, easy-to-use</span></span>

<span data-ttu-id="14f69-236">Azure RTOS NetX es fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="14f69-236">Azure RTOS NetX is simple to use.</span></span> <span data-ttu-id="14f69-237">La API de Azure RTOS NetX es intuitiva y altamente funcional.</span><span class="sxs-lookup"><span data-stu-id="14f69-237">The Azure RTOS NetX API is both intuitive and highly functional.</span></span> <span data-ttu-id="14f69-238">Los nombres de API se componen de palabras reales y no de la sopa de letras de nombres muy abreviados que son tan comunes en otros productos de redes.</span><span class="sxs-lookup"><span data-stu-id="14f69-238">The API names are made of real words and not “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="14f69-239">Todas las API de Azure RTOS NetX tienen *nx_* al inicio y siguen una convención de nomenclatura sustantivo-verbo.</span><span class="sxs-lookup"><span data-stu-id="14f69-239">All Azure RTOS NetX APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="14f69-240">Además, existe una coherencia funcional en la API.</span><span class="sxs-lookup"><span data-stu-id="14f69-240">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="14f69-241">Por ejemplo, todas las funciones de API que se suspenden tienen un tiempo de espera opcional que funciona de forma idéntica.</span><span class="sxs-lookup"><span data-stu-id="14f69-241">For example, all API functions that suspend have an optional timeout that functions in an identical manner.</span></span> <span data-ttu-id="14f69-242">En el caso de las aplicaciones heredadas, Azure RTOS NetX ofrece una capa adicional compatible con sockets BSD.</span><span class="sxs-lookup"><span data-stu-id="14f69-242">For legacy applications, Azure RTOS NetX offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="14f69-243">Esta capa ayuda a los desarrolladores a migrar fácilmente aplicaciones de redes de gran tamaño.</span><span class="sxs-lookup"><span data-stu-id="14f69-243">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="14f69-244">Comprobación de interoperabilidad</span><span class="sxs-lookup"><span data-stu-id="14f69-244">Interoperability verification</span></span>

<span data-ttu-id="14f69-245">Azure RTOS NetX se ajusta a los estándares RFC y ofrece una interoperabilidad completa con los dispositivos de la mayoría de los proveedores.</span><span class="sxs-lookup"><span data-stu-id="14f69-245">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="14f69-246">Azure RTOS NetX también emplea el estándar del sector IxANVL (Biblioteca de validación de red automatizada) para la implementación del protocolo TCP/IP principal de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="14f69-246">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="14f69-247">Tecnología avanzada</span><span class="sxs-lookup"><span data-stu-id="14f69-247">Advanced technology</span></span>

<span data-ttu-id="14f69-248">Azure RTOS NetX es una tecnología avanzada que incluye:</span><span class="sxs-lookup"><span data-stu-id="14f69-248">Azure RTOS NetX is advanced technology that includes:</span></span>

* <span data-ttu-id="14f69-249">Arquitectura Piconet™</span><span class="sxs-lookup"><span data-stu-id="14f69-249">Piconet™ architecture</span></span>
* <span data-ttu-id="14f69-250">ajustar escala automáticamente</span><span class="sxs-lookup"><span data-stu-id="14f69-250">automatic scaling</span></span>
* <span data-ttu-id="14f69-251">Tecnología UDP Fast-Path™</span><span class="sxs-lookup"><span data-stu-id="14f69-251">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="14f69-252">Administración de paquetes flexible</span><span class="sxs-lookup"><span data-stu-id="14f69-252">flexible packet management</span></span>
* <span data-ttu-id="14f69-253">Implementación y API sin copia</span><span class="sxs-lookup"><span data-stu-id="14f69-253">zero-copy API and implementation</span></span>
* <span data-ttu-id="14f69-254">Compatibilidad con host múltiple</span><span class="sxs-lookup"><span data-stu-id="14f69-254">multihomed support</span></span>
* <span data-ttu-id="14f69-255">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="14f69-255">optional timeout on all suspension</span></span>
* <span data-ttu-id="14f69-256">Compatibilidad con enrutamiento estático</span><span class="sxs-lookup"><span data-stu-id="14f69-256">static routing support</span></span>
* <span data-ttu-id="14f69-257">Compatibilidad con el análisis del sistema de Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="14f69-257">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="14f69-258">Tiempo de comercialización más rápido</span><span class="sxs-lookup"><span data-stu-id="14f69-258">Fastest time-to-market</span></span>

<span data-ttu-id="14f69-259">Azure RTOS NetX es fácil de instalar, conocer, usar, depurar, comprobar, certificar y mantener.</span><span class="sxs-lookup"><span data-stu-id="14f69-259">Azure RTOS NetX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="14f69-260">Como resultado, Azure RTOS NetX es una de las pilas TCP/IP más populares para dispositivos IoT integrados, incluidos muchos SoC de Broadcom, GainSpan, etc.</span><span class="sxs-lookup"><span data-stu-id="14f69-260">As a result, Azure RTOS NetX is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, and so forth.</span></span> <span data-ttu-id="14f69-261">Nuestra ventaja continua de plazo de comercialización se basa en lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="14f69-261">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="14f69-262">Documentación de calidad: consulte nuestra [guía de usuario de Azure RTOS NetX](about-this-guide.md) y véalo personalmente.</span><span class="sxs-lookup"><span data-stu-id="14f69-262">quality documentation – please review our [Azure RTOS NetX User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="14f69-263">Disponibilidad completa del código fuente</span><span class="sxs-lookup"><span data-stu-id="14f69-263">complete source code availability</span></span>
* <span data-ttu-id="14f69-264">API fáciles de usar</span><span class="sxs-lookup"><span data-stu-id="14f69-264">easy-to-use API</span></span>
* <span data-ttu-id="14f69-265">Conjunto de características completo y avanzado</span><span class="sxs-lookup"><span data-stu-id="14f69-265">comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="14f69-266">Una licencia sencilla</span><span class="sxs-lookup"><span data-stu-id="14f69-266">One Simple License</span></span>

<span data-ttu-id="14f69-267">No hay ningún costo asociado al uso y las pruebas del código fuente ni a las licencias de producción si se implementa en dispositivos con licencia previa; todos los demás dispositivos necesitan una licencia anual sencilla.</span><span class="sxs-lookup"><span data-stu-id="14f69-267">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="14f69-268">Código fuente completo y de máxima calidad</span><span class="sxs-lookup"><span data-stu-id="14f69-268">Full, highest-quality source code</span></span>

<span data-ttu-id="14f69-269">A lo largo de los años, el código fuente de Azure RTOS NetX ha marcado el listón en calidad y facilidad de comprensión.</span><span class="sxs-lookup"><span data-stu-id="14f69-269">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="14f69-270">Además, la convención de tener una función por archivo facilita la navegación por el origen.</span><span class="sxs-lookup"><span data-stu-id="14f69-270">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="14f69-271">Compatible con las arquitecturas más populares</span><span class="sxs-lookup"><span data-stu-id="14f69-271">Supports most popular architectures</span></span>

<span data-ttu-id="14f69-272">Azure RTOS NetX se ejecuta en los microprocesadores de 32 y 64 bits más populares, de serie, totalmente probado y totalmente compatible, incluidas las siguientes arquitecturas avanzadas:</span><span class="sxs-lookup"><span data-stu-id="14f69-272">Azure RTOS NetX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="14f69-273">**Dispositivos analógicos**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="14f69-273">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="14f69-274">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="14f69-274">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="14f69-275">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="14f69-275">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="14f69-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="14f69-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="14f69-277">**Cadence**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="14f69-277">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="14f69-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="14f69-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="14f69-279">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="14f69-279">**Cypress**: RISC-V</span></span>

<span data-ttu-id="14f69-280">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="14f69-280">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="14f69-281">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="14f69-281">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="14f69-282">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="14f69-282">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="14f69-283">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="14f69-283">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="14f69-284">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="14f69-284">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="14f69-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="14f69-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="14f69-286">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="14f69-286">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="14f69-287">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="14f69-287">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="14f69-288">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="14f69-288">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="14f69-289">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="14f69-289">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="14f69-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="14f69-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="14f69-291">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="14f69-291">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="14f69-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="14f69-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="14f69-293">*Todas las cifras de tiempos y tamaños enumeradas son estimaciones y pueden ser diferentes en su plataforma de desarrollo.*</span><span class="sxs-lookup"><span data-stu-id="14f69-293">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
