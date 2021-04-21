---
title: Instalación y uso de GUIX Studio
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la herramienta de diseño de sistemas de interfaz de usuario GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7b5f94c26842b408ea1b00aeeb78e111bea3623
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815498"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a><span data-ttu-id="b4a77-103">Capítulo 2: Instalación y uso de GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="b4a77-103">Chapter 2: Installation and Use of GUIX Studio</span></span>

<span data-ttu-id="b4a77-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la herramienta de diseño de sistemas de interfaz de usuario GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="b4a77-104">This chapter contains a description of various issues related to installation, setup, and usage of the GUIX Studio UI system design tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="b4a77-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="b4a77-105">Product Distribution</span></span>

<span data-ttu-id="b4a77-106">Puede obtener la aplicación de GUIX Studio desde [Microsoft Store](https://microsoft.com/store/apps) buscando GUIX Studio o yendo directamente a [la página de GUIX Studio](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span><span class="sxs-lookup"><span data-stu-id="b4a77-106">You can obtain the GUIX Studio app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for GUIX Studio, or by going directly to [the GUIX Studio page](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="b4a77-107">Después, haga lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="b4a77-107">Then do the following.</span></span>

1. <span data-ttu-id="b4a77-108">Desde la página de GUIX Studio en Microsoft Store, haga clic en el botón **Obtener** o **Instalar** para descargar GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="b4a77-108">From the GUIX Studio page in the App Store, click the **Get** or **Install** button to download GUIX Studio.</span></span>

1. <span data-ttu-id="b4a77-109">Puede que el explorador le muestre un mensaje preguntándole si quiere abrir Microsoft Store, como se muestra en la siguiente figura.</span><span class="sxs-lookup"><span data-stu-id="b4a77-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="b4a77-110">Si es así, seleccione el botón **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="b4a77-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="b4a77-111">![Seleccione Abrir para instalar GUIX Studio.](./media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="b4a77-111">![Choose Open to install GUIX Studio.](./media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="b4a77-112">Cuando finalice la instalación, seleccione el botón **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="b4a77-112">When the install finishes, choose the **Launch** button.</span></span>

1. <span data-ttu-id="b4a77-113">La primera vez que se inicia GUIX Studio, se muestra un cuadro de diálogo en el que se le pregunta si quiere clonar el repositorio de GUIX en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="b4a77-113">The first time that GUIX Studio launches, it displays a dialog box asking if you want to clone the GUIX repo to your local computer.</span></span> <span data-ttu-id="b4a77-114">Puede optar por clonar el repositorio e indicar la ubicación en la que ya ha clonado el repositorio, o bien no clonar el repositorio (en este caso, se instala un proyecto de ejemplo en el equipo).</span><span class="sxs-lookup"><span data-stu-id="b4a77-114">You can either choose to clone the repository, point to where you have already cloned the repo, or choose not to clone the repo at all (in which case, one example project is installed on your computer).</span></span>
<span data-ttu-id="b4a77-115">![Seleccione clonar el repositorio e indique la ubicación de un repositorio ya clonado, o bien omita este paso.](./media/guix-studio/clone-repo.png)</span><span class="sxs-lookup"><span data-stu-id="b4a77-115">![Choose to clone the repo, point to an already-cloned repo, or skip.](./media/guix-studio/clone-repo.png)</span></span>

> <span data-ttu-id="b4a77-116">!</span><span class="sxs-lookup"><span data-stu-id="b4a77-116">!</span></span>[!NOTE]
> <span data-ttu-id="b4a77-117">Puede volver a este cuadro de diálogo en cualquier momento eligiendo **Configure** (Configurar) en el menú principal de GUIX Studio y, después, **GUIX Repository** (Repositorio de GUIX).</span><span class="sxs-lookup"><span data-stu-id="b4a77-117">You can return to this dialog box at any time by choosing **Configure** from the main menu of GUIX Stuido, followed by **GUIX Repository**.</span></span>

<span data-ttu-id="b4a77-118">Una vez finalizado el proceso de inicio, ya podrá usar GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="b4a77-118">After the startup process is finished, you will be ready to use GUIX Studio.</span></span>

## <a name="using-guix-studio"></a><span data-ttu-id="b4a77-119">Uso de GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="b4a77-119">Using GUIX Studio</span></span>

<span data-ttu-id="b4a77-120">Es fácil usar GUIX Studio: tan solo ejecute GUIX Studio mediante el botón "***Start***" (Inicio).</span><span class="sxs-lookup"><span data-stu-id="b4a77-120">Using GUIX Studio is easy - simply run GUIX Studio via the "***Start***" button.</span></span> <span data-ttu-id="b4a77-121">Después de hacerlo, se mostrará la interfaz de usuario de GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="b4a77-121">At this point you will observe the GUIX Studio UI.</span></span> <span data-ttu-id="b4a77-122">Ahora podrá usar GUIX Studio para crear gráficamente su interfaz de usuario insertada.</span><span class="sxs-lookup"><span data-stu-id="b4a77-122">You are now ready to use GUIX Studio to graphically create your embedded UI.</span></span> <span data-ttu-id="b4a77-123">Puede crear un proyecto nuevo o abrir uno existente, incluidos los proyectos de ejemplo de GUIX.</span><span class="sxs-lookup"><span data-stu-id="b4a77-123">From here you create a new project or open an existing project, including the GUIX example projects.</span></span>

> [!NOTE]
> <span data-ttu-id="b4a77-124">También puede hacer doble clic en cualquier archivo de proyecto de GUIX Studio con la extensión "**gxp**", con lo que se iniciará GUIX Studio automáticamente y se abrirá el proyecto al que se hace referencia.</span><span class="sxs-lookup"><span data-stu-id="b4a77-124">You can also double-click on any GUIX Studio project file with an extension of "**gxp,**" which will automatically launch GUIX Studio and open the referenced project.</span></span>

## <a name="guix-studio-project-samples"></a><span data-ttu-id="b4a77-125">Proyectos de ejemplo de GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="b4a77-125">GUIX Studio Project Samples</span></span>

<span data-ttu-id="b4a77-126">En el subdirectorio "*_Samples_\*\*" de la instalación se encuentra una serie de archivos de proyectos de ejemplo de GUIX Studio con la extensión "\*\*\*gxp*\* _"_ .</span><span class="sxs-lookup"><span data-stu-id="b4a77-126">A series of example GUIX Studio project files with the extension "\***gxp**_" are found in the "_\*_Samples_\*\*" sub-directory of your installation.</span></span> <span data-ttu-id="b4a77-127">Estos proyectos de ejemplo pregenerados le ayudarán a familiarizarse con el uso de GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="b4a77-127">These pre-built example projects will help you get comfortable with using GUIX Studio.</span></span>

<span data-ttu-id="b4a77-128">Un archivo de proyecto de ejemplo que siempre está presente es \***samples/demo_guix_simple/guix_simple.gxp** _.</span><span class="sxs-lookup"><span data-stu-id="b4a77-128">One example project file that is always present is the file \***samples/demo_guix_simple/guix_simple.gxp** _.</span></span> <span data-ttu-id="b4a77-129">En este archivo de proyecto de ejemplo se muestra la definición de una interfaz de usuario de GUIX simple, tal como se describe en el _ *_Capítulo 7_*\* de este documento.</span><span class="sxs-lookup"><span data-stu-id="b4a77-129">This example project file shows the definition of a simple GUIX UI, as described in _ *_Chapter 7_*\* of this document.</span></span>

![Captura de pantalla de la interfaz de usuario de GUIX Studio.](./media/guix-studio/image_10.png)

<span data-ttu-id="b4a77-131">**Ilustración 1**</span><span class="sxs-lookup"><span data-stu-id="b4a77-131">**Figure 1**</span></span>

## <a name="keyboard-shortcuts"></a><span data-ttu-id="b4a77-132">Métodos abreviados de teclado.</span><span class="sxs-lookup"><span data-stu-id="b4a77-132">Keyboard Shortcuts</span></span>

- <span data-ttu-id="b4a77-133">**Ctrl + N**: nuevo proyecto</span><span class="sxs-lookup"><span data-stu-id="b4a77-133">**Ctrl + N:** New Project</span></span>
- <span data-ttu-id="b4a77-134">**Ctrl + O**: abrir proyecto</span><span class="sxs-lookup"><span data-stu-id="b4a77-134">**Ctrl + O:** Open Project</span></span>
- <span data-ttu-id="b4a77-135">**Ctrl + S**: guardar proyecto</span><span class="sxs-lookup"><span data-stu-id="b4a77-135">**Ctrl + S:** Save Project</span></span>
- <span data-ttu-id="b4a77-136">**Ctrl + Mayús + S**: guardar proyecto como</span><span class="sxs-lookup"><span data-stu-id="b4a77-136">**Ctrl + Shift + S:** Save Project As</span></span>
- <span data-ttu-id="b4a77-137">**Alt + F4**: salir</span><span class="sxs-lookup"><span data-stu-id="b4a77-137">**Alt + F4:** Exit</span></span>
