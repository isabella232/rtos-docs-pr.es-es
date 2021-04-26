---
title: Acerca de la guía del usuario de Azure RTOS NetX Duo
description: Esta guía contiene información completa acerca de Azure RTOS NetX Duo, la pila de red dual IPv4/IPv6 de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814878"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a><span data-ttu-id="9c998-103">Acerca de la guía del usuario de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9c998-103">About The Azure RTOS NetX Duo User Guide</span></span>

<span data-ttu-id="9c998-104">Esta guía contiene información completa acerca de Azure RTOS NetX Duo, la pila de red dual IPv4/IPv6 de alto rendimiento de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9c998-104">This guide contains comprehensive information about Azure RTOS NetX Duo, the Microsoft high-performance IPv4/IPv6 dual network stack.</span></span> 

<span data-ttu-id="9c998-105">Está destinada a desarrolladores de software insertado en tiempo real familiarizados con los conceptos básicos de redes, Azure RTOS ThreadX y el lenguaje de programación C.</span><span class="sxs-lookup"><span data-stu-id="9c998-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="9c998-106">Organización</span><span class="sxs-lookup"><span data-stu-id="9c998-106">Organization</span></span>

<span data-ttu-id="9c998-107">[Capítulo 1](chapter1.md): presenta Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9c998-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX Duo</span></span>

<span data-ttu-id="9c998-108">[Capítulo 2](chapter2.md): proporciona los pasos básicos para instalar y usar Azure RTOS NetX Duo con la aplicación ThreadX.</span><span class="sxs-lookup"><span data-stu-id="9c998-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX Duo with your ThreadX application</span></span>

<span data-ttu-id="9c998-109">[Capítulo 3](chapter3.md): proporciona una visión general funcional del sistema Azure RTOS NetX Duo e información básica sobre los estándares de redes TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="9c998-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX Duo system and basic information about the TCP/IP networking standards</span></span>

<span data-ttu-id="9c998-110">[Capítulo 4](chapter4.md): ofrece información detallada de la interfaz de la aplicación para Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9c998-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX Duo</span></span>

<span data-ttu-id="9c998-111">[Capítulo 5](chapter5.md): describe los controladores de red para Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9c998-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX Duo</span></span>

<span data-ttu-id="9c998-112">[Apéndice A](appendix-a.md): servicios de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9c998-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Duo Services</span></span>

<span data-ttu-id="9c998-113">[Apéndice B](appendix-b.md): constantes de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9c998-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Duo Constants</span></span>

<span data-ttu-id="9c998-114">[Apéndice C](appendix-c.md): tipos de datos de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9c998-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="9c998-115">[Apéndice D](appendix-d.md): API de socket compatible con BSD.</span><span class="sxs-lookup"><span data-stu-id="9c998-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="9c998-116">[Apéndice E](appendix-e.md): gráfico ASCII.</span><span class="sxs-lookup"><span data-stu-id="9c998-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="9c998-117">Convenciones de la guía</span><span class="sxs-lookup"><span data-stu-id="9c998-117">Guide Conventions</span></span>

<span data-ttu-id="9c998-118">Cursiva: el tipo de letra denota títulos de libros, destaca palabras importantes e indica variables.</span><span class="sxs-lookup"><span data-stu-id="9c998-118">Italics - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="9c998-119">**Negrita**: el tipo de letra indica nombres de archivo, palabras clave y, además, destaca palabras importantes y variables.</span><span class="sxs-lookup"><span data-stu-id="9c998-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c998-120">Los símbolos de información llaman la atención sobre información importante o adicional que podría afectar al rendimiento o al funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="9c998-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>
 
> [!WARNING]
> <span data-ttu-id="9c998-121">Los símbolos de advertencia llaman la atención sobre situaciones que los desarrolladores deben intentar evitar, ya que podrían dar lugar a errores irrecuperables.</span><span class="sxs-lookup"><span data-stu-id="9c998-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-netx-duo-data-types"></a><span data-ttu-id="9c998-122">Tipos de datos de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9c998-122">Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="9c998-123">Además de los tipos de datos de estructura de control personalizados de Azure RTOS NetX Duo, hay varios tipos de datos especiales que se usan en las interfaces de llamada de servicio de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9c998-123">In addition to the custom Azure RTOS NetX Duo control structure data types, there are several special data types that are used in Azure RTOS NetX Duo service call interfaces.</span></span> <span data-ttu-id="9c998-124">Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente.</span><span class="sxs-lookup"><span data-stu-id="9c998-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="9c998-125">De esta manera, se garantiza la portabilidad entre diferentes compiladores de C.</span><span class="sxs-lookup"><span data-stu-id="9c998-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="9c998-126">La implementación exacta se hereda de ThreadX y se puede encontrar en el archivo ***tx_port.h*** incluido en la distribución de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="9c998-126">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="9c998-127">A continuación se muestra una lista de los tipos de datos de llamada de servicio de Azure RTOS NetX Duo y sus significados asociados:</span><span class="sxs-lookup"><span data-stu-id="9c998-127">The following is a list of Azure RTOS NetX Duo service call data types and their associated meanings:</span></span>

