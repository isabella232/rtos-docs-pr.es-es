---
title: 'Capítulo 1: Introducción a Azure RTOS NetX Duo'
description: Este capítulo contiene una introducción a Azure RTOS NetX Duo y una descripción de sus aplicaciones y ventajas.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9b5e0ea82319bd369318cca753cf1db222ca29b0b4db3da150642ca007f1191
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789872"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo"></a>Capítulo 1: Introducción a Azure RTOS NetX Duo

Azure RTOS NetX Duo es una implementación en tiempo real de alto rendimiento de los estándares de TCP/IP diseñada exclusivamente para aplicaciones insertadas basadas en Azure RTOS ThreadX. Este capítulo contiene una introducción a NetX Duo y una descripción de sus aplicaciones y ventajas. 

## <a name="netx-duo-unique-features"></a>Características únicas de NetX Duo

A diferencia de otras implementaciones de TCP/IP, NetX Duo está diseñado para ser versátil, ya que permite escalar fácilmente desde pequeñas aplicaciones basadas en microcontroladores a otras que usan los potentes procesadores RISC y DSP. Significa un marcado contraste con las implementaciones de dominio público u otras implementaciones comerciales diseñadas originalmente para entornos de estación de trabajo, pero que después se han aprovechado para diseños insertados.

### <a name="piconettrade-architecture"></a>Arquitectura Piconet&trade;

Subyacente a la escalabilidad y el rendimiento superiores de NetX Duo está <em>Piconet</em>, una arquitectura de software especialmente diseñada para sistemas insertados. La arquitectura Piconet maximiza la escalabilidad mediante la implementación de los servicios de NetX Duo como una biblioteca de C. De esta manera, solo se incorporan a la imagen final en tiempo de ejecución los servicios que usa la aplicación. Por lo tanto, la aplicación determina el tamaño real de NetX Duo. Para la mayoría de las aplicaciones, los requisitos de la imagen de instrucción de NetX oscilan entre 5 KBytes y 30 KBytes. Con IPv6 e ICMPv6 habilitados para la configuración de direcciones IPv6 y los protocolos de detección de vecinos, el tamaño de NetX Duo oscila entre 30 Kbytes y 45 Kbytes.

NetX Duo consigue un rendimiento de red superior mediante la disposición en capas de las llamadas a funciones de componentes internos solo cuando es necesario. Además, gran parte del procesamiento de NetX Duo se realiza directamente en línea, lo que da lugar a ventajas de rendimiento destacables con respecto al software de red de estaciones de trabajo que se utilizaba en los diseños insertados en el pasado.

### <a name="zero-copy-implementation"></a>Implementación sin copia

NetX Duo proporciona una implementación de TCP/IP sin copia basada en paquetes. Sin copia significa que los datos del búfer de paquetes de la aplicación nunca se copian en NetX Duo. Esto mejora considerablemente el rendimiento y libera valiosos ciclos de procesador para la aplicación, lo que es importante en las aplicaciones insertadas.

### <a name="udp-fast-pathtrade-technology"></a>Tecnología UDP Fast Path&trade;

Con la <em>tecnología UDP Fast Path</em>, NetX Duo proporciona el procesamiento UDP más rápido posible. En el lado del envío, el procesamiento de UDP (incluida la suma de comprobación opcional de UDP) está incluido en el servicio <em>**nx_udp_socket_send**</em>. No se realiza ninguna llamada de función adicional hasta que el paquete está listo para enviarse mediante la rutina interna de envío IP de NetX Duo. Esta rutina también es plana (es decir, su anidamiento de llamadas de función es mínimo), por lo que el paquete se envía rápidamente al controlador de red de la aplicación. Cuando se recibe el paquete UDP, el procesamiento de recepción de paquetes de NetX Duo coloca el paquete directamente en la cola de recepción del socket UDP correspondiente o se lo pasa al primer subproceso suspendido en espera de un paquete recibido de la cola de recepción del socket UDP. No es necesario ningún otro modificador de contexto de ThreadX.

### <a name="ansi-c-source-cod"></a>Código fuente ANSI C

NetX Duo está escrito completamente en ANSI C y se puede portar de forma inmediata a prácticamente cualquier arquitectura de procesador que tenga un compilador ANSI C y compatibilidad con ThreadX. 

