---
title: 'Capítulo 3: Descripción de los servicios AutoIP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios AutoIP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0935295ef9f7255c0851e1f64013884dce4c52f1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814830"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a><span data-ttu-id="c5f5c-103">Capítulo 3: Descripción de los servicios AutoIP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-103">Chapter 3 - Description of Azure RTOS NetX Duo AutoIP services</span></span>

<span data-ttu-id="c5f5c-104">Este capítulo contiene una descripción de todos los servicios AutoIP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-104">This chapter contains a description of all Azure RTOS NetX Duo AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="c5f5c-105">En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="c5f5c-106">**nx_auto_ip_create**: *crea una instancia de AutoIP*</span><span class="sxs-lookup"><span data-stu-id="c5f5c-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="c5f5c-107">**nx_auto_ip_delete**: *elimina una instancia de AutoIP*</span><span class="sxs-lookup"><span data-stu-id="c5f5c-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="c5f5c-108">**nx_auto_ip_get_address**: *obtiene la dirección AutoIP actual*</span><span class="sxs-lookup"><span data-stu-id="c5f5c-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="c5f5c-109">**nx_auto_ip_set_interface**: *establece la interfaz IP que necesita una dirección AutoIP*</span><span class="sxs-lookup"><span data-stu-id="c5f5c-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="c5f5c-110">**nx_auto_ip_start**: *inicia el procesamiento de AutoIP*</span><span class="sxs-lookup"><span data-stu-id="c5f5c-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="c5f5c-111">**nx_auto_ip_stop**: *detiene el procesamiento de AutoIP*</span><span class="sxs-lookup"><span data-stu-id="c5f5c-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="c5f5c-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="c5f5c-112">nx_auto_ip_create</span></span>

<span data-ttu-id="c5f5c-113">Crea instancias de AutoIP</span><span class="sxs-lookup"><span data-stu-id="c5f5c-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c5f5c-114">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a><span data-ttu-id="c5f5c-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="c5f5c-115">Description</span></span>

<span data-ttu-id="c5f5c-116">Este servicio crea una instancia de AutoIP en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c5f5c-117">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c5f5c-117">Input Parameters</span></span>

- <span data-ttu-id="c5f5c-118">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-118">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="c5f5c-119">**name**: nombre de la instancia de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-119">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="c5f5c-120">**ip_ptr**: puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-120">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="c5f5c-121">**stack_ptr**: puntero al área de la pila de subprocesos AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-121">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="c5f5c-122">**stack_size**: tamaño del área de la pila de subprocesos AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-122">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="c5f5c-123">**priority**: prioridad del subproceso AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-123">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="c5f5c-124">Si se utiliza DHCP, el subproceso DHCP debe tener una prioridad más alta que el subproceso de la instancia de IP y el subproceso AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-124">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="c5f5c-125">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c5f5c-125">Return Values</span></span>

- <span data-ttu-id="c5f5c-126">**NX_SUCCESS**: (0x00) Creación correcta de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-126">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="c5f5c-127">**NX_AUTO_IP_ERROR**: (0XA00) Error de creación de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-127">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="c5f5c-128">NX_PTR_ERROR: (0x16) AutoIP, ip_ptr o puntero de pila no válidos.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-128">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="c5f5c-129">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-129">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c5f5c-130">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c5f5c-130">Allowed From</span></span>

<span data-ttu-id="c5f5c-131">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c5f5c-131">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="c5f5c-132">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-132">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="c5f5c-133">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c5f5c-133">See Also</span></span>

<span data-ttu-id="c5f5c-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="c5f5c-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="c5f5c-135">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="c5f5c-135">nx_auto_ip_delete</span></span>

<span data-ttu-id="c5f5c-136">Elimina instancias de AutoIP</span><span class="sxs-lookup"><span data-stu-id="c5f5c-136">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c5f5c-137">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-137">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="c5f5c-138">Descripción</span><span class="sxs-lookup"><span data-stu-id="c5f5c-138">Description</span></span>

