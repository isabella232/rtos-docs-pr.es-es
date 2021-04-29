---
title: 'Capítulo 4: API NAND de Azure RTOS LevelX'
description: Las API NAND de Azure RTOS LevelX disponibles para la aplicación.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73bb94768396b4b8461791a164a102d1f8ef159f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815429"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a><span data-ttu-id="ea7ba-103">Capítulo 4: API NAND de Azure RTOS LevelX</span><span class="sxs-lookup"><span data-stu-id="ea7ba-103">Chapter 4 - Azure RTOS LevelX NAND APIs</span></span>

<span data-ttu-id="ea7ba-104">Las API NAND de Azure RTOS LevelX disponibles para la aplicación son:</span><span class="sxs-lookup"><span data-stu-id="ea7ba-104">The Azure RTOS LevelX NAND APIs available to the application are:</span></span>

- <span data-ttu-id="ea7ba-105">***lx_nand_flash_close** _: _cerrar la instancia de memoria flash NAND*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-105">***lx_nand_flash_close** _: _Close NAND flash instance*</span></span>
- <span data-ttu-id="ea7ba-106">***lx_nand_flash_defragment** _: _desfragmentar la instancia de memoria flash NAND*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-106">***lx_nand_flash_defragment** _: _Defragment NAND flash instance*</span></span>
- <span data-ttu-id="ea7ba-107">***lx_nand_flash_extended_cache_enable** _: _habilitar o deshabilitar la memoria caché NAND extendida*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-107">***lx_nand_flash_extended_cache_enable** _: _Enable/disable extended NAND cache*</span></span>
- <span data-ttu-id="ea7ba-108">***lx_nand_flash_initialize** _: _inicializar la compatibilidad con memoria flash NAND*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-108">***lx_nand_flash_initialize** _: _Initialize NAND flash support*</span></span>
- <span data-ttu-id="ea7ba-109">***lx_nand_flash_open** _: _abrir instancia de memoria flash NAND*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-109">***lx_nand_flash_open** _: _Open NAND flash instance*</span></span>
- <span data-ttu-id="ea7ba-110">***lx_nand_flash_page_ecc_check** _: _comprobar página de errores ECC con corrección*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-110">***lx_nand_flash_page_ecc_check** _: _Check page for ECC errors with correction*</span></span>
- <span data-ttu-id="ea7ba-111">***lx_nand_flash_page_ecc_compute** _: _calcular ECC de la página*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-111">***lx_nand_flash_page_ecc_compute** _: _Computes ECC for page*</span></span>
- <span data-ttu-id="ea7ba-112">***lx_nand_flash_partial_defragment** _: _desfragmentar parcialmente la instancia de memoria flash NAND*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-112">***lx_nand_flash_partial_defragment** _: _Partial defragment of NAND flash instance*</span></span>
- <span data-ttu-id="ea7ba-113">***lx_nand_flash_sector_read** _: _leer sector de memoria flash NAND*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-113">***lx_nand_flash_sector_read** _: _Read NAND flash sector*</span></span>
- <span data-ttu-id="ea7ba-114">***lx_nand_flash_sector_release** _: _liberar sector de memoria flash NAND*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-114">***lx_nand_flash_sector_release** _: _Release NAND flash sector*</span></span>
- <span data-ttu-id="ea7ba-115">***lx_nand_flash_sector_write** _: _escribir sector de memoria flash NAND*</span><span class="sxs-lookup"><span data-stu-id="ea7ba-115">***lx_nand_flash_sector_write** _: _Write NAND flash sector*</span></span>

## <a name="lx_nand_flash_close"></a><span data-ttu-id="ea7ba-116">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-116">lx_nand_flash_close</span></span>

<span data-ttu-id="ea7ba-117">Cerrar instancia de memoria flash NAND</span><span class="sxs-lookup"><span data-stu-id="ea7ba-117">Close NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-118">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-118">Prototype</span></span>

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="ea7ba-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-119">Description</span></span>

<span data-ttu-id="ea7ba-120">Este servicio cierra la instancia de memoria flash NAND abierta previamente.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-120">This service closes the previously opened NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-121">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-121">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-122">**nand_flash**: puntero de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-122">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-123">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-123">Return Values</span></span>

