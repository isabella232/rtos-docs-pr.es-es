---
title: 'Capítulo 1: Introducción a Azure RTOS NetX'
description: Este capítulo contiene una introducción a Azure RTOS NetX y una descripción de sus aplicaciones y ventajas.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48be6a7ecddc53b36b3cc1a9ecfb50a11e285881
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815314"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx"></a>Capítulo 1: Introducción a Azure RTOS NetX

Azure RTOS NetX es una implementación en tiempo real de alto rendimiento de los estándares de TCP/IP diseñada exclusivamente para aplicaciones insertadas basadas en ThreadX. Este capítulo contiene una introducción a NetX y una descripción de sus aplicaciones y ventajas.

## <a name="netx-unique-features"></a>Características únicas de NetX

A diferencia de otras implementaciones de TCP/IP, NetX está diseñado para ser versátil, ya que permite escalar fácilmente desde pequeñas aplicaciones basadas en microcontroladores a otras que usan los potentes procesadores RISC y DSP. Significa un marcado contraste con las implementaciones de dominio público u otras implementaciones comerciales diseñadas originalmente para entornos de estación de trabajo, pero que después se han aprovechado para diseños insertados.

### <a name="piconettrade-architecture"></a>Arquitectura Piconet&trade;

Subyacente a la escalabilidad y el rendimiento superiores de NetX está *Piconet*, una arquitectura de software especialmente diseñada para sistemas insertados. La arquitectura Piconet maximiza la escalabilidad mediante la implementación de los servicios de NetX como una biblioteca de C. De esta manera, solo se incorporan a la imagen final en tiempo de ejecución los servicios que realmente usa la aplicación. Por lo tanto, la aplicación determina completamente el tamaño real de NetX. Para la mayoría de las aplicaciones, los requisitos de tamaño de la imagen de NetX oscilan entre 5 KBytes y 30 KBytes.

NetX consigue un rendimiento de red superior mediante la disposición en capas de las llamadas a funciones de componentes internos solo cuando es absolutamente necesario. Además, gran parte del procesamiento de NetX se realiza directamente en línea, lo que da lugar a ventajas de rendimiento destacables con respecto al software de red de estaciones de trabajo que solía usarse en los diseños insertados en el pasado.</th>

### <a name="zero-copy-implementation"></a>Implementación sin copia

NetX proporciona una implementación de TCP/IP *sin copia* basada en paquetes. Sin copia significa que los datos del búfer de paquetes de la aplicación nunca se copian en NetX. Esto mejora considerablemente el rendimiento y libera valiosos ciclos de procesador para la aplicación, lo que es muy importante en las aplicaciones insertadas.

### <a name="udp-fast-pathtrade-technology"></a>Tecnología UDP Fast Path&trade;

Con la *tecnología UDP Fast Path*, NetX proporciona el procesamiento UDP más rápido posible. En el lado del envío, el procesamiento de UDP (incluida la suma de comprobación opcional de UDP) está completamente incluido en el servicio ***nx_udp_socket_send***. No se realiza ninguna llamada de función adicional hasta que el paquete está listo para enviarse mediante la rutina interna de envío IP de NetX. Esta rutina también es plana (es decir, su anidamiento de llamadas de función es mínimo), por lo que el paquete se envía rápidamente al controlador de red de la aplicación. Cuando se recibe el paquete UDP, el procesamiento de recepción de paquetes de NetX coloca el paquete directamente en la cola de recepción del socket UDP correspondiente o se lo pasa al primer subproceso suspendido en espera de un paquete recibido de la cola de recepción del socket UDP. No es necesario ningún otro modificador de contexto de ThreadX.

### <a name="ansi-c-source-code"></a>Código fuente ANSI C

NetX está escrito completamente en ANSI C y se puede portar de forma inmediata a prácticamente cualquier arquitectura de procesador que tenga un compilador ANSI C y compatibilidad con ThreadX.

### <a name="not-a-black-box"></a>No es una caja negra

La mayoría de las distribuciones de NetX incluyen el código fuente en C completo. Esto elimina los problemas de "caja negra" que se producen con muchas implementaciones de red comerciales. Al usar NetX, los desarrolladores de aplicaciones pueden ver exactamente lo que hace la pila de red; no hay misterios.
  
Gracias a disponer del código fuente, también permite modificaciones específicas de la aplicación. Aunque no se recomienda, es ciertamente útil tener la capacidad de modificar la pila de red si es necesario.  

Estas características son especialmente cómodas para los desarrolladores acostumbrados a trabajar con pilas de red de dominio público o de desarrollo interno. Esperan tener el código fuente y la capacidad de modificarlo. NetX es el software de red definitivo para dichos desarrolladores.

### <a name="bsd-compatible-socket-api"></a>API de socket compatible con BSD

En el caso de las aplicaciones heredadas, NetX proporciona una interfaz de socket compatible con BSD que realiza llamadas a la API de NetX subyacente de alto rendimiento. Esto ayuda a migrar el código de aplicación de red existente a NetX.

## <a name="rfcs-supported-by-netx"></a>RFC compatibles con NetX

