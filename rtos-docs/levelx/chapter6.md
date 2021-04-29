---
title: 'Capítulo 6: API NOR de Azure RTOS LevelX'
description: Información sobre las API NOR de Azure RTOS LevelX disponibles para la aplicación.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ab7d3a7e431d7c8f49ef4f5cab9216dc77c8d33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815421"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a><span data-ttu-id="16159-103">Capítulo 6: API NOR de Azure RTOS LevelX</span><span class="sxs-lookup"><span data-stu-id="16159-103">Chapter 6 - Azure RTOS LevelX NOR APIs</span></span>

<span data-ttu-id="16159-104">Las funciones de las API NOR de Azure RTOS LevelX disponibles para la aplicación son las siguientes.</span><span class="sxs-lookup"><span data-stu-id="16159-104">The Azure RTOS LevelX NOR API functions available to the application are as follows.</span></span>

- <span data-ttu-id="16159-105">***lx_nor_flash_close** _: _cerrar la instancia de memoria flash NOR*</span><span class="sxs-lookup"><span data-stu-id="16159-105">***lx_nor_flash_close** _: _Close NOR flash instance*</span></span>
- <span data-ttu-id="16159-106">***lx_nor_flash_defragment** _: _desfragmentar la instancia de memoria flash NOR*</span><span class="sxs-lookup"><span data-stu-id="16159-106">***lx_nor_flash_defragment** _: _Defragment NOR flash instance*</span></span>
- <span data-ttu-id="16159-107">***lx_nor_flash_extended_cache_enable** _: _habilitar o deshabilitar la memoria caché NOR extendida*</span><span class="sxs-lookup"><span data-stu-id="16159-107">***lx_nor_flash_extended_cache_enable** _: _Enable/disable extended NOR cache*</span></span>
- <span data-ttu-id="16159-108">***lx_nor_flash_initialize** _: _inicializar la compatibilidad con memoria flash NOR*</span><span class="sxs-lookup"><span data-stu-id="16159-108">***lx_nor_flash_initialize** _: _Initialize NOR flash support*</span></span>
- <span data-ttu-id="16159-109">***lx_nor_flash_open** _: _abrir la instancia de memoria flash NOR*</span><span class="sxs-lookup"><span data-stu-id="16159-109">***lx_nor_flash_open** _: _Open NOR flash instance*</span></span>
- <span data-ttu-id="16159-110">***lx_nor_flash_partial_defragment** _: _desfragmentar parcialmente la instancia de memoria flash NOR*</span><span class="sxs-lookup"><span data-stu-id="16159-110">***lx_nor_flash_partial_defragment** _: _Partial defragment of NOR flash instance*</span></span>
- <span data-ttu-id="16159-111">***lx_nor_flash_sector_read** _: _leer un sector de memoria flash NOR*</span><span class="sxs-lookup"><span data-stu-id="16159-111">***lx_nor_flash_sector_read** _: _Read NOR flash sector*</span></span>
- <span data-ttu-id="16159-112">***lx_nor_flash_sector_release** _: _liberar un sector de memoria flash NOR*</span><span class="sxs-lookup"><span data-stu-id="16159-112">***lx_nor_flash_sector_release** _: _Release NOR flash sector*</span></span>
- <span data-ttu-id="16159-113">***lx_nor_flash_sector_write** _: _escribir un sector de memoria flash NOR*</span><span class="sxs-lookup"><span data-stu-id="16159-113">***lx_nor_flash_sector_write** _: _Write NOR flash sector*</span></span>

## <a name="lx_nor_flash_close"></a><span data-ttu-id="16159-114">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="16159-114">lx_nor_flash_close</span></span>

<span data-ttu-id="16159-115">Cerrar la instancia de memoria flash NOR</span><span class="sxs-lookup"><span data-stu-id="16159-115">Close NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="16159-116">Prototipo</span><span class="sxs-lookup"><span data-stu-id="16159-116">Prototype</span></span>

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="16159-117">Descripción</span><span class="sxs-lookup"><span data-stu-id="16159-117">Description</span></span>

<span data-ttu-id="16159-118">Este servicio cierra la instancia de memoria flash NOR abierta previamente.</span><span class="sxs-lookup"><span data-stu-id="16159-118">This service closes the previously opened NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="16159-119">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="16159-119">Input Parameters</span></span>

- <span data-ttu-id="16159-120">*nor_flash*: puntero a la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-120">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="16159-121">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="16159-121">Return Values</span></span>

