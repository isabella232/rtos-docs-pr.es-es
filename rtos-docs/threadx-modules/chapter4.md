---
title: 'Capítulo 4: API de módulo'
author: philmea
ms.author: philmea
description: Este artículo es un resumen de las API adicionales disponibles para un módulo.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814378"
---
# <a name="chapter-4---module-apis"></a><span data-ttu-id="629af-103">Capítulo 4: API de módulo</span><span class="sxs-lookup"><span data-stu-id="629af-103">Chapter 4 - Module APIs</span></span>

## <a name="summary-of-module-apis"></a><span data-ttu-id="629af-104">Resumen de las API de un módulo</span><span class="sxs-lookup"><span data-stu-id="629af-104">Summary of Module APIs</span></span>

<span data-ttu-id="629af-105">Hay varias funciones API adicionales disponibles para un módulo, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="629af-105">There are several additional API functions available to a module, as follows:</span></span>

- <span data-ttu-id="629af-106">\***txm_module_application_request**: solicitud específica de una aplicación al código residente\*.</span><span class="sxs-lookup"><span data-stu-id="629af-106">***txm_module_application_request** _ - _Application-specific request to resident code*</span></span>
- <span data-ttu-id="629af-107">\***txm_module_object_allocate**: asignar memoria fuera del módulo para el objeto\*.</span><span class="sxs-lookup"><span data-stu-id="629af-107">***txm_module_object_allocate** _ - _Allocate memory outside of module for object*</span></span>
- <span data-ttu-id="629af-108">\***txm_module_object_deallocate**: desasignar memoria de objeto asignada previamente\*.</span><span class="sxs-lookup"><span data-stu-id="629af-108">***txm_module_object_deallocate** _ - _Deallocate previously allocated object memory*</span></span>
- <span data-ttu-id="629af-109">\***txm_module_object_pointer_get**: buscar un objeto del sistema y recuperar un puntero de objeto\*.</span><span class="sxs-lookup"><span data-stu-id="629af-109">***txm_module_object_pointer_get** _ - _Find system object and retrieve object pointer*</span></span>
- <span data-ttu-id="629af-110">\***txm_module_object_pointer_get_extended**: buscar un objeto del sistema y recuperar un puntero de objeto, seguridad de la longitud del nombre\*.</span><span class="sxs-lookup"><span data-stu-id="629af-110">***txm_module_object_pointer_get_extended** _ - _Find system object and retrieve object pointer, name length safety*</span></span>

## <a name="return-values"></a><span data-ttu-id="629af-111">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="629af-111">Return values</span></span>

<span data-ttu-id="629af-112">Se devuelven códigos de error adicionales para algunas API de Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="629af-112">Additional error codes are returned for some Azure RTOS APIs.</span></span> <span data-ttu-id="629af-113">Estos códigos de error adicionales se definen de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="629af-113">These additional error codes are defined as follows:</span></span>

- <span data-ttu-id="629af-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): indica que el módulo no tiene las propiedades correctas para realizar una llamada de API.</span><span class="sxs-lookup"><span data-stu-id="629af-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): Indicates the module does not have the correct properties to make an API call.</span></span> <span data-ttu-id="629af-115">Por ejemplo, llamar a las API de seguimiento en modo de usuario.</span><span class="sxs-lookup"><span data-stu-id="629af-115">For example, calling trace APIs in user mode.</span></span>
- <span data-ttu-id="629af-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): indica que la memoria suministrada por el módulo no es válida o está en una ubicación no válida.</span><span class="sxs-lookup"><span data-stu-id="629af-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): Indicates the memory supplied by the module is invalid or is in an invalid location.</span></span> <span data-ttu-id="629af-117">Por ejemplo, en los módulos protegidos en memoria, no se permite que los bloques de control de objetos estén ubicados en la memoria a la que puede tener acceso el módulo.</span><span class="sxs-lookup"><span data-stu-id="629af-117">For example, in memory protected modules, object control blocks are not allowed to be located in memory the module can access.</span></span>
- <span data-ttu-id="629af-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): la devolución de llamada especificada en la API está fuera del intervalo del código del módulo y, por lo tanto, no es válida.</span><span class="sxs-lookup"><span data-stu-id="629af-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): Callback specified in the API is outside the range of the module's code and is therefore invalid.</span></span>

