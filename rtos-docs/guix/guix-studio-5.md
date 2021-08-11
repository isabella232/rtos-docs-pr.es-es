---
title: Diseñador de pantallas de GUIX Studio
description: El propósito principal de GUIX Studio es diseñar pantallas de aplicación.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 91377a663dfb605caa33ab019f437f2c3ed1adc7
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178313"
---
# <a name="chapter-5-guix-studio-screen-designer"></a>Capítulo 5: Diseñador de pantallas de GUIX Studio

El propósito principal de GUIX Studio es diseñar pantallas de aplicación. El diseño de la pantalla se logra a través de las diversas vistas descritas anteriormente en el capítulo 3. Sin embargo, el elemento principal del diseño de pantalla en GUIX Studio es la ***vista de destino***, que es donde todos los elementos de pantalla se muestran visualmente y exactamente de la misma manera en que aparecen en la pantalla de destino insertada. Estos elementos de pantalla pueden seleccionarse, moverse, cambiar de tamaño, etc. a través de operaciones sencillas del mouse y el botón. Además, las operaciones de los botones de alineación y de orden Z están disponibles en los objetos seleccionados en la vista de destino. En las siguientes subsecciones se describen varias características del diseño de pantalla de GUIX Studio. 

## <a name="creatingconfiguring-projects"></a>Crear o configurar proyectos

La creación de proyectos en GUIX Studio es sencilla, simplemente seleccione el botón ***Nuevo proyecto** o el proyecto de selección de menú _*_Proyecto, Nuevo proyecto_*_. A continuación, GUIX Studio presenta el cuadro de diálogo *_Configurar proyecto_**. En este cuadro de diálogo, se especifica la configuración de pantalla básica, así como la información de la ruta de acceso donde se encuentra el código generado por GUIX Studio.

Cuando se crea un nuevo proyecto, se muestra el cuadro de diálogo Configurar proyecto. Aquí es donde el desarrollador especifica el número de pantallas de hardware disponibles en el destino y las propiedades que se muestran. Las propiedades incluyen el nombre lógico de la pantalla, la resolución x/y, la profundidad de color y el formato, y otras propiedades de presentación. GUIX Studio admite varias pantallas en el mismo proyecto. Si se necesitan pantallas adicionales, el campo ***Número de pantallas** debe cambiarse para que coincida con el número de pantallas en el dispositivo insertado. El número máximo de pantallas de un proyecto es 4. La *_Figura 21_** muestra el cuadro de diálogo Configurar proyecto.

La modificación del proyecto o la configuración de pantalla se realiza mediante la opción de menú ***Configurar, Proyecto o Mostrar** o seleccionando el proyecto o la pantalla, haciendo clic con el botón derecho y seleccionando _*_Configurar, Proyecto o Mostrar_*_. En cualquier caso, se muestra el cuadro de diálogo *_Configurar proyecto_** para facilitar los cambios en la configuración del proyecto o mostrar.

![Captura de pantalla del cuadro de diálogo Configurar proyecto.](./media/guix-studio/config_project.png)

**Figura 21**

En el grupo Directorios se pueden especificar los directorios de salida predeterminados para los archivos de código fuente y de encabezado de C generados por Studio. Normalmente, estos directorios se guardan en relación con la ubicación del proyecto para facilitar el traslado de los proyectos de un equipo a otro o de un sistema de archivos a otro.

El campo Encabezados adicionales es donde puede especificar archivos de encabezado personalizados. Si se necesita más de un archivo de encabezado, use puntos y comas para delimitar la lista.

Al invocar los comandos de Studio "Generar aplicación" o "Generar recursos", estos son los directorios predeterminados en los que se escribirán los archivos de código fuente. Por supuesto, puede invalidar estas ubicaciones de directorio en cualquier momento si escribe nuevas ubicaciones en el cuadro de diálogo directorio de salida.

## <a name="selecting-widgets"></a>Selección de widgets

La selección de widgets se realiza haciendo clic en el widget en el árbol de widgets ***Vista de proyecto** o haciendo clic en el widget visible en el área de _*_Vista de destino_*_. Cuando se selecciona un solo widget, sus propiedades se muestran en el área de _*_Vista de propiedades_*_. En la _*_figura 22_*_ se muestra el widget "_ *_Botón_* *" seleccionado.

![Captura de pantalla del widget seleccionado.](./media/guix-studio/select_button.png)

**Figura 22**

## <a name="using-properties"></a>Utilizar propiedades

