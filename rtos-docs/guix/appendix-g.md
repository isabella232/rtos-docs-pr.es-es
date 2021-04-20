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
# <a name="appendix-g---guix-font-structure"></a><span data-ttu-id="a3d26-103">Apéndice G: estructura de fuentes de GUIX</span><span class="sxs-lookup"><span data-stu-id="a3d26-103">Appendix G - GUIX Font Structure</span></span>

<span data-ttu-id="a3d26-104">Las fuentes de GUIX se suelen producir mediante la aplicación GUIX Studio, mientras que los glifos de fuente se representan mediante el controlador de pantalla de GUIX.</span><span class="sxs-lookup"><span data-stu-id="a3d26-104">GUIX fonts are normally produced by the GUIX Studio application, and font glyphs are rendered by the GUIX display driver.</span></span> <span data-ttu-id="a3d26-105">El software de aplicación solo necesita especificar la fuente y los colores que debe usar cada widget de presentación de texto.</span><span class="sxs-lookup"><span data-stu-id="a3d26-105">The application software need only specify the font and colors that each text display widget should use.</span></span> <span data-ttu-id="a3d26-106">Las estructuras de datos de fuente de GUIX se documentan aquí con ánimo de exhaustividad y con el fin de que los desarrolladores puedan crear sus propios métodos para generar otras fuentes o convertirlas al formato de fuente de GUIX.</span><span class="sxs-lookup"><span data-stu-id="a3d26-106">The GUIX font data structures are documented here for completeness, and to enable developers to create their own methods for generating or converting other fonts into the GUIX font format.</span></span>

<span data-ttu-id="a3d26-107">Cada fuente de GUIX comienza con una estructura GX_FONT.</span><span class="sxs-lookup"><span data-stu-id="a3d26-107">Each GUIX font starts with a GX_FONT structure.</span></span> <span data-ttu-id="a3d26-108">La estructura GX_FONT define parámetros de fuente globales, como el carácter incluido en la fuente y el alto de línea de esta.</span><span class="sxs-lookup"><span data-stu-id="a3d26-108">The GX_FONT structure defines global font parameters, such as the character included within the font and the line height of the font.</span></span> <span data-ttu-id="a3d26-109">La estructura GX_FONT apunta a una matriz de estructuras GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="a3d26-109">The GX_FONT structure points at an array of GX_GLYPH structures.</span></span> <span data-ttu-id="a3d26-110">Cada estructura GX_GLYPH define el ancho, el alto y el desplazamiento de línea base de un glifo de carácter específico.</span><span class="sxs-lookup"><span data-stu-id="a3d26-110">Each GX_GLYPH structure defines the width, height, and baseline offset of one specific character glyph.</span></span> <span data-ttu-id="a3d26-111">La estructura GX_GLYPH también apunta a los datos de mapa de bits del glifo (que pueden ser NULL en el caso de caracteres de espacio en blanco).</span><span class="sxs-lookup"><span data-stu-id="a3d26-111">The GX_GLYPH structure also points to the actual glyph bitmap data (which may be NULL for whitespace characters).</span></span>

<span data-ttu-id="a3d26-112">La estructura GX_FONT, incluida en gx_api.h, se declara de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a3d26-112">The GX_FONT structure, contained in gx_api.h, is declared as follows:</span></span>

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

<span data-ttu-id="a3d26-113">El campo gx_font_format define los bits por píxel de la fuente y otras marcas, tal y como se define en el archivo de encabezado gx_api.h.</span><span class="sxs-lookup"><span data-stu-id="a3d26-113">The gx_font_format field defines the font bits-per-pixel and other flags, as defined in the gx_api.h header file.</span></span>

<span data-ttu-id="a3d26-114">El campo gx_font_prespace define el espacio en píxeles que se va a omitir encima de cada línea de texto en una representación de texto de varias líneas.</span><span class="sxs-lookup"><span data-stu-id="a3d26-114">The gx_font_prespace defines the pixel space to skip above each line of text in a multi-line text display.</span></span>