- <span data-ttu-id="16159-122">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="16159-122">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="16159-123">**LX_ERROR**: (0x01) Error al cerrar la instancia de memoria flash.</span><span class="sxs-lookup"><span data-stu-id="16159-123">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="16159-124">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="16159-124">Allowed From</span></span>

<span data-ttu-id="16159-125">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="16159-125">Threads</span></span>

### <a name="example"></a><span data-ttu-id="16159-126">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="16159-126">Example</span></span>

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="16159-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="16159-127">See Also</span></span>

- <span data-ttu-id="16159-128">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-128">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="16159-129">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="16159-129">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="16159-130">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="16159-130">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="16159-131">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="16159-131">lx_nor_flash_open</span></span>
- <span data-ttu-id="16159-132">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-132">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="16159-133">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="16159-133">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="16159-134">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="16159-134">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="16159-135">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="16159-135">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_defragment"></a><span data-ttu-id="16159-136">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-136">lx_nor_flash_defragment</span></span>

<span data-ttu-id="16159-137">Desfragmentar la instancia de flash NOR</span><span class="sxs-lookup"><span data-stu-id="16159-137">Defragment NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="16159-138">Prototipo</span><span class="sxs-lookup"><span data-stu-id="16159-138">Prototype</span></span>

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="16159-139">Descripción</span><span class="sxs-lookup"><span data-stu-id="16159-139">Description</span></span>

<span data-ttu-id="16159-140">Este servicio desfragmenta la instancia de memoria flash NOR abierta previamente.</span><span class="sxs-lookup"><span data-stu-id="16159-140">This service defragments the previously opened NOR flash instance.</span></span> <span data-ttu-id="16159-141">El proceso de desfragmentación maximiza el número de sectores y bloques libres.</span><span class="sxs-lookup"><span data-stu-id="16159-141">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="16159-142">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="16159-142">Input Parameters</span></span>

- <span data-ttu-id="16159-143">*nor_flash*: puntero a la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-143">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="16159-144">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="16159-144">Return Values</span></span>

- <span data-ttu-id="16159-145">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="16159-145">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="16159-146">**LX_ERROR**: (0x01) Error al desfragmentar la instancia de memoria flash.</span><span class="sxs-lookup"><span data-stu-id="16159-146">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="16159-147">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="16159-147">Allowed From</span></span>

<span data-ttu-id="16159-148">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="16159-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="16159-149">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="16159-149">Example</span></span>

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="16159-150">Consulte también</span><span class="sxs-lookup"><span data-stu-id="16159-150">See Also</span></span>

- <span data-ttu-id="16159-151">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="16159-151">lx_nor_flash_close</span></span>
- <span data-ttu-id="16159-152">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="16159-152">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="16159-153">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="16159-153">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="16159-154">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="16159-154">lx_nor_flash_open</span></span>
- <span data-ttu-id="16159-155">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-155">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="16159-156">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="16159-156">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="16159-157">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="16159-157">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="16159-158">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="16159-158">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_extended_cache_enable"></a><span data-ttu-id="16159-159">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="16159-159">lx_nor_flash_extended_cache_enable</span></span>

<span data-ttu-id="16159-160">Habilitar o deshabilitar la memoria caché NOR extendida</span><span class="sxs-lookup"><span data-stu-id="16159-160">Enable/disable extended NOR cache</span></span>

### <a name="prototype"></a><span data-ttu-id="16159-161">Prototipo</span><span class="sxs-lookup"><span data-stu-id="16159-161">Prototype</span></span>

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="16159-162">Descripción</span><span class="sxs-lookup"><span data-stu-id="16159-162">Description</span></span>

<span data-ttu-id="16159-163">Este servicio implementa una capa de memoria caché de sectores NOR en RAM mediante la memoria proporcionada por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="16159-163">This service implements a NOR sector cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="16159-164">Cada 512 bytes de memoria proporcionados se traduce en un sector NOR que se puede almacenar en caché.</span><span class="sxs-lookup"><span data-stu-id="16159-164">Each 512 bytes of memory supplied translates to one NOR sector that can be cached.</span></span> <span data-ttu-id="16159-165">Los sectores almacenados en caché son los que contienen la información de control de bloques, por ejemplo, recuento de borrados, mapa de sectores libres e información de asignación de sectores.</span><span class="sxs-lookup"><span data-stu-id="16159-165">The sectors cached are those that contain the block control information, e.g., erase count, free sector map, and sector mapping information.</span></span> <span data-ttu-id="16159-166">Los sectores de datos no se almacenan en esta memoria caché.</span><span class="sxs-lookup"><span data-stu-id="16159-166">Data sectors are not stored in this cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="16159-167">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="16159-167">Input Parameters</span></span>

