---
title: Acerca de la guía del usuario de Azure RTOS NetX
description: Esta guía contiene información completa acerca de Azure RTOS NetX, la pila de red de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 01077e3315e87b918cdfd47423d8e0c1b6bbdbbd
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550276"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a><span data-ttu-id="1b315-103">Acerca de la guía del usuario de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="1b315-103">About The Azure RTOS NetX User Guide</span></span>

<span data-ttu-id="1b315-104">Esta guía contiene información completa acerca de Azure RTOS NetX, la pila de red de alto rendimiento de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1b315-104">This guide contains comprehensive information about Azure RTOS NetX, the Microsoft high-performance network stack.</span></span>

<span data-ttu-id="1b315-105">Está destinado a desarrolladores de software insertado en tiempo real familiarizados con los conceptos básicos de redes, Azure RTOS ThreadX y el lenguaje de programación C.</span><span class="sxs-lookup"><span data-stu-id="1b315-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="1b315-106">Organización</span><span class="sxs-lookup"><span data-stu-id="1b315-106">Organization</span></span>

<span data-ttu-id="1b315-107">[Capítulo 1](chapter1.md): presenta Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="1b315-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX</span></span>

<span data-ttu-id="1b315-108">[Capítulo 2](chapter2.md): proporciona los pasos básicos para instalar y usar Azure RTOS NetX con la aplicación ThreadX.</span><span class="sxs-lookup"><span data-stu-id="1b315-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX with your ThreadX application.</span></span>

<span data-ttu-id="1b315-109">[Capítulo 3](chapter3.md): proporciona una visión general funcional del sistema Azure RTOS NetX e información básica sobre los estándares de redes TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="1b315-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX system and basic information about the TCP/IP networking standards.</span></span>

<span data-ttu-id="1b315-110">[Capítulo 4](chapter4.md): ofrece información detallada de la interfaz de la aplicación para Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="1b315-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX.</span></span>

<span data-ttu-id="1b315-111">[Capítulo 5](chapter5.md): describe los controladores de red para Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="1b315-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX.</span></span>

<span data-ttu-id="1b315-112">[Apéndice A](appendix-a.md): servicios de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="1b315-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Services</span></span>

<span data-ttu-id="1b315-113">[Apéndice B](appendix-b.md): constantes de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="1b315-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Constants</span></span>

<span data-ttu-id="1b315-114">[Apéndice C](appendix-c.md): tipos de datos de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="1b315-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="1b315-115">[Apéndice D](appendix-d.md): API de socket compatible con BSD</span><span class="sxs-lookup"><span data-stu-id="1b315-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="1b315-116">[Apéndice E](appendix-e.md): tabla ASCII</span><span class="sxs-lookup"><span data-stu-id="1b315-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="azure-rtos-netx-data-types"></a><span data-ttu-id="1b315-117">Tipos de datos de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="1b315-117">Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="1b315-118">Además de los tipos de datos de estructura de control personalizados de Azure RTOS NetX, hay varios tipos de datos especiales que se usan en las interfaces de llamada de servicio de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="1b315-118">In addition to the custom Azure RTOS NetX control structure data types, there are several special data types that are used in Azure RTOS NetX service call interfaces.</span></span> <span data-ttu-id="1b315-119">Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente.</span><span class="sxs-lookup"><span data-stu-id="1b315-119">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="1b315-120">De esta manera, se garantiza la portabilidad entre diferentes compiladores de C.</span><span class="sxs-lookup"><span data-stu-id="1b315-120">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="1b315-121">La implementación exacta se hereda de ThreadX y se puede encontrar en el archivo ***tx_port.h*** incluido en la distribución de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="1b315-121">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="1b315-122">A continuación se muestra una lista de los tipos de datos de llamada de servicio de Azure RTOS NetX y sus significados asociados:</span><span class="sxs-lookup"><span data-stu-id="1b315-122">The following is a list of Azure RTOS NetX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="1b315-123">Tipo de datos</span><span class="sxs-lookup"><span data-stu-id="1b315-123">Data Types</span></span> | <span data-ttu-id="1b315-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="1b315-124">Description</span></span>  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="1b315-125">**UINT**</span><span class="sxs-lookup"><span data-stu-id="1b315-125">**UINT**</span></span>  | <span data-ttu-id="1b315-126">Entero sin signo básico.</span><span class="sxs-lookup"><span data-stu-id="1b315-126">Basic unsigned integer.</span></span> <span data-ttu-id="1b315-127">Este tipo debe admitir datos sin signo de 32 bits, pero se asigna al tipo de datos sin signo más conveniente.</span><span class="sxs-lookup"><span data-stu-id="1b315-127">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="1b315-128">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="1b315-128">**ULONG**</span></span> | <span data-ttu-id="1b315-129">Tipo entero largo sin signo.</span><span class="sxs-lookup"><span data-stu-id="1b315-129">Unsigned long type.</span></span> <span data-ttu-id="1b315-130">Este tipo debe admitir datos sin signo de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="1b315-130">This type must support 32-bit unsigned data.</span></span>                                                                      |
| <span data-ttu-id="1b315-131">**VOID**</span><span class="sxs-lookup"><span data-stu-id="1b315-131">**VOID**</span></span>  | <span data-ttu-id="1b315-132">Casi siempre equivale al tipo void del compilador.</span><span class="sxs-lookup"><span data-stu-id="1b315-132">Almost always equivalent to the compiler's void type.</span></span>                                                                                 |
| <span data-ttu-id="1b315-133">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="1b315-133">**CHAR**</span></span>  | <span data-ttu-id="1b315-134">Suele ser un tipo de carácter de 8 bits estándar.</span><span class="sxs-lookup"><span data-stu-id="1b315-134">Most often a standard 8-bit character type.</span></span>                                                                                           |