Como se mencionó anteriormente, las propiedades de un widget seleccionado se presentan en la ***Vista de propiedades**. Todos los widgets tienen un conjunto común de propiedades, así como algunas propiedades que son específicas del tipo de widget determinado. Por ejemplo, un widget de botón tiene una propiedad *_Insertada_** mientras que un widget de ventana no. A continuación se muestran el conjunto común de propiedades de widget:

| Propiedad         | Significado                                                                               |
| ---------------- | ------------------------------------------------------------------------------------- |
| Tipo de widget    | Tipo de widget, como referencia                                                                               |
| Nombre del widget      | Nombre del widget, que se pasa a la función de creación del widget y que se usa para la nomenclatura de variables en los archivos de código fuente generados.               |
| Id. del widget        | Id. del widget. Este valor de id. se usa para generar señales de widgets secundarios en sus pantallas primarias.                            |
| Left             | Coordenada del widget situada más a la izquierda                                                                                                 |
| Superior              | Coordenada superior del widget                                                                                                  |
| Ancho            | Ancho del widget en píxeles                                                                                                      |
| Alto           | Alto del widget en píxeles                                                                                                     |
| Borde           | Tipo de borde del widget                                                                                                          |
| Transparente      | Se debe comprobar si el widget es parcialmente transparente                                                                       |
| Dibujo seleccionado    | Se debe comprobar si el widget debe dibujarse inicialmente en el estado seleccionado.                                            |
| Habilitar           | Debe comprobarse si el usuario final puede seleccionar el widget o hacer clic en él.                                                    |
| Acepta Focus    | Se debe comprobar si el widget acepta Focus.                                                                                 |
| Asignación en runtime | Se debe comprobar si el bloque de control del widget se debe asignar dinámicamente.                                                 |
| Relleno normal      | Id. de recurso de color de relleno normal                                                                                                  |
| Relleno seleccionado    | Id. de recurso de color de relleno seleccionado                                                                                                |
| Función de dibujo    | Nombre de la función de dibujo personalizada definida por el usuario. Si este campo está en blanco, se usa la función de dibujo estándar para ese tipo de widget. |
| Función de evento   | Nombre de la función de control de eventos personalizada definida por el usuario. Si está en blanco, se usa el control de eventos estándar para este tipo de widget.          |

En la ***Figura 23*** se muestran las propiedades de un widget de ventana simple.

![Captura de pantalla de las propiedades de un widget de ventana simple.](./media/guix-studio/image57.jpg)

**Figura 23**

Muchos tipos de widget tienen propiedades adicionales específicas de cada tipo de widget.

Por ejemplo, en la Figura 23 anterior, el tipo de widget de ventana admite un identificador de PixelMap de papel tapiz y un valor de estilo que indica si el papel tapiz debe centrarse o colocarse en mosaico.

Los widgets de texto admiten un campo de id. de cadena, junto con los estilos de alineación de texto y una especificación de fuente. Las propiedades adicionales del widget son normalmente muy intuitivas una vez que haya leído la descripción de cada tipo de widget y los estilos disponibles y los parámetros de función Crear para ese tipo de widget.

## <a name="manipulating-widgets"></a>Manipulación de Widgets

Para manipular un widget, primero se debe seleccionar. Para ello, haga clic directamente en el widget en la ***Vista de destino** o selecciónelo en el árbol del widget de la *_Vista de proyecto_*. Una vez seleccionado, el widget tendrá un contorno discontinuo. En este estado, se puede mover simplemente haciendo clic en el widget y arrastrándolo a la ubicación deseada en su primario. Si el widget es de nivel superior, al arrastralo se establece eficazmente la posición inicial de este en la pantalla de destino. Por supuesto, siempre es posible migrar o cambiar el tamaño de cualquier widget en cualquier momento mediante la API de GUIX.

Para cambiar el alto del widget, coloque el mouse en el borde superior del widget y espere a que el puntero del mouse cambie a una flecha hacia abajo. En este momento, se puede cambiar el alto del widget simplemente moviendo el mouse mientras se presiona el botón secundario del mouse. Se puede cambiar el tamaño del ancho del mouse de manera similar colocando el puntero del mouse en el borde izquierdo del widget.En la  ***figura 24** se muestra el widget "_ *_Botón_* *" cuyo tamaño se ha cambiado y se ha pasado al área izquierda o superior de la ventana primaria.

![Captura de pantalla del widget de botón.](./media/guix-studio/resize_button.png)

**Figura 24**

## <a name="manipulating-multiple-widgets"></a>Manipular varios widgets

