---
title: Descripción de Azure RTOS NetX Duo
description: Azure RTOS NetX Duo es una pila de red TCP/IP avanzada y de clase industrial diseñada específicamente para aplicaciones IoT y en tiempo real con alto grado de inserción.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 2339da391e52b437a2111ae439cccf41e038bdcf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815337"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="68c03-103">Introducción a Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="68c03-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="68c03-104">La pila de red TCP/IP insertada de Azure RTOS NetX Duo es la pila de red TCP/IP dual para IPv4 e IPv6 de clase industrial de Microsoft, que está diseñada específicamente para aplicaciones IoT, en tiempo real y con alto grado de inserción.</span><span class="sxs-lookup"><span data-stu-id="68c03-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="68c03-105">NetX Duo proporciona aplicaciones insertadas con los principales protocolos de red, como IPv4, IPv6, TCP y UDP, así como un conjunto completo de protocolos adicionales de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="68c03-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="68c03-106">Azure RTOS NetX Duo ofrece seguridad mediante productos adicionales de seguridad como complementos, entre los que se incluyen IPsec y SSL/TLS/DTLS de Azure RTOS NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="68c03-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="68c03-107">Todo esto, combinado con una pequeña superficie, una ejecución rápida y una facilidad de uso superior, hacen que Azure RTOS NetX Duo sea la opción ideal para las aplicaciones IoT insertadas más exigentes.</span><span class="sxs-lookup"><span data-stu-id="68c03-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="68c03-108">Protocolos de API</span><span class="sxs-lookup"><span data-stu-id="68c03-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="68c03-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="68c03-109">MQTT</span></span>

* <span data-ttu-id="68c03-110">Transporte de telemetría de cola de mensajes (MQTT)</span><span class="sxs-lookup"><span data-stu-id="68c03-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="68c03-111">Memoria flash mínima de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-111">Minimal 2.7 KB FLASH</span></span>
* <span data-ttu-id="68c03-112">API de MQTT intuitivas: *nx_mqtt_* \*</span><span class="sxs-lookup"><span data-stu-id="68c03-112">Intuitive MQTT APIs: *nx_mqtt_*\*</span></span>

### <a name="auto-ip"></a><span data-ttu-id="68c03-113">IP automática</span><span class="sxs-lookup"><span data-stu-id="68c03-113">Auto IP</span></span>

* <span data-ttu-id="68c03-114">Asignación automática de direcciones IPv4</span><span class="sxs-lookup"><span data-stu-id="68c03-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="68c03-115">1,2 KB como mínimo, 300 bytes de RAM</span><span class="sxs-lookup"><span data-stu-id="68c03-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="68c03-116">API de IP automática intuitivas: *nx_autoip_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http-https"></a><span data-ttu-id="68c03-117">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="68c03-117">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="68c03-118">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="68c03-118">HTTP 1.0</span></span>

* <span data-ttu-id="68c03-119">Protocolo de transferencia de hipertexto (HTTP)</span><span class="sxs-lookup"><span data-stu-id="68c03-119">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="68c03-120">Memoria flash mínima de 2,8 KB a 4,8 KB y de 0,4 KB a 1,0 KB de RAM</span><span class="sxs-lookup"><span data-stu-id="68c03-120">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="68c03-121">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="68c03-121">Client and server support</span></span>
* <span data-ttu-id="68c03-122">API intuitivas: *nx_http_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-122">Intuitive APIs: *nx_http_\**</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="68c03-123">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="68c03-123">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="68c03-124">Protocolo de transferencia de hipertexto (HTTP)</span><span class="sxs-lookup"><span data-stu-id="68c03-124">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="68c03-125">Memoria flash mínima de 3,0 KB a 9,5 KB y de 0,5 KB a 2 KB de RAM</span><span class="sxs-lookup"><span data-stu-id="68c03-125">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="68c03-126">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="68c03-126">Client and server support</span></span>
* <span data-ttu-id="68c03-127">Varias sesiones de cliente entrantes</span><span class="sxs-lookup"><span data-stu-id="68c03-127">Multiple incoming client sessions</span></span>
* <span data-ttu-id="68c03-128">Texto sin formato y HTTPS cifrado</span><span class="sxs-lookup"><span data-stu-id="68c03-128">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="68c03-129">Compatibilidad con conexiones persistentes</span><span class="sxs-lookup"><span data-stu-id="68c03-129">Persistent connection support</span></span>
* <span data-ttu-id="68c03-130">Carga de archivos de varias partes</span><span class="sxs-lookup"><span data-stu-id="68c03-130">Multipart file upload</span></span>
* <span data-ttu-id="68c03-131">Totalmente integrado con TLS de Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="68c03-131">Fully integrated with Azure RTOS NetX Secure TLS</span></span>
* <span data-ttu-id="68c03-132">API intuitivas: *nx_web_http\**</span><span class="sxs-lookup"><span data-stu-id="68c03-132">Intuitive APIs: *nx_web_http\**</span></span>

### <a name="smtp"></a><span data-ttu-id="68c03-133">SMTP</span><span class="sxs-lookup"><span data-stu-id="68c03-133">SMTP</span></span>

* <span data-ttu-id="68c03-134">Protocolo simple de transferencia de correo (SMTP)</span><span class="sxs-lookup"><span data-stu-id="68c03-134">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="68c03-135">Mínimo 4,1 KB y una superficie de RAM de 0,6 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-135">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-136">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="68c03-136">Client support</span></span>
* <span data-ttu-id="68c03-137">API de SMTP intuitivas: *nx_smtp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-137">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp"></a><span data-ttu-id="68c03-138">DHCP</span><span class="sxs-lookup"><span data-stu-id="68c03-138">DHCP</span></span>

