---
title: Descripción de Azure RTOS GUIX y Azure RTOS GUIX Studio
description: Azure RTOS GUIX es un paquete de calidad profesional creado para satisfacer las necesidades de los desarrolladores de sistemas insertados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 8f4a1578fcabdabfb213ced9c6593f6cffc964aa
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171410"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="b8f17-103">Información general de Azure RTOS GUIX y Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="b8f17-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="b8f17-104">La GUI insertada de Azure GUIX es la solución de GUI avanzada de nivel industrial de Microsoft diseñada específicamente para aplicaciones de IoT, en tiempo real e integradas profundamente.</span><span class="sxs-lookup"><span data-stu-id="b8f17-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="b8f17-105">Microsoft también proporciona una herramienta de diseño de escritorio WYSIWYG completa denominada Azure RTOS GUIX Studio, que permite a los desarrolladores diseñar su GUI en el escritorio y generar código de interfaz gráfica de usuario de Azure RTOS GUIX insertado que se puede exportar al destino.</span><span class="sxs-lookup"><span data-stu-id="b8f17-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="b8f17-106">Azure RTOS GUIX está totalmente integrado con los RTOS de Azure RTO ThreadX y está disponible para muchos de los mismos procesadores admitidos por Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b8f17-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="b8f17-107">Todo esto, combinado con un tamaño extremadamente pequeño, una ejecución rápida y una facilidad de uso superior, hacen de Azure RTOS GUIX la opción ideal para las aplicaciones de IoT integradas más exigentes que requieren una interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="b8f17-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="b8f17-108">Azure RTOS GUIX API</span><span class="sxs-lookup"><span data-stu-id="b8f17-108">Azure RTOS GUIX API</span></span>

### <a name="powerful-apis"></a><span data-ttu-id="b8f17-109">API eficaces</span><span class="sxs-lookup"><span data-stu-id="b8f17-109">Powerful APIs</span></span>

* <span data-ttu-id="b8f17-110">Compatibilidad total con el dibujo de lienzo directo cuando sea necesario</span><span class="sxs-lookup"><span data-stu-id="b8f17-110">Full support for direct canvas drawing when needed</span></span>
* <span data-ttu-id="b8f17-111">Fácil de interactuar con el código generado por Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="b8f17-111">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>
* <span data-ttu-id="b8f17-112">API para líneas, rectángulos, polígonos, etc.</span><span class="sxs-lookup"><span data-stu-id="b8f17-112">APIs for line, rectangle, polygon, etc.</span></span>
* <span data-ttu-id="b8f17-113">API para círculos, arco, circular, cuerda, elipse, etc.</span><span class="sxs-lookup"><span data-stu-id="b8f17-113">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>
* <span data-ttu-id="b8f17-114">API para dibujar y colocar texto</span><span class="sxs-lookup"><span data-stu-id="b8f17-114">APIs for text drawing and positioning</span></span>
* <span data-ttu-id="b8f17-115">Suavizado de contorno, relleno de textura y rellenos sólidos</span><span class="sxs-lookup"><span data-stu-id="b8f17-115">Anti-aliasing, texture fills, and solid fills</span></span>
* <span data-ttu-id="b8f17-116">API para crear y modificar pantallas y widgets</span><span class="sxs-lookup"><span data-stu-id="b8f17-116">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="b8f17-117">Archivos generados por Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="b8f17-117">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="b8f17-118">Archivos de código fuente ANSI C generados automáticamente</span><span class="sxs-lookup"><span data-stu-id="b8f17-118">Automatically generated ANSI C source files</span></span>
* <span data-ttu-id="b8f17-119">Aísla el software de la aplicación de los detalles del diseño</span><span class="sxs-lookup"><span data-stu-id="b8f17-119">Insulates application software from layout details</span></span>
* <span data-ttu-id="b8f17-120">Incluye fuentes e imágenes que requiere el diseño de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="b8f17-120">Includes fonts and images required by UI design</span></span>
* <span data-ttu-id="b8f17-121">Archivos generados compilados con código de aplicación</span><span class="sxs-lookup"><span data-stu-id="b8f17-121">Generated files compiled with application code</span></span>
* <span data-ttu-id="b8f17-122">El diseño de pantalla se puede actualizar sin afectar a la lógica de la aplicación</span><span class="sxs-lookup"><span data-stu-id="b8f17-122">Screen layout can be updated without affecting application logic</span></span>
* <span data-ttu-id="b8f17-123">Los identificadores de recursos crean independencia de lenguaje y tema</span><span class="sxs-lookup"><span data-stu-id="b8f17-123">Resource IDs create language and theme independence</span></span>
* <span data-ttu-id="b8f17-124">Funciones de dibujo y procesamiento de eventos personalizadas proporcionadas por el usuario</span><span class="sxs-lookup"><span data-stu-id="b8f17-124">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="b8f17-125">Biblioteca de widgets</span><span class="sxs-lookup"><span data-stu-id="b8f17-125">Widget library</span></span>