<span data-ttu-id="c5f5c-139">Este servicio elimina una instancia de AutoIP creada anteriormente en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-139">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c5f5c-140">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c5f5c-140">Input Parameters</span></span>

- <span data-ttu-id="c5f5c-141">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-141">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c5f5c-142">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c5f5c-142">Return Values</span></span>

- <span data-ttu-id="c5f5c-143">**NX_SUCCESS**: (0x00) Eliminación correcta de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-143">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="c5f5c-144">**NX_AUTO_IP_ERROR**: (0XA00) Error de eliminación de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-144">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="c5f5c-145">NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-145">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="c5f5c-146">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-146">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c5f5c-147">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c5f5c-147">Allowed From</span></span>

<span data-ttu-id="c5f5c-148">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="c5f5c-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c5f5c-149">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-149">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="c5f5c-150">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c5f5c-150">See Also</span></span>

<span data-ttu-id="c5f5c-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="c5f5c-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="c5f5c-152">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="c5f5c-152">nx_auto_ip_get_address</span></span>

<span data-ttu-id="c5f5c-153">Obtiene la dirección AutoIP actual</span><span class="sxs-lookup"><span data-stu-id="c5f5c-153">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="c5f5c-154">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-154">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="c5f5c-155">Descripción</span><span class="sxs-lookup"><span data-stu-id="c5f5c-155">Description</span></span>

<span data-ttu-id="c5f5c-156">Este servicio recupera la dirección AutoIP configurada actualmente.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-156">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="c5f5c-157">Si no hay ninguna, se devuelve la dirección IP 0.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-157">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c5f5c-158">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c5f5c-158">Input Parameters</span></span>

- <span data-ttu-id="c5f5c-159">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-159">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="c5f5c-160">**local_ip_address**: destino de la dirección IP devuelta.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-160">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="c5f5c-161">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c5f5c-161">Return Values</span></span>

- <span data-ttu-id="c5f5c-162">**NX_SUCCESS**: (0x00) Se ha obtenido la dirección AutoIP correctamente.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-162">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="c5f5c-163">**NX_AUTO_IP_NO_LOCAL**: (0XA01) No hay ninguna dirección AutoIP válida.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-163">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="c5f5c-164">NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-164">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="c5f5c-165">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-165">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c5f5c-166">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c5f5c-166">Allowed From</span></span>

<span data-ttu-id="c5f5c-167">Inicialización, temporizadores, subprocesos, ISR</span><span class="sxs-lookup"><span data-stu-id="c5f5c-167">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c5f5c-168">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-168">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="c5f5c-169">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c5f5c-169">See Also</span></span>

<span data-ttu-id="c5f5c-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="c5f5c-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="c5f5c-171">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="c5f5c-171">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="c5f5c-172">Establece la interfaz de red para AutoIP</span><span class="sxs-lookup"><span data-stu-id="c5f5c-172">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="c5f5c-173">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-173">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="c5f5c-174">Descripción</span><span class="sxs-lookup"><span data-stu-id="c5f5c-174">Description</span></span>

<span data-ttu-id="c5f5c-175">Este servicio establece el índice de la interfaz de red que AutoIP sondeará para buscar una dirección IP de red.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-175">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="c5f5c-176">El valor predeterminado es cero (la interfaz de red principal).</span><span class="sxs-lookup"><span data-stu-id="c5f5c-176">The default is zero (the primary network interface).</span></span> <span data-ttu-id="c5f5c-177">Solo se aplica a los dispositivos de host múltiple.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-177">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c5f5c-178">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c5f5c-178">Input Parameters</span></span>

- <span data-ttu-id="c5f5c-179">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-179">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="c5f5c-180">**interface_index**: interfaz para sondear si hay una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-180">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="c5f5c-181">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c5f5c-181">Return Values</span></span>

