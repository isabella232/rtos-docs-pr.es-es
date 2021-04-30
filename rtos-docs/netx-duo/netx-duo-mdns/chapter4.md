---
title: 'Capítulo 4: Descripción de los servicios mDNS'
description: Este capítulo contiene una descripción de todos los servicios mDNS de NetX.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89df0ab5f09be8ad50a27d23bae8b20d71caa0b4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814665"
---
# <a name="chapter-4---description-of-mdns-services"></a><span data-ttu-id="56800-103">Capítulo 4: Descripción de los servicios mDNS</span><span class="sxs-lookup"><span data-stu-id="56800-103">Chapter 4 - Description of mDNS services</span></span>

<span data-ttu-id="56800-104">Este capítulo contiene una descripción de todos los servicios mDNS de NetX (se enumeran a continuación).</span><span class="sxs-lookup"><span data-stu-id="56800-104">This chapter contains a description of all NetX mDNS services (listed below).</span></span>

> [!NOTE]
> <span data-ttu-id="56800-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="56800-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_mdns_create"></a><span data-ttu-id="56800-106">nx_mdns_create</span><span class="sxs-lookup"><span data-stu-id="56800-106">nx_mdns_create</span></span>

<span data-ttu-id="56800-107">Crear una instancia de mDNS</span><span class="sxs-lookup"><span data-stu-id="56800-107">Create an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-108">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-108">Prototype</span></span>

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a><span data-ttu-id="56800-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-109">Description</span></span>

<span data-ttu-id="56800-110">Este servicio crea una instancia de mDNS en la instancia de IP específica y los recursos asociados.</span><span class="sxs-lookup"><span data-stu-id="56800-110">This service creates an mDNS instance on the specific IP instance and associated resources.</span></span> <span data-ttu-id="56800-111">También se crea un subproceso para controlar los mensajes de mDNS entrantes, para responder a las consultas y para transmitir periódicamente mensajes de consulta.</span><span class="sxs-lookup"><span data-stu-id="56800-111">A thread is also created to handle incoming mDNS messages, to respond to queries, and to periodically transmit query messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-112">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-112">Input Parameters</span></span>

- <span data-ttu-id="56800-113">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-113">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-114">**ip_ptr** Puntero a la instancia de IP asociada.</span><span class="sxs-lookup"><span data-stu-id="56800-114">**ip_ptr** Pointer to the associated IP instance.</span></span>
- <span data-ttu-id="56800-115">**packet_pool** Puntero a un grupo de paquetes válido.</span><span class="sxs-lookup"><span data-stu-id="56800-115">**packet_pool** Pointer to a valid packet pool.</span></span>
- <span data-ttu-id="56800-116">**priority** Prioridad del subproceso de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-116">**priority** Priority of the mDNS thread.</span></span>
- <span data-ttu-id="56800-117">**stack_ptr** Puntero al área de pila del subproceso de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-117">**stack_ptr** Pointer to the stack area for the mDNS thread</span></span>
- <span data-ttu-id="56800-118">**stack_size** Tamaño del área de pila.</span><span class="sxs-lookup"><span data-stu-id="56800-118">**stack_size** Size of the stack area.</span></span>
- <span data-ttu-id="56800-119">**host_name** Nombre de host asignado a este nodo.</span><span class="sxs-lookup"><span data-stu-id="56800-119">**host_name** Host name assigned to this node.</span></span>
- <span data-ttu-id="56800-120">**local_service_cache** Espacio de almacenamiento para servicios registrados locales.</span><span class="sxs-lookup"><span data-stu-id="56800-120">**local_service_cache** Storage space for local registered services.</span></span>
- <span data-ttu-id="56800-121">**local_service_cache_size** Tamaño de la caché de servicios local.</span><span class="sxs-lookup"><span data-stu-id="56800-121">**local_service_cache_size** Size of the local service cache.</span></span>
- <span data-ttu-id="56800-122">**peer_service_cache** Espacio de almacenamiento para la información de servicio recibida.</span><span class="sxs-lookup"><span data-stu-id="56800-122">**peer_service_cache** Storage space for service information received</span></span>
- <span data-ttu-id="56800-123">**peer_service_cache_size** Tamaño de la caché de servicio del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="56800-123">**peer_service_cache_size** Size of the peer service cache</span></span>
- <span data-ttu-id="56800-124">**probing_notify** Función de devolución de llamada opcional invocada al final de la operación de sondeo.</span><span class="sxs-lookup"><span data-stu-id="56800-124">**probing_notify** Optional callback function invoked at the end of the probing operation.</span></span> <span data-ttu-id="56800-125">Notifica a la aplicación si el nombre de host (cuando se habilita mDNS en una interfaz local) o el nombre del servicio (después de registrar un servicio) es único.</span><span class="sxs-lookup"><span data-stu-id="56800-125">It notifies the application whether or not the host name (when enabling mDNS on a local interface), or the service name (after registering a service) is unique.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-126">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-126">Return Values</span></span>

- <span data-ttu-id="56800-127">**NX_SUCCESS** (0x00) Se creó correctamente la instancia de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-127">**NX_SUCCESS** (0x00) Successfully created mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-128">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-128">Allowed From</span></span>

<span data-ttu-id="56800-129">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-130">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-130">Example</span></span>

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a><span data-ttu-id="56800-131">nx_mdns_delete</span><span class="sxs-lookup"><span data-stu-id="56800-131">nx_mdns_delete</span></span>

<span data-ttu-id="56800-132">Eliminar una instancia de mDNS</span><span class="sxs-lookup"><span data-stu-id="56800-132">Delete an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-133">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-133">Prototype</span></span>

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="56800-134">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-134">Description</span></span>

<span data-ttu-id="56800-135">Este servicio elimina la instancia de mDNS y libera sus recursos.</span><span class="sxs-lookup"><span data-stu-id="56800-135">This service deletes the mDNS instance and frees its resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-136">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-136">Input Parameters</span></span>

- <span data-ttu-id="56800-137">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-137">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-138">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-138">Return Values</span></span>

- <span data-ttu-id="56800-139">**NX_SUCCESS** (0x00) Se eliminó correctamente la instancia de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-139">**NX_SUCCESS** (0x00) Successfully deleted the mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-140">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-140">Allowed From</span></span>