La selección de varios widgets se logra haciendo clic en varios widgets en la vista de destino mientras mantiene presionada la tecla ***Ctrl***. Al hacerlo, se mostrará cada uno de los widgets seleccionados con un contorno discontinuo. Tenga en cuenta que al seleccionar varios widgets, cada widget del grupo de selección debe ser un elemento secundario del mismo elemento primario.

Una vez que se seleccionan varios widgets, se pueden mover simultáneamente haciendo clic dentro de uno en los widgets seleccionados y moviendo el mouse con el botón derecho del mouse presionado. Además, los botones de alineación de la ***Barra de herramientas** se pueden usar para alinear el grupo de widgets seleccionados. La _*_figura 25_*_ muestra ambos widgets seleccionados "_*_botón_*_" y "_*_botón nuevo_*_" , y la _*_Figura 26_*_ muestra el resultado de la selección del botón *_Alinear a la izquierda_* * mientras se seleccionan estos widgets.

![Captura de pantalla del botón y los widgets de botón nuevos seleccionados](./media/guix-studio/multiple_select.png)

**Figura 25**

![Captura de pantalla del resultado de la selección del botón de alinear a la izquierda.](./media/guix-studio/align_left.png)

**Figura 26**

## <a name="cutcopypaste-operations"></a>Operaciones de cortar, copiar y pegar

Un widget seleccionado en la ***Vista de destino** se puede cortar, copiar y pegar en modo estándar. Los widgets y las pantallas se pueden copiar en un proyecto o copiarse de un proyecto y pegarse en otro. La _*_Barra de herramientas_*_ tiene botones para cortar, copiar y pegar. También hay las mismas opciones en la opción de menú Edición. Tenga en cuenta que al pegar un widget, debe seleccionarse el widget primario antes de pegar el nuevo widget. En la _*_figura 27_*_ se muestra el resultado de seleccionar el widget "_ *_Botón_**", copiarlo y pegar la copia en la misma ventana.

![Captura de pantalla de las operaciones de cortar, copiar y pegar.](./media/guix-studio/copy_paste_button.png)

**Figura 27**

Copiar y pegar dentro de un proyecto suele ser sencillo, ya que los recursos que podrían necesitar los widgets copiados siempre están presentes cuando se trabaja en un proyecto. Sin embargo, si copia un widget del proyecto A y lo pega en el proyecto B, pueden surgir algunos problemas con las dependencias de recursos.

Al copiar widgets en Studio, la aplicación de Studio crea una lista de los recursos que necesitan los widgets copiados y genera una tabla de dependencias de recursos portable en forma de XML que se copia en el portapapeles de Windows, junto con la información del widget copiado real. Al pegar los widgets en un proyecto diferente, Studio examina primero la lista de dependencias de recursos y agrega los recursos necesarios al proyecto abierto si aún no existen. Studio identifica los recursos coincidentes por los nombres de identificador de recurso y, para los recursos de cadena, Studio también compara el contenido de la cadena. Si se encuentran recursos coincidentes, Studio actualiza los identificadores de recursos de los widgets pegados para usar correctamente los recursos del nuevo proyecto. Si no se encuentran los recursos, se agregan.

Cuando Studio agrega un recurso al proyecto como parte de una operación de pegado de widget, Studio está agregando realmente un vínculo al recurso en el caso de los recursos de fuente y PixelMap. Este vínculo se genera desde el proyecto de origen y recibirá mensajes de advertencia si esos recursos no se encuentran en relación con la ubicación del proyecto en el que va a pegar. Los vínculos de recursos se agregarán al proyecto independientemente de, pero es posible que tenga que copiar manualmente las fuentes y los archivos de imagen en las ubicaciones adecuadas del nuevo árbol del proyecto para eliminar los errores de carga de recursos. Studio no copia archivos .ttf, .png o .jpg de una ubicación a otra.

La forma más sencilla de evitar cualquier problema en este sentido es mantener una estructura de directorios coherente entre los proyectos que desea compartir. Si desea trasladar las cosas del proyecto a al proyecto B fácilmente, mantenga las imágenes de gráficos y las fuentes utilizadas por ambos proyectos en un subdirectorio coherente de cada carpeta del proyecto.

## <a name="changing-z-order"></a>Cambiar el orden Z

Los widgets se pueden colocar fácilmente delante o detrás de otros widgets. Esto se consigue seleccionando el widget y seleccionando los botones ***Ir al principio** o _*_Ir a atrás_*_ en la _*_Barra de herramientas_*_. _ *_Figura 28_** muestra el movimiento del segundo botón hacia atrás.

