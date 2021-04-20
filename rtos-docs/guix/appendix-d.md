---
title: 'Apéndice D: atributos de pincel, lienzo y degradado de GUIX'
description: Obtenga información sobre los atributos de pincel, lienzo y degradado de GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 19c0687a54be244ae395124664b4b6da0f4e90b6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815570"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a><span data-ttu-id="10a00-103">Apéndice D: atributos de pincel, lienzo y degradado de GUIX</span><span class="sxs-lookup"><span data-stu-id="10a00-103">Appendix D - GUIX Brush, Canvas and Gradient Attributes</span></span>

<span data-ttu-id="10a00-104">__**Estilos de pincel:**__</span><span class="sxs-lookup"><span data-stu-id="10a00-104">__**Brush Styles:**__</span></span>

<span data-ttu-id="10a00-105">**GX_BRUSH_OUTLINE**</span><span class="sxs-lookup"><span data-stu-id="10a00-105">**GX_BRUSH_OUTLINE**</span></span>
- <span data-ttu-id="10a00-106">Valor: 0x0000</span><span class="sxs-lookup"><span data-stu-id="10a00-106">Value: 0x0000</span></span>
- <span data-ttu-id="10a00-107">Descripción: este estilo de pincel se aplica a funciones de dibujo de formas, como gx_canvas_rectangle_draw o gx_canvas_polygon_draw.</span><span class="sxs-lookup"><span data-stu-id="10a00-107">Description: This brush style applies to shape drawing functions such as gx_canvas_rectangle_draw or gx_canvas_polygon_draw.</span></span> <span data-ttu-id="10a00-108">Este estilo indica que la forma debe tener contorno, además de poder tener relleno.</span><span class="sxs-lookup"><span data-stu-id="10a00-108">This style indicateds the shape should be outlined, in addition to optionally being fill.</span></span> <span data-ttu-id="10a00-109">Si se establece el estilo GX_BRUSH_OUTLINE, y el GX_BRSUH_SOLID_FILL está desactivado, la forma solo tendrá contorno.</span><span class="sxs-lookup"><span data-stu-id="10a00-109">If the GX_BRUSH_OUTLINE style is set and the GX_BRSUH_SOLID_FILL is cleared, the shape is only outlined.</span></span>

<span data-ttu-id="10a00-110">**GX_BRUSH_SOLID_FILL**</span><span class="sxs-lookup"><span data-stu-id="10a00-110">**GX_BRUSH_SOLID_FILL**</span></span>
- <span data-ttu-id="10a00-111">Valor: 0x0001</span><span class="sxs-lookup"><span data-stu-id="10a00-111">Value: 0x0001</span></span>
- <span data-ttu-id="10a00-112">Descripción: este estilo de pincel se aplica a funciones de dibujo de formas e indica que la forma solicitada se debe rellenar con un color sólido usando el color de relleno actual del pincel.</span><span class="sxs-lookup"><span data-stu-id="10a00-112">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be filled with a solid color using the current brush fill color.</span></span>

<span data-ttu-id="10a00-113">**GX_BRUSH_PIXELMAP_FILL**</span><span class="sxs-lookup"><span data-stu-id="10a00-113">**GX_BRUSH_PIXELMAP_FILL**</span></span>
- <span data-ttu-id="10a00-114">Valor: 0x0002</span><span class="sxs-lookup"><span data-stu-id="10a00-114">Value: 0x0002</span></span>
- <span data-ttu-id="10a00-115">Descripción: este estilo de pincel se aplica a funciones de dibujo de formas e indica que la forma solicitada se debe rellenar con una trama usando el mapa de píxeles actual del pincel.</span><span class="sxs-lookup"><span data-stu-id="10a00-115">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be pattern filled with the current brush pixelmap.</span></span>

