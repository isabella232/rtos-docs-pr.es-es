---
title: Descripción de GUIX Studio
description: Este capítulo contiene una descripción de la herramienta de análisis del sistema de GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 89bbcd51c22dddef6e420750e8c8805a66344335
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814966"
---
# <a name="chapter-3-description-of-guix-studio"></a>Capítulo 3: Descripción de GUIX Studio

Este capítulo contiene una descripción de la herramienta de análisis del sistema de GUIX Studio. En este capítulo se encuentra una descripción de la funcionalidad general de la GUI. 

## <a name="guix-studio-views"></a>Vistas de GUIX Studio

Hay cinco áreas principales de la interfaz de usuario de GUIX Studio, concretamente la ***Barra de herramientas** _, la _*_Vista de proyecto_*_, la Vista de _*_propiedades_*_, la _*_Vista de destino_*_ y la _*_Vista de recursos_*_ . En la _ *_ilustración 2_** se muestra la interfaz de usuario básica de GUIX Studio. En las siguientes subsecciones, se detallan cada una de las vistas.

![Captura de pantalla de la interfaz de usuario básica de GUIX Studio.](./media/guix-studio/image_10.png)

**Ilustración 2**

### <a name="title"></a>Título

- GUIX Studio 18: el ***título** _ muestra la versión de GUIX Studio, así como el proyecto actualmente abierto, como se muestra previamente en la parte superior de la _ *_ilustración 2_**.

### <a name="toolbar"></a>Barra de herramientas

La ***Barra de herramientas** _ muestra los botones disponibles para el desarrollador de GUIX Studio, como se muestra en la _*_ilustración 3_**.

![Captura de pantalla de la Barra de herramientas de GUIX Studio.](./media/guix-studio/image11.jpg)

**Ilustración 3**

Los botones de la Barra de herramientas se definen de la siguiente forma:

![New button](./media/guix-studio/new-button.png) Crea un nuevo proyecto de GUIX Studio.

![Botón Abrir](./media/guix-studio/open-button.png) Abre un proyecto existente de GUIX Studio.

![Botón Guardar](./media/guix-studio/save-button.png) Guarda el proyecto.

![Botón Cortar](./media/guix-studio/cut-button.png) Corta el widget seleccionado, incluidos los secundarios.

![botón Copiar](./media/guix-studio/copy-button.png) Copia el widget seleccionado, incluidos los secundarios.

![Botón Pegar](./media/guix-studio/paste-button.png) Pega el widget y los secundarios.

![Botón Alinear a la izquierda](./media/guix-studio/left-align-button.png) Alinea a la izquierda los widgets seleccionados.

![Botón Alinear a la derecha](./media/guix-studio/right-align-button.png) Alinea a la derecha los widgets seleccionados.

![Botón Alinear en la parte superior](./media/guix-studio/top-align-button.png) Alinea en la parte superior los widgets seleccionados.

![Botón Alinear en la parte inferior](./media/guix-studio/bottom-align-button.png) Alinea en la parte inferior los widgets seleccionados.

![Espaciar verticalmente](./media/guix-studio/space-vertically-button.png) Espacia de forma uniforme los widgets seleccionados verticalmente.

![Botón Espaciar horizontalmente](./media/guix-studio/space-horizontally-button.png) Espacia de forma uniforme los widgets seleccionados horizontalmente.

![Botón Igualar ancho](./media/guix-studio/equal-width-button.png) Hace que los widgets seleccionados tengan el mismo ancho.

![Botón Igualar alto](./media/guix-studio/equal-height-button.png) Hace que los widgets seleccionados tengan el mismo alto.

![Botón Desplazar al frente](./media/guix-studio/move-front-button.png) Mueve los widgets seleccionados al frente.

![Botón Desplazar hacia atrás](./media/guix-studio/move-back-button.png) Mueve los widgets seleccionados hacia atrás.

![Botón Cambiar tamaño](./media/guix-studio/size-button.png) Cambia el tamaño del widget según el contenido.

![Botón Alejar](./media/guix-studio/zoom-out-button.png) Aleja la pantalla de destino.

