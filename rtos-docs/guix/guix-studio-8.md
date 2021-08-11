---
title: Notas sobre la edición de tipos de widgets específicos
description: Comentarios detallados que describen los métodos de edición para determinados tipos de widgets complejos.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 374471df85c4cd0fffae5b5cc7ad31d2237877f2
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178289"
---
# <a name="chapter-8-notes-on-editing-specific-widget-types"></a>Capítulo 8: Notas sobre la edición de tipos de widgets específicos

GUIX Studio permite al usuario crear y modificar fácilmente widgets de GUIX que compondrán las pantallas de la interfaz de usuario de la aplicación. La mayoría de estos métodos de edición son intuitivos y obvios. Por ejemplo, si desea cambiar el tamaño de un widget, selecciónelo con el mouse y arrastre los bordes. También puede escribir directamente en los campos de propiedades izquierda/superior/ancho/alto del widget seleccionado.

Algunos tipos de widget requieren un proceso de edición más avanzado, porque la compatibilidad de las características de estos widgets es un poco más compleja.

En este capítulo se proporcionan notas sobre las características de edición más avanzadas para estos tipos de widget más complejos. Estas notas se ampliarán a medida que las características de GUIX Studio avancen junto con los tipos de widgets que se proporcionan en la biblioteca de GUIX.

## <a name="rich-text-view"></a>Vista de texto enriquecido

Este widget se usa para mostrar texto enriquecido que admite códigos de formato de texto alineado. Estos códigos de formato incluyen negrita, cursiva, entre varios otros. Para empezar, haga clic con el botón derecho en el elemento primario seleccionado de la *Vista de proyecto* o la *Vista de destino* y seleccione el menú **Insert/Text/Rich Text View** (Insertar/Texto/Vista de texto enriquecido) para insertar un widget de vista de texto enriquecido.

Además del conjunto estándar de propiedades que admiten todos los tipos de widget, el tipo de widget de vista de texto enriquecido es compatible con otras propiedades.

### <a name="additional-properties"></a>Propiedades adicionales

| Propiedad | Significado |
|----------|---------|
| Alineación del texto | Alineación predeterminada del texto. |
| Fuente normal| Fuente de predeterminada del texto. |
| Fuente en negrita  | Fuente de texto para el texto etiquetado como negrita. |
| Fuente en cursiva| Fuente de texto para el texto etiquetado como cursiva.|
| Fuente en negrita y cursiva| Fuente de texto para el texto etiquetado como negrita y cursiva. |
| Copia privada del texto | Se debe comprobar si el widget mantiene su propia copia privada de cualquier texto asignado. |
| Espacio en blanco | Ancho del margen entre el widget y el texto mostrado, en píxeles. |
| Espacio entre líneas | Espacio entre dos líneas del texto, en píxeles. |
|||

### <a name="the-rich-text-formatting-codes"></a>Códigos de formato de texto enriquecido

Los códigos de formato siguientes se admiten para el formato de texto.

|Etiqueta|Significado|
|---|---|
|\<b>\</b> | Permite representar la fuente de texto con el id. de fuente en negrita especificado por el usuario.|
|\<i>\</i> | Permite representar la fuente de texto con el id. de fuente en cursiva especificado por el usuario.|
|\<u>\</u> | Permite representar texto subrayado.|
|\<f GX_FONT_ID>\</f> | Permite representar texto con el id. de fuente especificado. |
|\<c GX_COLOR_ID>\</c> | Permite representar texto con el id. de color especificado.|
|\<hc GX_COLOR_ID>\</hc> | Permite representar texto con el id. de color de fondo especificado.|
|\<align left/right/center>\</align> | Permite asignar la alineación del texto.|
|||

Hay dos maneras de editar la cadena de texto enriquecido desde GUIX Studio:

- Utilice el cuadro de diálogo Editar texto enriquecido, que es el método de edición recomendado y más sencillo.
- Utilice el cuadro de diálogo Editor de la tabla de cadenas, que le permite insertar manualmente las etiquetas de formato que se muestran en la tabla anterior.

Después de seleccionar un widget de vista de texto enriquecido en la *Vista de destino*, seleccione el botón **Editar texto enriquecido** en la *Vista de propiedades* para invocar al cuadro de diálogo para editar el texto enriquecido, tal como se muestra en la figura 8.1.

![Captura de pantalla del cuadro de diálogo Editar texto enriquecido de GUIX Studio.](./media/guix-studio/edit_rich_text_dialog.png)

**Figura 8.1**

El panel izquierdo es el campo de edición de texto enriquecido. Puede usar los iconos de la barra de herramientas para insertar las etiquetas que necesite. Seleccione cualquier bloque de texto en el campo de edición y, luego, seleccione los botones de la barra de herramientas para aplicar los estilos y colores necesarios al bloque de texto seleccionado. El cuadro de diálogo Editar texto enriquecido es una forma sencilla de insertar los códigos de formato en la cadena de prueba. También puede insertar estas etiquetas de manera manual o incluso generarlas en tiempo de ejecución, si es necesario.

El panel derecho es la vista previa del widget para mostrar cómo se representa el texto en la vista de destino. El color de fondo de la vista previa del widget es fijo, lo que quizás no coincide con el color de fondo asignado del widget en la vista de destino.

Los nombres de los id. de recursos se usan en texto enriquecido para hacer referencia a recursos de fuente o de color específicos. Si se cambia el nombre de un recurso de una fuente o un color después de que la cadena de texto enriquecido haya hecho referencia a él, GUIX Studio actualizará automáticamente la cadena de texto enriquecido para que refleje los cambios de nombre del recurso. Por otro lado, si elimina un recurso de fuente o de color al que hace referencia un widget de texto enriquecido, debe modificar manualmente el texto enriquecido afectado para quitar o cambiar los nombres de los id. de recurso que se eliminaron.

Al seleccionar el botón Guardar en este cuadro de diálogo, la cadena de texto enriquecido que definió se agrega a la tabla de cadenas del proyecto.

## <a name="string-scroll-wheel"></a>Rueda de desplazamiento de cadenas

Un widget de desplazamiento de cadenas admite la visualización de una matriz de cadenas. Estas cadenas se pueden asignar de manera dinámica o, en caso de que la aplicación admita varios idiomas, las cadenas asignadas se pueden extraer de la tabla de cadenas activa.

El widget de rueda de desplazamiento de cadenas admite una matriz de cadenas. El cuadro de diálogo de edición de la rueda de desplazamiento de cadenas, que se muestra en la figura 8.2, se proporciona para permitir que el usuario asigne esta matriz de cadenas.

![Captura de pantalla del cuadro de diálogo de edición de la rueda de desplazamiento de cadenas de GUIX Studio.](./media/guix-studio/string_scroll_wheel_edit.png)

**Figura 8.2**

Para invocar este cuadro de diálogo, seleccione un widget de rueda de desplazamiento de cadenas en la *Vista de destino* o la *Vista de proyecto*. Una vez que se selecciona este tipo de widget, la *Vista de propiedades* incluirá el botón **Editar cadenas**. Seleccione este botón para invocar el cuadro de diálogo de edición de la rueda de desplazamiento de cadenas.

Para asignar una cadena a cada índice de texto, puede seleccionar un id. de cadena en la lista desplegable, o bien puede escribir un valor de cadena nuevo en el campo de texto de la derecha. Cuando termine de hacer los cambios, las cadenas nuevas o modificadas se guardan en la tabla de cadenas activa.

## <a name="sprite"></a>Sprite