* <span data-ttu-id="68c03-139">Protocolo de configuración dinámica de host (DHCP)</span><span class="sxs-lookup"><span data-stu-id="68c03-139">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="68c03-140">Memoria flash mínima de 3,6 KB a 4,6 KB y superficie de RAM de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-140">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-141">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="68c03-141">Client and server support</span></span>
* <span data-ttu-id="68c03-142">Compatibilidad con IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="68c03-142">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="68c03-143">API de DHCP intuitivas: *nx_dhcp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-143">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="nat"></a><span data-ttu-id="68c03-144">NAT</span><span class="sxs-lookup"><span data-stu-id="68c03-144">NAT</span></span>

* <span data-ttu-id="68c03-145">Traducción de direcciones de red (NAT)</span><span class="sxs-lookup"><span data-stu-id="68c03-145">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="68c03-146">Mínimo 3,5 KB y una superficie de RAM de 0,6 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-146">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-147">Compatibilidad con direcciones IPv4</span><span class="sxs-lookup"><span data-stu-id="68c03-147">IPv4 address support</span></span>
* <span data-ttu-id="68c03-148">API de NAT intuitivas: *nx_nat_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-148">Intuitive NAT APIs: *nx_nat_\**</span></span>
* <span data-ttu-id="68c03-149">NAT solo está disponible con Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="68c03-149">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="68c03-150">SNMP</span><span class="sxs-lookup"><span data-stu-id="68c03-150">SNMP</span></span>

