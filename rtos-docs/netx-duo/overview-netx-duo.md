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
# <a name="overview-of-azure-rtos-netx-duo"></a>Introducción a Azure RTOS NetX Duo

La pila de red TCP/IP insertada de Azure RTOS NetX Duo es la pila de red TCP/IP dual para IPv4 e IPv6 de clase industrial de Microsoft, que está diseñada específicamente para aplicaciones IoT, en tiempo real y con alto grado de inserción. NetX Duo proporciona aplicaciones insertadas con los principales protocolos de red, como IPv4, IPv6, TCP y UDP, así como un conjunto completo de protocolos adicionales de nivel superior. Azure RTOS NetX Duo ofrece seguridad mediante productos adicionales de seguridad como complementos, entre los que se incluyen IPsec y SSL/TLS/DTLS de Azure RTOS NetX Secure. Todo esto, combinado con una pequeña superficie, una ejecución rápida y una facilidad de uso superior, hacen que Azure RTOS NetX Duo sea la opción ideal para las aplicaciones IoT insertadas más exigentes.

## <a name="api-protocols"></a>Protocolos de API

### <a name="mqtt"></a>MQTT

* Transporte de telemetría de cola de mensajes (MQTT)
* Memoria flash mínima de 2,7 KB

### <a name="auto-ip"></a>IP automática

* Asignación automática de direcciones IPv4
* Mínimo 1,2 KB, 300 bytes de RAM

### <a name="http-https"></a>HTTP, HTTPS

#### <a name="http-10"></a>HTTP 1.0

* Protocolo de transferencia de hipertexto (HTTP)
* Memoria flash mínima de 2,8 KB a 4,8 KB y de 0,4 KB a 1,0 KB de RAM
* Compatibilidad con clientes y servidores

#### <a name="httphttps-11"></a>HTTP/HTTPS 1.1

* Protocolo de transferencia de hipertexto (HTTP)
* Memoria flash mínima de 3,0 KB a 9,5 KB y de 0,5 KB a 2 KB de RAM
* Compatibilidad con clientes y servidores
* Varias sesiones de cliente entrantes
* Texto sin formato y HTTPS cifrado
* Compatibilidad con conexiones persistentes
* Carga de archivos de varias partes
* Totalmente integrado con TLS de Azure RTOS NetX Secure

### <a name="smtp"></a>SMTP

* Protocolo simple de transferencia de correo (SMTP)
* Mínimo 4,1 KB y una superficie de RAM de 0,6 KB
* Compatibilidad con clientes

### <a name="dhcp"></a>DHCP

* Protocolo de configuración dinámica de host (DHCP)
* Memoria flash mínima de 3,6 KB a 4,6 KB y superficie de RAM de 2,7 KB
* Compatibilidad con clientes y servidores
* Compatibilidad con IPv4 e IPv6

### <a name="nat"></a>NAT

* Traducción de direcciones de red (NAT)
* Mínimo 3,5 KB y una superficie de RAM de 0,6 KB
* Compatibilidad con direcciones IPv4
* NAT solo está disponible con Azure RTOS NetX Duo

### <a name="snmp"></a>SNMP

* Protocolo simple de administración de redes (SNMP)
* Mínimo 10,9 KB y una superficie de RAM de 2,6 KB
* Compatibilidad del agente con V1, V2 y V3

### <a name="dns-mdns-dns-sd"></a>DNS, mDNS, DNS-SD

* Sistema de nombres de dominio (DNS)
* Sistema de nombres de dominio de multidifusión (mDNS)
* Detección de servicios basada en DNS (DNS-SD)
* DNS: Memoria flash mínima de 2,4 KB a 3 KB y superficie de RAM de 1 KB
* Compatibilidad con clientes
* mDNS y DNS-SD solo están disponibles con Azure RTOS NetX Duo.

### <a name="pop3"></a>POP3

* Protocolo de oficina de correos versión 3 (POP3)
* Mínimo 8,1 KB y una superficie de RAM de 1,4 KB
* Compatibilidad con clientes

### <a name="telnet"></a>TELNET

* Mínimo 0,5 KB y una superficie de RAM de 0,3 KB
* Compatibilidad con clientes y servidores
* API de Telnet intuitivas: *nx_telnet_\**

