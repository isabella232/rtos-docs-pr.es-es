---
title: 'Capítulo 3: Descripción de los servicios del servidor PPPoE de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios del servicio PPPoE de Azure RTOS NetX (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815121"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a><span data-ttu-id="6d475-103">Capítulo 3: Descripción de los servicios del servidor PPPoE de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="6d475-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Server Services</span></span>

<span data-ttu-id="6d475-104">Este capítulo contiene una descripción de todos los servicios del servicio PPPoE de Azure RTOS NetX (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="6d475-104">This chapter contains a description of all Azure RTOS NetX PPPoE Server services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="6d475-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="6d475-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="6d475-106">**nx_pppoe_server_create**: *crea una instancia del servidor PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="6d475-106">**nx_pppoe_server_create**: *Create a PPPoE Server instance*</span></span>

- <span data-ttu-id="6d475-107">**nx_pppoe_server_ac_name_set**: *establece el nombre del concentrador de acceso*.</span><span class="sxs-lookup"><span data-stu-id="6d475-107">**nx_pppoe_server_ac_name_set**: *Set Access Concentrator name*</span></span>

- <span data-ttu-id="6d475-108">**nx_pppoe_server_delete**: *elimina una instancia del servidor PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="6d475-108">**nx_pppoe_server_delete**: *Delete a PPPoE Server instance*</span></span>

- <span data-ttu-id="6d475-109">**nx_pppoe_server_enable**: *habilita servicios del servidor PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="6d475-109">**nx_pppoe_server_enable**: *Enable PPPoE Server services*</span></span>

- <span data-ttu-id="6d475-110">**nx_pppoe_server_disable**: *deshabilita los servicios del servidor PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="6d475-110">**nx_pppoe_server_disable**: *Disable PPPoE Server services*</span></span>

- <span data-ttu-id="6d475-111">**nx_pppoe_server_callback_notify_set**: *establece funciones de notificación de devolución de llamada del servidor PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="6d475-111">**nx_pppoe_server_callback_notify_set**: *Set PPPoE Server callback notify functions*</span></span>

- <span data-ttu-id="6d475-112">**nx_pppoe_server_service_name_set**: *establece el nombre del servicio del servidor PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="6d475-112">**nx_pppoe_server_service_name_set**: *Set PPPoE Server service name*</span></span>

- <span data-ttu-id="6d475-113">**nx_pppoe_server_session_send**: *envía datos del servidor PPPoE a la sesión especificada*.</span><span class="sxs-lookup"><span data-stu-id="6d475-113">**nx_pppoe_server_session_send**: *Send PPPoE Server data to specified session*</span></span>

- <span data-ttu-id="6d475-114">**nx_pppoe_server_session_packet_send**: *envía un paquete del servidor PPPoE a la sesión especificada*.</span><span class="sxs-lookup"><span data-stu-id="6d475-114">**nx_pppoe_server_session_packet_send**: *Send PPPoE Server packet to specified session*</span></span>

- <span data-ttu-id="6d475-115">**nx_pppoe_server_session_terminate**: *finaliza la sesión PPPoE especificada*.</span><span class="sxs-lookup"><span data-stu-id="6d475-115">**nx_pppoe_server_session_terminate**: *Terminate the specified PPPoE session*</span></span>

- <span data-ttu-id="6d475-116">**nx_pppoe_server_session_get**: *obtiene la información de sesión especificada*.</span><span class="sxs-lookup"><span data-stu-id="6d475-116">**nx_pppoe_server_session_get**: *Get the specified session information*</span></span>

## <a name="nx_pppoe_server_create"></a><span data-ttu-id="6d475-117">nx_pppoe_server_create</span><span class="sxs-lookup"><span data-stu-id="6d475-117">nx_pppoe_server_create</span></span>

<span data-ttu-id="6d475-118">Crea una instancia del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-118">Create a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-119">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-119">Prototype</span></span>

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a><span data-ttu-id="6d475-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-120">Description</span></span>

<span data-ttu-id="6d475-121">Este servicio crea una instancia del servidor PPPoE con el controlador de vínculo proporcionado por el usuario para la instancia de IP NetX especificada.</span><span class="sxs-lookup"><span data-stu-id="6d475-121">This service creates a PPPoE Server instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="6d475-122">Si el controlador de vínculo no se ha inicializado y está habilitado, el software del servidor PPPoE es responsable de inicializar el controlador de vínculo.</span><span class="sxs-lookup"><span data-stu-id="6d475-122">If link driver has not been initialized, and enabled, PPPoE sever software is responsible initializing the link driver.</span></span>

<span data-ttu-id="6d475-123">Además, la aplicación debe proporcionar un grupo de paquetes creado previamente para la instancia del servidor PPPoE que se va a utilizar para la asignación interna de paquetes.</span><span class="sxs-lookup"><span data-stu-id="6d475-123">In addition, the application must supply a previously created packet pool for the PPPoE Server instance to use for internal packet allocation.</span></span>

<span data-ttu-id="6d475-124">Tenga en cuenta que, por lo general, se recomienda crear el subproceso de IP de NetX con una prioridad más alta que la prioridad de subproceso del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-124">Note that it is generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Server thread priority.</span></span> <span data-ttu-id="6d475-125">Consulte el servicio *nx_ip_create* para obtener más información sobre cómo especificar la prioridad del subproceso de IP.</span><span class="sxs-lookup"><span data-stu-id="6d475-125">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-126">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-126">Input Parameters</span></span>

- <span data-ttu-id="6d475-127">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-127">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="6d475-128">**nombre**: nombre de esta instancia del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-128">**name**: Name of this PPPoE Server instance.</span></span>
- <span data-ttu-id="6d475-129">**ip_ptr**: puntero al bloque de control de la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="6d475-129">**ip_ptr**: Pointer to control block for IP instance.</span></span>
- <span data-ttu-id="6d475-130">**interface_index**: índice de interfaz.</span><span class="sxs-lookup"><span data-stu-id="6d475-130">**interface_index**: Interface index.</span></span>
- <span data-ttu-id="6d475-131">**pppoe_link_driver**: controlador de vínculo proporcionado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="6d475-131">**pppoe_link_driver**: User supplied link driver.</span></span>
- <span data-ttu-id="6d475-132">**pool_ptr**: puntero al grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="6d475-132">**pool_ptr**: Pointer to packet pool.</span></span>
- <span data-ttu-id="6d475-133">**stack_ptr**: puntero al inicio del área de pila del subproceso del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-133">**stack_ptr**: Pointer to start of PPPoE Server thread's stack area.</span></span>
- <span data-ttu-id="6d475-134">**stack_size**: tamaño en bytes de la pila del subproceso.</span><span class="sxs-lookup"><span data-stu-id="6d475-134">**stack_size**: Size in bytes in the thread's stack.</span></span>
- <span data-ttu-id="6d475-135">**prioridad**: prioridad de los subprocesos de servidor PPPoE internos (1-31).</span><span class="sxs-lookup"><span data-stu-id="6d475-135">**priority**: Priority of internal PPPoE Server threads (1-31).</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-136">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-136">Return Values</span></span>

- <span data-ttu-id="6d475-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) creación correcta del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server create.</span></span>
- <span data-ttu-id="6d475-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) servidor PPPoE no válido, IP, grupo de paquetes o puntero de pila.</span><span class="sxs-lookup"><span data-stu-id="6d475-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="6d475-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) interfaz no válida.</span><span class="sxs-lookup"><span data-stu-id="6d475-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Invalid interface.</span></span>
- <span data-ttu-id="6d475-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) tamaño de carga no válido del grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="6d475-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid payload size of packet pool.</span></span>
- <span data-ttu-id="6d475-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) tamaño de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Invalid memory size.</span></span>
- <span data-ttu-id="6d475-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) prioridad no válida del subproceso del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Invalid priority of PPPoE Server thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-143">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-143">Allowed From</span></span>

<span data-ttu-id="6d475-144">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-145">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-145">Example</span></span>

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a><span data-ttu-id="6d475-146">nx_pppoe_server_delete</span><span class="sxs-lookup"><span data-stu-id="6d475-146">nx_pppoe_server_delete</span></span>

<span data-ttu-id="6d475-147">Elimina una instancia del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-147">Delete a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-148">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-148">Prototype</span></span>

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="6d475-149">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-149">Description</span></span>

<span data-ttu-id="6d475-150">Este servicio elimina la instancia del servidor PPPoE creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="6d475-150">This service deletes the previously created PPPoE Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-151">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-151">Input Parameters</span></span>

- <span data-ttu-id="6d475-152">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-152">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-153">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-153">Return Values</span></span>

- <span data-ttu-id="6d475-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="6d475-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-156">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-156">Allowed From</span></span>

<span data-ttu-id="6d475-157">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-158">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-158">Example</span></span>

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a><span data-ttu-id="6d475-159">nx_pppoe_server_enable</span><span class="sxs-lookup"><span data-stu-id="6d475-159">nx_pppoe_server_enable</span></span>

<span data-ttu-id="6d475-160">Habilita el servicio del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-160">Enable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-161">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-161">Prototype</span></span>

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="6d475-162">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-162">Description</span></span>

<span data-ttu-id="6d475-163">Este servicio habilita los servicios del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-163">This service enables the PPPoE Server services.</span></span>

> [!NOTE]
> <span data-ttu-id="6d475-164">Se debe llamar a esta función después de *nx_pppoe_server_create* y *nx_pppoe_server_callback_notify_set*.</span><span class="sxs-lookup"><span data-stu-id="6d475-164">This function must be called after *nx_pppoe_server_create* and *nx_pppoe_server_callback_notify_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-165">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-165">Input Parameters</span></span>

- <span data-ttu-id="6d475-166">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-166">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-167">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-167">Return Values</span></span>

- <span data-ttu-id="6d475-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="6d475-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-170">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-170">Allowed From</span></span>

<span data-ttu-id="6d475-171">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-171">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-172">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-172">Example</span></span>

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a><span data-ttu-id="6d475-173">nx_pppoe_server_disable</span><span class="sxs-lookup"><span data-stu-id="6d475-173">nx_pppoe_server_disable</span></span>

<span data-ttu-id="6d475-174">Deshabilita el servicio del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-174">Disable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-175">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-175">Prototype</span></span>

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="6d475-176">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-176">Description</span></span>

<span data-ttu-id="6d475-177">Este servicio deshabilita los servicios del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-177">This service disables the PPPoE Server services.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-178">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-178">Input Parameters</span></span>

- <span data-ttu-id="6d475-179">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-179">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-180">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-180">Return Values</span></span>

- <span data-ttu-id="6d475-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="6d475-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-183">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-183">Allowed From</span></span>

<span data-ttu-id="6d475-184">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-184">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-185">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-185">Example</span></span>

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a><span data-ttu-id="6d475-186">nx_pppoe_server_callback_notify_set</span><span class="sxs-lookup"><span data-stu-id="6d475-186">nx_pppoe_server_callback_notify_set</span></span>

<span data-ttu-id="6d475-187">Establece funciones de notificación de devolución de llamada del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-187">Set PPPoE Server callback notify functions</span></span> 

### <a name="prototype"></a><span data-ttu-id="6d475-188">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-188">Prototype</span></span>

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a><span data-ttu-id="6d475-189">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-189">Description</span></span>

<span data-ttu-id="6d475-190">Este servicio establece las funciones de notificación de devolución de llamada del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-190">This service sets PPPoE Server callback notify functions.</span></span>

> [!NOTE]
> <span data-ttu-id="6d475-191">Se debe llamar a esta función antes de *nx_pppoe_server_enable*, y se debe establecer el puntero de función pppoe_data_receive_notify, si no es así, *nx_pppoe_server_enable* producirá un error.</span><span class="sxs-lookup"><span data-stu-id="6d475-191">This function must be called before *nx_pppoe_server_enabl, and* the pppoe_data_receive_notify function pointer must be set, if not, *nx_pppoe_server_enable* will be failure.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-192">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-192">Input Parameters</span></span>

- <span data-ttu-id="6d475-193">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-193">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="6d475-194">**pppoe_discover_initiation_notify**: función de aplicación a la que se llama cada vez que se recibe el mensaje de inicio de la detección de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-194">**pppoe_discover_initiation_notify**: Application function that is called whenever PPPoE discover initiation message is received.</span></span> <span data-ttu-id="6d475-195">Si este valor es NULL, la función de devolución de llamada de detección de inicio está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="6d475-195">If this value is NULL, discover initiation callback function is disabled.</span></span>
- <span data-ttu-id="6d475-196">**pppoe_discover_request_notify**: función de aplicación a la que se llama cada vez que se recibe el mensaje de solicitud de detección de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-196">**pppoe_discover_request_notify**: Application function that is called whenever PPPoE discover request message is received.</span></span> <span data-ttu-id="6d475-197">Si este valor es NULL, la función de devolución de llamada de solicitud de detección está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="6d475-197">If this value is NULL, discover request callback function is disabled.</span></span>
- <span data-ttu-id="6d475-198">**pppoe_discover_terminate_notify**: función de aplicación a la que se llama siempre que se recibe el mensaje de finalización de la detección de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-198">**pppoe_discover_terminate_notify**: Application function that is called whenever PPPoE discover terminate message is received.</span></span> <span data-ttu-id="6d475-199">Si este valor es NULL, se deshabilita la función de devolución de llamada de finalización.</span><span class="sxs-lookup"><span data-stu-id="6d475-199">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="6d475-200">**pppoe_discover_terminate_confirm**: función de aplicación a la que se llama cada vez que se envía un mensaje de finalización de la detección de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-200">**pppoe_discover_terminate_confirm**: Application function that is called whenever PPPoE discover terminate message is sent.</span></span> <span data-ttu-id="6d475-201">Si este valor es NULL, se deshabilita la función de devolución de llamada de finalización.</span><span class="sxs-lookup"><span data-stu-id="6d475-201">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="6d475-202">**pppoe_data_receive_notify**: función de aplicación a la que se llama cada vez que se recibe un mensaje de datos de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-202">**pppoe_data_receive_notify**: Application function that is called whenever PPPoE data message is received.</span></span> <span data-ttu-id="6d475-203">Este valor no se debe cambiar.</span><span class="sxs-lookup"><span data-stu-id="6d475-203">This value must not be zero.</span></span>
- <span data-ttu-id="6d475-204">**pppoe_data_send_notify**: función de aplicación a la que se llama cada vez que se envía un mensaje de datos de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-204">**pppoe_data_send_notify**: Application function that is called whenever PPPoE data message is sent.</span></span> <span data-ttu-id="6d475-205">Si este valor es NULL, la función de devolución de llamada de envío de datos está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="6d475-205">If this value is NULL, data send callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-206">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-206">Return Values</span></span>

- <span data-ttu-id="6d475-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="6d475-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero del servidor PPPoE o puntero de función no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer or function pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-209">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-209">Allowed From</span></span>

<span data-ttu-id="6d475-210">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-210">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-211">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-211">Example</span></span>

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a><span data-ttu-id="6d475-212">nx_pppoe_server_ac_name_set</span><span class="sxs-lookup"><span data-stu-id="6d475-212">nx_pppoe_server_ac_name_set</span></span>

<span data-ttu-id="6d475-213">Establece el nombre del concentrador de acceso.</span><span class="sxs-lookup"><span data-stu-id="6d475-213">Set Access Concentrator name</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-214">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-214">Prototype</span></span>

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a><span data-ttu-id="6d475-215">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-215">Description</span></span>

<span data-ttu-id="6d475-216">Esta función establece la llamada de función de nombre de concentrador de acceso.</span><span class="sxs-lookup"><span data-stu-id="6d475-216">This function set Access Concentrator name function call.</span></span>

> [!NOTE]
> <span data-ttu-id="6d475-217">La cadena de ac_name debe terminar en NULL y la longitud de ac_name coincide con la longitud especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="6d475-217">The string of ac_name must be NULL-terminated and length of ac_name matches the length specified in the argument list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-218">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-218">Input Parameters</span></span>

- <span data-ttu-id="6d475-219">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-219">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="6d475-220">**ac_name**: nombre del concentrador de acceso.</span><span class="sxs-lookup"><span data-stu-id="6d475-220">**ac_name**: Access Concentrator name.</span></span>
- <span data-ttu-id="6d475-221">**ac_name_length**: longitud de ac_ame.</span><span class="sxs-lookup"><span data-stu-id="6d475-221">**ac_name_length**: Length of ac_ame.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-222">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-222">Return Values</span></span>

- <span data-ttu-id="6d475-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) conjunto de servidores PPPoE correctos.</span><span class="sxs-lookup"><span data-stu-id="6d475-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server set.</span></span>
- <span data-ttu-id="6d475-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) servidor PPPoE no válido, IP, grupo de paquetes o puntero de pila.</span><span class="sxs-lookup"><span data-stu-id="6d475-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="6d475-225">**NX_SIZE_ERROR**: (0x09) error de comprobación de name_length.</span><span class="sxs-lookup"><span data-stu-id="6d475-225">**NX_SIZE_ERROR**: (0x09) Check name_length fail.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-226">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-226">Allowed From</span></span>

<span data-ttu-id="6d475-227">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-227">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-228">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-228">Example</span></span>

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a><span data-ttu-id="6d475-229">nx_pppoe_server_service_name_set</span><span class="sxs-lookup"><span data-stu-id="6d475-229">nx_pppoe_server_service_name_set</span></span>

<span data-ttu-id="6d475-230">Establece el nombre de servicio del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-230">Set PPPoE Server service name</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-231">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-231">Prototype</span></span>

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a><span data-ttu-id="6d475-232">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-232">Description</span></span>

<span data-ttu-id="6d475-233">Este servicio establece el nombre del servicio de servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-233">This service sets PPPoE Server service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-234">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-234">Input Parameters</span></span>

- <span data-ttu-id="6d475-235">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-235">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-236">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-236">Return Values</span></span>

- <span data-ttu-id="6d475-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="6d475-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-239">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-239">Allowed From</span></span>

<span data-ttu-id="6d475-240">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-240">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-241">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-241">Example</span></span>

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a><span data-ttu-id="6d475-242">nx_pppoe_server_session_send</span><span class="sxs-lookup"><span data-stu-id="6d475-242">nx_pppoe_server_session_send</span></span>

<span data-ttu-id="6d475-243">Envía datos del servidor PPPoE a la sesión especificada.</span><span class="sxs-lookup"><span data-stu-id="6d475-243">Send PPPoE Server data to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-244">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-244">Prototype</span></span>

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a><span data-ttu-id="6d475-245">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-245">Description</span></span>

<span data-ttu-id="6d475-246">Este servicio envía un marco PPPoE mediante el identificador de sesión especificado.</span><span class="sxs-lookup"><span data-stu-id="6d475-246">This service sends PPPoE frame using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-247">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-247">Input Parameters</span></span>

- <span data-ttu-id="6d475-248">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-248">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="6d475-249">**session_index**: índice de la sesión.</span><span class="sxs-lookup"><span data-stu-id="6d475-249">**session_index**: The index of session.</span></span>
- <span data-ttu-id="6d475-250">**data_ptr**: puntero al inicio de la trama de datos del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-250">**data_ptr**: Pointer to start of PPPoE Server data frame.</span></span>
- <span data-ttu-id="6d475-251">**Data_length**: longitud de la trama de datos del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-251">**data_length**: Length of PPPoE Server data frame.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-252">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-252">Return Values</span></span>

- <span data-ttu-id="6d475-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="6d475-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="6d475-255">NX_PPPOE_SERVER_NOT_ENABLED: el servicio del servidor PPPoE de (0xC6) no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="6d475-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="6d475-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) índice de sesión PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="6d475-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) no se ha establecido la sesión PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-258">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-258">Allowed From</span></span>

