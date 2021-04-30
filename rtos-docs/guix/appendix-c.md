---
title: 'Apéndice C: Estilos de widget de GUIX'
description: Obtenga información sobre los estilos de widget de GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 83d5c5167739e91b7af8fce6b04213f610984fc6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815573"
---
# <a name="appendix-c---guix-widget-styles"></a>Apéndice C: Estilos de widget de GUIX

__***Estilos generales (usados con la mayoría de los tipos de widget):***__

**GX_STYLE_BORDER_NONE**
  - Valor: 0x00000000
  - Descripción: use este estilo para dibujar un widget sin borde.

**GX_STYLE_BORDER_RAISED**
  - Valor: 0x00000001
  - Descripción: dibuje un widget con un borde elevado.

**GX_STYLE_BORDER_RECESSED**
  - Valor: 0x00000002
  - Descripción: dibuje un widget con un borde empotrado.

**GX_STYLE_BORDER_THIN**
  - Valor: 0x00000004
  - Descripción: dibuje un borde con un ancho de un píxel.

**GX_STYLE_BORDER_THICK** 
  - Valor: 0x00000008
  - Descripción: dibuje un widget con un borde grueso.

**GX_STYLE_BORDER_MASK**
  - Valor: 0x0000000f
  - Descripción: valor de máscara que se usa para probar solo los campos de estilo del miembro de estilo del widget.

**GX_STYLE_TRANSPARENT**
  - Valor: 0x10000000
  - Descripción: cree un widget que sea al menos parcialmente transparente. Este estilo se debe usar cuando un widget no se dibuja totalmente opaco, incluidos los widgets que dibujan un mapa de píxeles semitransparente como fondo. Esta marca de estilo informa a GUIX de que se debe dibujar el elemento primario del widget para actualizar su área de fondo.

**GX_STYLE_DRAW_SELECTED**
  - Valor: 0x20000000
  - Descripción: especifique que el widget se debe dibujar con las fuentes y los colores de estado seleccionados. La forma de usar el estilo DRAW_SELECTED para indicar que el widget está seleccionado varía en función del tipo de widget.

**GX_STYLE_ENABLED**
  - Valor: 0x40000000
  - Descripción: marque el widget como habilitado para que este pueda aceptar eventos de entrada de usuario y generar señales de salida.
  
**GX_STYLE_DYNAMICALLY_ALLOCATED**
  - Valor: 0x80000000
  - Descripción: indica que la memoria del bloque de control del widget se asigna dinámicamente mediante el servicio gx_system_memory_allocator cuando se crea el widget. La memoria se libera si se destruye el widget.

**GX_STYLE_USE_LOCAL_ALPHA**
  - Valor: 0x01000000
  - Descripción: indica a las funciones de dibujo de GUIX que usen el valor alfa del widget local al dibujar el widget. La lógica interna de GUIX suele usar esta marca para implementar animaciones de difuminado del widget.


__***Estilos de alineación de texto (estilos aplicados a todos los widgets que dibujan texto):***__

**GX_STYLE_TEXT_LEFT**
  - Valor: 0x00001000
  - Descripción: el texto se dibuja alineado a la izquierda en el área cliente del widget.

**GX_STYLE_TEXT_RIGHT** 
  - Valor: 0x00002000
  - Descripción: el texto se dibuja alineado a la derecha en el área cliente del widget.

**GX_STYLE_TEXT_CENTER**
  - Valor: 0x00004000
  - Descripción: el texto se dibuja centrado en el área cliente del widget.

**GX_STYLE_TEXT_COPY**
  - Valor: 0x00008000
  - Descripción: de forma predeterminada, los widgets que dibujan texto conservan solo un puntero al texto que pasa la aplicación. En el caso de texto definido de forma estática que se especifique en la tabla de cadenas, no hay ningún motivo por el que el widget deba hacer una copia privada del texto asignado. Sin embargo, si el texto asignado a un widget se crea de forma dinámica con funciones como sprint() o gx_utility_ltoa, a menudo resulta conveniente indicar al widget que mantenga su propia copia privada de cualquier texto asignado. De este modo, la aplicación puede usar variables automáticas o temporales al definir la cadena de texto en aquellos casos en los que, de lo contrario, tendría que especificar matrices de caracteres definidas estáticamente para cada widget de texto que use texto definido dinámicamente. Cuando se establezca esta marca de estilo, el widget utilizará la función gx_system_memory_allocator con el fin de asignar dinámicamente el bloque de memoria necesario para contener una copia privada de la cadena asignada. Por lo tanto, el uso de esta marca de estilo se basa en la aplicación que define las funciones memory_allocator y memory_deallocator. GX_STYLE_TEXT_COPY no debe borrarse una vez que se haya establecido, ya que, de lo contrario, los resultados serán imprevisibles.

__***Estilos de botón (solo se aplican a los tipos de widget de botón de GUIX):***__