### <a name="ftp-tftp"></a>FTP, TFTP

* Protocolo de transferencia de archivos (FTP)
* Protocolo trivial de transferencia de archivos (TFTP)
* FTP: memoria flash mínima de 1,8 KB a 7,2 KB y superficie de RAM de 0,6 KB a 2,1 KB
* TFTP: memoria flash mínima de 1,7 KB a 2,4 KB y superficie de RAM de 0,3 KB a 1,8 KB
* Compatibilidad con clientes y servidores
* API intuitivas de FTP y TFTP: *nx_ftp_\** o *nx_tftp_\**

### <a name="ppp-pppoe"></a>PPP, PPPoE

* Protocolo punto a punto (PPP)
* Protocolo punto a punto sobre Ethernet (PPPoE)
* Mínimo 7,1 KB y una superficie de RAM de 3,8 KB
* API de PPP intuitivas: *nx_ppp_\**

* PPPoE solo está disponible con Azure RTOS NetX Duo

### <a name="sntp"></a>SNTP

* Protocolo simple de tiempo de red (SNTP)
* Mínimo 4 KB y una superficie de RAM de 0,5 KB
* Compatibilidad con clientes
* API de SNTP intuitivas: *nx_sntp_\**

### <a name="azure-rtos-netx-duo-api"></a>API de Azure RTOS NetX Duo

* API intuitivas y coherentes
* Convención de nomenclatura sustantivo-verbo
* Implementación rápida de la API sin copia
* Todas las API comienzan por <i>nx_*</i> para identificarlas fácilmente como pertenecientes a Azure RTOS NetX
* Las API de bloqueo tienen un tiempo de espera de subprocesos opcional
* Consulte [Guía del usuario de Azure RTOS NetX Duo](about-this-guide.md) para más información.
* Capa de BSD opcional para la portabilidad de código de sockets heredado

### <a name="igmp"></a>IGMP

* Protocolo de administración de grupos de Internet (IGMP)
* Memoria flash mínima de 2,5 KB
* Compatibilidad con grupos de multidifusión IPv4
* Validado por IxANVL de IXIA
* Estadísticas de IGMP opcionales
* Seguimiento de nivel de sistema mediante Azure RTOS ThreadX
* API de IGMP intuitivas: *nx_igmp_\**

### <a name="azure-rtos-netx-secure-dtls"></a>DTLS de Azure RTOS NetX Secure

* Seguridad de la capa de transporte del datagrama (DTLS) 1.0 y 1.2
* Memoria flash mínima de 11 KB
* Tamaño de clave rápido con software RSA de 2048 bits ~1 segundo @120MHz
* Implementación optimizada de X.509
* Totalmente integrado con los sockets UDP de Azure RTOS NetX Duo
* Compatibilidad con el cifrado mediante hardware
* Compatibilidad con criptografía de software: RSA (todos los tamaños de clave), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Criptografía de curva elíptica (ECC) con ECDSA (firma) y ECDH (cifrado), incluidas las curvas P 192/224/256/384/521
* Compatibilidad con claves cifradas (dependiente del hardware)

### <a name="azure-rtos-netx-secure-tls"></a>TLS de Azure RTOS NetX Secure

* Seguridad de la capa de transporte (TLS) 1.0, 1.1 y 1.2
* Memoria flash mínima de 8,8 KB
* Tamaño de clave rápido con software RSA de 2048 bits ~1 segundo @120MHz
* Implementación optimizada de X.509
* Totalmente integrado con los sockets TCP de Azure RTOS NetX Duo
* Compatibilidad con el cifrado mediante hardware
* Compatibilidad con criptografía de software: RSA (todos los tamaños de clave), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Criptografía de curva elíptica (ECC) con ECDSA (firma) y ECDH (cifrado), incluidas las curvas P 192/224/256/384/521
* Compatibilidad con claves cifradas (dependiente del hardware)

### <a name="icmp"></a>ICMP