<span data-ttu-id="10a00-116">**GX_BRUSH_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="10a00-116">**GX_BRUSH_ALIAS**</span></span>
- <span data-ttu-id="10a00-117">Valor: 0x0004</span><span class="sxs-lookup"><span data-stu-id="10a00-117">Value: 0x0004</span></span>
- <span data-ttu-id="10a00-118">Descripción: este estilo de pincel se aplica a todo el dibujo de líneas y a todos los contornos de formas.</span><span class="sxs-lookup"><span data-stu-id="10a00-118">Description: This brush style applies to all line drawing and shape outlines.</span></span> <span data-ttu-id="10a00-119">Si se establece esta marca, las líneas y los contornos se dibujan con los algoritmos de dibujo suavizado más precisos, pero que también consumen más tiempo.</span><span class="sxs-lookup"><span data-stu-id="10a00-119">If this flag is set, lines and outlines are drawing with the more accurate but also more time consuming anti-aliased drawing algorithms.</span></span> <span data-ttu-id="10a00-120">Esta marca de estilo solo se usa para profundidades de color de 16 bpp o superiores.</span><span class="sxs-lookup"><span data-stu-id="10a00-120">This style flag is only used for 16-bpp color depths and higher.</span></span>

<span data-ttu-id="10a00-121">**GX_BRUSH_UNDERLINE**</span><span class="sxs-lookup"><span data-stu-id="10a00-121">**GX_BRUSH_UNDERLINE**</span></span>
- <span data-ttu-id="10a00-122">Valor: 0x0008</span><span class="sxs-lookup"><span data-stu-id="10a00-122">Value: 0x0008</span></span>
- <span data-ttu-id="10a00-123">Descripción: esta marca se aplica al dibujo de texto e indica que el siguiente texto que se dibuje debe estar subrayado.</span><span class="sxs-lookup"><span data-stu-id="10a00-123">Description: This flag applies to text drawing, and indicates that subsequent text drawn should be underlined.</span></span>

<span data-ttu-id="10a00-124">**GX_BRUSH_ROUND**</span><span class="sxs-lookup"><span data-stu-id="10a00-124">**GX_BRUSH_ROUND**</span></span>
- <span data-ttu-id="10a00-125">Valor: 0x0010</span><span class="sxs-lookup"><span data-stu-id="10a00-125">Value: 0x0010</span></span>
- <span data-ttu-id="10a00-126">Descripción: esta marca se aplica al dibujo de líneas e indica que los extremos de línea se dibujan con una forma redonda o circular, en lugar de la forma cuadrada predeterminada.</span><span class="sxs-lookup"><span data-stu-id="10a00-126">Description: This flag applies to line drawing, and indicates that line ends are drawn with a round or circular shape, rather than the default square shape.</span></span>

<span data-ttu-id="10a00-127">__**Marcas de lienzo:**__</span><span class="sxs-lookup"><span data-stu-id="10a00-127">__**Canvas Flags:**__</span></span>

<span data-ttu-id="10a00-128">**GX_CANVAS_SIMPLE**</span><span class="sxs-lookup"><span data-stu-id="10a00-128">**GX_CANVAS_SIMPLE**</span></span>
- <span data-ttu-id="10a00-129">Valor: 0x01</span><span class="sxs-lookup"><span data-stu-id="10a00-129">Value: 0x01</span></span>
- <span data-ttu-id="10a00-130">Descripción: lienzo de memoria que se usa para dibujar fuera de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="10a00-130">Description: A memory canvas which is used to off-screen drawing.</span></span>

<span data-ttu-id="10a00-131">**GX_CANVAS_MANAGED**</span><span class="sxs-lookup"><span data-stu-id="10a00-131">**GX_CANVAS_MANAGED**</span></span>
- <span data-ttu-id="10a00-132">Valor: 0x02</span><span class="sxs-lookup"><span data-stu-id="10a00-132">Value: 0x02</span></span>
- <span data-ttu-id="10a00-133">Descripción: lienzo que se vacía automáticamente en la pantalla activa, ya sea como parte del proceso de creación de la composición o como parte de la operación de alternancia de búfer para arquitecturas de un solo lienzo.</span><span class="sxs-lookup"><span data-stu-id="10a00-133">Description: A canvas which automatically flushed to the active display, either as part of the composite building process or as part of the buffer toggle operation for single-canvas architectures.</span></span>

<span data-ttu-id="10a00-134">**GX_CANVAS_VISIBLE**</span><span class="sxs-lookup"><span data-stu-id="10a00-134">**GX_CANVAS_VISIBLE**</span></span>
- <span data-ttu-id="10a00-135">Valor: 0x04</span><span class="sxs-lookup"><span data-stu-id="10a00-135">Value: 0x04</span></span>
- <span data-ttu-id="10a00-136">Descripción: esta marca se puede usar para activar y desactivar un lienzo, sin perder el contenido del dibujo que contiene.</span><span class="sxs-lookup"><span data-stu-id="10a00-136">Description: This flag can be used to turn on and off a canvas, without losing the canvas drawing contents.</span></span>