<span data-ttu-id="56800-141">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-142">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-142">Example</span></span>

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a><span data-ttu-id="56800-143">nx_mdns_enable</span><span class="sxs-lookup"><span data-stu-id="56800-143">nx_mdns_enable</span></span>

<span data-ttu-id="56800-144">Iniciar el servicio mDNS</span><span class="sxs-lookup"><span data-stu-id="56800-144">Start the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-145">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-145">Prototype</span></span>

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="56800-146">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-146">Description</span></span>

<span data-ttu-id="56800-147">Esta API habilita el servicio mDNS en una interfaz física específica.</span><span class="sxs-lookup"><span data-stu-id="56800-147">This API enables mDNS service on specific physical interface.</span></span> <span data-ttu-id="56800-148">Una vez habilitado el servicio, el módulo mDNS sondea primero todos sus nombres de servicio únicos en la red antes de responder a las consultas recibidas en la interfaz.</span><span class="sxs-lookup"><span data-stu-id="56800-148">Once the service is enabled, the mDNS module first probes all its unique service names on the network before responding to queries received on the interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-149">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-149">Input Parameters</span></span>

- <span data-ttu-id="56800-150">**mdns_ptr** Puntero al bloque de control de instancia de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-150">**mdns_ptr** Pointer to the mDNS instance control block.</span></span>
- <span data-ttu-id="56800-151">**interface_index** Índice de la interfaz en la que se va a habilitar el servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-151">**interface_index** Index to the interface where the service is to be enabled</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-152">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-152">Return Values</span></span>

- <span data-ttu-id="56800-153">**NX_SUCCESS** (0x00) Se habilitó correctamente el servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-153">**NX_SUCCESS** (0x00) Successfully enabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-154">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-154">Allowed From</span></span>

<span data-ttu-id="56800-155">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-155">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-156">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-156">Example</span></span>

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a><span data-ttu-id="56800-157">nx_mdns_disable</span><span class="sxs-lookup"><span data-stu-id="56800-157">nx_mdns_disable</span></span>

<span data-ttu-id="56800-158">Deshabilitar el servicio mDNS</span><span class="sxs-lookup"><span data-stu-id="56800-158">Disable the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-159">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-159">Prototype</span></span>

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="56800-160">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-160">Description</span></span>

<span data-ttu-id="56800-161">Esta API deshabilita el servicio mDNS en la interfaz física específica.</span><span class="sxs-lookup"><span data-stu-id="56800-161">This API disables mDNS service on the specific physical interface.</span></span> <span data-ttu-id="56800-162">Una vez deshabilitado el servicio, mDNS envía mensajes de despedida para cada servicio local a la red que está conectado a la interfaz, para notificarlo a los nodos vecinos.</span><span class="sxs-lookup"><span data-stu-id="56800-162">Once the service is disabled, the mDNS sends "goodbye" messages for every local service to the network that is attached to the interface, so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-163">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-163">Input Parameters</span></span>

- <span data-ttu-id="56800-164">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-164">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-165">**interface_index** Índice de la interfaz en la que se va a deshabilitar el servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-165">**interface_index** Index to the interface where the service is to be disabled</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-166">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-166">Return Values</span></span>

- <span data-ttu-id="56800-167">**NX_SUCCESS** (0x00) Se habilitó correctamente el servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-167">**NX_SUCCESS** (0x00) Successfully disabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-168">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-168">Allowed From</span></span>

<span data-ttu-id="56800-169">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-170">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-170">Example</span></span>

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a><span data-ttu-id="56800-171">nx_mdns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="56800-171">nx_mdns_cache_notify_set</span></span>

<span data-ttu-id="56800-172">Instalar la función de notificación completa de la caché de mDNS</span><span class="sxs-lookup"><span data-stu-id="56800-172">Installs the mDNS cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-173">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-173">Prototype</span></span>

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a><span data-ttu-id="56800-174">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-174">Description</span></span>

<span data-ttu-id="56800-175">Este servicio instala una función de devolución de llamada proporcionada por el usuario, que se invoca cuando la caché de servicio local o la caché de servicio del mismo nivel se llenan.</span><span class="sxs-lookup"><span data-stu-id="56800-175">This service installs a user-supplied callback function, which is invoked when either the local service cache or peer service cache becomes full.</span></span> <span data-ttu-id="56800-176">Cuando la caché de servicio está llena, no se pueden agregar más registros de recursos de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-176">When the service cache is full, no more mDNS Resource Record can be added.</span></span> <span data-ttu-id="56800-177">Tenga en cuenta que la caché de servicio puede llenarse como resultado de la fragmentación interna, cuando se agregan y quitan servicios con distintas longitudes de cadena.</span><span class="sxs-lookup"><span data-stu-id="56800-177">Note that the service cache may become full as a result of internal fragmentation, when services with various string lengths are added and removed.</span></span> <span data-ttu-id="56800-178">Al recibir una notificación de caché llena en la caché de servicio del mismo nivel, la aplicación puede usar el servicio "*nx_mdns_service_cache_clear"* para borrar todas las entradas de dicha caché.</span><span class="sxs-lookup"><span data-stu-id="56800-178">On receiving a cache full notification on peer service cache, the application may use the service "*nx_mdns_service_cache_clear"* to erase all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-179">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-179">Input Parameters</span></span>

- <span data-ttu-id="56800-180">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-180">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-181">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-181">Return Values</span></span>

- <span data-ttu-id="56800-182">**NX_SUCCESS** (0x00) Se instaló correctamente la función de devolución de llamada de notificación de la caché de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-182">**NX_SUCCESS** (0x00) Successfully installed the mDNS cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-183">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-183">Allowed From</span></span>

<span data-ttu-id="56800-184">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-185">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-185">Example</span></span>

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a><span data-ttu-id="56800-186">nx_mdns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="56800-186">nx_mdns_cache_notify_clear</span></span>

<span data-ttu-id="56800-187">Borrar la función de notificación completa de la caché del servicio mDNS</span><span class="sxs-lookup"><span data-stu-id="56800-187">Clear the mDNS service cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-188">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-188">Prototype</span></span>

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="56800-189">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-189">Description</span></span>

<span data-ttu-id="56800-190">Este servicio borra una función de devolución de llamada de notificación de la caché de servicio proporcionada por el usuario.</span><span class="sxs-lookup"><span data-stu-id="56800-190">This service clears a user-supplied service cache notify callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-191">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-191">Input Parameters</span></span>

