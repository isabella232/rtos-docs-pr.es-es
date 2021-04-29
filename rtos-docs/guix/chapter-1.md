---
title: 'Capítulo 1: Introducción a GUIX'
description: GUIX es una implementación en tiempo real de alto rendimiento de una GUI diseñada exclusivamente para aplicaciones insertadas basadas en Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b90da988a03d59b1bca3f5584164d641bef96454
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815522"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a>Capítulo 1: Introducción a Azure RTOS GUIX

Azure RTOS GUIX (GUIX) es una implementación en tiempo real de alto rendimiento de un marco de interfaz gráfica diseñada exclusivamente para aplicaciones insertadas basadas en ThreadX. Este capítulo contiene una introducción a GUIX y una descripción de sus aplicaciones y ventajas.

## <a name="guix-feature-overview"></a>Información general de las características de GUIX

A diferencia de muchas otras implementaciones de GUI, GUIX está diseñada para ser versátil, ya que permite escalar fácilmente desde pequeñas aplicaciones basadas en microcontroladores a otras que usan los potentes procesadores RISC y DSP. Significa un marcado contraste con las implementaciones de dominio público u otras implementaciones comerciales diseñadas originalmente para entornos de estación de trabajo, pero que después se han aprovechado para diseños insertados. A continuación, se ofrece información general sobre las características de GUIX:

- Fácil de usar con la herramienta de diseño basada en host GUIX Studio

- Entorno de tiempo de ejecución de GUIX de Win32 para un prototipo completo hospedado

- Compatible con la mayoría de los procesadores que ThreadX admite

- Escrita exclusivamente en ANSI C

- Endian neutro

- La GUI insertada más pequeña y rápida

- Tiempo de ejecución configurable, número de objetos, tamaño de la pantalla, etc.

- Interfaz de controlador de pantalla fácil de escribir

- Compatibilidad con color (hasta 32 bpp de profundidad de color), monocromo y escala de grises

- Compatibilidad multilingüe a través de la codificación de cadenas UTF8 y los recursos de cadena

- Fuentes gratuitas predeterminadas y facilidad para la adición de otras nuevas

- Compatibilidad con varios lienzos de dibujo, de varios tamaños

- Compatibilidad con varias pantallas de diferentes tamaños y profundidades de color

- Compatibilidad con la transición de pantalla (fundido de entrada, fundido de salida, pasar el dedo, etc.)

- Compatibilidad con pantalla táctil, gesto y teclado virtual

- Compresión de mapa de bits

- Compatibilidad con la combinación alfa

- Compatibilidad con la interpolación

- Compatibilidad con el suavizado de contorno

- Cambio de aspecto visual y temas

- Combinación de lienzos

- Administración completa de ventanas

  - Relación de elementos primarios y secundarios

  - Creación, eliminación, cambio de tamaño y movimiento dinámicos
  - Control de eventos y dibujo independientes 
  - Orden Z
  - Recorte y vistas

- Amplio conjunto de widgets

  - Varios tipos de botón, controles deslizantes y diales

  - Lista desplegable
  
  - Prompt

  - Vista de texto de varias líneas
  
  - Entrada de texto de una y varias líneas
  
  - Ruedas del mouse numéricas y textuales
  
  - Ventanas y barras de desplazamiento
  
  - Barra de progreso radial
  
  - Sprite

### <a name="ansi-c-source-code"></a>Código fuente ANSI C

GUIX está escrita completamente en ANSI C y se puede portar de forma inmediata a prácticamente cualquier arquitectura de procesador que tenga un compilador ANSI C y compatibilidad con ThreadX. Aunque está escrita en ANSI C, GUIX utiliza un modelo orientado a objetos y la herencia.

### <a name="not-a-black-box"></a>No es una caja negra

La mayoría de las distribuciones de GUIX incluyen el código fuente C completo. Esto elimina los problemas de "caja negra" que se producen con muchas implementaciones de GUI comerciales. Al usar GUIX, los desarrolladores de aplicaciones pueden ver exactamente lo que está haciendo la GUI; no hay misterio.