* <span data-ttu-id="b8f17-126">Conjunto predefinido pero personalizable de elementos comunes de la interfaz</span><span class="sxs-lookup"><span data-stu-id="b8f17-126">Pre-defined but customizable set of common interface elements</span></span>
* <span data-ttu-id="b8f17-127">Extremadamente pequeño, compacto y eficaz</span><span class="sxs-lookup"><span data-stu-id="b8f17-127">Extremely small, compact, and efficient</span></span>
* <span data-ttu-id="b8f17-128">La biblioteca incluye el botón, el medidor, la lista, la ventana, el desplazamiento, el control deslizante, la barra de progreso, el símbolo del sistema y muchos más</span><span class="sxs-lookup"><span data-stu-id="b8f17-128">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>
* <span data-ttu-id="b8f17-129">Dibujo y apariencia totalmente personalizables</span><span class="sxs-lookup"><span data-stu-id="b8f17-129">Fully customizable drawing and appearance</span></span>
* <span data-ttu-id="b8f17-130">Control de eventos y operaciones totalmente personalizables</span><span class="sxs-lookup"><span data-stu-id="b8f17-130">Fully customizable operation and event handling</span></span>
* <span data-ttu-id="b8f17-131">Solo los widgets usados están vinculados con el software de la aplicación</span><span class="sxs-lookup"><span data-stu-id="b8f17-131">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="b8f17-132">Matemáticas y utilidades</span><span class="sxs-lookup"><span data-stu-id="b8f17-132">Math and utilities</span></span>

* <span data-ttu-id="b8f17-133">Funciones para sin, cos, arcsin, arccos, tangente, raíz cuadrada</span><span class="sxs-lookup"><span data-stu-id="b8f17-133">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>
* <span data-ttu-id="b8f17-134">Funciones para manipular regiones de pantalla</span><span class="sxs-lookup"><span data-stu-id="b8f17-134">Functions for manipulating screen regions</span></span>
* <span data-ttu-id="b8f17-135">Configuración e inicio del sistema</span><span class="sxs-lookup"><span data-stu-id="b8f17-135">System configuration and startup</span></span>
* <span data-ttu-id="b8f17-136">Definición del grupo de memoria (opcional)</span><span class="sxs-lookup"><span data-stu-id="b8f17-136">Memory pool definition (optional)</span></span>
* <span data-ttu-id="b8f17-137">Administración de temporizadores</span><span class="sxs-lookup"><span data-stu-id="b8f17-137">Timer Management</span></span>
* <span data-ttu-id="b8f17-138">Administrador de animaciones</span><span class="sxs-lookup"><span data-stu-id="b8f17-138">Animation Management</span></span>
* <span data-ttu-id="b8f17-139">Mantenimiento de la lista de integridad</span><span class="sxs-lookup"><span data-stu-id="b8f17-139">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="b8f17-140">Procesamiento de imágenes</span><span class="sxs-lookup"><span data-stu-id="b8f17-140">Image processing</span></span>

* <span data-ttu-id="b8f17-141">Funciones para descodificar en tiempo de ejecución imágenes jpeg y png</span><span class="sxs-lookup"><span data-stu-id="b8f17-141">Functions for runtime decode of jpeg and png images</span></span>
* <span data-ttu-id="b8f17-142">Aplicar la conversión de espacio de colores y interpolación</span><span class="sxs-lookup"><span data-stu-id="b8f17-142">Apply dithering and color space conversion</span></span>
* <span data-ttu-id="b8f17-143">Rotación de imagen</span><span class="sxs-lookup"><span data-stu-id="b8f17-143">Image rotation</span></span>
* <span data-ttu-id="b8f17-144">Escalado de imagen</span><span class="sxs-lookup"><span data-stu-id="b8f17-144">Image scaling</span></span>
* <span data-ttu-id="b8f17-145">Combinación de imagen</span><span class="sxs-lookup"><span data-stu-id="b8f17-145">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="b8f17-146">Procesamiento de eventos</span><span class="sxs-lookup"><span data-stu-id="b8f17-146">Event processing</span></span>

* <span data-ttu-id="b8f17-147">Suspende automáticamente el subproceso de Azure RTOS GUIX cuando está inactivo</span><span class="sxs-lookup"><span data-stu-id="b8f17-147">Automatically suspends Azure RTOS GUIX thread when idle</span></span>
* <span data-ttu-id="b8f17-148">Modelo de programación orientado a eventos conocido en el diseño de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="b8f17-148">Event-driven programming model popular in UI design</span></span>
* <span data-ttu-id="b8f17-149">Aísla los controladores de entrada del subproceso de dibujo de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="b8f17-149">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>
* <span data-ttu-id="b8f17-150">Funciones para enviar y recibir eventos</span><span class="sxs-lookup"><span data-stu-id="b8f17-150">Functions for sending and receiving events</span></span>
* <span data-ttu-id="b8f17-151">Tipos de eventos predefinidos para todos los tipos de widgets de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="b8f17-151">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>
* <span data-ttu-id="b8f17-152">Se admiten eventos personalizados definidos por el usuario</span><span class="sxs-lookup"><span data-stu-id="b8f17-152">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="b8f17-153">Procesamiento de lienzo</span><span class="sxs-lookup"><span data-stu-id="b8f17-153">Canvas processing</span></span>

