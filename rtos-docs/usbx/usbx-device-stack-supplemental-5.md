---
title: 'Capítulo 5: USBX OTG'
description: Obtenga información sobre la compatibilidad de USBX con las funcionalidades del OTG USB cuando hay una controladora USB compatible con el OTG disponible en el diseño del hardware.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 64a3c44f84b9ffca31d9e616d14d3d5d87c56bd7
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550327"
---
# <a name="chapter-5---usbx-otg"></a><span data-ttu-id="cf025-103">Capítulo 5: USBX OTG</span><span class="sxs-lookup"><span data-stu-id="cf025-103">Chapter 5 - USBX OTG</span></span>

<span data-ttu-id="cf025-104">USBX admite las funcionalidades del OTG USB cuando hay una controladora USB compatible con el OTG disponible en el diseño del hardware.</span><span class="sxs-lookup"><span data-stu-id="cf025-104">USBX supports the OTG functionalities of USB when an OTG compliant USB controller is available in the hardware design.</span></span>

<span data-ttu-id="cf025-105">USBX admite OTG en la pila USB principal,</span><span class="sxs-lookup"><span data-stu-id="cf025-105">USBX supports OTG in the core USB stack.</span></span> <span data-ttu-id="cf025-106">pero para que el grupo OTG funcione, requiere un controlador USB específico.</span><span class="sxs-lookup"><span data-stu-id="cf025-106">But for OTG to function, it requires a specific USB controller.</span></span> <span data-ttu-id="cf025-107">Puede encontrar las funciones del controlador del USBX OTG en el directorio usbx_otg.</span><span class="sxs-lookup"><span data-stu-id="cf025-107">USBX OTG controller functions can be found in the usbx_otg directory.</span></span> <span data-ttu-id="cf025-108">La versión actual de USBX solo admite NXP LPC3131 con capacidades de OTG completas.</span><span class="sxs-lookup"><span data-stu-id="cf025-108">The current USBX version only supports the NXP LPC3131 with full OTG capabilities.</span></span>

<span data-ttu-id="cf025-109">Puede encontrar las funciones del driver de controlador regulares (host o dispositivo) en el directorio usbx_device_controllers y usbx_host_controllers de USBX estándar, pero el directorio usbx_otg contiene las funciones del OTG específicas asociadas con el controlador USB.</span><span class="sxs-lookup"><span data-stu-id="cf025-109">The regular controller driver functions (host or device) can still be found in the standard USBX usbx_device_controllers and usbx_host_controllers but the usbx_otg directory contains the specific OTG functions associated with the USB controller.</span></span>

<span data-ttu-id="cf025-110">Hay cuatro categorías de funciones para un controlador del OTG además de las funciones habituales de host o de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cf025-110">There are four categories of functions for an OTG controller in addition to the usual host/device functions.</span></span>

- <span data-ttu-id="cf025-111">Funciones específicas de VBUS</span><span class="sxs-lookup"><span data-stu-id="cf025-111">VBUS specific functions</span></span>
- <span data-ttu-id="cf025-112">Inicio y detención del controlador</span><span class="sxs-lookup"><span data-stu-id="cf025-112">Start and Stop of the controller</span></span>
- <span data-ttu-id="cf025-113">Administrador de roles USB</span><span class="sxs-lookup"><span data-stu-id="cf025-113">USB role manager</span></span>
- <span data-ttu-id="cf025-114">Controladores de interrupciones</span><span class="sxs-lookup"><span data-stu-id="cf025-114">Interrupt handlers</span></span>

## <a name="vbus-functions"></a><span data-ttu-id="cf025-115">Funciones de VBUS</span><span class="sxs-lookup"><span data-stu-id="cf025-115">VBUS functions</span></span>

<span data-ttu-id="cf025-116">Cada controlador debe tener un administrador de VBUS para cambiar el estado de VBUS en función de los requisitos de administración de energía.</span><span class="sxs-lookup"><span data-stu-id="cf025-116">Each controller needs to have a VBUS manager to change the state of VBUS based on power management requirements.</span></span> <span data-ttu-id="cf025-117">Normalmente, esta función solo realiza la activación o desactivación de VBUS.</span><span class="sxs-lookup"><span data-stu-id="cf025-117">Usually, this function only performs turning on or off VBUS.</span></span>

## <a name="start-and-stop-the-controller"></a><span data-ttu-id="cf025-118">Inicio y detención del controlador</span><span class="sxs-lookup"><span data-stu-id="cf025-118">Start and Stop the controller</span></span>

<span data-ttu-id="cf025-119">A diferencia de una implementación USB normal, el OTG requiere que el host o la pila del dispositivo se activen y desactiven al cambiar el rol.</span><span class="sxs-lookup"><span data-stu-id="cf025-119">Unlike a regular USB implementation, OTG requires the host and/or the device stack to be activated and deactivated when the role changes.</span></span>