- <span data-ttu-id="56800-192">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-192">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-193">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-193">Return Values</span></span>

- <span data-ttu-id="56800-194">**NX_SUCCESS** (0x00) Se borró correctamente la función de devolución de llamada de notificación de la caché del servicio mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-194">**NX_SUCCESS** (0x00) Successfully cleared the mDNS service cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-195">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-195">Allowed From</span></span>

<span data-ttu-id="56800-196">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-197">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-197">Example</span></span>

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a><span data-ttu-id="56800-198">nx_mdns_domain_name_set</span><span class="sxs-lookup"><span data-stu-id="56800-198">nx_mdns_domain_name_set</span></span>

<span data-ttu-id="56800-199">Establecer el nombre de dominio</span><span class="sxs-lookup"><span data-stu-id="56800-199">Sets the domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-200">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-200">Prototype</span></span>

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="56800-201">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-201">Description</span></span>

<span data-ttu-id="56800-202">Este servicio configura el nombre de dominio local predeterminado.</span><span class="sxs-lookup"><span data-stu-id="56800-202">This service sets up the default local domain name.</span></span> <span data-ttu-id="56800-203">Cuando se crea la instancia de mDNS, el nombre de dominio local predeterminado se establece en "local".</span><span class="sxs-lookup"><span data-stu-id="56800-203">When the mDNS instance is created, the default local domain name is set to “.local”.</span></span> <span data-ttu-id="56800-204">Esta API permite a una aplicación sobrescribir el nombre de dominio local predeterminado.</span><span class="sxs-lookup"><span data-stu-id="56800-204">This API allows an application to overwrite the default local domain name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-205">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-205">Input Parameters</span></span>

- <span data-ttu-id="56800-206">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-206">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-207">**domain_name** Nombre de dominio que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="56800-207">**domain_name** The domain name to be used.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-208">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-208">Return Values</span></span>

- <span data-ttu-id="56800-209">**NX_SUCCESS** (0x00) Se configuró correctamente el dominio local.</span><span class="sxs-lookup"><span data-stu-id="56800-209">**NX_SUCCESS** (0x00) Successfully configured local domain.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-210">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-210">Allowed From</span></span>

<span data-ttu-id="56800-211">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-212">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-212">Example</span></span>

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a><span data-ttu-id="56800-213">nx_mdns_service_announcement_timing_set</span><span class="sxs-lookup"><span data-stu-id="56800-213">nx_mdns_service_announcement_timing_set</span></span>

<span data-ttu-id="56800-214">Establece los parámetros de tiempo de los mensajes de anuncio de servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-214">Sets the timing parameters for service announcement messages</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-215">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-215">Prototype</span></span>

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a><span data-ttu-id="56800-216">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-216">Description</span></span>

<span data-ttu-id="56800-217">Este servicio reconfigura los parámetros de tiempo empleados por mDNS al enviar los anuncios de servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-217">This service reconfigures the timing parameters employed by mDNS when sending the service announcements.</span></span> <span data-ttu-id="56800-218">El período de publicación comienza a partir de *t* tics y se puede ampliar de manera telescópica con 2 elevado a la potencia del factor *k*.</span><span class="sxs-lookup"><span data-stu-id="56800-218">Publish period starts from *t* ticks and can be expanded telescopically with 2 to the power of *k* factor.</span></span> <span data-ttu-id="56800-219">El número de repeticiones por anuncio es *p*, el intervalo entre cada anuncio repetido es *intervalo* tics y el número de períodos de anuncio es max_time.</span><span class="sxs-lookup"><span data-stu-id="56800-219">The number of repetitions per advertisement is *p*, the interval between each repeated advertisement is *interval* ticks, and the number of announcement period is max_time.</span></span> <span data-ttu-id="56800-220">De forma predeterminada, el período inicial se establece en 1 segundo, con k = 1 (el período se duplica cada vez), *p = 1* (sin repetición), retrans_interval = 0 (sin intervalo de tiempo), period_interval = 0xFFFFFFFF (intervalo de período máximo) y max_time = 3 (número de anuncios).</span><span class="sxs-lookup"><span data-stu-id="56800-220">By default, the initial period is set to 1 second, with k = 1 (the period doubles each time), *p = 1* (no repetition), retrans_interval = 0(no time interval), period_interval = 0xFFFFFFFF(max period interval) and max_time = 3(number of advertisement).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-221">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-221">Input Parameters</span></span>

- <span data-ttu-id="56800-222">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-222">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-223">**t** Número de tics del período inicial.</span><span class="sxs-lookup"><span data-stu-id="56800-223">**t** Number of ticks for the initial period.</span></span> <span data-ttu-id="56800-224">El valor predeterminado es 100 tics para 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="56800-224">Default is 100 ticks for 1 second.</span></span>
- <span data-ttu-id="56800-225">**p** Número de repeticiones.</span><span class="sxs-lookup"><span data-stu-id="56800-225">**p** Number of repetitions.</span></span> <span data-ttu-id="56800-226">El valor predeterminado es 1.</span><span class="sxs-lookup"><span data-stu-id="56800-226">Default value is 1.</span></span>
- <span data-ttu-id="56800-227">**k** Factor telescópico.</span><span class="sxs-lookup"><span data-stu-id="56800-227">**k** Telescopic factor.</span></span> <span data-ttu-id="56800-228">El valor predeterminado es 1.</span><span class="sxs-lookup"><span data-stu-id="56800-228">Default value is 1.</span></span>
- <span data-ttu-id="56800-229">**retrans_interval** Número de tics que hay que esperar antes de enviar mensajes de anuncio repetidos.</span><span class="sxs-lookup"><span data-stu-id="56800-229">**retrans_interval** Number of ticks to wait before sending out repeated announcement messages.</span></span> <span data-ttu-id="56800-230">El valor predeterminado es 0.</span><span class="sxs-lookup"><span data-stu-id="56800-230">Default value is 0.</span></span>
- <span data-ttu-id="56800-231">**period_interval** Número de tics entre dos períodos de anuncio.</span><span class="sxs-lookup"><span data-stu-id="56800-231">**period_interval** Number of ticks between two announcement period.</span></span> <span data-ttu-id="56800-232">El valor predeterminado es 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="56800-232">Default value is 0xFFFFFFFF.</span></span>
- <span data-ttu-id="56800-233">**max_time** Número de períodos de anuncio que se van a usar para el anuncio.</span><span class="sxs-lookup"><span data-stu-id="56800-233">**max_time** Number of announcement period to use for the advertisement.</span></span> <span data-ttu-id="56800-234">Después de los períodos de anuncio de *max_time*, no se envían más mensajes de anuncio.</span><span class="sxs-lookup"><span data-stu-id="56800-234">After the *max_time* announcement periods, no more announcement messages are sent.</span></span> <span data-ttu-id="56800-235">El valor predeterminado es 3.</span><span class="sxs-lookup"><span data-stu-id="56800-235">Default value is 3.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-236">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-236">Return Values</span></span>