![Captura de pantalla del orden z del botón.](./media/guix-studio/change_z_order.png)

**Figura 28**

## <a name="assigning-colors-fonts-and-pixelmaps"></a>Asignar colores, fuentes y PixelMap

Además de seleccionar colores, fuentes y PixelMap en la vista de propiedades de un widget seleccionado, también se admite un método abreviado de arrastrar y colocar para asignar recursos a los widgets. Para usar esta característica, simplemente haga clic con el botón izquierdo en un recurso, como un color de fuente en la vista de recursos, y arrastre el recurso sobre el widget deseado en la vista de destino. Coloque el recurso soltando el botón primario del mouse sobre el widget.

Los recursos de color siempre se asignan al color de fondo normal del widget cuando se usa el método de arrastrar y colocar. Otros colores, como el color seleccionado o el color del texto seleccionado, deben asignarse mediante la vista Propiedades.

Del mismo modo, los recursos de PixelMap se asignan al campo de PixelMap "normal" o "Relleno" de un widget que admite la visualización PixelMap. Para asignar otros campos a un widget que admita varios PixelMap, debe usar la vista Propiedades.

## <a name="using-templates"></a>Uso de plantillas

Cualquier pantalla o colección de widgets secundarios que diseñe en Studio se puede usar como plantilla para nuevas pantallas y nuevos controles secundarios. Puede basar una plantilla en un widget de tipo ventana, que es el caso de uso normal, o en cualquier otro tipo de widget. El uso de una plantilla es similar a copiar y pegar un widget, excepto que cualquier elemento derivado de una plantilla se modifica automáticamente cuando se modifica la plantilla en la que se basa. No se permite modificar las propiedades del widget de plantilla cuando se trabaja con una pantalla derivada o una instancia heredada de la plantilla. Sin embargo, al modificar las propiedades de la plantilla de cualquier modo, todas las instancias que hacen referencia a esa plantilla se actualizan automáticamente, ya que se derivan de esa plantilla.

Otra ventaja de usar plantillas para elementos repetidos es que el archivo de especificaciones generadas por Studio normalmente tendrá un tamaño menor que si se repiten los elementos repetidos cada vez que se usan.

Para designar que se va a usar una pantalla o una colección de widgets secundarios como plantilla, active la casilla "Plantilla" en la vista de propiedades del widget. Una vez activada la casilla "Plantilla", el widget de plantilla aparecerá en el menú desplegable ***Insertar|Plantilla***.

Como ejemplo del uso de una plantilla, puede definir una ventana que se use como barra de botones. Esta ventana puede contener varios botones secundarios y esta barra de botones se usa con frecuencia en varias pantallas. Puede definir una pequeña ventana independiente dentro del proyecto de Studio que contiene los botones secundarios necesarios y asignarle el nombre "button_bar". A continuación, seleccione esta ventana y active la propiedad "plantilla". A continuación, seleccione una pantalla en la que desee agregar esta barra de botones. Use el comando de menú Insertar|Plantilla|button_bar para insertar una instancia de la ventana de button_bar en la pantalla. Tenga en cuenta que puede cambiar la posición de la barra de botones, pero no tiene permiso para cambiar la mayoría de las propiedades. Sin embargo, puede usar el widget button_bar (y cualquier elemento secundario) igual que cualquier otro tipo de widget GUIX predefinido. Para modificar el button_bar, debe seleccionar la plantilla de button_bar para realizar los cambios.

Otro ejemplo de uso típico de una plantilla es una aplicación que incluye muchas pantallas similares. Por ejemplo, la aplicación puede tener 10 pantallas diferentes que comparten una barra de título común, el color de relleno, el tamaño, etc. En este caso, podría definir una pantalla de plantilla que incluya los widgets secundarios de la barra de título y configure el tamaño de la pantalla, el color de relleno y otras propiedades. Una vez definida esta pantalla de plantilla, puede derivar las 10 pantallas diferentes de esta plantilla. Cuando se usa el comando de menú Insertar|Plantilla|\<base_screen>, la pantalla se iniciará con todos los widgets y valores secundarios de la pantalla de la plantilla. Tenga en cuenta que cada pantalla que se deriva de la pantalla de la plantilla no es una copia de la plantilla, sino que es realmente una instancia derivada de la pantalla de la plantilla. Después, puede personalizar cada pantalla derivada para que contenga todo el contenido adicional que se necesite.