<span data-ttu-id="6d475-259">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-259">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-260">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-260">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a><span data-ttu-id="6d475-261">nx_pppoe_server_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="6d475-261">nx_pppoe_server_session_packet_send</span></span>

<span data-ttu-id="6d475-262">Envía paquete del servidor PPPoE a la sesión especificada.</span><span class="sxs-lookup"><span data-stu-id="6d475-262">Send PPPoE Server packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-263">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-263">Prototype</span></span>

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="6d475-264">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-264">Description</span></span>

<span data-ttu-id="6d475-265">Este servicio envía un paquete PPPoE mediante el identificador de sesión especificado.</span><span class="sxs-lookup"><span data-stu-id="6d475-265">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-266">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-266">Input Parameters</span></span>

- <span data-ttu-id="6d475-267">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-267">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="6d475-268">**session_index**: índice de la sesión.</span><span class="sxs-lookup"><span data-stu-id="6d475-268">**session_index**: The index of session.</span></span>
- <span data-ttu-id="6d475-269">**packet_ptr**: puntero al paquete PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-269">**packet_ptr**: Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-270">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-270">Return Values</span></span>

- <span data-ttu-id="6d475-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="6d475-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="6d475-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) paquete del servidor PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid PPPoE Server packet.</span></span>
- <span data-ttu-id="6d475-274">NX_PPPOE_SERVER_NOT_ENABLED: el servicio del servidor PPPoE de (0xC6) no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="6d475-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="6d475-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) índice de sesión PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="6d475-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) no se ha establecido la sesión PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-277">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-277">Allowed From</span></span>

