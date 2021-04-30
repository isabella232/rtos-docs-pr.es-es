---
title: 'Capítulo 3: Introducción funcional a GUIX'
description: Este capítulo contiene información general funcional del producto de interfaz de usuario GUIX de alto rendimiento.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 53ffc900debd3bfaa1a38d792ddf294b2ce92461
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550310"
---
# <a name="chapter-3---functional-overview-of-guix"></a>Capítulo 3: Introducción funcional a GUIX

Este capítulo contiene información general funcional del producto de interfaz de usuario GUIX de alto rendimiento. 

## <a name="execution-overview"></a>Información general sobre la ejecución

GUIX implementa un modelo de programación basado en eventos. Esto significa que el marco de GUIX está principalmente controlado por la recepción de eventos insertados en la cola de eventos de GUIX. El procesamiento de estos eventos tiene lugar en el contexto del subproceso de GUIX, que es un subproceso de ThreadX creado durante la inicialización del sistema de GUIX.

Las aplicaciones de GUIX definen la interfaz de usuario mediante llamadas a las funciones de API de GUIX para crear ventanas y widgets secundarios, y personalizan la apariencia de estos widgets mediante llamadas a otras funciones de API que se usan para definir colores, estilos, fuentes y otros atributos de cada tipo de ventana o widget. Si usa GUIX Studio para crear la apariencia de las pantallas de la interfaz de usuario, esta aplicación se encarga de gran parte de esta labor de llamar a funciones de API de GUIX para crear la pantalla.

Las aplicaciones de GUIX interactúan con el usuario del sistema y con la lógica de negocios externa mediante el control de los eventos recuperados de la cola de eventos de GUIX.
Normalmente, estos eventos se crean mediante widgets de GUIX, pero también pueden ser creados por subprocesos externos. Cuando se presiona un botón de GUIX típico, ese botón envía un evento a su ventana principal. El programa de la aplicación actuará a partir de esta acción de presionar el botón proporcionando un controlador para el evento que la representa.

A menudo se crean otros subprocesos de GUIX para elementos como los controladores de entrada. Un controlador de entrada de pantalla táctil típico se ejecuta como un subproceso externo independiente del subproceso principal de GUIX. El controlador de entrada táctil hace llegar la información táctil al subproceso de GUIX mediante el envío de eventos a la cola de eventos de GUIX.

Dado que muchas operaciones de interfaz de usuario, como las animaciones, requieren información de tiempo precisa, GUIX también implementa una interfaz de temporizador sencilla y fácil de usar. Esta interfaz de temporizador se basa en el servicio de temporizador de ThreadX y se configura automáticamente al iniciar el sistema.

La gran mayoría del software de GUIX no tiene dependencia alguna del hardware. El marco de trabajo sí requiere controladores de entrada y controladores gráficos específicos del hardware. En el capítulo 5 se trata en detalle el modo en que se implementan estos controladores específicos de hardware.

## <a name="initialization"></a>Inicialización 

Se debe llamar al servicio ***gx_system_initialize*** antes de llamar a cualquier otro servicio de GUIX. Se puede llamar a la inicialización del sistema de GUIX desde la rutina ***tx_application_define*** de ThreadX (contexto de inicialización) o desde subprocesos de la aplicación. La función ***gx_system_initialize*** crea la cola de eventos de GUIX, inicializa la utilidad del temporizador de GUIX, crea el subproceso del sistema de GUIX principal e inicializa diversas estructuras de datos mantenidas por GUIX durante la ejecución de la aplicación.

Después de que ***gx_system_initialize*** vuelve, la aplicación está lista para crear pantallas, lienzos, ventanas, widgets, y para personalizar las propiedades de todos los objetos de GUIX. Se pueden llamar a muchas de las API de creación de objetos de GUIX desde ***tx_application_define*** o desde subprocesos de la aplicación.

## <a name="application-interface-calls"></a>Llamadas a la interfaz de la aplicación 

Las llamadas desde la aplicación se realizan principalmente desde ***tx_application_define*** (contexto de inicialización) o desde subprocesos de la aplicación. Consulte la sección "Permitido desde" de cada API de GUIX que se describe en el capítulo 4 para determinar el contexto desde el que se puede llamar.

En su mayor parte, el procesamiento de actividades intensivas se difiere al subproceso interno de GUIX, incluido el procesamiento de eventos y el dibujo de widgets y ventanas.

Se puede llamar a las funciones de API de GUIX desde cualquier subproceso en cualquier momento.
Sin embargo, se suele considerar que una arquitectura de mejor calidad es la que separa la lógica de negocios crítica en el tiempo de la lógica de la interfaz de usuario. Las operaciones de dibujo de la interfaz de usuario a veces pueden tardar mucho tiempo en función del tamaño de la pantalla y el rendimiento de la CPU, por lo que no querrá que los subprocesos críticos en el tiempo se retrasen a la espera de que se complete una operación de dibujo.

## <a name="internal-guix-thread"></a>Subproceso interno de GUIX 

Como se mencionó, GUIX tiene un subproceso interno que realiza la mayor parte del procesamiento de la GUI. Este subproceso lo crea el software de la aplicación mediante una llamada a ***gx_system_initialize** _ seguida de _*_gx_system_start_**.

La prioridad del subproceso interno de GUIX viene determinada por el elemento `#define GX_SYSTEM_THREAD_PRIORITY`. El valor predeterminado es 16 (prioridad media), pero se puede modificar especificándolo en el archivo de encabezado gx_port.h o gx_user.h, lo que invalida el valor predeterminado.

La porción de tiempo del subproceso de GUIX se define de forma similar con el elemento `#define GX_SYSTEM_THREAD_TIMESLICE`, cuyo valor predeterminado es 10 ms.

El tamaño de la pila de subprocesos del sistema viene determinado por el elemento `#define GX_THREAD_STACK_SIZE`, que se encuentra en el archivo de encabezado ***gx_port. h***, pero también se puede invalidar especificándolo en el archivo de encabezado gx_user.h.

El bucle de ejecución del subproceso interno de GUIX se compone de tres acciones.
En primer lugar, GUIX recupera los eventos de la cola de eventos de GUIX y envía esos eventos para su procesamiento por parte de las ventanas y los widgets de GUIX. Normalmente, los eventos se insertan en la cola de eventos de GUIX mediante temporizadores periódicos, dispositivos de entrada como una pantalla táctil o un teclado numérico, y por los propios widgets de GUIX a medida que procesan la entrada del usuario. A continuación, una vez procesados todos los eventos, GUIX determina si se necesita una actualización de pantalla y, si es así, realiza el procesamiento necesario para actualizar los datos gráficos de la pantalla, principalmente mediante una llamada a las funciones de dibujo de las ventanas y los widgets que se han marcado como modificados. Por último, GUIX suspende el subproceso de GUIX hasta que lleguen uno o varios eventos nuevos de entrada.

## <a name="event-processing"></a>Procesamiento de eventos 

Los eventos de entrada táctil o de lápiz se procesan determinando la ventana o el widget de nivel superior situado por debajo de la posición del píxel de entrada táctil o de lápiz, y llamando a la función de procesamiento de eventos de esa ventana o ese widget. Si el widget entiende los eventos de entrada del lápiz, procesará el evento según corresponda en ese tipo de widget. De lo contrario, el widget de nivel superior pasará el evento de entrada táctil o de lápiz a su elemento principal para el procesamiento. Esta subida del evento por la cadena continúa hasta que se administra el evento o hasta que este llega a la ventana raíz, en cuyo caso se descarta.

Los eventos de teclado numérico se envían a la ventana o el widget que tenga el foco de entrada. El componente gx_system de GUIX mantiene el estado del foco de entrada.

Los eventos de temporizador siempre se envían para su procesamiento a la ventana o el widget que tiene la propiedad del temporizador.

Los eventos generados internamente, como los eventos de clic de botón o los eventos de cambio de valor del control deslizante, siempre se envían al elemento principal del widget que genera el evento. Si el elemento principal no procesa el evento, se sube por la cadena de manera similar a como sucede en los eventos de entrada táctil o de lápiz.

## <a name="drawing"></a>Dibujo 

Una vez completado todo el procesamiento de eventos, el subproceso interno de GUIX determina si se necesita una actualización de pantalla y, en ese caso, llama a las funciones de dibujo de la ventana o del widget adecuadas. Cuando se completa el dibujo, el subproceso interno de GUIX simplemente espera en su cola de eventos la llegada del siguiente evento de GUIX que se va a procesar.

GUIX implementa el concepto de *áreas con modificaciones*, que son áreas que deben volver a dibujarse, en cada widget y lienzo. Un widget solo puede dibujar en áreas que se han marcado previamente como áreas con modificaciones. Cuando se llama a una función de dibujo de widget, todas las operaciones de dibujo se recortan internamente al rectángulo con modificaciones definido previamente.
Los intentos de dibujar fuera de esta área se omiten.

Los widgets y las ventanas se marcan a sí mismos como elementos con modificaciones mediante una llamada a la función de API ***gx_system_dirty_mark***. Esta función señala que toda la ventana o todo el widget se debe volver a dibujar. Se puede invocar otra función, ***gx_system_dirty_partial_add***, como alternativa para indicar que solo una parte de la ventana o el widget tiene modificaciones.

Este proceso por el que se marcan los widgets como modificados y solo se vuelven a dibujar cuando se han procesado todos los eventos de entrada se denomina *dibujo diferido*. El algoritmo de dibujo diferido de GUIX y el mantenimiento de la lista de elementos modificados se han diseñado para mejorar la eficacia del dibujo. Dado que las operaciones de dibujo suelen ser costosas, GUIX hace todo lo posible para evitar dibujos innecesarios.

El dibujo se realiza en un *lienzo* de GUIX. Un lienzo es un área de memoria reservada para contener datos gráficos. Un lienzo puede estar o no vinculado directamente al búfer de cuadros de hardware, en función de la arquitectura del sistema y las restricciones de memoria. Para que se pueda dibujar, se debe abrir un lienzo con este fin llamando a la función de API ***gx_canvas_drawing_initiate***. Esta API prepara un lienzo para dibujar y establece el *contexto de dibujo* actual. Cuando GUIX realiza una actualización del lienzo del sistema, se abre el lienzo para dibujar y se establece el contexto de dibujo antes de invocar las API de dibujo en el nivel de widget. Por lo tanto, no es necesario que los widgets inicien el dibujo en un lienzo dentro de su función de dibujo.

Sin embargo, si una aplicación desea realizar un dibujo inmediato en un lienzo, fuera del flujo del algoritmo de dibujo diferido estándar de GUIX, debe invocar directamente la función ***gx_canvas_drawing_initiate*** antes de llamar a cualquier otra función de API de dibujo y la función ***gx_canvas_drawing_complete*** una vez que se haya completado el dibujo inmediato.

## <a name="user-input"></a>Entrada del usuario 

GUIX admite dispositivos de pantalla táctil, mouse y teclado con tipos de eventos predefinidos. Se pueden usar otros dispositivos de entrada definiendo tipos de eventos personalizados o asignando el dispositivo de entrada personalizado a los tipos de eventos predefinidos.

Las acciones asociadas a estos dispositivos se traducen en eventos que se procesan en el subproceso interno de GUIX. El software de nivel de controlador escrito para admitir una pantalla táctil debe preparar y enviar a la cola de eventos de GUIX los eventos para las operaciones de subir, bajar y arrastrar el lápiz. Del mismo modo, un controlador de entrada de teclado debe generar eventos para las entrada de presión y liberación de la tecla.

## <a name="modal-dialog-execution"></a>Ejecución de cuadros de diálogo modales 

La ejecución de cuadros de diálogo modales hace referencia a la presentación al usuario de una ventana que debe cerrarse de alguna manera para que otras ventanas o widgets de GUIX puedan recibir la entrada del usuario. Los cuadros de diálogo modales capturan toda la entrada del usuario mientras se muestra la ventana de diálogo, independientemente de la posición x,y de los eventos de entrada táctil o de mouse.

El software de la aplicación desencadena los cuadros de diálogo modales creando primero la ventana de la manera normal con una llamada a ***gx_window_create*** y llamando después a la función de API ***gx_window_execute*** de GUIX.

Cuando se llama a la función ***gx_window_execute***, GUIX entra en un bucle de procesamiento de eventos local. La función ***gx_window_execute*** no vuelve al autor de la llamada hasta que se cierra la ventana del cuadro de diálogo, ya sea debido a la entrada del usuario o a una llamada a ***gx_window_close***. Por esta razón, es muy importante no llamar nunca a la función ***gx_window_execute*** desde cualquier subproceso que no sea el subproceso interno de GUIX.

## <a name="periodic-processing"></a>Procesamiento periódico 

Para proporcionar efectos de pantalla, animación con sprites y compatibilidad con solicitudes periódicas de aplicación, GUIX usa un temporizador de ThreadX. Este único temporizador se utiliza para controlar todas las necesidades relacionadas con el tiempo de GUIX. De forma predeterminada, la frecuencia de procesamiento del temporizador interno de GUIX se establece en 20 ms por medio de la constante **GX_SYSTEM_TIMER_MS**, que se define en **_gx_api.h_**, a menos que se haya definido previamente en los encabezados gx_port.h o gx_user.h. La aplicación puede cambiar la frecuencia predeterminada por medio de una opción de compilación al compilar la biblioteca de GUIX o redefiniéndola explícitamente en ***gx_user.h***.

> [!IMPORTANT]
> Tenga en cuenta que la frecuencia del temporizador de GUIX se expresa en tics del temporizador de RTOS y se define mediante la constante **GX_SYSTEM_TIMER_TICKS**. El valor de **GX_SYSTEM_TIMER_TICKS** se calcula usando **GX_SYSTEM_TIMER_MS** y **TX_TIMER_TICKS_PER_SECOND**. El usuario puede volver a definir cualquiera de estos valores en ***gx_port.h** _ o _ *_gx_user. h_** para ajustar la frecuencia y la resolución del temporizador de GUIX.

## <a name="display-driver"></a>Controlador de pantalla 

Los controladores de pantalla son responsables de proporcionar un conjunto de funciones de dibujo al código principal de GUIX. La implementación de cada una de estas funciones de dibujo viene determinada por el controlador y, cuando sea posible, aprovechará la compatibilidad con la aceleración de hardware. En general, la función de dibujo escribe los datos de píxeles en un búfer de memoria, que puede ser el búfer de cuadros físico o bien un búfer secundario, en función de la arquitectura del controlador. Muchos controladores implementan el almacenamiento en búfer doble mediante dos búferes de cuadros, entre los que se alterna invocando la función de alternancia de búfer. GUIX llama a estas funciones internamente en los momentos adecuados. En el caso de los sistemas con restricción de memoria, las funciones de dibujo solo pueden escribir en un búfer de cuadros de memoria.

GUIX proporciona implementaciones de software predeterminadas de cada función de dibujo de bajo nivel en todos los formatos y profundidades de color compatibles. Estas funciones se invocan por medio de punteros de función que se mantienen dentro de la estructura de **GX_DISPLAY**. Cuando se crean controladores específicos del hardware, por lo general sobrescriben algunos de estos punteros de función con funciones específicas del hardware de destino.

Para implementar un controlador de pantalla de hardware típico, se crea primero el controlador de pantalla predeterminado de GUIX para la profundidad de color y el formato necesarios.
Después, el controlador de hardware reemplaza las funciones que deban optimizarse o personalizarse para la implementación de hardware concreta.