- <span data-ttu-id="56800-237">**NX_SUCCESS** (0x00) Establece correctamente los valores de tiempo.</span><span class="sxs-lookup"><span data-stu-id="56800-237">**NX_SUCCESS** (0x00) Successfully sets the timing values.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-238">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-238">Allowed From</span></span>

<span data-ttu-id="56800-239">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-240">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-240">Example</span></span>

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a><span data-ttu-id="56800-241">nx_mdns_service_add</span><span class="sxs-lookup"><span data-stu-id="56800-241">nx_mdns_service_add</span></span>

<span data-ttu-id="56800-242">Agregar un servicio local</span><span class="sxs-lookup"><span data-stu-id="56800-242">Add a local service</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-243">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-243">Prototype</span></span>

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="56800-244">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-244">Description</span></span>

<span data-ttu-id="56800-245">Esta API registra un servicio ofrecido por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="56800-245">This API registers a service offered by the application.</span></span> <span data-ttu-id="56800-246">Si se establece la marca *is_unique*, mDNS sondea el nombre del servicio para asegurarse de que es único en la red local antes de empezar a anunciar el servicio en la red.</span><span class="sxs-lookup"><span data-stu-id="56800-246">If the flag *is_unique* is set, mDNS probes the service name to make sure it is unique on the local network before starting to announce the service on the network.</span></span> <span data-ttu-id="56800-247">*Instance* es la parte de instancia del nombre del servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-247">*Instance* is the instance portion of the service name.</span></span> <span data-ttu-id="56800-248">*service* es la parte de servicio del nombre del servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-248">The *service* is the service portion of the service name.</span></span> <span data-ttu-id="56800-249">Por ejemplo, "_http._tcp" es un servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-249">For example “_http._tcp” is a service.</span></span> <span data-ttu-id="56800-250">Para describir un servicio con subtipo, el autor de llamada debe usar el parámetro *subtype*.</span><span class="sxs-lookup"><span data-stu-id="56800-250">To describe a service with subtype, caller must use the *subtype* parameter.</span></span> <span data-ttu-id="56800-251">Por ejemplo, si el servicio deseado es "_printer._sub._http._tcp", el campo de servicio es "_http._tcp:" y el campo de subtipo es "_printer".</span><span class="sxs-lookup"><span data-stu-id="56800-251">For example, if the desired service is “_printer._sub._http._tcp”, the service field is “_http._tcp:, and the subtype field is “_printer”.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-252">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-252">Input Parameters</span></span>

- <span data-ttu-id="56800-253">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-253">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-254">**instance** Puntero al nombre de instancia del servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-254">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="56800-255">**service** Puntero al tipo de servicio mDNS, excluida la información del subtipo.</span><span class="sxs-lookup"><span data-stu-id="56800-255">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="56800-256">**subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-256">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="56800-257">**priority** Prioridad del servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-257">**priority** Service priority</span></span>
- <span data-ttu-id="56800-258">**weight** Peso del servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-258">**weight** Service weight</span></span>
- <span data-ttu-id="56800-259">**port** Número de puerto TCP o UDP que usa el servicio</span><span class="sxs-lookup"><span data-stu-id="56800-259">**port** TCP or UDP port number the service uses</span></span>
- <span data-ttu-id="56800-260">**text** Información de texto adicional.</span><span class="sxs-lookup"><span data-stu-id="56800-260">**text** Additional text information</span></span>
- <span data-ttu-id="56800-261">**is_unique** Marca booleana que indica si el servicio es compartido o único.</span><span class="sxs-lookup"><span data-stu-id="56800-261">**is_unique** Boolean flag indicating whether the service is shared or unique.</span></span> <span data-ttu-id="56800-262">En el caso de los servicios registrados como únicos, mDNS debe sondear el servicio en la red antes de iniciar su oferta.</span><span class="sxs-lookup"><span data-stu-id="56800-262">For services registered as unique, mDNS must probe the service on the network before starting offering it.</span></span>
- <span data-ttu-id="56800-263">**Interface_index** Interfaz física mediante la que se ofrece el servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-263">**Interface_index** Physical interface the service is offered through.</span></span> <span data-ttu-id="56800-264">Con los servicios que se ofrecen mediante cualquiera de los servicios asociados, se usa el valor *NX_MDNS_ALL_INTERFACES*.</span><span class="sxs-lookup"><span data-stu-id="56800-264">For a service that is offered through any of the attached services, the value *NX_MDNS_ALL_INTERFACES* is used.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-265">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-265">Return Values</span></span>

- <span data-ttu-id="56800-266">**NX_SUCCESS** (0x00) Se registró correctamente el servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-266">**NX_SUCCESS** (0x00) Successfully registered the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-267">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-267">Allowed From</span></span>

<span data-ttu-id="56800-268">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-269">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-269">Example</span></span>

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a><span data-ttu-id="56800-270">nx_mdns_service_delete</span><span class="sxs-lookup"><span data-stu-id="56800-270">nx_mdns_service_delete</span></span>

<span data-ttu-id="56800-271">Quitar un servicio registrado anterior</span><span class="sxs-lookup"><span data-stu-id="56800-271">Remove a previous registered service</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-272">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-272">Prototype</span></span>

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="56800-273">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-273">Description</span></span>

<span data-ttu-id="56800-274">Esta API elimina un servicio registrado anterior.</span><span class="sxs-lookup"><span data-stu-id="56800-274">This API deletes a previous registered service.</span></span> <span data-ttu-id="56800-275">Cuando se elimina el servicio, se envían mensajes de despedida a la red local para notificarlo a los nodos vecinos.</span><span class="sxs-lookup"><span data-stu-id="56800-275">As the service is deleted, "goodbye" messages are sent to the local network so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-276">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-276">Input Parameters</span></span>

