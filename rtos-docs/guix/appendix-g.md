---
title: 'Apéndice G: estructura de fuentes de GUIX'
description: Obtenga información sobre la estructura de fuentes de GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5f0232e6c21851014b85cfe7b07795062fd1e8d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815565"
---
# <a name="appendix-g---guix-font-structure"></a>Apéndice G: estructura de fuentes de GUIX

Las fuentes de GUIX se suelen producir mediante la aplicación GUIX Studio, mientras que los glifos de fuente se representan mediante el controlador de pantalla de GUIX. El software de aplicación solo necesita especificar la fuente y los colores que debe usar cada widget de presentación de texto. Las estructuras de datos de fuente de GUIX se documentan aquí con ánimo de exhaustividad y con el fin de que los desarrolladores puedan crear sus propios métodos para generar otras fuentes o convertirlas al formato de fuente de GUIX.

Cada fuente de GUIX comienza con una estructura GX_FONT. La estructura GX_FONT define parámetros de fuente globales, como el carácter incluido en la fuente y el alto de línea de esta. La estructura GX_FONT apunta a una matriz de estructuras GX_GLYPH. Cada estructura GX_GLYPH define el ancho, el alto y el desplazamiento de línea base de un glifo de carácter específico. La estructura GX_GLYPH también apunta a los datos de mapa de bits del glifo (que pueden ser NULL en el caso de caracteres de espacio en blanco).

La estructura GX_FONT, incluida en gx_api.h, se declara de la siguiente manera:

```c
typedef struct GX_FONT_STRUCT
{
    GX_UBYTE                     gx_font_format
    GX_UBYTE                     gx_font_prespace
    GX_UBYTE                     gx_font_postspace
    GX_UBYTE                     gx_font_line_height 
    GX_UBYTE                     gx_font_baseline
    USHORT                       gx_font_first_glyph
    USHORT                       gx_font_last_glyph 
    GX_CONST GX_GLYPH           *gx_font_glyphs
    const struct GX_FONT_STRUCT *gx_font_next_page
} GX_FONT;
```

El campo gx_font_format define los bits por píxel de la fuente y otras marcas, tal y como se define en el archivo de encabezado gx_api.h.

El campo gx_font_prespace define el espacio en píxeles que se va a omitir encima de cada línea de texto en una representación de texto de varias líneas.

El campo gx_font_postspace define el espacio en píxeles que se va a omitir debajo de cada línea de texto en una representación de texto de varias líneas.

El campo gx_font_line_height define la altura del glifo más alto de la fuente.

El campo gx_font_baseline define la distancia, en píxeles, desde la fila superior de píxeles del glifo hasta la línea base de la fuente.

El campo gx_font_first_glyph define la primera codificación de caracteres Unicode incluida en esta página de fuentes.

El campo gx_font_last_glyph define la última codificación de caracteres Unicode incluida en esta página de fuentes.

El puntero gx_font_glyphs apunta a una matriz de estructuras GX_GLYPH. El tamaño de esta matriz debe coincidir con el número de caracteres que contiene esta página de fuentes, es decir, (gx_font_last_glyph – gx_font_first_glyph) + 1.

El miembro gx_font_next_page se usa para fuentes de varias páginas. Las fuentes de varias páginas se usan con juegos de caracteres extendidos y para optimizar el tamaño de las matrices de estructuras GX_GLYPH. Si todos los caracteres de la fuente están incluidos dentro de una misma página, o bien si se trata de la última página de la fuente en cuestión, el miembro gx_font_next_page se establece en GX_NULL.

Como ya se ha indicado, la estructura GX_FONT anterior contiene un puntero a una matriz de estructuras GX_GLYPHS. Debe haber una estructura GX_GLYPH por cada carácter de la página de fuentes. La estructura GX_GLYPH se define de la siguiente manera:

```c
typedef struct GX_GLYPH_STRUCT
{
    GX_CONST GX_UBYTE *gx_glyph_map;
    GX_BYTE            gx_glyph_ascent;
    GX_BYTE            gx_glyph_descent;
    GX_BYTE            gx_glyph_advance;
    GX_BYTE            gx_glyph_leading;
    GX_UBYTE           gx_glyph_width;
    GX_UBYTE           gx_glyph_height;
} GX_GLYPH;
```

El puntero gx_glyph_map apunta al mapa de bits del glifo. Este puntero puede ser GX_NULL en el caso de caracteres de espacio en blanco. Los datos de mapa de bits se codifican como valores alfa de 1, 2, 4 u 8 bpp. En el caso de los datos de 1 bit, un valor de 1 indica que el píxel se debe escribir en el color de primer plano, mientras que un valor de 0 indica que el píxel es transparente. En el caso de los datos de 8 bits, los valores van de 0 (totalmente transparente) a 255 (totalmente opaco). Todos los valores intermedios representan un valor de mezcla para fuentes suavizadas. Los datos de mapa de bits de glifo siempre se rellenan hasta la alineación completa de bytes en el caso de los formatos que usan valores de datos inferiores a 8 bpp.

Los valores gx_glyph_ascent y gx_glyph_descent colocan el glifo verticalmente con respecto a la línea base de la fuente.

Los valores gx_glyph_width y gx_glyph_height especifican el tamaño de los datos de mapa de bits del glifo.

El valor gx_glyph_advance especifica el ancho en píxeles que se debe adelantar la posición de dibujo después de dibujar el glifo (puede no coincidir con el ancho del glifo).

El valor gx_glyph_leading especifica los píxeles que se debe avanzar en la dirección x antes de representar el glifo.