---
title: Acerca de la guía de Azure RTOS ThreadX
description: En esta guía se proporciona información exhaustiva sobre Azure RTOS ThreadX, el kernel de alto rendimiento en tiempo real de Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ad9f782942bcdbb2dc49a9c841d865d97bcb1d4e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815114"
---
# <a name="about-the-azure-rtos-threadx-guide"></a><span data-ttu-id="a6a4f-103">Acerca de la guía de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a6a4f-103">About the Azure RTOS ThreadX Guide</span></span>

<span data-ttu-id="a6a4f-104">En esta guía se proporciona información exhaustiva sobre Azure RTOS ThreadX, el kernel de alto rendimiento en tiempo real de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-104">This guide provides comprehensive information about Azure RTOS ThreadX, the Microsoft high-performance real-time kernel.</span></span> 

<span data-ttu-id="a6a4f-105">Está diseñada para el desarrollador de software insertado en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="a6a4f-106">El desarrollador debe estar familiarizado con las funciones del sistema operativo estándar en tiempo real y el lenguaje de programación C.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-106">The developer should be familiar with standard real-time operating system functions and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="a6a4f-107">Organización</span><span class="sxs-lookup"><span data-stu-id="a6a4f-107">Organization</span></span>

<span data-ttu-id="a6a4f-108">[Capítulo 1](chapter1.md): ofrece una introducción básica a Azure RTOS ThreadX y su relación con el desarrollo insertado en tiempo real</span><span class="sxs-lookup"><span data-stu-id="a6a4f-108">[Chapter 1](chapter1.md) - Provides a basic overview of Azure RTOS ThreadX and its relationship to real-time embedded development</span></span>

<span data-ttu-id="a6a4f-109">[Capítulo 2](chapter2.md): proporciona los pasos básicos para instalar y usar Azure RTOS ThreadX en la aplicación *desde el primer momento*</span><span class="sxs-lookup"><span data-stu-id="a6a4f-109">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS ThreadX in your application right *out of the box*</span></span>

<span data-ttu-id="a6a4f-110">[Capítulo 3](chapter3.md): describe en detalle el funcionamiento de Azure RTOS ThreadX, el kernel de alto rendimiento en tiempo real</span><span class="sxs-lookup"><span data-stu-id="a6a4f-110">[Chapter 3](chapter3.md) - Describes in detail the functional operation of Azure RTOS ThreadX, the high performance real-time kernel</span></span>

<span data-ttu-id="a6a4f-111">[Capítulo 4](chapter4.md): detalla la interfaz de la aplicación para Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a6a4f-111">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS ThreadX</span></span>

<span data-ttu-id="a6a4f-112">[Capítulo 5](chapter5.md): describe los controladores de E/S de escritura para aplicaciones de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a6a4f-112">[Chapter 5](chapter5.md) - Describes writing I/O drivers for Azure RTOS ThreadX applications</span></span>

<span data-ttu-id="a6a4f-113">[Capítulo 6](chapter6.md): describe la aplicación de demostración que se proporciona con cada paquete de soporte técnico del procesador Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a6a4f-113">[Chapter 6](chapter6.md) - Describes the demonstration application that is supplied with every Azure RTOS ThreadX processor support package</span></span>

<span data-ttu-id="a6a4f-114">[Apéndice A](appendix-a.md): API de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a6a4f-114">[Appendix A](appendix-a.md) - Azure RTOS ThreadX API</span></span>

<span data-ttu-id="a6a4f-115">[Apéndice B](appendix-b.md): constantes de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a6a4f-115">[Appendix B](appendix-b.md) - Azure RTOS ThreadX constants</span></span>

<span data-ttu-id="a6a4f-116">[Apéndice C](appendix-c.md): tipos de datos de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a6a4f-116">[Appendix C](appendix-c.md) - Azure RTOS ThreadX data types</span></span>

<span data-ttu-id="a6a4f-117">[Apéndice D](appendix-d.md): gráficos ASCII</span><span class="sxs-lookup"><span data-stu-id="a6a4f-117">[Appendix D](appendix-d.md) - ASCII chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="a6a4f-118">Convenciones de la guía</span><span class="sxs-lookup"><span data-stu-id="a6a4f-118">Guide Conventions</span></span>

<span data-ttu-id="a6a4f-119">*Cursiva*: el tipo de letra denota títulos de libros, destaca palabras importantes e indica parámetros.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-119">*Italics* - typeface denotes book titles, emphasizes important words, and indicates parameters.</span></span>

<span data-ttu-id="a6a4f-120">**Negrita**: el tipo de letra denota palabras clave, constantes, nombres de tipos, elementos de la interfaz de usuario, nombres de variables y destaca palabras importantes.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-120">**Boldface** - typeface denotes key words, constants, type names, user interface elements, variable names, and further emphasizes important words.</span></span>

