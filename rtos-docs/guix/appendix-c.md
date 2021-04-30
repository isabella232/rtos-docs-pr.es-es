---
title: 'Apéndice C: Estilos de widget de GUIX'
description: Obtenga información sobre los estilos de widget de GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 83d5c5167739e91b7af8fce6b04213f610984fc6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815573"
---
# <a name="appendix-c---guix-widget-styles"></a><span data-ttu-id="fd3e9-103">Apéndice C: Estilos de widget de GUIX</span><span class="sxs-lookup"><span data-stu-id="fd3e9-103">Appendix C - GUIX Widget Styles</span></span>

<span data-ttu-id="fd3e9-104">__***Estilos generales (usados con la mayoría de los tipos de widget):***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-104">__***General Styles (Used with most widget types):***__</span></span>

<span data-ttu-id="fd3e9-105">**GX_STYLE_BORDER_NONE**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-105">**GX_STYLE_BORDER_NONE**</span></span>
  - <span data-ttu-id="fd3e9-106">Valor: 0x00000000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-106">Value: 0x00000000</span></span>
  - <span data-ttu-id="fd3e9-107">Descripción: use este estilo para dibujar un widget sin borde.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-107">Description: Use this style to draw a widget with no border.</span></span>

<span data-ttu-id="fd3e9-108">**GX_STYLE_BORDER_RAISED**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-108">**GX_STYLE_BORDER_RAISED**</span></span>
  - <span data-ttu-id="fd3e9-109">Valor: 0x00000001</span><span class="sxs-lookup"><span data-stu-id="fd3e9-109">Value: 0x00000001</span></span>
  - <span data-ttu-id="fd3e9-110">Descripción: dibuje un widget con un borde elevado.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-110">Description: Draw widget with a raised border.</span></span>

<span data-ttu-id="fd3e9-111">**GX_STYLE_BORDER_RECESSED**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-111">**GX_STYLE_BORDER_RECESSED**</span></span>
  - <span data-ttu-id="fd3e9-112">Valor: 0x00000002</span><span class="sxs-lookup"><span data-stu-id="fd3e9-112">Value: 0x00000002</span></span>
  - <span data-ttu-id="fd3e9-113">Descripción: dibuje un widget con un borde empotrado.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-113">Description: Draw widget with a recessed border.</span></span>

<span data-ttu-id="fd3e9-114">**GX_STYLE_BORDER_THIN**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-114">**GX_STYLE_BORDER_THIN**</span></span>
  - <span data-ttu-id="fd3e9-115">Valor: 0x00000004</span><span class="sxs-lookup"><span data-stu-id="fd3e9-115">Value: 0x00000004</span></span>
  - <span data-ttu-id="fd3e9-116">Descripción: dibuje un borde con un ancho de un píxel.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-116">Description: Draw a one-pixel width border.</span></span>

<span data-ttu-id="fd3e9-117">**GX_STYLE_BORDER_THICK**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-117">**GX_STYLE_BORDER_THICK**</span></span> 
  - <span data-ttu-id="fd3e9-118">Valor: 0x00000008</span><span class="sxs-lookup"><span data-stu-id="fd3e9-118">Value: 0x00000008</span></span>
  - <span data-ttu-id="fd3e9-119">Descripción: dibuje un widget con un borde grueso.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-119">Description: Draw widget with a thick border.</span></span>

<span data-ttu-id="fd3e9-120">**GX_STYLE_BORDER_MASK**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-120">**GX_STYLE_BORDER_MASK**</span></span>
  - <span data-ttu-id="fd3e9-121">Valor: 0x0000000f</span><span class="sxs-lookup"><span data-stu-id="fd3e9-121">Value: 0x0000000f</span></span>
  - <span data-ttu-id="fd3e9-122">Descripción: valor de máscara que se usa para probar solo los campos de estilo del miembro de estilo del widget.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-122">Description: Mask value used to test only the style fields of the widget style member.</span></span>

<span data-ttu-id="fd3e9-123">**GX_STYLE_TRANSPARENT**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-123">**GX_STYLE_TRANSPARENT**</span></span>
  - <span data-ttu-id="fd3e9-124">Valor: 0x10000000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-124">Value: 0x10000000</span></span>
  - <span data-ttu-id="fd3e9-125">Descripción: cree un widget que sea al menos parcialmente transparente.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-125">Description: Create a widget that is at least partially transparent.</span></span> <span data-ttu-id="fd3e9-126">Este estilo se debe usar cuando un widget no se dibuja totalmente opaco, incluidos los widgets que dibujan un mapa de píxeles semitransparente como fondo.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-126">This style should be used when a widget does not draw itself fully opaque, including widgets that draw a semi-transparent pixelmap as the widget background.</span></span> <span data-ttu-id="fd3e9-127">Esta marca de estilo informa a GUIX de que se debe dibujar el elemento primario del widget para actualizar su área de fondo.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-127">This style flag informs GUIX that the widget parent must be drawn to refresh the widget background area.</span></span>