* <span data-ttu-id="b8f17-154">Recorte y mantenimiento del orden Z</span><span class="sxs-lookup"><span data-stu-id="b8f17-154">Clipping and Z-Order maintenance</span></span>
* <span data-ttu-id="b8f17-155">Aísla la biblioteca de widgets de detalles de hardware</span><span class="sxs-lookup"><span data-stu-id="b8f17-155">Insulates widget library from hardware details</span></span>
* <span data-ttu-id="b8f17-156">Aísla la aplicación de los detalles de hardware</span><span class="sxs-lookup"><span data-stu-id="b8f17-156">Insulates application from hardware details</span></span>
* <span data-ttu-id="b8f17-157">Actualización automática en segundo plano de áreas desfasadas</span><span class="sxs-lookup"><span data-stu-id="b8f17-157">Automatic background refresh of dirty areas</span></span>
* <span data-ttu-id="b8f17-158">Se admiten varios lienzos con capas y combinación</span><span class="sxs-lookup"><span data-stu-id="b8f17-158">Multiple canvases with layering and blending supported</span></span>
* <span data-ttu-id="b8f17-159">Se puede invocar directamente mediante el software de la aplicación</span><span class="sxs-lookup"><span data-stu-id="b8f17-159">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="b8f17-160">Controladores de dispositivo de entrada</span><span class="sxs-lookup"><span data-stu-id="b8f17-160">Input device driver(s)</span></span>

* <span data-ttu-id="b8f17-161">Compatibilidad específica con el hardware, Azure RTOS GUIX y la aplicación aislada de los detalles de hardware</span><span class="sxs-lookup"><span data-stu-id="b8f17-161">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>
* <span data-ttu-id="b8f17-162">Touch resistente, extremo touch y teclado numérico compatible</span><span class="sxs-lookup"><span data-stu-id="b8f17-162">Resistive Touch, Cap Touch, and keypad supported</span></span>
* <span data-ttu-id="b8f17-163">Eventos de entrada pasados a la cola de eventos de Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="b8f17-163">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="b8f17-164">Mostrar controladores</span><span class="sxs-lookup"><span data-stu-id="b8f17-164">Display drivers</span></span>

* <span data-ttu-id="b8f17-165">Compatibilidad específica del hardware</span><span class="sxs-lookup"><span data-stu-id="b8f17-165">Hardware-specific support</span></span>
* <span data-ttu-id="b8f17-166">Controladores genéricos proporcionados para todos los formatos y la profundidad de color</span><span class="sxs-lookup"><span data-stu-id="b8f17-166">Generic drivers provided for all color depth and formats</span></span>
* <span data-ttu-id="b8f17-167">Personalización para el uso de aceleradores de gráficos disponibles</span><span class="sxs-lookup"><span data-stu-id="b8f17-167">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="b8f17-168">Hardware de destino</span><span class="sxs-lookup"><span data-stu-id="b8f17-168">Target hardware</span></span>

* <span data-ttu-id="b8f17-169">Casi cualquier hardware con capacidad de salida gráfica es compatible con GUIX</span><span class="sxs-lookup"><span data-stu-id="b8f17-169">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>
* <span data-ttu-id="b8f17-170">Se admiten varias pantallas físicas</span><span class="sxs-lookup"><span data-stu-id="b8f17-170">Multiple physical displays supported</span></span>
* <span data-ttu-id="b8f17-171">Requisitos de RAM y Flash mínimos</span><span class="sxs-lookup"><span data-stu-id="b8f17-171">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="b8f17-172">Crear interfaces de usuario elegantes</span><span class="sxs-lookup"><span data-stu-id="b8f17-172">Create Elegant User Interfaces</span></span>

<span data-ttu-id="b8f17-173">Azure RTOS GUIX y Azure RTOS GUIX Studio proporcionan todas las características necesarias para crear interfaces de usuario de forma exclusiva.</span><span class="sxs-lookup"><span data-stu-id="b8f17-173">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="b8f17-174">El paquete estándar de Azure RTOS GUIX incluye varias interfaces de usuario de ejemplo, entre las que se incluyen una referencia de dispositivo médico, una referencia de smart watch, una referencia de automatización doméstica, una referencia de control industrial, una referencia de automóviles y varios ejemplos de objetos sprite y animación.</span><span class="sxs-lookup"><span data-stu-id="b8f17-174">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="b8f17-175">Haga clic en los ejemplos de referencia que se muestran a continuación.</span><span class="sxs-lookup"><span data-stu-id="b8f17-175">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="b8f17-176">Automatización de inicio</span><span class="sxs-lookup"><span data-stu-id="b8f17-176">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="b8f17-177">Medicina</span><span class="sxs-lookup"><span data-stu-id="b8f17-177">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="b8f17-178">Consumidor</span><span class="sxs-lookup"><span data-stu-id="b8f17-178">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="b8f17-179">Electrodomésticos</span><span class="sxs-lookup"><span data-stu-id="b8f17-179">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="b8f17-180">Automoción</span><span class="sxs-lookup"><span data-stu-id="b8f17-180">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="b8f17-181">Industrial</span><span class="sxs-lookup"><span data-stu-id="b8f17-181">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="b8f17-182">Cada referencia de Azure RTOS GUIX tiene un proyecto de Azure RTOS GUIX Studio correspondiente que define todos los elementos gráficos del diseño de referencia.</span><span class="sxs-lookup"><span data-stu-id="b8f17-182">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="b8f17-183">Es fácil cambiar el diseño de una referencia.</span><span class="sxs-lookup"><span data-stu-id="b8f17-183">Changing a reference design is easy.</span></span> <span data-ttu-id="b8f17-184">Simplemente abra el proyecto Azure RTOS GUIX correspondiente, realice los cambios deseados, guarde el proyecto y, a continuación, seleccione *Proyecto*.</span><span class="sxs-lookup"><span data-stu-id="b8f17-184">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="b8f17-185">Genere todos los archivos de salida para generar el código C para Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="b8f17-185">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="b8f17-186">A continuación, simplemente vuelva a compilar la aplicación de destino y ejecútela para observar el diseño de referencia modificado.</span><span class="sxs-lookup"><span data-stu-id="b8f17-186">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="memory-footprint"></a><span data-ttu-id="b8f17-187">Superficie de memoria</span><span class="sxs-lookup"><span data-stu-id="b8f17-187">Memory footprint</span></span>

