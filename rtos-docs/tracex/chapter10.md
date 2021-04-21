---
title: 'Capítulo 10: Eventos de usuario de cliente'
description: En este capítulo se incluye una descripción de cómo crear eventos definidos por el usuario, iconos personalizados y campos de información para dichos eventos.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 635c2d79922de9d5649bab841ae946cac862056c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815790"
---
# <a name="chapter-10---customer-user-events"></a><span data-ttu-id="66076-103">Capítulo 10: Eventos de usuario de cliente</span><span class="sxs-lookup"><span data-stu-id="66076-103">Chapter 10 - Customer user events</span></span>

<span data-ttu-id="66076-104">En este capítulo se incluye una descripción de cómo crear eventos definidos por el usuario, iconos personalizados y campos de información para dichos eventos.</span><span class="sxs-lookup"><span data-stu-id="66076-104">This chapter contains a description of how to create user-defined events and custom icons and information fields for such events.</span></span> <span data-ttu-id="66076-105">En este capítulo se incluyen las secciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="66076-105">This chapter includes the following sections:</span></span> 

## <a name="inserting-user-defined-events"></a><span data-ttu-id="66076-106">Inserción de eventos definidos por el usuario</span><span class="sxs-lookup"><span data-stu-id="66076-106">Inserting User-Defined Events</span></span>

<span data-ttu-id="66076-107">ThreadX ofrece la posibilidad de que los desarrolladores registren sus propios eventos definidos por el usuario, proporcionando información aún más útil que se puede ver gráficamente mediante TraceX.</span><span class="sxs-lookup"><span data-stu-id="66076-107">ThreadX provides the ability for developers to log their own user-defined events, providing even more useful information that can be viewed graphically by TraceX.</span></span> <span data-ttu-id="66076-108">Los números de eventos definidos por el usuario oscilan entre</span><span class="sxs-lookup"><span data-stu-id="66076-108">User-defined event numbers range from</span></span>

<span data-ttu-id="66076-109">**TX_TRACE_USER_EVENT_START** (4096) y **TX_TRACE_USER_EVENT_END** (65535), ambos incluidos.</span><span class="sxs-lookup"><span data-stu-id="66076-109">**TX_TRACE_USER_EVENT_START** (4096) through **TX_TRACE_USER_EVENT_END** (65535), inclusive.</span></span> <span data-ttu-id="66076-110">La colocación de los eventos en el búfer de seguimiento se realiza mediante ***tx_trace_user_event_insert***, que se define en el capítulo 5.</span><span class="sxs-lookup"><span data-stu-id="66076-110">The placement of the events in the trace buffer is done via the ***tx_trace_user_event_insert***, defined in Chapter 5.</span></span> <span data-ttu-id="66076-111">Las llamadas de ejemplo siguientes insertan dos eventos definidos por el usuario en el búfer de seguimiento actual, en concreto el evento definido por el usuario 4096 y el evento definido por el usuario 4098:</span><span class="sxs-lookup"><span data-stu-id="66076-111">The following example calls insert two user-defined events into the current trace buffer on the target, namely user-defined event 4096 and event 4098:</span></span>

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a><span data-ttu-id="66076-112">Visualización predeterminada de eventos definidos por el usuario</span><span class="sxs-lookup"><span data-stu-id="66076-112">Default Display of User-Defined Events</span></span>

![Icono de evento definido por el usuario](./media/user-guide/tx-events/image0.png)

<span data-ttu-id="66076-114">De forma predeterminada, TraceX muestra todos los eventos de usuario con un icono de evento definido por el usuario predeterminado, como se describe en el capítulo 6.</span><span class="sxs-lookup"><span data-stu-id="66076-114">By default, TraceX displays all user events with a default user-defined Event icon as described in Chapter 6.</span></span> <span data-ttu-id="66076-115">La figura 28 muestra el icono de evento predeterminado definido por el usuario para los eventos 452 y 453, que se colocaron en el búfer de eventos mediante los ejemplos de ***tx_trace_user_event_insert*** anteriores.</span><span class="sxs-lookup"><span data-stu-id="66076-115">Figure 28 shows the default user-defined event icon for events 452 and 453, which were placed in the event buffer via the previous ***tx_trace_user_event_insert*** examples.</span></span>

<span data-ttu-id="66076-116">![Captura de pantalla de la visualización predeterminada de eventos definidos por el usuario.](./media/user-guide/10.1.png)
**FIGURA 28**</span><span class="sxs-lookup"><span data-stu-id="66076-116">![Screenshot of the default display of user-defined events.](./media/user-guide/10.1.png)
**FIGURE 28**</span></span>

