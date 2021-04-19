---
title: Descripción de Azure RTOS GUIX y Azure RTOS GUIX Studio
description: Azure RTOS GUIX es un paquete de calidad profesional creado para satisfacer las necesidades de los desarrolladores de sistemas insertados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0d0ff37784673f851ab918e20b255d19ddf98b0f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815449"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="9f7c3-103">Información general de Azure RTOS GUIX y Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="9f7c3-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="9f7c3-104">La GUI insertada de Azure GUIX es la solución de GUI avanzada de nivel industrial de Microsoft diseñada específicamente para aplicaciones de IoT, en tiempo real e integradas profundamente.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="9f7c3-105">Microsoft también proporciona una herramienta de diseño de escritorio WYSIWYG completa denominada Azure RTOS GUIX Studio, que permite a los desarrolladores diseñar su GUI en el escritorio y generar código de interfaz gráfica de usuario de Azure RTOS GUIX insertado que se puede exportar al destino.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="9f7c3-106">Azure RTOS GUIX está totalmente integrado con los RTOS de Azure RTO ThreadX y está disponible para muchos de los mismos procesadores admitidos por Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="9f7c3-107">Todo esto, combinado con un tamaño extremadamente pequeño, una ejecución rápida y una facilidad de uso superior, hacen de Azure RTOS GUIX la opción ideal para las aplicaciones de IoT integradas más exigentes que requieren una interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="9f7c3-108">Azure RTOS GUIX API</span><span class="sxs-lookup"><span data-stu-id="9f7c3-108">Azure RTOS GUIX API</span></span>

### <a name="intuitive-and-consistent-api"></a><span data-ttu-id="9f7c3-109">API intuitivas y coherentes</span><span class="sxs-lookup"><span data-stu-id="9f7c3-109">Intuitive and consistent API</span></span>

* <span data-ttu-id="9f7c3-110">Convención de nomenclatura sustantivo-verbo</span><span class="sxs-lookup"><span data-stu-id="9f7c3-110">Noun-verb naming convention</span></span>

* <span data-ttu-id="9f7c3-111">Todas las API tienen *gx_* líderes para identificar fácilmente como GUIX de Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="9f7c3-111">All APIs have leading *gx_* to easily identify as Azure RTOS GUIX</span></span>

* <span data-ttu-id="9f7c3-112">Modelo de programación basado en eventos (API)</span><span class="sxs-lookup"><span data-stu-id="9f7c3-112">Event-driven programming model (API)</span></span>

* <span data-ttu-id="9f7c3-113">Compatibilidad total con el dibujo de lienzo directo cuando sea necesario</span><span class="sxs-lookup"><span data-stu-id="9f7c3-113">Full support for direct canvas drawing when needed</span></span>

* <span data-ttu-id="9f7c3-114">Fácil de interactuar con el código generado por Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="9f7c3-114">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>

* <span data-ttu-id="9f7c3-115">API para líneas, rectángulos, polígonos, etc.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-115">APIs for line, rectangle, polygon, etc.</span></span>

* <span data-ttu-id="9f7c3-116">API para círculos, arco, circular, cuerda, elipse, etc.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-116">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>

* <span data-ttu-id="9f7c3-117">API para dibujar y colocar texto</span><span class="sxs-lookup"><span data-stu-id="9f7c3-117">APIs for text drawing and positioning</span></span>

* <span data-ttu-id="9f7c3-118">Suavizado de contorno, relleno de textura y rellenos sólidos</span><span class="sxs-lookup"><span data-stu-id="9f7c3-118">Anti-aliasing, texture fills, and solid fills</span></span>

* <span data-ttu-id="9f7c3-119">API para crear y modificar pantallas y widgets</span><span class="sxs-lookup"><span data-stu-id="9f7c3-119">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="9f7c3-120">Archivos generados por Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="9f7c3-120">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="9f7c3-121">Archivos de código fuente ANSI C generados automáticamente</span><span class="sxs-lookup"><span data-stu-id="9f7c3-121">Automatically generated ANSI C source files</span></span>

* <span data-ttu-id="9f7c3-122">Aísla el software de la aplicación de los detalles del diseño</span><span class="sxs-lookup"><span data-stu-id="9f7c3-122">Insulates application software from layout details</span></span>

* <span data-ttu-id="9f7c3-123">Incluye fuentes e imágenes que requiere el diseño de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="9f7c3-123">Includes fonts and images required by UI design</span></span>

* <span data-ttu-id="9f7c3-124">Archivos generados compilados con código de aplicación</span><span class="sxs-lookup"><span data-stu-id="9f7c3-124">Generated files compiled with application code</span></span>

* <span data-ttu-id="9f7c3-125">El diseño de pantalla se puede actualizar sin afectar a la lógica de la aplicación</span><span class="sxs-lookup"><span data-stu-id="9f7c3-125">Screen layout can be updated without affecting application logic</span></span>

* <span data-ttu-id="9f7c3-126">Los identificadores de recursos crean independencia de lenguaje y tema</span><span class="sxs-lookup"><span data-stu-id="9f7c3-126">Resource IDs create language and theme independence</span></span>

* <span data-ttu-id="9f7c3-127">Funciones de dibujo y procesamiento de eventos personalizadas proporcionadas por el usuario</span><span class="sxs-lookup"><span data-stu-id="9f7c3-127">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="9f7c3-128">Biblioteca de widgets</span><span class="sxs-lookup"><span data-stu-id="9f7c3-128">Widget library</span></span>

* <span data-ttu-id="9f7c3-129">Conjunto predefinido pero personalizable de elementos comunes de la interfaz</span><span class="sxs-lookup"><span data-stu-id="9f7c3-129">Pre-defined but customizable set of common interface elements</span></span>

* <span data-ttu-id="9f7c3-130">Extremadamente pequeño, compacto y eficaz</span><span class="sxs-lookup"><span data-stu-id="9f7c3-130">Extremely small, compact, and efficient</span></span>

* <span data-ttu-id="9f7c3-131">La biblioteca incluye el botón, el medidor, la lista, la ventana, el desplazamiento, el control deslizante, la barra de progreso, el símbolo del sistema y muchos más</span><span class="sxs-lookup"><span data-stu-id="9f7c3-131">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>