<span data-ttu-id="b8f17-188">Azure RTOS GUIX tiene una superficie mínima de 13,2 KB de FLASH y 4 KB de RAM para soporte básico, sin incluir la memoria necesaria para un lienzo.</span><span class="sxs-lookup"><span data-stu-id="b8f17-188">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="b8f17-189">En el caso de una pantalla con la tecnología interna GRAM y de actualización automática, no se requiere memoria de lienzo.</span><span class="sxs-lookup"><span data-stu-id="b8f17-189">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="b8f17-190">Sin embargo, para mejorar el rendimiento del dibujo o para una configuración de pantalla que no use GRAM local para esta, la aplicación define un área de memoria de lienzo.</span><span class="sxs-lookup"><span data-stu-id="b8f17-190">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="b8f17-191">Los requisitos de memoria de lienzo son una función del tamaño de este y la profundidad de color, y se definen mediante la fórmula:</span><span class="sxs-lookup"><span data-stu-id="b8f17-191">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="b8f17-192"><i>Lienzo RAM (bytes) = (x \* y \* (bpp/8))</i></span><span class="sxs-lookup"><span data-stu-id="b8f17-192"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="b8f17-193">Donde "x" y "y" son las dimensiones del lienzo (Mostrar).</span><span class="sxs-lookup"><span data-stu-id="b8f17-193">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="b8f17-194">La mayoría de las aplicaciones también usan recursos gráficos, que no se incluyen en los requisitos básicos de almacenamiento de la biblioteca Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="b8f17-194">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="b8f17-195">Estos recursos incluyen fuentes, iconos gráficos (PixelMap) y cadenas estáticas.</span><span class="sxs-lookup"><span data-stu-id="b8f17-195">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="b8f17-196">Estos datos se pueden almacenar en la sección de memoria const (es decir, FLASH).</span><span class="sxs-lookup"><span data-stu-id="b8f17-196">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="b8f17-197">El tamaño de este área de memoria depende de varios factores, como el número y el tamaño de las fuentes únicas utilizadas, el número y el tamaño de los iconos gráficos usados, el formato de color de salida y si cada recurso está usando datos comprimidos, ya que Azure RTOS GUIX admite la compresión RLE de los datos de fuente y de PixelMap.</span><span class="sxs-lookup"><span data-stu-id="b8f17-197">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="b8f17-198">Los requisitos de almacenamiento de cada recurso se muestran dentro de la aplicación Azure RTOS GUIX Studio, lo que permite al usuario realizar un seguimiento y supervisar la cantidad de memoria Flash que consumirán los recursos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b8f17-198">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="b8f17-199">Al igual que Azure RTOS ThreadX, el tamaño de Azure RTOS GUIX se escala automáticamente en función de los servicios que la aplicación usa realmente.</span><span class="sxs-lookup"><span data-stu-id="b8f17-199">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="b8f17-200">Esto elimina prácticamente la necesidad de configuraciones y parámetros de compilación complicados, lo que facilita el trabajo del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="b8f17-200">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="b8f17-201">Simple y fácil de usar</span><span class="sxs-lookup"><span data-stu-id="b8f17-201">Simple, easy-to-use</span></span>

