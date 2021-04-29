---
title: 'Capítulo 1: Introducción a GUIX'
description: GUIX es una implementación en tiempo real de alto rendimiento de una GUI diseñada exclusivamente para aplicaciones insertadas basadas en Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b90da988a03d59b1bca3f5584164d641bef96454
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815522"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a><span data-ttu-id="785cc-103">Capítulo 1: Introducción a Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="785cc-103">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>

<span data-ttu-id="785cc-104">Azure RTOS GUIX (GUIX) es una implementación en tiempo real de alto rendimiento de un marco de interfaz gráfica diseñada exclusivamente para aplicaciones insertadas basadas en ThreadX.</span><span class="sxs-lookup"><span data-stu-id="785cc-104">Azure RTOS GUIX (GUIX) is a high-performance real-time implementation of a graphical interface framework designed exclusively for embedded ThreadX-based applications.</span></span> <span data-ttu-id="785cc-105">Este capítulo contiene una introducción a GUIX y una descripción de sus aplicaciones y ventajas.</span><span class="sxs-lookup"><span data-stu-id="785cc-105">This chapter contains an introduction to GUIX and a description of its applications and benefits.</span></span>

## <a name="guix-feature-overview"></a><span data-ttu-id="785cc-106">Información general de las características de GUIX</span><span class="sxs-lookup"><span data-stu-id="785cc-106">GUIX Feature Overview</span></span>

<span data-ttu-id="785cc-107">A diferencia de muchas otras implementaciones de GUI, GUIX está diseñada para ser versátil, ya que permite escalar fácilmente desde pequeñas aplicaciones basadas en microcontroladores a otras que usan los potentes procesadores RISC y DSP.</span><span class="sxs-lookup"><span data-stu-id="785cc-107">Unlike many other GUI implementations, GUIX is designed to be versatile—easily scaling from small micro-controller-based applications to those that use powerful RISC and DSP processors.</span></span> <span data-ttu-id="785cc-108">Significa un marcado contraste con las implementaciones de dominio público u otras implementaciones comerciales diseñadas originalmente para entornos de estación de trabajo, pero que después se han aprovechado para diseños insertados.</span><span class="sxs-lookup"><span data-stu-id="785cc-108">This is in sharp contrast to public domain or other commercial implementations originally intended for workstation environments but then squeezed into embedded designs.</span></span> <span data-ttu-id="785cc-109">A continuación, se ofrece información general sobre las características de GUIX:</span><span class="sxs-lookup"><span data-stu-id="785cc-109">An overview of GUIX features follows:</span></span>

- <span data-ttu-id="785cc-110">Fácil de usar con la herramienta de diseño basada en host GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="785cc-110">Easy to use with host-based design tool GUIX Studio</span></span>

- <span data-ttu-id="785cc-111">Entorno de tiempo de ejecución de GUIX de Win32 para un prototipo completo hospedado</span><span class="sxs-lookup"><span data-stu-id="785cc-111">Win32 GUIX run-time environment for complete hosted prototyping</span></span>

- <span data-ttu-id="785cc-112">Compatible con la mayoría de los procesadores que ThreadX admite</span><span class="sxs-lookup"><span data-stu-id="785cc-112">Supports most processors supported by ThreadX</span></span>

- <span data-ttu-id="785cc-113">Escrita exclusivamente en ANSI C</span><span class="sxs-lookup"><span data-stu-id="785cc-113">Written exclusively in ANSI C</span></span>

- <span data-ttu-id="785cc-114">Endian neutro</span><span class="sxs-lookup"><span data-stu-id="785cc-114">Endian neutral</span></span>

- <span data-ttu-id="785cc-115">La GUI insertada más pequeña y rápida</span><span class="sxs-lookup"><span data-stu-id="785cc-115">Smallest, Fasted Embedded GUI</span></span>

- <span data-ttu-id="785cc-116">Tiempo de ejecución configurable, número de objetos, tamaño de la pantalla, etc.</span><span class="sxs-lookup"><span data-stu-id="785cc-116">Run-time configurable, number of objects, screen size, etc.</span></span>

