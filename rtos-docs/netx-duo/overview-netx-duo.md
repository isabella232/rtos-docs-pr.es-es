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
# <a name="overview-of-azure-rtos-netx-duo"></a>Introducción a Azure RTOS NetX Duo

La pila de red TCP/IP insertada de Azure RTOS NetX Duo es la pila de red TCP/IP dual para IPv4 e IPv6 de clase industrial de Microsoft, que está diseñada específicamente para aplicaciones IoT, en tiempo real y con alto grado de inserción. NetX Duo proporciona aplicaciones insertadas con los principales protocolos de red, como IPv4, IPv6, TCP y UDP, así como un conjunto completo de protocolos adicionales de nivel superior. Azure RTOS NetX Duo ofrece seguridad mediante productos adicionales de seguridad como complementos, entre los que se incluyen IPsec y SSL/TLS/DTLS de Azure RTOS NetX Secure. Todo esto, combinado con una pequeña superficie, una ejecución rápida y una facilidad de uso superior, hacen que Azure RTOS NetX Duo sea la opción ideal para las aplicaciones IoT insertadas más exigentes.

## <a name="api-protocols"></a>Protocolos de API

### <a name="mqtt"></a>MQTT

* Transporte de telemetría de cola de mensajes (MQTT)
* Memoria flash mínima de 2,7 KB
* API de MQTT intuitivas: *nx_mqtt_* \*

### <a name="auto-ip"></a>IP automática

* Asignación automática de direcciones IPv4
* 1,2 KB como mínimo, 300 bytes de RAM
* API de IP automática intuitivas: *nx_autoip_\**

### <a name="http-https"></a>HTTP, HTTPS

#### <a name="http-10"></a>HTTP 1.0

* Protocolo de transferencia de hipertexto (HTTP)
* Memoria flash mínima de 2,8 KB a 4,8 KB y de 0,4 KB a 1,0 KB de RAM
* Compatibilidad con clientes y servidores
* API intuitivas: *nx_http_\**

#### <a name="httphttps-11"></a>HTTP/HTTPS 1.1

* Protocolo de transferencia de hipertexto (HTTP)
* Memoria flash mínima de 3,0 KB a 9,5 KB y de 0,5 KB a 2 KB de RAM
* Compatibilidad con clientes y servidores
* Varias sesiones de cliente entrantes
* Texto sin formato y HTTPS cifrado
* Compatibilidad con conexiones persistentes
* Carga de archivos de varias partes
* Totalmente integrado con TLS de Azure RTOS NetX Secure
* API intuitivas: *nx_web_http\**

### <a name="smtp"></a>SMTP

* Protocolo simple de transferencia de correo (SMTP)
* Mínimo 4,1 KB y una superficie de RAM de 0,6 KB
* Compatibilidad con clientes
* API de SMTP intuitivas: *nx_smtp_\**

### <a name="dhcp"></a>DHCP

* Protocolo de configuración dinámica de host (DHCP)
* Memoria flash mínima de 3,6 KB a 4,6 KB y superficie de RAM de 2,7 KB
* Compatibilidad con clientes y servidores
* Compatibilidad con IPv4 e IPv6
* API de DHCP intuitivas: *nx_dhcp_\**

### <a name="nat"></a>NAT

* Traducción de direcciones de red (NAT)
* Mínimo 3,5 KB y una superficie de RAM de 0,6 KB
* Compatibilidad con direcciones IPv4
* API de NAT intuitivas: *nx_nat_\**
* NAT solo está disponible con Azure RTOS NetX Duo

### <a name="snmp"></a>SNMP

* Protocolo simple de administración de redes (SNMP)
* Mínimo 10,9 KB y una superficie de RAM de 2,6 KB
* Compatibilidad del agente con V1, V2 y V3
* API de SNMP intuitivas: *nx_snmp_\**

### <a name="dns-mdns-dns-sd"></a>DNS, mDNS, DNS-SD