<span data-ttu-id="6d475-278">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-279">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-279">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a><span data-ttu-id="6d475-280">nx_pppoe_server_session_terminate</span><span class="sxs-lookup"><span data-stu-id="6d475-280">nx_pppoe_server_session_terminate</span></span>

<span data-ttu-id="6d475-281">Finaliza la sesión de PPPoE especificada.</span><span class="sxs-lookup"><span data-stu-id="6d475-281">Terminate the specified PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-282">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-282">Prototype</span></span>

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a><span data-ttu-id="6d475-283">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-283">Description</span></span>

<span data-ttu-id="6d475-284">Este servicio finaliza la sesión de PPPoE especificada.</span><span class="sxs-lookup"><span data-stu-id="6d475-284">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-285">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-285">Input Parameters</span></span>

- <span data-ttu-id="6d475-286">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-286">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="6d475-287">**session_index**: índice de la sesión.</span><span class="sxs-lookup"><span data-stu-id="6d475-287">**session_index**: The index of session.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-288">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-288">Return Values</span></span>

- <span data-ttu-id="6d475-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="6d475-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="6d475-291">NX_PPPOE_SERVER_NOT_ENABLED: el servicio del servidor PPPoE de (0xC6) no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="6d475-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="6d475-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) índice de sesión PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="6d475-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) no se ha establecido la sesión PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-294">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-294">Allowed From</span></span>

