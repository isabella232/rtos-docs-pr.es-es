---
title: Recursos de GUIX Studio
description: GUIX Studio le proporciona la oportunidad de administrar todos los recursos de la interfaz de usuario que la aplicación usará para los colores, fuentes, mapas de píxeles y cadenas. En las secciones siguientes se describe cómo agregar, modificar y eliminar recursos en el diseño de la pantalla de la interfaz de usuario.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 7dd3485f112bce379ab7d6b11a808605bca191a0
ms.sourcegitcommit: 1d90854d1da01f4b65e54d732ee9190b57a531e1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/26/2021
ms.locfileid: "105569004"
---
# <a name="chapter-4-guix-studio-resources"></a>Capítulo 4: Recursos de GUIX Studio

GUIX Studio le proporciona la oportunidad de administrar todos los recursos de la interfaz de usuario que la aplicación usará para los colores, fuentes, mapas de píxeles y cadenas. En las secciones siguientes se describe cómo agregar, modificar y eliminar recursos en el diseño de la pantalla de la interfaz de usuario. 

Toda la administración de recursos se realiza dentro de la ***Vista de recursos** _ de la interfaz de usuario de GUIX Studio, tal como se muestra a continuación en la _*_Figura 8_**.

![Captura de pantalla de la Vista de recursos de GUIX Studio.](./media/guix-studio/image38.jpg)

**Figura 8**

## <a name="color-resources"></a>Recursos de color

La sección ***Colores** _ de la _*_Vista de recursos_*_ permite administrar los recursos de los colores. Puede expandir esta vista haciendo clic en el campo _ *+* * del encabezado de la vista, lo que da como resultado la vista que se muestra a continuación en la **_Figura 9_**:

![Captura de pantalla de la sección Colores de la Vista de recursos](./media/guix-studio/image_39.png)

**Figura 9**

Los recursos de los colores se componen de uno o varios colores, y cada uno tiene un nombre lógico único. Por ejemplo, en la **Figura 9**, el nombre lógico **CANVAS**, que es el id. de color del sistema para el color de relleno de fondo de la pantalla, está asociado al color físico negro. Este recurso de color se usa siempre que la aplicación especifica **GX_COLOR_ID_CANVAS** como color en las propiedades del objeto.

El Color de "muestra" indica que el valor RGB de color se muestra a la izquierda, seguido del nombre de id. del color. Puede cambiar el valor RGB asociado a cualquier nombre de id. en cualquier momento. No se pueden cambiar los nombres de los id. de color del sistema predefinidos porque la biblioteca GUIX los usa internamente. Sin embargo, puede cambiar cualquiera de los valores de color. Cambiar el valor de color del sistema es un **cambio global**. Esto significa que cualquier widget que no tenga una asignación de color específica tomará el nuevo valor de color del sistema.

Puede cambiar el nombre y el valor de los colores personalizados que haya agregado al tema.

Para modificar un recurso de color, haga doble clic (o haga clic con el botón derecho y seleccione el menú) en el recurso de color. Esta acción muestra el cuadro de diálogo de definición de colores. En este cuadro de diálogo se puede modificar el recurso de color para que coincida con las necesidades de la interfaz de usuario de la aplicación.En la  ***Figura 10** _ se muestra el cuadro de diálogo de modificación cuando se hace doble clic en _ *CANVAS**. La apariencia de este cuadro de diálogo cambiará en función de la configuración del formato de color de la pantalla de destino.

![Captura de pantalla del cuadro de diálogo Editar color.](./media/guix-studio/edit_color.png)

**Figura 10**

La apariencia del cuadro de diálogo Editar color cambiará en función de la configuración del formato y la profundidad del color de la pantalla actual.

Para agregar un nuevo recurso de color, vaya a la sección ***Colores** _ de la _ *_Vista de recursos_** y seleccione el botón siguiente:

![Botón "Agregar nuevo color"](./media/guix-studio/image41.jpg)

Use el cuadro de diálogo de color resultante para agregar un nuevo recurso de color, tal como se muestra a continuación en la **Figura 11**:*

![Captura de pantalla del nuevo color en el cuadro de diálogo Editar color.](./media/guix-studio/new_color.png)

**Figura 11**

Después de completar estos pasos, podrá seleccionar en la aplicación **Guardar** un nuevo recurso de color con el nombre **NEW_COLOR** que tenga el color físico verde.

**Consideraciones especiales al cambiar la configuración del formato de color de presentación:**

Al crear un nuevo proyecto, se le pedirá automáticamente que configure las pantallas de este y el formato de color de cada pantalla. Lo más frecuente es realizar estas selecciones una vez y que no necesite modificar esas opciones de configuración.

También puede determinar si es necesario cambiar la configuración del formato de color de la pantalla en otro momento. En ese caso, GUIX Studio hará una conversión mejor de los valores RGB de color del sistema y del usuario actuales, pasando del formato de color anterior al nuevo formato de color. Esta conversión sigue algunas reglas lógicas.

