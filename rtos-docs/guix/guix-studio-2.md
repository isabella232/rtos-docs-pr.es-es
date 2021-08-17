---
title: Instalación y uso de GUIX Studio
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la herramienta de diseño de sistemas de interfaz de usuario GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 55d2b0ac08bdceebdf286effe4bbc679320541243ff78359deafe0858a7b597e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786479"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a>Capítulo 2: Instalación y uso de GUIX Studio

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la herramienta de diseño de sistemas de interfaz de usuario GUIX Studio. 

## <a name="product-distribution"></a>Distribución del producto

Puede obtener la aplicación de GUIX Studio desde [Microsoft Store](https://microsoft.com/store/apps) buscando GUIX Studio o yendo directamente a [la página de GUIX Studio](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab). Después, haga lo siguiente.

1. Desde la página de GUIX Studio en Microsoft Store, haga clic en el botón **Obtener** o **Instalar** para descargar GUIX Studio.

1. Puede que el explorador le muestre un mensaje preguntándole si quiere abrir Microsoft Store, como se muestra en la siguiente figura. Si es así, seleccione el botón **Abrir**.
![Seleccione Abrir para instalar GUIX Studio.](./media/guix-studio/open-ms-store.png)

1. Cuando finalice la instalación, seleccione el botón **Iniciar**.

1. La primera vez que se inicia GUIX Studio, se muestra un cuadro de diálogo en el que se le pregunta si quiere clonar el repositorio de GUIX en el equipo local. Puede optar por clonar el repositorio e indicar la ubicación en la que ya ha clonado el repositorio, o bien no clonar el repositorio (en este caso, se instala un proyecto de ejemplo en el equipo).
![Seleccione clonar el repositorio e indique la ubicación de un repositorio ya clonado, o bien omita este paso.](./media/guix-studio/clone-repo.png)

> ![!NOTE]
> Puede volver a este cuadro de diálogo en cualquier momento eligiendo **Configure** (Configurar) en el menú principal de GUIX Studio y, después, **GUIX Repository** (Repositorio de GUIX).

Una vez finalizado el proceso de inicio, ya podrá usar GUIX Studio.

## <a name="using-guix-studio"></a>Uso de GUIX Studio

Es fácil usar GUIX Studio: tan solo ejecute GUIX Studio mediante el botón "***Start***" (Inicio). Después de hacerlo, se mostrará la interfaz de usuario de GUIX Studio. Ahora podrá usar GUIX Studio para crear gráficamente su interfaz de usuario insertada. Puede crear un proyecto nuevo o abrir uno existente, incluidos los proyectos de ejemplo de GUIX.

> [!NOTE]
> También puede hacer doble clic en cualquier archivo de proyecto de GUIX Studio con la extensión "**gxp**", con lo que se iniciará GUIX Studio automáticamente y se abrirá el proyecto al que se hace referencia.

## <a name="guix-studio-project-samples"></a>Proyectos de ejemplo de GUIX Studio

En el subdirectorio "*_Samples_**" de la instalación se encuentra una serie de archivos de proyectos de ejemplo de GUIX Studio con la extensión "***gxp** _"_ . Estos proyectos de ejemplo pregenerados le ayudarán a familiarizarse con el uso de GUIX Studio.

Un archivo de proyecto de ejemplo que siempre está presente es ***samples/demo_guix_simple/guix_simple.gxp** _. En este archivo de proyecto de ejemplo se muestra la definición de una interfaz de usuario de GUIX simple, tal como se describe en el _ *_Capítulo 7_** de este documento.

![Captura de pantalla de la interfaz de usuario de GUIX Studio.](./media/guix-studio/image_10.png)

**Ilustración 1**

## <a name="keyboard-shortcuts"></a>Métodos abreviados de teclado.

- **Ctrl + N**: nuevo proyecto
- **Ctrl + O**: abrir proyecto
- **Ctrl + S**: guardar proyecto
- **Ctrl + Mayús + S**: guardar proyecto como
- **Alt + F4**: salir
