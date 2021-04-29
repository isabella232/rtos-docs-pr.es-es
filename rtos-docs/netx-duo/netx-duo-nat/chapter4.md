---
title: 'Capítulo 4: Descripción de los servicios NAT'
description: Este capítulo contiene una descripción de todos los servicios de la API NAT de NetX Duo en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8bdbdfcb2da6425fb99cadc7b2f6815dedc12953
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814621"
---
# <a name="chapter-4---description-of-nat-services"></a><span data-ttu-id="f1807-103">Capítulo 4: Descripción de los servicios NAT</span><span class="sxs-lookup"><span data-stu-id="f1807-103">Chapter 4 - Description of NAT services</span></span>

<span data-ttu-id="f1807-104">Este capítulo contiene una descripción de todos los servicios de la API NAT de NetX Duo (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="f1807-104">This chapter contains a description of all NetX Duo NAT API services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="f1807-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="f1807-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_nat_create"></a><span data-ttu-id="f1807-106">nx_nat_create</span><span class="sxs-lookup"><span data-stu-id="f1807-106">nx_nat_create</span></span>

<span data-ttu-id="f1807-107">Crear un servidor de NAT</span><span class="sxs-lookup"><span data-stu-id="f1807-107">Create a NAT Server</span></span>

### <a name="prototype"></a><span data-ttu-id="f1807-108">Prototipo</span><span class="sxs-lookup"><span data-stu-id="f1807-108">Prototype</span></span>

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a><span data-ttu-id="f1807-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="f1807-109">Description</span></span>

<span data-ttu-id="f1807-110">Este servicio crea una instancia del servidor de NAT.</span><span class="sxs-lookup"><span data-stu-id="f1807-110">This service creates an instance of the NAT server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f1807-111">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="f1807-111">Input Parameters</span></span>

- <span data-ttu-id="f1807-112">**nat_ptr** Puntero a la instancia de NAT que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="f1807-112">**nat_ptr** Pointer to NAT instance to create</span></span>
- <span data-ttu-id="f1807-113">**ip_ptr** Puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="f1807-113">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="f1807-114">**global_interface_index** Índice de la interfaz de red global.</span><span class="sxs-lookup"><span data-stu-id="f1807-114">**global_interface_index** Index to the global network interface</span></span>
- <span data-ttu-id="f1807-115">**dynamic_cache_memory** Área de memoria de puntero a la tabla NAT.</span><span class="sxs-lookup"><span data-stu-id="f1807-115">**dynamic_cache_memory** Pointer memory area to NAT table</span></span>
- <span data-ttu-id="f1807-116">**dynamic_cache_size** Tamaño del área de memoria para la tabla NAT.</span><span class="sxs-lookup"><span data-stu-id="f1807-116">**dynamic_cache_size** Size of memory area for NAT table</span></span>

### <a name="return-values"></a><span data-ttu-id="f1807-117">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="f1807-117">Return Values</span></span>

- <span data-ttu-id="f1807-118">**NX_SUCCESS** (0x00) Servidor NAT creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="f1807-118">**NX_SUCCESS** (0x00) NAT server successfully created</span></span>
- <span data-ttu-id="f1807-119">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="f1807-119">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="f1807-120">NX_NAT_PARAM_ERROR (0xD01) Entrada no de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="f1807-120">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>
- <span data-ttu-id="f1807-121">NX_NAT_CACHE_ERROR (0xD02) Entrada de puntero de caché no válida.</span><span class="sxs-lookup"><span data-stu-id="f1807-121">NX_NAT_CACHE_ERROR (0xD02) Invalid cache pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f1807-122">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="f1807-122">Allowed From</span></span>

<span data-ttu-id="f1807-123">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="f1807-123">Application code</span></span>

### <a name="example"></a><span data-ttu-id="f1807-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f1807-124">Example</span></span>

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a><span data-ttu-id="f1807-125">nx_nat_delete</span><span class="sxs-lookup"><span data-stu-id="f1807-125">nx_nat_delete</span></span>

<span data-ttu-id="f1807-126">Eliminar un servidor NAT</span><span class="sxs-lookup"><span data-stu-id="f1807-126">Delete a NAT Server</span></span>

### <a name="prototype"></a><span data-ttu-id="f1807-127">Prototipo</span><span class="sxs-lookup"><span data-stu-id="f1807-127">Prototype</span></span>

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="f1807-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="f1807-128">Description</span></span>

<span data-ttu-id="f1807-129">Este servicio elimina un servidor NAT creado previamente.</span><span class="sxs-lookup"><span data-stu-id="f1807-129">This service deletes a previously created NAT Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f1807-130">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="f1807-130">Input Parameters</span></span>

- <span data-ttu-id="f1807-131">**nat_ptr** Puntero a la instancia de NAT que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="f1807-131">**nat_ptr** Pointer to NAT instance to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="f1807-132">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="f1807-132">Return Values</span></span>

- <span data-ttu-id="f1807-133">**NX_SUCCESS** (0X00) Servicio NAT eliminado correctamente</span><span class="sxs-lookup"><span data-stu-id="f1807-133">**NX_SUCCESS** (0x00) NAT successfully deleted</span></span>
- <span data-ttu-id="f1807-134">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="f1807-134">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f1807-135">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="f1807-135">Allowed From</span></span>

<span data-ttu-id="f1807-136">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="f1807-136">Application code</span></span>

### <a name="example"></a><span data-ttu-id="f1807-137">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f1807-137">Example</span></span>

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a><span data-ttu-id="f1807-138">nx_nat_enable</span><span class="sxs-lookup"><span data-stu-id="f1807-138">nx_nat_enable</span></span>

<span data-ttu-id="f1807-139">Habilitar la instancia de IP para NAT</span><span class="sxs-lookup"><span data-stu-id="f1807-139">Enable the IP instance for NAT</span></span>

### <a name="prototype"></a><span data-ttu-id="f1807-140">Prototipo</span><span class="sxs-lookup"><span data-stu-id="f1807-140">Prototype</span></span>

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="f1807-141">Descripción</span><span class="sxs-lookup"><span data-stu-id="f1807-141">Description</span></span>

<span data-ttu-id="f1807-142">Este servicio habilita la instancia de IP para NAT (por ejemplo, reenviar los paquetes recibidos al servidor NAT).</span><span class="sxs-lookup"><span data-stu-id="f1807-142">This service enables the IP instance for NAT (e.g. forward received packets to the NAT server).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f1807-143">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="f1807-143">Input Parameters</span></span>

- <span data-ttu-id="f1807-144">**nat_ptr** Puntero a la instancia de NAT.</span><span class="sxs-lookup"><span data-stu-id="f1807-144">**nat_ptr** Pointer to NAT instance</span></span>

### <a name="return-values"></a><span data-ttu-id="f1807-145">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="f1807-145">Return Values</span></span>

- <span data-ttu-id="f1807-146">**NX_SUCCESS** (0X00) Servicio NAT habilitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="f1807-146">**NX_SUCCESS** (0x00) NAT successfully enabled</span></span>
- <span data-ttu-id="f1807-147">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="f1807-147">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f1807-148">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="f1807-148">Allowed From</span></span>

<span data-ttu-id="f1807-149">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="f1807-149">Application code</span></span>

### <a name="example"></a><span data-ttu-id="f1807-150">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f1807-150">Example</span></span>

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a><span data-ttu-id="f1807-151">nx_nat_disable</span><span class="sxs-lookup"><span data-stu-id="f1807-151">nx_nat_disable</span></span>

<span data-ttu-id="f1807-152">Deshabilitar la instancia de IP para NAT</span><span class="sxs-lookup"><span data-stu-id="f1807-152">Disable the IP instance for NAT</span></span>

### <a name="prototype"></a><span data-ttu-id="f1807-153">Prototipo</span><span class="sxs-lookup"><span data-stu-id="f1807-153">Prototype</span></span>

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="f1807-154">Descripción</span><span class="sxs-lookup"><span data-stu-id="f1807-154">Description</span></span>

<span data-ttu-id="f1807-155">Este servicio deshabilita NAT en la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="f1807-155">This service disables NAT on the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f1807-156">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="f1807-156">Input Parameters</span></span>

- <span data-ttu-id="f1807-157">**nat_ptr** Puntero a la instancia de NAT.</span><span class="sxs-lookup"><span data-stu-id="f1807-157">**nat_ptr** Pointer to NAT instance</span></span>

### <a name="return-values"></a><span data-ttu-id="f1807-158">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="f1807-158">Return Values</span></span>

- <span data-ttu-id="f1807-159">**NX_SUCCESS** (0X00) Servicio NAT deshabilitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="f1807-159">**NX_SUCCESS** (0x00) NAT successfully disabled</span></span>
- <span data-ttu-id="f1807-160">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="f1807-160">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f1807-161">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="f1807-161">Allowed From</span></span>

<span data-ttu-id="f1807-162">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="f1807-162">Application code</span></span>

### <a name="example"></a><span data-ttu-id="f1807-163">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f1807-163">Example</span></span>

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a><span data-ttu-id="f1807-164">nx_nat_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="f1807-164">nx_nat_cache_notify_set</span></span>

<span data-ttu-id="f1807-165">Establecer una función de devolución de llamada de notificación completa de caché</span><span class="sxs-lookup"><span data-stu-id="f1807-165">Set a cache full notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="f1807-166">Prototipo</span><span class="sxs-lookup"><span data-stu-id="f1807-166">Prototype</span></span>

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a><span data-ttu-id="f1807-167">Descripción</span><span class="sxs-lookup"><span data-stu-id="f1807-167">Description</span></span>

<span data-ttu-id="f1807-168">Este servicio registra la devolución de llamada completa de la memoria caché con el puntero de función de entrada cache_full_notify_cb que apunta a una función de notificación completa de caché definida por el usuario.</span><span class="sxs-lookup"><span data-stu-id="f1807-168">This service registers the cache full callback with the input function pointer cache_full_notify_cb which points to a user defined cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f1807-169">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="f1807-169">Input Parameters</span></span>

- <span data-ttu-id="f1807-170">**nat_ptr** Puntero a la instancia de NAT.</span><span class="sxs-lookup"><span data-stu-id="f1807-170">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="f1807-171">**cache_full_notify_cb** Puntero a la función de notificación completa de caché.</span><span class="sxs-lookup"><span data-stu-id="f1807-171">**cache_full_notify_cb** Pointer to cache full notify function</span></span>

### <a name="return-values"></a><span data-ttu-id="f1807-172">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="f1807-172">Return Values</span></span>

- <span data-ttu-id="f1807-173">**NX_SUCCESS** (0X00) Establecimiento correcto de la función de notificación completa de caché.</span><span class="sxs-lookup"><span data-stu-id="f1807-173">**NX_SUCCESS** (0x00) Cache full notify function successfully set</span></span>
- <span data-ttu-id="f1807-174">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="f1807-174">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="f1807-175">NX_NAT_PARAM_ERROR (0xD01) Entrada no de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="f1807-175">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f1807-176">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="f1807-176">Allowed From</span></span>

<span data-ttu-id="f1807-177">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="f1807-177">Application code</span></span>

### <a name="example"></a><span data-ttu-id="f1807-178">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f1807-178">Example</span></span>

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a><span data-ttu-id="f1807-179">nx_nat_inbound_entry_create</span><span class="sxs-lookup"><span data-stu-id="f1807-179">nx_nat_inbound_entry_create</span></span>

<span data-ttu-id="f1807-180">Crear una entrada en la tabla de traducción de NAT</span><span class="sxs-lookup"><span data-stu-id="f1807-180">Create an inbound entry in the NAT translation table</span></span>

### <a name="prototype"></a><span data-ttu-id="f1807-181">Prototipo</span><span class="sxs-lookup"><span data-stu-id="f1807-181">Prototype</span></span>

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a><span data-ttu-id="f1807-182">Descripción</span><span class="sxs-lookup"><span data-stu-id="f1807-182">Description</span></span>

<span data-ttu-id="f1807-183">Este servicio crea una entrada como estática (entrada permanente, nunca expira) y la agrega a la tabla de traducciones de NAT.</span><span class="sxs-lookup"><span data-stu-id="f1807-183">This service creates an inbound entry as static (permanent entry, never expires) and adds it to the NAT translation table.</span></span> <span data-ttu-id="f1807-184">Estas entradas se crean normalmente para los servidores de host locales en los que se inicia una conexión desde un host de la red externa.</span><span class="sxs-lookup"><span data-stu-id="f1807-184">These entries are usually created for local host servers where a connection is initiated from a host on the outside network.</span></span> <span data-ttu-id="f1807-185">El servidor de NAT comprueba que el puerto externo no se esté usando en la tabla de traducciones o que esté enlazado con un socket de NetX Duo anterior del mismo protocolo.</span><span class="sxs-lookup"><span data-stu-id="f1807-185">The NAT server checks that the external port is not already in use in the translation table or bound by a previously existing NetX Duo socket of the same protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f1807-186">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="f1807-186">Input Parameters</span></span>

- <span data-ttu-id="f1807-187">**nat_ptr** Puntero a la instancia de NAT.</span><span class="sxs-lookup"><span data-stu-id="f1807-187">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="f1807-188">**entry_ptr** Puntero a la entrada de traducción.</span><span class="sxs-lookup"><span data-stu-id="f1807-188">**entry_ptr** Pointer to translation entry</span></span>
- <span data-ttu-id="f1807-189">**local_ip_address** Dirección IP del host local.</span><span class="sxs-lookup"><span data-stu-id="f1807-189">**local_ip_address** Local host IP address</span></span>
- <span data-ttu-id="f1807-190">**external_port** Puerto de destino en la red externa.</span><span class="sxs-lookup"><span data-stu-id="f1807-190">**external_port** Destination port on the external network</span></span>
- <span data-ttu-id="f1807-191">**local_port** Puerto de origen (host local).</span><span class="sxs-lookup"><span data-stu-id="f1807-191">**local_port** Source (local host) port</span></span>
- <span data-ttu-id="f1807-192">**protocol** Protocolo de paquetes (por ejemplo, TCP).</span><span class="sxs-lookup"><span data-stu-id="f1807-192">**protocol** Packet protocol (e.g TCP)</span></span>

### <a name="return-values"></a><span data-ttu-id="f1807-193">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="f1807-193">Return Values</span></span>

- <span data-ttu-id="f1807-194">**NX_SUCCESS**: (0x00) Entrada creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="f1807-194">**NX_SUCCESS** (0x00) Entry successfully created</span></span>
- <span data-ttu-id="f1807-195">**NX_NAT_PORT_UNAVAILABLE** (0xD0D) Puerto externo no válido.</span><span class="sxs-lookup"><span data-stu-id="f1807-195">**NX_NAT_PORT_UNAVAILABLE** (0xD0D) Invalid external port</span></span>
- <span data-ttu-id="f1807-196">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="f1807-196">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="f1807-197">NX_NAT_PARAM_ERROR (0xD01) Entrada no de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="f1807-197">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f1807-198">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="f1807-198">Allowed From</span></span>

<span data-ttu-id="f1807-199">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="f1807-199">Application code</span></span>

### <a name="example"></a><span data-ttu-id="f1807-200">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f1807-200">Example</span></span>

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a><span data-ttu-id="f1807-201">nx_nat_inbound_entry_delete</span><span class="sxs-lookup"><span data-stu-id="f1807-201">nx_nat_inbound_entry_delete</span></span>

<span data-ttu-id="f1807-202">Eliminar una entrada en la tabla de traducciones de NAT</span><span class="sxs-lookup"><span data-stu-id="f1807-202">Delete an inbound entry in the NAT translation table</span></span>

### <a name="prototype"></a><span data-ttu-id="f1807-203">Prototipo</span><span class="sxs-lookup"><span data-stu-id="f1807-203">Prototype</span></span>

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a><span data-ttu-id="f1807-204">Descripción</span><span class="sxs-lookup"><span data-stu-id="f1807-204">Description</span></span>

<span data-ttu-id="f1807-205">Este servicio elimina la entrada especificada de la tabla de traducción.</span><span class="sxs-lookup"><span data-stu-id="f1807-205">This service deletes the specified inbound entry from the translation table.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="f1807-206">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="f1807-206">Input Parameters</span></span>

- <span data-ttu-id="f1807-207">**nat_ptr** Puntero a la instancia de NAT.</span><span class="sxs-lookup"><span data-stu-id="f1807-207">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="f1807-208">**delete_entry_ptr** Puntero a la entrada de traducciones de NAT.</span><span class="sxs-lookup"><span data-stu-id="f1807-208">**delete_entry_ptr** Pointer to the NAT translation entry</span></span>

### <a name="return-values"></a><span data-ttu-id="f1807-209">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="f1807-209">Return Values</span></span>

- <span data-ttu-id="f1807-210">**NX_SUCCESS**: (0x00) Entrada eliminada correctamente.</span><span class="sxs-lookup"><span data-stu-id="f1807-210">**NX_SUCCESS** (0x00) Entry successfully deleted</span></span>
- <span data-ttu-id="f1807-211">**NX_NAT_ENTRY_NOT_FOUND** (0xD04) Entrada no encontrada.</span><span class="sxs-lookup"><span data-stu-id="f1807-211">**NX_NAT_ENTRY_NOT_FOUND** (0xD04) Entry does not found</span></span>
- <span data-ttu-id="f1807-212">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="f1807-212">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="f1807-213">NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Tipo de traducción no válido.</span><span class="sxs-lookup"><span data-stu-id="f1807-213">NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Invalid translation type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f1807-214">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="f1807-214">Allowed From</span></span>

<span data-ttu-id="f1807-215">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="f1807-215">Application code</span></span>

### <a name="example"></a><span data-ttu-id="f1807-216">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f1807-216">Example</span></span>

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```