<span data-ttu-id="1b315-135">Se usan tipos de datos adicionales en el código fuente de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="1b315-135">Additional data types are used within the Azure RTOS NetX source.</span></span> <span data-ttu-id="1b315-136">Se encuentran en los archivos \***tx_port.h** _ o _ \*_nx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="1b315-136">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="1b315-137">Centro de soporte al cliente</span><span class="sxs-lookup"><span data-stu-id="1b315-137">Customer Support Center</span></span>

<span data-ttu-id="1b315-138">Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="1b315-138">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="1b315-139">Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:</span><span class="sxs-lookup"><span data-stu-id="1b315-139">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="1b315-140">Una descripción detallada del problema, incluida la frecuencia de repetición y si se puede reproducir de forma fiable.</span><span class="sxs-lookup"><span data-stu-id="1b315-140">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="1b315-141">Una descripción detallada de los cambios en la aplicación o en Azure RTOS NetX que precedieron al problema.</span><span class="sxs-lookup"><span data-stu-id="1b315-141">A detailed description of any changes to the application and/or Azure RTOS NetX that preceded the problem.</span></span>

3. <span data-ttu-id="1b315-142">El contenido de las cadenas **_tx_version_id** y **_nx_version_id** que se encuentran en los archivos **_tx_port.h_ *_ y _* _nx_port.h_** de la distribución.</span><span class="sxs-lookup"><span data-stu-id="1b315-142">The contents of the **_tx_version_id** and **_nx_version_id** strings found in the **_tx_port.h_*_ and _*_nx_port.h_** files of your distribution.</span></span> <span data-ttu-id="1b315-143">Estas cadenas nos proporcionarán información valiosa sobre el entorno en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="1b315-143">These strings will provide us valuable information regarding your run-time environment.</span></span>

4. <span data-ttu-id="1b315-144">El contenido de la memoria RAM de las siguientes variables **ULONG**:</span><span class="sxs-lookup"><span data-stu-id="1b315-144">The contents in RAM of the following **ULONG** variables:</span></span>

    <span data-ttu-id="1b315-145">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="1b315-145">**_tx_build_options**</span></span>

    <span data-ttu-id="1b315-146">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="1b315-146">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="1b315-147">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="1b315-147">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="1b315-148">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="1b315-148">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="1b315-149">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="1b315-149">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="1b315-150">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="1b315-150">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="1b315-151">Estas variables nos proporcionarán información sobre cómo se compilaron las bibliotecas de Azure RTOS ThreadX y de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="1b315-151">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX libraries were built.</span></span>

5. <span data-ttu-id="1b315-152">Un búfer de seguimiento capturado inmediatamente después de que se haya detectado el problema.</span><span class="sxs-lookup"><span data-stu-id="1b315-152">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="1b315-153">Esto se consigue mediante la compilación de las bibliotecas de Azure RTOS ThreadX y Azure RTOS NetX con **TX_ENABLE_EVENT_TRACE** y una llamada a **tx_trace_enable** con la información del búfer de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="1b315-153">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX libraries with **TX_ENABLE_EVENT_TRACE** and calling **tx_trace_enable** with the trace buffer information.</span></span> <span data-ttu-id="1b315-154">Consulte la guía del usuario de Azure RTOS TraceX para más información.</span><span class="sxs-lookup"><span data-stu-id="1b315-154">Refer to the Azure RTOS TraceX User Guide for details.</span></span>
