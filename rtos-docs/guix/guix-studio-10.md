---
title: Proyecto de ejemplo simple
description: En este capítulo se describe cómo crear un proyecto de ejemplo en GUIX Studio y cómo ejecutar el ejemplo en GUIX.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3661396f097e0ed7bd872fae01a7bec9212001b9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815005"
---
# <a name="chapter-10-example-project"></a>Capítulo 10: Proyecto de ejemplo

En este capítulo se describe cómo crear un proyecto de ejemplo en GUIX Studio y cómo ejecutar el ejemplo en GUIX.

## <a name="create-new-project"></a>Creación de un proyecto

El primer paso es crear un nuevo proyecto y configurar las pantallas y los idiomas que el proyecto admitirá. La primera vez que inicie GUIX Studio, verá la pantalla ***Proyectos recientes***:

![Captura de pantalla del cuadro de diálogo Proyectos recientes de GUIX Studio.](./media/guix-studio/recent_projects.png)

**Figura 10.1**

Haga clic en el botón ***Crear proyecto** _… para iniciar un nuevo proyecto. Aparecerá el cuadro de diálogo _ *_Nuevo proyecto de GUIX_**, que se muestra aquí:

![Captura de pantalla del cuadro de diálogo Crear proyecto de GUIX Studio.](./media/guix-studio/create_new_project.png)

**Figura 10.2**

Escriba el nombre "***new_example***" como nombre del proyecto. Los nombres de proyecto deben usar reglas de nomenclatura de variables estándar de C; es decir, sin caracteres especiales ni reservados. Escriba la ruta de acceso a la ubicación donde se debe guardar el proyecto. La ruta de acceso debe ser un directorio del sistema de archivos válido; es decir, GUIX Studio no creará el directorio si no existe. Haga clic en "Aceptar" para crear el proyecto.

La siguiente pantalla que se muestra es Configuración del proyecto, que se muestra aquí:

![Captura de pantalla del cuadro de diálogo Configurar proyecto de GUIX Studio.](./media/guix-studio/config_new_project.png)

**Figura 10.3**

Este cuadro de diálogo permite especificar el número de pantallas que admitirá el proyecto y asignar un nombre a cada pantalla. Debe especificar el formato de color admitido por cada pantalla y, opcionalmente, escribir un nombre de ruta de acceso para los archivos de salida generados por Studio para cada pantalla. El directorio predeterminado para los archivos de salida es " ***\\***", lo que significa que los archivos de salida de C se escriben en el mismo directorio que el propio proyecto.

En este ejemplo, deje el valor de ***Number of Displays** _ (Número de pantallas) establecido en "1", escriba el nombre "_*_main_display_*_" en el campo de nombre para pantalla y active "_*_allocate canvas memory_*_" (asignar memoria de lienzo). Deje los campos resolución, formato de color y directorio con sus valores predeterminados y haga clic en _*_Aceptar_**.

Ahora debería ver el proyecto abierto con el IDE de Studio, como se muestra en la figura 10.4:

![Captura de pantalla de un proyecto abierto con el IDE de Studio.](./media/guix-studio/initial_screen.png)

**Figura 10.4**

Al crear un nuevo proyecto, GUIX Studio crea automáticamente una ventana predeterminada como punto de partida para el proyecto. Este cuadro gris es la ventana predeterminada que se crea automáticamente centrada en la *vista de destino*.

Si esta ventana no está seleccionada, haga clic en la ventana para que el cuadro de selección discontinuo se dibuje en torno a la ventana. Ahora, en el cuadro **Ver propiedades** _*, cambie los valores de _*_Widget Name_*_ (Nombre del widget), _*_Widget Id_*_ (Id. del widget), _*_Izquierda_*_, _*_Parte superior_*_ , _*_Ancho_*_ , _*_Alto_*_ y *_Borde_* * para que coincidan con los valores que se muestran a continuación. Cuando realice estos cambios, debería verlos inmediatamente en la vista de destino.

