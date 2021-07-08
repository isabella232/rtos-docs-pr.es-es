---
title: Descripción de Azure RTOS NetX Duo
description: Azure RTOS NetX Duo es una pila de red TCP/IP avanzada y de clase industrial diseñada específicamente para aplicaciones IoT y en tiempo real con alto grado de inserción.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 6112ab5cb711ca1a5c83fd5cd4b43abc0302c6c5
ms.sourcegitcommit: f9d8cf23becf96d5bd6d31dd54f89c48962fd09b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549344"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="d6b4c-103">Introducción a Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d6b4c-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="d6b4c-104">La pila de red TCP/IP insertada de Azure RTOS NetX Duo es la pila de red TCP/IP dual para IPv4 e IPv6 de clase industrial de Microsoft, que está diseñada específicamente para aplicaciones IoT, en tiempo real y con alto grado de inserción.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="d6b4c-105">NetX Duo proporciona aplicaciones insertadas con los principales protocolos de red, como IPv4, IPv6, TCP y UDP, así como un conjunto completo de protocolos adicionales de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="d6b4c-106">Azure RTOS NetX Duo ofrece seguridad mediante productos adicionales de seguridad como complementos, entre los que se incluyen IPsec y SSL/TLS/DTLS de Azure RTOS NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="d6b4c-107">Todo esto, combinado con una pequeña superficie, una ejecución rápida y una facilidad de uso superior, hacen que Azure RTOS NetX Duo sea la opción ideal para las aplicaciones IoT insertadas más exigentes.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="d6b4c-108">Protocolos de API</span><span class="sxs-lookup"><span data-stu-id="d6b4c-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="d6b4c-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="d6b4c-109">MQTT</span></span>

* <span data-ttu-id="d6b4c-110">Transporte de telemetría de cola de mensajes (MQTT)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="d6b4c-111">Memoria flash mínima de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="d6b4c-112">IP automática</span><span class="sxs-lookup"><span data-stu-id="d6b4c-112">Auto IP</span></span>

* <span data-ttu-id="d6b4c-113">Asignación automática de direcciones IPv4</span><span class="sxs-lookup"><span data-stu-id="d6b4c-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="d6b4c-114">Mínimo 1,2 KB, 300 bytes de RAM</span><span class="sxs-lookup"><span data-stu-id="d6b4c-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="d6b4c-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="d6b4c-115">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="d6b4c-116">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="d6b4c-116">HTTP 1.0</span></span>

