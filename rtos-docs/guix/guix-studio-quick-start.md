---
title: Guía de inicio rápido al sistema operativo Azure Real-Time (RTOS) GUIX Studio
description: Esta guía ofrece una breve introducción al uso de la aplicación Azure RTOS GUIX Studio, el entorno de desarrollo rápido de interfaces de usuario basado en Microsoft Windows diseñado específicamente para la biblioteca en tiempo de ejecución de Azure RTOS GUIX de Microsoft.
author: philmea
ms.author: philmea
ms.date: 7/20/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9ab4dfb2edd8990692ee3dc134207f43e4c757538dbc738f6f406bf40864bfb3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785431"
---
# <a name="azure-rtos-guix-studio-quick-start-guide"></a>Guía de inicio rápido de Azure RTOS GUIX Studio

En esta guía se proporciona una breve introducción sobre el uso de Azure RTOS GUIX Studio. GUIX Studio es una aplicación de diseño de interfaz de usuario basada en Windows diseñada para su uso con la biblioteca en tiempo de ejecución de Azure RTOS GUIX de Microsoft. 

Está destinada al desarrollador de software insertado en tiempo real que usa el sistema operativo en tiempo real ThreadX (RTOS) y la biblioteca en tiempo de ejecución de UI de Azure RTOS GUIX. El desarrollador debe estar familiarizado con los conceptos estándar de Azure RTOS ThreadX y Azure RTOS GUIX.

## <a name="summary"></a>Resumen

Azure RTOS GUIX Studio incluye todo lo que necesita para crear, compilar y ejecutar su propio diseño de interfaz gráfica. Si está evaluando GUIX Studio, el kit de evaluación está diseñado para permitirle compilar y ejecutar el diseño de GUIX como una aplicación de escritorio de Windows independiente con fines de prueba y evaluación. Dado que GUIX está diseñado para su uso en casi cualquier destino incrustado capaz de salida gráfica, el trabajo que realice y los diseños que cree en el escritorio siempre se pueden compilar y ejecutar en el destino incrustado sin cambiar el software de la aplicación.
El instalador de GUIX Studio coloca varios componentes en el sistema de desarrollo:

- La aplicación GUIX Studio.
- Varios proyectos de ejemplo de GUIX.
- Todos los recursos de gráficos y fuentes usados en los proyectos de ejemplo.
- Archivos de solución y archivos de proyecto para compilar en un entorno de escritorio de Windows mediante el IDE de Microsoft Visual Studio.
- Bibliotecas predefinidas GUIX y ThreadX para Win32, que le permiten compilar y ejecutar sus propias aplicaciones en su equipo.
- Archivos de encabezado de las API GUIX y ThreadX.

## <a name="prerequisites"></a>Requisitos previos

El instalador de Azure RTOS GUIX Studio incluye varios proyectos de ejemplo sencillos, y esperamos que empiece por modificar, compilar y ejecutar estos ejemplos a medida que aprenda a usar la aplicación GUIX Studio. Para compilar y ejecutar los ejemplos en el escritorio de Windows, necesitará un compilador de Microsoft Visual Studio. Estas herramientas se pueden descargar desde la siguiente ubicación:

https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs#DownloadFamilies_4

Si no tiene instaladas las herramientas de desarrollo de Microsoft, sigue pudiendo probarlas y usar la aplicación GUIX Studio para crear su propio diseño de interfaz y examinar el código fuente generado. Sin embargo, no podrá compilar y ejecutar el diseño como una aplicación independiente.

## <a name="running-the-examples"></a>Ejecutar los ejemplos

Después de ejecutar el instalador de GUIX Studio, encontrará varios archivos de proyecto y compilaciones de ejemplo de Studio en el contenido instalado. Para comprobar que las herramientas de escritorio están instaladas y funcionan correctamente, se recomienda empezar por compilar y ejecutar cada uno de los ejemplos proporcionados tal cual. Haremos referencia a su directorio de instalación como \<root>, en cuyo caso debe usar el explorador de archivos y navegar a \<root>/GUIX_Studio_6.x/examples. En este directorio debería ver varios programas de ejemplo sencillos, como demo_guix_calculator, demo_guix_car_infotainment, demo_guix__home_automation, demo_guix_widget_types y otros.

## <a name="building-an-example"></a>Compilar un ejemplo