- <span data-ttu-id="56800-277">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-277">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-278">**instance** Puntero al nombre de instancia del servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-278">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="56800-279">**service** Puntero al tipo de servicio mDNS, excluida la información del subtipo.</span><span class="sxs-lookup"><span data-stu-id="56800-279">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="56800-280">**subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-280">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-281">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-281">Return Values</span></span>

- <span data-ttu-id="56800-282">**NX_SUCCESS** (0x00) Se eliminó correctamente el servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-282">**NX_SUCCESS** (0x00) Successfully deleted the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-283">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-283">Allowed From</span></span>

<span data-ttu-id="56800-284">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-285">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-285">Example</span></span>

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a><span data-ttu-id="56800-286">nx_mdns_service_one_shot_query</span><span class="sxs-lookup"><span data-stu-id="56800-286">nx_mdns_service_one_shot_query</span></span>

<span data-ttu-id="56800-287">Iniciar la detección de servicios una sola vez</span><span class="sxs-lookup"><span data-stu-id="56800-287">Initiate one-shot service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-288">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-288">Prototype</span></span>

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="56800-289">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-289">Description</span></span>

<span data-ttu-id="56800-290">Este servicio realiza una consulta de mDNS una sola vez.</span><span class="sxs-lookup"><span data-stu-id="56800-290">This service performs a one-shot mDNS query.</span></span> <span data-ttu-id="56800-291">Si el servicio especificado se encuentra en la caché de servicio del mismo nivel, se devuelve la primera instancia.</span><span class="sxs-lookup"><span data-stu-id="56800-291">If the specified service is found in the peer service cache, the first instance is returned.</span></span> <span data-ttu-id="56800-292">Si no se encuentra ningún servicio en la caché de servicio del mismo nivel local, el módulo mDNS emite un comando de consulta y espera la respuesta.</span><span class="sxs-lookup"><span data-stu-id="56800-292">If no services are found in the local peer service cache, the mDNS module issues a query command and wait for response.</span></span> <span data-ttu-id="56800-293">El servicio se bloquea hasta que se recibe la primera respuesta o se agota el tiempo de espera de la consulta.</span><span class="sxs-lookup"><span data-stu-id="56800-293">The service is blocked till either the first answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-294">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-294">Input Parameters</span></span>

- <span data-ttu-id="56800-295">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-295">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-296">**instance** Puntero al nombre de instancia del servicio, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-296">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="56800-297">**service** Puntero al tipo de servicio mDNS, excluida la información del subtipo.</span><span class="sxs-lookup"><span data-stu-id="56800-297">**service** Pointer to the mDNS service type, excluding subtype information.</span></span> <span data-ttu-id="56800-298">La aplicación debe especificar el tipo de servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-298">the application must specify the service type.</span></span>
- <span data-ttu-id="56800-299">**subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-299">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="56800-300">**service_ptr** Puntero proporcionado por el usuario a la estructura NX_MDNS_SERVICE que almacena los resultados de la consulta.</span><span class="sxs-lookup"><span data-stu-id="56800-300">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the query results.</span></span>
- <span data-ttu-id="56800-301">**WAIT_OPTION** Cantidad de tiempo de espera, en tics, para obtener una respuesta.</span><span class="sxs-lookup"><span data-stu-id="56800-301">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-302">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-302">Return Values</span></span>

- <span data-ttu-id="56800-303">**NX_SUCCESS** (0x00) Se obtuvo correctamente la información del servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-303">**NX_SUCCESS** (0x00) Successfully obtained service information.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-304">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-304">Allowed From</span></span>

<span data-ttu-id="56800-305">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-305">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-306">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-306">Example</span></span>

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a><span data-ttu-id="56800-307">nx_mdns_service_continuous_query</span><span class="sxs-lookup"><span data-stu-id="56800-307">nx_mdns_service_continuous_query</span></span>

<span data-ttu-id="56800-308">Iniciar la detección continua de servicios</span><span class="sxs-lookup"><span data-stu-id="56800-308">Initiate continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-309">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-309">Prototype</span></span>

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="56800-310">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-310">Description</span></span>

<span data-ttu-id="56800-311">Este servicio inicia una consulta continua.</span><span class="sxs-lookup"><span data-stu-id="56800-311">This service starts a continuous query.</span></span> <span data-ttu-id="56800-312">Tenga en cuenta que el servicio se devuelve inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="56800-312">Note that the service returns immediately.</span></span> <span data-ttu-id="56800-313">Después de emitir una consulta continua, la aplicación puede recuperar el registro del servicio mediante la API *nx_mdns_service_lookup*.</span><span class="sxs-lookup"><span data-stu-id="56800-313">After issuing a continuous query, the application may retrieve service record by using the API *nx_mdns_service_lookup*.</span></span> <span data-ttu-id="56800-314">Para detener la consulta continua, la aplicación puede usar la API *nx_mdns_service_query_stop*.</span><span class="sxs-lookup"><span data-stu-id="56800-314">To stop the continuous query, the application may use the API *nx_mdns_service_query_stop*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-315">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-315">Input Parameters</span></span>

- <span data-ttu-id="56800-316">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-316">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-317">**instance** Puntero al nombre de instancia del servicio, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-317">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="56800-318">**service** Puntero al tipo de servicio mDNS, excluida la información de subtipo, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-318">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="56800-319">**subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-319">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-320">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-320">Return Values</span></span>

- <span data-ttu-id="56800-321">**NX_SUCCESS** (0x00) Se inició correctamente la consulta.</span><span class="sxs-lookup"><span data-stu-id="56800-321">**NX_SUCCESS** (0x00) Successfully started continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-322">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-322">Allowed From</span></span>

<span data-ttu-id="56800-323">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-323">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-324">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-324">Example</span></span>

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a><span data-ttu-id="56800-325">nx_mdns_service_query_stop</span><span class="sxs-lookup"><span data-stu-id="56800-325">nx_mdns_service_query_stop</span></span>

<span data-ttu-id="56800-326">Cesar una detección continua de servicios emitida previamente</span><span class="sxs-lookup"><span data-stu-id="56800-326">Cease a previously issued continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-327">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-327">Prototype</span></span>

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="56800-328">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-328">Description</span></span>

