---
title: 'Capítulo 3: Descripción de los servicios AutoIP de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios AutoIP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 22cc06c32cc9f1857b32d1d2b44a506ea1652cfd
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815285"
---
# <a name="chapter-3---description-of-azure-rtos-netx-autoip-services"></a><span data-ttu-id="2e576-103">Capítulo 3: Descripción de los servicios AutoIP de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="2e576-103">Chapter 3 - Description of Azure RTOS NetX AutoIP services</span></span>

<span data-ttu-id="2e576-104">Este capítulo contiene una descripción de todos los servicios AutoIP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="2e576-104">This chapter contains a description of all Azure RTOS NetX AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="2e576-105">En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="2e576-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="2e576-106">**nx_auto_ip_create**: *crea una instancia de AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="2e576-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="2e576-107">**nx_auto_ip_delete**: *elimina una instancia de AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="2e576-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="2e576-108">**nx_auto_ip_get_address**: *obtiene la dirección AutoIP actual*.</span><span class="sxs-lookup"><span data-stu-id="2e576-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="2e576-109">**nx_auto_ip_set_interface**: *establece la interfaz IP que necesita una dirección AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="2e576-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="2e576-110">**nx_auto_ip_start**: *inicia el procesamiento de AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="2e576-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="2e576-111">**nx_auto_ip_stop**: *detiene el procesamiento de AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="2e576-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="2e576-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="2e576-112">nx_auto_ip_create</span></span>

<span data-ttu-id="2e576-113">Crea una instancia de AutoIP</span><span class="sxs-lookup"><span data-stu-id="2e576-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2e576-114">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2e576-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
            NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
            UINT priority);