En el caso de los colores definidos por el usuario, GUIX Studio siempre intenta convertir el color anterior al color coincidente que sea más aproximado en el nuevo formato de color. Si va a convertir a partir de una profundidad de color alta, como el formato de color 16 BPP 5:6:5 a un formato de color monocromo o de escala grises, este cambio puede dar lugar a conversiones de color no deseadas. Al realizar un cambio grande en la configuración de la profundidad de color de la pantalla, es posible que necesite realizar algunas actualizaciones manuales de la nueva tabla de colores definida por el usuario.

En el caso de los colores predefinidos del sistema, GUIX Studio define internamente tres tablas de color predeterminadas y únicas. Una tabla de colores predeterminada se usa para todas las profundidades de color superiores a la escala de grises de 4-BPP, se usa una segunda tabla de colores predeterminada para los formatos de color de escala de grises (1 BPP < display_color_format <= 4bpp) y, por último, se usa una tercera tabla de colores de sistema predeterminada para el formato de color monocromo.

Al cambiar el formato del color de presentación mediante el cuadro de diálogo de configuración del proyecto, se aplican las siguientes reglas:

1) Si los formatos de color de pantalla antiguos y nuevos usan tablas de color del sistema predeterminadas, tal y como se definió anteriormente, todos los colores del sistema se restablecen a los colores predeterminados y predefinidos. En otras palabras, si cambia de color a la escala de grises, o desde la escala de grises a la profundidad de color monocromo, los colores del sistema se restablecerán a los valores predeterminados definidos internamente para la nueva profundidad de color. Aunque esto puede provocar la pérdida de información de colores personalizados, esta solución le ofrece un punto de partida razonable cuando realiza un cambio drástico en la configuración del formato de color de la pantalla.

2) Si los formatos de color antiguos y nuevos usan la misma tabla de colores predeterminada (esto significa que se está realizando un cambio de formato de color menos drástico), GUIX Studio probará cada color del sistema para determinar si se ha modificado el valor RGB de color del sistema de su valor predeterminado. Si se ha modificado el valor RGB de color del sistema, GUIX Studio realizará una conversión para encontrar la mejor coincidencia del formato de color anterior al aplicar el nuevo formato de color. Si el color del sistema no se ha modificado, se restablecerá el color predeterminado para el nuevo formato de color.

**Consideraciones especiales para la operación del modo de paleta:**

Cuando un proyecto se configura para el formato de color del modo de paleta de 256 colores, el usuario puede configurar la definición de la paleta que se va a instalar y utilizar. Puede obtener acceso y editar la definición de la paleta mediante el cuadro de diálogo Configuración|Temas y, si el proyecto está establecido para 8 BPP, debería ver el botón "Editar paleta". Haga clic en este botón para abrir el cuadro de diálogo Editar paleta:

![Captura de pantalla del cuadro de diálogo Editar paleta.](./media/guix-studio/edit_palette.png)

GUIX Studio divide la paleta en dos secciones: la sección "Definido por el usuario" y la sección "Generado automáticamente". GUIX Studio ejecuta un sofisticado algoritmo de generación de paletas que es óptimo para crear la mejor paleta que le permita mostrar las imágenes que se incluyen en cada tema. Puede dividir cualquier número de entradas de paleta que necesite definir; para ello, escriba un número en el campo "Entradas de paleta predefinidas" y escriba cualquier valor RGB que quiera usar en cualquiera de estas ranuras. Las ranuras restantes se asignarán a Studio para crear una paleta de colores óptima para mostrar las imágenes.

Cuando se ejecuta en este modo, si quiere editar un color definido en la vista de recursos, el editor de colores solo le permitirá seleccionar elementos en las entradas de paleta predefinidas que haya definido. Esto se debe a que GUIX Studio genera automáticamente las demás entradas de paleta y cambiará a medida que se modifiquen las imágenes agregadas al proyecto.

Si necesita que se muestren fuentes con suavizado de contorno cuando se ejecuta el modo de paleta de 8 BPP, debe definir una matriz de entradas de paleta que creen un degradado para cada color de primer plano o DE fondo que se use para mostrar el texto suavizado. Puede usar ocho entradas de paleta para el degradado de cada combinación de colores o 16 entradas de paleta para obtener un degradado más suave. Este número de entradas de paleta se determina mediante la casilla "Número de colores de texto con suavizado de contorno del modo de paleta" del cuadro de diálogo de Configuración del proyecto. Puede usar un degradado con solo ocho entradas para minimizar las entradas de paleta que se usan para cada combinación de colores, o bien usar 16 degradados de entrada para proporcionar la apariencia más suave del texto con suavizado de contorno.