GUIX admite formatos de color de píxel que van desde un formato monocromo de 1 bpp a un formato a:r: g:b de 32 bpp. GUIX también admite muchas variaciones dentro de cada categoría de profundidad de color general, como el orden de bytes r:g: b frente b:g:r, un formato de píxel empaquetado frente a formatos de píxeles alineados por palabras, y canales alfa. Actualmente se admiten 25 formatos de color distintos, pero esta lista crece a medida que los proveedores de hardware ofrecen nuevas variaciones.

## <a name="display-memory-architectures"></a>Arquitecturas de memoria para pantallas

Los diferentes destinos y pantallas de hardware usan una gama de arquitecturas de memoria de pantalla diferentes, en función de las restricciones de memoria del destino y de los requisitos de funcionalidad de la aplicación. Describiremos aquí algunas de las arquitecturas de memoria comunes con una breve descripción de cada una.

Modelo 1) No hay ningún búfer de cuadros y los datos gráficos se incluyen en una memoria GRAM externa:

![No hay ningún búfer de cuadros y los datos gráficos se incluyen en una memoria GRAM externa](./media/guix/user-guide/no-frame-buffer.png)

En el modelo anterior, no existe memoria para un búfer de cuadros en la memoria local de la CPU. Todos los datos gráficos se almacenan en una memoria gráfica de acceso aleatorio (GRAM) externa que se incorpora en la propia pantalla. La interfaz a la GRAM externa puede ser paralela o serie. Este tipo de arquitectura tiene un costo muy bajo; sin embargo, puede mostrar un efecto de pantalla partida no deseado cuando se actualizan los datos gráficos.

Modelo 2) Un búfer de cuadros local:

![Un búfer de cuadros local](./media/guix/user-guide/one-local-frame-buffer.png)

En este modelo, la memoria de los datos gráficos se asigna desde una memoria de acceso aleatorio a la que se puede acceder directamente desde la CPU. El hardware dedicado debe estar presente para transmitir reiteradamente los datos gráficos (junto con las señales de tiempo) de la memoria local a la pantalla. Este modelo se diferencia del modelo 1 en que la memoria gráfica es un bloque de la SRAM o DRAM local disponible para la CPU. Puede ser la misma memoria en la que residen las variables de la pila y del programa.

Modelo 3) Búfer de cuadros local + GRAM externa:

![Búfer de cuadros local + GRAM externa](./media/guix/user-guide/local-frame-buffer-external-gram.png)

El modelo 3 es una combinación de los dos primeros. En este modelo, hay suficiente memoria local como para contener un búfer de cuadros. Además, el dispositivo de pantalla proporciona una GRAM externa y se actualiza automáticamente con los datos proporcionados en la GRAM. Esta arquitectura se beneficia de una eficacia de actualización mejorada, ya que podemos transferir la parte modificada del búfer de cuadros local a la GRAM externa en una transferencia de bloques, a menudo mediante canales DMA incorporados. Este modelo también elimina los efectos de pantalla partida y parpadeo que pueden encontrarse en los dos primeros modelos, porque solo se copia el contenido gráfico completo en la GRAM externa.

Modelo 4) Búferes de cuadros de ping pong:

![Búferes de cuadros de ping pong](./media/guix/user-guide/ping-pong-frame-buffers.png)

En el modelo 4, hay suficiente memoria para proporcionar dos búferes de cuadros locales. En este caso, GUIX trata un búfer de cuadros como el búfer de cuadros activo y el otro como búfer de cuadros de trabajo. Cuando se realiza una actualización de pantalla o una operación de dibujo, tiene lugar en el búfer de trabajo. Cuando se completa la operación de dibujo, los búferes se alternan; el búfer de trabajo se convierte en el búfer activo y este en el búfer de trabajo. Este modelo también elimina los efectos de parpadeo de la pantalla y pantalla partida que se pueden observar en un sistema de almacenamiento en un solo búfer.

Modelo 5) Búferes de ping pong con composición de lienzos:

![Búferes de ping pong con composición de lienzos](./media/guix/user-guide/ping-pong-buffers-canvas-composting.png)

En el modelo 5 se puede crear cualquier número de lienzos hasta los límites de la memoria disponible. Los lienzos se pueden superponer o combinar según se defina en la aplicación para crear la composición. Cuando se crea una nueva composición después de una operación de actualización de pantalla, los búferes de composición activo y de trabajo se alternan en una operación idéntica a la arquitectura de búferes de ping pong estándar. El modelo 5 incluye la capacidad de realizar operaciones de fundido y combinación mediante la combinación de los lienzos en una composición de salida final.

Modelo 6) Composición de lienzos con GRAM externa:

![Composición de lienzos con GRAM externa](./media/guix/user-guide/canvas-compositing-external-gram.png)

El modelo 6 es una ligera variación del modelo 5, en el que solo se requiere un búfer de composición y, a continuación, el búfer de composición se transfiere a la GRAM externa. Este modelo también admite la combinación y las superposiciones de pantalla completa.

## <a name="string-encoding"></a>Codificación de cadenas 

GUIX es compatible de forma predeterminada con la codificación de cadenas en formato UTF8. Esta compatibilidad se puede deshabilitar definiendo **GX_DISABLE_UTF8_SUPPORT** en el archivo de encabezado ***gx_user. h***. Si la codificación UTF8 está deshabilitada, GUIX utilizará internamente solo la codificación de caracteres ASCII de 8 bits estándar y la página de códigos Latin-1. Al deshabilitar la codificación de cadenas UTF8 se consigue una superficie de biblioteca de GUIX ligeramente más pequeña y una ejecución en tiempo de ejecución ligeramente más rápida de las funciones de control de cadenas y de dibujo de texto.

La codificación de cadenas UTF8 tiene los siguientes rasgos:

  - Las cadenas ASCII no ocupan más espacio de almacenamiento que la codificación ASCII estándar de 7 bits.

  - La mayoría de las funciones de cadena de ANSI-C funcionan con la codificación de cadenas UTF8 sin modificaciones.

Todos los juegos de caracteres activos del mundo, incluidos los juegos de caracteres kanji, se pueden representar mediante la codificación de cadenas UTF8.

### <a name="static-and-dynamic-strings"></a>Cadenas estáticas y dinámicas 

Las cadenas asignadas a los widgets de GUIX que admiten la presentación de texto pueden ser constantes de cadena definidas de forma estática (que normalmente se colocan en el almacenamiento de constantes como parte de la tabla de cadenas de GUIX que se describe a continuación) y cadenas definidas dinámicamente (que son cadenas generadas en tiempo de ejecución mediante servicios como ***sprintf** _ o _*_gx_utility_ltoa_**).

Algunos ejemplos de cadenas dinámicas pueden incluir un valor que se muestra como un número en un widget de solicitud de GUIX o una cadena de "fecha y hora" que tiene un formato dinámico según la ubicación del usuario y las preferencias de formato. Si crea cadenas en tiempo de ejecución que se asignarán a widgets de GUIX como **GX_PROMPT** o **GX_TEXT_BUTTON**, debe elegir si el almacenamiento para estas cadenas generadas en tiempo de ejecución se asigna estáticamente (es decir,
con matrices de caracteres globales) o si se define e instala una función de asignador de memoria dinámica y se usa el estilo **GX_STYLE_TEXT_COPY**, que indica a esos widgets que creen una copia privada de las cadenas de texto asignadas.

El uso de almacenamiento temporal, como una matriz de caracteres automática, para incluir una cadena generada dinámicamente y, a continuación, la asignación de esta cadena a un widget que no tenga el estilo **GX_STYLE_TEXT_COPY** se considera un error de programación. Cuando este estilo no está habilitado, el widget simplemente copia el puntero de cadena proporcionado; los datos de cadena deben asignarse de forma estática o, de lo contrario, es probable que el puntero de cadena del widget acabe apuntando a datos no utilizados, lo que produciría resultados imprevisibles.

### <a name="passing-gx_string-arguments"></a>Paso de argumentos a GX_STRING 

Las funciones de API de GUIX que aceptan un parámetro GX_STRING siempre comprueban que la longitud de la cadena a la que señala el campo **GX_STRING.gx_string_ptr** coincida con el valor del campo **GX_STRING.gx_string_length**. Si los dos campos no son coherentes, se devuelve un error **GX_INVALID_STRING_LENGTH** y la API a la que se ha llamado vuelve sin aceptar la asignación de cadena.

Por motivos de seguridad, el software de GUIX nunca usa internamente las funciones de cadena estándar de C como ***strlen** _ o _*_strcpy_**. Se sabe que estas funciones son susceptibles a ataques malintencionados cuando se adquieren datos de cadena de forma dinámica, lo que suele ser el caso en las aplicaciones conectadas.

Las versiones de la biblioteca de GUIX anteriores a la versión 5.6 definían las funciones de API que aceptaban (`GX_CONST GX_CHAR *text`) como parámetro. Estas funciones, si bien todavía se admiten por compatibilidad con versiones anteriores, se han quedado obsoletas y se han reemplazado por las funciones de API preferidas que aceptan (`GX_CONST GX_STRING *string`) como parámetro de entrada.

De forma predeterminada, la API de control de texto en desuso está habilitada, lo que permite que todas las aplicaciones escritas previamente se compilen correctamente con las actualizaciones más recientes de la biblioteca de GUIX. Para deshabilitar la API de control de texto en desuso, debe agregarse la definición **GX_DISABLE_DEPRECATED_STRING_API** al archivo de encabezado **_gx_user. h_ *_. Todas las aplicaciones nuevas deben definir _* GX_DISABLE_DEPRECATED_STRING_API** y solo deben usar las funciones de API de reemplazo. Todos los archivos de salida generados por GUIX Studio para la versión 5.6 o posterior de la biblioteca de GUIX utilizarán solo las funciones de API de reemplazo.

En la tabla siguiente se indican los nombres de las funciones de API de reemplazo en desuso y las recién definidas:

| **Nombre de función en desuso**              | **Reemplazada por**                              |
| ------------------------------------------ | ----------------------------------------------- |
| gx_binres_language_table_load          | gx_binres_language_table_load_ext          |
| gx_canvas_rotated_text_draw            | gx_canvas_rotated_text_draw_ext            |
| gx_canvas_text_draw                     | gx_canvas_text_draw_ext                     |
| gx_context_string_get                   | gx_context_string_get_ext                   |
| gx_display_language_table_get          | gx_display_language_table_get_ext          |
| gx_display_language_table_set          | gx_display_language_table_set_ext          |
| gx_display_string_get                   | gx_display_string_get_ext                   |
| gx_display_string_table_get            | gx_display_string_table_get_ext            |
| gx_multi_line_text_button_text_set   | gx_multi_line_text_button_text_set_ext   |
| gx_multi_line_text_input_char_insert | gx_multi_line_text_input_char_insert_ext |
| gx_multi_line_text_input_text_set    | gx_multi_line_text_input_text_set_ext    |
| gx_multi_line_text_view_text_set     | gx_multi_line_text_view_text_set_ext     |
| gx_prompt_text_get                      | gx_prompt_text_get_ext                      |
| gx_prompt_text_set                      | gx_prompt_text_set_ext                      |
| gx_single_line_text_input_text_set   | gx_single_line_text_input_text_set_ext   |
| gx_system_string_width_get             | gx_system_string_width_get_ext             |
| gx_system_version_string_get           | gx_system_version_string_get_ext           |
| gx_text_button_text_get                | gx_text_button_text_get_ext                |
| gx_text_button_text_set                | gx_text_button_text_set_ext                |
| gx_text_scroll_wheel_callback_set     | gx_text_scroll_wheel_callback_set_ext     |
| gx_utility_string_to_alphamap          | gx_utility_string_to_alphamap_ext          |
| gx_widget_string_get                    | gx_widget_string_get_ext                    |
| gx_widget_text_blend                    | gx_widget_text_blend_ext                    |
| gx_widget_text_draw                     | gx_widget_text_draw_ext                     |

### <a name="guix-string-table"></a>Tabla de cadenas de GUIX 

La tabla de cadenas y los recursos de cadena de GUIX se registran con una instancia de pantalla de GUIX.

Cada pantalla de un sistema de varias pantallas tiene su propia tabla de cadenas, y cada pantalla se puede ejecutar en su propio idioma seleccionado. Los otros tipos de recursos de GUIX (colores, fuentes y mapas de píxeles) también se mantienen mediante el componente de pantalla de GUIX, ya que estos tipos de recursos son específicos de cada formato y profundidad de color de pantalla.

Aunque puede crear manualmente la tabla de cadenas de la aplicación, en la mayoría de los casos es la aplicación GUIX Studio la que define esta tabla como parte del archivo de recursos del proyecto. Los idiomas disponibles también se definen en el archivo de encabezado del recurso. La tabla de cadenas de pantalla es una tabla de varias columnas de punteros a cadenas de la aplicación. Cada columna de la tabla de cadenas representa un idioma admitido por la aplicación.
Si la aplicación admite solo un idioma, como el español, la tabla de cadenas solo tendrá una columna. Aun así, puede agregar compatibilidad con otros idiomas en cualquier momento sin necesidad de modificar el software de la aplicación.

La tabla de cadenas activa se asigna mediante una llamada a la función de API ***gx_display_string_table_set***. Esta llamada la realiza automáticamente el código de inicio generado por GUIX Studio, pero también puede proceder directamente de la aplicación para cambiar la tabla de cadenas activa.

El idioma activo se asigna mediante una llamada a la función de API ***gx_display_active_language_set***. Esta función determina qué columna de la tabla de cadenas de pantalla está activa.

Cuando se invoca esta función, se envía un evento **GX_EVENT_LANGUAGE_CHANGE** a todos los widgets de GUIX visibles, lo que les permite actualizarse para mostrar los datos de la cadena que ha pasado a estar activa.

Los widgets y el software de la aplicación resuelven las cadenas definidas estáticamente mediante valores de identificador de cadena y las funciones de API ***gx_display_string_get_ext*** o ***gx_widget_string_get_ext***. Estas funciones devuelven el valor de **GX_STRING** asociado a un identificador de cadena determinado y al idioma activo actualmente.

### <a name="bi-directional-text-display"></a>Visualización de texto bidireccional 

GUIX proporciona dos estrategias para la compatibilidad con el texto bidireccional.

Una opción es realizar la reordenación de texto bidireccional en la aplicación GUIX Studio. Si se usa esta opción, GUIX Studio es responsable de generar el texto bidireccional en el archivo de salida según su orden de visualización. Esta solución no tiene ningún impacto en el rendimiento en tiempo de ejecución y no requiere ninguna adición a la biblioteca en tiempo de ejecución de GUIX. Para permitir que GUIX Studio genere cadenas de texto bidireccionales según el orden de visualización, debe activar la casilla **Generate Bidi Text in Display Order** (Generar texto bidireccional en el orden de visualización) en el cuadro de diálogo de configuración de idioma de GUIX Studio:

![Configuración de idiomas](./media/guix/user-guide/configure-languages.png)

Con estas opciones seleccionadas, el archivo de recursos generado contendrá cadenas bidireccionales generadas según el orden de visualización y no se requerirá ningún procesamiento adicional dentro de la biblioteca en tiempo de ejecución de GUIX.

La segunda opción consiste en realizar una reordenación del texto bidireccional en tiempo de ejecución. Esta opción es compatible con las aplicaciones que deben administrar cadenas de texto bidireccionales definidas dinámicamente y que no se generan en la aplicación GUIX Studio. En este caso, la biblioteca en tiempo de ejecución de GUIX es responsable de reordenar el texto bidireccional antes de dibujar cada cadena de texto. Esta solución afecta al rendimiento en tiempo de ejecución y a la memoria. Debe haber suficiente memoria dinámica disponible para el proceso de reordenación del texto bidireccional. Esta solución requiere la definición GX_DYNAMIC_BIDI_TEXT_SUPPORT condicional al compilar la biblioteca de GUIX. Se proporcionan dos funciones de API, ***gx_system_bidi_text_enable*** y ***gx_system_bidi_text_disable***, para habilitar o deshabilitar la compatibilidad de texto bidireccional en tiempo de ejecución.