![Botón Acercar](./media/guix-studio/zoom-in-button.png) Acerca la pantalla de destino.

![Botón Grabar](./media/guix-studio/record-button.png) Graba la macro.

![Botón Reproducir](./media/guix-studio/playback-button.png) Reproduce la macro.

![Botón Ejecutar](./media/guix-studio/run-button.png) Ejecuta una aplicación.

![Botón Acerca de](./media/guix-studio/about-button.png) Acerca de GUIX Studio

### <a name="project-view"></a>Project View

La ***Vista de proyecto** _ muestra los objetos GUIX de lista jerárquica que componen la interfaz de usuario insertada. Para agregar nuevos objetos GUIX, haga clic en el objeto primario y, a continuación, seleccione un objeto en el menú _*_Insertar_*_ (o haga clic con el botón derecho en el objeto y realice la selección en el menú contextual). En la _*_ilustración 4_*_ a continuación, se muestra la _*_Vista de proyecto_** de GUIX Studio.

![Captura de pantalla de la Vista de proyecto de GUIX Studio.](./media/guix-studio/image_35.png)

**Ilustración 4**

### <a name="properties-view"></a>Vista de propiedades

En la ***Vista de propiedades** _, se muestra información detallada sobre las propiedades del objeto GUIX seleccionado actualmente, que se puede seleccionar a través de la _*_Vista de proyecto_*_ o haciendo clic directamente en el objeto en la _*_Vista de destino_*_. En la _*_ilustración 5_*_ a continuación, se muestra la _*_Vista de propiedades_** de GUIX Studio.

![Captura de pantalla de la Vista de propiedades de GUIX Studio.](./media/guix-studio/image36.jpg)

**Ilustración 5**

### <a name="target-view"></a>Vista de destino

La ***Vista de destino** _ es el área de diseño y el diseño de la pantalla WYSIWYG. Esta vista está pensada para representar el monitor físico o los monitores disponibles en el hardware de destino. Los objetos se pueden seleccionar, mover, cambiar de tamaño, etc. con operaciones de mouse simples. Además, las operaciones de los botones de alineación y de orden Z están disponibles en los objetos seleccionados en la Vista de destino. Al seleccionar un objeto en la _*_Vista de destino_*_, también se mostrarán las propiedades de ese objeto en la _*_Vista de propiedades_*_. En la _*_ilustración 6_*_ a continuación se muestra la _*_Vista de proyecto_** de GUIX Studio.

![Captura de pantalla de la Vista de destino de GUIX Studio.](./media/guix-studio/image_37.png)

**Ilustración 6**

### <a name="resource-view"></a>Vista de recursos

La ***Vista de recursos** _ se utiliza para administrar los recursos (colores, fuentes, pixelmaps y cadenas) disponibles para las pantallas de aplicaciones definidas para cada pantalla. Puede hacer clic en los encabezados de grupo de la Vista de recursos para expandir cada grupo y examinar el contenido del grupo. En la _*_ilustración 7_*_ a continuación, se muestra la _*_Vista de recursos_** de GUIX Studio.

![Captura de pantalla de la Vista de recursos de GUIX Studio.](./media/guix-studio/image38.jpg)

**Ilustración 7**

El título de los grupos de recursos indica el nombre del tema actual. Si hay varios temas disponibles, puede hacer clic en las flechas arriba y abajo para cambiar entre los temas.

Cada grupo de recursos de la vista anterior se puede expandir o contraer haciendo clic en el encabezado de grupo. A continuación, se muestra una descripción más detallada de cada grupo de recursos en el siguiente capítulo.

## <a name="the-guix-studio-project"></a>Proyecto de GUIX Studio

Un proyecto de GUIX Studio mantiene información sobre el diseño de la pantalla de la interfaz de usuario y los recursos de la interfaz de usuario. Los datos del proyecto se guardan en un archivo de formato XML con la extensión ".***gxp***". Dado que el archivo del proyecto es un archivo de esquema XML, se puede controlar con versiones y compartirse de forma similar a cualquier otro archivo de código fuente.