Para simplificar la definición de un degradado de color para mostrar texto con suavizado de contorno o para generar un degradado de color para su propio uso, el cuadro de diálogo Editar paleta proporciona el botón Generar degradado. Para usar esta característica, primero debe asignar los valores r:g:b de los colores de degradado inicial y final.

Por ejemplo, si quiere mostrar texto de color rojo con suavizado de contorno en un fondo gris medio con ocho entradas de paleta a partir del índice 50, debe asignar el valor r:g:b de 255:0:0 al índice de paleta 50 y el valor r:g:b de 128:128:128 al índice de la paleta 57. Escriba estos valores de índice de paleta en los campos de inicio y fin del índice de este cuadro de diálogo y haga clic en el botón Generar degradado. Las entradas de paleta de 51 a 56 se inicializarán para definir una transición de degradado suave entre los colores de enlazado.

## <a name="font-resources"></a>Recursos de fuentes

Con el fin de administrar los recursos de fuente, la sección ***Fuentes** _ de la _*_Vista de recursos_*_ debe expandirse primero haciendo clic en el campo _ *+* *, lo que da como resultado el cuadro de diálogo que se muestra a continuación en la **_Figura 12_**:

![Captura de pantalla de la sección Fuentes en la Vista de recursos.](./media/guix-studio/image44.jpg)

**Figura 12**

Los recursos de la fuente se componen de una o varias fuentes, y cada una tiene un nombre lógico único. Por ejemplo, en la **Figura 12**, el nombre lógico **SYSTEM** está asociado a una fuente específica. Este recurso de fuente se usa siempre que la aplicación especifica el valor **SYSTEM** como la fuente en las propiedades del objeto. El grupo de fuentes muestra una vista previa WYSIWYG de los glifos de la fuente de la izquierda, el alto de la fuente en píxeles, el nombre del id. de fuente y el tamaño de fuente (en KB).

En la vista anterior, las cuatro primeras fuentes son las fuentes predeterminadas y predefinidas que requiere la biblioteca de GUIX. Puede cambiar los datos de fuente asociados a estas fuentes; sin embargo, no puede cambiar los nombres de id. de fuente.

La última fuente que se mostró anteriormente, denominada "Italic", es una fuente personalizada que el usuario ha agregado al proyecto.

Para modificar un recurso de fuente, haga doble clic (o haga clic con el botón derecho y seleccione el menú) en el recurso de fuente. En este cuadro de diálogo se puede modificar el recurso de fuente para que coincida con las necesidades de la interfaz de usuario de la aplicación.En la  ***Figura 13** _ se muestra el cuadro de diálogo de modificación cuando se hace doble clic en _ *SYSTEM**.