* Protocolo de mensajes de control de Internet (ICMP)
* Memoria flash mínima de 2,5 KB
* Compatibilidad con IPv4 e IPv6
* Validado por IxANVL de IXIA
* Solicitud de ping y respuesta de ping
* Suspensión de subprocesos opcional en solicitudes de ping
* Tiempo de espera opcional en todas las suspensiones
* Estadísticas de ICMP opcionales
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX
* API de ICMP intuitivas: *nx_icmp_\**

### <a name="udp"></a>UDP

* Protocolo de datagramas de usuario (UDP)
* Memoria flash mínima de 2,5 KB, 124 bytes de RAM por socket
* Procesamiento rápido de paquetes TCP, casi a la velocidad del cableado:
    * RX: 95 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 14 % de uso de MCU
    * TX: 94 Mbps en Ethernet de 100 Mbps, MCU @100MHz, 10 % de uso de MCU
* Tecnología UDP Fast Path™
* No hay límites en el número de UDP
* Validado por IxANVL de IXIA
* Suspensión opcional en la recepción de sockets
* Tiempo de espera opcional en todas las suspensiones
* Estadísticas de UDP opcionales
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX
* API de UDP intuitivas: *nx_udp_\**

### <a name="tcp"></a>TCP

* Protocolo de control de transmisión (TCP)
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

### <a name="arprarp"></a>ARP/RARP

* Protocolo de resolución de direcciones (ARP)
* Protocolo de resolución de direcciones inversa (RARP)
* Memoria flash mínima de 1,7 KB, tamaño de RAM
* Resolución dinámica de direcciones MAC de 32 bits IPv4 y 48 bits
* Validado por IxANVL de IXIA
* Memoria caché de ARP flexible y definida por el usuario
* Compatibilidad con ARP gratuito
* Estadísticas de ARP/RARP opcionales determinadas por la aplicación
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX
* API de ARP/RARP intuitivas: *nx_arp_\** , *nx_rarp_\**

### <a name="ipv4-amp-ipv6"></a>IPv4 e IPv6

* Protocolo de Internet (IP)
* Memoria flash mínima de 3,5 KB a 8,5 KB y superficie de RAM de 2 KB a 3 KB
* Arquitectura Piconet™
* Rendimiento rápido, casi a la velocidad del cableado
* Compatibilidad con varias interfaces
* Compatibilidad con host múltiple
* Compatibilidad con enrutamiento estático
* Compatibilidad con la fragmentación IP y el reensamblado
* Compatibilidad con direcciones IPv4 e IPv6
* Validado por IxANVL de IXIA
* Certificación del logotipo IPv6 Ready Fase II
* Estadísticas de IP opcionales
* Interfaz del controlador de la capa física bien definida e intuitiva
* Seguimiento de nivel de sistema mediante Azure RTOS TraceX
* API de capa de IP intuitivas: *nx_ip_\** , *nxd_ip_\** , *nxd_ipv6_\**
* Certificado previamente por TUV y UL para CEI 61508 SIL 4, CEI 62304 clase C, ISO 26262 ASIL D y EN 50128 SW-SIL4

### <a name="azure-rtos-netx-secure-ipsec"></a>IPSEC de Azure RTOS NetX Secure

* Protocolo de seguridad de Internet (IPSec)
* Capa de IP
* Compatibilidad con el cifrado mediante hardware
* Compatibilidad con el cifrado de software, incluidos:
    * DES, 3DES
    * AES
    * HMAC-MD5
    * HMAC-SHA1
* Compatibilidad con el Intercambio de claves por red (IKE) versión 2
* API de IPsec intuitivas: *nx_ipsec_\**
* IPsec solo está disponible con Azure RTOS NetX Duo

## <a name="safe-and-secure"></a>Seguro

Azure RTOS NetX Duo es seguro. Esta seguridad se proporciona mediante productos de seguridad como complementos, entre los que se incluyen IPsec, SSL, TLS y DTLS. Además, la aplicación tiene un control total sobre todo el acceso externo a Azure RTOS NetX Duo, lo que facilita la determinación del riesgo de seguridad.

Microsoft Azure RTOS proporciona a los OEM componentes para proteger la comunicación y crear código y aislamiento de datos mediante los mecanismos de protección de hardware MCU y MPU subyacentes. En última instancia, el fabricante de los dispositivos tiene la responsabilidad de asegurarse de que el dispositivo cumpla totalmente los requisitos de seguridad en constante evolución asociados a su caso de uso específico.