No debe utilizar **GX_DYNAMIC_BIDI_TEXT_SUPPORT** y a la vez configurar GUIX Studio para generar texto bidireccional según el orden de visualización. Debe seleccionar una estrategia u otra para controlar las cadenas de texto bidireccional.

## <a name="memory-usage"></a>Uso de la memoria 

GUIX reside con el programa de la aplicación. Como resultado, el uso de memoria estática (o memoria fija) de GUIX viene determinado por las herramientas de desarrollo; es decir, el compilador, el enlazador y el localizador. El uso de memoria dinámica (o memoria en tiempo de ejecución) está bajo el control directo de la aplicación.

### <a name="static-memory-usage"></a>Uso de memoria estática 

La mayoría de las herramientas de desarrollo dividen la imagen del programa de la aplicación en cinco áreas básicas: *instrucciones*, *constantes*, *datos inicializados*, *datos sin inicializar* y la *pila de subprocesos de GUIX*. En la figura 2 del manual del usuario de ThreadX SMP se muestra un ejemplo de estas áreas de memoria.

Es importante entender que se trata solo de un ejemplo. El diseño de la memoria estática real es específico del procesador, las herramientas de desarrollo, el hardware subyacente y la propia aplicación.

El área de instrucciones contiene todas las instrucciones del procesador del programa. Esta área suele encontrarse en la ROM.

El área de constantes contiene varias constantes compiladas; en GUIX contiene los valores predeterminados y todos los recursos de la aplicación (imágenes, cadenas, fuentes y colores). Además, esta área contiene la "copia inicial" del área de datos inicializados. Durante el proceso de inicialización del compilador, esta parte del área de constantes se usa para configurar los datos inicializados globales en la RAM. El área de constantes suele ser la más grande, suele seguir al área de instrucciones y suele encontrarse en la ROM.

Por lo general, los mapas de píxeles y las fuentes de GUIX suelen requerir una gran cantidad de almacenamiento de datos constantes. Estas grandes áreas de datos estáticos normalmente se mantienen en la memoria ROM o FLASH.

La pila de subprocesos de GUIX se define dentro del área de datos no inicializados (como una variable global) en el archivo ***gx_system.h*** de la siguiente manera:

```C
_gx_system_thread_stack[GX_THREAD_STACK_SIZE];
```

**GX_THREAD_STACK_SIZE** se define en **_gx_port. h_**, pero la aplicación puede invalidarlo definiendo este símbolo en el archivo de encabezado ***gx_user.h*** o por medio de las opciones del proyecto o los parámetros de la línea de comandos. El tamaño de la pila debe ser lo suficientemente grande como para administrar el peor caso en el control de eventos y las llamadas de dibujo anidadas.

### <a name="dynamic-memory-usage"></a>Uso de memoria dinámica 

Como se ha mencionado antes, el uso de memoria dinámica está bajo el control directo de la aplicación. Los bloques de control y la memoria asociados a los lienzos, etc., se pueden colocar en cualquier parte del espacio de memoria del destino. Se trata de una característica importante, ya que facilita el uso de diferentes tipos de memoria física en tiempo de ejecución.

Por ejemplo, imagine que un entorno de hardware de destino tiene memoria rápida y memoria lenta. Si la aplicación necesita un rendimiento adicional para el dibujo, la memoria del lienzo se puede colocar explícitamente en el área de memoria de alta velocidad para conseguir el mejor rendimiento.

Varios servicios y características opcionales de GUIX requieren un mecanismo de asignación de memoria dinámica en tiempo de ejecución, que se conoce normalmente como montón. Estos servicios y características son totalmente opcionales; muchas aplicaciones de GUIX no usan ningún montón y no definen ningún mecanismo de asignación de memoria en tiempo de ejecución.

Si va a utilizar servicios que requieren la asignación de memoria en tiempo de ejecución, debe instalar las funciones a las que GUIX llamará cuando se deba asignar o liberar memoria dinámicamente. Puede implementar estas funciones como prefiera, de modo que, incluso en este caso, la ubicación del grupo de memoria dinámica esté bajo control de la aplicación. Para disponer de compatibilidad con la asignación de memoria dinámica, la aplicación debe invocar el servicio de API ***gx_system_memory_allocator_set*** durante el inicio del programa para definir los servicios de asignación y liberación de memoria. Consulte en la documentación de esta API un ejemplo completo.

Los servicios de GUIX que requieren servicios de asignación y desasignación de memoria en tiempo de ejecución incluyen los siguientes:

  - Carga de recursos binarios del almacenamiento externo en el entorno de ejecución de GUIX.

  - Descodificador de imágenes JPEG en tiempo de ejecución de software.

  - Descodificador de imágenes PNG en tiempo de ejecución de software.

  - Uso de widgets de texto con GX_STYLE_TEXT_COPY.

  - Funciones de utilidad de cambio de tamaño y rotación de mapa de píxeles en tiempo de ejecución.
  - Asignación de bloques de control de pantalla y de widget en tiempo de ejecución.

En el caso de las aplicaciones más pequeñas, los recursos de GUIX se suelen compilar y vincular estáticamente como parte de la imagen de aplicación, y no es necesaria la instalación de recursos binarios. Los recursos binarios permiten que una aplicación instale recursos (fuentes, imágenes, idiomas) en tiempo de ejecución cargados desde alguna ubicación de almacenamiento, como una unidad flash o una dirección URL.

Los descodificadores de JPEG y PNG en tiempo de ejecución son componentes opcionales. La mayoría de las aplicaciones de GUIX permiten que la herramienta GUIX Studio descodifique previamente todos los archivos de imagen necesarios y los almacene como recursos de datos de mapa de píxeles propiedad de GUIX. Estos servicios se proporcionan para la integridad de las aplicaciones que requieren la conversión en tiempo de ejecución de imágenes JPEG o PNG al formato de mapa de píxeles.

**GX_STYLE_TEXT_COPY** permite al usuario especificar que uno o varios widgets determinados mantendrán su propia copia privada del texto asignado dinámicamente. El uso de esta opción requiere que se instale antes el mecanismo de asignación de memoria. Si **<span class="underline">no</span>** se proporciona esta marca de estilo cuando se crea un widget de tipo de texto, la aplicación debe asignar áreas de almacenamiento estáticas para todas las cadenas de texto creadas y asignadas dinámicamente. En este caso, no se deben usar variables automáticas para almacenar los datos de cadena generados en tiempo de ejecución. Si está habilitado el estilo de **GX_STYLE_TEXT_COPY**, se pueden usar variables automáticas para contener los datos de cadena asignados a widgets de GUIX, ya que cada widget creará su propia copia del texto asignado.

Las funciones de utilidad de cambio de tamaño y rotación de mapas de píxeles devuelven el mapa de píxeles trasladado resultante como un nuevo mapa de píxeles disponible para la aplicación.
Si se usan estos servicios, debe haber suficiente memoria dinámica para incluir estos bloques de datos de mapas de píxeles que se generan en tiempo de ejecución.

Por último, los bloques de control de las pantallas y los widgets de GUIX se pueden asignar de forma estática o dinámica. En el caso de aplicaciones más pequeñas, es habitual crear todas las pantallas de la aplicación durante el inicio del programa y utilizar bloques de control asignados estáticamente. En el caso de las aplicaciones de gran tamaño, los controles de pantallas y de widgets secundarios suelen crearse dinámicamente a medida que son necesarios. Los bloques de control asignados dinámicamente se especifican seleccionando la casilla de verificación **Runtime Allocate** (Asignación en tiempo de ejecución) en la vista de propiedades de GUIX Studio o pasando la marca de estilo **GX_STYLE_DYNAMICALLY_ALLOCATED** al crear un widget por medio de la API estándar. El uso de bloques de control de widget asignados dinámicamente requiere que estén definidos los servicios de asignación y desasignación de memoria, tal como se describió anteriormente.

## <a name="guix-components"></a>Componentes de GUIX 

Las API de GUIX se dividen y se organizan en varios grupos básicos que se corresponden con los componentes fundamentales del sistema de GUIX. A continuación se indican los componentes fundamentales:

| Componentes  | Descripción  |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GX_SYSTEM  | Es el componente de sistema de GUIX, responsable de la inicialización, los eventos, los temporizadores, las tablas de cadenas y la administración de la jerarquía de widgets visibles.                                                                                                                                                                                                                                                                      |
| GX_CANVAS  | Es un área de dibujo. Un lienzo puede ser una abstracción fina del búfer de cuadros de hardware o también podría ser directamente un lienzo de memoria. El tipo de lienzo viene determinado por los parámetros que se pasan a la función de API gx_canvas_create.                                                                                                                                                                                   |
| GX_CONTEXT | El componente de contexto de dibujo. El contexto de dibujo contiene información sobre la pantalla, el lienzo y el pincel, así como el área de recorte de las operaciones de dibujo actuales.                                                                                                                                                                                                                                      |
| GX_DISPLAY | Proporciona las API y las implementaciones de nivel de controlador que permiten que la aplicación y los widgets de GUIX realicen dibujos en un lienzo. GX_DISPLAY se implementa para representar correctamente los gráficos en cada lienzo con el formato de color necesario del lienzo correspondiente. El componente GX_DISPLAY también administra los recursos (colores, fuentes y mapas de píxeles) disponibles para los widgets que dibujan en los lienzos vinculados a cada pantalla. |
| GX_WIDGET  | Objeto de widget visible básico y las API asociadas. Todos los tipos de widgets de GUIX se basan o derivan del tipo GX_WIDGET básico.                                                                                                                                                                                                                                                                      |
| GX_UTILITY | En este grupo se incluyen funciones de utilidad para trabajar con rectángulos, funciones de conversión de cadenas y funciones matemáticas no ANSI.                                                                                                                                                                                                                                                         |

Además de estos componentes básicos, GUIX incluye API exclusivas de cada tipo de widget proporcionado en la biblioteca. Estas API se describen en el capítulo 4 de este manual del usuario, "Descripción de los servicios de GUIX".

## <a name="guix-system-component"></a>Componente de sistema de GUIX

El componente de sistema de GUIX proporciona varios servicios globales para la aplicación de interfaz de usuario. Estos servicios incluyen: *inicialización, administración de eventos, administración de pantallas, administración de recursos, administración de temporizadores* y *administración de widgets*. Cada servicio es esencial para la organización del programa de la aplicación; se describen con más detalle en las subsecciones siguientes.

### <a name="initialization"></a>Inicialización 

La inicialización de GUIX se realiza cuando la aplicación llama al servicio ***gx_system_initialize***, ya sea desde la rutina ***tx_application_define*** de ThreadX (contexto de inicialización) o desde subprocesos de la aplicación. La función ***gx_system_initialize*** inicializa todas las estructuras de datos globales de GUIX y crea la exclusión mutua, la cola de eventos, el temporizador y el subproceso del sistema de GUIX. Una vez que vuelve ***gx_system_initialize***, la aplicación puede usar GUIX.

### <a name="thread-processing"></a>Procesamiento de subprocesos 

El subproceso interno de GUIX, creado durante la inicialización, es responsable de la mayor parte del procesamiento que se realiza en GUIX. En primer lugar, el procesamiento de este subproceso completa cualquier inicialización adicional que precise el controlador de pantalla subyacente. A continuación, el subproceso de GUIX entra en un bucle en el que primero procesa todos los eventos presentes en la cola de eventos de GUIX y, a continuación, actualiza la pantalla si es necesario. La actualización de la pantalla ejecuta las funciones de dibujo necesarias de GUIX, en función de lo que esté visible y se haya marcado como modificado, lo que significa que debe volver a dibujarse. Cuando no hay eventos y nada más que actualizar en la pantalla, el subproceso de GUIX se suspende y se queda esperando a que llegue el siguiente evento de GUIX.

### <a name="rtos-binding"></a>Enlace con RTOS 

El componente de sistema de GUIX está configurado de forma predeterminada para utilizar el sistema operativo en tiempo real de ThreadX para servicios como servicios de subprocesos, servicios de cola de eventos y servicios de temporizador. GUIX se puede distribuir fácilmente a otros sistemas operativos si se usa la directiva de preprocesador GX_DISABLE_THREADX_BINDING y se vuelve a compilar la biblioteca de GUIX. De este modo, se quitan las dependencias de ThreadX del código fuente de GUIX y el desarrollador de la aplicación puede implementar los servicios de sistema operativo necesarios con cualquier RTOS que se proporcione en el sistema de destino. En el [Apéndice F Servicios de enlace con RTOS en GUIX](appendix-f.md) se describen los servicios que deben implementarse para distribuir GUIX a un sistema operativo distinto del sistema operativo de ThreadX.

### <a name="multithread-safety"></a>Seguridad para subprocesos 

La API de GUIX está disponible en el contexto de subprocesos de GUIX y en otros subprocesos de aplicación. Los subprocesos de aplicación pueden interactuar con el subproceso de GUIX mediante el envío y la recepción de eventos, el acceso a las variables compartidas y el uso de las funciones de API de GUIX. GUIX usa una exclusión mutua de ThreadX interna para la protección de los recursos multiproceso. Además, impide que la estructura interna de los widgets visibles se modifique una vez iniciada una operación de actualización de pantalla. Las API que modificarían el árbol de objetos visibles se bloquean mientras las operaciones de dibujo están en curso y se liberan una vez completada la actualización de la pantalla.

### <a name="system-timers"></a>Temporizadores del sistema 

GUIX proporciona a la aplicación temporizadores periódicos, que a menudo se usan para la actualización periódica de los datos que se muestran en las ventanas de GUIX. Esto se logra a través de un temporizador periódico de ThreadX, que también se usa para realizar efectos en el nivel de sistema de GUIX, como el fundido de entrada y de salida de pantalla, etc.

La aplicación puede crear temporizadores y usar la misma utilidad de temporizador que GUIX usa internamente. Por supuesto, la aplicación también puede crear y usar directamente temporizadores de ThreadX si es necesario. La ventaja de los temporizadores de GUIX es que son muy fáciles de usar y están preconfigurados para funcionar dentro del sistema de procesamiento basado en eventos de GUIX.

Para crear e iniciar un temporizador de GUIX, la aplicación debe invocar la función ***gx_system_timer_start***. Los parámetros de esta función incluyen un puntero al widget que realiza la llamada, el identificador del temporizador (lo que permite que un widget inicie varios temporizadores) y los valores inicial y de tiempo de espera para la reprogramación. Si el valor del tiempo de espera para la reprogramación es 0, el temporizador solo se ejecutará una vez y se eliminará de la lista de temporizadores activos una vez que expire.

Una vez iniciado el temporizador de GUIX, enviará eventos GX_EVENT_TIMEOUT al propietario del temporizador, ya sea una vez o periódicamente según el valor de reprogramación del temporizador. Un temporizador de GUIX puede detenerse llamando a la función de API ***gx_system_timer_stop***.

### <a name="pen-speed-configuration"></a>Configuración de la velocidad del lápiz 

El componente de sistema de GUIX contiene información de configuración relacionada con el seguimiento de la velocidad del lápiz. GUIX genera eventos **GX_EVENT_VERTICAL_FLICK** y **GX_EVENT_HORIZONTAL_FLICK** internamente en función de la velocidad y la distancia de los eventos PEN_DOWN generados por el controlador de entrada táctil, si existe. La aplicación puede configurar la distancia y la velocidad mínimas necesarias para desencadenar estos eventos generados internamente mediante la función de API **_gx_system_pen_configure_**.

