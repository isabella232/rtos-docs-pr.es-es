---
title: Manual del usuario de Azure RTOS TraceX
description: Este manual contiene información completa sobre Azure RTOS TraceX, la herramienta de análisis del sistema basada en Microsoft Windows de Microsoft.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 92d886b19a0c67292cd4f6a5f8bd7f9d3106374b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815966"
---
# <a name="about-this-guide"></a><span data-ttu-id="104c1-103">Acerca de esta guía</span><span class="sxs-lookup"><span data-stu-id="104c1-103">About this guide</span></span>

<span data-ttu-id="104c1-104">Este manual contiene información completa sobre Azure RTOS TraceX, la herramienta de análisis del sistema basada en Microsoft Windows para Microsoft Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="104c1-104">This guide contains comprehensive information about Azure RTOS TraceX, the Microsoft Windows-based system analysis tool for Microsoft Azure RTOS.</span></span>

<span data-ttu-id="104c1-105">Está destinada al desarrollador de software insertado en tiempo real que usa los componentes de complemento y el sistema operativo en tiempo real (RTOS) de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="104c1-105">It is intended for the embedded real-time software developer using Azure RTOS ThreadX Real-Time Operating System (RTOS) and add-on components.</span></span> <span data-ttu-id="104c1-106">El desarrollador debe estar familiarizado con los conceptos estándar de Azure RTOS ThreadX, Azure RTOS FileX y Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="104c1-106">The developer should be familiar with standard Azure RTOS ThreadX Azure RTOS FileX, and Azure RTOS NetX concepts.</span></span>

## <a name="organization"></a><span data-ttu-id="104c1-107">Organización</span><span class="sxs-lookup"><span data-stu-id="104c1-107">Organization</span></span>

- <span data-ttu-id="104c1-108">[Capítulo 1](chapter1.md): contiene una introducción básica de Azure RTOS TraceX y describe su relación con el desarrollo en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="104c1-108">[Chapter 1](chapter1.md) - contains an basic overview of Azure RTOS TraceX and describes its relationship to real-time development.</span></span>
- <span data-ttu-id="104c1-109">[Capítulo 2](chapter2.md): proporciona los pasos básicos para instalar y utilizar Azure RTOS TraceX a fin de analizar la aplicación desde el primer momento.</span><span class="sxs-lookup"><span data-stu-id="104c1-109">[Chapter 2](chapter2.md) - gives the basic steps to install and use Azure RTOS TraceX to analyze your application right out of the box.</span></span>
- <span data-ttu-id="104c1-110">[Capítulo 3](chapter3.md): describe las principales características de Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="104c1-110">[Chapter 3](chapter3.md) - describes the main features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="104c1-111">[Capítulo 4](chapter4.md): proporciona los detalles de las características de análisis de rendimiento de Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="104c1-111">[Chapter 4](chapter4.md) - details performance analysis features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="104c1-112">[Capítulo 5](chapter5.md): describe cómo configurar Azure RTOS ThreadX, Azure RTOS FileX y Azure RTOS NetX para generar un búfer de seguimiento que sea visible para Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="104c1-112">[Chapter 5](chapter5.md) - describes how to set up Azure RTOS ThreadX, Azure RTOS FileX, and Azure RTOS NetX in order to generate a trace buffer that is viewable by Azure RTOS TraceX.</span></span>
- <span data-ttu-id="104c1-113">[Capítulo 6](chapter6.md): describe los eventos de Azure RTOS TraceX de forma detallada.</span><span class="sxs-lookup"><span data-stu-id="104c1-113">[Chapter 6](chapter6.md) - describes Azure RTOS TraceX events in detail.</span></span>
- <span data-ttu-id="104c1-114">[Capítulo 7](chapter7.md): describe los eventos de Azure RTOS FileX de forma detallada.</span><span class="sxs-lookup"><span data-stu-id="104c1-114">[Chapter 7](chapter7.md) - describes Azure RTOS FileX events in detail.</span></span>
- <span data-ttu-id="104c1-115">[Capítulo 8](chapter8.md): describe los eventos de Azure RTOS NetX de forma detallada.</span><span class="sxs-lookup"><span data-stu-id="104c1-115">[Chapter 8](chapter8.md) - describes Azure RTOS NetX events in detail.</span></span>
- <span data-ttu-id="104c1-116">[Capítulo 9](chapter9.md): describe los eventos de Azure RTOS USBX de forma detallada.</span><span class="sxs-lookup"><span data-stu-id="104c1-116">[Chapter 9](chapter9.md) - describes Azure RTOS USBX events in detail.</span></span>
- <span data-ttu-id="104c1-117">[Capítulo 10](chapter10.md): describe cómo crear eventos de usuario personalizados de forma detallada.</span><span class="sxs-lookup"><span data-stu-id="104c1-117">[Chapter 10](chapter10.md) - describes creating custom user events in detail.</span></span>
- <span data-ttu-id="104c1-118">[Capítulo 11](chapter11.md): describe el búfer de seguimiento interno de forma detallada.</span><span class="sxs-lookup"><span data-stu-id="104c1-118">[Chapter 11](chapter11.md) - describes the internal trace buffer in detail.</span></span>
- <span data-ttu-id="104c1-119">[Apéndice A](appendix-a.md): archivo específico del puerto de Azure RTOS ThreadX con su origen de marca de tiempo para recopilar eventos de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="104c1-119">[Appendix A](appendix-a.md) - Azure RTOS ThreadX port-specific file with its time-stamp source for gathering trace events.</span></span>
- <span data-ttu-id="104c1-120">[Apéndice B](appendix-b.md): archivo *tx_trace.h* de Azure RTOS ThreadX que muestra los detalles de implementación relacionados con el búfer de seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="104c1-120">[Appendix B](appendix-b.md) - Azure RTOS ThreadX *tx_trace.h* file that shows implementation details regarding the event trace buffer.</span></span>
- <span data-ttu-id="104c1-121">[Apéndice C](appendix-c.md): se resumen las utilidades de línea de comandos para convertir varios formatos de archivo en archivos binarios de Azure RTOS TraceX adecuados.</span><span class="sxs-lookup"><span data-stu-id="104c1-121">[Appendix C](appendix-c.md) - Summarizes command line utilities for converting various file formats into proper Azure RTOS TraceX binary files.</span></span>
- <span data-ttu-id="104c1-122">[Apéndice D](appendix-d.md): ejemplos de archivos de seguimiento de volcado de varias herramientas de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="104c1-122">[Appendix D](appendix-d.md) - Examples of dumping trace files from various development tools.</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="104c1-123">Convenciones de la guía</span><span class="sxs-lookup"><span data-stu-id="104c1-123">Guide Conventions</span></span>

