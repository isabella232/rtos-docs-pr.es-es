---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios de Azure RTOS NetX en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814481"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a><span data-ttu-id="a9163-103">Capítulo 4: Descripción de los servicios de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="a9163-103">Chapter 4 - Description of Azure RTOS NetX Services</span></span>

<span data-ttu-id="a9163-104">Este capítulo contiene una descripción de todos los servicios de Azure RTOS NetX en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="a9163-104">This chapter contains a description of all Azure RTOS NetX services in alphabetic order.</span></span> <span data-ttu-id="a9163-105">Los nombres de los servicios están diseñados de modo que todos los servicios similares están agrupados.</span><span class="sxs-lookup"><span data-stu-id="a9163-105">Service names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="a9163-106">Por ejemplo, todos los servicios ARP se encuentran al principio de este capítulo.</span><span class="sxs-lookup"><span data-stu-id="a9163-106">For example, all ARP services are found at the beginning of this chapter.</span></span>

> [!NOTE]
> <span data-ttu-id="a9163-107">*Tenga en cuenta que una API de socket compatible con BSD está disponible para el código de aplicación heredado que no puede sacar el máximo partido de la API NetX de alto rendimiento. Consulte el Apéndice D para obtener más información sobre la API de socket compatible con BSD.*</span><span class="sxs-lookup"><span data-stu-id="a9163-107">*Note that a BSD-Compatible Socket API is available for legacy application code that cannot take full advantage of the high-performance NetX API. Refer to Appendix D for more information on the BSD-Compatible Socket API.*</span></span>

<span data-ttu-id="a9163-108">En la sección "Valores devueltos" de cada descripción, los valores en **NEGRITA** no se ven afectados por la opción NX_DISABLE_ERROR_CHECKING que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están deshabilitados por completo.</span><span class="sxs-lookup"><span data-stu-id="a9163-108">In the "Return Values" section of each description, values in **BOLD** are not affected by the NX_DISABLE_ERROR_CHECKING option used to disable the API error checking, while values in non-bold are completely disabled.</span></span> <span data-ttu-id="a9163-109">Las secciones "Permitido desde" indican desde donde se puede llamar a cada servicio de NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-109">The "Allowed From" sections indicate from which each NetX service can be called.</span></span>

## <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="a9163-110">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="a9163-110">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="a9163-111">Invalida todas las entradas dinámicas en la memoria caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-111">Invalidate all dynamic entries in the ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-112">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-112">Prototype</span></span>

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-113">Description</span></span>

<span data-ttu-id="a9163-114">Este servicio invalida todas las entradas de ARP dinámicas que se encuentran actualmente en la memoria caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-114">This service invalidates all dynamic ARP entries currently in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-115">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-115">Parameters</span></span>

- <span data-ttu-id="a9163-116">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-116">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-117">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-117">Return Values</span></span>

- <span data-ttu-id="a9163-118">**NX_SUCCESS**: (0x00) la caché de ARP se invalidó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-118">**NX_SUCCESS** (0x00) Successful ARP cache invalidate.</span></span>
- <span data-ttu-id="a9163-119">**NX_NOT_ENABLED**: (0x14) ARP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-119">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="a9163-120">**NX_PTR_ERROR**: (0x07) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-120">**NX_PTR_ERROR** (0x07) Invalid IP address.</span></span>
- <span data-ttu-id="a9163-121">**NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="a9163-121">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-122">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-122">Allowed From</span></span>

<span data-ttu-id="a9163-123">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-123">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-124">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-124">Preemption Possible</span></span>

<span data-ttu-id="a9163-125">No</span><span class="sxs-lookup"><span data-stu-id="a9163-125">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-126">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-126">Example</span></span>

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-127">See Also</span></span>

- <span data-ttu-id="a9163-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="a9163-129">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-129">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="a9163-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="a9163-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="a9163-132">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="a9163-132">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="a9163-133">Establece la entrada de ARP dinámica.</span><span class="sxs-lookup"><span data-stu-id="a9163-133">Set dynamic ARP entry</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-134">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-134">Prototype</span></span>

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="a9163-135">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-135">Description</span></span>

<span data-ttu-id="a9163-136">Este servicio asigna una entrada dinámica de la memoria caché de ARP y configura la dirección IP especificada a la asignación de la dirección física.</span><span class="sxs-lookup"><span data-stu-id="a9163-136">This service allocates a dynamic entry from the ARP cache and sets up the specified IP to physical address mapping.</span></span> <span data-ttu-id="a9163-137">Si no se especifica ninguna dirección física, se envía una solicitud de ARP real a la red para que se resuelva dicha dirección.</span><span class="sxs-lookup"><span data-stu-id="a9163-137">If a zero physical address is specified, an actual ARP request is sent to the network in order to have the physical address resolved.</span></span> <span data-ttu-id="a9163-138">Tenga en cuenta también que esta entrada se quitará si está activa la caducidad de ARP o si se ha agotado la memoria caché de ARP y se trata de la entrada de ARP usada menos recientemente.</span><span class="sxs-lookup"><span data-stu-id="a9163-138">Also note that this entry will be removed if ARP aging is active or if the ARP cache is exhausted and this is the least recently used ARP entry.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-139">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-139">Parameters</span></span>

- <span data-ttu-id="a9163-140">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-140">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-141">**ip_address**: dirección IP que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="a9163-141">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="a9163-142">**physical_msw**: los 16 bits superiores (47-32) de la dirección física.</span><span class="sxs-lookup"><span data-stu-id="a9163-142">**physical_msw** Top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="a9163-143">**physical_lsw**: los 32 bits inferiores (31-0) de la dirección física.</span><span class="sxs-lookup"><span data-stu-id="a9163-143">**physical_lsw** Lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-144">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-144">Return Values</span></span>

- <span data-ttu-id="a9163-145">**NX_SUCCESS**: (0x00) la entrada dinámica de ARP se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-145">**NX_SUCCESS** (0x00) Successful ARP dynamic entry set.</span></span>
- <span data-ttu-id="a9163-146">**NX_NO_MORE_ENTRIES**: (0X17) no hay más entradas de ARP disponibles en la memoria caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-146">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="a9163-147">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-147">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="a9163-148">**NX_PTR_ERROR**: (0x07) el puntero de instancia de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-148">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="a9163-149">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-149">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="a9163-150">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-150">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-151">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-151">Allowed From</span></span>

<span data-ttu-id="a9163-152">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-152">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-153">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-153">Preemption Possible</span></span>

<span data-ttu-id="a9163-154">No</span><span class="sxs-lookup"><span data-stu-id="a9163-154">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-155">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-155">Example</span></span>

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-156">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-156">See Also</span></span>

- <span data-ttu-id="a9163-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span></span>
- <span data-ttu-id="a9163-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span><span class="sxs-lookup"><span data-stu-id="a9163-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="a9163-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="a9163-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_enable"></a><span data-ttu-id="a9163-161">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-161">nx_arp_enable</span></span>

<span data-ttu-id="a9163-162">Habilita el protocolo de resolución de direcciones (ARP).</span><span class="sxs-lookup"><span data-stu-id="a9163-162">Enables Address Resolution Protocol (ARP).</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-163">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-163">Prototype</span></span>

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a><span data-ttu-id="a9163-164">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-164">Description</span></span>

<span data-ttu-id="a9163-165">Este servicio inicializa el componente ARP de NetX para la instancia de IP específica.</span><span class="sxs-lookup"><span data-stu-id="a9163-165">This service initializes the ARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="a9163-166">La inicialización de ARP incluye la configuración de la caché de ARP y varias rutinas de procesamiento de ARP necesarias para enviar y recibir mensajes de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-166">ARP initialization includes setting up the ARP cache and various ARP processing routines necessary for sending and receiving ARP messages.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-167">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-167">Parameters</span></span>

- <span data-ttu-id="a9163-168">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-168">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-169">**arp_cache_memory**: puntero al área de memoria para colocar la caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-169">**arp_cache_memory** Pointer to memory area to place ARP cache.</span></span>
- <span data-ttu-id="a9163-170">**arp_cache_size**: cada entrada de ARP tiene 52 bytes. Por lo tanto el número total de entradas de ARP es el tamaño dividido entre 52.</span><span class="sxs-lookup"><span data-stu-id="a9163-170">**arp_cache_size** Each ARP entry is 52 bytes, the total number of ARP entries is, therefore, the size divided by 52.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-171">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-171">Return Values</span></span>

- <span data-ttu-id="a9163-172">**NX_SUCCESS**: (0x00) ARP se habilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-172">**NX_SUCCESS** (0x00) Successful ARP enable.</span></span>
- <span data-ttu-id="a9163-173">**NX_PTR_ERROR**: (0x07) el puntero de memoria caché o la IP no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-173">**NX_PTR_ERROR** (0x07) Invalid IP or cache memory pointer.</span></span>
- <span data-ttu-id="a9163-174">**NX_SIZE_ERROR**: (0x09) la memoria caché de ARP proporcionada por el usuario es demasiado pequeña.</span><span class="sxs-lookup"><span data-stu-id="a9163-174">**NX_SIZE_ERROR** (0x09) User supplied ARP cache memory is too small.</span></span>
- <span data-ttu-id="a9163-175">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-175">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-176">**NX_ALREADY_ENABLED**: (0X15) este componente ya se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-176">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-177">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-177">Allowed From</span></span>

<span data-ttu-id="a9163-178">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-178">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-179">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-179">Preemption Possible</span></span>

<span data-ttu-id="a9163-180">No</span><span class="sxs-lookup"><span data-stu-id="a9163-180">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-181">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-181">Example</span></span>

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a><span data-ttu-id="a9163-182">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-182">See Also</span></span>

- <span data-ttu-id="a9163-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="a9163-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span><span class="sxs-lookup"><span data-stu-id="a9163-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="a9163-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="a9163-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="a9163-187">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="a9163-187">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="a9163-188">Envía una solicitud de ARP innecesaria.</span><span class="sxs-lookup"><span data-stu-id="a9163-188">Send gratuitous ARP request</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-189">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-189">Prototype</span></span>

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="a9163-190">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-190">Description</span></span>

<span data-ttu-id="a9163-191">Este servicio recorre todas las interfaces físicas para transmitir solicitudes de ARP innecesarias, siempre y cuando la dirección IP de la interfaz sea válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-191">This service goes through all the physical interfaces to transmit gratuitous ARP requests as long as the interface IP address is valid.</span></span> <span data-ttu-id="a9163-192">Si posteriormente se recibe una respuesta de ARP, se llama al controlador de respuesta proporcionado para procesar la respuesta al ARP innecesario.</span><span class="sxs-lookup"><span data-stu-id="a9163-192">If an ARP response is subsequently received, the supplied response handler is called to process the response to the gratuitous ARP.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-193">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-193">Parameters</span></span>

- <span data-ttu-id="a9163-194">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-194">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-195">**response_handler**: puntero a la función de control de respuesta.</span><span class="sxs-lookup"><span data-stu-id="a9163-195">**response_handler** Pointer to response handling function.</span></span> <span data-ttu-id="a9163-196">Si se proporciona NX_NULL, se omiten las respuestas.</span><span class="sxs-lookup"><span data-stu-id="a9163-196">If NX_NULL is supplied, responses are ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-197">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-197">Return Values</span></span>

- <span data-ttu-id="a9163-198">**NX_SUCCESS**: (0x00) se realizó correctamente el envío de ARP innecesario.</span><span class="sxs-lookup"><span data-stu-id="a9163-198">**NX_SUCCESS** (0x00) Successful gratuitous ARP send.</span></span>
- <span data-ttu-id="a9163-199">**NX_NO_PACKET**: (0X01) no hay ningún paquete disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-199">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="a9163-200">**NX_NOT_ENABLED**: (0x14) ARP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-200">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="a9163-201">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP actual no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-201">**NX_IP_ADDRESS_ERROR** (0x21) Current IP address is invalid.</span></span>
- <span data-ttu-id="a9163-202">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-202">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-203">**NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="a9163-203">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-204">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-204">Allowed From</span></span>

<span data-ttu-id="a9163-205">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-206">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-206">Preemption Possible</span></span>

<span data-ttu-id="a9163-207">No</span><span class="sxs-lookup"><span data-stu-id="a9163-207">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-208">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-208">Example</span></span>

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-209">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-209">See Also</span></span>

- <span data-ttu-id="a9163-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="a9163-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="a9163-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="a9163-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="a9163-214">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="a9163-214">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="a9163-215">Buscar la dirección de hardware físico dada una dirección IP</span><span class="sxs-lookup"><span data-stu-id="a9163-215">Locate physical hardware address given an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-216">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-216">Prototype</span></span>

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a><span data-ttu-id="a9163-217">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-217">Description</span></span>

<span data-ttu-id="a9163-218">Este servicio intenta encontrar una dirección de hardware físico en la memoria caché de ARP que está asociada con la dirección IP proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-218">This service attempts to find a physical hardware address in the ARP cache that is associated with the supplied IP address.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-219">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-219">Parameters</span></span>

- <span data-ttu-id="a9163-220">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-220">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-221">**ip_address**: dirección IP que se buscará.</span><span class="sxs-lookup"><span data-stu-id="a9163-221">**ip_address** IP address to search for.</span></span>
- <span data-ttu-id="a9163-222">**physical_msw**: puntero a la variable para devolver los 16 bits superiores (47-32) de la dirección física.</span><span class="sxs-lookup"><span data-stu-id="a9163-222">**physical_msw** Pointer to the variable for returning the top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="a9163-223">**physical_lsw**: puntero a la variable para devolver los 32 bits inferiores (31-0) de la dirección física.</span><span class="sxs-lookup"><span data-stu-id="a9163-223">**physical_lsw** Pointer to the variable for returning the lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-224">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-224">Return Values</span></span>

- <span data-ttu-id="a9163-225">**NX_SUCCESS**: (0x00) se encontró la dirección de hardware de ARP correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-225">**NX_SUCCESS** (0x00) Successful ARP hardware address find.</span></span>
- <span data-ttu-id="a9163-226">**NX_ENTRY_NOT_FOUND**: (0x16) no se encontró la asignación en la memoria caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-226">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="a9163-227">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-227">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="a9163-228">**NX_PTR_ERROR** (0x07) Puntero de memoria o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-228">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="a9163-229">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-229">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-230">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-230">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-231">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-231">Allowed From</span></span>

<span data-ttu-id="a9163-232">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-232">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-233">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-233">Preemption Possible</span></span>

<span data-ttu-id="a9163-234">No</span><span class="sxs-lookup"><span data-stu-id="a9163-234">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-235">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-235">Example</span></span>

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a><span data-ttu-id="a9163-236">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-236">See Also</span></span>

- <span data-ttu-id="a9163-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="a9163-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,</span></span>
- <span data-ttu-id="a9163-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="a9163-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_info_get"></a><span data-ttu-id="a9163-241">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-241">nx_arp_info_get</span></span>

<span data-ttu-id="a9163-242">Recupera información acerca de las actividades de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-242">Retrieve information about ARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-243">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-243">Prototype</span></span>

```C
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="a9163-244">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-244">Description</span></span>

<span data-ttu-id="a9163-245">Este servicio recupera información sobre las actividades de ARP de la instancia de IP asociada.</span><span class="sxs-lookup"><span data-stu-id="a9163-245">This service retrieves information about ARP activities for the associated IP instance.</span></span>

<span data-ttu-id="a9163-246">*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de la llamada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-246">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-247">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-247">Parameters</span></span>

- <span data-ttu-id="a9163-248">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-248">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-249">**arp_requests_sent**: puntero al destino para el total de solicitudes de ARP enviadas desde esta instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-249">**arp_requests_sent** Pointer to destination for the total ARP requests sent from this IP instance.</span></span>
- <span data-ttu-id="a9163-250">**arp_requests_received**: puntero al destino para el total de solicitudes de ARP recibidas de la red.</span><span class="sxs-lookup"><span data-stu-id="a9163-250">**arp_requests_received** Pointer to destination for the total ARP requests received from the network.</span></span>
- <span data-ttu-id="a9163-251">**arp_responses_sent**: puntero al destino para el total de respuestas de ARP enviadas desde esta instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-251">**arp_responses_sent** Pointer to destination for the total ARP responses sent from this IP instance.</span></span>
- <span data-ttu-id="a9163-252">**arp_responses_received**: puntero al destino para el total de respuestas de ARP recibidas de la red.</span><span class="sxs-lookup"><span data-stu-id="a9163-252">**arp_responses_received** Pointer to the destination for the total ARP responses received from the network.</span></span>
- <span data-ttu-id="a9163-253">**arp_dynamic_entries**: puntero al destino para el número actual de entradas de ARP dinámicas.</span><span class="sxs-lookup"><span data-stu-id="a9163-253">**arp_dynamic_entries** Pointer to the destination for the current number of dynamic ARP entries.</span></span>
- <span data-ttu-id="a9163-254">**arp_static_entries**: puntero al destino para el número actual de entradas de ARP estáticas.</span><span class="sxs-lookup"><span data-stu-id="a9163-254">**arp_static_entries** Pointer to the destination for the current number of static ARP entries.</span></span>
- <span data-ttu-id="a9163-255">**arp_aged_entries**: puntero al destino del número total de entradas de ARP que han vencido y han dejado de ser válidas.</span><span class="sxs-lookup"><span data-stu-id="a9163-255">**arp_aged_entries** Pointer to the destination of the total number of ARP entries that have aged and became invalid.</span></span>
- <span data-ttu-id="a9163-256">**arp_invalid_messages**: puntero al destino del total de mensajes de ARP no válidos recibidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-256">**arp_invalid_messages** Pointer to the destination of the total invalid ARP messages received.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-257">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-257">Return Values</span></span>

- <span data-ttu-id="a9163-258">**NX_SUCCESS**: (0x00) la información de ARP se recuperó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-258">**NX_SUCCESS** (0x00) Successful ARP information retrieval.</span></span>
- <span data-ttu-id="a9163-259">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-259">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-260">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-260">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-261">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-261">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-262">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-262">Allowed From</span></span>

<span data-ttu-id="a9163-263">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-263">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-264">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-264">Preemption Possible</span></span>

<span data-ttu-id="a9163-265">No</span><span class="sxs-lookup"><span data-stu-id="a9163-265">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-266">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-266">Example</span></span>

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
    &arp_requests_received,
    &arp_responses_sent,
    &arp_responses_received,
    &arp_dynamic_entries,
    &arp_static_entries,
    &arp_aged_entries,
    &arp_invalid_messages);
/* If status is NX_SUCCESS, the ARP information has been stored in
    the supplied variables. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-267">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-267">See Also</span></span>

- <span data-ttu-id="a9163-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="a9163-269">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-269">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="a9163-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span><span class="sxs-lookup"><span data-stu-id="a9163-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span></span>
- <span data-ttu-id="a9163-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="a9163-272">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-272">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_ip_address_find"></a><span data-ttu-id="a9163-273">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="a9163-273">nx_arp_ip_address_find</span></span>

<span data-ttu-id="a9163-274">Busca la dirección IP según una dirección física.</span><span class="sxs-lookup"><span data-stu-id="a9163-274">Locate IP address given a physical address</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-275">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-275">Prototype</span></span>

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="a9163-276">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-276">Description</span></span>

<span data-ttu-id="a9163-277">Este servicio intenta buscar una dirección IP en la memoria caché de ARP que está asociada con la dirección física proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-277">This service attempts to find an IP address in the ARP cache that is associated with the supplied physical address.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-278">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-278">Parameters</span></span>

- <span data-ttu-id="a9163-279">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-279">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-280">**ip_address**: puntero para devolver la dirección IP, si se encuentra una que se ha asignado.</span><span class="sxs-lookup"><span data-stu-id="a9163-280">**ip_address** Pointer to return IP address, if one is found that has been mapped.</span></span>
- <span data-ttu-id="a9163-281">**physical_msw**: los 16 bits superiores (47-32) de la dirección física que se buscará.</span><span class="sxs-lookup"><span data-stu-id="a9163-281">**physical_msw** Top 16 bits (47-32) of the physical address to search for.</span></span>
- <span data-ttu-id="a9163-282">**physical_lsw**: los 32 bits inferiores (31-0) de la dirección física que se buscará.</span><span class="sxs-lookup"><span data-stu-id="a9163-282">**physical_lsw** Lower 32 bits (31-0) of the physical address to search for.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-283">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-283">Return Values</span></span>

- <span data-ttu-id="a9163-284">**NX_SUCCESS**: (0x00) se encontró la dirección IP de ARP correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-284">**NX_SUCCESS** (0x00) Successful ARP IP address find</span></span>
- <span data-ttu-id="a9163-285">**NX_ENTRY_NOT_FOUND**: (0x16) no se encontró la asignación en la memoria caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-285">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="a9163-286">**NX_PTR_ERROR** (0x07) Puntero de memoria o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-286">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="a9163-287">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-287">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-288">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-288">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="a9163-289">**NX_INVALID_PARAMETERS**: (0x4D) los elementos Physical_msw y physical_lsw son 0.</span><span class="sxs-lookup"><span data-stu-id="a9163-289">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-290">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-290">Allowed From</span></span>

<span data-ttu-id="a9163-291">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-291">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-292">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-292">Preemption Possible</span></span>

<span data-ttu-id="a9163-293">No</span><span class="sxs-lookup"><span data-stu-id="a9163-293">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-294">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-294">Example</span></span>

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a><span data-ttu-id="a9163-295">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-295">See Also</span></span>

- <span data-ttu-id="a9163-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="a9163-297">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-297">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="a9163-298">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-298">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="a9163-299">nx_arp_static_entries_delete,nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-299">nx_arp_static_entries_delete,nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="a9163-300">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-300">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="a9163-301">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-301">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="a9163-302">Elimina todas las entradas de ARP estáticas.</span><span class="sxs-lookup"><span data-stu-id="a9163-302">Delete all static ARP entries</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-303">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-303">Prototype</span></span>

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-304">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-304">Description</span></span>

<span data-ttu-id="a9163-305">Este servicio elimina todas las entradas estáticas en la caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-305">This service deletes all static entries in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-306">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-306">Parameters</span></span>

- <span data-ttu-id="a9163-307">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-307">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-308">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-308">Return Values</span></span>

- <span data-ttu-id="a9163-309">**NX_SUCCESS**: (0x00) se eliminan las entradas estáticas.</span><span class="sxs-lookup"><span data-stu-id="a9163-309">**NX_SUCCESS** (0x00) Static entries are deleted.</span></span>
- <span data-ttu-id="a9163-310">**NX_PTR_ERROR** (0x07) Puntero ip_ptr no válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-310">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>
- <span data-ttu-id="a9163-311">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-311">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-312">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-312">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-313">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-313">Allowed From</span></span>

<span data-ttu-id="a9163-314">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-314">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-315">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-315">Preemption Possible</span></span>

<span data-ttu-id="a9163-316">No</span><span class="sxs-lookup"><span data-stu-id="a9163-316">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-317">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-317">Example</span></span>

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-318">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-318">See Also</span></span>

- <span data-ttu-id="a9163-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="a9163-320">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-320">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="a9163-321">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-321">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="a9163-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="a9163-323">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-323">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_create"></a><span data-ttu-id="a9163-324">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="a9163-324">nx_arp_static_entry_create</span></span>

<span data-ttu-id="a9163-325">Crea una dirección IP estática para la asignación de hardware en la caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-325">Create static IP to hardware mapping in ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-326">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-326">Prototype</span></span>

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="a9163-327">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-327">Description</span></span>

<span data-ttu-id="a9163-328">Este servicio crea una asignación estática de la dirección IP a la dirección física en la caché de ARP para la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-328">This service creates a static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span> <span data-ttu-id="a9163-329">Las entradas de ARP estáticas no están sujetas a actualizaciones periódicas de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-329">Static ARP entries are not subject to ARP periodic updates.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-330">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-330">Parameters</span></span>

- <span data-ttu-id="a9163-331">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-331">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-332">**ip_address**: dirección IP que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="a9163-332">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="a9163-333">**physical_msw**: los 16 bits superiores (47-32) de la dirección física que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="a9163-333">**physical_msw** Top 16 bits (47-32) of the physical address to map.</span></span>
- <span data-ttu-id="a9163-334">**physical_lsw**: los 32 bits inferiores (31-0) de la dirección física que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="a9163-334">**physical_lsw** Lower 32 bits (31-0) of the physical address to map.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-335">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-335">Return Values</span></span>

- <span data-ttu-id="a9163-336">**NX_SUCCESS**: (0x00) la entrada estática de ARP se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-336">**NX_SUCCESS** (0x00) Successful ARP static entry create.</span></span>
- <span data-ttu-id="a9163-337">**NX_NO_MORE_ENTRIES**: (0X17) no hay más entradas de ARP disponibles en la memoria caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-337">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="a9163-338">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-338">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="a9163-339">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-339">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-340">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-340">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-341">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-341">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="a9163-342">**NX_INVALID_PARAMETERS**: (0x4D) los elementos Physical_msw y physical_lsw son 0.</span><span class="sxs-lookup"><span data-stu-id="a9163-342">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-343">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-343">Allowed From</span></span>

<span data-ttu-id="a9163-344">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-344">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-345">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-345">Preemption Possible</span></span>

<span data-ttu-id="a9163-346">No</span><span class="sxs-lookup"><span data-stu-id="a9163-346">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-347">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-347">Example</span></span>

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-348">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-348">See Also</span></span>

- <span data-ttu-id="a9163-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="a9163-350">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-350">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="a9163-351">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-351">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="a9163-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="a9163-353">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-353">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="a9163-354">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-354">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="a9163-355">Elimina una dirección IP estática para la asignación de hardware en la caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-355">Delete static IP to hardware mapping in ARP cache</span></span>


### <a name="prototype"></a><span data-ttu-id="a9163-356">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-356">Prototype</span></span>

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="a9163-357">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-357">Description</span></span>

<span data-ttu-id="a9163-358">Este servicio busca y elimina una asignación estática de dirección IP a dirección física creada anteriormente en la caché de ARP para la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-358">This service finds and deletes a previously created static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-359">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-359">Parameters</span></span>

- <span data-ttu-id="a9163-360">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-360">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-361">**ip_address**: la dirección IP se asignó estáticamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-361">**ip_address** IP address that was mapped statically.</span></span>
- <span data-ttu-id="a9163-362">**physical_msw**: los 16 bits superiores (47-32) de la dirección física asignada estáticamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-362">**physical_msw** Top 16 bits (47 - 32) of the physical address that was mapped statically.</span></span>
- <span data-ttu-id="a9163-363">**physical_lsw**: los 32 bits inferiores (31-0) de la dirección física asignada estáticamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-363">**physical_lsw** Lower 32 bits (31 - 0) of the physical address that was mapped statically.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-364">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-364">Return Values</span></span>

- <span data-ttu-id="a9163-365">**NX_SUCCESS**: (0x00) la entrada estática de ARP se eliminó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-365">**NX_SUCCESS** (0x00) Successful ARP static entry delete.</span></span>
- <span data-ttu-id="a9163-366">**NX_ENTRY_NOT_FOUND**: (0x16) no se encontró la entrada de ARP estática en la caché de ARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-366">**NX_ENTRY_NOT_FOUND** (0x16) Static ARP entry was not found in the ARP cache.</span></span>
- <span data-ttu-id="a9163-367">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-367">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-368">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-368">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-369">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-369">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="a9163-370">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-370">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="a9163-371">**NX_INVALID_PARAMETERS**: (0x4D) los elementos Physical_msw y physical_lsw son 0.</span><span class="sxs-lookup"><span data-stu-id="a9163-371">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-372">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-372">Allowed From</span></span>

<span data-ttu-id="a9163-373">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-373">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-374">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-374">Preemption Possible</span></span>

<span data-ttu-id="a9163-375">No</span><span class="sxs-lookup"><span data-stu-id="a9163-375">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-376">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-376">Example</span></span>

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-377">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-377">See Also</span></span>

- <span data-ttu-id="a9163-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="a9163-379">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-379">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="a9163-380">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-380">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="a9163-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="a9163-382">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="a9163-382">nx_arp_static_entry_create</span></span>

## <a name="nx_icmp_enable"></a><span data-ttu-id="a9163-383">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-383">nx_icmp_enable</span></span>

<span data-ttu-id="a9163-384">Habilita el Protocolo de mensajes de control de Internet (ICMP).</span><span class="sxs-lookup"><span data-stu-id="a9163-384">Enable Internet Control Message Protocol (ICMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-385">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-385">Prototype</span></span>

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-386">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-386">Description</span></span>

<span data-ttu-id="a9163-387">Este servicio habilita el componente ICMP para la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-387">This service enables the ICMP component for the specified IP instance.</span></span>
<span data-ttu-id="a9163-388">El componente ICMP es responsable de controlar los mensajes de error de Internet y las solicitudes y respuestas de ping.</span><span class="sxs-lookup"><span data-stu-id="a9163-388">The ICMP component is responsible for handling Internet error messages and ping requests and replies.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-389">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-389">Parameters</span></span>

- <span data-ttu-id="a9163-390">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-390">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-391">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-391">Return Values</span></span>

- <span data-ttu-id="a9163-392">**NX_SUCCESS**: (0x00) ICMP se habilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-392">**NX_SUCCESS** (0x00) Successful ICMP enable.</span></span>
- <span data-ttu-id="a9163-393">**NX_ALREADY_ENABLED**: (0x15) ICMP ya está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-393">**NX_ALREADY_ENABLED** (0x15) ICMP is already enabled.</span></span>
- <span data-ttu-id="a9163-394">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-394">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-395">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-395">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-396">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-396">Allowed From</span></span>

<span data-ttu-id="a9163-397">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-397">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-398">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-398">Preemption Possible</span></span>

<span data-ttu-id="a9163-399">No</span><span class="sxs-lookup"><span data-stu-id="a9163-399">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-400">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-400">Example</span></span>

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-401">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-401">See Also</span></span>

- <span data-ttu-id="a9163-402">nx_icmp_info_get, nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="a9163-402">nx_icmp_info_get, nx_icmp_ping</span></span>

## <a name="nx_icmp_info_get"></a><span data-ttu-id="a9163-403">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-403">nx_icmp_info_get</span></span>

<span data-ttu-id="a9163-404">Recupera información acerca de las actividades de ICMP.</span><span class="sxs-lookup"><span data-stu-id="a9163-404">Retrieve information about ICMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-405">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-405">Prototype</span></span>

```C
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```

### <a name="description"></a><span data-ttu-id="a9163-406">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-406">Description</span></span>

<span data-ttu-id="a9163-407">Este servicio recupera información sobre las actividades de ICMP de la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-407">This service retrieves information about ICMP activities for the specified IP instance.</span></span>

<span data-ttu-id="a9163-408">*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de la llamada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-408">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-409">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-409">Parameters</span></span>

- <span data-ttu-id="a9163-410">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-410">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-411">**pings_sent**: puntero al destino para el número total de pings enviados.</span><span class="sxs-lookup"><span data-stu-id="a9163-411">**pings_sent** Pointer to destination for the total number of pings sent.</span></span>
- <span data-ttu-id="a9163-412">**ping_timeouts**: puntero al destino para el número total de tiempos de espera de ping.</span><span class="sxs-lookup"><span data-stu-id="a9163-412">**ping_timeouts** Pointer to destination for the total number of ping timeouts.</span></span>
- <span data-ttu-id="a9163-413">**ping_threads_suspended**: puntero al destino del número total de subprocesos suspendidos en solicitudes de ping.</span><span class="sxs-lookup"><span data-stu-id="a9163-413">**ping_threads_suspended** Pointer to destination of the total number of threads suspended on ping requests.</span></span>
- <span data-ttu-id="a9163-414">**ping_responses_received**: puntero al destino del número total de respuestas de ping recibidas.</span><span class="sxs-lookup"><span data-stu-id="a9163-414">**ping_responses_received** Pointer to estination of the total number of ping responses received.</span></span>
- <span data-ttu-id="a9163-415">**icmp_checksum_errors**: puntero al destino del número total de errores de suma de comprobación de ICMP.</span><span class="sxs-lookup"><span data-stu-id="a9163-415">**icmp_checksum_errors** Pointer to destination of the total number of ICMP checksum errors.</span></span>
- <span data-ttu-id="a9163-416">**icmp_unhandled_messages**: puntero al destino del número total de mensajes de ICMP no administrados.</span><span class="sxs-lookup"><span data-stu-id="a9163-416">**icmp_unhandled_messages** Pointer to estination of the total number of un-handled ICMP messages.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-417">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-417">Return Values</span></span>

- <span data-ttu-id="a9163-418">**NX_SUCCESS**: (0x00) la información de ICMP se recuperó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-418">**NX_SUCCESS** (0x00) Successful ICMP information retrieval.</span></span>
- <span data-ttu-id="a9163-419">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-419">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-420">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-420">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-421">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-421">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-422">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-422">Allowed From</span></span>

<span data-ttu-id="a9163-423">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-423">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-424">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-424">Preemption Possible</span></span>

<span data-ttu-id="a9163-425">No</span><span class="sxs-lookup"><span data-stu-id="a9163-425">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-426">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-426">Example</span></span>

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-427">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-427">See Also</span></span>

- <span data-ttu-id="a9163-428">nx_icmp_enable, nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="a9163-428">nx_icmp_enable, nx_icmp_ping</span></span>

## <a name="nx_icmp_ping"></a><span data-ttu-id="a9163-429">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="a9163-429">nx_icmp_ping</span></span>

<span data-ttu-id="a9163-430">Envía una solicitud de ping a la dirección IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-430">Send ping request to specified IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-431">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-431">Prototype</span></span>

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-432">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-432">Description</span></span>

<span data-ttu-id="a9163-433">Este servicio envía una solicitud de ping a la dirección IP especificada y espera un mensaje de respuesta de ping durante el período de tiempo especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-433">This service sends a ping request to the specified IP address and waits for the specified amount of time for a ping response message.</span></span> <span data-ttu-id="a9163-434">Si no se recibe ninguna respuesta, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="a9163-434">If no response is received, an error is returned.</span></span> <span data-ttu-id="a9163-435">De lo contrario, se devuelve el mensaje de respuesta completo en la variable a la que apunta el elemento response_ptr.</span><span class="sxs-lookup"><span data-stu-id="a9163-435">Otherwise, the entire response message is returned in the variable pointed to by response_ptr.</span></span>

<span data-ttu-id="a9163-436">*Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido cuando ya no se necesite.*</span><span class="sxs-lookup"><span data-stu-id="a9163-436">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet after it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-437">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-437">Parameters</span></span>

- <span data-ttu-id="a9163-438">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-438">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-439">**ip_address**: dirección IP, en orden de bytes del host, a la que se va a hacer ping.</span><span class="sxs-lookup"><span data-stu-id="a9163-439">**ip_address** IP address, in host byte order, to ping.</span></span> <span data-ttu-id="a9163-440">Puntero de datos al área de datos para el mensaje de ping.</span><span class="sxs-lookup"><span data-stu-id="a9163-440">data Pointer to data area for ping message.</span></span>
- <span data-ttu-id="a9163-441">**data_size**: número de bytes en los datos de ping</span><span class="sxs-lookup"><span data-stu-id="a9163-441">**data_size** Number of bytes in the ping data</span></span>
- <span data-ttu-id="a9163-442">**response_ptr**: puntero al puntero de paquete en el que se devuelve el mensaje de respuesta de ping.</span><span class="sxs-lookup"><span data-stu-id="a9163-442">**response_ptr** Pointer to packet pointer to return the ping response message in.</span></span>
- <span data-ttu-id="a9163-443">**wait_option**: define cuánto tiempo se debe esperar una respuesta de ping.</span><span class="sxs-lookup"><span data-stu-id="a9163-443">**wait_option** Defines how long to wait for a ping response.</span></span> <span data-ttu-id="a9163-444">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-444">wait options are defined as follows:</span></span>

  - <span data-ttu-id="a9163-445">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-445">NX_NO_WAIT (0x00000000)</span></span>
  - <span data-ttu-id="a9163-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="a9163-447">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-447">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-448">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-448">Return Values</span></span>

- <span data-ttu-id="a9163-449">**NX_SUCCESS**: (0x00) el ping se hizo correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-449">**NX_SUCCESS** (0x00) Successful ping.</span></span> <span data-ttu-id="a9163-450">El puntero del mensaje de respuesta se ha colocado en la variable a la que apunta el elemento response_ptr.</span><span class="sxs-lookup"><span data-stu-id="a9163-450">Response message pointer was placed in the variable pointed to by response_ptr.</span></span>
- <span data-ttu-id="a9163-451">**NX_NO_PACKET**: (0X01) no se pudo asignar un paquete de solicitud de ping.</span><span class="sxs-lookup"><span data-stu-id="a9163-451">**NX_NO_PACKET** (0x01) Unable to allocate a ping request packet.</span></span>
- <span data-ttu-id="a9163-452">**NX_OVERFLOW**: (0x03) el área de datos especificada supera el tamaño de paquete predeterminado para esta instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-452">**NX_OVERFLOW** (0x03) Specified data area exceeds the default packet size for this IP instance.</span></span>
- <span data-ttu-id="a9163-453">**NX_NO_RESPONSE**: (0x29) la IP solicitada no ha respondido.</span><span class="sxs-lookup"><span data-stu-id="a9163-453">**NX_NO_RESPONSE** (0x29) Requested IP did not respond.</span></span>
- <span data-ttu-id="a9163-454">**NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-454">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="a9163-455">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-455">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="a9163-456">**NX_PTR_ERROR** (0x07) Puntero de respuesta o IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-456">**NX_PTR_ERROR** (0x07) Invalid IP or response pointer.</span></span>
- <span data-ttu-id="a9163-457">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-457">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-458">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-458">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-459">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-459">Allowed From</span></span>

<span data-ttu-id="a9163-460">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-460">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-461">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-461">Preemption Possible</span></span>

<span data-ttu-id="a9163-462">No</span><span class="sxs-lookup"><span data-stu-id="a9163-462">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-463">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-463">Example</span></span>

```C
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
    Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
    &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
    address 1.2.3.5 and the response packet is contained in the
    packet pointed to by response_ptr. It should have the same "abcd"
    four bytes of data. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-464">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-464">See Also</span></span>

- <span data-ttu-id="a9163-465">nx_icmp_enable, nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-465">nx_icmp_enable, nx_icmp_info_get</span></span>

## <a name="nx_igmp_enable"></a><span data-ttu-id="a9163-466">nx_igmp_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-466">nx_igmp_enable</span></span>

