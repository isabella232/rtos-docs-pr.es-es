---
title: 'Capítulo 2: Instalación y uso de GUIX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de GUIX para desarrollar interfaces de usuario.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6527227062fc667b3f527a798d6621914c374c5c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814981"
---
# <a name="chapter-2---installation-and-use-of-guix"></a>Capítulo 2: Instalación y uso de GUIX

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de GUIX para desarrollar interfaces de usuario.  

## <a name="host-considerations"></a>Consideraciones sobre el host

El desarrollo insertado se realiza normalmente en equipos host Windows o Linux (Unix). Una vez que la aplicación se compila, se vincula y se genera el archivo ejecutable en el host, se descarga en el hardware de destino para poder ejecutarse.

Normalmente, la descarga de destino se realiza desde el depurador de la herramienta de desarrollo. Después de la descarga, el depurador es responsable de proporcionar el control de ejecución de destino (ir, detener, punto de interrupción, etc.), así como el acceso a los registros de la memoria y del procesador.

La mayoría de los depuradores de herramientas de desarrollo se comunican con el hardware de destino mediante conexiones de depuración en chip (OCD), como JTAG (IEEE 1149.1) y el modo de depuración en segundo plano (BDM). Los depuradores también se comunican con el hardware de destino mediante conexiones de emulación en el circuito (ICE). Las conexiones OCD e ICE proporcionan soluciones sólidas con una intrusión mínima en el software residente de destino.

En cuanto a los recursos utilizados en el host, el código fuente de GUIX se entrega en formato ASCII y requiere aproximadamente 30 MB de espacio en el disco duro del equipo host.

## <a name="target-considerations"></a>Consideraciones sobre el destino

GUIX requiere entre 5 kB y 80 kB de memoria de solo lectura (ROM) en el destino. Se necesitan entre 5 y 10 kB más de memoria de acceso aleatorio (RAM) en el destino para la pila de subprocesos de GUIX y otras estructuras de datos globales.

Además, GUIX requiere el uso de un objeto de exclusión mutua de ThreadX y un temporizador de ThreadX. Estos recursos se utilizan para satisfacer las necesidades de procesamiento periódico y para la protección de subprocesos en GUIX.

## <a name="product-distribution"></a>Distribución del producto

Azure RTOS GUIX se puede obtener en nuestro repositorio de código fuente público: <https://github.com/azure-rtos/guix/>.

A continuación se muestra una lista de los archivos importantes que son comunes a la mayoría de las distribuciones del producto:

| Nombre de archivo&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| Descripción   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| gx_api.h        | Este archivo de encabezado de C contiene todas las equivalencias del sistema, estructuras de datos y prototipos del servicio. |
| gx_port.h       | Este archivo de encabezado de C contiene todas las estructuras y definiciones de datos específicas de la herramienta de desarrollo y del destino.                                                                                                                                         |
| gx.a (o gx.lib) | Se trata de la versión binaria de la biblioteca de C de GUIX. Este archivo se genera normalmente compilando y archivando los archivos de origen de la biblioteca de GUIX proporcionados; sin embargo, esta biblioteca puede proporcionarse en un formato predefinido en función del tipo de licencia y del destino de hardware. |
|

> [!IMPORTANT]
> *Todos los nombres de archivos están en minúsculas, lo que facilita la conversión de los comandos para plataformas de desarrollo de Linux (Unix).*

## <a name="guix-installation"></a>Instalación de GUIX

GUIX se instala clonando el repositorio de GitHub en la máquina local. A continuación se muestra la sintaxis típica para crear un clon del repositorio de GUIX en el equipo:

```c
    git clone https://github.com/azure-rtos/guix
```

También se puede descargar una copia del repositorio mediante el botón Download (Descargar) de la página principal de GitHub.

Además, encontrará instrucciones para compilar la biblioteca de GUIX en la página principal del repositorio en línea.

>[!NOTE]  
> *El software de la aplicación necesita acceso al archivo de biblioteca de GUIX (normalmente, **gx.a** o **gx.lib**) y a los archivos de inclusión de C **gx_api.h** y **gx_port.h**. Con este fin, hay que establecer la ruta adecuada para las herramientas de desarrollo o copiar estos archivos en el área desarrollo de la aplicación.*

## <a name="using-guix"></a>Uso de GUIX