<span data-ttu-id="b8f17-202">Azure RTOS GUIX es muy simple de usar y Azure RTOS GUIX Studio lo hace aún más fácil al permitir a los desarrolladores diseñar visualmente en el escritorio y generar código C que se ejecuta en el objetivo real.</span><span class="sxs-lookup"><span data-stu-id="b8f17-202">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="b8f17-203">Después, las aplicaciones pueden agregar sus propias funciones de control de eventos y dibujo personalizadas para completar su GUI.</span><span class="sxs-lookup"><span data-stu-id="b8f17-203">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="b8f17-204">El uso de la API de Azure RTOS GUIX es sencillo.</span><span class="sxs-lookup"><span data-stu-id="b8f17-204">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="b8f17-205">La API de Azure RTOS GUIX es intuitiva y altamente funcional.</span><span class="sxs-lookup"><span data-stu-id="b8f17-205">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="b8f17-206">Los nombres de API se componen de palabras reales y no de la "sopa de letras" ni de los nombres muy abreviados que son tan comunes en otros productos del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="b8f17-206">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="b8f17-207">Todas las API de Azure RTOS GUIX tienen una *gx_* inicial y siguen una convención de nomenclatura de sustantivos.</span><span class="sxs-lookup"><span data-stu-id="b8f17-207">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="b8f17-208">Además, existe una coherencia funcional en la API.</span><span class="sxs-lookup"><span data-stu-id="b8f17-208">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="b8f17-209">Por ejemplo, todas las API que inicializan un bloque de control widget se denominan &lt;widget_type&gt;_create y los parámetros de la función crear para cada tipo de widget siempre se definen en el mismo orden.</span><span class="sxs-lookup"><span data-stu-id="b8f17-209">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="b8f17-210">Conjunto completo de widgets integrados</span><span class="sxs-lookup"><span data-stu-id="b8f17-210">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="b8f17-211">Azure RTOS GUIX ofrece un amplio conjunto de widgets integrados, entre los que se incluyen:</span><span class="sxs-lookup"><span data-stu-id="b8f17-211">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>
* <span data-ttu-id="b8f17-212">Menú Accordion</span><span class="sxs-lookup"><span data-stu-id="b8f17-212">Accordion Menu</span></span>
* <span data-ttu-id="b8f17-213">Botón</span><span class="sxs-lookup"><span data-stu-id="b8f17-213">Button</span></span>
* <span data-ttu-id="b8f17-214">Casilla de verificación</span><span class="sxs-lookup"><span data-stu-id="b8f17-214">Checkbox</span></span>
* <span data-ttu-id="b8f17-215">Medidor circular</span><span class="sxs-lookup"><span data-stu-id="b8f17-215">Circular Gauge</span></span>
* <span data-ttu-id="b8f17-216">Lista desplegable</span><span class="sxs-lookup"><span data-stu-id="b8f17-216">Drop Down List</span></span>
* <span data-ttu-id="b8f17-217">Lista horizontal</span><span class="sxs-lookup"><span data-stu-id="b8f17-217">Horizontal List</span></span>
* <span data-ttu-id="b8f17-218">Horizontal Scrollbar Window</span><span class="sxs-lookup"><span data-stu-id="b8f17-218">Horizontal Scrollbar Window</span></span>
* <span data-ttu-id="b8f17-219">Icono</span><span class="sxs-lookup"><span data-stu-id="b8f17-219">Icon</span></span>
* <span data-ttu-id="b8f17-220">Botón de icono</span><span class="sxs-lookup"><span data-stu-id="b8f17-220">Icon Button</span></span>
* <span data-ttu-id="b8f17-221">Gráfico de líneas</span><span class="sxs-lookup"><span data-stu-id="b8f17-221">Line Chart</span></span>
* <span data-ttu-id="b8f17-222">Menú</span><span class="sxs-lookup"><span data-stu-id="b8f17-222">Menu</span></span>
* <span data-ttu-id="b8f17-223">Botón de texto de varias líneas</span><span class="sxs-lookup"><span data-stu-id="b8f17-223">Multi Line Text Button</span></span>
* <span data-ttu-id="b8f17-224">Entrada de texto de varias líneas</span><span class="sxs-lookup"><span data-stu-id="b8f17-224">Multi Line Text Input</span></span>
* <span data-ttu-id="b8f17-225">Vista de texto de varias líneas</span><span class="sxs-lookup"><span data-stu-id="b8f17-225">Multi Line Text View</span></span>
* <span data-ttu-id="b8f17-226">Solicitud PixelMap numérica</span><span class="sxs-lookup"><span data-stu-id="b8f17-226">Numeric Pixelmap Prompt</span></span>
* <span data-ttu-id="b8f17-227">Solicitud numérica</span><span class="sxs-lookup"><span data-stu-id="b8f17-227">Numeric Prompt</span></span>
* <span data-ttu-id="b8f17-228">Rueda del mouse numérico</span><span class="sxs-lookup"><span data-stu-id="b8f17-228">Numeric Scroll Wheel</span></span>
* <span data-ttu-id="b8f17-229">Botón PixelMap</span><span class="sxs-lookup"><span data-stu-id="b8f17-229">Pixelmap Button</span></span>
* <span data-ttu-id="b8f17-230">Símbolo del sistema de PixelMap</span><span class="sxs-lookup"><span data-stu-id="b8f17-230">Pixelmap Prompt</span></span>
* <span data-ttu-id="b8f17-231">Control deslizante PixelMap</span><span class="sxs-lookup"><span data-stu-id="b8f17-231">Pixelmap Slider</span></span>
* <span data-ttu-id="b8f17-232">Sprite PixelMap</span><span class="sxs-lookup"><span data-stu-id="b8f17-232">Pixelmap Sprite</span></span>
* <span data-ttu-id="b8f17-233">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="b8f17-233">Progress Bar</span></span>
* <span data-ttu-id="b8f17-234">Prompt</span><span class="sxs-lookup"><span data-stu-id="b8f17-234">Prompt</span></span>
* <span data-ttu-id="b8f17-235">Barra de progreso radial</span><span class="sxs-lookup"><span data-stu-id="b8f17-235">Radial Progress Bar</span></span>
* <span data-ttu-id="b8f17-236">Radio Button</span><span class="sxs-lookup"><span data-stu-id="b8f17-236">Radio Button</span></span>
* <span data-ttu-id="b8f17-237">Rueda del mouse</span><span class="sxs-lookup"><span data-stu-id="b8f17-237">Scroll Wheel</span></span>
* <span data-ttu-id="b8f17-238">Entrada de texto de una sola línea</span><span class="sxs-lookup"><span data-stu-id="b8f17-238">Single Line Text Input</span></span>
* <span data-ttu-id="b8f17-239">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="b8f17-239">Slider</span></span>
* <span data-ttu-id="b8f17-240">Rueda del mouse de cadena</span><span class="sxs-lookup"><span data-stu-id="b8f17-240">String Scroll Wheel</span></span>
* <span data-ttu-id="b8f17-241">Botón de texto</span><span class="sxs-lookup"><span data-stu-id="b8f17-241">Text Button</span></span>
* <span data-ttu-id="b8f17-242">Vista de árbol</span><span class="sxs-lookup"><span data-stu-id="b8f17-242">Tree View</span></span>
* <span data-ttu-id="b8f17-243">Lista vertical</span><span class="sxs-lookup"><span data-stu-id="b8f17-243">Vertical List</span></span>
* <span data-ttu-id="b8f17-244">Barra de desplazamiento vertical</span><span class="sxs-lookup"><span data-stu-id="b8f17-244">Vertical Scrollbar</span></span>