La compatibilidad de NetX con los RFC que describen los protocolos de red básicos incluye, pero no se limita a, los siguientes protocolos de red. NetX sigue todas las recomendaciones generales y los requisitos básicos dentro de las restricciones de un sistema operativo en tiempo real con una superficie de memoria pequeña y una ejecución eficiente.

| RFC      | Descripción                                            |
|----------|--------------------------------------------------------|
| RFC 1112 | Extensiones de host para multidifusión IP (IGMPv1)           |
| RFC 1122 | Requisitos para hosts de Internet: capas de comunicación |
| RFC 2236 | Protocolo de administración de grupos de Internet, versión 2          |
| RFC 768  | Protocolo de datagramas de usuario (UDP)                           |
| RFC 791  | Protocolo de Internet (IP)                                 |
| RFC 792  | Protocolo de mensajes de control de Internet (ICMP)               |
| RFC 793  | Protocolo de control de transmisión (TCP)                    |
| RFC 826  | Protocolo de resolución de direcciones Ethernet (ARP)             |
| RFC 903  | Protocolo de resolución de direcciones inversa (RARP)             |
|          |                                                        |

## <a name="embedded-network-applications"></a>Aplicaciones de red insertadas

Las aplicaciones de red insertadas son aplicaciones que requieren acceso de red y que se ejecutan en microprocesadores ocultos dentro de productos, como teléfonos móviles, equipos de comunicación, motores de automóviles, impresoras láser, dispositivos médicos, etc. Estas aplicaciones casi siempre presentan algunas restricciones de memoria y rendimiento. Otra diferencia de las aplicaciones de red insertadas es que el software y el hardware tienen un propósito dedicado.

### <a name="real-time-network-software"></a>Software de red en tiempo real  

Básicamente, el software de red que debe realizar su procesamiento dentro de un período de tiempo exacto se llama software de *red* en *tiempo real* y, cuando se imponen restricciones de tiempo en las aplicaciones de red, se clasifican como aplicaciones en tiempo real. Las aplicaciones de red insertadas casi siempre son en tiempo real debido a su interacción inherente con el mundo externo.

## <a name="netx-benefits"></a>Ventajas de NetX

Las principales ventajas de usar NetX para aplicaciones insertadas son la conectividad a Internet de alta velocidad y unos requisitos de memoria muy pequeños. NetX también está totalmente integrado con el sistema operativo en tiempo real de alto rendimiento y multitarea ThreadX.

### <a name="improved-responsiveness"></a>Capacidad de respuesta mejorada  

La pila de protocolos de alto rendimiento de NetX permite a las aplicaciones de red insertadas responder más rápido que nunca. Esto es especialmente importante para las aplicaciones insertadas que tienen un volumen significativo de tráfico de red o requisitos de procesamiento exigentes en un único paquete.

### <a name="software-maintenance"></a>Mantenimiento de software

El uso de NetX permite a los desarrolladores crear particiones con facilidad de los aspectos de red de su aplicación insertada. Esta creación de particiones hace que todo el proceso de desarrollo sea fácil y que mejore significativamente el mantenimiento futuro del software.

### <a name="increased-throughput"></a>Aumento del rendimiento

NetX proporciona las redes de mayor rendimiento disponibles, lo que se consigue mediante una sobrecarga mínima de procesamiento de paquetes. Esto también permite un mayor rendimiento.

### <a name="processor-isolation"></a>Aislamiento del procesador

NetX proporciona una interfaz sólida e independiente del procesador entre la aplicación y el procesador y el hardware de red subyacentes. Esto permite a los desarrolladores concentrarse en los aspectos de red de la aplicación en lugar de dedicar tiempo adicional a solucionar problemas de hardware que afectan directamente a las redes.

### <a name="ease-of-use"></a>Facilidad de uso

NetX se ha diseñado pensando en el desarrollador de aplicaciones. La arquitectura de NetX y la interfaz de llamada de servicio son fáciles de entender. Como resultado, los desarrolladores de NetX pueden usar rápidamente sus características avanzadas.

### <a name="improve-time-to-market"></a>Mejor tiempo de comercialización

Las eficaces características de NetX agilizan el proceso de desarrollo de software. NetX abstrae la mayoría los problemas del procesador y el hardware de red, con lo que se eliminan estas preocupaciones de la mayoría de las áreas específicas de red de la aplicación. Esto, combinado con la facilidad de uso y un conjunto de características avanzadas, da lugar a un tiempo de comercialización más rápido.

### <a name="protecting-the-software-investment"></a>Protección de la inversión en software

NetX está escrito exclusivamente en ANSI C y está totalmente integrado con el sistema operativo en tiempo real ThreadX. Esto significa que las aplicaciones NetX se pueden portar al instante a todos los procesadores compatibles con ThreadX. Mejor aún, una arquitectura de procesador completamente nueva puede ser compatible con ThreadX en cuestión de semanas. Como resultado, el uso de NetX garantiza la ruta de migración de la aplicación y protege la inversión en desarrollo original.