**GX_STYLE_BUTTON_PUSHED**
  - Valor: 0x00000010
  - Descripción: indica que el botón está presionado o seleccionado.

**GX_STYLE_BUTTON_TOGGLE**
  - Valor: 0x00000020
  - Descripción: el botón se presionará o dejará de estar presionado con cada evento de clic. Este estilo se suele usar con botones de tipo "casilla de verificación".

**GX_STYLE_BUTTON_RADIO**
  - Valor: 0x00000040
  - Descripción: este estilo indica que el botón será exclusivo y anulará la selección de cualquier botón del mismo nivel cuando esté seleccionado. Este estilo se suele usar con botones de tipo "botón de selección".

**GX_STYLE_BUTTON_EVENT_ON_PUSH**
  - Valor: 0x00000080
  - Descripción: indica que el botón genera un evento de clic cuando se presiona por primera vez. La operación predeterminada es generar un evento de clic cuando se libera el botón.

**GX_STYLE_BUTTON_REPEAT**
  - Valor: 0x00000100
  - Descripción: indica que el botón debe enviar eventos de clic repetidos al botón primario cuando aquel se mantiene presionado.

__***Estilos de lista (solo se aplican a los tipos de widget de lista de GUIX):***__

**GX_STYLE_CENTER_SELECTED** 
  - Valor: 0x00000010
  - Descripción: reservado.

**GX_STYLE_WRAP**
  - Valor: 0x00000020
  - Descripción: los elementos secundarios de la lista se ajustan de principio a fin al arrastrar la lista o desplazarse más allá del índice de inicio o finalización de esta.

**GX_STYLE_FLICKABLE**
  - Valor: 0x00000040
  - Descripción: reservado.

__***Estilos de botón de mapa de píxeles e icono:***__

**GX_STYLE_HALIGN_CENTER**
  - Valor: 0x00010000
  - Descripción: el mapa de píxeles debe estar centrado dentro del límite del botón en el eje horizontal.

**GX_STYLE_HALIGN_LEFT**
  - Valor: 0x00020000
  - Descripción: el mapa de píxeles debe estar alineado a la izquierda dentro del límite del botón en el eje horizontal.

**GX_STYLE_HALIGN_RIGHT**
  - Valor: 0x00040000
  - Descripción: el mapa de píxeles debe estar alineado a la derecha dentro del límite del botón en el eje horizontal.

**GX_STYLE_VALIGN_CENTER**
  - Valor: 0x00080000
  - Descripción: el mapa de píxeles debe estar centrado dentro del límite del botón en el eje vertical.

**GX_STYLE_VALIGN_TOP**
  - Valor: 0x00100000
  - Descripción: el mapa de píxeles debe estar alineado a la parte superior dentro del límite del botón en el eje vertical.

**GX_STYLE_VALIGN_BOTTOM**
  - Valor: 0x00200000
  - Descripción: el mapa de píxeles debe estar alineado a la parte inferior dentro del límite del botón en el eje horizontal.

__***Estilos de control deslizante (solo se aplican a los tipos de widget derivados y GX_SLIDER):***__

**GX_STYLE_SHOW_NEEDLE**
  - Valor: 0x00000200
  - Descripción: este estilo debe estar incluido para que el control deslizante dibuje el indicador de aguja. Este estilo se puede deshabilitar si la aplicación quiere deshabilitar la aguja del control deslizante o dibujar un indicador de aguja personalizado.

**GX_STYLE_SHOW_TICKMARKS**
  - Valor: 0x00000400
  - Descripción: cuando este estilo está habilitado, el widget de control deslizante dibuja mediante software las líneas discontinuas de marca de graduación.

**GX_STYLE_SLIDER_VERTICAL**
  - Valor: 0x00000800
  - Descripción: establezca esta marca de estilo para crear un control deslizante vertical o bórrela para crear uno horizontal.

__***Estilos de sprite (solo se aplican a los tipos de widget GX_SPRITE):***__

**GX_STYLE_SPRITE_AUTO**
  - Valor: 0x00000010
  - Descripción: indica que la animación de sprite se ejecutará automáticamente cuando el widget de sprite haya recibido el evento GX_EVENT_SHOW.

**GX_STYLE_SPRITE_LOOP**
  - Valor: 0x00000020
  - Descripción: con este estilo, el widget de sprite recorrerá continuamente en bucle los fotogramas de animación de sprite hasta que la aplicación detenga el sprite.

__***Estilos de control deslizante de mapa de píxeles:***__

**GX_STYLE_TILE_BACKGROUND**
  - Valor: 0x00001000
  - Descripción: la imagen de fondo del control deslizante se coloca en mosaico para rellenar el rectángulo delimitador del sprite. De este modo, se puede usar una pequeña imagen de franjas verticales u horizontales para rellenar el fondo del control deslizante.

__***Otros estilos de barra de progreso:***__