- <span data-ttu-id="ea7ba-124">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-124">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ea7ba-125">**LX_ERROR**: (0x01) Error al cerrar la instancia de memoria flash.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-125">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-126">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-126">Allowed From</span></span>

<span data-ttu-id="ea7ba-127">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-127">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-128">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-128">Example</span></span>

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-129">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-129">See Also</span></span>

- <span data-ttu-id="ea7ba-130">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-130">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="ea7ba-131">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-131">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ea7ba-132">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-132">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="ea7ba-133">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-133">lx_nand_flash_open</span></span>
- <span data-ttu-id="ea7ba-134">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-134">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="ea7ba-135">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-135">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="ea7ba-136">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-136">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="ea7ba-137">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-137">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="ea7ba-138">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-138">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="ea7ba-139">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-139">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_defragment"></a><span data-ttu-id="ea7ba-140">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-140">lx_nand_flash_defragment</span></span>

<span data-ttu-id="ea7ba-141">Desfragmentar instancia de memoria flash NAND</span><span class="sxs-lookup"><span data-stu-id="ea7ba-141">Defragment NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-142">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-142">Prototype</span></span>

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="ea7ba-143">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-143">Description</span></span>

<span data-ttu-id="ea7ba-144">Este servicio desfragmenta la instancia de memoria flash NAND abierta previamente.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-144">This service defragments the previously opened NAND flash instance.</span></span> <span data-ttu-id="ea7ba-145">El proceso de desfragmentación maximiza el número de páginas y bloques libres.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-145">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-146">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-146">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-147">**nand_flash**: puntero de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-147">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-148">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-148">Return Values</span></span>

- <span data-ttu-id="ea7ba-149">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-149">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ea7ba-150">**LX_ERROR**: (0x01) Error al desfragmentar la instancia de memoria flash.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-150">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-151">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-151">Allowed From</span></span>

<span data-ttu-id="ea7ba-152">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-152">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-153">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-153">Example</span></span>

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-154">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-154">See Also</span></span>

- <span data-ttu-id="ea7ba-155">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-155">lx_nand_flash_close</span></span>
- <span data-ttu-id="ea7ba-156">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-156">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ea7ba-157">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-157">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="ea7ba-158">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-158">lx_nand_flash_open</span></span>
- <span data-ttu-id="ea7ba-159">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-159">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="ea7ba-160">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-160">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="ea7ba-161">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-161">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="ea7ba-162">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-162">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="ea7ba-163">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-163">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="ea7ba-164">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-164">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_extended_cache_enable"></a><span data-ttu-id="ea7ba-165">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-165">lx_nand_flash_extended_cache_enable</span></span>

<span data-ttu-id="ea7ba-166">Habilitar o deshabilitar la memoria caché NAND extendida</span><span class="sxs-lookup"><span data-stu-id="ea7ba-166">Enable/disable extended NAND cache</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-167">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-167">Prototype</span></span>

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="ea7ba-168">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-168">Description</span></span>

<span data-ttu-id="ea7ba-169">Este servicio implementa una capa de memoria caché en RAM mediante la memoria proporcionada por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-169">This service implements a cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="ea7ba-170">La cantidad total de memoria necesaria para la operación de caché completa se puede calcular de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="ea7ba-170">The total amount of memory required for full cache operation can be calculated as follows:</span></span>

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

<span data-ttu-id="ea7ba-171">Si la memoria proporcionada no es lo suficientemente grande como para dar cabida a toda la memoria caché NAND, esta rutina habilitará la mayor parte posible de la memoria caché flash NAND en función de la memoria suministrada.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-171">If the supplied memory is not large enough to accommodate the full NAND cache, this routine will enable as much of the NAND flash cache as possible based on the memory supplied.</span></span>