<span data-ttu-id="b8f17-245">También es fácil para la aplicación crear sus propios widgets de cliente.</span><span class="sxs-lookup"><span data-stu-id="b8f17-245">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="b8f17-246">Completar la API de dibujo de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="b8f17-246">Complete low-level drawing API</span></span>

<span data-ttu-id="b8f17-247">Azure RTOS GUIX proporciona una API de dibujo de lienzo sólida, lo que permite que la aplicación represente formas gráficas complejas.</span><span class="sxs-lookup"><span data-stu-id="b8f17-247">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="b8f17-248">Todas las funciones admiten el suavizado de contorno en los objetivos de profundidad de color alta y todas las formas se pueden rellenar, incluidos los rellenos de patrón sólido y PixelMap.</span><span class="sxs-lookup"><span data-stu-id="b8f17-248">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="b8f17-249">Todos los primitivos de dibujo admiten el pincel alfa cuando se ejecutan con 16 bpp y una profundidad de color superior.</span><span class="sxs-lookup"><span data-stu-id="b8f17-249">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="b8f17-250">Las funciones de dibujo incluyen:</span><span class="sxs-lookup"><span data-stu-id="b8f17-250">Drawing functions include:</span></span>

* <span data-ttu-id="b8f17-251">Dibujo de arco</span><span class="sxs-lookup"><span data-stu-id="b8f17-251">Arc Draw</span></span>
* <span data-ttu-id="b8f17-252">Dibujo con círculo</span><span class="sxs-lookup"><span data-stu-id="b8f17-252">Circle Draw</span></span>
* <span data-ttu-id="b8f17-253">Dibujo de línea</span><span class="sxs-lookup"><span data-stu-id="b8f17-253">Line Draw</span></span>
* <span data-ttu-id="b8f17-254">Dibujo circular</span><span class="sxs-lookup"><span data-stu-id="b8f17-254">Pie Draw</span></span>
* <span data-ttu-id="b8f17-255">PixelMap Blend</span><span class="sxs-lookup"><span data-stu-id="b8f17-255">Pixelmap Blend</span></span>
* <span data-ttu-id="b8f17-256">Icono de PixelMap</span><span class="sxs-lookup"><span data-stu-id="b8f17-256">Pixelmap Tile</span></span>
* <span data-ttu-id="b8f17-257">Dibujo de polígono</span><span class="sxs-lookup"><span data-stu-id="b8f17-257">Polygon Draw</span></span>
* <span data-ttu-id="b8f17-258">Dibujo de texto</span><span class="sxs-lookup"><span data-stu-id="b8f17-258">Text Draw</span></span>
* <span data-ttu-id="b8f17-259">Dibujo de cuerda</span><span class="sxs-lookup"><span data-stu-id="b8f17-259">Chord Draw</span></span>
* <span data-ttu-id="b8f17-260">Dibujo de elipse</span><span class="sxs-lookup"><span data-stu-id="b8f17-260">Ellipse Draw</span></span>
* <span data-ttu-id="b8f17-261">Dibujo de píxeles</span><span class="sxs-lookup"><span data-stu-id="b8f17-261">Pixel Draw</span></span>
* <span data-ttu-id="b8f17-262">Dibujo de PixelMap</span><span class="sxs-lookup"><span data-stu-id="b8f17-262">Pixelmap Draw</span></span>
* <span data-ttu-id="b8f17-263">Girar PixelMap</span><span class="sxs-lookup"><span data-stu-id="b8f17-263">Pixelmap Rotate</span></span>
* <span data-ttu-id="b8f17-264">Dibujo de rectángulo</span><span class="sxs-lookup"><span data-stu-id="b8f17-264">Rectangle Draw</span></span>
* <span data-ttu-id="b8f17-265">Combinación de texto</span><span class="sxs-lookup"><span data-stu-id="b8f17-265">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="b8f17-266">Fuentes gratuitas predeterminadas y fáciles de agregar</span><span class="sxs-lookup"><span data-stu-id="b8f17-266">Default free fonts and easy to add more</span></span>