* Sistema de nombres de dominio (DNS)
* Sistema de nombres de dominio de multidifusión (mDNS)
* Detección de servicios basada en DNS (DNS-SD)
* DNS: Memoria flash mínima de 2,4 KB a 3 KB y superficie de RAM de 1 KB
* Compatibilidad con clientes
* API intuitivas: *nx_dns_\**
* mDNS y DNS-SD solo están disponibles con Azure RTOS NetX Duo.

### <a name="p0p3"></a>POP3

* Protocolo de oficina de correos versión 3 (POP3)
* Mínimo 8,1 KB y una superficie de RAM de 1,4 KB
* Compatibilidad con clientes
* API de POP3 intuitivas: *nx_pop3_\**

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

## <a name="small-footprint"></a>Superficie pequeña

Azure RTOS NetX Duo tiene una superficie notablemente pequeña, de 9 KB a 15 KB, para la compatibilidad básica con IP y UDP. Se necesita una memoria de área de instrucciones adicional de 10 KB a 13 KB para la funcionalidad de TCP. El uso de RAM de Azure RTOS NetX Duo suele oscilar entre 2,6 KB y 3,6 KB más la memoria del grupo de paquetes, definida por la aplicación. Al igual que Azure RTOS ThreadX, el tamaño de Azure RTOS NetX Duo se escala automáticamente en función de los servicios que usa la aplicación. Esto elimina prácticamente la necesidad de configuraciones y parámetros de compilación complicados, lo que facilita el trabajo del desarrollador.

## <a name="fast-execution"></a>Ejecución rápida

Azure RTOS NetX Duo proporciona una implementación de envío y recepción de paquetes sin copia, muy integrada con Azure RTOS ThreadX, para lograr el rendimiento más rápido posible. Por ejemplo, Azure RTOS NetX Duo normalmente puede lograr transferencias de datos cercanas a la velocidad del cableado en un procesador de 80 MHz (o menos), en tanto que se usa un pequeño porcentaje de ciclos del procesador.

## <a name="simple-easy-to-use"></a>Simple y fácil de usar

La API de Azure RTOS NetX Duo es intuitiva, sencilla y muy funcional.

Los nombres de API se componen de palabras reales y no de la sopa de letras de nombres muy abreviados que son tan comunes en otros productos de redes. Todas las API de Azure RTOS NetX Duo tienen *nx_* al inicio y siguen una convención de nomenclatura sustantivo-verbo. Además, existe una coherencia funcional en la API. Por ejemplo, todas las funciones de API con suspensión tienen un tiempo de espera opcional que funciona de forma idéntica.

En el caso de las aplicaciones heredadas, Azure RTOS NetX Duo ofrece una capa adicional compatible con sockets BSD. Esta capa ayuda a los desarrolladores a migrar fácilmente aplicaciones de redes de gran tamaño.

## <a name="safe-and-secure"></a>Seguro

Azure RTOS NetX Duo es seguro. Esta seguridad se proporciona mediante productos de seguridad como complementos, entre los que se incluyen IPsec, SSL, TLS y DTLS. Además, la aplicación tiene un control total sobre todo el acceso externo a Azure RTOS NetX Duo, lo que facilita la determinación del riesgo de seguridad.

Microsoft Azure RTOS proporciona a los OEM componentes para proteger la comunicación y crear código y aislamiento de datos mediante los mecanismos de protección de hardware MCU y MPU subyacentes. En última instancia, el fabricante de los dispositivos tiene la responsabilidad de asegurarse de que el dispositivo cumpla totalmente los requisitos de seguridad en constante evolución asociados a su caso de uso específico.

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>Certificado previamente por TUV y UL para varios estándares de seguridad