<span data-ttu-id="ea7ba-172">La memoria caché NAND se deshabilita si la dirección de memoria especificada es NULL.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-172">The NAND cache is disabled if the memory address specified is NULL.</span></span> <span data-ttu-id="ea7ba-173">Por lo tanto, la caché NAND podría usarse de manera temporal.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-173">Hence, the NAND cache maybe be used in a temporary fashion.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-174">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-174">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-175">**nand_flash**: puntero de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-175">**nand_flash**: NAND flash instance pointer.</span></span>  
- <span data-ttu-id="ea7ba-176">**memory**: dirección de inicio de la memoria caché, alineada para el acceso ULONG.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-176">**memory**: Starting address for cache memory aligned for ULONG access.</span></span> <span data-ttu-id="ea7ba-177">Un valor LX_NULL deshabilita la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-177">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="ea7ba-178">**size**: el tamaño en bytes de la memoria suministrada.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-178">**size**: The size in bytes of the memory supplied.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-179">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-179">Return Values</span></span>

- <span data-ttu-id="ea7ba-180">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-180">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ea7ba-181">**LX_ERROR**: (0x01) No hay suficiente memoria para un elemento de la memoria caché NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-181">**LX_ERROR**: (0x01) Not enough memory for one element of the NAND cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-182">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-182">Allowed From</span></span>

<span data-ttu-id="ea7ba-183">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-183">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-184">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-184">Example</span></span>

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-185">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-185">See Also</span></span>

- <span data-ttu-id="ea7ba-186">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-186">lx_nand_flash_close</span></span>
- <span data-ttu-id="ea7ba-187">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-187">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="ea7ba-188">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-188">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="ea7ba-189">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-189">lx_nand_flash_open</span></span>
- <span data-ttu-id="ea7ba-190">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-190">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="ea7ba-191">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-191">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="ea7ba-192">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-192">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="ea7ba-193">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-193">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="ea7ba-194">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-194">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="ea7ba-195">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-195">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_initialize"></a><span data-ttu-id="ea7ba-196">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-196">lx_nand_flash_initialize</span></span>

<span data-ttu-id="ea7ba-197">Inicializar la compatibilidad con la memoria flash NAND</span><span class="sxs-lookup"><span data-stu-id="ea7ba-197">Initialize NAND flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-198">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-198">Prototype</span></span>

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="ea7ba-199">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-199">Description</span></span>

<span data-ttu-id="ea7ba-200">Este servicio inicializa la compatibilidad con la memoria flash NAND de LevelX.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-200">This service initializes LevelX NAND flash support.</span></span> <span data-ttu-id="ea7ba-201">Se debe antes que a cualquier otra API NAND de LevelX.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-201">It must be called before any other LevelX NAND APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-202">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-202">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-203">**None**</span><span class="sxs-lookup"><span data-stu-id="ea7ba-203">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-204">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-204">Return Values</span></span>

- <span data-ttu-id="ea7ba-205">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-205">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ea7ba-206">**LX_ERROR**: (0x01) Error al inicializar o a la compatibilidad con flash.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-206">**LX_ERROR**: (0x01) Error initializing NAND flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-207">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-207">Allowed From</span></span>

<span data-ttu-id="ea7ba-208">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-209">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-209">Example</span></span>

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-210">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-210">See Also</span></span>

- <span data-ttu-id="ea7ba-211">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-211">lx_nand_flash_close</span></span>
- <span data-ttu-id="ea7ba-212">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-212">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="ea7ba-213">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-213">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ea7ba-214">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-214">lx_nand_flash_open</span></span>
- <span data-ttu-id="ea7ba-215">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-215">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="ea7ba-216">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-216">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="ea7ba-217">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-217">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="ea7ba-218">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-218">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="ea7ba-219">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-219">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="ea7ba-220">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-220">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_open"></a><span data-ttu-id="ea7ba-221">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-221">lx_nand_flash_open</span></span>

<span data-ttu-id="ea7ba-222">Abrir instancia de memoria flash NAND</span><span class="sxs-lookup"><span data-stu-id="ea7ba-222">Open NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-223">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-223">Prototype</span></span>

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a><span data-ttu-id="ea7ba-224">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-224">Description</span></span>