- <span data-ttu-id="c5f5c-182">**NX_SUCCESS**: (0x00) Interfaz de AutoIP configurada correctamente.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-182">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="c5f5c-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Interfaz de red no válida NX_PTR_ERROR (0x16) Puntero de AutoIP no válido.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface NX_PTR_ERROR (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="c5f5c-184">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c5f5c-185">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c5f5c-185">Allowed From</span></span>

<span data-ttu-id="c5f5c-186">Inicialización, temporizadores, subprocesos, ISR</span><span class="sxs-lookup"><span data-stu-id="c5f5c-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c5f5c-187">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a><span data-ttu-id="c5f5c-188">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c5f5c-188">See Also</span></span>

<span data-ttu-id="c5f5c-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="c5f5c-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="c5f5c-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="c5f5c-190">nx_auto_ip_start</span></span>

<span data-ttu-id="c5f5c-191">Inicia el procesamiento de AutoIP</span><span class="sxs-lookup"><span data-stu-id="c5f5c-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="c5f5c-192">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="c5f5c-193">Descripción</span><span class="sxs-lookup"><span data-stu-id="c5f5c-193">Description</span></span>

<span data-ttu-id="c5f5c-194">Este servicio inicia el protocolo AutoIP en una instancia de AutoIP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c5f5c-195">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c5f5c-195">Input Parameters</span></span>

- <span data-ttu-id="c5f5c-196">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="c5f5c-197">**starting_local_address**: dirección de inicio de AutoIP opcional.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="c5f5c-198">Un valor de IP_ADDRESS (0,0,0,0) especifica que se debe derivar una dirección AutoIP aleatoria.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="c5f5c-199">De lo contrario, si se especifica una dirección AutoIP válida, NetX AutoIP intenta asignar esa dirección.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="c5f5c-200">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c5f5c-200">Return Values</span></span>

- <span data-ttu-id="c5f5c-201">**NX_SUCCESS**: (0x00) Inicio correcto de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="c5f5c-202">**NX_AUTO_IP_ERROR**: (0XA00) Error de inicio de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="c5f5c-203">NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="c5f5c-204">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c5f5c-205">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c5f5c-205">Allowed From</span></span>

<span data-ttu-id="c5f5c-206">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c5f5c-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="c5f5c-207">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="c5f5c-208">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c5f5c-208">See Also</span></span>

<span data-ttu-id="c5f5c-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="c5f5c-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="c5f5c-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="c5f5c-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="c5f5c-211">Detiene el procesamiento de AutoIP</span><span class="sxs-lookup"><span data-stu-id="c5f5c-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="c5f5c-212">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="c5f5c-213">Descripción</span><span class="sxs-lookup"><span data-stu-id="c5f5c-213">Description</span></span>

<span data-ttu-id="c5f5c-214">Este servicio detiene el protocolo AutoIP en una instancia de AutoIP creada e iniciada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="c5f5c-215">Este servicio se suele utilizar cuando se cambia la dirección IP mediante DHCP o manualmente por una dirección que no es AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c5f5c-216">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c5f5c-216">Input Parameters</span></span>

- <span data-ttu-id="c5f5c-217">**auto_ip_ptr**: puntero al bloque de control de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c5f5c-218">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c5f5c-218">Return Values</span></span>

- <span data-ttu-id="c5f5c-219">**NX_SUCCESS**: (0x00) Detención correcta de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="c5f5c-220">**NX_AUTO_IP_ERROR**: (0XA00) Error de detención de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="c5f5c-221">NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="c5f5c-222">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="c5f5c-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c5f5c-223">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c5f5c-223">Allowed From</span></span>

<span data-ttu-id="c5f5c-224">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="c5f5c-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c5f5c-225">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c5f5c-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="c5f5c-226">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c5f5c-226">See Also</span></span>

<span data-ttu-id="c5f5c-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="c5f5c-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>