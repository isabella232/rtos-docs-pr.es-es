---
title: Manual del usuario de Azure RTOS FileX
description: Esta guía contiene información exhaustiva sobre Azure RTOS FileX, el sistema de archivos en tiempo real de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0ebcebdd2b227ed8d9ccf8b3078b716f90f35bef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814426"
---
# <a name="about-this-filex-user-guide"></a><span data-ttu-id="37ebb-103">Acerca de esta guía del usuario de FileX</span><span class="sxs-lookup"><span data-stu-id="37ebb-103">About This FileX User Guide</span></span>

<span data-ttu-id="37ebb-104">Esta guía contiene información exhaustiva sobre Azure RTOS FileX, el sistema de archivos incrustado en tiempo real de alto rendimiento de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="37ebb-104">This guide contains comprehensive information about Azure RTOS FileX, the high-performance, real-time embedded file system from Microsoft.</span></span> <span data-ttu-id="37ebb-105">Para sacar el máximo partido de esta guía, debe estar familiarizado con las funciones estándar del sistema operativo en tiempo real, los servicios del sistema de archivos FAT y el lenguaje de programación C.</span><span class="sxs-lookup"><span data-stu-id="37ebb-105">To gain the most from this guide, you should be familiar with standard real-time operating system functions, FAT file system services, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="37ebb-106">Organización</span><span class="sxs-lookup"><span data-stu-id="37ebb-106">Organization</span></span>

<span data-ttu-id="37ebb-107">[Capítulo 1](chapter1.md) Presenta Azure RTOS FileX.</span><span class="sxs-lookup"><span data-stu-id="37ebb-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS FileX</span></span>

<span data-ttu-id="37ebb-108">[Capítulo 2](chapter2.md) Proporciona los pasos básicos para instalar y usar Azure RTOS FileX con su aplicación de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="37ebb-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS FileX with your Azure RTOS ThreadX application</span></span>

<span data-ttu-id="37ebb-109">[Capítulo 3](chapter3.md) Proporciona una visión general funcional del sistema de Azure RTOS FileX y la información básica sobre los formatos del sistema de archivos FAT.</span><span class="sxs-lookup"><span data-stu-id="37ebb-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS FileX system and basic information about FAT file system formats</span></span>

<span data-ttu-id="37ebb-110">[Capítulo 4](chapter4.md) : detalla la interfaz de la aplicación para Azure RTOS FileX.</span><span class="sxs-lookup"><span data-stu-id="37ebb-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS FileX</span></span>

<span data-ttu-id="37ebb-111">[Capítulo 5](chapter5.md) Describe el controlador de RAM de Azure RTOS FileX proporcionado y cómo escribir sus propios controladores personalizados de Azure RTOS FileX.</span><span class="sxs-lookup"><span data-stu-id="37ebb-111">[Chapter 5](chapter5.md) - Describes the supplied Azure RTOS FileX RAM driver and how to write your own custom Azure RTOS FileX drivers</span></span>

<span data-ttu-id="37ebb-112">[Capítulo 6](chapter6.md) Describe del módulo de tolerancia a errores de Azure RTOS FileX.</span><span class="sxs-lookup"><span data-stu-id="37ebb-112">[Chapter 6](chapter6.md) - Describes the Azure RTOS FileX Fault Tolerant Module</span></span>

<span data-ttu-id="37ebb-113">[Apéndice A](appendix-a.md) Servicios de Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="37ebb-113">[Appendix A](appendix-a.md) - Azure RTOS FileX Services</span></span>

<span data-ttu-id="37ebb-114">[Apéndice B](appendix-b.md) Constantes de Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="37ebb-114">[Appendix B](appendix-b.md) - Azure RTOS FileX Constants</span></span>

<span data-ttu-id="37ebb-115">[Apéndice C](appendix-c.md) Tipos de datos de Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="37ebb-115">[Appendix C](appendix-c.md) - Azure RTOS FileX Data Types</span></span>