### <a name="not-a-black-box"></a>No es una caja negra

La mayoría de las distribuciones de NetX Duo incluyen el código fuente en C completo. Esto elimina los problemas de "caja negra" que se producen con muchas implementaciones de red comerciales. Al usar NetX Duo, los desarrolladores de aplicaciones pueden ver exactamente lo que hace la pila de red; no hay misterios.

Gracias a disponer del código fuente, también permite modificaciones específicas de la aplicación. Aunque no se recomienda, es útil tener la capacidad de modificar la pila de red si es necesario.

Estas características son especialmente cómodas para los desarrolladores acostumbrados a trabajar con pilas de red de dominio público o de desarrollo interno. Esperan tener el código fuente y la capacidad de modificarlo. NetX Duo es el software de red definitivo para dichos desarrolladores.

### <a name="bsd-compatible-socket-api"></a>API de socket compatible con BSD

En el caso de las aplicaciones heredadas, NetX Duo también proporciona una interfaz de socket compatible con BSD que realiza llamadas a la API de NetX Duo subyacente de alto rendimiento. Esto ayuda a migrar el código de aplicación de red existente a NetX Duo.

## <a name="rfcs-supported-by-netx-duo"></a>RFC compatibles con NetX Duo

La compatibilidad de NetX Duo con los RFC que describen los protocolos de red básicos incluye, pero no se limita a, los siguientes protocolos de red. NetX Duo sigue todas las recomendaciones generales y los requisitos básicos dentro de las restricciones de un sistema operativo en tiempo real con una superficie de memoria pequeña y una ejecución eficiente.

| **RFC**  | **Descripción**                                        |
| -------- | ------------------------------------------------------ |
|RFC 1112 | Extensiones de host para multidifusión IP (IGMPv1)           |
|RFC 1122 | Requisitos para hosts de Internet: capas de comunicación |
|RFC 2236 | Protocolo de administración de grupos de Internet, versión 2          |
|RFC 768  | Protocolo de datagramas de usuario (UDP)                           |
|RFC 791  | Protocolo de Internet (IP)                                 |
|RFC 792  | Protocolo de mensajes de control de Internet (ICMP)               |
|RFC 793  | Protocolo de control de transmisión (TCP)                    |
|RFC 826  | Protocolo de resolución de direcciones Ethernet (ARP) |
|RFC 903  | Protocolo de resolución de direcciones inversa (RARP) |
|RFC 5681 | Control de congestión de TCP                     |

A continuación se muestran los RFC relacionados con IPv6 compatibles con NetX Duo.

|**RFC** |**Descripción**|
-------- | ------------------------------------------ |
|RFC 1981 |Detección de MTU de ruta de acceso para el protocolo de Internet v6 (IPv6)|
|RFC 2460 | Especificación del protocolo de Internet v6 (IPv6)|
|RFC 2464 |Transmisión de paquetes IPv6 sobre redes Ethernet|
|RFC 4291 |Arquitectura de direccionamiento del protocolo de Internet v6 (IPv6)|
|RFC 4443 |Especificación del protocolo de mensajes de control de Internet (ICMPv6) para el protocolo de Internet v6 (IPv6)|
|RFC 4861 |Detección de vecinos para IP v6|
|RFC 4862 |Configuración automática de direcciones sin estado de IPv6|

## <a name="embedded-network-applications"></a>Aplicaciones de red insertadas

Las aplicaciones de red insertadas son aplicaciones que requieren acceso de red y que se ejecutan en microprocesadores ocultos dentro de productos, como teléfonos móviles, equipos de comunicación, motores de automóviles, impresoras láser, dispositivos médicos, etc. Estas aplicaciones casi siempre presentan algunas restricciones de memoria y rendimiento. Otra diferencia de las aplicaciones de red insertadas es que el software y el hardware tienen un propósito dedicado.

El software de red que debe realizar su procesamiento dentro de un período de tiempo exacto se llama software de *red* en *tiempo real* y, cuando se imponen restricciones de tiempo en las aplicaciones de red, se clasifican como aplicaciones en tiempo real. Las aplicaciones de red insertadas casi siempre son en tiempo real debido a su interacción inherente con el mundo externo.