## <a name="usb-role-manager"></a><span data-ttu-id="cf025-120">Administrador de roles USB</span><span class="sxs-lookup"><span data-stu-id="cf025-120">USB role Manager</span></span>

<span data-ttu-id="cf025-121">El administrador de roles USB recibe comandos para cambiar el estado del USB.</span><span class="sxs-lookup"><span data-stu-id="cf025-121">The USB role manager receives commands to change the state of the USB.</span></span> <span data-ttu-id="cf025-122">Hay varios estados hacia y desde los que es necesario realizar transiciones:</span><span class="sxs-lookup"><span data-stu-id="cf025-122">There are several states that need transitions to and from:</span></span>

| <span data-ttu-id="cf025-123">Estado</span><span class="sxs-lookup"><span data-stu-id="cf025-123">State</span></span>                    | <span data-ttu-id="cf025-124">Value</span><span class="sxs-lookup"><span data-stu-id="cf025-124">Value</span></span> | <span data-ttu-id="cf025-125">Descripción</span><span class="sxs-lookup"><span data-stu-id="cf025-125">Description</span></span>                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| <span data-ttu-id="cf025-126">UX_OTG_IDLE</span><span class="sxs-lookup"><span data-stu-id="cf025-126">UX_OTG_IDLE</span></span>            | <span data-ttu-id="cf025-127">0</span><span class="sxs-lookup"><span data-stu-id="cf025-127">0</span></span>     | <span data-ttu-id="cf025-128">El dispositivo está inactivo</span><span class="sxs-lookup"><span data-stu-id="cf025-128">The device is Idle.</span></span> <span data-ttu-id="cf025-129">No está conectado a nada</span><span class="sxs-lookup"><span data-stu-id="cf025-129">Not connected to anything</span></span> |
| <span data-ttu-id="cf025-130">UX_OTG_IDLE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="cf025-130">UX_OTG_IDLE_TO_HOST</span></span>  | <span data-ttu-id="cf025-131">1</span><span class="sxs-lookup"><span data-stu-id="cf025-131">1</span></span>     | <span data-ttu-id="cf025-132">El dispositivo está conectado a un conector de tipo A</span><span class="sxs-lookup"><span data-stu-id="cf025-132">Device is connected with type A connector</span></span>             |
| <span data-ttu-id="cf025-133">UX_OTG_IDLE_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="cf025-133">UX_OTG_IDLE_TO_SLAVE</span></span> | <span data-ttu-id="cf025-134">2</span><span class="sxs-lookup"><span data-stu-id="cf025-134">2</span></span>     | <span data-ttu-id="cf025-135">El dispositivo está conectado a un conector de tipo B</span><span class="sxs-lookup"><span data-stu-id="cf025-135">Device is connected with type B connector</span></span>             |
| <span data-ttu-id="cf025-136">UX_OTG_HOST_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="cf025-136">UX_OTG_HOST_TO_IDLE</span></span>  | <span data-ttu-id="cf025-137">3</span><span class="sxs-lookup"><span data-stu-id="cf025-137">3</span></span>     | <span data-ttu-id="cf025-138">El dispositivo host se ha desconectado</span><span class="sxs-lookup"><span data-stu-id="cf025-138">Host device got disconnected</span></span>                          |
| <span data-ttu-id="cf025-139">UX_OTG_HOST_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="cf025-139">UX_OTG_HOST_TO_SLAVE</span></span> | <span data-ttu-id="cf025-140">4</span><span class="sxs-lookup"><span data-stu-id="cf025-140">4</span></span>     | <span data-ttu-id="cf025-141">Intercambio de roles de Host a Subordinado</span><span class="sxs-lookup"><span data-stu-id="cf025-141">Role swap from Host to Slave</span></span>                          |
| <span data-ttu-id="cf025-142">UX_OTG_SLAVE_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="cf025-142">UX_OTG_SLAVE_TO_IDLE</span></span> | <span data-ttu-id="cf025-143">5</span><span class="sxs-lookup"><span data-stu-id="cf025-143">5</span></span>     | <span data-ttu-id="cf025-144">El dispositivo subordinado está desconectado</span><span class="sxs-lookup"><span data-stu-id="cf025-144">Slave device is disconnected</span></span>                          |
| <span data-ttu-id="cf025-145">UX_OTG_SLAVE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="cf025-145">UX_OTG_SLAVE_TO_HOST</span></span> | <span data-ttu-id="cf025-146">6</span><span class="sxs-lookup"><span data-stu-id="cf025-146">6</span></span>     | <span data-ttu-id="cf025-147">Intercambio de roles de Subordinado a Host</span><span class="sxs-lookup"><span data-stu-id="cf025-147">Role swap from Slave to Host</span></span>                          |