<span data-ttu-id="fd3e9-128">**GX_STYLE_DRAW_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-128">**GX_STYLE_DRAW_SELECTED**</span></span>
  - <span data-ttu-id="fd3e9-129">Valor: 0x20000000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-129">Value: 0x20000000</span></span>
  - <span data-ttu-id="fd3e9-130">Descripción: especifique que el widget se debe dibujar con las fuentes y los colores de estado seleccionados.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-130">Description: Specify that the widget should be drawn using selected state colors and fonts.</span></span> <span data-ttu-id="fd3e9-131">La forma de usar el estilo DRAW_SELECTED para indicar que el widget está seleccionado varía en función del tipo de widget.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-131">Different widget types use the DRAW_SELECTED style in different ways to indicate the widget is currently selected.</span></span>

<span data-ttu-id="fd3e9-132">**GX_STYLE_ENABLED**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-132">**GX_STYLE_ENABLED**</span></span>
  - <span data-ttu-id="fd3e9-133">Valor: 0x40000000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-133">Value: 0x40000000</span></span>
  - <span data-ttu-id="fd3e9-134">Descripción: marque el widget como habilitado para que este pueda aceptar eventos de entrada de usuario y generar señales de salida.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-134">Description: Mark the widget as enabled, which allows the widget to accept user input events and generate output signals.</span></span>
  
<span data-ttu-id="fd3e9-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span></span>
  - <span data-ttu-id="fd3e9-136">Valor: 0x80000000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-136">Value: 0x80000000</span></span>
  - <span data-ttu-id="fd3e9-137">Descripción: indica que la memoria del bloque de control del widget se asigna dinámicamente mediante el servicio gx_system_memory_allocator cuando se crea el widget. La memoria se libera si se destruye el widget.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-137">Description: Indicates the widget control block memory is dynamically allocated using the gx_system_memory_allocator service when the widget is created, and the control block memory is freed if the widget is destroyed.</span></span>

<span data-ttu-id="fd3e9-138">**GX_STYLE_USE_LOCAL_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-138">**GX_STYLE_USE_LOCAL_ALPHA**</span></span>
  - <span data-ttu-id="fd3e9-139">Valor: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-139">Value: 0x01000000</span></span>
  - <span data-ttu-id="fd3e9-140">Descripción: indica a las funciones de dibujo de GUIX que usen el valor alfa del widget local al dibujar el widget.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-140">Description: Instructs GUIX drawing functions to use the local widget alpha value when drawing the widget.</span></span> <span data-ttu-id="fd3e9-141">La lógica interna de GUIX suele usar esta marca para implementar animaciones de difuminado del widget.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-141">This flag is normally used by the internal GUIX logic to implement widget fading animations.</span></span>


<span data-ttu-id="fd3e9-142">__***Estilos de alineación de texto (estilos aplicados a todos los widgets que dibujan texto):***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-142">__***Text Alignment Styles (styles applied to all widgets that draw text):***__</span></span>

<span data-ttu-id="fd3e9-143">**GX_STYLE_TEXT_LEFT**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-143">**GX_STYLE_TEXT_LEFT**</span></span>
  - <span data-ttu-id="fd3e9-144">Valor: 0x00001000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-144">Value: 0x00001000</span></span>
  - <span data-ttu-id="fd3e9-145">Descripción: el texto se dibuja alineado a la izquierda en el área cliente del widget.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-145">Description: Text is drawn left-aligned within the widget client area.</span></span>

<span data-ttu-id="fd3e9-146">**GX_STYLE_TEXT_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-146">**GX_STYLE_TEXT_RIGHT**</span></span> 
  - <span data-ttu-id="fd3e9-147">Valor: 0x00002000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-147">Value: 0x00002000</span></span>
  - <span data-ttu-id="fd3e9-148">Descripción: el texto se dibuja alineado a la derecha en el área cliente del widget.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-148">Description: Text is drawn right-aligned within the widget client area.</span></span>

<span data-ttu-id="fd3e9-149">**GX_STYLE_TEXT_CENTER**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-149">**GX_STYLE_TEXT_CENTER**</span></span>
  - <span data-ttu-id="fd3e9-150">Valor: 0x00004000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-150">Value: 0x00004000</span></span>
  - <span data-ttu-id="fd3e9-151">Descripción: el texto se dibuja centrado en el área cliente del widget.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-151">Description: Text is drawn center-aligned within the widget client area.</span></span>

