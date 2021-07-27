---
title: Descripción de Azure RTOS NetX
description: Azure RTOS NetX es una implementación de alto rendimiento de los estándares del protocolo TCP/IP, totalmente integrada con Azure RTOS ThreadX y disponible para todos los procesadores compatibles.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 63fd212249da6154926684f9bc844d2c2a78e84e
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754852"
---
# <a name="overview-of-azure-rtos-netx"></a>Introducción a Azure RTOS NetX

Azure RTOS NetX es una pila de red insertada en IPv4 TCP/IP y de nivel industrial diseñada específicamente para aplicaciones de IoT, en tiempo real y profundamente insertadas. Azure RTOS NetX es la pila de red IPv4 original de Microsoft y es esencialmente un subconjunto de Azure RTOS. NetX proporciona aplicaciones insertadas con los principales protocolos de red, como IPv4, TCP y UDP, así como un conjunto completo de protocolos adicionales de nivel superior. Una pequeña superficie, una ejecución rápida y una facilidad de uso superior hacen que Azure RTOS NetX sea una opción ideal para las aplicaciones de IoT integradas más exigentes.

## <a name="api-protocols"></a>Protocolos de API
Azure RTOS NetX proporciona compatibilidad con los siguientes protocolos.

### <a name="telnet"></a>TELNET

* Superficie de memoria RAM mínima 0,5 KB y 0,3 KB.
* Compatibilidad con cliente y servidor.

### <a name="auto-ip"></a>IP automática

* Asignación automática de direcciones IPv4.
* Mínimo 1,2 KB; 300 bytes de RAM.

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP - Protocolo de transferencia de hipertexto (HTTP)

* Memoria flash mínima de 2,8 KB a 4,8 KB; superficie de memoria RAM de 0,4 KB a 1,0 KB.
* Compatibilidad con cliente y servidor.

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP - Protocolo simple de transferencia de correo (SMTP)

* Mínimo 4,1 KB y una superficie de RAM de 0,6 KB
* Compatibilidad con clientes

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP - Protocolo de configuración dinámica de host (DHCP)

* Memoria flash mínima de 3,6 KB a 4,6 KB, superficie de RAM de 2,7 KB
* Compatibilidad con clientes y servidores
* Compatibilidad con IPv4

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3: Protocolo de oficina de correos, versión 3 (POP3)

* Mínimo 8,1 KB y una superficie de RAM de 1,4 KB
* Compatibilidad con clientes

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP - Protocolo simple de administración de redes (SNMP)

* Mínimo 10,9 KB y una superficie de RAM de 2,6 KB
* Compatibilidad del agente con V1, V2 y V3

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP, TFTP - Protocolo de transferencia de archivos (FTP), Protocolo trivial de transferencia de archivos (TFTP)

* FTP: memoria flash mínima de 1,8 KB a 7,2 KB y superficie de RAM de 0,6 KB a 2,1 KB
* TFTP: memoria flash mínima de 1,7 KB a 2,4 KB y superficie de RAM de 0,3 KB a 1,8 KB
* Compatibilidad con clientes y servidores

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP - Protocolo punto a punto (PPP)

* Mínimo 7,1 KB y una superficie de RAM de 3,8 KB
* Confiable.

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP-Protocolo simple de tiempo de red (SNTP)

* Mínimo 4 KB y una superficie de RAM de 0,5 KB
* Compatibilidad con clientes

### <a name="azure-rtos-netx-api"></a>API de Azure RTOS NetX

* Implementación rápida de la API sin copia
* Capa de BSD opcional para la portabilidad de código de sockets heredado

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP - Protocolo de administración de grupos de Internet (IGMP)

* Memoria flash mínima de 2,5 KB
* Compatibilidad con grupos de multidifusión IPv4
* Validado por IxANVL de IXIA
* Estadísticas de IGMP opcionales
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX

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

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP - Protocolo de mensajes de control de Internet (ICMP)

* Memoria flash mínima de 2,5 KB
* Compatibilidad con IPv4
* Validado por IxANVL de IXIA
* Solicitud de ping y respuesta de ping
* Suspensión de subprocesos opcional en solicitudes de ping
* Tiempo de espera opcional en todas las suspensiones
* Estadísticas de ICMP opcionales
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX

### <a name="ipv4---internet-protocol-ip"></a>IPv4 - Protocolo de Internet (IP)

* Memoria flash mínima de 3,5 KB a 8,5 KB; superficie de memoria RAM de 2 KB a 3 KB.
* Arquitectura Piconet™.
* Rendimiento rápido, casi a velocidad de cable.
* Compatibilidad con varias interfaces.
* Compatibilidad con hosts múltiples.
* Compatibilidad con enrutamiento estático.
* Compatibilidad con el reensamblado y la fragmentación IP.
* Compatibilidad con IPv4.
* Validado por IxANVL de IXIA.
* Certificación de logotipo Preparado para fase II.
* Estadísticas de IP opcionales.
* Interfaz del controlador de la capa física intuitiva y bien definida.
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX.

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP - Protocolo de resolución de direcciones (ARP), Protocolo de resolución inversa de direcciones (RARP)

* Memoria flash mínima de 1,7 KB, tamaño de RAM.
* Resolución dinámica de direcciones MAC de 32 bits IPv4 y 48 bits.
* Validado por IxANVL de IXIA.
* Caché de ARP flexible y definida por el usuario.
* Compatibilidad con ARP gratuita.
* Estadísticas de ARP/RARP opcionales determinadas por la aplicación.
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX.

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.

## <a name="interoperability-verification"></a>Comprobación de interoperabilidad

Azure RTOS NetX se ajusta a los estándares de RFC y ofrece una interoperabilidad completa con los dispositivos de la mayoría de los proveedores. Azure RTOS NetX también emplea el estándar del sector IxANVL (Biblioteca de validación de red automatizada) para la implementación del protocolo TCP/IP principal de Azure RTOS NetX.

## <a name="advanced-technology"></a>Tecnología avanzada

Azure RTOS NetX es una tecnología avanzada que incluye los elementos siguientes.
* Arquitectura Piconet™.
* Escalado automático.
* Tecnología UDP Fast-Path™.
* Administración de paquetes flexible.
* Implementación y API sin copia.
* Compatibilidad con hosts múltiples.
* Tiempo de espera opcional en todas las suspensiones.
* Compatibilidad con enrutamiento estático.
* Compatibilidad con el análisis del sistema de Azure RTOS TraceX.