## <a name="interrupt-handlers"></a><span data-ttu-id="cf025-148">Controladores de interrupciones</span><span class="sxs-lookup"><span data-stu-id="cf025-148">Interrupt handlers</span></span>

<span data-ttu-id="cf025-149">Tanto los drivers de controlador de dispositivo como de host para el OTG necesitan diferentes controladores de interrupción para supervisar las señales más allá de las interrupciones USB tradicionales, en particular, las señales debidas a SRP y VBUS.</span><span class="sxs-lookup"><span data-stu-id="cf025-149">Both host and device controller drivers for OTG needs different interrupt handlers to monitor signals beyond traditional USB interrupts, in particular signals due to SRP and VBUS.</span></span>

<span data-ttu-id="cf025-150">Cómo inicializar un controlador OTG USB.</span><span class="sxs-lookup"><span data-stu-id="cf025-150">How to initialize a USB OTG controller.</span></span> <span data-ttu-id="cf025-151">Aquí se usa NXP LPC3131 como ejemplo.</span><span class="sxs-lookup"><span data-stu-id="cf025-151">We use the NXP LPC3131 as an example here.</span></span>

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

<span data-ttu-id="cf025-152">En este ejemplo, se inicializa LPC3131 en el modo OTG pasando una función VBUS y una devolución de llamada para el cambio de modo (de host a subordinado o viceversa).</span><span class="sxs-lookup"><span data-stu-id="cf025-152">In this example, we initialize the LPC3131 in OTG mode by passing a VBUS function and a callback for mode change (from host to slave or vice versa).</span></span>

<span data-ttu-id="cf025-153">La función de devolución de llamada simplemente debe registrar el nuevo modo y reactivar un subproceso pendiente para que actúe el nuevo estado.</span><span class="sxs-lookup"><span data-stu-id="cf025-153">The callback function should simply record the new mode and wake up a pending thread to act up the new state.</span></span>

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

<span data-ttu-id="cf025-154">El valor de modo que se pasa puede tener los valores siguientes.</span><span class="sxs-lookup"><span data-stu-id="cf025-154">The mode value that is passed can have the following values.</span></span>

- <span data-ttu-id="cf025-155">**UX_OTG_MODE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="cf025-155">**UX_OTG_MODE_IDLE**</span></span>
- <span data-ttu-id="cf025-156">**UX_OTG_MODE_SLAVE**</span><span class="sxs-lookup"><span data-stu-id="cf025-156">**UX_OTG_MODE_SLAVE**</span></span>
- <span data-ttu-id="cf025-157">**UX_OTG_MODE_HOST**</span><span class="sxs-lookup"><span data-stu-id="cf025-157">**UX_OTG_MODE_HOST**</span></span>

<span data-ttu-id="cf025-158">La aplicación siempre puede comprobar qué dispositivo es examinando la variable:</span><span class="sxs-lookup"><span data-stu-id="cf025-158">The application can always check what the device is by looking at the variable:</span></span>

```C
_ux_system_otg -> ux_system_otg_device_type
```

<span data-ttu-id="cf025-159">Los valores pueden ser cualquiera de los siguientes:</span><span class="sxs-lookup"><span data-stu-id="cf025-159">Its values can be any of the following.</span></span>

- <span data-ttu-id="cf025-160">**UX_OTG_DEVICE_A**</span><span class="sxs-lookup"><span data-stu-id="cf025-160">**UX_OTG_DEVICE_A**</span></span>
- <span data-ttu-id="cf025-161">**UX_OTG_DEVICE_B**</span><span class="sxs-lookup"><span data-stu-id="cf025-161">**UX_OTG_DEVICE_B**</span></span>
- <span data-ttu-id="cf025-162">**UX_OTG_DEVICE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="cf025-162">**UX_OTG_DEVICE_IDLE**</span></span>

<span data-ttu-id="cf025-163">Un dispositivo host del OTG USB siempre puede solicitar un intercambio de roles emitiendo el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="cf025-163">A USB OTG host device can always ask for a role swap by issuing the following command.</span></span>

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

<span data-ttu-id="cf025-164">En el caso de un dispositivo subordinado, no hay ningún comando que emitir, pero el dispositivo subordinado puede establecer un estado para cambiar el rol, el cual recogerá el host cuando emita una **GET_STATUS** y, después, se iniciará el intercambio.</span><span class="sxs-lookup"><span data-stu-id="cf025-164">For a slave device, there is no command to issue but the slave device can set a state to change the role, which will be picked up by the host when it issues a **GET_STATUS** and the swap will then be initiated.</span></span>

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