<span data-ttu-id="56800-329">Esta API finaliza una detección continua de servicios emitida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="56800-329">This API terminates a previous issued continuous service discovery.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-330">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-330">Input Parameters</span></span>

- <span data-ttu-id="56800-331">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-331">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-332">**instance** Puntero al nombre de instancia del servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-332">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="56800-333">**service** Puntero a la información de subtipo del tipo de servicio mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-333">**service** Pointer to the mDNS service type, subtype information.</span></span>
- <span data-ttu-id="56800-334">**subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-334">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-335">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-335">Return Values</span></span>

- <span data-ttu-id="56800-336">**NX_SUCCESS** (0x00) Se detuvo correctamente la consulta.</span><span class="sxs-lookup"><span data-stu-id="56800-336">**NX_SUCCESS** (0x00) Successfully stopped continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-337">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-337">Allowed From</span></span>

<span data-ttu-id="56800-338">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-338">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-339">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-339">Example</span></span>

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a><span data-ttu-id="56800-340">nx_mdns_service_lookup</span><span class="sxs-lookup"><span data-stu-id="56800-340">nx_mdns_service_lookup</span></span>

<span data-ttu-id="56800-341">Recupera el servicio de la caché de servicio del mismo nivel local.</span><span class="sxs-lookup"><span data-stu-id="56800-341">Retrieves the service from the local peer service cache</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-342">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-342">Prototype</span></span>

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a><span data-ttu-id="56800-343">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-343">Description</span></span>

<span data-ttu-id="56800-344">Este servicio busca servicios que coincidan con el nombre de instancia (si se proporciona) y con el tipo de servicio en la caché de servicio del mismo nivel local.</span><span class="sxs-lookup"><span data-stu-id="56800-344">This service looks up services matching the instance name (if provided) and the type of service in the local peer service cache.</span></span> <span data-ttu-id="56800-345">La aplicación iniciará la búsqueda de servicio con *instance_index* establecido en cero con respecto al primer servicio de la caché que coincida con la descripción.</span><span class="sxs-lookup"><span data-stu-id="56800-345">Application shall start the service lookup with *instance_index* set to zero for the first service in the cache that matches the description.</span></span> <span data-ttu-id="56800-346">La aplicación mantendrá el uso de este servicio con un aumento del valor de *instance_index* para los servicios adicionales que se encuentran en la caché, hasta que el servicio devuelva *NX_NO_MORE_ENTRIES*, que indica el final de esta.</span><span class="sxs-lookup"><span data-stu-id="56800-346">Application shall keep using this service with increasing *instance_index* value for additional services found in the cache, till the service returns *NX_NO_MORE_ENTRIES*, which indicates the end of the cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-347">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-347">Input Parameters</span></span>

- <span data-ttu-id="56800-348">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-348">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-349">**instance** Puntero al nombre de instancia del servicio, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-349">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="56800-350">**service** Puntero al tipo de servicio mDNS, excluida la información de subtipo, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-350">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="56800-351">**subtype** Puntero a la parte del subtipo del servicio mDNS, si procede.</span><span class="sxs-lookup"><span data-stu-id="56800-351">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="56800-352">**Instance_index** Número de índice de la instancia que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="56800-352">**Instance_index** Index number to the instance to be returned.</span></span>
- <span data-ttu-id="56800-353">**service_ptr** Puntero proporcionado por el usuario a la estructura NX_MDNS_SERVICE que almacena los resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="56800-353">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the lookup results.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-354">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-354">Return Values</span></span>

- <span data-ttu-id="56800-355">**NX_SUCCESS** (0x00) Se recuperó correctamente el servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-355">**NX_SUCCESS** (0x00) Successfully retrieved the service</span></span>
- <span data-ttu-id="56800-356">**NX_NO_MORE_ENTRIES** (0X17) No se encuentra ninguna entrada de servicio en el número de índice especificado.</span><span class="sxs-lookup"><span data-stu-id="56800-356">**NX_NO_MORE_ENTRIES** (0x17) No service entry is found at the specified index number.</span></span> <span data-ttu-id="56800-357">Este código de error indica el final de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="56800-357">This error code indicates the end of the search.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-358">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-358">Allowed From</span></span>

<span data-ttu-id="56800-359">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-360">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-360">Example</span></span>

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a><span data-ttu-id="56800-361">nx_mdns_service_ignore_set</span><span class="sxs-lookup"><span data-stu-id="56800-361">nx_mdns_service_ignore_set</span></span>

<span data-ttu-id="56800-362">Configurar un conjunto de omisiones de servicios</span><span class="sxs-lookup"><span data-stu-id="56800-362">Configures a service ignore set</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-363">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-363">Prototype</span></span>

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a><span data-ttu-id="56800-364">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-364">Description</span></span>

<span data-ttu-id="56800-365">Esta API configura una máscara para omitir los servicios especificados por la máscara de bits *service_mask*.</span><span class="sxs-lookup"><span data-stu-id="56800-365">This API configures a mask to ignore services specified by the *service_mask* bitmask.</span></span> <span data-ttu-id="56800-366">Opcionalmente, el usuario puede usar el parámetro service_mask para seleccionar los tipos de servicio que no desee almacenar en caché.</span><span class="sxs-lookup"><span data-stu-id="56800-366">User may optionally use the service_mask to select service types it does not wish to be cached.</span></span> <span data-ttu-id="56800-367">En la tabla *nx_mdns_service_types* de *nxd_mdns.c.* , se define una lista de servicios.</span><span class="sxs-lookup"><span data-stu-id="56800-367">A list of services is defined in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span> <span data-ttu-id="56800-368">La máscara correspondiente del primer tipo de servicio de nx_mdns_service_types[] es 0x00000001, la máscara del segundo tipo de servicio es 0x00000002, etc.</span><span class="sxs-lookup"><span data-stu-id="56800-368">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-369">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-369">Input Parameters</span></span>