Azure RTOS NetX Duo ha sido certificado por SGS-TUV Saar para su uso en sistemas críticos para la seguridad, de acuerdo con CEI-61508 SIL 4, CEI-62304 Clase de seguridad de SW C, ISO 26262 ASIL D y EN 50128. La certificación confirma que Azure RTOS NetX Duo se puede usar en el desarrollo de software relacionado con la seguridad para los niveles de integridad de seguridad más altos de CEI-61508, CEI-62304, ISO 26262 y EN 50128 para la "Seguridad funcional de los sistemas eléctricos, electrónicos y electrónicos programables relacionados con la seguridad". SG-TUV Saar, que es una sociedad conjunta entre las empresas alemanas SGS-Group y TUV Saarland, se ha convertido en la empresa líder independiente acreditada para probar, auditar, comprobar y certificar software insertado para sistemas relacionados con la seguridad en todo el mundo. El estándar de seguridad industrial CEI 61508 y todos los estándares que se derivan de él, incluidos CEI-62304, ISO 26262 y EN 50128, se usan para garantizar la seguridad funcional de los dispositivos médicos eléctricos, electrónicos y electrónicos programables relacionados con la seguridad, los sistemas de control de procesos, la maquinaria industrial, los automóviles y los sistemas de control de ferrocarriles.

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="Certificación SGS-TUV":::

Azure RTOS NetX Duo ha sido reconocido por UL por su conformidad con los estándares de seguridad para software de componentes programables UL 60730-1 anexo H, CSA E60730-1 anexo H, CEI 60730-1 anexo H, UL 60335-1 anexo R, CEI 60335-1 anexo R y UL 1998. UL es una empresa global e independiente especializada en la seguridad en la ciencia con más de un siglo de experiencia aportando innovaciones en soluciones de seguridad que abarcan desde la adopción pública de electricidad hasta los avances en sostenibilidad, energías renovables y nanotecnología.

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="Certificación UL CRU":::

Los artefactos (certificado, manual de seguridad, informe de pruebas, etc.) asociados a las certificaciones TUV y UL están disponibles para su venta.

En los casos en los que la aplicación necesite certificación adicional, hay un servicio de certificación disponible con Microsoft para proporcionar una certificación llave en mano para varios estándares con la plataforma de hardware real e incluso abarcando el código de la aplicación. Póngase en contacto con nosotros para más detalles sobre nuestro servicio de certificación.

## <a name="eal4-common-criteria-security-certification"></a>Certificación de seguridad EAL4+ de Common Criteria

Azure RTOS ha logrado la certificación de seguridad EAL4+ de Common Criteria. El objetivo de la evaluación (TOE) cubre Azure RTOS ThreadX, Azure RTOS NetX Duo, TLS de Azure RTOS NetX Secure y MQTT de Azure RTOS NetX. Representa los protocolos de IoT más habituales que requieren los sensores, dispositivos, enrutadores perimetrales y puertas de enlace con alto grado de inserción.

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="Certificación EAL":::

El recurso de evaluación de seguridad de TI usado para la certificación de seguridad de Microsoft Azure RTOS SC es Brightsight BV y la entidad de certificación es SERTIT.

## <a name="fips-140-2-validated"></a>Validación conforme a FIPS 140-2

Las bibliotecas criptográficas de Azure RTOS NetX han logrado la certificación del Estándar federal de procesamiento de información 140-2 (FIPS 140-2) para software, que especifica los requisitos para los módulos criptográficos. FIPS 140-2 requiere que todos los organismos y departamentos gubernamentales federales que usan seguridad basada en cifrado cumplan los estándares específicos relacionados con el nivel y las funcionalidades de cifrado. Estos estándares de seguridad basados en el cifrado también se reconocen en Canadá y en la Unión Europea.

El laboratorio de evaluación de la seguridad de la información utilizado para las bibliotecas criptográficas de Azure RTOS NetX fue atsec y la entidad de certificación es el Instituto nacional de estándares y tecnología (NIST). Consulte el [sitio web del NIST](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) para más información.

## <a name="interoperability-verification"></a>Comprobación de interoperabilidad

