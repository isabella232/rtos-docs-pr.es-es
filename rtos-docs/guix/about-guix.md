---
title: Guía del usuario de Azure RTOS GUIX
description: Esta guía contiene información exhaustiva sobre Azure RTOS GUIX, el producto de GUI de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b7af0fba59b599c9c8db3ab80a3271eacfd11992
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815581"
---
# <a name="about-guix-user-guide"></a><span data-ttu-id="45478-103">Acerca de la guía del usuario de GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-103">About GUIX User Guide</span></span>

<span data-ttu-id="45478-104">Esta guía contiene información exhaustiva sobre Azure RTOS GUIX, el producto de GUI de alto rendimiento de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="45478-104">This guide contains comprehensive information about Azure RTOS GUIX, the high-performance GUI product from Microsoft.</span></span> <span data-ttu-id="45478-105">Está destinada a los desarrolladores de software insertado en tiempo real que están familiarizados con los conceptos básicos de GUI, Azure RTOS ThreadX y el lenguaje de programación C.</span><span class="sxs-lookup"><span data-stu-id="45478-105">It is intended for embedded real-time software developers familiar with basic GUI concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="45478-106">Organización</span><span class="sxs-lookup"><span data-stu-id="45478-106">Organization</span></span>

[<span data-ttu-id="45478-107">Capítulo 1: Introducción a Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-107">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>](chapter-1.md)

[<span data-ttu-id="45478-108">Capítulo 2: Instalación y uso de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-108">Chapter 2 - Installation and use of Azure RTOS GUIX</span></span>](chapter-2.md)

[<span data-ttu-id="45478-109">Capítulo 3: Introducción funcional a Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-109">Chapter 3 - Functional Overview of Azure RTOS GUIX</span></span>](chapter-3.md)

[<span data-ttu-id="45478-110">Capítulo 4: Descripción de los servicios de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-110">Chapter 4 - Description of Azure RTOS GUIX Services</span></span>](chapter-4.md)

[<span data-ttu-id="45478-111">Capítulo 5: Controladores de pantalla de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-111">Chapter 5 - Azure RTOS GUIX Display Drivers</span></span>](chapter-5.md)  

[<span data-ttu-id="45478-112">Ejemplo de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-112">Azure RTOS GUIX Example</span></span>](guix-example.md)

[<span data-ttu-id="45478-113">Apéndice A: Definiciones de color de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-113">Appendix A - Azure RTOS GUIX Color Definitions</span></span>](appendix-a.md)

[<span data-ttu-id="45478-114">Apéndice B: Formatos de color de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-114">Appendix B - Azure RTOS GUIX Color Formats</span></span>](appendix-b.md)

[<span data-ttu-id="45478-115">Apéndice C: Estilos de widget de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-115">Appendix C - Azure RTOS GUIX Widget Styles</span></span>](appendix-c.md)

[<span data-ttu-id="45478-116">Apéndice D: Atributos de pincel, lienzo y degradado de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-116">Appendix D - Azure RTOS GUIX Brush, Canvas and Gradient Attributes</span></span>](appendix-d.md)

[<span data-ttu-id="45478-117">Apéndice E: Descripción de eventos de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-117">Appendix E - Azure RTOS GUIX Event Description</span></span>](appendix-e.md)

[<span data-ttu-id="45478-118">Apéndice F: Servicios de enlace de RTOS de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-118">Appendix F - Azure RTOS GUIX RTOS Binding Services</span></span>](appendix-f.md)

[<span data-ttu-id="45478-119">Apéndice G: Estructura de fuente de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-119">Appendix G - Azure RTOS GUIX Font Structure</span></span>](appendix-g.md)

[<span data-ttu-id="45478-120">Apéndice H: Marcas de configuración de tiempo de compilación de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-120">Appendix H - Azure RTOS GUIX Build-Time Configuration flags</span></span>](appendix-h.md)

[<span data-ttu-id="45478-121">Apéndice I: Estructuras de información de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-121">Appendix I - Azure RTOS GUIX Information Structures</span></span>](appendix-i.md)

## <a name="guide-conventions"></a><span data-ttu-id="45478-122">Convenciones de la guía</span><span class="sxs-lookup"><span data-stu-id="45478-122">Guide Conventions</span></span>

<span data-ttu-id="45478-123">*Cursiva*: el tipo de letra denota títulos de libros, destaca palabras importantes e indica variables.</span><span class="sxs-lookup"><span data-stu-id="45478-123">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="45478-124">**Negrita**: el tipo de letra indica nombres de archivo, palabras clave y, además, destaca palabras importantes y variables.</span><span class="sxs-lookup"><span data-stu-id="45478-124">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45478-125">Los símbolos de información llaman la atención sobre información importante o adicional que podría afectar al rendimiento o al funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="45478-125">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

## <a name="azure-rtos-guix-data-types"></a><span data-ttu-id="45478-126">Tipos de datos de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="45478-126">Azure RTOS GUIX Data Types</span></span>

<span data-ttu-id="45478-127">Además de los tipos de datos personalizados de la estructura de control de Azure RTOS GUIX, hay varios tipos de datos especiales que se usan en las interfaces de llamada a servicios de Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="45478-127">In addition to the custom Azure RTOS GUIX control structure data types, there are several special data types that are used in Azure RTOS GUIX service call interfaces.</span></span> <span data-ttu-id="45478-128">Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente.</span><span class="sxs-lookup"><span data-stu-id="45478-128">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="45478-129">De esta manera, se garantiza la portabilidad entre diferentes compiladores de C.</span><span class="sxs-lookup"><span data-stu-id="45478-129">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="45478-130">La implementación exacta se hereda de ThreadX y se puede encontrar en el archivo ***tx_port.h*** incluido en la distribución de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="45478-130">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="45478-131">A continuación se muestra una lista de los tipos de datos de llamada a servicios de Azure RTOS GUIX y sus significados asociados:</span><span class="sxs-lookup"><span data-stu-id="45478-131">The following is a list of Azure RTOS GUIX service call data types and their associated meanings:</span></span>

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="45478-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="45478-132">**UINT**</span></span>             | <span data-ttu-id="45478-133">Entero sin signo básico.</span><span class="sxs-lookup"><span data-stu-id="45478-133">Basic unsigned integer.</span></span> <span data-ttu-id="45478-134">Este tipo se asigna al tipo de datos sin signo más conveniente.</span><span class="sxs-lookup"><span data-stu-id="45478-134">This type is mapped to the most convenient unsigned data type.</span></span>                                |
| <span data-ttu-id="45478-135">**INT**</span><span class="sxs-lookup"><span data-stu-id="45478-135">**INT**</span></span>              | <span data-ttu-id="45478-136">Entero con signo básico.</span><span class="sxs-lookup"><span data-stu-id="45478-136">Basic signed integer.</span></span> <span data-ttu-id="45478-137">Este tipo se asigna al tipo de datos con signo más conveniente.</span><span class="sxs-lookup"><span data-stu-id="45478-137">This type is mapped to the most convenient signed data type.</span></span>                                    |
| <span data-ttu-id="45478-138">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="45478-138">**ULONG**</span></span>            | <span data-ttu-id="45478-139">Tipo largo sin signo.</span><span class="sxs-lookup"><span data-stu-id="45478-139">Unsigned long type.</span></span> <span data-ttu-id="45478-140">Este tipo debe admitir datos sin signo de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="45478-140">This type must support 32-bit unsigned data.</span></span>                                                      |
| <span data-ttu-id="45478-141">**VOID**</span><span class="sxs-lookup"><span data-stu-id="45478-141">**VOID**</span></span>             | <span data-ttu-id="45478-142">Casi siempre equivale al tipo void del compilador.</span><span class="sxs-lookup"><span data-stu-id="45478-142">Almost always equivalent to the compiler’s void type.</span></span>                                                                 |
| <span data-ttu-id="45478-143">**GX_CHAR**</span><span class="sxs-lookup"><span data-stu-id="45478-143">**GX_CHAR**</span></span>         | <span data-ttu-id="45478-144">La mayoría de las veces se usa typedef como tipo de carácter definido por el compilador.</span><span class="sxs-lookup"><span data-stu-id="45478-144">Most often typedefed as the compiler defined char type.</span></span>                                                               |
| <span data-ttu-id="45478-145">**GX_BYTE**</span><span class="sxs-lookup"><span data-stu-id="45478-145">**GX_BYTE**</span></span>          | <span data-ttu-id="45478-146">Tipo con signo de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="45478-146">8-bit signed type.</span></span>                                                                                                    |
| <span data-ttu-id="45478-147">**GX_UBYTE**</span><span class="sxs-lookup"><span data-stu-id="45478-147">**GX_UBYTE**</span></span>         | <span data-ttu-id="45478-148">Tipo sin signo de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="45478-148">8-bit unsigned type.</span></span>                                                                                                  |
| <span data-ttu-id="45478-149">**GX_VALUE**</span><span class="sxs-lookup"><span data-stu-id="45478-149">**GX_VALUE**</span></span>        | <span data-ttu-id="45478-150">Tipo con signo de 16 o 32 bits.</span><span class="sxs-lookup"><span data-stu-id="45478-150">16 or 32 bit signed type.</span></span> <span data-ttu-id="45478-151">Se define según sea necesario para obtener el mejor rendimiento en el sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="45478-151">Defined as needed for best performance on the target system.</span></span>                                |
| <span data-ttu-id="45478-152">**GX_FIXED_VAL**</span><span class="sxs-lookup"><span data-stu-id="45478-152">**GX_FIXED_VAL**</span></span>   | <span data-ttu-id="45478-153">Tipo de datos numérico de punto fijo.</span><span class="sxs-lookup"><span data-stu-id="45478-153">Fixed point numeric data type.</span></span>                                                                                        |
| <span data-ttu-id="45478-154">**GX_RESOURCE_ID**</span><span class="sxs-lookup"><span data-stu-id="45478-154">**GX_RESOURCE_ID**</span></span> | <span data-ttu-id="45478-155">Tipo largo sin signo.</span><span class="sxs-lookup"><span data-stu-id="45478-155">Unsigned long type.</span></span>                                                                                                   |
| <span data-ttu-id="45478-156">**GX_COLOR**</span><span class="sxs-lookup"><span data-stu-id="45478-156">**GX_COLOR**</span></span>        | <span data-ttu-id="45478-157">Tipo largo sin signo.</span><span class="sxs-lookup"><span data-stu-id="45478-157">Unsigned long type.</span></span>                                                                                                   |
| <span data-ttu-id="45478-158">**GX_STRING**</span><span class="sxs-lookup"><span data-stu-id="45478-158">**GX_STRING**</span></span>       | <span data-ttu-id="45478-159">Estructura que contiene GX_CHAR \*gx_string_ptr y UINT gx_string_length.</span><span class="sxs-lookup"><span data-stu-id="45478-159">Structure containing GX_CHAR \*gx_string_ptr and UINT gx_string_length.</span></span>                                          |
| <span data-ttu-id="45478-160">**GX_POINT**</span><span class="sxs-lookup"><span data-stu-id="45478-160">**GX_POINT**</span></span>        | <span data-ttu-id="45478-161">Estructura que contiene gx_point_x y gx_point_y.</span><span class="sxs-lookup"><span data-stu-id="45478-161">Structure containing gx_point_x and gx_point_y.</span></span>                                                                   |
| <span data-ttu-id="45478-162">**GX_RECTANGLE**</span><span class="sxs-lookup"><span data-stu-id="45478-162">**GX_RECTANGLE**</span></span>    | <span data-ttu-id="45478-163">Estructura que contiene los campos gx_rectangle_left, gx_rectangle_top, gx_rectangle_right y gx_rectangle_bottom.</span><span class="sxs-lookup"><span data-stu-id="45478-163">Structure containing gx_rectangle_left, gx_rectangle_top, gx_rectangle_right, and gx_rectangle_bottom fields.</span></span> |
| <span data-ttu-id="45478-164">**GX_GLYPH**</span><span class="sxs-lookup"><span data-stu-id="45478-164">**GX_GLYPH**</span></span>        | <span data-ttu-id="45478-165">Estructura que contiene métricas de glifo.</span><span class="sxs-lookup"><span data-stu-id="45478-165">Structure containing glyph metrics.</span></span>                                                                                   |
| <span data-ttu-id="45478-166">**GX_FONT**</span><span class="sxs-lookup"><span data-stu-id="45478-166">**GX_FONT**</span></span>         | <span data-ttu-id="45478-167">Estructura que contiene métricas de fuente.</span><span class="sxs-lookup"><span data-stu-id="45478-167">Structure containing font metrics.</span></span>                                                                                    |
| <span data-ttu-id="45478-168">**GX_BRUSH**</span><span class="sxs-lookup"><span data-stu-id="45478-168">**GX_BRUSH**</span></span>        | <span data-ttu-id="45478-169">Estructura que contiene métricas de pincel.</span><span class="sxs-lookup"><span data-stu-id="45478-169">Structure containing brush metrics.</span></span>                                                                               |
<span data-ttu-id="45478-170">**GX_PIXELMAP**</span><span class="sxs-lookup"><span data-stu-id="45478-170">**GX_PIXELMAP**</span></span>       | <span data-ttu-id="45478-171">Estructura que contiene métricas de mapa de píxeles.</span><span class="sxs-lookup"><span data-stu-id="45478-171">Structure containing pixelmap metrics.</span></span>

<span data-ttu-id="45478-172">En el origen de Azure RTOS GUIX se usan tipos de datos adicionales.</span><span class="sxs-lookup"><span data-stu-id="45478-172">Additional data types are used within the Azure RTOS GUIX source.</span></span> <span data-ttu-id="45478-173">Se encuentran en los archivos \***tx_port.h** _ o _ \*_gx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="45478-173">They are located in either the ***tx_port.h** _ or _ *_gx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="45478-174">Centro de soporte al cliente</span><span class="sxs-lookup"><span data-stu-id="45478-174">Customer Support Center</span></span>

<span data-ttu-id="45478-175">Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="45478-175">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="45478-176">Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:</span><span class="sxs-lookup"><span data-stu-id="45478-176">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="45478-177">Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.</span><span class="sxs-lookup"><span data-stu-id="45478-177">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="45478-178">Una descripción detallada de los cambios en la aplicación o en Azure RTOS GUIX que han precedido al problema.</span><span class="sxs-lookup"><span data-stu-id="45478-178">A detailed description of any changes to the application and/or Azure RTOS GUIX that preceded the problem.</span></span>

3. <span data-ttu-id="45478-179">El contenido de las cadenas _tx_version_id y _gx_version_id que se encuentran en los archivos \***tx_port.h**_ y _ *_gx_port.h_*\* de la distribución.</span><span class="sxs-lookup"><span data-stu-id="45478-179">The contents of the _tx_version_id and _gx_version_id strings found in the \***tx_port.h**_ and _ *_gx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="45478-180">Estas cadenas nos proporcionan información valiosa sobre el entorno en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="45478-180">These strings will provide us valuable Information regarding your run-time environment.</span></span>

4. <span data-ttu-id="45478-181">El contenido en la RAM de las siguientes variables ULONG:</span><span class="sxs-lookup"><span data-stu-id="45478-181">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="45478-182">**_tx_build_options** **_gx_system_build_options**</span><span class="sxs-lookup"><span data-stu-id="45478-182">**_tx_build_options** **_gx_system_build_options**</span></span>

    <span data-ttu-id="45478-183">Estas variables nos proporcionan información sobre cómo se han compilado las bibliotecas de Azure RTOS ThreadX y Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="45478-183">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS GUIX libraries were built.</span></span>

5. <span data-ttu-id="45478-184">El contenido en la RAM de las siguientes variables ULONG:</span><span class="sxs-lookup"><span data-stu-id="45478-184">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="45478-185">**_gx_system_last_error** **_gx_system_error_count**</span><span class="sxs-lookup"><span data-stu-id="45478-185">**_gx_system_last_error** **_gx_system_error_count**</span></span>

    <span data-ttu-id="45478-186">Estas variables hacen un seguimiento de los errores internos del sistema en Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="45478-186">These variables keep track of internal system errors in Azure RTOS GUIX.</span></span> <span data-ttu-id="45478-187">Si _gx_system_error_count es mayor que uno, establezca un punto de interrupción en el valor devuelto de la función _gx_system_error_process y proporcione el valor de _gx_system_last_error en este punto.</span><span class="sxs-lookup"><span data-stu-id="45478-187">If the _gx_system_error_count is greater than one, please set a breakpoint on the function return in the _gx_system_error_process function and provide the value of _gx_system_last_error at this point.</span></span> <span data-ttu-id="45478-188">Esto suspende el primer error interno del sistema de Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="45478-188">This will yield the first internal Azure RTOS GUIX system error.</span></span>

6. <span data-ttu-id="45478-189">Un búfer de seguimiento capturado inmediatamente después de que se haya detectado el problema.</span><span class="sxs-lookup"><span data-stu-id="45478-189">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="45478-190">Puede hacerse si se compilan las bibliotecas de Azure RTOS ThreadX y Azure RTOS GUIX con TX_ENABLE_EVENT_TRACE y se llama a tx_trace_enable con la información del búfer de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="45478-190">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS GUIX libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>

7. <span data-ttu-id="45478-191">El proyecto de Azure RTOS GUIX Studio que usa, si procede, o, al menos, un pequeño proyecto suficiente para mostrar la deficiencia que está notificando.</span><span class="sxs-lookup"><span data-stu-id="45478-191">The Azure RTOS GUIX Studio project you are using, if applicable, or at a minimum a small project sufficient to demonstrate the deficiency you are reporting.</span></span>