<span data-ttu-id="a9163-467">Habilita el protocolo de administración de grupos de Internet (IGMP).</span><span class="sxs-lookup"><span data-stu-id="a9163-467">Enable Internet Group Management Protocol (IGMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-468">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-468">Prototype</span></span>

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-469">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-469">Description</span></span>

<span data-ttu-id="a9163-470">Este servicio habilita el componente IGMP en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-470">This service enables the IGMP component on the specified IP instance.</span></span>
<span data-ttu-id="a9163-471">El componente IGMP es responsable de proporcionar compatibilidad con las operaciones de administración de grupos de multidifusión de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-471">The IGMP component is responsible for providing support for IP multicast group management operations.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-472">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-472">Parameters</span></span>

- <span data-ttu-id="a9163-473">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-473">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-474">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-474">Return Values</span></span>

- <span data-ttu-id="a9163-475">**NX_SUCCESS**: (0x00) IGMP se habilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-475">**NX_SUCCESS** (0x00) Successful IGMP enable.</span></span>
- <span data-ttu-id="a9163-476">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-476">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-477">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-477">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-478">**NX_ALREADY_ENABLED**: (0X15) este componente ya se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-478">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-479">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-479">Allowed From</span></span>

<span data-ttu-id="a9163-480">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-480">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-481">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-481">Preemption Possible</span></span>

<span data-ttu-id="a9163-482">No</span><span class="sxs-lookup"><span data-stu-id="a9163-482">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-483">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-483">Example</span></span>

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-484">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-484">See Also</span></span>

- <span data-ttu-id="a9163-485">nx_igmp_info_get,nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-485">nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="a9163-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="a9163-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="a9163-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="a9163-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_info_get"></a><span data-ttu-id="a9163-488">nx_igmp_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-488">nx_igmp_info_get</span></span>

<span data-ttu-id="a9163-489">Recupera información acerca de las actividades de IGMP.</span><span class="sxs-lookup"><span data-stu-id="a9163-489">Retrieve information about IGMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-490">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-490">Prototype</span></span>

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a><span data-ttu-id="a9163-491">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-491">Description</span></span>

<span data-ttu-id="a9163-492">Este servicio recupera información sobre las actividades de IGMP de la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-492">This service retrieves information about IGMP activities for the specified IP instance.</span></span>

<span data-ttu-id="a9163-493">*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de la llamada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-493">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-494">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-494">Parameters</span></span>

- <span data-ttu-id="a9163-495">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-495">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-496">**igmp_reports_sent**: puntero al destino para el número total de informes de ICMP enviados.</span><span class="sxs-lookup"><span data-stu-id="a9163-496">**igmp_reports_sent** Pointer to destination for the total number of ICMP reports sent.</span></span>
- <span data-ttu-id="a9163-497">**igmp_queries_received**: puntero al destino para el número total de consultas recibidas por el enrutador de multidifusión.</span><span class="sxs-lookup"><span data-stu-id="a9163-497">**igmp_queries_received** Pointer to destination for the total number of queries received by multicast router.</span></span>
- <span data-ttu-id="a9163-498">**igmp_checksum_errors**: puntero al destino del número total de errores de suma de comprobación de IGMP en paquetes recibidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-498">**igmp_checksum_errors** Pointer to destination of the total number of IGMP checksum errors on receive packets.</span></span>
- <span data-ttu-id="a9163-499">**current_groups_joined**: puntero al destino del número actual de grupos unidos a través de esta instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-499">**current_groups_joined** Pointer to destination of the current number of groups joined through this IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-500">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-500">Return Values</span></span>

- <span data-ttu-id="a9163-501">**NX_SUCCESS**: (0x00) la información de IGMP se recuperó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-501">**NX_SUCCESS** (0x00) Successful IGMP information retrieval.</span></span>
- <span data-ttu-id="a9163-502">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-502">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-503">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-503">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-504">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-504">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-505">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-505">Allowed From</span></span>

<span data-ttu-id="a9163-506">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-506">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-507">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-507">Preemption Possible</span></span>

<span data-ttu-id="a9163-508">No</span><span class="sxs-lookup"><span data-stu-id="a9163-508">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-509">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-509">Example</span></span>

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-510">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-510">See Also</span></span>

- <span data-ttu-id="a9163-511">nx_igmp_enable, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-511">nx_igmp_enable, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="a9163-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="a9163-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="a9163-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="a9163-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="a9163-514">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="a9163-514">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="a9163-515">Deshabilita el bucle invertido de IGMP.</span><span class="sxs-lookup"><span data-stu-id="a9163-515">Disable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-516">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-516">Prototype</span></span>

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-517">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-517">Description</span></span>

<span data-ttu-id="a9163-518">Este servicio deshabilita el bucle invertido de IGMP para todos los grupos de multidifusión posteriores combinados.</span><span class="sxs-lookup"><span data-stu-id="a9163-518">This service disables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-519">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-519">Parameters</span></span>

- <span data-ttu-id="a9163-520">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-520">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-521">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-521">Return Values</span></span>
- <span data-ttu-id="a9163-522">**NX_SUCCESS**: (0x00) el bucle invertido de IGMP se deshabilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-522">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="a9163-523">**NX_NOT_ENABLED** (0x14) IGMP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-523">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="a9163-524">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-524">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-525">**NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso ni una inicialización.</span><span class="sxs-lookup"><span data-stu-id="a9163-525">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-526">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-526">Allowed From</span></span>

<span data-ttu-id="a9163-527">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-527">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-528">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-528">Preemption Possible</span></span>

<span data-ttu-id="a9163-529">No</span><span class="sxs-lookup"><span data-stu-id="a9163-529">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-530">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-530">Example</span></span>

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-531">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-531">See Also</span></span>

- <span data-ttu-id="a9163-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,</span></span>
- <span data-ttu-id="a9163-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="a9163-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="a9163-534">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="a9163-534">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="a9163-535">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-535">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="a9163-536">Habilita el bucle invertido de IGMP.</span><span class="sxs-lookup"><span data-stu-id="a9163-536">Enable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-537">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-537">Prototype</span></span>

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-538">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-538">Description</span></span>

<span data-ttu-id="a9163-539">Este servicio habilita el bucle invertido de IGMP para todos los grupos de multidifusión posteriores combinados.</span><span class="sxs-lookup"><span data-stu-id="a9163-539">This service enables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-540">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-540">Parameters</span></span>

- <span data-ttu-id="a9163-541">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-541">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-542">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-542">Return Values</span></span>
- <span data-ttu-id="a9163-543">**NX_SUCCESS**: (0x00) el bucle invertido de IGMP se deshabilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-543">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="a9163-544">**NX_NOT_ENABLED** (0x14) IGMP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-544">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="a9163-545">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-545">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-546">**NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso ni una inicialización.</span><span class="sxs-lookup"><span data-stu-id="a9163-546">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-547">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-547">Allowed From</span></span>

<span data-ttu-id="a9163-548">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-548">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-549">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-549">Preemption Possible</span></span>

<span data-ttu-id="a9163-550">No</span><span class="sxs-lookup"><span data-stu-id="a9163-550">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-551">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-551">Example</span></span>

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-552">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-552">See Also</span></span>

- <span data-ttu-id="a9163-553">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-553">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="a9163-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="a9163-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="a9163-555">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="a9163-555">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_interface_join"></a><span data-ttu-id="a9163-556">nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="a9163-556">nx_igmp_multicast_interface_join</span></span>

<span data-ttu-id="a9163-557">Conecta la instancia de IP al grupo de multidifusión especificado a través de una interfaz.</span><span class="sxs-lookup"><span data-stu-id="a9163-557">Join IP instance to specified multicast group via an interface</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-558">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-558">Prototype</span></span>

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="a9163-559">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-559">Description</span></span>

<span data-ttu-id="a9163-560">Este servicio conecta una instancia de IP al grupo de multidifusión especificado a través de una interfaz de red especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-560">This service joins an IP instance to the specified multicast group via a specified network interface.</span></span> <span data-ttu-id="a9163-561">Se mantiene un contador interno para realizar un seguimiento del número de veces que se ha unido el mismo grupo.</span><span class="sxs-lookup"><span data-stu-id="a9163-561">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="a9163-562">Después de unirse al grupo de multidifusión, el componente IGMP permitirá la recepción de paquetes IP con esta dirección de grupo a través de la interfaz de red especificada y también notificará a los enrutadores que esta IP forma parte de este grupo de multidifusión.</span><span class="sxs-lookup"><span data-stu-id="a9163-562">After joining the multicast group, the IGMP component will allow reception of IP packets with this group address via the specified network interface and also report to routers that this IP is a member of this multicast group.</span></span> <span data-ttu-id="a9163-563">Los mensajes de unión, informe y abandono de la pertenencia a IGMP también se envían a través de la interfaz de red especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-563">The IGMP membership join, report, and leave messages are also sent via the specified network interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-564">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-564">Parameters</span></span>

- <span data-ttu-id="a9163-565">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-565">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-566">**group_address**: dirección del grupo de multidifusión IP de la clase D que se unirá en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-566">**group_address** Class D IP multicast group address to join in host byte order.</span></span>
- <span data-ttu-id="a9163-567">**interface_index**: índice de la interfaz asociada a la instancia de NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-567">**interface_index** Index of the Interface attached to the NetX instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-568">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-568">Return Values</span></span>

- <span data-ttu-id="a9163-569">**NX_SUCCESS**: (0x00) el grupo de multidifusión se unió correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-569">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="a9163-570">**NX_NO_MORE_ENTRIES**: (0X17) no se pueden unir más grupos de multidifusión; se superó el máximo.</span><span class="sxs-lookup"><span data-stu-id="a9163-570">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="a9163-571">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-571">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-572">**NX_INVALID_INTERFACE**: (0x4C) el índice del dispositivo apunta a una interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-572">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="a9163-573">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección del grupo de multidifusión proporcionada no es una dirección de clase D válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-573">**NX_IP_ADDRESS_ERROR** (0x21) Multicast group address provided is not a valid class D address.</span></span>
- <span data-ttu-id="a9163-574">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-574">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-575">**NX_NOT_ENABLED**: (0x14) la compatibilidad con la multidifusión IP no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-575">**NX_NOT_ENABLED** (0x14) IP multicast support is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-576">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-576">Allowed From</span></span>

<span data-ttu-id="a9163-577">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-577">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-578">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-578">Preemption Possible</span></span>

<span data-ttu-id="a9163-579">No</span><span class="sxs-lookup"><span data-stu-id="a9163-579">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-580">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-580">Example</span></span>

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-581">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-581">See Also</span></span>

- <span data-ttu-id="a9163-582">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-582">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="a9163-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="a9163-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="a9163-584">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="a9163-584">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_join"></a><span data-ttu-id="a9163-585">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="a9163-585">nx_igmp_multicast_join</span></span>

<span data-ttu-id="a9163-586">Conecta la instancia de IP al grupo de multidifusión especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-586">Join IP instance to specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-587">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-587">Prototype</span></span>

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="a9163-588">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-588">Description</span></span>

<span data-ttu-id="a9163-589">Este servicio une una instancia de IP al grupo de multidifusión especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-589">This service joins an IP instance to the specified multicast group.</span></span> <span data-ttu-id="a9163-590">Se mantiene un contador interno para realizar un seguimiento del número de veces que se ha conectado el mismo grupo.</span><span class="sxs-lookup"><span data-stu-id="a9163-590">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="a9163-591">El controlador recibe la orden de enviar un informe de IGMP si se trata de la primera vez que se solicita la unión en la red que indica la intención del host para unirse al grupo.</span><span class="sxs-lookup"><span data-stu-id="a9163-591">The driver is commanded to send an IGMP report if this is the first join request out on the network indicating the host's intention to join the group.</span></span> <span data-ttu-id="a9163-592">Una vez unido, el componente IGMP permitirá la recepción de paquetes IP con esta dirección de grupo y notificará a los enrutadores que esta dirección IP forma parte de este grupo de multidifusión.</span><span class="sxs-lookup"><span data-stu-id="a9163-592">After joining, the IGMP component will allow reception of IP packets with this group address and report to routers that this IP is a member of this multicast group.</span></span>

> [!NOTE]
> <span data-ttu-id="a9163-593">*Para unirse a un grupo de multidifusión en un dispositivo no primario, use el servicio **nx_igmp_multicast_interface_join.***</span><span class="sxs-lookup"><span data-stu-id="a9163-593">*To join a multicast group on a non-primary device, use the service **nx_igmp_multicast_interface_join.***</span></span>

- <span data-ttu-id="a9163-594">**Parámetros**</span><span class="sxs-lookup"><span data-stu-id="a9163-594">**Parameters**</span></span>

- <span data-ttu-id="a9163-595">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-595">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-596">**group_address**: dirección del grupo de multidifusión IP de la clase D que se unirá.</span><span class="sxs-lookup"><span data-stu-id="a9163-596">**group_address** Class D IP multicast group address to join.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-597">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-597">Return Values</span></span>

- <span data-ttu-id="a9163-598">**NX_SUCCESS**: (0x00) el grupo de multidifusión se unió correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-598">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="a9163-599">**NX_NO_MORE_ENTRIES**: (0X17) no se pueden unir más grupos de multidifusión; se superó el máximo.</span><span class="sxs-lookup"><span data-stu-id="a9163-599">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="a9163-600">**NX_INVALID_INTERFACE**: (0x4C) el índice del dispositivo apunta a una interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-600">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="a9163-601">**NX_IP_ADDRESS_ERROR** (0x21) Dirección de grupo IP no válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-601">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="a9163-602">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-602">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-603">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-603">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-604">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-604">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-605">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-605">Allowed From</span></span>

<span data-ttu-id="a9163-606">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-606">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-607">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-607">Preemption Possible</span></span>

<span data-ttu-id="a9163-608">No</span><span class="sxs-lookup"><span data-stu-id="a9163-608">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-609">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-609">Example</span></span>

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-610">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-610">See Also</span></span>

- <span data-ttu-id="a9163-611">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-611">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="a9163-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="a9163-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="a9163-613">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="a9163-613">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="a9163-614">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="a9163-614">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="a9163-615">Hace que la instancia de IP salga del grupo de multidifusión especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-615">Cause IP instance to leave specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-616">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-616">Prototype</span></span>

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="a9163-617">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-617">Description</span></span>

<span data-ttu-id="a9163-618">Este servicio hace que una instancia de IP salga del grupo de multidifusión especificado si el número de solicitudes para salir coincide con el número de solicitudes para unirse.</span><span class="sxs-lookup"><span data-stu-id="a9163-618">This service causes an IP instance to leave the specified multicast group, if the number of leave requests matches the number of join requests.</span></span> <span data-ttu-id="a9163-619">De lo contrario, el recuento de uniones interno simplemente se reduce.</span><span class="sxs-lookup"><span data-stu-id="a9163-619">Otherwise, the internal join count is simply decremented.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-620">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-620">Parameters</span></span>

- <span data-ttu-id="a9163-621">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-621">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-622">**group_address**: grupo de multidifusión que va a salir.</span><span class="sxs-lookup"><span data-stu-id="a9163-622">**group_address** Multicast group to leave.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-623">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-623">Return Values</span></span>

- <span data-ttu-id="a9163-624">**NX_SUCCESS**: (0x00) el grupo de multidifusión se unió correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-624">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="a9163-625">**NX_ENTRY_NOT_FOUND**: (0x16) no se encontró la solicitud anterior para unirse.</span><span class="sxs-lookup"><span data-stu-id="a9163-625">**NX_ENTRY_NOT_FOUND** (0x16) Previous join request was not found.</span></span>
- <span data-ttu-id="a9163-626">**NX_INVALID_INTERFACE**: (0x4C) el índice del dispositivo apunta a una interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-626">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="a9163-627">**NX_IP_ADDRESS_ERROR** (0x21) Dirección de grupo IP no válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-627">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="a9163-628">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-628">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-629">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-629">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-630">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-630">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-631">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-631">Allowed From</span></span>

<span data-ttu-id="a9163-632">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-632">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-633">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-633">Preemption Possible</span></span>

<span data-ttu-id="a9163-634">No</span><span class="sxs-lookup"><span data-stu-id="a9163-634">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-635">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-635">Example</span></span>

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a><span data-ttu-id="a9163-636">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-636">See Also</span></span>

- <span data-ttu-id="a9163-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="a9163-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="a9163-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="a9163-639">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="a9163-639">nx_igmp_multicast_join</span></span>

## <a name="nx_ip_address_change_notifiy"></a><span data-ttu-id="a9163-640">nx_ip_address_change_notifiy</span><span class="sxs-lookup"><span data-stu-id="a9163-640">nx_ip_address_change_notifiy</span></span>

<span data-ttu-id="a9163-641">Envía una notificación a la aplicación si cambia la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-641">Notify application if IP address changes</span></span>


### <a name="prototype"></a><span data-ttu-id="a9163-642">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-642">Prototype</span></span>

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a><span data-ttu-id="a9163-643">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-643">Description</span></span>

<span data-ttu-id="a9163-644">Este servicio registra una función de notificación de la aplicación a la que se llama cada vez que se cambia la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-644">This service registers an application notification function that is called whenever the IP address is changed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-645">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-645">Parameters</span></span>

- <span data-ttu-id="a9163-646">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-646">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-647">**change_notify**: puntero a la función de notificación de cambio de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-647">**change_notify** Pointer to IP change notification function.</span></span> <span data-ttu-id="a9163-648">Si este parámetro es NX_NULL, se deshabilita la notificación de cambio de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-648">If this parameter is NX_NULL, IP address change notification is disabled.</span></span>
- <span data-ttu-id="a9163-649">**additional_info**: puntero a información adicional opcional que también se proporciona a la función de notificación cuando se cambia la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-649">**additional_info** Pointer to optional additional information that is also supplied to the notification function when the IP address is changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-650">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-650">Return Values</span></span>

- <span data-ttu-id="a9163-651">**NX_SUCCESS**: (0x00) el cambio de dirección IP se notificó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-651">**NX_SUCCESS** (0x00) Successful IP address change notification.</span></span>
- <span data-ttu-id="a9163-652">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-652">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-653">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-653">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-654">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-654">Allowed From</span></span>

<span data-ttu-id="a9163-655">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-655">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-656">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-656">Preemption Possible</span></span>

<span data-ttu-id="a9163-657">No</span><span class="sxs-lookup"><span data-stu-id="a9163-657">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-658">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-658">Example</span></span>

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-659">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-659">See Also</span></span>

- <span data-ttu-id="a9163-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span></span>
- <span data-ttu-id="a9163-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="a9163-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="a9163-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="a9163-664">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-664">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_address_get"></a><span data-ttu-id="a9163-665">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="a9163-665">nx_ip_address_get</span></span>

<span data-ttu-id="a9163-666">Recupera la dirección IP y la máscara de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-666">Retrieve IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-667">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-667">Prototype</span></span>

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="a9163-668">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-668">Description</span></span>

<span data-ttu-id="a9163-669">Este servicio recupera la dirección IP y la máscara de subred de la interfaz de red principal.</span><span class="sxs-lookup"><span data-stu-id="a9163-669">This service retrieves IP address and its subnet mask of the primary network interface.</span></span>

<span data-ttu-id="a9163-670">\*Para obtener información del dispositivo secundario, use el servicio siguiente:</span><span class="sxs-lookup"><span data-stu-id="a9163-670">\*To obtain information of the secondary device, use the service</span></span>
- <span data-ttu-id="a9163-671">**nx_ip_interface_address_get**.\*</span><span class="sxs-lookup"><span data-stu-id="a9163-671">**nx_ip_interface_address_get**.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-672">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-672">Parameters</span></span>

- <span data-ttu-id="a9163-673">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-673">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-674">**ip_address**: puntero al destino de la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-674">**ip_address** Pointer to destination for IP address.</span></span>
- <span data-ttu-id="a9163-675">**network_mask**: puntero al destino de la máscara de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-675">**network_mask** Pointer to destination for network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-676">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-676">Return Values</span></span>

- <span data-ttu-id="a9163-677">**NX_SUCCESS**: (0x00) la dirección IP se obtuvo correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-677">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="a9163-678">**NX_PTR_ERROR**: (0X07) la IP o el puntero de variable devuelto no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-678">**NX_PTR_ERROR** (0x07) Invalid IP or return variable pointer.</span></span>
- <span data-ttu-id="a9163-679">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-679">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-680">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-680">Allowed From</span></span>

<span data-ttu-id="a9163-681">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-681">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-682">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-682">Preemption Possible</span></span>

<span data-ttu-id="a9163-683">No</span><span class="sxs-lookup"><span data-stu-id="a9163-683">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-684">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-684">Example</span></span>

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-685">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-685">See Also</span></span>

- <span data-ttu-id="a9163-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,</span></span>
- <span data-ttu-id="a9163-687">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-687">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="a9163-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="a9163-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="a9163-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="a9163-691">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-691">nx_system_initialize</span></span>

## <a name="nx_ip_address_set"></a><span data-ttu-id="a9163-692">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="a9163-692">nx_ip_address_set</span></span>

<span data-ttu-id="a9163-693">Establece la dirección IP y la máscara de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-693">Set IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-694">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-694">Prototype</span></span>

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="a9163-695">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-695">Description</span></span>

<span data-ttu-id="a9163-696">Este servicio establece la dirección IP y la máscara de red para la interfaz de red principal.</span><span class="sxs-lookup"><span data-stu-id="a9163-696">This service sets IP address and network mask for the primary network interface.</span></span>

<span data-ttu-id="a9163-697">*Para establecer la dirección IP y la máscara de red para el dispositivo secundario, use el servicio **nx_ip_interface_address_set**.*</span><span class="sxs-lookup"><span data-stu-id="a9163-697">*To set IP address and network mask for the secondary device, use the service **nx_ip_interface_address_set**.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-698">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-698">Parameters</span></span>

- <span data-ttu-id="a9163-699">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-699">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-700">**ip_address**: nueva dirección IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-700">**ip_address** New IP address.</span></span>
- <span data-ttu-id="a9163-701">**network_mask**: nueva máscara de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-701">**network_mask** New network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-702">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-702">Return Values</span></span>

- <span data-ttu-id="a9163-703">**NX_SUCCESS**: (0x00) la dirección IP se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-703">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="a9163-704">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-704">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="a9163-705">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-705">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-706">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-706">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-707">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-707">Allowed From</span></span>

<span data-ttu-id="a9163-708">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-708">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-709">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-709">Preemption Possible</span></span>

<span data-ttu-id="a9163-710">No</span><span class="sxs-lookup"><span data-stu-id="a9163-710">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-711">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-711">Example</span></span>

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-712">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-712">See Also</span></span>

- <span data-ttu-id="a9163-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,</span></span>
- <span data-ttu-id="a9163-714">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-714">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="a9163-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="a9163-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="a9163-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="a9163-718">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-718">nx_system_initialize</span></span>

## <a name="nx_ip_create"></a><span data-ttu-id="a9163-719">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="a9163-719">nx_ip_create</span></span>

<span data-ttu-id="a9163-720">Crea una instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-720">Create an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-721">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-721">Prototype</span></span>

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="a9163-722">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-722">Description</span></span>

<span data-ttu-id="a9163-723">Este servicio crea una instancia de IP con la dirección IP y el controlador de red que proporcionó el usuario.</span><span class="sxs-lookup"><span data-stu-id="a9163-723">This service creates an IP instance with the user supplied IP address and network driver.</span></span> <span data-ttu-id="a9163-724">Además, la aplicación debe proporcionar un grupo de paquetes creado previamente para la instancia de IP que se va a utilizar para la asignación interna de paquetes.</span><span class="sxs-lookup"><span data-stu-id="a9163-724">In addition, the application must supply a previously created packet pool for the IP instance to use for internal packet allocation.</span></span> <span data-ttu-id="a9163-725">Tenga en cuenta que no se llama al controlador de red de aplicación proporcionado hasta que se ejecuta este subproceso de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-725">Note that the supplied application network driver is not called until this IP's thread executes.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-726">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-726">Parameters</span></span>

- <span data-ttu-id="a9163-727">**ip_ptr**: puntero al bloque de control para crear una nueva instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-727">**ip_ptr** Pointer to control block to create a new IP instance.</span></span>
- <span data-ttu-id="a9163-728">**name**: nombre de esta nueva instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-728">**name** Name of this new IP instance.</span></span>
- <span data-ttu-id="a9163-729">**ip_address**: dirección IP de esta nueva instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-729">**ip_address** IP address for this new IP instance.</span></span>
- <span data-ttu-id="a9163-730">**network_mask**: máscara para delimitar la parte de la red de la dirección IP para los usos de subredes y superredes.</span><span class="sxs-lookup"><span data-stu-id="a9163-730">**network_mask** Mask to delineate the network portion of the IP address for sub-netting and super-netting uses.</span></span>
- <span data-ttu-id="a9163-731">**default_pool**: puntero al bloque de control del grupo de paquetes NetX creado previamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-731">**default_pool** Pointer to control block of previously created NetX packet pool.</span></span>
- <span data-ttu-id="a9163-732">**ip_network_driver**: controlador de red proporcionado por el usuario que se usa para enviar y recibir paquetes IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-732">**ip_network_driver** User-supplied network driver used to send and receive IP packets.</span></span>
- <span data-ttu-id="a9163-733">**memory_ptr**: puntero al área de memoria del área de pila del subproceso del asistente de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-733">**memory_ptr** Pointer to memory area for the IP helper thread’s stack area.</span></span>
- <span data-ttu-id="a9163-734">**memory_size** Número de bytes en el área de memoria para la pila del subproceso del asistente de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-734">**memory_size** Number of bytes in the memory area for the IP helper thread’s stack.</span></span>
- <span data-ttu-id="a9163-735">**priority**: prioridad del subproceso del asistente de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-735">**priority** Priority of IP helper thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-736">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-736">Return Values</span></span>
- <span data-ttu-id="a9163-737">**NX_SUCCESS**: (0x00) la instancia de IP se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-737">**NX_SUCCESS** (0x00) Successful IP instance creation.</span></span>
- <span data-ttu-id="a9163-738">**NX_NOT_IMPLEMENTED**: (0x4A) la biblioteca NetX se configuro incorrectamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-738">**NX_NOT_IMPLEMENTED** (0x4A) NetX library is configured incorrectly.</span></span>
- <span data-ttu-id="a9163-739">**NX_PTR_ERROR**: (0X07) la IP, el puntero de función del controlador de red, el grupo de paquetes o el puntero de memoria no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-739">**NX_PTR_ERROR** (0x07) Invalid IP, network driver function pointer, packet pool, or memory pointer.</span></span>
- <span data-ttu-id="a9163-740">**NX_SIZE_ERROR**: (0X09) el tamaño de pila proporcionado es demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="a9163-740">**NX_SIZE_ERROR** (0x09) The supplied stack size is too small.</span></span>
- <span data-ttu-id="a9163-741">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-741">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-742">**NX_IP_ADDRESS_ERROR**: (0X21) la dirección IP proporcionada no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-742">**NX_IP_ADDRESS_ERROR** (0x21) The supplied IP address is invalid.</span></span>
- <span data-ttu-id="a9163-743">**NX_OPTION_ERROR**: (0X21) la prioridad del subproceso de IP proporcionada no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-743">**NX_OPTION_ERROR** (0x21) The supplied IP thread priority is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-744">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-744">Allowed From</span></span>

<span data-ttu-id="a9163-745">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-745">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-746">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-746">Preemption Possible</span></span>

<span data-ttu-id="a9163-747">No</span><span class="sxs-lookup"><span data-stu-id="a9163-747">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-748">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-748">Example</span></span>

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-749">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-749">See Also</span></span>

- <span data-ttu-id="a9163-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-751">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-751">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="a9163-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="a9163-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="a9163-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="a9163-755">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-755">nx_system_initialize</span></span>

## <a name="nx_ip_delete"></a><span data-ttu-id="a9163-756">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-756">nx_ip_delete</span></span>

<span data-ttu-id="a9163-757">Elimina la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-757">Delete previously created IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="a9163-758">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-758">Prototype</span></span>

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-759">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-759">Description</span></span>

<span data-ttu-id="a9163-760">Este servicio elimina una instancia de IP creada anteriormente y libera todos los recursos del sistema que pertenecen a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-760">This service deletes a previously created IP instance and releases all of the system resources owned by the IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-761">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-761">Parameters</span></span>
- <span data-ttu-id="a9163-762">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-762">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-763">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-763">Return Values</span></span>

- <span data-ttu-id="a9163-764">**NX_SUCCESS**: (0x00) la dirección IP se eliminó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-764">**NX_SUCCESS** (0x00) Successful IP deletion.</span></span>
- <span data-ttu-id="a9163-765">**NX_SOCKETS_BOUND**: (0X28) esta instancia de IP todavía tiene sockets UDP o TCP enlazados.</span><span class="sxs-lookup"><span data-stu-id="a9163-765">**NX_SOCKETS_BOUND** (0x28) This IP instance still has UDP or TCP sockets bound to it.</span></span> <span data-ttu-id="a9163-766">Todos los sockets se deben desenlazar y eliminar antes de eliminar la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-766">All sockets must be unbound and deleted prior to deleting the IP instance.</span></span>
- <span data-ttu-id="a9163-767">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-767">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-768">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-768">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-769">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-769">Allowed From</span></span>

<span data-ttu-id="a9163-770">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-770">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-771">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-771">Preemption Possible</span></span>

<span data-ttu-id="a9163-772">Sí</span><span class="sxs-lookup"><span data-stu-id="a9163-772">Yes</span></span>

### <a name="example"></a><span data-ttu-id="a9163-773">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-773">Example</span></span>

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-774">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-774">See Also</span></span>

- <span data-ttu-id="a9163-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-776">nx_ip_create, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-776">nx_ip_create, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="a9163-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="a9163-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="a9163-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="a9163-780">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-780">nx_system_initialize</span></span>

## <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="a9163-781">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="a9163-781">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="a9163-782">Emite el comando para el controlador de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-782">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-783">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-783">Prototype</span></span>

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-784">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-784">Description</span></span>

<span data-ttu-id="a9163-785">Este servicio proporciona una interfaz directa al controlador de la interfaz de red principal de la aplicación especificado durante la llamada ***nx_ip_create***.</span><span class="sxs-lookup"><span data-stu-id="a9163-785">This service provides a direct interface to the application's primary network interface driver specified during the ***nx_ip_create*** call.</span></span>

<span data-ttu-id="a9163-786">Los comandos específicos de la aplicación se pueden usar siempre que su valor numérico sea mayor o igual que NX_LINK_USER_COMMAND.</span><span class="sxs-lookup"><span data-stu-id="a9163-786">Application-specific commands can be used providing their numeric value is greater than or equal to NX_LINK_USER_COMMAND.</span></span>

<span data-ttu-id="a9163-787">*Para emitir el comando para el dispositivo secundario, use el servicio **nx_ip_driver_interface_direct_command**.*</span><span class="sxs-lookup"><span data-stu-id="a9163-787">*To issue command for the secondary device, use the **nx_ip_driver_interface_direct_command** service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-788">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-788">Parameters</span></span>

- <span data-ttu-id="a9163-789">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-789">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-790">**command**: código de comando numérico.</span><span class="sxs-lookup"><span data-stu-id="a9163-790">**command** Numeric command code.</span></span> <span data-ttu-id="a9163-791">Los comandos estándar se definen de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a9163-791">Standard commands are defined as follows:</span></span>

- <span data-ttu-id="a9163-792">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="a9163-792">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="a9163-793">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="a9163-793">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="a9163-794">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="a9163-794">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="a9163-795">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="a9163-795">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="a9163-796">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="a9163-796">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="a9163-797">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="a9163-797">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="a9163-798">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="a9163-798">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="a9163-799">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="a9163-799">NX_LINK_USER_COMMAND (50)</span></span>

- <span data-ttu-id="a9163-800">**return_value_ptr**: puntero a la variable devuelta en el autor de llamada.</span><span class="sxs-lookup"><span data-stu-id="a9163-800">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-801">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-801">Return Values</span></span>

- <span data-ttu-id="a9163-802">**NX_SUCCESS**: (0x00) comando directo de controlador de red correcto.</span><span class="sxs-lookup"><span data-stu-id="a9163-802">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="a9163-803">**NX_UNHANDLED_COMMAND**: (0X44) comando de controlador de red no controlado o no implementado.</span><span class="sxs-lookup"><span data-stu-id="a9163-803">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="a9163-804">**NX_PTR_ERROR**: (0X07) la IP o el puntero de valor devuelto no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-804">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="a9163-805">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-805">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-806">**NX_INVALID_INTERFACE**: (0x4C) el índice de la interfaz no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-806">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-807">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-807">Allowed From</span></span>

<span data-ttu-id="a9163-808">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-808">Threads</span></span>

- <span data-ttu-id="a9163-809">**Adelantamiento posible**</span><span class="sxs-lookup"><span data-stu-id="a9163-809">**Preemption Possible**</span></span>

<span data-ttu-id="a9163-810">No</span><span class="sxs-lookup"><span data-stu-id="a9163-810">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-811">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-811">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-812">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-812">See Also</span></span>

- <span data-ttu-id="a9163-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="a9163-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="a9163-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="a9163-817">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-817">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_driver_interface_direct_command"></a><span data-ttu-id="a9163-818">nx_ip_driver_interface_direct_command</span><span class="sxs-lookup"><span data-stu-id="a9163-818">nx_ip_driver_interface_direct_command</span></span>

<span data-ttu-id="a9163-819">Emite el comando para el controlador de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-819">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-820">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-820">Prototype</span></span>

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-821">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-821">Description</span></span>

<span data-ttu-id="a9163-822">Este servicio proporciona un comando directo al controlador de dispositivo de red de la aplicación en la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-822">This service provides a direct command to the application's network device driver in the IP instance.</span></span> <span data-ttu-id="a9163-823">Los comandos específicos de la aplicación se pueden usar siempre que su valor numérico sea mayor o igual que *NX_LINK_USER_COMMAND*.</span><span class="sxs-lookup"><span data-stu-id="a9163-823">Application-specific commands can be used providing their numeric value is greater than or equal to *NX_LINK_USER_COMMAND*.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-824">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-824">Parameters</span></span>

- <span data-ttu-id="a9163-825">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-825">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-826">**command**: código de comando numérico.</span><span class="sxs-lookup"><span data-stu-id="a9163-826">**command** Numeric command code.</span></span> <span data-ttu-id="a9163-827">Los comandos estándar se definen de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a9163-827">Standard commands are defined as follows:</span></span>
- <span data-ttu-id="a9163-828">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="a9163-828">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="a9163-829">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="a9163-829">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="a9163-830">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="a9163-830">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="a9163-831">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="a9163-831">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="a9163-832">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="a9163-832">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="a9163-833">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="a9163-833">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="a9163-834">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="a9163-834">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="a9163-835">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="a9163-835">NX_LINK_USER_COMMAND (50)</span></span>
- <span data-ttu-id="a9163-836">**interface_index**: índice de la interfaz de red a la que debe enviarse el comando.</span><span class="sxs-lookup"><span data-stu-id="a9163-836">**interface_index** Index of the network interface the command should be sent to.</span></span>
- <span data-ttu-id="a9163-837">**return_value_ptr**: puntero a la variable devuelta en el autor de llamada.</span><span class="sxs-lookup"><span data-stu-id="a9163-837">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-838">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-838">Return Values</span></span>
- <span data-ttu-id="a9163-839">**NX_SUCCESS**: (0x00) comando directo de controlador de red correcto.</span><span class="sxs-lookup"><span data-stu-id="a9163-839">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="a9163-840">**NX_UNHANDLED_COMMAND**: (0X44) comando de controlador de red no controlado o no implementado.</span><span class="sxs-lookup"><span data-stu-id="a9163-840">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="a9163-841">**NX_INVALID_INTERFACE**: (0x4C) el índice de interfaz no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-841">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index</span></span>
- <span data-ttu-id="a9163-842">**NX_PTR_ERROR**: (0X07) la IP o el puntero de valor devuelto no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-842">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="a9163-843">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-843">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-844">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-844">Allowed From</span></span>

<span data-ttu-id="a9163-845">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-845">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-846">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-846">Preemption Possible</span></span>

<span data-ttu-id="a9163-847">No</span><span class="sxs-lookup"><span data-stu-id="a9163-847">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-848">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-848">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;
    status = nx_ip_driver_interface_direct_command(&ip_0,
    NX_LINK_GET_STATUS,
    interface_index,
    &link_status);
/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-849">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-849">See Also</span></span>

- <span data-ttu-id="a9163-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="a9163-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="a9163-854">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-854">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="a9163-855">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="a9163-855">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="a9163-856">Deshabilita el reenvío de paquetes IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-856">Disable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-857">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-857">Prototype</span></span>

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-858">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-858">Description</span></span>

<span data-ttu-id="a9163-859">Este servicio deshabilita el reenvío de paquetes IP dentro del componente IP de NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-859">This service disables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="a9163-860">Al crear la tarea IP, este servicio se deshabilita automáticamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-860">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-861">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-861">Parameters</span></span>

- <span data-ttu-id="a9163-862">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-862">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-863">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-863">Return Values</span></span>

- <span data-ttu-id="a9163-864">**NX_SUCCESS**: (0x00) el reenvío de IP se deshabilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-864">**NX_SUCCESS** (0x00) Successful IP forwarding disable.</span></span>
- <span data-ttu-id="a9163-865">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-865">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-866">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-866">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-867">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-867">Allowed From</span></span>

<span data-ttu-id="a9163-868">Inicialización, subprocesos, temporizadores</span><span class="sxs-lookup"><span data-stu-id="a9163-868">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-869">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-869">Preemption Possible</span></span>

<span data-ttu-id="a9163-870">No</span><span class="sxs-lookup"><span data-stu-id="a9163-870">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-871">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-871">Example</span></span>

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-872">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-872">See Also</span></span>

- <span data-ttu-id="a9163-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="a9163-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="a9163-877">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-877">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="a9163-878">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-878">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="a9163-879">Habilita el reenvío de paquetes IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-879">Enable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-880">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-880">Prototype</span></span>

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-881">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-881">Description</span></span>

<span data-ttu-id="a9163-882">Este servicio habilita el reenvío de paquetes IP dentro del componente IP de NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-882">This service enables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="a9163-883">Al crear la tarea IP, este servicio se deshabilita automáticamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-883">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-884">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-884">Parameters</span></span>

- <span data-ttu-id="a9163-885">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-885">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-886">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-886">Return Values</span></span>
- <span data-ttu-id="a9163-887">**NX_SUCCESS**: (0x00) el reenvío de IP se habilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-887">**NX_SUCCESS** (0x00) Successful IP forwarding enable.</span></span>
- <span data-ttu-id="a9163-888">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-888">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-889">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-889">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-890">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-890">Allowed From</span></span>

<span data-ttu-id="a9163-891">Inicialización, subprocesos, temporizadores</span><span class="sxs-lookup"><span data-stu-id="a9163-891">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-892">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-892">Preemption Possible</span></span>

<span data-ttu-id="a9163-893">No</span><span class="sxs-lookup"><span data-stu-id="a9163-893">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-894">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-894">Example</span></span>

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-895">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-895">See Also</span></span>

- <span data-ttu-id="a9163-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="a9163-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="a9163-900">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-900">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_disable"></a><span data-ttu-id="a9163-901">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="a9163-901">nx_ip_fragment_disable</span></span>

<span data-ttu-id="a9163-902">Deshabilita la fragmentación de paquetes IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-902">Disable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-903">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-903">Prototype</span></span>

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-904">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-904">Description</span></span>

<span data-ttu-id="a9163-905">Este servicio deshabilita la funcionalidad de fragmentación y reensamblado de paquetes IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-905">This service disables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="a9163-906">En el caso de los paquetes que esperan el reensamblado, este servicio los libera.</span><span class="sxs-lookup"><span data-stu-id="a9163-906">For packets waiting to be reassembled, this service releases these packets.</span></span> <span data-ttu-id="a9163-907">Al crear la tarea de IP, este servicio se deshabilita automáticamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-907">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-908">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-908">Parameters</span></span>

- <span data-ttu-id="a9163-909">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-909">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-910">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-910">Return Values</span></span>
- <span data-ttu-id="a9163-911">**NX_SUCCESS**: (0X00) el fragmento de IP se deshabilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-911">**NX_SUCCESS** (0x00) Successful IP fragment disable.</span></span>
- <span data-ttu-id="a9163-912">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-912">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-913">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-913">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-914">**NX_NOT_ENABLED**: (0x14) la fragmentación de IP no está habilitada en la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-914">**NX_NOT_ENABLED** (0x14) IP Fragmentation is not enabled on the IP instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-915">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-915">Allowed From</span></span>

<span data-ttu-id="a9163-916">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-916">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-917">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-917">Preemption Possible</span></span>

<span data-ttu-id="a9163-918">No</span><span class="sxs-lookup"><span data-stu-id="a9163-918">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-919">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-919">Example</span></span>

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-920">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-920">See Also</span></span>

- <span data-ttu-id="a9163-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="a9163-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="a9163-925">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-925">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_enable"></a><span data-ttu-id="a9163-926">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-926">nx_ip_fragment_enable</span></span>

<span data-ttu-id="a9163-927">Habilita la fragmentación de paquetes IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-927">Enable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-928">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-928">Prototype</span></span>

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-929">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-929">Description</span></span>

<span data-ttu-id="a9163-930">Este servicio habilita la funcionalidad de fragmentación y reensamblado de paquetes IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-930">This service enables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="a9163-931">Al crear la tarea de IP, este servicio se deshabilita automáticamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-931">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-932">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-932">Parameters</span></span>

- <span data-ttu-id="a9163-933">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-933">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-934">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-934">Return Values</span></span>

- <span data-ttu-id="a9163-935">**NX_SUCCESS**: (0X00) el fragmento de IP se habilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-935">**NX_SUCCESS** (0x00) Successful IP fragment enable.</span></span>
- <span data-ttu-id="a9163-936">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-936">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-937">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-937">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-938">**NX_NOT_ENABLED**: (0x14) las características de fragmentación de IP no se compilan en NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-938">**NX_NOT_ENABLED** (0x14) IP Fragmentation features is not compiled into NetX.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-939">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-939">Allowed From</span></span>

<span data-ttu-id="a9163-940">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-940">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-941">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-941">Preemption Possible</span></span>

<span data-ttu-id="a9163-942">No</span><span class="sxs-lookup"><span data-stu-id="a9163-942">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-943">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-943">Example</span></span>

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-944">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-944">See Also</span></span>

- <span data-ttu-id="a9163-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="a9163-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,</span></span>
- <span data-ttu-id="a9163-949">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-949">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="a9163-950">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="a9163-950">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="a9163-951">Establece la dirección IP de la puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="a9163-951">Set Gateway IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-952">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-952">Prototype</span></span>

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a><span data-ttu-id="a9163-953">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-953">Description</span></span>

<span data-ttu-id="a9163-954">Este servicio establece la dirección IP de la puerta de enlace de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-954">This service sets the IP gateway IP address.</span></span> <span data-ttu-id="a9163-955">Todo el tráfico fuera de red se enruta a esta puerta de enlace para su transmisión.</span><span class="sxs-lookup"><span data-stu-id="a9163-955">All out-of-network traffic are routed to this gateway for transmission.</span></span> <span data-ttu-id="a9163-956">La puerta de enlace debe ser accesible directamente a través de una de las interfaces de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-956">The gateway must be directly accessible through one of the network interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-957">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-957">Parameters</span></span>

- <span data-ttu-id="a9163-958">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-958">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-959">**ip_address**: dirección IP de la puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="a9163-959">**ip_address** IP address of the gateway.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-960">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-960">Return Values</span></span>

- <span data-ttu-id="a9163-961">**NX_SUCCESS**: (0x00) la dirección IP de la puerta de enlace se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-961">**NX_SUCCESS** (0x00) Successful Gateway IP address set.</span></span>
- <span data-ttu-id="a9163-962">**NX_PTR_ERROR**: (0x07) el puntero de instancia de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-962">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="a9163-963">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-963">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="a9163-964">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-964">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-965">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-965">Allowed From</span></span>

<span data-ttu-id="a9163-966">Inicialización, subproceso</span><span class="sxs-lookup"><span data-stu-id="a9163-966">Initialization, thread</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-967">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-967">Preemption Possible</span></span>

<span data-ttu-id="a9163-968">No</span><span class="sxs-lookup"><span data-stu-id="a9163-968">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-969">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-969">Example</span></span>

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a><span data-ttu-id="a9163-970">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-970">See Also</span></span>

- <span data-ttu-id="a9163-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_info_get"></a><span data-ttu-id="a9163-972">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-972">nx_ip_info_get</span></span>

<span data-ttu-id="a9163-973">Recupera información acerca de las actividades de la IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-973">Retrieve information about IP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-974">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-974">Prototype</span></span>

```C
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```

### <a name="description"></a><span data-ttu-id="a9163-975">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-975">Description</span></span>

<span data-ttu-id="a9163-976">Este servicio recupera información sobre las actividades de la IP de la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-976">This service retrieves information about IP activities for the specified IP instance.</span></span>

<span data-ttu-id="a9163-977">*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-977">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-978">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-978">Parameters</span></span>

- <span data-ttu-id="a9163-979">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-979">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-980">**ip_total_packets_sent**: puntero al destino para el número total de paquetes IP enviados.</span><span class="sxs-lookup"><span data-stu-id="a9163-980">**ip_total_packets_sent** Pointer to destination for the total number of IP packets sent.</span></span>
- <span data-ttu-id="a9163-981">**ip_total_bytes_sent**: puntero al destino para el número total de bytes enviados.</span><span class="sxs-lookup"><span data-stu-id="a9163-981">**ip_total_bytes_sent** Pointer to destination for the total number of bytes sent.</span></span>
- <span data-ttu-id="a9163-982">**ip_total_packets_received**: puntero al destino del número total de paquetes de recepción IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-982">**ip_total_packets_received** Pointer to destination of the total number of IP receive packets.</span></span>
- <span data-ttu-id="a9163-983">**ip_total_bytes_received**: puntero al destino del número total de bytes de IP recibidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-983">**ip_total_bytes_received** Pointer to destination of the total number of IP bytes received.</span></span>
- <span data-ttu-id="a9163-984">**ip_invalid_packets**: puntero al destino del número total de paquetes IP no válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-984">**ip_invalid_packets** Pointer to destination of the total number of invalid IP packets.</span></span>
- <span data-ttu-id="a9163-985">**ip_receive_packets_dropped**: puntero al destino del número total de paquetes recibidos anulados.</span><span class="sxs-lookup"><span data-stu-id="a9163-985">**ip_receive_packets_dropped** Pointer to destination of the total number of receive packets dropped.</span></span>
- <span data-ttu-id="a9163-986">**ip_receive_checksum_errors**: puntero al destino del número total de errores de suma de comprobación en paquetes recibidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-986">**ip_receive_checksum_errors** Pointer to destination of the total number of checksum errors in receive packets.</span></span>
- <span data-ttu-id="a9163-987">**ip_send_packets_dropped**: puntero al destino del número total de paquetes enviados anulados.</span><span class="sxs-lookup"><span data-stu-id="a9163-987">**ip_send_packets_dropped** Pointer to destination of the total number of send packets dropped.</span></span>
- <span data-ttu-id="a9163-988">**ip_total_fragments_sent**: puntero al destino del número total de fragmentos enviados.</span><span class="sxs-lookup"><span data-stu-id="a9163-988">**ip_total_fragments_sent** Pointer to destination of the total number of fragments sent.</span></span>
- <span data-ttu-id="a9163-989">**ip_total_fragments_received**: puntero al destino del número total de fragmentos recibidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-989">**ip_total_fragments_received** Pointer to destination of the total number of fragments received.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-990">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-990">Return Values</span></span>

- <span data-ttu-id="a9163-991">**NX_SUCCESS**: (0x00) la información de IP se recuperó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-991">**NX_SUCCESS** (0x00) Successful IP information retrieval.</span></span>
- <span data-ttu-id="a9163-992">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-992">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-993">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-993">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-994">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-994">Allowed From</span></span>

<span data-ttu-id="a9163-995">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-995">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-996">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-996">Preemption Possible</span></span>

<span data-ttu-id="a9163-997">No</span><span class="sxs-lookup"><span data-stu-id="a9163-997">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-998">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-998">Example</span></span>

```C
/* Retrieve IP information from previously created IP
Instance 0. */
status = nx_ip_info_get(&ip_0,
    &ip_total_packets_sent,
    &ip_total_bytes_sent,
    &ip_total_packets_received,
    &ip_total_bytes_received,
    &ip_invalid_packets,
    &ip_receive_packets_dropped,
    &ip_receive_checksum_errors,
    &ip_send_packets_dropped,
    &ip_total_fragments_sent,
    &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-999">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-999">See Also</span></span>

- <span data-ttu-id="a9163-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="a9163-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="a9163-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_interface_address_get"></a><span data-ttu-id="a9163-1005">nx_ip_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="a9163-1005">nx_ip_interface_address_get</span></span>

<span data-ttu-id="a9163-1006">Recupera la dirección IP de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="a9163-1006">Retrieve interface IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1007">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1007">Prototype</span></span>

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="a9163-1008">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1008">Description</span></span>

<span data-ttu-id="a9163-1009">Este servicio recupera la dirección IP de una interfaz de red especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1009">This service retrieves the IP address of a specified network interface.</span></span>

<span data-ttu-id="a9163-1010">*El dispositivo especificado, si no es el dispositivo primario, debe estar conectado previamente a la instancia de IP.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1010">*The specified device, if not the primary device, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1011">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1011">Parameters</span></span>

- <span data-ttu-id="a9163-1012">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1012">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1013">**interface_index**: índice de la interfaz; el mismo valor que el índice de la interfaz de red asociada a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1013">**interface_index** Interface index, the same value as the index to the network interface attached to the IP instance.</span></span>
- <span data-ttu-id="a9163-1014">**ip_address**: puntero al destino de la dirección IP de la interfaz del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1014">**ip_address** Pointer to destination for the device interface IP address.</span></span>
- <span data-ttu-id="a9163-1015">**network_mask**: puntero al destino de la máscara de red de la interfaz del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1015">**network_mask** Pointer to destination for the device interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1016">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1016">Return Values</span></span>

- <span data-ttu-id="a9163-1017">**NX_SUCCESS**: (0x00) la dirección IP se obtuvo correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1017">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="a9163-1018">**NX_INVALID_INTERFACE**: (0x4C) la interfaz de red especificada no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1018">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="a9163-1019">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1019">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-1020">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1020">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1021">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1021">Allowed From</span></span>

<span data-ttu-id="a9163-1022">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1022">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1023">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1023">Preemption Possible</span></span>

<span data-ttu-id="a9163-1024">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1024">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1025">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1025">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1026">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1026">See Also</span></span>

- <span data-ttu-id="a9163-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span><span class="sxs-lookup"><span data-stu-id="a9163-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="a9163-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="a9163-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="a9163-1029">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-1029">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_address_set"></a><span data-ttu-id="a9163-1030">nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="a9163-1030">nx_ip_interface_address_set</span></span>

<span data-ttu-id="a9163-1031">Establece la dirección IP de la interfaz y la máscara de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-1031">Set interface IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1032">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1032">Prototype</span></span>

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="a9163-1033">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1033">Description</span></span>

<span data-ttu-id="a9163-1034">Este servicio establece la dirección IP y la máscara de red para la interfaz IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1034">This service sets the IP address and network mask for the specified IP interface.</span></span>

<span data-ttu-id="a9163-1035">*La interfaz especificada se debe conectar previamente a la instancia de IP.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1035">*The specified interface must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1036">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1036">Parameters</span></span>

- <span data-ttu-id="a9163-1037">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1037">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1038">**interface_index**: índice de la interfaz asociada a la instancia de NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-1038">**interface_index** Index of the interface attached to the NetX instance.</span></span>
- <span data-ttu-id="a9163-1039">**ip_address**: nueva dirección IP de la interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-1039">**ip_address** New network interface IP address.</span></span>
- <span data-ttu-id="a9163-1040">**network_mask**: nueva máscara de red de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="a9163-1040">**network_mask** New interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1041">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1041">Return Values</span></span>

- <span data-ttu-id="a9163-1042">**NX_SUCCESS**: (0x00) la dirección IP se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1042">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="a9163-1043">**NX_INVALID_INTERFACE**: (0x4C) la interfaz de red especificada no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1043">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="a9163-1044">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1044">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-1045">**NX_PTR_ERROR**: (0x07) los punteros no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1045">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="a9163-1046">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1046">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1047">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1047">Allowed From</span></span>

<span data-ttu-id="a9163-1048">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1048">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1049">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1049">Preemption Possible</span></span>

<span data-ttu-id="a9163-1050">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1050">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1051">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1051">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1052">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1052">See Also</span></span>

- <span data-ttu-id="a9163-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span><span class="sxs-lookup"><span data-stu-id="a9163-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="a9163-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="a9163-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="a9163-1055">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-1055">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_attach"></a><span data-ttu-id="a9163-1056">nx_ip_interface_attach</span><span class="sxs-lookup"><span data-stu-id="a9163-1056">nx_ip_interface_attach</span></span>

<span data-ttu-id="a9163-1057">Conecta la interfaz de red a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1057">Attach network interface to IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1058">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1058">Prototype</span></span>

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="a9163-1059">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1059">Description</span></span>

<span data-ttu-id="a9163-1060">Este servicio agrega una interfaz de red física a la interfaz IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1060">This service adds a physical network interface to the IP interface.</span></span> <span data-ttu-id="a9163-1061">Tenga en cuenta que la instancia de IP se crea con la interfaz principal, por lo que cada interfaz adicional es secundaria para la interfaz principal.</span><span class="sxs-lookup"><span data-stu-id="a9163-1061">Note the IP instance is created with the primary interface so each additional interface is secondary to the primary interface.</span></span> <span data-ttu-id="a9163-1062">El número total de interfaces de red conectadas a la instancia de IP (incluida la interfaz principal) no puede superar el recuento de **NX_MAX_PHYSICAL_INTERFACES**.</span><span class="sxs-lookup"><span data-stu-id="a9163-1062">The total number of network interfaces attached to the IP instance (including the primary interface) cannot exceed **NX_MAX_PHYSICAL_INTERFACES**.</span></span>

<span data-ttu-id="a9163-1063">Si el subproceso de IP todavía no se ha ejecutado, las interfaces secundarias se inicializarán como parte del proceso de inicio del subproceso de IP que inicializa todas las interfaces físicas.</span><span class="sxs-lookup"><span data-stu-id="a9163-1063">If the IP thread has not been running yet, the secondary interfaces will be initialized as part of the IP thread startup process that initializes all physical interfaces.</span></span>

<span data-ttu-id="a9163-1064">Si el subproceso de IP aún no se está ejecutando, la interfaz secundaria se inicializa como parte del servicio ***nx_ip_interface_attach***.</span><span class="sxs-lookup"><span data-stu-id="a9163-1064">If the IP thread is not running yet, the secondary interface is initialized as part of the ***nx_ip_interface_attach*** service.</span></span>

<span data-ttu-id="a9163-1065">*ip_ptr debe apuntar a una estructura IP de NetX válida.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1065">*ip_ptr must point to a valid NetX IP structure.*</span></span>

- <span data-ttu-id="a9163-1066">***NX_MAX_PHYSICAL_INTERFACES** debe configurarse para el número de interfaces de red de la instancia de IP. El valor predeterminado es uno.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1066">***NX_MAX_PHYSICAL_INTERFACES** must be configured for the number of network interfaces for the IP instance. The default value is one.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1067">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1067">Parameters</span></span>

- <span data-ttu-id="a9163-1068">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1068">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1069">**interface_name**: puntero a la cadena de nombre de interfaz.</span><span class="sxs-lookup"><span data-stu-id="a9163-1069">**interface_name** Pointer to interface name string.</span></span>
- <span data-ttu-id="a9163-1070">**ip_address**: dirección IP del dispositivo en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-1070">**ip_address** Device IP address in host byte order.</span></span>
- <span data-ttu-id="a9163-1071">**network_mask**: máscara de red del dispositivo en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-1071">**network_mask** Device network mask in host byte order.</span></span>
- <span data-ttu-id="a9163-1072">**ip_link_driver**: controlador Ethernet para la interfaz.</span><span class="sxs-lookup"><span data-stu-id="a9163-1072">**ip_link_driver** Ethernet driver for the interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1073">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1073">Return Values</span></span>

- <span data-ttu-id="a9163-1074">**NX_SUCCESS**: (0x00) la entrada se agrega a la tabla de enrutamiento estática.</span><span class="sxs-lookup"><span data-stu-id="a9163-1074">**NX_SUCCESS** (0x00) Entry is added to static routing table.</span></span>
- <span data-ttu-id="a9163-1075">**NX_NO_MORE_ENTRIES**: (0x17) número máximo de interfaces.</span><span class="sxs-lookup"><span data-stu-id="a9163-1075">**NX_NO_MORE_ENTRIES** (0x17) Max number of interfaces.</span></span>
- <span data-ttu-id="a9163-1076">**NX_MAX_PHYSICAL_INTERFACES**: se superó el número máximo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1076">**NX_MAX_PHYSICAL_INTERFACES** is exceeded.</span></span>
- <span data-ttu-id="a9163-1077">**NX_DUPLICATED_ENTRY**: (0X52) la dirección IP suministrada ya se usa en esta instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1077">**NX_DUPLICATED_ENTRY** (0x52) The supplied IP address is already used on this IP instance.</span></span>
- <span data-ttu-id="a9163-1078">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1078">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-1079">**NX_PTR_ERROR**: (0x07) la entrada del puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1079">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="a9163-1080">**NX_IP_ADDRESS_ERROR**: (0x21) la entrada de la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1080">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1081">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1081">Allowed From</span></span>

<span data-ttu-id="a9163-1082">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1082">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1083">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1083">Preemption Possible</span></span>

<span data-ttu-id="a9163-1084">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1084">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1085">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1085">Example</span></span>

```C
/* Attach secondary device for device IP address 192.168.1.68 with
    the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
    IP_ADDRESS(192,168,1,68),
    0xFFFFFF00UL,
    nx_etherDriver);
/* If status is NX_SUCCESS the interface was successfully added to
    the IP instance interface table. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1086">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1086">See Also</span></span>

- <span data-ttu-id="a9163-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="a9163-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="a9163-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="a9163-1089">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-1089">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_info_get"></a><span data-ttu-id="a9163-1090">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-1090">nx_ip_interface_info_get</span></span>

<span data-ttu-id="a9163-1091">Recupera parámetros de la interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-1091">Retrieve network interface parameters</span></span>


### <a name="prototype"></a><span data-ttu-id="a9163-1092">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1092">Prototype</span></span>

```C
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```

### <a name="description"></a><span data-ttu-id="a9163-1093">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1093">Description</span></span>

<span data-ttu-id="a9163-1094">Este servicio recupera información de los parámetros de red de la interfaz de red especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1094">This service retrieves information on network parameters for the specified network interface.</span></span> <span data-ttu-id="a9163-1095">Todos los datos se recuperan en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-1095">All data are retrieved in host byte order.</span></span>

<span data-ttu-id="a9163-1096">*ip_ptr debe apuntar a una estructura IP de NetX válida. La interfaz especificada, si no es la principal, se debe conectar previamente a la instancia de IP.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1096">*ip_ptr must point to a valid NetX IP structure. The specified interface, if not the primary interface, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1097">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1097">Parameters</span></span>

- <span data-ttu-id="a9163-1098">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1098">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1099">**interface_index**: índice que especifica la interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-1099">**interface_index** Index specifying network interface.</span></span>
- <span data-ttu-id="a9163-1100">**interface_name**: puntero al búfer que contiene el nombre de la interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-1100">**interface_name** Pointer to the buffer that holds the name of the network interface.</span></span>
- <span data-ttu-id="a9163-1101">**ip_address**: puntero al destino de la dirección IP de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="a9163-1101">**ip_address** Pointer to the destination for the IP address of the interface.</span></span>
- <span data-ttu-id="a9163-1102">**network_mask**: puntero al destino de la máscara de red.</span><span class="sxs-lookup"><span data-stu-id="a9163-1102">**network_mask** Pointer to destination for network mask.</span></span>
- <span data-ttu-id="a9163-1103">**mtu_size**: puntero al destino de la unidad de transferencia máxima de esta interfaz.</span><span class="sxs-lookup"><span data-stu-id="a9163-1103">**mtu_size** Pointer to destination for maximum transfer unit for this interface.</span></span>
- <span data-ttu-id="a9163-1104">**physical_address_msw**: puntero al destino para los 16 bits superiores de la dirección MAC del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1104">**physical_address_msw** Pointer to destination for top 16 bits of the device MAC address.</span></span>
- <span data-ttu-id="a9163-1105">**physical_address_lsw**: puntero al destino para los 32 bits inferiores de la dirección MAC del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1105">**physical_address_lsw** Pointer to destination for lower 32 bits of the device MAC address.</span></span>


### <a name="return-values"></a><span data-ttu-id="a9163-1106">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1106">Return Values</span></span>
- <span data-ttu-id="a9163-1107">**NX_SUCCESS**: (0x00) se obtuvo la información de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="a9163-1107">**NX_SUCCESS** (0x00) Interface information has been obtained.</span></span>
- <span data-ttu-id="a9163-1108">**NX_PTR_ERROR**: (0x07) la entrada del puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1108">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="a9163-1109">**NX_INVALID_INTERFACE**: (0x4C) el puntero de la IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1109">**NX_INVALID_INTERFACE** (0x4C) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-1110">**NX_CALLER_ERROR**: (0x11) no se llama al servicio desde el contexto de la inicialización del sistema o del subproceso.</span><span class="sxs-lookup"><span data-stu-id="a9163-1110">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1111">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1111">Allowed From</span></span>

<span data-ttu-id="a9163-1112">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1112">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1113">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1113">Preemption Possible</span></span>

<span data-ttu-id="a9163-1114">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1114">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1115">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1115">Example</span></span>

```C
/* Retrieve interface parameters for the specified interface (index
    1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1

status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
    &name_ptr, &ip_address,
    &network_mask,
    &mtu_size,
    &physical_address_msw,
    &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
    successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1116">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1116">See Also</span></span>

- <span data-ttu-id="a9163-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="a9163-1118">nx_ip_interface_attach, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="a9163-1118">nx_ip_interface_attach, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="a9163-1119">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-1119">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_status_check"></a><span data-ttu-id="a9163-1120">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="a9163-1120">nx_ip_interface_status_check</span></span>

<span data-ttu-id="a9163-1121">Comprobar el estado de una instancia de IP</span><span class="sxs-lookup"><span data-stu-id="a9163-1121">Check status of an IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="a9163-1122">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1122">Prototype</span></span>

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-1123">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1123">Description</span></span>

<span data-ttu-id="a9163-1124">Este servicio comprueba y, de manera opcional, espera el estado especificado de la interfaz de red de una instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1124">This service checks and optionally waits for the specified status of the network interface of a previously created IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1125">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1125">Parameters</span></span>

- <span data-ttu-id="a9163-1126">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1126">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1127">**interface_index**: número de índice de interfaz</span><span class="sxs-lookup"><span data-stu-id="a9163-1127">**interface_index** Interface index number</span></span>
- <span data-ttu-id="a9163-1128">**needed_status** Estado de IP solicitado, definido en el formato de mapa de bits de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a9163-1128">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
    - <span data-ttu-id="a9163-1129">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="a9163-1129">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
    - <span data-ttu-id="a9163-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="a9163-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
    - <span data-ttu-id="a9163-1131">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="a9163-1131">NX_IP_LINK_ENABLED (0x0004)</span></span>
    - <span data-ttu-id="a9163-1132">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="a9163-1132">NX_IP_ARP_ENABLED (0x0008)</span></span>
    - <span data-ttu-id="a9163-1133">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="a9163-1133">NX_IP_UDP_ENABLED (0x0010)</span></span>
    - <span data-ttu-id="a9163-1134">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="a9163-1134">NX_IP_TCP_ENABLED (0x0020)</span></span>
    - <span data-ttu-id="a9163-1135">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="a9163-1135">NX_IP_IGMP_ENABLED (0x0040)</span></span>
    - <span data-ttu-id="a9163-1136">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="a9163-1136">NX_IP_RARP_COMPLETE (0x0080)</span></span>
    - <span data-ttu-id="a9163-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="a9163-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="a9163-1138">**actual_status** Puntero al destino del conjunto de bits real.</span><span class="sxs-lookup"><span data-stu-id="a9163-1138">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="a9163-1139">**wait_option** Define cómo se comporta el servicio si los bits de estado solicitados no están disponibles.</span><span class="sxs-lookup"><span data-stu-id="a9163-1139">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="a9163-1140">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-1140">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="a9163-1141">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1141">NX_NO_WAIT (0x00000000)</span></span>
    - <span data-ttu-id="a9163-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="a9163-1143">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-1143">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1144">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1144">Return Values</span></span>

- <span data-ttu-id="a9163-1145">**NX_SUCCESS** (0X00) Comprobación de estado de IP correcta.</span><span class="sxs-lookup"><span data-stu-id="a9163-1145">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="a9163-1146">**NX_NOT_SUCCESSFUL** (0X43) La solicitud de estado no se ha satisfecho dentro del tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1146">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="a9163-1147">**NX_PTR_ERROR** (0x07) El puntero IP no es o ha dejado de ser válido o el puntero de estado real no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1147">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="a9163-1148">**NX_OPTION_ERROR** (0x0a) Opción de estado necesario no válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1148">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="a9163-1149">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1149">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-1150">**NX_INVALID_INTERFACE**: (0x4C) el valor de interface_index está fuera del intervalo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1150">**NX_INVALID_INTERFACE** (0x4C) Interface_index is out of range.</span></span> <span data-ttu-id="a9163-1151">o la interfaz no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1151">or the interface is not valid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1152">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1152">Allowed From</span></span>

<span data-ttu-id="a9163-1153">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1153">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1154">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1154">Preemption Possible</span></span>

<span data-ttu-id="a9163-1155">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1155">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1156">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1156">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1157">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1157">See Also</span></span>

- <span data-ttu-id="a9163-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="a9163-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="a9163-1160">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-1160">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_link_status_change_notify_set"></a><span data-ttu-id="a9163-1161">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-1161">nx_ip_link_status_change_notify_set</span></span>

<span data-ttu-id="a9163-1162">Establece la función de devolución de llamada de notificación de cambio de estado de vínculo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1162">Set the link status change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1163">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1163">Prototype</span></span>

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a><span data-ttu-id="a9163-1164">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1164">Description</span></span>

<span data-ttu-id="a9163-1165">Este servicio configura la función de devolución de llamada de notificación de cambio del estado del vínculo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1165">This service configures the link status change notify callback function.</span></span> <span data-ttu-id="a9163-1166">La rutina de *link_status_change_notify* proporcionada por el usuario se invoca cuando se cambia el estado de la interfaz principal o secundaria (por ejemplo, se cambia la dirección IP). Si *link_status_change_notify* es NULL, se deshabilita la característica de devolución de llamada de notificación de cambio del estado del vínculo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1166">The user-supplied *link_status_change_notify* routine is invoked when either the primary or secondary interface status is changed (such as IP address is changed.) If *link_status_change_notify* is NULL, the link status change notify callback feature is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1167">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1167">Parameters</span></span>

- <span data-ttu-id="a9163-1168">**ip_ptr**: puntero de bloque de control IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1168">**ip_ptr** IP control block pointer</span></span>
- <span data-ttu-id="a9163-1169">**link_status_change_notify**: función de devolución de llamada proporcionada por el usuario a la que se llamará cuando se cambie la interfaz física.</span><span class="sxs-lookup"><span data-stu-id="a9163-1169">**link_status_change_notify** User-supplied callback function to be called upon a change to the physical interface.</span></span>


### <a name="return-values"></a><span data-ttu-id="a9163-1170">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1170">Return Values</span></span>

- <span data-ttu-id="a9163-1171">**NX_SUCCESS**: (0x00) se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1171">**NX_SUCCESS** (0x00) Successful set</span></span>
- <span data-ttu-id="a9163-1172">**NX_PTR_ERROR**: (0x07) el puntero de bloque de control de IP o el nuevo puntero de dirección física no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1172">**NX_PTR_ERROR** (0x07) Invalid IP control block pointer or new physical address pointer</span></span>
- <span data-ttu-id="a9163-1173">**NX_CALLER_ERROR**: (0x11) no se llama al servicio desde el contexto de la inicialización del sistema o del subproceso.</span><span class="sxs-lookup"><span data-stu-id="a9163-1173">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="a9163-1174">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1174">Allowed From</span></span>

<span data-ttu-id="a9163-1175">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1175">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1176">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1176">Preemption Possible</span></span>

<span data-ttu-id="a9163-1177">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1177">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1178">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1178">Example</span></span>

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1179">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1179">See Also</span></span>

- <span data-ttu-id="a9163-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="a9163-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="a9163-1182">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="a9163-1182">nx_ip_interface_status_check</span></span>

## <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="a9163-1183">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="a9163-1183">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="a9163-1184">Deshabilita el envío o recepción de paquetes sin formato.</span><span class="sxs-lookup"><span data-stu-id="a9163-1184">Disable raw packet sending/receiving</span></span>


### <a name="prototype"></a><span data-ttu-id="a9163-1185">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1185">Prototype</span></span>

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1186">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1186">Description</span></span>

<span data-ttu-id="a9163-1187">Este servicio deshabilita la transmisión y recepción de paquetes IP sin formato para esta instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1187">This service disables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="a9163-1188">Si el servicio de paquetes sin formato se habilitó previamente y hay paquetes sin formato en la cola de recepción, este servicio liberará cualquier paquete sin formato recibido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1188">If the raw packet service was previously enabled, and there are raw packets in the receive queue, this service will release any received raw packets.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1189">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1189">Parameters</span></span>

- <span data-ttu-id="a9163-1190">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1190">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1191">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1191">Return Values</span></span>

- <span data-ttu-id="a9163-1192">**NX_SUCCESS**: (0x00) los paquetes de IP sin formato se deshabilitaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1192">**NX_SUCCESS** (0x00) Successful IP raw packet disable.</span></span>
- <span data-ttu-id="a9163-1193">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1193">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-1194">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1194">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1195">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1195">Allowed From</span></span>

<span data-ttu-id="a9163-1196">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1196">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1197">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1197">Preemption Possible</span></span>

<span data-ttu-id="a9163-1198">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1198">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1199">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1199">Example</span></span>

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1200">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1200">See Also</span></span>

- <span data-ttu-id="a9163-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="a9163-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="a9163-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="a9163-1203">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-1203">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="a9163-1204">Habilita el procesamiento de paquetes sin formato.</span><span class="sxs-lookup"><span data-stu-id="a9163-1204">Enable raw packet processing</span></span>


### <a name="prototype"></a><span data-ttu-id="a9163-1205">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1205">Prototype</span></span>

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1206">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1206">Description</span></span>

<span data-ttu-id="a9163-1207">Este servicio habilita la transmisión y recepción de paquetes IP sin formato para esta instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1207">This service enables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="a9163-1208">Los paquetes TCP, UDP, ICMP e IGMP entrantes se siguen procesando en NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-1208">Incoming TCP, UDP, ICMP, and IGMP packets are still processed by NetX.</span></span> <span data-ttu-id="a9163-1209">Los paquetes con tipos de protocolo de capa superior desconocidos se procesan mediante la rutina de recepción de paquetes sin formato.</span><span class="sxs-lookup"><span data-stu-id="a9163-1209">Packets with unknown upper layer protocol types are processed by raw packet reception routine.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1210">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1210">Parameters</span></span>

- <span data-ttu-id="a9163-1211">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1211">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1212">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1212">Return Values</span></span>

- <span data-ttu-id="a9163-1213">**NX_SUCCESS**: (0x00) los paquetes de IP sin formato se habilitaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1213">**NX_SUCCESS** (0x00) Successful IP raw packet enable.</span></span>
- <span data-ttu-id="a9163-1214">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1214">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-1215">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1215">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1216">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1216">Allowed From</span></span>

<span data-ttu-id="a9163-1217">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1217">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1218">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1218">Preemption Possible</span></span>

<span data-ttu-id="a9163-1219">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1219">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1220">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1220">Example</span></span>

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1221">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1221">See Also</span></span>

- <span data-ttu-id="a9163-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="a9163-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="a9163-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_interface_send"></a><span data-ttu-id="a9163-1224">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="a9163-1224">nx_ip_raw_packet_interface_send</span></span>

<span data-ttu-id="a9163-1225">Envía un paquete de Raw IP a través de la interfaz de red especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1225">Send raw IP packet through specified network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1226">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1226">Prototype</span></span>

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="a9163-1227">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1227">Description</span></span>

<span data-ttu-id="a9163-1228">Este servicio envía un paquete de Raw IP a la dirección IP de destino mediante la dirección IP local especificada como dirección de origen y a través de la interfaz de red asociada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1228">This service sends a raw IP packet to the destination IP address using the specified local IP address as the source address, and through the associated network interface.</span></span> <span data-ttu-id="a9163-1229">Tenga en cuenta que esta rutina se devuelve inmediatamente y, por lo tanto, no se conoce si se ha enviado realmente el paquete IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1229">Note that this routine returns immediately, and it is, therefore, not known if the IP packet has actually been sent.</span></span> <span data-ttu-id="a9163-1230">El controlador de red será responsable de liberar el paquete cuando se complete la transmisión.</span><span class="sxs-lookup"><span data-stu-id="a9163-1230">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span> <span data-ttu-id="a9163-1231">Este servicio difiere de otros, ya que no hay ninguna manera de saber si el paquete se envió realmente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1231">This service differs from other services in that there is no way of knowing if the packet was actually sent.</span></span> <span data-ttu-id="a9163-1232">Podría perderse en Internet.</span><span class="sxs-lookup"><span data-stu-id="a9163-1232">It could get lost on the Internet.</span></span>

<span data-ttu-id="a9163-1233">*Tenga en cuenta que el procesamiento Raw IP debe estar habilitado.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1233">*Note that raw IP processing must be enabled.*</span></span>

<span data-ttu-id="a9163-1234">*Este servicio es similar a **nx_ip_raw_packet_send**, salvo en el hecho de que permite a una aplicación enviar paquetes de Raw IP desde una interfaz física especificada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1234">*This service is similar to **nx_ip_raw_packet_send**, except that this service allows an application to send raw IP packet from a specified physical interfaces.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1235">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1235">Parameters</span></span>

- <span data-ttu-id="a9163-1236">**ip_ptr**: puntero a la tarea de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1236">**ip_ptr** Pointer to previously created IP task.</span></span>
- <span data-ttu-id="a9163-1237">**packet_ptr**: puntero al paquete que se va a transmitir.</span><span class="sxs-lookup"><span data-stu-id="a9163-1237">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="a9163-1238">**destination_ip**: dirección IP para enviar el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1238">**destination_ip** IP address to send packet.</span></span>
- <span data-ttu-id="a9163-1239">**address_index**: índice de la dirección de la interfaz en la que se va a enviar el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1239">**address_index** Index of the address of the interface to send packet out on.</span></span>
- <span data-ttu-id="a9163-1240">**type_of_service**: tipo de servicio para el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1240">**type_of_service** Type of service for packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1241">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1241">Return Values</span></span>

- <span data-ttu-id="a9163-1242">**NX_SUCCESS**: (0x00) se transmitió correctamente el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1242">**NX_SUCCESS** (0x00) Packet successfully transmitted.</span></span>
- <span data-ttu-id="a9163-1243">**NX_IP_ADDRESS_ERROR**: (0X21) no hay ninguna interfaz de salida adecuada disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-1243">**NX_IP_ADDRESS_ERROR** (0x21) No suitable outgoing interface available.</span></span>
- <span data-ttu-id="a9163-1244">**NX_NOT_ENABLED**: (0x14) no se ha habilitado el procesamiento de paquetes Raw IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1244">**NX_NOT_ENABLED** (0x14) Raw IP packet processing not enabled.</span></span>
- <span data-ttu-id="a9163-1245">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1245">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-1246">**NX_PTR_ERROR**: (0x07) la entrada del puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1246">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="a9163-1247">**NX_OPTION_ERROR**: (0x0A) el tipo de servicio especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1247">**NX_OPTION_ERROR** (0x0A) Invalid type of service specified.</span></span>
- <span data-ttu-id="a9163-1248">**NX_OVERFLOW**: (0x03) el puntero de anteposición de paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1248">**NX_OVERFLOW** (0x03) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="a9163-1249">**NX_UNDERFLOW**: (0x02) el puntero de anteposición de paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1249">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="a9163-1250">**NX_INVALID_INTERFACE**: (0x4C) el índice de interfaz especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1250">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1251">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1251">Allowed From</span></span>

<span data-ttu-id="a9163-1252">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1252">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1253">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1253">Preemption Possible</span></span>

<span data-ttu-id="a9163-1254">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1254">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1255">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1255">Example</span></span>

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1256">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1256">See Also</span></span>

- <span data-ttu-id="a9163-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="a9163-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="a9163-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span></span>

## <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="a9163-1259">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="a9163-1259">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="a9163-1260">Recibe un paquete de Raw IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1260">Receive raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1261">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1261">Prototype</span></span>

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-1262">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1262">Description</span></span>

<span data-ttu-id="a9163-1263">Este servicio recibe un paquete de Raw IP de la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1263">This service receives a raw IP packet from the specified IP instance.</span></span> <span data-ttu-id="a9163-1264">Si hay paquetes IP en la cola de recepción de paquetes sin procesar, el primer paquete (más antiguo) se devuelve al autor de llamada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1264">If there are IP packets on the raw packet receive queue, the first (oldest) packet is returned to the caller.</span></span> <span data-ttu-id="a9163-1265">De lo contrario, si no hay paquetes disponibles, el autor de llamada puede suspenderse según lo especifique la opción de espera.</span><span class="sxs-lookup"><span data-stu-id="a9163-1265">Otherwise, if no packets are available, the caller may suspend as specified by the wait option.</span></span>

<span data-ttu-id="a9163-1266">*Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido cuando ya no se necesite.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1266">*If NX_SUCCESS, is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1267">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1267">Parameters</span></span>

- <span data-ttu-id="a9163-1268">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1268">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1269">**packet_ptr**: puntero al puntero para colocar el paquete de Raw IP recibido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1269">**packet_ptr** Pointer to pointer to place the received raw IP packet in.</span></span>
- <span data-ttu-id="a9163-1270">**wait_option**: define cómo se comporta el servicio si no hay ningún paquete de Raw IP disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-1270">**wait_option** Defines how the service behaves if there are no raw IP packets available.</span></span> <span data-ttu-id="a9163-1271">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-1271">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-1272">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1272">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-1274">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-1274">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1275">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1275">Return Values</span></span>

- <span data-ttu-id="a9163-1276">**NX_SUCCESS**: (0x00) los paquetes de Raw IP se recibieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1276">**NX_SUCCESS** (0x00) Successful IP raw packet receive.</span></span>
- <span data-ttu-id="a9163-1277">**NX_NO_PACKET**: (0X01) no hay ningún paquete disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-1277">**NX_NO_PACKET** (0x01) No packet was available.</span></span>
- <span data-ttu-id="a9163-1278">**NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1278">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="a9163-1279">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1279">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="a9163-1280">**NX_PTR_ERROR**: (0X07) la IP o el puntero de paquete devuelto no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1280">**NX_PTR_ERROR** (0x07) Invalid IP or return packet pointer.</span></span>
- <span data-ttu-id="a9163-1281">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1281">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1282">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1282">Allowed From</span></span>

<span data-ttu-id="a9163-1283">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1283">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1284">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1284">Preemption Possible</span></span>

<span data-ttu-id="a9163-1285">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1285">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1286">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1286">Example</span></span>

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1287">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1287">See Also</span></span>

- <span data-ttu-id="a9163-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="a9163-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="a9163-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="a9163-1290">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="a9163-1290">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="a9163-1291">Envía un paquete de Raw IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1291">Send raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1292">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1292">Prototype</span></span>

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="a9163-1293">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1293">Description</span></span>

<span data-ttu-id="a9163-1294">Este servicio envía un paquete de Raw IP a la dirección IP de destino.</span><span class="sxs-lookup"><span data-stu-id="a9163-1294">This service sends a raw IP packet to the destination IP address.</span></span> <span data-ttu-id="a9163-1295">Tenga en cuenta que esta rutina se devuelve inmediatamente y, por lo tanto, no se conoce si se ha enviado realmente el paquete IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1295">Note that this routine returns immediately, and it is therefore not known whether the IP packet has actually been sent.</span></span> <span data-ttu-id="a9163-1296">El controlador de red será responsable de liberar el paquete cuando se complete la transmisión.</span><span class="sxs-lookup"><span data-stu-id="a9163-1296">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span>

<span data-ttu-id="a9163-1297">En el caso de un sistema de host múltiple, NetX usa la dirección IP de destino para encontrar una interfaz de red adecuada y la dirección IP de la interfaz como dirección de origen.</span><span class="sxs-lookup"><span data-stu-id="a9163-1297">For a multihome system, NetX uses the destination IP address to find an appropriate network interface and uses the IP address of the interface as the source address.</span></span> <span data-ttu-id="a9163-1298">Si la dirección IP de destino es de difusión o multidifusión, se usa la primera interfaz válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1298">If the destination IP address is broadcast or multicast, the first valid interface is used.</span></span> <span data-ttu-id="a9163-1299">En este caso, las aplicaciones usan el elemento ***nx_ip_raw_packet_interface_send***.</span><span class="sxs-lookup"><span data-stu-id="a9163-1299">Applications use the ***nx_ip_raw_packet_interface_send*** in this case.</span></span>

<span data-ttu-id="a9163-1300">*A menos que se devuelva un error, la aplicación no debe liberar el paquete después de esta llamada. Si lo hace, se producirán resultados imprevisibles, ya que el controlador de red liberará el paquete después de la transmisión.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1300">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1301">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1301">Parameters</span></span>

- <span data-ttu-id="a9163-1302">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1302">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1303">**packet_ptr**: puntero al paquete de Raw IP que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="a9163-1303">**packet_ptr** Pointer to the raw IP packet to send.</span></span>
- <span data-ttu-id="a9163-1304">**destination_ip**: dirección IP de destino, que puede ser una dirección IP de host específica, una difusión de red, un bucle invertido interno o una dirección de multidifusión.</span><span class="sxs-lookup"><span data-stu-id="a9163-1304">**destination_ip** Destination IP address, which can be a specific host IP address, a network broadcast, an internal loop-back, or a multicast address.</span></span>
- <span data-ttu-id="a9163-1305">**type_of_service**: define el tipo de servicio para la transmisión. Los valores válidos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="a9163-1305">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
- <span data-ttu-id="a9163-1306">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1306">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="a9163-1307">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1307">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="a9163-1308">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1308">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="a9163-1309">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1309">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="a9163-1310">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1310">NX_IP_MIN_COST (0x00020000)</span></span>


### <a name="return-values"></a><span data-ttu-id="a9163-1311">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1311">Return Values</span></span>

- <span data-ttu-id="a9163-1312">**NX_SUCCESS**: (0x00) se inició el envío correcto de paquetes de Raw IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1312">**NX_SUCCESS** (0x00) Successful IP raw packet send initiated.</span></span>
- <span data-ttu-id="a9163-1313">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1313">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="a9163-1314">**NX_NOT_ENABLED**: (0x14) la característica de Raw IP no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1314">**NX_NOT_ENABLED** (0x14) Raw IP feature is not enabled.</span></span>
- <span data-ttu-id="a9163-1315">**NX_OPTION_ERROR**: (0x0A) el tipo de servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1315">**NX_OPTION_ERROR** (0x0A) Invalid type of service.</span></span>
- <span data-ttu-id="a9163-1316">**NX_UNDERFLOW**: (0X02) no dispone de espacio suficiente para anteponer un encabezado IP en el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1316">**NX_UNDERFLOW** (0x02) Not enough room to prepend an IP header on the packet.</span></span>
- <span data-ttu-id="a9163-1317">**NX_OVERFLOW**: (0x03) el puntero para anexar paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1317">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="a9163-1318">**NX_PTR_ERROR**: (0X07) la IP o el puntero del paquete no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1318">**NX_PTR_ERROR** (0x07) Invalid IP or packet pointer.</span></span>
- <span data-ttu-id="a9163-1319">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1319">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1320">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1320">Allowed From</span></span>

<span data-ttu-id="a9163-1321">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1321">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1322">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1322">Preemption Possible</span></span>

<span data-ttu-id="a9163-1323">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1323">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1324">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1324">Example</span></span>

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1325">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1325">See Also</span></span>

- <span data-ttu-id="a9163-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="a9163-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span></span>
- <span data-ttu-id="a9163-1328">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="a9163-1328">nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_static_route_add"></a><span data-ttu-id="a9163-1329">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="a9163-1329">nx_ip_static_route_add</span></span>

<span data-ttu-id="a9163-1330">Agrega una ruta predeterminada a la tabla de enrutamiento.</span><span class="sxs-lookup"><span data-stu-id="a9163-1330">Add static route to the routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1331">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1331">Prototype</span></span>

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a><span data-ttu-id="a9163-1332">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1332">Description</span></span>

<span data-ttu-id="a9163-1333">Este servicio agrega una entrada a la tabla de enrutamiento estático.</span><span class="sxs-lookup"><span data-stu-id="a9163-1333">This service adds an entry to the static routing table.</span></span> <span data-ttu-id="a9163-1334">Tenga en cuenta que la dirección *next_hop* debe ser accesible directamente desde uno de los dispositivos de red local.</span><span class="sxs-lookup"><span data-stu-id="a9163-1334">Note that the *next_hop* address must be directly accessible from one of the local network devices.</span></span>

<span data-ttu-id="a9163-1335">*Tenga en cuenta que el elemento ip_ptr debe apuntar a una estructura IP de NetX válida y la biblioteca NetX debe compilarse con NX_ENABLE_IP_STATIC_ROUTING definido para usar este servicio. De forma predeterminada, NetX se compila sin el elemento NX_ENABLE_IP_STATIC_ROUTING definido.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1335">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1336">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1336">Parameters</span></span>

- <span data-ttu-id="a9163-1337">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1337">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1338">**network_address**: dirección de red de destino, en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-1338">**network_address** Target network address, in host byte order</span></span>
- <span data-ttu-id="a9163-1339">**net_mask**: máscara de red de destino, en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-1339">**net_mask** Target network mask, in host byte order</span></span>
- <span data-ttu-id="a9163-1340">**next_hop**: dirección del próximo salto para la red de destino, en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-1340">**next_hop** Next hop address for the target network, in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1341">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1341">Return Values</span></span>

- <span data-ttu-id="a9163-1342">**NX_SUCCESS**: (0x00) la entrada se agrega a la tabla de enrutamiento estática.</span><span class="sxs-lookup"><span data-stu-id="a9163-1342">**NX_SUCCESS** (0x00) Entry is added to the static routing table.</span></span>
- <span data-ttu-id="a9163-1343">**NX_OVERFLOW**: (0x03) la tabla de enrutamiento estática está llena.</span><span class="sxs-lookup"><span data-stu-id="a9163-1343">**NX_OVERFLOW** (0x03) Static routing table is full.</span></span>
- <span data-ttu-id="a9163-1344">**NX_NOT_SUPPORTED**: (0X4B) esta característica no está compilada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1344">**NX_NOT_SUPPORTED** (0x4B) This feature is not compiled in.</span></span>
- <span data-ttu-id="a9163-1345">**NX_IP_ADDRESS_ERROR**: (0x21) el próximo salto no es accesible directamente a través de interfaces locales.</span><span class="sxs-lookup"><span data-stu-id="a9163-1345">**NX_IP_ADDRESS_ERROR** (0x21) Next hop is not directly accessible via local interfaces.</span></span>
- <span data-ttu-id="a9163-1346">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1346">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-1347">**NX_PTR_ERROR** (0x07) Puntero ip_ptr no válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1347">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1348">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1348">Allowed From</span></span>

<span data-ttu-id="a9163-1349">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1349">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1350">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1350">Preemption Possible</span></span>

<span data-ttu-id="a9163-1351">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1352">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1352">Example</span></span>

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1353">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1353">See Also</span></span>

- <span data-ttu-id="a9163-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_static_route_delete"></a><span data-ttu-id="a9163-1355">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-1355">nx_ip_static_route_delete</span></span>

<span data-ttu-id="a9163-1356">Elimina una ruta estática de la tabla de enrutamiento.</span><span class="sxs-lookup"><span data-stu-id="a9163-1356">Delete static route from routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1357">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1357">Prototype</span></span>

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a><span data-ttu-id="a9163-1358">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1358">Description</span></span>

<span data-ttu-id="a9163-1359">Este servicio elimina una entrada de la tabla de enrutamiento estática.</span><span class="sxs-lookup"><span data-stu-id="a9163-1359">This service deletes an entry from the static routing table.</span></span>

<span data-ttu-id="a9163-1360">*Tenga en cuenta que el elemento ip_ptr debe apuntar a una estructura IP de NetX válida y la biblioteca NetX debe compilarse con NX_ENABLE_IP_STATIC_ROUTING definido para usar este servicio. De forma predeterminada, NetX se compila sin el elemento NX_ENABLE_IP_STATIC_ROUTING definido.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1360">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1361">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1361">Parameters</span></span>

- <span data-ttu-id="a9163-1362">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1362">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1363">**network_address**: dirección de red de destino, en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-1363">**network_address** Target network address, in host byte order.</span></span>
- <span data-ttu-id="a9163-1364">**net_mask**: máscara de red de destino, en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-1364">**net_mask** Target network mask, in host byte order.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1365">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1365">Allowed From</span></span>

<span data-ttu-id="a9163-1366">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1366">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1367">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1367">Preemption Possible</span></span>

<span data-ttu-id="a9163-1368">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1368">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1369">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1369">Example</span></span>

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1370">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1370">See Also</span></span>

- <span data-ttu-id="a9163-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="a9163-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span></span>

## <a name="nx_ip_status_check"></a><span data-ttu-id="a9163-1372">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="a9163-1372">nx_ip_status_check</span></span>

<span data-ttu-id="a9163-1373">Comprobar el estado de una instancia de IP</span><span class="sxs-lookup"><span data-stu-id="a9163-1373">Check status of an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1374">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1374">Prototype</span></span>

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-1375">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1375">Description</span></span>

<span data-ttu-id="a9163-1376">Este servicio comprueba y, de manera opcional, espera el estado especificado de la interfaz de red primaria de una instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1376">This service checks and optionally waits for the specified status of the primary network interface of a previously created IP instance.</span></span> <span data-ttu-id="a9163-1377">Para obtener el estado de las interfaces secundarias, las aplicaciones deben usar el servicio ***nx_ip_interface_status_check.***</span><span class="sxs-lookup"><span data-stu-id="a9163-1377">To obtain status on secondary interfaces, applications shall use the service ***nx_ip_interface_status_check.***</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1378">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1378">Parameters</span></span>

- <span data-ttu-id="a9163-1379">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1379">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1380">**needed_status** Estado de IP solicitado, definido en el formato de mapa de bits de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a9163-1380">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
- <span data-ttu-id="a9163-1381">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="a9163-1381">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
- <span data-ttu-id="a9163-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="a9163-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
- <span data-ttu-id="a9163-1383">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="a9163-1383">NX_IP_LINK_ENABLED (0x0004)</span></span>
- <span data-ttu-id="a9163-1384">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="a9163-1384">NX_IP_ARP_ENABLED (0x0008)</span></span>
- <span data-ttu-id="a9163-1385">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="a9163-1385">NX_IP_UDP_ENABLED (0x0010)</span></span>
- <span data-ttu-id="a9163-1386">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="a9163-1386">NX_IP_TCP_ENABLED (0x0020)</span></span>
- <span data-ttu-id="a9163-1387">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="a9163-1387">NX_IP_IGMP_ENABLED (0x0040)</span></span>
- <span data-ttu-id="a9163-1388">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="a9163-1388">NX_IP_RARP_COMPLETE (0x0080)</span></span>
- <span data-ttu-id="a9163-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="a9163-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="a9163-1390">**actual_status** Puntero al destino del conjunto de bits real.</span><span class="sxs-lookup"><span data-stu-id="a9163-1390">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="a9163-1391">**wait_option** Define cómo se comporta el servicio si los bits de estado solicitados no están disponibles.</span><span class="sxs-lookup"><span data-stu-id="a9163-1391">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="a9163-1392">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-1392">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-1393">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1393">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-1395">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-1395">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1396">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1396">Return Values</span></span>

- <span data-ttu-id="a9163-1397">**NX_SUCCESS** (0X00) Comprobación de estado de IP correcta.</span><span class="sxs-lookup"><span data-stu-id="a9163-1397">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="a9163-1398">**NX_NOT_SUCCESSFUL** (0X43) La solicitud de estado no se ha satisfecho dentro del tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1398">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="a9163-1399">**NX_PTR_ERROR** (0x07) El puntero IP no es o ha dejado de ser válido o el puntero de estado real no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1399">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="a9163-1400">**NX_OPTION_ERROR** (0x0a) Opción de estado necesario no válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1400">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="a9163-1401">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1401">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1402">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1402">Allowed From</span></span>

<span data-ttu-id="a9163-1403">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1403">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1404">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1404">Preemption Possible</span></span>

<span data-ttu-id="a9163-1405">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1405">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1406">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1406">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1407">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1407">See Also</span></span>

- <span data-ttu-id="a9163-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="a9163-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="a9163-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span></span>

## <a name="nx_packet_allocate"></a><span data-ttu-id="a9163-1413">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="a9163-1413">nx_packet_allocate</span></span>

<span data-ttu-id="a9163-1414">Asigna un paquete del grupo especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1414">Allocate packet from specified pool</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1415">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1415">Prototype</span></span>

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-1416">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1416">Description</span></span>

<span data-ttu-id="a9163-1417">Este servicio asigna un paquete del grupo especificado y ajusta el puntero antepuesto en el paquete según el tipo de paquete especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1417">This service allocates a packet from the specified pool and adjusts the prepend pointer in the packet according to the type of packet specified.</span></span> <span data-ttu-id="a9163-1418">Si no hay ningún paquete disponible, el servicio se suspende según la opción de espera proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1418">If no packet is available, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1419">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1419">Parameters</span></span>

- <span data-ttu-id="a9163-1420">**pool_ptr**: puntero a un grupo de paquetes creado previamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1420">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="a9163-1421">**packet_ptr**: puntero al puntero del puntero de paquete asignado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1421">**packet_ptr** Pointer to the pointer of the allocated packet pointer.</span></span>
- <span data-ttu-id="a9163-1422">**packet_type**: define el tipo de paquete solicitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1422">**packet_type** Defines the type of packet requested.</span></span> <span data-ttu-id="a9163-1423">Consulte "Grupos de paquetes" en la página 49 del capítulo 3 para obtener una lista de los tipos de paquetes admitidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1423">See “Packet Pools” on page 49 in Chapter 3 for a list of supported packet types.</span></span>
- <span data-ttu-id="a9163-1424">**wait_option**: define el tiempo de espera en tics si no hay paquetes disponibles en el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="a9163-1424">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="a9163-1425">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-1425">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-1426">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1426">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-1428">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-1428">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1429">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1429">Return Values</span></span>

- <span data-ttu-id="a9163-1430">**NX_SUCCESS**: (0x00) los paquetes se asignaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1430">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="a9163-1431">**NX_NO_PACKET**: (0X01) no hay ningún paquete disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-1431">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="a9163-1432">**NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1432">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="a9163-1433">**NX_INVALID_PARAMETERS** (0x4D) El tamaño de paquete no admite el protocolo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1433">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="a9163-1434">**NX_OPTION_ERROR**: (0X0a) el tipo de paquete no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1434">**NX_OPTION_ERROR** (0x0A) Invalid packet type.</span></span>
- <span data-ttu-id="a9163-1435">**NX_PTR_ERROR**: (0x07) el grupo o el puntero de devolución de paquetes no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1435">**NX_PTR_ERROR** (0x07) Invalid pool or packet return pointer.</span></span>
- <span data-ttu-id="a9163-1436">**NX_CALLER_ERROR**: (0x11) la opción de espera de un elemento distinto de un subproceso no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1436">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1437">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1437">Allowed From</span></span>

<span data-ttu-id="a9163-1438">Inicialización, subprocesos, temporizadores e ISR (controladores de red de la aplicación).</span><span class="sxs-lookup"><span data-stu-id="a9163-1438">Initialization, threads, timers, and ISRs (application network drivers).</span></span> <span data-ttu-id="a9163-1439">La opción de espera debe ser NX_NO_WAIT cuando se usa en ISR o en el contexto del temporizador.</span><span class="sxs-lookup"><span data-stu-id="a9163-1439">Wait option must be NX_NO_WAIT when used in ISR or in timer context.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1440">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1440">Preemption Possible</span></span>

<span data-ttu-id="a9163-1441">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1441">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1442">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1442">Example</span></span>

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1443">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1443">See Also</span></span>

- <span data-ttu-id="a9163-1444">nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="a9163-1444">nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="a9163-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="a9163-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="a9163-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="a9163-1447">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="a9163-1447">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="a9163-1448">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1448">nx_packet_transmit_release</span></span>

## <a name="nx_packet_copy"></a><span data-ttu-id="a9163-1449">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="a9163-1449">nx_packet_copy</span></span>

<span data-ttu-id="a9163-1450">Copia el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1450">Copy packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1451">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1451">Prototype</span></span>

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-1452">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1452">Description</span></span>

<span data-ttu-id="a9163-1453">Este servicio copia la información del paquete proporcionado en uno o varios paquetes nuevos que se asignan desde el grupo de paquetes proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1453">This service copies the information in the supplied packet to one or more new packets that are allocated from the supplied packet pool.</span></span> <span data-ttu-id="a9163-1454">Si se completa correctamente, se devuelve el puntero al nuevo paquete en el destino al que apunta el elemento **new_packet_ptr**.</span><span class="sxs-lookup"><span data-stu-id="a9163-1454">If successful, the pointer to the new packet is returned in destination pointed to by **new_packet_ptr**.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1455">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1455">Parameters</span></span>

- <span data-ttu-id="a9163-1456">**packet_ptr**: puntero al paquete de origen.</span><span class="sxs-lookup"><span data-stu-id="a9163-1456">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="a9163-1457">**new_packet_ptr**: puntero al destino en el que se va a devolver el puntero a la nueva copia del paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1457">**new_packet_ptr** Pointer to the destination of where to return the pointer to the new copy of the packet.</span></span>
- <span data-ttu-id="a9163-1458">**pool_ptr**: puntero al grupo de paquetes creado anteriormente que se utiliza para asignar uno o varios paquetes para la copia.</span><span class="sxs-lookup"><span data-stu-id="a9163-1458">**pool_ptr** Pointer to the previously created packet pool that is used to allocate one or more packets for the copy.</span></span>
- <span data-ttu-id="a9163-1459">**wait_option**: define cómo espera el servicio si no hay ningún paquete disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-1459">**wait_option** Defines how the service waits if there are no packets available.</span></span> <span data-ttu-id="a9163-1460">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-1460">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-1461">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1461">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-1463">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-1463">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1464">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1464">Return Values</span></span>
- <span data-ttu-id="a9163-1465">**NX_SUCCESS**: (0x00) los paquetes se copiaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1465">**NX_SUCCESS** (0x00) Successful packet copy.</span></span>
- <span data-ttu-id="a9163-1466">**NX_NO_PACKET**: (0x01) el paquete no está disponible para la copia.</span><span class="sxs-lookup"><span data-stu-id="a9163-1466">**NX_NO_PACKET** (0x01) Packet not available for copy.</span></span>
- <span data-ttu-id="a9163-1467">**NX_INVALID_PACKET**: (0X12) error en la copia o el paquete de origen está vacío.</span><span class="sxs-lookup"><span data-stu-id="a9163-1467">**NX_INVALID_PACKET** (0x12) Empty source packet or copy failed.</span></span>
- <span data-ttu-id="a9163-1468">**NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1468">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="a9163-1469">**NX_INVALID_PARAMETERS**: (0x4D) el tamaño de paquete no admite el protocolo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1469">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="a9163-1470">**NX_PTR_ERROR**: (0x07) el grupo, el paquete o el puntero de destino no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1470">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or destination pointer.</span></span>
- <span data-ttu-id="a9163-1471">**NX_UNDERFLOW**: (0x02) el puntero de anteposición de paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1471">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="a9163-1472">**NX_OVERFLOW**: (0x03) el puntero para anexar paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1472">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="a9163-1473">**NX_CALLER_ERROR**: (0x11) se especificó una opción de espera en la inicialización o en una ISR.</span><span class="sxs-lookup"><span data-stu-id="a9163-1473">**NX_CALLER_ERROR** (0x11) A wait option was specified in initialization or in an ISR.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1474">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1474">Allowed From</span></span>

<span data-ttu-id="a9163-1475">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="a9163-1475">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1476">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1476">Preemption Possible</span></span>

<span data-ttu-id="a9163-1477">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1477">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1478">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1478">Example</span></span>

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1479">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1479">See Also</span></span>

- <span data-ttu-id="a9163-1480">nx_packet_allocate, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="a9163-1480">nx_packet_allocate, nx_packet_data_append,</span></span>
- <span data-ttu-id="a9163-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="a9163-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="a9163-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="a9163-1483">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="a9163-1483">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="a9163-1484">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1484">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_append"></a><span data-ttu-id="a9163-1485">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="a9163-1485">nx_packet_data_append</span></span>

<span data-ttu-id="a9163-1486">Anexa datos al final del paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1486">Append data to end of packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1487">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1487">Prototype</span></span>

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-1488">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1488">Description</span></span>

<span data-ttu-id="a9163-1489">Este servicio anexa datos al final del paquete especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1489">This service appends data to the end of the specified packet.</span></span> <span data-ttu-id="a9163-1490">El área de datos proporcionada se copia en el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1490">The supplied data area is copied into the packet.</span></span> <span data-ttu-id="a9163-1491">Si no hay suficiente memoria disponible y la característica de paquetes encadenados está habilitada, se asignarán uno o varios paquetes para satisfacer la solicitud.</span><span class="sxs-lookup"><span data-stu-id="a9163-1491">If there is not enough memory available, and the chained packet feature is enabled, one or more packets will be allocated to satisfy the request.</span></span> <span data-ttu-id="a9163-1492">Si la característica de paquetes encadenados no está habilitada, se devuelve *NX_SIZE_ERROR*.</span><span class="sxs-lookup"><span data-stu-id="a9163-1492">If the chained packet feature is not enabled, *NX_SIZE_ERROR* is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1493">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1493">Parameters</span></span>

- <span data-ttu-id="a9163-1494">**packet_ptr**: puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1494">**packet_ptr** Packet pointer.</span></span>
- <span data-ttu-id="a9163-1495">**data_start**: puntero al inicio del área de datos del usuario que se va a anexar al paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1495">**data_start** Pointer to the start of the user’s data area to append to the packet.</span></span>
- <span data-ttu-id="a9163-1496">**data_size**: tamaño del área de datos del usuario.</span><span class="sxs-lookup"><span data-stu-id="a9163-1496">**data_size** Size of user’s data area.</span></span>
- <span data-ttu-id="a9163-1497">**pool_ptr**: puntero al grupo de paquetes desde el que se va a asignar otro paquete si no hay suficiente espacio en el paquete actual.</span><span class="sxs-lookup"><span data-stu-id="a9163-1497">**pool_ptr** Pointer to packet pool from which to allocate another packet if there is not enough room in the current packet.</span></span>
- <span data-ttu-id="a9163-1498">**wait_option**: define cómo se comporta el servicio si no hay ningún paquete disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-1498">**wait_option** Defines how the service behaves if there are no packets available.</span></span> <span data-ttu-id="a9163-1499">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-1499">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-1500">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1500">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-1502">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-1502">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1503">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1503">Return Values</span></span>

- <span data-ttu-id="a9163-1504">**NX_SUCCESS**: (0x00) el paquete se anexó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1504">**NX_SUCCESS** (0x00) Successful packet append.</span></span>
- <span data-ttu-id="a9163-1505">**NX_NO_PACKET**: (0X01) no hay ningún paquete disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-1505">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="a9163-1506">**NX_WAIT_ABORTED**: (0x1A) una llamada a *tx_thread_wait_abort* ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1506">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="a9163-1507">**NX_INVALID_PARAMETERS**: (0x4D) el tamaño de paquete no admite el protocolo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1507">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="a9163-1508">**NX_UNDERFLOW**: (0x02) el puntero antepuesto es menor que el inicio de carga.</span><span class="sxs-lookup"><span data-stu-id="a9163-1508">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="a9163-1509">**NX_OVERFLOW**: (0x03) el puntero anexado es mayor que el final de la carga.</span><span class="sxs-lookup"><span data-stu-id="a9163-1509">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>
- <span data-ttu-id="a9163-1510">**NX_PTR_ERROR**: (0x07): el grupo, el paquete o el puntero de datos no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1510">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or data Pointer.</span></span>
- <span data-ttu-id="a9163-1511">**NX_SIZE_ERROR**: (0x09) el tamaño de datos no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1511">**NX_SIZE_ERROR** (0x09) Invalid data size.</span></span>
- <span data-ttu-id="a9163-1512">**NX_CALLER_ERROR**: (0x11) la opción de espera de un elemento distinto de un subproceso no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1512">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1513">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1513">Allowed From</span></span>

<span data-ttu-id="a9163-1514">Inicialización, subprocesos, temporizadores e ISR (controladores de red de la aplicación)</span><span class="sxs-lookup"><span data-stu-id="a9163-1514">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1515">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1515">Preemption Possible</span></span>

<span data-ttu-id="a9163-1516">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1516">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1517">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1517">Example</span></span>

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a><span data-ttu-id="a9163-1518">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1518">See Also</span></span>

- <span data-ttu-id="a9163-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,</span><span class="sxs-lookup"><span data-stu-id="a9163-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,</span></span>
- <span data-ttu-id="a9163-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="a9163-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="a9163-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="a9163-1522">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1522">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_extract_offset"></a><span data-ttu-id="a9163-1523">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="a9163-1523">nx_packet_data_extract_offset</span></span>

<span data-ttu-id="a9163-1524">Extrae datos del paquete mediante un desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="a9163-1524">Extract data from packet via an offset</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1525">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1525">Prototype</span></span>

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="a9163-1526">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1526">Description</span></span>

<span data-ttu-id="a9163-1527">Este servicio copia los datos de un paquete de NetX (o cadena de paquetes) a partir del desplazamiento especificado desde el puntero antepuesto del paquete del tamaño especificado en bytes en el búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1527">This service copies data from a NetX packet (or packet chain) starting at the specified offset from the packet prepend pointer of the specified size in bytes into the specified buffer.</span></span> <span data-ttu-id="a9163-1528">El número de bytes que se copian realmente se devuelve en *bytes_copied.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1528">The number of bytes actually copied is returned in *bytes_copied.*</span></span> <span data-ttu-id="a9163-1529">Este servicio no quita los datos del paquete ni ajusta el puntero antepuesto u otra información de estado interno.</span><span class="sxs-lookup"><span data-stu-id="a9163-1529">This service does not remove data from the packet, nor does it adjust the prepend pointer or other internal state information.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1530">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1530">Parameters</span></span>

- <span data-ttu-id="a9163-1531">**packet_ptr**: puntero al paquete que se va a extraer.</span><span class="sxs-lookup"><span data-stu-id="a9163-1531">**packet_ptr** Pointer to packet to extract</span></span>
- <span data-ttu-id="a9163-1532">**offset**: desplazamiento desde el puntero antepuesto actual.</span><span class="sxs-lookup"><span data-stu-id="a9163-1532">**offset** Offset from the current prepend pointer.</span></span>
- <span data-ttu-id="a9163-1533">**buffer_start**: puntero al principio del búfer de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="a9163-1533">**buffer_start** Pointer to start of save buffer</span></span>
- <span data-ttu-id="a9163-1534">**buffer_length**: número de bytes que se van a copiar.</span><span class="sxs-lookup"><span data-stu-id="a9163-1534">**buffer_length** Number of bytes to copy</span></span>
- <span data-ttu-id="a9163-1535">**bytes_copied**: número de bytes copiados realmente</span><span class="sxs-lookup"><span data-stu-id="a9163-1535">**bytes_copied** Number of bytes actually copied</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1536">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1536">Return Values</span></span>

- <span data-ttu-id="a9163-1537">**NX_SUCCESS**: (0x00) los paquetes se copiaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1537">**NX_SUCCESS** (0x00) Successful packet copy</span></span>
- <span data-ttu-id="a9163-1538">**NX_PACKET_OFFSET_ERROR**: (0x53) se proporcionó un valor de desplazamiento no válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1538">**NX_PACKET_OFFSET_ERROR** (0x53) Invalid offset value was supplied</span></span>
- <span data-ttu-id="a9163-1539">**NX_PTR_ERROR**: (0X07) el puntero de paquete o de búfer no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1539">**NX_PTR_ERROR** (0x07) Invalid packet pointer or buffer pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1540">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1540">Allowed From</span></span>

<span data-ttu-id="a9163-1541">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="a9163-1541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1542">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1542">Preemption Possible</span></span>

<span data-ttu-id="a9163-1543">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1543">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1544">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1544">Example</span></span>

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1545">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1545">See Also</span></span>

- <span data-ttu-id="a9163-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="a9163-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="a9163-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="a9163-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="a9163-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="a9163-1549">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1549">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_retrieve"></a><span data-ttu-id="a9163-1550">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="a9163-1550">nx_packet_data_retrieve</span></span>

<span data-ttu-id="a9163-1551">Recupera datos de un paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1551">Retrieve data from packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1552">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1552">Prototype</span></span>

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="a9163-1553">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1553">Description</span></span>

<span data-ttu-id="a9163-1554">Este servicio copia los datos del paquete proporcionado en el búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1554">This service copies data from the supplied packet into the supplied buffer.</span></span> <span data-ttu-id="a9163-1555">El número real de bytes copiados se devuelve en el destino al que apunta **bytes_copied**.</span><span class="sxs-lookup"><span data-stu-id="a9163-1555">The actual number of bytes copied is returned in the destination pointed to by **bytes_copied**.</span></span>

<span data-ttu-id="a9163-1556">Tenga en cuenta que este servicio no cambia el estado interno del paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1556">Note that this service does not change internal state of the packet.</span></span> <span data-ttu-id="a9163-1557">Los datos que se están recuperando siguen estando disponibles en el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1557">The data being retrieved is still available in the packet.</span></span>

<span data-ttu-id="a9163-1558">*El búfer de destino debe ser lo suficientemente grande como para incluir el contenido del paquete. Si no es así, se dañará la memoria, lo que dará lugar a resultados imprevisibles.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1558">*The destination buffer must be large enough to hold the packet's contents. If not, memory will be corrupted causing unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1559">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1559">Parameters</span></span>

- <span data-ttu-id="a9163-1560">**packet_ptr**: puntero al paquete de origen.</span><span class="sxs-lookup"><span data-stu-id="a9163-1560">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="a9163-1561">**buffer_start**: puntero al principio del área del búfer.</span><span class="sxs-lookup"><span data-stu-id="a9163-1561">**buffer_start** Pointer to the start of the buffer area.</span></span>
- <span data-ttu-id="a9163-1562">**bytes_copied**: puntero al destino para el número de bytes copiados.</span><span class="sxs-lookup"><span data-stu-id="a9163-1562">**bytes_copied** Pointer to the destination for the number of bytes copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1563">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1563">Return Values</span></span>

- <span data-ttu-id="a9163-1564">**NX_SUCCESS**: (0x00) los datos de los paquetes se recuperaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1564">**NX_SUCCESS** (0x00) Successful packet data retrieve.</span></span>
- <span data-ttu-id="a9163-1565">**NX_INVALID_PACKET**: (0X12) el paquete no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1565">**NX_INVALID_PACKET** (0x12) Invalid packet.</span></span>
- <span data-ttu-id="a9163-1566">**NX_PTR_ERROR**: (0x07) el paquete, el inicio del búfer o el puntero de bytes copiados no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1566">**NX_PTR_ERROR** (0x07) Invalid packet, buffer start, or bytes copied pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1567">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1567">Allowed From</span></span>

<span data-ttu-id="a9163-1568">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="a9163-1568">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1569">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1569">Preemption Possible</span></span>

<span data-ttu-id="a9163-1570">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1570">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1571">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1571">Example</span></span>

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1572">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1572">See Also</span></span>

- <span data-ttu-id="a9163-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="a9163-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="a9163-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span></span>
- <span data-ttu-id="a9163-1575">nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-1575">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="a9163-1576">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="a9163-1576">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="a9163-1577">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1577">nx_packet_transmit_release</span></span>

## <a name="nx_packet_length_get"></a><span data-ttu-id="a9163-1578">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="a9163-1578">nx_packet_length_get</span></span>

<span data-ttu-id="a9163-1579">Obtiene la longitud de los datos de un paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1579">Get length of packet data</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1580">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1580">Prototype</span></span>

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a><span data-ttu-id="a9163-1581">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1581">Description</span></span>

<span data-ttu-id="a9163-1582">Este servicio obtiene la longitud de los datos en el paquete especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1582">This service gets the length of the data in the specified packet.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1583">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1583">Parameters</span></span>

- <span data-ttu-id="a9163-1584">**packet_ptr**: puntero al paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1584">**packet_ptr** Pointer to the packet.</span></span>
- <span data-ttu-id="a9163-1585">**length**: destino de la longitud del paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1585">**length** Destination for the packet length.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1586">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1586">Allowed From</span></span>

<span data-ttu-id="a9163-1587">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="a9163-1587">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1588">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1588">Preemption Possible</span></span>

<span data-ttu-id="a9163-1589">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1589">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1590">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1590">Example</span></span>

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1591">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1591">See Also</span></span>

- <span data-ttu-id="a9163-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="a9163-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="a9163-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="a9163-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="a9163-1594">nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-1594">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="a9163-1595">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="a9163-1595">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="a9163-1596">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1596">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_create"></a><span data-ttu-id="a9163-1597">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="a9163-1597">nx_packet_pool_create</span></span>

<span data-ttu-id="a9163-1598">Crea un grupo de paquetes en el área de memoria especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1598">Create packet pool in specified memory area</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1599">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1599">Prototype</span></span>

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="a9163-1600">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1600">Description</span></span>

<span data-ttu-id="a9163-1601">Este servicio crea un grupo de paquetes del tamaño de paquete especificado en el área de memoria proporcionada por el usuario.</span><span class="sxs-lookup"><span data-stu-id="a9163-1601">This service creates a packet pool of the specified packet size in the memory area supplied by the user.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1602">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1602">Parameters</span></span>

- <span data-ttu-id="a9163-1603">**pool_ptr**: puntero al bloque de control del grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="a9163-1603">**pool_ptr** Pointer to packet pool control block.</span></span>
- <span data-ttu-id="a9163-1604">**name**: puntero al nombre de la aplicación para el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="a9163-1604">**name** Pointer to application’s name for the packet pool.</span></span>
- <span data-ttu-id="a9163-1605">**payload_size**: número de bytes en cada paquete del grupo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1605">**payload_size** Number of bytes in each packet in the pool.</span></span> <span data-ttu-id="a9163-1606">Este valor debe ser de al menos 40 bytes y también debe ser divisible por 4.</span><span class="sxs-lookup"><span data-stu-id="a9163-1606">This value must be at least 40 bytes and must also be evenly divisible by 4.</span></span>
- <span data-ttu-id="a9163-1607">**memory_ptr**: puntero al área de memoria en la que se va a colocar el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="a9163-1607">**memory_ptr** Pointer to the memory area to place the packet pool in.</span></span> <span data-ttu-id="a9163-1608">El puntero se debe alinear en un límite ULONG.</span><span class="sxs-lookup"><span data-stu-id="a9163-1608">The pointer should be aligned on an ULONG boundary.</span></span>
- <span data-ttu-id="a9163-1609">**memory_size**: tamaño del área de memoria del grupo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1609">**memory_size** Size of the pool memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1610">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1610">Return Values</span></span>

- <span data-ttu-id="a9163-1611">**NX_SUCCESS**: (0x00) el grupo de paquetes se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1611">**NX_SUCCESS** (0x00) Successful packet pool create.</span></span>
- <span data-ttu-id="a9163-1612">**NX_PTR_ERROR**: (0x07) el puntero de memoria o el grupo no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1612">**NX_PTR_ERROR** (0x07) Invalid pool or memory pointer.</span></span>
- <span data-ttu-id="a9163-1613">**NX_SIZE_ERROR**: (0x09) el tamaño de memoria o el bloque no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1613">**NX_SIZE_ERROR** (0x09) Invalid block or memory size.</span></span>
- <span data-ttu-id="a9163-1614">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1614">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1615">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1615">Allowed From</span></span>

<span data-ttu-id="a9163-1616">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1616">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1617">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1617">Preemption Possible</span></span>

<span data-ttu-id="a9163-1618">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1618">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1619">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1619">Example</span></span>

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1620">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1620">See Also</span></span>

- <span data-ttu-id="a9163-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="a9163-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="a9163-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="a9163-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="a9163-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,</span></span>
- <span data-ttu-id="a9163-1624">nx_packet_release, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1624">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_delete"></a><span data-ttu-id="a9163-1625">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-1625">nx_packet_pool_delete</span></span>

<span data-ttu-id="a9163-1626">Elimina un grupo de paquetes creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1626">Delete previously created packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1627">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1627">Prototype</span></span>

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1628">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1628">Description</span></span>

<span data-ttu-id="a9163-1629">Este servicio elimina un grupo de paquetes creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1629">This service deletes a previously-created packet pool.</span></span> <span data-ttu-id="a9163-1630">NetX comprueba si hay subprocesos suspendidos en los paquetes del grupo de paquetes y borra la suspensión.</span><span class="sxs-lookup"><span data-stu-id="a9163-1630">NetX checks for any threads currently suspended on packets in the packet pool and clears the suspension.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1631">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1631">Parameters</span></span>

- <span data-ttu-id="a9163-1632">**pool_ptr**: puntero del bloque de control del grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="a9163-1632">**pool_ptr** Packet pool control block pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1633">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1633">Return Values</span></span>

- <span data-ttu-id="a9163-1634">**NX_SUCCESS**: (0x00) el grupo de paquetes se eliminó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1634">**NX_SUCCESS** (0x00) Successful packet pool delete.</span></span>
- <span data-ttu-id="a9163-1635">**NX_PTR_ERROR**: (0x07) el puntero del grupo no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1635">**NX_PTR_ERROR** (0x07) Invalid pool pointer.</span></span>
- <span data-ttu-id="a9163-1636">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1636">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1637">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1637">Allowed From</span></span>

<span data-ttu-id="a9163-1638">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1638">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1639">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1639">Preemption Possible</span></span>

<span data-ttu-id="a9163-1640">Sí</span><span class="sxs-lookup"><span data-stu-id="a9163-1640">Yes</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1641">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1641">Example</span></span>

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1642">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1642">See Also</span></span>

- <span data-ttu-id="a9163-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="a9163-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="a9163-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="a9163-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="a9163-1645">nx_packet_length_get, nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-1645">nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="a9163-1646">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="a9163-1646">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="a9163-1647">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1647">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_info_get"></a><span data-ttu-id="a9163-1648">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-1648">nx_packet_pool_info_get</span></span>

<span data-ttu-id="a9163-1649">Recupera información acerca de un grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="a9163-1649">Retrieve information about a packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1650">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1650">Prototype</span></span>

```C
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```

### <a name="description"></a><span data-ttu-id="a9163-1651">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1651">Description</span></span>

<span data-ttu-id="a9163-1652">Este servicio recupera información sobre el grupo de paquetes especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1652">This service retrieves information about the specified packet pool.</span></span>

<span data-ttu-id="a9163-1653">*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1653">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1654">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1654">Parameters</span></span>

- <span data-ttu-id="a9163-1655">**pool_ptr**: puntero a un grupo de paquetes creado previamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1655">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="a9163-1656">**total_packets**: puntero al destino para el número total de paquetes en el grupo.</span><span class="sxs-lookup"><span data-stu-id="a9163-1656">**total_packets** Pointer to destination for the total number of packets in the pool.</span></span>
- <span data-ttu-id="a9163-1657">**free_packets**: puntero al destino para el número total de paquetes actualmente disponibles.</span><span class="sxs-lookup"><span data-stu-id="a9163-1657">**free_packets** Pointer to destination for the total number of currently free packets.</span></span>
- <span data-ttu-id="a9163-1658">**empty_pool_requests**: puntero al destino del número total de solicitudes de asignación cuando el grupo estaba vacío.</span><span class="sxs-lookup"><span data-stu-id="a9163-1658">**empty_pool_requests** Pointer to destination of the total number of allocation requests when the pool was empty.</span></span>
- <span data-ttu-id="a9163-1659">**empty_pool_suspensions**: puntero al destino del número total de suspensiones del grupo vacío.</span><span class="sxs-lookup"><span data-stu-id="a9163-1659">**empty_pool_suspensions** Pointer to destination of the total number of empty pool suspensions.</span></span>
- <span data-ttu-id="a9163-1660">**invalid_packet_releases**: puntero al destino del número total de versiones de paquetes no válidas.</span><span class="sxs-lookup"><span data-stu-id="a9163-1660">**invalid_packet_releases** Pointer to destination of the total number of invalid packet releases.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1661">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1661">Return Values</span></span>

- <span data-ttu-id="a9163-1662">**TX_SUCCESS**: (0x00) la información del grupo de paquetes se recuperó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1662">**NX_SUCCESS** (0x00) Successful packet pool information retrieval.</span></span>
- <span data-ttu-id="a9163-1663">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1663">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-1664">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1664">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1665">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1665">Allowed From</span></span>

<span data-ttu-id="a9163-1666">Inicialización, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="a9163-1666">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1667">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1667">Preemption Possible</span></span>

<span data-ttu-id="a9163-1668">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1668">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1669">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1669">Example</span></span>

```C
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
    &total_packets,
    &free_packets,
    &empty_pool_requests,
    &empty_pool_suspensions,
    &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1670">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1670">See Also</span></span>

- <span data-ttu-id="a9163-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="a9163-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="a9163-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="a9163-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="a9163-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span></span>
- <span data-ttu-id="a9163-1674">nx_packet_release, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1674">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_release"></a><span data-ttu-id="a9163-1675">nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1675">nx_packet_release</span></span>

<span data-ttu-id="a9163-1676">Libera el paquete previamente asignado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1676">Release previously allocated packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1677">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1677">Prototype</span></span>

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1678">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1678">Description</span></span>

<span data-ttu-id="a9163-1679">Este servicio libera un paquete, incluidos los paquetes adicionales encadenados al paquete especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1679">This service releases a packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="a9163-1680">Si otro subproceso está bloqueado en la asignación de paquetes, se le proporciona el paquete y se reanuda.</span><span class="sxs-lookup"><span data-stu-id="a9163-1680">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span>

<span data-ttu-id="a9163-1681">*La aplicación debe impedir que se libere un paquete más de una vez, ya que, si lo hace, se producirán resultados imprevisibles.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1681">*The application must prevent releasing a packet more than once, because doing so will cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1682">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1682">Parameters</span></span>

- <span data-ttu-id="a9163-1683">**packet_ptr**: puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1683">**packet_ptr** Packet pointer.</span></span>


### <a name="return-values"></a><span data-ttu-id="a9163-1684">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1684">Return Values</span></span>
- <span data-ttu-id="a9163-1685">**NX_SUCCESS**: (0x00) los paquetes se liberaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1685">**NX_SUCCESS** (0x00) Successful packet release.</span></span>
- <span data-ttu-id="a9163-1686">**NX_PTR_ERROR**: (0X07) el puntero del paquete no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1686">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="a9163-1687">**NX_UNDERFLOW**: (0x02) el puntero antepuesto es menor que el inicio de carga.</span><span class="sxs-lookup"><span data-stu-id="a9163-1687">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="a9163-1688">**NX_OVERFLOW**: (0x03) el puntero anexado es mayor que el final de la carga.</span><span class="sxs-lookup"><span data-stu-id="a9163-1688">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1689">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1689">Allowed From</span></span>

<span data-ttu-id="a9163-1690">Inicialización, subprocesos, temporizadores e ISR (controladores de red de la aplicación)</span><span class="sxs-lookup"><span data-stu-id="a9163-1690">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1691">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1691">Preemption Possible</span></span>

<span data-ttu-id="a9163-1692">Sí</span><span class="sxs-lookup"><span data-stu-id="a9163-1692">Yes</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1693">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1693">Example</span></span>

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1694">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1694">See Also</span></span>

- <span data-ttu-id="a9163-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="a9163-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="a9163-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="a9163-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="a9163-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="a9163-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span></span>

## <a name="nx_packet_transmit_release"></a><span data-ttu-id="a9163-1699">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1699">nx_packet_transmit_release</span></span>

<span data-ttu-id="a9163-1700">Libera un paquete transmitido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1700">Release a transmitted packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1701">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1701">Prototype</span></span>

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1702">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1702">Description</span></span>

<span data-ttu-id="a9163-1703">En el caso de los paquetes que no son de TCP, este servicio libera un paquete transmitido, incluidos los paquetes adicionales encadenados al paquete especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1703">For non-TCP packets, this service releases a transmitted packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="a9163-1704">Si otro subproceso está bloqueado en la asignación de paquetes, se le proporciona el paquete y se reanuda.</span><span class="sxs-lookup"><span data-stu-id="a9163-1704">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span> <span data-ttu-id="a9163-1705">En el caso de un paquete de TCP transmitido, este se marca como transmitido, pero no se libera hasta que se confirma.</span><span class="sxs-lookup"><span data-stu-id="a9163-1705">For a transmitted TCP packet, the packet is marked as being transmitted but not released till the packet is acknowledged.</span></span> <span data-ttu-id="a9163-1706">Normalmente, se llama a este servicio desde el controlador de red de la aplicación después de que se transmita un paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1706">This service is typically called from the application's network driver after a packet is transmitted.</span></span>

<span data-ttu-id="a9163-1707">*El controlador de red debe quitar el encabezado de medios físicos y ajustar la longitud del paquete antes de llamar a este servicio.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1707">*The network driver should remove the physical media header and adjust the length of the packet before calling this service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1708">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1708">Parameters</span></span>

- <span data-ttu-id="a9163-1709">**packet_ptr**: puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-1709">**packet_ptr** Packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1710">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1710">Return Values</span></span>

- <span data-ttu-id="a9163-1711">**NX_SUCCESS** (0x00) Paquetes transmitidos liberados correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1711">**NX_SUCCESS** (0x00) Successful transmit packet release.</span></span>
- <span data-ttu-id="a9163-1712">**NX_PTR_ERROR**: (0X07) el puntero del paquete no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1712">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="a9163-1713">**NX_UNDERFLOW**: (0x02) el puntero antepuesto es menor que el inicio de carga.</span><span class="sxs-lookup"><span data-stu-id="a9163-1713">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="a9163-1714">**NX_OVERFLOW**: (0x03) el puntero anexado es mayor que el final de la carga.</span><span class="sxs-lookup"><span data-stu-id="a9163-1714">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1715">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1715">Allowed From</span></span>

<span data-ttu-id="a9163-1716">Inicialización, subprocesos, temporizadores y controladores de red de la aplicación (incluidos ISR)</span><span class="sxs-lookup"><span data-stu-id="a9163-1716">Initialization, threads, timers, Application network drivers (including ISRs)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1717">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1717">Preemption Possible</span></span>

<span data-ttu-id="a9163-1718">Sí</span><span class="sxs-lookup"><span data-stu-id="a9163-1718">Yes</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1719">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1719">Example</span></span>

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1720">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1720">See Also</span></span>

- <span data-ttu-id="a9163-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="a9163-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="a9163-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="a9163-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="a9163-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="a9163-1724">nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="a9163-1724">nx_packet_pool_info_get, nx_packet_release</span></span>

## <a name="nx_rarp_disable"></a><span data-ttu-id="a9163-1725">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="a9163-1725">nx_rarp_disable</span></span>

<span data-ttu-id="a9163-1726">Deshabilita Reverse Address Resolution Protocol (RARP).</span><span class="sxs-lookup"><span data-stu-id="a9163-1726">Disable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1727">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1727">Prototype</span></span>

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1728">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1728">Description</span></span>

<span data-ttu-id="a9163-1729">Este servicio deshabilita el componente RARP de NetX para la instancia de IP específica.</span><span class="sxs-lookup"><span data-stu-id="a9163-1729">This service disables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="a9163-1730">En el caso de un sistema de host múltiple, este servicio deshabilita RARP en todas las interfaces.</span><span class="sxs-lookup"><span data-stu-id="a9163-1730">For a multihome system, this service disables RARP on all interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1731">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1731">Parameters</span></span>

- <span data-ttu-id="a9163-1732">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1732">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1733">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1733">Return Values</span></span>

- <span data-ttu-id="a9163-1734">**NX_SUCCESS**: (0x00) RARP se deshabilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1734">**NX_SUCCESS** (0x00) Successful RARP disable.</span></span>
- <span data-ttu-id="a9163-1735">**NX_NOT_ENABLED**: (0X14) RARP no se habilitó.</span><span class="sxs-lookup"><span data-stu-id="a9163-1735">**NX_NOT_ENABLED** (0x14) RARP was not enabled.</span></span>
- <span data-ttu-id="a9163-1736">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1736">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-1737">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1737">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1738">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1738">Allowed From</span></span>

<span data-ttu-id="a9163-1739">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1739">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1740">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1740">Preemption Possible</span></span>

<span data-ttu-id="a9163-1741">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1741">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1742">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1742">Example</span></span>

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1743">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1743">See Also</span></span>

- <span data-ttu-id="a9163-1744">nx_rarp_enable, nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-1744">nx_rarp_enable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_enable"></a><span data-ttu-id="a9163-1745">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-1745">nx_rarp_enable</span></span>

<span data-ttu-id="a9163-1746">Habilita Reverse Address Resolution Protocol (RARP).</span><span class="sxs-lookup"><span data-stu-id="a9163-1746">Enable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1747">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1747">Prototype</span></span>

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1748">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1748">Description</span></span>

<span data-ttu-id="a9163-1749">Este servicio habilita el componente RARP de NetX para la instancia de IP específica.</span><span class="sxs-lookup"><span data-stu-id="a9163-1749">This service enables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="a9163-1750">Los componentes RARP buscan una dirección IP cero en todas las interfaces de red asociadas.</span><span class="sxs-lookup"><span data-stu-id="a9163-1750">The RARP components searches through all attached network interfaces for zero IP address.</span></span> <span data-ttu-id="a9163-1751">Una dirección IP cero indica que la interfaz todavía no tiene ninguna asignación de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1751">A zero IP address indicates the interface does not have IP address assignment yet.</span></span> <span data-ttu-id="a9163-1752">RARP intenta resolver la dirección IP mediante la habilitación del proceso RARP en esa interfaz.</span><span class="sxs-lookup"><span data-stu-id="a9163-1752">RARP attempts to resolve the IP address by enabling RARP process on that interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1753">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1753">Parameters</span></span>

- <span data-ttu-id="a9163-1754">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1754">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1755">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1755">Return Values</span></span>

- <span data-ttu-id="a9163-1756">**NX_SUCCESS**: (0x00) RARP se habilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1756">**NX_SUCCESS** (0x00) Successful RARP enable.</span></span>
- <span data-ttu-id="a9163-1757">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP ya es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1757">**NX_IP_ADDRESS_ERROR** (0x21) IP address is already valid.</span></span>
- <span data-ttu-id="a9163-1758">**NX_ALREADY_ENABLED**: (0x15) RARP ya estaba habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1758">**NX_ALREADY_ENABLED** (0x15) RARP was already enabled.</span></span>
- <span data-ttu-id="a9163-1759">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1759">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-1760">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1760">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1761">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1761">Allowed From</span></span>

<span data-ttu-id="a9163-1762">Inicialización, subprocesos, temporizadores</span><span class="sxs-lookup"><span data-stu-id="a9163-1762">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1763">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1763">Preemption Possible</span></span>

<span data-ttu-id="a9163-1764">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1764">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1765">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1765">Example</span></span>

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1766">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1766">See Also</span></span>

- <span data-ttu-id="a9163-1767">nx_rarp_disable, nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-1767">nx_rarp_disable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_info_get"></a><span data-ttu-id="a9163-1768">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-1768">nx_rarp_info_get</span></span>

<span data-ttu-id="a9163-1769">Recupera información acerca de las actividades de RARP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1769">Retrieve information about RARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1770">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1770">Prototype</span></span>

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="a9163-1771">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1771">Description</span></span>

<span data-ttu-id="a9163-1772">Este servicio recupera información sobre las actividades de RARP de la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1772">This service retrieves information about RARP activities for the specified IP instance.</span></span>

<span data-ttu-id="a9163-1773">*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1773">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1774">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1774">Parameters</span></span>

- <span data-ttu-id="a9163-1775">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1775">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1776">**rarp_requests_sent**: puntero al destino para el número total de solicitudes de RARP enviadas.</span><span class="sxs-lookup"><span data-stu-id="a9163-1776">**rarp_requests_sent** Pointer to destination for the total number of RARP requests sent.</span></span>
- <span data-ttu-id="a9163-1777">**rarp_responses_received**: puntero al destino para el número total de respuestas de RARP recibidas.</span><span class="sxs-lookup"><span data-stu-id="a9163-1777">**rarp_responses_received** Pointer to destination for the total number of RARP responses received.</span></span>
- <span data-ttu-id="a9163-1778">**rarp_invalid_messages**: puntero al destino del número total de mensajes no válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1778">**rarp_invalid_messages** Pointer to destination of the total number of invalid messages.</span></span>


### <a name="return-values"></a><span data-ttu-id="a9163-1779">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1779">Return Values</span></span>
- <span data-ttu-id="a9163-1780">**NX_SUCCESS**: (0x00) la información de RARP se recuperó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1780">**NX_SUCCESS** (0x00) Successful RARP information retrieval.</span></span>
- <span data-ttu-id="a9163-1781">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1781">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-1782">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1782">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="a9163-1783">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1784">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1784">Allowed From</span></span>

<span data-ttu-id="a9163-1785">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1785">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1786">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1786">Preemption Possible</span></span>

<span data-ttu-id="a9163-1787">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1787">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1788">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1788">Example</span></span>

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1789">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1789">See Also</span></span>

- <span data-ttu-id="a9163-1790">nx_rarp_disable, nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-1790">nx_rarp_disable, nx_rarp_enable</span></span>

## <a name="nx_system_initialize"></a><span data-ttu-id="a9163-1791">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="a9163-1791">nx_system_initialize</span></span>

<span data-ttu-id="a9163-1792">Inicializa el sistema NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-1792">Initialize NetX System</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1793">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1793">Prototype</span></span>

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="a9163-1794">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1794">Description</span></span>

<span data-ttu-id="a9163-1795">Este servicio inicializa los recursos básicos del sistema NetX como preparación para su uso.</span><span class="sxs-lookup"><span data-stu-id="a9163-1795">This service initializes the basic NetX system resources in preparation for use.</span></span> <span data-ttu-id="a9163-1796">La aplicación debe llamarlo durante la inicialización y antes de que se realice cualquier otra llamada a NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-1796">It should be called by the application during initialization and before any other NetX call are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1797">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1797">Parameters</span></span>

<span data-ttu-id="a9163-1798">Ninguno</span><span class="sxs-lookup"><span data-stu-id="a9163-1798">None</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1799">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1799">Return Values</span></span>

<span data-ttu-id="a9163-1800">Ninguno</span><span class="sxs-lookup"><span data-stu-id="a9163-1800">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1801">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1801">Allowed From</span></span>

<span data-ttu-id="a9163-1802">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="a9163-1802">Initialization, threads, timers, ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1803">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1803">Preemption Possible</span></span>

<span data-ttu-id="a9163-1804">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1804">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1805">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1805">Example</span></span>

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1806">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1806">See Also</span></span>

- <span data-ttu-id="a9163-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="a9163-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="a9163-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="a9163-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="a9163-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="a9163-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="a9163-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span></span>

## <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="a9163-1812">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="a9163-1812">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="a9163-1813">Enlazar el socket TCP del cliente al puerto TCP</span><span class="sxs-lookup"><span data-stu-id="a9163-1813">Bind client TCP socket to TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1814">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1814">Prototype</span></span>

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-1815">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1815">Description</span></span>

<span data-ttu-id="a9163-1816">Este servicio enlaza el socket de cliente TCP creado previamente al puerto TCP especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1816">This service binds the previously created TCP client socket to the specified TCP port.</span></span> <span data-ttu-id="a9163-1817">El intervalo de sockets TCP válidos es de 0 a 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="a9163-1817">Valid TCP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="a9163-1818">Si el puerto TCP especificado no está disponible, el servicio se suspende según la opción de espera proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1818">If the specified TCP port is unavailable, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1819">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1819">Parameters</span></span>

- <span data-ttu-id="a9163-1820">**socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1820">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="a9163-1821">**port**: número de puerto que se va a enlazar (de 1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="a9163-1821">**port** Port number to bind (1 through 0xFFFF).</span></span> <span data-ttu-id="a9163-1822">Si el número de puerto es NX_ANY_PORT (0x0000), la instancia de IP buscará el siguiente puerto disponible y lo utilizará para el enlace.</span><span class="sxs-lookup"><span data-stu-id="a9163-1822">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="a9163-1823">**wait_option**: define cómo se comporta el servicio si el puerto ya está enlazado a otro socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-1823">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="a9163-1824">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-1824">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-1825">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1825">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-1827">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-1827">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1828">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1828">Return Values</span></span>

- <span data-ttu-id="a9163-1829">**NX_SUCCESS**: (0x00) el socket se enlazó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1829">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="a9163-1830">**NX_ALREADY_BOUND**: (0X22) este socket ya está enlazado a otro puerto TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1830">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another TCP port.</span></span>
- <span data-ttu-id="a9163-1831">**NX_PORT_UNAVAILABLE**: (0x23) el puerto ya está enlazado a otro socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-1831">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="a9163-1832">**NX_NO_FREE_PORTS**: (0X45) no hay ningún puerto disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-1832">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="a9163-1833">**NX_WAIT_ABORTED**: (0x1A) una llamada a *tx_thread_wait_abort* ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1833">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="a9163-1834">**NX_INVALID_PORT**: (0x46) el puerto no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1834">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="a9163-1835">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1835">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-1836">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1836">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-1837">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1837">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1838">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1838">Allowed From</span></span>

<span data-ttu-id="a9163-1839">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1839">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1840">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1840">Preemption Possible</span></span>

<span data-ttu-id="a9163-1841">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1841">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1842">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1842">Example</span></span>

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1843">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1843">See Also</span></span>

- <span data-ttu-id="a9163-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="a9163-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="a9163-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="a9163-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="a9163-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="a9163-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="a9163-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="a9163-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-1853">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-1853">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="a9163-1854">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="a9163-1854">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="a9163-1855">Conecta el socket TCP del cliente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1855">Connect client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1856">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1856">Prototype</span></span>

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-1857">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1857">Description</span></span>

<span data-ttu-id="a9163-1858">Este servicio conecta el socket de cliente TCP creado y enlazado previamente al puerto del servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1858">This service connects the previously-created and bound TCP client socket to the specified server's port.</span></span> <span data-ttu-id="a9163-1859">Los puertos de servidor TCP válidos oscilan entre 0 y 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="a9163-1859">Valid TCP server ports range from 0 through 0xFFFF.</span></span> <span data-ttu-id="a9163-1860">Si la conexión no se completa inmediatamente, el servicio se suspende según la opción de espera proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1860">If the connection does not complete immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1861">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1861">Parameters</span></span>

- <span data-ttu-id="a9163-1862">**socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1862">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="a9163-1863">**server_IP**: dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="a9163-1863">**server_ip** Server’s IP address.</span></span>
- <span data-ttu-id="a9163-1864">**server_port**: número de puerto del servidor al que conectarse (de 1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="a9163-1864">**server_port** Server port number to connect to (1 through 0xFFFF).</span></span>
- <span data-ttu-id="a9163-1865">**wait_option**: define cómo se comporta el servicio mientras se establece la conexión.</span><span class="sxs-lookup"><span data-stu-id="a9163-1865">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="a9163-1866">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-1866">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-1867">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-1867">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-1869">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-1869">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1870">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1870">Return Values</span></span>

- <span data-ttu-id="a9163-1871">**NX_SUCCESS**: (0x00) el socket se conectó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1871">**NX_SUCCESS** (0x00) Successful socket connect.</span></span>
- <span data-ttu-id="a9163-1872">**NX_NOT_BOUND**: (0x24) el socket no está enlazado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1872">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="a9163-1873">**NX_NOT_CLOSED**: (0x35) el socket no está en un estado cerrado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1873">**NX_NOT_CLOSED** (0x35) Socket is not in a closed state.</span></span>
- <span data-ttu-id="a9163-1874">**NX_IN_PROGRESS**: (0X37) no se especificó ninguna espera. El intento de conexión está en curso.</span><span class="sxs-lookup"><span data-stu-id="a9163-1874">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="a9163-1875">**NX_INVALID_INTERFACE**: (0x4C) la interfaz proporcionada no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1875">**NX_INVALID_INTERFACE** (0x4C) Invalid interface supplied.</span></span>
- <span data-ttu-id="a9163-1876">**NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-1876">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="a9163-1877">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP del servidor no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-1877">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address.</span></span>
- <span data-ttu-id="a9163-1878">**NX_INVALID_PORT**: (0x46) el puerto no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1878">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="a9163-1879">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1879">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-1880">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1880">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-1881">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1881">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1882">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1882">Allowed From</span></span>

<span data-ttu-id="a9163-1883">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1883">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1884">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1884">Preemption Possible</span></span>

<span data-ttu-id="a9163-1885">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1885">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1886">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1886">Example</span></span>

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1887">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1887">See Also</span></span>

- <span data-ttu-id="a9163-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="a9163-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="a9163-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="a9163-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="a9163-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="a9163-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="a9163-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="a9163-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="a9163-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span></span>
- <span data-ttu-id="a9163-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-1897">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-1897">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="a9163-1898">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="a9163-1898">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="a9163-1899">Obtiene el número de puerto enlazado al socket TCP del cliente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1899">Get port number bound to client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1900">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1900">Prototype</span></span>

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1901">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1901">Description</span></span>

<span data-ttu-id="a9163-1902">Este servicio recupera el número de puerto asociado al socket, lo que resulta útil para buscar el puerto asignado por NetX en situaciones en las que se especificó el elemento NX_ANY_PORT cuando se enlazó el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-1902">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1903">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1903">Parameters</span></span>

- <span data-ttu-id="a9163-1904">**socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1904">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="a9163-1905">**port_ptr**: puntero al destino del número de puerto de devolución.</span><span class="sxs-lookup"><span data-stu-id="a9163-1905">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="a9163-1906">Los números de puerto válidos oscilan entre 1 y 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="a9163-1906">Valid port numbers are (1 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1907">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1907">Return Values</span></span>

- <span data-ttu-id="a9163-1908">**NX_SUCCESS**: (0x00) el socket se enlazó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1908">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="a9163-1909">**NX_NOT_BOUND** (0X24) este socket no está enlazado a ningún puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-1909">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="a9163-1910">**NX_PTR_ERROR**: (0x07) el puntero de socket o de devolución de puerto no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-1910">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="a9163-1911">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1911">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-1912">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1912">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1913">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1913">Allowed From</span></span>

<span data-ttu-id="a9163-1914">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1914">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1915">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1915">Preemption Possible</span></span>

<span data-ttu-id="a9163-1916">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1916">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1917">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1917">Example</span></span>

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1918">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1918">See Also</span></span>

- <span data-ttu-id="a9163-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="a9163-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="a9163-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="a9163-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="a9163-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="a9163-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="a9163-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-1928">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-1928">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="a9163-1929">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="a9163-1929">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="a9163-1930">Desenlaza el socket de cliente TCP del puerto TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1930">Unbind TCP client socket from TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1931">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1931">Prototype</span></span>

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1932">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1932">Description</span></span>

<span data-ttu-id="a9163-1933">Este servicio libera el enlace entre el socket de cliente TCP y un puerto TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1933">This service releases the binding between the TCP client socket and a TCP port.</span></span> <span data-ttu-id="a9163-1934">Si hay otros subprocesos en espera de enlazar otro socket al mismo número de puerto, el primer subproceso suspendido se enlaza a este puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-1934">If there are other threads waiting to bind another socket to the same port number, the first suspended thread is then bound to this port.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1935">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1935">Parameters</span></span>

- <span data-ttu-id="a9163-1936">**socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1936">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1937">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1937">Return Values</span></span>

- <span data-ttu-id="a9163-1938">**NX_SUCCESS**: (0x00) el socket se desenlazó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1938">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="a9163-1939">**NX_NOT_BOUND**: (0x24) el socket no estaba enlazado a ningún puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-1939">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="a9163-1940">**NX_NOT_CLOSED**: (0x35) el socket no se desconectó.</span><span class="sxs-lookup"><span data-stu-id="a9163-1940">**NX_NOT_CLOSED** (0x35) Socket has not been disconnected.</span></span>
- <span data-ttu-id="a9163-1941">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1941">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-1942">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1942">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-1943">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1943">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1944">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1944">Allowed From</span></span>

<span data-ttu-id="a9163-1945">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-1945">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1946">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1946">Preemption Possible</span></span>

<span data-ttu-id="a9163-1947">Sí</span><span class="sxs-lookup"><span data-stu-id="a9163-1947">Yes</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1948">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1948">Example</span></span>

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1949">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1949">See Also</span></span>

- <span data-ttu-id="a9163-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="a9163-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="a9163-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="a9163-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="a9163-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="a9163-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="a9163-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-1959">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-1959">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_enable"></a><span data-ttu-id="a9163-1960">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-1960">nx_tcp_enable</span></span>

<span data-ttu-id="a9163-1961">Habilita el componente TCP de NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-1961">Enable TCP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1962">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1962">Prototype</span></span>

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1963">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1963">Description</span></span>

<span data-ttu-id="a9163-1964">Este servicio habilita el componente de Protocolo de control de transmisión (TCP) de NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-1964">This service enables the Transmission Control Protocol (TCP) component of NetX.</span></span> <span data-ttu-id="a9163-1965">Una vez habilitado, la aplicación puede establecer conexiones TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-1965">After enabled, TCP connections may be established by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1966">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1966">Parameters</span></span>

- <span data-ttu-id="a9163-1967">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1967">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-1968">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-1968">Return Values</span></span>

- <span data-ttu-id="a9163-1969">**NX_SUCCESS**: (0x00) TCP se habilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1969">**NX_SUCCESS** (0x00) Successful TCP enable.</span></span>
- <span data-ttu-id="a9163-1970">**NX_ALREADY_ENABLED**: (0x15) TCP ya está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-1970">**NX_ALREADY_ENABLED** (0x15) TCP is already enabled.</span></span>
- <span data-ttu-id="a9163-1971">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1971">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-1972">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-1972">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-1973">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-1973">Allowed From</span></span>

<span data-ttu-id="a9163-1974">Inicialización, subprocesos, temporizadores</span><span class="sxs-lookup"><span data-stu-id="a9163-1974">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-1975">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-1975">Preemption Possible</span></span>

<span data-ttu-id="a9163-1976">No</span><span class="sxs-lookup"><span data-stu-id="a9163-1976">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-1977">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-1977">Example</span></span>

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-1978">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-1978">See Also</span></span>

- <span data-ttu-id="a9163-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="a9163-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="a9163-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="a9163-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="a9163-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-1988">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-1988">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_free_port_find"></a><span data-ttu-id="a9163-1989">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="a9163-1989">nx_tcp_free_port_find</span></span>

<span data-ttu-id="a9163-1990">Busca el siguiente puerto TCP disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-1990">Find next available TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-1991">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-1991">Prototype</span></span>

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-1992">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-1992">Description</span></span>

<span data-ttu-id="a9163-1993">Este servicio intenta localizar un puerto TCP disponible (sin enlazar) a partir del puerto proporcionado por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a9163-1993">This service attempts to locate a free TCP port (unbound) starting from the application supplied port.</span></span> <span data-ttu-id="a9163-1994">La lógica de búsqueda se ajustará si la búsqueda alcanza el valor de puerto máximo de 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="a9163-1994">The search logic will wrap around if the search happens to reach the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="a9163-1995">Si la búsqueda se realiza correctamente, se devuelve el puerto disponible en la variable a la que apunta *free_port_ptr*.</span><span class="sxs-lookup"><span data-stu-id="a9163-1995">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="a9163-1996">*Se puede llamar a este servicio desde otro subproceso y hacer que se devuelva el mismo puerto. Para evitar esta condición de carrera, es posible que la aplicación quiera proteger este servicio y el enlace de socket de cliente real mediante una exclusión mutua.*</span><span class="sxs-lookup"><span data-stu-id="a9163-1996">*This service can be called from another thread and have the same port returned. To prevent this race condition, the application may wish to place this service and the actual client socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-1997">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-1997">Parameters</span></span>

- <span data-ttu-id="a9163-1998">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-1998">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-1999">**port**: número de puerto en el que debe iniciarse la búsqueda (de 1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="a9163-1999">**port** Port number to start search at (1 through 0xFFFF).</span></span>
- <span data-ttu-id="a9163-2000">**free_port_ptr**: puntero al valor devuelto del puerto disponible de destino.</span><span class="sxs-lookup"><span data-stu-id="a9163-2000">**free_port_ptr** Pointer to the destination free port return value.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2001">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2001">Return Values</span></span>

- <span data-ttu-id="a9163-2002">**NX_SUCCESS**: (0x00) se encontró un puerto disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-2002">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="a9163-2003">**NX_NO_FREE_PORTS**: (0X45) no se encontró ningún puerto disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-2003">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="a9163-2004">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2004">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-2005">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2006">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="a9163-2007">**NX_INVALID_PORT**: (0X46) el número de puerto especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2007">**NX_INVALID_PORT** (0x46) The specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2008">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2008">Allowed From</span></span>

<span data-ttu-id="a9163-2009">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2009">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2010">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2010">Preemption Possible</span></span>

<span data-ttu-id="a9163-2011">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2011">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2012">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2012">Example</span></span>

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2013">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2013">See Also</span></span>

- <span data-ttu-id="a9163-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="a9163-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="a9163-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="a9163-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-2023">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2023">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_info_get"></a><span data-ttu-id="a9163-2024">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-2024">nx_tcp_info_get</span></span>

<span data-ttu-id="a9163-2025">Recupera información acerca de las actividades de TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2025">Retrieve information about TCP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2026">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2026">Prototype</span></span>

```C
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```

### <a name="description"></a><span data-ttu-id="a9163-2027">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2027">Description</span></span>

<span data-ttu-id="a9163-2028">Este servicio recupera información sobre las actividades de TCP de la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2028">This service retrieves information about TCP activities for the specified IP instance.</span></span>

<span data-ttu-id="a9163-2029">*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2029">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2030">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2030">Parameters</span></span>

- <span data-ttu-id="a9163-2031">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2031">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-2032">**tcp_packets_sent**: puntero al destino para el número total de paquetes TCP enviados.</span><span class="sxs-lookup"><span data-stu-id="a9163-2032">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent.</span></span>
- <span data-ttu-id="a9163-2033">**tcp_bytes_sent**: puntero al destino para el número total de bytes TCP enviados.</span><span class="sxs-lookup"><span data-stu-id="a9163-2033">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent.</span></span>
- <span data-ttu-id="a9163-2034">**tcp_packets_received**: puntero al destino del número total de paquetes TCP recibidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2034">**tcp_packets_received** Pointer to destination of the total number of TCP packets received.</span></span>
- <span data-ttu-id="a9163-2035">**tcp_bytes_received**: puntero al destino del número total de bytes TCP recibidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2035">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received.</span></span>
- <span data-ttu-id="a9163-2036">**tcp_invalid_packets**: puntero al destino del número total de paquetes TCP no válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2036">**tcp_invalid_packets** Pointer to destination of the total number of invalid TCP packets.</span></span>
- <span data-ttu-id="a9163-2037">**tcp_receive_packets_dropped**: puntero al destino del número total de paquetes TCP recibidos anulados.</span><span class="sxs-lookup"><span data-stu-id="a9163-2037">**tcp_receive_packets_dropped** Pointer to destination of the total number of TCP receive packets dropped.</span></span>
- <span data-ttu-id="a9163-2038">**tcp_checksum_errors**: puntero al destino del número total de paquetes TCP con errores de suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="a9163-2038">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors.</span></span>
- <span data-ttu-id="a9163-2039">**tcp_connections**: puntero al destino del número total de conexiones TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2039">**tcp_connections** Pointer to destination of the total number of TCP connections.</span></span>
- <span data-ttu-id="a9163-2040">**tcp_disconnections**: puntero al destino del número total de desconexiones TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2040">**tcp_disconnections** Pointer to destination of the total number of TCP disconnections.</span></span>
- <span data-ttu-id="a9163-2041">**tcp_connections_dropped**: puntero al destino del número total de conexiones TCP anuladas.</span><span class="sxs-lookup"><span data-stu-id="a9163-2041">**tcp_connections_dropped** Pointer to destination of the total number of TCP connections dropped.</span></span>
- <span data-ttu-id="a9163-2042">**tcp_retransmit_packets**: puntero al destino del número total de paquetes TCP retransmitidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2042">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packets retransmitted.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2043">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2043">Return Values</span></span>

- <span data-ttu-id="a9163-2044">**NX_SUCCESS**: (0x00) la información de TCP se recuperó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2044">**NX_SUCCESS** (0x00) Successful TCP information retrieval.</span></span>
- <span data-ttu-id="a9163-2045">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2045">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-2046">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2046">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2047">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2047">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2048">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2048">Allowed From</span></span>

<span data-ttu-id="a9163-2049">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2049">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2050">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2050">Preemption Possible</span></span>

<span data-ttu-id="a9163-2051">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2051">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2052">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2052">Example</span></span>

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
status = nx_tcp_info_get(&ip_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_invalid_packets,
    &tcp_receive_packets_dropped,
    &tcp_checksum_errors,
    &tcp_connections,
    &tcp_disconnections
    &tcp_connections_dropped,
    &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2053">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2053">See Also</span></span>

- <span data-ttu-id="a9163-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="a9163-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="a9163-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="a9163-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-2063">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2063">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="a9163-2064">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="a9163-2064">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="a9163-2065">Acepta la conexión TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2065">Accept TCP connection</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2066">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2066">Prototype</span></span>

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-2067">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2067">Description</span></span>

<span data-ttu-id="a9163-2068">Este servicio acepta (o se prepara para aceptar) una solicitud de conexión de socket de cliente TCP para un puerto que se configuró previamente para la escucha.</span><span class="sxs-lookup"><span data-stu-id="a9163-2068">This service accepts (or prepares to accept) a TCP client socket connection request for a port that was previously set up for listening.</span></span> <span data-ttu-id="a9163-2069">Este servicio se puede llamar inmediatamente después de que la aplicación llame al servicio de escucha o de reescucha, o después de que se llame a la rutina de devolución de llamada de escucha cuando la conexión de cliente existe realmente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2069">This service may be called immediately after the application calls the listen or re-listen service, or after the listen callback routine is called when the client connection is actually present.</span></span> <span data-ttu-id="a9163-2070">Si no se puede establecer una conexión de inmediato, el servicio se suspende según la opción de espera proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2070">If a connection cannot not be established right away, the service suspends according to the supplied wait option.</span></span>

<span data-ttu-id="a9163-2071">*La aplicación debe llamar a **nx_tcp_server_socket_unaccept** cuando ya no se necesite la conexión para quitar el enlace del socket de servidor al puerto del servidor.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2071">*The application must call **nx_tcp_server_socket_unaccept** after the connection is no longer needed to remove the server socket's binding to the server port.*</span></span>

<span data-ttu-id="a9163-2072">*Se llama a las rutinas de devolución de llamada de la aplicación desde el subproceso auxiliar de IP.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2072">*Application callback routines are called from within the IP's helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2073">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2073">Parameters</span></span>

- <span data-ttu-id="a9163-2074">**socket_ptr**: puntero al bloque de control del socket de servidor TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2074">**socket_ptr** Pointer to the TCP server socket control block.</span></span>
- <span data-ttu-id="a9163-2075">**wait_option**: define cómo se comporta el servicio mientras se establece la conexión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2075">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="a9163-2076">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-2076">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-2077">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2077">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-2079">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-2079">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>


### <a name="return-values"></a><span data-ttu-id="a9163-2080">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2080">Return Values</span></span>
- <span data-ttu-id="a9163-2081">**NX_SUCCESS**: (0x00) el socket de servidor TCP (conexión pasiva) se aceptó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2081">**NX_SUCCESS** (0x00) Successful TCP server socket accept (passive connect).</span></span>
- <span data-ttu-id="a9163-2082">**NX_NOT_LISTEN_STATE**: (0X36) el socket de servidor proporcionado no está en un estado de escucha.</span><span class="sxs-lookup"><span data-stu-id="a9163-2082">**NX_NOT_LISTEN_STATE** (0x36) The server socket supplied is not in a listen state.</span></span>
- <span data-ttu-id="a9163-2083">**NX_IN_PROGRESS**: (0X37) no se especificó ninguna espera. El intento de conexión está en curso.</span><span class="sxs-lookup"><span data-stu-id="a9163-2083">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="a9163-2084">**NX_WAIT_ABORTED**: (0x1A) una llamada a *tx_thread_wait_abort* ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2084">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="a9163-2085">**NX_PTR_ERROR**: (0x07) error del puntero de socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2085">**NX_PTR_ERROR** (0x07) Socket pointer error.</span></span>
- <span data-ttu-id="a9163-2086">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2086">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2087">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2087">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2088">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2088">Allowed From</span></span>

<span data-ttu-id="a9163-2089">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2089">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2090">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2090">Preemption Possible</span></span>

<span data-ttu-id="a9163-2091">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2091">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2092">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2092">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;
    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
                message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
            again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="a9163-2093">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2093">See Also</span></span>

- <span data-ttu-id="a9163-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="a9163-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="a9163-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-2103">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2103">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="a9163-2104">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="a9163-2104">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="a9163-2105">Habilita la escucha para la conexión de cliente en el puerto TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2105">Enable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2106">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2106">Prototype</span></span>

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a><span data-ttu-id="a9163-2107">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2107">Description</span></span>

<span data-ttu-id="a9163-2108">Este servicio habilita la escucha de una solicitud de conexión de cliente en el puerto TCP especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2108">This service enables listening for a client connection request on the specified TCP port.</span></span> <span data-ttu-id="a9163-2109">Cuando se recibe una solicitud de conexión de cliente, el socket del servidor proporcionado se enlaza al puerto especificado y se llama a la función de devolución de llamada de escucha proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2109">When a client connection request is received, the supplied server socket is bound to the specified port and the supplied listen callback function is called.</span></span>

<span data-ttu-id="a9163-2110">El procesamiento de la rutina de devolución de llamada de escucha depende completamente de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a9163-2110">The listen callback routine's processing is completely up to the application.</span></span> <span data-ttu-id="a9163-2111">Puede contener lógica para reactivar un subproceso de aplicación que posteriormente realiza una operación de aceptación.</span><span class="sxs-lookup"><span data-stu-id="a9163-2111">It may contain logic to wake up an application thread that subsequently performs an accept operation.</span></span> <span data-ttu-id="a9163-2112">Si la aplicación ya tiene un subproceso suspendido en el procesamiento de aceptación para este socket, es posible que la rutina de devolución de llamada de escucha no sea necesaria.</span><span class="sxs-lookup"><span data-stu-id="a9163-2112">If the application already has a thread suspended on accept processing for this socket, the listen callback routine may not be needed.</span></span>

<span data-ttu-id="a9163-2113">Si la aplicación quiere controlar conexiones de cliente adicionales en el mismo puerto, se debe llamar a ***nx_tcp_server_socket_relisten*** con un socket disponible (un socket en estado CLOSED) para la conexión siguiente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2113">If the application wishes to handle additional client connections on the same port, the ***nx_tcp_server_socket_relisten*** must be called with an available socket (a socket in the CLOSED state) for the next connection.</span></span> <span data-ttu-id="a9163-2114">Hasta que se llame al servicio de reescucha, las conexiones de cliente adicionales se ponen en cola.</span><span class="sxs-lookup"><span data-stu-id="a9163-2114">Until the re-listen service is called, additional client connections are queued.</span></span> <span data-ttu-id="a9163-2115">Cuando se supera la profundidad máxima de la cola, se anula la solicitud de conexión más antigua para poner en cola la nueva solicitud de conexión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2115">When the maximum queue depth is exceeded, the oldest connection request is dropped in favor of queuing the new connection request.</span></span> <span data-ttu-id="a9163-2116">Este servicio especifica la profundidad máxima de la cola.</span><span class="sxs-lookup"><span data-stu-id="a9163-2116">The maximum queue depth is specified by this service.</span></span>

<span data-ttu-id="a9163-2117">*Se llama a las rutinas de devolución de llamada de la aplicación desde el subproceso auxiliar de IP.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2117">*Application callback routines are called from the internal IP helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2118">Parameters</span></span>

- <span data-ttu-id="a9163-2119">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2119">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-2120">**port**: número de puerto en el que se realiza la escucha (de 1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="a9163-2120">**port** Port number to listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="a9163-2121">**socket_ptr**: puntero al socket que se va a utilizar para la conexión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2121">**socket_ptr** Pointer to socket to use for the connection.</span></span>
- <span data-ttu-id="a9163-2122">**listen_queue_size**: número de solicitudes de conexión de cliente que se pueden poner en cola.</span><span class="sxs-lookup"><span data-stu-id="a9163-2122">**listen_queue_size** Number of client connection requests that can be queued.</span></span>
- <span data-ttu-id="a9163-2123">**listen_callback**: función de aplicación a la que se llamará cuando se reciba la conexión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2123">**listen_callback** Application function to call when the connection is received.</span></span> <span data-ttu-id="a9163-2124">Si se especifica un valor NULL, la característica de devolución de llamada de escucha se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="a9163-2124">If a NULL is specified, the listen callback feature is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2125">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2125">Return Values</span></span>

- <span data-ttu-id="a9163-2126">**NX_SUCCESS**: (0x00) la escucha del puerto TCP se habilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2126">**NX_SUCCESS** (0x00) Successful TCP port listen enable.</span></span>
- <span data-ttu-id="a9163-2127">**NX_MAX_LISTEN**: (0X33) no hay más estructuras de solicitud de escucha disponibles.</span><span class="sxs-lookup"><span data-stu-id="a9163-2127">**NX_MAX_LISTEN** (0x33) No more listen request structures are available.</span></span> <span data-ttu-id="a9163-2128">La constante NX_MAX_LISTEN_REQUESTS en nx_api.h define el número de solicitudes de escucha activas posibles.</span><span class="sxs-lookup"><span data-stu-id="a9163-2128">The constant NX_MAX_LISTEN_REQUESTS in nx_api.h defines how many active listen requests are possible.</span></span>
- <span data-ttu-id="a9163-2129">**NX_NOT_CLOSED**: (0X35) el socket de servidor proporcionado no está en estado cerrado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2129">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="a9163-2130">**NX_ALREADY_BOUND**: (0X22) el socket de servidor proporcionado ya está enlazado a un puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-2130">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="a9163-2131">**NX_DUPLICATE_LISTEN**: (0x34) ya existe una solicitud de escucha activa para este puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-2131">**NX_DUPLICATE_LISTEN** (0x34) There is already an active listen request for this port.</span></span>
- <span data-ttu-id="a9163-2132">**NX_INVALID_PORT**: (0x46) el puerto especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2132">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="a9163-2133">**NX_PTR_ERROR**: (0X07) la IP o el puntero de socket no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="a9163-2134">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2135">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2136">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2136">Allowed From</span></span>

<span data-ttu-id="a9163-2137">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2138">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2138">Preemption Possible</span></span>

<span data-ttu-id="a9163-2139">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2139">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2140">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2140">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket.
        This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created
        and the link is enabled "my_pool" packet pool has already
        been created.
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
        Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

    /* Wait for 200 ticks for the client socket connection
        to complete. */
    status = nx_tcp_server_socket_accept(&server_socket, 200);

    /* Check for a successful connection. */
    if (status == NX_SUCCESS)
    {
        /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
        nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
            NX_WAIT_FOREVER);

        /* Place "Hello_and_Goodbye" in the packet. */
        nx_packet_data_append(my_packet, "Hello_and_Goodbye",
            sizeof("Hello_and_Goodbye"),
            &my_pool,
            NX_WAIT_FOREVER);

        /* Send "Hello_and_Goodbye" to client. */
        nx_tcp_socket_send(&server_socket, my_packet, 200);

        /* Check for an error. */
        if (status)
        {
            /* Error, release the packet. */
            nx_packet_release(my_packet);
        }
        /* Now disconnect the server socket from the client. */
        nx_tcp_socket_disconnect(&server_socket, 200);
    }

    /* Unaccept the server socket. Note that unaccept is called
        even if disconnect or accept fails. */
    nx_tcp_server_socket_unaccept(&server_socket);

    /* Setup server socket for listening with this socket
    again. */
    nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
}