```

### <a name="description"></a><span data-ttu-id="2e576-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="2e576-115">Description</span></span>

<span data-ttu-id="2e576-116">Este servicio crea una instancia de AutoIP en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="2e576-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

- <span data-ttu-id="2e576-117">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-117">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2e576-118">**name**: nombre de la instancia de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-118">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="2e576-119">**ip_ptr**: puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="2e576-119">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="2e576-120">**stack_ptr**: puntero al área de la pila de subprocesos AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-120">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="2e576-121">**stack_size**: tamaño del área de la pila de subprocesos AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-121">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="2e576-122">**priority**: prioridad del subproceso AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-122">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="2e576-123">Si se utiliza DHCP, el subproceso DHCP debe tener una prioridad más alta que el subproceso de la instancia de IP y el subproceso AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-123">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="2e576-124">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2e576-124">Return Values</span></span>

- <span data-ttu-id="2e576-125">**NX_SUCCESS**: (0x00) Creación correcta de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-125">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="2e576-126">**NX_AUTO_IP_ERROR**: (0XA00) Error de creación de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-126">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="2e576-127">NX_PTR_ERROR: (0x16) AutoIP, ip_ptr o puntero de pila no válidos.</span><span class="sxs-lookup"><span data-stu-id="2e576-127">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="2e576-128">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="2e576-128">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e576-129">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2e576-129">Allowed From</span></span>

<span data-ttu-id="2e576-130">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="2e576-130">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2e576-131">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2e576-131">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="2e576-132">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2e576-132">See Also</span></span>

<span data-ttu-id="2e576-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e576-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="2e576-134">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="2e576-134">nx_auto_ip_delete</span></span>

<span data-ttu-id="2e576-135">Elimina una instancia de AutoIP</span><span class="sxs-lookup"><span data-stu-id="2e576-135">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2e576-136">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2e576-136">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="2e576-137">Descripción</span><span class="sxs-lookup"><span data-stu-id="2e576-137">Description</span></span>

<span data-ttu-id="2e576-138">Este servicio elimina una instancia de AutoIP creada anteriormente en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="2e576-138">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e576-139">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2e576-139">Input Parameters</span></span>

- <span data-ttu-id="2e576-140">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-140">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2e576-141">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2e576-141">Return Values</span></span>

- <span data-ttu-id="2e576-142">**NX_SUCCESS**: (0x00) Eliminación correcta de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-142">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="2e576-143">**NX_AUTO_IP_ERROR**: (0XA00) Error de eliminación de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-143">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="2e576-144">NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.</span><span class="sxs-lookup"><span data-stu-id="2e576-144">NX_PTR_ERROR (0x16): Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2e576-145">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="2e576-145">NX_CALLER_ERROR (0x11): Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e576-146">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2e576-146">Allowed From</span></span>

<span data-ttu-id="2e576-147">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="2e576-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2e576-148">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2e576-148">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="2e576-149">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2e576-149">See Also</span></span>

<span data-ttu-id="2e576-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e576-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="2e576-151">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="2e576-151">nx_auto_ip_get_address</span></span>

<span data-ttu-id="2e576-152">Obtiene la dirección AutoIP actual</span><span class="sxs-lookup"><span data-stu-id="2e576-152">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="2e576-153">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2e576-153">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="2e576-154">Descripción</span><span class="sxs-lookup"><span data-stu-id="2e576-154">Description</span></span>

<span data-ttu-id="2e576-155">Este servicio recupera la dirección AutoIP configurada actualmente.</span><span class="sxs-lookup"><span data-stu-id="2e576-155">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="2e576-156">Si no hay ninguna, se devuelve la dirección IP 0.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="2e576-156">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e576-157">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2e576-157">Input Parameters</span></span>

- <span data-ttu-id="2e576-158">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-158">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2e576-159">**local_ip_address**: destino de la dirección IP devuelta.</span><span class="sxs-lookup"><span data-stu-id="2e576-159">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="2e576-160">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2e576-160">Return Values</span></span>

- <span data-ttu-id="2e576-161">**NX_SUCCESS**: (0x00) Se ha obtenido la dirección AutoIP correctamente.</span><span class="sxs-lookup"><span data-stu-id="2e576-161">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="2e576-162">**NX_AUTO_IP_NO_LOCAL**: (0XA01) No hay ninguna dirección AutoIP válida.</span><span class="sxs-lookup"><span data-stu-id="2e576-162">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="2e576-163">NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.</span><span class="sxs-lookup"><span data-stu-id="2e576-163">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2e576-164">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="2e576-164">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e576-165">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2e576-165">Allowed From</span></span>

<span data-ttu-id="2e576-166">Inicialización, temporizadores, subprocesos, ISR</span><span class="sxs-lookup"><span data-stu-id="2e576-166">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="2e576-167">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2e576-167">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="2e576-168">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2e576-168">See Also</span></span>

<span data-ttu-id="2e576-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e576-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="2e576-170">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="2e576-170">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="2e576-171">Establece la interfaz de red para AutoIP</span><span class="sxs-lookup"><span data-stu-id="2e576-171">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="2e576-172">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2e576-172">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2e576-173">Descripción</span><span class="sxs-lookup"><span data-stu-id="2e576-173">Description</span></span>

<span data-ttu-id="2e576-174">Este servicio establece el índice de la interfaz de red que AutoIP sondeará para buscar una dirección IP de red.</span><span class="sxs-lookup"><span data-stu-id="2e576-174">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="2e576-175">El valor predeterminado es cero (la interfaz de red principal).</span><span class="sxs-lookup"><span data-stu-id="2e576-175">The default is zero (the primary network interface).</span></span> <span data-ttu-id="2e576-176">Solo se aplica a los dispositivos de host múltiple.</span><span class="sxs-lookup"><span data-stu-id="2e576-176">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e576-177">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2e576-177">Input Parameters</span></span>

- <span data-ttu-id="2e576-178">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-178">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2e576-179">**interface_index**: interfaz para sondear si hay una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="2e576-179">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="2e576-180">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2e576-180">Return Values</span></span>

- <span data-ttu-id="2e576-181">**NX_SUCCESS**: (0x00) Interfaz de AutoIP configurada correctamente.</span><span class="sxs-lookup"><span data-stu-id="2e576-181">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="2e576-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="2e576-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface</span></span> 
- <span data-ttu-id="2e576-183">NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.</span><span class="sxs-lookup"><span data-stu-id="2e576-183">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2e576-184">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="2e576-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e576-185">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2e576-185">Allowed From</span></span>

<span data-ttu-id="2e576-186">Inicialización, temporizadores, subprocesos, ISR</span><span class="sxs-lookup"><span data-stu-id="2e576-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="2e576-187">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2e576-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block auto_ip_0. */
```