### <a name="screen-stack"></a>Pila de pantallas 

El componente de sistema de GUIX proporciona servicios relacionados con la pila de pantallas de GUIX, una funcionalidad opcional que da soporte a una pila de widgets virtuales en la que la aplicación puede insertar, sacar y recuperar pantallas en tiempo de ejecución. La pila de pantallas es útil para administrar sistemas de menús complejos, donde la ruta por la que el usuario puede llegar a varios estados del sistema de menús es variable. Se puede volver al estado anterior en el sistema de menús fácilmente si se inserta primero el estado anterior de la pantalla, después se muestra la nueva pantalla y se permite que la nueva pantalla saque el estado anterior de la pila de pantallas cuando se descarte la pantalla actual.

### <a name="clipboard-maintenance"></a>Mantenimiento del portapapeles 

GUIX admite un portapapeles para copiar y pegar texto en tiempo de ejecución. Esta compatibilidad la proporciona el componente de sistema de GUIX.

### <a name="dirty-list-maintenance"></a>Mantenimiento de la lista de elementos modificados 

GUIX mantiene una lista de widgets modificados, lo que significa que los widgets son visibles y deben volver a dibujarse debido a los cambios de estado o a que han pasado a estar visibles por primera vez. Esta lista de elementos modificados mejora el rendimiento del dibujo ya que permite que GUIX realice una operación de actualización de lienzo para reflejar todos los cambios actuales en el estado de la interfaz de usuario, en lugar de realizar la actualización a medida que se hace cada cambio de la interfaz de usuario.
Esta lista de elementos modificados también se mantiene mediante el componente de sistema de GUIX.

### <a name="animation-control-block-pool"></a>Grupo de bloques de control de animación 

A menudo las aplicaciones desean ejecutar varias secuencias de animación y con frecuencia en paralelo. GUIX mantiene un grupo de bloques de control de animación desde los que la aplicación puede asignar y usar las animaciones. Esto libera a la aplicación de la definición estática de estos bloques de control y permite que se reutilicen en momentos diferentes, en lugar de crear un bloque de control de animación para cada animación que pueda definir la aplicación. El grupo de bloques de control de animación también se mantiene mediante el componente de sistema de GUIX.

### <a name="system-error-handling"></a>Control de errores del sistema 

El controlador de errores del sistema de GUIX está pensado para ayudar a la aplicación a encontrar errores internos del sistema en GUIX que podrían ser más difíciles de determinar desde la perspectiva de las API. Siempre que se produce un error de sistema dentro de GUIX, se llama a la función interna ***_gx_system_error_process***. Esta función guarda el código de error proporcionado e incrementa el número total de errores del sistema detectados. Las variables de error del sistema se definen de la siguiente manera:

UINT **_gx_system_last_error**;

ULONG **_gx_system_error_count**;

Si la aplicación GUIX se comporta de forma extraña, resulta útil consultar la variable de recuento de errores en el depurador. Si se ha establecido, una buena forma de solucionar el problema es establecer un punto de interrupción en la función ***_gx_system_error_process*** y ver cuándo y desde dónde se le llama.

## <a name="guix-canvas-component"></a>Componente de lienzo de GUIX

El componente de lienzo es responsable de todo el procesamiento relacionado con el lienzo. Un lienzo es realmente un búfer de cuadros virtual. La aplicación debe crear al menos un lienzo para generar la salida gráfica.
Normalmente, se crea al menos un lienzo por cada pantalla física que admita el sistema.

Todo el dibujo de GUIX tiene lugar en un lienzo. En sistemas más sencillos o con restricción de memoria, es probable que solo haya un lienzo que esté vinculado directamente al búfer de cuadros visible, mientras que los sistemas con más memoria y requisitos gráficos más avanzados pueden requerir varios lienzos. El hecho de que haya varios lienzos disponibles para una pantalla permite utilizar características como los efectos de fundido de entrada y salida de las ventanas y las pantallas.
Los lienzos pueden ser de uno de dos tipos principales: simples o administrados.

Un lienzo simple es un área de dibujo fuera de la pantalla que usa la aplicación.
GUIX no hace nada directamente con un lienzo simple, pero la aplicación puede usarlo para representar un dibujo complejo en un búfer fuera de pantalla y, a continuación, usar este búfer para actualizar el lienzo visible cuando sea necesario.

El lienzo administrado se muestra automáticamente en el búfer de cuadros de hardware de GUIX. Este lienzo se incluye al crear un lienzo compuesto en los sistemas con memoria suficiente para admitir varios lienzos administrados. Los lienzos administrados tienen un orden Z mantenido por GUIX y recorte de vistas aplicado.

Un lienzo se diferencia de un búfer de cuadros en que es más genérico. En los sistemas con restricción de memoria solo puede haber un lienzo y la memoria de este lienzo puede ser la memoria de búfer de cuadros visible. Sin embargo, en sistemas más complejos que admiten superposiciones gráficas más avanzadas y varios lienzos, se asignan áreas propias de memoria a los lienzos administrados, áreas que son diferentes de la memoria de búfer de cuadros de hardware.
Estos lienzos administrados se representan en el búfer de cuadros visible durante la operación de alternancia o actualización del búfer de cuadros.

En el caso de hardware compatible con varias capas gráficas, es decir, varios búferes de cuadros superpuestos, la aplicación puede enlazar uno o varios lienzos a las capas gráficas de hardware mediante la API ***gx_canvas_hardware_layer_bind***. Este servicio informa al lienzo de que está vinculado a una capa gráfica de hardware determinada; una vez que se ha vinculado, este lienzo intentará utilizar la compatibilidad de hardware para la visibilidad del lienzo (es decir, gx_canvas_show, gx_canvas_hide), la combinación alfa del lienzo (es decir, ***gx_canvas_alpha_set***) y el desplazamiento del lienzo dentro de la pantalla (***gx_canvas_offset_set***).

En el caso de las arquitecturas distintas de la organización de búfer de un solo lienzo y un solo cuadro, el tamaño de un lienzo viene determinado por la aplicación y puede ser diferente del tamaño fijo de un búfer de cuadros.
También puede estar en un desplazamiento seleccionado por la aplicación. Otra información, como el orden Z, se mantiene en el lienzo. Una vez completado el dibujo del lienzo, el controlador de pantalla transfiere el contenido del lienzo a la pantalla física. En algunos sistemas que no tienen suficiente memoria como para disponer de áreas de memoria independientes para el lienzo y el búfer de cuadros, la actualización del lienzo se realiza directamente en la pantalla física por medio del controlador de pantalla.

### <a name="canvas-creation"></a>Creación de lienzos 

Un objeto de lienzo se puede crear durante la inicialización o en cualquier momento durante la ejecución de los subprocesos de la aplicación. No hay ningún límite en el número de objetos de lienzo que puede crear una aplicación. Sin embargo, la mayoría de las aplicaciones crearán uno solo para todo el dibujo de GUIX.

### <a name="canvas-control-block"></a>Bloque de control del lienzo 

Las características de cada objeto de lienzo se encuentran en su bloque de control **GX_CANVAS** y se definen en **_gx_api. h_**. La aplicación proporciona la memoria necesaria para un objeto de lienzo, que se puede ubicar en cualquier parte de la memoria. Sin embargo, es más común que el bloque de control y el área de dibujo del objeto de lienzo se creen como una estructura global, mediante su definición fuera del ámbito de cualquier función.

### <a name="canvas-alpha-channel"></a>Canal alfa del lienzo

GUIX admite la combinación alfa de los colores de primer plano y de fondo en muchos niveles, incluido el canal alfa del mapa de bits (que especifica una relación de combinación por píxel), el valor alfa del pincel (que especifica la relación de combinación de un pincel de 16 bpp y profundidades de color superiores) y el valor alfa del lienzo (que especifica la relación de combinación de un lienzo superpuesto).

El valor alfa de un lienzo se usa cuando varios lienzos se componen juntos para su presentación en el búfer de cuadros. Si el orden Z de los lienzos es tal que un lienzo está por encima de otros, se puede establecer el valor alfa de ese lienzo para combinarlo con los que se encuentran detrás. La modificación rápida del valor alfa de un lienzo se usa para proporcionar efectos de transición de fundido de entrada a la pantalla, pero este valor alfa del lienzo se puede usar de muchas maneras.

Si un lienzo se enlaza a una capa gráfica de hardware mediante gx_canvas_hardware_layer_bind(), GUIX intentará implementar la combinación alfa del lienzo usando la compatibilidad de hardware, lo que minimiza la sobrecarga de software asociada a la combinación de un lienzo superpuesto.

Los valores alfa van desde 0 hasta 255, donde un valor de 0 significa que el píxel es totalmente transparente y los valores mayores que 0 indican cada vez menor transparencia, que solo se admite en controladores de pantalla que se ejecutan a 16 bpp y valores superiores, a menos que se proporcione asistencia de hardware para la combinación de lienzos.

### <a name="canvas-offset"></a>Desplazamiento del lienzo 

Un lienzo se puede desplazar dentro del búfer de cuadros visible invocando el servicio de API ***gx_canvas_offset_set***. Los desplazamientos de lienzo se suelen usar para implementar animaciones de sprites. Si un lienzo se enlaza a una capa gráfica de hardware mediante la invocación de la función de API ***gx_canvas_hardware_layer_bind***, GUIX intentará implementar los cambios de desplazamiento del lienzo mediante la compatibilidad de hardware, minimizando así la sobrecarga de software asociada al cambio de posición del lienzo.

### <a name="canvas-drawing"></a>Dibujo del lienzo 

El componente de lienzo de GUIX proporciona una API de dibujo completa a la aplicación. Antes de que se puedan invocar las API de dibujo, como ***gx_canvas_line_draw*** o ***gx_canvas_pixelmap_draw***, se debe abrir el lienzo de destino donde se va a dibujar invocando la función de API ***gx_canvas_drawing_initiate***. Esta función prepara un lienzo para dibujar y crea un ***contexto de dibujo***.

Las API de dibujo que se representan en el lienzo, como ***gx_canvas_line_draw** _ o _*_gx_canvas_text_draw_*_, usan los parámetros que se encuentran en el pincel del contexto del dibujo actual para definir el estilo de línea, el ancho y los colores. Estos parámetros de pincel se modifican mediante una llamada a las funciones de API _*_gx_context_brush_define_*_, _*_gx_context_brush_set_**, ***gx_context_brush_style_set**_ y otras funciones de API similares una vez que se ha establecido un contexto de dibujo con una llamada a _*_gx_canvas_drawing_initiate_**.

Cuando GUIX invoca las funciones de dibujo de ventanas y widgets como parte de una operación de actualización de lienzo diferida, se abre el lienzo de destino para dibujar antes de llamar a las funciones de dibujo de widget. Por lo tanto, las funciones de dibujo de widget estándar no necesitan abrir el lienzo de destino, ya se ha abierto antes.

En algunos casos, es posible que la aplicación desee forzar el dibujo inmediato en un lienzo. En este caso, la aplicación puede realizar los pasos siguientes.

1. Llamar a la función de API ***gx_canvas_drawing_initiate***, pasando el lienzo de destino y el rectángulo dentro de ese lienzo en el que desea dibujar. 

2. Llamar a cualquier número de API de dibujo de lienzo para lograr el dibujo deseado.

3. Llamar a la función de API ***gx_canvas_drawing_complete*** para indicar que se ha completado el dibujo. Esto vacía el lienzo en el búfer de cuadros visible o también desencadena una operación de alternancia de búfer, en función de la arquitectura de la memoria del sistema.

### <a name="drawing-apis"></a>API de dibujo 

Hay varias primitivas de dibujo principales que GUIX precisa para dibujar todos los elementos visuales de la pantalla. El software de la aplicación también puede invocar estas API de dibujo, normalmente como parte de una función de dibujo de widget personalizada. Estas API de dibujo en el lienzo de GUIX realizan la validación de parámetros y el recorte y, a continuación, pasan las coordenadas del dibujo recortado al controlador de pantalla para las implementaciones de dibujo específicas del hardware y del formato de color. Estas funciones de API de dibujo se definen como se indica a continuación.

- gx_canvas_alpha_set
- gx_canvas_arc_draw
- gx_canvas_block_move
- gx_canvas_circle_draw
- gx_canvas_ellipse_draw
- gx_canvas_glyphs_draw
- gx_canvas_hardware_layer_bind
- gx_canvas_hide
- gx_canvas_line_draw
- gx_canvas_offset_set
- gx_canvas_pie_draw
- gx_canvas_pixel_draw
- gx_canvas_pixelmap_blend
- gx_canvas_pixelmap_rotate
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw
- gx_canvas_rotated_text_draw
- gx_canvas_shift
- gx_canvas_show
- gx_canvas_text_draw

La API de dibujo se invoca por medio de la API de lienzo de GUIX y todo el dibujo se realiza mediante funciones de API gx_canvas_*. El dibujo se realiza utilizando el pincel actual en el contexto del dibujo actual. Cualquiera de las funciones anteriores de dibujo de formas puede crear un contorno, rellenar con color sólido o rellenar con un mapa de píxeles, según se defina en el pincel actual. Para modificar el ancho, el color o el relleno del contorno de la forma, se usan las funciones de API gx_context_brush_* para definir el pincel en el contexto del dibujo actual.

Las API de dibujo del nivel de aplicación anteriores no realizan el dibujo real en el lienzo, sino que comprueban los parámetros del autor de la llamada antes de invocar la función de dibujo del nivel de controlador de pantalla. La función de dibujo del nivel de controlador es la que realmente escribe los datos de píxeles en la memoria del lienzo.

GUIX proporciona funciones de dibujo de controlador de pantalla genéricas o estándar para varias profundidades de color, como 1, 2, 4, 8, 16, 24 y 32 bits por píxel (bpp). En algunos casos, la implementación de dibujo de software predeterminada se sustituye por implementaciones aceleradas por hardware para los destinos de hardware que proporcionan un acelerador de dibujo 2D.

### <a name="color-depth"></a>Profundidad de color 

GUIX admite profundidades de color de hasta 32 bpp, así como la opción monocroma y la escala de grises. La compatibilidad del tipo de profundidad de color viene determinada en gran medida por la funcionalidad de la pantalla física subyacente y también afecta a la cantidad de memoria necesaria para el área de dibujo del lienzo. A continuación se muestra una lista de profundidades de color compatibles junto con una breve descripción de las variaciones dentro de esa profundidad de color.

| Formato de&nbsp;color       | Descripción                                                                                                   |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| Monocromo de 1 bit   | Formato empaquetado de 1 bit por píxel.                                                                                                   |
| Escala de grises de 2 bits    | 4 niveles de gris, formato empaquetado de cuatro píxeles por byte.                                                                                      |
| Escala de grises de 4 bits    | 16 niveles de gris, formato empaquetado de dos píxeles por byte.                                                                                      |
| Color de 4 bits        | Una organización de memoria plana de formato VGA.                                                                                         |
| Escala de grises de 8 bits    | 256 niveles de gris                                                                                                                  |
| Modo de paleta de 8 bits | 1 byte por píxel usado como índice de paleta                                                                                           |
| Modo r:g:b de 8 bits   | Un formato r:g:b 2:3:2 que se utiliza con menos frecuencia.                                                                                         |
| 16 bits             | Cada píxel requiere dos bytes. El orden de bytes puede ser r:g: b o b:g:r. Normalmente usa una estructura 5:6:5, pero también puede ser 5:5:5 o a:r:g:b 4:4:4:4. |
| 24 bits             | Cada píxel requiere 3 bytes (formato empaquetado) o 4 (formato no empaquetado). Puede usar un orden de bytes r:g:b o b:g:r, según precise el hardware. |
| 32 bits             | Cada píxel requiere 4 bytes con un canal alfa. Puede usar un orden de bytes a:r:g:b o b:g:r:a, según determine el hardware.              |