- <span data-ttu-id="785cc-117">Interfaz de controlador de pantalla fácil de escribir</span><span class="sxs-lookup"><span data-stu-id="785cc-117">Easy to write display driver interface</span></span>

- <span data-ttu-id="785cc-118">Compatibilidad con color (hasta 32 bpp de profundidad de color), monocromo y escala de grises</span><span class="sxs-lookup"><span data-stu-id="785cc-118">Color (up to 32-bpp color depth), monochrome, and grayscale support</span></span>

- <span data-ttu-id="785cc-119">Compatibilidad multilingüe a través de la codificación de cadenas UTF8 y los recursos de cadena</span><span class="sxs-lookup"><span data-stu-id="785cc-119">Multilingual support via UTF8 string encoding and string resources</span></span>

- <span data-ttu-id="785cc-120">Fuentes gratuitas predeterminadas y facilidad para la adición de otras nuevas</span><span class="sxs-lookup"><span data-stu-id="785cc-120">Default free fonts and easy to add new fonts</span></span>

- <span data-ttu-id="785cc-121">Compatibilidad con varios lienzos de dibujo, de varios tamaños</span><span class="sxs-lookup"><span data-stu-id="785cc-121">Multiple drawing Canvases supported, of various sizes</span></span>

- <span data-ttu-id="785cc-122">Compatibilidad con varias pantallas de diferentes tamaños y profundidades de color</span><span class="sxs-lookup"><span data-stu-id="785cc-122">Multiple displays of different sizes and color depths supported</span></span>

- <span data-ttu-id="785cc-123">Compatibilidad con la transición de pantalla (fundido de entrada, fundido de salida, pasar el dedo, etc.)</span><span class="sxs-lookup"><span data-stu-id="785cc-123">Screen Transition support (fade in, fade out, swipe, etc.)</span></span>

- <span data-ttu-id="785cc-124">Compatibilidad con pantalla táctil, gesto y teclado virtual</span><span class="sxs-lookup"><span data-stu-id="785cc-124">Touch Screen, Gesture, and Virtual Keyboard Support</span></span>

- <span data-ttu-id="785cc-125">Compresión de mapa de bits</span><span class="sxs-lookup"><span data-stu-id="785cc-125">Bitmap compression</span></span>

- <span data-ttu-id="785cc-126">Compatibilidad con la combinación alfa</span><span class="sxs-lookup"><span data-stu-id="785cc-126">Alpha Blending Support</span></span>

- <span data-ttu-id="785cc-127">Compatibilidad con la interpolación</span><span class="sxs-lookup"><span data-stu-id="785cc-127">Dither Support</span></span>

- <span data-ttu-id="785cc-128">Compatibilidad con el suavizado de contorno</span><span class="sxs-lookup"><span data-stu-id="785cc-128">Anti-Aliasing Support</span></span>

- <span data-ttu-id="785cc-129">Cambio de aspecto visual y temas</span><span class="sxs-lookup"><span data-stu-id="785cc-129">Skinning and Themes</span></span>

- <span data-ttu-id="785cc-130">Combinación de lienzos</span><span class="sxs-lookup"><span data-stu-id="785cc-130">Canvas Blending</span></span>

- <span data-ttu-id="785cc-131">Administración completa de ventanas</span><span class="sxs-lookup"><span data-stu-id="785cc-131">Complete Window Management</span></span>

  - <span data-ttu-id="785cc-132">Relación de elementos primarios y secundarios</span><span class="sxs-lookup"><span data-stu-id="785cc-132">Parent/Child Relationship</span></span>

  - <span data-ttu-id="785cc-133">Creación, eliminación, cambio de tamaño y movimiento dinámicos</span><span class="sxs-lookup"><span data-stu-id="785cc-133">Dynamic creation, deletion, resizing, moving</span></span>
  - <span data-ttu-id="785cc-134">Control de eventos y dibujo independientes</span><span class="sxs-lookup"><span data-stu-id="785cc-134">Separate event handling and drawing</span></span> 
  - <span data-ttu-id="785cc-135">Orden Z</span><span class="sxs-lookup"><span data-stu-id="785cc-135">Z-order</span></span>
  - <span data-ttu-id="785cc-136">Recorte y vistas</span><span class="sxs-lookup"><span data-stu-id="785cc-136">Clipping and views</span></span>