<span data-ttu-id="fd3e9-152">**GX_STYLE_TEXT_COPY**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-152">**GX_STYLE_TEXT_COPY**</span></span>
  - <span data-ttu-id="fd3e9-153">Valor: 0x00008000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-153">Value: 0x00008000</span></span>
  - <span data-ttu-id="fd3e9-154">Descripción: de forma predeterminada, los widgets que dibujan texto conservan solo un puntero al texto que pasa la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-154">Description: By default, widgets that draw text keep only a pointer to the text which is passed in by the application.</span></span> <span data-ttu-id="fd3e9-155">En el caso de texto definido de forma estática que se especifique en la tabla de cadenas, no hay ningún motivo por el que el widget deba hacer una copia privada del texto asignado.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-155">For statically defined text that is defined within the string table, there is no reason for the widget to make a private copy of the text assigned.</span></span> <span data-ttu-id="fd3e9-156">Sin embargo, si el texto asignado a un widget se crea de forma dinámica con funciones como sprint() o gx_utility_ltoa, a menudo resulta conveniente indicar al widget que mantenga su propia copia privada de cualquier texto asignado.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-156">However, if the text assigned to a widget is created dynamically using functions like sprint() or gx_utility_ltoa, then it is often convenient to tell the widget to keep it’s own private copy of any text assigned.</span></span> <span data-ttu-id="fd3e9-157">De este modo, la aplicación puede usar variables automáticas o temporales al definir la cadena de texto en aquellos casos en los que, de lo contrario, tendría que especificar matrices de caracteres definidas estáticamente para cada widget de texto que use texto definido dinámicamente.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-157">This allows the application to use automatic or temporary variables when defining the text string, when the application would otherwise be required to define statically defined character arrays for each text widget that is using dynamically defined text.</span></span> <span data-ttu-id="fd3e9-158">Cuando se establezca esta marca de estilo, el widget utilizará la función gx_system_memory_allocator con el fin de asignar dinámicamente el bloque de memoria necesario para contener una copia privada de la cadena asignada.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-158">When this style flag is set, the widget will use the gx_system_memory_allocator function to dynamically allocate the memory block needed to hold a private copy of the assigned string.</span></span> <span data-ttu-id="fd3e9-159">Por lo tanto, el uso de esta marca de estilo se basa en la aplicación que define las funciones memory_allocator y memory_deallocator.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-159">Therefore using this style flag is predicated on the application defining memory_allocator and memory_deallocator functions.</span></span> <span data-ttu-id="fd3e9-160">GX_STYLE_TEXT_COPY no debe borrarse una vez que se haya establecido, ya que, de lo contrario, los resultados serán imprevisibles.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-160">GX_STYLE_TEXT_COPY should not be cleared after it has been set, and doing so will cause unpredictable results.</span></span>

<span data-ttu-id="fd3e9-161">__***Estilos de botón (solo se aplican a los tipos de widget de botón de GUIX):***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-161">__***Button Styles (apply only to GUIX button widget types):***__</span></span>

<span data-ttu-id="fd3e9-162">**GX_STYLE_BUTTON_PUSHED**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-162">**GX_STYLE_BUTTON_PUSHED**</span></span>
  - <span data-ttu-id="fd3e9-163">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="fd3e9-163">Value 0x00000010</span></span>
  - <span data-ttu-id="fd3e9-164">Descripción: indica que el botón está presionado o seleccionado.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-164">Description: Indicates the button is in the pushed or selected state.</span></span>

<span data-ttu-id="fd3e9-165">**GX_STYLE_BUTTON_TOGGLE**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-165">**GX_STYLE_BUTTON_TOGGLE**</span></span>
  - <span data-ttu-id="fd3e9-166">Valor: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="fd3e9-166">Value 0x00000020</span></span>
  - <span data-ttu-id="fd3e9-167">Descripción: el botón se presionará o dejará de estar presionado con cada evento de clic.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-167">Description: Button will switch status between pushed and unpushed on every click event.</span></span> <span data-ttu-id="fd3e9-168">Este estilo se suele usar con botones de tipo "casilla de verificación".</span><span class="sxs-lookup"><span data-stu-id="fd3e9-168">This style is commonly used with “checkbox” style buttons.</span></span>

<span data-ttu-id="fd3e9-169">**GX_STYLE_BUTTON_RADIO**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-169">**GX_STYLE_BUTTON_RADIO**</span></span>
  - <span data-ttu-id="fd3e9-170">Valor: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="fd3e9-170">Value 0x00000040</span></span>
  - <span data-ttu-id="fd3e9-171">Descripción: este estilo indica que el botón será exclusivo y anulará la selección de cualquier botón del mismo nivel cuando esté seleccionado.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-171">Description: This style indicates the button will be exclusive, and deselect any button siblings when selected.</span></span> <span data-ttu-id="fd3e9-172">Este estilo se suele usar con botones de tipo "botón de selección".</span><span class="sxs-lookup"><span data-stu-id="fd3e9-172">This style is commonly used with “radio button” style buttons.</span></span>