### <a name="mouse-support"></a>Compatibilidad con el mouse 

GUIX admite el dibujo de un cursor del mouse en cualquier lienzo que se desee. El cursor del mouse puede dibujarse en el software o ser compatible con la superposición de cursor de hardware. En cualquier caso, la API que se proporciona a la aplicación y que está relacionada con la compatibilidad con el cursor del mouse es la misma tanto si se usa el dibujo del cursor del mouse de software o hardware.

La compatibilidad con el mouse de GUIX solo está habilitada si se define `#define GX_MOUSE_SUPPORT` en el archivo de encabezado gx_user.h antes de compilar la biblioteca de GUIX.

La aplicación debe definir el cursor del mouse y la zona activa mediante la función de API ***gx_canvas_mouse_define***. Esta API acepta un puntero al lienzo en el que se debe dibujar la imagen del cursor y un puntero a una estructura **GX_MOUSE_CURSOR_INFO**, que define la imagen del cursor del mouse y la zona activa de la imagen del mouse respecto a la esquina superior izquierda de la imagen.

## <a name="guix-display-component"></a>Componente de pantalla de GUIX 

El componente de pantalla es fundamental en GUIX, ya que administra el procesamiento de todos los objetos de pantalla, que en sí contienen uno o varios lienzos, widgets y ventanas. El componente de pantalla también interactúa con el controlador de pantalla de hardware subyacente asociado a cada pantalla por medio de una serie de punteros de función.

### <a name="display-creation"></a>Creación de la pantalla 

El objeto de pantalla se puede crear durante la inicialización o en cualquier momento durante la ejecución de los subprocesos de la aplicación. Normalmente, una aplicación crea un objeto de pantalla para administrar cada pantalla física. Si ha usado GUIX Studio para definir la aplicación y las pantallas físicas disponibles, usará la función API gx_studio_display_configure para crear e inicializar cada una de las pantallas.

### <a name="display-control-block"></a>Bloque de control de la pantalla 

Las características de cada objeto de pantalla se encuentran en su bloque de control ***GX_DISPLAY** _ y se definen en _*_gx_api.h_**. La aplicación proporciona la memoria necesaria para un objeto de pantalla, que se puede ubicar en cualquier parte de la memoria. Sin embargo, es más habitual que el bloque de control de la pantalla forme una estructura global mediante su definición fuera del ámbito de cualquier función.

### <a name="resource-management"></a>Administración de recursos 

Los recursos son componentes de interfaz de usuario que la aplicación necesita, pero no son código de aplicación. Los recursos son datos de la aplicación y normalmente se definen de forma estática. Entre los tipos de recursos se incluyen mapas de píxeles, fuentes, colores y cadenas. Estos recursos se pueden cambiar en cualquier momento, normalmente sin cambiar el software de la aplicación. Es importante mantener el almacenamiento de los recursos y las referencias a ellos separados del software de la aplicación para permitir el cambio de la apariencia de la interfaz de usuario sin necesidad de cambiar el código de la aplicación, ya que los cambios en el software de la aplicación suelen requerir los procedimientos de prueba y comprobación asociados.

El módulo de ***pantalla*** de GUIX proporciona funciones de administración para todos los recursos que dependen de la profundidad de color y el formato de la pantalla. Estas funciones incluyen el mantenimiento de las tablas activas de mapas de píxeles, fuentes y colores. El recurso de la tabla de cadenas se mantiene en el módulo del sistema de GUIX, ya que normalmente no es necesario cambiar los recursos de cadena en función del formato y la profundidad de color.

El software de la aplicación hace referencia a los recursos por su identificador, que es un índice en la tabla de recursos correspondiente. Esto permite cambiar la tabla; por ejemplo, podría cambiarse la tabla de colores cuando un producto cambia de "modo diurno" a "modo nocturno" y los valores del identificador de color seguirían siendo los mismos.

Los recursos de la aplicación se escriben en un archivo de recursos (o un conjunto de archivos de recursos) mediante la aplicación GUIX Studio. Las fuentes, los mapas de píxeles y los colores predeterminados se proporcionan automáticamente cuando se crea un nuevo proyecto de GUIX Studio, pero estos valores predeterminados se reemplazan fácilmente a medida que se define la apariencia de la aplicación.

Es importante tener en cuenta que los identificadores de recursos de los colores, fuentes y mapas de píxeles no se pueden resolver en sus valores de color, fuente o mapa de píxeles reales hasta que se conozca el componente de pantalla activo. Dado que la arquitectura de GUIX admite varias pantallas activas, los identificadores de recursos solo se pueden resolver en sus valores de recurso cuando un widget y su identificador de recurso asociado se pueden resolver en una pantalla específica. Esta propiedad se conoce como enlace dinámico. El identificador de recurso de una propiedad como el color de texto (por ejemplo, el identificador de recurso de **GX_COLOR_ID_TEXT**) podría resolverse en un valor R:G:B de 16 bits para blanco cuando se usa en una pantalla, pero resolverse en un valor de color negro monocromo cuando se usa en otra pantalla.

En la práctica, este enlace dinámico de los identificadores de recursos con sus valores significa que los componentes internos de GUIX y del software de la aplicación solo deberían resolver los identificadores de recursos en los valores de recurso dentro de un contexto de dibujo activo. El contexto de dibujo activo especifica la pantalla activa actualmente, lo que permite a GUIX resolver cada identificador de recurso en un valor de recurso específico. Si se precisa el software de la aplicación para encontrar un valor de recurso específico fuera de un contexto de dibujo, lo mismo puede suceder con los widgets visibles. Los widgets visibles se vinculan a una ventana raíz que también se puede usar para resolver el lienzo activo y la pantalla para ese widget.

Si se ha creado un widget pero aún no se ha mostrado (es decir, no se ha vinculado a ninguna ventana raíz u otro elemento principal visible), los identificadores de recurso asociados a ese widget solo se pueden resolver en un valor de recurso específico mediante la indexación directa en la tabla de recursos asignada a una pantalla específica. Este acceso directo a una tabla de recursos específica puede realizarse de forma segura mediante el software de la aplicación, pero nunca se realiza en el software interno de la biblioteca de GUIX.

### <a name="widget-defaults"></a>Valores predeterminados de widget 

El componente de pantalla de GUIX también proporciona definiciones predeterminadas para varios atributos de widget. A menos que la aplicación especifique lo contrario, los widgets y ventanas se crean con estos atributos del sistema. Se componen principalmente de fuentes, colores y mapas de bits que se mantienen en las tablas de recursos del sistema. El componente de pantalla de GUIX también mantiene atributos adicionales para la apariencia predeterminada de la barra de desplazamiento.

La configuración de color predeterminada se define mediante la tabla de colores asignada a cada pantalla y los identificadores de color predeterminados predefinidos. Estos identificadores de colores predeterminados incluyen los siguientes.

| Identificador de color | Descripción |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| GX_COLOR_ID_CANVAS | Color predeterminado del lienzo (es decir, fondo de la pantalla) |
| GX_COLOR_ID_WIDGET_FILL | Color predeterminado de relleno del widget |
| GX_COLOR_ID_WINDOW_FILL | Color predeterminado de relleno de la ventana |
| GX_COLOR_ID_DISABLED_FILL | Color predeterminado de relleno del widget deshabilitado |
| GX_COLOR_ID_DEFAULT_BORDER | Color predeterminado de borde del widget |
| GX_COLOR_ID_WINDOW_BORDER | Color predeterminado de borde de la ventana |
| GX_COLOR_ID_TEXT | Color predeterminado del texto |
| GX_COLOR_ID_SELECTED_TEXT | Color predeterminado del texto seleccionado |
| GX_COLOR_ID_DISABLED_TEXT | Color predeterminado del texto deshabilitado |
| GX_COLOR_ID_SELECTED_TEXT_FILL | Color predeterminado de relleno del texto seleccionado |
| GX_COLOR_ID_READONLY_TEXT | Color predeterminado del texto de solo lectura |
| GX_COLOR_ID_READONLY_FILL | Color predeterminado de relleno del texto de solo lectura |
| GX_COLOR_ID_SCROLL_FILL |    Color de relleno de la barra de desplazamiento |
| GX_COLOR_ID_SCROLL_BUTTON | Color de relleno del botón de la barra de desplazamiento |
| GX_COLOR_ID_SHADOW | Color predeterminado de la sombra |
| GX_COLOR_ID_SHINE | Color predeterminado del resaltado |
| GX_COLOR_ID_BUTTON_BORDER | Color de borde del widget de botón |
| GX_COLOR_ID_BUTTON_UPPER | Color de relleno superior del widget de botón |
| GX_COLOR_ID_BUTTON_LOWER | Color de relleno inferior del widget de botón |
| GX_COLOR_ID_BUTTON_TEXT | Color de texto del widget de botón |
| GX_COLOR_ID_TEXT_INPUT_TEXT | Color de texto del widget de entrada de texto |
| GX_COLOR_ID_TEXT_INPUT_FILL | Color de relleno de la entrada de texto |
| GX_COLOR_ID_SLIDER_TICK | Color usado para dibujar marcas de graduación del control deslizante |
| GX_COLOR_ID_SLIDER_GROOVE_BOTTOM | Color usado para dibujar la ranura del control deslizante |
| GX_COLOR_ID_SLIDER_NEEDLE_OUTLINE | Color usado para dibujar el contorno de la aguja |
| GX_COLOR_ID_SLIDER_NEEDLE_FILL | Color usado para rellenar la aguja del control deslizante |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE1 | Color usado para dibujar el resaltado de la aguja |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE2 | Color usado para dibujar la sombra de la aguja |

Estos valores de identificador de color se asignan a un valor de color específico, según se define en la tabla de colores asignada a cada pantalla. Estos valores predeterminados se pueden cambiar como un grupo para una pantalla mediante una llamada a la función de API ***gx_display_color_table_set***. Si usa GUIX Studio, la tabla de colores de la pantalla se inicializa automáticamente cuando la aplicación llama a la función ***gx_studio_display_configure***.

El componente de pantalla de GUIX también mantiene una tabla de fuentes predeterminadas. En esta tabla se define la fuente que utiliza cada tipo de widget, a menos que la aplicación indique otra específicamente. Los identificadores de la tabla de fuentes de pantalla predefinidas incluyen los siguientes valores.

| Identificador de&nbsp;fuente | Descripción |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------|
| GX_FONT_ID_DEFAULT | Fuente predeterminada usada cuando no se define ninguna fuente específica. |
| GX_FONT_ID_BUTTON | Fuente predeterminada usada para todo el texto de los botones. |
| GX_FONT_ID_TEXT_INPUT | Fuente predeterminada utilizada para los campos de edición de texto. |

El identificador de fuente que se utiliza en cualquier widget de tipo de texto se puede volver a asignar mediante la API **gx_<tipo_de_widget>_font_set** proporcionada para cada tipo de widget relacionado con texto. La tabla de fuentes completa se puede volver a asignar mediante una llamada a la función de API **gx_display_font_table_set**.

### <a name="scrollbar-appearance"></a>Apariencia de la barra de desplazamiento 

El componente de pantalla de GUIX también mantiene la configuración predeterminada de la apariencia de la barra de desplazamiento para esa pantalla. Esta configuración se establece mediante la estructura **GX_SCROLLBAR_APPEARANCE** que se define a continuación. La pantalla de GUIX mantiene una estructura de apariencia de la barra de desplazamiento para las barras de desplazamiento verticales y otra para las horizontales. La aplicación puede modificar la apariencia predeterminada de la barra de desplazamiento de cualquier pantalla inicializando una estructura **GX_SCROLLBAR_APPEARANCE** e invocando la función de API ***gx_display_scroll_appearance_set***.

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
| Miembros de la estructura GX_SCROLLBAR_APPEARANCE | Descripción |
| --- | --- |
| gx_scroll_width | Ancho de una barra de desplazamiento vertical o altura de una barra de desplazamiento horizontal, en píxeles. |
| gx_scroll_thumb_width | Ancho de los botones de desplazamiento y final, en píxeles. |
| gx_scroll_thumb_travel_max | Desplazamiento desde el final de la barra de desplazamiento hasta el punto máximo del recorrido del botón de desplazamiento. |
| gx_scroll_fill_pixelmap | Mapa de píxeles que se usa para rellenar el fondo de la barra de desplazamiento. |
| gx_scroll_thumb_pixelmap | Mapa de píxeles que se usa para dibujar el botón de control de desplazamiento. |
| gx_scroll_up_pixelmap | Mapa de píxeles que se usa para dibujar el botón de desplazamiento hacia arriba. |
| gx_scroll_down_pixelmap | Mapa de píxeles que se usa para dibujar el botón de desplazamiento hacia abajo. |
| gx_scroll_fill_color | Identificador del color que se usa para rellenar el fondo de la barra de desplazamiento. |
| gx_scroll_button_color | Identificador del color que se usa para rellenar el botón de control de desplazamiento de la barra. |

Además de estos valores predeterminados para fuentes, colores y estilos, la aplicación puede establecer cualquiera de estos parámetros de forma específica para cada caso según sea necesario mediante la API proporcionada por cada tipo de widget.

### <a name="skinning-and-themes"></a>Cambio del aspecto visual y temas

El cambio del aspecto visual permite que los widgets y las ventanas de GUIX cambien fácilmente su apariencia base; es decir, al cambiar la "máscara" en un lugar, se cambiará la apariencia base de todos los widgets y ventanas asociados.

Para volver a cambiar el aspecto visual de la aplicación GUIX, es necesario proporcionar una nueva tabla de colores, fuentes o mapas de píxeles a las tablas de recursos del componente de pantalla de GUIX. Dado que todos los widgets de GUIX hacen referencia a su color, mapa de bits o fuente por identificador de recurso, al indicar una nueva tabla de recursos todos los widgets de GUIX empiezan a usar los nuevos colores y mapas de píxeles cuando se dibujan en la pantalla deseada.

Un conjunto de fuentes, colores y mapas de píxeles diseñado para funcionar de forma combinada con el fin de proporcionar una apariencia atractiva se denomina *tema*. Un tema define un conjunto de tablas de recursos y el tamaño de cada una de estas tablas. La aplicación GUIX Studio permite definir cualquier número de temas para cualquier pantalla. Es necesario pasar el índice de tema inicial a la función generada por GUIX Studio ***gx_studio_display_configure***, que instala el tema inicial en la pantalla creada. El tema activo de una pantalla se puede cambiar en cualquier momento llamando a la función ***gx_display_theme_install***.

### <a name="root-window"></a>Ventana raíz

Cuando una aplicación crea un lienzo visible, también debe crear una ventana raíz para ese lienzo. Esta ventana especial actúa básicamente como un contenedor de todos los widgets y ventanas de la aplicación de nivel superior. La ventana raíz dibuja el fondo del lienzo y, dado que se deriva de la clase **GX_WINDOW**, también puede tener papel tapiz. Para cambiar el color de fondo de la pantalla o el lienzo, solo tiene que cambiar el color de relleno de la ventana raíz asociada a ese lienzo.

Si usa la función generada por GUIX Studio denominada ***gx_studio_display_configure*** para configurar las pantallas, el lienzo y la ventana raíz de cada pantalla se crean automáticamente como parte de esta función de inicialización.