* <span data-ttu-id="9f7c3-132">Dibujo y apariencia totalmente personalizables</span><span class="sxs-lookup"><span data-stu-id="9f7c3-132">Fully customizable drawing and appearance</span></span>

* <span data-ttu-id="9f7c3-133">Control de eventos y operaciones totalmente personalizables</span><span class="sxs-lookup"><span data-stu-id="9f7c3-133">Fully customizable operation and event handling</span></span>

* <span data-ttu-id="9f7c3-134">Solo los widgets usados están vinculados con el software de la aplicación</span><span class="sxs-lookup"><span data-stu-id="9f7c3-134">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="9f7c3-135">Matemáticas y utilidades</span><span class="sxs-lookup"><span data-stu-id="9f7c3-135">Math and utilities</span></span>

* <span data-ttu-id="9f7c3-136">Funciones para sin, cos, arcsin, arccos, tangente, raíz cuadrada</span><span class="sxs-lookup"><span data-stu-id="9f7c3-136">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>

* <span data-ttu-id="9f7c3-137">Funciones para manipular regiones de pantalla</span><span class="sxs-lookup"><span data-stu-id="9f7c3-137">Functions for manipulating screen regions</span></span>

* <span data-ttu-id="9f7c3-138">Configuración e inicio del sistema</span><span class="sxs-lookup"><span data-stu-id="9f7c3-138">System configuration and startup</span></span>

* <span data-ttu-id="9f7c3-139">Definición del grupo de memoria (opcional)</span><span class="sxs-lookup"><span data-stu-id="9f7c3-139">Memory pool definition (optional)</span></span>

* <span data-ttu-id="9f7c3-140">Administración de temporizadores</span><span class="sxs-lookup"><span data-stu-id="9f7c3-140">Timer Management</span></span>

* <span data-ttu-id="9f7c3-141">Administrador de animaciones</span><span class="sxs-lookup"><span data-stu-id="9f7c3-141">Animation Management</span></span>

* <span data-ttu-id="9f7c3-142">Mantenimiento de la lista de integridad</span><span class="sxs-lookup"><span data-stu-id="9f7c3-142">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="9f7c3-143">Procesamiento de imágenes</span><span class="sxs-lookup"><span data-stu-id="9f7c3-143">Image processing</span></span>

* <span data-ttu-id="9f7c3-144">Funciones para descodificar en tiempo de ejecución imágenes jpeg y png</span><span class="sxs-lookup"><span data-stu-id="9f7c3-144">Functions for runtime decode of jpeg and png images</span></span>

* <span data-ttu-id="9f7c3-145">Aplicar la conversión de espacio de colores y interpolación</span><span class="sxs-lookup"><span data-stu-id="9f7c3-145">Apply dithering and color space conversion</span></span>

* <span data-ttu-id="9f7c3-146">Rotación de imagen</span><span class="sxs-lookup"><span data-stu-id="9f7c3-146">Image rotation</span></span>

* <span data-ttu-id="9f7c3-147">Escalado de imagen</span><span class="sxs-lookup"><span data-stu-id="9f7c3-147">Image scaling</span></span>

* <span data-ttu-id="9f7c3-148">Combinación de imagen</span><span class="sxs-lookup"><span data-stu-id="9f7c3-148">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="9f7c3-149">Procesamiento de eventos</span><span class="sxs-lookup"><span data-stu-id="9f7c3-149">Event processing</span></span>

* <span data-ttu-id="9f7c3-150">Suspende automáticamente el subproceso de Azure RTOS GUIX cuando está inactivo</span><span class="sxs-lookup"><span data-stu-id="9f7c3-150">Automatically suspends Azure RTOS GUIX thread when idle</span></span>

* <span data-ttu-id="9f7c3-151">Modelo de programación orientado a eventos conocido en el diseño de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="9f7c3-151">Event-driven programming model popular in UI design</span></span>

* <span data-ttu-id="9f7c3-152">Aísla los controladores de entrada del subproceso de dibujo de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="9f7c3-152">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>

* <span data-ttu-id="9f7c3-153">Funciones para enviar y recibir eventos</span><span class="sxs-lookup"><span data-stu-id="9f7c3-153">Functions for sending and receiving events</span></span>

* <span data-ttu-id="9f7c3-154">Tipos de eventos predefinidos para todos los tipos de widgets de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="9f7c3-154">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>

* <span data-ttu-id="9f7c3-155">Se admiten eventos personalizados definidos por el usuario</span><span class="sxs-lookup"><span data-stu-id="9f7c3-155">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="9f7c3-156">Procesamiento de lienzo</span><span class="sxs-lookup"><span data-stu-id="9f7c3-156">Canvas processing</span></span>

* <span data-ttu-id="9f7c3-157">Recorte y mantenimiento del orden Z</span><span class="sxs-lookup"><span data-stu-id="9f7c3-157">Clipping and Z-Order maintenance</span></span>

* <span data-ttu-id="9f7c3-158">Aísla la biblioteca de widgets de detalles de hardware</span><span class="sxs-lookup"><span data-stu-id="9f7c3-158">Insulates widget library from hardware details</span></span>

* <span data-ttu-id="9f7c3-159">Aísla la aplicación de los detalles de hardware</span><span class="sxs-lookup"><span data-stu-id="9f7c3-159">Insulates application from hardware details</span></span>

* <span data-ttu-id="9f7c3-160">Actualización automática en segundo plano de áreas desfasadas</span><span class="sxs-lookup"><span data-stu-id="9f7c3-160">Automatic background refresh of dirty areas</span></span>

* <span data-ttu-id="9f7c3-161">Se admiten varios lienzos con capas y combinación</span><span class="sxs-lookup"><span data-stu-id="9f7c3-161">Multiple canvases with layering and blending supported</span></span>

* <span data-ttu-id="9f7c3-162">Se puede invocar directamente mediante el software de la aplicación</span><span class="sxs-lookup"><span data-stu-id="9f7c3-162">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="9f7c3-163">Controladores de dispositivo de entrada</span><span class="sxs-lookup"><span data-stu-id="9f7c3-163">Input device driver(s)</span></span>