<span data-ttu-id="a6a4f-121">***Cursiva y negrita***: el tipo de letra denota nombres de archivo y nombres de función.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-121">***Italics and Boldface*** - typeface denotes file names and function names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6a4f-122">Los símbolos de información llaman la atención sobre información importante o adicional que podría afectar al rendimiento o al funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-122">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!WARNING]
> <span data-ttu-id="a6a4f-123">Los símbolos de advertencia llaman la atención sobre situaciones que los desarrolladores deben intentar evitar, ya que podrían dar lugar a errores irrecuperables.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-123">Warning symbols draw attention to situations in which developers should take care to avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-threadx-data-types"></a><span data-ttu-id="a6a4f-124">Tipos de datos de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a6a4f-124">Azure RTOS ThreadX Data Types</span></span>

<span data-ttu-id="a6a4f-125">Además de los tipos de datos personalizados de la estructura de control de Azure RTOS ThreadX, hay varios tipos de datos especiales que se usan en las interfaces de llamada a servicios de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-125">In addition to the custom Azure RTOS ThreadX control structure data types, there are a series of special data types that are used in Azure RTOS ThreadX service call interfaces.</span></span> <span data-ttu-id="a6a4f-126">Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-126">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="a6a4f-127">De esta manera, se garantiza la portabilidad entre diferentes compiladores de C.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-127">This is done to insure portability between different C compilers.</span></span> <span data-ttu-id="a6a4f-128">La implementación exacta se puede encontrar en el archivo ***tx_port.h*** incluido en el origen.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-128">The exact implementation can be found in the ***tx_port.h*** file included with the source.</span></span>

<span data-ttu-id="a6a4f-129">A continuación se muestra una lista de los tipos de datos de llamada a servicios de Azure RTOS ThreadX y sus significados asociados:</span><span class="sxs-lookup"><span data-stu-id="a6a4f-129">The following is a list of Azure RTOS ThreadX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="a6a4f-130">Tipo de datos</span><span class="sxs-lookup"><span data-stu-id="a6a4f-130">Data type</span></span>  | <span data-ttu-id="a6a4f-131">Descripción</span><span class="sxs-lookup"><span data-stu-id="a6a4f-131">Description</span></span> |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="a6a4f-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="a6a4f-132">**UINT**</span></span> | <span data-ttu-id="a6a4f-133">Entero sin signo básico.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-133">Basic unsigned integer.</span></span> <span data-ttu-id="a6a4f-134">Este tipo debe admitir datos sin signo de 8 bits, pero se asigna al tipo de datos sin signo más conveniente.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-134">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="a6a4f-135">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="a6a4f-135">**ULONG**</span></span> | <span data-ttu-id="a6a4f-136">Tipo largo sin signo.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-136">Unsigned long type.</span></span> <span data-ttu-id="a6a4f-137">Este tipo debe admitir datos sin signo de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-137">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="a6a4f-138">**VOID**</span><span class="sxs-lookup"><span data-stu-id="a6a4f-138">**VOID**</span></span> | <span data-ttu-id="a6a4f-139">Casi siempre equivale al tipo void del compilador.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-139">Almost always equivalent to the compiler's void type.</span></span> |
| <span data-ttu-id="a6a4f-140">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="a6a4f-140">**CHAR**</span></span> | <span data-ttu-id="a6a4f-141">Suele ser un tipo de carácter de 8 bits estándar.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-141">Most often a standard 8-bit character type.</span></span> |
|  |  |

<span data-ttu-id="a6a4f-142">En el origen de Azure RTOS ThreadX se usan tipos de datos adicionales.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-142">Additional data types are used within the Azure RTOS ThreadX source.</span></span> <span data-ttu-id="a6a4f-143">También se encuentran en el archivo ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-143">They are also located in the ***tx_port.h*** file.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="a6a4f-144">Centro de soporte al cliente</span><span class="sxs-lookup"><span data-stu-id="a6a4f-144">Customer Support Center</span></span>

<span data-ttu-id="a6a4f-145">Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="a6a4f-146">Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:</span><span class="sxs-lookup"><span data-stu-id="a6a4f-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="a6a4f-147">Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="a6a4f-148">Una descripción detallada de los cambios en la aplicación o en Azure RTOS ThreadX que han precedido al problema.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-148">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="a6a4f-149">Contenido de la cadena *_tx_version_id* que se encuentra en el archivo *tx_port.h* de la distribución.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-149">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="a6a4f-150">Esta cadena nos proporciona información valiosa sobre el entorno en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-150">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="a6a4f-151">El contenido en la RAM de la variable **_tx_build_options** **ULONG**.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-151">The contents in RAM of the **_tx_build_options** **ULONG** variable.</span></span> <span data-ttu-id="a6a4f-152">Esta variable nos proporciona información sobre cómo se ha compilado la biblioteca de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a6a4f-152">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
