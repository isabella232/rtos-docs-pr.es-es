---
title: 'Capítulo 2: Instalación y uso de Azure RTOS LevelX'
description: La instalación y el uso de LevelX son sencillos y se describen en las siguientes secciones de este capítulo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 34110e74e8ad0a6acd376c00c1284a3ea715c5f5
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223322"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a><span data-ttu-id="04586-103">Capítulo 2: Instalación y uso de Azure RTOS LevelX</span><span class="sxs-lookup"><span data-stu-id="04586-103">Chapter 2 - Installation and use of Azure RTOS LevelX</span></span>

<span data-ttu-id="04586-104">La instalación y el uso de Azure RTOS LevelX son sencillos y se describen en las siguientes secciones de este capítulo.</span><span class="sxs-lookup"><span data-stu-id="04586-104">Installation and use of Azure RTOS LevelX is straightforward and described in the following sections of this chapter.</span></span>

## <a name="distribution"></a><span data-ttu-id="04586-105">Distribución</span><span class="sxs-lookup"><span data-stu-id="04586-105">Distribution</span></span>

<span data-ttu-id="04586-106">LevelX se distribuye en ANSI C, donde cada función se encuentra en su propio archivo de C independiente.</span><span class="sxs-lookup"><span data-stu-id="04586-106">LevelX is distributed in ANSI C where each function is contained in its own separate C file.</span></span> <span data-ttu-id="04586-107">Los archivos de la distribución de LevelX son los siguientes.</span><span class="sxs-lookup"><span data-stu-id="04586-107">The files in the LevelX distribution are as follows.</span></span>
- <span data-ttu-id="04586-108">lx_api.h</span><span class="sxs-lookup"><span data-stu-id="04586-108">lx_api.h</span></span>
- <span data-ttu-id="04586-109">lx_nand_flash_256byte_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="04586-109">lx_nand_flash_256byte_ecc_check.c</span></span>
- <span data-ttu-id="04586-110">lx_nand_flash_256byte_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="04586-110">lx_nand_flash_256byte_ecc_compute.c</span></span>
- <span data-ttu-id="04586-111">lx_nand_flash_block_full_update.c</span><span class="sxs-lookup"><span data-stu-id="04586-111">lx_nand_flash_block_full_update.c</span></span>
- <span data-ttu-id="04586-112">lx_nand_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="04586-112">lx_nand_flash_block_reclaim.c</span></span>
- <span data-ttu-id="04586-113">lx_nand_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="04586-113">lx_nand_flash_close.c</span></span>
- <span data-ttu-id="04586-114">lx_nand_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="04586-114">lx_nand_flash_defragment.c</span></span>  
- <span data-ttu-id="04586-115">lx_nand_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="04586-115">lx_nand_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="04586-116">lx_nand_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="04586-116">lx_nand_flash_initialize.c</span></span>
- <span data-ttu-id="04586-117">lx_nand_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="04586-117">lx_nand_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="04586-118">lx_nand_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="04586-118">lx_nand_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="04586-119">lx_nand_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="04586-119">lx_nand_flash_open.c</span></span>
- <span data-ttu-id="04586-120">lx_nand_flash_page_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="04586-120">lx_nand_flash_page_ecc_check.c</span></span>
- <span data-ttu-id="04586-121">lx_nand_flash_page_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="04586-121">lx_nand_flash_page_ecc_compute.c</span></span>  
- <span data-ttu-id="04586-122">lx_nand_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="04586-122">lx_nand_flash_partial_defragment.c</span></span>
- <span data-ttu-id="04586-123">lx_nand_flash_physical_page_allocate.c</span><span class="sxs-lookup"><span data-stu-id="04586-123">lx_nand_flash_physical_page_allocate.c</span></span>
- <span data-ttu-id="04586-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="04586-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="04586-125">lx_nand_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="04586-125">lx_nand_flash_sector_read.c</span></span>
- <span data-ttu-id="04586-126">lx_nand_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="04586-126">lx_nand_flash_sector_release.c</span></span>
- <span data-ttu-id="04586-127">lx_nand_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="04586-127">lx_nand_flash_sector_write.c</span></span>
- <span data-ttu-id="04586-128">lx_nand_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="04586-128">lx_nand_flash_system_error.c</span></span>
- <span data-ttu-id="04586-129">lx_nor_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="04586-129">lx_nor_flash_block_reclaim.c</span></span>
- <span data-ttu-id="04586-130">lx_nor_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="04586-130">lx_nor_flash_close.c</span></span>
- <span data-ttu-id="04586-131">lx_nor_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="04586-131">lx_nor_flash_defragment.c</span></span>  
- <span data-ttu-id="04586-132">lx_nor_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="04586-132">lx_nor_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="04586-133">lx_nor_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="04586-133">lx_nor_flash_initialize.c</span></span>
- <span data-ttu-id="04586-134">lx_nor_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="04586-134">lx_nor_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="04586-135">lx_nor_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="04586-135">lx_nor_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="04586-136">lx_nor_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="04586-136">lx_nor_flash_open.c</span></span>
- <span data-ttu-id="04586-137">lx_nor_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="04586-137">lx_nor_flash_partial_defragment.c</span></span>
- <span data-ttu-id="04586-138">lx_nor_flash_physical_sector_allocate.c</span><span class="sxs-lookup"><span data-stu-id="04586-138">lx_nor_flash_physical_sector_allocate.c</span></span>
- <span data-ttu-id="04586-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="04586-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="04586-140">lx_nor_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="04586-140">lx_nor_flash_sector_read.c</span></span>
- <span data-ttu-id="04586-141">lx_nor_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="04586-141">lx_nor_flash_sector_release.c</span></span>
- <span data-ttu-id="04586-142">lx_nor_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="04586-142">lx_nor_flash_sector_write.c</span></span>
- <span data-ttu-id="04586-143">lx_nor_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="04586-143">lx_nor_flash_system_error.c</span></span>