<span data-ttu-id="ea7ba-225">Este servicio abre una instancia de memoria flash NAND con la función de inicialización del controlador y el bloque de control de memoria flash NAND especificados.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-225">This service opens a NAND flash instance with the specified NAND flash control block and driver initialization function.</span></span> <span data-ttu-id="ea7ba-226">Tenga en cuenta que la función de inicialización del controlador es responsable de la instalación de varios punteros de función para la lectura, escritura y borrado de bloques o páginas del hardware NAND asociado a esta instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-226">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks/pages of the NAND hardware associated with this NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-227">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-227">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-228">**nand_flash**: puntero de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-228">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="ea7ba-229">**name**: nombre de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-229">**name**: Name of NAND flash instance.</span></span>
- <span data-ttu-id="ea7ba-230">**nand_driver_initialize**: puntero de función a la función de inicialización del controlador de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-230">**nand_driver_initialize**: Function pointer to NAND flash driver initialization function.</span></span> <span data-ttu-id="ea7ba-231">Consulte el capítulo 3 de esta guía para más información sobre las responsabilidades del controlador de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-231">Please refer to Chapter 3 of this guide for more details on NAND flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-232">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-232">Return Values</span></span>

- <span data-ttu-id="ea7ba-233">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-233">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ea7ba-234">**LX_ERROR**: (0x01) Error al abrir la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-234">**LX_ERROR**: (0x01) Error opening NAND flash instance.</span></span>
- <span data-ttu-id="ea7ba-235">**LX_NO_MEMORY**: (0x08) El controlador no proporcionó ningún búfer para leer una página en RAM.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-235">**LX_NO_MEMORY**: (0x08) Driver did not provide buffer for reading one page into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-236">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-236">Allowed From</span></span>

<span data-ttu-id="ea7ba-237">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-238">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-238">Example</span></span>

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-239">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-239">See Also</span></span>

- <span data-ttu-id="ea7ba-240">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-240">lx_nand_flash_close</span></span>
- <span data-ttu-id="ea7ba-241">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-241">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="ea7ba-242">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-242">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ea7ba-243">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-243">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="ea7ba-244">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-244">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="ea7ba-245">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-245">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="ea7ba-246">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-246">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="ea7ba-247">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-247">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="ea7ba-248">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-248">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="ea7ba-249">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-249">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_check"></a><span data-ttu-id="ea7ba-250">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-250">lx_nand_flash_page_ecc_check</span></span>

<span data-ttu-id="ea7ba-251">Comprobar página de errores ECC con corrección</span><span class="sxs-lookup"><span data-stu-id="ea7ba-251">Check page for ECC errors with correction</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-252">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-252">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="ea7ba-253">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-253">Description</span></span>

<span data-ttu-id="ea7ba-254">Este servicio comprueba la integridad del búfer de páginas NAND proporcionado con el ECC suministrado.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-254">This service verifies the integrity of the supplied NAND page buffer with the supplied ECC.</span></span> <span data-ttu-id="ea7ba-255">Se supone que el tamaño de página (definido en el puntero de instancia de memoria flash NAND) es un múltiplo de 256 bytes y el código ECC proporcionado es capaz de corregir un error de 1 bit en cada fragmento de 256 bytes de la página.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-255">Page size (defined in the NAND flash instance pointer) is assumed to be a multiple of 256-bytes and the ECC code supplied is capable of correcting a 1 bit error in each 256-byte portion of the page.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-256">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-256">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-257">**nand_flash**: puntero de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-257">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="ea7ba-258">**page_buffer**: puntero al búfer de página de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-258">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="ea7ba-259">**ecc_buffer**: puntero a ECC para la página de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-259">**ecc_buffer**: Pointer to ECC for NAND flash page.</span></span> <span data-ttu-id="ea7ba-260">Tenga en cuenta que hay 3 bytes de ECC por fragmento de 256 bytes de la página.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-260">Note that there are 3 ECC bytes per 256-byte portion of the page.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-261">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-261">Return Values</span></span>

- <span data-ttu-id="ea7ba-262">**LX_SUCCESS**: (0x00) La página NAND no contiene errores.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-262">**LX_SUCCESS**: (0x00) NAND page has no errors.</span></span>
- <span data-ttu-id="ea7ba-263">**LX_NAND_ERROR_CORRECTED**: (0x06) Se corrigieron uno o más errores de 1 bit en la página NAND, las correcciones están en el búfer de páginas.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-263">**LX_NAND_ERROR_CORRECTED**: (0x06) One or more 1-bit errors were corrected in the NAND page—correction(s) are in the page buffer.</span></span>
- <span data-ttu-id="ea7ba-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Demasiados errores para corregir en la página NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Too many errors to correct on the NAND page.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-265">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-265">Allowed From</span></span>