<span data-ttu-id="6d475-295">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-296">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-296">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a><span data-ttu-id="6d475-297">nx_pppoe_server_session_get</span><span class="sxs-lookup"><span data-stu-id="6d475-297">nx_pppoe_server_session_get</span></span>

<span data-ttu-id="6d475-298">Obtiene la información de sesión de PPPoE especificada.</span><span class="sxs-lookup"><span data-stu-id="6d475-298">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-299">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-299">Prototype</span></span>

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="6d475-300">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-300">Description</span></span>

<span data-ttu-id="6d475-301">Este servicio obtiene la información de sesión de PPPoE especificada, la dirección física del cliente y el identificador de sesión.</span><span class="sxs-lookup"><span data-stu-id="6d475-301">This service gets the specified PPPoE session information, client physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-302">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-302">Input Parameters</span></span>

- <span data-ttu-id="6d475-303">**pppoe_server_ptr**: puntero al bloque de control del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-303">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="6d475-304">**session_index**: índice de la sesión.</span><span class="sxs-lookup"><span data-stu-id="6d475-304">**session_index**: The index of session.</span></span>
- <span data-ttu-id="6d475-305">**client_mac_msw**: puntero MSW de dirección física del cliente.</span><span class="sxs-lookup"><span data-stu-id="6d475-305">**client_mac_msw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="6d475-306">**client_mac_lsw**: puntero MSW de dirección física del cliente.</span><span class="sxs-lookup"><span data-stu-id="6d475-306">**client_mac_lsw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="6d475-307">**session_id**: puntero de identificador de sesión.</span><span class="sxs-lookup"><span data-stu-id="6d475-307">**session_id**: Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-308">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-308">Return Values</span></span>