Cuando empiece a usar GUIX Studio por primera vez, deberá abrir uno de los proyectos de ejemplo que se proporcionan con la distribución o crear uno. Todo el trabajo se guarda en el archivo de datos del proyecto.

GUIX Studio también genera archivos de código fuente ANSI C. Estos archivos de código fuente contienen los recursos de la aplicación o las estructuras de datos que describen las pantallas diseñadas. GUIX Studio también escribe en estas funciones de API de archivos de código fuente generadas que saben utilizar las estructuras de datos generadas para crear las pantallas de la aplicación de manera dinámica. El software de la aplicación simplemente invocará las funciones de API proporcionadas para crear las pantallas diseñadas en GUIX Studio.

A medida que avance en el diseño de la interfaz de usuario, deberá usar periódicamente GUIX Studio para generar los archivos de salida compatibles con GUIX que le permitirán compilar y ejecutar la interfaz que ha diseñado. Puede compilar y ejecutar los archivos de código fuente generados para el hardware de destino o en el escritorio de Windows que simula ThreadX y GUIX.

## <a name="guix-studio-project-organization"></a>Organización de proyectos de GUIX Studio

Resulta útil tener cierto conocimiento de la organización básica de un proyecto de GUIX Studio para comprender cómo usar GUIX Studio de forma eficaz y comprender la información que se presenta en la Vista de proyecto del IDE de GUIX Studio. La Vista de proyecto es una representación visual de resumen de toda la información contenida en el proyecto.

Antes de describir el proyecto, es necesario definir algunos términos. En primer lugar, usamos el término **monitor** para indicar un dispositivo de visualización físico. Suele ser un dispositivo LCD, pero podría usar otra tecnología. El siguiente término es **pantalla**, que se refiere a un objeto GUIX de nivel superior, normalmente una ventana GUIX, y todos sus elementos secundarios asociados. La pantalla es una construcción de software que se puede definir y modificar en tiempo de ejecución. Por último, el **tema** es una colección de recursos. Un tema incluye una tabla de definiciones de color, definiciones de fuentes y definiciones de mapas de píxeles diseñadas para funcionar bien de forma conjunta y proporcionar una apariencia y funcionamiento coherentes al usuario final.

El proyecto incluye primero un conjunto de información global, como el nombre del proyecto, el número de monitores compatibles, la resolución y el formato de color de cada monitor, así como el número de idiomas compatibles y el nombre de cada idioma compatible. El nombre del proyecto es el primer nodo que se muestra en la Vista de proyecto.

El proyecto siguiente organiza toda la información necesaria para un máximo de 4 monitores físicos y las pantallas y recursos disponibles para cada monitor. Los nombres para mostrar son los nodos del siguiente nivel en el árbol de la Vista de proyecto.

Una característica única de la aplicación GUIX Studio es la compatibilidad integrada con varios monitores físicos, cada uno con su propia resolución x,y, formato de color, pantallas y recursos. Aunque la gran mayoría de las aplicaciones de GUIX usan solo un monitor físico, esta capacidad es importante para quienes hacen un producto que debe ser compatible con varios monitores físicos simultáneos.

Debajo de cada definición de monitor, se encuentran las ventanas de nivel superior o las pantallas definidas para ese monitor. Las definiciones de pantalla se pueden anidar en cualquier nivel en función del número y el anidamiento de widgets secundarios en cada pantalla.

Esta pantalla y la organización del widget secundario se muestran de forma gráfica en la Vista de proyecto.

También se asocian a cada monitor los temas soportados por el monitor y el contenido de los recursos que forman cada tema. Si el proyecto incluye varios monitores, observará que la Vista de recursos cambia su contenido al seleccionar un monitor y, a continuación, otro. Esto se debe a que el contenido del recurso se vincula a cada monitor. No solo el formato de color puede ser diferente, también los mapas de píxeles, los colores y las fuentes que decida usar pueden variar de un monitor físico a otro.

El último componente que mantiene el proyecto son los datos de la tabla de cadenas asociados a cada monitor. Dado que los monitores pueden tener resoluciones x,y muy diferentes, los datos de cadena se mantienen de forma independiente para cada monitor definido en el proyecto.
