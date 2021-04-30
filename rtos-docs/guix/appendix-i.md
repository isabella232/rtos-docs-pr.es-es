---
title: 'Apéndice I: Estructuras de información de GUIX'
description: Obtenga información sobre las estructuras de información de GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 03a10aeb65017befaf5e7b440046dbff9f9252ef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815526"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="5347f-103">Apéndice I: Estructuras de información de GUIX</span><span class="sxs-lookup"><span data-stu-id="5347f-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="5347f-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="5347f-105">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="5347f-106">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-106">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="5347f-107">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="5347f-107">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="5347f-108">Texto que se va a reordenar.</span><span class="sxs-lookup"><span data-stu-id="5347f-108">Text for reordering</span></span> |
| <span data-ttu-id="5347f-109">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="5347f-109">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="5347f-110">Fuente utilizada para mostrar el texto, establézcala en GX_NULL si no se necesita salto de línea.</span><span class="sxs-lookup"><span data-stu-id="5347f-110">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="5347f-111">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="5347f-111">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="5347f-112">Ancho disponible para mostrar, establézcalo en -1 si no se necesita salto de línea.</span><span class="sxs-lookup"><span data-stu-id="5347f-112">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="5347f-113">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-113">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="5347f-114">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-114">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="5347f-115">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-115">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="5347f-116">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="5347f-116">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="5347f-117">Puntero a la matriz de texto bidireccional reordenado.</span><span class="sxs-lookup"><span data-stu-id="5347f-117">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="5347f-118">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="5347f-118">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="5347f-119">Líneas totales de texto bidireccional resuelto para un párrafo.</span><span class="sxs-lookup"><span data-stu-id="5347f-119">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="5347f-120">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="5347f-120">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="5347f-121">Información del texto bidireccional resuelto para el párrafo siguiente.</span><span class="sxs-lookup"><span data-stu-id="5347f-121">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="5347f-122">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-122">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="5347f-123">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-123">Definition</span></span>

```c
typedef struct GX_CIRCULAR_GAUGE_INFO_STRUCT
{
    INT             gx_circular_gauge_info_animation_steps;
    INT             gx_circular_gauge_info_animation_delay;
    GX_VALUE        gx_circular_gauge_info_needle_xpos;
    GX_VALUE        gx_circular_gauge_info_needle_ypos;
    GX_VALUE        gx_circular_gauge_info_needle_xcor;
    GX_VALUE        gx_circular_gauge_info_needle_ycor;
    GX_RESOURCE_ID  gx_circular_gauge_info_needle_pixelmap;
} GX_CIRCULAR_GAUGE_INFO;
```
### <a name="members"></a><span data-ttu-id="5347f-124">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-124">Members</span></span>

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="5347f-125">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="5347f-125">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="5347f-126">Pasos totales por los que se desplazará la aguja al pasar del ángulo de aguja actual a un ángulo de aguja recién asignado.</span><span class="sxs-lookup"><span data-stu-id="5347f-126">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="5347f-127">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="5347f-127">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="5347f-128">Número de tics del reloj de GUIX que se van a retrasar entre los pasos de la animación.</span><span class="sxs-lookup"><span data-stu-id="5347f-128">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="5347f-129">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="5347f-129">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="5347f-130">Distancia desde la izquierda del widget del medidor hasta el centro de rotación de la aguja del medidor.</span><span class="sxs-lookup"><span data-stu-id="5347f-130">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="5347f-131">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="5347f-131">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="5347f-132">Distancia desde la parte superior del widget del medidor hasta el centro de rotación de la aguja del medidor.</span><span class="sxs-lookup"><span data-stu-id="5347f-132">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="5347f-133">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="5347f-133">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="5347f-134">Distancia desde la izquierda de la imagen de la aguja hasta el centro de rotación de la aguja del medidor.</span><span class="sxs-lookup"><span data-stu-id="5347f-134">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="5347f-135">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="5347f-135">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="5347f-136">Distancia desde la parte superior de la imagen de aguja hasta el centro de rotación de la aguja del medidor.</span><span class="sxs-lookup"><span data-stu-id="5347f-136">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="5347f-137">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-137">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="5347f-138">Identificador de recurso del mapa de píxeles que se usará para dibujar la aguja del medidor.</span><span class="sxs-lookup"><span data-stu-id="5347f-138">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="5347f-139">El widget del medidor girará esta imagen según sea necesario para mostrar la aguja del medidor en cualquier posición.</span><span class="sxs-lookup"><span data-stu-id="5347f-139">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="5347f-140">En el diagrama siguiente se muestran las coordenadas xpos, ypos, xcor e ycor:</span><span class="sxs-lookup"><span data-stu-id="5347f-140">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![Diagrama de las coordenadas X e Y de la aguja](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="5347f-142">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-142">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="5347f-143">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-143">Definition</span></span>