## <a name="netx-duo-benefits"></a>Ventajas de NetX Duo

Las principales ventajas de usar NetX Duo para aplicaciones insertadas son la conectividad a Internet de alta velocidad y unos requisitos de memoria pequeños. NetX Duo también está integrado con el sistema operativo en tiempo real de alto rendimiento y multitarea ThreadX.

### <a name="improved-responsiveness"></a>Capacidad de respuesta mejorada

La pila de protocolos de alto rendimiento de NetX Duo permite a las aplicaciones de red insertadas responder más rápido que nunca. Esto es especialmente importante para las aplicaciones insertadas que tienen un volumen significativo de tráfico de red o requisitos de procesamiento exigentes en un único paquete.

### <a name="software-maintenance"></a>Mantenimiento de software

El uso de NetX Duo permite a los desarrolladores crear particiones con facilidad de los aspectos de red de su aplicación insertada. Esta creación de particiones hace que todo el proceso de desarrollo sea fácil y que mejore significativamente el mantenimiento futuro del software.

### <a name="increased-throughput"></a>Aumento del rendimiento

NetX Duo proporciona las redes de mayor rendimiento disponibles, lo que se consigue mediante una sobrecarga mínima de procesamiento de paquetes. Esto también permite un mayor rendimiento.

### <a name="processor-isolation"></a>Aislamiento del procesador

NetX Duo proporciona una interfaz sólida e independiente del procesador entre la aplicación y el procesador y el hardware de red subyacentes. Esto permite a los desarrolladores concentrarse en los aspectos de red de la aplicación en lugar de dedicar tiempo adicional a solucionar problemas de hardware que afectan directamente a las redes.

### <a name="ease-of-use"></a>Facilidad de uso

NetX Duo se ha diseñado pensando en el desarrollador de aplicaciones. La arquitectura de NetX Duo y la interfaz de llamada de servicio son fáciles de entender. Como resultado, los desarrolladores de NetX Duo pueden usar rápidamente sus características avanzadas.

### <a name="improve-time-to-market"></a>Mejor tiempo de comercialización

Las eficaces características de NetX Duo agilizan el proceso de desarrollo de software. NetX Duo abstrae la mayoría los problemas del procesador y el hardware de red, con lo que se eliminan estas preocupaciones de la mayoría de las áreas específicas de red de la aplicación. Esto, combinado con la facilidad de uso y un conjunto de características avanzadas, da lugar a un tiempo de comercialización más rápido.

### <a name="protecting-the-software-investment"></a>Protección de la inversión en software

NetX Duo está escrito exclusivamente en ANSI C y está totalmente integrado con el sistema operativo en tiempo real ThreadX. Esto significa que las aplicaciones NetX Duo se pueden portar al instante a todos los procesadores compatibles con ThreadX. Mejor aún, una arquitectura de procesador nueva puede ser compatible con ThreadX en cuestión de semanas. Como resultado, el uso de NetX Duo garantiza la ruta de migración de la aplicación y protege la inversión en desarrollo original.

## <a name="ipv6-ready-logo-certification"></a>Certificación del logotipo IPv6 Ready