<span data-ttu-id="ea7ba-266">Controlador LevelX</span><span class="sxs-lookup"><span data-stu-id="ea7ba-266">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-267">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-267">Example</span></span>

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-268">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-268">See Also</span></span>

- <span data-ttu-id="ea7ba-269">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-269">lx_nand_flash_close</span></span>
- <span data-ttu-id="ea7ba-270">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-270">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="ea7ba-271">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-271">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ea7ba-272">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-272">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="ea7ba-273">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-273">lx_nand_flash_open</span></span>
- <span data-ttu-id="ea7ba-274">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-274">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="ea7ba-275">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-275">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="ea7ba-276">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-276">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="ea7ba-277">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-277">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="ea7ba-278">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-278">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_compute"></a><span data-ttu-id="ea7ba-279">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-279">lx_nand_flash_page_ecc_compute</span></span>

<span data-ttu-id="ea7ba-280">Calcular ECC para la página</span><span class="sxs-lookup"><span data-stu-id="ea7ba-280">Compute ECC for page</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-281">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-281">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="ea7ba-282">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-282">Description</span></span>

<span data-ttu-id="ea7ba-283">Este servicio calcula el ECC del búfer de página NAND proporcionado y devuelve el ECC en el búfer de ECC suministrado.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-283">This service computes the ECC of the supplied NAND page buffer and returns the ECC in the supplied ECC buffer.</span></span> <span data-ttu-id="ea7ba-284">Se supone que el tamaño de página es un múltiplo de 256 bytes (definido en el puntero de instancia de memoria flash NAND).</span><span class="sxs-lookup"><span data-stu-id="ea7ba-284">Page size is assume to be a multiple of 256-bytes (defined in the NAND flash instance pointer).</span></span> <span data-ttu-id="ea7ba-285">El código ECC se usa para comprobar la integridad de la página cuando se lea en un momento posterior.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-285">The ECC code is used to verify the integrity of the page when it is read at a later time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-286">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-286">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-287">**nand_flash**: puntero de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-287">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="ea7ba-288">**page_buffer**: puntero al búfer de página de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-288">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="ea7ba-289">**ecc_buffer**: puntero al destino de ECC de la página de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-289">**ecc_buffer**: Pointer to destination for ECC of the NAND flash page.</span></span> <span data-ttu-id="ea7ba-290">Tenga en cuenta que debe tener 3 bytes de almacenamiento de ECC por fragmento de 256 bytes de la página.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-290">Note that must be 3 bytes of ECC storage per 256-byte portion of the page.</span></span> <span data-ttu-id="ea7ba-291">Por ejemplo, una página de 2048 bytes requeriría 24 bytes para el ECC.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-291">For example, a 2048 byte page would require 24 bytes for the ECC.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-292">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-292">Return Values</span></span>

- <span data-ttu-id="ea7ba-293">**LX_SUCCESS**: (0x00) El ECC se calculó correctamente.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-293">**LX_SUCCESS**: (0x00) ECC successfully calculated.</span></span>
- <span data-ttu-id="ea7ba-294">**LX_ERROR**: (0x01) Error al calcular el ECC.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-294">**LX_ERROR**: (0x01) Error calculating ECC.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-295">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-295">Allowed From</span></span>

<span data-ttu-id="ea7ba-296">Controlador LevelX</span><span class="sxs-lookup"><span data-stu-id="ea7ba-296">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-297">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-297">Example</span></span>

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-298">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-298">See Also</span></span>

- <span data-ttu-id="ea7ba-299">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-299">lx_nand_flash_close</span></span>
- <span data-ttu-id="ea7ba-300">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-300">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="ea7ba-301">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-301">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ea7ba-302">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-302">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="ea7ba-303">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-303">lx_nand_flash_open</span></span>
- <span data-ttu-id="ea7ba-304">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-304">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="ea7ba-305">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-305">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="ea7ba-306">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-306">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="ea7ba-307">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-307">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="ea7ba-308">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-308">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_partial_defragment"></a><span data-ttu-id="ea7ba-309">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-309">lx_nand_flash_partial_defragment</span></span>