```c
typedef struct GX_LINE_CHART_INFO_STRUCT
{
    INT            gx_line_chart_min_val;
    INT            gx_line_chart_max_val;
    INT           *gx_line_chart_data;
    GX_VALUE       gx_line_left_margin;
    GX_VALUE       gx_line_top_margin;
    GX_VALUE       gx_line_right_margin;
    GX_VALUE       gx_line_bottom_margin;
    GX_VALUE       gx_line_chart_max_data_count;
    GX_VALUE       gx_line_chart_active_data_count;
    GX_VALUE       gx_line_chart_axis_line_width;
    GX_VALUE       gx_line_chart_data_line_width;
    GX_RESOURCE_ID gx_line_chart_axis_color;
    GX_RESOURCE_ID gx_line_chart_line_color;
} GX_LINE_CHART_INFO;
```

### <a name="members"></a><span data-ttu-id="5347f-144">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-144">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="5347f-145">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="5347f-145">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="5347f-146">Valor de datos mínimo, que se usa para calcular el escalado.</span><span class="sxs-lookup"><span data-stu-id="5347f-146">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="5347f-147">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="5347f-147">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="5347f-148">Valor de datos máximo, que se usa para calcular el escalado.</span><span class="sxs-lookup"><span data-stu-id="5347f-148">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="5347f-149">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="5347f-149">**gx_line_chart_data**</span></span>             | <span data-ttu-id="5347f-150">Puntero a una matriz de valores enteros.</span><span class="sxs-lookup"><span data-stu-id="5347f-150">Pointer to an array of integer values.</span></span> <span data-ttu-id="5347f-151">Estos son los valores enteros trazados por el widget de gráfico de líneas.</span><span class="sxs-lookup"><span data-stu-id="5347f-151">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="5347f-152">**gx_line_<side>_margin**</span><span class="sxs-lookup"><span data-stu-id="5347f-152">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="5347f-153">Desplazamiento desde el límite exterior de la ventana del gráfico hasta el área de representación del gráfico real.</span><span class="sxs-lookup"><span data-stu-id="5347f-153">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="5347f-154">El eje del gráfico y la línea de datos siempre se trazan dentro de este límite interno, lo que permite que la aplicación dibuje etiquetas y otra información dentro de la ventana del gráfico, pero fuera del área de gráficos de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5347f-154">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="5347f-155">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="5347f-155">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="5347f-156">Número de valores de datos que pueden estar presentes.</span><span class="sxs-lookup"><span data-stu-id="5347f-156">The number of data values which may be present.</span></span> <span data-ttu-id="5347f-157">Este parámetro se usa para calcular el escalado o el intervalo del eje X para trazar los puntos de datos.</span><span class="sxs-lookup"><span data-stu-id="5347f-157">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="5347f-158">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="5347f-158">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="5347f-159">Número de valores de datos que se encuentran realmente en la matriz de datos.</span><span class="sxs-lookup"><span data-stu-id="5347f-159">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="5347f-160">Un gráfico de líneas se puede escalar para que dibuje un máximo de 100 valores (por ejemplo), pero en alguna actualización en particular puede estar presente un número menor de valores de datos.</span><span class="sxs-lookup"><span data-stu-id="5347f-160">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="5347f-161">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="5347f-161">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="5347f-162">Ancho de la línea que se usa para dibujar los ejes horizontal y vertical.</span><span class="sxs-lookup"><span data-stu-id="5347f-162">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="5347f-163">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="5347f-163">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="5347f-164">Ancho de la línea de datos trazada.</span><span class="sxs-lookup"><span data-stu-id="5347f-164">Width of the plotted data line</span></span> |
| <span data-ttu-id="5347f-165">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-165">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="5347f-166">Identificador de recurso del color utilizado para dibujar las líneas de los ejes.</span><span class="sxs-lookup"><span data-stu-id="5347f-166">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="5347f-167">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-167">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="5347f-168">Identificador de recurso del color utilizado para dibujar la línea de datos del gráfico.</span><span class="sxs-lookup"><span data-stu-id="5347f-168">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="5347f-169">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-169">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="5347f-170">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-170">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a><span data-ttu-id="5347f-171">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-171">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="5347f-172">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="5347f-172">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="5347f-173">Identificador de recurso de la imagen del mouse.</span><span class="sxs-lookup"><span data-stu-id="5347f-173">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="5347f-174">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="5347f-174">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="5347f-175">Desplazamiento desde la izquierda de la imagen del mouse hasta la zona activa de la imagen del mouse.</span><span class="sxs-lookup"><span data-stu-id="5347f-175">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="5347f-176">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="5347f-176">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="5347f-177">Desplazamiento desde la parte superior de la imagen del mouse hasta la zona activa de la imagen del mouse.</span><span class="sxs-lookup"><span data-stu-id="5347f-177">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="5347f-178">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="5347f-178">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="5347f-179">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-179">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a><span data-ttu-id="5347f-180">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-180">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="5347f-181">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="5347f-181">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="5347f-182">Distancia mínima de arrastre por cada tic del temporizador de GUIX para desencadenar un evento FLICK.</span><span class="sxs-lookup"><span data-stu-id="5347f-182">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="5347f-183">Llamar a GX_FIXED_VAL_MAKE para crear un valor de tipo de datos de punto fijo</span><span class="sxs-lookup"><span data-stu-id="5347f-183">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="5347f-184">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="5347f-184">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="5347f-185">Velocidad de arrastre máxima en tics del temporizador de GUIX para desencadenar un evento FLICK.</span><span class="sxs-lookup"><span data-stu-id="5347f-185">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="5347f-186">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-186">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="5347f-187">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-187">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="5347f-188">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-188">Members</span></span>

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="5347f-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="5347f-190">Identificador de recurso del mapa de píxeles para rellenar el fondo antes de la aguja.</span><span class="sxs-lookup"><span data-stu-id="5347f-190">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="5347f-191">Si no se establece el mapa de píxeles de fondo superior, se usa para rellenar el fondo antes y después de la aguja.</span><span class="sxs-lookup"><span data-stu-id="5347f-191">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="5347f-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="5347f-193">Identificador de recurso del mapa de píxeles para rellenar el fondo después de la aguja.</span><span class="sxs-lookup"><span data-stu-id="5347f-193">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="5347f-194">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-194">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="5347f-195">Identificador de recurso del mapa de píxeles de la aguja.</span><span class="sxs-lookup"><span data-stu-id="5347f-195">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="5347f-196">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-196">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="5347f-197">**Definición**</span><span class="sxs-lookup"><span data-stu-id="5347f-197">**Definition**</span></span>