* <span data-ttu-id="9f7c3-164">Compatibilidad específica con el hardware, Azure RTOS GUIX y la aplicación aislada de los detalles de hardware</span><span class="sxs-lookup"><span data-stu-id="9f7c3-164">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>

* <span data-ttu-id="9f7c3-165">Touch resistente, extremo touch y teclado numérico compatible</span><span class="sxs-lookup"><span data-stu-id="9f7c3-165">Resistive Touch, Cap Touch, and keypad supported</span></span>

* <span data-ttu-id="9f7c3-166">Eventos de entrada pasados a la cola de eventos de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="9f7c3-166">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="9f7c3-167">Mostrar controladores</span><span class="sxs-lookup"><span data-stu-id="9f7c3-167">Display drivers</span></span>

* <span data-ttu-id="9f7c3-168">Compatibilidad específica del hardware</span><span class="sxs-lookup"><span data-stu-id="9f7c3-168">Hardware-specific support</span></span>

* <span data-ttu-id="9f7c3-169">Controladores genéricos proporcionados para todos los formatos y la profundidad de color</span><span class="sxs-lookup"><span data-stu-id="9f7c3-169">Generic drivers provided for all color depth and formats</span></span>

* <span data-ttu-id="9f7c3-170">Personalización para el uso de aceleradores de gráficos disponibles</span><span class="sxs-lookup"><span data-stu-id="9f7c3-170">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="9f7c3-171">Hardware de destino</span><span class="sxs-lookup"><span data-stu-id="9f7c3-171">Target hardware</span></span>

* <span data-ttu-id="9f7c3-172">Casi cualquier hardware con capacidad de salida gráfica es compatible con GUIX</span><span class="sxs-lookup"><span data-stu-id="9f7c3-172">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>

* <span data-ttu-id="9f7c3-173">Se admiten varias pantallas físicas</span><span class="sxs-lookup"><span data-stu-id="9f7c3-173">Multiple physical displays supported</span></span>

* <span data-ttu-id="9f7c3-174">Requisitos de RAM y Flash mínimos</span><span class="sxs-lookup"><span data-stu-id="9f7c3-174">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="9f7c3-175">Crear interfaces de usuario elegantes</span><span class="sxs-lookup"><span data-stu-id="9f7c3-175">Create Elegant User Interfaces</span></span>

<span data-ttu-id="9f7c3-176">Azure RTOS GUIX y Azure RTOS GUIX Studio proporcionan todas las características necesarias para crear interfaces de usuario de forma exclusiva.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-176">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="9f7c3-177">El paquete estándar de Azure RTOS GUIX incluye varias interfaces de usuario de ejemplo, entre las que se incluyen una referencia de dispositivo médico, una referencia de smart watch, una referencia de automatización doméstica, una referencia de control industrial, una referencia de automóviles y varios ejemplos de objetos sprite y animación.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-177">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="9f7c3-178">Haga clic en los ejemplos de referencia que se muestran a continuación.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-178">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="9f7c3-179">Automatización de inicio</span><span class="sxs-lookup"><span data-stu-id="9f7c3-179">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="9f7c3-180">Medicina</span><span class="sxs-lookup"><span data-stu-id="9f7c3-180">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="9f7c3-181">Consumidor</span><span class="sxs-lookup"><span data-stu-id="9f7c3-181">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="9f7c3-182">Electrodomésticos</span><span class="sxs-lookup"><span data-stu-id="9f7c3-182">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="9f7c3-183">Automoción</span><span class="sxs-lookup"><span data-stu-id="9f7c3-183">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="9f7c3-184">Industrial</span><span class="sxs-lookup"><span data-stu-id="9f7c3-184">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="9f7c3-185">Cada referencia de Azure RTOS GUIX tiene un proyecto de Azure RTOS GUIX Studio correspondiente que define todos los elementos gráficos del diseño de referencia.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-185">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="9f7c3-186">Es fácil cambiar el diseño de una referencia.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-186">Changing a reference design is easy.</span></span> <span data-ttu-id="9f7c3-187">Simplemente abra el proyecto Azure RTOS GUIX correspondiente, realice los cambios deseados, guarde el proyecto y, a continuación, seleccione *Proyecto*.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-187">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="9f7c3-188">Genere todos los archivos de salida para generar el código C para Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-188">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="9f7c3-189">A continuación, simplemente vuelva a compilar la aplicación de destino y ejecútela para observar el diseño de referencia modificado.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-189">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="small-footprint"></a><span data-ttu-id="9f7c3-190">Superficie pequeña</span><span class="sxs-lookup"><span data-stu-id="9f7c3-190">Small-footprint</span></span>

<span data-ttu-id="9f7c3-191">Azure RTOS GUIX tiene una superficie mínima de 13,2 KB de FLASH y 4 KB de RAM para soporte básico, sin incluir la memoria necesaria para un lienzo.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-191">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="9f7c3-192">En el caso de una pantalla con la tecnología interna GRAM y de actualización automática, no se requiere memoria de lienzo.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-192">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="9f7c3-193">Sin embargo, para mejorar el rendimiento del dibujo o para una configuración de pantalla que no use GRAM local para esta, la aplicación define un área de memoria de lienzo.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-193">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="9f7c3-194">Los requisitos de memoria de lienzo son una función del tamaño de este y la profundidad de color, y se definen mediante la fórmula:</span><span class="sxs-lookup"><span data-stu-id="9f7c3-194">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="9f7c3-195"><i>Lienzo RAM (bytes) = (x \* y \* (bpp/8))</i></span><span class="sxs-lookup"><span data-stu-id="9f7c3-195"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="9f7c3-196">Donde "x" y "y" son las dimensiones del lienzo (Mostrar).</span><span class="sxs-lookup"><span data-stu-id="9f7c3-196">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="9f7c3-197">La mayoría de las aplicaciones también usan recursos gráficos, que no se incluyen en los requisitos básicos de almacenamiento de la biblioteca Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-197">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="9f7c3-198">Estos recursos incluyen fuentes, iconos gráficos (PixelMap) y cadenas estáticas.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-198">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="9f7c3-199">Estos datos se pueden almacenar en la sección de memoria const (es decir, FLASH).</span><span class="sxs-lookup"><span data-stu-id="9f7c3-199">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="9f7c3-200">El tamaño de este área de memoria depende de varios factores, como el número y el tamaño de las fuentes únicas utilizadas, el número y el tamaño de los iconos gráficos usados, el formato de color de salida y si cada recurso está usando datos comprimidos, ya que Azure RTOS GUIX admite la compresión RLE de los datos de fuente y de PixelMap.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-200">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="9f7c3-201">Los requisitos de almacenamiento de cada recurso se muestran dentro de la aplicación Azure RTOS GUIX Studio, lo que permite al usuario realizar un seguimiento y supervisar la cantidad de memoria Flash que consumirán los recursos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-201">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="9f7c3-202">Al igual que Azure RTOS ThreadX, el tamaño de Azure RTOS GUIX se escala automáticamente en función de los servicios que la aplicación usa realmente.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-202">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="9f7c3-203">Esto elimina prácticamente la necesidad de configuraciones y parámetros de compilación complicados, lo que facilita el trabajo del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-203">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

