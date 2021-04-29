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
# <a name="overview-of-azure-rtos-netx"></a>Introducción a Azure RTOS NetX

Azure RTOS NetX es una pila de red insertada en IPv4 TCP/IP y de nivel industrial diseñada específicamente para aplicaciones de IoT, en tiempo real y profundamente insertadas. Azure RTOS NetX es la pila de red IPv4 original de Microsoft y es esencialmente un subconjunto de Azure RTOS. NetX proporciona aplicaciones insertadas con los principales protocolos de red, como IPv4, TCP y UDP, así como un conjunto completo de protocolos adicionales de nivel superior. Una pequeña superficie, una ejecución rápida y una facilidad de uso superior hacen que Azure RTOS NetX sea una opción ideal para las aplicaciones de IoT integradas más exigentes.

## <a name="api-protocols"></a>Protocolos de API

### <a name="telnet"></a>TELNET

* Mínimo 0,5 KB y una superficie de RAM de 0,3 KB
* Compatibilidad con clientes y servidores
* API de Telnet intuitivas: *nx_telnet_\**

### <a name="auto-ip"></a>IP automática

* Asignación automática de direcciones IPv4
* Mínimo 1,2 KB, 300 bytes de RAM
* API de IP automática intuitivas: *nx_autoip_\**

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP - Protocolo de transferencia de hipertexto (HTTP)

* Memoria flash mínima 2,8 KB a 4,8 KB, superficie de RAM de 0,4 KB a 1,0 KB
* Compatibilidad con clientes y servidores
* API de HTTP intuitivas: *nx_http_\**

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP - Protocolo simple de transferencia de correo (SMTP)

* Mínimo 4,1 KB y una superficie de RAM de 0,6 KB
* Compatibilidad con clientes
* API de SMTP intuitivas: *nx_smtp_\**

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP - Protocolo de configuración dinámica de host (DHCP)

* Memoria flash mínima de 3,6 KB a 4,6 KB, superficie de RAM de 2,7 KB
* Compatibilidad con clientes y servidores
* Compatibilidad con IPv4
* API de DHCP intuitiva: *nx_dhcp_\**

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3: Protocolo de oficina de correos, versión 3 (POP3)

* Mínimo 8,1 KB y una superficie de RAM de 1,4 KB
* Compatibilidad con clientes
* API de POP3 intuitivas: *nx_pop3_\**

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP - Protocolo simple de administración de redes (SNMP)

* Mínimo 10,9 KB y una superficie de RAM de 2,6 KB
* Compatibilidad del agente con V1, V2 y V3
* API de SNMP intuitivas: *nx_snmp_\**

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP, TFTP - Protocolo de transferencia de archivos (FTP), Protocolo trivial de transferencia de archivos (TFTP)

* FTP: memoria flash mínima de 1,8 KB a 7,2 KB y superficie de RAM de 0,6 KB a 2,1 KB
* TFTP: memoria flash mínima de 1,7 KB a 2,4 KB y superficie de RAM de 0,3 KB a 1,8 KB
* Compatibilidad con clientes y servidores
* API intuitivas de FTP y TFTP: <i>nx_ftp_ *</i> o <i>nx_tftp_* </i>

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP - Protocolo punto a punto (PPP)

* Mínimo 7,1 KB y una superficie de RAM de 3,8 KB
* API de PPP intuitivas: *nx_ppp_\**

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP-Protocolo simple de tiempo de red (SNTP)

* Mínimo 4 KB y una superficie de RAM de 0,5 KB
* Compatibilidad con clientes
* API de SNTP intuitivas: *nx_sntp_\**

### <a name="azure-rtos-netx-api"></a>API de Azure RTOS NetX

* API intuitivas y coherentes
* Convención de nomenclatura sustantivo-verbo
* Implementación rápida de la API sin copia
* Todas las funciones de la API comienzan por <i>nx_*</i> para identificarlas fácilmente como pertenecientes a Azure RTOS NetX
* Tiempo de espera de subproceso opcional para las funciones de la API de bloqueo
* Capa de BSD opcional para la portabilidad de código de sockets heredado

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP - Protocolo de administración de grupos de Internet (IGMP)