### <a name="anti-aliasing"></a>Suavizado de contorno 

El suavizado de contorno es una característica opcional de GUIX que se usa para suavizar líneas, curvas y fuentes. El suavizado de contorno solo se admite cuando se ejecuta con un controlador de pantalla que utiliza una profundidad de color de 16 bpp o superior.

El dibujo de líneas con suavizado de contorno se habilita estableciendo la función **GX_BRUSH_ALIAS** en el pincel activo. Esto se aplica a las líneas dibujadas directamente y a líneas como el borde de un polígono o un círculo.

El dibujo de texto con suavizado de contorno se habilita mediante el uso de una fuente suavizada generada por la aplicación GUIX Studio. Al crear la fuente, se especifica si se debe generar con suavizado de contorno o como binaria.
Las fuentes con suavizado de contorno de GUIX usan 16 niveles de transparencia para cada píxel.

### <a name="clipping"></a>Recorte 

El componente de pantalla de GUIX admite el recorte internamente. También se admite en los niveles de ventana y widget de la arquitectura de elementos principales y secundarios mantenida por los widgets de GUIX. No se puede dibujar ninguna ventana o ningún widget fuera del área del widget y tampoco se permite dibujar un widget fuera del área de su elemento principal.

Esto también impide que los widgets se dibujen en coordenadas de píxeles que se encuentran fuera de la memoria del lienzo, lo que podría provocar daños en la memoria o un error del sistema. No se pueden dibujar widgets fuera del área del widget, del área de su elemento principal ni más allá de la extensión del lienzo.

Además, los widgets solo pueden dibujar en áreas que se han marcado previamente como modificadas. Esto evita que se dibuje una ventana completa; por ejemplo, cuando solo se revela una esquina de la ventana. Solo se marca como modificada la parte de la ventana que realmente necesita actualizarse y, por tanto, la función de dibujo de la ventana solo actualiza realmente los píxeles del área modificada.

El componente de pantalla de GUIX aplica estos algoritmos de recorte antes de invocar las funciones de dibujo en el nivel de controlador.

### <a name="views"></a>Vistas 

GUIX siempre mantiene un conjunto de vistas para cada ventana raíz y cada ventana secundaria de la ventana raíz. Las vistas son un área de recorte dinámica que se determina en tiempo de ejecución y que cambia a medida que se modifica la posición de la ventana y el orden Z.
GUIX usa vistas para evitar que una ventana o un widget en segundo plano se dibujen sobre una ventana o widget en primer plano. Las vistas imponen la disciplina del orden Z. Además, son importantes por motivos de eficacia, ya que impiden que una ventana en segundo plano dibuje en cualquier área del lienzo que no se pueda ver. Si una ventana está completamente cubierta por otra ventana, no se permitirá que la ventana cubierta dibuje en el lienzo, incluso si intenta hacerlo.

### <a name="display-driver-interface"></a>Interfaz del controlador de pantalla 

Los controladores de pantalla de GUIX son responsables de todas las interacciones con la pantalla física subyacente. Estos controladores tienen tres funciones básicas: inicialización, dibujo y visualización del búfer de cuadros.
La inicialización es responsable de preparar el hardware de la pantalla física, informando a GUIX de sus propiedades y de qué funciones de dibujo específicas deben usarse. La inicialización del controlador de pantalla principal se llama desde la función ***gx_display_create*** de GUIX. Además, el subproceso de GUIX también llamará a una inicialización del controlador de pantalla secundario desde el contexto del subproceso. Este controlador de pantalla secundario solo es necesario si el controlador requiere servicios de RTOS durante su inicialización; por ejemplo, interrupciones de dispositivo o solicitudes ***tx_thread_sleep*** para el retraso entre los pasos del proceso de inicialización.

Una vez completada la inicialización, el controlador de pantalla es responsable de cualquier dibujo directo que pueda realizarse en el hardware de la pantalla física.
Por último, el controlador de pantalla es responsable de mostrar el búfer de cuadros.

## <a name="guix-widget-component"></a>Componente de widget de GUIX

Un widget de GUIX es un elemento gráfico visible. Hay componentes de GUIX que no son visibles, como los temporizadores y las funciones de utilidad matemáticas.
Sin embargo, todos los componentes visibles se derivan del componente de widget de GUIX básico. Un widget de GUIX es el bloque de creación principal de la pantalla de GUIX; todos los demás elementos gráficos se derivan de la funcionalidad del widget base.

Los widgets de GUIX utilizan una implementación orientada a objetos con compatibilidad total de herencia. Esto se logra mediante ANSI C, lo que da como resultado unos requisitos de memoria y procesamiento lo más pequeños posible. Cuando indicamos que un widget determinado, como **GX_BUTTON**, se *deriva de* otro widget, como el widget base **GX_WIDGET**, nos referimos a que la estructura de control de **GX_BUTTON** contiene todas las variables de miembro y punteros de función de **GX_WIDGET**, con algunas variables adicionales específicas de **GX_BUTTON**. GUIX crea capas de widgets de este modo, de modo que los widgets más complejos se basan siempre en un widget más sencillo anterior. Este modelo jerárquico de derivación facilita el aprendizaje de las API que se usan para modificar los parámetros del widget. Si desea modificar el color de un botón, por ejemplo, usará la misma API que usa para modificar el color de un widget; es decir, ***gx_widget_fill_color_set***.

La organización de los widgets visibles se mantiene en forma de elementos principales y secundarios mediante listas estructuradas de árbol que vinculan los widgets secundarios a sus elementos principales. Los elementos secundarios heredan características de sus elementos principales, como las vistas en las que pueden dibujar y el lienzo en el que dibujan.
Los widgets secundarios pueden tener sus propios widgets secundarios, que heredan a su vez varias características del elemento principal. Las características de cualquier widget se pueden redefinir explícitamente por medio de varias llamadas API de GUIX.

### <a name="widget-creation"></a>Creación de widgets 

Un objeto de widget se puede crear durante la inicialización o en cualquier momento durante la ejecución de los subprocesos de la aplicación. No hay ningún límite en el número de objetos de widget que puede crear una aplicación. Tampoco hay ningún límite en el número de elementos secundarios que puede tener cualquier widget, dentro de los límites de memoria del hardware de destino.

Cada tipo de widget tiene su propia función de creación, como ***gx_button_create** _ o _*_gx_prompt_create_**. Los tres primeros parámetros de estas funciones son siempre los mismos: un puntero a la estructura de control del widget, un puntero de cadena al nombre del widget y un puntero al elemento principal del widget. Cada función de creación puede tener cualquier número de parámetros adicionales en función de los requisitos de ese tipo de widget concreto.

### <a name="widget-control-block"></a>Bloque de control del widget 

Las características de cada objeto de widget se encuentran en su bloque de control ***GX_WIDGET** _ y se definen en **_gx_api.h_**. La aplicación proporciona la memoria necesaria para un objeto de widget, que se puede ubicar en cualquier parte de la memoria. Sin embargo, es más habitual que el bloque de control del objeto de widget forme una estructura global mediante su definición fuera del ámbito de cualquier función. Si usa GUIX Studio, los bloques de control de widget se pueden asignar estáticamente en el archivo de especificaciones generadas por Studio, o bien los puede asignar la aplicación dinámicamente.

### <a name="dynamic-widget-control-block-allocation-and-de-allocation"></a>Asignación y desasignación dinámica de bloques de control de widget 

Si usa la asignación dinámica de bloques de control, deberá definir dos funciones que GUIX usará para asignar y liberar la memoria necesaria para los bloques de control de widget. Las funciones de administración de memoria se pasan al componente de sistema de GUIX por medio de la función de API ***gx_system_memory_allocator_set***. Esta función permite pasar dos punteros de función a GUIX: el primero es un puntero a una función de asignación de memoria y el segundo un puntero a una función de liberación de memoria. Lo más frecuente es que implemente estas funciones mediante grupos de bytes de ThreadX, pero el diseño de GUIX le permite implementar la administración dinámica de la memoria de la manera que prefiera.

La asignación dinámica de widgets se suele emplear dentro del archivo de especificaciones de aplicación generado por Studio, cuando se selecciona la opción de asignación dinámica en el campo de propiedades del widget de Studio. Sin embargo, también puede usar la asignación dinámica de bloques de control dentro de la aplicación. En este caso, debe invocar la función de API ***gx_widget_allocate** _ para asignar el bloque de control del widget. A continuación, cuando cree el widget, asegúrese de pasar la marca de estilo _ *GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** (junto con cualquier otra marca de estilo necesaria) a la función de creación del widget. Esta marca se usa para marcar el widget como asignado dinámicamente en el campo de estado del widget. Si el widget se elimina posteriormente mediante **_gx_widget_delete_**, GUIX comprobará este campo de estado y llamará automáticamente a la función de desasignación de memoria para asegurarse de que no haya fugas de memoria.

> [!IMPORTANT]
> Un widget creado mediante un bloque de control asignado dinámicamente se debe crear con la marca de estilo **GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** para evitar la pérdida de memoria.

### <a name="types"></a>Tipos

GUIX proporciona un completo conjunto totalmente funcional de widgets integrados. Como se mencionó anteriormente, todos los widgets especializados se derivan del widget base. A continuación se incluye una lista de los widgets integrados en GUIX:

**GX_TYPE_WIDGET**

**GX_TYPE_BUTTON**

**GX_TYPE_TEXT_BUTTON**

**GX_TYPE_MULTI_LINE_TEXT_BUTTON**

**GX_TYPE_RADIO_BUTTON**

**GX_TYPE_CHECKBOX**

**GX_TYPE_PIXELMAP_BUTTON**

**GX_TYPE_ICON_BUTTON**

**GX_TYPE_ICON**

**GX_TYPE_SPRITE**

**GX_TYPE_SLIDER**

**GX_TYPE_PIXELMAP_SLIDER**

**GX_TYPE_VERTICAL_SCROLL**

**GX_TYPE_HORIZONTAL_SCROLL**

**GX_TYPE_PROGRESS_BAR**

**GX_TYPE_PROMPT**

**GX_TYPE_NUMERIC_PROMPT**

**GX_TYPE_PIXELMAP_PROMPT**

**GX_TYPE_NUMERIC_PIXELMAP_PROMPT**

**GX_TYPE_SINGLE_LINE_TEXT_INPUT**

**GX_TYPE_MULTI_LINE_TEXT_VIEW**

**GX_TYPE_MULTI_LINE_TEXT_INPUT**

**GX_TYPE_WINDOW**

**GX_TYPE_ROOT_WINDOW**

**GX_TYPE_VERTICAL_LIST**

**GX_TYPE_HORIZONTAL_LIST**

**GX_TYPE_POPUP_LIST**

**GX_TYPE_DROP_LIST**

**GX_TYPE_LINE_CHART**

**GX_TYPE_DIALOG**

**GX_TYPE_KEYBOARD**

**GX_TYPE_SCROLL_WHEEL**

**GX_TYPE_TEXT_SCROLL_WHEEL**

**GX_TYPE_STRING_SCROLL_WHEEL**

**GX_TYPE_NUMERIC_SCROLL_WHEEL**

**GX_TYPE_CIRCULAR_GAUGE**

**GX_TYPE_RADIAL_PROGRESS_BAR**

**GX_TYPE_RADIAL_SLIDER**

**GX_TYPE_MENU_LIST**

**GX_TYPE_MENU**

**GX_TYPE_ACCORDION_MENU**

**GX_TYPE_TREE_VIEW**


### <a name="styles"></a>Estilos

Los estilos de los widgets se componen de elementos como las propiedades de borde (sin borde o borde elevado, hundido, fino o grueso), así como las propiedades de determinados tipos de widget, como se indicó anteriormente. Las marcas de estilo del widget suponen el método más sencillo para modificar la apariencia de cualquier widget.
El estilo inicial del widget es siempre un parámetro que se pasa a la función de creación específica del tipo de widget.

### <a name="colors"></a>Colores 

Los widgets se dibujan a sí mismos con los colores definidos en la tabla de colores del sistema.
Se definen identificadores de color para el fondo del lienzo, el color predeterminado de relleno del widget, el color de relleno del botón, el color de relleno de los widgets de texto, el color de relleno de la ventana y otros valores predeterminados de color. Además, en los objetos **GX_WINDOW** se puede mostrar un mapa de bits o un papel tapiz mientras se rellena el cliente de la ventana.

El método más sencillo para cambiar la combinación predeterminada de colores es usar GUIX Studio y crear o definir una combinación de colores que cumpla sus requisitos.
También puede definir la combinación de colores manualmente creando una matriz de valores de GX_COLOR e invocando la función de API gx_system_color_table_set.

### <a name="event-notification"></a>Notificación de evento 

Los eventos de GUIX son solicitudes realizadas a uno o varios widgets para hacer una acción concreta y notificaciones para advertir a los widgets sobre las entradas de usuario y los cambios de estado internos del sistema. Por ejemplo, cuando un widget obtiene el foco, se envía el evento **GX_EVENT_FOCUS_GAINED** al widget por medio del servicio de API ***gx_system_event_send***.

Los eventos se pasan a través de la cola de eventos de GUIX; cada evento es una instancia de la estructura de datos **GX_EVENT**. Esta estructura de datos **GX_EVENT** se define en ***gx_api. h***; sin embargo, los campos más importantes de la estructura son **gx_event_type**, **gx_event_sender**, **gx_event_target** y **gx_event_payload**.

El campo **gx_event_type** se utiliza para identificar la clase de evento concreta. El tipo de evento indica si es, por ejemplo, un evento **GX_EVENT_PEN_DOWN** o un evento **GX_EVENT_TIMER**. **gx_event_payload** es una unión de varios campos de datos, de los que no todos son válidos para cada tipo de evento.
Primero se usa el campo de tipo de evento, antes de examinar los demás campos de datos del evento.

El campo **gx_event_sender** contiene el identificador del widget que generó el evento, si este es una notificación de widget secundario.

El campo **gx_event_target** se puede usar para enrutar eventos definidos por el usuario a una ventana o un widget determinado. Si desea enviar un evento a una ventana determinada, debe dar a la ventana un valor de identificador único (para que se pueda identificar de forma positiva) y, al compilar el evento, colocar el valor del identificador de ventana en el campo **gx_event_target**. Si no conoce el identificador de destino o si desea que el evento se enrute al widget que tiene el foco de entrada, asegúrese de establecer el campo **gx_event_target** en 0.

Por último, el campo **gx_event_payload** es una unión de varios tipos de datos. En el caso de los eventos **GX_EVENT_PEN_DOWN** y **GX_EVENT_PEN_UP**, el campo **gx_event_pointdata** indica la posición del lápiz mediante las coordenadas de píxeles x,y. En el caso de los eventos de temporizador, el campo **gx_event_timer_id** contiene el identificador del temporizador expirado. En otros tipos de eventos se usan otros campos de datos de carga. La lista completa de los tipos de eventos predefinidos y sus campos de carga se define en el [Apéndice E Descripciones de eventos de GUIX](appendix-e.md).

La aplicación también puede agregar sus propios eventos personalizados, empezando numéricamente después de la constante **GX_FIRST_APP_EVENT**. Todos los números de evento después de esta constante están reservados para el uso de la aplicación. Por supuesto, el controlador de eventos de widget de la aplicación debe incluir procesamiento para estos eventos de aplicación.

### <a name="event-processing"></a>Procesamiento de eventos 