Es fácil usar GUIX. Básicamente, el código de la aplicación debe incluir ***gx_api.h** _ durante la compilación y vincularse con la biblioteca de GUIX _*_gx.a_*_ (o _ *_gx.lib_*)*.

Para compilar una aplicación de GUIX, hay que seguir cuatro sencillos pasos:

| Pasos   | Descripción    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Paso&nbsp;1. | Incluya el archivo ***gx_api.h*** en todos los archivos de la aplicación que usen servicios o estructuras de datos de GUIX.                                                               |
| Paso&nbsp;2. | Inicialice el sistema GUIX llamando a ***gx_system_initialize** _ desde la función _ *_tx_application_define_** o un subproceso de la aplicación.                       |
| Paso&nbsp;3. | Cree una instancia de pantalla, un lienzo para la pantalla, y la ventana raíz y las demás ventanas o widgets necesarios.                                 |
| Paso&nbsp;4. | Compile el origen de la aplicación y vincúlelo con la biblioteca en tiempo de ejecución de GUIX ***gx.a** _ (o _*_gx.lib_**). La imagen resultante se puede descargar en el destino y ejecutarse. |

## <a name="troubleshooting"></a>Solución de problemas

Cada puerto de GUIX se entrega con una aplicación de demostración que se ejecuta en un hardware de pantalla específico. Esta misma demostración básica se entrega con todas las versiones de GUIX. Normalmente, es conveniente que primero se ejecute el sistema de demostración.

Si el sistema de demostración no se ejecuta correctamente, realice las siguientes operaciones para acotar el problema:

1. Determine qué parte de la demostración se está ejecutando.

2. Aumente el tamaño de la pila del subproceso de GUIX cambiando la constante de tiempo de compilación **GX_THREAD_STACK_SIZE** y volviendo a compilar la biblioteca de GUIX.

3. Vuelva a compilar la biblioteca de GUIX con las opciones de depuración pertinentes que aparecen en la sección "Opciones de configuración".

4. Examine el estado de devolución de todas las llamadas API.

5. Determine si hay un error interno del sistema estableciendo un punto de interrupción en la función ***_gx_system_error_process***. El código de error y el autor de la llamada deberían proporcionar pistas sobre qué es lo que podría estar fallando.

6. Omita temporalmente los cambios recientes para ver si el problema desaparece o cambia. Esta información debería resultar útil para los ingenieros de soporte técnico de Microsoft.

Siga los procedimientos descritos en la sección "Qué necesitamos de usted" para enviar la información recopilada en los pasos de solución de problemas.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración al compilar la aplicación y la biblioteca de GUIX mediante GUIX. Estas opciones se usan para ajustar el tamaño de la biblioteca y el conjunto de características para que se adapten mejor a los requisitos de la aplicación. Por ejemplo, si la aplicación va a tener un solo subproceso que usa los servicios de la API de GUIX, debe definirse la marca de configuración **GX_DISABLE_MULTITHREAD_SUPPORT** para eliminar la sobrecarga asociada a proteger las secciones de código críticas contra el adelantamiento por parte de varios subprocesos. Las distintas marcas de configuración pueden definirse en el origen de la aplicación, en la línea de comandos o en el archivo de inclusión **_gx_user.h_**.

Cada vez que se modifican las marcas de configuración de la biblioteca de GUIX, hay que volver a compilar la biblioteca de GUIX y los módulos de la aplicación para que se apliquen los cambios de la configuración.

La lista completa de marcas de configuración puede consultarte en "Apéndice H: marcas de configuración de tiempo de compilación de GUIX".

## <a name="guix-version-id"></a>Identificador de la versión de GUIX

La versión actual de GUIX está disponible tanto para el software de usuario como para el de la aplicación durante el tiempo de ejecución. El programador puede obtener la versión de GUIX si examina el archivo ***gx_port.h** _. Además, este archivo también contiene un historial de versiones del puerto correspondiente. El software de la aplicación puede obtener la versión de GUIX examinando la cadena global _ *_ _gx_version_id_* _ en _*_gx_port.h_**.

El software de la aplicación también puede obtener información de la versión a partir de las constantes que se muestran a continuación definidas en ***gx_api.h**.* Estas constantes identifican la versión actual del producto por su nombre, además de la versión principal y secundaria.

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