```c
typedef struct GX_PROGRESS_BAR_INFO_STRUCT
{
    INT gx_progress_bar_info_min_val;
    INT gx_progress_bar_info_max_val;
    INT gx_progress_bar_info_current_val;
    GX_RESOURCE_ID gx_progress_bar_font_id;
    GX_RESOURCE_ID gx_progress_bar_normal_text_color;
    GX_RESOURCE_ID gx_progress_bar_selected_text_color;
    GX_RESOURCE_ID gx_progress_bar_disabled_text_color;
    GX_RESOURCE_ID gx_progress_bar_fill_pixelmap;
} GX_PROGRESS_BAR_INFO;
```

### <a name="members"></a><span data-ttu-id="5347f-198">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-198">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="5347f-199">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="5347f-199">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="5347f-200">Valor mínimo notificado.</span><span class="sxs-lookup"><span data-stu-id="5347f-200">Minimum reported value</span></span> |
| <span data-ttu-id="5347f-201">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="5347f-201">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="5347f-202">Valor máximo notificado.</span><span class="sxs-lookup"><span data-stu-id="5347f-202">Maximum reported value</span></span> |
| <span data-ttu-id="5347f-203">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="5347f-203">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="5347f-204">Valor actual</span><span class="sxs-lookup"><span data-stu-id="5347f-204">Current value</span></span> |
| <span data-ttu-id="5347f-205">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="5347f-205">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="5347f-206">Identificador de recurso de la fuente, utilizado para dibujar el valor de texto opcional en el widget de la barra de progreso.</span><span class="sxs-lookup"><span data-stu-id="5347f-206">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="5347f-207">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-207">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="5347f-208">Identificador de recurso del color del texto en estado normal, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso.</span><span class="sxs-lookup"><span data-stu-id="5347f-208">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="5347f-209">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-209">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="5347f-210">Identificador de recurso del color del texto cuando el widget tiene el foco, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso.</span><span class="sxs-lookup"><span data-stu-id="5347f-210">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="5347f-211">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-211">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="5347f-212">Identificador de recurso del color del texto cuando no está activo GX_STYLE_ENABLED, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso.</span><span class="sxs-lookup"><span data-stu-id="5347f-212">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="5347f-213">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-213">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="5347f-214">Identificador de recurso del mapa de píxeles para el relleno del fondo.</span><span class="sxs-lookup"><span data-stu-id="5347f-214">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="5347f-215">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-215">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="5347f-216">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-216">Definition</span></span>