- <span data-ttu-id="56800-370">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-370">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-371">**service_mask** Tipos de servicio definidos por el usuario que se van a omitir.</span><span class="sxs-lookup"><span data-stu-id="56800-371">**service_mask** User-defined service types to ignore.</span></span> <span data-ttu-id="56800-372">La máscara es un tipo ULONG de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="56800-372">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="56800-373">Cada bit representa una entrada en la matriz *nx_mdns_service_types* definida por el usuario.</span><span class="sxs-lookup"><span data-stu-id="56800-373">Each bit represents an entry in the user-defined *nx_mdns_service_types* array.</span></span> <span data-ttu-id="56800-374">Si se establece un bit, el tipo de servicio correspondiente especificado en la matriz *nx_mdns_service_type* no se almacenará en la caché de servicio del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="56800-374">If a bit is set, the corresponding service type specified in the *nx_mdns_service_type* array will not store in the peer service cache.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-375">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-375">Return Values</span></span>

- <span data-ttu-id="56800-376">**NX_SUCCESS** (0x00) Establece correctamente la máscara de omisión del servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-376">**NX_SUCCESS** (0x00) Successfully sets the service ignore mask.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-377">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-377">Allowed From</span></span>

<span data-ttu-id="56800-378">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-378">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-379">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-379">Example</span></span>

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a><span data-ttu-id="56800-380">nx_mdns_service_notify_set</span><span class="sxs-lookup"><span data-stu-id="56800-380">nx_mdns_service_notify_set</span></span>

<span data-ttu-id="56800-381">Configurar una función de devolución de llamada de notificación de cambio de servicio</span><span class="sxs-lookup"><span data-stu-id="56800-381">Configures a service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-382">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-382">Prototype</span></span>

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a><span data-ttu-id="56800-383">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-383">Description</span></span>

<span data-ttu-id="56800-384">Esta API configura una función de devolución de llamada de notificación de cambio de servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-384">This API configures a service change notify callback function.</span></span> <span data-ttu-id="56800-385">Esta función de devolución de llamada se invoca cuando se agrega, cambia o deja de estar disponible un servicio ofrecido por otros nodos de la red.</span><span class="sxs-lookup"><span data-stu-id="56800-385">This callback function is invoked when a service offered by other nodes on the network is added, changed or is no longer available.</span></span> <span data-ttu-id="56800-386">Opcionalmente, el usuario puede usar el parámetro service_mask para seleccionar los tipos de servicio que quiere supervisar.</span><span class="sxs-lookup"><span data-stu-id="56800-386">User may optionally use the service_mask to select service types it wishes to monitor.</span></span> <span data-ttu-id="56800-387">En la tabla *nx_mdns_service_types* de *nxd_mdns. c.* , hay una lista de servicios en proceso de supervisión que están codificados de forma rígida.</span><span class="sxs-lookup"><span data-stu-id="56800-387">A list of services being monitored are hard-coded in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span>

<span data-ttu-id="56800-388">La máscara correspondiente del primer tipo de servicio de nx_mdns_service_types[] es 0x00000001, la máscara del segundo tipo de servicio es 0x00000002, etc.</span><span class="sxs-lookup"><span data-stu-id="56800-388">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-389">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-389">Input Parameters</span></span>

- <span data-ttu-id="56800-390">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-390">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-391">**service_mask** Tipos de servicio definidos por el usuario que se van a supervisar.</span><span class="sxs-lookup"><span data-stu-id="56800-391">**service_mask** User-defined service types to monitor.</span></span> <span data-ttu-id="56800-392">La máscara es un tipo ULONG de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="56800-392">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="56800-393">Cada bit representa una entrada en la matriz de *nx_mdns_service_types*.</span><span class="sxs-lookup"><span data-stu-id="56800-393">Each bit represents an entry in the *nx_mdns_service_types* array.</span></span>
- <span data-ttu-id="56800-394">**service_change_notify** Función de devolución de llamada que se invoca cuando cambia el servicio especificado.</span><span class="sxs-lookup"><span data-stu-id="56800-394">**service_change_notify** The callback function to be invoked when the specified service is changed.</span></span> <span data-ttu-id="56800-395">La información detallada del servicio se devuelve en la memoria a la que apunta *service_ptr*.</span><span class="sxs-lookup"><span data-stu-id="56800-395">The detailed service information is returned in the memory pointed to by *service_ptr.*</span></span> <span data-ttu-id="56800-396">Tenga en cuenta que el contenido de la memoria no es válido después de volver de la función de devolución de llamada de notificación.</span><span class="sxs-lookup"><span data-stu-id="56800-396">Note that the content in the memory is invalid after returning from the notify callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-397">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-397">Return Values</span></span>

- <span data-ttu-id="56800-398">**NX_SUCCESS** (0x00) Se instaló correctamente la función de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="56800-398">**NX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-399">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-399">Allowed From</span></span>

<span data-ttu-id="56800-400">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-401">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-401">Example</span></span>

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a><span data-ttu-id="56800-402">nx_mdns_service_notify_clear</span><span class="sxs-lookup"><span data-stu-id="56800-402">nx_mdns_service_notify_clear</span></span>

<span data-ttu-id="56800-403">Borrar la función de devolución de llamada de notificación de cambio de servicio</span><span class="sxs-lookup"><span data-stu-id="56800-403">Clear the service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-404">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-404">Prototype</span></span>

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="56800-405">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-405">Description</span></span>

<span data-ttu-id="56800-406">Esta API borra la función de devolución de llamada de notificación de cambio de servicio.</span><span class="sxs-lookup"><span data-stu-id="56800-406">This API clears the service change notify callback function and the .</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-407">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-407">Input Parameters</span></span>

- <span data-ttu-id="56800-408">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-408">**mdns_ptr** Pointer to mDNS control block..</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-409">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-409">Return Values</span></span>

- <span data-ttu-id="56800-410">**NX_SUCCESS** (0x00) Se borró correctamente la función de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="56800-410">**NX_SUCCESS** (0x00) Successfully cleared the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-411">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-411">Allowed From</span></span>

<span data-ttu-id="56800-412">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-413">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-413">Example</span></span>

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a><span data-ttu-id="56800-414">nx_mdns_host_address_get</span><span class="sxs-lookup"><span data-stu-id="56800-414">nx_mdns_host_address_get</span></span>

<span data-ttu-id="56800-415">Obtener la dirección de host</span><span class="sxs-lookup"><span data-stu-id="56800-415">Get the host address</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-416">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-416">Prototype</span></span>

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="56800-417">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-417">Description</span></span>