La certificación "IPv6 Ready" de NetX Duo se obtuvo mediante el paquete de prueba automática del protocolo básico IPv6 (fase 2) disponible en la organización IPv6 Ready. Consulte los siguientes sitios web del proyecto IPv6-Ready para más información sobre la plataforma de pruebas y los casos de prueba: [ **https://www.ipv6ready.org/**](https://www.ipv6ready.org/)

El conjunto de pruebas automáticas del protocolo básico IPv6 (fase 2) valida que una pila IPv6 observa los requisitos establecidos en los siguientes RFC con pruebas exhaustivas:  
Sección 1: RFC 2460  
Sección 2: RFC 4861  
Sección 3: RFC 4862  
Sección 4: RFC 1981  
Sección 5: RFC 4443  

## <a name="ixanvl-test"></a>Prueba IxANVL

NetX Duo se ha probado con IxANVL de IXIA. IxANVL es el estándar del sector para la validación automatizada de redes y protocolos. Puede encontrar más información sobre IxANVL en: [ **https://www.ixiacom.com/products/ixanvl**](https://www.ipv6ready.org/)

En particular, se han probado con IxANVL los siguientes módulos de NetX Duo:

|**Módulo** | **Estándar** |
| --------- | ------------ |
|IP | RFC791 </br> RFC1122 </br> RFC894|
|ICMP | RFC792 </br> RFC1122 </br> RFC1812|
|UDP | RFC768 </br> RFC1122|
|TCP-Básico| RFC793 </br> RFC1122 </br> RFC2460|
|TCP-Avanzado| RFC1981</br>RFC2001</br>RFC2385</br>RFC2463</br>RFC813</br>RFC896|
|TCP-Rendimiento| RFC793</br>RFC1323</br>RFC2018|

## <a name="safety-certifications"></a>Certificaciones de seguridad

### <a name="tv-certification"></a>Certificación TÜV  

NetX Duo está certificado por SG-TÜV Saar para su uso en sistemas críticos para la seguridad, según CEI-61508 y CEI-62304. La certificación confirma que se puede usar NetX Duo en el desarrollo de software relacionado con la seguridad para los niveles de integridad de seguridad más altos de la Comisión electrotécnica internacional (CEI) 61508 e CEI 62304 para la "Seguridad funcional de los sistemas eléctricos, electrónicos y electrónicos programables relacionados con la seguridad". SGS-TÜV Saar, que es una sociedad conjunta entre las empresas alemanas SGS-Group y TÜV Saarland, se ha convertido en la empresa líder independiente acreditada para probar, auditar, comprobar y certificar software insertado para sistemas relacionados con la seguridad en todo el mundo. El estándar de seguridad industrial CEI 61508 y todos los estándares que se derivan de él, incluido CEI 62304, se usan para garantizar la seguridad funcional de los dispositivos médicos eléctricos, electrónicos y electrónicos programables relacionados con la seguridad, los sistemas de control de procesos, la maquinaria industrial y los sistemas de control de ferrocarriles. 

SGS-TÜV Saar ha certificado NetX Duo para su uso en sistemas de automóviles críticos para la seguridad, según el estándar ISO 26262. Además, NetX Duo está certificado para el nivel D de integridad de la seguridad del automóvil (ASIL), que representa el nivel más alto de la certificación ISO 26262. 

Además, SGS-TÜV Saar ha certificado NetX Duo para su uso en aplicaciones ferroviarias críticas para la seguridad, cumpliendo el estándar EN 50128 hasta SW-SIL 4.

![Diagrama del logotipo de certificación SGS-TÜV Saar.](./media/user-guide/sgs-tuv-saar-logo.png)

CEI 61508 hasta SIL 4  
CEI 62304 hasta la clase C de seguridad de SW ISO 26262 ASIL D EN 50128 SW-SIL 4

> [!IMPORTANT]
> *Póngase en contacto con Microsoft para más información sobre qué versiones de NetX Duo están certificadas por TÜV o para la disponibilidad de informes de las pruebas, certificados y documentación asociada.*

### <a name="ul-certification"></a>Certificación UL

NetX Duo ha sido certificado por UL por su conformidad con los estándares de seguridad para software de componentes programables UL 60730-1 anexo H, CSA E60730-1 anexo H, CEI 60730-1 anexo H, UL 60335-1 anexo R, CEI 60335-1 anexo R y UL 1998. Junto con CEI/UL 60730-1, que tiene requisitos para "Controles que usan software" en el anexo H, el estándar CEI 60335-1 describe los requisitos para "circuitos electrónicos programables" en el anexo R. CEI 60730 en su anexo H y CEI 60335-1 en su anexo R abordan la seguridad del hardware y el software MCU que se usa en dispositivos como lavadoras, lavavajillas, secadoras, frigoríficos, congeladores y hornos.

![Diagrama del logotipo de certificación UL.](./media/user-guide/c-ru-us-logo.png)

*UL/CEI 60730, UL/CEI 60335, UL 1998*

> [!IMPORTANT]  
> *Póngase en contacto con Microsoft para más información sobre qué versiones de NetX Duo están certificadas por UL o para la disponibilidad de informes de las pruebas, certificados y documentación asociada.*