- <span data-ttu-id="785cc-137">Amplio conjunto de widgets</span><span class="sxs-lookup"><span data-stu-id="785cc-137">Extensive Set of Widgets</span></span>

  - <span data-ttu-id="785cc-138">Varios tipos de botón, controles deslizantes y diales</span><span class="sxs-lookup"><span data-stu-id="785cc-138">Various button types, sliders, and dials</span></span>

  - <span data-ttu-id="785cc-139">Lista desplegable</span><span class="sxs-lookup"><span data-stu-id="785cc-139">Drop Down List</span></span>
  
  - <span data-ttu-id="785cc-140">Prompt</span><span class="sxs-lookup"><span data-stu-id="785cc-140">Prompt</span></span>

  - <span data-ttu-id="785cc-141">Vista de texto de varias líneas</span><span class="sxs-lookup"><span data-stu-id="785cc-141">Multi-Line text view</span></span>
  
  - <span data-ttu-id="785cc-142">Entrada de texto de una y varias líneas</span><span class="sxs-lookup"><span data-stu-id="785cc-142">Single and Multi-Line text input</span></span>
  
  - <span data-ttu-id="785cc-143">Ruedas del mouse numéricas y textuales</span><span class="sxs-lookup"><span data-stu-id="785cc-143">Numeric and Textual Scroll Wheels</span></span>
  
  - <span data-ttu-id="785cc-144">Ventanas y barras de desplazamiento</span><span class="sxs-lookup"><span data-stu-id="785cc-144">Windows and Scroll Bars</span></span>
  
  - <span data-ttu-id="785cc-145">Barra de progreso radial</span><span class="sxs-lookup"><span data-stu-id="785cc-145">Radial Progress Bar</span></span>
  
  - <span data-ttu-id="785cc-146">Sprite</span><span class="sxs-lookup"><span data-stu-id="785cc-146">Sprite</span></span>

### <a name="ansi-c-source-code"></a><span data-ttu-id="785cc-147">Código fuente ANSI C</span><span class="sxs-lookup"><span data-stu-id="785cc-147">ANSI C Source Code</span></span>

<span data-ttu-id="785cc-148">GUIX está escrita completamente en ANSI C y se puede portar de forma inmediata a prácticamente cualquier arquitectura de procesador que tenga un compilador ANSI C y compatibilidad con ThreadX.</span><span class="sxs-lookup"><span data-stu-id="785cc-148">GUIX is written completely in ANSI C and is portable immediately to virtually any processor architecture that has an ANSI C compiler and ThreadX support.</span></span> <span data-ttu-id="785cc-149">Aunque está escrita en ANSI C, GUIX utiliza un modelo orientado a objetos y la herencia.</span><span class="sxs-lookup"><span data-stu-id="785cc-149">Although written in ANSI C, GUIX uses an object oriented model and inheritance.</span></span>

### <a name="not-a-black-box"></a><span data-ttu-id="785cc-150">No es una caja negra</span><span class="sxs-lookup"><span data-stu-id="785cc-150">Not A Black Box</span></span>

<span data-ttu-id="785cc-151">La mayoría de las distribuciones de GUIX incluyen el código fuente C completo.</span><span class="sxs-lookup"><span data-stu-id="785cc-151">Most distributions of GUIX include the complete C source code.</span></span> <span data-ttu-id="785cc-152">Esto elimina los problemas de "caja negra" que se producen con muchas implementaciones de GUI comerciales.</span><span class="sxs-lookup"><span data-stu-id="785cc-152">This eliminates the “black-box” problems that occur with many commercial GUI implementations.</span></span> <span data-ttu-id="785cc-153">Al usar GUIX, los desarrolladores de aplicaciones pueden ver exactamente lo que está haciendo la GUI; no hay misterio.</span><span class="sxs-lookup"><span data-stu-id="785cc-153">By using GUIX, applications developers can see exactly what the GUI is doing—there are no mysteries!</span></span>

