---
title: Manual del usuario de la pila del host Azure RTOS USBX
description: En esta guía se proporciona información completa sobre Azure RTOS USBX, el software de base USB de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 243b12c4757ee945def8fea01c0d4114e39312ce
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815606"
---
# <a name="azure-rtos-usbx-host-stack-user-guide"></a><span data-ttu-id="06c4e-103">Manual del usuario de la pila del host Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="06c4e-103">Azure RTOS USBX Host Stack User Guide</span></span>

<span data-ttu-id="06c4e-104">En esta guía se proporciona información completa sobre Azure RTOS USBX, el software de base USB de alto rendimiento de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="06c4e-104">This guide provides comprehensive information about Azure RTOS USBX, the high-performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="06c4e-105">Está diseñada para el desarrollador de software insertado en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="06c4e-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="06c4e-106">El desarrollador debe estar familiarizado con las funciones estándar del sistema operativo en tiempo real, la especificación USB y el lenguaje de programación C.</span><span class="sxs-lookup"><span data-stu-id="06c4e-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="06c4e-107">Para obtener información técnica relacionada con USB, consulte la especificación USB y las especificaciones de clase USB que se pueden descargar en [https://www.USB.org/developers](https://www.USB.org/developers).</span><span class="sxs-lookup"><span data-stu-id="06c4e-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at [https://www.USB.org/developers](https://www.USB.org/developers)</span></span>

## <a name="organization"></a><span data-ttu-id="06c4e-108">Organización</span><span class="sxs-lookup"><span data-stu-id="06c4e-108">Organization</span></span>

- <span data-ttu-id="06c4e-109">[**Capítulo 1**](usbx-host-stack-1.md): contiene una introducción a Azure RTOS USBX.</span><span class="sxs-lookup"><span data-stu-id="06c4e-109">[**Chapter 1**](usbx-host-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="06c4e-110">[**Capítulo 2**](usbx-host-stack-2.md): proporciona los pasos básicos para instalar y usar Azure RTOS USBX con su aplicación de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="06c4e-110">[**Chapter 2**](usbx-host-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your Azure RTOS ThreadX application</span></span>

- <span data-ttu-id="06c4e-111">[**Capítulo 3**](usbx-host-stack-3.md): proporciona una visión general funcional de Azure RTOS USBX e información básica sobre USB.</span><span class="sxs-lookup"><span data-stu-id="06c4e-111">[**Chapter 3**](usbx-host-stack-3.md) - provides a functional overview of Azure RTOS USBX and basic information about USB</span></span>

- <span data-ttu-id="06c4e-112">[**Capítulo 4**](usbx-host-stack-4.md): información detallada de la interfaz de la aplicación para Azure RTOS USBX en modo host.</span><span class="sxs-lookup"><span data-stu-id="06c4e-112">[**Chapter 4**](usbx-host-stack-4.md) - details the application's interface to Azure RTOS USBX in host mode</span></span>

- <span data-ttu-id="06c4e-113">[**Capítulo 5**](usbx-host-stack-5.md): describe las API de las clases de host de Azure RTOS USBX.</span><span class="sxs-lookup"><span data-stu-id="06c4e-113">[**Chapter 5**](usbx-host-stack-5.md) - describes the APIs of the Azure RTOS USBX Host classes</span></span>

- <span data-ttu-id="06c4e-114">[**Capítulo 6**](usbx-host-stack-6.md): descripción de la clase CDC-ECM de Azure RTOS USBX.</span><span class="sxs-lookup"><span data-stu-id="06c4e-114">[**Chapter 6**](usbx-host-stack-6.md) - describes the Azure RTOS USBX CDC-ECM class</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="06c4e-115">Centro de soporte al cliente</span><span class="sxs-lookup"><span data-stu-id="06c4e-115">Customer Support Center</span></span>

<span data-ttu-id="06c4e-116">Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="06c4e-116">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="06c4e-117">Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:</span><span class="sxs-lookup"><span data-stu-id="06c4e-117">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="06c4e-118">Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.</span><span class="sxs-lookup"><span data-stu-id="06c4e-118">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="06c4e-119">Una descripción detallada de los cambios en la aplicación o en Azure RTOS ThreadX que han precedido al problema.</span><span class="sxs-lookup"><span data-stu-id="06c4e-119">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="06c4e-120">Contenido de la cadena *_tx_version_id* que se encuentra en el archivo *tx_port.h* de la distribución.</span><span class="sxs-lookup"><span data-stu-id="06c4e-120">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="06c4e-121">Esta cadena nos proporciona información valiosa sobre el entorno en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="06c4e-121">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="06c4e-122">El contenido en la RAM de la variable *_tx_build_options* ULONG.</span><span class="sxs-lookup"><span data-stu-id="06c4e-122">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="06c4e-123">Esta variable nos proporciona información sobre cómo se ha compilado la biblioteca de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="06c4e-123">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