Hay una función de procesamiento de eventos de widget predeterminada para cada widget, ***gx_<tipo_de_widget>_event_process***. En la mayoría de los casos, la aplicación no tendrá que preocuparse por el control de eventos de ningún widget. Sin embargo, en situaciones en las que la aplicación requiere procesamiento de eventos personalizado o complementario, puede invalidar la función de procesamiento predeterminada por su cuenta mediante la API de GUIX ***gx_widget_event_process_set***. Esta función invalida la función de procesamiento de eventos predeterminada con la función de procesamiento de eventos especificada en la API.

> [!IMPORTANT]
> Las funciones de procesamiento de eventos de la aplicación pueden aprovechar las ventajas del procesamiento predeterminado (es decir, evitar duplicarlo); basta con llamar directamente al procesamiento de ***gx_widget_event_process*** predeterminado.

La llamada al procesamiento de eventos se realiza exclusivamente desde el contexto del subproceso interno del sistema de GUIX. De esta manera, los requisitos de la pila para procesar el control de eventos solo se aplican al subproceso de GUIX.

### <a name="implementing-custom-event-processing-example"></a>Implementación del procesamiento personalizado de eventos (ejemplo) 

Puede proporcionar su propia función de procesamiento de eventos para cualquier widget o ventana en el sistema de GUIX. Si crea su propio tipo de widget personalizado, por lo general instalará el controlador de eventos personalizado en la función de creación del widget. Si solo va a ampliar o modificar la operación de una ventana o widget existente, puede llamar a la función de API gx_widget_event_process_set tras haber creado el widget o la ventana. Casi siempre proporcionará su propio control de eventos para las ventanas de nivel superior (también denominadas pantallas) con el fin de procesar eventos generados por los controles secundarios. El procesamiento de eventos generados por los controles secundarios de una pantalla es la forma principal de agregar funcionalidad a la aplicación GUIX.

Por ejemplo, supongamos que define una pantalla de nivel superior denominada "main_menu".
Esta pantalla podría definirse mediante GUIX Studio o bien podría crear esta pantalla en el código de la aplicación. Si define la pantalla en GUIX Studio, simplemente escriba el nombre del controlador de eventos en el campo de propiedades de Studio para esa pantalla; el código de especificaciones generado por Studio instalará automáticamente el controlador de eventos. En este caso, se llamará al controlador de eventos personalizado ***main_menu_event_handler***, que se debe codificar de la siguiente manera:

```C
int main_menu_item; /* example: variable to keep track of selected item */

UINT main_menu_event_handler(GX_WINDOW *main_screen, GX_EVENT *event_ptr)
{
    UINT status = GX_SUCCESS;

    switch(event_ptr->gx_event_type)
    {
    /* this is an example for catching events from a child button */
    case GX_SIGNAL(IDB_CHILD_BUTTON, GX_EVENT_CLICKED):
        /* insert your button handler code here */
        break;

    case GX_EVENT_SHOW:
        /* add functionality to the show event handler */
        /* first, do default processing */
        status = gx_window_event_process(main_screen, event_ptr); /* note 1 */

        /* now add my own processing */
        main_menu_item = 0;
        break;

    default:
        /* pass all other events to base processing function */
        status = gx_window_event_process(main_screen, event_ptr); /* note 1 */
        break;
    }
    return status;
}
```

En el ejemplo anterior, es importante tener en cuenta que, en el caso de los eventos del sistema como **GX_EVENT_SHOW** (eventos generados internamente para advertir a un widget de un cambio de estado), la aplicación debe pasar esos eventos a la función de procesamiento de eventos del widget base para asegurarse de que se produce el procesamiento normal. A continuación, la aplicación puede agregar lógica adicional según sea necesario. Todos los eventos que no se controlan desde la aplicación (el caso predeterminado anterior) también se deben pasar a la función de procesamiento de eventos base. Puesto que este ejemplo correspondía a una pantalla de nivel superior basada en **GX_WINDOW**, la función de procesamiento de eventos predeterminada es gx_window_event_process.

### <a name="drawing-function"></a>Función de dibujo 

Todo el dibujo del widget se realiza de forma independiente del control de eventos. Esto es más eficaz porque el dibujo suele ser costoso en cuanto a ciclos de la CPU. Mediante la implementación de un algoritmo de dibujo diferido, todos los eventos pendientes y los cambios de visualización asociados se pueden completar antes de que se realice cualquier dibujo, lo que evita el dibujo innecesario. De forma similar al procesamiento de eventos, hay una función de dibujo de widget predeterminada para la mayoría de los widgets, con el nombre ***gx_<xxx>_draw***, donde xxx es el tipo de widget. En la mayoría de los casos, la aplicación no tendrá que preocuparse por la función de dibujo de ningún widget. Sin embargo, en situaciones en las que la aplicación requiere procesamiento de eventos personalizado o complementario, puede invalidar la función de dibujo predeterminada por su cuenta mediante la API de GUIX ***gx_widget_draw_set***. Esta función permite que la aplicación proporcione su propia función de dibujo personalizada para cualquier widget. A su vez, esto permite que la aplicación defina tipos de widgets completos.

> [!IMPORTANT]
> Las funciones de dibujo de la aplicación pueden aprovechar las ventajas del dibujo predeterminado (es decir, no duplicar la codificación); basta con llamarlo directamente desde la función de dibujo invalidada.

La llamada al dibujo del widget se realiza exclusivamente desde el contexto del subproceso interno del sistema de GUIX. De esta manera, los requisitos de tiempo y de pila para realizar el dibujo solo se aplican al subproceso de GUIX.

### <a name="implementing-custom-drawing-example"></a>Implementación de dibujo personalizado (ejemplo) 

La referencia a la función de dibujo de cualquier widget se realiza por medio de un puntero de función indirecto que es miembro del bloque de control de GX_WIDGET. Si usa GUIX Studio para definir el widget, puede instalar su propio puntero de función escribiendo el nombre de la función en el parámetro de función de dibujo de las propiedades del widget; Studio instalará el puntero de función cuando se cree el widget. Si crea el widget en el código de la aplicación, debe usar la función de API ***gx_widget_draw_set*** para instalar la función de dibujo personalizada una vez creado el widget.

En este ejemplo, supongamos que desea personalizar la apariencia de un botón. El botón tendrá un aspecto muy similar al de un botón creado con **GX_TEXT_BUTTON**, pero se agregará un pequeño mapa de bits verde "LED_ON" en la parte central derecha del botón cuando esté presionado y un pequeño mapa de bits rojo "LED_OFF" cuando no lo esté. Queremos crear un botón que se parezca a las ilustraciones siguientes.

![Captura de pantalla del botón verde cuando está activado.](./media/guix/image4.jpg) botón personalizado "activado"

![Captura de pantalla del botón rojo cuando está desactivado.](./media/guix/image5.jpg) botón personalizado "desactivado"

En este caso, escribiría una función de dibujo de botón similar a la siguiente.

```C
UINT my_button_draw(GX_TEXT_BUTTON *button)
{
    GX_PIXELMAP *map;
    ULONG button_style;
    INT xpos;
    INT ypos;

    /* first, do the normal text button drawing */
    gx_text_button_draw(button);

    /* now add our extra pixelmap */

    gx_widget_style_get(button, &button_style);

    if (button_style & GX_STYLE_BUTTON_PUSHED)
    {
        /* use the ON pixelmap */
        gx_context_pixelmap_get(GX_PIXELMAP_ID_LED_ON, &map);
    }
    else
    {
        /* use the OFF pixelmap */
        gx_context_pixelmap_get(GX_PIXELMAP_ID_LED_OFF, &map);
    }
    if (map)
    {
        /* draw it 20 pixels in from right edge */
        xpos = button->gx_widget_size.gx_rectangle_right;
        xpos -= map->gx_pixelmap_width + 20;

        /* and draw 10 pixels from the top edge */
        ypos = button->gx_widget_size.gx_rectangle_top + 10;

        /* draw the extra pixelmap on top of the button */
        gx_canvas_pixelmap_draw(xpos, ypos, map);
    }
}
```

## <a name="guix-drawing-context-component"></a>Componente de contexto de dibujo de GUIX 

El contexto de dibujo se crea dinámicamente, en tiempo de ejecución, a medida que GUIX realiza cada operación de actualización del lienzo. Este contexto une el lienzo, el controlador de pantalla y el pincel que se usan para realizar las operaciones de dibujo actuales.

Para definirlo, se usa la estructura **GX_DRAW_CONTEXT**.
Esta estructura contiene variables que definen el recorte y la vista de la operación de dibujo actual, definen el lienzo actual y definen el controlador de pantalla actual en uso. La estructura **GX_DRAW_CONTEXT** también contiene el pincel que se utiliza para dibujar. El pincel del contexto de dibujo es el miembro con el que trabajará directamente en las funciones de dibujo personalizadas. La estructura del pincel se define como se muestra en el código siguiente.

```C
typedef struct GX_BRUSH_STRUCT
{
    GX_PIXELMAP *gx_brush_pixelmap;
    GX_FONT     *gx_brush_font;
    ULONG        gx_brush_line_pattern;
    ULONG        gx_brush_pattern_mask;
    GX_COLOR     gx_brush_fill_color;  
    GX_COLOR     gx_brush_line_color;  
    UINT         gx_brush_style;
    GX_VALUE     gx_brush_width;
    UCHAR        gx_brush_alpha;  
} GX_BRUSH;
```

El campo **gx_brush_pixelmap** define un mapa de píxeles que se va a usar para los rellenos de rectángulos y polígonos. Este miembro no se usa a menos que **gx_brush_style** incluya el estilo **GX_BRUSH_PIXELMAP**.

El miembro **gx_brush_font** define la fuente utilizada para dibujar el texto.
El miembro **gx_brush_line_pattern** define el patrón utilizado para las líneas discontinuas.
El miembro **gx_brush_style** es un conjunto de marcas de estilo que se pueden combinar mediante OR para definir todos los atributos del pincel. A continuación se indican las marcas de estilo de pincel disponibles.

**GX_BRUSH_OUTLINE**  
**GX_BRUSH_SOLID_FILL**  
**GX_BRUSH_PIXELMAP_FILL**  
**GX_BRUSH_ALIAS**  
**GX_BRUSH_UNDERLINE**  
**GX_BRUSH_ROUND**

El miembro **gx_brush_width** define el ancho de línea para el dibujo de líneas o el ancho del contorno para el dibujo de formas con contornos.

El miembro **gx_brush_line_color** define el color de primer plano del dibujo de líneas y del dibujo de texto.

El miembro **gx_brush_fill_color** define el color de relleno sólido que se usa para las formas. El componente de contexto de GUIX proporciona un conjunto de API diseñadas para que sea muy fácil modificar el pincel actual en el contexto activo. Estas API incluyen, entre muchas otras, **gx_context_brush_define**, **gx_context_line_color_set**, **gx_context_fill_color_set** y **gx_context_font_set**.

Los objetos secundarios heredan el contexto de dibujo de un objeto principal. En realidad, los objetos secundarios heredan un clon del contexto de dibujo principal cuando se invocan sus funciones de dibujo. El elemento secundario puede modificar el contexto sin afectar al dibujo principal, pero también puede heredar información del elemento principal, como el color y el estilo del pincel, si se desea.

## <a name="guix-window-component"></a>Componente de ventana de GUIX 

El componente de ventana es responsable de todo el procesamiento de ventanas en GUIX. Una ventana de GUIX es fundamentalmente un área de visualización única que puede contener uno o más widgets secundarios. En GUIX, la ventana es simplemente una forma especial del objeto de widget fundamental.

Las ventanas de GUIX utilizan una implementación orientada a objetos con compatibilidad total de herencia. Esto se logra mediante ANSI C, lo que da como resultado unos requisitos de memoria y procesamiento lo más pequeños posible.

Las ventanas de GUIX amplían la funcionalidad del widget de GUIX principalmente agregando compatibilidad para el desplazamiento horizontal y vertical. Los objetos de ventana de GUIX pueden crear y mostrar automáticamente barras de desplazamiento y responder a la entrada de la barra de desplazamiento. Las ventanas que se pueden mover también disponen de control de eventos integrado para permitir que la ventana se mueva o se arrastre según los eventos de entrada del lápiz.
Por último, la ventana de GUIX responde a la recepción del foco de entrada moviendo la ventana al primer puesto en el orden Z de las ventanas.

La ventana de GUIX mantiene el concepto de *área cliente*, que es la parte interna de la ventana una vez que sus bordes y los objetos que no son de cliente, como las barras de desplazamiento, se quitan del área disponible. Los widgets secundarios del área cliente se recortan al área cliente de la ventana, en tanto que los elementos secundarios que no son de cliente, como las barras de desplazamiento, se pueden dibujar fuera del área cliente, aunque se siguen recortando a las dimensiones externas de la ventana.

Las ventanas se mantienen con un enfoque principal-secundario, donde los elementos secundarios heredan las características de su elemento principal. Las ventanas secundarias pueden tener a su vez sus propias ventanas secundarias, que también heredan varias características del elemento principal. Las características de cualquier ventana se pueden redefinir explícitamente por medio de diversas llamadas API de GUIX.

### <a name="window-creation"></a>Creación de ventanas 

Un objeto de ventana se puede crear durante la inicialización o en cualquier momento durante la ejecución de los subprocesos de la aplicación. No hay ningún límite en el número de objetos de ventana que puede crear una aplicación. Tampoco hay ningún límite en el número de elementos secundarios que puede tener una ventana.

### <a name="window-control-block"></a>Bloque de control de la ventana 

Las características de cada objeto de ventana se encuentran en su bloque de control **GX_WINDOW** y se definen en **_gx_api.h_**. La aplicación proporciona la memoria necesaria para un objeto de ventana, que se puede ubicar en cualquier parte de la memoria. Sin embargo, es más habitual que el bloque de control del objeto de ventana forme una estructura global mediante su definición fuera del ámbito de cualquier función.

### <a name="root-window"></a>Ventana raíz 

GUIX requiere lo que se denomina ventana raíz para cada lienzo. La ventana raíz no tiene bordes y tiene las mismas dimensiones que el lienzo al que está asociada. Se usa principalmente como contenedor para todos los widgets y ventanas de primer nivel. Normalmente, la aplicación crea la ventana raíz por medio de la función de API ***gx_window_root_create***, poco después de la creación de la pantalla y el lienzo. Si usa la función gx_studio_display_configure generada por Studio, se puede devolver la dirección de la ventana raíz en la ubicación que se pasa como último parámetro de esta función.

De manera predeterminada, una ventana raíz no puede moverse y, en el caso más simple, tiene el tamaño del lienzo. La ventana raíz de hecho dibuja el fondo de la pantalla, de modo que, para cambiar el color de fondo de la pantalla o para mostrar el papel tapiz de fondo, se asignaría un color o un papel tapiz a la ventana raíz.

Si se puede mover una ventana raíz, no cambia su posición en el lienzo como haría una ventana secundaria, sino que mueve el propio lienzo.
Esta característica permite a la ventana raíz de GUIX aprovechar el hardware compatible con varios búferes de cuadros con registros de desplazamiento de hardware.

### <a name="background"></a>Fondo 

Los fondos de las ventanas son colores sólidos o imágenes de mapa de bits. Hay un fondo de ventana predeterminado en el nivel de sistema que proporciona el valor predeterminado para el conjunto inicial de ventanas. Por supuesto, cualquier fondo de ventana se puede cambiar a través de las API de GUIX.

Para cambiar el fondo de color sólido de una ventana, use la API ***gx_widget_fill_color_set***. Para asignar un papel tapiz de fondo a una ventana, use la API ***gx_window_wallpaper_set***.

### <a name="scrolling"></a>Desplazamiento 