<span data-ttu-id="785cc-154">Gracias a disponer del código fuente, también permite modificaciones específicas de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="785cc-154">Having the source code also allows for application specific modifications.</span></span> <span data-ttu-id="785cc-155">Aunque no se recomienda, es ciertamente útil tener la capacidad de modificar la GUI si es necesario.</span><span class="sxs-lookup"><span data-stu-id="785cc-155">Although not recommended, it is certainly beneficial to have the ability to modify the GUI if it is required.</span></span> <span data-ttu-id="785cc-156">Estas características son especialmente reconfortantes para los desarrolladores acostumbrados a trabajar con productos de dominio público o interno.</span><span class="sxs-lookup"><span data-stu-id="785cc-156">These features are especially comforting to developers accustomed to working with in-house or public domain products.</span></span> <span data-ttu-id="785cc-157">Esperan tener el código fuente y la capacidad de modificarlo.</span><span class="sxs-lookup"><span data-stu-id="785cc-157">They expect to have source code and the ability to modify it.</span></span> <span data-ttu-id="785cc-158">GUIX es el software de GUI definitivo para dichos desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="785cc-158">GUIX is the ultimate GUI software for such developers.</span></span>

## <a name="embedded-gui-applications"></a><span data-ttu-id="785cc-159">Aplicaciones insertadas de GUI</span><span class="sxs-lookup"><span data-stu-id="785cc-159">Embedded GUI Applications</span></span>

<span data-ttu-id="785cc-160">Las aplicaciones insertadas de GUI son aplicaciones que requieren una interfaz de usuario y que se ejecutan en microprocesadores ocultos dentro de productos, como teléfonos móviles, equipos de comunicación, motores de automóviles, impresoras láser, dispositivos médicos, etc.</span><span class="sxs-lookup"><span data-stu-id="785cc-160">Embedded GUI applications are applications that have a user interface requirement and execute on microprocessors hidden inside products such as cellular phones, communication equipment, automotive engines, laser printers, medical devices, and so forth.</span></span> <span data-ttu-id="785cc-161">Estas aplicaciones casi siempre presentan algunas restricciones de memoria y rendimiento.</span><span class="sxs-lookup"><span data-stu-id="785cc-161">Such applications almost always have some memory and performance constraints.</span></span> <span data-ttu-id="785cc-162">Otra diferencia de la GUI insertada es que el software y el hardware tienen un propósito dedicado.</span><span class="sxs-lookup"><span data-stu-id="785cc-162">Another distinction of embedded GUI is that their software and hardware have a dedicated purpose.</span></span>

### <a name="real-time-gui-software"></a><span data-ttu-id="785cc-163">Software de GUI en tiempo real</span><span class="sxs-lookup"><span data-stu-id="785cc-163">Real-time GUI Software</span></span>

<span data-ttu-id="785cc-164">Básicamente, el software de GUI que debe realizar su procesamiento dentro de un período de tiempo exacto se denomina software de *GUI en tiempo real* y, cuando se imponen restricciones de tiempo en las aplicaciones de GUI, se clasifican como aplicaciones en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="785cc-164">Basically, GUI software that must perform its processing within an exact period of time is called *real-time GUI* software, and when time constraints are imposed on GUI applications, they are classified as realtime applications.</span></span> <span data-ttu-id="785cc-165">Las aplicaciones insertadas de GUI casi siempre son en tiempo real debido a su interacción inherente con el mundo externo.</span><span class="sxs-lookup"><span data-stu-id="785cc-165">Embedded GUI applications are almost always real-time because of their inherent interaction with the external world.</span></span>