<span data-ttu-id="fd3e9-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span></span>
  - <span data-ttu-id="fd3e9-174">Valor: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="fd3e9-174">Value: 0x00000080</span></span>
  - <span data-ttu-id="fd3e9-175">Descripción: indica que el botón genera un evento de clic cuando se presiona por primera vez.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-175">Description: Indicates the button generates a click event when initially pushed.</span></span> <span data-ttu-id="fd3e9-176">La operación predeterminada es generar un evento de clic cuando se libera el botón.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-176">The default operation is to generate a click event when the button is released.</span></span>

<span data-ttu-id="fd3e9-177">**GX_STYLE_BUTTON_REPEAT**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-177">**GX_STYLE_BUTTON_REPEAT**</span></span>
  - <span data-ttu-id="fd3e9-178">Valor: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="fd3e9-178">Value 0x00000100</span></span>
  - <span data-ttu-id="fd3e9-179">Descripción: indica que el botón debe enviar eventos de clic repetidos al botón primario cuando aquel se mantiene presionado.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-179">Description: Indicates the button should send repeated click events to the button parent when the button is held in the pushed state.</span></span>

<span data-ttu-id="fd3e9-180">__***Estilos de lista (solo se aplican a los tipos de widget de lista de GUIX):***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-180">__***List Styles (apply only to GUIX list widget types):***__</span></span>

<span data-ttu-id="fd3e9-181">**GX_STYLE_CENTER_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-181">**GX_STYLE_CENTER_SELECTED**</span></span> 
  - <span data-ttu-id="fd3e9-182">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="fd3e9-182">Value: 0x00000010</span></span>
  - <span data-ttu-id="fd3e9-183">Descripción: reservado.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-183">Description: Reserved</span></span>

<span data-ttu-id="fd3e9-184">**GX_STYLE_WRAP**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-184">**GX_STYLE_WRAP**</span></span>
  - <span data-ttu-id="fd3e9-185">Valor: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="fd3e9-185">Value 0x00000020</span></span>
  - <span data-ttu-id="fd3e9-186">Descripción: los elementos secundarios de la lista se ajustan de principio a fin al arrastrar la lista o desplazarse más allá del índice de inicio o finalización de esta.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-186">Description: The list children wrap from start to end when the list is dragged or scrolled past the starting or ending list index.</span></span>

<span data-ttu-id="fd3e9-187">**GX_STYLE_FLICKABLE**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-187">**GX_STYLE_FLICKABLE**</span></span>
  - <span data-ttu-id="fd3e9-188">Valor: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="fd3e9-188">Value: 0x00000040</span></span>
  - <span data-ttu-id="fd3e9-189">Descripción: reservado.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-189">Description: Reserved</span></span>

<span data-ttu-id="fd3e9-190">__***Estilos de botón de mapa de píxeles e icono:***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-190">__***Pixelmap Button and Icon Button Styles:***__</span></span>

<span data-ttu-id="fd3e9-191">**GX_STYLE_HALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-191">**GX_STYLE_HALIGN_CENTER**</span></span>
  - <span data-ttu-id="fd3e9-192">Valor: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-192">Value: 0x00010000</span></span>
  - <span data-ttu-id="fd3e9-193">Descripción: el mapa de píxeles debe estar centrado dentro del límite del botón en el eje horizontal.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-193">Description: The button pixelmap should be center aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="fd3e9-194">**GX_STYLE_HALIGN_LEFT**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-194">**GX_STYLE_HALIGN_LEFT**</span></span>
  - <span data-ttu-id="fd3e9-195">Valor: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-195">Value: 0x00020000</span></span>
  - <span data-ttu-id="fd3e9-196">Descripción: el mapa de píxeles debe estar alineado a la izquierda dentro del límite del botón en el eje horizontal.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-196">Description: The button pixelmap should be left aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="fd3e9-197">**GX_STYLE_HALIGN_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-197">**GX_STYLE_HALIGN_RIGHT**</span></span>
  - <span data-ttu-id="fd3e9-198">Valor: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-198">Value 0x00040000</span></span>
  - <span data-ttu-id="fd3e9-199">Descripción: el mapa de píxeles debe estar alineado a la derecha dentro del límite del botón en el eje horizontal.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-199">Description: The button pixelmap should be right aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="fd3e9-200">**GX_STYLE_VALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-200">**GX_STYLE_VALIGN_CENTER**</span></span>
  - <span data-ttu-id="fd3e9-201">Valor: 0x00080000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-201">Value 0x00080000</span></span>
  - <span data-ttu-id="fd3e9-202">Descripción: el mapa de píxeles debe estar centrado dentro del límite del botón en el eje vertical.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-202">Description: The button pixelmap should be center aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="fd3e9-203">**GX_STYLE_VALIGN_TOP**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-203">**GX_STYLE_VALIGN_TOP**</span></span>
  - <span data-ttu-id="fd3e9-204">Valor: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-204">Value: 0x00100000</span></span>
  - <span data-ttu-id="fd3e9-205">Descripción: el mapa de píxeles debe estar alineado a la parte superior dentro del límite del botón en el eje vertical.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-205">Description: The button pixelmap should be top aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="fd3e9-206">**GX_STYLE_VALIGN_BOTTOM**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-206">**GX_STYLE_VALIGN_BOTTOM**</span></span>
  - <span data-ttu-id="fd3e9-207">Valor: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-207">Value: 0x00200000</span></span>
  - <span data-ttu-id="fd3e9-208">Descripción: el mapa de píxeles debe estar alineado a la parte inferior dentro del límite del botón en el eje horizontal.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-208">Description: The button pixelmap should be bottom aligned within the button boundary on the vertical horizontal axis.</span></span>