* Memoria flash mínima de 2,5 KB
* Compatibilidad con grupos de multidifusión IPv4
* Validado por IxANVL de IXIA
* Estadísticas de IGMP opcionales
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX
* API de IGMP intuitivas: *nx_igmp_\**

### <a name="udp---user-datagram-protocol-udp"></a>UDP - Protocolo de datagramas de usuario (UDP)

* Memoria flash mínima de 2,5 KB, 124 bytes de RAM por socket
* Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:
* RX: 95 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 14 % de uso de MCU
* TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 10 % de uso de MCU
* Tecnología UDP Fast Path™
* No hay límites en el número de UDP.
* Validado por IxANVL de IXIA
* Suspensión opcional en la recepción de sockets
* Tiempo de espera opcional en todas las suspensiones
* Estadísticas de UDP opcionales
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX
* API de UDP intuitivas: *nx_udp_\**

### <a name="tcp---transmission-control-protocol-tcp"></a>TCP - Protocolo de control de transmisión (TCP)

* Memoria flash mínima de 10,5 KB a 12,5 KB, 280 bytes de RAM por socket
* Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:
* RX: 93 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 20 % de uso de MCU
* TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 27 % de uso de MCU
* Conexión confiable
* No hay límites en el número de sockets de TCP
* Validado por IxANVL de IXIA
* Suspensión opcional en la recepción y transmisión de sockets
* Tiempo de espera opcional en todas las suspensiones
* Estadísticas de TCP opcionales
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX
* API de TCP intuitivas: *nx_tcp_\**

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP - Protocolo de mensajes de control de Internet (ICMP)

* Memoria flash mínima de 2,5 KB
* Compatibilidad con IPv4
* Validado por IxANVL de IXIA
* Solicitud de ping y respuesta de ping
* Suspensión de subprocesos opcional en solicitudes de ping
* Tiempo de espera opcional en todas las suspensiones
* Estadísticas de ICMP opcionales
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX
* API de ICMP intuitivas: *nx_icmp_\**

### <a name="ipv4---internet-protocol-ip"></a>IPv4 - Protocolo de Internet (IP)

* Memoria flash mínima de 3,5 KB a 8,5 KB y superficie de RAM de 2 KB a 3 KB
* Arquitectura Piconet™
* Rendimiento rápido, casi a la velocidad del cableado
* Compatibilidad con varias interfaces
* Compatibilidad con host múltiple
* Compatibilidad con enrutamiento estático
* Compatibilidad con la fragmentación IP y el reensamblado
* Compatibilidad con IPv4
* Validado por IxANVL de IXIA
* Certificación de logotipo preparado para fase II
* Estadísticas de IP opcionales
* Interfaz del controlador de la capa física bien definida e intuitiva
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX
* API de capa de IP intuitivas: *nx_ip_\** , *nxd_ip_\**
* Certificado previamente por TUV y UL para CEI 61508 SIL 4, CEI 62304 clase C, ISO 26262 ASIL D y EN 50128 SW-SIL4

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP - Protocolo de resolución de direcciones (ARP), Protocolo de resolución inversa de direcciones (RARP)

* Memoria flash mínima de 1,7 KB, tamaño de RAM
* Resolución dinámica de direcciones MAC de 32 bits IPv4 y 48 bits
* Validado por IxANVL de IXIA
* Memoria caché de ARP flexible y definida por el usuario
* Compatibilidad con ARP gratuito
* Estadísticas de ARP/RARP opcionales determinadas por la aplicación
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX
* API de ARP/RARP intuitivas: *nx_arp_\** , *nx_rarp_\**

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.

## <a name="small-footprint"></a>Superficie pequeña

Azure RTOS NetX tiene una superficie notablemente pequeña, de 9 KB a 15 KB, para la compatibilidad básica con IP y UDP. Se necesita una memoria de área de instrucciones adicional de 10 KB a 13 KB para la funcionalidad de TCP. El uso de RAM de Azure RTOS NetX suele oscilar entre 2,6 KB y 3,6 KB más la memoria del grupo de paquetes, definida por la aplicación. Al igual que Azure RTOS ThreadX, el tamaño de Azure RTOS NetX se escala automáticamente en función de los servicios que usa la aplicación. Esto elimina prácticamente la necesidad de configuraciones y parámetros de compilación complicados, lo que facilita el trabajo del desarrollador.