---

## <a name="txm_module_application_request"></a><span data-ttu-id="629af-119">txm_module_application_request</span><span class="sxs-lookup"><span data-stu-id="629af-119">txm_module_application_request</span></span>

<span data-ttu-id="629af-120">Solicitud específica de la aplicación para el código residente.</span><span class="sxs-lookup"><span data-stu-id="629af-120">Application-specific request to resident code.</span></span>

### <a name="prototype"></a><span data-ttu-id="629af-121">Prototipo</span><span class="sxs-lookup"><span data-stu-id="629af-121">Prototype</span></span>

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a><span data-ttu-id="629af-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="629af-122">Description</span></span>

<span data-ttu-id="629af-123">Este servicio realiza la solicitud especificada a la parte residente de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="629af-123">This service makes the specified request to the resident portion of the application.</span></span> <span data-ttu-id="629af-124">Se supone que la estructura de la solicitud está preparada antes de la llamada.</span><span class="sxs-lookup"><span data-stu-id="629af-124">It is assumed that the request structure is prepared prior to the call.</span></span> <span data-ttu-id="629af-125">El procesamiento real de la solicitud tiene lugar en el código residente en la función ***_txm_module_manager_application_request***.</span><span class="sxs-lookup"><span data-stu-id="629af-125">The actual processing of the request takes place in the resident code in the function ***_txm_module_manager_application_request***.</span></span> <span data-ttu-id="629af-126">De forma predeterminada, esta función se deja vacía y está diseñada para que la modifique el desarrollador de la aplicación residente.</span><span class="sxs-lookup"><span data-stu-id="629af-126">By default, this function is left empty and is designed for the resident application developer to modify.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="629af-127">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="629af-127">Input parameters</span></span>

- <span data-ttu-id="629af-128">**request** Id. de solicitud (aplicación definida)</span><span class="sxs-lookup"><span data-stu-id="629af-128">**request** Request ID (application defined)</span></span>
- <span data-ttu-id="629af-129">**param_1** Primer parámetro</span><span class="sxs-lookup"><span data-stu-id="629af-129">**param_1** First parameter</span></span>
- <span data-ttu-id="629af-130">**param_2** Segundo parámetro</span><span class="sxs-lookup"><span data-stu-id="629af-130">**param_2** Second parameter</span></span>
- <span data-ttu-id="629af-131">**param_3** Tercer parámetro</span><span class="sxs-lookup"><span data-stu-id="629af-131">**param_3** Third parameter</span></span>

### <a name="return-values"></a><span data-ttu-id="629af-132">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="629af-132">Return values</span></span>