### <a name="see-also"></a><span data-ttu-id="2e576-188">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2e576-188">See Also</span></span>

<span data-ttu-id="2e576-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e576-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="2e576-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="2e576-190">nx_auto_ip_start</span></span>

<span data-ttu-id="2e576-191">Inicia el procesamiento de AutoIP</span><span class="sxs-lookup"><span data-stu-id="2e576-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2e576-192">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2e576-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="2e576-193">Descripción</span><span class="sxs-lookup"><span data-stu-id="2e576-193">Description</span></span>

<span data-ttu-id="2e576-194">Este servicio inicia el protocolo AutoIP en una instancia de AutoIP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2e576-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e576-195">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2e576-195">Input Parameters</span></span>

- <span data-ttu-id="2e576-196">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="2e576-197">**starting_local_address**: dirección de inicio de AutoIP opcional.</span><span class="sxs-lookup"><span data-stu-id="2e576-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="2e576-198">Un valor de IP_ADDRESS (0,0,0,0) especifica que se debe derivar una dirección AutoIP aleatoria.</span><span class="sxs-lookup"><span data-stu-id="2e576-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="2e576-199">De lo contrario, si se especifica una dirección AutoIP válida, NetX AutoIP intenta asignar esa dirección.</span><span class="sxs-lookup"><span data-stu-id="2e576-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="2e576-200">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2e576-200">Return Values</span></span>

- <span data-ttu-id="2e576-201">**NX_SUCCESS**: (0x00) Inicio correcto de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="2e576-202">**NX_AUTO_IP_ERROR**: (0XA00) Error de inicio de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="2e576-203">NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.</span><span class="sxs-lookup"><span data-stu-id="2e576-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2e576-204">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="2e576-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e576-205">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2e576-205">Allowed From</span></span>

<span data-ttu-id="2e576-206">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="2e576-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2e576-207">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2e576-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="2e576-208">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2e576-208">See Also</span></span>

<span data-ttu-id="2e576-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e576-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="2e576-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="2e576-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="2e576-211">Detiene el procesamiento de AutoIP</span><span class="sxs-lookup"><span data-stu-id="2e576-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2e576-212">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2e576-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="2e576-213">Descripción</span><span class="sxs-lookup"><span data-stu-id="2e576-213">Description</span></span>

<span data-ttu-id="2e576-214">Este servicio detiene el protocolo AutoIP en una instancia de AutoIP creada e iniciada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2e576-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="2e576-215">Este servicio se suele utilizar cuando se cambia la dirección IP mediante DHCP o manualmente por una dirección que no es AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2e576-216">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2e576-216">Input Parameters</span></span>

- <span data-ttu-id="2e576-217">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2e576-218">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2e576-218">Return Values</span></span>

- <span data-ttu-id="2e576-219">**NX_SUCCESS**: (0x00) Detención correcta de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="2e576-220">**NX_AUTO_IP_ERROR**: (0XA00) Error de detención de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="2e576-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="2e576-221">NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.</span><span class="sxs-lookup"><span data-stu-id="2e576-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="2e576-222">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="2e576-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2e576-223">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2e576-223">Allowed From</span></span>

<span data-ttu-id="2e576-224">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="2e576-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2e576-225">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2e576-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="2e576-226">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2e576-226">See Also</span></span>

<span data-ttu-id="2e576-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="2e576-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>