- <span data-ttu-id="6d475-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) eliminación correcta del servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="6d475-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) puntero de servidor PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="6d475-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) índice de sesión PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="6d475-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="6d475-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) no se ha establecido la sesión PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-313">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-313">Allowed From</span></span>

<span data-ttu-id="6d475-314">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-314">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-315">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-315">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a><span data-ttu-id="6d475-316">PppInitInd</span><span class="sxs-lookup"><span data-stu-id="6d475-316">PppInitInd</span></span>

<span data-ttu-id="6d475-317">Configura el nombre de servicio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="6d475-317">Configure the default Service Name</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-318">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-318">Prototype</span></span>

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="6d475-319">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-319">Description</span></span>

<span data-ttu-id="6d475-320">El software de PPPoE expondrá esta función para permitir que el software de TTP configure el "nombre de servicio predeterminado" que debe usar PPPoE para filtrar las solicitudes de PADI entrantes.</span><span class="sxs-lookup"><span data-stu-id="6d475-320">The PPPoE software will expose this function to allow TTP's software to configure the 'default Service Name' that the PPPoE should use to filter incoming PADI requests.</span></span> <span data-ttu-id="6d475-321">El software de PPPoE debe recordar esta información y, si se recibe un paquete PADI que contiene un nombre de servicio que coincide con, debe llamar a PppDiscoverReq.</span><span class="sxs-lookup"><span data-stu-id="6d475-321">The PPPoE software should remember this information, and if a PADI packet is received containing a service name that matches then it should call PppDiscoverReq.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-322">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-322">Input Parameters</span></span>