## <a name="fast-execution"></a>Ejecución rápida

Azure RTOS NetX proporciona una implementación de envío y recepción de paquetes sin copia, y está muy integrada con Azure RTOS ThreadX, para lograr el rendimiento más rápido posible. Por ejemplo, Azure RTOS NetX normalmente puede lograr transferencias de datos cercanas a la velocidad del cableado en un procesador de 80 MHz (o menos), en tanto que se usa un pequeño porcentaje de ciclos del procesador.

## <a name="simple-easy-to-use"></a>Simple y fácil de usar

Azure RTOS NetX es fácil de usar. La API de Azure RTOS NetX es intuitiva y altamente funcional. Los nombres de API se componen de palabras reales y no de la sopa de letras de nombres muy abreviados que son tan comunes en otros productos de redes. Todas las API de Azure RTOS NetX tienen *nx_* al inicio y siguen una convención de nomenclatura sustantivo-verbo. Además, existe una coherencia funcional en la API. Por ejemplo, todas las funciones de API que se suspenden tienen un tiempo de espera opcional que funciona de forma idéntica. En el caso de las aplicaciones heredadas, Azure RTOS NetX ofrece una capa adicional compatible con sockets BSD. Esta capa ayuda a los desarrolladores a migrar fácilmente aplicaciones de redes de gran tamaño.

## <a name="interoperability-verification"></a>Comprobación de interoperabilidad

Azure RTOS NetX se ajusta a los estándares RFC y ofrece una interoperabilidad completa con los dispositivos de la mayoría de los proveedores. Azure RTOS NetX también emplea el estándar del sector IxANVL (Biblioteca de validación de red automatizada) para la implementación del protocolo TCP/IP principal de Azure RTOS NetX.

## <a name="advanced-technology"></a>Tecnología avanzada

Azure RTOS NetX es una tecnología avanzada que incluye:

* Arquitectura Piconet™
* ajustar escala automáticamente
* Tecnología UDP Fast-Path™
* Administración de paquetes flexible
* Implementación y API sin copia
* Compatibilidad con host múltiple
* Tiempo de espera opcional en todas las suspensiones
* Compatibilidad con enrutamiento estático
* Compatibilidad con el análisis del sistema de Azure RTOS TraceX

## <a name="fastest-time-to-market"></a>Tiempo de comercialización más rápido

Azure RTOS NetX es fácil de instalar, conocer, usar, depurar, comprobar, certificar y mantener. Como resultado, Azure RTOS NetX es una de las pilas TCP/IP más populares para dispositivos IoT integrados, incluidos muchos SoC de Broadcom, GainSpan, etc. Nuestra ventaja continua de plazo de comercialización se basa en lo siguiente:

* Documentación de calidad: consulte nuestra [guía de usuario de Azure RTOS NetX](about-this-guide.md) y véalo personalmente.
* Disponibilidad completa del código fuente
* API fáciles de usar
* Conjunto de características completo y avanzado

## <a name="one-simple-license"></a>Una licencia sencilla

No hay ningún costo asociado al uso y las pruebas del código fuente ni a las licencias de producción si se implementa en dispositivos con licencia previa; todos los demás dispositivos necesitan una licencia anual sencilla.

## <a name="full-highest-quality-source-code"></a>Código fuente completo y de máxima calidad

A lo largo de los años, el código fuente de Azure RTOS NetX ha marcado el listón en calidad y facilidad de comprensión. Además, la convención de tener una función por archivo facilita la navegación por el origen.

## <a name="supports-most-popular-architectures"></a>Compatible con las arquitecturas más populares

Azure RTOS NetX se ejecuta en los microprocesadores de 32 y 64 bits más populares, de serie, totalmente probado y totalmente compatible, incluidas las siguientes arquitecturas avanzadas:

**Dispositivos analógicos**: SHARC, Blackfin, CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: Apollo MCU

**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Cadence**: Xtensa, Diamond

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi

**Cypress**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10

**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, Synergy

**Silicon Labs**: EFM32

**Synopsys**: ARC 600, 700, ARC EM, ARC HS

**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Todas las cifras de tiempos y tamaños enumeradas son estimaciones y pueden ser diferentes en su plataforma de desarrollo.*