### <a name="fast-execution"></a><span data-ttu-id="9f7c3-204">Ejecución rápida</span><span class="sxs-lookup"><span data-stu-id="9f7c3-204">Fast execution</span></span>

<span data-ttu-id="9f7c3-205">Azure RTOS GUIX está escrito exclusivamente en C y está diseñado para la velocidad.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-205">Azure RTOS GUIX is written exclusively in C and is designed for speed.</span></span> <span data-ttu-id="9f7c3-206">Azure RTOS GUIX tiene una capa mínima de llamadas de función interna.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-206">Azure RTOS GUIX has minimal internal function call layering.</span></span>

<span data-ttu-id="9f7c3-207">Además, Azure RTOS GUIX proporciona un recorte optimizado, dibujo y control de eventos.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-207">In addition, Azure RTOS GUIX provides optimized clipping, drawing, and event handling.</span></span> <span data-ttu-id="9f7c3-208">Todo esto y una filosofía general de diseño orientada al rendimiento ayudan a Azure RTOS GUIX a lograr el rendimiento más rápido posible.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-208">All of this and a general performance-oriented design philosophy help Azure RTOS GUIX achieve the fastest possible performance.</span></span>

### <a name="pre-certified--by-tuv-to-many-safety-standards"></a><span data-ttu-id="9f7c3-209">Certificado previamente por TUV para varios estándares de seguridad</span><span class="sxs-lookup"><span data-stu-id="9f7c3-209">Pre-certified  by TUV to many safety standards</span></span>

<span data-ttu-id="9f7c3-210">Azure RTOS GUIX ha sido certificado por los SG-TUV Saar para su uso en sistemas críticos para la seguridad, según CEI-61508 SIL 4, CEI-62304 SW Clase de seguridad C, ISO 26262 ASIL D y EN 50128.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-210">Azure RTOS GUIX has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="9f7c3-211">La certificación confirma que Azure RTOS GUIX se puede usar en el desarrollo de software relacionado con la seguridad para los niveles de integridad de seguridad más altos de CEI-61508, CEI-62304, ISO 26262 y EN 50128 para la "seguridad funcional de sistemas relacionados con la seguridad electrónica de electricidad, electrónica y programable".</span><span class="sxs-lookup"><span data-stu-id="9f7c3-211">The certification confirms that Azure RTOS GUIX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="9f7c3-212">SG-TUV Saar, que es una sociedad conjunta entre las empresas alemanas SGS-Group y TUV Saarland, se ha convertido en la empresa líder independiente acreditada para probar, auditar, comprobar y certificar software insertado para sistemas relacionados con la seguridad en todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-212">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="9f7c3-213">El estándar de seguridad industrial CEI 61508, y todos los estándares que se derivan de él, incluidos CEI-62304, ISO 26262 y EN 50128, se usan para garantizar la seguridad funcional de los dispositivos médicos eléctricos, electrónicos y programables relacionados con la seguridad electrónica, los sistemas de control de procesos, la maquinaria industrial, los automóviles y los sistemas de control de ferrocarriles.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-213">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

<img alt="SGS-TUV Saar" class="img-responsive" src="https://rtos.com/wp-content/uploads/2017/10/partener-logo-sgs-tuv-saar-2.png"/>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="9f7c3-214">Simple y fácil de usar</span><span class="sxs-lookup"><span data-stu-id="9f7c3-214">Simple, easy-to-use</span></span>

<span data-ttu-id="9f7c3-215">Azure RTOS GUIX es muy simple de usar y Azure RTOS GUIX Studio lo hace aún más fácil al permitir a los desarrolladores diseñar visualmente en el escritorio y generar código C que se ejecuta en el objetivo real.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-215">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="9f7c3-216">Después, las aplicaciones pueden agregar sus propias funciones de control de eventos y dibujo personalizadas para completar su GUI.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-216">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="9f7c3-217">El uso de la API de Azure RTOS GUIX es sencillo.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-217">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="9f7c3-218">La API de Azure RTOS GUIX es intuitiva y altamente funcional.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-218">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="9f7c3-219">Los nombres de API se componen de palabras reales y no de la "sopa de letras" ni de los nombres muy abreviados que son tan comunes en otros productos del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-219">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="9f7c3-220">Todas las API de Azure RTOS GUIX tienen una *gx_* inicial y siguen una convención de nomenclatura de sustantivos.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-220">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="9f7c3-221">Además, existe una coherencia funcional en la API.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-221">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="9f7c3-222">Por ejemplo, todas las API que inicializan un bloque de control widget se denominan &lt;widget_type&gt;_create y los parámetros de la función crear para cada tipo de widget siempre se definen en el mismo orden.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-222">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="9f7c3-223">Conjunto completo de widgets integrados</span><span class="sxs-lookup"><span data-stu-id="9f7c3-223">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="9f7c3-224">Azure RTOS GUIX ofrece un amplio conjunto de widgets integrados, entre los que se incluyen:</span><span class="sxs-lookup"><span data-stu-id="9f7c3-224">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>

