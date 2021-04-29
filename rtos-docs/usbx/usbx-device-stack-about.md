---
title: Manual del usuario de la pila del dispositivo Azure RTOS USBX
description: En esta guía se proporciona información completa sobre Azure RTOS USBX, el software de base USB de alto rendimiento de Microsoft
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: c8e9360c8b72adbc41f840a48e333668c489399e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814338"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a><span data-ttu-id="96691-103">Manual del usuario de la pila del dispositivo Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="96691-103">Azure RTOS USBX Device Stack User Guide</span></span>

<span data-ttu-id="96691-104">En esta guía se proporciona información completa sobre Azure RTOS USBX, el software de base USB de alto rendimiento de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="96691-104">This guide provides comprehensive information about Azure RTOS USBX, the high performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="96691-105">Está diseñado para el desarrollador de software en tiempo real insertado.</span><span class="sxs-lookup"><span data-stu-id="96691-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="96691-106">El desarrollador debe estar familiarizado con las funciones estándar del sistema operativo en tiempo real, la especificación USB y el lenguaje de programación C.</span><span class="sxs-lookup"><span data-stu-id="96691-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="96691-107">Para obtener información técnica relacionada con USB, consulte la especificación USB y las especificaciones de clase USB que se pueden descargar en https://www.USB.org/developers</span><span class="sxs-lookup"><span data-stu-id="96691-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at https://www.USB.org/developers</span></span>

## <a name="organization"></a><span data-ttu-id="96691-108">Organización</span><span class="sxs-lookup"><span data-stu-id="96691-108">Organization</span></span>

- <span data-ttu-id="96691-109">[**Capítulo 1**](usbx-device-stack-1.md): contiene una introducción a Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="96691-109">[**Chapter 1**](usbx-device-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="96691-110">[**Capítulo 2**](usbx-device-stack-2.md) : proporciona los pasos básicos para instalar y usar Azure RTOS USBX con su aplicación ThreadX</span><span class="sxs-lookup"><span data-stu-id="96691-110">[**Chapter 2**](usbx-device-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your ThreadX application</span></span>

- <span data-ttu-id="96691-111">[**Capítulo 3**](usbx-device-stack-3.md): describe los componentes funcionales de la pila de dispositivos Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="96691-111">[**Chapter 3**](usbx-device-stack-3.md) - describes the functional components of the Azure RTOS USBX device stack</span></span>

- <span data-ttu-id="96691-112">[**Capítulo 4**](usbx-device-stack-4.md): describe los servicios de pila de dispositivos Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="96691-112">[**Chapter 4**](usbx-device-stack-4.md) - describes the Azure RTOS USBX device stack services</span></span>

- <span data-ttu-id="96691-113">[**Capítulo 5**](usbx-device-stack-5.md): describe cada clase de dispositivo Azure RTOS USBX, incluidas sus API</span><span class="sxs-lookup"><span data-stu-id="96691-113">[**Chapter 5**](usbx-device-stack-5.md) - describes each Azure RTOS USBX device class including their APIs</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="96691-114">Centro de soporte al cliente</span><span class="sxs-lookup"><span data-stu-id="96691-114">Customer Support Center</span></span>

<span data-ttu-id="96691-115">Envíe una incidencia de soporte técnico a través de Azure Portal si tiene alguna pregunta o necesita ayuda siguiendo los pasos que se describen a continuación.</span><span class="sxs-lookup"><span data-stu-id="96691-115">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="96691-116">Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de forma más eficaz:</span><span class="sxs-lookup"><span data-stu-id="96691-116">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="96691-117">Una descripción detallada del problema, incluida la frecuencia de repetición y si se puede reproducir de forma fiable.</span><span class="sxs-lookup"><span data-stu-id="96691-117">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="96691-118">Una descripción detallada de los cambios en la aplicación o en Azure RTOS ThreadX que precedieron al problema.</span><span class="sxs-lookup"><span data-stu-id="96691-118">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="96691-119">Contenido de la cadena de **_tx_version_id** que se encuentra en el archivo **_tx_port.h_** de la distribución.</span><span class="sxs-lookup"><span data-stu-id="96691-119">The contents of the **_tx_version_id** string found in the **_tx_port.h_** file of your distribution.</span></span> <span data-ttu-id="96691-120">Esta cadena nos proporcionará información de valor sobre el entorno en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="96691-120">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="96691-121">El contenido de la RAM de la variable *_tx_build_options* **ULONG**.</span><span class="sxs-lookup"><span data-stu-id="96691-121">The contents in RAM of the *_tx_build_options* **ULONG** variable.</span></span> <span data-ttu-id="96691-122">Esta variable nos proporcionará información sobre cómo se compiló la biblioteca de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="96691-122">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