<span data-ttu-id="56800-418">Este servicio realiza una consulta mDNS en las direcciones IPv4 e IPv6 del host.</span><span class="sxs-lookup"><span data-stu-id="56800-418">This service performs a mDNS query on host IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="56800-419">Si la dirección del nombre de host especificado se encuentra en la caché de servicio del mismo nivel, se devuelve la dirección.</span><span class="sxs-lookup"><span data-stu-id="56800-419">If the address of specified host name is found in peer service cache, the address is returned.</span></span> <span data-ttu-id="56800-420">Si no se encuentra ninguna dirección en esta caché, el módulo mDNS emite consultas de tipo A y AAAA y espera la respuesta.</span><span class="sxs-lookup"><span data-stu-id="56800-420">If no address is found in the peer service cache, the mDNS module issues A and AAAA type queries and wait for response.</span></span> <span data-ttu-id="56800-421">Esta API se bloquea hasta que se recibe una respuesta o se agota el tiempo de espera de la consulta.</span><span class="sxs-lookup"><span data-stu-id="56800-421">This API blocks until either an answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-422">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-422">Input Parameters</span></span>

- <span data-ttu-id="56800-423">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-423">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="56800-424">**host_name** Puntero al nombre de host.</span><span class="sxs-lookup"><span data-stu-id="56800-424">**host_name** Pointer to host name.</span></span>
- <span data-ttu-id="56800-425">**ipv4_address** Puntero a una dirección alineada de 4 bytes para el espacio de almacenamiento de direcciones IPv4.</span><span class="sxs-lookup"><span data-stu-id="56800-425">**ipv4_address** Pointer to a 4-byte aligned address for IPv4 address storage space.</span></span> <span data-ttu-id="56800-426">El usuario debe asignar 4 bytes de espacio para la dirección IPv4.</span><span class="sxs-lookup"><span data-stu-id="56800-426">User shall allocate 4 bytes of space for the IPv4 - address.</span></span> <span data-ttu-id="56800-427">La dirección de NX_NULL se puede pasar a esta API si la aplicación no necesita recuperar la dirección IPv4.</span><span class="sxs-lookup"><span data-stu-id="56800-427">NX_NULL address can be passed into this API if application does not need to retrieve IPv4 address.</span></span>
- <span data-ttu-id="56800-428">**ipv6_address** Puntero a la dirección alineada de 4 bytes para el espacio de almacenamiento de direcciones IPv6.</span><span class="sxs-lookup"><span data-stu-id="56800-428">**ipv6_address** Pointer to the 4-byte aligned address for IPv6 address storage space.</span></span> <span data-ttu-id="56800-429">El usuario debe asignar 16 bytes de espacio para la dirección IPv6.</span><span class="sxs-lookup"><span data-stu-id="56800-429">User shall allocate 16 bytes of space for the - IPv6 address.</span></span> <span data-ttu-id="56800-430">La dirección de NX_NULL se puede pasar a esta API si la aplicación no necesita recuperar la dirección IPv6.</span><span class="sxs-lookup"><span data-stu-id="56800-430">NX_NULL address can be passed into this API if application does not need to retrieve IPv6 address.</span></span>
- <span data-ttu-id="56800-431">**WAIT_OPTION** Cantidad de tiempo de espera, en tics, para obtener una respuesta.</span><span class="sxs-lookup"><span data-stu-id="56800-431">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-432">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-432">Return Values</span></span>

- <span data-ttu-id="56800-433">**NX_SUCCESS** (0x00) Se obtuvo correctamente la dirección del host.</span><span class="sxs-lookup"><span data-stu-id="56800-433">**NX_SUCCESS** (0x00) Successfully obtained host address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-434">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-434">Allowed From</span></span>

<span data-ttu-id="56800-435">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-436">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-436">Example</span></span>

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a><span data-ttu-id="56800-437">nx_mdns_local_cache_clear</span><span class="sxs-lookup"><span data-stu-id="56800-437">nx_mdns_local_cache_clear</span></span>

<span data-ttu-id="56800-438">Borrar todos los servicios locales</span><span class="sxs-lookup"><span data-stu-id="56800-438">Erase all local services</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-439">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-439">Prototype</span></span>

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="56800-440">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-440">Description</span></span>

<span data-ttu-id="56800-441">Este servicio borra todas las entradas de la caché del servicio local después de enviar el mensaje de despedida.</span><span class="sxs-lookup"><span data-stu-id="56800-441">This service clears all entries in the local service cache after send the Goodbye message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-442">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-442">Input Parameters</span></span>

- <span data-ttu-id="56800-443">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-443">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-444">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-444">Return Values</span></span>

- <span data-ttu-id="56800-445">**NX_SUCCESS** (0x00) Se borraron correctamente todas las entradas de la caché.</span><span class="sxs-lookup"><span data-stu-id="56800-445">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-446">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-446">Allowed From</span></span>

<span data-ttu-id="56800-447">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-447">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-448">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-448">Example</span></span>

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a><span data-ttu-id="56800-449">nx_mdns_peer_cache_clear</span><span class="sxs-lookup"><span data-stu-id="56800-449">nx_mdns_peer_cache_clear</span></span>

<span data-ttu-id="56800-450">Borrar todos los servicios detectados</span><span class="sxs-lookup"><span data-stu-id="56800-450">Erase all the discovered services</span></span>

### <a name="prototype"></a><span data-ttu-id="56800-451">Prototipo</span><span class="sxs-lookup"><span data-stu-id="56800-451">Prototype</span></span>

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="56800-452">Descripción</span><span class="sxs-lookup"><span data-stu-id="56800-452">Description</span></span>

<span data-ttu-id="56800-453">Este servicio borra todas las entradas de la caché de servicio del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="56800-453">This service clears all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="56800-454">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="56800-454">Input Parameters</span></span>

- <span data-ttu-id="56800-455">**mdns_ptr** Puntero al bloque de control de mDNS.</span><span class="sxs-lookup"><span data-stu-id="56800-455">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="56800-456">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="56800-456">Return Values</span></span>

- <span data-ttu-id="56800-457">**NX_SUCCESS** (0x00) Se borraron correctamente todas las entradas de la caché.</span><span class="sxs-lookup"><span data-stu-id="56800-457">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="56800-458">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="56800-458">Allowed From</span></span>

<span data-ttu-id="56800-459">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="56800-459">Threads</span></span>

### <a name="example"></a><span data-ttu-id="56800-460">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="56800-460">Example</span></span>

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