**GX_STYLE_PROGRESS_PERCENT**
  - Valor: 0x00000010
  - Descripción: cuando se establece este estilo, la barra de progreso dibuja su valor como porcentaje, no como valor sin formato. El texto se centra en el rectángulo delimitador de la barra de progreso.

**GX_STYLE_PROGRESS_TEXT_DRAW**
  - Valor: 0x00000020
  - Descripción: dibuje el valor de la barra de progreso actual como texto decimal centrado en la barra.

**GX_STYLE_PROGRESS_VERTICAL**
  - Valor: 0x0000040
  - Descripción: indica que el progreso está orientado verticalmente. La orientación es horizontal de manera predeterminada.

**GX_STYLE_PROGRESS_SEGMENT_FILL**:
  - **Valor**: 0x00000100
  - Descripción: el valor de la barra de progreso se indica mediante rectángulos rellenos segmentados, no mediante un relleno sólido.

__***Otros estilos de barra de progreso radial:***__

**GX_STYLE_RADIAL_PROGRESS_ALIAS**
  - Valor: 0x00000200
  - Descripción: dibuje la barra de progreso radial con estilos de pincel suavizados. Para ello, hace falta más ancho de banda de CPU, pero el resultado es también una apariencia más agradable. En el caso de destinos de CPU de menor rendimiento, si se borra esta marca de estilo, el resultado será una velocidad de dibujo mayor.

**GX_STYLE_RADIAL_PROGRESS_ROUND**
  - Valor: 0x00000400
  - Descripción: use un estilo de pincel de extremo de línea redondo al dibujar el arco de la barra de progreso radial. El extremo de línea es cuadrado de manera predeterminada.

__***Otros estilos de entrada de texto:***__

**GX_STYLE_CURSOR_BLINK**
  - Valor: 0x00000040
  - Descripción: el cursor del widget de entrada de texto parpadeará en lugar de permanecer estable.

**GX_STYLE_CURSOR_ALWAYS**
  - Valor: 0x00000080
  - Descripción. Normalmente, el cursor del widget de entrada de texto solo se muestra cuando el widget tiene el foco de entrada. Esta marca de estilo hará que el cursor esté siempre visible independientemente del foco de entrada.

**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**
  - Valor: 0x00000100
  - Descripción: use esta marca de estilo para establecer el evento GX_EVENT_TEXT_EDITED cada vez que el widget de entrada de texto reciba el evento de presión de tecla.

__***Otros estilos de ventana:***__

**GX_STYLE_TILE_WALLPAPER**
  - Valor: 0x00040000
  - Descripción: la ventana colocará en mosaico cualquier imagen de fondo de pantalla asignada para rellenar el rectángulo cliente de la ventana.

**GX_STYLE_AUTO_HSCROLL**
  - Valor: 0x00100000
  - Descripción: reservado para su uso futuro.

**GX_STYLE_AUTO_VSCROLL**
  - Valor: 0x00200000
  - Descripción: reservado para su uso futuro.

__***Otros estilos de menú:***__

**GX_STYLE_MENU_EXPANDED**
  - Valor: 0x00000010
  - Descripción: el widget de menú de acordeón está inicialmente expandido.

__***Otros estilos de vista de árbol:***__

**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**
  - Valor: 0x00000010
  - Descripción: el widget de vista de árbol debe dibujar líneas desde el icono de nodo hasta el nodo raíz del árbol.

__***Otros estilos de barra de desplazamiento:***__

**GX_SCROLLBAR_BACKGROUND_TILE**
  - Valor: 0x00010000
  - Descripción: reservado para su uso futuro.

**GX_SCROLLBAR_RELATIVE_THUMB**
  - Valor: 0x00020000
  - Descripción: el ancho (en el caso de una barra de desplazamiento horizontal) o el alto (en el caso de una barra de desplazamiento vertical) del control de la barra de desplazamiento se calculan en función de la relación entre el área visible de la ventana primaria y el intervalo mínimo y máximo de la barra.

**GX_SCROLLBAR_END_BUTTONS**
  - Valor: 0x00040000
  - Descripción: la barra de desplazamiento crea y agrega automáticamente botones en cada extremo de la región de la barra.

**GX_SCROLLBAR_VERTICAL** 
  - Valor: 0x01000000
  - Descripción: la barra de desplazamiento está orientada verticalmente.

**GX_SCROLLBAR_HORIZONTAL**
  - Valor: 0x02000000
  - Descripción: la barra de desplazamiento está orientada horizontalmente.

__***Estilos de rueda de desplazamiento de texto:***__

**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**
  - Valor: 0x00000200
  - Descripción: la rueda de desplazamiento usa un algoritmo sinusoidal para que parezca que tiene una forma redondeada. Esta marca de estilo puede suponer una sobrecarga considerable para el rendimiento del widget de rueda de desplazamiento, pero también puede dar a la rueda una apariencia 3D realista.