* <span data-ttu-id="68c03-151">Protocolo simple de administración de redes (SNMP)</span><span class="sxs-lookup"><span data-stu-id="68c03-151">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="68c03-152">Mínimo 10,9 KB y una superficie de RAM de 2,6 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-152">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-153">Compatibilidad del agente con V1, V2 y V3</span><span class="sxs-lookup"><span data-stu-id="68c03-153">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="68c03-154">API de SNMP intuitivas: *nx_snmp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-154">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="68c03-155">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="68c03-155">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="68c03-156">Sistema de nombres de dominio (DNS)</span><span class="sxs-lookup"><span data-stu-id="68c03-156">Domain Name System (DNS)</span></span>
* <span data-ttu-id="68c03-157">Sistema de nombres de dominio de multidifusión (mDNS)</span><span class="sxs-lookup"><span data-stu-id="68c03-157">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="68c03-158">Detección de servicios basada en DNS (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="68c03-158">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="68c03-159">DNS: Memoria flash mínima de 2,4 KB a 3 KB y superficie de RAM de 1 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-159">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-160">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="68c03-160">Client support</span></span>
* <span data-ttu-id="68c03-161">API intuitivas: *nx_dns_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-161">Intuitive APIs: *nx_dns_\**</span></span>
* <span data-ttu-id="68c03-162">mDNS y DNS-SD solo están disponibles con Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="68c03-162">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="68c03-163">POP3</span><span class="sxs-lookup"><span data-stu-id="68c03-163">P0P3</span></span>

* <span data-ttu-id="68c03-164">Protocolo de oficina de correos versión 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="68c03-164">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="68c03-165">Mínimo 8,1 KB y una superficie de RAM de 1,4 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-165">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-166">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="68c03-166">Client support</span></span>
* <span data-ttu-id="68c03-167">API de POP3 intuitivas: *nx_pop3_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-167">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="telnet"></a><span data-ttu-id="68c03-168">TELNET</span><span class="sxs-lookup"><span data-stu-id="68c03-168">TELNET</span></span>

* <span data-ttu-id="68c03-169">Mínimo 0,5 KB y una superficie de RAM de 0,3 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-169">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-170">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="68c03-170">Client and server support</span></span>
* <span data-ttu-id="68c03-171">API de Telnet intuitivas: *nx_telnet_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-171">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="68c03-172">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="68c03-172">FTP, TFTP</span></span>

* <span data-ttu-id="68c03-173">Protocolo de transferencia de archivos (FTP)</span><span class="sxs-lookup"><span data-stu-id="68c03-173">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="68c03-174">Protocolo trivial de transferencia de archivos (TFTP)</span><span class="sxs-lookup"><span data-stu-id="68c03-174">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="68c03-175">FTP: memoria flash mínima de 1,8 KB a 7,2 KB y superficie de RAM de 0,6 KB a 2,1 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-175">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-176">TFTP: memoria flash mínima de 1,7 KB a 2,4 KB y superficie de RAM de 0,3 KB a 1,8 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-176">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-177">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="68c03-177">Client and server support</span></span>
* <span data-ttu-id="68c03-178">API intuitivas de FTP y TFTP: *nx_ftp_\** o *nx_tftp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-178">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="68c03-179">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="68c03-179">PPP, PPPoE</span></span>

* <span data-ttu-id="68c03-180">Protocolo punto a punto (PPP)</span><span class="sxs-lookup"><span data-stu-id="68c03-180">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="68c03-181">Protocolo punto a punto sobre Ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="68c03-181">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="68c03-182">Mínimo 7,1 KB y una superficie de RAM de 3,8 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-182">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-183">API de PPP intuitivas: *nx_ppp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-183">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="68c03-184">PPPoE solo está disponible con Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="68c03-184">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="68c03-185">SNTP</span><span class="sxs-lookup"><span data-stu-id="68c03-185">SNTP</span></span>

* <span data-ttu-id="68c03-186">Protocolo simple de tiempo de red (SNTP)</span><span class="sxs-lookup"><span data-stu-id="68c03-186">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="68c03-187">Mínimo 4 KB y una superficie de RAM de 0,5 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-187">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="68c03-188">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="68c03-188">Client support</span></span>
* <span data-ttu-id="68c03-189">API de SNTP intuitivas: *nx_sntp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-189">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="68c03-190">API de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="68c03-190">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="68c03-191">API intuitivas y coherentes</span><span class="sxs-lookup"><span data-stu-id="68c03-191">Intuitive and consistent API</span></span>
* <span data-ttu-id="68c03-192">Convención de nomenclatura sustantivo-verbo</span><span class="sxs-lookup"><span data-stu-id="68c03-192">Noun-verb naming convention</span></span>
* <span data-ttu-id="68c03-193">Implementación rápida de la API sin copia</span><span class="sxs-lookup"><span data-stu-id="68c03-193">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="68c03-194">Todas las API comienzan por <i>nx_\*</i> para identificarlas fácilmente como pertenecientes a Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="68c03-194">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="68c03-195">Las API de bloqueo tienen un tiempo de espera de subprocesos opcional</span><span class="sxs-lookup"><span data-stu-id="68c03-195">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="68c03-196">Consulte [Guía del usuario de Azure RTOS NetX Duo](about-this-guide.md) para más información.</span><span class="sxs-lookup"><span data-stu-id="68c03-196">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="68c03-197">Capa de BSD opcional para la portabilidad de código de sockets heredado</span><span class="sxs-lookup"><span data-stu-id="68c03-197">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="68c03-198">IGMP</span><span class="sxs-lookup"><span data-stu-id="68c03-198">IGMP</span></span>

* <span data-ttu-id="68c03-199">Protocolo de administración de grupos de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="68c03-199">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="68c03-200">Memoria flash mínima de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-200">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="68c03-201">Compatibilidad con grupos de multidifusión IPv4</span><span class="sxs-lookup"><span data-stu-id="68c03-201">IPv4 multicast group support</span></span>
* <span data-ttu-id="68c03-202">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="68c03-202">IXIA IxANVL validated</span></span>
* <span data-ttu-id="68c03-203">Estadísticas de IGMP opcionales</span><span class="sxs-lookup"><span data-stu-id="68c03-203">Optional IGMP statistics</span></span>
* <span data-ttu-id="68c03-204">Seguimiento de nivel de sistema mediante Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="68c03-204">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="68c03-205">API de IGMP intuitivas: *nx_igmp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-205">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="68c03-206">DTLS de Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="68c03-206">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="68c03-207">Seguridad de la capa de transporte del datagrama (DTLS) 1.0 y 1.2</span><span class="sxs-lookup"><span data-stu-id="68c03-207">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="68c03-208">Memoria flash mínima de 11 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-208">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="68c03-209">Tamaño de clave rápido con software RSA de 2048 bits ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="68c03-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="68c03-210">Implementación optimizada de X.509</span><span class="sxs-lookup"><span data-stu-id="68c03-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="68c03-211">Totalmente integrado con los sockets UDP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="68c03-211">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="68c03-212">Compatibilidad con el cifrado mediante hardware</span><span class="sxs-lookup"><span data-stu-id="68c03-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="68c03-213">Compatibilidad con criptografía de software: RSA (todos los tamaños de clave), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="68c03-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="68c03-214">Criptografía de curva elíptica (ECC) con ECDSA (firma) y ECDH (cifrado), incluidas las curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="68c03-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="68c03-215">Compatibilidad con claves cifradas (dependiente del hardware)</span><span class="sxs-lookup"><span data-stu-id="68c03-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="68c03-216">TLS de Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="68c03-216">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="68c03-217">Seguridad de la capa de transporte (TLS) 1.0, 1.1 y 1.2</span><span class="sxs-lookup"><span data-stu-id="68c03-217">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="68c03-218">Memoria flash mínima de 8,8 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-218">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="68c03-219">Tamaño de clave rápido con software RSA de 2048 bits ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="68c03-219">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="68c03-220">Implementación optimizada de X.509</span><span class="sxs-lookup"><span data-stu-id="68c03-220">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="68c03-221">Totalmente integrado con los sockets TCP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="68c03-221">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="68c03-222">Compatibilidad con el cifrado mediante hardware</span><span class="sxs-lookup"><span data-stu-id="68c03-222">Hardware Crypto Support</span></span>
* <span data-ttu-id="68c03-223">Compatibilidad con criptografía de software: RSA (todos los tamaños de clave), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="68c03-223">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="68c03-224">Criptografía de curva elíptica (ECC) con ECDSA (firma) y ECDH (cifrado), incluidas las curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="68c03-224">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="68c03-225">Compatibilidad con claves cifradas (dependiente del hardware)</span><span class="sxs-lookup"><span data-stu-id="68c03-225">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="68c03-226">ICMP</span><span class="sxs-lookup"><span data-stu-id="68c03-226">ICMP</span></span>

* <span data-ttu-id="68c03-227">Protocolo de mensajes de control de Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="68c03-227">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="68c03-228">Memoria flash mínima de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-228">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="68c03-229">Compatibilidad con IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="68c03-229">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="68c03-230">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="68c03-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="68c03-231">Solicitud de ping y respuesta de ping</span><span class="sxs-lookup"><span data-stu-id="68c03-231">Ping request and ping response</span></span>
* <span data-ttu-id="68c03-232">Suspensión de subprocesos opcional en solicitudes de ping</span><span class="sxs-lookup"><span data-stu-id="68c03-232">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="68c03-233">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="68c03-233">Optional timeout on all suspension</span></span>
* <span data-ttu-id="68c03-234">Estadísticas de ICMP opcionales</span><span class="sxs-lookup"><span data-stu-id="68c03-234">Optional ICMP statistics</span></span>
* <span data-ttu-id="68c03-235">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="68c03-235">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="68c03-236">API de ICMP intuitivas: *nx_icmp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-236">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="68c03-237">UDP</span><span class="sxs-lookup"><span data-stu-id="68c03-237">UDP</span></span>

* <span data-ttu-id="68c03-238">Protocolo de datagramas de usuario (UDP)</span><span class="sxs-lookup"><span data-stu-id="68c03-238">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="68c03-239">Memoria flash mínima de 2,5 KB, 124 bytes de RAM por socket</span><span class="sxs-lookup"><span data-stu-id="68c03-239">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="68c03-240">Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:</span><span class="sxs-lookup"><span data-stu-id="68c03-240">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="68c03-241">RX: 95 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 14 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="68c03-241">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="68c03-242">TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 10 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="68c03-242">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="68c03-243">Tecnología UDP Fast Path™</span><span class="sxs-lookup"><span data-stu-id="68c03-243">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="68c03-244">No hay límites en el número de UDP</span><span class="sxs-lookup"><span data-stu-id="68c03-244">No limits on the number of UDP</span></span>
* <span data-ttu-id="68c03-245">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="68c03-245">IXIA IxANVL validated</span></span>
* <span data-ttu-id="68c03-246">Suspensión opcional en la recepción de sockets</span><span class="sxs-lookup"><span data-stu-id="68c03-246">Optional suspension on socket receive</span></span>
* <span data-ttu-id="68c03-247">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="68c03-247">Optional timeout on all suspension</span></span>
* <span data-ttu-id="68c03-248">Estadísticas de UDP opcionales</span><span class="sxs-lookup"><span data-stu-id="68c03-248">Optional UDP statistics</span></span>
* <span data-ttu-id="68c03-249">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="68c03-249">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="68c03-250">API de UDP intuitivas: *nx_udp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-250">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="68c03-251">TCP</span><span class="sxs-lookup"><span data-stu-id="68c03-251">TCP</span></span>

* <span data-ttu-id="68c03-252">Protocolo de control de transmisión (TCP)</span><span class="sxs-lookup"><span data-stu-id="68c03-252">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="68c03-253">Memoria flash mínima de 10,5 KB a 12,5 KB, 280 bytes de RAM por socket</span><span class="sxs-lookup"><span data-stu-id="68c03-253">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="68c03-254">Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:</span><span class="sxs-lookup"><span data-stu-id="68c03-254">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="68c03-255">RX: 93 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 20 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="68c03-255">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="68c03-256">TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 27 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="68c03-256">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="68c03-257">Conexión confiable</span><span class="sxs-lookup"><span data-stu-id="68c03-257">Reliable connection</span></span>
* <span data-ttu-id="68c03-258">No hay límites en el número de sockets de TCP</span><span class="sxs-lookup"><span data-stu-id="68c03-258">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="68c03-259">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="68c03-259">IXIA IxANVL validated</span></span>
* <span data-ttu-id="68c03-260">Suspensión opcional en la recepción y transmisión de sockets</span><span class="sxs-lookup"><span data-stu-id="68c03-260">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="68c03-261">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="68c03-261">Optional timeout on all suspension</span></span>
* <span data-ttu-id="68c03-262">Estadísticas de TCP opcionales</span><span class="sxs-lookup"><span data-stu-id="68c03-262">Optional TCP statistics</span></span>
* <span data-ttu-id="68c03-263">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="68c03-263">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="68c03-264">API de TCP intuitivas: *nx_tcp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-264">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="68c03-265">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="68c03-265">ARP/RARP</span></span>

* <span data-ttu-id="68c03-266">Protocolo de resolución de direcciones (ARP)</span><span class="sxs-lookup"><span data-stu-id="68c03-266">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="68c03-267">Protocolo de resolución de direcciones inversa (RARP)</span><span class="sxs-lookup"><span data-stu-id="68c03-267">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="68c03-268">Memoria flash mínima de 1,7 KB, tamaño de RAM</span><span class="sxs-lookup"><span data-stu-id="68c03-268">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="68c03-269">Resolución dinámica de direcciones MAC de 32 bits IPv4 y 48 bits</span><span class="sxs-lookup"><span data-stu-id="68c03-269">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="68c03-270">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="68c03-270">IXIA IxANVL validated</span></span>
* <span data-ttu-id="68c03-271">Memoria caché de ARP flexible y definida por el usuario</span><span class="sxs-lookup"><span data-stu-id="68c03-271">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="68c03-272">Compatibilidad con ARP gratuito</span><span class="sxs-lookup"><span data-stu-id="68c03-272">Gratuitous ARP support</span></span>
* <span data-ttu-id="68c03-273">Estadísticas de ARP/RARP opcionales determinadas por la aplicación</span><span class="sxs-lookup"><span data-stu-id="68c03-273">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="68c03-274">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="68c03-274">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="68c03-275">API de ARP/RARP intuitivas: *nx_arp_\** , *nx_rarp_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-275">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="68c03-276">IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="68c03-276">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="68c03-277">Protocolo de Internet (IP)</span><span class="sxs-lookup"><span data-stu-id="68c03-277">Internet Protocol (IP)</span></span>
* <span data-ttu-id="68c03-278">Memoria flash mínima de 3,5 KB a 8,5 KB y superficie de RAM de 2 KB a 3 KB</span><span class="sxs-lookup"><span data-stu-id="68c03-278">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="68c03-279">Arquitectura Piconet™</span><span class="sxs-lookup"><span data-stu-id="68c03-279">Piconet™ architecture</span></span>
* <span data-ttu-id="68c03-280">Rendimiento rápido, casi a la velocidad del cableado</span><span class="sxs-lookup"><span data-stu-id="68c03-280">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="68c03-281">Compatibilidad con varias interfaces</span><span class="sxs-lookup"><span data-stu-id="68c03-281">Multiple interface support</span></span>
* <span data-ttu-id="68c03-282">Compatibilidad con host múltiple</span><span class="sxs-lookup"><span data-stu-id="68c03-282">Multihomed support</span></span>
* <span data-ttu-id="68c03-283">Compatibilidad con enrutamiento estático</span><span class="sxs-lookup"><span data-stu-id="68c03-283">Static routing support</span></span>
* <span data-ttu-id="68c03-284">Compatibilidad con la fragmentación IP y el reensamblado</span><span class="sxs-lookup"><span data-stu-id="68c03-284">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="68c03-285">Compatibilidad con direcciones IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="68c03-285">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="68c03-286">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="68c03-286">IXIA IxANVL validated</span></span>
* <span data-ttu-id="68c03-287">Certificación del logotipo IPv6 Ready Fase II</span><span class="sxs-lookup"><span data-stu-id="68c03-287">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="68c03-288">Estadísticas de IP opcionales</span><span class="sxs-lookup"><span data-stu-id="68c03-288">Optional IP statistics</span></span>
* <span data-ttu-id="68c03-289">Interfaz del controlador de la capa física bien definida e intuitiva</span><span class="sxs-lookup"><span data-stu-id="68c03-289">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="68c03-290">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="68c03-290">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="68c03-291">API de capa de IP intuitivas: *nx_ip_\** , *nxd_ip_\** , *nxd_ipv6_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-291">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="68c03-292">Certificado previamente por TUV y UL para CEI 61508 SIL 4, CEI 62304 clase C, ISO 26262 ASIL D y EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="68c03-292">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="68c03-293">IPSEC de Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="68c03-293">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="68c03-294">Protocolo de seguridad de Internet (IPSec)</span><span class="sxs-lookup"><span data-stu-id="68c03-294">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="68c03-295">Capa de IP</span><span class="sxs-lookup"><span data-stu-id="68c03-295">IP layer</span></span>
* <span data-ttu-id="68c03-296">Compatibilidad con el cifrado mediante hardware</span><span class="sxs-lookup"><span data-stu-id="68c03-296">Hardware crypto support</span></span>
* <span data-ttu-id="68c03-297">Compatibilidad con el cifrado de software, incluidos:</span><span class="sxs-lookup"><span data-stu-id="68c03-297">Software crypto support, including:</span></span>
    * <span data-ttu-id="68c03-298">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="68c03-298">DES, 3DES</span></span>
    * <span data-ttu-id="68c03-299">AES</span><span class="sxs-lookup"><span data-stu-id="68c03-299">AES</span></span>
    * <span data-ttu-id="68c03-300">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="68c03-300">HMAC-MD5</span></span>
    * <span data-ttu-id="68c03-301">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="68c03-301">HMAC-SHA1</span></span>
* <span data-ttu-id="68c03-302">Compatibilidad con el Intercambio de claves por red (IKE) versión 2</span><span class="sxs-lookup"><span data-stu-id="68c03-302">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="68c03-303">API de IPsec intuitivas: *nx_ipsec_\**</span><span class="sxs-lookup"><span data-stu-id="68c03-303">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="68c03-304">IPsec solo está disponible con Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="68c03-304">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="small-footprint"></a><span data-ttu-id="68c03-305">Superficie pequeña</span><span class="sxs-lookup"><span data-stu-id="68c03-305">Small-footprint</span></span>

<span data-ttu-id="68c03-306">Azure RTOS NetX Duo tiene una superficie notablemente pequeña, de 9 KB a 15 KB, para la compatibilidad básica con IP y UDP.</span><span class="sxs-lookup"><span data-stu-id="68c03-306">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="68c03-307">Se necesita una memoria de área de instrucciones adicional de 10 KB a 13 KB para la funcionalidad de TCP.</span><span class="sxs-lookup"><span data-stu-id="68c03-307">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="68c03-308">El uso de RAM de Azure RTOS NetX Duo suele oscilar entre 2,6 KB y 3,6 KB más la memoria del grupo de paquetes, definida por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="68c03-308">Azure RTOS NetX Duo RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="68c03-309">Al igual que Azure RTOS ThreadX, el tamaño de Azure RTOS NetX Duo se escala automáticamente en función de los servicios que usa la aplicación.</span><span class="sxs-lookup"><span data-stu-id="68c03-309">Like Azure RTOS ThreadX, the size of Azure RTOS NetX Duo automatically scales based on the services used by the application.</span></span> <span data-ttu-id="68c03-310">Esto elimina prácticamente la necesidad de configuraciones y parámetros de compilación complicados, lo que facilita el trabajo del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="68c03-310">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="68c03-311">Ejecución rápida</span><span class="sxs-lookup"><span data-stu-id="68c03-311">Fast execution</span></span>

<span data-ttu-id="68c03-312">Azure RTOS NetX Duo proporciona una implementación de envío y recepción de paquetes sin copia, muy integrada con Azure RTOS ThreadX, para lograr el rendimiento más rápido posible.</span><span class="sxs-lookup"><span data-stu-id="68c03-312">Azure RTOS NetX Duo provides a zero-copy packet send/receive implementation, highly integrated with Azure RTOS ThreadX, to achieve the fastest possible performance.</span></span> <span data-ttu-id="68c03-313">Por ejemplo, Azure RTOS NetX Duo normalmente puede lograr transferencias de datos cercanas a la velocidad del cableado en un procesador de 80 MHz (o menos), en tanto que se usa un pequeño porcentaje de ciclos del procesador.</span><span class="sxs-lookup"><span data-stu-id="68c03-313">For example, Azure RTOS NetX Duo can typically achieve near wirespeed data transfers on an 80 MHz (or less) processor, while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="68c03-314">Simple y fácil de usar</span><span class="sxs-lookup"><span data-stu-id="68c03-314">Simple, easy-to-use</span></span>

<span data-ttu-id="68c03-315">La API de Azure RTOS NetX Duo es intuitiva, sencilla y muy funcional.</span><span class="sxs-lookup"><span data-stu-id="68c03-315">The Azure RTOS NetX Duo API is intuitive, straightforward,  and highly functional.</span></span>

<span data-ttu-id="68c03-316">Los nombres de API se componen de palabras reales y no de la sopa de letras de nombres muy abreviados que son tan comunes en otros productos de redes.</span><span class="sxs-lookup"><span data-stu-id="68c03-316">The API names are made of real words and not the “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="68c03-317">Todas las API de Azure RTOS NetX Duo tienen *nx_* al inicio y siguen una convención de nomenclatura sustantivo-verbo.</span><span class="sxs-lookup"><span data-stu-id="68c03-317">All Azure RTOS NetX Duo APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="68c03-318">Además, existe una coherencia funcional en la API.</span><span class="sxs-lookup"><span data-stu-id="68c03-318">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="68c03-319">Por ejemplo, todas las funciones de API con suspensión tienen un tiempo de espera opcional que funciona de forma idéntica.</span><span class="sxs-lookup"><span data-stu-id="68c03-319">For example, all API functions that suspend have an optional timeout that operates in an identical manner.</span></span>

<span data-ttu-id="68c03-320">En el caso de las aplicaciones heredadas, Azure RTOS NetX Duo ofrece una capa adicional compatible con sockets BSD.</span><span class="sxs-lookup"><span data-stu-id="68c03-320">For legacy applications, Azure RTOS NetX Duo offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="68c03-321">Esta capa ayuda a los desarrolladores a migrar fácilmente aplicaciones de redes de gran tamaño.</span><span class="sxs-lookup"><span data-stu-id="68c03-321">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="68c03-322">Seguro</span><span class="sxs-lookup"><span data-stu-id="68c03-322">Safe and secure</span></span>

<span data-ttu-id="68c03-323">Azure RTOS NetX Duo es seguro.</span><span class="sxs-lookup"><span data-stu-id="68c03-323">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="68c03-324">Esta seguridad se proporciona mediante productos de seguridad como complementos, entre los que se incluyen IPsec, SSL, TLS y DTLS.</span><span class="sxs-lookup"><span data-stu-id="68c03-324">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="68c03-325">Además, la aplicación tiene un control total sobre todo el acceso externo a Azure RTOS NetX Duo, lo que facilita la determinación del riesgo de seguridad.</span><span class="sxs-lookup"><span data-stu-id="68c03-325">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="68c03-326">Microsoft Azure RTOS proporciona a los OEM componentes para proteger la comunicación y crear código y aislamiento de datos mediante los mecanismos de protección de hardware MCU y MPU subyacentes.</span><span class="sxs-lookup"><span data-stu-id="68c03-326">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="68c03-327">En última instancia, el fabricante de los dispositivos tiene la responsabilidad de asegurarse de que el dispositivo cumpla totalmente los requisitos de seguridad en constante evolución asociados a su caso de uso específico.</span><span class="sxs-lookup"><span data-stu-id="68c03-327">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="68c03-328">Certificado previamente por TUV y UL para varios estándares de seguridad</span><span class="sxs-lookup"><span data-stu-id="68c03-328">Pre-certified  by TUV and UL to many safety standards</span></span>

<span data-ttu-id="68c03-329">Azure RTOS NetX Duo ha sido certificado por SGS-TUV Saar para su uso en sistemas críticos para la seguridad, de acuerdo con CEI-61508 SIL 4, CEI-62304 Clase de seguridad de SW C, ISO 26262 ASIL D y EN 50128.</span><span class="sxs-lookup"><span data-stu-id="68c03-329">Azure RTOS NetX Duo has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="68c03-330">La certificación confirma que Azure RTOS NetX Duo se puede usar en el desarrollo de software relacionado con la seguridad para los niveles de integridad de seguridad más altos de CEI-61508, CEI-62304, ISO 26262 y EN 50128 para la "Seguridad funcional de los sistemas eléctricos, electrónicos y electrónicos programables relacionados con la seguridad".</span><span class="sxs-lookup"><span data-stu-id="68c03-330">The certification confirms that Azure RTOS NetX Duo can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="68c03-331">SG-TUV Saar, que es una sociedad conjunta entre las empresas alemanas SGS-Group y TUV Saarland, se ha convertido en la empresa líder independiente acreditada para probar, auditar, comprobar y certificar software insertado para sistemas relacionados con la seguridad en todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="68c03-331">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="68c03-332">El estándar de seguridad industrial CEI 61508 y todos los estándares que se derivan de él, incluidos CEI-62304, ISO 26262 y EN 50128, se usan para garantizar la seguridad funcional de los dispositivos médicos eléctricos, electrónicos y electrónicos programables relacionados con la seguridad, los sistemas de control de procesos, la maquinaria industrial, los automóviles y los sistemas de control de ferrocarriles.</span><span class="sxs-lookup"><span data-stu-id="68c03-332">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="Certificación SGS-TUV":::

<span data-ttu-id="68c03-334">Azure RTOS NetX Duo ha sido reconocido por UL por su conformidad con los estándares de seguridad para software de componentes programables UL 60730-1 anexo H, CSA E60730-1 anexo H, CEI 60730-1 anexo H, UL 60335-1 anexo R, CEI 60335-1 anexo R y UL 1998.</span><span class="sxs-lookup"><span data-stu-id="68c03-334">Azure RTOS NetX Duo has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="68c03-335">UL es una empresa global e independiente especializada en la seguridad en la ciencia con más de un siglo de experiencia aportando innovaciones en soluciones de seguridad que abarcan desde la adopción pública de electricidad hasta los avances en sostenibilidad, energías renovables y nanotecnología.</span><span class="sxs-lookup"><span data-stu-id="68c03-335">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="Certificación UL CRU":::

<span data-ttu-id="68c03-337">Los artefactos (certificado, manual de seguridad, informe de pruebas, etc.) asociados a las certificaciones TUV y UL están disponibles para su venta.</span><span class="sxs-lookup"><span data-stu-id="68c03-337">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="68c03-338">En los casos en los que la aplicación necesite certificación adicional, hay un servicio de certificación disponible con Microsoft para proporcionar una certificación llave en mano para varios estándares con la plataforma de hardware real e incluso abarcando el código de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="68c03-338">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span> <span data-ttu-id="68c03-339">Póngase en contacto con nosotros para más detalles sobre nuestro servicio de certificación.</span><span class="sxs-lookup"><span data-stu-id="68c03-339">Contact us for more details on our certification service.</span></span>

## <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="68c03-340">Certificación de seguridad EAL4+ de Common Criteria</span><span class="sxs-lookup"><span data-stu-id="68c03-340">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="68c03-341">Azure RTOS ha logrado la certificación de seguridad EAL4+ de Common Criteria.</span><span class="sxs-lookup"><span data-stu-id="68c03-341">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="68c03-342">El objetivo de la evaluación (TOE) cubre Azure RTOS ThreadX, Azure RTOS NetX Duo, TLS de Azure RTOS NetX Secure y MQTT de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="68c03-342">The Target of Evalution (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="68c03-343">Representa los protocolos de IoT más habituales que requieren los sensores, dispositivos, enrutadores perimetrales y puertas de enlace con alto grado de inserción.</span><span class="sxs-lookup"><span data-stu-id="68c03-343">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="Certificación EAL":::

<span data-ttu-id="68c03-345">El recurso de evaluación de seguridad de TI usado para la certificación de seguridad de Microsoft Azure RTOS SC es Brightsight BV y la entidad de certificación es SERTIT.</span><span class="sxs-lookup"><span data-stu-id="68c03-345">The IT Security Evaluation Facility used for the Microsoft Azure RTOS SC security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

## <a name="fips-140-2-validated"></a><span data-ttu-id="68c03-346">Validación conforme a FIPS 140-2</span><span class="sxs-lookup"><span data-stu-id="68c03-346">FIPS 140-2 Validated</span></span>

<span data-ttu-id="68c03-347">Las bibliotecas criptográficas de Azure RTOS NetX han logrado la certificación del Estándar federal de procesamiento de información 140-2 (FIPS 140-2) para software, que especifica los requisitos para los módulos criptográficos.</span><span class="sxs-lookup"><span data-stu-id="68c03-347">Azure RTOS NetX Crypto libraries have achieved Federal Information Processing Standardization 140-2 (FIPS 140-2) Certification for software, which specifies requirements for cryptography modules.</span></span> <span data-ttu-id="68c03-348">FIPS 140-2 requiere que todos los organismos y departamentos gubernamentales federales que usan seguridad basada en cifrado cumplan los estándares específicos relacionados con el nivel y las funcionalidades de cifrado.</span><span class="sxs-lookup"><span data-stu-id="68c03-348">FIPS 140-2 requires all federal government agencies and departments that use cryptographic-based security to meet specific standards related to encryption strength and capabilities.</span></span> <span data-ttu-id="68c03-349">Estos estándares de seguridad basados en el cifrado también se reconocen en Canadá y en la Unión Europea.</span><span class="sxs-lookup"><span data-stu-id="68c03-349">These cryptographic-based security standards are also recognized in Canada and the European Union.</span></span>

<span data-ttu-id="68c03-350">El laboratorio de evaluación de la seguridad de la información utilizado para las bibliotecas criptográficas de Azure RTOS NetX fue atsec y la entidad de certificación es el Instituto nacional de estándares y tecnología (NIST).</span><span class="sxs-lookup"><span data-stu-id="68c03-350">The Information Security evaluation lab used for Azure RTOS NetX Crypto libraries was atsec and the certification authority is The National Institute of Standards and Technology (NIST).</span></span> <span data-ttu-id="68c03-351">Consulte el [sitio web del NIST](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) para más información.</span><span class="sxs-lookup"><span data-stu-id="68c03-351">Review the [NIST website](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) for additional details.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="68c03-352">Comprobación de interoperabilidad</span><span class="sxs-lookup"><span data-stu-id="68c03-352">Interoperability verification</span></span>

<span data-ttu-id="68c03-353">NetX Duo se ajusta a los estándares RFC y ofrece una interoperabilidad completa con los dispositivos de la mayoría de los proveedores.</span><span class="sxs-lookup"><span data-stu-id="68c03-353">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logotipo IPv6 Ready](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="68c03-355">Azure RTOS NetX Duo es una de las pilas TCP/IP insertadas que han conseguido la rigurosa certificación del logotipo IPv6-Ready, evidencia de que ha superado las pruebas de conformidad e interoperabilidad, administradas y validadas por el Foro de IPv6.</span><span class="sxs-lookup"><span data-stu-id="68c03-355">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="68c03-356">NetX Duo también emplea el estándar del sector IxANVL (Biblioteca de validación de red automatizada) para la implementación del protocolo TCP/IP principal de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="68c03-356">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="68c03-357">Solución IoT integral</span><span class="sxs-lookup"><span data-stu-id="68c03-357">Comprehensive IoT solution</span></span>

<span data-ttu-id="68c03-358">Azure RTOS NetX Duo tiene una superficie notablemente pequeña, de 9 KB a 15 KB, para la compatibilidad básica con IP y UDP.</span><span class="sxs-lookup"><span data-stu-id="68c03-358">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="68c03-359">NetX Duo tiene una de las redes TCP/IP más completas para aplicaciones IoT con alto grado de inserción.</span><span class="sxs-lookup"><span data-stu-id="68c03-359">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="68c03-360">Esta compatibilidad incluye los siguientes productos de protocolo de complementos:</span><span class="sxs-lookup"><span data-stu-id="68c03-360">This support includes the following add-on protocol products:</span></span>

<span data-ttu-id="68c03-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="68c03-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="68c03-362">Tecnología avanzada</span><span class="sxs-lookup"><span data-stu-id="68c03-362">Advanced technology</span></span>

<span data-ttu-id="68c03-363">Azure RTOS NetX Duo es una tecnología avanzada que incluye:</span><span class="sxs-lookup"><span data-stu-id="68c03-363">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="68c03-364">Arquitectura Piconet™</span><span class="sxs-lookup"><span data-stu-id="68c03-364">Piconet™ architecture</span></span>
* <span data-ttu-id="68c03-365">Escalado automático</span><span class="sxs-lookup"><span data-stu-id="68c03-365">Automatic scaling</span></span>
* <span data-ttu-id="68c03-366">Tecnología UDP Fast-Path™</span><span class="sxs-lookup"><span data-stu-id="68c03-366">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="68c03-367">Administración de paquetes flexible</span><span class="sxs-lookup"><span data-stu-id="68c03-367">Flexible packet management</span></span>
* <span data-ttu-id="68c03-368">Implementación y API sin copia</span><span class="sxs-lookup"><span data-stu-id="68c03-368">Zero-copy API and implementation</span></span>
* <span data-ttu-id="68c03-369">Compatibilidad con host múltiple</span><span class="sxs-lookup"><span data-stu-id="68c03-369">Multihomed support</span></span>
* <span data-ttu-id="68c03-370">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="68c03-370">Optional timeout on all suspension</span></span>
* <span data-ttu-id="68c03-371">Compatibilidad con enrutamiento estático</span><span class="sxs-lookup"><span data-stu-id="68c03-371">Static routing support</span></span>
* <span data-ttu-id="68c03-372">IPsec</span><span class="sxs-lookup"><span data-stu-id="68c03-372">IPsec</span></span>
* <span data-ttu-id="68c03-373">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="68c03-373">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="68c03-374">Compatibilidad con el análisis del sistema de Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="68c03-374">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="68c03-375">Tiempo de comercialización más rápido</span><span class="sxs-lookup"><span data-stu-id="68c03-375">Fastest time-to-market</span></span>

<span data-ttu-id="68c03-376">Azure RTOS NetX Duo es fácil de instalar, aprender, usar, depurar, comprobar, certificar y mantener.</span><span class="sxs-lookup"><span data-stu-id="68c03-376">Azure RTOS NetX Duo is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="68c03-377">Como resultado, NetX Duo es una de las pilas TCP/IP más populares para dispositivos IoT insertados, incluidos muchos SoC de Broadcom, GainSpan, etc. Nuestra sólida ventaja en el tiempo de comercialización se basa en lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="68c03-377">As a result, NetX Duo is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, etc. Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="68c03-378">Documentación de calidad: consulte nuestra [Guía del usuario de Azure RTOS NetX Duo](about-this-guide.md) y véalo usted mismo.</span><span class="sxs-lookup"><span data-stu-id="68c03-378">Quality documentation – please review our [Azure RTOS NetX Duo User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="68c03-379">Disponibilidad completa del código fuente</span><span class="sxs-lookup"><span data-stu-id="68c03-379">Complete source code availability</span></span>
* <span data-ttu-id="68c03-380">API fáciles de usar</span><span class="sxs-lookup"><span data-stu-id="68c03-380">Easy-to-use API</span></span>
* <span data-ttu-id="68c03-381">Conjunto de características completo y avanzado</span><span class="sxs-lookup"><span data-stu-id="68c03-381">Comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="68c03-382">Una licencia sencilla</span><span class="sxs-lookup"><span data-stu-id="68c03-382">One Simple License</span></span>

<span data-ttu-id="68c03-383">No hay ningún costo asociado al uso y las pruebas del código fuente ni a las licencias de producción si se implementa en dispositivos con licencia previa; todos los demás dispositivos necesitan una licencia anual sencilla.</span><span class="sxs-lookup"><span data-stu-id="68c03-383">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="68c03-384">Código fuente completo y de máxima calidad</span><span class="sxs-lookup"><span data-stu-id="68c03-384">Full, highest-quality source code</span></span>

<span data-ttu-id="68c03-385">A lo largo de los años, el código fuente de Azure RTOS NetX Duo ha marcado el listón en calidad y facilidad de comprensión.</span><span class="sxs-lookup"><span data-stu-id="68c03-385">Throughout the years, Azure RTOS NetX Duo source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="68c03-386">Además, la convención de tener una función por archivo facilita el examen del código fuente.</span><span class="sxs-lookup"><span data-stu-id="68c03-386">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="68c03-387">Compatible con las arquitecturas más populares</span><span class="sxs-lookup"><span data-stu-id="68c03-387">Supports most popular architectures</span></span>

<span data-ttu-id="68c03-388">Azure RTOS NetX Duo se ejecuta en los microprocesadores de 32 y 64 bits más populares, de serie, totalmente probado y totalmente compatible, incluidas las siguientes arquitecturas avanzadas:</span><span class="sxs-lookup"><span data-stu-id="68c03-388">Azure RTOS NetX Duo runs on most popular 32/64-bit microprocessors out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="68c03-389">**Dispositivos analógicos**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="68c03-389">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="68c03-390">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="68c03-390">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="68c03-391">**Ambiqmicro**: MCU serie pollo</span><span class="sxs-lookup"><span data-stu-id="68c03-391">**Ambiqmicro**: pollo MCUs</span></span>

<span data-ttu-id="68c03-392">**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="68c03-392">**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="68c03-393">**Cadence**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="68c03-393">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="68c03-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="68c03-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="68c03-395">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="68c03-395">**Cypress**: RISC-V</span></span>

<span data-ttu-id="68c03-396">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="68c03-396">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="68c03-397">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="68c03-397">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="68c03-398">**Intel e Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="68c03-398">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="68c03-399">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="68c03-399">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="68c03-400">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="68c03-400">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="68c03-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="68c03-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="68c03-402">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="68c03-402">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="68c03-403">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="68c03-403">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="68c03-404">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="68c03-404">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="68c03-405">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="68c03-405">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="68c03-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="68c03-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="68c03-407">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="68c03-407">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="68c03-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="68c03-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="68c03-409">*Todas las cifras de tiempos y tamaños enumeradas son estimaciones y pueden ser diferentes en su plataforma de desarrollo.*</span><span class="sxs-lookup"><span data-stu-id="68c03-409">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>

## <a name="related-services"></a><span data-ttu-id="68c03-410">Servicios relacionados</span><span class="sxs-lookup"><span data-stu-id="68c03-410">Related services</span></span>

<span data-ttu-id="68c03-411">El módulo de seguridad RTOS de Azure Security Center para IoT proporciona una solución de seguridad integral para dispositivos Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="68c03-411">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="68c03-412">El módulo de seguridad de Azure RTOS ofrece detección de actividad de red malintencionada, creación de línea base del comportamiento del dispositivo basada en alertas personalizadas y ayuda a mejorar la higiene de la seguridad del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="68c03-412">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="68c03-413">Más información en [Información general: microagente de Defender para IoT de Defender para IoT para Azure RTOS (versión preliminar)](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) o comience a trabajar con la guía de inicio rápido [Configuración del módulo de seguridad para Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module).</span><span class="sxs-lookup"><span data-stu-id="68c03-413">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="68c03-414">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="68c03-414">Next steps</span></span>

<span data-ttu-id="68c03-415">Para más información acerca de NetX Duo, comience con la [Guía del usuario de Azure RTOS NetX Duo](about-this-guide.md).</span><span class="sxs-lookup"><span data-stu-id="68c03-415">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
