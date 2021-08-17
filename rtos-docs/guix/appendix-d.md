---
title: 'Apéndice D: atributos de pincel, lienzo y degradado de GUIX'
description: Obtenga información sobre los atributos de pincel, lienzo y degradado de GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9fbc98f1094cab6be4bc0826fef7c0feb77b50b066b22342cd52404bd85ff98e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784638"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a>Apéndice D: atributos de pincel, lienzo y degradado de GUIX

__**Estilos de pincel:**__

**GX_BRUSH_OUTLINE**
- Valor: 0x0000
- Descripción: este estilo de pincel se aplica a funciones de dibujo de formas, como gx_canvas_rectangle_draw o gx_canvas_polygon_draw. Este estilo indica que la forma debe tener contorno, además de poder tener relleno. Si se establece el estilo GX_BRUSH_OUTLINE, y el GX_BRSUH_SOLID_FILL está desactivado, la forma solo tendrá contorno.

**GX_BRUSH_SOLID_FILL**
- Valor: 0x0001
- Descripción: este estilo de pincel se aplica a funciones de dibujo de formas e indica que la forma solicitada se debe rellenar con un color sólido usando el color de relleno actual del pincel.

**GX_BRUSH_PIXELMAP_FILL**
- Valor: 0x0002
- Descripción: este estilo de pincel se aplica a funciones de dibujo de formas e indica que la forma solicitada se debe rellenar con una trama usando el mapa de píxeles actual del pincel.

**GX_BRUSH_ALIAS**
- Valor: 0x0004
- Descripción: este estilo de pincel se aplica a todo el dibujo de líneas y a todos los contornos de formas. Si se establece esta marca, las líneas y los contornos se dibujan con los algoritmos de dibujo suavizado más precisos, pero que también consumen más tiempo. Esta marca de estilo solo se usa para profundidades de color de 16 bpp o superiores.

**GX_BRUSH_UNDERLINE**
- Valor: 0x0008
- Descripción: esta marca se aplica al dibujo de texto e indica que el siguiente texto que se dibuje debe estar subrayado.

**GX_BRUSH_ROUND**
- Valor: 0x0010
- Descripción: esta marca se aplica al dibujo de líneas e indica que los extremos de línea se dibujan con una forma redonda o circular, en lugar de la forma cuadrada predeterminada.

__**Marcas de lienzo:**__

**GX_CANVAS_SIMPLE**
- Valor: 0x01
- Descripción: lienzo de memoria que se usa para dibujar fuera de la pantalla.

**GX_CANVAS_MANAGED**
- Valor: 0x02
- Descripción: lienzo que se vacía automáticamente en la pantalla activa, ya sea como parte del proceso de creación de la composición o como parte de la operación de alternancia de búfer para arquitecturas de un solo lienzo.

**GX_CANVAS_VISIBLE**
- Valor: 0x04
- Descripción: esta marca se puede usar para activar y desactivar un lienzo, sin perder el contenido del dibujo que contiene.

**GX_CANVAS_MODIFIED**
- Valor: 0x08
- Descripción: reservado para su uso futuro.

**GX_CANVAS_COMPOSITE**
- Valor: 0x20
- Descripción: la aplicación usa esta marca al configurar un sistema que compondrá varios lienzos administrados en el compuesto. La composición se conduce al búfer de cuadros del hardware.

__**Tipos de degradado:**__

**GX_GRADIENT_TYPE_VERTICAL**
- Valor: 0x01
- Descripción: crea un degradado de mapa alfa vertical.

**GX_GRADIENT_TYPE_ALPHA**
- Valor: 0x02
- Descripción: crea un degradado de mapa alfa. En estos momentos, este es el único estilo de degradado admitido.

**GX_GRADIENT_TYPE_MIRROR**
- Valor: 0x04
- Descripción: esta marca indica que el degradado debe alcanzar su punto máximo en el centro del intervalo de ancho o alto y volver al valor inicial cuando llegue al borde derecho o inferior. Sin esta marca de estilo, el degradado será lineal de arriba abajo o de izquierda a derecha, en función de la marca GX_GRADIENT_TYPE_VERTICAL.