* <span data-ttu-id="9f7c3-225">Menú Accordion</span><span class="sxs-lookup"><span data-stu-id="9f7c3-225">Accordion Menu</span></span>

* <span data-ttu-id="9f7c3-226">Botón</span><span class="sxs-lookup"><span data-stu-id="9f7c3-226">Button</span></span>

* <span data-ttu-id="9f7c3-227">Casilla de verificación</span><span class="sxs-lookup"><span data-stu-id="9f7c3-227">Checkbox</span></span>

* <span data-ttu-id="9f7c3-228">Medidor circular</span><span class="sxs-lookup"><span data-stu-id="9f7c3-228">Circular Gauge</span></span>

* <span data-ttu-id="9f7c3-229">Lista desplegable</span><span class="sxs-lookup"><span data-stu-id="9f7c3-229">Drop Down List</span></span>

* <span data-ttu-id="9f7c3-230">Lista horizontal</span><span class="sxs-lookup"><span data-stu-id="9f7c3-230">Horizontal List</span></span>

* <span data-ttu-id="9f7c3-231">Horizontal Scrollbar Window</span><span class="sxs-lookup"><span data-stu-id="9f7c3-231">Horizontal Scrollbar Window</span></span>

* <span data-ttu-id="9f7c3-232">Icono</span><span class="sxs-lookup"><span data-stu-id="9f7c3-232">Icon</span></span>

* <span data-ttu-id="9f7c3-233">Botón de icono</span><span class="sxs-lookup"><span data-stu-id="9f7c3-233">Icon Button</span></span>

* <span data-ttu-id="9f7c3-234">Gráfico de líneas</span><span class="sxs-lookup"><span data-stu-id="9f7c3-234">Line Chart</span></span>

* <span data-ttu-id="9f7c3-235">Menú</span><span class="sxs-lookup"><span data-stu-id="9f7c3-235">Menu</span></span>

* <span data-ttu-id="9f7c3-236">Botón de texto de varias líneas</span><span class="sxs-lookup"><span data-stu-id="9f7c3-236">Multi Line Text Button</span></span>

* <span data-ttu-id="9f7c3-237">Entrada de texto de varias líneas</span><span class="sxs-lookup"><span data-stu-id="9f7c3-237">Multi Line Text Input</span></span>

* <span data-ttu-id="9f7c3-238">Vista de texto de varias líneas</span><span class="sxs-lookup"><span data-stu-id="9f7c3-238">Multi Line Text View</span></span>

* <span data-ttu-id="9f7c3-239">Solicitud PixelMap numérica</span><span class="sxs-lookup"><span data-stu-id="9f7c3-239">Numeric Pixelmap Prompt</span></span>

* <span data-ttu-id="9f7c3-240">Solicitud numérica</span><span class="sxs-lookup"><span data-stu-id="9f7c3-240">Numeric Prompt</span></span>

* <span data-ttu-id="9f7c3-241">Rueda del mouse numérico</span><span class="sxs-lookup"><span data-stu-id="9f7c3-241">Numeric Scroll Wheel</span></span>

* <span data-ttu-id="9f7c3-242">Botón PixelMap</span><span class="sxs-lookup"><span data-stu-id="9f7c3-242">Pixelmap Button</span></span>

* <span data-ttu-id="9f7c3-243">Símbolo del sistema de PixelMap</span><span class="sxs-lookup"><span data-stu-id="9f7c3-243">Pixelmap Prompt</span></span>

* <span data-ttu-id="9f7c3-244">Control deslizante PixelMap</span><span class="sxs-lookup"><span data-stu-id="9f7c3-244">Pixelmap Slider</span></span>

* <span data-ttu-id="9f7c3-245">Sprite PixelMap</span><span class="sxs-lookup"><span data-stu-id="9f7c3-245">Pixelmap Sprite</span></span>

* <span data-ttu-id="9f7c3-246">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="9f7c3-246">Progress Bar</span></span>

* <span data-ttu-id="9f7c3-247">Prompt</span><span class="sxs-lookup"><span data-stu-id="9f7c3-247">Prompt</span></span>

* <span data-ttu-id="9f7c3-248">Barra de progreso radial</span><span class="sxs-lookup"><span data-stu-id="9f7c3-248">Radial Progress Bar</span></span>

* <span data-ttu-id="9f7c3-249">Radio Button</span><span class="sxs-lookup"><span data-stu-id="9f7c3-249">Radio Button</span></span>

* <span data-ttu-id="9f7c3-250">Rueda del mouse</span><span class="sxs-lookup"><span data-stu-id="9f7c3-250">Scroll Wheel</span></span>

* <span data-ttu-id="9f7c3-251">Entrada de texto de una sola línea</span><span class="sxs-lookup"><span data-stu-id="9f7c3-251">Single Line Text Input</span></span>

* <span data-ttu-id="9f7c3-252">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="9f7c3-252">Slider</span></span>

* <span data-ttu-id="9f7c3-253">Rueda del mouse de cadena</span><span class="sxs-lookup"><span data-stu-id="9f7c3-253">String Scroll Wheel</span></span>

* <span data-ttu-id="9f7c3-254">Botón de texto</span><span class="sxs-lookup"><span data-stu-id="9f7c3-254">Text Button</span></span>

* <span data-ttu-id="9f7c3-255">Vista de árbol</span><span class="sxs-lookup"><span data-stu-id="9f7c3-255">Tree View</span></span>

* <span data-ttu-id="9f7c3-256">Lista vertical</span><span class="sxs-lookup"><span data-stu-id="9f7c3-256">Vertical List</span></span>

* <span data-ttu-id="9f7c3-257">Barra de desplazamiento vertical</span><span class="sxs-lookup"><span data-stu-id="9f7c3-257">Vertical Scrollbar</span></span>

<span data-ttu-id="9f7c3-258">También es fácil para la aplicación crear sus propios widgets de cliente.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-258">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="9f7c3-259">Completar la API de dibujo de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="9f7c3-259">Complete low-level drawing API</span></span>