* <span data-ttu-id="d6b4c-117">Protocolo de transferencia de hipertexto (HTTP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-117">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="d6b4c-118">Memoria flash mínima de 2,8 KB a 4,8 KB y de 0,4 KB a 1,0 KB de RAM</span><span class="sxs-lookup"><span data-stu-id="d6b4c-118">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="d6b4c-119">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="d6b4c-119">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="d6b4c-120">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="d6b4c-120">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="d6b4c-121">Protocolo de transferencia de hipertexto (HTTP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-121">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="d6b4c-122">Memoria flash mínima de 3,0 KB a 9,5 KB y de 0,5 KB a 2 KB de RAM</span><span class="sxs-lookup"><span data-stu-id="d6b4c-122">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="d6b4c-123">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="d6b4c-123">Client and server support</span></span>
* <span data-ttu-id="d6b4c-124">Varias sesiones de cliente entrantes</span><span class="sxs-lookup"><span data-stu-id="d6b4c-124">Multiple incoming client sessions</span></span>
* <span data-ttu-id="d6b4c-125">Texto sin formato y HTTPS cifrado</span><span class="sxs-lookup"><span data-stu-id="d6b4c-125">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="d6b4c-126">Compatibilidad con conexiones persistentes</span><span class="sxs-lookup"><span data-stu-id="d6b4c-126">Persistent connection support</span></span>
* <span data-ttu-id="d6b4c-127">Carga de archivos de varias partes</span><span class="sxs-lookup"><span data-stu-id="d6b4c-127">Multipart file upload</span></span>
* <span data-ttu-id="d6b4c-128">Totalmente integrado con TLS de Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="d6b4c-128">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="d6b4c-129">SMTP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-129">SMTP</span></span>

* <span data-ttu-id="d6b4c-130">Protocolo simple de transferencia de correo (SMTP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-130">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="d6b4c-131">Mínimo 4,1 KB y una superficie de RAM de 0,6 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-131">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-132">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="d6b4c-132">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="d6b4c-133">DHCP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-133">DHCP</span></span>

* <span data-ttu-id="d6b4c-134">Protocolo de configuración dinámica de host (DHCP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-134">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="d6b4c-135">Memoria flash mínima de 3,6 KB a 4,6 KB y superficie de RAM de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-135">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-136">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="d6b4c-136">Client and server support</span></span>
* <span data-ttu-id="d6b4c-137">Compatibilidad con IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="d6b4c-137">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="d6b4c-138">NAT</span><span class="sxs-lookup"><span data-stu-id="d6b4c-138">NAT</span></span>

* <span data-ttu-id="d6b4c-139">Traducción de direcciones de red (NAT)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-139">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="d6b4c-140">Mínimo 3,5 KB y una superficie de RAM de 0,6 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-140">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-141">Compatibilidad con direcciones IPv4</span><span class="sxs-lookup"><span data-stu-id="d6b4c-141">IPv4 address support</span></span>
* <span data-ttu-id="d6b4c-142">NAT solo está disponible con Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d6b4c-142">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="d6b4c-143">SNMP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-143">SNMP</span></span>

* <span data-ttu-id="d6b4c-144">Protocolo simple de administración de redes (SNMP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-144">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="d6b4c-145">Mínimo 10,9 KB y una superficie de RAM de 2,6 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-145">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-146">Compatibilidad del agente con V1, V2 y V3</span><span class="sxs-lookup"><span data-stu-id="d6b4c-146">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="d6b4c-147">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="d6b4c-147">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="d6b4c-148">Sistema de nombres de dominio (DNS)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-148">Domain Name System (DNS)</span></span>
* <span data-ttu-id="d6b4c-149">Sistema de nombres de dominio de multidifusión (mDNS)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-149">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="d6b4c-150">Detección de servicios basada en DNS (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-150">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="d6b4c-151">DNS: Memoria flash mínima de 2,4 KB a 3 KB y superficie de RAM de 1 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-151">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-152">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="d6b4c-152">Client support</span></span>
* <span data-ttu-id="d6b4c-153">mDNS y DNS-SD solo están disponibles con Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-153">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="pop3"></a><span data-ttu-id="d6b4c-154">POP3</span><span class="sxs-lookup"><span data-stu-id="d6b4c-154">POP3</span></span>

* <span data-ttu-id="d6b4c-155">Protocolo de oficina de correos versión 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-155">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="d6b4c-156">Mínimo 8,1 KB y una superficie de RAM de 1,4 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-156">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-157">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="d6b4c-157">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="d6b4c-158">TELNET</span><span class="sxs-lookup"><span data-stu-id="d6b4c-158">TELNET</span></span>

* <span data-ttu-id="d6b4c-159">Mínimo 0,5 KB y una superficie de RAM de 0,3 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-159">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-160">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="d6b4c-160">Client and server support</span></span>
* <span data-ttu-id="d6b4c-161">API de Telnet intuitivas: *nx_telnet_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-161">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="d6b4c-162">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-162">FTP, TFTP</span></span>

* <span data-ttu-id="d6b4c-163">Protocolo de transferencia de archivos (FTP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-163">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="d6b4c-164">Protocolo trivial de transferencia de archivos (TFTP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-164">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="d6b4c-165">FTP: memoria flash mínima de 1,8 KB a 7,2 KB y superficie de RAM de 0,6 KB a 2,1 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-165">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-166">TFTP: memoria flash mínima de 1,7 KB a 2,4 KB y superficie de RAM de 0,3 KB a 1,8 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-166">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-167">Compatibilidad con clientes y servidores</span><span class="sxs-lookup"><span data-stu-id="d6b4c-167">Client and server support</span></span>
* <span data-ttu-id="d6b4c-168">API intuitivas de FTP y TFTP: *nx_ftp_\** o *nx_tftp_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-168">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="d6b4c-169">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="d6b4c-169">PPP, PPPoE</span></span>

* <span data-ttu-id="d6b4c-170">Protocolo punto a punto (PPP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-170">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="d6b4c-171">Protocolo punto a punto sobre Ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-171">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="d6b4c-172">Mínimo 7,1 KB y una superficie de RAM de 3,8 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-172">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-173">API de PPP intuitivas: *nx_ppp_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-173">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="d6b4c-174">PPPoE solo está disponible con Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d6b4c-174">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="d6b4c-175">SNTP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-175">SNTP</span></span>

* <span data-ttu-id="d6b4c-176">Protocolo simple de tiempo de red (SNTP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-176">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="d6b4c-177">Mínimo 4 KB y una superficie de RAM de 0,5 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-177">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="d6b4c-178">Compatibilidad con clientes</span><span class="sxs-lookup"><span data-stu-id="d6b4c-178">Client support</span></span>
* <span data-ttu-id="d6b4c-179">API de SNTP intuitivas: *nx_sntp_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-179">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="d6b4c-180">API de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d6b4c-180">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="d6b4c-181">API intuitivas y coherentes</span><span class="sxs-lookup"><span data-stu-id="d6b4c-181">Intuitive and consistent API</span></span>
* <span data-ttu-id="d6b4c-182">Convención de nomenclatura sustantivo-verbo</span><span class="sxs-lookup"><span data-stu-id="d6b4c-182">Noun-verb naming convention</span></span>
* <span data-ttu-id="d6b4c-183">Implementación rápida de la API sin copia</span><span class="sxs-lookup"><span data-stu-id="d6b4c-183">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="d6b4c-184">Todas las API comienzan por <i>nx_\*</i> para identificarlas fácilmente como pertenecientes a Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="d6b4c-184">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="d6b4c-185">Las API de bloqueo tienen un tiempo de espera de subprocesos opcional</span><span class="sxs-lookup"><span data-stu-id="d6b4c-185">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="d6b4c-186">Consulte [Guía del usuario de Azure RTOS NetX Duo](about-this-guide.md) para más información.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-186">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="d6b4c-187">Capa de BSD opcional para la portabilidad de código de sockets heredado</span><span class="sxs-lookup"><span data-stu-id="d6b4c-187">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="d6b4c-188">IGMP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-188">IGMP</span></span>

* <span data-ttu-id="d6b4c-189">Protocolo de administración de grupos de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-189">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="d6b4c-190">Memoria flash mínima de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-190">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="d6b4c-191">Compatibilidad con grupos de multidifusión IPv4</span><span class="sxs-lookup"><span data-stu-id="d6b4c-191">IPv4 multicast group support</span></span>
* <span data-ttu-id="d6b4c-192">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="d6b4c-192">IXIA IxANVL validated</span></span>
* <span data-ttu-id="d6b4c-193">Estadísticas de IGMP opcionales</span><span class="sxs-lookup"><span data-stu-id="d6b4c-193">Optional IGMP statistics</span></span>
* <span data-ttu-id="d6b4c-194">Seguimiento de nivel de sistema mediante Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="d6b4c-194">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="d6b4c-195">API de IGMP intuitivas: *nx_igmp_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-195">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="d6b4c-196">DTLS de Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="d6b4c-196">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="d6b4c-197">Seguridad de la capa de transporte del datagrama (DTLS) 1.0 y 1.2</span><span class="sxs-lookup"><span data-stu-id="d6b4c-197">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="d6b4c-198">Memoria flash mínima de 11 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-198">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="d6b4c-199">Tamaño de clave rápido con software RSA de 2048 bits ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="d6b4c-199">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="d6b4c-200">Implementación optimizada de X.509</span><span class="sxs-lookup"><span data-stu-id="d6b4c-200">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="d6b4c-201">Totalmente integrado con los sockets UDP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d6b4c-201">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="d6b4c-202">Compatibilidad con el cifrado mediante hardware</span><span class="sxs-lookup"><span data-stu-id="d6b4c-202">Hardware Crypto Support</span></span>
* <span data-ttu-id="d6b4c-203">Compatibilidad con criptografía de software: RSA (todos los tamaños de clave), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-203">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="d6b4c-204">Criptografía de curva elíptica (ECC) con ECDSA (firma) y ECDH (cifrado), incluidas las curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="d6b4c-204">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="d6b4c-205">Compatibilidad con claves cifradas (dependiente del hardware)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-205">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="d6b4c-206">TLS de Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="d6b4c-206">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="d6b4c-207">Seguridad de la capa de transporte (TLS) 1.0, 1.1 y 1.2</span><span class="sxs-lookup"><span data-stu-id="d6b4c-207">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="d6b4c-208">Memoria flash mínima de 8,8 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-208">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="d6b4c-209">Tamaño de clave rápido con software RSA de 2048 bits ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="d6b4c-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="d6b4c-210">Implementación optimizada de X.509</span><span class="sxs-lookup"><span data-stu-id="d6b4c-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="d6b4c-211">Totalmente integrado con los sockets TCP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d6b4c-211">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="d6b4c-212">Compatibilidad con el cifrado mediante hardware</span><span class="sxs-lookup"><span data-stu-id="d6b4c-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="d6b4c-213">Compatibilidad con criptografía de software: RSA (todos los tamaños de clave), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="d6b4c-214">Criptografía de curva elíptica (ECC) con ECDSA (firma) y ECDH (cifrado), incluidas las curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="d6b4c-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="d6b4c-215">Compatibilidad con claves cifradas (dependiente del hardware)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="d6b4c-216">ICMP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-216">ICMP</span></span>

* <span data-ttu-id="d6b4c-217">Protocolo de mensajes de control de Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-217">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="d6b4c-218">Memoria flash mínima de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-218">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="d6b4c-219">Compatibilidad con IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="d6b4c-219">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="d6b4c-220">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="d6b4c-220">IXIA IxANVL validated</span></span>
* <span data-ttu-id="d6b4c-221">Solicitud de ping y respuesta de ping</span><span class="sxs-lookup"><span data-stu-id="d6b4c-221">Ping request and ping response</span></span>
* <span data-ttu-id="d6b4c-222">Suspensión de subprocesos opcional en solicitudes de ping</span><span class="sxs-lookup"><span data-stu-id="d6b4c-222">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="d6b4c-223">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="d6b4c-223">Optional timeout on all suspension</span></span>
* <span data-ttu-id="d6b4c-224">Estadísticas de ICMP opcionales</span><span class="sxs-lookup"><span data-stu-id="d6b4c-224">Optional ICMP statistics</span></span>
* <span data-ttu-id="d6b4c-225">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d6b4c-225">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="d6b4c-226">API de ICMP intuitivas: *nx_icmp_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-226">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="d6b4c-227">UDP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-227">UDP</span></span>

* <span data-ttu-id="d6b4c-228">Protocolo de datagramas de usuario (UDP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-228">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="d6b4c-229">Memoria flash mínima de 2,5 KB, 124 bytes de RAM por socket</span><span class="sxs-lookup"><span data-stu-id="d6b4c-229">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="d6b4c-230">Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:</span><span class="sxs-lookup"><span data-stu-id="d6b4c-230">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="d6b4c-231">RX: 95 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 14 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="d6b4c-231">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="d6b4c-232">TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 10 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="d6b4c-232">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="d6b4c-233">Tecnología UDP Fast Path™</span><span class="sxs-lookup"><span data-stu-id="d6b4c-233">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="d6b4c-234">No hay límites en el número de UDP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-234">No limits on the number of UDP</span></span>
* <span data-ttu-id="d6b4c-235">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="d6b4c-235">IXIA IxANVL validated</span></span>
* <span data-ttu-id="d6b4c-236">Suspensión opcional en la recepción de sockets</span><span class="sxs-lookup"><span data-stu-id="d6b4c-236">Optional suspension on socket receive</span></span>
* <span data-ttu-id="d6b4c-237">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="d6b4c-237">Optional timeout on all suspension</span></span>
* <span data-ttu-id="d6b4c-238">Estadísticas de UDP opcionales</span><span class="sxs-lookup"><span data-stu-id="d6b4c-238">Optional UDP statistics</span></span>
* <span data-ttu-id="d6b4c-239">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d6b4c-239">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="d6b4c-240">API de UDP intuitivas: *nx_udp_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-240">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="d6b4c-241">TCP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-241">TCP</span></span>

* <span data-ttu-id="d6b4c-242">Protocolo de control de transmisión (TCP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-242">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="d6b4c-243">Memoria flash mínima de 10,5 KB a 12,5 KB, 280 bytes de RAM por socket</span><span class="sxs-lookup"><span data-stu-id="d6b4c-243">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="d6b4c-244">Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:</span><span class="sxs-lookup"><span data-stu-id="d6b4c-244">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="d6b4c-245">RX: 93 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 20 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="d6b4c-245">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="d6b4c-246">TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 27 % de uso de MCU</span><span class="sxs-lookup"><span data-stu-id="d6b4c-246">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="d6b4c-247">Conexión confiable</span><span class="sxs-lookup"><span data-stu-id="d6b4c-247">Reliable connection</span></span>
* <span data-ttu-id="d6b4c-248">No hay límites en el número de sockets de TCP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-248">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="d6b4c-249">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="d6b4c-249">IXIA IxANVL validated</span></span>
* <span data-ttu-id="d6b4c-250">Suspensión opcional en la recepción y transmisión de sockets</span><span class="sxs-lookup"><span data-stu-id="d6b4c-250">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="d6b4c-251">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="d6b4c-251">Optional timeout on all suspension</span></span>
* <span data-ttu-id="d6b4c-252">Estadísticas de TCP opcionales</span><span class="sxs-lookup"><span data-stu-id="d6b4c-252">Optional TCP statistics</span></span>
* <span data-ttu-id="d6b4c-253">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d6b4c-253">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="d6b4c-254">API de TCP intuitivas: *nx_tcp_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-254">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="d6b4c-255">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-255">ARP/RARP</span></span>

* <span data-ttu-id="d6b4c-256">Protocolo de resolución de direcciones (ARP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-256">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="d6b4c-257">Protocolo de resolución de direcciones inversa (RARP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-257">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="d6b4c-258">Memoria flash mínima de 1,7 KB, tamaño de RAM</span><span class="sxs-lookup"><span data-stu-id="d6b4c-258">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="d6b4c-259">Resolución dinámica de direcciones MAC de 32 bits IPv4 y 48 bits</span><span class="sxs-lookup"><span data-stu-id="d6b4c-259">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="d6b4c-260">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="d6b4c-260">IXIA IxANVL validated</span></span>
* <span data-ttu-id="d6b4c-261">Memoria caché de ARP flexible y definida por el usuario</span><span class="sxs-lookup"><span data-stu-id="d6b4c-261">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="d6b4c-262">Compatibilidad con ARP gratuito</span><span class="sxs-lookup"><span data-stu-id="d6b4c-262">Gratuitous ARP support</span></span>
* <span data-ttu-id="d6b4c-263">Estadísticas de ARP/RARP opcionales determinadas por la aplicación</span><span class="sxs-lookup"><span data-stu-id="d6b4c-263">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="d6b4c-264">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d6b4c-264">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="d6b4c-265">API de ARP/RARP intuitivas: *nx_arp_\** , *nx_rarp_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-265">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="d6b4c-266">IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="d6b4c-266">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="d6b4c-267">Protocolo de Internet (IP)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-267">Internet Protocol (IP)</span></span>
* <span data-ttu-id="d6b4c-268">Memoria flash mínima de 3,5 KB a 8,5 KB y superficie de RAM de 2 KB a 3 KB</span><span class="sxs-lookup"><span data-stu-id="d6b4c-268">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="d6b4c-269">Arquitectura Piconet™</span><span class="sxs-lookup"><span data-stu-id="d6b4c-269">Piconet™ architecture</span></span>
* <span data-ttu-id="d6b4c-270">Rendimiento rápido, casi a la velocidad del cableado</span><span class="sxs-lookup"><span data-stu-id="d6b4c-270">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="d6b4c-271">Compatibilidad con varias interfaces</span><span class="sxs-lookup"><span data-stu-id="d6b4c-271">Multiple interface support</span></span>
* <span data-ttu-id="d6b4c-272">Compatibilidad con host múltiple</span><span class="sxs-lookup"><span data-stu-id="d6b4c-272">Multihomed support</span></span>
* <span data-ttu-id="d6b4c-273">Compatibilidad con enrutamiento estático</span><span class="sxs-lookup"><span data-stu-id="d6b4c-273">Static routing support</span></span>
* <span data-ttu-id="d6b4c-274">Compatibilidad con la fragmentación IP y el reensamblado</span><span class="sxs-lookup"><span data-stu-id="d6b4c-274">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="d6b4c-275">Compatibilidad con direcciones IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="d6b4c-275">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="d6b4c-276">Validado por IxANVL de IXIA</span><span class="sxs-lookup"><span data-stu-id="d6b4c-276">IXIA IxANVL validated</span></span>
* <span data-ttu-id="d6b4c-277">Certificación del logotipo IPv6 Ready Fase II</span><span class="sxs-lookup"><span data-stu-id="d6b4c-277">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="d6b4c-278">Estadísticas de IP opcionales</span><span class="sxs-lookup"><span data-stu-id="d6b4c-278">Optional IP statistics</span></span>
* <span data-ttu-id="d6b4c-279">Interfaz del controlador de la capa física bien definida e intuitiva</span><span class="sxs-lookup"><span data-stu-id="d6b4c-279">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="d6b4c-280">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d6b4c-280">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="d6b4c-281">API de capa de IP intuitivas: *nx_ip_\** , *nxd_ip_\** , *nxd_ipv6_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-281">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="d6b4c-282">Certificado previamente por TUV y UL para CEI 61508 SIL 4, CEI 62304 clase C, ISO 26262 ASIL D y EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="d6b4c-282">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="d6b4c-283">IPSEC de Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="d6b4c-283">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="d6b4c-284">Protocolo de seguridad de Internet (IPSec)</span><span class="sxs-lookup"><span data-stu-id="d6b4c-284">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="d6b4c-285">Capa de IP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-285">IP layer</span></span>
* <span data-ttu-id="d6b4c-286">Compatibilidad con el cifrado mediante hardware</span><span class="sxs-lookup"><span data-stu-id="d6b4c-286">Hardware crypto support</span></span>
* <span data-ttu-id="d6b4c-287">Compatibilidad con el cifrado de software, incluidos:</span><span class="sxs-lookup"><span data-stu-id="d6b4c-287">Software crypto support, including:</span></span>
    * <span data-ttu-id="d6b4c-288">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="d6b4c-288">DES, 3DES</span></span>
    * <span data-ttu-id="d6b4c-289">AES</span><span class="sxs-lookup"><span data-stu-id="d6b4c-289">AES</span></span>
    * <span data-ttu-id="d6b4c-290">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="d6b4c-290">HMAC-MD5</span></span>
    * <span data-ttu-id="d6b4c-291">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="d6b4c-291">HMAC-SHA1</span></span>
* <span data-ttu-id="d6b4c-292">Compatibilidad con el Intercambio de claves por red (IKE) versión 2</span><span class="sxs-lookup"><span data-stu-id="d6b4c-292">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="d6b4c-293">API de IPsec intuitivas: *nx_ipsec_\**</span><span class="sxs-lookup"><span data-stu-id="d6b4c-293">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="d6b4c-294">IPsec solo está disponible con Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d6b4c-294">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="d6b4c-295">Seguro</span><span class="sxs-lookup"><span data-stu-id="d6b4c-295">Safe and secure</span></span>

<span data-ttu-id="d6b4c-296">Azure RTOS NetX Duo es seguro.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-296">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="d6b4c-297">Esta seguridad se proporciona mediante productos de seguridad como complementos, entre los que se incluyen IPsec, SSL, TLS y DTLS.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-297">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="d6b4c-298">Además, la aplicación tiene un control total sobre todo el acceso externo a Azure RTOS NetX Duo, lo que facilita la determinación del riesgo de seguridad.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-298">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="d6b4c-299">Microsoft Azure RTOS proporciona a los OEM componentes para proteger la comunicación y crear código y aislamiento de datos mediante los mecanismos de protección de hardware MCU y MPU subyacentes.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-299">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="d6b4c-300">En última instancia, el fabricante de los dispositivos tiene la responsabilidad de asegurarse de que el dispositivo cumpla totalmente los requisitos de seguridad en constante evolución asociados a su caso de uso específico.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-300">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>


## <a name="interoperability-verification"></a><span data-ttu-id="d6b4c-301">Comprobación de interoperabilidad</span><span class="sxs-lookup"><span data-stu-id="d6b4c-301">Interoperability verification</span></span>

<span data-ttu-id="d6b4c-302">NetX Duo se ajusta a los estándares RFC y ofrece una interoperabilidad completa con los dispositivos de la mayoría de los proveedores.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-302">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logotipo IPv6 Ready](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="d6b4c-304">Azure RTOS NetX Duo es una de las pilas TCP/IP insertadas que han conseguido la rigurosa certificación del logotipo IPv6-Ready, evidencia de que ha superado las pruebas de conformidad e interoperabilidad, administradas y validadas por el Foro de IPv6.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-304">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="d6b4c-305">NetX Duo también emplea el estándar del sector IxANVL (Biblioteca de validación de red automatizada) para la implementación del protocolo TCP/IP principal de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-305">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="d6b4c-306">Solución IoT integral</span><span class="sxs-lookup"><span data-stu-id="d6b4c-306">Comprehensive IoT solution</span></span>

<span data-ttu-id="d6b4c-307">NetX Duo tiene una de las redes TCP/IP más completas para aplicaciones IoT con alto grado de inserción.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-307">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="d6b4c-308">Esta compatibilidad incluye los siguientes productos de protocolo de complementos.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-308">This support includes the following add-on protocol products.</span></span>

<span data-ttu-id="d6b4c-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="d6b4c-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="d6b4c-310">Tecnología avanzada</span><span class="sxs-lookup"><span data-stu-id="d6b4c-310">Advanced technology</span></span>

<span data-ttu-id="d6b4c-311">Azure RTOS NetX Duo es una tecnología avanzada que incluye:</span><span class="sxs-lookup"><span data-stu-id="d6b4c-311">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="d6b4c-312">Arquitectura Piconet™</span><span class="sxs-lookup"><span data-stu-id="d6b4c-312">Piconet™ architecture</span></span>
* <span data-ttu-id="d6b4c-313">Escalado automático</span><span class="sxs-lookup"><span data-stu-id="d6b4c-313">Automatic scaling</span></span>
* <span data-ttu-id="d6b4c-314">Tecnología UDP Fast-Path™</span><span class="sxs-lookup"><span data-stu-id="d6b4c-314">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="d6b4c-315">Administración de paquetes flexible</span><span class="sxs-lookup"><span data-stu-id="d6b4c-315">Flexible packet management</span></span>
* <span data-ttu-id="d6b4c-316">Implementación y API sin copia</span><span class="sxs-lookup"><span data-stu-id="d6b4c-316">Zero-copy API and implementation</span></span>
* <span data-ttu-id="d6b4c-317">Compatibilidad con host múltiple</span><span class="sxs-lookup"><span data-stu-id="d6b4c-317">Multihomed support</span></span>
* <span data-ttu-id="d6b4c-318">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="d6b4c-318">Optional timeout on all suspension</span></span>
* <span data-ttu-id="d6b4c-319">Compatibilidad con enrutamiento estático</span><span class="sxs-lookup"><span data-stu-id="d6b4c-319">Static routing support</span></span>
* <span data-ttu-id="d6b4c-320">IPsec</span><span class="sxs-lookup"><span data-stu-id="d6b4c-320">IPsec</span></span>
* <span data-ttu-id="d6b4c-321">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="d6b4c-321">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="d6b4c-322">Compatibilidad con el análisis del sistema de Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="d6b4c-322">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="d6b4c-323">Servicios relacionados</span><span class="sxs-lookup"><span data-stu-id="d6b4c-323">Related services</span></span>

### <a name="azure-iot"></a><span data-ttu-id="d6b4c-324">Azure IoT</span><span class="sxs-lookup"><span data-stu-id="d6b4c-324">Azure IoT</span></span>

<span data-ttu-id="d6b4c-325">NetX Duo incluye [Azure IoT Middleware para Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), una biblioteca específica para plataformas que actúa como capa de enlace entre Azure RTOS y el SDK de Azure para C insertado, con el fin de facilitar la conectividad con los servicios de Azure IoT.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-325">NetX Duo includes [Azure IoT Middleware for Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), a platform-specific library that acts as a binding layer between the Azure RTOS and the Azure SDK for Embedded C to facilitate connectivity to Azure IoT services.</span></span> <span data-ttu-id="d6b4c-326">Estos son los objetivos de Azure IoT Middleware:</span><span class="sxs-lookup"><span data-stu-id="d6b4c-326">The goals of Azure IoT Middleware are the following.</span></span>
* <span data-ttu-id="d6b4c-327">Proporcionar las interfaces de cliente inteligentes (IoTHub_Client y DeviceProvisioning_Client) que los desarrolladores necesitan para sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-327">Provide the smart client interfaces (IoTHub_Client, DeviceProvisioning_Client) that developers need for their applications.</span></span>
* <span data-ttu-id="d6b4c-328">Organizar la interacción entre el SDK de C insertado y la plataforma.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-328">Orchestrate the interaction between the Embedded C SDK and the platform.</span></span>
* <span data-ttu-id="d6b4c-329">Proporcionar la inicialización de la plataforma Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-329">Provide Azure RTOS platform initialization.</span></span>
* <span data-ttu-id="d6b4c-330">Compatibilidad con IoT Plug and Play.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-330">IoT Plug and Play support.</span></span>
* <span data-ttu-id="d6b4c-331">Funcionalidades de seguridad.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-331">Security capabilities.</span></span>
* <span data-ttu-id="d6b4c-332">Conocimiento de la limitación de recursos.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-332">Resource limitation aware.</span></span>
* <span data-ttu-id="d6b4c-333">Compatibilidad de protocolos.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-333">Protocol support.</span></span>

![Servicios relacionados con Azure RTOS NetX Duo](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a><span data-ttu-id="d6b4c-335">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="d6b4c-335">Azure Defender</span></span>

<span data-ttu-id="d6b4c-336">El módulo de seguridad de Azure Defender para IoT proporciona una solución de seguridad completa para dispositivos Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-336">The Azure Defender for IoT security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="d6b4c-337">El módulo de seguridad de Azure RTOS ofrece detección de actividad de red malintencionada, creación de línea base del comportamiento del dispositivo basada en alertas personalizadas y ayuda a mejorar la higiene de la seguridad del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-337">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="d6b4c-338">Más información en [Información general: microagente de Defender para IoT de Defender para IoT para Azure RTOS (versión preliminar)](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) o comience a trabajar con la guía de inicio rápido [Configuración del módulo de seguridad para Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module).</span><span class="sxs-lookup"><span data-stu-id="d6b4c-338">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

### <a name="device-update-for-iot-hub"></a><span data-ttu-id="d6b4c-339">Device Update para IoT Hub</span><span class="sxs-lookup"><span data-stu-id="d6b4c-339">Device Update for IoT Hub</span></span>

<span data-ttu-id="d6b4c-340">[Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) es un servicio que permite implementar actualizaciones inalámbricas (OTA) para sus dispositivos IoT.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-340">The [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) is a service that enables you to deploy over-the-air updates (OTA) for your IoT devices.</span></span> <span data-ttu-id="d6b4c-341">El módulo Device Update for IoT Hub es la implementación del agente de Device Update para IoT Hub en Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-341">The Device Update for IoT Hub module is the implementation of Device Update for IoT Hub Agent in Azure RTOS NetX Duo.</span></span> <span data-ttu-id="d6b4c-342">Proporciona API sencillas para que los generadores de dispositivos integren la funcionalidad de actualización de dispositivos en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-342">It provides simple APIs for device builders to integrate the Device Update capability in their application.</span></span>

<span data-ttu-id="d6b4c-343">Consulte los ejemplos de paneles clave de evaluación de semiconductores que incluyen las guías introductorias para aprender a configurar, crear e implementar las actualizaciones inalámbricas en los dispositivos.</span><span class="sxs-lookup"><span data-stu-id="d6b4c-343">See the samples of key semiconductors evaluation boards that include the get started guides to learn configure, build and deploy the over-the-air (OTA) updates to the devices.</span></span>

<span data-ttu-id="d6b4c-344">Y puede obtener más información sobre el uso de [Device Update for IoT Hub con Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span><span class="sxs-lookup"><span data-stu-id="d6b4c-344">And you can learn more details about use [Device Update for IoT Hub with Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d6b4c-345">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="d6b4c-345">Next steps</span></span>

<span data-ttu-id="d6b4c-346">Para más información acerca de NetX Duo, comience con la [Guía del usuario de Azure RTOS NetX Duo](about-this-guide.md).</span><span class="sxs-lookup"><span data-stu-id="d6b4c-346">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