<span data-ttu-id="37ebb-116">[Apéndice D](appendix-d.md) Gráficos ASCII</span><span class="sxs-lookup"><span data-stu-id="37ebb-116">[Appendix D](appendix-d.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="37ebb-117">Convenciones de la guía</span><span class="sxs-lookup"><span data-stu-id="37ebb-117">Guide Conventions</span></span>

<span data-ttu-id="37ebb-118">*Cursiva*: el tipo de letra denota títulos de libros, destaca palabras importantes e indica variables.</span><span class="sxs-lookup"><span data-stu-id="37ebb-118">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="37ebb-119">**Negrita**: el tipo de letra indica nombres de archivo, palabras clave y, además, destaca palabras importantes y variables.</span><span class="sxs-lookup"><span data-stu-id="37ebb-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="37ebb-120">Los símbolos de información llaman la atención sobre información importante o adicional que podría afectar al rendimiento o al funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="37ebb-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="37ebb-121">Los símbolos de advertencia llaman la atención sobre situaciones que los desarrolladores deben intentar evitar, ya que podrían dar lugar a errores irrecuperables.</span><span class="sxs-lookup"><span data-stu-id="37ebb-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="filex-data-types"></a><span data-ttu-id="37ebb-122">Tipos de datos FileX</span><span class="sxs-lookup"><span data-stu-id="37ebb-122">FileX Data Types</span></span>

<span data-ttu-id="37ebb-123">Además de los tipos de datos personalizados de la estructura de control de Azure RTOS FileX, hay varios tipos de datos especiales que se usan en las interfaces de llamada a servicios de Azure RTOS FileX.</span><span class="sxs-lookup"><span data-stu-id="37ebb-123">In addition to the custom Azure RTOS FileX control structure data types, there is a series of special data types that are used in Azure RTOS FileX service call interfaces.</span></span> <span data-ttu-id="37ebb-124">Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente.</span><span class="sxs-lookup"><span data-stu-id="37ebb-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="37ebb-125">De esta manera, se garantiza la portabilidad entre diferentes compiladores de C.</span><span class="sxs-lookup"><span data-stu-id="37ebb-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="37ebb-126">La implementación exacta se hereda de Azure RTOS ThreadX y se puede encontrar en el archivo tx_port.h incluido en la distribución de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="37ebb-126">The exact implementation is inherited from Azure RTOS ThreadX and can be found in the tx_port.h file included in the Azure RTOS ThreadX distribution.</span></span>

<span data-ttu-id="37ebb-127">A continuación se muestra una lista de los tipos de datos de llamada a servicios de Azure RTOS FileX y sus significados asociados.</span><span class="sxs-lookup"><span data-stu-id="37ebb-127">The following is a list of Azure RTOS FileX service call data types and their associated meanings.</span></span>
| <span data-ttu-id="37ebb-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="37ebb-128">Type</span></span>  | <span data-ttu-id="37ebb-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="37ebb-129">Description</span></span>  |
|---|---|
| <span data-ttu-id="37ebb-130">**UINT**</span><span class="sxs-lookup"><span data-stu-id="37ebb-130">**UINT**</span></span> | <span data-ttu-id="37ebb-131">Entero sin signo básico.</span><span class="sxs-lookup"><span data-stu-id="37ebb-131">Basic unsigned integer.</span></span> <span data-ttu-id="37ebb-132">Este tipo debe admitir datos sin signo de 8 bits, pero se asigna al tipo de datos sin signo más conveniente.</span><span class="sxs-lookup"><span data-stu-id="37ebb-132">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="37ebb-133">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="37ebb-133">**ULONG**</span></span> | <span data-ttu-id="37ebb-134">Tipo largo sin signo.</span><span class="sxs-lookup"><span data-stu-id="37ebb-134">Unsigned long type.</span></span> <span data-ttu-id="37ebb-135">Este tipo debe admitir datos sin signo de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="37ebb-135">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="37ebb-136">**VOID**</span><span class="sxs-lookup"><span data-stu-id="37ebb-136">**VOID**</span></span> | <span data-ttu-id="37ebb-137">Casi siempre equivale al tipo void del compilador.</span><span class="sxs-lookup"><span data-stu-id="37ebb-137">Almost always equivalent to the compiler’s void type.</span></span> |
| <span data-ttu-id="37ebb-138">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="37ebb-138">**CHAR**</span></span> | <span data-ttu-id="37ebb-139">Suele ser un tipo de carácter de 8 bits estándar.</span><span class="sxs-lookup"><span data-stu-id="37ebb-139">Most often a standard 8-bit character type.</span></span> |
| <span data-ttu-id="37ebb-140">**ULONG64**</span><span class="sxs-lookup"><span data-stu-id="37ebb-140">**ULONG64**</span></span> | <span data-ttu-id="37ebb-141">Tipo de datos entero sin signo de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="37ebb-141">64-bit unsigned integer data type.</span></span> |

<span data-ttu-id="37ebb-142">Se usan tipos de datos adicionales en el origen de FileX.</span><span class="sxs-lookup"><span data-stu-id="37ebb-142">Additional data types are used within the FileX source.</span></span> <span data-ttu-id="37ebb-143">Se encuentran en los archivos \***tx_port.h** _ o _ \*_fx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="37ebb-143">They are located in either the ***tx_port.h** _ or _ *_fx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="37ebb-144">Centro de soporte al cliente</span><span class="sxs-lookup"><span data-stu-id="37ebb-144">Customer Support Center</span></span>

<span data-ttu-id="37ebb-145">Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="37ebb-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="37ebb-146">Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible.</span><span class="sxs-lookup"><span data-stu-id="37ebb-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="37ebb-147">Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.</span><span class="sxs-lookup"><span data-stu-id="37ebb-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="37ebb-148">Una descripción detallada de los cambios en la aplicación o en FileX que precedieron al problema.</span><span class="sxs-lookup"><span data-stu-id="37ebb-148">A detailed description of any changes to the application and/or FileX that preceded the problem.</span></span>
3. <span data-ttu-id="37ebb-149">El contenido de las cadenas_tx_version_id y _fx_version_id que se encuentran en los archivos **tx_port.h**_ y _ *_fx_port.h_*\* de la distribución.</span><span class="sxs-lookup"><span data-stu-id="37ebb-149">The contents of the _tx_version_id and _fx_version_id strings found in the \***tx_port.h**_ and _ *_fx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="37ebb-150">Estas cadenas nos proporcionan información valiosa sobre el entorno en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="37ebb-150">These strings will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="37ebb-151">El contenido en la RAM de las siguientes variables **ULONG**.</span><span class="sxs-lookup"><span data-stu-id="37ebb-151">The contents in RAM of the following **ULONG** variables.</span></span> <span data-ttu-id="37ebb-152">Estas variables nos proporcionarán información sobre cómo se compilaron las bibliotecas de ThreadX y FileX:</span><span class="sxs-lookup"><span data-stu-id="37ebb-152">These variables will give us information on how your ThreadX and FileX libraries were built:</span></span>

    <span data-ttu-id="37ebb-153">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="37ebb-153">**_tx_build_options**</span></span>

    <span data-ttu-id="37ebb-154">**_fx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="37ebb-154">**_fx_system_build_options1**</span></span>

    <span data-ttu-id="37ebb-155">**_fx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="37ebb-155">**_fx_system_build_options2**</span></span>

    <span data-ttu-id="37ebb-156">**_fx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="37ebb-156">**_fx_system_build_options3**</span></span>