<span data-ttu-id="66076-117">También hay información detallada disponible para los eventos definidos por el usuario.</span><span class="sxs-lookup"><span data-stu-id="66076-117">Detailed information is also available for user-defined Events.</span></span> <span data-ttu-id="66076-118">La figura 28 muestra la información detallada de eventos del evento 452, que tiene el número de evento 4096 y muestra los cuatro campos de información especificados.</span><span class="sxs-lookup"><span data-stu-id="66076-118">Figure 28 shows the detailed event information for event 452, which has event number 4096 and shows the specified four information fields.</span></span>

<span data-ttu-id="66076-119">![Captura de pantalla de la visualización detallada de eventos definidos por el usuario.](./media/user-guide/10.2.png)
**FIGURA 29**</span><span class="sxs-lookup"><span data-stu-id="66076-119">![Screenshot of the detailed display of user-defined events.](./media/user-guide/10.2.png)
**FIGURE 29**</span></span>

## <a name="defining-custom-user-defined-event-icons"></a><span data-ttu-id="66076-120">Definición de iconos de eventos definidos por el usuario personalizados</span><span class="sxs-lookup"><span data-stu-id="66076-120">Defining Custom User-Defined Event Icons</span></span>

<span data-ttu-id="66076-121">TraceX también proporciona al usuario la capacidad de crear iconos de eventos personalizados definidos por el usuario y etiquetas de campo de información personalizadas.</span><span class="sxs-lookup"><span data-stu-id="66076-121">TraceX also provides the user the ability to create custom user-defined event icons and custom information field labels.</span></span> <span data-ttu-id="66076-122">Esta capacidad se consigue agregando especificaciones de icono de evento al archivo de configuración \***tracex_custom.trxc** _.</span><span class="sxs-lookup"><span data-stu-id="66076-122">This capability is achieved by adding event icon specifications to the \***tracex_custom.trxc** _ configuration file.</span></span> <span data-ttu-id="66076-123">Este archivo se encuentra en el subdirectorio _ *_CustomEvents_*\* del directorio de instalación de TraceX definido por el usuario, que por defecto es c:\Azure_RTOS\TraceX.</span><span class="sxs-lookup"><span data-stu-id="66076-123">This file is located in the _ *_CustomEvents_*\* subdirectory of your user-defined TraceX installation directory, which defaults to c:\Azure_RTOS\TraceX.</span></span> <span data-ttu-id="66076-124">En la figura 30 se muestra una ruta de acceso al directorio de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="66076-124">An example directory path is shown in Figure 30.</span></span>

<span data-ttu-id="66076-125">![Captura de pantalla de una ruta de acceso al directorio de ejemplo.](./media/user-guide/custom_events_folder.png)
**FIGURA 30**</span><span class="sxs-lookup"><span data-stu-id="66076-125">![Screenshot of an example directory path.](./media/user-guide/custom_events_folder.png)
**FIGURE 30**</span></span>

<span data-ttu-id="66076-126">El archivo de configuración de eventos personalizado ***tracex_custom.trxc*** es un simple archivo de texto ASCII que contiene cero o más definiciones de eventos personalizados.</span><span class="sxs-lookup"><span data-stu-id="66076-126">The ***tracex_custom.trxc*** custom event configuration file is a simple ASCII text file containing zero or more custom event definitions.</span></span> <span data-ttu-id="66076-127">El formato del archivo es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="66076-127">The format of the file is as follows:</span></span>

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

<span data-ttu-id="66076-128">Cada línea entre Start y End se usa para definir un único evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="66076-128">Each line between Start and End is used to define a single custom event.</span></span> <span data-ttu-id="66076-129">TraceX proporciona una versión de plantilla de este archivo sin eventos personalizados definidos (nada entre las etiquetas "Start" y "End").</span><span class="sxs-lookup"><span data-stu-id="66076-129">TraceX provides a template version of this file with no custom events defined (nothing between the "Start" and "End" labels).</span></span> <span data-ttu-id="66076-130">El formato de una definición de evento personalizado es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="66076-130">The format of a custom event definition is as follows:</span></span>

<span data-ttu-id="66076-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span><span class="sxs-lookup"><span data-stu-id="66076-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span></span>

<span data-ttu-id="66076-132">donde:</span><span class="sxs-lookup"><span data-stu-id="66076-132">where:</span></span>

