---
title: 'Capítulo 2: Instalación y uso de Azure RTOS TraceX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la herramienta de análisis del sistema de Azure RTOS TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815769"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a><span data-ttu-id="02968-103">Capítulo 2: Instalación y uso de Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="02968-103">Chapter 2 - Installation and use of Azure RTOS TraceX</span></span>

<span data-ttu-id="02968-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la herramienta de análisis del sistema de Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="02968-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS TraceX system analysis tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="02968-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="02968-105">Product Distribution</span></span>

<span data-ttu-id="02968-106">Para obtener la aplicación TraceX desde [Microsoft App Store](https://microsoft.com/store/apps), busque TraceX o vaya directamente a la [página de TraceX](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span><span class="sxs-lookup"><span data-stu-id="02968-106">You can obtain the TraceX app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for TraceX, or by going directly to [the TraceX page](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="02968-107">Después, haga lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="02968-107">Then do the following.</span></span>

1. <span data-ttu-id="02968-108">En la página de TraceX de App Store, haga clic en el botón **Obtener** o **Instalar** para instalar TraceX.</span><span class="sxs-lookup"><span data-stu-id="02968-108">From the TraceX page in the App Store, click the **Get** or **Install** button to install TraceX.</span></span>

1. <span data-ttu-id="02968-109">Puede que el explorador le muestre un mensaje preguntándole si quiere abrir Microsoft Store, como se muestra en la siguiente figura.</span><span class="sxs-lookup"><span data-stu-id="02968-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="02968-110">Si es así, seleccione el botón **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="02968-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="02968-111">![Seleccione Abrir para instalar TraceX](../guix/media/guix-studio/open-ms-store.png).</span><span class="sxs-lookup"><span data-stu-id="02968-111">![Choose Open to install TraceX.](../guix/media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="02968-112">Cuando finalice la instalación, seleccione el botón **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="02968-112">When the install finishes, choose the **Launch** button.</span></span> 

## <a name="using-tracex"></a><span data-ttu-id="02968-113">Uso de TraceX</span><span class="sxs-lookup"><span data-stu-id="02968-113">Using TraceX</span></span>

<span data-ttu-id="02968-114">Usar TraceX es tan sencillo como abrir un archivo de seguimiento dentro de TraceX.</span><span class="sxs-lookup"><span data-stu-id="02968-114">Using TraceX is as easy as opening a trace file inside TraceX!</span></span> <span data-ttu-id="02968-115">Ejecute TraceX mediante el botón \***Iniciar** _.</span><span class="sxs-lookup"><span data-stu-id="02968-115">Run TraceX via the \***Start** _ button.</span></span> <span data-ttu-id="02968-116">En este punto, observará la interfaz gráfica de usuario (GUI) de TraceX.</span><span class="sxs-lookup"><span data-stu-id="02968-116">At this point you will observe the TraceX graphic user interface (GUI).</span></span> <span data-ttu-id="02968-117">Ahora está listo para usar TraceX para ver gráficamente un búfer de seguimiento de destino existente.</span><span class="sxs-lookup"><span data-stu-id="02968-117">You are now ready to use TraceX to graphically view an existing target trace buffer.</span></span> <span data-ttu-id="02968-118">Es sencillo; para ello, haga clic en _ *_Archivo -> Abrir_*\* y, después, escriba el archivo de seguimiento binario.</span><span class="sxs-lookup"><span data-stu-id="02968-118">This is easily done by clicking _ *_File -> Open,_*\* then entering the binary trace file.</span></span>

>[!IMPORTANT]
><span data-ttu-id="02968-119">*También puede hacer doble clic en cualquier archivo de seguimiento con una extensión de **trx**, que iniciará automáticamente TraceX*.</span><span class="sxs-lookup"><span data-stu-id="02968-119">*You can also double-click on any trace file with an extension of **trx,** which will automatically launch TraceX.*</span></span>

![Captura de pantalla de la GUI de TraceX](./media/user-guide/screen_shot_8.png)

<span data-ttu-id="02968-121">**FIGURA 1**</span><span class="sxs-lookup"><span data-stu-id="02968-121">**FIGURE 1**</span></span>

>[!IMPORTANT]
><span data-ttu-id="02968-122">*Consulte el **capítulo 5** para obtener instrucciones sobre cómo generar búferes de seguimiento en el destino mediante ThreadX*.</span><span class="sxs-lookup"><span data-stu-id="02968-122">*Refer to **Chapter 5** for instructions on how to generate trace buffers on the target using ThreadX.*</span></span>

## <a name="tracex-examples"></a><span data-ttu-id="02968-123">Ejemplos de TraceX</span><span class="sxs-lookup"><span data-stu-id="02968-123">TraceX Examples</span></span>

<span data-ttu-id="02968-124">La primera vez que ejecute la aplicación TraceX, o cuando se actualice la aplicación TraceX, se le pedirá que instale los archivos de seguimiento de ejemplo de TraceX y el archivo custom_events.trxc en un directorio definido por el usuario en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="02968-124">The first time you run the TraceX application, or when the TraceX application is updated, you will be prompted to install the TraceX example trace files and the custom_events.trxc file to a user-defined directory on your local machine.</span></span>

<span data-ttu-id="02968-125">Después de completar este paso de instalación, los archivos de seguimiento de ejemplo con la extensión **trx** se encuentran en el subdirectorio **TraceFiles** de la carpeta de instalación.</span><span class="sxs-lookup"><span data-stu-id="02968-125">After this installation step in completed, the example trace files with the extension **trx** are found in the **TraceFiles** subdirectory of your installation folder.</span></span> <span data-ttu-id="02968-126">Estos ejemplos creados previamente le ayudarán a familiarizarse con el uso de TraceX en los búferes de seguimiento generados por ThreadX que se ejecutan con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="02968-126">These pre-built examples will help you get comfortable with using TraceX on the trace buffers generated by ThreadX running with your application.</span></span>

<span data-ttu-id="02968-127">Un archivo de seguimiento de ejemplo siempre está presente es el archivo \***demo_threadx.trx** _.</span><span class="sxs-lookup"><span data-stu-id="02968-127">One example trace file always present is the file \***demo_threadx.trx** _.</span></span> <span data-ttu-id="02968-128">Este archivo de seguimiento de ejemplo muestra la ejecución de la demostración de ThreadX estándar, como se describe en el capítulo 6 del manual del usuario de _ThreadX\*.</span><span class="sxs-lookup"><span data-stu-id="02968-128">This example trace file shows the execution of the standard ThreadX demo, as described in Chapter 6 of the _ThreadX User Guide\*.</span></span>

![Captura de pantalla del cuadro de diálogo Abrir en TraceX](./media/user-guide/screen_shot_9.png)

<span data-ttu-id="02968-130">**FIGURA 2**</span><span class="sxs-lookup"><span data-stu-id="02968-130">**FIGURE 2**</span></span>