<span data-ttu-id="a3d26-115">El campo gx_font_postspace define el espacio en píxeles que se va a omitir debajo de cada línea de texto en una representación de texto de varias líneas.</span><span class="sxs-lookup"><span data-stu-id="a3d26-115">The gx_font_postspace field defines the pixel space to skip below each line of text in a multi-line text display.</span></span>

<span data-ttu-id="a3d26-116">El campo gx_font_line_height define la altura del glifo más alto de la fuente.</span><span class="sxs-lookup"><span data-stu-id="a3d26-116">The gx_font_line_height field defines the height of the tallest glyph in the font.</span></span>

<span data-ttu-id="a3d26-117">El campo gx_font_baseline define la distancia, en píxeles, desde la fila superior de píxeles del glifo hasta la línea base de la fuente.</span><span class="sxs-lookup"><span data-stu-id="a3d26-117">The gx_font_baseline field defines the distance, in pixels, from the top row of glyph pixels to the font baseline.</span></span>

<span data-ttu-id="a3d26-118">El campo gx_font_first_glyph define la primera codificación de caracteres Unicode incluida en esta página de fuentes.</span><span class="sxs-lookup"><span data-stu-id="a3d26-118">The gx_font_first_glyph field defines the first Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="a3d26-119">El campo gx_font_last_glyph define la última codificación de caracteres Unicode incluida en esta página de fuentes.</span><span class="sxs-lookup"><span data-stu-id="a3d26-119">The gx_font_last_glyph field defines the last Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="a3d26-120">El puntero gx_font_glyphs apunta a una matriz de estructuras GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="a3d26-120">The gx_font_glyphs pointer points to an array of GX_GLYPH structures.</span></span> <span data-ttu-id="a3d26-121">El tamaño de esta matriz debe coincidir con el número de caracteres que contiene esta página de fuentes, es decir,</span><span class="sxs-lookup"><span data-stu-id="a3d26-121">This array must be equal in size to the number of characters contained on this font page, i.e</span></span> <span data-ttu-id="a3d26-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span><span class="sxs-lookup"><span data-stu-id="a3d26-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span></span>

<span data-ttu-id="a3d26-123">El miembro gx_font_next_page se usa para fuentes de varias páginas.</span><span class="sxs-lookup"><span data-stu-id="a3d26-123">The gx_font_next_page member is used for multiple page fonts.</span></span> <span data-ttu-id="a3d26-124">Las fuentes de varias páginas se usan con juegos de caracteres extendidos y para optimizar el tamaño de las matrices de estructuras GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="a3d26-124">Multiple page fonts are used for extended character sets and to optimize the size of the GX_GLYPH structure arrays.</span></span> <span data-ttu-id="a3d26-125">Si todos los caracteres de la fuente están incluidos dentro de una misma página, o bien si se trata de la última página de la fuente en cuestión, el miembro gx_font_next_page se establece en GX_NULL.</span><span class="sxs-lookup"><span data-stu-id="a3d26-125">If all of the characters of the font are contained within one font page, or if this is the last page of the font in question, the gx_font_next_page member is set to GX_NULL.</span></span>

<span data-ttu-id="a3d26-126">Como ya se ha indicado, la estructura GX_FONT anterior contiene un puntero a una matriz de estructuras GX_GLYPHS.</span><span class="sxs-lookup"><span data-stu-id="a3d26-126">As noted above, the GX_FONT structure above contains a pointer to an array of GX_GLYPHS structures.</span></span> <span data-ttu-id="a3d26-127">Debe haber una estructura GX_GLYPH por cada carácter de la página de fuentes.</span><span class="sxs-lookup"><span data-stu-id="a3d26-127">There must be one GX_GLYPH structure for each character on the font page.</span></span> <span data-ttu-id="a3d26-128">La estructura GX_GLYPH se define de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a3d26-128">The GX_GLYPH structure is defined as:</span></span>

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