GUIX admite el desplazamiento de ventanas estándar, ya sea horizontal o vertical, cuando el área necesaria para mostrar los elementos secundarios de la ventana supera el tamaño actual de la ventana. Para habilitar el desplazamiento, la aplicación debe crear las barras de desplazamiento deseadas y asociarlas a la ventana.

El componente de ventana de GUIX proporciona una implementación de desplazamiento predeterminada que se basa en el tamaño del área cliente de la ventana y la extensión de todos los widgets secundarios. Las aplicaciones también pueden proporcionar su propia implementación e interpretación de desplazamiento invalidando la función ***gx_window_scroll_info_get*** en una ventana determinada.

### <a name="event-notification"></a>Notificación de evento 

La función de procesamiento de eventos de ventana predeterminada difiere del procesamiento de eventos de GX_WIDGET principalmente en el control de los eventos de desplazamiento y ajuste de tamaño. GX_WINDOW proporciona controladores predeterminado para estos eventos.

La aplicación también puede agregar sus propios eventos personalizados, empezando numéricamente después de la constante **GX_FIRST_APP_EVENT**. Todos los números de evento después de esta constante están reservados para el uso de la aplicación. Por supuesto, el controlador de eventos de ventana de la aplicación debe incluir procesamiento para estos eventos de aplicación.

### <a name="event-processing"></a>Procesamiento de eventos 

Al igual que en todos los demás tipos de widgets, hay una función de procesamiento de eventos de ventana predeterminada para cada ventana, denominada ***gx_window_event_process***. Normalmente, invalidará esta función de control de eventos con su propio controlador de eventos en las ventanas que cree. Así es como responderá a los eventos y tomará medidas en función de los eventos generados por los controles secundarios de la ventana.

Es importante recordar que debe invocar la función base ***gx_window_event_process*** para los eventos del sistema de GUIX si invalida ese controlador de eventos, para permitir que se produzca el control de eventos predeterminado además de cualquier acción que agregue al controlador de eventos. Por ejemplo, si proporciona un controlador personalizado para el evento **GX_EVENT_SHOW** y no pasa este evento a ***gx_window_event_process***, la ventana nunca se hará visible.
Para proporcionar un controlador de eventos personalizado para una ventana, use la función ***gx_widget_event_process_set*** para definir la dirección del controlador de eventos. Esta función invalida la función de procesamiento de eventos predeterminada con la función de procesamiento de eventos especificada en la API.

> [!IMPORTANT]
> Las funciones de procesamiento de eventos de aplicación pueden aprovechar las ventajas del procesamiento predeterminado (es decir, evitar duplicarlo); basta con llamar directamente al procesamiento de ***gx_window_event_process*** predeterminado.

La llamada al procesamiento de eventos se realiza exclusivamente desde el contexto del subproceso interno del sistema de GUIX. De esta manera, los requisitos de la pila para procesar el control de eventos solo se aplican al subproceso de GUIX.

## <a name="guix-image-reader-component"></a>Componente de lector de imágenes de GUIX 

El componente de lector de imágenes proporciona utilidades y funciones de API para descomprimir imágenes comprimidas sin procesar al formato de mapa de píxeles de GUIX. Se admiten los datos de imagen JPEG y PNG sin procesar, con formatos adicionales reservados para futuras versiones.

Tenga en cuenta que en la gran mayoría de las aplicaciones de GUIX no es necesario el componente de lector de imágenes de GUIX. La mayoría de las aplicaciones se basan en la aplicación GUIX Studio para convertir los recursos gráficos con formato JPEG y PNG en recursos **GX_PIXELMAP** compatibles con GUIX. El componente de lector de imágenes de GUIX se emplea cuando los recursos gráficos sin procesar solo se conocen en tiempo de ejecución, o cuando las restricciones de almacenamiento del sistema impiden el almacenamiento de recursos en formato **GX_PIXELMAP**. Los datos de imagen con formato JPEG y PNG suelen ser más compactos que el formato **GX_PIXELMAP**; sin embargo, hay una sobrecarga en tiempo de ejecución asociada a la descompresión y la conversión del espacio de colores de estos tipos de imagen de forma dinámica.

Si se pasan imágenes JPEG o PNG sin procesar a la función de API gx_canvas_pixelmap_draw, GUIX descomprime y dibuja dinámicamente los datos JPEG o PNG. Tenga en cuenta que esto afectará de forma importante a la velocidad del dibujo en tiempo de ejecución. No se recomienda pasar datos de imagen sin procesar a la función gx_canvas_pixelmap_draw a menos que esté usando un destino de hardware que admita la descompresión de JPEG o PNG asistida por hardware.

> [!IMPORTANT]
> Al pasar imágenes JPEG o PNG sin procesar a la API gx_canvas_pixelmap_draw, se produce una sobrecarga en tiempo de ejecución importante en la mayoría del hardware de destino.

Como alternativa, los datos JPEG y PNG sin procesar se pueden convertir al formato GX_PIXELMAP en tiempo de ejecución mediante el componente de lector de imágenes.
Los mapas de píxeles generados de esta manera se pueden usar y dibujar del mismo modo que los mapas de píxeles generados por Studio e incluidos en el archivo de recursos. Esto permite que la aplicación realice la descompresión, la interpolación y la conversión del espacio de colores de la imagen una vez (normalmente durante el inicio del programa) en lugar de realizar estas operaciones cada vez que se dibuja la imagen.

Las funciones del componente de lector de imágenes incluyen:

***gx_image_reader_create***  
***gx_image_reader_palette_set***  
***gx_image_reader_start***

## <a name="guix-animation-component"></a>Componente de animación de GUIX 

El componente de animación de GUIX es un conjunto de funciones y servicios que se usan en las automatizaciones de transición de pantallas y widgets. Este componente admite animaciones de tipo fundido de entrada y salida, movimiento o deslizamiento en cualquier tipo de widget.

Las animaciones de tipo fundido se pueden lograr cambiando el valor alfa interno de los widgets de fundido (si **GX_BRUSH_ALPHA_SUPPORT** está habilitado) o dibujando cualquier colección de widgets en un lienzo de memoria independiente que después se combina con el fondo. En el caso de los destinos de hardware que admiten varias capas gráficas de hardware, la compatibilidad con los efectos de fundido suave se consigue mejor con este enfoque de combinación de lienzos, que suele necesitar muy poco ancho de banda de CPU de núcleo. En el caso de los destinos de hardware que no admiten varias capas gráficas, se admite la combinación utilizando el valor alfa del pincel de GUIX cuando se ejecuta con una profundidad de color de 16 bpp y superior.

Si una animación debe usar un lienzo de dibujo independiente, el componente de animación de GUIX proporciona el servicio de API gx_animation_canvas_define para este fin. Otros tipos de animación no requieren un lienzo independiente, pero lo utilizarán si está disponible. Así se consigue hacer el mejor uso posible de cualquier compatibilidad de hardware subyacente para varias superficies de hardware.

Las variables que controlan una animación se definen mediante dos bloques de control. En primer lugar, el bloque de control **GX_ANIMATION**, que define el controlador de animación. Este controlador de animación es el motor que ejecuta la secuencia de animación que se define. Un solo controlador de animación se puede volver a usar muchas veces para ejecutar muchas secuencias de animación diferentes. Si necesita ejecutar varias secuencias de animación simultáneamente, puede crear varios controladores de animación con **GX_ANIMATION**.

El componente de sistema de GUIX puede proporcionar un bloque reutilizable de estructuras de control **GX_ANIMATION**, que la aplicación puede solicitar cuando se necesite animación y que se devuelve automáticamente al grupo del sistema cuando se completa la secuencia de animación. Esto hace que la aplicación no tenga que definir estáticamente una estructura **GX_ANIMATION** para cada animación que se puede implementar. El tamaño de este grupo de estructuras **GX_ANIMATION** se define mediante la constante **GX_ANIMATION_POOL_SIZE**, cuyo valor predeterminado es 6, lo que significa que, de forma predeterminada, se pueden asignar 6 animaciones simultáneas desde el grupo del sistema. Esta constante se puede modificar en el archivo de encabezado gx_user.h si se requieren más animaciones simultáneas. Si **GX_ANIMATION_POOL_SIZE** se establece en cero, el componente de sistema de GUIX no proporciona un grupo de animaciones ni servicios relacionados.

El segundo bloque de control o estructura que se usa para definir una animación es la estructura **GX_ANIMATION_INFO**. Esta estructura se utiliza para definir una secuencia de animación concreta. Esta estructura de información se pasa al controlador de animación para iniciar una secuencia de animación mediante el servicio de API gx_animation_start. La estructura **GX_ANIMATION_INFO** contiene los siguientes campos:

```C
typedef struct GX_ANIMATION_INFO_STRUCT
{
    GX_WIDGET *gx_animation_target;
    GX_WIDGET *gx_animation_parent;
    GX_WIDGET *gx_animation_screen_list;
    USHORT gx_animation_style;
    USHORT gx_animation_id;
    USHORT gx_animation_start_delay;
    USHORT gx_animation_frame_interval;
    GX_POINT gx_animation_start_position;
    GX_POINT gx_animation_end_position;
    GX_UBYTE gx_animation_start_alpha;
    GX_UBYTE gx_animation_end_alpha;
    GX_UBYTE gx_animation_steps;
} GX_ANIMATION_INFO;
```

El miembro **gx_animation_target** define el widget de destino sobre el que actuará el controlador de animación.

El miembro **gx_animation_parent** define el widget principal, si existe, al que se asociará el widget de destino cuando se complete la secuencia de animación. gx_animation_parent también es el destinatario del evento GX_ANIMATION_COMPLETE que se genera cuando se completa una animación.

El miembro **gx_animation_screen_list** define una lista de widgets para animaciones de deslizamiento de pantalla controladas por entradas de lápiz. La lista de widgets debe terminar con el puntero GX_NULL, y cada widget de la lista debe tener las mismas dimensiones x,y que el miembro gx_animation_parent.

El miembro **gx_animation_style** es una máscara de bits que define el tipo de animación que se va a realizar y las opciones asociadas. A continuación se indican las marcas de estilo de animación.

| Marca de&nbsp;estilo de&nbsp;animación | Descripción |
| --- | --- |
| GX_ANIMATION_TRANSLATE | Solicita una animación de tipo deslizamiento o fundido. |
| GX_ANIMATION_SCREEN_DRAG | Solicita una animación de arrastre de pantalla controlada por la entrada de lápiz. |

Las siguientes marcas se pueden usar en combinación con animaciones de tipo **SCREEN_DRAG**.

| Marcas de&nbsp;arrastre de&nbsp;pantalla | Descripción |
| --- | --- |
| GX_ANIMATION_WRAP | La lista de pantallas debe ajustarse del final al principio. |
| GX_ANIMATION_HORIZONTAL | Arrastre de pantalla permitido en dirección horizontal.  |
| GX_ANIMATION_VERTICAL | Arrastre de pantalla permitido en dirección vertical. |

La marca siguiente se puede utilizar en combinación con las animaciones de traslación.

| Marcas de&nbsp;animaciones de&nbsp;traslación | Descripción |
| --- | --- |
| GX_ANIMATION_DETACH | El destino de la animación se desasocia del elemento principal de la animación cuando se completa la animación. Si el destino se asignó y creó dinámicamente mediante el control de eventos automatizado generado por GUIX Studio, el destino se eliminará una vez desasociado. |
| GX_ANIMATION_TRANSLATE | Se trata de animaciones controladas por temporizador. La aplicación define la posición inicial y final y los valores alfa inicial y final del widget de destino, y el administrador de animaciones crea un temporizador que actúa como el elemento de ejecución de la animación.
| GX_ANIMATION_SCREEN_DRAG | Difiere de las animaciones **TRANSLATE** en que este tipo de animación está controlado por eventos de entrada de lápiz. Este tipo de animación hace un seguimiento de la entrada de pantalla táctil para deslizar el widget de destino cuando el usuario arrastra un lápiz por la pantalla táctil de entrada. Esta animación se habilita cuando la aplicación llama a la API **_gx_animation_drag_enable_**. |

El valor **gx_animation_id** se pasa al elemento principal de la animación en el campo event.gx_event_sender del evento **GX_ANIMATION_COMPLETE**. El elemento principal de la animación usa este valor para determinar cuál de las posibles animaciones secundarias está informando de la finalización. Este valor puede ser 0, en cuyo caso no se generará ningún evento **ANIMATION_COMPLETE**.

El valor de **gx_animation_start_delay** es un recuento de tics de GUIX que indica el número de tics de temporizador que pasarán después de llamar a **_gx_animation_start_ *_ y antes de ejecutar realmente la animación. El valor puede ser 0 para iniciar la animación inmediatamente después de llamar a _* _gx_animation_start_**.

El campo **gx_animation_frame_interval** define el número de tics de temporizador de GUIX (un múltiplo de la tasa de tics del sistema operativo subyacente) que transcurrirán entre cada fotograma de la secuencia de animación. El valor mínimo es 1.

El campo **gx_animation_start_position** define el punto inicial superior izquierdo del widget de destino en las animaciones de traslación.

El campo **gx_animation_end_position** define el punto final superior izquierdo del widget de destino en las animaciones de traslación.

El campo **gx_animation_start_alpha** define el valor alfa inicial del lienzo en las animaciones de traslación.

El campo **gx_animation_end_alpha** define el valor alfa final del lienzo en las animaciones de traslación.

El campo **gx_animation_steps** define el número de pasos o fotogramas que debe ejecutar el controlador en las animaciones de traslación. Con un número mayor de pasos se consigue una apariencia de deslizamiento o fundido más suave, pero también consume un mayor ancho de banda del sistema.

Para implementar efectos de animación en la aplicación, primero debe llamar a ***gx_animation_create*** para inicializar el controlador de animación. Si la animación va a usar un lienzo secundario, inicialice este lienzo llamando a gx_animation_canvas_define. A continuación, debe inicializar la estructura **GX_ANIMATION_INFO** para definir el tipo específico de animación que se va a realizar y los demás parámetros de animación. Por último, llame a gx_animation_start para desencadenar la secuencia de animación.

Cuando el controlador de animación completa una secuencia de animación, envía un evento **GX_ANIMATION_COMPLETE** al widget principal, lo que permite que se realice cualquier operación de limpieza deseada del lienzo de animación en ese momento.

## <a name="guix-utility-component"></a>Componente de utilidad de GUIX 

El componente de utilidad es responsable de todas las funciones de utilidad comunes en GUIX. Se trata de funciones habituales que son utilidades prácticas y se pueden invocar desde cualquier parte de la aplicación o desde el código interno de GUIX. A continuación se indican las funciones del componente de utilidad.

***gx_utility_canvas_to_bmp***

***gx_utility_circle_point_get***

***gx_utility_alphamap_create***

***gx_utility_gradient_create***

***gx_utility_gradient_delete***

***gx_utlity_ltoa***

***gx_utility_math_acos***

***gx_utility_math_asin***

***gx_utility_math_cos***

***gx_utility_math_sin***

***gx_utility_math_sqrt***

***gx_utility_pixelmap_resize***

***gx_utility_pixelmap_rotate***

***gx_utility_pixelmap_simple_rotate***

***gx_utility_rectangle_center***

***gx_utility_rectangle_center_find***

***gx_utility_rectangle_combine***

***gx_utility_rectangle_compare***

***gx_utility_rectangle_define***

***gx_utility_rectangle_overlap_detect***

***gx_utility_rectangle_point_detect***

***gx_utility_rectangle_resize***

***gx_utility_rectangle_shift***

***gx_utility_string_to_alphamap***