<span data-ttu-id="04586-144">También hay ejemplos de controladores de simulador y FileX, tanto para instancias de NAND de LevelX como para instancias de NOR, como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="04586-144">There are also simulator and FileX driver samples for both LevelX NAND and NOR instances, as follows.</span></span>

- <span data-ttu-id="04586-145">demo_filex_nand_flash.c</span><span class="sxs-lookup"><span data-stu-id="04586-145">demo_filex_nand_flash.c</span></span>  
- <span data-ttu-id="04586-146">fx_nand_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="04586-146">fx_nand_flash_simulated_driver.c</span></span>
- <span data-ttu-id="04586-147">lx_nand_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="04586-147">lx_nand_flash_simulator.c</span></span>
- <span data-ttu-id="04586-148">demo_filex_nor_flash.c</span><span class="sxs-lookup"><span data-stu-id="04586-148">demo_filex_nor_flash.c</span></span>  
- <span data-ttu-id="04586-149">fx_nor_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="04586-149">fx_nor_flash_simulated_driver.c</span></span>
- <span data-ttu-id="04586-150">lx_nor_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="04586-150">lx_nor_flash_simulator.c</span></span>

<span data-ttu-id="04586-151">Por supuesto, si solo se requiere memoria flash NAND, solo se necesitan los archivos para memoria flash NAND de LevelX (***lx_nand_\*.c***).</span><span class="sxs-lookup"><span data-stu-id="04586-151">Of course, if only NAND flash is required, only the LevelX NAND flash files (***lx_nand_\*.c***) are needed.</span></span> <span data-ttu-id="04586-152">Del mismo modo, si solo se requiere memoria flash NOR, solo se necesitan los archivos para memoria flash NOR (\*\*_lx_nor_\_.c\*\*\*).</span><span class="sxs-lookup"><span data-stu-id="04586-152">Similarly, if only NOR flash is required, only the NOR flash files (\*\*_lx_nor_\_.c\*\*\*) are needed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="04586-153">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="04586-153">Configuration Options</span></span>

<span data-ttu-id="04586-154">LevelX se puede configurar en tiempo de compilación mediante las definiciones condicionales que se describen a continuación.</span><span class="sxs-lookup"><span data-stu-id="04586-154">LevelX can be configured at compile time via the conditional defines described below.</span></span> <span data-ttu-id="04586-155">Basta con agregar la definición deseada a la compilación de cada código fuente de LevelX para utilizar la opción.</span><span class="sxs-lookup"><span data-stu-id="04586-155">Simply add the desired define to the compilation of each LevelX source to use the option.</span></span>