/* We are now done so unlisten on server port 12. */
nx_tcp_server_socket_unlisten(&my_ip, 12);

/* Delete the server socket. */
nx_tcp_socket_delete(&server_socket);
```

### <a name="see-also"></a><span data-ttu-id="a9163-2141">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2141">See Also</span></span>

- <span data-ttu-id="a9163-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="a9163-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="a9163-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-2151">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2151">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="a9163-2152">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="a9163-2152">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="a9163-2153">Reescucha la conexión de cliente en el puerto TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2153">Re-listen for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2154">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2154">Prototype</span></span>

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-2155">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2155">Description</span></span>

<span data-ttu-id="a9163-2156">Se llama a este servicio después de que se haya recibido una conexión en un puerto que se configuró anteriormente para la escucha.</span><span class="sxs-lookup"><span data-stu-id="a9163-2156">This service is called after a connection has been received on a port that was setup previously for listening.</span></span> <span data-ttu-id="a9163-2157">La finalidad principal de este servicio es proporcionar un nuevo socket de servidor para la siguiente conexión de cliente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2157">The main purpose of this service is to provide a new server socket for the next client connection.</span></span> <span data-ttu-id="a9163-2158">Si una solicitud de conexión se pone en cola, la conexión se procesará inmediatamente durante esta llamada de servicio.</span><span class="sxs-lookup"><span data-stu-id="a9163-2158">If a connection request is queued, the connection will be processed immediately during this service call.</span></span>

<span data-ttu-id="a9163-2159">*También se llama a la misma rutina de devolución de llamada especificada por la solicitud de escucha original cuando existe una conexión para este nuevo socket de servidor.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2159">*The same callback routine specified by the original listen request is also called when a connection is present for this new server socket.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2160">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2160">Parameters</span></span>

- <span data-ttu-id="a9163-2161">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2161">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-2162">**port**: número de puerto en el que se realiza la reescucha (de 1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="a9163-2162">**port** Port number to re-listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="a9163-2163">**socket_ptr**: socket que se va a usar para la siguiente conexión de cliente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2163">**socket_ptr** Socket to use for the next client connection.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2164">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2164">Return Values</span></span>
- <span data-ttu-id="a9163-2165">**NX_SUCCESS**: (0x00) la reescucha del puerto TCP se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2165">**NX_SUCCESS** (0x00) Successful TCP port re-listen.</span></span>
- <span data-ttu-id="a9163-2166">**NX_NOT_CLOSED**: (0X35) el socket de servidor proporcionado no está en estado cerrado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2166">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="a9163-2167">**NX_ALREADY_BOUND**: (0X22) el socket de servidor proporcionado ya está enlazado a un puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-2167">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="a9163-2168">**NX_INVALID_RELISTEN**: (0x47) ya hay un puntero de socket válido para este puerto o el puerto especificado no tiene ninguna solicitud de escucha activa.</span><span class="sxs-lookup"><span data-stu-id="a9163-2168">**NX_INVALID_RELISTEN** (0x47) There is already a valid socket pointer for this port or the port specified does not have a listen request active.</span></span>
- <span data-ttu-id="a9163-2169">**NX_CONNECTION_PENDING**: (0X48) igual que NX_SUCCESS, salvo que había una solicitud de conexión en cola y se procesó durante esta llamada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2169">**NX_CONNECTION_PENDING** (0x48) Same as NX_SUCCESS, except there was a queued connection request and it was processed during this call.</span></span>
- <span data-ttu-id="a9163-2170">**NX_INVALID_PORT**: (0x46) el puerto especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2170">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="a9163-2171">**NX_PTR_ERROR** (0x07) Dirección IP o puntero de devolución de llamada de escucha no válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2171">**NX_PTR_ERROR** (0x07) Invalid IP or listen callback pointer.</span></span>
- <span data-ttu-id="a9163-2172">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2172">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2173">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2173">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2174">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2174">Allowed From</span></span>

<span data-ttu-id="a9163-2175">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2175">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2176">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2176">Preemption Possible</span></span>

<span data-ttu-id="a9163-2177">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2177">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2178">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2178">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
    }

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
    "port_12_semaphore" has already been created with an initial
        count of 0.
        "my_ip" has already been created and the link is enabled.
        "my_pool" packet pool has already been created. */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);
    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
        complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is
        called even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
        again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="a9163-2179">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2179">See Also</span></span>

- <span data-ttu-id="a9163-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="a9163-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="a9163-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="a9163-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-2189">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2189">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="a9163-2190">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="a9163-2190">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="a9163-2191">Quita la asociación de un socket con el puerto de escucha.</span><span class="sxs-lookup"><span data-stu-id="a9163-2191">Remove socket association with listening port</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2192">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2192">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-2193">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2193">Description</span></span>

<span data-ttu-id="a9163-2194">Este servicio quita la asociación entre este socket de servidor y el puerto del servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2194">This service removes the association between this server socket and the specified server port.</span></span> <span data-ttu-id="a9163-2195">La aplicación debe llamar a este servicio después de una desconexión o después de una llamada de aceptación incorrecta.</span><span class="sxs-lookup"><span data-stu-id="a9163-2195">The application must call this service after a disconnection or after an unsuccessful accept call.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2196">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2196">Parameters</span></span>

- <span data-ttu-id="a9163-2197">**socket_ptr**: puntero a la instancia de socket de servidor de configuración anterior.</span><span class="sxs-lookup"><span data-stu-id="a9163-2197">**socket_ptr** Pointer to previously setup server socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2198">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2198">Return Values</span></span>

- <span data-ttu-id="a9163-2199">**NX_SUCCESS**: (0x00) la operación de no aceptación del socket de servidor se completó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2199">**NX_SUCCESS** (0x00) Successful server socket unaccept.</span></span>
- <span data-ttu-id="a9163-2200">**NX_NOT_LISTEN_STATE**: (0x36) el socket del servidor está en un estado inadecuado y probablemente no esté desconectado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2200">**NX_NOT_LISTEN_STATE** (0x36) Server socket is in an improper state, and is probably not disconnected.</span></span>
- <span data-ttu-id="a9163-2201">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2201">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2202">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2202">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2203">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2203">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2204">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2204">Allowed From</span></span>

<span data-ttu-id="a9163-2205">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2206">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2206">Preemption Possible</span></span>

<span data-ttu-id="a9163-2207">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2207">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2208">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2208">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
        */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request
            is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet,
                "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called even
            if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="a9163-2209">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2209">See Also</span></span>

- <span data-ttu-id="a9163-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,</span></span>
- <span data-ttu-id="a9163-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="a9163-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="a9163-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="a9163-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-2218">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2218">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="a9163-2219">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="a9163-2219">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="a9163-2220">Deshabilita la escucha para la conexión de cliente en el puerto TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2220">Disable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2221">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2221">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a><span data-ttu-id="a9163-2222">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2222">Description</span></span>

<span data-ttu-id="a9163-2223">Este servicio deshabilita la escucha de una solicitud de conexión de cliente en el puerto TCP especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2223">This service disables listening for a client connection request on the specified TCP port.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2224">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2224">Parameters</span></span>

- <span data-ttu-id="a9163-2225">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2225">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-2226">**port**: número de puerto para deshabilitar la escucha (de 0 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="a9163-2226">**port** Number of port to disable listening (0 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2227">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2227">Return Values</span></span>

- <span data-ttu-id="a9163-2228">**NX_SUCCESS**: (0x00) la escucha de puerto TCP se deshabilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2228">**NX_SUCCESS** (0x00) Successful TCP listen disable.</span></span>
- <span data-ttu-id="a9163-2229">**NX_ENTRY_NOT_FOUND**: (0x16) no se ha habilitó la escucha para el puerto especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2229">**NX_ENTRY_NOT_FOUND** (0x16) Listening was not enabled for the specified port.</span></span>
- <span data-ttu-id="a9163-2230">**NX_INVALID_PORT**: (0x46) el puerto especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2230">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="a9163-2231">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2231">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-2232">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2232">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2233">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2233">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2234">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2234">Allowed From</span></span>

<span data-ttu-id="a9163-2235">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2235">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2236">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2236">Preemption Possible</span></span>

<span data-ttu-id="a9163-2237">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2237">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2238">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2238">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request is
            present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"), &my_pool,
                NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }
            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }
        /* Unaccept the server socket. Note that unaccept is called even if
        disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="a9163-2239">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2239">See Also</span></span>

- <span data-ttu-id="a9163-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="a9163-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="a9163-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="a9163-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-2249">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2249">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="a9163-2250">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="a9163-2250">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="a9163-2251">Recupera el número de bytes disponibles para la recuperación</span><span class="sxs-lookup"><span data-stu-id="a9163-2251">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2252">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2252">Prototype</span></span>

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="a9163-2253">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2253">Description</span></span>

<span data-ttu-id="a9163-2254">Este servicio obtiene el número de bytes disponibles para la recuperación en el socket TCP especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2254">This service obtains the number of bytes available for retrieval in the specified TCP socket.</span></span> <span data-ttu-id="a9163-2255">Tenga en cuenta que el socket TCP ya debe estar conectado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2255">Note that the TCP socket must already be connected.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2256">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2256">Parameters</span></span>

- <span data-ttu-id="a9163-2257">**socket_ptr**: puntero al socket TCP creado y conectado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2257">**socket_ptr** Pointer to previously created and connected TCP socket.</span></span>
- <span data-ttu-id="a9163-2258">**bytes_available**: puntero al destino para los bytes disponibles.</span><span class="sxs-lookup"><span data-stu-id="a9163-2258">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2259">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2259">Return Values</span></span>

- <span data-ttu-id="a9163-2260">**NX_SUCCESS**: (0x00) el servicio se ejecuta correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2260">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="a9163-2261">El número de bytes disponibles para la lectura se devuelve al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2261">Number of bytes available for read is returned to the caller.</span></span>
- <span data-ttu-id="a9163-2262">**NX_NOT_CONNECTED**: (0x38) el socket no está en estado conectado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2262">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="a9163-2263">**NX_PTR_ERROR**: (0x07) los punteros no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2263">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="a9163-2264">**NX_NOT_ENABLED**: (0x14) el TCP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2264">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="a9163-2265">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2265">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2266">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2266">Allowed From</span></span>

<span data-ttu-id="a9163-2267">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2267">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2268">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2268">Preemption Possible</span></span>

<span data-ttu-id="a9163-2269">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2269">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2270">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2270">Example</span></span>

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2271">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2271">See Also</span></span>

- <span data-ttu-id="a9163-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="a9163-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="a9163-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="a9163-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-2281">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2281">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_create"></a><span data-ttu-id="a9163-2282">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="a9163-2282">nx_tcp_socket_create</span></span>

<span data-ttu-id="a9163-2283">Crea un cliente TCP o un socket de servidor</span><span class="sxs-lookup"><span data-stu-id="a9163-2283">Create TCP client or server socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2284">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2284">Prototype</span></span>

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="a9163-2285">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2285">Description</span></span>

<span data-ttu-id="a9163-2286">Este servicio crea un cliente TCP o un socket de servidor para la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2286">This service creates a TCP client or server socket for the specified IP instance.</span></span>

<span data-ttu-id="a9163-2287">*Se llama a las rutinas de devolución de llamada de aplicación desde el subproceso asociado con esta instancia de IP.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2287">*Application callback routines are called from the thread associated with this IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2288">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2288">Parameters</span></span>

- <span data-ttu-id="a9163-2289">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2289">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-2290">**socket_ptr**: puntero al nuevo bloque de control de socket TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2290">**socket_ptr** Pointer to new TCP socket control block.</span></span>
- <span data-ttu-id="a9163-2291">**name**: nombre de la aplicación para este socket TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2291">**name** Application name for this TCP socket.</span></span>
- <span data-ttu-id="a9163-2292">**type_of_service**: define el tipo de servicio para la transmisión. Los valores válidos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="a9163-2292">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>

- <span data-ttu-id="a9163-2293">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2293">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="a9163-2294">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2294">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="a9163-2295">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2295">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="a9163-2296">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2296">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="a9163-2297">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2297">NX_IP_MIN_COST (0x00020000)</span></span>

- <span data-ttu-id="a9163-2298">**fragment**: especifica si se permite o no la fragmentación de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2298">**fragment**  Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="a9163-2299">Si se especifica NX_FRAGMENT_OKAY (0X0), se permite la fragmentación de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2299">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="a9163-2300">Si se especifica NX_DONT_FRAGMENT (0x4000), se deshabilita la fragmentación de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2300">If  NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="a9163-2301">**time_to_live**: especifica el valor de 8 bits que define el número de enrutadores que puede autorizar este paquete antes de que desaparezca.</span><span class="sxs-lookup"><span data-stu-id="a9163-2301">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="a9163-2302">El elemento NX_IP_TIME_TO_LIVE especifica el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2302">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="a9163-2303">**window_size**: define el número máximo de bytes permitidos en la cola de recepción de este socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2303">**window_size** Defines the maximum number of bytes allowed in the receive queue for this socket</span></span>
- <span data-ttu-id="a9163-2304">**urgent_data_callback**: función de aplicación a la que se llama cada vez que se detectan datos urgentes en el flujo de recepción.</span><span class="sxs-lookup"><span data-stu-id="a9163-2304">**urgent_data_callback** Application function that is called whenever urgent data is detected in the receive stream.</span></span> <span data-ttu-id="a9163-2305">Si este valor es NX_NULL, se omiten los datos urgentes.</span><span class="sxs-lookup"><span data-stu-id="a9163-2305">If this value is NX_NULL, urgent data is ignored.</span></span>
- <span data-ttu-id="a9163-2306">**disconnect_callback**: función de aplicación a la que se llama siempre que el socket emite una desconexión en el otro extremo de la conexión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2306">**disconnect_callback** Application function that is called whenever a disconnect is issued by the socket at the other end of the connection.</span></span> <span data-ttu-id="a9163-2307">Si este valor es NX_NULL, la función de devolución de llamada de desconexión se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="a9163-2307">If this value is NX_NULL, the disconnect callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2308">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2308">Return Values</span></span>
- <span data-ttu-id="a9163-2309">**NX_SUCCESS**: (0x00) el socket de cliente TCP se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2309">**NX_SUCCESS** (0x00) Successful TCP client socket create.</span></span>
- <span data-ttu-id="a9163-2310">**NX_OPTION_ERROR**: (0x0A) el tipo de servicio, el fragmento, el tamaño de la ventana o la opción de período de vida no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2310">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, invalid window size, or time-tolive option.</span></span>
- <span data-ttu-id="a9163-2311">**NX_PTR_ERROR**: (0X07) la IP o el puntero de socket no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2311">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="a9163-2312">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2312">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2313">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2313">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2314">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2314">Allowed From</span></span>

<span data-ttu-id="a9163-2315">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2315">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2316">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2316">Preemption Possible</span></span>

<span data-ttu-id="a9163-2317">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2317">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2318">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2318">Example</span></span>

```C
/* Create a TCP client socket on the previously created IP instance,
    with normal delivery, IP fragmentation enabled, 0x80 time to
    live, a 200-byte receive window, no urgent callback routine, and
    the "client_disconnect" routine to handle disconnection initiated
    from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
    "Client Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY,
    0x80, 200, NX_NULL
    client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
    to be bound. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2319">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2319">See Also</span></span>

- <span data-ttu-id="a9163-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="a9163-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="a9163-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="a9163-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-2329">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2329">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_delete"></a><span data-ttu-id="a9163-2330">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-2330">nx_tcp_socket_delete</span></span>

<span data-ttu-id="a9163-2331">Elimina un socket TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2331">Delete TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2332">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2332">Prototype</span></span>

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-2333">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2333">Description</span></span>

<span data-ttu-id="a9163-2334">Este servicio elimina un socket TCP creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2334">This service deletes a previously created TCP socket.</span></span> <span data-ttu-id="a9163-2335">Si el socket sigue enlazado o conectado, el servicio devuelve un código de error.</span><span class="sxs-lookup"><span data-stu-id="a9163-2335">If the socket is still bound or connected, the service returns an error code.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2336">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2336">Parameters</span></span>

- <span data-ttu-id="a9163-2337">**socket_ptr**: socket TCP creado previamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2337">**socket_ptr** Previously created TCP socket</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2338">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2338">Return Values</span></span>

- <span data-ttu-id="a9163-2339">**NX_SUCCESS**: (0x00) el socket se eliminó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2339">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="a9163-2340">**NX_NOT_CREATED**: (0x27) no se creó el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2340">**NX_NOT_CREATED** (0x27) Socket was not created.</span></span>
- <span data-ttu-id="a9163-2341">**NX_STILL_BOUND**: (0x42) el socket sigue estando enlazado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2341">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="a9163-2342">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2342">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2343">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2343">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2344">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2344">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2345">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2345">Allowed From</span></span>

<span data-ttu-id="a9163-2346">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2346">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2347">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2347">Preemption Possible</span></span>

<span data-ttu-id="a9163-2348">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2348">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2349">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2349">Example</span></span>

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2350">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2350">See Also</span></span>

- <span data-ttu-id="a9163-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="a9163-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="a9163-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="a9163-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="a9163-2360">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2360">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="a9163-2361">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="a9163-2361">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="a9163-2362">Desconecta conexiones de socket de cliente y servidor.</span><span class="sxs-lookup"><span data-stu-id="a9163-2362">Disconnect client and server socket connections</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2363">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2363">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-2364">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2364">Description</span></span>

<span data-ttu-id="a9163-2365">Este servicio desconecta una conexión de socket de servidor o cliente establecida.</span><span class="sxs-lookup"><span data-stu-id="a9163-2365">This service disconnects an established client or server socket connection.</span></span> <span data-ttu-id="a9163-2366">Una desconexión de un socket de servidor debe ir seguida de una solicitud de desaceptación, mientras que un socket de cliente que está desconectado se deja en un estado listo para otra solicitud de conexión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2366">A disconnect of a server socket should be followed by an unaccept request, while a client socket that is disconnected is left in a state ready for another connection request.</span></span> <span data-ttu-id="a9163-2367">Si el proceso de desconexión no puede finalizar inmediatamente, el servicio se suspende según la opción de espera proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2367">If the disconnect process cannot finish immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2368">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2368">Parameters</span></span>

- <span data-ttu-id="a9163-2369">**socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2369">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="a9163-2370">**wait_option**: define cómo se comporta el servicio mientras la desconexión está en curso.</span><span class="sxs-lookup"><span data-stu-id="a9163-2370">**wait_option** Defines how the service behaves while the disconnection is in progress.</span></span> <span data-ttu-id="a9163-2371">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-2371">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-2372">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2372">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-2374">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-2374">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2375">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2375">Return Values</span></span>

- <span data-ttu-id="a9163-2376">**NX_SUCCESS**: (0x00) el socket se desconectó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2376">**NX_SUCCESS** (0x00) Successful socket disconnect.</span></span>
- <span data-ttu-id="a9163-2377">**NX_NOT_CONNECTED**: (0x38) el socket especificado no está conectado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2377">**NX_NOT_CONNECTED** (0x38) Specified socket is not connected.</span></span>
- <span data-ttu-id="a9163-2378">**NX_IN_PROGRESS**: (0x37) la desconexión está en curso; no se especificó ninguna espera.</span><span class="sxs-lookup"><span data-stu-id="a9163-2378">**NX_IN_PROGRESS** (0x37) Disconnect is in progress, no wait was specified.</span></span>
- <span data-ttu-id="a9163-2379">**NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2379">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="a9163-2380">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2380">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2381">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2381">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2382">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2382">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2383">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2383">Allowed From</span></span>

<span data-ttu-id="a9163-2384">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2384">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2385">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2385">Preemption Possible</span></span>

<span data-ttu-id="a9163-2386">Sí</span><span class="sxs-lookup"><span data-stu-id="a9163-2386">Yes</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2387">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2387">Example</span></span>

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2388">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2388">See Also</span></span>

- <span data-ttu-id="a9163-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="a9163-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="a9163-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="a9163-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="a9163-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect_complete_notify"></a><span data-ttu-id="a9163-2398">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="a9163-2398">nx_tcp_socket_disconnect_complete_notify</span></span>

<span data-ttu-id="a9163-2399">Instala la función de devolución de llamada de notificación de realización de la desconexión de TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2399">Install TCP disconnect complete notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2400">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2400">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="a9163-2401">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2401">Description</span></span>

<span data-ttu-id="a9163-2402">Este servicio registra una función de devolución de llamada que se invoca después de que se complete una operación de desconexión de socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2402">This service registers a callback function which is invoked after a socket disconnect operation is completed.</span></span> <span data-ttu-id="a9163-2403">La función de devolución de llamada de realización de la desconexión de socket TCP está disponible si NetX se crea con la opción siguiente definida:</span><span class="sxs-lookup"><span data-stu-id="a9163-2403">The TCP socket disconnect complete callback function is available if NetX is built with the option</span></span>

- <span data-ttu-id="a9163-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT***</span><span class="sxs-lookup"><span data-stu-id="a9163-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2405">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2405">Parameters</span></span>

- <span data-ttu-id="a9163-2406">**socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2406">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="a9163-2407">**tcp_disconnect_complete_notify**: función de devolución de llamada que se va a instalar.</span><span class="sxs-lookup"><span data-stu-id="a9163-2407">**tcp_disconnect_complete_notify** The callback function to be installed.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2408">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2408">Return Values</span></span>
- <span data-ttu-id="a9163-2409">**NX_SUCCESS**: (0x00) la función de devolución de llamada se ha registrado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2409">**NX_SUCCESS** (0x00) Successfully registered the callback function.</span></span>
- <span data-ttu-id="a9163-2410">**NX_NOT_SUPPORTED**: (0X4B) la característica de notificación extendida no está integrada en la biblioteca de NetX</span><span class="sxs-lookup"><span data-stu-id="a9163-2410">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="a9163-2411">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2411">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2412">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2412">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2413">**NX_NOT_ENABLED**: (0x14) la característica de TCP no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2413">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2414">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2414">Allowed From</span></span>

<span data-ttu-id="a9163-2415">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2415">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2416">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2416">Preemption Possible</span></span>

<span data-ttu-id="a9163-2417">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2417">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2418">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2418">Example</span></span>

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a><span data-ttu-id="a9163-2419">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2419">See Also</span></span>

- <span data-ttu-id="a9163-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,</span></span>
- <span data-ttu-id="a9163-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="a9163-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="a9163-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="a9163-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="a9163-2424">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="a9163-2424">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="a9163-2425">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2425">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_establish_notify"></a><span data-ttu-id="a9163-2426">nx_tcp_socket_establish_notify</span><span class="sxs-lookup"><span data-stu-id="a9163-2426">nx_tcp_socket_establish_notify</span></span>

<span data-ttu-id="a9163-2427">Define la función de devolución de llamada de notificación de establecimiento de TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2427">Set TCP establish notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2428">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2428">Prototype</span></span>

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="a9163-2429">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2429">Description</span></span>

<span data-ttu-id="a9163-2430">Este servicio registra una función de devolución de llamada a la que se llama después de que un socket TCP establezca una conexión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2430">This service registers a callback function, which is called after a TCP socket makes a connection.</span></span> <span data-ttu-id="a9163-2431">La función de devolución de llamada de establecimiento de socket TCP está disponible si NetX se crea con la opción ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definida.</span><span class="sxs-lookup"><span data-stu-id="a9163-2431">The TCP socket establish callback function is available if NetX is built with the option ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2432">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2432">Parameters</span></span>

- <span data-ttu-id="a9163-2433">**socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2433">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="a9163-2434">**tcp_establish_notify**: función de devolución de llamada invocada después de establecer una conexión TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2434">**tcp_establish_notify** Callback function invoked after a TCP connection is established.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2435">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2435">Return Values</span></span>

- <span data-ttu-id="a9163-2436">**NX_SUCCESS**: (0x00) la función de notificación se definió correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2436">**NX_SUCCESS** (0x00) Successfully sets the notify function.</span></span>
- <span data-ttu-id="a9163-2437">**NX_NOT_SUPPORTED**: (0X4B) la característica de notificación extendida no está integrada en la biblioteca de NetX</span><span class="sxs-lookup"><span data-stu-id="a9163-2437">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="a9163-2438">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2438">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2439">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2439">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2440">**NX_NOT_ENABLED**: (0x14) la aplicación no ha habilitado TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2440">**NX_NOT_ENABLED** (0x14) TCP has not been enabled by the application.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2441">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2441">Allowed From</span></span>

<span data-ttu-id="a9163-2442">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2442">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2443">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2443">Preemption Possible</span></span>

<span data-ttu-id="a9163-2444">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2444">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2445">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2445">Example</span></span>

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="a9163-2446">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2446">See Also</span></span>

- <span data-ttu-id="a9163-2447">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2447">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="a9163-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="a9163-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="a9163-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="a9163-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="a9163-2452">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2452">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="a9163-2453">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-2453">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="a9163-2454">Recupera información acerca de las actividades de socket TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2454">Retrieve information about TCP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2455">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2455">Prototype</span></span>

```C
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```

### <a name="description"></a><span data-ttu-id="a9163-2456">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2456">Description</span></span>

<span data-ttu-id="a9163-2457">Este servicio recupera información sobre las actividades de socket TCP de la instancia de socket TCP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2457">This service retrieves information about TCP socket activities for the specified TCP socket instance.</span></span>

<span data-ttu-id="a9163-2458">*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2458">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2459">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2459">Parameters</span></span>

- <span data-ttu-id="a9163-2460">**socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2460">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="a9163-2461">**tcp_packets_sent**: puntero al destino para el número total de paquetes TCP enviados en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2461">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent on socket.</span></span>
- <span data-ttu-id="a9163-2462">**tcp_bytes_sent**: puntero al destino para el número total de bytes TCP enviados en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2462">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent on socket.</span></span>
- <span data-ttu-id="a9163-2463">**tcp_packets_received**: puntero al destino del número total de paquetes TCP recibidos en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2463">**tcp_packets_received** Pointer to destination of the total number of TCP packets received on socket.</span></span>
- <span data-ttu-id="a9163-2464">**tcp_bytes_received**: puntero al destino del número total de bytes TCP recibidos en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2464">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received on socket.</span></span>
- <span data-ttu-id="a9163-2465">**tcp_retransmit_packets**: puntero al destino del número total de retransmisiones de paquetes TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2465">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packet retransmissions.</span></span>
- <span data-ttu-id="a9163-2466">**tcp_packets_queued**: puntero al destino del número total de paquetes TCP en cola en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2466">**tcp_packets_queued** Pointer to destination of the total number of queued TCP packets on socket.</span></span>
- <span data-ttu-id="a9163-2467">**tcp_checksum_errors**: puntero al destino del número total de paquetes TCP con errores de suma de comprobación en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2467">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors on socket.</span></span>
- <span data-ttu-id="a9163-2468">**tcp_socket_state**: puntero al destino del estado actual del socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2468">**tcp_socket_state** Pointer to destination of the socket’s current state.</span></span>
- <span data-ttu-id="a9163-2469">**tcp_transmit_queue_depth**: puntero al destino del número total de paquetes transmitidos que están en la cola en espera de confirmación.</span><span class="sxs-lookup"><span data-stu-id="a9163-2469">**tcp_transmit_queue_depth** Pointer to destination of the total number of transmit packets still queued waiting for ACK.</span></span>
- <span data-ttu-id="a9163-2470">**tcp_transmit_window**: puntero al destino del tamaño de la ventana de transmisión actual.</span><span class="sxs-lookup"><span data-stu-id="a9163-2470">**tcp_transmit_window** Pointer to destination of the current transmit window size.</span></span>
- <span data-ttu-id="a9163-2471">**tcp_receive_window**: puntero al destino del tamaño de la ventana de recepción actual.</span><span class="sxs-lookup"><span data-stu-id="a9163-2471">**tcp_receive_window** Pointer to destination of the current receive window size.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2472">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2472">Return Values</span></span>

- <span data-ttu-id="a9163-2473">**NX_SUCCESS**: (0x00) la información del socket TCP se recuperó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2473">**NX_SUCCESS** (0x00) Successful TCP socket information retrieval.</span></span>
- <span data-ttu-id="a9163-2474">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2474">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2475">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2475">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2476">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2476">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2477">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2477">Return Values</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="allowed-from"></a><span data-ttu-id="a9163-2478">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2478">Allowed From</span></span>

<span data-ttu-id="a9163-2479">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2479">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2480">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2480">Preemption Possible</span></span>

<span data-ttu-id="a9163-2481">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2481">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2482">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2482">Example</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2483">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2483">See Also</span></span>

- <span data-ttu-id="a9163-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="a9163-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="a9163-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="a9163-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="a9163-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="a9163-2493">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="a9163-2493">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="a9163-2494">Obtiene MSS del socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2494">Get MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2495">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2495">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="a9163-2496">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2496">Description</span></span>

<span data-ttu-id="a9163-2497">Este servicio recupera el tamaño de segmento máximo local (MSS) del socket especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2497">This service retrieves the specified socket's local Maximum Segment Size (MSS).</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2498">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2498">Parameters</span></span>

- <span data-ttu-id="a9163-2499">**socket_ptr**: puntero al socket creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2499">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="a9163-2500">**mss**: destino para el valor de MSS devuelto.</span><span class="sxs-lookup"><span data-stu-id="a9163-2500">**mss** Destination for returning MSS.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2501">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2501">Return Values</span></span>

- <span data-ttu-id="a9163-2502">**NX_SUCCESS**: (0x00) el valor de MSS se obtuvo correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2502">**NX_SUCCESS** (0x00) Successful MSS get.</span></span>
- <span data-ttu-id="a9163-2503">**NX_PTR_ERROR**: (0x07) el socket o el puntero de destino de MSS no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2503">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="a9163-2504">**NX_NOT_ENABLED**: (0x14) el TCP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2504">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="a9163-2505">**NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso ni una inicialización.</span><span class="sxs-lookup"><span data-stu-id="a9163-2505">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2506">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2506">Allowed From</span></span>

<span data-ttu-id="a9163-2507">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2508">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2508">Preemption Possible</span></span>

<span data-ttu-id="a9163-2509">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2509">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2510">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2510">Example</span></span>

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2511">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2511">See Also</span></span>

- <span data-ttu-id="a9163-2512">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2512">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2513">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2513">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="a9163-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="a9163-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="a9163-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="a9163-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="a9163-2517">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="a9163-2517">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="a9163-2518">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2518">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="a9163-2519">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="a9163-2519">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="a9163-2520">Obtiene el valor de MSS del socket TCP del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="a9163-2520">Get MSS of the peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2521">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2521">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="a9163-2522">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2522">Description</span></span>

<span data-ttu-id="a9163-2523">Este servicio recupera el tamaño máximo de segmento (MSS) anunciado por el socket del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="a9163-2523">This service retrieves the Maximum Segment Size (MSS) advertised by the peer socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2524">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2524">Parameters</span></span>

- <span data-ttu-id="a9163-2525">**socket_ptr**: puntero al socket creado y conectado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2525">**socket_ptr** Pointer to previously created and connected socket.</span></span>
- <span data-ttu-id="a9163-2526">**mss**: destino para devolver el valor de MSS.</span><span class="sxs-lookup"><span data-stu-id="a9163-2526">**mss** Destination for returning the MSS.</span></span>


### <a name="return-values"></a><span data-ttu-id="a9163-2527">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2527">Return Values</span></span>

- <span data-ttu-id="a9163-2528">**NX_SUCCESS**: (0x00) el valor de MSS del mismo nivel se obtuvo correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2528">**NX_SUCCESS** (0x00) Successful peer MSS get.</span></span>
- <span data-ttu-id="a9163-2529">**NX_PTR_ERROR**: (0x07) el socket o el puntero de destino de MSS no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2529">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="a9163-2530">**NX_NOT_ENABLED**: (0x14) el TCP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2530">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="a9163-2531">**NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso ni una inicialización.</span><span class="sxs-lookup"><span data-stu-id="a9163-2531">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2532">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2532">Allowed From</span></span>

<span data-ttu-id="a9163-2533">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2533">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2534">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2534">Preemption Possible</span></span>

<span data-ttu-id="a9163-2535">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2535">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2536">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2536">Example</span></span>

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2537">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2537">See Also</span></span>

- <span data-ttu-id="a9163-2538">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2538">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2539">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2539">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="a9163-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="a9163-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="a9163-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="a9163-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="a9163-2543">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="a9163-2543">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="a9163-2544">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2544">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="a9163-2545">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2545">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="a9163-2546">Define el valor de MSS del socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2546">Set MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2547">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2547">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a><span data-ttu-id="a9163-2548">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2548">Description</span></span>

<span data-ttu-id="a9163-2549">Este servicio establece el tamaño máximo de segmento (MSS) del socket especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2549">This service sets the specified socket's Maximum Segment Size (MSS).</span></span> <span data-ttu-id="a9163-2550">Tenga en cuenta que el valor de MSS debe estar dentro de la MTU de IP de la interfaz de red De este modo, hay espacio para los encabezados IP y TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2550">Note the MSS value must be within the network interface IP MTU, allowing room for IP and TCP headers.</span></span>

<span data-ttu-id="a9163-2551">Este servicio debe usarse antes de que un socket TCP inicie el proceso de conexión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2551">This service should be used before a TCP socket starts the connection process.</span></span> <span data-ttu-id="a9163-2552">Si se usa el servicio después de establecer una conexión TCP, el nuevo valor no tiene ningún efecto en la conexión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2552">If the service is used after a TCP connection is established, the new value has no effect on the connection.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2553">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2553">Parameters</span></span>

- <span data-ttu-id="a9163-2554">**socket_ptr**: puntero al socket creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2554">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="a9163-2555">**mss**: valor de MSS que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="a9163-2555">**mss** Value of MSS to set.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2556">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2556">Return Values</span></span>

- <span data-ttu-id="a9163-2557">**NX_SUCCESS**: (0x00) el valor de MSS se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2557">**NX_SUCCESS** (0x00) Successful MSS set.</span></span>
- <span data-ttu-id="a9163-2558">**NX_SIZE_ERROR**: (0x09) el valor de MSS especificado es demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="a9163-2558">**NX_SIZE_ERROR** (0x09) Specified MSS value is too large.</span></span>
- <span data-ttu-id="a9163-2559">**NX_NOT_CONNECTED**: (0x38) no se estableció la conexión TCP</span><span class="sxs-lookup"><span data-stu-id="a9163-2559">**NX_NOT_CONNECTED** (0x38) TCP connection has not been established</span></span>
- <span data-ttu-id="a9163-2560">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2560">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2561">**NX_NOT_ENABLED**: (0x14) el TCP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2561">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="a9163-2562">**NX_CALLER_ERROR**: (0x11) el autor de llamada no es un subproceso ni una inicialización.</span><span class="sxs-lookup"><span data-stu-id="a9163-2562">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2563">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2563">Allowed From</span></span>

<span data-ttu-id="a9163-2564">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2564">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2565">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2565">Preemption Possible</span></span>

<span data-ttu-id="a9163-2566">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2566">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2567">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2567">Example</span></span>

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2568">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2568">See Also</span></span>

- <span data-ttu-id="a9163-2569">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2569">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2570">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2570">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="a9163-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="a9163-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="a9163-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="a9163-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="a9163-2574">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="a9163-2574">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="a9163-2575">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2575">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="a9163-2576">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-2576">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="a9163-2577">Recupera información sobre el socket TCP del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="a9163-2577">Retrieve information about peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2578">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2578">Prototype</span></span>

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a><span data-ttu-id="a9163-2579">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2579">Description</span></span>

<span data-ttu-id="a9163-2580">Este servicio recupera información del puerto y la dirección IP del mismo nivel para el socket TCP conectado a través de la red IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2580">This service retrieves peer IP address and port information for the connected TCP socket over IP network.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2581">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2581">Parameters</span></span>

- <span data-ttu-id="a9163-2582">**socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2582">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="a9163-2583">**peer_ip_address**: puntero al destino de la dirección IP del mismo nivel, en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-2583">**peer_ip_address** Pointer to destination for peer IP address, in host byte order.</span></span>
- <span data-ttu-id="a9163-2584">**peer_port**: puntero al destino del número de puerto del mismo nivel, en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-2584">**peer_port** Pointer to destination for peer port number, in host byte order.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2585">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2585">Return Values</span></span>

- <span data-ttu-id="a9163-2586">**NX_SUCCESS**: (0x00) el servicio se ejecuta correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2586">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="a9163-2587">El número de puerto y de dirección IP del mismo nivel se devuelven al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2587">Peer IP address and port number are returned to the caller.</span></span>
- <span data-ttu-id="a9163-2588">**NX_NOT_CONNECTED**: (0x38) el socket no está en estado conectado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2588">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="a9163-2589">**NX_PTR_ERROR**: (0x07) los punteros no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2589">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="a9163-2590">**NX_NOT_ENABLED**: (0x14) el TCP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2590">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="a9163-2591">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2591">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2592">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2592">Allowed From</span></span>

<span data-ttu-id="a9163-2593">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2593">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2594">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2594">Preemption Possible</span></span>

<span data-ttu-id="a9163-2595">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2595">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2596">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2596">Example</span></span>

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2597">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2597">See Also</span></span>

- <span data-ttu-id="a9163-2598">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2598">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2599">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2599">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="a9163-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="a9163-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="a9163-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="a9163-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="a9163-2603">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="a9163-2603">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="a9163-2604">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2604">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_receive"></a><span data-ttu-id="a9163-2605">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="a9163-2605">nx_tcp_socket_receive</span></span>

<span data-ttu-id="a9163-2606">Recupera datos de un socket TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2606">Receive data from TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2607">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2607">Prototype</span></span>

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-2608">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2608">Description</span></span>

<span data-ttu-id="a9163-2609">Este servicio recibe datos TCP del socket especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2609">This service receives TCP data from the specified socket.</span></span> <span data-ttu-id="a9163-2610">Si no hay datos en cola en el socket especificado, el autor de llamada se suspende en función de la opción de espera proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2610">If no data are queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="a9163-2611">*Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2611">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2612">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2612">Parameters</span></span>

- <span data-ttu-id="a9163-2613">**socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2613">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="a9163-2614">**packet_ptr**: puntero al puntero de paquete TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2614">**packet_ptr** Pointer to TCP packet pointer.</span></span>
- <span data-ttu-id="a9163-2615">**wait_option**: define cómo se comporta el servicio si no hay ningún dato en la cola de este socket actualmente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2615">**wait_option** Defines how the service behaves if no data are currently queued on this socket.</span></span> <span data-ttu-id="a9163-2616">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-2616">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-2617">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2617">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-2619">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-2619">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2620">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2620">Return Values</span></span>
- <span data-ttu-id="a9163-2621">**NX_SUCCESS**: (0x00) los datos del socket se recibieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2621">**NX_SUCCESS** (0x00) Successful socket data receive.</span></span>
- <span data-ttu-id="a9163-2622">**NX_NOT_BOUND**: (0x24) el socket todavía no está enlazado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2622">**NX_NOT_BOUND** (0x24) Socket is not bound yet.</span></span>
- <span data-ttu-id="a9163-2623">**NX_NO_PACKET**: (0X01) no se recibió ningún dato.</span><span class="sxs-lookup"><span data-stu-id="a9163-2623">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="a9163-2624">**NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2624">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="a9163-2625">**NX_NOT_CONNECTED**: (0X38) el socket ya no está conectado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2625">**NX_NOT_CONNECTED** (0x38) The socket is no longer connected.</span></span>
- <span data-ttu-id="a9163-2626">**NX_PTR_ERROR**: (0X07) el socker o el puntero de paquete devuelto no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2626">**NX_PTR_ERROR** (0x07) Invalid socket or return packet pointer.</span></span>
- <span data-ttu-id="a9163-2627">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2627">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2628">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2628">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2629">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2629">Allowed From</span></span>

<span data-ttu-id="a9163-2630">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2630">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2631">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2631">Preemption Possible</span></span>

<span data-ttu-id="a9163-2632">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2632">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2633">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2633">Example</span></span>

<span data-ttu-id="a9163-2634">/\* Recibe un paquete del socket de cliente TCP creado y conectado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2634">/\* Receive a packet from the previously created and connected TCP client socket.</span></span> <span data-ttu-id="a9163-2635">Si no hay ningún paquete disponible, espera hasta 200 tics del temporizador antes de abandonarlo.</span><span class="sxs-lookup"><span data-stu-id="a9163-2635">If no packet is available, wait for 200 timer ticks before giving up.</span></span> <span data-ttu-id="a9163-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span><span class="sxs-lookup"><span data-stu-id="a9163-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span></span>

<span data-ttu-id="a9163-2637">/\* Si el estado es NX_SUCCESS, el paquete recibido apunta a "packet_ptr".</span><span class="sxs-lookup"><span data-stu-id="a9163-2637">/\* If status is NX_SUCCESS, the received packet is pointed to by "packet_ptr".</span></span> */