<span data-ttu-id="fd3e9-209">__***Estilos de control deslizante (solo se aplican a los tipos de widget derivados y GX_SLIDER):***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-209">__***Slider Styles (Appy only to GX_SLIDER and derived widget types):***__</span></span>

<span data-ttu-id="fd3e9-210">**GX_STYLE_SHOW_NEEDLE**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-210">**GX_STYLE_SHOW_NEEDLE**</span></span>
  - <span data-ttu-id="fd3e9-211">Valor: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="fd3e9-211">Value: 0x00000200</span></span>
  - <span data-ttu-id="fd3e9-212">Descripción: este estilo debe estar incluido para que el control deslizante dibuje el indicador de aguja.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-212">Description: This style must be included for the slider to draw the needle indicator.</span></span> <span data-ttu-id="fd3e9-213">Este estilo se puede deshabilitar si la aplicación quiere deshabilitar la aguja del control deslizante o dibujar un indicador de aguja personalizado.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-213">This style can be disabled if the application wants to disable the slider needle or draw a custom needle indicator.</span></span>

<span data-ttu-id="fd3e9-214">**GX_STYLE_SHOW_TICKMARKS**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-214">**GX_STYLE_SHOW_TICKMARKS**</span></span>
  - <span data-ttu-id="fd3e9-215">Valor: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="fd3e9-215">Value: 0x00000400</span></span>
  - <span data-ttu-id="fd3e9-216">Descripción: cuando este estilo está habilitado, el widget de control deslizante dibuja mediante software las líneas discontinuas de marca de graduación.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-216">Description: The slider widget will do software drawing of dashed tickmark lines when this style is enabled.</span></span>

<span data-ttu-id="fd3e9-217">**GX_STYLE_SLIDER_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-217">**GX_STYLE_SLIDER_VERTICAL**</span></span>
  - <span data-ttu-id="fd3e9-218">Valor: 0x00000800</span><span class="sxs-lookup"><span data-stu-id="fd3e9-218">Value 0x00000800</span></span>
  - <span data-ttu-id="fd3e9-219">Descripción: establezca esta marca de estilo para crear un control deslizante vertical o bórrela para crear uno horizontal.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-219">Description: Set this style flag to create a vertical slider, and clear this style flag to create a horizontal slider.</span></span>

<span data-ttu-id="fd3e9-220">__***Estilos de sprite (solo se aplican a los tipos de widget GX_SPRITE):***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-220">__***Sprite Styles (Applies only to GX_SPRITE widget types):***__</span></span>

<span data-ttu-id="fd3e9-221">**GX_STYLE_SPRITE_AUTO**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-221">**GX_STYLE_SPRITE_AUTO**</span></span>
  - <span data-ttu-id="fd3e9-222">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="fd3e9-222">Value: 0x00000010</span></span>
  - <span data-ttu-id="fd3e9-223">Descripción: indica que la animación de sprite se ejecutará automáticamente cuando el widget de sprite haya recibido el evento GX_EVENT_SHOW.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-223">Description: Indicates the sprite animation will run automatically when the sprite widget received the GX_EVENT_SHOW event.</span></span>