- <span data-ttu-id="04586-156">**LX_DIRECT_READ**: definido, esta opción omite la rutina de lectura del controlador de memoria flash NOR para favorecer o leer directamente la memoria NOR, lo que da lugar a un aumento significativo del rendimiento.</span><span class="sxs-lookup"><span data-stu-id="04586-156">**LX_DIRECT_READ**:  Defined, this option bypasses the NOR flash driver read routine in favor or reading the NOR memory directly, resulting in a significant performance increase.</span></span>
- <span data-ttu-id="04586-157">**LX_FREE_SECTOR_DATA_VERIFY**: definido, esto hace que la lógica de apertura de la instancia de NOR de LevelX compruebe que los sectores NOR libres son todos unos.</span><span class="sxs-lookup"><span data-stu-id="04586-157">**LX_FREE_SECTOR_DATA_VERIFY**: Defined, this causes the LevelX NOR instance open logic to verify free NOR sectors are all ones.</span></span>
- <span data-ttu-id="04586-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: de forma predeterminada, este valor es 16 y define el tamaño de la memoria caché de asignación de sectores lógicos.</span><span class="sxs-lookup"><span data-stu-id="04586-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**:  By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="04586-159">Los valores grandes mejoran el rendimiento, pero tienen un costo de memoria.</span><span class="sxs-lookup"><span data-stu-id="04586-159">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="04586-160">El tamaño mínimo es 8 y todos los valores deben ser una potencia de 2.</span><span class="sxs-lookup"><span data-stu-id="04586-160">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="04586-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: definido, esto crea una memoria caché de asignación directa, de modo que no hay errores de caché.</span><span class="sxs-lookup"><span data-stu-id="04586-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Defined, this creates a direct mapping cache, such that there are no cache misses.</span></span> <span data-ttu-id="04586-162">También requiere que LX_NAND_SECTOR_MAPPING_CACHE_SIZE represente el número exacto de páginas totales del dispositivo flash.</span><span class="sxs-lookup"><span data-stu-id="04586-162">It also requires that LX_NAND_SECTOR_MAPPING_CACHE_SIZE represents the exact number of total pages in your flash device.</span></span>
- <span data-ttu-id="04586-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: definido, esto deshabilita la memoria caché NOR extendida.</span><span class="sxs-lookup"><span data-stu-id="04586-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Defined, this disabled the extended NOR cache.</span></span>
- <span data-ttu-id="04586-164">**LX_NOR_EXTENDED_CACHE_SIZE**: de forma predeterminada, este valor es 8, que representa un máximo de 8 sectores que se pueden almacenar en memoria caché en una instancia de NOR.</span><span class="sxs-lookup"><span data-stu-id="04586-164">**LX_NOR_EXTENDED_CACHE_SIZE**: By default this value is 8, which represents a maximum of 8 sectors that can be cached in a NOR instance.</span></span>
- <span data-ttu-id="04586-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: de forma predeterminada, este valor es 16 y define el tamaño de la memoria caché de asignación de sectores lógicos.</span><span class="sxs-lookup"><span data-stu-id="04586-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="04586-166">Los valores grandes mejoran el rendimiento, pero tienen un costo de memoria.</span><span class="sxs-lookup"><span data-stu-id="04586-166">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="04586-167">El tamaño mínimo es 8 y todos los valores deben ser una potencia de 2.</span><span class="sxs-lookup"><span data-stu-id="04586-167">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="04586-168">**LX_THREAD_SAFE_ENABLE**: definido, esto hace que LevelX sea seguro para subprocesos mediante un objeto de exclusión mutua de ThreadX en toda la API.</span><span class="sxs-lookup"><span data-stu-id="04586-168">**LX_THREAD_SAFE_ENABLE**: Defined, this makes LevelX thread-safe by using a ThreadX mutex object throughout the API.</span></span>
- <span data-ttu-id="04586-169">**LX_STANDALONE_ENABLE**: si se define, permite usar LevelX en modo independiente (sin Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="04586-169">**LX_STANDALONE_ENABLE**: Defined, enables LevelX to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="04586-170">De forma predeterminada, este símbolo no está definido.</span><span class="sxs-lookup"><span data-stu-id="04586-170">By default this symbol is not defined.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04586-171">Cuando se usa LevelX en modo independiente (se debe definir **LX_STANDALONE_ENABLE**), no se necesitan archivos ni bibliotecas de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="04586-171">When using LevelX in Standalone mode (**LX_STANDALONE_ENABLE** must be defined), ThreadX files/libraries are not required.</span></span> <span data-ttu-id="04586-172">La característica Seguro para subprocesos de LevelX está deshabilitada en este modo.</span><span class="sxs-lookup"><span data-stu-id="04586-172">LevelX thread-safe feature is disabled in this mode.</span></span>

## <a name="using-levelx"></a><span data-ttu-id="04586-173">Uso de LevelX</span><span class="sxs-lookup"><span data-stu-id="04586-173">Using LevelX</span></span>

<span data-ttu-id="04586-174">Para usar LevelX, ya sea por sí mismo o con FileX, incluya el archivo \***lx_api.h** _ en el código que hace referencia a la API de LevelX.</span><span class="sxs-lookup"><span data-stu-id="04586-174">To use LevelX, either by itself or with FileX, include the file \***lx_api.h** _ in the code that references the LevelX API.</span></span> <span data-ttu-id="04586-175">Asegúrese también de que el código del objeto de LevelX esté disponible en tiempo de vínculo.</span><span class="sxs-lookup"><span data-stu-id="04586-175">Also ensure that the LevelX object code is available at link time.</span></span> <span data-ttu-id="04586-176">Examine los archivos _*_demo_filex_nand_flash.c_*_ y _ *_demo_filex_nor_flash.c_*\* para obtener ejemplos de cómo usar LevelX.</span><span class="sxs-lookup"><span data-stu-id="04586-176">Please examine the files _*_demo_filex_nand_flash.c_*_ and _ *_demo_filex_nor_flash.c_*\* for examples of how to use LevelX.</span></span>