- <span data-ttu-id="66076-133">number: define el número de evento definido por el usuario, entre 4096 y 65535, ambos incluidos.</span><span class="sxs-lookup"><span data-stu-id="66076-133">number: Defines the user-defined event number, between 4096 and 65535, inclusive.</span></span></th>
- <span data-ttu-id="66076-134">name: define el nombre lógico para el evento definido por el usuario.</span><span class="sxs-lookup"><span data-stu-id="66076-134">name: Defines the logical name for the user-defined event.</span></span></td>
- <span data-ttu-id="66076-135">abbreviation: define la abreviatura de eventos definidos por el usuario de dos letras.</span><span class="sxs-lookup"><span data-stu-id="66076-135">abbreviation: Defines the two-letter user-defined event abbreviation.</span></span></td>
- <span data-ttu-id="66076-136">top_color: define el valor RGB de la mitad superior del icono, que es un número de tres dígitos entre paréntesis.</span><span class="sxs-lookup"><span data-stu-id="66076-136">top_color: Defines the RGB value for the top-half of the icon, which is a three-digit number in parenthesis.</span></span> <span data-ttu-id="66076-137">Algunas definiciones RGB típicas son</span><span class="sxs-lookup"><span data-stu-id="66076-137">Some typical RGB definitions are</span></span>
  - <span data-ttu-id="66076-138">NEGRO = (0,0,0)</span><span class="sxs-lookup"><span data-stu-id="66076-138">BLACK = (0,0,0)</span></span>       
  - <span data-ttu-id="66076-139">BLANCO = (255,255,255)</span><span class="sxs-lookup"><span data-stu-id="66076-139">WHITE = (255,255,255)</span></span>
  - <span data-ttu-id="66076-140">ROJO = (255,0,0)</span><span class="sxs-lookup"><span data-stu-id="66076-140">RED = (255,0,0)</span></span>     
  - <span data-ttu-id="66076-141">VERDE = (0,255,0)</span><span class="sxs-lookup"><span data-stu-id="66076-141">GREEN = (0,255,0)</span></span>     
  - <span data-ttu-id="66076-142">AZUL = (0,0,255)</span><span class="sxs-lookup"><span data-stu-id="66076-142">BLUE = (0,0,255)</span></span>     
  - <span data-ttu-id="66076-143">AMARILLO = (255,255,0)</span><span class="sxs-lookup"><span data-stu-id="66076-143">YELLOW = (255,255,0)</span></span>   
  - <span data-ttu-id="66076-144">CIAN = (0,255,255)</span><span class="sxs-lookup"><span data-stu-id="66076-144">CYAN = (0,255,255)</span></span>   
  - <span data-ttu-id="66076-145">MAGENTA = (255,0,255)</span><span class="sxs-lookup"><span data-stu-id="66076-145">MAGENTA = (255,0,255)</span></span>   
  <span data-ttu-id="66076-146">El uso de la especificación RBG proporciona al usuario una amplia gama de colores para cada icono definido por el usuario.</span><span class="sxs-lookup"><span data-stu-id="66076-146">Using the RBG specification gives the user a broad range of colors for each user-defined icon.</span></span> <span data-ttu-id="66076-147">Para obtener más información sobre la definición de color RBG, consulte: https://en.wikipedia.org/wiki/RGB#Digital_representations</span><span class="sxs-lookup"><span data-stu-id="66076-147">For more information on RBG color definition, see: https://en.wikipedia.org/wiki/RGB#Digital_representations</span></span>
- <span data-ttu-id="66076-148">bottom_color: define el valor RGB de la mitad inferior del icono, que es un número de tres dígitos entre paréntesis.</span><span class="sxs-lookup"><span data-stu-id="66076-148">botton_color: Defines the RGB value for the bottom half of the icon, which is a three-digit number in parenthesis.</span></span>
- <span data-ttu-id="66076-149">label1: etiqueta para \***info_field_1** _, como se especifica en la llamada _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="66076-149">label1: Label for ***info_field_1** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="66076-150">label2: etiqueta para \***info_field_2** _, como se especifica en la llamada _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="66076-150">label2: Label for ***info_field_2** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="66076-151">label3: etiqueta para \***info_field_3** _, como se especifica en la llamada _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="66076-151">label3: Label for ***info_field_3** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="66076-152">label4: etiqueta para \***info_field_4** _, como se especifica en la llamada _ \*_tx_trace_user_event_insert_\*\*.</span><span class="sxs-lookup"><span data-stu-id="66076-152">label4: Label for ***info_field_4** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>