<span data-ttu-id="10a00-137">**GX_CANVAS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="10a00-137">**GX_CANVAS_MODIFIED**</span></span>
- <span data-ttu-id="10a00-138">Valor: 0x08</span><span class="sxs-lookup"><span data-stu-id="10a00-138">Value: 0x08</span></span>
- <span data-ttu-id="10a00-139">Descripción: reservado para su uso futuro.</span><span class="sxs-lookup"><span data-stu-id="10a00-139">Description: Reserved for future use.</span></span>

<span data-ttu-id="10a00-140">**GX_CANVAS_COMPOSITE**</span><span class="sxs-lookup"><span data-stu-id="10a00-140">**GX_CANVAS_COMPOSITE**</span></span>
- <span data-ttu-id="10a00-141">Valor: 0x20</span><span class="sxs-lookup"><span data-stu-id="10a00-141">Value: 0x20</span></span>
- <span data-ttu-id="10a00-142">Descripción: la aplicación usa esta marca al configurar un sistema que compondrá varios lienzos administrados en el compuesto. La composición se conduce al búfer de cuadros del hardware.</span><span class="sxs-lookup"><span data-stu-id="10a00-142">Description: This flag is used by the application when configuring a multiple-canvas system which will composite multiple managed canvases into the composite canvas, and the composite is the driven to the hardware frame buffer.</span></span>

<span data-ttu-id="10a00-143">__**Tipos de degradado:**__</span><span class="sxs-lookup"><span data-stu-id="10a00-143">__**Gradient Types:**__</span></span>

<span data-ttu-id="10a00-144">**GX_GRADIENT_TYPE_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="10a00-144">**GX_GRADIENT_TYPE_VERTICAL**</span></span>
- <span data-ttu-id="10a00-145">Valor: 0x01</span><span class="sxs-lookup"><span data-stu-id="10a00-145">Value: 0x01</span></span>
- <span data-ttu-id="10a00-146">Descripción: crea un degradado de mapa alfa vertical.</span><span class="sxs-lookup"><span data-stu-id="10a00-146">Description: Creates a vertical alphamap gradient.</span></span>

<span data-ttu-id="10a00-147">**GX_GRADIENT_TYPE_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="10a00-147">**GX_GRADIENT_TYPE_ALPHA**</span></span>
- <span data-ttu-id="10a00-148">Valor: 0x02</span><span class="sxs-lookup"><span data-stu-id="10a00-148">Value: 0x02</span></span>
- <span data-ttu-id="10a00-149">Descripción: crea un degradado de mapa alfa.</span><span class="sxs-lookup"><span data-stu-id="10a00-149">Description: Creats an alpha-map style gradient.</span></span> <span data-ttu-id="10a00-150">En estos momentos, este es el único estilo de degradado admitido.</span><span class="sxs-lookup"><span data-stu-id="10a00-150">This is currently the only gradient style supported.</span></span>

<span data-ttu-id="10a00-151">**GX_GRADIENT_TYPE_MIRROR**</span><span class="sxs-lookup"><span data-stu-id="10a00-151">**GX_GRADIENT_TYPE_MIRROR**</span></span>
- <span data-ttu-id="10a00-152">Valor: 0x04</span><span class="sxs-lookup"><span data-stu-id="10a00-152">Value: 0x04</span></span>
- <span data-ttu-id="10a00-153">Descripción: esta marca indica que el degradado debe alcanzar su punto máximo en el centro del intervalo de ancho o alto y volver al valor inicial cuando llegue al borde derecho o inferior.</span><span class="sxs-lookup"><span data-stu-id="10a00-153">Description: This flag indicates that the gradient should peak at the center of the width/height range, and return to the starting value as it reaches the right/bottom edge.</span></span> <span data-ttu-id="10a00-154">Sin esta marca de estilo, el degradado será lineal de arriba abajo o de izquierda a derecha, en función de la marca GX_GRADIENT_TYPE_VERTICAL.</span><span class="sxs-lookup"><span data-stu-id="10a00-154">Without this style flag, the gradient will be a linear gradient from top-to-bottom or left-to-right, depending on the GX_GRADIENT_TYPE_VERTICAL flag.</span></span>