- <span data-ttu-id="6d475-323">**length**: longitud del nombre de servicio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="6d475-323">**length**: Length of default service name.</span></span>
- <span data-ttu-id="6d475-324">**aData**: nombre de servicio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="6d475-324">**aData**: Default service name.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-325">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-325">Return Values</span></span>

<span data-ttu-id="6d475-326">**None**</span><span class="sxs-lookup"><span data-stu-id="6d475-326">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-327">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-327">Allowed From</span></span>

<span data-ttu-id="6d475-328">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-329">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-329">Example</span></span>

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a><span data-ttu-id="6d475-330">PppDiscoverCnf</span><span class="sxs-lookup"><span data-stu-id="6d475-330">PppDiscoverCnf</span></span>

<span data-ttu-id="6d475-331">Define el campo de nombre de servicio del paquete PADO.</span><span class="sxs-lookup"><span data-stu-id="6d475-331">Define the Service Name field of the PADO packet</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-332">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-332">Prototype</span></span>

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="6d475-333">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-333">Description</span></span>

<span data-ttu-id="6d475-334">El software de PPPoE expondrá esta función para permitir que el software de TTP defina el campo de nombre de servicio del paquete PADO.</span><span class="sxs-lookup"><span data-stu-id="6d475-334">The PPPoE software will expose this function to allow TTP's software to define the Service Name field of the PADO packet.</span></span> <span data-ttu-id="6d475-335">El software de PPPoE no debe enviar el paquete PADO hasta que se llame a PppDiscoverCnf.</span><span class="sxs-lookup"><span data-stu-id="6d475-335">The PPPoE software should not send the PADO until the PppDiscoverCnf is called.</span></span>

<span data-ttu-id="6d475-336">El paquete PADO debe contener un nombre de concentrador de acceso (con el identificador de etiqueta 0x0102, tal y como se define en RFC2516), definido en la inicialización del software de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-336">The PADO packet shall contain an access concentrator name (using the tag id 0x0102 as defined in RFC2516), defined on initialisation of the PPPoE software.</span></span>

<span data-ttu-id="6d475-337">Se pueden pasar varios nombres de servicio en aData, y cada nombre debe terminar en NULL.</span><span class="sxs-lookup"><span data-stu-id="6d475-337">Multiple service names can be passed in aData, with each name to be null terminated.</span></span>