### <a name="see-also"></a><span data-ttu-id="a9163-2638">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2638">See Also</span></span>

- <span data-ttu-id="a9163-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="a9163-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="a9163-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="a9163-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="a9163-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="a9163-2648">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="a9163-2648">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="a9163-2649">Notifica a la aplicación los paquetes recibidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2649">Notify application of received packets</span></span>


### <a name="prototype"></a><span data-ttu-id="a9163-2650">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2650">Prototype</span></span>

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="a9163-2651">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2651">Description</span></span>

<span data-ttu-id="a9163-2652">Este servicio configura el puntero de la función de notificación de recepción con la función de devolución de llamada especificada por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a9163-2652">This service configures the receive notify function pointer with the callback function specified by the application.</span></span> <span data-ttu-id="a9163-2653">A continuación, se llama a esta función de devolución de llamada siempre que se reciban uno o varios paquetes en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2653">This callback function is then called whenever one or more packets are received on the socket.</span></span> <span data-ttu-id="a9163-2654">Si se proporciona un puntero NX_NULL, la función de notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="a9163-2654">If a NX_NULL pointer is supplied, the notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2655">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2655">Parameters</span></span>

- <span data-ttu-id="a9163-2656">**socket_ptr**: puntero al socket TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2656">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="a9163-2657">**tcp_receive_notify**: puntero de función de devolución de llamada de la aplicación al que se llama cuando se reciben uno o varios paquetes en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2657">**tcp_receive_notify** Application callback function pointer that is called when one or more packets are received on the socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2658">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2658">Return Values</span></span>