<span data-ttu-id="ea7ba-310">Desfragmentar parcialmente la instancia de memoria flash NAND</span><span class="sxs-lookup"><span data-stu-id="ea7ba-310">Partial defragment of NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-311">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-311">Prototype</span></span>

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="ea7ba-312">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-312">Description</span></span>

<span data-ttu-id="ea7ba-313">Este servicio desfragmenta la instancia de memoria flash NAND abierta anteriormente hasta el número máximo de bloques especificado.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-313">This service defragments the previously opened NAND flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="ea7ba-314">El proceso de desfragmentación maximiza el número de páginas y bloques libres.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-314">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-315">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-315">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-316">**nand_flash**: puntero de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-316">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="ea7ba-317">**max_blocks**: número máximo de bloques.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-317">**max_blocks**: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-318">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-318">Return Values</span></span>

- <span data-ttu-id="ea7ba-319">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-319">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ea7ba-320">**LX_ERROR**: (0x01) Error al desfragmentar la instancia de memoria flash.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-320">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-321">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-321">Allowed From</span></span>

<span data-ttu-id="ea7ba-322">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-322">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-323">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-323">Example</span></span>

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-324">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-324">See Also</span></span>

- <span data-ttu-id="ea7ba-325">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-325">lx_nand_flash_close</span></span>
- <span data-ttu-id="ea7ba-326">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-326">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="ea7ba-327">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-327">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ea7ba-328">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-328">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="ea7ba-329">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-329">lx_nand_flash_open</span></span>
- <span data-ttu-id="ea7ba-330">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-330">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="ea7ba-331">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-331">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="ea7ba-332">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-332">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="ea7ba-333">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-333">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="ea7ba-334">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-334">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_read"></a><span data-ttu-id="ea7ba-335">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-335">lx_nand_flash_sector_read</span></span>

<span data-ttu-id="ea7ba-336">Leer sector de memoria flash NAND</span><span class="sxs-lookup"><span data-stu-id="ea7ba-336">Read NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-337">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-337">Prototype</span></span>

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="ea7ba-338">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-338">Description</span></span>

<span data-ttu-id="ea7ba-339">Este servicio lee el sector lógico de la instancia de memoria flash NAND y, si la operación se realiza correctamente, devuelve el contenido en el búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-339">This service reads the logical sector from the NAND flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="ea7ba-340">Tenga en cuenta que el tamaño del sector NAND siempre es el tamaño de página del hardware NAND subyacente.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-340">Note that NAND sector size is always the page size of the underlying NAND hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-341">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-341">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-342">**nand_flash**: puntero de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-342">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="ea7ba-343">**logical_sector**: sector lógico que se va a leer.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-343">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="ea7ba-344">**buffer**: puntero al destino del contenido del sector lógico.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-344">**buffer**: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="ea7ba-345">Tenga en cuenta que se supone que el búfer tiene el tamaño de la página de memoria flash NAND y está alineado para el acceso ULONG.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-345">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-346">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-346">Return Values</span></span>

- <span data-ttu-id="ea7ba-347">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-347">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ea7ba-348">**LX_ERROR**: (0x01) Error al leer el sector de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-348">**LX_ERROR**: (0x01) Error reading NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-349">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-349">Allowed From</span></span>

<span data-ttu-id="ea7ba-350">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-351">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-351">Example</span></span>

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-352">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-352">See Also</span></span>

- <span data-ttu-id="ea7ba-353">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-353">lx_nand_flash_close</span></span>
- <span data-ttu-id="ea7ba-354">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-354">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="ea7ba-355">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-355">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ea7ba-356">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-356">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="ea7ba-357">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-357">lx_nand_flash_open</span></span>
- <span data-ttu-id="ea7ba-358">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-358">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="ea7ba-359">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-359">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="ea7ba-360">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-360">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="ea7ba-361">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-361">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="ea7ba-362">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-362">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_release"></a><span data-ttu-id="ea7ba-363">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-363">lx_nand_flash_sector_release</span></span>