<span data-ttu-id="6d475-338">El carácter NULL se usa como separador para proporcionar la máxima flexibilidad en caso de que otros comandos deban pasarse como parte del nombre del servicio.</span><span class="sxs-lookup"><span data-stu-id="6d475-338">Null character is used as a separator to provide maximum flexibility in case other commands need to be passed in as part of the service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-339">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-339">Input Parameters</span></span>

- <span data-ttu-id="6d475-340">**length**: longitud del nombre de servicio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="6d475-340">**length**: Length of default service name.</span></span>
- <span data-ttu-id="6d475-341">**aData**: nombre de servicio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="6d475-341">**aData**: Default service name.</span></span>
- <span data-ttu-id="6d475-342">**interfaceHandle**: identificador de interfaz.</span><span class="sxs-lookup"><span data-stu-id="6d475-342">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-343">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-343">Return Values</span></span>

<span data-ttu-id="6d475-344">**None**</span><span class="sxs-lookup"><span data-stu-id="6d475-344">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-345">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-345">Allowed From</span></span>

<span data-ttu-id="6d475-346">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-346">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-347">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-347">Example</span></span>

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a><span data-ttu-id="6d475-348">PppOpenCnf</span><span class="sxs-lookup"><span data-stu-id="6d475-348">PppOpenCnf</span></span>

<span data-ttu-id="6d475-349">Acepta o rechaza la sesión PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-349">Accept or reject the PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-350">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-350">Prototype</span></span>

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="6d475-351">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-351">Description</span></span>

<span data-ttu-id="6d475-352">El software de PPPoE expondrá esta función para permitir que el software de TTP acepte o rechace la sesión de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-352">The PPPoE software will expose this function to allow TTP's software to accept or reject the PPPoE session.</span></span>  <span data-ttu-id="6d475-353">En respuesta a esta pila de PPPoE, se debe aceptar la conexión y asignar un número de Session_ID PPPoE único asociado a interfaceHandle.</span><span class="sxs-lookup"><span data-stu-id="6d475-353">In response to this the PPPoE stack should accept the connection and assign a unique PPPoE Session_ID number associated with the interfaceHandle.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-354">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-354">Input Parameters</span></span>

- <span data-ttu-id="6d475-355">**Aceptar**: NX_TRUE si se va a aceptar la conexión.</span><span class="sxs-lookup"><span data-stu-id="6d475-355">**accept**: NX_TRUE if the connection is to be accepted.</span></span>
- <span data-ttu-id="6d475-356">**interfaceHandle**: identificador de interfaz.</span><span class="sxs-lookup"><span data-stu-id="6d475-356">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-357">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-357">Return Values</span></span>

<span data-ttu-id="6d475-358">**None**</span><span class="sxs-lookup"><span data-stu-id="6d475-358">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-359">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-359">Allowed From</span></span>

<span data-ttu-id="6d475-360">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-360">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-361">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-361">Example</span></span>

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a><span data-ttu-id="6d475-362">PppCloseInd</span><span class="sxs-lookup"><span data-stu-id="6d475-362">PppCloseInd</span></span>

<span data-ttu-id="6d475-363">Cierra una sesión de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-363">Close a PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-364">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-364">Prototype</span></span>

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a><span data-ttu-id="6d475-365">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-365">Description</span></span>

<span data-ttu-id="6d475-366">El software de PPPoE expondrá esta función para permitir que el software de TTP cierre una sesión de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-366">The PPPoE software will expose this function to allow TTP's software to close a PPPoE session.</span></span>

<span data-ttu-id="6d475-367">El software de PPPoE indicará la cadena de código de causa de la etiqueta de Generic-Error (0x0203) en el mensaje PADT.</span><span class="sxs-lookup"><span data-stu-id="6d475-367">The PPPoE software will indicate the cause code string in the Generic-Error tag (0x0203) in the PADT message</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-368">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-368">Input Parameters</span></span>

- <span data-ttu-id="6d475-369">**interfaceHandle**: identificador de interfaz.</span><span class="sxs-lookup"><span data-stu-id="6d475-369">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="6d475-370">**causeCode**: cadena terminada en NULL para enviar información sobre la razón por la que se cierra la conexión desde el servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-370">**causeCode**: Null terminated string for sending information about the reason for closing the connection from the PPPoE Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-371">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-371">Return Values</span></span>

<span data-ttu-id="6d475-372">**None**</span><span class="sxs-lookup"><span data-stu-id="6d475-372">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-373">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-373">Allowed From</span></span>

<span data-ttu-id="6d475-374">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-374">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-375">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-375">Example</span></span>

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a><span data-ttu-id="6d475-376">PppCloseCnf</span><span class="sxs-lookup"><span data-stu-id="6d475-376">PppCloseCnf</span></span>