<span data-ttu-id="104c1-124">*Cursiva*: el tipo de letra denota títulos de libros, destaca palabras importantes e indica variables.</span><span class="sxs-lookup"><span data-stu-id="104c1-124">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="104c1-125">**Negrita**: el tipo de letra indica nombres de archivo, palabras clave y, además, destaca palabras importantes y variables.</span><span class="sxs-lookup"><span data-stu-id="104c1-125">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="104c1-126">Indica la información de la nota.</span><span class="sxs-lookup"><span data-stu-id="104c1-126">Indicates information of note.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="104c1-127">Centro de asistencia al cliente</span><span class="sxs-lookup"><span data-stu-id="104c1-127">Customer Support Center</span></span>

<span data-ttu-id="104c1-128">Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="104c1-128">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="104c1-129">Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:</span><span class="sxs-lookup"><span data-stu-id="104c1-129">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="104c1-130">Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.</span><span class="sxs-lookup"><span data-stu-id="104c1-130">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="104c1-131">Una descripción detallada de los cambios en la aplicación o en Azure RTOS ThreadX que han precedido al problema.</span><span class="sxs-lookup"><span data-stu-id="104c1-131">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="104c1-132">Contenido de la cadena *_tx_version_id* que se encuentra en el archivo *tx_port.h* de la distribución.</span><span class="sxs-lookup"><span data-stu-id="104c1-132">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="104c1-133">Esta cadena nos proporciona información valiosa sobre el entorno en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="104c1-133">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="104c1-134">El contenido en la RAM de la variable *_tx_build_options* ULONG.</span><span class="sxs-lookup"><span data-stu-id="104c1-134">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="104c1-135">Esta variable nos proporciona información sobre cómo se ha compilado la biblioteca de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="104c1-135">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