Gracias a disponer del código fuente, también permite modificaciones específicas de la aplicación. Aunque no se recomienda, es ciertamente útil tener la capacidad de modificar la GUI si es necesario. Estas características son especialmente reconfortantes para los desarrolladores acostumbrados a trabajar con productos de dominio público o interno. Esperan tener el código fuente y la capacidad de modificarlo. GUIX es el software de GUI definitivo para dichos desarrolladores.

## <a name="embedded-gui-applications"></a>Aplicaciones insertadas de GUI

Las aplicaciones insertadas de GUI son aplicaciones que requieren una interfaz de usuario y que se ejecutan en microprocesadores ocultos dentro de productos, como teléfonos móviles, equipos de comunicación, motores de automóviles, impresoras láser, dispositivos médicos, etc. Estas aplicaciones casi siempre presentan algunas restricciones de memoria y rendimiento. Otra diferencia de la GUI insertada es que el software y el hardware tienen un propósito dedicado.

### <a name="real-time-gui-software"></a>Software de GUI en tiempo real

Básicamente, el software de GUI que debe realizar su procesamiento dentro de un período de tiempo exacto se denomina software de *GUI en tiempo real* y, cuando se imponen restricciones de tiempo en las aplicaciones de GUI, se clasifican como aplicaciones en tiempo real. Las aplicaciones insertadas de GUI casi siempre son en tiempo real debido a su interacción inherente con el mundo externo.

## <a name="guix-benefits"></a>Ventajas de GUIX

Las principales ventajas de usar GUIX para las aplicaciones insertadas son el alto rendimiento, las características enriquecidas y muy pocos requisitos de memoria. GUIX también está totalmente integrada con el sistema operativo en tiempo real de alto rendimiento y multitarea Azure RTOS ThreadX.

### <a name="improved-responsiveness"></a>Mayor capacidad de respuesta

El producto GUIX de alto rendimiento permite a las aplicaciones responder más rápido que nunca. Esto es especialmente importante para las aplicaciones insertadas con un volumen significativo de información visual o con requisitos estrictos de tiempo para mostrar dicha información.

### <a name="software-maintenance"></a>Mantenimiento de software

El uso de GUIX permite a los desarrolladores crear con facilidad particiones de los aspectos de la GUI de su aplicación insertada. Esta creación de particiones hace que todo el proceso de desarrollo sea fácil y que mejore significativamente el mantenimiento futuro del software.

### <a name="increased-throughput"></a>Aumento del rendimiento

GUIX proporciona la GUI de mayor rendimiento disponible, que se transfiere directamente a la aplicación insertada. Las aplicaciones de GUIX pueden procesar la información de la interfaz de usuario más rápido que las aplicaciones que no son de GUIX.

### <a name="processor-isolation"></a>Aislamiento del procesador

GUIX proporciona una interfaz sólida e independiente del procesador entre la aplicación y el procesador subyacente y el hardware de visualización. Esto permite a los desarrolladores concentrarse en los aspectos de alto nivel de la interfaz de usuario en lugar de dedicar tiempo adicional a solucionar problemas del hardware de visualización.

### <a name="ease-of-use"></a>Facilidad de uso

GUIX se ha diseñado pensando en el desarrollador de aplicaciones. La arquitectura de GUIX y la interfaz de llamada de servicio son fáciles de entender. Como resultado, los desarrolladores de GUIX pueden usar rápidamente sus características avanzadas.

### <a name="improve-time-to-market"></a>Mejor tiempo de comercialización

Las eficaces características de GUIX agilizan el proceso de desarrollo de software. GUIX abstrae la mayoría los problemas del procesador y hardware de visualización, con lo que se eliminan estas preocupaciones de la mayoría de las implementaciones de interfaz de usuario de aplicación. Esta característica, combinada con el conjunto de características avanzadas y de facilidad de uso, da lugar a un tiempo de comercialización más rápido.

### <a name="protecting-the-software-investment"></a>Protección de la inversión en software

GUIX se ha escrito exclusivamente en ANSI C y está totalmente integrada con el sistema operativo en tiempo real Azure RTOS ThreadX. Esto significa que las aplicaciones de GUIX se pueden portar al instante a todos los procesadores compatibles con ThreadX. Mejor aún, una arquitectura de procesador completamente nueva puede ser compatible con ThreadX en cuestión de semanas. Como resultado, el uso de GUIX garantiza la ruta de migración de la aplicación y protege la inversión de desarrollo original.