Tenga en cuenta que, además de guardar el tamaño del archivo de especificaciones generadas, el uso de plantillas puede facilitar la administración de los cambios en la apariencia de la aplicación. En el ejemplo anterior, supongamos que es necesario cambiar el color de fondo de las 10 pantallas similares. En lugar de ser necesario seleccionar cada pantalla y cambiar la configuración de color de relleno, solo tiene que seleccionar la plantilla base y cambiar su color de relleno, y este cambio se reflejará inmediatamente en todas las pantallas derivadas.

Comentario adicional sobre las plantillas: debe asegurarse de que se mantiene el flujo de procesamiento de eventos, lo que significa que si proporciona un controlador de eventos para una pantalla base (para controlar los eventos de widget comunes) y para una pantalla derivada, el controlador de eventos de pantalla derivado debe llamar al controlador de eventos base_screen en el caso predeterminado. Esto permitirá que el controlador de eventos de pantalla base procese eventos generados por widgets comunes a todas las pantallas derivadas de esta base de plantilla.

## <a name="record-and-playback-macro"></a>Grabación y reproducción de Macro

Las funciones de grabación y reproducción de macro le ayudan a grabar y reproducir pulsaciones de teclas y eventos del mouse.

La grabación en un archivo de macro se realiza seleccionando el botón de barra de herramientas ***Grabar macro** o el menú seleccionar _*_Editar, grabar macro_*_. GUIX Studio presentará el cuadro de diálogo _*_Grabar macro_*_, que le permite especificar el directorio para el archivo de macro. Después de hacer esta selección, haga clic en el botón _*_Grabar_*_ para iniciar la grabación. Una vez finalizada la grabación, seleccione de nuevo el botón de la barra de herramientas _*_Grabar macro_*_ o use el menú desplegable para seleccionar *_Editar, finalizar macro_** para finalizar la grabación de macros.

La reproducción de un archivo de macro se consigue seleccionando el botón de barra de herramientas ***Reproducción macro** mediante el menú desplegable principal para seleccionar el comando _*_Editar y reproducir macro_*_. GUIX Studio presenta el cuadro de diálogo *_Reproducir macro_**, que permite especificar el archivo de macro grabado previamente que se va a ejecutar.

Al grabar macros que eligen archivos de entrada o salida, como agregar una fuente o una imagen, es importante usar el teclado para escribir el nombre de archivo, en lugar de utilizar el mouse para seleccionar desde el explorador de archivos. Dado que la grabadora de macro registra eventos de mouse y teclado, y como el explorador de archivos puede cambiar con el tiempo, es más confiable escribir el nombre de archivo que para seleccionar el archivo de forma gráfica.

## <a name="zooming-target-view"></a>Zoom de vista de destino

La función acercar le ayuda a obtener una vista más cercana de la pantalla de destino.

Puede elegir la configuración de zoom porcentual que desee en la opción de menú ***Configurar|Vista de destino|Zoom.** La *_Barra de herramientas_** también tiene botones para acercar o alejar.

## <a name="gridsnap-settings"></a>Configuración de cuadrícula o ajuste

El cuadro de diálogo ***Cuadrícula y configuración de ajuste** contiene algunos valores y opciones para cuadrícula y ajustar. En la _*_Figura 29_*_ se muestra el cuadro de diálogo de _*_Configuración de cuadrícula y ajuste_*_ cuando se selecciona el menú *_Configurar|Vista de destino|Cuadrícula y ajuste_**.

![Captura de pantalla de la Configuración de cuadrícula y ajuste.](./media/guix-studio/image63.jpg)

**Figura 29**

Activar la opción ***Mostrar cuadrícula** mostrará la cuadrícula en la pantalla de destino, podrá especificar el incremento de la cuadrícula (en píxeles) en el campo _*_Espaciado entre cuadrículas_*_. La opción *_Ajustar a la cuadrícula_** le ayuda a obtener la posición adecuada de un widget, active esta opción para las instantáneas activas.

Cuando está habilitada la opción ***Cuadrícula y ajuste***:

- Si arrastra un objeto con el mouse en la vista de destino, el objeto se moverá por incremento de la cuadrícula.
- Si arrastra el borde de un objeto para cambiar su tamaño, el borde que está arrastrando se ajustará a la posición de la cuadrícula.
- Si selecciona un objeto y usa las teclas arriba/izquierda/abajo/derecha, el widget seleccionado se moverá por incremento de ajuste, podrá especificar el incremento de ajuste (en píxeles) en el campo ***Espaciado de ajuste***.