- <span data-ttu-id="16159-168">**nor_flash**: puntero a la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-168">**nor_flash**: NOR flash instance pointer.</span></span>  
- <span data-ttu-id="16159-169">**memory**: dirección de inicio de la memoria caché, alineada para el acceso ULONG.</span><span class="sxs-lookup"><span data-stu-id="16159-169">**memory**: Starting address for cache memory, aligned for ULONG access.</span></span> <span data-ttu-id="16159-170">Un valor LX_NULL deshabilita la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="16159-170">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="16159-171">**size**: tamaño en bytes de la memoria suministrada (debe ser múltiplo de 512 bytes).</span><span class="sxs-lookup"><span data-stu-id="16159-171">**size**: The size in bytes of the memory supplied (should be multiple of 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="16159-172">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="16159-172">Return Values</span></span>

- <span data-ttu-id="16159-173">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="16159-173">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="16159-174">**LX_ERROR**: (0x01) No hay suficiente memoria para un sector NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-174">**LX_ERROR**: (0x01) Not enough memory for one NOR sector.</span></span>
- <span data-ttu-id="16159-175">**LX_DISABLED**: (0x09) memoria caché NOR extendida deshabilitada mediante la opción de configuración.</span><span class="sxs-lookup"><span data-stu-id="16159-175">**LX_DISABLED**: (0x09) NOR extended cache disabled by configuration option.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="16159-176">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="16159-176">Allowed From</span></span>

<span data-ttu-id="16159-177">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="16159-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="16159-178">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="16159-178">Example</span></span>

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="16159-179">Consulte también</span><span class="sxs-lookup"><span data-stu-id="16159-179">See Also</span></span>

- <span data-ttu-id="16159-180">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="16159-180">lx_nor_flash_close</span></span>
- <span data-ttu-id="16159-181">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-181">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="16159-182">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="16159-182">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="16159-183">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="16159-183">lx_nor_flash_open</span></span>
- <span data-ttu-id="16159-184">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-184">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="16159-185">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="16159-185">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="16159-186">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="16159-186">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="16159-187">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="16159-187">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_initialize"></a><span data-ttu-id="16159-188">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="16159-188">lx_nor_flash_initialize</span></span>

<span data-ttu-id="16159-189">Inicializar la compatibilidad con memoria flash NOR</span><span class="sxs-lookup"><span data-stu-id="16159-189">Initialize NOR flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="16159-190">Prototipo</span><span class="sxs-lookup"><span data-stu-id="16159-190">Prototype</span></span>

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="16159-191">Descripción</span><span class="sxs-lookup"><span data-stu-id="16159-191">Description</span></span>

<span data-ttu-id="16159-192">Este servicio inicializa la compatibilidad con memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-192">This service initializes LevelX NOR flash support.</span></span> <span data-ttu-id="16159-193">Se debe llamar al servicio antes que a cualquier otra API NOR de LevelX.</span><span class="sxs-lookup"><span data-stu-id="16159-193">It must be called before any other LevelX NOR APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="16159-194">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="16159-194">Input Parameters</span></span>

- <span data-ttu-id="16159-195">**None**</span><span class="sxs-lookup"><span data-stu-id="16159-195">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="16159-196">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="16159-196">Return Values</span></span>

- <span data-ttu-id="16159-197">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="16159-197">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="16159-198">**LX_ERROR**: (0x01) Error al inicializar la compatibilidad con memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-198">**LX_ERROR**: (0x01) Error initializing NOR flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="16159-199">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="16159-199">Allowed From</span></span>

<span data-ttu-id="16159-200">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="16159-200">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="16159-201">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="16159-201">Example</span></span>

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="16159-202">Consulte también</span><span class="sxs-lookup"><span data-stu-id="16159-202">See Also</span></span>

- <span data-ttu-id="16159-203">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="16159-203">lx_nor_flash_close</span></span>
- <span data-ttu-id="16159-204">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-204">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="16159-205">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="16159-205">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="16159-206">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-206">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="16159-207">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="16159-207">lx_nor_flash_open</span></span>
- <span data-ttu-id="16159-208">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="16159-208">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="16159-209">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="16159-209">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="16159-210">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="16159-210">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_open"></a><span data-ttu-id="16159-211">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="16159-211">lx_nor_flash_open</span></span>

<span data-ttu-id="16159-212">Abrir la instancia de memoria flash NOR</span><span class="sxs-lookup"><span data-stu-id="16159-212">Open NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="16159-213">Prototipo</span><span class="sxs-lookup"><span data-stu-id="16159-213">Prototype</span></span>

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a><span data-ttu-id="16159-214">Descripción</span><span class="sxs-lookup"><span data-stu-id="16159-214">Description</span></span>

<span data-ttu-id="16159-215">Este servicio abre una instancia de memoria flash NOR con la función de inicialización del controlador y el bloque de control de memoria flash NOR especificados.</span><span class="sxs-lookup"><span data-stu-id="16159-215">This service opens a NOR flash instance with the specified NOR flash control block and driver initialization function.</span></span> <span data-ttu-id="16159-216">Tenga en cuenta que la función de inicialización del controlador es responsable de la instalación de varios punteros de función para la lectura, escritura y borrado de bloques del hardware NOR asociado a esta instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-216">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks of the NOR hardware associated with this NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="16159-217">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="16159-217">Input Parameters</span></span>

- <span data-ttu-id="16159-218">*nor_flash*: puntero a la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-218">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="16159-219">*name*: nombre de la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-219">*name*: Name of NOR flash instance.</span></span>
- <span data-ttu-id="16159-220">*nor_driver_initialize*: puntero de función a la función de inicialización del controlador de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-220">*nor_driver_initialize*: Function pointer to NOR flash driver Initialization function.</span></span> <span data-ttu-id="16159-221">Consulte el capítulo 5 de esta guía para más información sobre las responsabilidades del controlador de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-221">Please refer to Chapter 5 of this guide for more details on NOR flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="16159-222">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="16159-222">Return Values</span></span>

- <span data-ttu-id="16159-223">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="16159-223">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="16159-224">**LX_ERROR**: (0x01) Error al abrir la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-224">**LX_ERROR**: (0x01) Error opening NOR flash instance.</span></span>
- <span data-ttu-id="16159-225">**LX_NO_MEMORY**: (0x08) El controlador no proporcionó ningún búfer para leer ningún sector en RAM.</span><span class="sxs-lookup"><span data-stu-id="16159-225">**LX_NO_MEMORY**:  (0x08) Driver did not provide buffer for reading none sector into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="16159-226">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="16159-226">Allowed From</span></span>

<span data-ttu-id="16159-227">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="16159-227">Threads</span></span>

### <a name="example"></a><span data-ttu-id="16159-228">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="16159-228">Example</span></span>

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="16159-229">Consulte también</span><span class="sxs-lookup"><span data-stu-id="16159-229">See Also</span></span>

- <span data-ttu-id="16159-230">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="16159-230">lx_nor_flash_close</span></span>
- <span data-ttu-id="16159-231">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-231">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="16159-232">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="16159-232">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="16159-233">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="16159-233">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="16159-234">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-234">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="16159-235">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="16159-235">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="16159-236">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="16159-236">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="16159-237">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="16159-237">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_partial_defragment"></a><span data-ttu-id="16159-238">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-238">lx_nor_flash_partial_defragment</span></span>

<span data-ttu-id="16159-239">Desfragmentar parcialmente la instancia de memoria flash NOR</span><span class="sxs-lookup"><span data-stu-id="16159-239">Partial defragment of NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="16159-240">Prototipo</span><span class="sxs-lookup"><span data-stu-id="16159-240">Prototype</span></span>

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="16159-241">Descripción</span><span class="sxs-lookup"><span data-stu-id="16159-241">Description</span></span>

<span data-ttu-id="16159-242">Este servicio desfragmenta la instancia de memoria flash NOR abierta anteriormente hasta el número máximo de bloques especificado.</span><span class="sxs-lookup"><span data-stu-id="16159-242">This service defragments the previously opened NOR flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="16159-243">El proceso de desfragmentación maximiza el número de sectores y bloques libres.</span><span class="sxs-lookup"><span data-stu-id="16159-243">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="16159-244">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="16159-244">Input Parameters</span></span>

- <span data-ttu-id="16159-245">*nor_flash*: puntero a la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-245">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="16159-246">*max_blocks*: número máximo de bloques.</span><span class="sxs-lookup"><span data-stu-id="16159-246">*max_blocks*: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="16159-247">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="16159-247">Return Values</span></span>

- <span data-ttu-id="16159-248">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="16159-248">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="16159-249">**LX_ERROR**: (0x01) Error al desfragmentar la instancia de memoria flash.</span><span class="sxs-lookup"><span data-stu-id="16159-249">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="16159-250">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="16159-250">Allowed From</span></span>

<span data-ttu-id="16159-251">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="16159-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="16159-252">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="16159-252">Example</span></span>

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="16159-253">Consulte también</span><span class="sxs-lookup"><span data-stu-id="16159-253">See Also</span></span>

- <span data-ttu-id="16159-254">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="16159-254">lx_nor_flash_close</span></span>
- <span data-ttu-id="16159-255">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-255">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="16159-256">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="16159-256">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="16159-257">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="16159-257">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="16159-258">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="16159-258">lx_nor_flash_open</span></span>
- <span data-ttu-id="16159-259">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="16159-259">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="16159-260">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="16159-260">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="16159-261">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="16159-261">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_read"></a><span data-ttu-id="16159-262">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="16159-262">lx_nor_flash_sector_read</span></span>

<span data-ttu-id="16159-263">Leer un sector de memoria flash NOR</span><span class="sxs-lookup"><span data-stu-id="16159-263">Read NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="16159-264">Prototipo</span><span class="sxs-lookup"><span data-stu-id="16159-264">Prototype</span></span>

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="16159-265">Descripción</span><span class="sxs-lookup"><span data-stu-id="16159-265">Description</span></span>

<span data-ttu-id="16159-266">Este servicio lee el sector lógico de la instancia de memoria flash NOR y, si la operación se realiza correctamente, devuelve el contenido en el búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="16159-266">This service reads the logical sector from the NOR flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="16159-267">Tenga en cuenta que el tamaño de un sector NOR siempre de 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="16159-267">Note that NOR sector size is always 512 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="16159-268">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="16159-268">Input Parameters</span></span>

- <span data-ttu-id="16159-269">*nor_flash*: puntero a la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-269">*nor_flash* NOR flash instance pointer.</span></span>
- <span data-ttu-id="16159-270">*logical_sector*: sector lógico que se va a leer.</span><span class="sxs-lookup"><span data-stu-id="16159-270">*logical_sector*: Logical sector to read.</span></span>
- <span data-ttu-id="16159-271">*buffer*: puntero al destino del contenido del sector lógico.</span><span class="sxs-lookup"><span data-stu-id="16159-271">*buffer*: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="16159-272">Tenga en cuenta que se supone que el búfer es de 512 bytes y está alineado para el acceso ULONG.</span><span class="sxs-lookup"><span data-stu-id="16159-272">Note that the buffer is assumed to be 512 bytes and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="16159-273">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="16159-273">Return Values</span></span>

- <span data-ttu-id="16159-274">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="16159-274">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="16159-275">**LX_ERROR**: (0x01) Error al leer el sector de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-275">**LX_ERROR**: (0x01) Error reading NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="16159-276">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="16159-276">Allowed From</span></span>

<span data-ttu-id="16159-277">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="16159-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="16159-278">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="16159-278">Example</span></span>

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="16159-279">Consulte también</span><span class="sxs-lookup"><span data-stu-id="16159-279">See Also</span></span>

- <span data-ttu-id="16159-280">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="16159-280">lx_nor_flash_close</span></span>
- <span data-ttu-id="16159-281">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-281">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="16159-282">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="16159-282">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="16159-283">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="16159-283">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="16159-284">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="16159-284">lx_nor_flash_open</span></span>
- <span data-ttu-id="16159-285">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-285">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="16159-286">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="16159-286">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="16159-287">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="16159-287">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_release"></a><span data-ttu-id="16159-288">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="16159-288">lx_nor_flash_sector_release</span></span>

<span data-ttu-id="16159-289">Liberar un sector de memoria flash NOR</span><span class="sxs-lookup"><span data-stu-id="16159-289">Release NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="16159-290">Prototipo</span><span class="sxs-lookup"><span data-stu-id="16159-290">Prototype</span></span>

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="16159-291">Descripción</span><span class="sxs-lookup"><span data-stu-id="16159-291">Description</span></span>

<span data-ttu-id="16159-292">Este servicio libera la asignación del sector lógico en la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-292">This service releases the logical sector mapping in the NOR flash instance.</span></span> <span data-ttu-id="16159-293">La liberación de un sector lógico cuando no se usa hace que la nivelación del desgaste de LevelX sea más eficaz.</span><span class="sxs-lookup"><span data-stu-id="16159-293">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="16159-294">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="16159-294">Input Parameters</span></span>

- <span data-ttu-id="16159-295">*nor_flash*: puntero a la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-295">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="16159-296">*logical_sector*: sector lógico que se va a liberar.</span><span class="sxs-lookup"><span data-stu-id="16159-296">*logical_sector*: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="16159-297">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="16159-297">Return Values</span></span>

- <span data-ttu-id="16159-298">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="16159-298">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="16159-299">**LX_ERROR**: (0x01) error al escribir el sector de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-299">**LX_ERROR**: (0x01) Error NOR flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="16159-300">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="16159-300">Allowed From</span></span>

<span data-ttu-id="16159-301">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="16159-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="16159-302">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="16159-302">Example</span></span>

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="16159-303">Consulte también</span><span class="sxs-lookup"><span data-stu-id="16159-303">See Also</span></span>

- <span data-ttu-id="16159-304">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="16159-304">lx_nor_flash_close</span></span>
- <span data-ttu-id="16159-305">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-305">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="16159-306">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="16159-306">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="16159-307">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="16159-307">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="16159-308">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="16159-308">lx_nor_flash_open</span></span>
- <span data-ttu-id="16159-309">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-309">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="16159-310">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="16159-310">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="16159-311">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="16159-311">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_write"></a><span data-ttu-id="16159-312">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="16159-312">lx_nor_flash_sector_write</span></span>

<span data-ttu-id="16159-313">Escribir un sector de memoria flash NOR</span><span class="sxs-lookup"><span data-stu-id="16159-313">Write NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="16159-314">Prototipo</span><span class="sxs-lookup"><span data-stu-id="16159-314">Prototype</span></span>

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="16159-315">Descripción</span><span class="sxs-lookup"><span data-stu-id="16159-315">Description</span></span>

<span data-ttu-id="16159-316">Este servicio escribe el sector lógico especificado en la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-316">This service writes the specified logical sector in the NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="16159-317">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="16159-317">Input Parameters</span></span>

- <span data-ttu-id="16159-318">*nor_flash*: puntero a la instancia de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-318">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="16159-319">*logical_sector*: sector lógico que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="16159-319">*logical_sector*: Logical sector to write.</span></span>
- <span data-ttu-id="16159-320">*buffer*: puntero al contenido del sector lógico.</span><span class="sxs-lookup"><span data-stu-id="16159-320">*buffer*: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="16159-321">Tenga en cuenta que se supone que el búfer es de 512 bytes y está alineado para el acceso ULONG.</span><span class="sxs-lookup"><span data-stu-id="16159-321">Note that the buffer is assumed to be 512 bytes aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="16159-322">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="16159-322">Return Values</span></span>

- <span data-ttu-id="16159-323">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="16159-323">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="16159-324">**LX_NO_SECTORS**: (0x02) No hay más sectores libres disponibles para realizar la escritura.</span><span class="sxs-lookup"><span data-stu-id="16159-324">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="16159-325">**LX_ERROR**: (0x01) Error al liberar el sector de memoria flash NOR.</span><span class="sxs-lookup"><span data-stu-id="16159-325">**LX_ERROR**: (0x01) Error releasing NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="16159-326">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="16159-326">Allowed From</span></span>

<span data-ttu-id="16159-327">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="16159-327">Threads</span></span>

### <a name="example"></a><span data-ttu-id="16159-328">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="16159-328">Example</span></span>

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="16159-329">Consulte también</span><span class="sxs-lookup"><span data-stu-id="16159-329">See Also</span></span>

- <span data-ttu-id="16159-330">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="16159-330">lx_nor_flash_close</span></span>
- <span data-ttu-id="16159-331">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-331">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="16159-332">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="16159-332">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="16159-333">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="16159-333">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="16159-334">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="16159-334">lx_nor_flash_open</span></span>
- <span data-ttu-id="16159-335">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="16159-335">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="16159-336">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="16159-336">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="16159-337">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="16159-337">lx_nor_flash_sector_release</span></span>