<span data-ttu-id="a3d26-129">El puntero gx_glyph_map apunta al mapa de bits del glifo.</span><span class="sxs-lookup"><span data-stu-id="a3d26-129">The gx_glyph_map pointer points to the glyph bitmap.</span></span> <span data-ttu-id="a3d26-130">Este puntero puede ser GX_NULL en el caso de caracteres de espacio en blanco.</span><span class="sxs-lookup"><span data-stu-id="a3d26-130">This pointer may be GX_NULL for whitespace characters.</span></span> <span data-ttu-id="a3d26-131">Los datos de mapa de bits se codifican como valores alfa de 1, 2, 4 u 8 bpp.</span><span class="sxs-lookup"><span data-stu-id="a3d26-131">The bitmap data is encoded as 1 bpp, 2 bpp, 4 bpp, or 8 bpp alpha values.</span></span> <span data-ttu-id="a3d26-132">En el caso de los datos de 1 bit, un valor de 1 indica que el píxel se debe escribir en el color de primer plano, mientras que un valor de 0 indica que el píxel es transparente.</span><span class="sxs-lookup"><span data-stu-id="a3d26-132">For 1 bit data, a value of 1 indicates that the pixel should be written in the foreground color, and a value of 0 indicates that the pixel is transparent.</span></span> <span data-ttu-id="a3d26-133">En el caso de los datos de 8 bits, los valores van de 0 (totalmente transparente) a 255 (totalmente opaco).</span><span class="sxs-lookup"><span data-stu-id="a3d26-133">For 8 bit data, the values range from 0 (fully transparent) to 255 (fully opague).</span></span> <span data-ttu-id="a3d26-134">Todos los valores intermedios representan un valor de mezcla para fuentes suavizadas.</span><span class="sxs-lookup"><span data-stu-id="a3d26-134">All intermediate value represent a blending value for anti-aliased fonts.</span></span> <span data-ttu-id="a3d26-135">Los datos de mapa de bits de glifo siempre se rellenan hasta la alineación completa de bytes en el caso de los formatos que usan valores de datos inferiores a 8 bpp.</span><span class="sxs-lookup"><span data-stu-id="a3d26-135">The glyph bitmap data is always padded to full byte alignment for formats using less than 8bpp data values.</span></span>

<span data-ttu-id="a3d26-136">Los valores gx_glyph_ascent y gx_glyph_descent colocan el glifo verticalmente con respecto a la línea base de la fuente.</span><span class="sxs-lookup"><span data-stu-id="a3d26-136">The gx_glyph_ascent and gx_glyph_descent values position the glyph vertically with respect to the font baseline.</span></span>

<span data-ttu-id="a3d26-137">Los valores gx_glyph_width y gx_glyph_height especifican el tamaño de los datos de mapa de bits del glifo.</span><span class="sxs-lookup"><span data-stu-id="a3d26-137">The gx_glyph_width and gx_glyph_height values specify the size of the glyph bitmap data.</span></span>

<span data-ttu-id="a3d26-138">El valor gx_glyph_advance especifica el ancho en píxeles que se debe adelantar la posición de dibujo después de dibujar el glifo (puede no coincidir con el ancho del glifo).</span><span class="sxs-lookup"><span data-stu-id="a3d26-138">The gx_glyph_advance value specifies the pixel width to advance the drawing position after drawing the glyph (this may not be equal to the glyph width).</span></span>

<span data-ttu-id="a3d26-139">El valor gx_glyph_leading especifica los píxeles que se debe avanzar en la dirección x antes de representar el glifo.</span><span class="sxs-lookup"><span data-stu-id="a3d26-139">The gx_glyph_leading value specifies the pixels to advance in the x-direction prior to rendering the glyph.</span></span>