<span data-ttu-id="6d475-377">Confirma que se ha liberado el identificador.</span><span class="sxs-lookup"><span data-stu-id="6d475-377">Confirm that the handle has been freed</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-378">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-378">Prototype</span></span>

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="6d475-379">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-379">Description</span></span>

<span data-ttu-id="6d475-380">El software de PPPoE expondrá esta función para permitir que el software de TTP confirme que el identificador se ha liberado.</span><span class="sxs-lookup"><span data-stu-id="6d475-380">The PPPoE software will expose this function to allow TTP's software to confirm that the handle has been freed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-381">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-381">Input Parameters</span></span>

- <span data-ttu-id="6d475-382">**interfaceHandle**: identificador de interfaz.</span><span class="sxs-lookup"><span data-stu-id="6d475-382">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-383">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-383">Return Values</span></span>

<span data-ttu-id="6d475-384">**None**</span><span class="sxs-lookup"><span data-stu-id="6d475-384">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-385">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-385">Allowed From</span></span>

<span data-ttu-id="6d475-386">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-386">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-387">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-387">Example</span></span>

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a><span data-ttu-id="6d475-388">PppTransmitDataCnf</span><span class="sxs-lookup"><span data-stu-id="6d475-388">PppTransmitDataCnf</span></span>

<span data-ttu-id="6d475-389">Permite la confirmación de los datos de PPP anteriores.</span><span class="sxs-lookup"><span data-stu-id="6d475-389">Allow a preceding PPP data to be acknowledged</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-390">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-390">Prototype</span></span>

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a><span data-ttu-id="6d475-391">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-391">Description</span></span>

<span data-ttu-id="6d475-392">El software de PPPoE expondrá esta función para permitir que se confirme un PppTransmitDataReq anterior.</span><span class="sxs-lookup"><span data-stu-id="6d475-392">The PPPoE software will expose this function to allow a preceding PppTransmitDataReq to be acknowledged.</span></span>  <span data-ttu-id="6d475-393">Implica que el software de TTP está listo para una nueva trama PPP de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6d475-393">It implies that TTP's software is ready for a new PPP frame from PPPoE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-394">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-394">Input Parameters</span></span>

- <span data-ttu-id="6d475-395">**interfaceHandle**: identificador de interfaz.</span><span class="sxs-lookup"><span data-stu-id="6d475-395">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="6d475-396">**aData**: puntero el búfer de datos de PPP que se ha aceptado.</span><span class="sxs-lookup"><span data-stu-id="6d475-396">**aData**: Pointer the PPP data buffer that has been accepted.</span></span>
- <span data-ttu-id="6d475-397">**Packet_id**: identificador de paquete.</span><span class="sxs-lookup"><span data-stu-id="6d475-397">**Packet_id**: Packet identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-398">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-398">Return Values</span></span>

<span data-ttu-id="6d475-399">**None**</span><span class="sxs-lookup"><span data-stu-id="6d475-399">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-400">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-400">Allowed From</span></span>

<span data-ttu-id="6d475-401">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-401">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-402">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-402">Example</span></span>

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a><span data-ttu-id="6d475-403">PppReceiveDataInd</span><span class="sxs-lookup"><span data-stu-id="6d475-403">PppReceiveDataInd</span></span>

<span data-ttu-id="6d475-404">Recibe datos de la transmisión a través de Ethernet.</span><span class="sxs-lookup"><span data-stu-id="6d475-404">Receive data from transmission over Ethernet</span></span>

### <a name="prototype"></a><span data-ttu-id="6d475-405">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6d475-405">Prototype</span></span>

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="6d475-406">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d475-406">Description</span></span>

<span data-ttu-id="6d475-407">El software de PPPoE expondrá esta función para recibir datos de transmisión a través de Ethernet.</span><span class="sxs-lookup"><span data-stu-id="6d475-407">The PPPoE software will expose this function to receive data for transmission over Ethernet</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d475-408">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6d475-408">Input Parameters</span></span>

- <span data-ttu-id="6d475-409">**interfaceHandle**: identificador de interfaz.</span><span class="sxs-lookup"><span data-stu-id="6d475-409">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="6d475-410">**length**: el número de bytes en aData.</span><span class="sxs-lookup"><span data-stu-id="6d475-410">**length**: The number of bytes in aData.</span></span>
- <span data-ttu-id="6d475-411">**aData**: búfer de datos que contiene el marco de datos de PPP.</span><span class="sxs-lookup"><span data-stu-id="6d475-411">**aData**: Data buffer containing the frame of PPP data.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d475-412">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6d475-412">Return Values</span></span>

<span data-ttu-id="6d475-413">**None**</span><span class="sxs-lookup"><span data-stu-id="6d475-413">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d475-414">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6d475-414">Allowed From</span></span>

<span data-ttu-id="6d475-415">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="6d475-415">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="6d475-416">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d475-416">Example</span></span>

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```