<span data-ttu-id="9f7c3-260">Azure RTOS GUIX proporciona una API de dibujo de lienzo sólida, lo que permite que la aplicación represente formas gráficas complejas.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-260">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="9f7c3-261">Todas las funciones admiten el suavizado de contorno en los objetivos de profundidad de color alta y todas las formas se pueden rellenar, incluidos los rellenos de patrón sólido y PixelMap.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-261">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="9f7c3-262">Todos los primitivos de dibujo admiten el pincel alfa cuando se ejecutan con 16 bpp y una profundidad de color superior.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-262">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="9f7c3-263">Las funciones de dibujo incluyen:</span><span class="sxs-lookup"><span data-stu-id="9f7c3-263">Drawing functions include:</span></span>

* <span data-ttu-id="9f7c3-264">Dibujo de arco</span><span class="sxs-lookup"><span data-stu-id="9f7c3-264">Arc Draw</span></span>

* <span data-ttu-id="9f7c3-265">Dibujo con círculo</span><span class="sxs-lookup"><span data-stu-id="9f7c3-265">Circle Draw</span></span>

* <span data-ttu-id="9f7c3-266">Dibujo de línea</span><span class="sxs-lookup"><span data-stu-id="9f7c3-266">Line Draw</span></span>

* <span data-ttu-id="9f7c3-267">Dibujo circular</span><span class="sxs-lookup"><span data-stu-id="9f7c3-267">Pie Draw</span></span>

* <span data-ttu-id="9f7c3-268">PixelMap Blend</span><span class="sxs-lookup"><span data-stu-id="9f7c3-268">Pixelmap Blend</span></span>

* <span data-ttu-id="9f7c3-269">Icono de PixelMap</span><span class="sxs-lookup"><span data-stu-id="9f7c3-269">Pixelmap Tile</span></span>

* <span data-ttu-id="9f7c3-270">Dibujo de polígono</span><span class="sxs-lookup"><span data-stu-id="9f7c3-270">Polygon Draw</span></span>

* <span data-ttu-id="9f7c3-271">Dibujo de texto</span><span class="sxs-lookup"><span data-stu-id="9f7c3-271">Text Draw</span></span>

* <span data-ttu-id="9f7c3-272">Dibujo de cuerda</span><span class="sxs-lookup"><span data-stu-id="9f7c3-272">Chord Draw</span></span>

* <span data-ttu-id="9f7c3-273">Dibujo de elipse</span><span class="sxs-lookup"><span data-stu-id="9f7c3-273">Ellipse Draw</span></span>

* <span data-ttu-id="9f7c3-274">Dibujo de píxeles</span><span class="sxs-lookup"><span data-stu-id="9f7c3-274">Pixel Draw</span></span>

* <span data-ttu-id="9f7c3-275">Dibujo de PixelMap</span><span class="sxs-lookup"><span data-stu-id="9f7c3-275">Pixelmap Draw</span></span>

* <span data-ttu-id="9f7c3-276">Girar PixelMap</span><span class="sxs-lookup"><span data-stu-id="9f7c3-276">Pixelmap Rotate</span></span>

* <span data-ttu-id="9f7c3-277">Dibujo de rectángulo</span><span class="sxs-lookup"><span data-stu-id="9f7c3-277">Rectangle Draw</span></span>

* <span data-ttu-id="9f7c3-278">Combinación de texto</span><span class="sxs-lookup"><span data-stu-id="9f7c3-278">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="9f7c3-279">Fuentes gratuitas predeterminadas y fáciles de agregar</span><span class="sxs-lookup"><span data-stu-id="9f7c3-279">Default free fonts and easy to add more</span></span>

<span data-ttu-id="9f7c3-280">Azure RTOS GUIX proporciona un conjunto gratuito de fuentes TrueType.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-280">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="9f7c3-281">Los desarrolladores pueden agregar fuentes TrueType adicionales según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-281">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="9f7c3-282">El formato de fuente Azure RTOS GUIX admite el suavizado de contorno 8 bpp, el suavizado de contorno de 4 bpp y las fuentes monocromáticas 1 bpp.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-282">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="9f7c3-283">En el caso de la mayoría de las aplicaciones con restricciones de recursos, Azure RTOS GUIX prerepresenta las fuentes TrueType en un formato de mapa de bits comprimido mediante nuestra herramienta de escritorio de GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-283">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="9f7c3-284">Implementación descodificador de JPG y PNG personalizado</span><span class="sxs-lookup"><span data-stu-id="9f7c3-284">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="9f7c3-285">Implementación del descodificador JPG y PNG personalizado, implementación del descodificador de archivos JPG y PNG.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-285">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="9f7c3-286">Esta implementación admite la conversión de espacio de colores, la interpolación y la creación en tiempo de ejecución de imágenes con formato PixelMap compatible con Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-286">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="9f7c3-287">Amplia compatibilidad con pantallas y pantallas táctiles</span><span class="sxs-lookup"><span data-stu-id="9f7c3-287">Extensive display and touchscreen support</span></span>