- <span data-ttu-id="a9163-2659">**NX_SUCCESS**: (0x00) la recepción del socket se notificó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2659">**NX_SUCCESS** (0x00) Successful socket receive notify.</span></span>
- <span data-ttu-id="a9163-2660">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2660">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2661">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2661">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2662">**NX_NOT_ENABLED**: (0x14) la característica de TCP no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2662">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2663">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2663">Allowed From</span></span>

<span data-ttu-id="a9163-2664">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2664">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2665">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2665">Preemption Possible</span></span>

<span data-ttu-id="a9163-2666">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2666">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2667">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2667">Example</span></span>

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2668">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2668">See Also</span></span>

- <span data-ttu-id="a9163-2669">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2669">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2670">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2670">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="a9163-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="a9163-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="a9163-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="a9163-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="a9163-2674">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="a9163-2674">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="a9163-2675">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2675">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_send"></a><span data-ttu-id="a9163-2676">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="a9163-2676">nx_tcp_socket_send</span></span>

<span data-ttu-id="a9163-2677">Envía datos a través de un socket TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2677">Send data through a TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2678">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2678">Prototype</span></span>

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-2679">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2679">Description</span></span>

<span data-ttu-id="a9163-2680">Este servicio envía datos TCP a través de un socket TCP previamente conectado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2680">This service sends TCP data through a previously connected TCP socket.</span></span> <span data-ttu-id="a9163-2681">Si el último tamaño de la ventana anunciado del receptor es menor que esta solicitud, el servicio se suspende opcionalmente en función de la opción de espera especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2681">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait option specified.</span></span> <span data-ttu-id="a9163-2682">Este servicio garantiza que no se envíen datos de paquetes mayores que el valor de MSS a la capa de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2682">This service guarantees that no packet data larger than MSS is sent to the IP layer.</span></span>