## <a name="interoperability-verification"></a>Comprobación de interoperabilidad

NetX Duo se ajusta a los estándares RFC y ofrece una interoperabilidad completa con los dispositivos de la mayoría de los proveedores.

![Logotipo IPv6 Ready](./media/overview-netx-duo/ipv6-ready-logo.png)

Azure RTOS NetX Duo es una de las pilas TCP/IP insertadas que han conseguido la rigurosa certificación del logotipo IPv6-Ready, evidencia de que ha superado las pruebas de conformidad e interoperabilidad, administradas y validadas por el Foro de IPv6. NetX Duo también emplea el estándar del sector IxANVL (Biblioteca de validación de red automatizada) para la implementación del protocolo TCP/IP principal de NetX Duo.

## <a name="comprehensive-iot-solution"></a>Solución IoT integral

NetX Duo tiene una de las redes TCP/IP más completas para aplicaciones IoT con alto grado de inserción. Esta compatibilidad incluye los siguientes productos de protocolo de complementos.

MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP

## <a name="advanced-technology"></a>Tecnología avanzada

Azure RTOS NetX Duo es una tecnología avanzada que incluye:

* Arquitectura Piconet™
* Escalado automático
* Tecnología UDP Fast-Path™
* Administración de paquetes flexible
* Implementación y API sin copia
* Compatibilidad con host múltiple
* Tiempo de espera opcional en todas las suspensiones
* Compatibilidad con enrutamiento estático
* IPsec
* SSL/TLS/DTLS
* Compatibilidad con el análisis del sistema de Azure RTOS TraceX

## <a name="related-services"></a>Servicios relacionados

### <a name="azure-iot"></a>Azure IoT

NetX Duo incluye [Azure IoT Middleware para Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), una biblioteca específica para plataformas que actúa como capa de enlace entre Azure RTOS y el SDK de Azure para C insertado, con el fin de facilitar la conectividad con los servicios de Azure IoT. Estos son los objetivos de Azure IoT Middleware:
* Proporcionar las interfaces de cliente inteligentes (IoTHub_Client y DeviceProvisioning_Client) que los desarrolladores necesitan para sus aplicaciones.
* Organizar la interacción entre el SDK de C insertado y la plataforma.
* Proporcionar la inicialización de la plataforma Azure RTOS.
* Compatibilidad con IoT Plug and Play.
* Funcionalidades de seguridad.
* Conocimiento de la limitación de recursos.
* Compatibilidad de protocolos.

![Servicios relacionados con Azure RTOS NetX Duo](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a>Azure Defender

El módulo de seguridad de Azure Defender para IoT proporciona una solución de seguridad completa para dispositivos Azure RTOS. El módulo de seguridad de Azure RTOS ofrece detección de actividad de red malintencionada, creación de línea base del comportamiento del dispositivo basada en alertas personalizadas y ayuda a mejorar la higiene de la seguridad del dispositivo. Más información en [Información general: microagente de Defender para IoT de Defender para IoT para Azure RTOS (versión preliminar)](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) o comience a trabajar con la guía de inicio rápido [Configuración del módulo de seguridad para Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module).

### <a name="device-update-for-iot-hub"></a>Device Update para IoT Hub

[Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) es un servicio que permite implementar actualizaciones inalámbricas (OTA) para sus dispositivos IoT. El módulo Device Update for IoT Hub es la implementación del agente de Device Update para IoT Hub en Azure RTOS NetX Duo. Proporciona API sencillas para que los generadores de dispositivos integren la funcionalidad de actualización de dispositivos en sus aplicaciones.

Consulte los ejemplos de paneles clave de evaluación de semiconductores que incluyen las guías introductorias para aprender a configurar, crear e implementar las actualizaciones inalámbricas en los dispositivos.

Y puede obtener más información sobre el uso de [Device Update for IoT Hub con Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).

## <a name="next-steps"></a>Pasos siguientes

Para más información acerca de NetX Duo, comience con la [Guía del usuario de Azure RTOS NetX Duo](about-this-guide.md).