```c
typedef struct GX_RADIAL_PROGRESS_BAR_INFO_STRUCT
{
    GX_VALUE       gx_radial_progress_bar_info_xcenter;
    GX_VALUE       gx_radial_progress_bar_info_ycenter;
    GX_VALUE       gx_radial_progress_bar_info_radius;
    GX_VALUE       gx_radial_progress_bar_info_current_val;
    GX_VALUE       gx_radial_progress_bar_info_anchor_val;
    GX_RESOURCE_ID gx_radial_progress_bar_info_font_id;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_disabled_text_color;
    GX_VALUE       gx_radial_progress_bar_info_normal_brush_width;
    GX_VALUE       gx_radial_progress_bar_info_selected_brush_width;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_brush_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_brush_color;
} GX_RADIAL_PROGRESS_BAR_INFO;
```

### <a name="members"></a><span data-ttu-id="5347f-217">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-217">Members</span></span>

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="5347f-218">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="5347f-218">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="5347f-219">Posición del widget en la coordenada X.</span><span class="sxs-lookup"><span data-stu-id="5347f-219">Widget position in x coordinate</span></span> |
| <span data-ttu-id="5347f-220">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="5347f-220">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="5347f-221">Posición del widget en la coordenada Y.</span><span class="sxs-lookup"><span data-stu-id="5347f-221">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="5347f-222">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="5347f-222">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="5347f-223">Radio del círculo de progreso.</span><span class="sxs-lookup"><span data-stu-id="5347f-223">Radius of the progress circle</span></span> |
| <span data-ttu-id="5347f-224">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="5347f-224">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="5347f-225">Valor actual, limitado al intervalo [-360, 360], indica la diferencia angular entre la posición del delimitador y el punto final del arco superior. Un valor negativo hace que el arco se dibuje en el sentido de las agujas del reloj a partir de la posición del delimitador.</span><span class="sxs-lookup"><span data-stu-id="5347f-225">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="5347f-226">Un valor positivo hace que el arco se dibuje en sentido contrario a las agujas del reloj a partir de la posición del delimitador.</span><span class="sxs-lookup"><span data-stu-id="5347f-226">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="5347f-227">La aplicación debe escalar el valor real que se indica para asignar un valor angular al widget de la barra de progreso.</span><span class="sxs-lookup"><span data-stu-id="5347f-227">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="5347f-228">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="5347f-228">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="5347f-229">Ángulo inicial del arco de progreso superior. El valor se define en términos de grados enteros; 0 grados indica que apunta a la derecha y 90 grados indica que apunta hacia arriba.</span><span class="sxs-lookup"><span data-stu-id="5347f-229">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="5347f-230">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="5347f-230">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="5347f-231">Identificador de recurso de la fuente, utilizado para dibujar el valor de texto opcional en el widget de la barra de progreso.</span><span class="sxs-lookup"><span data-stu-id="5347f-231">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="5347f-232">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-232">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="5347f-233">Identificador de recurso del color del texto en estado normal, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso.</span><span class="sxs-lookup"><span data-stu-id="5347f-233">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="5347f-234">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-234">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="5347f-235">Identificador de recurso del color del texto cuando el widget tiene el foco, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso.</span><span class="sxs-lookup"><span data-stu-id="5347f-235">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="5347f-236">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-236">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="5347f-237">Identificador de recurso del color del texto cuando no está activo GX_STYLE_ENABLED, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso.</span><span class="sxs-lookup"><span data-stu-id="5347f-237">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="5347f-238">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="5347f-238">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="5347f-239">Ancho del círculo de progreso inferior.</span><span class="sxs-lookup"><span data-stu-id="5347f-239">Width of the lower progress circle</span></span> |
| <span data-ttu-id="5347f-240">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="5347f-240">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="5347f-241">Ancho del arco de progreso superior; el arco superior puede ser más estrecho, igual o más ancho que el círculo inferior.</span><span class="sxs-lookup"><span data-stu-id="5347f-241">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="5347f-242">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-242">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="5347f-243">Identificador de recurso del color para rellenar el círculo de progreso inferior.</span><span class="sxs-lookup"><span data-stu-id="5347f-243">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="5347f-244">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-244">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="5347f-245">Identificador de recurso del color para rellenar el arco de progreso superior.</span><span class="sxs-lookup"><span data-stu-id="5347f-245">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="5347f-246">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-246">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="5347f-247">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-247">Definition</span></span>