<span data-ttu-id="fd3e9-224">**GX_STYLE_SPRITE_LOOP**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-224">**GX_STYLE_SPRITE_LOOP**</span></span>
  - <span data-ttu-id="fd3e9-225">Valor: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="fd3e9-225">Value: 0x00000020</span></span>
  - <span data-ttu-id="fd3e9-226">Descripción: con este estilo, el widget de sprite recorrerá continuamente en bucle los fotogramas de animación de sprite hasta que la aplicación detenga el sprite.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-226">Description: With this style, the sprite widget will continuously loop through sprite animation frames until the sprite is stopped by the application.</span></span>

<span data-ttu-id="fd3e9-227">__***Estilos de control deslizante de mapa de píxeles:***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-227">__***Pixelmap Slider Styles:***__</span></span>

<span data-ttu-id="fd3e9-228">**GX_STYLE_TILE_BACKGROUND**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-228">**GX_STYLE_TILE_BACKGROUND**</span></span>
  - <span data-ttu-id="fd3e9-229">Valor: 0x00001000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-229">Value 0x00001000</span></span>
  - <span data-ttu-id="fd3e9-230">Descripción: la imagen de fondo del control deslizante se coloca en mosaico para rellenar el rectángulo delimitador del sprite.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-230">Description: The slider background image is tiled to fill the sprite bounding rectangle.</span></span> <span data-ttu-id="fd3e9-231">De este modo, se puede usar una pequeña imagen de franjas verticales u horizontales para rellenar el fondo del control deslizante.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-231">This allows a small vertical or horizontal stripe image to be used to fill the slider background.</span></span>

<span data-ttu-id="fd3e9-232">__***Otros estilos de barra de progreso:***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-232">__***Additional Progress Bar Styles:***__</span></span>

<span data-ttu-id="fd3e9-233">**GX_STYLE_PROGRESS_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-233">**GX_STYLE_PROGRESS_PERCENT**</span></span>
  - <span data-ttu-id="fd3e9-234">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="fd3e9-234">Value: 0x00000010</span></span>
  - <span data-ttu-id="fd3e9-235">Descripción: cuando se establece este estilo, la barra de progreso dibuja su valor como porcentaje, no como valor sin formato.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-235">Description: When this style is set, the progress bar will draw  bar value as a percentage rather than a raw value.</span></span> <span data-ttu-id="fd3e9-236">El texto se centra en el rectángulo delimitador de la barra de progreso.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-236">The text is centered in the progress bar bounding rectangle.</span></span>

<span data-ttu-id="fd3e9-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span></span>
  - <span data-ttu-id="fd3e9-238">Valor: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="fd3e9-238">Value: 0x00000020</span></span>
  - <span data-ttu-id="fd3e9-239">Descripción: dibuje el valor de la barra de progreso actual como texto decimal centrado en la barra.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-239">Description: Draw the current progress bar value as decimal text centered within the progress bar.</span></span>

<span data-ttu-id="fd3e9-240">**GX_STYLE_PROGRESS_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-240">**GX_STYLE_PROGRESS_VERTICAL**</span></span>
  - <span data-ttu-id="fd3e9-241">Valor: 0x0000040</span><span class="sxs-lookup"><span data-stu-id="fd3e9-241">Value: 0x0000040</span></span>
  - <span data-ttu-id="fd3e9-242">Descripción: indica que el progreso está orientado verticalmente.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-242">Description: Indicate the progress is vertically oriented.</span></span> <span data-ttu-id="fd3e9-243">La orientación es horizontal de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-243">The default is horizontal orientation.</span></span>

<span data-ttu-id="fd3e9-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span><span class="sxs-lookup"><span data-stu-id="fd3e9-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span></span>
  - <span data-ttu-id="fd3e9-245">**Valor**: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="fd3e9-245">**Value**: 0x00000100</span></span>
  - <span data-ttu-id="fd3e9-246">Descripción: el valor de la barra de progreso se indica mediante rectángulos rellenos segmentados, no mediante un relleno sólido.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-246">Description: The progress bar value is indicated with segmented filled rectangles, rather than a solid fill.</span></span>

<span data-ttu-id="fd3e9-247">__***Otros estilos de barra de progreso radial:***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-247">__***Additional Radial Progress Bar Styles:***__</span></span>

<span data-ttu-id="fd3e9-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span></span>
  - <span data-ttu-id="fd3e9-249">Valor: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="fd3e9-249">Value: 0x00000200</span></span>
  - <span data-ttu-id="fd3e9-250">Descripción: dibuje la barra de progreso radial con estilos de pincel suavizados.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-250">Description: Draw the radial progress bar using anti-aliased brush styles.</span></span> <span data-ttu-id="fd3e9-251">Para ello, hace falta más ancho de banda de CPU, pero el resultado es también una apariencia más agradable.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-251">This requires more CPU bandwidth but also produces a nicer appearance.</span></span> <span data-ttu-id="fd3e9-252">En el caso de destinos de CPU de menor rendimiento, si se borra esta marca de estilo, el resultado será una velocidad de dibujo mayor.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-252">For lower performance CPU targets, clearing this style flag will result in faster drawing speed.</span></span>