- <span data-ttu-id="629af-133">**TX_SUCCESS** (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="629af-133">**TX_SUCCESS** (0x00) Successful request.</span></span>
- <span data-ttu-id="629af-134">**TX_NOT_AVAILABLE** (0x1D) La solicitud no es compatible con el código residente.</span><span class="sxs-lookup"><span data-stu-id="629af-134">**TX_NOT_AVAILABLE** (0x1D) Request not supported by resident code.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="629af-135">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="629af-135">Allowed from</span></span>

<span data-ttu-id="629af-136">Subprocesos de módulo</span><span class="sxs-lookup"><span data-stu-id="629af-136">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="629af-137">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="629af-137">Example</span></span>

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a><span data-ttu-id="629af-138">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="629af-138">txm_module_object_allocate</span></span>

<span data-ttu-id="629af-139">Asigne memoria en el grupo de objetos (creado por la aplicación residente) para un bloque de control de objeto de módulo.</span><span class="sxs-lookup"><span data-stu-id="629af-139">Allocate memory in the object pool (created by the resident application) for a module object control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="629af-140">Prototipo</span><span class="sxs-lookup"><span data-stu-id="629af-140">Prototype</span></span>

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a><span data-ttu-id="629af-141">Descripción</span><span class="sxs-lookup"><span data-stu-id="629af-141">Description</span></span>

<span data-ttu-id="629af-142">Este servicio asigna memoria para un objeto de módulo de la memoria fuera del módulo, lo que ayuda a evitar que el código del módulo dañe el bloque de control de objetos.</span><span class="sxs-lookup"><span data-stu-id="629af-142">This service allocates memory for a module object from memory outside of the module, which helps prevent corruption of the object control block by the module's code.</span></span> <span data-ttu-id="629af-143">En los sistemas protegidos en memoria, todos los bloques de control de objetos se deben asignar con esta API para poder crearlos.</span><span class="sxs-lookup"><span data-stu-id="629af-143">In memory protected systems, all object control blocks must be allocated with this API before they can be created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="629af-144">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="629af-144">Input parameters</span></span>

- <span data-ttu-id="629af-145">**object_ptr** Destino del puntero de objeto en una asignación correcta.</span><span class="sxs-lookup"><span data-stu-id="629af-145">**object_ptr** Destination of object pointer on successful allocation.</span></span>
- <span data-ttu-id="629af-146">**object_size** Tamaño en bytes del objeto que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="629af-146">**object_size** Size in bytes of the object to be allocated.</span></span>

### <a name="return-values"></a><span data-ttu-id="629af-147">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="629af-147">Return values</span></span>

- <span data-ttu-id="629af-148">**TX_SUCCESS** (0x00) Asignación correcta de objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-148">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>
- <span data-ttu-id="629af-149">**TX_NO_MEMORY** (0x10) No hay suficiente memoria.</span><span class="sxs-lookup"><span data-stu-id="629af-149">**TX_NO_MEMORY** (0x10) Not enough memory.</span></span>
- <span data-ttu-id="629af-150">**TX_NOT_AVAILABLE** (0x1D) El administrador de módulos no ha creado un grupo de objetos del que asignar</span><span class="sxs-lookup"><span data-stu-id="629af-150">**TX_NOT_AVAILABLE** (0x1D) Module manager has not created an object pool to allocate from</span></span>

### <a name="allowed-from"></a><span data-ttu-id="629af-151">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="629af-151">Allowed from</span></span>

<span data-ttu-id="629af-152">Subprocesos de módulo</span><span class="sxs-lookup"><span data-stu-id="629af-152">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="629af-153">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="629af-153">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a><span data-ttu-id="629af-154">Vea también</span><span class="sxs-lookup"><span data-stu-id="629af-154">See also</span></span>

- <span data-ttu-id="629af-155">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="629af-155">txm_module_object_deallocate</span></span>
- <span data-ttu-id="629af-156">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="629af-156">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_deallocate"></a><span data-ttu-id="629af-157">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="629af-157">txm_module_object_deallocate</span></span>

<span data-ttu-id="629af-158">Desasigne la memoria de objetos previamente asignados.</span><span class="sxs-lookup"><span data-stu-id="629af-158">Deallocate previously allocated object memory</span></span>

### <a name="prototype"></a><span data-ttu-id="629af-159">Prototipo</span><span class="sxs-lookup"><span data-stu-id="629af-159">Prototype</span></span>

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a><span data-ttu-id="629af-160">Descripción</span><span class="sxs-lookup"><span data-stu-id="629af-160">Description</span></span>

<span data-ttu-id="629af-161">***Este servicio está en desuso porque ya no es necesario***.</span><span class="sxs-lookup"><span data-stu-id="629af-161">***This service has been deprecated because it is no longer needed***.</span></span>

<span data-ttu-id="629af-162">La memoria que se asignó previamente a través de *txm_module_object_allocate* ***_ se ha desasignado en el \__servicio de eliminación*** _\* _tx_.</span><span class="sxs-lookup"><span data-stu-id="629af-162">The memory that was previously allocated via ***txm_module_object_allocate\**_ is deallocated in the _*_tx_\__delete service***.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="629af-163">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="629af-163">Input parameters</span></span>

- <span data-ttu-id="629af-164">**object_ptr** Puntero de objeto que se va a desasignar.</span><span class="sxs-lookup"><span data-stu-id="629af-164">**object_ptr** Object pointer to deallocate.</span></span>

### <a name="return-values"></a><span data-ttu-id="629af-165">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="629af-165">Return values</span></span>

- <span data-ttu-id="629af-166">**TX_SUCCESS** (0x00) Asignación correcta de objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-166">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="629af-167">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="629af-167">Allowed from</span></span>

<span data-ttu-id="629af-168">Subprocesos de módulo</span><span class="sxs-lookup"><span data-stu-id="629af-168">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="629af-169">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="629af-169">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a><span data-ttu-id="629af-170">Vea también</span><span class="sxs-lookup"><span data-stu-id="629af-170">See also</span></span>

- <span data-ttu-id="629af-171">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="629af-171">txm_module_object_allocate</span></span>
- <span data-ttu-id="629af-172">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="629af-172">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_pointer_get"></a><span data-ttu-id="629af-173">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="629af-173">txm_module_object_pointer_get</span></span>

<span data-ttu-id="629af-174">Busque un objeto del sistema y recupere un puntero de objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-174">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="629af-175">Prototipo</span><span class="sxs-lookup"><span data-stu-id="629af-175">Prototype</span></span>

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="629af-176">Descripción</span><span class="sxs-lookup"><span data-stu-id="629af-176">Description</span></span>

<span data-ttu-id="629af-177">Este servicio recupera el puntero de objeto de un tipo determinado con un nombre determinado.</span><span class="sxs-lookup"><span data-stu-id="629af-177">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="629af-178">Si no se encuentra el objeto, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="629af-178">If the object is not found, an error is returned.</span></span> <span data-ttu-id="629af-179">De lo contrario, si se encuentra el objeto, la dirección de ese objeto se coloca en "object_ptr".</span><span class="sxs-lookup"><span data-stu-id="629af-179">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="629af-180">Este puntero se puede usar para realizar llamadas de servicio de sistema, para interactuar con el código residente u otros módulos cargados en el sistema.</span><span class="sxs-lookup"><span data-stu-id="629af-180">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="629af-181">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="629af-181">Input parameters</span></span>

- <span data-ttu-id="629af-182">**object_type** Tipo de objeto de ThreadX solicitado.</span><span class="sxs-lookup"><span data-stu-id="629af-182">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="629af-183">Los tipos válidos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="629af-183">Valid types are as follows:</span></span>
  - <span data-ttu-id="629af-184">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-184">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="629af-185">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-185">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="629af-186">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-186">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="629af-187">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-187">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="629af-188">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-188">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="629af-189">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-189">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="629af-190">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-190">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="629af-191">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-191">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="629af-192">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-192">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="629af-193">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-193">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="629af-194">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-194">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="629af-195">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-195">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="629af-196">**name** Nombre de objeto específico de la aplicación tal y como se definió al crear el objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-196">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="629af-197">**object_ptr** Destino del puntero de objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-197">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="629af-198">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="629af-198">Return values</span></span>

- <span data-ttu-id="629af-199">**TX_SUCCESS** (0x00) Obtención correcta de objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-199">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="629af-200">**TX_OPTION_ERROR** (0x08) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="629af-200">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="629af-201">**TX_PTR_ERROR** (0x03) Destino no válido.</span><span class="sxs-lookup"><span data-stu-id="629af-201">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="629af-202">**TX_SIZE_ERROR** (0x05) Tamaño no válido.</span><span class="sxs-lookup"><span data-stu-id="629af-202">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="629af-203">**TX_NO_INSTANCE** (0x0D) No se encontró el objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-203">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="629af-204">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="629af-204">Allowed from</span></span>

<span data-ttu-id="629af-205">Subprocesos de módulo</span><span class="sxs-lookup"><span data-stu-id="629af-205">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="629af-206">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="629af-206">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="629af-207">Vea también</span><span class="sxs-lookup"><span data-stu-id="629af-207">See also</span></span>

- <span data-ttu-id="629af-208">txm_module_manager_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="629af-208">txm_module_manager_object_pointer_get_extended</span></span>

---

## <a name="txm_module_object_pointer_get_extended"></a><span data-ttu-id="629af-209">txm_module_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="629af-209">txm_module_object_pointer_get_extended</span></span>

<span data-ttu-id="629af-210">Busque un objeto del sistema y recupere un puntero de objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-210">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="629af-211">Prototipo</span><span class="sxs-lookup"><span data-stu-id="629af-211">Prototype</span></span>

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="629af-212">Descripción</span><span class="sxs-lookup"><span data-stu-id="629af-212">Description</span></span>

<span data-ttu-id="629af-213">Este servicio recupera el puntero de objeto de un tipo determinado con un nombre determinado.</span><span class="sxs-lookup"><span data-stu-id="629af-213">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="629af-214">Si no se encuentra el objeto, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="629af-214">If the object is not found, an error is returned.</span></span> <span data-ttu-id="629af-215">De lo contrario, si se encuentra el objeto, la dirección de ese objeto se coloca en "object_ptr".</span><span class="sxs-lookup"><span data-stu-id="629af-215">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="629af-216">Este puntero se puede usar para realizar llamadas de servicio de sistema, para interactuar con el código residente u otros módulos cargados en el sistema.</span><span class="sxs-lookup"><span data-stu-id="629af-216">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="629af-217">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="629af-217">Input parameters</span></span>

- <span data-ttu-id="629af-218">**object_type** Tipo de objeto de ThreadX solicitado.</span><span class="sxs-lookup"><span data-stu-id="629af-218">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="629af-219">Los tipos válidos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="629af-219">Valid types are as follows:</span></span>
  - <span data-ttu-id="629af-220">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-220">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="629af-221">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-221">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="629af-222">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-222">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="629af-223">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-223">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="629af-224">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-224">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="629af-225">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-225">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="629af-226">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-226">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="629af-227">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-227">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="629af-228">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-228">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="629af-229">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-229">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="629af-230">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-230">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="629af-231">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="629af-231">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="629af-232">**name** Nombre de objeto específico de la aplicación tal y como se definió al crear el objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-232">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="629af-233">**name_length** Longitud del nombre.</span><span class="sxs-lookup"><span data-stu-id="629af-233">**name_length** Length of name.</span></span>
- <span data-ttu-id="629af-234">**object_ptr** Destino del puntero de objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-234">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="629af-235">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="629af-235">Return values</span></span>

- <span data-ttu-id="629af-236">**TX_SUCCESS** (0x00) Obtención correcta de objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-236">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="629af-237">**TX_OPTION_ERROR** (0x08) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="629af-237">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="629af-238">**TX_PTR_ERROR** (0x03) Destino no válido.</span><span class="sxs-lookup"><span data-stu-id="629af-238">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="629af-239">**TX_SIZE_ERROR** (0x05) Tamaño no válido.</span><span class="sxs-lookup"><span data-stu-id="629af-239">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="629af-240">**TX_NO_INSTANCE** (0x0D) No se encontró el objeto.</span><span class="sxs-lookup"><span data-stu-id="629af-240">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="629af-241">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="629af-241">Allowed from</span></span>

<span data-ttu-id="629af-242">Subprocesos de módulo</span><span class="sxs-lookup"><span data-stu-id="629af-242">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="629af-243">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="629af-243">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="629af-244">Vea también</span><span class="sxs-lookup"><span data-stu-id="629af-244">See also</span></span>

- <span data-ttu-id="629af-245">txm_module_manager_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="629af-245">txm_module_manager_object_pointer_get</span></span>