Se usa un widget de sprite para mostrar una secuencia de imágenes que proporcionará un efecto de animación. Un widget de sprite requiere una lista de fotogramas, que es una matriz de identificadores de imagen y parámetros únicos que se aplican a cada imagen del fotograma. Para crear esta lista de fotogramas para el widget de sprite, se proporciona el cuadro de diálogo para editar fotogramas de sprite, que se muestra en la figura 8.3:

![Captura de pantalla del cuadro de diálogo para editar fotogramas de sprite de GUIX Studio.](./media/guix-studio/edit_sprite_frames.png)

**Figura 8.3**

Para invocar este cuadro de diálogo, seleccione un widget de sprite en la *vista de destino* o la *vista de proyecto*. Una vez que se selecciona este tipo de widget, la *Vista de propiedades* incluirá el botón **Editar lista de fotogramas**. Seleccione este botón para invocar el cuadro de diálogo de edición de la rueda de desplazamiento de cadenas.

El campo *Número total de fotogramas de Sprite* es un campo de entrada que permite escribir el número entero total de fotogramas que mostrará el widget de sprite. Las imágenes se pueden reutilizar en la lista de fotogramas, lo que significa que no todas las imágenes deben ser únicas.

El campo de id. de fotograma de sprite es un valor de selección de índice de fotograma que va de 1 al número total de fotogramas. Aumente y disminuya este valor para pasar de un fotograma de sprite al siguiente.

Cada fotograma de sprite tiene varios parámetros. El primero es la operación en segundo plano. Este campo imita las funcionalidades del popular formato de animación GIF. Las opciones aquí incluyen las siguientes:

- Ninguna operación, que significa que la imagen del fotograma actual se dibuja sobre la imagen del fotograma anterior.
- Restaurar primer mapa de píxeles, que significa que el mapa de píxeles del índice 1 se dibuja antes del mapa de píxeles actual.
- Relleno de color sólido, que significa que el fondo del sprite se rellena con el color de fondo del sprite antes de que se dibuje el fotograma actual.

El campo Id. de mapa de píxeles permite seleccionar cualquier mapa de píxeles previamente agregado a los recursos del proyecto. Se puede usar el mismo identificador de mapa de píxeles para varios fotogramas. Por ejemplo, la animación de sprite puede utilizar el movimiento de la imagen (mediante los campos de desplazamiento x e y) en lugar de usar imágenes de sprites diferentes (o además de usar imágenes de sprites diferentes).

El campo Valor alfa se aplica a todo el dibujo del mapa de píxeles. Este campo solo tiene efecto cuando se ejecuta con una profundidad de color de 8 bpp y superior. El valor alfa 0 es totalmente transparente y el valor alfa 255 es opaco.

Se puede especificar un desplazamiento dentro del fotograma de sprite en el que se dibujará el mapa de píxeles actual con los campos de desplazamiento X e Y del fotograma. En otras palabras, no es necesario que cada imagen dibujada sea del tamaño completo del widget de sprite.

El período de retraso especifica el tiempo de retraso antes de pasar al fotograma de sprite siguiente. Este valor se expresa en tics y, para la configuración predeterminada del temporizador de GUIX/THREADX, cada tic representa 50 ms.

Cuando cambie los cambios en el cuadro de diálogo para editar fotogramas de sprite, GUIX Studio podrá generar toda la matriz de lista de fotogramas como parte de la generación de archivos de especificaciones de salida.

### <a name="assign-a-sprite-widget-with-gif-resource"></a>Asignación de un widget de sprites con un recurso GIF
Puede agregar un recurso GIF al grupo de recursos **Pixelmap** y asignar dicho recurso directamente al widget de sprites. Una vez establecido el recurso GIF, se generará automáticamente una lista de fotogramas; puede editar aún más cada fotograma de la lista mediante el cuadro de diálogo de edición de sprites:

![Captura de pantalla del cuadro de diálogo para editar fotogramas de sprite de GUIX Studio para un recurso GIF.](./media/guix-studio/edit_sprite_gif_frames.jpg)

**Figura 8.4**