<span data-ttu-id="fd3e9-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span></span>
  - <span data-ttu-id="fd3e9-254">Valor: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="fd3e9-254">Value: 0x00000400</span></span>
  - <span data-ttu-id="fd3e9-255">Descripción: use un estilo de pincel de extremo de línea redondo al dibujar el arco de la barra de progreso radial. El extremo de línea es cuadrado de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-255">Description: Use a round line end brush style when drawing the radial progress bar arc. The default is a square line end.</span></span>

<span data-ttu-id="fd3e9-256">__***Otros estilos de entrada de texto:***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-256">__***Additional Text Input Styles:***__</span></span>

<span data-ttu-id="fd3e9-257">**GX_STYLE_CURSOR_BLINK**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-257">**GX_STYLE_ CURSOR_BLINK**</span></span>
  - <span data-ttu-id="fd3e9-258">Valor: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="fd3e9-258">Value: 0x00000040</span></span>
  - <span data-ttu-id="fd3e9-259">Descripción: el cursor del widget de entrada de texto parpadeará en lugar de permanecer estable.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-259">Description: The text input widget cursor will flash on and off rather than being steady.</span></span>

<span data-ttu-id="fd3e9-260">**GX_STYLE_CURSOR_ALWAYS**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-260">**GX_STYLE_ CURSOR_ALWAYS**</span></span>
  - <span data-ttu-id="fd3e9-261">Valor: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="fd3e9-261">Value: 0x00000080</span></span>
  - <span data-ttu-id="fd3e9-262">Descripción.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-262">Description.</span></span> <span data-ttu-id="fd3e9-263">Normalmente, el cursor del widget de entrada de texto solo se muestra cuando el widget tiene el foco de entrada.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-263">The text input widget cursor is normally only displayed when the widget owns input focus.</span></span> <span data-ttu-id="fd3e9-264">Esta marca de estilo hará que el cursor esté siempre visible independientemente del foco de entrada.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-264">This style flag will make the cursor always visible regardless of input focus.</span></span>

<span data-ttu-id="fd3e9-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span></span>
  - <span data-ttu-id="fd3e9-266">Valor: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="fd3e9-266">Value: 0x00000100</span></span>
  - <span data-ttu-id="fd3e9-267">Descripción: use esta marca de estilo para establecer el evento GX_EVENT_TEXT_EDITED cada vez que el widget de entrada de texto reciba el evento de presión de tecla.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-267">Description: With this style flag set the GX_EVENT_TEXT_EDITED event every time key down event is received by the text input widget.</span></span>

<span data-ttu-id="fd3e9-268">__***Otros estilos de ventana:***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-268">__***Additional Window Styles:***__</span></span>

<span data-ttu-id="fd3e9-269">**GX_STYLE_TILE_WALLPAPER**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-269">**GX_STYLE_TILE_WALLPAPER**</span></span>
  - <span data-ttu-id="fd3e9-270">Valor: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-270">Value: 0x00040000</span></span>
  - <span data-ttu-id="fd3e9-271">Descripción: la ventana colocará en mosaico cualquier imagen de fondo de pantalla asignada para rellenar el rectángulo cliente de la ventana.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-271">Description: The window will tile any assigned wallpaper image to fill the window client rectangle.</span></span>

<span data-ttu-id="fd3e9-272">**GX_STYLE_AUTO_HSCROLL**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-272">**GX_STYLE_AUTO_HSCROLL**</span></span>
  - <span data-ttu-id="fd3e9-273">Valor: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-273">Value: 0x00100000</span></span>
  - <span data-ttu-id="fd3e9-274">Descripción: reservado para su uso futuro.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-274">Description: Reserved for future use.</span></span>

<span data-ttu-id="fd3e9-275">**GX_STYLE_AUTO_VSCROLL**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-275">**GX_STYLE_AUTO_VSCROLL**</span></span>
  - <span data-ttu-id="fd3e9-276">Valor: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-276">Value: 0x00200000</span></span>
  - <span data-ttu-id="fd3e9-277">Descripción: reservado para su uso futuro.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-277">Description: Reserved for future use.</span></span>

<span data-ttu-id="fd3e9-278">__***Otros estilos de menú:***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-278">__***Additional Menu Styles:***__</span></span>

<span data-ttu-id="fd3e9-279">**GX_STYLE_MENU_EXPANDED**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-279">**GX_STYLE_MENU_EXPANDED**</span></span>
  - <span data-ttu-id="fd3e9-280">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="fd3e9-280">Value: 0x00000010</span></span>
  - <span data-ttu-id="fd3e9-281">Descripción: el widget de menú de acordeón está inicialmente expandido.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-281">Description: Accordion menu widget is initially in expanded state.</span></span>