<span data-ttu-id="a9163-2683">*A menos que se devuelva un error, la aplicación no debe liberar el paquete después de esta llamada. Si lo hace, se producirán resultados imprevisibles, ya que el controlador de red también intentará liberar el paquete después de la transmisión.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2683">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will also try to release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2684">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2684">Parameters</span></span>

- <span data-ttu-id="a9163-2685">**socket_ptr**: puntero a la instancia de socket de TCP conectada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2685">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="a9163-2686">**packet_ptr**: puntero del paquete de datos de TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2686">**packet_ptr** TCP data packet pointer.</span></span>
- <span data-ttu-id="a9163-2687">**wait_option**: define cómo se comporta el servicio si la solicitud es mayor que el tamaño de la ventana del receptor.</span><span class="sxs-lookup"><span data-stu-id="a9163-2687">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span> <span data-ttu-id="a9163-2688">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-2688">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-2689">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2689">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-2691">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-2691">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2692">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2692">Return Values</span></span>

- <span data-ttu-id="a9163-2693">**NX_SUCCESS**: (0x00) el socket se envió correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2693">**NX_SUCCESS** (0x00) Successful socket send.</span></span>
- <span data-ttu-id="a9163-2694">**NX_NOT_BOUND**: (0x24) el socket no estaba enlazado a ningún puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-2694">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="a9163-2695">**NX_NO_INTERFACE_ADDRESS**: (0x50) no se encontró ninguna interfaz de salida adecuada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2695">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface found.</span></span>
- <span data-ttu-id="a9163-2696">**NX_NOT_CONNECTED**: (0X38) el socket ya no está conectado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2696">**NX_NOT_CONNECTED** (0x38) Socket is no longer connected.</span></span>
- <span data-ttu-id="a9163-2697">**NX_WINDOW_OVERFLOW**: (0x39) la solicitud es mayor que el tamaño de la ventana anunciado del receptor en bytes.</span><span class="sxs-lookup"><span data-stu-id="a9163-2697">**NX_WINDOW_OVERFLOW** (0x39) Request is greater than receiver’s advertised window size in bytes.</span></span>
- <span data-ttu-id="a9163-2698">**NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2698">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="a9163-2699">**NX_INVALID_PACKET**: (0X12) no se asignó el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-2699">**NX_INVALID_PACKET** (0x12) Packet is not allocated.</span></span>
- <span data-ttu-id="a9163-2700">**NX_TX_QUEUE_DEPTH**: (0x49) se alcanzó la profundidad máxima de la cola de transmisión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2700">**NX_TX_QUEUE_DEPTH** (0x49) Maximum transmit queue depth has been reached.</span></span>
- <span data-ttu-id="a9163-2701">**NX_OVERFLOW**: (0x03) el puntero para anexar paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2701">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="a9163-2702">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2702">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2703">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2703">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2704">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2704">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="a9163-2705">**NX_UNDERFLOW**: (0x02) el puntero de anteposición de paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2705">**NX_UNDERFLOW** (0x02) Packet prepend pointer is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2706">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2706">Allowed From</span></span>