## <a name="guix-benefits"></a><span data-ttu-id="785cc-166">Ventajas de GUIX</span><span class="sxs-lookup"><span data-stu-id="785cc-166">GUIX Benefits</span></span>

<span data-ttu-id="785cc-167">Las principales ventajas de usar GUIX para las aplicaciones insertadas son el alto rendimiento, las características enriquecidas y muy pocos requisitos de memoria.</span><span class="sxs-lookup"><span data-stu-id="785cc-167">The primary benefits of using GUIX for embedded applications are high-performance, feature rich, and very small memory requirements.</span></span> <span data-ttu-id="785cc-168">GUIX también está totalmente integrada con el sistema operativo en tiempo real de alto rendimiento y multitarea Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="785cc-168">GUIX is also completely integrated with the high-performance, multitasking Azure RTOS ThreadX real-time operating system.</span></span>

### <a name="improved-responsiveness"></a><span data-ttu-id="785cc-169">Mayor capacidad de respuesta</span><span class="sxs-lookup"><span data-stu-id="785cc-169">Improved Responsiveness</span></span>

<span data-ttu-id="785cc-170">El producto GUIX de alto rendimiento permite a las aplicaciones responder más rápido que nunca.</span><span class="sxs-lookup"><span data-stu-id="785cc-170">The high-performance GUIX product enables applications to respond faster than ever before.</span></span> <span data-ttu-id="785cc-171">Esto es especialmente importante para las aplicaciones insertadas con un volumen significativo de información visual o con requisitos estrictos de tiempo para mostrar dicha información.</span><span class="sxs-lookup"><span data-stu-id="785cc-171">This is especially important for embedded applications that either have a significant volume of visual information or strict timing requirements on displaying such information.</span></span>

### <a name="software-maintenance"></a><span data-ttu-id="785cc-172">Mantenimiento de software</span><span class="sxs-lookup"><span data-stu-id="785cc-172">Software Maintenance</span></span>

<span data-ttu-id="785cc-173">El uso de GUIX permite a los desarrolladores crear con facilidad particiones de los aspectos de la GUI de su aplicación insertada.</span><span class="sxs-lookup"><span data-stu-id="785cc-173">Using GUIX allows developers to easily partition the GUI aspects of their embedded application.</span></span> <span data-ttu-id="785cc-174">Esta creación de particiones hace que todo el proceso de desarrollo sea fácil y que mejore significativamente el mantenimiento futuro del software.</span><span class="sxs-lookup"><span data-stu-id="785cc-174">This partitioning makes the entire development process easy and significantly enhances future software maintenance.</span></span>

### <a name="increased-throughput"></a><span data-ttu-id="785cc-175">Aumento del rendimiento</span><span class="sxs-lookup"><span data-stu-id="785cc-175">Increased Throughput</span></span>

<span data-ttu-id="785cc-176">GUIX proporciona la GUI de mayor rendimiento disponible, que se transfiere directamente a la aplicación insertada.</span><span class="sxs-lookup"><span data-stu-id="785cc-176">GUIX provides the highest-performance GUI available, which directly transfers to the embedded application.</span></span> <span data-ttu-id="785cc-177">Las aplicaciones de GUIX pueden procesar la información de la interfaz de usuario más rápido que las aplicaciones que no son de GUIX.</span><span class="sxs-lookup"><span data-stu-id="785cc-177">GUIX applications are able to process user interface information faster than non-GUIX applications!</span></span>

### <a name="processor-isolation"></a><span data-ttu-id="785cc-178">Aislamiento del procesador</span><span class="sxs-lookup"><span data-stu-id="785cc-178">Processor Isolation</span></span>