<span data-ttu-id="fd3e9-282">__***Otros estilos de vista de árbol:***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-282">__***Additional Tree View Styles:***__</span></span>

<span data-ttu-id="fd3e9-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span></span>
  - <span data-ttu-id="fd3e9-284">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="fd3e9-284">Value: 0x00000010</span></span>
  - <span data-ttu-id="fd3e9-285">Descripción: el widget de vista de árbol debe dibujar líneas desde el icono de nodo hasta el nodo raíz del árbol.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-285">Description: Tree view widget should draw lines from node icon to root tree node.</span></span>

<span data-ttu-id="fd3e9-286">__***Otros estilos de barra de desplazamiento:***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-286">__***Additional Scrollbar Styles:***__</span></span>

<span data-ttu-id="fd3e9-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span></span>
  - <span data-ttu-id="fd3e9-288">Valor: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-288">Value: 0x00010000</span></span>
  - <span data-ttu-id="fd3e9-289">Descripción: reservado para su uso futuro.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-289">Description: Reserved for future use.</span></span>

<span data-ttu-id="fd3e9-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span></span>
  - <span data-ttu-id="fd3e9-291">Valor: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-291">Value: 0x00020000</span></span>
  - <span data-ttu-id="fd3e9-292">Descripción: el ancho (en el caso de una barra de desplazamiento horizontal) o el alto (en el caso de una barra de desplazamiento vertical) del control de la barra de desplazamiento se calculan en función de la relación entre el área visible de la ventana primaria y el intervalo mínimo y máximo de la barra.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-292">Description: The scrollbar thumb width (for a horizontal scroll bar) or height (for a vertical scroll bar) are calculated based on the ratio of the visible area of the parent window to the min and max scrollbar range.</span></span>

<span data-ttu-id="fd3e9-293">**GX_SCROLLBAR_END_BUTTONS**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-293">**GX_SCROLLBAR_END_BUTTONS**</span></span>
  - <span data-ttu-id="fd3e9-294">Valor: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-294">Value: 0x00040000</span></span>
  - <span data-ttu-id="fd3e9-295">Descripción: la barra de desplazamiento crea y agrega automáticamente botones en cada extremo de la región de la barra.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-295">Description: The scrollbar automatically creates and attaches buttons at each end of the scrollbar region.</span></span>

<span data-ttu-id="fd3e9-296">**GX_SCROLLBAR_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-296">**GX_SCROLLBAR_VERTICAL**</span></span> 
  - <span data-ttu-id="fd3e9-297">Valor: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-297">Value: 0x01000000</span></span>
  - <span data-ttu-id="fd3e9-298">Descripción: la barra de desplazamiento está orientada verticalmente.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-298">Description: The scrollbar is vertically oriented.</span></span>

<span data-ttu-id="fd3e9-299">**GX_SCROLLBAR_HORIZONTAL**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-299">**GX_SCROLLBAR_HORIZONTAL**</span></span>
  - <span data-ttu-id="fd3e9-300">Valor: 0x02000000</span><span class="sxs-lookup"><span data-stu-id="fd3e9-300">Value: 0x02000000</span></span>
  - <span data-ttu-id="fd3e9-301">Descripción: la barra de desplazamiento está orientada horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-301">Description: The scrollbar is horizontally oriented.</span></span>

<span data-ttu-id="fd3e9-302">__***Estilos de rueda de desplazamiento de texto:***__</span><span class="sxs-lookup"><span data-stu-id="fd3e9-302">__***Text Scroll Wheel Styles:***__</span></span>

<span data-ttu-id="fd3e9-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span><span class="sxs-lookup"><span data-stu-id="fd3e9-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span></span>
  - <span data-ttu-id="fd3e9-304">Valor: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="fd3e9-304">Value: 0x00000200</span></span>
  - <span data-ttu-id="fd3e9-305">Descripción: la rueda de desplazamiento usa un algoritmo sinusoidal para que parezca que tiene una forma redondeada.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-305">Description: The scroll wheel uses a Sinusoidal algorithm to make the scroll wheel appear to have a rounded shape.</span></span> <span data-ttu-id="fd3e9-306">Esta marca de estilo puede suponer una sobrecarga considerable para el rendimiento del widget de rueda de desplazamiento, pero también puede dar a la rueda una apariencia 3D realista.</span><span class="sxs-lookup"><span data-stu-id="fd3e9-306">This style flag can add significant overhead to the performance of the scroll wheel widget, but can also give the wheel a 3D realistic appearance.</span></span>