! [[Captura de pantalla del cuadro de diálogo de modificación cuando se hace doble clic en SYSTEM.](./media/guix-studio/edit_system_font.png)

**Figura 13**

Para agregar un nuevo recurso de fuente, vaya a la sección ***Fuentes** _ de la _ *_Vista de recursos_** y seleccione el botón siguiente:

![Botón Agregar nueva fuente](./media/guix-studio/image46.jpg)

Este botón invocará el cuadro de diálogo `Font Edit` para agregar un nuevo recurso de fuente, tal como se muestra a continuación en la ***Figura 14***:

![Captura de pantalla del cuadro de diálogo de modificación para agregar un nuevo recurso de fuente.](./media/guix-studio/add_new_font.png)

**Figura 14**

GUIX Studio crea nuevas fuentes de GUIX que representan una fuente TrueType que se ha solucionado con un tamaño determinado. Por lo tanto, el cuadro de diálogo anterior requiere una ruta de fuente TrueType. Puede usar el botón Examinar para buscar un directorio que contenga archivos de fuentes en el sistema de desarrollo. También se incluyen varias fuentes TrueType en la subcarpeta GUIX/fuentes, siempre que haya instalado GUIX Studio.

Si es posible, la ubicación del archivo de fuente TrueType se almacena internamente mediante una ruta de acceso relativa al proyecto. Por esta razón, es importante mantener todos los archivos de fuentes en una ubicación común y usar una estructura de árbol de directorios común para los proyectos y archivos de fuentes con el fin de permitirle trasladar proyectos de GUIX Studio de una estación de desarrollo a otra.

El campo Nombre de fuente permite especificar el nombre del id. de recurso de fuente. Este es el id. de recurso que se usará en el código que haya generado GUIX Studio y que también usa la aplicación al hacer referencia a la fuente. Este nombre debe seguir los requisitos de sintaxis de nomenclatura de variables de C.

Una vez que haya elegido un archivo de fuente TrueType para usarlo como entrada, escriba un nombre lógico de fuente.

La casilla "**Generar información de interletraje**" indica a GUIX Studio que debe incluir información de interletraje dentro de la fuente generada, que se usa para ajustar las posiciones relativas de los glifos sucesivos en una cadena. Si quiere aplicar el interletraje a las cadenas, debe usar una fuente que contenga información de interletraje y activar esta casilla. También necesitará definir la opción de compilación de la biblioteca de GUIX "GX_FONT_KERNING_SUPPORT" para admitir la representación de texto con información de interletraje.

La casilla "**Incluir juego de caracteres definido por la tabla de cadenas**" indica a GUIX Studio que debe incluir los glifos a los que hace referencia la tabla de cadenas estáticas dentro de la fuente generada. Puede incluir glifos adicionales seleccionando y editando los intervalos de caracteres que se enumeran a continuación, pero se puede seleccionar esta opción para generar rápidamente el juego de caracteres mínimo necesario para mostrar las cadenas definidas en la tabla de cadenas. Por supuesto, si la tabla de cadenas usa glifos que no están presentes en la fuente de origen TrueType, dichos caracteres no estarán disponibles en la fuente GUIX y no se mostrarán en el sistema de destino.

Para generar una fuente más completa, o una fuente que incluya caracteres que no se puedan usar en la tabla de cadenas definida estáticamente, también puede seleccionar intervalos de caracteres en la lista siguiente. Tenga en cuenta que puede seleccionar cualquier número de intervalos de caracteres y puede editar el código de carácter inicial y final real que se va a incluir en cada intervalo seleccionado.

Los intervalos de caracteres predefinidos y los nombres de página solo son sugerencias que permiten seleccionar fácilmente el juego de caracteres necesario para los idiomas activos que se usan hoy en día. Los nombres de idioma enumerados no tienen ningún efecto en la fuente GUIX generada y puede escribir cualquier intervalo de caracteres hexadecimales que quiera para cualquier intervalo de caracteres habilitado o seleccionado.

Por ejemplo, si quiere generar una fuente que solo contenga caracteres numéricos, puede seleccionar la página de códigos "ASCII", pero debe escribir el valor inicial 0030 y el valor final 0039 para generar una fuente que contenga solo los caracteres numéricos. Tenga en cuenta que los valores de intervalo de caracteres están codificados en hexadecimal, que es la notación normal de las tablas de caracteres Unicode.

De forma predeterminada, GUIX Studio y la biblioteca de GUIX admiten los códigos de carácter 0x0000 a 0xFFFF, que abarcan todos los idiomas activos, formatos matemáticos y otros símbolos que se usan hoy en día. Si necesita usar códigos de carácter por encima del valor 0xFFFF, incluidas ciertas áreas de uso privado, deberá activar la casilla "Admitir el intervalo de caracteres extendidos". Cuando esta casilla está seleccionada, GUIX Studio permite al usuario especificar intervalos de caracteres de 0x0000 a 0x10ffff, que incluye los intervalos de caracteres de uso privado de Unicode. Si necesita este intervalo de caracteres extendidos, también tendrá que definir la opción de compilación de la biblioteca de GUIX "GX_EXTENDED_UNICODE_SUPPORT" para que la biblioteca de GUIX admita internamente códigos de caracteres de 32 bits, en lugar de la configuración predeterminada que admite códigos de caracteres de 16 bits.

Si selecciona la casilla "Incluir juego de caracteres definido por la tabla de cadenas" y uno o varios de los intervalos de caracteres de la lista siguiente, GUIX Studio combinará estas selecciones en el supraconjunto de los intervalos seleccionados y los caracteres que se usan en la tabla de cadenas. Por supuesto, la fuente de origen TrueType seleccionada también debe contener los caracteres necesarios para que GUIX Studio genere glifos significativos para cada valor de carácter solicitado.

Una vez determinado el intervalo de caracteres, especifique el alto de la fuente en píxeles y el formato de esta. Se admiten tanto fuentes con suavizado de contorno como binarias. Las fuentes binarias requieren menos espacio de almacenamiento de datos estático; sin embargo, las fuentes con suavizado de contorno proporcionan el mejor aspecto en los destinos que se ejecutan con una profundidad de color de 4 BPP o mayor.

>[!NOTE]  
> *El "alto de fuente" hace referencia al cuadrado EM de la fuente. En el tipo de metal tradicional, el cuadrado EM era igual a la altura de línea del cuerpo de metal desde el que surgía cada letra, y cada cuerpo de metal tenía el mismo tamaño. En el tipo metal, el tamaño físico de una letra no podía superar normalmente el cuadrado EM. En el tipo digital, EM es una cuadrícula de resolución arbitraria que se utiliza como espacio de diseño de una fuente digital. Para estas fuentes digitales es habitual que algunas características del glifo, como los acentos y los descensos, se extiendan más allá de los límites del cuadrado EM. El resultado final es que la altura de widget necesaria para mostrar por completo una fuente determinada, a menudo debe ser ligeramente mayor que la altura de píxel de la fuente solicitada.*

Una vez completados todos los campos de configuración de fuente, haga clic en el botón Aceptar para crear un nuevo recurso de fuente. GUIX Studio generará una fuente compatible con GUIX con las propiedades elegidas, agregará esa fuente a los recursos del proyecto y hará que la fuente esté disponible para que la use la aplicación.

## <a name="pixel-map-resources"></a>Recursos del mapa de píxeles

Con el fin de administrar los recursos del mapa de píxeles, la sección ***Mapa de píxeles** _ de la _*_Vista de recursos_*_ debe expandirse primero haciendo clic en el campo _ *+* *, lo que da como resultado el cuadro de diálogo que se muestra a continuación en la **_Figura 15_**:

Cuando se expande el grupo `Pixelmap`, debería ver una vista previa similar a la siguiente:

![Captura de pantalla de la sección Mapas de píxeles en la Vista de recursos.](./media/guix-studio/pixelmap_view.png)

**Figura 15**

Los recursos del mapa de píxeles se componen de uno o varios mapas de píxeles, cada uno de ellos con una vista previa de la imagen del mapa de píxeles a la izquierda, las dimensiones del mapa en píxeles, un nombre lógico único y el tamaño de almacenamiento del mapa de píxeles en el archivo de recursos de salida (en KB).

El primer grupo de mapas de píxeles incluye las asignaciones de píxeles del sistema predefinidas y que necesitan los widgets de GUIX, como los botones de radio y las casillas. Puede cambiar los datos del mapa de píxeles que están asociados a las asignaciones de píxeles del sistema; sin embargo, no puede cambiar estos nombres de id. de mapa de píxeles. También se muestra una serie de mapas de píxeles personalizados con nombres como "BACKGROUND" y "BUTTON_ACTIVE". Estos son ejemplos de mapas de píxeles que un usuario ha agregado al proyecto y que se pueden usar para representar un widget de GX_PIXELMAP_BUTTON.

Dado que muchos proyectos contienen un gran número de mapas de píxeles, la vista de mapa de píxeles permite definir cualquier número de carpetas de mapas de píxeles para organizar las imágenes del mapa de píxeles. 

Para agregar una nueva carpeta de mapas de píxeles, haga clic con el botón derecho en el encabezado de la sección `Pixelmaps` de la ***Vista de recursos*** y seleccione "Agregar carpeta".

Para modificar un recurso de mapa de píxeles, haga doble clic (o haga clic con el botón derecho y seleccione el menú) en el recurso de mapa de píxeles. En este cuadro de diálogo se puede modificar el recurso del mapa de píxeles para que coincida con las necesidades de la interfaz de usuario de la aplicación.En la  ***Figura 16** _ se muestra el cuadro de diálogo de modificación cuando se hace doble clic en _ *RADIO_ON**.

![Captura de pantalla del cuadro de diálogo Editar mapa de píxeles.](./media/guix-studio/image49.jpg)

**Figura 16**

El cuadro de diálogo `Edit Pixelmap` permite definir un nuevo mapa de píxeles o modificar el contenido de un mapa de píxeles existente. En segundo plano, GUIX Studio lee la imagen de entrada y la convierte al formato `GUIX GX_PIXELMAP` que puede usar la biblioteca de GUIX. Asimismo, GUIX Studio también convierte el espacio de colores de la imagen entrante en el espacio de colores de la pantalla en la que se utilizará este mapa de píxeles.

El primer campo de este cuadro de diálogo es la ruta de acceso a la imagen de origen. GUIX Studio admite la entrada de archivos de imagen con formato PNG (. png) o JPEG (. jpg). Puede usar el botón "examinar" para buscar el archivo de entrada que quiera usar en el sistema de archivos local.

Si es posible, la ubicación del archivo de fuente TrueType se almacena internamente mediante una ruta de acceso relativa al proyecto. Por esta razón, es importante mantener todos los archivos de imágenes en una ubicación común y usar una estructura de árbol de directorios común para los proyectos y archivos de imágenes con el fin de permitirle trasladar proyectos de GUIX Studio de una estación de desarrollo a otra y no perder los datos de la imagen de entrada.

Los campos `Pixelmap ID` permiten especificar el nombre lógico del recurso de mapa de píxeles. Este nombre se escribe aquí, debe ser único y debe seguir las reglas de sintaxis de nomenclatura de variables de C.

La casilla Especificar el archivo de salida le permite especificar un archivo de salida único para cada mapa de píxeles. Si no se selecciona esta casilla, los datos del mapa de píxeles se escriben en el archivo de recursos predeterminado de esta pantalla. Si la casilla está activada, puede escribir un nombre de archivo específico en el que se escribirán los datos de este mapa de píxeles. El objetivo de esta opción es permitir la división de los datos del mapa de píxeles (que pueden ser matrices de C muy grandes), en varios archivos de salida. Algunos compiladores luchan por controlar archivos de C que forman cientos de miles de líneas de código fuente.

La casilla "Comprimir salida" le permite especificar si la salida del mapa de píxeles usa un algoritmo de compresión de GUIX de su propiedad. Los archivos de salida comprimidos suelen ser más pequeños, pero también requieren tiempo del procesador para representarse en el destino. Lo más frecuente es elegir la compresión para los mapas de píxeles de gran tamaño y usar el formato no comprimido para las asignaciones de píxeles más pequeñas.

La casilla `Include Alpha Channel` determina la manera en que GUIX Studio emplea a veces la información del canal alfa presente en los archivos de entrada con formato. png. Si esta casilla está activada y la pantalla se está ejecutando con una profundidad de color de 16 BPP o superior, GUIX Studio conservará los todos los datos alfa entrantes en el archivo de salida. Si esta casilla no está activada, GUIX producirá un archivo de salida ligeramente más pequeño. Este archivo de salida puede incluir transparencia, pero no incluirá información completa de la combinación alfa.

La casilla `Dither` indica a GUIX Studio que debe aplicar un algoritmo de interpolación avanzada al convertir la imagen de entrada para usarla con una pantalla de profundidad de color inferior. Normalmente, la interpolación está habilitada, pero tenga en cuenta que puede producir archivos de salida más grandes si se usa la compresión, ya que habrá menos píxeles repetidos.

Una vez que todas las opciones estén establecidas según lo previsto, haga clic en el botón Aceptar para generar un nuevo recurso de mapa de píxeles. GUIX Studio leerá el archivo de imagen de entrada, lo descomprimirá, realizará la conversión del espacio de colores y la interpolación, y, opcionalmente, volverá a comprimir los datos y los guardará en un formato `GX_PIXELMAP` que sea compatible con GUIX. El nuevo mapa de píxeles se agrega a los recursos del proyecto y se pone a disposición de la aplicación para que lo use.

Para agregar un nuevo recurso de mapa de píxeles, vaya a la sección *`Pixelmaps` de la ***Vista de recursos*** y seleccione el botón siguiente:

![Agregue nuevo botón de mapa de píxeles.](./media/guix-studio/image50.jpg)

**Edición de mapas de píxeles por lotes**

Para modificar las propiedades de un grupo de mapas de píxeles, haga clic con el botón derecho en el grupo o la carpeta de mapas de píxeles y seleccione **Editar mapas de píxeles** en el menú para invocar el cuadro de diálogo **Editar mapas de píxeles**.

![Captura de pantalla del cuadro de diálogo Editar mapas de píxeles.](./media/guix-studio/batch_pixelmap_edit.jpg)

Descripción del estado de la casilla:

![Botón activado.](./media/guix-studio/checkbox_checked.jpg)
Este estado significa que todos los mapas de píxeles tienen activada la propiedad; puede desactivar el botón para cambiar la propiedad de todos los mapas de píxeles.

![Botón desactivado.](./media/guix-studio/checkbox_unchecked.jpg)
Este estado significa que todos los mapas de píxeles tienen activada la propiedad; puede activar el botón para cambiar la propiedad de todos los mapas de píxeles.

![Botón sin determinar.](./media/guix-studio/checkbox_undetermined.jpg)
Este estado significa que los mapas de píxeles tienen un estado diferente para la propiedad. Puede activar o desactivar el botón para cambiar la propiedad de todos los mapas de píxeles; de lo contrario, la propiedad permanece sin cambios.


## <a name="string-resources"></a>Recursos de cadena

Cuando se expande el grupo de cadenas, verá una vista previa de la tabla de cadenas del proyecto, tal como se muestra a continuación:

![Captura de pantalla del grupo de cadenas expandidas.](./media/guix-studio/string_res_view.png)

**Figura 17**

Los recursos de cadena se componen de una o varias cadenas, y cada una tiene un nombre lógico único. Por ejemplo, en la **Figura 17**, el nombre lógico "PATIENT_LIST" está asociado a la cadena "Patient List" que se muestra a su derecha. Este recurso de cadena se usa siempre que la aplicación especifica PATIENT_LIST como la cadena en las propiedades del objeto.

Recuerde siempre que los nombres de los id. de todos los tipos de recursos deben ser nombres de variable compatibles con la sintaxis de C. Estos nombres se utilizarán de manera general cuando los archivos de recursos del proyecto y los archivos de especificaciones se generan en Studio.

Para modificar un recurso de cadena, haga doble clic (o haga clic con el botón derecho y seleccione el menú) en el recurso de cadena para invocar el cuadro de diálogo ***Editor de la tabla de cadenas** _. En el cuadro de diálogo _*_Editor de la tabla de cadenas_*_, el recurso de cadena se puede modificar para que coincida con las necesidades de la interfaz de usuario de la aplicación. En la _*_Figura 18_*_ se muestra el cuadro de diálogo de modificación cuando se hace doble clic en _ *STRING_13**.

En este caso, el nombre del id. de cadena se muestra a la izquierda, que es el contenido de la cadena del primer idioma o del idioma de referencia que se muestra a la derecha. Por supuesto, el contenido exacto de la cadena es muy específico para la aplicación, pero el diseño de la vista previa del grupo de cadenas es coherente.

GUIX Studio admite aplicaciones de texto estático y multilingües mediante la definición y el mantenimiento de una tabla de cadenas. La tabla de cadenas define un id. de cadena para cada registro y una constante de cadena para cada registro de cada idioma admitido.

Los idiomas que admite la aplicación se definen mediante el cuadro de diálogo Configuración de idioma que se muestra aquí:

![Captura de pantalla del cuadro de diálogo Configuración de idioma.](./media/guix-studio/config_languages.png)

**Figura 18**

El cuadro de diálogo de Configuración de idioma se invoca mediante el comando Configuración | Idiomas en el menú de la aplicación. Este cuadro de diálogo permite definir el número de idiomas que debe admitir la aplicación y el nombre o el id. de idioma que se va a asociar a cada idioma. Los idiomas admitidos se pueden modificar una vez creado el proyecto; sin embargo, si se quita un idioma, debe tener en cuenta que los datos de cadena asociados a ese idioma también se quitarán y no se pueden recuperar.

La casilla "**Definido estáticamente**" indica que el idioma seleccionado se definirá estáticamente en formato de código fuente del archivo de recursos generado. Si no se define ningún idioma de forma estática, el puntero de la tabla de idioma se establecerá en NULL en la tabla de visualización generada, y la aplicación debe cargar e instalar un idioma mediante las API del cargador de recursos binario que proporciona la biblioteca de GUIX.

La casilla "**Admitir el texto bidireccional**" indica a GUIX Studio que habilite la compatibilidad de representación de texto bidireccional. Debe activar esta casilla si las cadenas que va a especificar para este idioma requieren la representación de texto bidireccional.

La casilla "**Generar texto bidireccional en el orden de visualización**" indica a GUIX Studio que genere texto bidireccional en el archivo de salida en su orden de visualización. Si se selecciona esta opción, no se requiere realizar ningún procesamiento en tiempo de ejecución en la biblioteca de GUIX para representar correctamente el texto bidireccional. Cuando se selecciona esta opción, NO se debe habilitar la representación de texto bidireccional en la biblioteca de GUIX. Esta configuración produce el mejor rendimiento en tiempo de ejecución, pero no admite la representación de cadenas de texto bidireccional definidas dinámicamente.

El primer idioma o el idioma del "Índice 1" se conoce como "idioma de referencia". Este es el idioma que GUIX Studio usará al definir y editar el diseño de la interfaz de usuario. Todos los demás idiomas de la tabla de cadenas se conocen como idiomas de traducción. GUIX Studio admite la exportación e importación de los datos de la tabla de cadenas en los archivos de datos con formato XLIFF o CSV estándar del sector, lo que resulta cómodo para intercambiar información de cadenas con traductores que podrían ayudar al desarrollador de la aplicación a agregar traducciones para los idiomas que se admiten, aparte del idioma de referencia. Al exportar la tabla de cadenas GUIX a un archivo XLIFF o CSV, el idioma de referencia, junto con un idioma de traducción, se incluye en el archivo de intercambio de datos de cadena XLIFF o CSV. Del mismo modo, cuando se importa un archivo XLIFF o CSV, los datos importados se usan para rellenar un idioma de traducción en la tabla de cadenas GUIX.

![Captura de pantalla del editor de la tabla de cadenas.](./media/guix-studio/image53.jpg)

**Figura 19**

En primer lugar, el cuadro de diálogo del Editor de la tabla de cadenas muestra una lista de id. de cadena a la izquierda, seguida de los datos de la cadena del idioma de referencia. Si se define más de un idioma, en una tercera columna se muestra cualquiera de los idiomas de traducción admitidos. Para abrir y cerrar la tercera columna, haga clic en la flecha pequeña situada en la parte superior derecha de la columna del idioma de referencia.

Cuando la columna del idioma de traducción esté visible, puede recorrer los idiomas de traducción contenidos en el proyecto; para ello, haga clic en las flechas pequeñas situadas en la parte superior derecha de la columna del idioma de traducción de la lista de cadenas.

Asimismo, puede editar un registro de cadenas; para ello, haga clic en el registro de la tabla para seleccionarlo. Cuando se selecciona un registro, el id. de la cadena de registro y el contenido de esta se muestran en los campos situados debajo de la vista de tabla. Puede escribir nuevos valores en estos campos para modificar el id. de cadena y el contenido de esta.

El cuadro del lado derecho de la vista de tabla muestra las vistas previas de los widgets que hacen referencia a la cadena seleccionada. Esto resulta útil para saber si una cadena editada superará un área específica del widget.

Los campos a la derecha del contenido de la cadena incluyen los siguientes elementos:

- "Número de referencias": este campo indica con qué frecuencia se usa un id. de cadena determinado en el proyecto de GUIX Studio. Si el recuento de referencias es 0, esta cadena puede estar obsoleta y el usuario puede quitarla de forma opcional.
- El Ancho de cadena (píxeles) indica el ancho de la visualización de la cadena con la fuente indicada.
- El campo "Notas" es un campo opcional de comentarios que le permite agregar información sobre el propósito o el uso de cada cadena. Estas notas se incluyen en los archivos XLIFF de datos de cadena exportados para que los traductores puedan crear traducciones de cadenas precisas y significativas.

Siempre que tenga abierto el cuadro de diálogo ***Editor de la tabla de cadenas***, puede agregar cadenas adicionales al proyecto; para ello, haga clic en el botón Agregar cadena situado en la parte superior del cuadro de diálogo. Las cadenas obsoletas o que no se usan se pueden quitar del proyecto; solo debe seleccionarlas primero y hacer clic en el botón Eliminar cadena que está en la parte superior del cuadro de diálogo.

Además de agregar manualmente nuevas cadenas al proyecto mediante el cuadro de diálogo Editor de la tabla de cadenas, también puede agregar cadenas nuevas de forma indirecta; para ello, escriba el contenido de la cadena en el campo de texto de la vista de propiedades de cualquier widget que admita texto. En otras palabras, cuando se agregan nuevos widgets en la vista de destino o cuando escribe información de texto en la vista Propiedades, estas acciones crean automáticamente entradas nuevas en la tabla de cadenas del proyecto.

## <a name="adding-language-translations"></a>Adición de traducciones de idioma

El editor de tablas de cadenas de GUIX Studio admite un flujo de trabajo para la definición de idiomas que permite al desarrollador crear una aplicación con su idioma principal y, a continuación, exportar los datos de cadena a un archivo XML o CSV de un esquema estándar para enviarlos a un experto en traducción de idiomas. A continuación, el archivo de traducción se devuelve al desarrollador, que puede volver a importar las traducciones de los idiomas en su proyecto de Studio, lo que agrega compatibilidad con un nuevo idioma a su aplicación.

Esta opción se invoca mediante el uso de los botones Exportar (para escribir los datos de cadena en un archivo) e Importar (para leer las cadenas traducidas) en la parte superior del Editor de la tabla de cadenas. El botón Exportar se usa para crear un archivo XML o CSV del esquema XLIFF que contiene las cadenas del idioma de referencia. Un traductor puede usar este archivo mediante herramientas y editores que admitan el formato de archivo XLIFF o CSV estándar.

Cuando un experto en traducción devuelve el archivo XLIFF con las nuevas traducciones de las cadenas, puede usar el botón Importar para leer los datos del archivo XLIFF o CSV. Si el archivo XLIFF o CSV contiene un nuevo idioma, este se agregará al proyecto. Si el archivo XLIFF contiene nuevos datos de cadena para un idioma existente, estos nuevos datos se importarán en el proyecto. Las cadenas del idioma de referencia no se modifican mediante la operación de importación.

Al hacer clic en el botón Exportar, se muestra el cuadro de diálogo del control de exportación XLIFF/CSV; este se muestra a continuación:

![Captura de pantalla del cuadro de diálogo del control de exportación XLIFF/CSV.](./media/guix-studio/image54.jpg)

**Figura 20**

Los campos Idioma de origen e Idioma de destino especifican qué columnas de la tabla de cadenas se escribirán en el archivo XLIFF o CSV, como el idioma de referencia y el idioma de traducción. El idioma de origen cuenta con las cadenas de referencia y el idioma de destino es el idioma que el traductor usará para proporcionar los datos de la cadena traducida.

El campo de versión XLIFF especifica una de las dos versiones principales del formato de archivo XLIFF, ya sea la versión 1.2 o la versión 2.0 (y versiones posteriores). Estos estándares de formato de archivo XLIFF son incompatibles y debe saber qué versión usan las herramientas antes de usar los comandos de exportación e importación de XLIFF. Puede encontrar más información sobre el esquema XLIFF y los estándares de XLIFF aquí:

- Versión 1.2: [https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html](https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html)
- Versión 2.0: [https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0os.pdf](https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0-os.pdf)

Los campos del nombre de archivo y la ruta de acceso de salida permiten especificar el nombre del archivo y la ubicación en la que se escribirá el archivo de salida. El nombre de archivo depende totalmente del usuario, pero se recomienda usar nombres que indiquen los idiomas de origen y de destino contenidos en el archivo exportado.