<span data-ttu-id="785cc-179">GUIX proporciona una interfaz sólida e independiente del procesador entre la aplicación y el procesador subyacente y el hardware de visualización.</span><span class="sxs-lookup"><span data-stu-id="785cc-179">GUIX provides a robust, processor-independent interface between the application and the underlying processor and display hardware.</span></span> <span data-ttu-id="785cc-180">Esto permite a los desarrolladores concentrarse en los aspectos de alto nivel de la interfaz de usuario en lugar de dedicar tiempo adicional a solucionar problemas del hardware de visualización.</span><span class="sxs-lookup"><span data-stu-id="785cc-180">This allows developers to concentrate on the high-level aspects of the user interface rather than spending extra time dealing with display hardware issues.</span></span>

### <a name="ease-of-use"></a><span data-ttu-id="785cc-181">Facilidad de uso</span><span class="sxs-lookup"><span data-stu-id="785cc-181">Ease of Use</span></span>

<span data-ttu-id="785cc-182">GUIX se ha diseñado pensando en el desarrollador de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="785cc-182">GUIX is designed with the application developer in mind.</span></span> <span data-ttu-id="785cc-183">La arquitectura de GUIX y la interfaz de llamada de servicio son fáciles de entender.</span><span class="sxs-lookup"><span data-stu-id="785cc-183">The GUIX architecture and service call interface are easy to understand.</span></span> <span data-ttu-id="785cc-184">Como resultado, los desarrolladores de GUIX pueden usar rápidamente sus características avanzadas.</span><span class="sxs-lookup"><span data-stu-id="785cc-184">As a result, GUIX developers can quickly use its advanced features.</span></span>

### <a name="improve-time-to-market"></a><span data-ttu-id="785cc-185">Mejor tiempo de comercialización</span><span class="sxs-lookup"><span data-stu-id="785cc-185">Improve Time to Market</span></span>

<span data-ttu-id="785cc-186">Las eficaces características de GUIX agilizan el proceso de desarrollo de software.</span><span class="sxs-lookup"><span data-stu-id="785cc-186">The powerful features of GUIX accelerate the software development process.</span></span> <span data-ttu-id="785cc-187">GUIX abstrae la mayoría los problemas del procesador y hardware de visualización, con lo que se eliminan estas preocupaciones de la mayoría de las implementaciones de interfaz de usuario de aplicación.</span><span class="sxs-lookup"><span data-stu-id="785cc-187">GUIX abstracts most processor and display hardware issues, thereby removing these concerns from a majority of application user interface implementation.</span></span> <span data-ttu-id="785cc-188">Esta característica, combinada con el conjunto de características avanzadas y de facilidad de uso, da lugar a un tiempo de comercialización más rápido.</span><span class="sxs-lookup"><span data-stu-id="785cc-188">This feature, coupled with the ease-of-use and advanced feature set, results in a faster time to market!</span></span>

### <a name="protecting-the-software-investment"></a><span data-ttu-id="785cc-189">Protección de la inversión en software</span><span class="sxs-lookup"><span data-stu-id="785cc-189">Protecting the Software Investment</span></span>

<span data-ttu-id="785cc-190">GUIX se ha escrito exclusivamente en ANSI C y está totalmente integrada con el sistema operativo en tiempo real Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="785cc-190">GUIX is written exclusively in ANSI C and is fully integrated with the Azure RTOS ThreadX real-time operating system.</span></span> <span data-ttu-id="785cc-191">Esto significa que las aplicaciones de GUIX se pueden portar al instante a todos los procesadores compatibles con ThreadX.</span><span class="sxs-lookup"><span data-stu-id="785cc-191">This means GUIX applications are instantly portable to all ThreadX supported processors.</span></span> <span data-ttu-id="785cc-192">Mejor aún, una arquitectura de procesador completamente nueva puede ser compatible con ThreadX en cuestión de semanas.</span><span class="sxs-lookup"><span data-stu-id="785cc-192">Better yet, a completely new processor architecture can be supported with ThreadX in a matter of weeks.</span></span> <span data-ttu-id="785cc-193">Como resultado, el uso de GUIX garantiza la ruta de migración de la aplicación y protege la inversión de desarrollo original.</span><span class="sxs-lookup"><span data-stu-id="785cc-193">As a result, using GUIX ensures the application’s migration path and protects the original development investment.</span></span>