<span data-ttu-id="9c998-128">**UINT**: entero sin signo básico.</span><span class="sxs-lookup"><span data-stu-id="9c998-128">**UINT**: Basic unsigned integer.</span></span> <span data-ttu-id="9c998-129">Este tipo debe admitir datos sin signo de 32 bits, pero se asigna al tipo de datos sin signo más conveniente.</span><span class="sxs-lookup"><span data-stu-id="9c998-129">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span>  
<span data-ttu-id="9c998-130">**ULONG**: tipo largo sin signo.</span><span class="sxs-lookup"><span data-stu-id="9c998-130">**ULONG**: Unsigned long type.</span></span> <span data-ttu-id="9c998-131">Este tipo debe admitir datos sin signo de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="9c998-131">This type must support 32-bit unsigned  data.</span></span>
<span data-ttu-id="9c998-132">**VOID**: casi siempre equivale al tipo void del compilador.</span><span class="sxs-lookup"><span data-stu-id="9c998-132">**VOID**: Almost always equivalent to the compiler's void type.</span></span>  
<span data-ttu-id="9c998-133">**CHAR**: suele ser un tipo de carácter de 8 bits estándar.</span><span class="sxs-lookup"><span data-stu-id="9c998-133">**CHAR**: Most often a standard 8-bit character type.</span></span>  

<span data-ttu-id="9c998-134">Se usan tipos de datos adicionales en el origen de datos de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9c998-134">Additional data types are used within the Azure RTOS NetX Duo source.</span></span> <span data-ttu-id="9c998-135">Se encuentran en los archivos \***tx_port.h** _ o _ \*_nx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="9c998-135">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="9c998-136">Centro de soporte al cliente</span><span class="sxs-lookup"><span data-stu-id="9c998-136">Customer Support Center</span></span>

<span data-ttu-id="9c998-137">Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="9c998-137">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="9c998-138">Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:</span><span class="sxs-lookup"><span data-stu-id="9c998-138">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="9c998-139">Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.</span><span class="sxs-lookup"><span data-stu-id="9c998-139">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="9c998-140">Una descripción detallada de los cambios en la aplicación o en Azure RTOS NetX Duo que precedieron al problema.</span><span class="sxs-lookup"><span data-stu-id="9c998-140">A detailed description of any changes to the application and/or Azure RTOS NetX Duo that preceded the problem.</span></span>
3. <span data-ttu-id="9c998-141">El contenido de las cadenas _tx_version_id y _nx_version_id que se encuentran en los archivos tx_port.h y nx_port.h de la distribución.</span><span class="sxs-lookup"><span data-stu-id="9c998-141">The contents of the _tx_version_id and _nx_version_id strings found in the tx_port.h and nx_port.h files of your distribution.</span></span> <span data-ttu-id="9c998-142">Estas cadenas nos proporcionan información valiosa sobre el entorno en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9c998-142">These strings will provide us valuable information regarding your run- time environment.</span></span>
4. <span data-ttu-id="9c998-143">El contenido en la RAM de las siguientes variables ULONG:</span><span class="sxs-lookup"><span data-stu-id="9c998-143">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="9c998-144">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="9c998-144">**_tx_build_options**</span></span>

    <span data-ttu-id="9c998-145">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="9c998-145">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="9c998-146">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="9c998-146">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="9c998-147">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="9c998-147">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="9c998-148">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="9c998-148">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="9c998-149">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="9c998-149">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="9c998-150">Estas variables nos proporcionarán información sobre cómo se compilaron las bibliotecas de Azure RTOS ThreadX y de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9c998-150">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX Duo libraries were built.</span></span>

5. <span data-ttu-id="9c998-151">Un búfer de seguimiento capturado inmediatamente después de que se haya detectado el problema.</span><span class="sxs-lookup"><span data-stu-id="9c998-151">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="9c998-152">Esto se consigue mediante la compilación de las bibliotecas de Azure RTOS ThreadX y Azure RTOS NetX Duo con TX_ENABLE_EVENT_TRACE y una llamada a tx_trace_enable con la información del búfer de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="9c998-152">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX Duo libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>