<span data-ttu-id="9f7c3-288">Azure RTOS GUIX proporciona controladores de pantalla genéricos para casi todos los formatos de color, incluido el monocromo de 1 bpp, la paleta de 8 bpp, el formato 3:3:2 de 8 bpp,</span><span class="sxs-lookup"><span data-stu-id="9f7c3-288">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="9f7c3-289">el formato 16 bpp 565 rgb, el formato 16 bpp 4:4:4:4, formato 32 bpp x:r:g:b y el formato 32 bpp a:r:g:b.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-289">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="9f7c3-290">Además, Azure RTOS GUIX se integra con muchos de los aceleradores de hardware y controladores LCD más populares (ST ChromeArt, Renesas Synergy, etc.).</span><span class="sxs-lookup"><span data-stu-id="9f7c3-290">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="9f7c3-291">Azure RTOS GUIX es totalmente compatible con la pantalla táctil (incluida la compatibilidad con gestos), el lápiz y los dispositivos de entrada de teclado virtual.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-291">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="9f7c3-292">Herramienta de escritorio WYSIWYG de Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="9f7c3-292">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="9f7c3-293">Azure RTOS GUIX Studio proporciona un entorno de diseño de pantalla WYSIWYG completo que permite al usuario arrastrar y colocar elementos gráficos usados para compilar las pantallas de la GUI.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-293">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="9f7c3-294">Azure RTOS GUIX Studio genera automáticamente un código de C compatible con la biblioteca de Azure RTOS GUIX, listo para compilarse y ejecutarse en el destino.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-294">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="9f7c3-295">Los desarrolladores pueden generar fuentes previamente representadas para su uso en una aplicación mediante la herramienta de generación de fuentes de Azure RTOS GUIX Studio integrada.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-295">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="9f7c3-296">Las fuentes se pueden generar en formatos monocromo o suavizados y se optimizan para ahorrar espacio en el destino.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-296">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="9f7c3-297">Las fuentes pueden incluir cualquier juego de caracteres, incluidos los caracteres Unicode para aplicaciones multilingües.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-297">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="9f7c3-298">Azure RTOS GUIX Studio facilita la importación de gráficos de archivos PNG o JPG con la conversión a los PixelMap de Azure RTOS GUIX comprimidos para su uso en el sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-298">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="9f7c3-299">Muchos de los tipos de widgets de Azure RTOS GUIX están diseñados para incorporar gráficos de usuario para una apariencia personalizada.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-299">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="9f7c3-300">Además, Azure RTOS GUIX Studio permite la personalización de los colores predeterminados y los estilos de dibujo usados por los widgets de Azure RTOS GUIX, lo que permite a los desarrolladores ajustar la apariencia de Azure RTOS GUIX muy fácilmente.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-300">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="9f7c3-301">La generación y el mantenimiento de cadenas de aplicación es otra instalación integrada de Azure RTOS GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-301">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="9f7c3-302">Esto permite a los desarrolladores diseñar una aplicación con un lenguaje para desarrollar y agregar de forma rápida y sencilla compatibilidad para idiomas adicionales después de lanzar el producto.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-302">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="9f7c3-303">Se puede ejecutar una aplicación completa de Azure RTOS GUIX en un equipo de escritorio en el entorno de Azure RTOS GUIX Studio, lo que permite una generación y demostración rápidas y sencillas de conceptos de GUI, pruebas de flujos de pantalla y observación de transiciones de pantalla y animaciones.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-303">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="9f7c3-304">Una vez completado, un diseño se puede exportar como estructuras de datos de C listas para el destino, listas para su compilación y vinculación con las bibliotecas de Azure RTOS GUIX y Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-304">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="9f7c3-305">Azure RTOS GUIX y Azure RTOS GUIX Studio admiten varios temas de recursos, lo que permite que una aplicación se pueda cambiar fácilmente de nivel en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-305">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="9f7c3-306">Las fuentes, los colores y el PixelMap se pueden cambiar en tiempo de ejecución con una API simple.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-306">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="9f7c3-307">Más información sobre GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="9f7c3-307">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="9f7c3-308">Completar la simulación de Win32</span><span class="sxs-lookup"><span data-stu-id="9f7c3-308">Complete Win32 simulation</span></span>

<span data-ttu-id="9f7c3-309">Azure RTOS GUIX se ejecuta en un equipo con Windows, usando exactamente la misma biblioteca de dibujo que se ejecuta en la placa de destino.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-309">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="9f7c3-310">Con Azure RTOS GUIX, puede compilar y ejecutar una aplicación GUI en el equipo y usar el mismo código de aplicación en el destino para la depuración, la creación de prototipos, la demostración y el funcionamiento del destino WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-310">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="9f7c3-311">Tecnología avanzada</span><span class="sxs-lookup"><span data-stu-id="9f7c3-311">Advanced technology</span></span>

* <span data-ttu-id="9f7c3-312">La tecnología avanzada de Azure RTOS GUIX incorpora:</span><span class="sxs-lookup"><span data-stu-id="9f7c3-312">Azure RTOS GUIX's advanced technology incorporates:</span></span>

* <span data-ttu-id="9f7c3-313">Combinación alfa</span><span class="sxs-lookup"><span data-stu-id="9f7c3-313">Alpha blending</span></span>

* <span data-ttu-id="9f7c3-314">Suavizado de contorno</span><span class="sxs-lookup"><span data-stu-id="9f7c3-314">Anti-Aliasing</span></span>

* <span data-ttu-id="9f7c3-315">Escalado automático</span><span class="sxs-lookup"><span data-stu-id="9f7c3-315">Automatic scaling</span></span>

* <span data-ttu-id="9f7c3-316">Compresión de mapa de bits</span><span class="sxs-lookup"><span data-stu-id="9f7c3-316">Bitmap compression</span></span>

* <span data-ttu-id="9f7c3-317">Combinación de lienzos</span><span class="sxs-lookup"><span data-stu-id="9f7c3-317">Canvas blending</span></span>

* <span data-ttu-id="9f7c3-318">Compatibilidad con widgets personalizados</span><span class="sxs-lookup"><span data-stu-id="9f7c3-318">Custom widget support</span></span>

* <span data-ttu-id="9f7c3-319">Compatibilidad con dibujos diferidos</span><span class="sxs-lookup"><span data-stu-id="9f7c3-319">Deferred drawing support</span></span>

* <span data-ttu-id="9f7c3-320">Compatibilidad con la interpolación</span><span class="sxs-lookup"><span data-stu-id="9f7c3-320">Dithering support</span></span>

* <span data-ttu-id="9f7c3-321">Programación neutra endian</span><span class="sxs-lookup"><span data-stu-id="9f7c3-321">Endian neutral programming</span></span>

* <span data-ttu-id="9f7c3-322">Compatibilidad con el acelerador de hardware</span><span class="sxs-lookup"><span data-stu-id="9f7c3-322">Hardware accelerator support</span></span>

* <span data-ttu-id="9f7c3-323">Compatibilidad multilingüe y codificación UTF-8</span><span class="sxs-lookup"><span data-stu-id="9f7c3-323">Multilingual support and UTF-8 encoding</span></span>

* <span data-ttu-id="9f7c3-324">Compatibilidad con varias pantallas y lienzos</span><span class="sxs-lookup"><span data-stu-id="9f7c3-324">Multiple display and canvas support</span></span>