<span data-ttu-id="66076-153">En la figura 10.4 se muestran definiciones de ejemplo para cada uno de los dos eventos definidos por el usuario que se usan en este capítulo.</span><span class="sxs-lookup"><span data-stu-id="66076-153">Example definitions for each of the two user-defined events used in this chapter are shown in Figure 10.4.</span></span> <span data-ttu-id="66076-154">La primera definición es para el evento 4096 de la línea 5 del archivo \***tracex_custom.trxc** _.</span><span class="sxs-lookup"><span data-stu-id="66076-154">The first definition is for event 4096 at line 5 of the \***tracex_custom.trxc** _ file.</span></span> <span data-ttu-id="66076-155">Esta definición proporciona al evento 4096 definido por el usuario el nombre _\*First_User_Event\*\*, especifica la abreviatura de dos letras **FE**, hace que la parte superior del icono sea roja, la parte inferior del icono verde y asigna a los campos de información los nombres **First_Info1**, **First_Info2**, **First_Info3** y **First_Info4**.</span><span class="sxs-lookup"><span data-stu-id="66076-155">This definition gives user-defined event 4096 the name _\*First_User_Event\*\*, specifies a two-letter abbreviation of **FE**, makes the top portion of the icon red, the bottom portion of the icon green, and names the information fields as **First_Info1**, **First_Info2**, **First_Info3**, and **First_Info4**.</span></span> <span data-ttu-id="66076-156">El evento 4098 definido por el usuario se define de forma similar en la línea 6 de **_tracex_custom.trxc_**.</span><span class="sxs-lookup"><span data-stu-id="66076-156">User-defined event 4098 is defined similarly at line 6 of **_tracex_custom.trxc_**.</span></span>

<span data-ttu-id="66076-157">![Captura de pantalla de las definiciones de ejemplo para los eventos definidos por el usuario.](./media/user-guide/10.4.png)
**FIGURA 31**</span><span class="sxs-lookup"><span data-stu-id="66076-157">![Screenshot of the example definitions for the user-defined events.](./media/user-guide/10.4.png)
**FIGURE 31**</span></span>

<span data-ttu-id="66076-158">Dado que TraceX lee el archivo \***tracex_custom.trxc** _ durante la inicialización, TraceX se debe cerrar y reiniciar para que las definiciones de iconos personalizados surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="66076-158">Since the \***tracex_custom.trxc** _ file is read by TraceX during initialization, TraceX must be exited and restarted before the custom icon definitions can take effect.</span></span> <span data-ttu-id="66076-159">En la figura 32 se muestra la pantalla de TraceX de los eventos definidos por el usuario 452 y 453 con los iconos de eventos personalizados definidos en _\*_tracex_custom.trxc_\*\*.</span><span class="sxs-lookup"><span data-stu-id="66076-159">Figure 32 shows the TraceX display of user-defined events 452 and 453 with the custom event icons defined in _\*_tracex_custom.trxc_\*\*.</span></span>

<span data-ttu-id="66076-160">![Captura de pantalla de la pantalla de TraceX de loa eventos definidos por el usuario con los iconos de eventos personalizados.](./media/user-guide/10.5.png)
**FIGURA 32**</span><span class="sxs-lookup"><span data-stu-id="66076-160">![Screenshot of the TraceX display of user defined events with the custom event icons.](./media/user-guide/10.5.png)
**FIGURE 32**</span></span>

<span data-ttu-id="66076-161">La información adicional en la definición de evento personalizado se muestra cuando se selecciona un evento con un doble clic, al pasar el puntero del mouse o al hacer clic en el botón del evento actual.</span><span class="sxs-lookup"><span data-stu-id="66076-161">The additional information in the custom event definition is shown when the event you select using a double-click, mouse-over, or clicking the current event button.</span></span> <span data-ttu-id="66076-162">En la figura 33 se muestra la selección de doble clic en el evento 452.</span><span class="sxs-lookup"><span data-stu-id="66076-162">Figure 33 shows the double-click selection on event 452.</span></span> <span data-ttu-id="66076-163">Todos los campos de información y el nombre de evento coinciden con la definición de ejemplo que se agregó a ***tracex_custom.trxc***.</span><span class="sxs-lookup"><span data-stu-id="66076-163">The event name and information fields all match the sample definition that was added to ***tracex_custom.trxc***.</span></span>

<span data-ttu-id="66076-164">![Captura de pantalla de la selección de doble clic en un evento.](./media/user-guide/10.6.png)
**FIGURA 33**</span><span class="sxs-lookup"><span data-stu-id="66076-164">![Screenshot of the double-click selection on an event.](./media/user-guide/10.6.png)
**FIGURE 33**</span></span>
