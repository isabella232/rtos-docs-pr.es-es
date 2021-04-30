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
# <a name="appendix-i---guix-information-structures"></a>Apéndice I: Estructuras de información de GUIX 

## <a name="gx_bidi_text_info"></a>GX_BIDI_TEXT_INFO 

### <a name="definition"></a>Definición

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a>Miembros

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_text_info_text**               | Texto que se va a reordenar. |
| **gx_bidi_text_info_font**               | Fuente utilizada para mostrar el texto, establézcala en GX_NULL si no se necesita salto de línea. |
| **gx_bidi_text_info_display_width**      | Ancho disponible para mostrar, establézcalo en -1 si no se necesita salto de línea. |

## <a name="gx_bidi_resolved_text_info"></a>GX_BIDI_RESOLVED_TEXT_INFO 

### <a name="definition"></a>Definición

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a>Miembros

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_resolved_text_info_text**             | Puntero a la matriz de texto bidireccional reordenado. |
| **gx_bidi_resolved_text_info_total_lines**      | Líneas totales de texto bidireccional resuelto para un párrafo. |
| **gx_bidi_resolved_text_info_next**             | Información del texto bidireccional resuelto para el párrafo siguiente. |

## <a name="gx_circular_gauge_info"></a>GX_CIRCULAR_GAUGE_INFO

### <a name="definition"></a>Definición

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
### <a name="members"></a>Miembros

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| **gx_circular_gauge_info_animation_steps**       | Pasos totales por los que se desplazará la aguja al pasar del ángulo de aguja actual a un ángulo de aguja recién asignado. |
| **gx_circular_gauge_info_animation_delay**       | Número de tics del reloj de GUIX que se van a retrasar entre los pasos de la animación. |
| **gx_circular_gauge_info_needle_xpos**           | Distancia desde la izquierda del widget del medidor hasta el centro de rotación de la aguja del medidor. |
| **gx_circular_gauge_info_needle_ypos**           | Distancia desde la parte superior del widget del medidor hasta el centro de rotación de la aguja del medidor. |
| **gx_circular_gauge_info_needle_xcor**           | Distancia desde la izquierda de la imagen de la aguja hasta el centro de rotación de la aguja del medidor. |
| **gx_circular_gauge_info_needle_ycor**           | Distancia desde la parte superior de la imagen de aguja hasta el centro de rotación de la aguja del medidor. |
| **gx_circular_gauge_info_needle_pixelmap**       | Identificador de recurso del mapa de píxeles que se usará para dibujar la aguja del medidor. El widget del medidor girará esta imagen según sea necesario para mostrar la aguja del medidor en cualquier posición. |

En el diagrama siguiente se muestran las coordenadas xpos, ypos, xcor e ycor:

![Diagrama de las coordenadas X e Y de la aguja](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a>GX_LINE_CHART_INFO

### <a name="definition"></a>Definición

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

### <a name="members"></a>Miembros

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_line_chart_min_val**          | Valor de datos mínimo, que se usa para calcular el escalado.
| **gx_line_chart_max_val**          | Valor de datos máximo, que se usa para calcular el escalado. |
| **gx_line_chart_data**             | Puntero a una matriz de valores enteros. Estos son los valores enteros trazados por el widget de gráfico de líneas. |
| **gx_line_<side>_margin**          | Desplazamiento desde el límite exterior de la ventana del gráfico hasta el área de representación del gráfico real. El eje del gráfico y la línea de datos siempre se trazan dentro de este límite interno, lo que permite que la aplicación dibuje etiquetas y otra información dentro de la ventana del gráfico, pero fuera del área de gráficos de caracteres. |
| **gx_line_chart_max_data_count**   | Número de valores de datos que pueden estar presentes. Este parámetro se usa para calcular el escalado o el intervalo del eje X para trazar los puntos de datos. |
| **gx_line_active_data_count**      | Número de valores de datos que se encuentran realmente en la matriz de datos. Un gráfico de líneas se puede escalar para que dibuje un máximo de 100 valores (por ejemplo), pero en alguna actualización en particular puede estar presente un número menor de valores de datos. |
| **gx_line_axis_line_width**        | Ancho de la línea que se usa para dibujar los ejes horizontal y vertical. |
| **gx_line_data_line_width**        | Ancho de la línea de datos trazada. |
| **gx_line_chart_axis_color**       | Identificador de recurso del color utilizado para dibujar las líneas de los ejes. |
| **gx_line_chart_line_color**       | Identificador de recurso del color utilizado para dibujar la línea de datos del gráfico. |

## <a name="gx_mouse_cursor_info"></a>GX_MOUSE_CURSOR_INFO 

### <a name="definition"></a>Definición

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a>Miembros

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_mouse_cursor_image_id**       | Identificador de recurso de la imagen del mouse. |
| **gx_mouse_cursor_hotspot_x**      | Desplazamiento desde la izquierda de la imagen del mouse hasta la zona activa de la imagen del mouse. |
| **gx_mouse_cursor_hotspot_y**      | Desplazamiento desde la parte superior de la imagen del mouse hasta la zona activa de la imagen del mouse. |

## <a name="gx_pen_configuration"></a>GX_PEN_CONFIGURATION 

### <a name="definition"></a>Definición

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a>Miembros

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_pen_configuration_min_drag_dist**       | Distancia mínima de arrastre por cada tic del temporizador de GUIX para desencadenar un evento FLICK. Llamar a GX_FIXED_VAL_MAKE para crear un valor de tipo de datos de punto fijo |
| **gx_pen_configuration_max_pen_speed_ticks** | Velocidad de arrastre máxima en tics del temporizador de GUIX para desencadenar un evento FLICK. | 

## <a name="gx_pixelmap_slider_info"></a>GX_PIXELMAP_SLIDER_INFO 

### <a name="definition"></a>Definición

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a>Miembros

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| **gx_pixelmap_slider_info_lower_background_pixelmap** | Identificador de recurso del mapa de píxeles para rellenar el fondo antes de la aguja. Si no se establece el mapa de píxeles de fondo superior, se usa para rellenar el fondo antes y después de la aguja. |
| **gx_pixelmap_slider_info_upper_background_pixelmap** | Identificador de recurso del mapa de píxeles para rellenar el fondo después de la aguja. |
| **gx_pixelmap_slider_info_needle_pixelmap**           | Identificador de recurso del mapa de píxeles de la aguja. |

## <a name="gx_progress_bar_info"></a>GX_PROGRESS_BAR_INFO 

### <a name="definition"></a>**Definición**

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

### <a name="members"></a>Miembros

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_progress_bar_info_min_val**             | Valor mínimo notificado. |
| **gx_progress_bar_info_max_val**             | Valor máximo notificado. |
| **gx_progress_bar_info_current_val**         | Valor actual |
| **gx_progress_bar_info_font_id**             | Identificador de recurso de la fuente, utilizado para dibujar el valor de texto opcional en el widget de la barra de progreso.      |
| **gx_progress_bar_normal_text_color**        | Identificador de recurso del color del texto en estado normal, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso. |
| **gx_progress_bar_selected_text_color**      | Identificador de recurso del color del texto cuando el widget tiene el foco, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso. |
| **gx_progress_bar_disabled_text_color**      | Identificador de recurso del color del texto cuando no está activo GX_STYLE_ENABLED, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso. |
| **gx_progress_bar_fill_pixelmap**            | Identificador de recurso del mapa de píxeles para el relleno del fondo.|

## <a name="gx_radial_progress_bar_info"></a>GX_RADIAL_PROGRESS_BAR_INFO

### <a name="definition"></a>Definición

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

### <a name="members"></a>Miembros

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| **gx_radial_progress_bar_info_xcenter**           | Posición del widget en la coordenada X. |
| **gx_radial_progress_bar_info_ycenter**           | Posición del widget en la coordenada Y.  |
| **gx_radial_progress_bar_info_radius**            | Radio del círculo de progreso. |
| **gx_radial_progress_bar_info_current_val**       | Valor actual, limitado al intervalo [-360, 360], indica la diferencia angular entre la posición del delimitador y el punto final del arco superior. Un valor negativo hace que el arco se dibuje en el sentido de las agujas del reloj a partir de la posición del delimitador. Un valor positivo hace que el arco se dibuje en sentido contrario a las agujas del reloj a partir de la posición del delimitador. La aplicación debe escalar el valor real que se indica para asignar un valor angular al widget de la barra de progreso. |
| **gx_radial_progress_bar_anchor_val**             | Ángulo inicial del arco de progreso superior. El valor se define en términos de grados enteros; 0 grados indica que apunta a la derecha y 90 grados indica que apunta hacia arriba. |
| **gx_radial_progress_bar_font_id**                | Identificador de recurso de la fuente, utilizado para dibujar el valor de texto opcional en el widget de la barra de progreso. |
| **gx_radial_progress_bar_normal_text_color**      | Identificador de recurso del color del texto en estado normal, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso. |
| **gx_radial_progress_bar_selected_text_color**    |Identificador de recurso del color del texto cuando el widget tiene el foco, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso. |
| **gx_radial_progress_bar_disabled_text_color**    | Identificador de recurso del color del texto cuando no está activo GX_STYLE_ENABLED, utilizado para definir el dibujo de texto opcional en el widget de la barra de progreso. |
| **gx_radial_progress_bar_normal_brush_width**     | Ancho del círculo de progreso inferior. |
| **gx_radial_progress_bar_selected_brush_width**   | Ancho del arco de progreso superior; el arco superior puede ser más estrecho, igual o más ancho que el círculo inferior. |
| **gx_radial_progress_bar_normal_brush_color**     | Identificador de recurso del color para rellenar el círculo de progreso inferior. |
| **gx_radial_progress_bar_selected_brush_color**   | Identificador de recurso del color para rellenar el arco de progreso superior. |

## <a name="gx_radial_slider_info"></a>GX_RADIAL_SLIDER_INFO 

### <a name="definition"></a>Definición

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

### <a name="members"></a>Miembros

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
**gx_radial_slider_info_xcenter**               | Distancia desde la izquierda del widget de control deslizante hasta el centro de rotación de la aguja del control deslizante. |
| **gx_radial_slider_info_ycenter**             | Distancia desde la parte superior del widget de control deslizante hasta el centro de rotación de la aguja del control deslizante. |
| **gx_radial_slider_info_radius**              | Radio del círculo del control deslizante radial. |
| **gx_radial_slider_info_track_width**         | Ancho de la pista del control deslizante radial. |
| **gx_radial_slider_info_current_angle**       | Ángulo del control deslizante actual. |
| **gx_radial_slider_info_min_angle**           | Ángulo mínimo del control deslizante. |
| **gx_radial_slider_info_max_angle**           | Ángulo máximo del control deslizante. |
| **gx_radial_slider_info_angle_list**          | Lista de valores de ángulo que define los ángulos del delimitador; si se establece, el ángulo del control deslizante solo puede ser uno de los ángulos del delimitador definidos. |
| **gx_radial_slider_info_list_count**          | Número de ángulos del delimitador. |
| **gx_radial_slider_info_background_pixelmap** | Identificador de recurso del mapa de píxeles del fondo. |
| **gx_radial_slider_info_needle_pixelmap**     | Identificador de recurso del mapa de píxeles de la aguja. |

## <a name="gx_rectangle"></a>GX_RECTANGLE

### <a name="definition"></a>Definición

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a>Miembros

|                                  |                         |
| -------------------------------- | ------------------------|
| **gx_rectangle_left**            | Izquierda del rectángulo.   |  
| **gx_rectangle_top**             | Parte superior del rectángulo.    | 
| **gx_rectangle_right**           | Derecha del rectángulo.  |
| **gx_rectangle_bottom**          | Parte inferior del rectángulo. |

## <a name="gx_rich_text_fonts"></a>GX_RICH_TEXT_FONTS 

### <a name="definition"></a>Definición

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a>Miembros

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_rich_text_fonts_normal_id**   | Identificador de recurso de la fuente de texto normal. |
| **gx_rich_text_fonts_bold_id**     | Identificador de recurso de la fuente de texto en negrita. |
| **gx_rich_text_fonts_italic_id**   | Identificador de recurso de la fuente de texto en cursiva. |
| **gx_rich_text_fonts_bold_italic_id** | Identificador de recurso de la fuente de texto en cursiva y negrita. |

## <a name="gx_scroll_info"></a>GX_SCROLL_INFO 
### <a name="definition"></a>**Definición**

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

### <a name="members"></a>Miembros

|                         |                               |
| ----------------------- | ----------------------------- |
| **gx_scroll_value**     | Posición de desplazamiento actual.       |
| **gx_scroll_minimum**   | Posición mínima notificada.     |
| **gx_scroll_maximum**   | Posición máxima notificada.     |
| **gx_scroll_visible**   | Intervalo visible de la ventana primaria.   |
| **gx_scroll_increment** | Valor delta mínimo de la barra de desplazamiento. |

## <a name="gx_scrollbar_appearance"></a>GX_SCROLLBAR_APPEARANCE 

### <a name="definition"></a>Definición

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

### <a name="members"></a>Miembros

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_scroll_width**                      | Ancho del widget de barra de desplazamiento en píxeles. |
| **gx_scroll_thumb_width**                | Ancho del botón de posición que se desliza en la barra de desplazamiento en píxeles. Normalmente, este valor es algunos píxeles menor que el ancho total de la barra de desplazamiento. |
| **gx_scroll_thumb_travel_min**           | Desplazamiento desde el final de la barra de desplazamiento hasta el punto mínimo del recorrido del botón de posición. Este límite se puede usar para impedir que el botón de posición se desplace hasta el final de la barra de desplazamiento. |
| **gx_scroll_thumb_travel_max**           | Desplazamiento desde el final de la barra de desplazamiento hasta el punto máximo del recorrido del botón de posición. Este límite se puede usar para impedir que el botón de posición se desplace hasta el final de la barra de desplazamiento. |
| **gx_scroll_thumb_border_style**         | Estilos de borde del botón de posición. |
| **gx_scroll_fill_pixelmap**              | Identificador del mapa de píxeles opcional. Si este identificador del mapa de píxeles no es cero, la barra de desplazamiento utiliza este del mapa de píxeles para dibujar el fondo de la barra de desplazamiento. |
| **gx_scroll_thumb_pixelmap**             | Identificador del mapa de píxeles opcional. Si este identificador del mapa de píxeles no es cero, el botón de posición de la barra de desplazamiento usa este del mapa de píxeles para dibujarse. |
| **gx_scroll_up_pixelmap**                | Identificador del mapa de píxeles opcional. Si este identificador del mapa de píxeles no es cero, la barra de desplazamiento usa este identificador del mapa de píxeles para dibujar el botón final de la barra de desplazamiento a la izquierda o hacia arriba. |
| **gx_scroll_down_pixelmap**              | Identificador del mapa de píxeles opcional. Si este identificador del mapa de píxeles no es cero, la barra de desplazamiento usa este identificador del mapa de píxeles para dibujar el botón final de la barra de desplazamiento a la derecha o hacia abajo. |
| **gx_scroll_thumb_color**                | Identificador de recurso del color utilizado para rellenar el botón de posición. |
| **gx_scroll_thumb_border_color**         | Identificador de recurso del color utilizado para dibujar el borde del botón de posición. | 
| **gx_scroll_button_color**               | Identificador de recurso del color utilizado para rellenar los botones finales de la barra de desplazamiento. |

## <a name="gx_slider_info"></a>GX_SLIDER_INFO

### <a name="definition"></a>Definición

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

### <a name="members"></a>Miembros

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| **gx_slider_info_min_val**              | Valor mínimo notificado. |
| **gx_slider_info_max_val**              | Valor máximo notificado. |
| **gx_slider_info_current_value**        | Valor actual |
| **gx_slider_info_min_travel**           | Límite del recorrido de la aguja. |
| **gx_slider_info_max_travel**           | Límite del recorrido de la aguja. |
| **gx_slider_info_needle_width**         | Ancho de la aguja en píxeles. |
| **gx_slider_info_needle_height**        | Alto de la aguja en píxeles. |
|**gx_slider_info_needle_inset**          | Posición de dibujo de la aguja. Si GX_STYLE_SLIDER_VERTICAL está establecido, se usa para especificar el desplazamiento desde la posición de inicio del dibujo de la aguja hasta la izquierda del control deslizante. En caso contrario, se usa para especificar el desplazamiento desde la posición de inicio del dibujo de la aguja hasta la parte superior del control deslizante. |
| **gx_slider_info_needle_hotspot_offset** | Desplazamiento de la zona activa de la aguja, se usa para especificar el desplazamiento desde la posición de inicio del dibujo de la aguja hasta la zona activa del control deslizante. |

## <a name="gx_sprite_frame"></a>GX_SPRITE_FRAME

### <a name="definition"></a>Definición

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

### <a name="members"></a>Miembros

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_sprite_frame_pixelmap**             | Identificador de recurso del mapa de píxeles que se va a mostrar para este fotograma. Este identificador puede ser 0. |
| **gx_sprite_frame_x_offset**             | Desplazamiento desde la izquierda del widget de sprite para mostrar el mapa de píxeles. |
| **gx_sprite_frame_y_offset**             | Desplazamiento desde la parte superior del widget de sprite para mostrar el mapa de píxeles. |
| **gx_sprite_frame_delay**                | Valor de retraso, en tics del temporizador de GUIX, después de mostrar este fotograma antes de avanzar al siguiente fotograma del sprite. |
| **gx_sprite_frame_background_operation** | Define cómo se debe borrar el fondo. Los valores posibles que admite este campo son los siguientes:<br />GX_SPRITE_BACKGROUND_NO_ACTION: sin relleno entre fotogramas.<br />GX_SPRITE_BACKGROUND_SOLID_FILL: volver a dibujar el fondo del sprite.<br />GX_SPRITE_BACKGROUND_RESTORE: restaurar el mapa de píxeles anterior. |
| **gx_sprite_frame_alpha**                | Valor alfa que se va a agregar al mapa de píxeles mostrado. El valor 255 especifica que no se debe imponer ningún valor alfa adicional. Si el mapa de píxeles incluye un canal alfa, este canal alfa se agregará al valor alfa del fotograma. |