<span data-ttu-id="a9163-2707">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2707">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2708">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2708">Preemption Possible</span></span>

<span data-ttu-id="a9163-2709">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2709">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2710">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2710">Example</span></span>

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2711">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2711">See Also</span></span>

- <span data-ttu-id="a9163-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="a9163-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="a9163-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="a9163-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span></span>

### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="a9163-2721">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="a9163-2721">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="a9163-2722">Espera a que el socket TCP entre en un estado específico.</span><span class="sxs-lookup"><span data-stu-id="a9163-2722">Wait for TCP socket to enter specific state</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2723">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2723">Prototype</span></span>

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="a9163-2724">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2724">Description</span></span>

<span data-ttu-id="a9163-2725">Este servicio espera a que el socket entre en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2725">This service waits for the socket to enter the desired state.</span></span> <span data-ttu-id="a9163-2726">Si el socket no se encuentra en el estado deseado, el servicio se suspende según la opción de espera proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2726">If the socket is not in the desired state, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2727">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2727">Parameters</span></span>

- <span data-ttu-id="a9163-2728">**socket_ptr**: puntero a la instancia de socket de TCP conectada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2728">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="a9163-2729">**desired_state**: estado de TCP deseado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2729">**desired_state** Desired TCP state.</span></span> <span data-ttu-id="a9163-2730">Los estados de socket de TCP válidos se definen de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a9163-2730">Valid TCP socket states are defined as follows:</span></span>
- <span data-ttu-id="a9163-2731">NX_TCP_CLOSED (0x01)</span><span class="sxs-lookup"><span data-stu-id="a9163-2731">NX_TCP_CLOSED (0x01)</span></span>
- <span data-ttu-id="a9163-2732">NX_TCP_LISTEN_STATE (0x02)</span><span class="sxs-lookup"><span data-stu-id="a9163-2732">NX_TCP_LISTEN_STATE (0x02)</span></span>
- <span data-ttu-id="a9163-2733">NX_TCP_SYN_SENT (0x03)</span><span class="sxs-lookup"><span data-stu-id="a9163-2733">NX_TCP_SYN_SENT (0x03)</span></span>
- <span data-ttu-id="a9163-2734">NX_TCP_SYN_RECEIVED (0x04)</span><span class="sxs-lookup"><span data-stu-id="a9163-2734">NX_TCP_SYN_RECEIVED (0x04)</span></span>
- <span data-ttu-id="a9163-2735">NX_TCP_ESTABLISHED (0x05)</span><span class="sxs-lookup"><span data-stu-id="a9163-2735">NX_TCP_ESTABLISHED (0x05)</span></span>
- <span data-ttu-id="a9163-2736">NX_TCP_CLOSE_WAIT (0x06)</span><span class="sxs-lookup"><span data-stu-id="a9163-2736">NX_TCP_CLOSE_WAIT (0x06)</span></span>
- <span data-ttu-id="a9163-2737">NX_TCP_FIN_WAIT_1 (0x07)</span><span class="sxs-lookup"><span data-stu-id="a9163-2737">NX_TCP_FIN_WAIT_1 (0x07)</span></span>
- <span data-ttu-id="a9163-2738">NX_TCP_FIN_WAIT_2 (0x08)</span><span class="sxs-lookup"><span data-stu-id="a9163-2738">NX_TCP_FIN_WAIT_2 (0x08)</span></span>
- <span data-ttu-id="a9163-2739">NX_TCP_CLOSING (0x09)</span><span class="sxs-lookup"><span data-stu-id="a9163-2739">NX_TCP_CLOSING (0x09)</span></span>
- <span data-ttu-id="a9163-2740">NX_TCP_TIMED_WAIT (0x0A)</span><span class="sxs-lookup"><span data-stu-id="a9163-2740">NX_TCP_TIMED_WAIT (0x0A)</span></span>
- <span data-ttu-id="a9163-2741">NX_TCP_LAST_ACK (0x0B)</span><span class="sxs-lookup"><span data-stu-id="a9163-2741">NX_TCP_LAST_ACK (0x0B)</span></span>
- <span data-ttu-id="a9163-2742">**wait_option**: define cómo se comporta el servicio si el estado solicitado no existe.</span><span class="sxs-lookup"><span data-stu-id="a9163-2742">**wait_option** Defines how the service behaves if the requested state is not present.</span></span> <span data-ttu-id="a9163-2743">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-2743">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-2744">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2744">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-2746">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-2746">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2747">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2747">Return Values</span></span>
- <span data-ttu-id="a9163-2748">**NX_SUCCESS**: (0x00) la espera del estado se completó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2748">**NX_SUCCESS** (0x00) Successful state wait.</span></span>
- <span data-ttu-id="a9163-2749">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2749">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2750">**NX_NOT_SUCCESSFUL**: (0X43) el estado no existe en el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2750">**NX_NOT_SUCCESSFUL** (0x43) State not present within the specified wait time.</span></span>
- <span data-ttu-id="a9163-2751">**NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2751">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="a9163-2752">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2752">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2753">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2753">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="a9163-2754">**NX_OPTION_ERROR**: (0X0a) el estado del socket deseado no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2754">**NX_OPTION_ERROR** (0x0A) The desired socket state is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2755">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2755">Allowed From</span></span>

<span data-ttu-id="a9163-2756">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2756">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2757">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2757">Preemption Possible</span></span>

<span data-ttu-id="a9163-2758">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2758">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2759">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2759">Example</span></span>

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2760">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2760">See Also</span></span>

- <span data-ttu-id="a9163-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="a9163-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="a9163-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="a9163-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="a9163-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="a9163-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="a9163-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="a9163-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="a9163-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="a9163-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span></span>

## <a name="nx_tcp_socket_timed_wait_callback"></a><span data-ttu-id="a9163-2770">nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="a9163-2770">nx_tcp_socket_timed_wait_callback</span></span>

<span data-ttu-id="a9163-2771">Instala la devolución de llamada para el estado de tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="a9163-2771">Install callback for timed wait state</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2772">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2772">Prototype</span></span>

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="a9163-2773">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2773">Description</span></span>

<span data-ttu-id="a9163-2774">Este servicio registra una función de devolución de llamada que se invoca cuando el socket TCP está en estado de tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="a9163-2774">This service registers a callback function which is invoked when the TCP socket is in timed wait state.</span></span> <span data-ttu-id="a9163-2775">Para usar este servicio, la biblioteca NetX debe compilarse con la opción ***NX_ENABLE_EXTENDED_NOTIFY*** definida.</span><span class="sxs-lookup"><span data-stu-id="a9163-2775">To use this service, the NetX library must be built with the option ***NX_ENABLE_EXTENDED_NOTIFY*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2776">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2776">Parameters</span></span>

- <span data-ttu-id="a9163-2777">**socket_ptr**: puntero a la instancia de socket de servidor o cliente conectada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2777">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="a9163-2778">**tcp_timed_wait_callback**: función de devolución de llamada de espera programada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2778">**tcp_timed_wait_callback** The timed wait callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2779">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2779">Return Values</span></span>

- <span data-ttu-id="a9163-2780">**NX_SUCCESS**: (0x00) el socket de la función de devolución de llamada se registró correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2780">**NX_SUCCESS** (0x00) Successfully registers the callback function socket</span></span>
- <span data-ttu-id="a9163-2781">**NX_NOT_SUPPORTED**: (0X4B) la biblioteca de NetX se genera sin la característica de notificación extendida habilitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2781">**NX_NOT_SUPPORTED** (0x4B) NetX library is built without the extended notify feature enabled.</span></span>
- <span data-ttu-id="a9163-2782">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2782">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2783">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2784">**NX_NOT_ENABLED**: (0x14) la característica de TCP no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2784">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2785">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2785">Allowed From</span></span>

<span data-ttu-id="a9163-2786">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2786">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2787">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2787">Preemption Possible</span></span>

<span data-ttu-id="a9163-2788">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2788">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2789">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2789">Example</span></span>

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="a9163-2790">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2790">See Also</span></span>

- <span data-ttu-id="a9163-2791">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2791">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2792">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2792">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="a9163-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="a9163-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="a9163-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="a9163-2796">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="a9163-2796">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="a9163-2797">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2797">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="a9163-2798">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="a9163-2798">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="a9163-2799">Configura parámetros de transmisión del socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2799">Configure socket's transmit parameters</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2800">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2800">Prototype</span></span>

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a><span data-ttu-id="a9163-2801">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2801">Description</span></span>

<span data-ttu-id="a9163-2802">Este servicio configura varios parámetros de transmisión del socket TCP especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2802">This service configures various transmit parameters of the specified TCP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2803">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2803">Parameters</span></span>

- <span data-ttu-id="a9163-2804">**socket_ptr**: puntero al socket TCP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2804">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="a9163-2805">**max_queue_depth**: número máximo de paquetes que se pueden poner en cola para su transmisión.</span><span class="sxs-lookup"><span data-stu-id="a9163-2805">**max_queue_depth** Maximum number of packets allowed to be queued for transmission.</span></span>
- <span data-ttu-id="a9163-2806">**timeout**: número de tics de temporizador de ThreadX; se espera una confirmación antes de que se vuelva a enviar el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-2806">**timeout** Number of ThreadX timer ticks an ACK is waited for before the packet is sent again.</span></span>
- <span data-ttu-id="a9163-2807">**max_retries**: número máximo de reintentos permitidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2807">**max_retries** Maximum number of retries allowed.</span></span>
- <span data-ttu-id="a9163-2808">**timeout_shift**: valor para desplazar el tiempo de espera de cada reintento subsiguiente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2808">**timeout_shift** Value to shift the timeout for each subsequent retry.</span></span> <span data-ttu-id="a9163-2809">Un valor de 0, da como resultado el mismo tiempo de espera entre reintentos sucesivos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2809">A value of 0, results in the same timeout between successive retries.</span></span> <span data-ttu-id="a9163-2810">Un valor de 1, duplica el tiempo de espera entre reintentos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2810">A value of 1, doubles the timeout between retries.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2811">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2811">Return Values</span></span>
- <span data-ttu-id="a9163-2812">**NX_SUCCESS**: (0x00) el socket de transmisión se configuró correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2812">**NX_SUCCESS** (0x00) Successful transmit socket configure.</span></span>
- <span data-ttu-id="a9163-2813">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2813">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-2814">**NX_OPTION_ERROR**: (0x0a) la opción de profundidad de la cola no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-2814">**NX_OPTION_ERROR** (0x0a) Invalid queue depth option.</span></span>
- <span data-ttu-id="a9163-2815">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2815">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2816">**NX_NOT_ENABLED**: (0x14) la característica de TCP no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2816">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2817">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2817">Allowed From</span></span>

<span data-ttu-id="a9163-2818">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2818">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2819">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2819">Preemption Possible</span></span>

<span data-ttu-id="a9163-2820">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2820">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2821">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2821">Example</span></span>

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2822">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2822">See Also</span></span>

- <span data-ttu-id="a9163-2823">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2823">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2824">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2824">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="a9163-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="a9163-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="a9163-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="a9163-2828">nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="a9163-2828">nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="a9163-2829">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2829">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_window_update_notify_set"></a><span data-ttu-id="a9163-2830">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="a9163-2830">nx_tcp_socket_window_update_notify_set</span></span>

<span data-ttu-id="a9163-2831">Notifica a la aplicación la actualizaciones del tamaño de la ventana.</span><span class="sxs-lookup"><span data-stu-id="a9163-2831">Notify application of window size updates</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2832">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2832">Prototype</span></span>

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="a9163-2833">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2833">Description</span></span>

<span data-ttu-id="a9163-2834">Este servicio instala una rutina de devolución de llamada de actualizaciones de la ventana del socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2834">This service installs a socket window update callback routine.</span></span> <span data-ttu-id="a9163-2835">Se llama a esta rutina automáticamente cada vez que el socket especificado recibe un paquete que indica un aumento en el tamaño de la ventana del host remoto.</span><span class="sxs-lookup"><span data-stu-id="a9163-2835">This routine is called automatically whenever the specified socket receives a packet indicating an increase in the window size of the remote host.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2836">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2836">Parameters</span></span>

- <span data-ttu-id="a9163-2837">**socket_ptr**: puntero a la instancia de socket TCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2837">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="a9163-2838">**tcp_window_update_notify**: rutina de devolución de llamada a la que se llamará cuando cambie el tamaño de la ventana.</span><span class="sxs-lookup"><span data-stu-id="a9163-2838">**tcp_window_update_notify** Callback routine to be called when the window size changes.</span></span> <span data-ttu-id="a9163-2839">Un valor NULL deshabilita la actualización de cambios de la ventana.</span><span class="sxs-lookup"><span data-stu-id="a9163-2839">A value of NULL disables the window change update.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2840">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2840">Return Values</span></span>
- <span data-ttu-id="a9163-2841">**NX_SUCCESS**: (0x00) la rutina de devolución de llamada se instala en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2841">**NX_SUCCESS** (0x00) Callback routine is installed on the socket.</span></span>
- <span data-ttu-id="a9163-2842">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2842">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2843">**NX_PTR_ERROR**: (0x07) los punteros no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2843">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="a9163-2844">**NX_NOT_ENABLED**: (0x14) la característica de TCP no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2844">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="a9163-2845">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2845">Allowed From</span></span>

<span data-ttu-id="a9163-2846">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2846">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2847">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2847">Preemption Possible</span></span>

<span data-ttu-id="a9163-2848">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2848">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2849">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2849">Example</span></span>

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a><span data-ttu-id="a9163-2850">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2850">See Also</span></span>

- <span data-ttu-id="a9163-2851">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-2851">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="a9163-2852">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2852">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="a9163-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="a9163-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="a9163-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="a9163-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="a9163-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="a9163-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span></span>

## <a name="nx_udp_enable"></a><span data-ttu-id="a9163-2857">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-2857">nx_udp_enable</span></span>

<span data-ttu-id="a9163-2858">Habilita el componente UDP de NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-2858">Enable UDP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2859">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2859">Prototype</span></span>

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-2860">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2860">Description</span></span>

<span data-ttu-id="a9163-2861">Este servicio habilita el componente de Protocolo de datagramas de usuario (UDP) de NetX.</span><span class="sxs-lookup"><span data-stu-id="a9163-2861">This service enables the User Datagram Protocol (UDP) component of NetX.</span></span> <span data-ttu-id="a9163-2862">Una vez habilitado, la aplicación puede enviar y recibir datagramas UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2862">After enabled, UDP datagrams may be sent and received by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2863">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2863">Parameters</span></span>

- <span data-ttu-id="a9163-2864">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2864">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2865">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2865">Return Values</span></span>

- <span data-ttu-id="a9163-2866">**NX_SUCCESS**: (0x00) UDP se habilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2866">**NX_SUCCESS** (0x00) Successful UDP enable.</span></span>
- <span data-ttu-id="a9163-2867">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2867">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-2868">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2868">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2869">**NX_ALREADY_ENABLED**: (0X15) este componente ya se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2869">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2870">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2870">Allowed From</span></span>

<span data-ttu-id="a9163-2871">Inicialización, subprocesos, temporizadores</span><span class="sxs-lookup"><span data-stu-id="a9163-2871">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2872">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2872">Preemption Possible</span></span>

<span data-ttu-id="a9163-2873">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2873">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2874">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2874">Example</span></span>

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2875">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2875">See Also</span></span>

- <span data-ttu-id="a9163-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,</span><span class="sxs-lookup"><span data-stu-id="a9163-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="a9163-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="a9163-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2883">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-2883">nx_udp_source_extract</span></span>

## <a name="nx_udp_free_port_find"></a><span data-ttu-id="a9163-2884">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="a9163-2884">nx_udp_free_port_find</span></span>

<span data-ttu-id="a9163-2885">Busca el siguiente puerto UDP disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-2885">Find next available UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2886">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2886">Prototype</span></span>

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-2887">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2887">Description</span></span>

<span data-ttu-id="a9163-2888">Este servicio busca un puerto UDP disponible (sin enlazar) a partir del número de puerto proporcionado por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a9163-2888">This service looks for a free UDP port (unbound) starting from the application supplied port number.</span></span> <span data-ttu-id="a9163-2889">La lógica de búsqueda se ajustará si la búsqueda alcanza el valor de puerto máximo de 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="a9163-2889">The search logic will wrap around if the search reaches the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="a9163-2890">Si la búsqueda se realiza correctamente, se devuelve el puerto disponible en la variable a la que apunta *free_port_ptr*.</span><span class="sxs-lookup"><span data-stu-id="a9163-2890">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="a9163-2891">*Se puede llamar a este servicio desde otro subproceso y hacer que se devuelva el mismo puerto. Para evitar esta condición de carrera, es posible que la aplicación quiera proteger este servicio y el enlace de socket real mediante una exclusión mutua.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2891">*This service can be called from another thread and can have the same port returned. To prevent this race condition, the application may wish to place this service and the actual socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2892">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2892">Parameters</span></span>