![Captura de pantalla del cuadro de diálogo Ver propiedades.](./media/guix-studio/initial_window_properties.png)

**Figura 10.5**

A continuación, agregaremos un recurso de mapa de píxeles que se usará en un widget ***GX_ICON** _. Se proporcionan varios iconos con la distribución de GUIX Studio que funcionarán correctamente en este ejemplo. Expanda la vista de recursos _*_Pixelmaps_*_ (Mapas de píxeles) y haga clic en el botón _ *_Add New Pixelmap_** (Agregar nuevo mapa de píxeles):

![Captura de pantalla del botón Add New Pixelmap (Agregar nuevo mapa de píxeles).](./media/guix-studio/image74.jpg)

Vaya a la carpeta de instalación de GUIX Studio y, dentro de la carpeta * **./graphics/icons** _, seleccione el archivo denominado _*_i_history_lg.png_*_. Haga clic en _*_Abrir_*_ para agregar este recurso al proyecto. La vista de recursos _ *_Pixelmaps_** (Mapas de píxeles) debería mostrar ahora una vista previa de la imagen de icono recién agregada:

![Captura de pantalla de la vista de recursos Pixelmaps (Mapas de píxeles).](./media/guix-studio/example_add_pixelmap.png)

**Figura 10.6**

Usaremos este nuevo recurso de imagen más adelante como parte del diseño de la interfaz de usuario.

Al igual que cuando se agrega un recurso mapa de píxeles, se agregará un nuevo recurso de fuente a nuestro cuadro de herramientas para que podamos usar esta fuente más adelante en nuestro diseño. Expanda la vista de recursos ***Fuentes** _ y haga clic en el botón _*_Add New Font_*_ (Agregar nueva fuente). Esta acción invocará al cuadro de diálogo _*_Agregar/Editar_*_ fuente. A continuación, vaya a las fuentes GUIX proporcionadas en la carpeta de instalación de GUIX Studio, _*_ .\\fonts\\verasans_ *_ y seleccione el archivo de fuentes TrueType denominado _* _VeraIt.ttf_*_. Escriba el nombre de fuente "_*_MEDIUM_ITALIC_*_" en el campo de nombre de fuente y escriba "_*_30_**" en el campo de altura. Ahora el cuadro de diálogo debería tener el aspecto siguiente:

![Captura de pantalla del cuadro de diálogo Edit Font (Editar fuente).](./media/guix-studio/example_add_font.png)

**Figura 10.7**

Haga clic en ***Aceptar*** para agregar esta fuente al proyecto. Ahora debería ver la fuente en la vista de recursos:

![Captura de pantalla de la sección Fuentes de la vista de recursos.](./media/guix-studio/example_font_added.png)

**Figura 10.8**

Usaremos esta nueva fuente más adelante en el diseño de la interfaz de usuario.

Ahora que tenemos nuevos recursos disponibles, es necesario agregar algunos widgets secundarios a la pantalla que puedan usar estos recursos. Seleccione la ventana creada anteriormente denominada "***hello_world** _"; para ello, haga clic con el botón derecho en la ventana de la vista de destino. En el menú emergente que aparece ahora, seleccione el comando de menú _*_Insertar, Texto, Solicitud_*_ para insertar un nuevo widget _ *_GX_PROMPT_** y adjunte el widget a la ventana en segundo plano. Ahora la ventana debería tener el aspecto siguiente:

![Captura de pantalla de un menú emergente con la selección de Solicitud](./media/guix-studio/image78.jpg)

**Figura 10.9**

Haga clic en la fuente denominada "***MEDIUM_ITALIC** _" en el vista de recursos _ *_Fuentes_**, y arrastre y coloque la fuente en el widget de solicitud. A continuación, edite las propiedades de la solicitud como se muestra en la figura 10.10 para cambiar el tamaño de la solicitud, establezca la transparencia, y cambie el texto y el estilo de la solicitud:

![Captura de pantalla de la vista de propiedades de la solicitud.](./media/guix-studio/image79.jpg)

**Figura 10.10**

Es posible que tenga que desplazarse verticalmente en la vista de propiedades para ver cada una de estas opciones en función de la resolución de la pantalla. Después de realizar estos cambios, la vista de destino debería tener el aspecto siguiente:

![Captura de pantalla de un menú emergente con la selección de Hola mundo.](./media/guix-studio/image80.jpg)

**Figura 10.11**

A continuación, colocaremos un widget de estilo de botón de icono en la pantalla. Haga clic en la ventana en segundo plano para seleccionarla y use el menú de nivel superior o el menú emergente que aparece al hacer clic con el botón derecho para seleccionar ***Insertar, Botón, Botón de icono** _ para agregar un nuevo recurso _*_GX_ICON_BUTTON_*_ a la ventana. Haga clic en el icono denominado _ *_I_HISTORY_LG_** que agregamos anteriormente y arrástrelo hasta el botón de icono. Con la vista de propiedades, ajuste la posición y el tamaño del icono como se muestra a continuación:

![Captura de pantalla de la vista de propiedades del widget de estilo de botón de icono.](./media/guix-studio/image81.jpg)

**Figura 10.12**

Ahora la pantalla debería tener el aspecto siguiente:

![Captura de pantalla de un menú emergente con el texto Hola mundo y el icono del portapapeles.](./media/guix-studio/image82.jpg)

**Figura 10.13**

Lo llamaremos completo para el diseño sencillo de la pantalla de ejemplo. Las pantallas de aplicación reales probablemente serán mucho más sofisticadas, pero esto es suficiente para mostrar cómo usar GUIX Studio para crear sus propias pantallas de aplicación.

## <a name="generate-resource-and-application-code"></a>Generación de código de recurso y aplicación

El siguiente paso es generar el archivo de recursos y el archivo de especificación que define la interfaz de usuario de tiempo de ejecución de GUIX insertada. Para generar los archivos de salida, tendrá que hacer clic con el botón derecho en el nodo ***main_display** _ en la vista del proyecto y seleccionar el comando _ *_Generate Resource Files_** (Generar archivos de recursos). Observará una ventana de información que indica que se han generado los archivos de recursos, como se muestra en la figura 10.14:

![Captura de pantalla de un cuadro de diálogo de notificación.](./media/guix-studio/image83.jpg)

**Figura 10.14**

Haga clic en ***Aceptar** _ para descartar esta notificación y use el mismo procedimiento para hacer clic con el botón derecho en el nodo _*_main_display_*_ y seleccione el comando _ *_Generate Specification Files_** (Generar archivos de especificación). Debe observar una ventana de notificación similar. Ahora ya ha generado los archivos de aplicación de interfaz de usuario simples.

## <a name="create-user-supplied-code"></a>Creación de código proporcionado por el usuario

El siguiente paso consiste en crear su propio archivo de aplicación que invocará el diseño de pantalla generado por GUIX Studio. Con el editor que prefiera, cree un archivo de código fuente denominado ***new_example.c*** y escriba el siguiente código fuente en este archivo:

```C

/* This is an example of the GUIX graphics framework in Win32. */
/* Include system files. */

#include <stdio.h>
#include "tx_api.h"
#include "gx_api.h"

/* Include GUIX resource and specification files for example. */

#include "new_example_resources.h"
#include "new_example_specifications.h"

/* Define the new example thread control block and stack. */

TX_THREAD new_example_thread;
UCHAR new_example_thread_stack[4096];

/* Define the root window pointer. */

GX_WINDOW_ROOT *root_window;

/* Define function prototypes. */

VOID new_example_thread_entry(ULONG thread_input);
UINT win32_graphics_driver_setup_24bpp(GX_DISPLAY *display);

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

VOID tx_application_define(void *first_unused_memory)
{
    /* Create the new example thread. */
    tx_thread_create(&new_example_thread, "GUIX New Example Thread", 
                      new_example_thread_entry, 0, 
                      new_example_thread_stack, sizeof(new_example_thread_stack),
                      1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

VOID new_example_thread_entry(ULONG thread_input)
{

    /* Initialize the GUIX library */
    gx_system_initialize();

    /* Configure the main display. */
    gx_studio_display_configure(MAIN_DISPLAY,                      /* Display to configure*/
                                win32_graphics_driver_setup_24bpp, /* Driver to use */
                                LANGUAGE_ENGLISH,                  /* Language to install */
                                MAIN_DISPLAY_DEFAULT_THEME,        /* Theme to install */
                                &root_window);                     /* Root window pointer */

    /* Create the screen - attached to root window. */

    gx_studio_named_widget_create("hello_world", (GX_WIDGET *) root_window, GX_NULL);

    /* Show the root window to make it visible. */
    gx_widget_show(root_window);

    /* Let GUIX run. */
    gx_system_start();

}
```

El código fuente anterior crea un subproceso de ThreadX típico denominado `GUIX New Example Thread` con un tamaño de pila de 4000 bytes. El trabajo interesante comienza en la función denominada ***new_example_thread_entry***. Esta función es el lugar en el que comienza a ejecutarse el subproceso específico de GUIX.

La primera llamada es a la función denominada ***gx_system_initialize***. Esta llamada siempre es necesaria antes de invocar otras API de GUIX para preparar la biblioteca de GUIX para su primer uso.

A continuación, el ejemplo llama a la función ***gx_studio_display_configure***. Esta función crea la instancia de visualización de GUIX, instala el lenguaje solicitado de la tabla de cadenas de aplicación, instala el tema solicitado desde los recursos de pantalla y devuelve un puntero a la ventana raíz que se creó para esta pantalla. La ventana raíz se usa como elemento primario de todas las pantallas de nivel superior que mostrará la aplicación.

A continuación, el ejemplo llama a ***gx_studio_named_widget_create** _ para crear una instancia de la pantalla _ *_hello_world_**. Esta función usa las estructuras de datos y los recursos generados por GUIX Studio para crear una instancia de la pantalla, tal como se ha definido. Pasamos el puntero de la ventana raíz como el segundo parámetro a esta llamada de función, lo que indica que queremos que la pantalla se conecte inmediatamente a la ventana raíz. El último parámetro es un puntero de retorno opcional que se puede usar si se desea mantener un puntero a la pantalla creada.

A continuación, se llama a ***gx_widget_show** _, que hace que la ventana raíz y todos sus elementos secundarios, incluida la pantalla _ *_hello_world_**, sean visibles.

Por último, el ejemplo llama a ***gx_system_start***. Esta función comienza a ejecutar el bucle de procesamiento de eventos del sistema GUIX.

## <a name="build-and-run-the-example"></a>Creación y ejecución del ejemplo

Compilar y ejecutar el ejemplo son tareas específicas del entorno y las herramientas de compilación. Sin embargo, los pasos del proceso general se pueden definir de la siguiente manera:

1. Crear un nuevo proyecto de directorio y aplicación.
1. Agregar estos archivos al proyecto:

    **new_example_resources.c**

    **new_example_specification.c**

    **new_example.c**

1. Agregar los archivos de compatibilidad en tiempo de ejecución de Win32 desde la ruta de instalación de GUIX Studio ***./win32_runtime***. Incluye el encabezado Win32 de ThreadX y GUIX, así como los archivos de la biblioteca en tiempo de ejecución.
1. Agregar la biblioteca Win32 de GUIX (***gx.lib***) al proyecto.
1. Agregar la biblioteca Win32 de ThreadX (***tx.lib***) al proyecto.
1. Compilar, vincular y ejecutar la aplicación.