```c
typedef struct GX_RADIAL_SLIDER_INFO_STRUCT
{
    GX_VALUE       gx_radial_slider_info_xcenter;
    GX_VALUE       gx_radial_slider_info_ycenter;
    USHORT         gx_radial_slider_info_radius;
    USHORT         gx_radial_slider_info_track_width;
    GX_VALUE       gx_radial_slider_info_current_angle;
    GX_VALUE       gx_radial_slider_info_min_angle;
    GX_VALUE       gx_radial_slider_info_max_angle;
    GX_VALUE      *gx_radial_slider_info_angle_list;
    USHORT         gx_radial_slider_info_list_cont;
    GX_RESOURCE_ID gx_radial_slider_info_background_pixelmap;
    GX_RESOURCE_ID gx_radial_slider_info_needle_pixelmap;
} GX_RADIAL_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="5347f-248">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-248">Members</span></span>

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="5347f-249">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="5347f-249">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="5347f-250">Distancia desde la izquierda del widget de control deslizante hasta el centro de rotación de la aguja del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="5347f-250">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="5347f-251">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="5347f-251">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="5347f-252">Distancia desde la parte superior del widget de control deslizante hasta el centro de rotación de la aguja del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="5347f-252">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="5347f-253">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="5347f-253">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="5347f-254">Radio del círculo del control deslizante radial.</span><span class="sxs-lookup"><span data-stu-id="5347f-254">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="5347f-255">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="5347f-255">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="5347f-256">Ancho de la pista del control deslizante radial.</span><span class="sxs-lookup"><span data-stu-id="5347f-256">Width of radial slider track</span></span> |
| <span data-ttu-id="5347f-257">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="5347f-257">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="5347f-258">Ángulo del control deslizante actual.</span><span class="sxs-lookup"><span data-stu-id="5347f-258">Current slider angle</span></span> |
| <span data-ttu-id="5347f-259">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="5347f-259">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="5347f-260">Ángulo mínimo del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="5347f-260">Minimum slider angle</span></span> |
| <span data-ttu-id="5347f-261">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="5347f-261">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="5347f-262">Ángulo máximo del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="5347f-262">Maximum slider angle</span></span> |
| <span data-ttu-id="5347f-263">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="5347f-263">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="5347f-264">Lista de valores de ángulo que define los ángulos del delimitador; si se establece, el ángulo del control deslizante solo puede ser uno de los ángulos del delimitador definidos.</span><span class="sxs-lookup"><span data-stu-id="5347f-264">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="5347f-265">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="5347f-265">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="5347f-266">Número de ángulos del delimitador.</span><span class="sxs-lookup"><span data-stu-id="5347f-266">Number of anchor angles</span></span> |
| <span data-ttu-id="5347f-267">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-267">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="5347f-268">Identificador de recurso del mapa de píxeles del fondo.</span><span class="sxs-lookup"><span data-stu-id="5347f-268">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="5347f-269">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-269">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="5347f-270">Identificador de recurso del mapa de píxeles de la aguja.</span><span class="sxs-lookup"><span data-stu-id="5347f-270">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="5347f-271">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="5347f-271">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="5347f-272">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-272">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a><span data-ttu-id="5347f-273">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-273">Members</span></span>

|                                  |                         |
| -------------------------------- | ------------------------|
| <span data-ttu-id="5347f-274">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="5347f-274">**gx_rectangle_left**</span></span>            | <span data-ttu-id="5347f-275">Izquierda del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="5347f-275">Left of the rectangle</span></span>   |  
| <span data-ttu-id="5347f-276">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="5347f-276">**gx_rectangle_top**</span></span>             | <span data-ttu-id="5347f-277">Parte superior del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="5347f-277">Top of the rectangle</span></span>    | 
| <span data-ttu-id="5347f-278">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="5347f-278">**gx_rectangle_right**</span></span>           | <span data-ttu-id="5347f-279">Derecha del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="5347f-279">Right of the rectangle</span></span>  |
| <span data-ttu-id="5347f-280">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="5347f-280">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="5347f-281">Parte inferior del rectángulo.</span><span class="sxs-lookup"><span data-stu-id="5347f-281">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="5347f-282">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="5347f-282">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="5347f-283">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-283">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a><span data-ttu-id="5347f-284">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-284">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="5347f-285">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="5347f-285">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="5347f-286">Identificador de recurso de la fuente de texto normal.</span><span class="sxs-lookup"><span data-stu-id="5347f-286">Resource ID of normal text font</span></span> |
| <span data-ttu-id="5347f-287">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="5347f-287">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="5347f-288">Identificador de recurso de la fuente de texto en negrita.</span><span class="sxs-lookup"><span data-stu-id="5347f-288">Resource ID of bold text font</span></span> |
| <span data-ttu-id="5347f-289">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="5347f-289">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="5347f-290">Identificador de recurso de la fuente de texto en cursiva.</span><span class="sxs-lookup"><span data-stu-id="5347f-290">Resource ID of italic text font</span></span> |
| <span data-ttu-id="5347f-291">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="5347f-291">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="5347f-292">Identificador de recurso de la fuente de texto en cursiva y negrita.</span><span class="sxs-lookup"><span data-stu-id="5347f-292">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="5347f-293">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-293">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="5347f-294">**Definición**</span><span class="sxs-lookup"><span data-stu-id="5347f-294">**Definition**</span></span>

```c
typedef struct GX_SCROLL_INFO_STRUCT
{
    INT      gx_scroll_value;
    INT      gx_scroll_minimum;
    INT      gx_scroll_maximum;
    GX_VALUE gx_scroll_visible;
    GX_VALUE gx_scroll_increment;
} GX_SCROLL_INFO;
```

### <a name="members"></a><span data-ttu-id="5347f-295">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-295">Members</span></span>

|                         |                               |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="5347f-296">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="5347f-296">**gx_scroll_value**</span></span>     | <span data-ttu-id="5347f-297">Posición de desplazamiento actual.</span><span class="sxs-lookup"><span data-stu-id="5347f-297">Current scroll position</span></span>       |
| <span data-ttu-id="5347f-298">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="5347f-298">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="5347f-299">Posición mínima notificada.</span><span class="sxs-lookup"><span data-stu-id="5347f-299">Minimum reported position</span></span>     |
| <span data-ttu-id="5347f-300">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="5347f-300">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="5347f-301">Posición máxima notificada.</span><span class="sxs-lookup"><span data-stu-id="5347f-301">Maximum reported position</span></span>     |
| <span data-ttu-id="5347f-302">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="5347f-302">**gx_scroll_visible**</span></span>   | <span data-ttu-id="5347f-303">Intervalo visible de la ventana primaria.</span><span class="sxs-lookup"><span data-stu-id="5347f-303">Parent window visible range</span></span>   |
| <span data-ttu-id="5347f-304">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="5347f-304">**gx_scroll_increment**</span></span> | <span data-ttu-id="5347f-305">Valor delta mínimo de la barra de desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="5347f-305">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="5347f-306">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="5347f-306">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="5347f-307">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-307">Definition</span></span>

```c
typedef struct GX_SCROLLBAR_APPEARANCE_STRUCT
{
    GX_VALUE       gx_scroll_width;
    GX_VALUE       gx_scroll_thumb_width;
    GX_VALUE       gx_scroll_thumb_travel_min;
    GX_VALUE       gx_scroll_thumb_travel_max;
    GX_UBYTE       gx_scroll_thumb_border_style;
    GX_RESOURCE_ID gx_scroll_fill_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_pixelmap;
    GX_RESOURCE_ID gx_scroll_up_pixelmap;
    GX_RESOURCE_ID gx_scroll_down_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_color;
    GX_RESOURCE_ID gx_scroll_thumb_border_color;
    GX_RESOURCE_ID gx_scroll_button_color;
} GX_SCROLLBAR_APPEARANCE;
```

### <a name="members"></a><span data-ttu-id="5347f-308">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-308">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="5347f-309">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="5347f-309">**gx_scroll_width**</span></span>                      | <span data-ttu-id="5347f-310">Ancho del widget de barra de desplazamiento en píxeles.</span><span class="sxs-lookup"><span data-stu-id="5347f-310">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="5347f-311">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="5347f-311">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="5347f-312">Ancho del botón de posición que se desliza en la barra de desplazamiento en píxeles.</span><span class="sxs-lookup"><span data-stu-id="5347f-312">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="5347f-313">Normalmente, este valor es algunos píxeles menor que el ancho total de la barra de desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="5347f-313">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="5347f-314">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="5347f-314">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="5347f-315">Desplazamiento desde el final de la barra de desplazamiento hasta el punto mínimo del recorrido del botón de posición.</span><span class="sxs-lookup"><span data-stu-id="5347f-315">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="5347f-316">Este límite se puede usar para impedir que el botón de posición se desplace hasta el final de la barra de desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="5347f-316">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="5347f-317">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="5347f-317">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="5347f-318">Desplazamiento desde el final de la barra de desplazamiento hasta el punto máximo del recorrido del botón de posición.</span><span class="sxs-lookup"><span data-stu-id="5347f-318">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="5347f-319">Este límite se puede usar para impedir que el botón de posición se desplace hasta el final de la barra de desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="5347f-319">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="5347f-320">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="5347f-320">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="5347f-321">Estilos de borde del botón de posición.</span><span class="sxs-lookup"><span data-stu-id="5347f-321">Border styles of thumb button</span></span> |
| <span data-ttu-id="5347f-322">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-322">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="5347f-323">Identificador del mapa de píxeles opcional.</span><span class="sxs-lookup"><span data-stu-id="5347f-323">Optional pixelmap ID.</span></span> <span data-ttu-id="5347f-324">Si este identificador del mapa de píxeles no es cero, la barra de desplazamiento utiliza este del mapa de píxeles para dibujar el fondo de la barra de desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="5347f-324">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="5347f-325">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-325">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="5347f-326">Identificador del mapa de píxeles opcional.</span><span class="sxs-lookup"><span data-stu-id="5347f-326">Optional pixelmap ID.</span></span> <span data-ttu-id="5347f-327">Si este identificador del mapa de píxeles no es cero, el botón de posición de la barra de desplazamiento usa este del mapa de píxeles para dibujarse.</span><span class="sxs-lookup"><span data-stu-id="5347f-327">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="5347f-328">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-328">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="5347f-329">Identificador del mapa de píxeles opcional.</span><span class="sxs-lookup"><span data-stu-id="5347f-329">Optional pixelmap ID.</span></span> <span data-ttu-id="5347f-330">Si este identificador del mapa de píxeles no es cero, la barra de desplazamiento usa este identificador del mapa de píxeles para dibujar el botón final de la barra de desplazamiento a la izquierda o hacia arriba.</span><span class="sxs-lookup"><span data-stu-id="5347f-330">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="5347f-331">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-331">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="5347f-332">Identificador del mapa de píxeles opcional.</span><span class="sxs-lookup"><span data-stu-id="5347f-332">Optional pixelmap ID.</span></span> <span data-ttu-id="5347f-333">Si este identificador del mapa de píxeles no es cero, la barra de desplazamiento usa este identificador del mapa de píxeles para dibujar el botón final de la barra de desplazamiento a la derecha o hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="5347f-333">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="5347f-334">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-334">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="5347f-335">Identificador de recurso del color utilizado para rellenar el botón de posición.</span><span class="sxs-lookup"><span data-stu-id="5347f-335">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="5347f-336">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-336">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="5347f-337">Identificador de recurso del color utilizado para dibujar el borde del botón de posición.</span><span class="sxs-lookup"><span data-stu-id="5347f-337">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="5347f-338">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="5347f-338">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="5347f-339">Identificador de recurso del color utilizado para rellenar los botones finales de la barra de desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="5347f-339">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="5347f-340">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="5347f-340">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="5347f-341">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-341">Definition</span></span>

```c
typedef struct GX_SLIDER_INFO_STRUCT
{
    INT      gx_slider_info_min_val;
    INT      gx_slider_info_max_val;
    INT      gx_slider_info_current_val;
    INT      gx_slider_info_increment;
    GX_VALUE gx_slider_info_min_travel;
    GX_VALUE gx_slider_info_max_travel;
    GX_VALUE gx_slider_info_needle_width;
    GX_VALUE gx_slider_info_needle_height;
    GX_VALUE gx_slider_info_needle_inset;
    GX_VALUE gx_slider_info_needle_hotspot_offset;
} GX_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="5347f-342">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-342">Members</span></span>

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="5347f-343">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="5347f-343">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="5347f-344">Valor mínimo notificado.</span><span class="sxs-lookup"><span data-stu-id="5347f-344">Minimum reported value</span></span> |
| <span data-ttu-id="5347f-345">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="5347f-345">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="5347f-346">Valor máximo notificado.</span><span class="sxs-lookup"><span data-stu-id="5347f-346">Maximum reported value</span></span> |
| <span data-ttu-id="5347f-347">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="5347f-347">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="5347f-348">Valor actual</span><span class="sxs-lookup"><span data-stu-id="5347f-348">Current value</span></span> |
| <span data-ttu-id="5347f-349">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="5347f-349">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="5347f-350">Límite del recorrido de la aguja.</span><span class="sxs-lookup"><span data-stu-id="5347f-350">Needle travel limit</span></span> |
| <span data-ttu-id="5347f-351">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="5347f-351">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="5347f-352">Límite del recorrido de la aguja.</span><span class="sxs-lookup"><span data-stu-id="5347f-352">Needle travel limit</span></span> |
| <span data-ttu-id="5347f-353">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="5347f-353">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="5347f-354">Ancho de la aguja en píxeles.</span><span class="sxs-lookup"><span data-stu-id="5347f-354">Needle width in pixel</span></span> |
| <span data-ttu-id="5347f-355">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="5347f-355">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="5347f-356">Alto de la aguja en píxeles.</span><span class="sxs-lookup"><span data-stu-id="5347f-356">Needle height in pixel</span></span> |
|<span data-ttu-id="5347f-357">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="5347f-357">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="5347f-358">Posición de dibujo de la aguja.</span><span class="sxs-lookup"><span data-stu-id="5347f-358">Needle draw position.</span></span> <span data-ttu-id="5347f-359">Si GX_STYLE_SLIDER_VERTICAL está establecido, se usa para especificar el desplazamiento desde la posición de inicio del dibujo de la aguja hasta la izquierda del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="5347f-359">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="5347f-360">En caso contrario, se usa para especificar el desplazamiento desde la posición de inicio del dibujo de la aguja hasta la parte superior del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="5347f-360">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="5347f-361">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="5347f-361">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="5347f-362">Desplazamiento de la zona activa de la aguja, se usa para especificar el desplazamiento desde la posición de inicio del dibujo de la aguja hasta la zona activa del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="5347f-362">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="5347f-363">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="5347f-363">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="5347f-364">Definición</span><span class="sxs-lookup"><span data-stu-id="5347f-364">Definition</span></span>

