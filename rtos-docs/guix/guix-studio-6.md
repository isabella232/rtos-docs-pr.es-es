---
title: Código generado por GUIX Studio
description: Cuando haya terminado de editar las pantallas y los recursos, GUIX Studio generará un conjunto de archivos de salida que se podrán incorporar a la aplicación insertada.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: f8868ec770aa8f7f35d2866b99e3eb8f501281a8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815473"
---
# <a name="chapter-6-guix-studio-generated-code"></a>Capítulo 6: Código generado por GUIX Studio

Cuando haya terminado de editar las pantallas y los recursos, GUIX Studio generará un conjunto de archivos de salida que se podrán incorporar a la aplicación insertada. Para generar los archivos de salida, seleccione ***Generate Resource Files** _ (Generar archivos de recursos) y _ *_Generate Specifications_** (Generar especificaciones) en el elemento de menú Project (Proyecto). Los archivos de código fuente del lenguaje “C” generados por GUIX Studio están diseñados para compilarse y vincularse con el código fuente de la aplicación insertada. Si se genera un archivo de recursos de formato binario, este se debe programar en un área de almacenamiento no volátil en el destino, y la función de la API de GUIX gx_binres_theme_install debe usarse para instalar los recursos binarios en el tiempo de ejecución.

El código de aplicación insertada del usuario hace referencia al código generado por GUIX Studio. Además, el código generado por GUIX Studio espera que todas las funciones personalizadas de dibujo de widgets, control de eventos y asignación de memoria especificadas en el proyecto se definan en el código de aplicación insertada del usuario. Si no es así, habrá errores de vínculo al crear la aplicación.

> [!NOTE]
> El usuario nunca debería tener que modificar el código generado por GUIX Studio, y debe evitar hacerlo. Todas las modificaciones de la interfaz de usuario deben realizarse en el proyecto de GUIX Studio asociado. Así se mantendrá el proyecto sincronizado con la aplicación insertada.

## <a name="generating-resource-files"></a>Generación de archivos de recursos

Los archivos de recursos generados por GUIX Studio contienen estructuras de datos preestablecidas que definen todos los recursos de GUIX Studio (colores, fuentes, mapas de píxeles y cadenas), que son, en la práctica, todos los recursos definidos en la sección ***Resource View*** (Vista de recursos) del proyecto. Estos archivos de recursos se pueden generar en código fuente o en formatos binarios.

De forma predeterminada, se generan dos archivos: un archivo es de código fuente estándar de C; el otro es un archivo de encabezado de C que proporciona referencias externas y constantes que son necesarias para que el código de la aplicación acceda a los recursos de GUIX definidos en el proyecto. Los nombres de archivo tienen el siguiente formato:

**{*project-name*}_resources.h**

**{*project-name*}_resources.c**

Por ejemplo, los archivos de recursos creados para el proyecto de GUIX Studio "***simple***" son:

**simple_resources.h**

**simple_resources.c**

Para generar los archivos de recursos, seleccione la opción ***Generate Resource Files** _ (Generar archivos de recursos) en la opción de menú _*_Project_*_ (Proyecto). El destino de los archivos de recursos se especifica en el cuadro de diálogo _*_Configure Project_*_ (Configurar proyecto), al que se puede acceder a través de la opción _*_Configure Project/Displays_*_ (Configurar proyecto/paneles) del elemento de menú _ *_Configure_** (Configurar).

En el caso de los recursos de mapas de píxeles y fuentes, puede especificar un nombre de archivo de salida personalizado para cada mapa de píxeles y fuente en los cuadros de diálogo de edición de recursos asociados. Esta característica permite colocar recursos muy grandes en archivos distintos, en lugar de colocar todos los recursos en un solo archivo de salida común. Si no especifica ningún nombre de archivo invalidado para un recurso de fuente o mapa de píxeles, esos recursos se escriben en el archivo de recursos común.

Si prefiere usar recursos binarios, puede especificar un formato de salida de s-record o raw. Los recursos binarios no se compilan ni vinculan con el código de la aplicación, sino que se cargan en tiempo de ejecución mediante la API gx_binres_them_load(). Este servicio de API crea tablas de recursos que dirigen a los recursos almacenados en memoria no volátil. Después, puede instalar estos recursos con un panel determinado mediante gx_display_theme_install().

## <a name="generating-specification-code"></a>Generación del código de especificación

Los archivos de especificación generados por GUIX Studio contienen todo el código C para crear la interfaz de usuario diseñada en GUIX Studio. Este código también hace referencia a los archivos de recursos generados para este proyecto. El código de aplicación del usuario realizará llamadas a este código para crear realmente los objetos de interfaz de usuario definidos en el proyecto. Además, el código de aplicación del usuario contiene todas las funciones personalizadas de dibujo de widgets, control de eventos y asignación de memoria que se especifiquen en el proyecto. De forma predeterminada, se generan dos archivos: un archivo es de código fuente estándar de C; el otro es un archivo de encabezado de C que proporciona referencias externas y constantes que son necesarias para que el código de la aplicación acceda a las especificaciones de GUIX Studio. Los nombres de archivo tienen el siguiente formato:

**{*project-name*}_specifications.h**

**{*project-name*}_specifications.c**

Por ejemplo, los archivos de especificaciones creados para el proyecto de GUIX Studio "***simple***" son:

**simple_specifications.h**

**simple_specifications.c**

Para generar los archivos de especificaciones, seleccione la opción ***Generate Specification Files** _ (Generar archivos de especificación) que hay en la opción de menú _*_Project_*_ (Proyecto). El destino de los archivos de especificaciones se especifica en el cuadro de diálogo _*_Configure Project_*_ (Configurar proyecto), al que se puede acceder a través de la opción _*_Configure Project/Displays_*_ (Configurar proyecto/paneles) del elemento de menú _ *_Configure_** (Configurar).

## <a name="integrating-with-user-code"></a>Integración con el código de usuario

Es sencillo integrar los archivos de recursos y especificaciones generados por GUIX Studio; tan solo siga estos pasos:

1. Copie o haga que los archivos de recursos y especificaciones sean accesibles a través de la configuración de la ruta de acceso al entorno de compilación insertado.
2. Agregue todos los archivos de recursos y especificaciones al proyecto IDE o archivo Make insertados.
3. Asegúrese de que el código insertado de la aplicación llama a las funciones necesarias para inicializar y crear la interfaz de usuario contenida en los archivos de recursos y especificaciones.
4. Asegúrese de que el código insertado de la aplicación contiene todas las funciones personalizadas necesarias de dibujo de widgets, control de eventos y asignación de memoria.
5. Cree la aplicación (compile y vincule).
6. Ejecute la aplicación.