Debería encontrar un subdirectorio denominado *Compilar* dentro de cada carpeta de ejemplo. Esta dirección incluye proyectos preconfigurados para cada cadena de herramientas admitida. Por ejemplo, puede ir a \<root>/GUIX_Studio_6. x/examples/termómetro/Build/vs_2019 y encontrará un archivo de solución preconfigurado de Microsoft Visual Studio y un archivo de proyecto listo para cargarse y ejecutarse en el IDE de Visual Studio. Si desea utilizar una cadena de herramientas diferente, póngase en contacto con [azure_rtos_support](https://docs.microsoft.com/azure/azure-portal/supportability/how-to-create-azure-support-request#create-a-support-request).

Se recomienda iniciar el IDE de Microsoft Visual C++ y abrir al menos uno de estos ejemplos. Presione la tecla \<F7> para compilar el proyecto de ejemplo y luego la tecla \<F5> para ejecutar el programa después de compilarse correctamente. Ahora debería ver una interfaz de usuario de GUIX que se ejecuta en una ventana de Microsoft Windows.

## <a name="designing-and-running-your-own-user-interface"></a>Diseñar y ejecutar su propia interfaz de usuario

Esta guía de inicio rápido no sustituye a la guía de usuario de GUIX Studio ni a la guía de usuario de GUIX, pero le mostraremos lo suficiente como para empezar y animarle a continuar y a consultar la guía de usuario de GUIX Studio para obtener información más detallada.

Existen dos métodos para crear y modificar su propia interfaz de usuario. Puede estudiar el manual de programación de la biblioteca de GUIX y usar la API de GUIX directamente desde el software de la aplicación para implementar completamente el diseño. Con frecuencia, usará la aplicación GUIX Studio para realizar la mayor parte del trabajo de diseño y diseño de los elementos de pantalla y, a continuación, completar el control de eventos y la lógica de la aplicación necesaria para que la interfaz de usuario realice trabajo real.

Cada uno de los ejemplos proporcionados se creó con la aplicación de diseño de la interfaz de GUIX Studio. Debe tener un icono en el escritorio para GUIX Studio 6.x.x.x después de ejecutar el instalador de GUIX Studio.  Inicie GUIX Studio ahora y abra el proyecto denominado "demo_guix_widget_types\guix_widget_types.gxp". La demo *widget_types* es un proyecto de ejemplo que muestra distintas variaciones de los tipos de widget GUIX más comunes.

Ahora que tiene un proyecto abierto, haga clic en "+" para abrir el nodo de árbol denominado "Primary" en la vista de proyecto en la esquina superior izquierda del IDE y haga clic en la ventana de nivel superior dentro de esta carpeta denominada "Menu_Screen". Su proyecto no debe aparecer como se muestra a continuación:

![Captura de pantalla de Studio con el proyecto abierto.](./media/guix-studio/qs_project_open.png)

## <a name="guix-studio-views"></a>Vistas de GUIX Studio

El IDE de GUIX Studio se compone de varias ***vistas***. Cada vista está diseñada para ayudarle a navegar por el diseño y realizar cambios en ese diseño.

### <a name="project-view"></a>Project View

La vista superior izquierda se denomina Vista de proyecto. Esta vista muestra cada una de las pantallas físicas que se incluyen en el proyecto (la mayoría de los proyectos solo tienen una pantalla) y las pantallas y widgets secundarios que se han diseñado para ejecutarse en esa pantalla.

### <a name="properties-view"></a>Vista de propiedades

Debajo de la Vista de proyecto se encuentra la Vista de propiedades. Como su nombre indica, esta vista permite modificar widgets cambiando varias propiedades asociadas a ellos.

### <a name="target-view"></a>Vista de destino

El área central de la pantalla se denomina Vista de destino. Esta vista es una pantalla WYSIWYG de la interfaz de usuario. Dado que la biblioteca GUIX se dibuja dentro de la vista de destino, esta vista es una representación precisa de los píxeles de la apariencia que tendrá el diseño al ejecutarse en el destino incrustado. Si hace clic en distintos widgets en la Vista de proyecto o en la Vista de destino central, verá cómo cambian los valores que se muestran en la Vista propiedades para mostrar las propiedades del widget que ha seleccionado.

### <a name="resource-view"></a>Vista de recursos

Por último, a la derecha verá lo que se denomina Vista de recursos. Esta vista permite seleccionar, agregar, eliminar y modificar los colores, las fuentes, los pixelmaps y las cadenas incluidas en el proyecto.

## <a name="modifying-the-example"></a>Modificar el ejemplo

GUIX Studio está diseñado para ser intuitivo. Para trasladar uno de los widgets mostrados anteriormente, simplemente haga clic en ese widget en la Vista de destino y arrástrelo a una nueva ubicación. Para cambiar los colores del widget, puede hacer clic en el widget deseado y cambiar los colores que se muestran en la Vista de propiedades. Para cambiar la fuente utilizada por un widget de presentación de texto, simplemente haga clic en la fuente deseada en el Vista de recursos y arrastre y coloque la fuente en el widget de destino deseado. Mueva el ratón sobre los botones de la barra de herramientas para ver una ayuda rápida sobre la operación que realiza cada botón.

Experimente y realice algunos cambios menores en el ejemplo. Por ejemplo, puede arrastrar un widget a una nueva ubicación, cambiar el color de fondo de una ventana o cambiar el tamaño de un botón. No se recomienda eliminar ningún widget del ejemplo hasta que obtenga más experiencia con GUIX, ya que la eliminación de widgets puede requerir modificaciones asociadas al código fuente de la aplicación.

## <a name="running-the-application-within-studio"></a>Ejecutar la aplicación en Studio

Puede usar el menú de comandos Editar | Ejecutar aplicación (o el botón Ejecutar aplicación en la barra de botones) para ejecutar la aplicación inmediatamente en una nueva ventana del escritorio. Las funciones de dibujo personalizadas y otros códigos de aplicación no se invocarán con este método, pero permiten desplazarse rápidamente por el diseño de la interfaz de usuario y obtener una idea general de la apariencia y funcionamiento de la aplicación, incluida la navegación de una pantalla a la siguiente.

## <a name="generating-source-files"></a>Generar archivos de origen

Después de realizar los cambios, debe invocar los comandos de menú de GUIX Studio para generar nuevos archivos de código fuente para el proyecto. Después, puede volver a generar el programa de ejemplo para ver los cambios en acción. Para generar archivos de código fuente, use los comandos de menú de GUIX Studio Proyecto|Generar archivos de recursos y Proyecto|Generar archivos de especificación (también puede hacer clic con el botón derecho en la pantalla de la vista de proyecto para ejecutar estos comandos).

A medida que genere estos nuevos archivos de código fuente, debería ver un mensaje de confirmación que le indique que los archivos de origen asociados al proyecto se han actualizado. Si no ve este mensaje de confirmación, asegúrese de que tiene permisos de escritura en el directorio en el que reside el proyecto. Ahora puede cerrar la aplicación GUIX Studio. Si ha realizado cambios en el proyecto, GUIX Studio le preguntará si desea guardar los cambios. Continúe y guarde los cambios, ya que estos ejemplos están diseñados para que los use y experimente con ellos mientras aprende a usar GUIX Studio.

### <a name="building-and-running-the-application"></a>Compilar y ejecutar la aplicación

Ahora que GUIX Studio ha generado los archivos de salida del proyecto, puede compilar y vincular para crear un ejecutable Win32 independiente. Además, para incorporar cualquier dibujo personalizado o control de eventos que haya definido en la aplicación, debe compilar y vincular los archivos de salida generados por GUIX Studio con su propio software de aplicación. Usaremos la cadena de herramientas Microsoft Visual C++ como ejemplo, pero se usará exactamente el mismo procedimiento si está creando y ejecutando para el destino previsto.

- Inicie el IDE de MSVC y abra la solución \<root>/GUIX_Studio_5. x/examples/demo_guix_widget_types/build/vs_2019/guix_widget_types.sln.

- Use la tecla \<F7> para recompilar la solución.
- Para ejecutar el programa, use la tecla \<F5>.
 
Ahora debería ver el programa en ejecución con los cambios realizados en Studio.

### <a name="learning-more"></a>Más información

La **Guía de usuario de GUIX Studio** está disponible en [azrtos-GUIX-Studio-User-Guide](https://docs.microsoft.com/azure/rtos/guix/about-guix-studio). La guía de usuario de GUIX Studio es una guía mucho más detallada sobre el uso de GUIX Studio.

Además, la **Guía de usuario de GUIX** está disponible en [azrtos-GUIX-User-Guide](https://docs.microsoft.com/azure/rtos/guix/about-guix).  En esta guía se proporciona información más detallada sobre lo que está ocurriendo "bajo el capó" cuando se ejecuta la aplicación de GUIX. Tendrá que acudir a ambas guías para utilizar todas las funcionalidades de la biblioteca en tiempo de ejecución de GUIX y GUIX Studio.

## <a name="customer-support-center"></a>Centro de soporte al cliente

Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos. Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:

- Una descripción detallada del problema, incluida la frecuencia con que se produce y cómo se puede reproducir de forma confiable.
- Adjunte el archivo de seguimiento que causa el problema.
- La versión de Azure RTOS GUIX Studio que está usando (aparece en la parte superior izquierda de la pantalla).
- La versión de Azure RTOS GUIX que está usando, incluidas las variables **_gx_version_idstring** y **_gx_build_options**.