```c
typedef struct GX_SPRITE_FRAME_STRUCT
{
    GX_RESOURCE_ID gx_sprite_frame_pixelmap;
    GX_VALUE gx_sprite_frame_x_offset;
    GX_VALUE gx_sprite_frame_y_offset;
    UINT gx_sprite_frame_delay;
    UINT gx_sprite_frame_background_operation;
    UCHAR gx_sprite_frame_alpha;
} GX_SPRITE_FRAME;
```

### <a name="members"></a><span data-ttu-id="5347f-365">Miembros</span><span class="sxs-lookup"><span data-stu-id="5347f-365">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="5347f-366">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="5347f-366">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="5347f-367">Identificador de recurso del mapa de píxeles que se va a mostrar para este fotograma.</span><span class="sxs-lookup"><span data-stu-id="5347f-367">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="5347f-368">Este identificador puede ser 0.</span><span class="sxs-lookup"><span data-stu-id="5347f-368">The ID can be 0.</span></span> |
| <span data-ttu-id="5347f-369">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="5347f-369">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="5347f-370">Desplazamiento desde la izquierda del widget de sprite para mostrar el mapa de píxeles.</span><span class="sxs-lookup"><span data-stu-id="5347f-370">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="5347f-371">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="5347f-371">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="5347f-372">Desplazamiento desde la parte superior del widget de sprite para mostrar el mapa de píxeles.</span><span class="sxs-lookup"><span data-stu-id="5347f-372">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="5347f-373">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="5347f-373">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="5347f-374">Valor de retraso, en tics del temporizador de GUIX, después de mostrar este fotograma antes de avanzar al siguiente fotograma del sprite.</span><span class="sxs-lookup"><span data-stu-id="5347f-374">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="5347f-375">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="5347f-375">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="5347f-376">Define cómo se debe borrar el fondo.</span><span class="sxs-lookup"><span data-stu-id="5347f-376">Define how the background should be erased.</span></span> <span data-ttu-id="5347f-377">Los valores posibles que admite este campo son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="5347f-377">Possible values for this field are:</span></span><br /><span data-ttu-id="5347f-378">GX_SPRITE_BACKGROUND_NO_ACTION: sin relleno entre fotogramas.</span><span class="sxs-lookup"><span data-stu-id="5347f-378">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="5347f-379">GX_SPRITE_BACKGROUND_SOLID_FILL: volver a dibujar el fondo del sprite.</span><span class="sxs-lookup"><span data-stu-id="5347f-379">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="5347f-380">GX_SPRITE_BACKGROUND_RESTORE: restaurar el mapa de píxeles anterior.</span><span class="sxs-lookup"><span data-stu-id="5347f-380">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="5347f-381">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="5347f-381">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="5347f-382">Valor alfa que se va a agregar al mapa de píxeles mostrado.</span><span class="sxs-lookup"><span data-stu-id="5347f-382">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="5347f-383">El valor 255 especifica que no se debe imponer ningún valor alfa adicional.</span><span class="sxs-lookup"><span data-stu-id="5347f-383">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="5347f-384">Si el mapa de píxeles incluye un canal alfa, este canal alfa se agregará al valor alfa del fotograma.</span><span class="sxs-lookup"><span data-stu-id="5347f-384">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