NetX Duo se ajusta a los estándares RFC y ofrece una interoperabilidad completa con los dispositivos de la mayoría de los proveedores.

![Logotipo IPv6 Ready](./media/overview-netx-duo/ipv6-ready-logo.png)

Azure RTOS NetX Duo es una de las pilas TCP/IP insertadas que han conseguido la rigurosa certificación del logotipo IPv6-Ready, evidencia de que ha superado las pruebas de conformidad e interoperabilidad, administradas y validadas por el Foro de IPv6. NetX Duo también emplea el estándar del sector IxANVL (Biblioteca de validación de red automatizada) para la implementación del protocolo TCP/IP principal de NetX Duo.

## <a name="comprehensive-iot-solution"></a>Solución IoT integral

Azure RTOS NetX Duo tiene una superficie notablemente pequeña, de 9 KB a 15 KB, para la compatibilidad básica con IP y UDP. NetX Duo tiene una de las redes TCP/IP más completas para aplicaciones IoT con alto grado de inserción. Esta compatibilidad incluye los siguientes productos de protocolo de complementos:

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

## <a name="fastest-time-to-market"></a>Tiempo de comercialización más rápido

Azure RTOS NetX Duo es fácil de instalar, aprender, usar, depurar, comprobar, certificar y mantener. Como resultado, NetX Duo es una de las pilas TCP/IP más populares para dispositivos IoT insertados, incluidos muchos SoC de Broadcom, GainSpan, etc. Nuestra sólida ventaja en el tiempo de comercialización se basa en lo siguiente:

* Documentación de calidad: consulte nuestra [Guía del usuario de Azure RTOS NetX Duo](about-this-guide.md) y véalo usted mismo.
* Disponibilidad completa del código fuente
* API fáciles de usar
* Conjunto de características completo y avanzado

## <a name="one-simple-license"></a>Una licencia sencilla

No hay ningún costo asociado al uso y las pruebas del código fuente ni a las licencias de producción si se implementa en dispositivos con licencia previa; todos los demás dispositivos necesitan una licencia anual sencilla.

## <a name="full-highest-quality-source-code"></a>Código fuente completo y de máxima calidad

A lo largo de los años, el código fuente de Azure RTOS NetX Duo ha marcado el listón en calidad y facilidad de comprensión. Además, la convención de tener una función por archivo facilita el examen del código fuente.

## <a name="supports-most-popular-architectures"></a>Compatible con las arquitecturas más populares

Azure RTOS NetX Duo se ejecuta en los microprocesadores de 32 y 64 bits más populares, de serie, totalmente probado y totalmente compatible, incluidas las siguientes arquitecturas avanzadas:

**Dispositivos analógicos**: SHARC, Blackfin, CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: MCU serie pollo

**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Cadence**: Xtensa, Diamond

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi

**Cypress**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel e Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10

**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, Synergy

**Silicon Labs**: EFM32

**Synopsys**: ARC 600, 700, ARC EM, ARC HS

**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Todas las cifras de tiempos y tamaños enumeradas son estimaciones y pueden ser diferentes en su plataforma de desarrollo.*

## <a name="related-services"></a>Servicios relacionados

El módulo de seguridad RTOS de Azure Security Center para IoT proporciona una solución de seguridad integral para dispositivos Azure RTOS. El módulo de seguridad de Azure RTOS ofrece detección de actividad de red malintencionada, creación de línea base del comportamiento del dispositivo basada en alertas personalizadas y ayuda a mejorar la higiene de la seguridad del dispositivo. Más información en [Información general: microagente de Defender para IoT de Defender para IoT para Azure RTOS (versión preliminar)](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) o comience a trabajar con la guía de inicio rápido [Configuración del módulo de seguridad para Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module).

## <a name="next-steps"></a>Pasos siguientes

Para más información acerca de NetX Duo, comience con la [Guía del usuario de Azure RTOS NetX Duo](about-this-guide.md).