* <span data-ttu-id="9f7c3-325">Recorte, dibujo y control de eventos optimizados</span><span class="sxs-lookup"><span data-stu-id="9f7c3-325">Optimized clipping, drawing, and event handling</span></span>

* <span data-ttu-id="9f7c3-326">Descodificador de JPEG y PNG runtime</span><span class="sxs-lookup"><span data-stu-id="9f7c3-326">Runtime JPEG and PNG decoder</span></span>

* <span data-ttu-id="9f7c3-327">Cambio de aspecto visual y temas</span><span class="sxs-lookup"><span data-stu-id="9f7c3-327">Skinning and Themes</span></span>

* <span data-ttu-id="9f7c3-328">Admite monocromo a través de color verdadero de 32 bits con formatos de gráficos alfa</span><span class="sxs-lookup"><span data-stu-id="9f7c3-328">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>

* <span data-ttu-id="9f7c3-329">Transiciones, sprites y compatibilidad con animaciones</span><span class="sxs-lookup"><span data-stu-id="9f7c3-329">Transitions, Sprites, and Animation support</span></span>

* <span data-ttu-id="9f7c3-330">Simulación de Win32</span><span class="sxs-lookup"><span data-stu-id="9f7c3-330">Win32 simulation</span></span>

* <span data-ttu-id="9f7c3-331">Administración de ventanas, incluidas las ventanillas y el mantenimiento de orden Z</span><span class="sxs-lookup"><span data-stu-id="9f7c3-331">Window management including Viewports and Z-order maintenance</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="9f7c3-332">Tiempo de comercialización más rápido</span><span class="sxs-lookup"><span data-stu-id="9f7c3-332">Fastest time-to-market</span></span>

<span data-ttu-id="9f7c3-333">Azure RTOS USBX es fácil de instalar, conocer, usar, depurar, comprobar, certificar y mantener.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-333">Azure RTOS GUIX is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="9f7c3-334">Azure RTOS GUIX Studio también ayuda a simplificar el diseño y la implementación de la GUI incrustada.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-334">Azure RTOS GUIX Studio also helps making embedded GUI design and implementation easier.</span></span> <span data-ttu-id="9f7c3-335">Como resultado, Azure RTOS GUIX es una de las soluciones GUI más populares para dispositivos IoT insertados.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-335">As a result, Azure RTOS GUIX is one of the most popular GUI solutions for embedded IoT devices.</span></span> <span data-ttu-id="9f7c3-336">Nuestra ventaja continua de plazo de comercialización se basa en lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9f7c3-336">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="9f7c3-337">Documentación de calidad: consulte nuestra [Guía de usuario de Azure RTOS GUIX](about-guix.md) y véalo usted mismo.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-337">Quality Documentation – please review our [Azure RTOS GUIX User Guide](about-guix.md) and see for yourself!</span></span>

* <span data-ttu-id="9f7c3-338">Disponibilidad completa del código fuente</span><span class="sxs-lookup"><span data-stu-id="9f7c3-338">Complete Source Code Availability</span></span>

* <span data-ttu-id="9f7c3-339">API fáciles de usar</span><span class="sxs-lookup"><span data-stu-id="9f7c3-339">Easy-to-use API</span></span>

* <span data-ttu-id="9f7c3-340">Conjunto de características completo y avanzado</span><span class="sxs-lookup"><span data-stu-id="9f7c3-340">Comprehensive and Advanced Feature Set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="9f7c3-341">Una licencia sencilla</span><span class="sxs-lookup"><span data-stu-id="9f7c3-341">One Simple License</span></span>

<span data-ttu-id="9f7c3-342">No hay ningún costo asociado al uso y las pruebas del código fuente ni a las licencias de producción si se implementa en dispositivos con licencia previa; todos los demás dispositivos necesitan una licencia anual sencilla.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-342">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="9f7c3-343">Código fuente completo y de máxima calidad</span><span class="sxs-lookup"><span data-stu-id="9f7c3-343">Full, highest-quality source code</span></span>

<span data-ttu-id="9f7c3-344">A lo largo de los años, el código fuente de Azure RTOS NetX ha marcado el listón en calidad y facilidad de comprensión.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-344">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="9f7c3-345">Además, la convención de tener una función por archivo facilita la navegación por el origen.</span><span class="sxs-lookup"><span data-stu-id="9f7c3-345">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="9f7c3-346">Compatible con las arquitecturas más populares</span><span class="sxs-lookup"><span data-stu-id="9f7c3-346">Supports most popular architectures</span></span>

<span data-ttu-id="9f7c3-347">Azure RTOS USBX se ejecuta en los microprocesadores de 32 o 64 bits más populares, de serie, totalmente probado y totalmente compatible, lo que incluye lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9f7c3-347">Azure RTOS GUIX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="9f7c3-348">Arquitecturas avanzadas:</span><span class="sxs-lookup"><span data-stu-id="9f7c3-348">Advanced Architectures:</span></span>

<span data-ttu-id="9f7c3-349">**Dispositivos analógicos**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="9f7c3-349">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="9f7c3-350">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="9f7c3-350">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="9f7c3-351">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="9f7c3-351">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="9f7c3-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="9f7c3-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="9f7c3-353">**Cadence**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="9f7c3-353">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="9f7c3-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="9f7c3-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="9f7c3-355">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="9f7c3-355">**Cypress**: RISC-V</span></span>

<span data-ttu-id="9f7c3-356">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="9f7c3-356">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="9f7c3-357">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="9f7c3-357">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="9f7c3-358">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="9f7c3-358">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="9f7c3-359">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="9f7c3-359">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="9f7c3-360">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="9f7c3-360">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="9f7c3-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="9f7c3-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="9f7c3-362">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="9f7c3-362">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="9f7c3-363">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="9f7c3-363">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="9f7c3-364">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="9f7c3-364">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="9f7c3-365">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="9f7c3-365">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="9f7c3-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="9f7c3-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="9f7c3-367">**Wave Computing**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="9f7c3-367">**Wave Computing**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="9f7c3-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="9f7c3-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>