<span data-ttu-id="b8f17-267">Azure RTOS GUIX proporciona un conjunto gratuito de fuentes TrueType.</span><span class="sxs-lookup"><span data-stu-id="b8f17-267">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="b8f17-268">Los desarrolladores pueden agregar fuentes TrueType adicionales según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="b8f17-268">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="b8f17-269">El formato de fuente Azure RTOS GUIX admite el suavizado de contorno 8 bpp, el suavizado de contorno de 4 bpp y las fuentes monocromáticas 1 bpp.</span><span class="sxs-lookup"><span data-stu-id="b8f17-269">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="b8f17-270">En el caso de la mayoría de las aplicaciones con restricciones de recursos, Azure RTOS GUIX prerepresenta las fuentes TrueType en un formato de mapa de bits comprimido mediante nuestra herramienta de escritorio de GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="b8f17-270">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="b8f17-271">Implementación descodificador de JPG y PNG personalizado</span><span class="sxs-lookup"><span data-stu-id="b8f17-271">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="b8f17-272">Implementación del descodificador JPG y PNG personalizado, implementación del descodificador de archivos JPG y PNG.</span><span class="sxs-lookup"><span data-stu-id="b8f17-272">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="b8f17-273">Esta implementación admite la conversión de espacio de colores, la interpolación y la creación en tiempo de ejecución de imágenes con formato PixelMap compatible con Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="b8f17-273">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="b8f17-274">Amplia compatibilidad con pantallas y pantallas táctiles</span><span class="sxs-lookup"><span data-stu-id="b8f17-274">Extensive display and touchscreen support</span></span>

<span data-ttu-id="b8f17-275">Azure RTOS GUIX proporciona controladores de pantalla genéricos para casi todos los formatos de color, incluido el monocromo de 1 bpp, la paleta de 8 bpp, el formato 3:3:2 de 8 bpp,</span><span class="sxs-lookup"><span data-stu-id="b8f17-275">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="b8f17-276">el formato 16 bpp 565 rgb, el formato 16 bpp 4:4:4:4, formato 32 bpp x:r:g:b y el formato 32 bpp a:r:g:b.</span><span class="sxs-lookup"><span data-stu-id="b8f17-276">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="b8f17-277">Además, Azure RTOS GUIX se integra con muchos de los aceleradores de hardware y controladores LCD más populares (ST ChromeArt, Renesas Synergy, etc.).</span><span class="sxs-lookup"><span data-stu-id="b8f17-277">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="b8f17-278">Azure RTOS GUIX es totalmente compatible con la pantalla táctil (incluida la compatibilidad con gestos), el lápiz y los dispositivos de entrada de teclado virtual.</span><span class="sxs-lookup"><span data-stu-id="b8f17-278">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="b8f17-279">Herramienta de escritorio WYSIWYG de Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="b8f17-279">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="b8f17-280">Azure RTOS GUIX Studio proporciona un entorno de diseño de pantalla WYSIWYG completo que permite al usuario arrastrar y colocar elementos gráficos usados para compilar las pantallas de la GUI.</span><span class="sxs-lookup"><span data-stu-id="b8f17-280">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="b8f17-281">Azure RTOS GUIX Studio genera automáticamente un código de C compatible con la biblioteca de Azure RTOS GUIX, listo para compilarse y ejecutarse en el destino.</span><span class="sxs-lookup"><span data-stu-id="b8f17-281">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="b8f17-282">Los desarrolladores pueden generar fuentes previamente representadas para su uso en una aplicación mediante la herramienta de generación de fuentes de Azure RTOS GUIX Studio integrada.</span><span class="sxs-lookup"><span data-stu-id="b8f17-282">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="b8f17-283">Las fuentes se pueden generar en formatos monocromo o suavizados y se optimizan para ahorrar espacio en el destino.</span><span class="sxs-lookup"><span data-stu-id="b8f17-283">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="b8f17-284">Las fuentes pueden incluir cualquier juego de caracteres, incluidos los caracteres Unicode para aplicaciones multilingües.</span><span class="sxs-lookup"><span data-stu-id="b8f17-284">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="b8f17-285">Azure RTOS GUIX Studio facilita la importación de gráficos de archivos PNG o JPG con la conversión a los PixelMap de Azure RTOS GUIX comprimidos para su uso en el sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="b8f17-285">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="b8f17-286">Muchos de los tipos de widgets de Azure RTOS GUIX están diseñados para incorporar gráficos de usuario para una apariencia personalizada.</span><span class="sxs-lookup"><span data-stu-id="b8f17-286">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="b8f17-287">Además, Azure RTOS GUIX Studio permite la personalización de los colores predeterminados y los estilos de dibujo usados por los widgets de Azure RTOS GUIX, lo que permite a los desarrolladores ajustar la apariencia de Azure RTOS GUIX muy fácilmente.</span><span class="sxs-lookup"><span data-stu-id="b8f17-287">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="b8f17-288">La generación y el mantenimiento de cadenas de aplicación es otra instalación integrada de Azure RTOS GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="b8f17-288">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="b8f17-289">Esto permite a los desarrolladores diseñar una aplicación con un lenguaje para desarrollar y agregar de forma rápida y sencilla compatibilidad para idiomas adicionales después de lanzar el producto.</span><span class="sxs-lookup"><span data-stu-id="b8f17-289">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="b8f17-290">Se puede ejecutar una aplicación completa de Azure RTOS GUIX en un equipo de escritorio en el entorno de Azure RTOS GUIX Studio, lo que permite una generación y demostración rápidas y sencillas de conceptos de GUI, pruebas de flujos de pantalla y observación de transiciones de pantalla y animaciones.</span><span class="sxs-lookup"><span data-stu-id="b8f17-290">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="b8f17-291">Una vez completado, un diseño se puede exportar como estructuras de datos de C listas para el destino, listas para su compilación y vinculación con las bibliotecas de Azure RTOS GUIX y Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b8f17-291">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="b8f17-292">Azure RTOS GUIX y Azure RTOS GUIX Studio admiten varios temas de recursos, lo que permite que una aplicación se pueda cambiar fácilmente de nivel en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="b8f17-292">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="b8f17-293">Las fuentes, los colores y el PixelMap se pueden cambiar en tiempo de ejecución con una API simple.</span><span class="sxs-lookup"><span data-stu-id="b8f17-293">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="b8f17-294">Más información sobre GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="b8f17-294">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="b8f17-295">Completar la simulación de Win32</span><span class="sxs-lookup"><span data-stu-id="b8f17-295">Complete Win32 simulation</span></span>

