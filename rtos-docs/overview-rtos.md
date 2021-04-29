---
title: ¿Qué es Microsoft Azure RTOS?
description: Azure RTOS es un sistema operativo en tiempo real (RTOS) para dispositivos IoT y perimetrales con tecnología de microcontroladores (MCU).
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3b1c63135f6069652d7f66fc976b9d770a4dfeb2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815118"
---
# <a name="what-is-microsoft-azure-rtos"></a>¿Qué es Microsoft Azure RTOS?

Azure RTOS es un sistema operativo en tiempo real (RTOS) para dispositivos IoT y perimetrales con tecnología de microcontroladores (MCU). Azure RTOS está diseñado para admitir la mayoría de los dispositivos altamente restringidos (con batería y con menos de 64 kB de memoria flash).
 
Azure RTOS está certificado previamente para una amplia variedad de estándares de seguridad. Entre ellas se incluyen las certificaciones IEC 61508 SIL 4, IEC 62304 clase C e ISO 26262 ASIL D. Azure RTOS ThreadX también tiene la certificación DO-178.

Azure RTOS proporciona un entorno certificado de seguridad de criterios comunes de EAL4 +, incluida la seguridad de la capa de IP completa a través de IPsec y la seguridad de la capa de socket a través de TLS y DTLS. Nuestra biblioteca de criptografía de software ha logrado la certificación FIPS 140-2. También aprovechamos las funcionalidades criptográficas de hardware, la protección de memoria a través de módulos de ThreadX y la compatibilidad con las características de seguridad de TrustZone ARMv8-M de ARM.

## <a name="components-of-azure-rtos"></a>Componentes de Azure RTOS

La plataforma Azure RTOS es la colección de soluciones en tiempo de ejecución, entre las que se incluyen Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo y Azure RTOS USBX.

### <a name="azure-rtos-threadx"></a>Azure RTO ThreadX

Azure RTOS ThreadX es un sistema operativo en tiempo real (RTOS) avanzado, diseñado específicamente para aplicaciones profundamente insertadas. Entre las múltiples ventajas que ofrece Azure RTOS ThreadX se encuentran las funciones avanzadas de programación, el envío de mensajes, la administración de interrupciones y los servicios de mensajería. Azure RTOS ThreadX tiene muchas características avanzadas, entre las que se incluyen la arquitectura picokernel, la programación de umbral de prioridad, el encadenamiento de eventos y un conjunto completo de servicios del sistema.

### <a name="azure-rtos-filex"></a>Azure RTO FileX

Azure RTOS FileX es un sistema de archivos compatible con FAT de alto rendimiento. Está totalmente integrado con Azure RTOS ThreadX y está disponible para todos los procesadores compatibles. Al igual que Azure RTOS ThreadX, Azure RTOS FileX está diseñado para ocupar poca superficie de memoria y proporcionar un alto rendimiento, lo que lo convierte en una opción ideal para las actuales aplicaciones profundamente insertadas, que requieren operaciones de archivos. Azure RTOS FileX admite la mayoría de los soportes físicos, como el disco RAM, Azure RTOS USBX, tarjeta SD y memorias Flash NAND/NOR a través de Azure RTO LevelX.

### <a name="azure-rtos-guix"></a>Azure RTO GUIX

Azure RTOS GUIX es un paquete de interfaz gráfica de usuario de calidad profesional creado para satisfacer las necesidades de los desarrolladores de sistemas insertados. A diferencia de las alternativas, Azure RTOS GUIX es pequeño, rápido y fácil de migrar a prácticamente cualquier configuración de hardware capaz de admitir la salida gráfica. Azure RTOS GUIX también ofrece un atractivo visual excepcional y una API intuitiva y potente para el desarrollo de interfaces de usuario a nivel de aplicación.

### <a name="azure-rtos-netx"></a>Azure RTO NetX

Azure RTOS NetX es una implementación de alto rendimiento de estándares de protocolos TCP/IP. Está totalmente integrado con Azure RTOS ThreadX y está disponible para todos los procesadores compatibles. Azure RTOS NetX tiene una arquitectura Piconet exclusiva. Combinado con una API de copia de cero, lo convierte en un ajuste perfecto para las aplicaciones profundamente incrustadas de hoy en día que requieren conectividad de red.

### <a name="azure-rtos-netx-duo"></a>Azure RTO NetX Duo

Azure RTOS NetX Duo es una pila de red TCP/IP avanzada y de nivel industrial diseñada específicamente para aplicaciones de IoT y en tiempo real insertadas. Azure RTOS NetX Duo es una pila de red IPv4 e IPv6 dual, mientras que NetX es la pila de red IPv4 original, esencialmente un subconjunto de Azure RTOS NetX Duo.

### <a name="azure-rtos-usbx"></a>Azure RTO USBX

Azure RTOS USBX es un host USB de alto rendimiento, un dispositivo y una pila insertada "on-the-go" (OTG). Está totalmente integrado con ThreadX y está disponible para todos los procesadores compatibles con Azure RTOS ThreadX. Al igual que Azure RTOS ThreadX, Azure RTOS USBX está diseñado para ocupar poca superficie de memoria y proporcionar un alto rendimiento, lo que lo convierte en una opción ideal para las aplicaciones profundamente insertadas, que requieren una interfaz con dispositivos USB.

### <a name="windows-tools"></a>Herramientas de Windows

Azure RTOS GUIX Studio proporciona un entorno de diseño de aplicaciones GUI completo, lo que facilita la creación y el mantenimiento de todos los elementos gráficos de la GUI de la aplicación. Azure RTOS GUIX Studio genera automáticamente un código de C compatible con la biblioteca de Azure RTOS GUIX, listo para compilarse y ejecutarse en el destino.

Azure RTOS TraceX es la herramienta de análisis basada en host que proporciona a los desarrolladores una vista gráfica de los eventos del sistema en tiempo real y les permite visualizar y comprender mejor el comportamiento de sus sistemas en tiempo real.

## <a name="in-the-context-of-azure-iot"></a>En el contexto de Azure IoT

Además de conectarse directamente a Azure IoT o conectarse indirectamente a través de Azure IoT Edge, Azure RTOS también está disponible en dispositivos Azure Sphere. La combinación de Azure RTOS y Azure Sphere reúne el mejor procesamiento en tiempo real y la mejor seguridad en un solo dispositivo.