<span data-ttu-id="ea7ba-364">Liberar sector de memoria flash NAND</span><span class="sxs-lookup"><span data-stu-id="ea7ba-364">Release NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-365">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-365">Prototype</span></span>

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="ea7ba-366">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-366">Description</span></span>

<span data-ttu-id="ea7ba-367">Este servicio libera la asignación del sector lógico en la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-367">This service releases the logical sector mapping in the NAND flash instance.</span></span> <span data-ttu-id="ea7ba-368">La liberación de un sector lógico cuando no se usa hace que la nivelación de la utilización de LevelX sea más eficaz.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-368">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-369">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-369">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-370">**nand_flash**: puntero de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-370">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="ea7ba-371">**logical_sector**: sector lógico que se va a liberar.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-371">**logical_sector**: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-372">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-372">Return Values</span></span>

- <span data-ttu-id="ea7ba-373">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-373">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ea7ba-374">**LX_ERROR**: (0x01) Error al escribir sector de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-374">**LX_ERROR**: (0x01) Error NAND flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-375">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-375">Allowed From</span></span>

<span data-ttu-id="ea7ba-376">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-376">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-377">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-377">Example</span></span>

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-378">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-378">See Also</span></span>

- <span data-ttu-id="ea7ba-379">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-379">lx_nand_flash_close</span></span>
- <span data-ttu-id="ea7ba-380">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-380">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="ea7ba-381">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-381">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ea7ba-382">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-382">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="ea7ba-383">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-383">lx_nand_flash_open</span></span>
- <span data-ttu-id="ea7ba-384">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-384">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="ea7ba-385">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-385">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="ea7ba-386">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-386">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="ea7ba-387">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-387">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="ea7ba-388">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-388">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_write"></a><span data-ttu-id="ea7ba-389">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="ea7ba-389">lx_nand_flash_sector_write</span></span>

<span data-ttu-id="ea7ba-390">Escribir sector de memoria flash NAND</span><span class="sxs-lookup"><span data-stu-id="ea7ba-390">Write NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="ea7ba-391">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-391">Prototype</span></span>

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="ea7ba-392">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea7ba-392">Description</span></span>

<span data-ttu-id="ea7ba-393">Este servicio escribe el sector lógico especificado en la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-393">This service writes the specified logical sector in the NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea7ba-394">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea7ba-394">Input Parameters</span></span>

- <span data-ttu-id="ea7ba-395">**nand_flash**: puntero de la instancia de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-395">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="ea7ba-396">**logical_sector**: sector lógico que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-396">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="ea7ba-397">**buffer**: puntero al contenido del sector lógico.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-397">**buffer**: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="ea7ba-398">Tenga en cuenta que se supone que el búfer tiene el tamaño de la página de memoria flash NAND y está alineado para el acceso ULONG.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-398">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea7ba-399">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-399">Return Values</span></span>

- <span data-ttu-id="ea7ba-400">**LX_SUCCESS**: (0x00) Solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-400">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="ea7ba-401">**LX_NO_SECTORS**: (0x02) No hay más sectores libres disponibles para realizar la escritura.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-401">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="ea7ba-402">**LX_ERROR**: (0x01) Error al liberar el sector de memoria flash NAND.</span><span class="sxs-lookup"><span data-stu-id="ea7ba-402">**LX_ERROR**: (0x01) Error releasing NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea7ba-403">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea7ba-403">Allowed From</span></span>

<span data-ttu-id="ea7ba-404">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea7ba-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea7ba-405">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea7ba-405">Example</span></span>

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="ea7ba-406">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea7ba-406">See Also</span></span>

- <span data-ttu-id="ea7ba-407">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="ea7ba-407">lx_nand_flash_close</span></span>
- <span data-ttu-id="ea7ba-408">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-408">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="ea7ba-409">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="ea7ba-409">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="ea7ba-410">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="ea7ba-410">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="ea7ba-411">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="ea7ba-411">lx_nand_flash_open</span></span>
- <span data-ttu-id="ea7ba-412">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="ea7ba-412">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="ea7ba-413">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="ea7ba-413">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="ea7ba-414">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="ea7ba-414">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="ea7ba-415">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="ea7ba-415">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="ea7ba-416">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="ea7ba-416">lx_nand_flash_sector_release</span></span>