<span data-ttu-id="b8f17-296">Azure RTOS GUIX se ejecuta en un equipo con Windows, usando exactamente la misma biblioteca de dibujo que se ejecuta en la placa de destino.</span><span class="sxs-lookup"><span data-stu-id="b8f17-296">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="b8f17-297">Con Azure RTOS GUIX, puede compilar y ejecutar una aplicación GUI en el equipo y usar el mismo código de aplicación en el destino para la depuración, la creación de prototipos, la demostración y el funcionamiento del destino WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="b8f17-297">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="b8f17-298">Tecnología avanzada</span><span class="sxs-lookup"><span data-stu-id="b8f17-298">Advanced technology</span></span>

* <span data-ttu-id="b8f17-299">La tecnología avanzada de Azure RTOS GUIX incorpora:</span><span class="sxs-lookup"><span data-stu-id="b8f17-299">Azure RTOS GUIX's advanced technology incorporates:</span></span>
* <span data-ttu-id="b8f17-300">Combinación alfa</span><span class="sxs-lookup"><span data-stu-id="b8f17-300">Alpha blending</span></span>
* <span data-ttu-id="b8f17-301">Suavizado de contorno</span><span class="sxs-lookup"><span data-stu-id="b8f17-301">Anti-Aliasing</span></span>
* <span data-ttu-id="b8f17-302">Escalado automático</span><span class="sxs-lookup"><span data-stu-id="b8f17-302">Automatic scaling</span></span>
* <span data-ttu-id="b8f17-303">Compresión de mapa de bits</span><span class="sxs-lookup"><span data-stu-id="b8f17-303">Bitmap compression</span></span>
* <span data-ttu-id="b8f17-304">Combinación de lienzos</span><span class="sxs-lookup"><span data-stu-id="b8f17-304">Canvas blending</span></span>
* <span data-ttu-id="b8f17-305">Compatibilidad con widgets personalizados</span><span class="sxs-lookup"><span data-stu-id="b8f17-305">Custom widget support</span></span>
* <span data-ttu-id="b8f17-306">Compatibilidad con dibujos diferidos</span><span class="sxs-lookup"><span data-stu-id="b8f17-306">Deferred drawing support</span></span>
* <span data-ttu-id="b8f17-307">Compatibilidad con la interpolación</span><span class="sxs-lookup"><span data-stu-id="b8f17-307">Dithering support</span></span>
* <span data-ttu-id="b8f17-308">Programación neutra endian</span><span class="sxs-lookup"><span data-stu-id="b8f17-308">Endian neutral programming</span></span>
* <span data-ttu-id="b8f17-309">Compatibilidad con el acelerador de hardware</span><span class="sxs-lookup"><span data-stu-id="b8f17-309">Hardware accelerator support</span></span>
* <span data-ttu-id="b8f17-310">Compatibilidad multilingüe y codificación UTF-8</span><span class="sxs-lookup"><span data-stu-id="b8f17-310">Multilingual support and UTF-8 encoding</span></span>
* <span data-ttu-id="b8f17-311">Compatibilidad con varias pantallas y lienzos</span><span class="sxs-lookup"><span data-stu-id="b8f17-311">Multiple display and canvas support</span></span>
* <span data-ttu-id="b8f17-312">Recorte, dibujo y control de eventos optimizados</span><span class="sxs-lookup"><span data-stu-id="b8f17-312">Optimized clipping, drawing, and event handling</span></span>
* <span data-ttu-id="b8f17-313">Descodificador de JPEG y PNG runtime</span><span class="sxs-lookup"><span data-stu-id="b8f17-313">Runtime JPEG and PNG decoder</span></span>
* <span data-ttu-id="b8f17-314">Cambio de aspecto visual y temas</span><span class="sxs-lookup"><span data-stu-id="b8f17-314">Skinning and Themes</span></span>
* <span data-ttu-id="b8f17-315">Admite monocromo a través de color verdadero de 32 bits con formatos de gráficos alfa</span><span class="sxs-lookup"><span data-stu-id="b8f17-315">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>
* <span data-ttu-id="b8f17-316">Transiciones, sprites y compatibilidad con animaciones</span><span class="sxs-lookup"><span data-stu-id="b8f17-316">Transitions, Sprites, and Animation support</span></span>
* <span data-ttu-id="b8f17-317">Simulación de Win32</span><span class="sxs-lookup"><span data-stu-id="b8f17-317">Win32 simulation</span></span>
* <span data-ttu-id="b8f17-318">Administración de ventanas, incluidas las ventanillas y el mantenimiento de orden Z</span><span class="sxs-lookup"><span data-stu-id="b8f17-318">Window management including Viewports and Z-order maintenance</span></span>