- <span data-ttu-id="a9163-2893">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2893">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-2894">**port**: número de puerto para iniciar la búsqueda (de 1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="a9163-2894">**port** Port number to start search (1 through 0xFFFF).</span></span>
- <span data-ttu-id="a9163-2895">**free_port_ptr**: puntero a la variable devuelta del puerto disponible de destino.</span><span class="sxs-lookup"><span data-stu-id="a9163-2895">**free_port_ptr** Pointer to the destination free port return variable.</span></span>


### <a name="return-values"></a><span data-ttu-id="a9163-2896">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2896">Return Values</span></span>

- <span data-ttu-id="a9163-2897">**NX_SUCCESS**: (0x00) se encontró un puerto disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-2897">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="a9163-2898">**NX_NO_FREE_PORTS**: (0X45) no se encontró ningún puerto disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-2898">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="a9163-2899">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2899">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-2900">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2900">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2901">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2901">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="a9163-2902">**NX_INVALID_PORT**: (0X46) el número de puerto especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2902">**NX_INVALID_PORT** (0x46) Specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2903">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2903">Allowed From</span></span>

<span data-ttu-id="a9163-2904">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2904">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2905">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2905">Preemption Possible</span></span>

<span data-ttu-id="a9163-2906">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2906">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2907">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2907">Example</span></span>

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2908">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2908">See Also</span></span>

- <span data-ttu-id="a9163-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,</span><span class="sxs-lookup"><span data-stu-id="a9163-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="a9163-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="a9163-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2916">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-2916">nx_udp_source_extract</span></span>

## <a name="nx_udp_info_get"></a><span data-ttu-id="a9163-2917">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-2917">nx_udp_info_get</span></span>

<span data-ttu-id="a9163-2918">Recupera información acerca de las actividades UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2918">Retrieve information about UDP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2919">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2919">Prototype</span></span>

```C
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="a9163-2920">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2920">Description</span></span>

<span data-ttu-id="a9163-2921">Este servicio recupera información sobre las actividades UDP de la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-2921">This service retrieves information about UDP activities for the specified IP instance.</span></span>

<span data-ttu-id="a9163-2922">*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-2922">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2923">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2923">Parameters</span></span>

- <span data-ttu-id="a9163-2924">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2924">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-2925">**udp_packets_sent**: puntero al destino para el número total de paquetes UDP enviados.</span><span class="sxs-lookup"><span data-stu-id="a9163-2925">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent.</span></span>
- <span data-ttu-id="a9163-2926">**udp_bytes_sent**: puntero al destino para el número total de bytes UDP enviados.</span><span class="sxs-lookup"><span data-stu-id="a9163-2926">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent.</span></span>
- <span data-ttu-id="a9163-2927">**udp_packets_received**: puntero al destino del número total de paquetes UDP recibidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2927">**udp_packets_received** Pointer to destination of the total number of UDP packets received.</span></span>
- <span data-ttu-id="a9163-2928">**udp_bytes_received**: puntero al destino del número total de bytes UDP recibidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2928">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received.</span></span>
- <span data-ttu-id="a9163-2929">**udp_invalid_packets**: puntero al destino del número total de paquetes UDP no válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-2929">**udp_invalid_packets** Pointer to destination of the total number of invalid UDP packets.</span></span>
- <span data-ttu-id="a9163-2930">**udp_receive_packets_dropped**: puntero al destino del número total de paquetes UDP recibidos anulados.</span><span class="sxs-lookup"><span data-stu-id="a9163-2930">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped.</span></span>
- <span data-ttu-id="a9163-2931">**udp_checksum_errors**: puntero al destino del número total de paquetes UDP con errores de suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="a9163-2931">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2932">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2932">Return Values</span></span>

- <span data-ttu-id="a9163-2933">**NX_SUCCESS**: (0x00) la información de UDP se recuperó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2933">**NX_SUCCESS** (0x00) Successful UDP information retrieval.</span></span>
- <span data-ttu-id="a9163-2934">**NX_PTR_ERROR**: (0x07) el puntero de IP no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2934">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="a9163-2935">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2935">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-2936">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2936">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="a9163-2937">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2937">Allowed From</span></span>

<span data-ttu-id="a9163-2938">Inicialización, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="a9163-2938">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2939">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2939">Preemption Possible</span></span>

<span data-ttu-id="a9163-2940">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2940">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2941">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2941">Example</span></span>

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_invalid_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2942">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2942">See Also</span></span>

- <span data-ttu-id="a9163-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,</span><span class="sxs-lookup"><span data-stu-id="a9163-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="a9163-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="a9163-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2950">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-2950">nx_udp_source_extract</span></span>

## <a name="nx_udp_packet_info_extract"></a><span data-ttu-id="a9163-2951">nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-2951">nx_udp_packet_info_extract</span></span>

<span data-ttu-id="a9163-2952">Extrae parámetros de la red de un paquete UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2952">Extract network parameters from UDP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2953">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2953">Prototype</span></span>

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="a9163-2954">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2954">Description</span></span>

<span data-ttu-id="a9163-2955">Este servicio extrae los parámetros de red, como la dirección IP, el número de puerto del mismo nivel y el tipo de protocolo (este servicio siempre devuelve el tipo UDP) de un paquete recibido en una interfaz entrante.</span><span class="sxs-lookup"><span data-stu-id="a9163-2955">This service extracts network parameters, such as IP address, peer port number, protocol type (this service always returns UDP type) from a packet received on an incoming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2956">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2956">Parameters</span></span>

- <span data-ttu-id="a9163-2957">**packet_ptr**: puntero al paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-2957">**packet_ptr** Pointer to packet.</span></span>
- <span data-ttu-id="a9163-2958">**ip_address**: puntero a la dirección IP del emisor.</span><span class="sxs-lookup"><span data-stu-id="a9163-2958">**ip_address** Pointer to sender IP address.</span></span>
- <span data-ttu-id="a9163-2959">**protocolo**: puntero al protocolo (UDP).</span><span class="sxs-lookup"><span data-stu-id="a9163-2959">**protocol** Pointer to protocol (UDP).</span></span>
- <span data-ttu-id="a9163-2960">**port**: puntero al número de puerto del emisor.</span><span class="sxs-lookup"><span data-stu-id="a9163-2960">**port** Pointer to sender’s port number.</span></span>
- <span data-ttu-id="a9163-2961">**interface_index**: puntero al índice de la interfaz de recepción.</span><span class="sxs-lookup"><span data-stu-id="a9163-2961">**interface_index** Pointer to receiving interface index.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2962">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2962">Return Values</span></span>

- <span data-ttu-id="a9163-2963">**NX_SUCCESS**: (0x00) los datos de la interfaz del paquetes se extrajeron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2963">**NX_SUCCESS** (0x00) Packet interface data successfully extracted.</span></span>
- <span data-ttu-id="a9163-2964">**NX_INVALID_PACKET**: (0X12) el paquete no contiene el marco de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2964">**NX_INVALID_PACKET** (0x12) Packet does not contain IP frame.</span></span>
- <span data-ttu-id="a9163-2965">**NX_PTR_ERROR**: (0x07) la entrada del puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-2965">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="a9163-2966">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-2966">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-2967">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-2967">Allowed From</span></span>

<span data-ttu-id="a9163-2968">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-2968">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-2969">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-2969">Preemption Possible</span></span>

<span data-ttu-id="a9163-2970">No</span><span class="sxs-lookup"><span data-stu-id="a9163-2970">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-2971">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-2971">Example</span></span>

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-2972">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-2972">See Also</span></span>

- <span data-ttu-id="a9163-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="a9163-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="a9163-2980">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-2980">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bind"></a><span data-ttu-id="a9163-2981">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="a9163-2981">nx_udp_socket_bind</span></span>

<span data-ttu-id="a9163-2982">Enlaza el socket UDP al puerto UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-2982">Bind UDP socket to UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-2983">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-2983">Prototype</span></span>

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-2984">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-2984">Description</span></span>

<span data-ttu-id="a9163-2985">Este servicio enlaza el socket UDP creado previamente al puerto UDP especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-2985">This service binds the previously created UDP socket to the specified UDP port.</span></span> <span data-ttu-id="a9163-2986">El intervalo de sockets UDP válidos es de 0 a 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="a9163-2986">Valid UDP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="a9163-2987">Si el número de puerto solicitado está enlazado a otro socket, este servicio espera durante el período de tiempo especificado para que el socket se desenlace del número de puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-2987">If the requested port number is bound to another socket, this service waits for specified period of time for the socket to unbind from the port number.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-2988">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-2988">Parameters</span></span>

- <span data-ttu-id="a9163-2989">**socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2989">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="a9163-2990">**port**: número de puerto al que se va a enlazar (de 1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="a9163-2990">**port** Port number to bind to (1 through 0xFFFF).</span></span> <span data-ttu-id="a9163-2991">Si el número de puerto es NX_ANY_PORT (0x0000), la instancia de IP buscará el siguiente puerto disponible y lo utilizará para el enlace.</span><span class="sxs-lookup"><span data-stu-id="a9163-2991">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="a9163-2992">**wait_option**: define cómo se comporta el servicio si el puerto ya está enlazado a otro socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-2992">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="a9163-2993">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-2993">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-2994">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-2994">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-2996">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-2996">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-2997">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-2997">Return Values</span></span>

- <span data-ttu-id="a9163-2998">**NX_SUCCESS**: (0x00) el socket se enlazó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-2998">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="a9163-2999">**NX_ALREADY_BOUND**: (0X22) este socket ya está enlazado a otro puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-2999">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another port.</span></span>
- <span data-ttu-id="a9163-3000">**NX_PORT_UNAVAILABLE**: (0x23) el puerto ya está enlazado a otro socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3000">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="a9163-3001">**NX_NO_FREE_PORTS**: (0X45) no hay ningún puerto disponible.</span><span class="sxs-lookup"><span data-stu-id="a9163-3001">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="a9163-3002">**NX_WAIT_ABORTED**: (0x1A) una llamada a tx_thread_wait_abort ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-3002">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="a9163-3003">**NX_INVALID_PORT**: (0x46) el puerto especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3003">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="a9163-3004">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3004">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-3005">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-3006">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3007">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3007">Allowed From</span></span>

<span data-ttu-id="a9163-3008">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-3008">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3009">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3009">Preemption Possible</span></span>

<span data-ttu-id="a9163-3010">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3010">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3011">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3011">Example</span></span>

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a><span data-ttu-id="a9163-3012">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3012">See Also</span></span>

- <span data-ttu-id="a9163-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="a9163-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="a9163-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="a9163-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="a9163-3020">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3020">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="a9163-3021">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="a9163-3021">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="a9163-3022">Recupera el número de bytes disponibles para la recuperación</span><span class="sxs-lookup"><span data-stu-id="a9163-3022">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3023">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3023">Prototype</span></span>

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="a9163-3024">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3024">Description</span></span>

<span data-ttu-id="a9163-3025">Este servicio recupera el número de bytes disponibles para la recepción en el socket UDP especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3025">This service retrieves number of bytes available for reception in the specified UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3026">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3026">Parameters</span></span>

- <span data-ttu-id="a9163-3027">**socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3027">**socket_ptr** Pointer to previously created UDP socket.</span></span>
- <span data-ttu-id="a9163-3028">**bytes_available**: puntero al destino para los bytes disponibles.</span><span class="sxs-lookup"><span data-stu-id="a9163-3028">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3029">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3029">Return Values</span></span>

- <span data-ttu-id="a9163-3030">**NX_SUCCESS**: (0x00) los bytes disponibles se recuperaron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3030">**NX_SUCCESS** (0x00) Successful bytes available retrieval.</span></span>
- <span data-ttu-id="a9163-3031">**NX_NOT_SUCCESSFUL**: (0X43) el socket no se enlazó a ningún puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-3031">**NX_NOT_SUCCESSFUL** (0x43) Socket not bound to a port.</span></span>
- <span data-ttu-id="a9163-3032">**NX_PTR_ERROR**: (0x07) los punteros no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-3032">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="a9163-3033">**NX_NOT_ENABLED**: (0x14) la característica de UDP no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="a9163-3033">**NX_NOT_ENABLED** (0x14) UDP feature is not enabled.</span></span>
- <span data-ttu-id="a9163-3034">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3034">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3035">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3035">Allowed From</span></span>

<span data-ttu-id="a9163-3036">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-3036">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3037">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3037">Preemption Possible</span></span>

<span data-ttu-id="a9163-3038">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3038">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3039">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3039">Example</span></span>

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="a9163-3040">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3040">See Also</span></span>

- <span data-ttu-id="a9163-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3042">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3042">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="a9163-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="a9163-3048">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3048">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="a9163-3049">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="a9163-3049">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="a9163-3050">Deshabilita la suma de comprobación para el socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3050">Disable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3051">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3051">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-3052">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3052">Description</span></span>

<span data-ttu-id="a9163-3053">Este servicio deshabilita la lógica de suma de comprobación para enviar y recibir paquetes en el socket UDP especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3053">This service disables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="a9163-3054">Cuando se deshabilita la lógica de suma de comprobación, se carga un valor de cero en el campo de suma de comprobación del encabezado UDP para todos los paquetes enviados a través de este socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3054">When the checksum logic is disabled, a value of zero is loaded into the UDP header's checksum field for all packets sent through this socket.</span></span> <span data-ttu-id="a9163-3055">Un valor de suma de comprobación de cero en el encabezado UDP indica al receptor que la suma de comprobación no se procesa para este paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-3055">A zero-value checksum value in the UDP header signals the receiver that checksum is not computed for this packet.</span></span>

<span data-ttu-id="a9163-3056">Tenga en cuenta también que esto no tiene ningún efecto si se definen los elementos ***NX_DISABLE_UDP_RX_CHECKSUM** _ y _ *_NX_DISABLE_UDP_TX_CHECKSUM_** al recibir y enviar paquetes UDP, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3056">Also note that this has no effect if ***NX_DISABLE_UDP_RX_CHECKSUM** _ and _ *_NX_DISABLE_UDP_TX_CHECKSUM_** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3057">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3057">Parameters</span></span>

- <span data-ttu-id="a9163-3058">**socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3058">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3059">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3059">Return Values</span></span>

- <span data-ttu-id="a9163-3060">**NX_SUCCESS**: (0x00) la suma de comprobación de socket se deshabilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3060">**NX_SUCCESS** (0x00) Successful socket checksum disable.</span></span>
- <span data-ttu-id="a9163-3061">**NX_NOT_BOUND**: (0x24) el socket no está enlazado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3061">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="a9163-3062">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3062">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-3063">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3063">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-3064">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3064">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3065">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3065">Allowed From</span></span>

<span data-ttu-id="a9163-3066">Inicialización, subprocesos, temporizador</span><span class="sxs-lookup"><span data-stu-id="a9163-3066">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3067">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3067">Preemption Possible</span></span>

<span data-ttu-id="a9163-3068">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3068">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3069">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3069">Example</span></span>

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-3070">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3070">See Also</span></span>

- <span data-ttu-id="a9163-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3072">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3072">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="a9163-3078">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3078">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="a9163-3079">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="a9163-3079">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="a9163-3080">Habilita la suma de comprobación para el socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3080">Enable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3081">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3081">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-3082">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3082">Description</span></span>

<span data-ttu-id="a9163-3083">Este servicio habilita la lógica de suma de comprobación para enviar y recibir paquetes en el socket UDP especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3083">This service enables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="a9163-3084">La suma de comprobación abarca todo el área de datos UDP y un seudoencabezado de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3084">The checksum covers the entire UDP data area as well as a pseudo IP header.</span></span>

<span data-ttu-id="a9163-3085">Tenga en cuenta también que esto no tiene ningún efecto si **NX_DISABLE_UDP_RX_CHECKSUM** y **NX_DISABLE_UDP_TX_CHECKSUM** se definen al recibir y enviar paquetes UDP, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3085">Also note that this has no effect if **NX_DISABLE_UDP_RX_CHECKSUM** and **NX_DISABLE_UDP_TX_CHECKSUM** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3086">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3086">Parameters</span></span>

- <span data-ttu-id="a9163-3087">**socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3087">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3088">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3088">Return Values</span></span>

- <span data-ttu-id="a9163-3089">**NX_SUCCESS**: (0x00) la suma de comprobación de socket se habilitó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3089">**NX_SUCCESS** (0x00) Successful socket checksum enable.</span></span>
- <span data-ttu-id="a9163-3090">**NX_NOT_BOUND**: (0x24) el socket no está enlazado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3090">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="a9163-3091">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3091">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-3092">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3092">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-3093">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3093">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3094">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3094">Allowed From</span></span>

<span data-ttu-id="a9163-3095">Inicialización, subprocesos, temporizador</span><span class="sxs-lookup"><span data-stu-id="a9163-3095">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3096">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3096">Preemption Possible</span></span>

<span data-ttu-id="a9163-3097">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3097">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3098">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3098">Example</span></span>

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-3099">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3099">See Also</span></span>

- <span data-ttu-id="a9163-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3101">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3101">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="a9163-3107">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3107">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_create"></a><span data-ttu-id="a9163-3108">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="a9163-3108">nx_udp_socket_create</span></span>

<span data-ttu-id="a9163-3109">Crea un socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3109">Create UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3110">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3110">Prototype</span></span>

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a><span data-ttu-id="a9163-3111">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3111">Description</span></span>

<span data-ttu-id="a9163-3112">Este servicio crea un socket UDP para la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-3112">This service creates a UDP socket for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3113">Parameters</span></span>

- <span data-ttu-id="a9163-3114">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3114">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a9163-3115">**socket_ptr**: puntero al nuevo bloque de control de socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3115">**socket_ptr** Pointer to new UDP socket control bloc.</span></span>
- <span data-ttu-id="a9163-3116">**name**: nombre de la aplicación para este socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3116">**name** Application name for this UDP socket.</span></span>
- <span data-ttu-id="a9163-3117">**type_of_service**: define el tipo de servicio para la transmisión. Los valores válidos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="a9163-3117">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
    - <span data-ttu-id="a9163-3118">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-3118">NX_IP_NORMAL (0x00000000)</span></span>
    - <span data-ttu-id="a9163-3119">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="a9163-3119">NX_IP_MIN_DELAY (0x00100000)</span></span>
    - <span data-ttu-id="a9163-3120">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="a9163-3120">NX_IP_MAX_DATA (0x00080000)</span></span>
    - <span data-ttu-id="a9163-3121">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="a9163-3121">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
    - <span data-ttu-id="a9163-3122">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="a9163-3122">NX_IP_MIN_COST (0x00020000)</span></span>
- <span data-ttu-id="a9163-3123">**fragment**: especifica si se permite o no la fragmentación de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3123">**fragment** Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="a9163-3124">Si se especifica NX_FRAGMENT_OKAY (0X0), se permite la fragmentación de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3124">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="a9163-3125">Si se especifica NX_DONT_FRAGMENT (0x4000), se deshabilita la fragmentación de IP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3125">If NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="a9163-3126">**time_to_live**: especifica el valor de 8 bits que define el número de enrutadores que puede autorizar este paquete antes de que desaparezca.</span><span class="sxs-lookup"><span data-stu-id="a9163-3126">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="a9163-3127">El elemento NX_IP_TIME_TO_LIVE especifica el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3127">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="a9163-3128">**queue_maximum**: define el número máximo de datagramas UDP que se pueden poner en cola para este socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3128">**queue_maximum** Defines the maximum number of UDP datagrams that can be queued for this socket.</span></span> <span data-ttu-id="a9163-3129">Una vez alcanzado el límite de la cola, se libera el paquete UDP más antiguo para cada paquete nuevo recibido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3129">After the queue limit is reached, for every new packet received the oldest UDP packet is released.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3130">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3130">Return Values</span></span>

- <span data-ttu-id="a9163-3131">**NX_SUCCESS**: (0x00) el socket UDP se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3131">**NX_SUCCESS** (0x00) Successful UDP socket create.</span></span>
- <span data-ttu-id="a9163-3132">**NX_OPTION_ERROR**: (0x0a) el tipo de servicio, el fragmento o la opción de período de vida no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-3132">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, or time-to-live option.</span></span>
- <span data-ttu-id="a9163-3133">**NX_PTR_ERROR**: (0X07) la IP o el puntero de socket no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-3133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="a9163-3134">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-3135">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3136">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3136">Allowed From</span></span>

<span data-ttu-id="a9163-3137">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-3137">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3138">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3138">Preemption Possible</span></span>

<span data-ttu-id="a9163-3139">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3139">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3140">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3140">Example</span></span>

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-3141">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3141">See Also</span></span>

- <span data-ttu-id="a9163-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3143">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3143">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span><span class="sxs-lookup"><span data-stu-id="a9163-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span></span>
- <span data-ttu-id="a9163-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="a9163-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="a9163-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="a9163-3149">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3149">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_delete"></a><span data-ttu-id="a9163-3150">nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="a9163-3150">nx_udp_socket_delete</span></span>

<span data-ttu-id="a9163-3151">Elimina el socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3151">Delete UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3152">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3152">Prototype</span></span>

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-3153">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3153">Description</span></span>

<span data-ttu-id="a9163-3154">Este servicio elimina un socket UDP creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3154">This service deletes a previously created UDP socket.</span></span> <span data-ttu-id="a9163-3155">Si el socket se ha enlazado a un puerto, primero se debe desenlazar.</span><span class="sxs-lookup"><span data-stu-id="a9163-3155">If the socket was bound to a port, the socket must be unbound first.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3156">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3156">Parameters</span></span>

- <span data-ttu-id="a9163-3157">**socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3157">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3158">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3158">Return Values</span></span>

- <span data-ttu-id="a9163-3159">**NX_SUCCESS**: (0x00) el socket se eliminó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3159">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="a9163-3160">**NX_STILL_BOUND**: (0x42) el socket sigue estando enlazado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3160">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="a9163-3161">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3161">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-3162">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3162">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-3163">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3163">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3164">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3164">Allowed From</span></span>

<span data-ttu-id="a9163-3165">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-3165">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3166">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3166">Preemption Possible</span></span>

<span data-ttu-id="a9163-3167">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3167">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3168">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3168">Example</span></span>

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-3169">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3169">See Also</span></span>

- <span data-ttu-id="a9163-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3171">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3171">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="a9163-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="a9163-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="a9163-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="a9163-3177">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3177">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_info_get"></a><span data-ttu-id="a9163-3178">nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="a9163-3178">nx_udp_socket_info_get</span></span>

<span data-ttu-id="a9163-3179">Recupera información acerca de las actividades del socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3179">Retrieve information about UDP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3180">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3180">Prototype</span></span>

```C
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="a9163-3181">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3181">Description</span></span>

<span data-ttu-id="a9163-3182">Este servicio recupera información sobre las actividades del socket UDP de la instancia de socket UDP especificada.</span><span class="sxs-lookup"><span data-stu-id="a9163-3182">This service retrieves information about UDP socket activities for the specified UDP socket instance.</span></span>

<span data-ttu-id="a9163-3183">*Si el puntero de destino es NX_NULL, esa información determinada no se devuelve al autor de llamada.*</span><span class="sxs-lookup"><span data-stu-id="a9163-3183">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3184">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3184">Parameters</span></span>

- <span data-ttu-id="a9163-3185">**socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3185">**socket_ptr** Pointer to previously-created UDP socket instance.</span></span>
- <span data-ttu-id="a9163-3186">**udp_packets_sent**: puntero al destino para el número total de paquetes UDP enviados en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3186">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent on socket.</span></span>
- <span data-ttu-id="a9163-3187">**udp_bytes_sent**: puntero al destino para el número total de bytes UDP enviados en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3187">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent on socket.</span></span>
- <span data-ttu-id="a9163-3188">**udp_packets_received**: puntero al destino del número total de paquetes UDP recibidos en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3188">**udp_packets_received** Pointer to destination of the total number of UDP packets received on socket.</span></span>
- <span data-ttu-id="a9163-3189">**udp_bytes_received**: puntero al destino del número total de bytes UDP recibidos en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3189">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received on socket.</span></span>
- <span data-ttu-id="a9163-3190">**udp_packets_queued**: puntero al destino del número total de paquetes UDP en cola en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3190">**udp_packets_queued** Pointer to destination of the total number of queued UDP packets on socket.</span></span>
- <span data-ttu-id="a9163-3191">**udp_receive_packets_dropped**: puntero al destino del número total de paquetes de recepción UDP anulados para el socket debido a que se superó el tamaño de la cola.</span><span class="sxs-lookup"><span data-stu-id="a9163-3191">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped for socket due to queue size being exceeded.</span></span>
- <span data-ttu-id="a9163-3192">**udp_checksum_errors**: puntero al destino del número total de paquetes UDP con errores de suma de comprobación en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3192">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors on socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3193">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3193">Return Values</span></span>

- <span data-ttu-id="a9163-3194">**NX_SUCCESS**: (0x00) la información del socket UDP se recuperó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3194">**NX_SUCCESS** (0x00) Successful UDP socket information retrieval.</span></span>
- <span data-ttu-id="a9163-3195">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3195">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-3196">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3196">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-3197">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3197">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3198">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3198">Allowed From</span></span>

<span data-ttu-id="a9163-3199">Inicialización, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="a9163-3199">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3200">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3200">Preemption Possible</span></span>

<span data-ttu-id="a9163-3201">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3201">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3202">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3202">Example</span></span>

```C
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
    &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_queued_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="a9163-3203">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3203">See Also</span></span>

- <span data-ttu-id="a9163-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3205">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3205">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="a9163-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="a9163-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="a9163-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="a9163-3211">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3211">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_port_get"></a><span data-ttu-id="a9163-3212">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="a9163-3212">nx_udp_socket_port_get</span></span>

<span data-ttu-id="a9163-3213">Recoge el número de puerto enlazado al socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3213">Pick up port number bound to UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3214">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3214">Prototype</span></span>

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-3215">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3215">Description</span></span>

<span data-ttu-id="a9163-3216">Este servicio recupera el número de puerto asociado al socket, lo que resulta útil para buscar el puerto asignado por NetX en situaciones en las que se especificó el elemento NX_ANY_PORT cuando se enlazó el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3216">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3217">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3217">Parameters</span></span>

- <span data-ttu-id="a9163-3218">**socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3218">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="a9163-3219">**port_ptr**: puntero al destino del número de puerto de devolución.</span><span class="sxs-lookup"><span data-stu-id="a9163-3219">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="a9163-3220">Los números de puerto válidos son (1- 0XFFFF).</span><span class="sxs-lookup"><span data-stu-id="a9163-3220">Valid port numbers are (1- 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3221">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3221">Return Values</span></span>

- <span data-ttu-id="a9163-3222">**NX_SUCCESS**: (0x00) el socket se enlazó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3222">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="a9163-3223">**NX_NOT_BOUND** (0X24) este socket no está enlazado a ningún puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-3223">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="a9163-3224">**NX_PTR_ERROR**: (0x07) el puntero de socket o de devolución de puerto no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-3224">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="a9163-3225">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3225">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-3226">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3226">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3227">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3227">Allowed From</span></span>

<span data-ttu-id="a9163-3228">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-3228">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3229">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3229">Preemption Possible</span></span>

<span data-ttu-id="a9163-3230">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3230">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3231">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3231">Example</span></span>

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-3232">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3232">See Also</span></span>

- <span data-ttu-id="a9163-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3234">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3234">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="a9163-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="a9163-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="a9163-3240">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3240">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive"></a><span data-ttu-id="a9163-3241">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="a9163-3241">nx_udp_socket_receive</span></span>

<span data-ttu-id="a9163-3242">Recibe el datagrama del socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3242">Receive datagram from UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3243">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3243">Prototype</span></span>

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a9163-3244">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3244">Description</span></span>

<span data-ttu-id="a9163-3245">Este servicio recibe un datagrama UDP del socket especificado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3245">This service receives an UDP datagram from the specified socket.</span></span> <span data-ttu-id="a9163-3246">Si no hay ningún datagrama en cola en el socket especificado, el autor de llamada se suspende en función de la opción de espera proporcionada.</span><span class="sxs-lookup"><span data-stu-id="a9163-3246">If no datagram is queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="a9163-3247">*Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite.*</span><span class="sxs-lookup"><span data-stu-id="a9163-3247">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3248">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3248">Parameters</span></span>

- <span data-ttu-id="a9163-3249">**socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3249">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="a9163-3250">**packet_ptr**: puntero al puntero de paquete de datagrama UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3250">**packet_ptr** Pointer to UDP datagram packet pointer.</span></span>
- <span data-ttu-id="a9163-3251">**wait_option**: define cómo se comporta el servicio si no hay ningún datagrama en la cola de este socket actualmente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3251">**wait_option** Defines how the service behaves if a datagram is not currently queued on this socket.</span></span> <span data-ttu-id="a9163-3252">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="a9163-3252">The wait options are defined as follows:</span></span>
- <span data-ttu-id="a9163-3253">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="a9163-3253">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="a9163-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="a9163-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="a9163-3255">Valor de tiempo de espera en tics (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="a9163-3255">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3256">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3256">Allowed From</span></span>

<span data-ttu-id="a9163-3257">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-3257">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3258">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3258">Preemption Possible</span></span>

<span data-ttu-id="a9163-3259">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3259">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3260">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3260">Example</span></span>

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-3261">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3261">See Also</span></span>

- <span data-ttu-id="a9163-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3263">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3263">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="a9163-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="a9163-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="a9163-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="a9163-3269">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3269">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="a9163-3270">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="a9163-3270">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="a9163-3271">Notifica a la aplicación cada paquete recibido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3271">Notify application of each received packet</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3272">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3272">Prototype</span></span>

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="a9163-3273">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3273">Description</span></span>

<span data-ttu-id="a9163-3274">Este servicio define el puntero de función de notificación de recepción a la función de devolución de llamada especificada por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a9163-3274">This service sets the receive notify function pointer to the callback function specified by the application.</span></span> <span data-ttu-id="a9163-3275">A continuación, se llama a esta función de devolución de llamada siempre que se recibe un paquete en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3275">This callback function is then called whenever a packet is received on the socket.</span></span> <span data-ttu-id="a9163-3276">Si se proporciona un puntero NX_NULL, la función de notificación de recepción se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="a9163-3276">If a NX_NULL pointer is supplied, the receive notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3277">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3277">Parameters</span></span>

- <span data-ttu-id="a9163-3278">**socket_ptr**: puntero al socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3278">**socket_ptr** Pointer to the UDP socket.</span></span>
- <span data-ttu-id="a9163-3279">**udp_receive_notify**: puntero de función de devolución de llamada de aplicación al que se llama cuando se recibe un paquete en el socket.</span><span class="sxs-lookup"><span data-stu-id="a9163-3279">**udp_receive_notify** Application callback function pointer that is called when a packet is received on the socket.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3280">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3280">Allowed From</span></span>

<span data-ttu-id="a9163-3281">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="a9163-3281">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3282">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3282">Preemption Possible</span></span>

<span data-ttu-id="a9163-3283">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3283">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3284">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3284">Example</span></span>

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a><span data-ttu-id="a9163-3285">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3285">See Also</span></span>

- <span data-ttu-id="a9163-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3287">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3287">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="a9163-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="a9163-3293">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3293">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_send"></a><span data-ttu-id="a9163-3294">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="a9163-3294">nx_udp_socket_send</span></span>

<span data-ttu-id="a9163-3295">Envía un datagrama UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3295">Send a UDP Datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3296">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3296">Prototype</span></span>

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="a9163-3297">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3297">Description</span></span>

<span data-ttu-id="a9163-3298">Este servicio envía un datagrama UDP a través de un socket UDP previamente creado y enlazado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3298">This service sends a UDP datagram through a previously created and bound UDP socket.</span></span> <span data-ttu-id="a9163-3299">NetX encuentra una dirección IP local adecuada como dirección de origen según la dirección IP de destino.</span><span class="sxs-lookup"><span data-stu-id="a9163-3299">NetX finds a suitable local IP address as source address based on the destination IP address.</span></span> <span data-ttu-id="a9163-3300">Para especificar una interfaz específica y una dirección IP de origen, la aplicación debe usar el servicio **nx_udp_socket_interface_send**.</span><span class="sxs-lookup"><span data-stu-id="a9163-3300">To specify a specific interface and source IP address, the application should use the **nx_udp_socket_interface_send** service.</span></span>

<span data-ttu-id="a9163-3301">Tenga en cuenta que este servicio se devuelve de manera inmediata, independientemente de si el datagrama UDP se envió correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3301">Note that this service returns immediately regardless of whether the UDP datagram was successfully sent.</span></span>

<span data-ttu-id="a9163-3302">El socket debe estar enlazado a un puerto local.</span><span class="sxs-lookup"><span data-stu-id="a9163-3302">The socket must be bound to a local port.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3303">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3303">Parameters</span></span>

- <span data-ttu-id="a9163-3304">**socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3304">**socket_ptr** Pointer to previously created UDP socket instance</span></span>
- <span data-ttu-id="a9163-3305">**packet_ptr**: puntero de paquete de datagrama UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3305">**packet_ptr** UDP datagram packet pointer</span></span>
- <span data-ttu-id="a9163-3306">**ip_address**: dirección IP de destino.</span><span class="sxs-lookup"><span data-stu-id="a9163-3306">**ip_address** Destination IP address</span></span>
- <span data-ttu-id="a9163-3307">**port**: número de puerto de destino válido entre 1 y 0xFFFF, en el orden de bytes del host.</span><span class="sxs-lookup"><span data-stu-id="a9163-3307">**port** Valid destination port number between 1 and 0xFFFF), in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3308">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3308">Return Values</span></span>

- <span data-ttu-id="a9163-3309">**NX_SUCCESS**: (0x00) el socket UDP se envió correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3309">**NX_SUCCESS** (0x00) Successful UDP socket send</span></span>
- <span data-ttu-id="a9163-3310">**NX_NOT_BOUND**: (0x24) el socket no se enlazó a ningún puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-3310">**NX_NOT_BOUND** (0x24) Socket not bound to any port</span></span>
- <span data-ttu-id="a9163-3311">**NX_NO_INTERFACE_ADDRESS**: (0x50) no se pudo encontrar ninguna interfaz de salida adecuada.</span><span class="sxs-lookup"><span data-stu-id="a9163-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface can be found.</span></span>
- <span data-ttu-id="a9163-3312">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP del servidor no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-3312">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address</span></span>
- <span data-ttu-id="a9163-3313">**NX_UNDERFLOW**: (0X02) no hay suficiente espacio para el encabezado UDP en el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-3313">**NX_UNDERFLOW** (0x02) Not enough room for UDP header in the packet</span></span>
- <span data-ttu-id="a9163-3314">**NX_OVERFLOW**: (0x03) el puntero para anexar paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3314">**NX_OVERFLOW** (0x03) Packet append pointer is invalid</span></span>
- <span data-ttu-id="a9163-3315">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3315">**NX_PTR_ERROR** (0x07) Invalid socket pointer</span></span>
- <span data-ttu-id="a9163-3316">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3316">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="a9163-3317">**NX_NOT_ENABLED**: (0x14) no se habilitó UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3317">**NX_NOT_ENABLED** (0x14) UDP has not been enabled</span></span>
- <span data-ttu-id="a9163-3318">**NX_INVALID_PORT**: (0x46) el número de puerto no está dentro de un intervalo válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3318">**NX_INVALID_PORT** (0x46) Port number is not within a valid range</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3319">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3319">Allowed From</span></span>

<span data-ttu-id="a9163-3320">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-3320">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3321">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3321">Preemption Possible</span></span>

<span data-ttu-id="a9163-3322">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3322">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3323">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3323">Example</span></span>

```C
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
    server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
    the packet out the UDP socket to its peer. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-3324">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3324">See Also</span></span>

- <span data-ttu-id="a9163-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3326">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3326">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="a9163-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="a9163-3332">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3332">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_interface_send"></a><span data-ttu-id="a9163-3333">nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="a9163-3333">nx_udp_socket_interface_send</span></span>

<span data-ttu-id="a9163-3334">Envía un datagrama a través de un socket UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3334">Send datagram through UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3335">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3335">Prototype</span></span>

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a><span data-ttu-id="a9163-3336">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3336">Description</span></span>

<span data-ttu-id="a9163-3337">Este servicio envía un datagrama UDP a través de un socket UDP creado y enlazado previamente a través de la interfaz de red con la dirección IP especificada como dirección de origen.</span><span class="sxs-lookup"><span data-stu-id="a9163-3337">This service sends a UDP datagram through a previously created and bound UDP socket through the network interface with the specified IP address as the source address.</span></span> <span data-ttu-id="a9163-3338">Tenga en cuenta que el servicio se devuelve de manera inmediata, independientemente de si el datagrama UDP se envió correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="a9163-3338">Note that service returns immediately, regardless of whether or not the UDP datagram was successfully sent.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3339">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3339">Parameters</span></span>

- <span data-ttu-id="a9163-3340">**socket_ptr**: socket en el que se va a transmitir el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-3340">**socket_ptr** Socket to transmit the packet out on.</span></span>
- <span data-ttu-id="a9163-3341">**packet_ptr**: puntero al paquete que se va a transmitir.</span><span class="sxs-lookup"><span data-stu-id="a9163-3341">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="a9163-3342">**ip_address**: dirección IP de destino a la que se enviará el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-3342">**ip_address** Destination IP address to send packet.</span></span>
- <span data-ttu-id="a9163-3343">**port**: puerto de destino.</span><span class="sxs-lookup"><span data-stu-id="a9163-3343">**port** Destination port.</span></span>
- <span data-ttu-id="a9163-3344">**address_index**: índice de la dirección asociada con la interfaz en la que se va a enviar el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-3344">**address_index** Index of the address associated with the interface to send packet on.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3345">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3345">Return Values</span></span>

- <span data-ttu-id="a9163-3346">**NX_SUCCESS**: (0x00) se envió correctamente el paquete.</span><span class="sxs-lookup"><span data-stu-id="a9163-3346">**NX_SUCCESS** (0x00) Packet successfully sent.</span></span>
- <span data-ttu-id="a9163-3347">**NX_NOT_BOUND**: (0x24) el socket no se enlazó a ningún puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-3347">**NX_NOT_BOUND** (0x24) Socket not bound to a port.</span></span>
- <span data-ttu-id="a9163-3348">**NX_IP_ADDRESS_ERROR**: (0x21) la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="a9163-3348">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="a9163-3349">**NX_NOT_ENABLED**: (0x14) el procesamiento de UDP no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3349">**NX_NOT_ENABLED** (0x14) UDP processing not enabled.</span></span>
- <span data-ttu-id="a9163-3350">**NX_PTR_ERROR**: (0x07) el puntero no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3350">**NX_PTR_ERROR** (0x07) Invalid pointer.</span></span>
- <span data-ttu-id="a9163-3351">**NX_OVERFLOW**: (0x03) el puntero para anexar paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3351">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="a9163-3352">**NX_UNDERFLOW**: (0x02) el puntero de anteposición de paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3352">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="a9163-3353">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3353">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-3354">**NX_INVALID_INTERFACE**: (0x4C) el índice de dirección no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3354">**NX_INVALID_INTERFACE** (0x4C) Invalid address index.</span></span>
- <span data-ttu-id="a9163-3355">**NX_INVALID_PORT**: (0x46) el número de puerto supera el número de puerto máximo.</span><span class="sxs-lookup"><span data-stu-id="a9163-3355">**NX_INVALID_PORT** (0x46) Port number exceeds maximum port number.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3356">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3356">Allowed From</span></span>

<span data-ttu-id="a9163-3357">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-3357">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3358">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3358">Preemption Possible</span></span>

<span data-ttu-id="a9163-3359">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3359">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3360">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3360">Example</span></span>

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-3361">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3361">See Also</span></span>

- <span data-ttu-id="a9163-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3363">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3363">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="a9163-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-3369">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="a9163-3369">nx_udp_socket_unbind</span></span>

## <a name="nx_udp_socket_unbind"></a><span data-ttu-id="a9163-3370">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="a9163-3370">nx_udp_socket_unbind</span></span>

<span data-ttu-id="a9163-3371">Desenlaza el socket UDP de un puerto UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3371">Unbind UDP socket from UDP port.</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3372">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3372">Prototype</span></span>

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="a9163-3373">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3373">Description</span></span>

<span data-ttu-id="a9163-3374">Este servicio libera el enlace entre el socket UDP y un puerto UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3374">This service releases the binding between the UDP socket and a UDP port.</span></span> <span data-ttu-id="a9163-3375">Los paquetes recibidos almacenados en la cola de recepción se liberan como parte de la operación de desenlace.</span><span class="sxs-lookup"><span data-stu-id="a9163-3375">Any received packets stored in the receive queue are released as part of the unbind operation.</span></span>

<span data-ttu-id="a9163-3376">Si hay otros subprocesos en espera de enlazar otro socket al puerto desenlazado, el primer subproceso suspendido se enlaza al nuevo puerto desenlazado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3376">If there are other threads waiting to bind another socket to the unbound port, the first suspended thread is then bound to the newly unbound port.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3377">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3377">Parameters</span></span>

- <span data-ttu-id="a9163-3378">**socket_ptr**: puntero a la instancia de socket UDP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3378">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3379">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3379">Return Values</span></span>

- <span data-ttu-id="a9163-3380">**NX_SUCCESS**: (0x00) el socket se desenlazó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3380">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="a9163-3381">**NX_NOT_BOUND**: (0x24) el socket no estaba enlazado a ningún puerto.</span><span class="sxs-lookup"><span data-stu-id="a9163-3381">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="a9163-3382">**NX_PTR_ERROR**: (0X07) el puntero de socket no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3382">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="a9163-3383">**NX_CALLER_ERROR**: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3383">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a9163-3384">**NX_NOT_ENABLED**: (0X14) este componente no se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3384">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3385">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3385">Allowed From</span></span>

<span data-ttu-id="a9163-3386">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a9163-3386">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3387">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3387">Preemption Possible</span></span>

<span data-ttu-id="a9163-3388">Sí</span><span class="sxs-lookup"><span data-stu-id="a9163-3388">Yes</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3389">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3389">Example</span></span>

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a><span data-ttu-id="a9163-3390">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3390">See Also</span></span>

- <span data-ttu-id="a9163-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3392">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3392">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="a9163-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span></span>

## <a name="nx_udp_source_extract"></a><span data-ttu-id="a9163-3399">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="a9163-3399">nx_udp_source_extract</span></span>

<span data-ttu-id="a9163-3400">Extrae la IP y el puerto de envío del datagrama UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3400">Extract IP and sending port from UDP datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="a9163-3401">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a9163-3401">Prototype</span></span>

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a><span data-ttu-id="a9163-3402">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9163-3402">Description</span></span>

<span data-ttu-id="a9163-3403">Este servicio extrae el número de puerto y la dirección IP del emisor de los encabezados IP y UDP del datagrama UDP proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a9163-3403">This service extracts the sender's IP and port number from the IP and UDP headers of the supplied UDP datagram.</span></span>

### <a name="parameters"></a><span data-ttu-id="a9163-3404">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9163-3404">Parameters</span></span>

- <span data-ttu-id="a9163-3405">**packet_ptr**: puntero de paquete de datagrama UDP.</span><span class="sxs-lookup"><span data-stu-id="a9163-3405">**packet_ptr** UDP datagram packet pointer.</span></span>
- <span data-ttu-id="a9163-3406">**ip_address**: puntero válido a la variable de dirección IP devuelta.</span><span class="sxs-lookup"><span data-stu-id="a9163-3406">**ip_address** Valid pointer to the return IP address variable.</span></span>
- <span data-ttu-id="a9163-3407">**port**: puntero válido a la variable de puerto devuelto.</span><span class="sxs-lookup"><span data-stu-id="a9163-3407">**port** Valid pointer to the return port variable.</span></span>

### <a name="return-values"></a><span data-ttu-id="a9163-3408">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a9163-3408">Return Values</span></span>

- <span data-ttu-id="a9163-3409">**NX_SUCCESS**: (0x00) el puerto o la IP de origen se extrajeron correctamente.</span><span class="sxs-lookup"><span data-stu-id="a9163-3409">**NX_SUCCESS** (0x00) Successful source IP/port extraction.</span></span>
- <span data-ttu-id="a9163-3410">**NX_INVALID_PACKET**: (0X12) el paquete proporcionado no es válido.</span><span class="sxs-lookup"><span data-stu-id="a9163-3410">**NX_INVALID_PACKET** (0x12) The supplied packet is invalid.</span></span>
- <span data-ttu-id="a9163-3411">**NX_PTR_ERROR**: (0x07) el paquete, la IP o el puerto de destino no son válidos.</span><span class="sxs-lookup"><span data-stu-id="a9163-3411">**NX_PTR_ERROR** (0x07) Invalid packet or IP or port destination.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a9163-3412">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a9163-3412">Allowed From</span></span>

<span data-ttu-id="a9163-3413">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="a9163-3413">Initialization, threads, timers, ISR</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="a9163-3414">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="a9163-3414">Preemption Possible</span></span>

<span data-ttu-id="a9163-3415">No</span><span class="sxs-lookup"><span data-stu-id="a9163-3415">No</span></span>

### <a name="example"></a><span data-ttu-id="a9163-3416">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a9163-3416">Example</span></span>

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a><span data-ttu-id="a9163-3417">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9163-3417">See Also</span></span>

- <span data-ttu-id="a9163-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="a9163-3419">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="a9163-3419">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="a9163-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="a9163-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="a9163-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="a9163-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="a9163-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="a9163-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="a9163-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="a9163-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="a9163-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="a9163-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="a9163-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="a9163-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span></span>