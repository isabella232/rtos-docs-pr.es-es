---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS FileX'
description: Este capítulo contiene una descripción de todos los servicios de Azure RTOS FileX en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 39b31c1abae8613eb54382162504aaadc07ceebf
ms.sourcegitcommit: 97f6724d6eee7b9c251a50c191911050c52b1c69
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025928"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="86a91-103">Capítulo 4: Descripción de los servicios de Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="86a91-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="86a91-104">Este capítulo contiene una descripción de todos los servicios de Azure RTOS FileX en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="86a91-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="86a91-105">Los nombres de los servicios están diseñados de modo que todos los servicios similares están agrupados.</span><span class="sxs-lookup"><span data-stu-id="86a91-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="86a91-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="86a91-107">Lee los atributos de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-108">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="86a91-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-109">Description</span></span>

<span data-ttu-id="86a91-110">Este servicio lee los atributos del directorio del medio especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-111">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-111">Input Parameters</span></span>

- <span data-ttu-id="86a91-112">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-113">**directory_name**: puntero al nombre del directorio solicitado (la ruta de acceso del directorio es opcional).</span><span class="sxs-lookup"><span data-stu-id="86a91-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="86a91-114">**attributes** _ptr: puntero al destino de los atributos del directorio que se va a colocar.</span><span class="sxs-lookup"><span data-stu-id="86a91-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="86a91-115">Los atributos de directorio se devuelven en un formato de mapa de bits con los siguientes valores posibles:</span><span class="sxs-lookup"><span data-stu-id="86a91-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="86a91-116">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="86a91-117">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="86a91-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="86a91-118">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="86a91-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="86a91-119">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="86a91-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="86a91-120">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="86a91-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="86a91-121">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="86a91-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-122">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-122">Return Values</span></span>

- <span data-ttu-id="86a91-123">**FX_SUCCESS** (0x00) Lectura correcta de atributos de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="86a91-124">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="86a91-125">**FX _NOT FOUND** (0x04) El directorio especificado no se ha encontrado en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="86a91-126">**FX_NOT_DIRECTORY** (0x0E) La entrada no es un directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="86a91-127">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="86a91-128">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-129">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="86a91-130">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="86a91-131">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-132">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="86a91-133">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="86a91-134">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-135">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-135">Allowed From</span></span>

<span data-ttu-id="86a91-136">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-137">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-138">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-138">See Also</span></span>

- <span data-ttu-id="86a91-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-140">fx_directory_create</span></span>
- <span data-ttu-id="86a91-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-141">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-142">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-143">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-146">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-152">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-155">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="86a91-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="86a91-160">Establece los atributos de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-161">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="86a91-162">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-162">Description</span></span>

<span data-ttu-id="86a91-163">Este servicio establece los atributos del directorio en los especificados por el autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="86a91-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-164">*Esta aplicación solo puede modificar un subconjunto de los atributos del directorio con este servicio. Cualquier intento de establecer atributos adicionales producirá un error.*</span><span class="sxs-lookup"><span data-stu-id="86a91-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-165">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-165">Input Parameters</span></span>

- <span data-ttu-id="86a91-166">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-167">**directory_name**: puntero al nombre del directorio solicitado (la ruta de acceso del directorio es opcional).</span><span class="sxs-lookup"><span data-stu-id="86a91-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="86a91-168">**attributes**: los nuevos atributos de este directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="86a91-169">Los atributos válidos de directorio se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="86a91-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="86a91-170">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="86a91-171">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="86a91-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="86a91-172">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="86a91-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="86a91-173">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="86a91-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-174">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-174">Return Values</span></span>

- <span data-ttu-id="86a91-175">**FX_SUCCESS** (0x00) Establecimiento correcto de atributos de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="86a91-176">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="86a91-177">**FX_NOT FOUND** (0x04) El directorio especificado no se ha encontrado en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="86a91-178">**FX_NOT_DIRECTORY** (0x0E) La entrada no es un directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="86a91-179">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="86a91-180">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="86a91-181">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-182">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="86a91-183">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="86a91-184">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-185">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="86a91-186">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="86a91-187">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="86a91-188">**FX_INVALID_ATTR** (0x19) Se han seleccionado atributos no válidos.</span><span class="sxs-lookup"><span data-stu-id="86a91-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="86a91-189">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-190">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-190">Allowed From</span></span>

<span data-ttu-id="86a91-191">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-192">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-193">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-193">See Also</span></span>

- <span data-ttu-id="86a91-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-195">fx_directory_create</span></span>
- <span data-ttu-id="86a91-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-196">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-197">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-198">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-201">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-207">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-210">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="86a91-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-214">fx_directory_create</span></span>

<span data-ttu-id="86a91-215">Crea un subdirectorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-216">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="86a91-217">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-217">Description</span></span>

<span data-ttu-id="86a91-218">Este servicio crea un subdirectorio en el directorio predeterminado actual o en la ruta de acceso proporcionada en el nombre de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="86a91-219">A diferencia del directorio raíz, los subdirectorios no tienen un límite en cuanto al número de archivos que pueden contener.</span><span class="sxs-lookup"><span data-stu-id="86a91-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="86a91-220">El directorio raíz solo puede contener el número de entradas determinado por el registro de arranque.</span><span class="sxs-lookup"><span data-stu-id="86a91-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-221">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-221">Input Parameters</span></span>

- <span data-ttu-id="86a91-222">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-223">**directory_name**: puntero al nombre del directorio que se va a crear (la ruta de acceso del directorio es opcional).</span><span class="sxs-lookup"><span data-stu-id="86a91-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-224">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-224">Return Values</span></span>

- <span data-ttu-id="86a91-225">**FX_SUCCESS** (0x00) Creación correcta de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="86a91-226">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="86a91-227">**FX_NOT FOUND** (0x04) El directorio especificado no se ha encontrado en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="86a91-228">**FX_NOT_DIRECTORY** (0x0E) La entrada no es un directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="86a91-229">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="86a91-230">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-231">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="86a91-232">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="86a91-233">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-234">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="86a91-235">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="86a91-236">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="86a91-237">**FX_INVALID_ATTR** (0x19) Se han seleccionado atributos no válidos.</span><span class="sxs-lookup"><span data-stu-id="86a91-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="86a91-238">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-239">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-239">Allowed From</span></span>

<span data-ttu-id="86a91-240">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-241">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-242">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-242">See Also</span></span>

- <span data-ttu-id="86a91-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-245">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-246">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-247">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-250">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-256">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-259">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="86a91-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-263">fx_directory_default_get</span></span>

<span data-ttu-id="86a91-264">Obtiene el último directorio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="86a91-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-265">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="86a91-266">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-266">Description</span></span>

<span data-ttu-id="86a91-267">Este servicio devuelve el puntero a la última ruta de acceso establecida por ***fx_directory_default_set***.</span><span class="sxs-lookup"><span data-stu-id="86a91-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="86a91-268">Si no se ha establecido el directorio predeterminado o si el directorio predeterminado actual es el directorio raíz, se devuelve un valor de FX_NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-269">*El tamaño predeterminado de la cadena de ruta de acceso interna es de 256 caracteres. Se puede cambiar modificando **FX_MAXIMUM_PATH** en **fx_api.h** y volviendo a generar toda la biblioteca FileX. Se mantiene la ruta de acceso de la cadena de caracteres para la aplicación y FileX no la usa internamente.*</span><span class="sxs-lookup"><span data-stu-id="86a91-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-270">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-270">Input Parameters</span></span>

- <span data-ttu-id="86a91-271">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-272">**return_path_name**: puntero al destino de la última cadena de directorio predeterminada.</span><span class="sxs-lookup"><span data-stu-id="86a91-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="86a91-273">Se devuelve un valor de FX_NULL si la configuración actual del directorio predeterminado es la raíz.</span><span class="sxs-lookup"><span data-stu-id="86a91-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="86a91-274">Cuando se abre el medio, la raíz es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="86a91-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-275">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-275">Return Values</span></span>

- <span data-ttu-id="86a91-276">**FX_SUCCESS** (0x00) Obtención correcta del directorio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="86a91-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="86a91-277">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="86a91-278">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o destino.</span><span class="sxs-lookup"><span data-stu-id="86a91-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="86a91-279">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-280">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-280">Allowed From</span></span>

<span data-ttu-id="86a91-281">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-282">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="86a91-283">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-283">See Also</span></span>

- <span data-ttu-id="86a91-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-286">fx_directory_create</span></span>
- <span data-ttu-id="86a91-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-287">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-288">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-291">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-297">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-300">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="86a91-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-304">fx_directory_default_set</span></span>

<span data-ttu-id="86a91-305">Establece el directorio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="86a91-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-306">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="86a91-307">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-307">Description</span></span>

<span data-ttu-id="86a91-308">Este servicio establece el directorio predeterminado del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="86a91-309">Si se proporciona un valor de FX_NULL, el directorio predeterminado se establece en el directorio raíz del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="86a91-310">Todas las operaciones de archivo posteriores que no especifiquen explícitamente una ruta de acceso tendrán este directorio como valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="86a91-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-311">*El tamaño predeterminado de la cadena de ruta de acceso interna es de 256 caracteres. Se puede cambiar modificando **FX_MAXIMUM_PATH** en **fx_api.h** y volviendo a generar toda la biblioteca FileX. Se mantiene la ruta de acceso de la cadena de caracteres para la aplicación y FileX no la usa internamente.*</span><span class="sxs-lookup"><span data-stu-id="86a91-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-312">*En el caso de los nombres proporcionados por la aplicación, FileX admite tanto los caracteres de barra diagonal inversa (\\) como los de barra diagonal (/) para separar los directorios, los subdirectorios y los nombres de archivo. Sin embargo, FileX solo usa el carácter de barra diagonal inversa en las rutas de acceso devueltas a la aplicación.*</span><span class="sxs-lookup"><span data-stu-id="86a91-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-313">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-313">Input Parameters</span></span>

- <span data-ttu-id="86a91-314">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-315">**new_path_name**: puntero al nuevo nombre de directorio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="86a91-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="86a91-316">Si se proporciona un valor de FX_NULL, el directorio predeterminado del medio se establece en el directorio raíz del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-317">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-317">Return Values</span></span>

- <span data-ttu-id="86a91-318">**FX_SUCCESS** (0x00) Establecimiento correcto del directorio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="86a91-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="86a91-319">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="86a91-320">**FX_INVALID_PATH** (0x0D) No se encontró el nuevo directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="86a91-321">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-322">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-323">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-323">Allowed From</span></span>

<span data-ttu-id="86a91-324">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-325">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-326">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-326">See Also</span></span>

- <span data-ttu-id="86a91-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-329">fx_directory_create</span></span>
- <span data-ttu-id="86a91-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-330">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-331">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-334">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-340">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-343">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="86a91-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-347">fx_directory_delete</span></span>

<span data-ttu-id="86a91-348">Elimina el subdirectorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-349">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="86a91-350">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-350">Description</span></span>

<span data-ttu-id="86a91-351">Este servicio elimina el directorio especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-351">This service deletes the specified directory.</span></span> <span data-ttu-id="86a91-352">Tenga en cuenta que el directorio debe estar vacío para eliminarlo.</span><span class="sxs-lookup"><span data-stu-id="86a91-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-353">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-353">Input Parameters</span></span>

- <span data-ttu-id="86a91-354">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-355">**directory_name**: puntero al nombre del directorio que se va a eliminar (la ruta de acceso del directorio es opcional).</span><span class="sxs-lookup"><span data-stu-id="86a91-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-356">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-356">Return Values</span></span>

- <span data-ttu-id="86a91-357">**FX_SUCCESS** (0x00) Eliminación correcta de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="86a91-358">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="86a91-359">**FX_NOT FOUND** (0x04) No se ha encontrado el directorio especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="86a91-360">**FX_DIR_NOT_EMPTY** (0x10) El directorio especificado no está vacío.</span><span class="sxs-lookup"><span data-stu-id="86a91-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="86a91-361">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="86a91-362">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="86a91-363">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-364">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="86a91-365">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="86a91-366">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-367">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="86a91-368">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="86a91-369">**FX_NOT_DIRECTORY** (0x0E) No es una entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="86a91-370">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="86a91-371">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-372">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-372">Allowed From</span></span>

<span data-ttu-id="86a91-373">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-374">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-375">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-375">See Also</span></span>

- <span data-ttu-id="86a91-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-378">fx_directory_create</span></span>
- <span data-ttu-id="86a91-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-379">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-380">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-383">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-389">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-392">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="86a91-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="86a91-397">Obtiene la primera entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-398">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="86a91-399">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-399">Description</span></span>

<span data-ttu-id="86a91-400">Este servicio recupera el nombre de la primera entrada en el directorio predeterminado y lo copia en el destino especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-401">*El destino especificado debe ser lo suficientemente grande como para contener el nombre de FileX de tamaño máximo, tal como se define en **FX_MAX_LONG_NAME_LEN.***</span><span class="sxs-lookup"><span data-stu-id="86a91-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-402">*Si usa una ruta de acceso no local, es importante para evitar (con un semáforo ThreadX, una exclusión mutua o un cambio de nivel de prioridad) que otros subprocesos de la aplicación cambien este directorio mientras se está llevando a cabo un cruce de directorio. De lo contrario, se pueden obtener resultados no válidos.*</span><span class="sxs-lookup"><span data-stu-id="86a91-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-403">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-403">Input Parameters</span></span>

- <span data-ttu-id="86a91-404">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-405">**return_entry_name**: puntero al destino del nombre de la primera entrada en el directorio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="86a91-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-406">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-406">Return Values</span></span>

- <span data-ttu-id="86a91-407">**FX_SUCCESS** (0x00) Búsqueda correcta de primera entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="86a91-408">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="86a91-409">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="86a91-410">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="86a91-411">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-412">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="86a91-413">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="86a91-414">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o destino.</span><span class="sxs-lookup"><span data-stu-id="86a91-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="86a91-415">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-416">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-416">Allowed From</span></span>

<span data-ttu-id="86a91-417">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-418">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-419">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-419">See Also</span></span>

- <span data-ttu-id="86a91-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-422">fx_directory_create</span></span>
- <span data-ttu-id="86a91-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-423">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-424">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-425">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-427">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-433">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-436">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="86a91-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="86a91-441">Obtiene la primera entrada de directorio con información completa.</span><span class="sxs-lookup"><span data-stu-id="86a91-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-442">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="86a91-443">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-443">Input Parameters</span></span>

- <span data-ttu-id="86a91-444">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-445">**directory_name**: puntero al destino del nombre de una entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="86a91-446">Debe ser al menos tan grande como FX_MAX_LONG_NAME_LEN.</span><span class="sxs-lookup"><span data-stu-id="86a91-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="86a91-447">**attributes**: si no es nulo, puntero al destino de los atributos de la entrada que se va a colocar.</span><span class="sxs-lookup"><span data-stu-id="86a91-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="86a91-448">Los atributos se devuelven en un formato de mapa de bits con los siguientes valores posibles:</span><span class="sxs-lookup"><span data-stu-id="86a91-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="86a91-449">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="86a91-450">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="86a91-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="86a91-451">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="86a91-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="86a91-452">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="86a91-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="86a91-453">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="86a91-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="86a91-454">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="86a91-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="86a91-455">**size**: si no es nulo, puntero al destino para el tamaño de la entrada en bytes.</span><span class="sxs-lookup"><span data-stu-id="86a91-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="86a91-456">**year**: si no es nulo, puntero al destino del año de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="86a91-457">**month**: si no es nulo, puntero al destino del mes de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="86a91-458">**day**: si no es nulo, puntero al destino del día de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="86a91-459">**hour**: si no es nulo, puntero al destino de la hora de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="86a91-460">**minute**: si no es nulo, puntero al destino del minuto de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="86a91-461">**second**: si no es nulo, puntero al destino del segundo de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-462">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-462">Return Values</span></span>

- <span data-ttu-id="86a91-463">**FX_SUCCESS** (0x00) Búsqueda correcta de primera entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="86a91-464">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="86a91-465">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="86a91-466">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="86a91-467">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="86a91-468">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-469">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="86a91-470">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="86a91-471">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-472">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="86a91-473">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o destino.</span><span class="sxs-lookup"><span data-stu-id="86a91-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="86a91-474">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-475">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-475">Allowed From</span></span>

<span data-ttu-id="86a91-476">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-477">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-477">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-478">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-478">See Also</span></span>

- <span data-ttu-id="86a91-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-481">fx_directory_create</span></span>
- <span data-ttu-id="86a91-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-482">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-483">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-484">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-486">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-492">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-495">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="86a91-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="86a91-499">fx_directory_information_get:</span></span>

<span data-ttu-id="86a91-500">Obtiene la información de entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-501">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="86a91-502">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-502">Input Parameters</span></span>

- <span data-ttu-id="86a91-503">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-504">**directory_name**: puntero al nombre de la entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="86a91-505">**attributes**: puntero al destino de los atributos.</span><span class="sxs-lookup"><span data-stu-id="86a91-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="86a91-506">**size**: puntero al destino del tamaño.</span><span class="sxs-lookup"><span data-stu-id="86a91-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="86a91-507">**year**: puntero al destino del año.</span><span class="sxs-lookup"><span data-stu-id="86a91-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="86a91-508">**month**: puntero al destino del mes.</span><span class="sxs-lookup"><span data-stu-id="86a91-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="86a91-509">**day**: puntero al destino del día.</span><span class="sxs-lookup"><span data-stu-id="86a91-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="86a91-510">**hour**: puntero al destino de la hora.</span><span class="sxs-lookup"><span data-stu-id="86a91-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="86a91-511">**minute**: puntero al destino del minuto.</span><span class="sxs-lookup"><span data-stu-id="86a91-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="86a91-512">**second**: puntero al destino del segundo.</span><span class="sxs-lookup"><span data-stu-id="86a91-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-513">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-513">Return Values</span></span>

- <span data-ttu-id="86a91-514">**FX_SUCCESS** (0x00) Búsqueda correcta de primera entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="86a91-515">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="86a91-516">**FX_NOT FOUND** (0x04) El directorio especificado no se ha encontrado en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="86a91-517">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="86a91-518">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="86a91-519">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-520">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="86a91-521">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-522">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="86a91-523">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o destino.</span><span class="sxs-lookup"><span data-stu-id="86a91-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="86a91-524">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-525">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-525">Allowed From</span></span>

<span data-ttu-id="86a91-526">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-527">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-527">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-528">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-528">See Also</span></span>

- <span data-ttu-id="86a91-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-531">fx_directory_create</span></span>
- <span data-ttu-id="86a91-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-532">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-533">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-534">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-542">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-545">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="86a91-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="86a91-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="86a91-550">Borra la ruta de acceso local predeterminada.</span><span class="sxs-lookup"><span data-stu-id="86a91-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-551">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="86a91-552">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-552">Description</span></span>

<span data-ttu-id="86a91-553">Este servicio borra la ruta de acceso local anterior configurada para el subproceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="86a91-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-554">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-554">Input Parameters</span></span>

- <span data-ttu-id="86a91-555">**media_ptr**: puntero a un medio abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-556">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-556">Return Values</span></span>

- <span data-ttu-id="86a91-557">**FX_SUCCESS** (0x00) Se ha borrado correctamente la ruta de acceso local.</span><span class="sxs-lookup"><span data-stu-id="86a91-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="86a91-558">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="86a91-559">**FX_NOT_IMPLEMENTED** (0x22) Se define FX_NO_LCOAL_PATH.</span><span class="sxs-lookup"><span data-stu-id="86a91-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="86a91-560">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-561">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-561">Allowed From</span></span>

<span data-ttu-id="86a91-562">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-563">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-564">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-564">See Also</span></span>

- <span data-ttu-id="86a91-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-567">fx_directory_create</span></span>
- <span data-ttu-id="86a91-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-568">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-569">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-570">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-573">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-578">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-581">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="86a91-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="86a91-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="86a91-586">Obtiene la cadena de ruta de acceso local actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-587">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="86a91-588">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-588">Description</span></span>

<span data-ttu-id="86a91-589">Este servicio devuelve el puntero de la ruta de acceso local del medio especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="86a91-590">Si no hay ninguna ruta de acceso local establecida, se devuelve un valor NULL al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="86a91-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-591">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-591">Input Parameters</span></span>

- <span data-ttu-id="86a91-592">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-593">**return_path_name**: puntero al puntero de la cadena de destino para la cadena de ruta de acceso local que se va a almacenar.</span><span class="sxs-lookup"><span data-stu-id="86a91-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-594">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-594">Return Values</span></span>

- <span data-ttu-id="86a91-595">**FX_SUCCESS** (0x00) Se ha obtenido correctamente la ruta de acceso local.</span><span class="sxs-lookup"><span data-stu-id="86a91-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="86a91-596">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="86a91-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="86a91-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="86a91-598">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="86a91-599">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-599">Allowed From</span></span>

<span data-ttu-id="86a91-600">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-601">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-602">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-602">See Also</span></span>

- <span data-ttu-id="86a91-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-605">fx_directory_create</span></span>
- <span data-ttu-id="86a91-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-606">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-607">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-608">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-611">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-616">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-619">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="86a91-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="86a91-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="86a91-624">Restaura la ruta de acceso local anterior.</span><span class="sxs-lookup"><span data-stu-id="86a91-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-625">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="86a91-626">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-626">Description</span></span>

<span data-ttu-id="86a91-627">Este servicio restaura una ruta de acceso local establecida previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-627">This service restores a previously set local path.</span></span> <span data-ttu-id="86a91-628">También se restaura la posición de búsqueda de directorio realizada en esta ruta de acceso local, lo que hace que esta rutina resulte útil cuando la aplicación realiza cruces de directorio recursivos.</span><span class="sxs-lookup"><span data-stu-id="86a91-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-629">*Cada ruta de acceso local contiene una cadena de ruta de acceso local del tamaño máximo de **FX_MAXIMUM_PATH**, que de forma predeterminada es de 256 caracteres. FileX no usa esta cadena de ruta de acceso interna y solo se proporciona para su uso por la aplicación. Si **FX_LOCAL_PATH** se va a declarar como una variable local, los usuarios deben tener cuidado del crecimiento de la pila por el tamaño de esta estructura. Los usuarios pueden reducir el tamaño de **FX_MAXIMUM_PATH** y volver a generar el origen de la biblioteca FileX.*</span><span class="sxs-lookup"><span data-stu-id="86a91-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-630">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-630">Input Parameters</span></span>

- <span data-ttu-id="86a91-631">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-632">**local_path_ptr**: puntero a la ruta de acceso local establecida previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="86a91-633">Es muy importante asegurarse de que este puntero apunta a una ruta de acceso local que se ha usado anteriormente y que todavía está intacta.</span><span class="sxs-lookup"><span data-stu-id="86a91-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-634">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-634">Return Values</span></span>

- <span data-ttu-id="86a91-635">**FX_SUCCESS** (0x00) Se ha restaurado correctamente la ruta de acceso local.</span><span class="sxs-lookup"><span data-stu-id="86a91-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="86a91-636">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="86a91-637">**FX_NOT_IMPLEMENTED** (0x22) Se define FX_NO_LCOAL_PATH.</span><span class="sxs-lookup"><span data-stu-id="86a91-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="86a91-638">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o ruta de acceso local.</span><span class="sxs-lookup"><span data-stu-id="86a91-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-639">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-639">Allowed From</span></span>

<span data-ttu-id="86a91-640">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-641">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-642">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-642">See Also</span></span>

- <span data-ttu-id="86a91-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-645">fx_directory_create</span></span>
- <span data-ttu-id="86a91-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-646">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-647">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-648">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-651">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-656">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-659">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="86a91-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="86a91-664">Configura una ruta de acceso local específica de subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-665">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="86a91-666">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-666">Description</span></span>

<span data-ttu-id="86a91-667">Este servicio configura una ruta de acceso específica de subproceso según lo especificado por \***new_path_string** _.</span><span class="sxs-lookup"><span data-stu-id="86a91-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="86a91-668">Después de completar esta rutina correctamente, la información de la ruta de acceso local almacenada en _ *_local_path_ptr_*\* tendrá prioridad sobre la ruta de acceso de medio global para todas las operaciones de archivos y directorios realizadas por este subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="86a91-669">Esto no tendrá ningún impacto en ningún otro subproceso del sistema.</span><span class="sxs-lookup"><span data-stu-id="86a91-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="86a91-670">*El tamaño predeterminado de la cadena de ruta de acceso local es de 256 caracteres. Se puede cambiar modificando **FX_MAXIMUM_PATH** en **fx_api.h** y volviendo a generar toda la biblioteca FileX. Se mantiene la ruta de acceso de la cadena de caracteres para la aplicación y FileX no la usa internamente.*</span><span class="sxs-lookup"><span data-stu-id="86a91-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-671">*En el caso de los nombres proporcionados por la aplicación, FileX admite tanto los caracteres de barra diagonal inversa (\\) como los de barra diagonal (/) para separar los directorios, los subdirectorios y los nombres de archivo. Sin embargo, FileX solo usa el carácter de barra diagonal inversa en las rutas de acceso devueltas a la aplicación.*</span><span class="sxs-lookup"><span data-stu-id="86a91-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-672">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-672">Input Parameters</span></span>

- <span data-ttu-id="86a91-673">**media_ptr**: puntero al medio abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="86a91-674">**local_path_ptr**: destino para retener la información de la ruta de acceso local específica de subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="86a91-675">La dirección de esta estructura se podrá proporcionar a la función de restauración de la ruta de acceso local en el futuro.</span><span class="sxs-lookup"><span data-stu-id="86a91-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="86a91-676">**new_path_name**: especifica la ruta de acceso local para el programa de instalación.</span><span class="sxs-lookup"><span data-stu-id="86a91-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-677">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-677">Return Values</span></span>

- <span data-ttu-id="86a91-678">**FX_SUCCESS** (0x00) Establecimiento correcto del directorio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="86a91-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="86a91-679">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="86a91-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="86a91-681">**FX_INVALID_PATH** (0x0D) No se encontró el nuevo directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="86a91-682">**FX_NOT_IMPLEMENTED** (0x22) Se define \*\*FX_NO_LCOAL_PATH.</span><span class="sxs-lookup"><span data-stu-id="86a91-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="86a91-683">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o ruta de acceso local.</span><span class="sxs-lookup"><span data-stu-id="86a91-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-684">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-684">Allowed From</span></span>

<span data-ttu-id="86a91-685">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-686">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-686">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a><span data-ttu-id="86a91-687">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-687">See Also</span></span>

- <span data-ttu-id="86a91-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-690">fx_directory_create</span></span>
- <span data-ttu-id="86a91-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-691">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-692">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-693">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-696">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-701">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-704">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="86a91-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="86a91-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="86a91-709">Obtiene el nombre largo del nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-710">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="86a91-711">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-711">Description</span></span>

<span data-ttu-id="86a91-712">Este servicio recupera el nombre largo (si existe) asociado al nombre corto (formato 8.3) proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="86a91-713">El nombre corto puede ser un nombre de archivo o un nombre de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-714">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-714">Input Parameters</span></span>

- <span data-ttu-id="86a91-715">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-716">**short_name**: puntero al nombre corto de origen (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="86a91-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="86a91-717">**long_name**: puntero al destino del nombre largo.</span><span class="sxs-lookup"><span data-stu-id="86a91-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="86a91-718">Si no hay ningún nombre largo, se devuelve el nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="86a91-719">Tenga en cuenta que el destino del nombre largo debe ser lo suficientemente grande como para contener el número de caracteres de FX_MAX_LONG_NAME_LEN.</span><span class="sxs-lookup"><span data-stu-id="86a91-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-720">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-720">Return Values</span></span>

- <span data-ttu-id="86a91-721">**FX_SUCCESS** (0x00) Obtención correcta de nombre largo.</span><span class="sxs-lookup"><span data-stu-id="86a91-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="86a91-722">**FX_NOT_FOUND** (0x04) No se ha encontrado el nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="86a91-723">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="86a91-724">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="86a91-725">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-726">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="86a91-727">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="86a91-728">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-729">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="86a91-730">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-731">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-731">Allowed From</span></span>

<span data-ttu-id="86a91-732">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-733">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-734">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-734">See Also</span></span>

- <span data-ttu-id="86a91-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-737">fx_directory_create</span></span>
- <span data-ttu-id="86a91-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-738">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-739">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-740">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-743">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-748">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-751">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="86a91-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="86a91-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="86a91-756">Obtiene el nombre largo del nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-757">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="86a91-758">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-758">Description</span></span>

<span data-ttu-id="86a91-759">Este servicio recupera el nombre largo (si existe) asociado al nombre corto (formato 8.3) proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="86a91-760">El nombre corto puede ser un nombre de archivo o un nombre de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-761">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-761">Input Parameters</span></span>

- <span data-ttu-id="86a91-762">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-763">**short_name**: puntero al nombre corto de origen (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="86a91-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="86a91-764">**long_name**: puntero al destino del nombre largo.</span><span class="sxs-lookup"><span data-stu-id="86a91-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="86a91-765">Si no hay ningún nombre largo, se devuelve el nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="86a91-766">Nota: El destino del nombre largo debe ser lo suficientemente grande como para contener el número de caracteres de **FX_MAX_LONG_NAME_LEN**.</span><span class="sxs-lookup"><span data-stu-id="86a91-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="86a91-767">**long_file_name_buffer_length**: longitud del búfer de nombres largos.</span><span class="sxs-lookup"><span data-stu-id="86a91-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-768">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-768">Return Values</span></span>

- <span data-ttu-id="86a91-769">**FX_SUCCESS** (0x00) Obtención correcta de nombre largo.</span><span class="sxs-lookup"><span data-stu-id="86a91-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="86a91-770">**FX_NOT_FOUND** (0x04) No se ha encontrado el nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="86a91-771">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-772">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="86a91-773">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-774">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-775">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-776">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="86a91-777">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="86a91-778">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-779">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-779">Allowed From</span></span>

<span data-ttu-id="86a91-780">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-781">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-782">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-782">See Also</span></span>

- <span data-ttu-id="86a91-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-785">fx_directory_create</span></span>
- <span data-ttu-id="86a91-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-786">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-787">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-788">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-791">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-799">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="86a91-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-803">fx_directory_name_test</span></span>

<span data-ttu-id="86a91-804">Pruebas de directorio</span><span class="sxs-lookup"><span data-stu-id="86a91-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-805">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="86a91-806">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-806">Description</span></span>

<span data-ttu-id="86a91-807">Este servicio comprueba si el nombre proporcionado es un directorio o no.</span><span class="sxs-lookup"><span data-stu-id="86a91-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="86a91-808">Si lo es, se devuelve FX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="86a91-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-809">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-809">Input Parameters</span></span>

- <span data-ttu-id="86a91-810">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-811">**directory_name**: puntero al nombre de la entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-812">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-812">Return Values</span></span>

- <span data-ttu-id="86a91-813">**FX_SUCCESS** (0x00) El nombre proporcionado es un directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="86a91-814">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="86a91-815">**FX_NOT_FOUND** (0x04) La entrada de directorio no se ha podido encontrar.</span><span class="sxs-lookup"><span data-stu-id="86a91-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="86a91-816">**FX_NOT_DIRECTORY** (0x0E) La entrada no es un directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="86a91-817">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-818">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="86a91-819">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-820">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-821">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-822">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="86a91-823">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="86a91-824">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-825">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-825">Allowed From</span></span>

<span data-ttu-id="86a91-826">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-827">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-828">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-828">See Also</span></span>

- <span data-ttu-id="86a91-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-831">fx_directory_create</span></span>
- <span data-ttu-id="86a91-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-832">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-833">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-834">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-837">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-845">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="86a91-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="86a91-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="86a91-849">Recoge la siguiente entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-850">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="86a91-851">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-851">Description</span></span>

<span data-ttu-id="86a91-852">Este servicio devuelve el siguiente nombre de entrada del directorio predeterminado actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-853">*Si usa una ruta de acceso no local, también es importante para evitar (con un semáforo ThreadX o un nivel de prioridad de subproceso) que otros subprocesos de la aplicación cambien este directorio mientras se está llevando a cabo un cruce de directorio. De lo contrario, se pueden obtener resultados no válidos.*</span><span class="sxs-lookup"><span data-stu-id="86a91-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-854">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-854">Input Parameters</span></span>

- <span data-ttu-id="86a91-855">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-856">**return_entry_name**: puntero al destino del nombre de la siguiente entrada en el directorio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="86a91-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="86a91-857">El búfer al que apunta este puntero debe ser lo suficientemente grande como para contener el tamaño máximo del nombre de FileX, definido por **_FX_MAX_LONG_NAME_LEN_**.</span><span class="sxs-lookup"><span data-stu-id="86a91-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-858">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-858">Return Values</span></span>

- <span data-ttu-id="86a91-859">**FX_SUCCESS** (0x00) Búsqueda correcta de siguiente entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="86a91-860">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-861">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="86a91-862">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-863">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-864">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-865">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-866">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-867">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-868">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-869">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-869">Allowed From</span></span>

<span data-ttu-id="86a91-870">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-871">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-872">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-872">See Also</span></span>

- <span data-ttu-id="86a91-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-875">fx_directory_create</span></span>
- <span data-ttu-id="86a91-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-876">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-877">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-878">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-881">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-887">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-889">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="86a91-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="86a91-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="86a91-894">Obtiene la siguiente entrada de directorio con información completa.</span><span class="sxs-lookup"><span data-stu-id="86a91-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-895">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-895">Prototype</span></span>

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="86a91-896">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-896">Description</span></span>

<span data-ttu-id="86a91-897">Este servicio recupera el nombre de la siguiente entrada del directorio predeterminado y lo copia en el destino especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="86a91-898">También devuelve información completa sobre la entrada tal y como se especifica en los parámetros de entrada adicionales.</span><span class="sxs-lookup"><span data-stu-id="86a91-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-899">\*El destino especificado debe ser lo suficientemente grande como para contener el nombre de FileX de tamaño máximo, tal como se define en \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="86a91-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-900">*Si usa una ruta de acceso no local, es importante para evitar (con un semáforo ThreadX, una exclusión mutua o un cambio de nivel de prioridad) que otros subprocesos de la aplicación cambien este directorio mientras se está llevando a cabo un cruce de directorio. De lo contrario, se pueden obtener resultados no válidos.*</span><span class="sxs-lookup"><span data-stu-id="86a91-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-901">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-901">Input Parameters</span></span>

- <span data-ttu-id="86a91-902">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-903">**directory_name**: puntero al destino del nombre de una entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="86a91-904">Debe ser al menos tan grande como **FX_MAX_LONG_NAME_LEN**.</span><span class="sxs-lookup"><span data-stu-id="86a91-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="86a91-905">**attributes**: si no es nulo, puntero al destino para los atributos de la entrada que se va a colocar. Los atributos se devuelven en un formato de mapa de bits con los siguientes valores posibles:</span><span class="sxs-lookup"><span data-stu-id="86a91-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="86a91-906">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="86a91-907">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="86a91-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="86a91-908">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="86a91-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="86a91-909">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="86a91-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="86a91-910">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="86a91-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="86a91-911">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="86a91-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="86a91-912">**size**: si no es nulo, puntero al destino para el tamaño de la entrada en bytes.</span><span class="sxs-lookup"><span data-stu-id="86a91-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="86a91-913">**month**: si no es nulo, puntero al destino del mes de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="86a91-914">**year**: si no es nulo, puntero al destino del año de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="86a91-915">**day**: si no es nulo, puntero al destino del día de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="86a91-916">**hour**: si no es nulo, puntero al destino de la hora de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="86a91-917">**minute**: si no es nulo, puntero al destino del minuto de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="86a91-918">**second**: si no es nulo, puntero al destino del segundo de modificación de la entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-919">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-919">Return Values</span></span>

- <span data-ttu-id="86a91-920">**FX_SUCCESS** (0x00) Búsqueda correcta de siguiente directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="86a91-921">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-922">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="86a91-923">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-924">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-925">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-926">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-927">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="86a91-928">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="86a91-929">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o todos los parámetros de entrada son NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="86a91-930">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-931">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-931">Allowed From</span></span>

<span data-ttu-id="86a91-932">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-933">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-933">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-934">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-934">See Also</span></span>

- <span data-ttu-id="86a91-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-937">fx_directory_create</span></span>
- <span data-ttu-id="86a91-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-938">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-939">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-940">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-943">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-949">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-951">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="86a91-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-955">fx_directory_rename</span></span>

<span data-ttu-id="86a91-956">Cambia el nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-957">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="86a91-958">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-958">Description</span></span>

<span data-ttu-id="86a91-959">Este servicio cambia el nombre del directorio por el nuevo nombre de directorio especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="86a91-960">El cambio de nombre también se realiza en relación con la ruta de acceso especificada o la ruta de acceso predeterminada.</span><span class="sxs-lookup"><span data-stu-id="86a91-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="86a91-961">Si se especifica una ruta de acceso en el nuevo nombre de directorio, el directorio cuyo nombre ha cambiado se mueve realmente a la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="86a91-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="86a91-962">Si no se especifica ninguna ruta de acceso, el directorio cuyo nombre ha cambiado se coloca en la ruta de acceso predeterminada actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-963">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-963">Input Parameters</span></span>

- <span data-ttu-id="86a91-964">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-965">**old_directory_name**: puntero al nombre de directorio actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="86a91-966">**new_directory_name**: puntero al nuevo nombre de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-967">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-967">Return Values</span></span>

- <span data-ttu-id="86a91-968">**FX_SUCCESS** (0x00) Cambio correcto de nombre de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="86a91-969">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-970">**FX_NOT_FOUND** (0x04) La entrada de directorio no se ha podido encontrar.</span><span class="sxs-lookup"><span data-stu-id="86a91-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="86a91-971">**FX_NOT_DIRECTORY** (0x0E) La entrada no es un directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="86a91-972">**FX_INVALID_NAME** (0x0C) El nuevo nombre de directorio no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="86a91-973">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-974">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-975">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-976">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-977">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-978">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="86a91-979">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="86a91-980">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="86a91-981">**FX_INVALID_PATH** (0x0D) Ruta de acceso no válida proporcionada con el nombre de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="86a91-982">**FX_ALREADY_CREATED** (0x0B) El directorio especificado ya se había creado.</span><span class="sxs-lookup"><span data-stu-id="86a91-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="86a91-983">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-984">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-985">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-985">Allowed From</span></span>

<span data-ttu-id="86a91-986">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-987">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-988">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-988">See Also</span></span>

- <span data-ttu-id="86a91-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-991">fx_directory_create</span></span>
- <span data-ttu-id="86a91-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-992">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-993">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-994">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-997">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="86a91-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="86a91-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="86a91-1010">Obtiene el nombre corto de un nombre largo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1011">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="86a91-1012">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1012">Description</span></span>

<span data-ttu-id="86a91-1013">Este servicio recupera el nombre corto (formato 8.3) asociado al nombre largo proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="86a91-1014">El nombre largo puede ser un nombre de archivo o un nombre de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1015">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1015">Input Parameters</span></span>

- <span data-ttu-id="86a91-1016">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-1017">**long_name**: puntero al nombre largo de origen.</span><span class="sxs-lookup"><span data-stu-id="86a91-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="86a91-1018">**short_name**: puntero al nombre corto de destino (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="86a91-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="86a91-1019">Tenga en cuenta que el destino del nombre corto debe ser lo suficientemente grande como para contener 14 caracteres.</span><span class="sxs-lookup"><span data-stu-id="86a91-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1020">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1020">Return Values</span></span>

- <span data-ttu-id="86a91-1021">**FX_SUCCESS** (0x00) Obtención correcta de nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="86a91-1022">**FX_NOT_FOUND** (0x04) No se ha encontrado el nombre largo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="86a91-1023">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1024">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-1025">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1026">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1027">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1028">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-1029">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="86a91-1030">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="86a91-1031">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1032">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1032">Allowed From</span></span>

<span data-ttu-id="86a91-1033">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1034">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1035">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1035">See Also</span></span>

- <span data-ttu-id="86a91-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1038">fx_directory_create</span></span>
- <span data-ttu-id="86a91-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1041">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1053">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="86a91-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="86a91-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="86a91-1057">Obtiene el nombre corto de un nombre largo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1058">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="86a91-1059">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1059">Description</span></span>

<span data-ttu-id="86a91-1060">Este servicio recupera el nombre corto (formato 8.3) asociado al nombre largo proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="86a91-1061">El nombre largo puede ser un nombre de archivo o un nombre de directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1062">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1062">Input Parameters</span></span>

- <span data-ttu-id="86a91-1063">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-1064">**long_name**: puntero al nombre largo de origen.</span><span class="sxs-lookup"><span data-stu-id="86a91-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="86a91-1065">**short_name**: puntero al nombre corto de destino (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="86a91-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="86a91-1066">Nota: El destino del nombre corto debe ser lo suficientemente grande como para contener 14 caracteres.</span><span class="sxs-lookup"><span data-stu-id="86a91-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="86a91-1067">**short_file_name_length**: longitud del búfer de nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1068">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1068">Return Values</span></span>

- <span data-ttu-id="86a91-1069">**FX_SUCCESS** (0x00) Obtención correcta de nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="86a91-1070">**FX_NOT_FOUND** (0x04) No se ha encontrado el nombre largo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="86a91-1071">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1072">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-1073">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1074">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1075">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1076">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-1077">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="86a91-1078">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="86a91-1079">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1080">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1080">Allowed From</span></span>

<span data-ttu-id="86a91-1081">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1082">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1083">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1083">See Also</span></span>

- <span data-ttu-id="86a91-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1086">fx_directory_create</span></span>
- <span data-ttu-id="86a91-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1089">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1101">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="86a91-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="86a91-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="86a91-1105">Habilita el servicio de tolerancia a errores.</span><span class="sxs-lookup"><span data-stu-id="86a91-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1106">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="86a91-1107">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1107">Description</span></span>

<span data-ttu-id="86a91-1108">Este servicio habilita el módulo de tolerancia a errores.</span><span class="sxs-lookup"><span data-stu-id="86a91-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="86a91-1109">Al iniciarse, el módulo de tolerancia a errores detecta si el sistema de archivos está bajo la protección de la tolerancia a errores de FileX.</span><span class="sxs-lookup"><span data-stu-id="86a91-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="86a91-1110">Si no es así, el servicio busca los sectores disponibles en el sistema de archivos para almacenar los registros en las transacciones del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="86a91-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="86a91-1111">Si el sistema de archivos se encuentra bajo la protección de la tolerancia a errores de FileX, aplica los registros al sistema de archivos para mantener su integridad.</span><span class="sxs-lookup"><span data-stu-id="86a91-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1112">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1112">Input Parameters</span></span>

- <span data-ttu-id="86a91-1113">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-1114">**memory_ptr**: puntero a un bloque de memoria utilizado por el módulo de tolerancia a errores como memoria temporal.</span><span class="sxs-lookup"><span data-stu-id="86a91-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="86a91-1115">**memory_size**: tamaño de la memoria temporal.</span><span class="sxs-lookup"><span data-stu-id="86a91-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="86a91-1116">Para que la tolerancia a errores funcione correctamente, el tamaño de la memoria temporal debe ser de al menos 3072 bytes, y debe ser un múltiplo del tamaño del sector.</span><span class="sxs-lookup"><span data-stu-id="86a91-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1117">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1117">Return Values</span></span>

- <span data-ttu-id="86a91-1118">**FX_SUCCESS** (0x00) Habilitación correcta de la tolerancia a errores.</span><span class="sxs-lookup"><span data-stu-id="86a91-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="86a91-1119">**FX_NOT_ENOUGH_MEMORY** (0x91) Tamaño de memoria demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="86a91-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="86a91-1120">**FX_BOOT_ERROR** (0x01) Error del sector de arranque.</span><span class="sxs-lookup"><span data-stu-id="86a91-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="86a91-1121">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1122">**FX_NO_MORE_ENTRIES** (0x0F) No hay más clústeres libres disponibles.</span><span class="sxs-lookup"><span data-stu-id="86a91-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="86a91-1123">**FX_NO_MORE_SPACE** (0x0A) El medio asociado con este archivo no tiene suficientes clústeres disponibles.</span><span class="sxs-lookup"><span data-stu-id="86a91-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="86a91-1124">**FX_SECTOR_INVALID** (0x89) El sector no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="86a91-1125">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1126">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-1127">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1128">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1128">Allowed From</span></span>

<span data-ttu-id="86a91-1129">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1130">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="86a91-1131">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1131">See Also</span></span>

- <span data-ttu-id="86a91-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-1132">fx_system_initialize</span></span>
- <span data-ttu-id="86a91-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-1133">fx_media_abort</span></span>
- <span data-ttu-id="86a91-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-1135">fx_media_check</span></span>
- <span data-ttu-id="86a91-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1136">fx_media_close</span></span>
- <span data-ttu-id="86a91-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-1140">fx_media_flush</span></span>
- <span data-ttu-id="86a91-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-1141">fx_media_format</span></span>
- <span data-ttu-id="86a91-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1142">fx_media_open</span></span>
- <span data-ttu-id="86a91-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1144">fx_media_read</span></span>
- <span data-ttu-id="86a91-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-1145">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="86a91-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1149">fx_file_allocate</span></span>

<span data-ttu-id="86a91-1150">Asigna espacio para un archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1151">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="86a91-1152">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1152">Description</span></span>

<span data-ttu-id="86a91-1153">Este servicio asigna y vincula uno o más clústeres contiguos al final del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="86a91-1154">FileX determina el número de clústeres necesarios dividiendo el tamaño solicitado por el número de bytes por clúster.</span><span class="sxs-lookup"><span data-stu-id="86a91-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="86a91-1155">Después, el resultado se redondea al siguiente clúster completo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="86a91-1156">Para asignar espacio más allá de 4 GB, la aplicación debe usar el servicio *fx_file_extended_allocate*.</span><span class="sxs-lookup"><span data-stu-id="86a91-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1157">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1157">Input Parameters</span></span>

- <span data-ttu-id="86a91-1158">**file_ptr**: puntero a un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="86a91-1159">**size**: número de bytes que se asignan al archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1160">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1160">Return Values</span></span>

- <span data-ttu-id="86a91-1161">**FX_SUCCESS** (0x00) Asignación correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="86a91-1162">**FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="86a91-1163">**FX_FAT_READ_ERROR** (0x03) No se ha podido leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1164">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1165">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="86a91-1166">**FX_NO_MORE_ENTRIES** (0x0F) No hay más clústeres libres disponibles.</span><span class="sxs-lookup"><span data-stu-id="86a91-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="86a91-1167">**FX_NO_MORE_SPACE** (0x0A) El medio asociado con este archivo no tiene suficientes clústeres disponibles.</span><span class="sxs-lookup"><span data-stu-id="86a91-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="86a91-1168">**FX_SECTOR_INVALID** (0x89) El sector no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="86a91-1169">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1170">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-1171">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-1172">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1173">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1173">Allowed From</span></span>

<span data-ttu-id="86a91-1174">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1175">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1176">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1176">See Also</span></span>

- <span data-ttu-id="86a91-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1180">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="86a91-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1182">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1189">fx_file_open- fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="86a91-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1191">fx_file_rename- fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="86a91-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1192">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1194">fx_file_write</span></span>
- <span data-ttu-id="86a91-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="86a91-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="86a91-1201">Lee atributos de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1202">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="86a91-1203">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1203">Description</span></span>

<span data-ttu-id="86a91-1204">Este servicio lee los atributos del archivo del medio especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1205">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1205">Input Parameters</span></span>

- <span data-ttu-id="86a91-1206">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-1207">**file_name**: puntero al nombre del archivo solicitado (la ruta de acceso del directorio es opcional).</span><span class="sxs-lookup"><span data-stu-id="86a91-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="86a91-1208">**attributes_ptr**: puntero al destino de los atributos del archivo que se va a colocar.</span><span class="sxs-lookup"><span data-stu-id="86a91-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="86a91-1209">Los atributos del archivo se devuelven en un formato de mapa de bits con los siguientes valores posibles:</span><span class="sxs-lookup"><span data-stu-id="86a91-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="86a91-1210">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="86a91-1211">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="86a91-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="86a91-1212">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="86a91-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="86a91-1213">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="86a91-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="86a91-1214">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="86a91-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="86a91-1215">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="86a91-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1216">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1216">Return Values</span></span>

- <span data-ttu-id="86a91-1217">**FX_SUCCESS** (0x00) Lectura correcta del atributo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="86a91-1218">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-1219">**FX_NOT FOUND** (0x04) El archivo especificado no se ha encontrado en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="86a91-1220">**FX_NOT_A_FILE** (0x05) El archivo especificado es un directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="86a91-1221">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1222">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1223">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-1224">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-1225">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1226">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o atributos.</span><span class="sxs-lookup"><span data-stu-id="86a91-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="86a91-1227">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1228">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1228">Allowed From</span></span>

<span data-ttu-id="86a91-1229">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1230">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="86a91-1231">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1231">See Also</span></span>

- <span data-ttu-id="86a91-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1232">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1235">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="86a91-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1237">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1244">fx_file_open</span></span>
- <span data-ttu-id="86a91-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1245">fx_file_read</span></span>
- <span data-ttu-id="86a91-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1247">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1248">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1249">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1251">fx_file_write</span></span>
- <span data-ttu-id="86a91-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="86a91-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="86a91-1258">Establece atributos de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1259">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="86a91-1260">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1260">Description</span></span>

<span data-ttu-id="86a91-1261">Este servicio establece los atributos del archivo en los especificados por el autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="86a91-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-1262">*La aplicación solo puede modificar un subconjunto de los atributos del archivo con este servicio. Cualquier intento de establecer atributos adicionales producirá un error.*</span><span class="sxs-lookup"><span data-stu-id="86a91-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1263">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1263">Input Parameters</span></span>

- <span data-ttu-id="86a91-1264">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-1265">**file_name**: puntero al nombre del archivo solicitado\*\* (la ruta de acceso del directorio es opcional).</span><span class="sxs-lookup"><span data-stu-id="86a91-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="86a91-1266">**attributes**: nuevos atributos del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="86a91-1267">Los atributos de archivo válidos se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="86a91-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="86a91-1268">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="86a91-1269">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="86a91-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="86a91-1270">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="86a91-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="86a91-1271">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="86a91-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1272">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1272">Return Values</span></span>

- <span data-ttu-id="86a91-1273">**FX_SUCCESS** (0x00) Establecimiento correcto del atributo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="86a91-1274">**FX_ACCESS_ERROR** (0x06) El archivo está abierto y sus atributos no se pueden establecer.</span><span class="sxs-lookup"><span data-stu-id="86a91-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="86a91-1275">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1276">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1277">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-1278">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en la tabla FAT o en la asignación de clúster de exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="86a91-1279">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="86a91-1280">**FX_NOT FOUND** (0x04) El archivo especificado no se ha encontrado en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="86a91-1281">**FX_NOT_A_FILE** (0x05) El archivo especificado es un directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="86a91-1282">**FX_SECTOR_INVALID** (0x89) El sector no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="86a91-1283">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1284">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-1285">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="86a91-1286">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-1287">**FX_INVALID_ATTR** (0x19) Se han seleccionado atributos no válidos.</span><span class="sxs-lookup"><span data-stu-id="86a91-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="86a91-1288">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1289">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1289">Allowed From</span></span>

<span data-ttu-id="86a91-1290">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1291">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="86a91-1292">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1292">See Also</span></span>

- <span data-ttu-id="86a91-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1293">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1296">fx_file_close</span></span>
- <span data-ttu-id="86a91-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1297">fx_file_create</span></span>
- <span data-ttu-id="86a91-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1299">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1306">fx_file_open</span></span>
- <span data-ttu-id="86a91-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1307">fx_file_read</span></span>
- <span data-ttu-id="86a91-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1309">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1310">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1311">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1313">fx_file_write</span></span>
- <span data-ttu-id="86a91-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="86a91-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="86a91-1320">Mejor esfuerzo para asignar espacio para un archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1321">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="86a91-1322">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1322">Description</span></span>

<span data-ttu-id="86a91-1323">Este servicio asigna y vincula uno o más clústeres contiguos al final del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="86a91-1324">FileX determina el número de clústeres necesarios dividiendo el tamaño solicitado por el número de bytes por clúster.</span><span class="sxs-lookup"><span data-stu-id="86a91-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="86a91-1325">Después, el resultado se redondea al siguiente clúster completo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="86a91-1326">Si no hay suficientes clústeres consecutivos disponibles en el medio, este servicio vincula el bloque más grande disponible de clústeres consecutivos al archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="86a91-1327">La cantidad de espacio realmente asignado al archivo se devuelve al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="86a91-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="86a91-1328">Para asignar espacio más allá de 4 GB, la aplicación debe usar el servicio *fx_file_extended_best_effort_allocate*.</span><span class="sxs-lookup"><span data-stu-id="86a91-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1329">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1329">Input Parameters</span></span>

- <span data-ttu-id="86a91-1330">**file_ptr**: puntero a un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="86a91-1331">**size**: número de bytes que se asignan al archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1332">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1332">Return Values</span></span>

- <span data-ttu-id="86a91-1333">**FX_SUCCESS** (0x00) Asignación correcta de mejor esfuerzo de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="86a91-1334">**FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="86a91-1335">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="86a91-1336">**FX_NO_MORE_SPACE** (0x0A) El medio asociado con este archivo no tiene suficientes clústeres disponibles.</span><span class="sxs-lookup"><span data-stu-id="86a91-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="86a91-1337">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1338">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1339">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1340">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-1341">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1342">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-1343">**FX_PTR_ERROR** (0x18) Puntero o destino no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="86a91-1344">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1345">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1345">Allowed From</span></span>

<span data-ttu-id="86a91-1346">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1347">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="86a91-1348">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1348">See Also</span></span>

- <span data-ttu-id="86a91-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1349">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1352">fx_file_close</span></span>
- <span data-ttu-id="86a91-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1353">fx_file_create</span></span>
- <span data-ttu-id="86a91-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1355">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1362">fx_file_open</span></span>
- <span data-ttu-id="86a91-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1363">fx_file_read</span></span>
- <span data-ttu-id="86a91-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1365">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1366">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1367">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1369">fx_file_write</span></span>
- <span data-ttu-id="86a91-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="86a91-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1375">fx_file_close</span></span>

<span data-ttu-id="86a91-1376">Cierra el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1377">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="86a91-1378">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1378">Description</span></span>

<span data-ttu-id="86a91-1379">Este servicio cierra el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1379">This service closes the specified file.</span></span> <span data-ttu-id="86a91-1380">Si el archivo estaba abierto para escritura y se ha modificado, este servicio completa el proceso de modificación del archivo actualizando su entrada de directorio con el nuevo tamaño y la fecha y hora actuales del sistema.</span><span class="sxs-lookup"><span data-stu-id="86a91-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1381">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1381">Input Parameters</span></span>

- <span data-ttu-id="86a91-1382">**file_ptr**: puntero a un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1383">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1383">Return Values</span></span>

- <span data-ttu-id="86a91-1384">**FX_SUCCESS** (0x00) Cierre correcto de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="86a91-1385">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="86a91-1386">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1387">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1388">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1389">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o atributos.</span><span class="sxs-lookup"><span data-stu-id="86a91-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="86a91-1390">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1391">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1391">Allowed From</span></span>

<span data-ttu-id="86a91-1392">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1393">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1394">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1394">See Also</span></span>

- <span data-ttu-id="86a91-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1395">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1399">fx_file_create</span></span>
- <span data-ttu-id="86a91-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1401">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1408">fx_file_open</span></span>
- <span data-ttu-id="86a91-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1409">fx_file_read</span></span>
- <span data-ttu-id="86a91-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1411">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1412">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1413">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1415">fx_file_write</span></span>
- <span data-ttu-id="86a91-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="86a91-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1421">fx_file_create</span></span>

<span data-ttu-id="86a91-1422">Crea un archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1423">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="86a91-1424">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1424">Description</span></span>

<span data-ttu-id="86a91-1425">Este servicio crea el archivo especificado en el directorio predeterminado o en la ruta de acceso al directorio suministrada con el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-1426">*Este servicio crea un archivo de longitud cero, es decir, sin clústeres asignados. La asignación se realizará automáticamente en las escrituras de archivos posteriores o se puede realizar por adelantado con el servicio fx_file_allocate o fx_file_extended_allocate para un espacio más allá de 4 GB).*</span><span class="sxs-lookup"><span data-stu-id="86a91-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1427">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1427">Input Parameters</span></span>

- <span data-ttu-id="86a91-1428">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-1429">**file_name**: puntero al nombre del archivo que se va a crear (la ruta de acceso del directorio es opcional).</span><span class="sxs-lookup"><span data-stu-id="86a91-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1430">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1430">Return Values</span></span>

- <span data-ttu-id="86a91-1431">**FX_SUCCESS** (0x00) Creación correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="86a91-1432">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-1433">**FX_ALREADY_CREATED** (0x0B) El archivo especificado ya se había creado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="86a91-1434">**FX_NO_MORE_SPACE** (0x0A) No hay más entradas en el directorio raíz o no hay más clústeres disponibles.</span><span class="sxs-lookup"><span data-stu-id="86a91-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="86a91-1435">**FX_INVALID_PATH** (0x0D) Ruta de acceso no válida proporcionada con el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="86a91-1436">**FX_INVALID_NAME** (0x0C) El nombre de archivo no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="86a91-1437">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1438">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1439">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1440">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-1441">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-1442">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="86a91-1443">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1444">**FX_WRITE_PROTECT** (0x23) El medio subyacente está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="86a91-1445">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="86a91-1446">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1447">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1447">Allowed From</span></span>

<span data-ttu-id="86a91-1448">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1449">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1450">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1450">See Also</span></span>
- <span data-ttu-id="86a91-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1451">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1455">fx_file_close</span></span>
- <span data-ttu-id="86a91-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1457">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1464">fx_file_open</span></span>
- <span data-ttu-id="86a91-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1465">fx_file_read</span></span>
- <span data-ttu-id="86a91-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1467">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1468">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1469">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1471">fx_file_write</span></span>
- <span data-ttu-id="86a91-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="86a91-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="86a91-1478">Establece la fecha y la hora del archivo</span><span class="sxs-lookup"><span data-stu-id="86a91-1478">Sets file date and time</span></span>

<span data-ttu-id="86a91-1479">Establecimiento de la fecha y la hora del archivo</span><span class="sxs-lookup"><span data-stu-id="86a91-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1480">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1480">Prototype</span></span>

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a><span data-ttu-id="86a91-1481">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1481">Description</span></span>

<span data-ttu-id="86a91-1482">Este servicio establece la fecha y hora del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="86a91-1483">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1483">Input Parameters</span></span>

- <span data-ttu-id="86a91-1484">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-1485">**file_name**: puntero al nombre del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="86a91-1486">**year**: valor del año (de 1980 a 2107 inclusive).</span><span class="sxs-lookup"><span data-stu-id="86a91-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="86a91-1487">**month**: valor del mes (de 1 a 12 inclusive).</span><span class="sxs-lookup"><span data-stu-id="86a91-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="86a91-1488">**day**: valor del día (de 1 a 31 inclusive).</span><span class="sxs-lookup"><span data-stu-id="86a91-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="86a91-1489">**hour**: valor de la hora (de 0 a 23 inclusive).</span><span class="sxs-lookup"><span data-stu-id="86a91-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="86a91-1490">**minute**: valor del minuto (de 0 a 59 inclusive).</span><span class="sxs-lookup"><span data-stu-id="86a91-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="86a91-1491">**second**: valor del segundo (de 0 a 59 inclusive).</span><span class="sxs-lookup"><span data-stu-id="86a91-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1492">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1492">Return Values</span></span>

- <span data-ttu-id="86a91-1493">**FX_SUCCESS** (0x00) Establecimiento correcto de fecha y hora.</span><span class="sxs-lookup"><span data-stu-id="86a91-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="86a91-1494">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-1495">**FX_NOT_FOUND** (0x04) No se ha encontrado el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="86a91-1496">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="86a91-1497">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1498">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1499">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-1500">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="86a91-1501">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1502">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-1503">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="86a91-1504">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="86a91-1505">**FX_INVALID_YEAR** (0x12) El año no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="86a91-1506">**FX_INVALID_MONTH** (0x13) El mes no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="86a91-1507">**FX_INVALID_DAY** (0x14) El día no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="86a91-1508">**FX_INVALID_HOUR** (0x15) La hora no es válida.</span><span class="sxs-lookup"><span data-stu-id="86a91-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="86a91-1509">**FX_INVALID_MINUTE** (0x16) El minuto no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="86a91-1510">**FX_INVALID_SECOND** (0x17) El segundo no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1511">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1511">Allowed From</span></span>

<span data-ttu-id="86a91-1512">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1513">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="86a91-1514">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1514">See Also</span></span>

- <span data-ttu-id="86a91-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1515">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1519">fx_file_close</span></span>
- <span data-ttu-id="86a91-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1520">fx_file_create</span></span>
- <span data-ttu-id="86a91-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1521">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1528">fx_file_open</span></span>
- <span data-ttu-id="86a91-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1529">fx_file_read</span></span>
- <span data-ttu-id="86a91-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1531">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1532">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1533">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1535">fx_file_write</span></span>
- <span data-ttu-id="86a91-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="86a91-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="86a91-1542">Elimina el archivo</span><span class="sxs-lookup"><span data-stu-id="86a91-1542">Deletes file</span></span>

<span data-ttu-id="86a91-1543">Eliminación de un archivo</span><span class="sxs-lookup"><span data-stu-id="86a91-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1544">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="86a91-1545">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1545">Description</span></span>

<span data-ttu-id="86a91-1546">Este servicio elimina el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="86a91-1547">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1547">Input Parameters</span></span>

- <span data-ttu-id="86a91-1548">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-1549">**file_name**: puntero al nombre del archivo que se va a eliminar (la ruta de acceso del directorio es opcional).</span><span class="sxs-lookup"><span data-stu-id="86a91-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1550">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1550">Return Values</span></span>

- <span data-ttu-id="86a91-1551">**FX_SUCCESS** (0x00) Eliminación correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="86a91-1552">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-1553">**FX_NOT FOUND** (0x04) No se ha encontrado el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="86a91-1554">**FX_NOT_A_FILE** (0x05) El nombre de archivo especificado era un directorio o un volumen.</span><span class="sxs-lookup"><span data-stu-id="86a91-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="86a91-1555">**FX_ACCESS_ERROR** (0x06) El archivo especificado está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="86a91-1556">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1557">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1558">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1559">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-1560">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-1561">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1562">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-1563">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="86a91-1564">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-1565">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1566">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1566">Allowed From</span></span>

<span data-ttu-id="86a91-1567">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1568">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1569">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1569">See Also</span></span>

- <span data-ttu-id="86a91-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1570">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1574">fx_file_close</span></span>
- <span data-ttu-id="86a91-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1575">fx_file_create</span></span>
- <span data-ttu-id="86a91-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1583">fx_file_open</span></span>
- <span data-ttu-id="86a91-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1584">fx_file_read</span></span>
- <span data-ttu-id="86a91-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1586">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1587">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1588">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1590">fx_file_write</span></span>
- <span data-ttu-id="86a91-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="86a91-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="86a91-1597">Asigna espacio para un archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1598">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="86a91-1599">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1599">Description</span></span>

<span data-ttu-id="86a91-1600">Este servicio asigna y vincula uno o más clústeres contiguos al final del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="86a91-1601">FileX determina el número de clústeres necesarios dividiendo el tamaño solicitado por el número de bytes por clúster.</span><span class="sxs-lookup"><span data-stu-id="86a91-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="86a91-1602">Después, el resultado se redondea al siguiente clúster completo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="86a91-1603">Este servicio está diseñado para exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="86a91-1604">El parámetro *size* toma un valor entero de 64 bits, lo que permite que el autor de la llamada preasigne espacio más allá del intervalo de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="86a91-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1605">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1605">Input Parameters</span></span>

- <span data-ttu-id="86a91-1606">**file_ptr**: puntero a un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="86a91-1607">**size**: número de bytes que se asignan al archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1608">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1608">Return Values</span></span>

- <span data-ttu-id="86a91-1609">**FX_SUCCESS** (0x00) Asignación correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="86a91-1610">**FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="86a91-1611">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="86a91-1612">**FX_NO_MORE_SPACE** (0x0A) El medio asociado con este archivo no tiene suficientes clústeres disponibles.</span><span class="sxs-lookup"><span data-stu-id="86a91-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="86a91-1613">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1614">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1615">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1616">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-1617">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1618">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-1619">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-1620">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1621">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1621">Allowed From</span></span>

<span data-ttu-id="86a91-1622">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1623">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1624">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1624">See Also</span></span>

- <span data-ttu-id="86a91-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1625">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1629">fx_file_close</span></span>
- <span data-ttu-id="86a91-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1630">fx_file_create</span></span>
- <span data-ttu-id="86a91-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1632">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1638">fx_file_open</span></span>
- <span data-ttu-id="86a91-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1639">fx_file_read</span></span>
- <span data-ttu-id="86a91-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1641">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1642">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1643">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1645">fx_file_write</span></span>
- <span data-ttu-id="86a91-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="86a91-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="86a91-1652">Mejor esfuerzo para asignar espacio para un archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1653">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="86a91-1654">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1654">Description</span></span>

<span data-ttu-id="86a91-1655">Este servicio asigna y vincula uno o más clústeres contiguos al final del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="86a91-1656">FileX determina el número de clústeres necesarios dividiendo el tamaño solicitado por el número de bytes por clúster.</span><span class="sxs-lookup"><span data-stu-id="86a91-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="86a91-1657">Después, el resultado se redondea al siguiente clúster completo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="86a91-1658">Si no hay suficientes clústeres consecutivos disponibles en el medio, este servicio vincula el bloque más grande disponible de clústeres consecutivos al archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="86a91-1659">La cantidad de espacio realmente asignado al archivo se devuelve al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="86a91-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="86a91-1660">Este servicio está diseñado para exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="86a91-1661">El parámetro *size* toma un valor entero de 64 bits, lo que permite que el autor de la llamada preasigne espacio más allá del intervalo de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="86a91-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1662">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1662">Input Parameters</span></span>

- <span data-ttu-id="86a91-1663">**file_ptr**: puntero a un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="86a91-1664">**size**: número de bytes que se asignan al archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1665">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1665">Return Values</span></span>

- <span data-ttu-id="86a91-1666">**FX_SUCCESS** (0x00) Asignación correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="86a91-1667">**FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="86a91-1668">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="86a91-1669">**FX_NO_MORE_SPACE** (0x0A) El medio asociado con este archivo no tiene suficientes clústeres disponibles.</span><span class="sxs-lookup"><span data-stu-id="86a91-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="86a91-1670">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1671">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1672">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1673">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-1674">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1675">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-1676">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-1677">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1678">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1678">Allowed From</span></span>

<span data-ttu-id="86a91-1679">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1680">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1680">Example</span></span>

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1681">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1681">See Also</span></span>

- <span data-ttu-id="86a91-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1682">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1686">fx_file_close</span></span>
- <span data-ttu-id="86a91-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1687">fx_file_create</span></span>
- <span data-ttu-id="86a91-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1689">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1695">fx_file_open</span></span>
- <span data-ttu-id="86a91-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1696">fx_file_read</span></span>
- <span data-ttu-id="86a91-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1698">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1699">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1700">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1702">fx_file_write</span></span>
- <span data-ttu-id="86a91-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="86a91-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="86a91-1709">Posiciona en un desplazamiento de bytes relativo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1710">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="86a91-1711">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1711">Description</span></span>

<span data-ttu-id="86a91-1712">Este servicio posiciona el puntero de lectura y escritura de archivo interno en el desplazamiento de bytes relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="86a91-1713">Cualquier solicitud de lectura o escritura de archivo subsiguiente comenzará en esta ubicación del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="86a91-1714">Este servicio está diseñado para exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="86a91-1715">El parámetro *byte_offset* toma un valor entero de 64 bits, lo que permite al autor de la llamada volver a posicionar el puntero de lectura y escritura más allá del intervalo de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="86a91-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-1716">*Si la operación de búsqueda intenta buscar más allá del final del archivo, el puntero de lectura y escritura del archivo se posiciona al final del archivo. Por el contrario, si la operación de búsqueda intenta posicionarse antes del principio del archivo, el puntero de lectura y escritura del archivo se posiciona al principio del archivo.*</span><span class="sxs-lookup"><span data-stu-id="86a91-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1717">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1717">Input Parameters</span></span>

- <span data-ttu-id="86a91-1718">**file_ptr**: puntero a un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="86a91-1719">**byte_offset**: desplazamiento de bytes relativo deseado en el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="86a91-1720">**seek_from**: la dirección y la ubicación desde donde se realizará la búsqueda relativa.</span><span class="sxs-lookup"><span data-stu-id="86a91-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="86a91-1721">Las opciones de búsqueda válidas son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="86a91-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="86a91-1722">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="86a91-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="86a91-1723">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="86a91-1724">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="86a91-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="86a91-1725">FX_SEEK_BACK (0x03) Si se especifica FX_SEEK_BEGIN, la operación de búsqueda se realiza desde el principio del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="86a91-1726">Si se especifica FX_SEEK_END, la operación de búsqueda se realiza hacia atrás desde el final del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="86a91-1727">Si se especifica FX_SEEK_FORWARD, la operación de búsqueda se realiza hacia delante desde la posición actual del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="86a91-1728">Si se especifica FX_SEEK_BACK, la operación de búsqueda se realiza hacia atrás desde la posición actual del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1729">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1729">Return Values</span></span>

- <span data-ttu-id="86a91-1730">**FX_SUCCESS** (0x00) Búsqueda relativa de archivo correcta.</span><span class="sxs-lookup"><span data-stu-id="86a91-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="86a91-1731">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="86a91-1732">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1733">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1734">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-1735">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1736">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-1737">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1738">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1738">Allowed From</span></span>

<span data-ttu-id="86a91-1739">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1740">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1741">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1741">See Also</span></span>

- <span data-ttu-id="86a91-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1742">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1746">fx_file_close</span></span>
- <span data-ttu-id="86a91-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1747">fx_file_create</span></span>
- <span data-ttu-id="86a91-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1749">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1755">fx_file_open</span></span>
- <span data-ttu-id="86a91-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1756">fx_file_read</span></span>
- <span data-ttu-id="86a91-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1758">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1759">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1760">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1762">fx_file_write</span></span>
- <span data-ttu-id="86a91-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="86a91-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="86a91-1769">Posiciona en el desplazamiento de bytes.</span><span class="sxs-lookup"><span data-stu-id="86a91-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1770">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="86a91-1771">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1771">Description</span></span>

<span data-ttu-id="86a91-1772">Este servicio posiciona el puntero de lectura y escritura de archivo interno en el desplazamiento de bytes especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="86a91-1773">Cualquier solicitud de lectura o escritura de archivo subsiguiente comenzará en esta ubicación del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="86a91-1774">Este servicio está diseñado para exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="86a91-1775">El parámetro *byte_offset* toma un valor entero de 64 bits, lo que permite al autor de la llamada volver a posicionar el puntero de lectura y escritura más allá del intervalo de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="86a91-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1776">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1776">Input Parameters</span></span>

- <span data-ttu-id="86a91-1777">**file_ptr**: puntero al bloque de control de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="86a91-1778">**byte_offset**: desplazamiento de bytes deseado en el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="86a91-1779">Un valor cero posicionará el puntero de lectura y escritura al principio del archivo, mientras que un valor mayor que el tamaño del archivo posicionará el puntero de lectura y escritura al final del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1780">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1780">Return Values</span></span>

- <span data-ttu-id="86a91-1781">**FX_SUCCESS** (0x00) Búsqueda correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="86a91-1782">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="86a91-1783">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1784">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1785">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-1786">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1787">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-1788">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1789">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1789">Allowed From</span></span>

<span data-ttu-id="86a91-1790">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1791">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1792">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1792">See Also</span></span>

- <span data-ttu-id="86a91-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1793">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1797">fx_file_close</span></span>
- <span data-ttu-id="86a91-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1798">fx_file_create</span></span>
- <span data-ttu-id="86a91-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1800">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1806">fx_file_open- fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="86a91-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1808">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1809">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1810">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1812">fx_file_write</span></span>
- <span data-ttu-id="86a91-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="86a91-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="86a91-1819">Trunca el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1820">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="86a91-1821">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1821">Description</span></span>

<span data-ttu-id="86a91-1822">Este servicio trunca el tamaño del archivo al tamaño especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="86a91-1823">Si el tamaño proporcionado es mayor que el tamaño real del archivo, este servicio no hace nada.</span><span class="sxs-lookup"><span data-stu-id="86a91-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="86a91-1824">No se libera ninguno de los clústeres de medios asociados con el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-1825">*Tenga cuidado al truncar archivos que también pueden estar abiertos para lectura al mismo tiempo. El truncamiento de un archivo abierto también para lectura puede dar lugar a lectura de datos no válidos.*</span><span class="sxs-lookup"><span data-stu-id="86a91-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="86a91-1826">Este servicio está diseñado para exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="86a91-1827">El parámetro *size* toma un valor entero de 64 bits, lo que permite que el autor de la llamada opere más allá del intervalo de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="86a91-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1828">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1828">Input Parameters</span></span>

- <span data-ttu-id="86a91-1829">**file_ptr**: puntero al bloque de control de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="86a91-1830">**size**: nuevo tamaño de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1830">**size**: New file size.</span></span> <span data-ttu-id="86a91-1831">Se descartan los bytes más allá de este nuevo tamaño de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1832">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1832">Return Values</span></span>

- <span data-ttu-id="86a91-1833">**FX_SUCCESS** (0x00) Truncamiento correcto de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="86a91-1834">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="86a91-1835">**FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="86a91-1836">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1837">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1838">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-1839">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-1840">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1841">**FX_WRITE_PROTECT** (0x23) El medio subyacente está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="86a91-1842">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-1843">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1844">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1844">Allowed From</span></span>

<span data-ttu-id="86a91-1845">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1846">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1847">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1847">See Also</span></span>

- <span data-ttu-id="86a91-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1848">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1852">fx_file_close</span></span>
- <span data-ttu-id="86a91-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1853">fx_file_create</span></span>
- <span data-ttu-id="86a91-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1855">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1861">fx_file_open</span></span>
- <span data-ttu-id="86a91-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1862">fx_file_read</span></span>
- <span data-ttu-id="86a91-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1864">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1865">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1866">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1868">fx_file_write</span></span>
- <span data-ttu-id="86a91-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="86a91-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="86a91-1875">Trunca el archivo y libera los clústeres.</span><span class="sxs-lookup"><span data-stu-id="86a91-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1876">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="86a91-1877">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1877">Description</span></span>

<span data-ttu-id="86a91-1878">Este servicio trunca el tamaño del archivo al tamaño especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="86a91-1879">Si el tamaño proporcionado es mayor que el tamaño real del archivo, este servicio no hace nada.</span><span class="sxs-lookup"><span data-stu-id="86a91-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="86a91-1880">A diferencia del servicio ***fx_file_extended_truncate***, este servicio libera todos los clústeres no utilizados.</span><span class="sxs-lookup"><span data-stu-id="86a91-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-1881">*Tenga cuidado al truncar archivos que también pueden estar abiertos para lectura al mismo tiempo. El truncamiento de un archivo abierto también para lectura puede dar lugar a lectura de datos no válidos.*</span><span class="sxs-lookup"><span data-stu-id="86a91-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="86a91-1882">Este servicio está diseñado para exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="86a91-1883">El parámetro *size* toma un valor entero de 64 bits, lo que permite que el autor de la llamada opere más allá del intervalo de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="86a91-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1884">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1884">Input Parameters</span></span>

- <span data-ttu-id="86a91-1885">**file_ptr**: puntero a un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="86a91-1886">**size**: nuevo tamaño de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1886">**size**: New file size.</span></span> <span data-ttu-id="86a91-1887">Se descartan los bytes más allá de este nuevo tamaño de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1888">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1888">Return Values</span></span>

- <span data-ttu-id="86a91-1889">**FX_SUCCESS** (0x00) Truncamiento correcto de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="86a91-1890">**FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="86a91-1891">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="86a91-1892">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1893">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-1894">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1895">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-1896">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-1897">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1898">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-1899">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-1900">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1901">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1901">Allowed From</span></span>

<span data-ttu-id="86a91-1902">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1903">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1904">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1904">See Also</span></span>

- <span data-ttu-id="86a91-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1905">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-1909">fx_file_close</span></span>
- <span data-ttu-id="86a91-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1910">fx_file_create</span></span>
- <span data-ttu-id="86a91-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1912">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1918">fx_file_open</span></span>
- <span data-ttu-id="86a91-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1919">fx_file_read</span></span>
- <span data-ttu-id="86a91-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1921">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1922">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1923">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1925">fx_file_write</span></span>
- <span data-ttu-id="86a91-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="86a91-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-1931">fx_file_open</span></span>

<span data-ttu-id="86a91-1932">Abre el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1933">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="86a91-1934">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1934">Description</span></span>

<span data-ttu-id="86a91-1935">Este servicio abre el archivo especificado para lectura o escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="86a91-1936">Se puede abrir un archivo para lectura varias veces, mientras que un archivo solo se puede abrir para escritura una vez hasta que el escritor cierre el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-1937">*Se debe tener cuidado si un archivo se abre simultáneamente para lectura y escritura. Puede que el lector no vea la escritura de archivo realizada cuando un archivo se abre al mismo tiempo para la lectura, a menos que el lector cierre y vuelva a abrir el archivo. Del mismo modo, el escritor del archivo debe tener cuidado al usar los servicios de truncamiento de archivo. Si el escritor trunca un archivo, los lectores del mismo archivo podrían devolver datos no válidos.*</span><span class="sxs-lookup"><span data-stu-id="86a91-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-1938">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-1938">Input Parameters</span></span>

- <span data-ttu-id="86a91-1939">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-1940">**file_ptr**: puntero al bloque de control de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="86a91-1941">**file_name**: puntero al nombre del archivo que se va a abrir (la ruta de acceso del directorio es opcional).</span><span class="sxs-lookup"><span data-stu-id="86a91-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="86a91-1942">**open_type**: tipo de archivo abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="86a91-1943">Las opciones válidas de tipo de apertura son:</span><span class="sxs-lookup"><span data-stu-id="86a91-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="86a91-1944">FX_OPEN_FOR_READ (0x00)</span><span class="sxs-lookup"><span data-stu-id="86a91-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="86a91-1945">FX_OPEN_FOR_WRITE (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="86a91-1946">FX_OPEN_FOR_READ_FAST (0x02)</span><span class="sxs-lookup"><span data-stu-id="86a91-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="86a91-1947">Abrir archivos con FX_OPEN_FOR_READ y FX_OPEN_FOR_READ_FAST es similar:</span><span class="sxs-lookup"><span data-stu-id="86a91-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="86a91-1948">FX_OPEN_FOR_READ incluye la comprobación de que la lista vinculada de clústeres que componen el archivo está intacta y FX_OPEN_FOR_READ_FAST no realiza esta comprobación, lo que hace que sea más rápida.</span><span class="sxs-lookup"><span data-stu-id="86a91-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-1949">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-1949">Return Values</span></span>

- <span data-ttu-id="86a91-1950">**FX_SUCCESS** (0x00) Apertura correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="86a91-1951">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-1952">**FX_NOT FOUND** (0x04) No se ha encontrado el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="86a91-1953">**FX_NOT_A_FILE** (0x05) El nombre de archivo especificado era un directorio o un volumen.</span><span class="sxs-lookup"><span data-stu-id="86a91-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="86a91-1954">**FX_FILE_CORRUPT** (0x08) El archivo especificado está dañado y la apertura generó un error.</span><span class="sxs-lookup"><span data-stu-id="86a91-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="86a91-1955">**FX_ACCESS_ERROR** (0x06) El archivo especificado ya está abierto o el tipo de apertura no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="86a91-1956">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-1957">**FX_MEDIA_INVALID** (0x02) Medio no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="86a91-1958">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-1959">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-1960">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-1961">**FX_WRITE_PROTECT** (0x23) El medio subyacente está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="86a91-1962">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="86a91-1963">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-1964">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-1964">Allowed From</span></span>

<span data-ttu-id="86a91-1965">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-1966">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-1967">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-1967">See Also</span></span>

- <span data-ttu-id="86a91-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1968">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1972">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="86a91-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-1974">fx_file_delete</span></span>
- <span data-ttu-id="86a91-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1981">fx_file_read</span></span>
- <span data-ttu-id="86a91-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1983">fx_file_rename</span></span>
- <span data-ttu-id="86a91-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-1984">fx_file_seek</span></span>
- <span data-ttu-id="86a91-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-1985">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-1987">fx_file_write</span></span>
- <span data-ttu-id="86a91-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="86a91-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-1993">fx_file_read</span></span>

<span data-ttu-id="86a91-1994">Lee bytes del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-1995">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="86a91-1996">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-1996">Description</span></span>

<span data-ttu-id="86a91-1997">Este servicio lee bytes del archivo y los almacena en el búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="86a91-1998">Una vez completada la lectura, el puntero de lectura interno del archivo se ajusta para que apunte al siguiente byte del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="86a91-1999">Si quedan menos bytes en la solicitud, solo los bytes restantes se almacenan en el búfer.</span><span class="sxs-lookup"><span data-stu-id="86a91-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="86a91-2000">En cualquier caso, el número total de bytes colocados en el búfer se devuelve al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="86a91-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2001">*La aplicación debe asegurarse de que el búfer proporcionado pueda almacenar el número especificado de bytes solicitados.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2002">*Se consigue un rendimiento más rápido si el búfer de destino se encuentra en un límite de palabra larga y el tamaño solicitado es divisible en partes iguales por sizeof(**ULONG**).*</span><span class="sxs-lookup"><span data-stu-id="86a91-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2003">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2003">Input Parameters</span></span>

- <span data-ttu-id="86a91-2004">**file_ptr**: puntero al bloque de control de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="86a91-2005">**buffer_ptr**: puntero al búfer de destino para la lectura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="86a91-2006">**request_size**: número máximo de bytes que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="86a91-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="86a91-2007">**actual_size**: puntero a la variable que va a contener el número real de bytes leídos en el búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2008">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2008">Return Values</span></span>

- <span data-ttu-id="86a91-2009">**FX_SUCCESS** (0x00) Lectura correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="86a91-2010">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="86a91-2011">**FX_FILE_CORRUPT** (0x08) El archivo especificado está dañado y la lectura generó un error.</span><span class="sxs-lookup"><span data-stu-id="86a91-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="86a91-2012">**FX_END_OF_FILE** (0x09) Se ha alcanzado el final del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="86a91-2013">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-2014">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-2015">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2016">**FX_PTR_ERROR** (0x18) Puntero no válido de búfer o archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="86a91-2017">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2018">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2018">Allowed From</span></span>

<span data-ttu-id="86a91-2019">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2020">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2020">Example</span></span>

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a><span data-ttu-id="86a91-2021">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2021">See Also</span></span>

- <span data-ttu-id="86a91-2022">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="86a91-2023">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="86a91-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="86a91-2024">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="86a91-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="86a91-2025">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="86a91-2026">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="86a91-2026">fx_file_close,</span></span>
- <span data-ttu-id="86a91-2027">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="86a91-2027">fx_file_create,</span></span>
- <span data-ttu-id="86a91-2028">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="86a91-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="86a91-2029">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="86a91-2029">fx_file_delete,</span></span>
- <span data-ttu-id="86a91-2030">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="86a91-2031">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="86a91-2032">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="86a91-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="86a91-2033">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="86a91-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="86a91-2034">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="86a91-2035">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="86a91-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="86a91-2036">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="86a91-2036">fx_file_open,</span></span>
- <span data-ttu-id="86a91-2037">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="86a91-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="86a91-2038">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="86a91-2038">fx_file_rename,</span></span>
- <span data-ttu-id="86a91-2039">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="86a91-2039">fx_file_seek,</span></span>
- <span data-ttu-id="86a91-2040">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="86a91-2041">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="86a91-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="86a91-2042">fx_file_write,</span><span class="sxs-lookup"><span data-stu-id="86a91-2042">fx_file_write,</span></span>
- <span data-ttu-id="86a91-2043">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="86a91-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="86a91-2044">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="86a91-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="86a91-2045">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="86a91-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="86a91-2046">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="86a91-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="86a91-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="86a91-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="86a91-2049">Posiciona en un desplazamiento de bytes relativo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2050">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="86a91-2051">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2051">Description</span></span>

<span data-ttu-id="86a91-2052">Este servicio posiciona el puntero de lectura y escritura de archivo interno en el desplazamiento de bytes relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="86a91-2053">Cualquier solicitud de lectura o escritura de archivo subsiguiente comenzará en esta ubicación del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-2054">*Si la operación de búsqueda intenta buscar más allá del final del archivo, el puntero de lectura y escritura del archivo se posiciona al final del archivo. Por el contrario, si la operación de búsqueda intenta posicionarse antes del principio del archivo, el puntero de lectura y escritura del archivo se posiciona al principio del archivo.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="86a91-2055">Para buscar con un valor de desplazamiento más allá de 4 GB, la aplicación debe usar el servicio *fx_file_extended_relative_seek*.</span><span class="sxs-lookup"><span data-stu-id="86a91-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2056">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2056">Input Parameters</span></span>

- <span data-ttu-id="86a91-2057">**file_ptr**: puntero a un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="86a91-2058">**byte_offset**: desplazamiento de bytes relativo deseado en el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="86a91-2059">**seek_from**: la dirección y la ubicación desde donde se realizará la búsqueda relativa.</span><span class="sxs-lookup"><span data-stu-id="86a91-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="86a91-2060">Las opciones de búsqueda válidas son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="86a91-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="86a91-2061">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="86a91-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="86a91-2062">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="86a91-2063">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="86a91-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="86a91-2064">FX_SEEK_BACK (0x03)</span><span class="sxs-lookup"><span data-stu-id="86a91-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="86a91-2065">Si se especifica FX_SEEK_BEGIN, la operación de búsqueda se realiza desde el principio del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="86a91-2066">Si se especifica FX_SEEK_END, la operación de búsqueda se realiza hacia atrás desde el final del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="86a91-2067">Si se especifica FX_SEEK_FORWARD, la operación de búsqueda se realiza hacia delante desde la posición actual del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="86a91-2068">Si se especifica FX_SEEK_BACK, la operación de búsqueda se realiza hacia atrás desde la posición actual del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2069">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2069">Return Values</span></span>

- <span data-ttu-id="86a91-2070">**FX_SUCCESS** (0x00) Búsqueda relativa de archivo correcta.</span><span class="sxs-lookup"><span data-stu-id="86a91-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="86a91-2071">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="86a91-2072">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2073">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-2074">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-2075">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-2076">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-2077">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2078">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2078">Allowed From</span></span>

<span data-ttu-id="86a91-2079">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2080">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-2081">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2081">See Also</span></span>

- <span data-ttu-id="86a91-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2082">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2086">fx_file_close</span></span>
- <span data-ttu-id="86a91-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2087">fx_file_create</span></span>
- <span data-ttu-id="86a91-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-2089">fx_file_delete</span></span>
- <span data-ttu-id="86a91-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2096">fx_file_open</span></span>
- <span data-ttu-id="86a91-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2097">fx_file_read</span></span>
- <span data-ttu-id="86a91-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2098">fx_file_rename</span></span>
- <span data-ttu-id="86a91-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2099">fx_file_seek</span></span>
- <span data-ttu-id="86a91-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2100">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2102">fx_file_write</span></span>
- <span data-ttu-id="86a91-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="86a91-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2108">fx_file_rename</span></span>

<span data-ttu-id="86a91-2109">Cambia el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2110">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="86a91-2111">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2111">Description</span></span>

<span data-ttu-id="86a91-2112">Este servicio cambia el nombre del archivo especificado por *old_file_name*.</span><span class="sxs-lookup"><span data-stu-id="86a91-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="86a91-2113">El cambio de nombre también se realiza en relación con la ruta de acceso especificada o la ruta de acceso predeterminada.</span><span class="sxs-lookup"><span data-stu-id="86a91-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="86a91-2114">Si se especifica una ruta de acceso en el nuevo nombre de archivo, el archivo cuyo nombre ha cambiado se mueve realmente a la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="86a91-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="86a91-2115">Si no se especifica ninguna ruta de acceso, el archivo cuyo nombre ha cambiado se coloca en la ruta de acceso predeterminada actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2116">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2116">Input Parameters</span></span>

- <span data-ttu-id="86a91-2117">**media_ptr**: puntero a un bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="86a91-2118">**old_file_name**: puntero al nombre del archivo cuyo nombre se va a cambiar (la ruta de acceso del directorio es opcional).</span><span class="sxs-lookup"><span data-stu-id="86a91-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="86a91-2119">**new_file_name**: puntero al nuevo nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="86a91-2120">No se permite la ruta de acceso al directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2121">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2121">Return Values</span></span>

- <span data-ttu-id="86a91-2122">**FX_SUCCESS** (0x00) Cambio correcto de nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="86a91-2123">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-2124">**FX_NOT FOUND** (0x04) No se ha encontrado el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="86a91-2125">**FX_NOT_A_FILE** (0x05) El archivo especificado es un directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="86a91-2126">**FX_ACCESS_ERROR** (0x06) El archivo especificado ya está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="86a91-2127">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2128">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-2129">**FX_INVALID_NAME** (0x0C) El nuevo nombre de archivo especificado no es un nombre de archivo válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="86a91-2130">**FX_INVALID_PATH** (0x0D) La ruta de acceso no es válida.</span><span class="sxs-lookup"><span data-stu-id="86a91-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="86a91-2131">**FX_ALREADY_CREATED** (0x0B) Se utiliza el nuevo nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="86a91-2132">**FX_MEDIA_INVALID** (0x02) El medio no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="86a91-2133">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-2134">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-2135">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-2136">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-2137">**FX_FAT_READ_ERROR** (0x03) No se puede leer la tabla FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="86a91-2138">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-2139">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2140">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2140">Allowed From</span></span>

<span data-ttu-id="86a91-2141">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2142">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-2143">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2143">See Also</span></span>

- <span data-ttu-id="86a91-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2144">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2148">fx_file_close</span></span>
- <span data-ttu-id="86a91-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2149">fx_file_create</span></span>
- <span data-ttu-id="86a91-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-2151">fx_file_delete</span></span>
- <span data-ttu-id="86a91-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2158">fx_file_open</span></span>
- <span data-ttu-id="86a91-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2159">fx_file_read</span></span>
- <span data-ttu-id="86a91-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2161">fx_file_seek</span></span>
- <span data-ttu-id="86a91-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2162">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2164">fx_file_write</span></span>
- <span data-ttu-id="86a91-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="86a91-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2170">fx_file_seek</span></span>

<span data-ttu-id="86a91-2171">Posiciona en el desplazamiento de bytes.</span><span class="sxs-lookup"><span data-stu-id="86a91-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2172">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="86a91-2173">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2173">Description</span></span>

<span data-ttu-id="86a91-2174">Este servicio posiciona el puntero de lectura y escritura de archivo interno en el desplazamiento de bytes especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="86a91-2175">Cualquier solicitud de lectura o escritura de archivo subsiguiente comenzará en esta ubicación del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="86a91-2176">Para buscar con un valor de desplazamiento más allá de 4 GB, la aplicación debe usar el servicio *fx_file_extended_seek*.</span><span class="sxs-lookup"><span data-stu-id="86a91-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2177">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2177">Input Parameters</span></span>

- <span data-ttu-id="86a91-2178">**file_ptr**: puntero al bloque de control de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="86a91-2179">**byte_offset**: desplazamiento de bytes deseado en el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="86a91-2180">Un valor cero posicionará el puntero de lectura y escritura al principio del archivo, mientras que un valor mayor que el tamaño del archivo posicionará el puntero de lectura y escritura al final del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2181">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2181">Return Values</span></span>

- <span data-ttu-id="86a91-2182">**FX_SUCCESS** (0x00) Búsqueda correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="86a91-2183">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="86a91-2184">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2185">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-2186">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-2187">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-2188">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-2189">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2190">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2190">Allowed From</span></span>

<span data-ttu-id="86a91-2191">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2192">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-2193">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2193">See Also</span></span>

- <span data-ttu-id="86a91-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2194">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2198">fx_file_close</span></span>
- <span data-ttu-id="86a91-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2199">fx_file_create</span></span>
- <span data-ttu-id="86a91-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-2201">fx_file_delete</span></span>
- <span data-ttu-id="86a91-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2208">fx_file_open</span></span>
- <span data-ttu-id="86a91-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2209">fx_file_read</span></span>
- <span data-ttu-id="86a91-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2210">fx_file_rename</span></span>
- <span data-ttu-id="86a91-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2211">fx_file_seek</span></span>
- <span data-ttu-id="86a91-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2212">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2214">fx_file_write</span></span>
- <span data-ttu-id="86a91-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="86a91-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2220">fx_file_truncate</span></span>

<span data-ttu-id="86a91-2221">Trunca el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2222">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="86a91-2223">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2223">Description</span></span>

<span data-ttu-id="86a91-2224">Este servicio trunca el tamaño del archivo al tamaño especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="86a91-2225">Si el tamaño proporcionado es mayor que el tamaño real del archivo, este servicio no hace nada.</span><span class="sxs-lookup"><span data-stu-id="86a91-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="86a91-2226">No se libera ninguno de los clústeres de medios asociados con el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2227">*Tenga cuidado al truncar archivos que también pueden estar abiertos para lectura al mismo tiempo. El truncamiento de un archivo abierto también para lectura puede dar lugar a lectura de datos no válidos.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="86a91-2228">Para operar más allá de los 4 GB, la aplicación debe usar el servicio *fx_file_extended_truncate*.</span><span class="sxs-lookup"><span data-stu-id="86a91-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2229">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2229">Input Parameters</span></span>

- <span data-ttu-id="86a91-2230">**file_ptr**: puntero al bloque de control de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="86a91-2231">**size**: nuevo tamaño de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2231">**size**: New file size.</span></span> <span data-ttu-id="86a91-2232">Se descartan los bytes más allá de este nuevo tamaño de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2233">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2233">Return Values</span></span>

- <span data-ttu-id="86a91-2234">**FX_SUCCESS** (0x00) Truncamiento correcto de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="86a91-2235">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="86a91-2236">**FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="86a91-2237">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2238">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-2239">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-2240">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-2241">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-2242">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="86a91-2243">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-2244">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2245">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2245">Allowed From</span></span>

<span data-ttu-id="86a91-2246">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2247">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-2248">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2248">See Also</span></span>

- <span data-ttu-id="86a91-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2249">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2253">fx_file_close</span></span>
- <span data-ttu-id="86a91-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2254">fx_file_create</span></span>
- <span data-ttu-id="86a91-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-2256">fx_file_delete</span></span>
- <span data-ttu-id="86a91-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2263">fx_file_open</span></span>
- <span data-ttu-id="86a91-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2264">fx_file_read</span></span>
- <span data-ttu-id="86a91-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2266">fx_file_rename</span></span>
- <span data-ttu-id="86a91-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2267">fx_file_seek</span></span>
- <span data-ttu-id="86a91-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2269">fx_file_write</span></span>
- <span data-ttu-id="86a91-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="86a91-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="86a91-2276">Trunca el archivo y libera los clústeres.</span><span class="sxs-lookup"><span data-stu-id="86a91-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2277">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="86a91-2278">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2278">Description</span></span>

<span data-ttu-id="86a91-2279">Este servicio trunca el tamaño del archivo al tamaño especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="86a91-2280">Si el tamaño proporcionado es mayor que el tamaño real del archivo, este servicio no hace nada.</span><span class="sxs-lookup"><span data-stu-id="86a91-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="86a91-2281">A diferencia del servicio ***fx_file_truncate***, este servicio libera todos los clústeres no utilizados.</span><span class="sxs-lookup"><span data-stu-id="86a91-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2282">*Tenga cuidado al truncar archivos que también pueden estar abiertos para lectura al mismo tiempo. El truncamiento de un archivo abierto también para lectura puede dar lugar a lectura de datos no válidos.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="86a91-2283">Para operar más allá de los 4 GB, la aplicación debe usar el servicio *fx_file_extended_release*.</span><span class="sxs-lookup"><span data-stu-id="86a91-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2284">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2284">Input Parameters</span></span>

- <span data-ttu-id="86a91-2285">**file_ptr**: puntero a un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="86a91-2286">**size**: nuevo tamaño de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2286">**size**: New file size.</span></span> <span data-ttu-id="86a91-2287">Se descartan los bytes más allá de este nuevo tamaño de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2288">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2288">Return Values</span></span>

- <span data-ttu-id="86a91-2289">**FX_SUCCESS** (0x00) Truncamiento correcto de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="86a91-2290">**FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="86a91-2291">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="86a91-2292">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2293">**FX_WRITE_PROTECT** (0x23) El medio subyacente está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="86a91-2294">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="86a91-2295">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-2296">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-2297">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-2298">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.</span><span class="sxs-lookup"><span data-stu-id="86a91-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="86a91-2299">**FX_PTR_ERROR** (0x18) Puntero no válido de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="86a91-2300">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2301">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2301">Allowed From</span></span>

<span data-ttu-id="86a91-2302">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2303">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="86a91-2304">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2304">See Also</span></span>

- <span data-ttu-id="86a91-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2305">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2309">fx_file_close</span></span>
- <span data-ttu-id="86a91-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2310">fx_file_create</span></span>
- <span data-ttu-id="86a91-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-2312">fx_file_delete</span></span>
- <span data-ttu-id="86a91-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2319">fx_file_open</span></span>
- <span data-ttu-id="86a91-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2320">fx_file_read</span></span>
- <span data-ttu-id="86a91-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2322">fx_file_rename</span></span>
- <span data-ttu-id="86a91-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2323">fx_file_seek</span></span>
- <span data-ttu-id="86a91-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2324">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2325">fx_file_write</span></span>
- <span data-ttu-id="86a91-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="86a91-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2331">fx_file_write</span></span>

<span data-ttu-id="86a91-2332">Escribe bytes en el archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2333">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="86a91-2334">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2334">Description</span></span>

<span data-ttu-id="86a91-2335">Este servicio escribe bytes del búfer especificado a partir de la posición actual del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="86a91-2336">Una vez completada la escritura, el puntero de lectura interno del archivo se ajusta para que apunte al siguiente byte del archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2337">*Se consigue un rendimiento más rápido si el búfer de origen se encuentra en un límite de palabra larga y el tamaño solicitado es divisible en partes iguales por sizeof(**ULONG**).*</span><span class="sxs-lookup"><span data-stu-id="86a91-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2338">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2338">Input Parameters</span></span>

- <span data-ttu-id="86a91-2339">**file_ptr**: puntero al bloque de control de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="86a91-2340">**buffer_ptr**: puntero al búfer de origen para la escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="86a91-2341">**size**: número de bytes para escribir.</span><span class="sxs-lookup"><span data-stu-id="86a91-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2342">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2342">Return Values</span></span>

- <span data-ttu-id="86a91-2343">**FX_SUCCESS** (0x00) Escritura correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="86a91-2344">**FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="86a91-2345">**FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="86a91-2346">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio disponible en los medios para realizar esta escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="86a91-2347">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2348">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-2349">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-2350">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-2351">**FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="86a91-2352">**FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="86a91-2353">**FX_PTR_ERROR** (0x18) Puntero no válido de búfer o archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="86a91-2354">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2355">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2355">Allowed From</span></span>

<span data-ttu-id="86a91-2356">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2357">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-2358">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2358">See Also</span></span>

- <span data-ttu-id="86a91-2359">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="86a91-2360">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="86a91-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="86a91-2361">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="86a91-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="86a91-2362">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="86a91-2363">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="86a91-2363">fx_file_close,</span></span>
- <span data-ttu-id="86a91-2364">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="86a91-2364">fx_file_create,</span></span>
- <span data-ttu-id="86a91-2365">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="86a91-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="86a91-2366">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="86a91-2366">fx_file_delete,</span></span>
- <span data-ttu-id="86a91-2367">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="86a91-2368">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="86a91-2369">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="86a91-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="86a91-2370">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="86a91-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="86a91-2371">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="86a91-2372">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="86a91-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="86a91-2373">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="86a91-2373">fx_file_open,</span></span>
- <span data-ttu-id="86a91-2374">fx_file_read,</span><span class="sxs-lookup"><span data-stu-id="86a91-2374">fx_file_read,</span></span>
- <span data-ttu-id="86a91-2375">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="86a91-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="86a91-2376">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="86a91-2376">fx_file_rename,</span></span>
- <span data-ttu-id="86a91-2377">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="86a91-2377">fx_file_seek,</span></span>
- <span data-ttu-id="86a91-2378">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="86a91-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="86a91-2379">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="86a91-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="86a91-2380">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="86a91-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="86a91-2381">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="86a91-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="86a91-2382">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="86a91-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="86a91-2383">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="86a91-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="86a91-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="86a91-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="86a91-2386">Establece la función de notificación de escritura de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2387">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="86a91-2388">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2388">Description</span></span>

<span data-ttu-id="86a91-2389">Este servicio instala la función de devolución de llamada que se invoca después de una operación de escritura de archivo correcta.</span><span class="sxs-lookup"><span data-stu-id="86a91-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2390">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2390">Input Parameters</span></span>

- <span data-ttu-id="86a91-2391">**file_ptr**: puntero al bloque de control de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="86a91-2392">**file_write_notify**: función de devolución de llamada de escritura de archivo que se va a instalar.</span><span class="sxs-lookup"><span data-stu-id="86a91-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="86a91-2393">Establezca la función de devolución de llamada en NULL para deshabilitarla.</span><span class="sxs-lookup"><span data-stu-id="86a91-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2394">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2394">Return Values</span></span>

- <span data-ttu-id="86a91-2395">**FX_SUCCESS** (0x00) La función de devolución de llamada se ha instalado correctamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="86a91-2396">**FX_PTR_ERROR** (0x18) file_ptr es NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="86a91-2397">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2398">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2398">Allowed From</span></span>

<span data-ttu-id="86a91-2399">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2400">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="86a91-2401">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2401">See Also</span></span>

- <span data-ttu-id="86a91-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2402">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2406">fx_file_close</span></span>
- <span data-ttu-id="86a91-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2407">fx_file_create</span></span>
- <span data-ttu-id="86a91-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-2409">fx_file_delete</span></span>
- <span data-ttu-id="86a91-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2416">fx_file_open</span></span>
- <span data-ttu-id="86a91-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2417">fx_file_read</span></span>
- <span data-ttu-id="86a91-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2419">fx_file_rename</span></span>
- <span data-ttu-id="86a91-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-2420">fx_file_seek</span></span>
- <span data-ttu-id="86a91-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-2421">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2423">fx_file_write</span></span>
- <span data-ttu-id="86a91-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="86a91-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2428">fx_media_abort</span></span>

<span data-ttu-id="86a91-2429">Anula las actividades de los medios.</span><span class="sxs-lookup"><span data-stu-id="86a91-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2430">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="86a91-2431">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2431">Description</span></span>

<span data-ttu-id="86a91-2432">Este servicio anula todas las actividades actuales asociadas a los medios, incluido el cierre de todos los archivos abiertos, el envío de una solicitud de anulación al controlador asociado y la colocación de los medios en un estado anulado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="86a91-2433">Normalmente, se llama a este servicio cuando se detectan errores de E/S.</span><span class="sxs-lookup"><span data-stu-id="86a91-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2434">*El medio debe volverse a abrir para poder usarlo de nuevo después de realizar una operación de anulación.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2435">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2435">Input Parameters</span></span>

- <span data-ttu-id="86a91-2436">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2437">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2437">Return Values</span></span>

- <span data-ttu-id="86a91-2438">**FX_SUCCESS** (0x00) Anulación correcta del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="86a91-2439">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-2440">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-2441">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2442">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2442">Allowed From</span></span>

<span data-ttu-id="86a91-2443">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2444">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2445">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2445">See Also</span></span>

- <span data-ttu-id="86a91-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2448">fx_media_check</span></span>
- <span data-ttu-id="86a91-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2449">fx_media_close</span></span>
- <span data-ttu-id="86a91-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2453">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2454">fx_media_format</span></span>
- <span data-ttu-id="86a91-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2455">fx_media_open</span></span>
- <span data-ttu-id="86a91-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2457">fx_media_read</span></span>
- <span data-ttu-id="86a91-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2458">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2461">fx_media_write</span></span>
- <span data-ttu-id="86a91-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="86a91-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="86a91-2464">Invalida la caché del sector lógico.</span><span class="sxs-lookup"><span data-stu-id="86a91-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2465">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="86a91-2466">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2466">Description</span></span>

<span data-ttu-id="86a91-2467">Este servicio vacía todos los sectores sucios de la memoria caché y, a continuación, invalida toda la caché del sector lógico.</span><span class="sxs-lookup"><span data-stu-id="86a91-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2468">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2468">Input Parameters</span></span>

- <span data-ttu-id="86a91-2469">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2470">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2470">Return Values</span></span>

- <span data-ttu-id="86a91-2471">**NX_SUCCESS** (0x00) Invalidación correcta de caché de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="86a91-2472">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-2473">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2474">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o memoria temporal.</span><span class="sxs-lookup"><span data-stu-id="86a91-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="86a91-2475">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2476">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2476">Allowed From</span></span>

<span data-ttu-id="86a91-2477">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2478">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2479">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2479">See Also</span></span>

- <span data-ttu-id="86a91-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2481">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2482">fx_media_check</span></span>
- <span data-ttu-id="86a91-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2483">fx_media_close</span></span>
- <span data-ttu-id="86a91-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2487">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2488">fx_media_format</span></span>
- <span data-ttu-id="86a91-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2489">fx_media_open</span></span>
- <span data-ttu-id="86a91-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2491">fx_media_read</span></span>
- <span data-ttu-id="86a91-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2492">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2495">fx_media_write</span></span>
- <span data-ttu-id="86a91-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="86a91-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2497">fx_media_check</span></span>

<span data-ttu-id="86a91-2498">Comprueba si hay errores en los medios.</span><span class="sxs-lookup"><span data-stu-id="86a91-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2499">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="86a91-2500">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2500">Description</span></span>

<span data-ttu-id="86a91-2501">Este servicio comprueba los medios especificados en busca de errores estructurales básicos, como la vinculación cruzada de archivos o directorios, cadenas FAT no válidas y clústeres perdidos.</span><span class="sxs-lookup"><span data-stu-id="86a91-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="86a91-2502">Este servicio también proporciona la capacidad de corregir los errores detectados.</span><span class="sxs-lookup"><span data-stu-id="86a91-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="86a91-2503">El servicio fx_media_check requiere memoria temporal para el análisis del equilibrio de carga en profundidad de los directorios y archivos del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="86a91-2504">En concreto, la memoria temporal que se proporciona al servicio de comprobación de medios debe ser lo suficientemente grande como para contener varias entradas de directorio, una estructura de datos para "apilar" la posición de la entrada de directorio actual antes de entrar en los subdirectorios y, por último, el mapa de bits de FAT lógica.</span><span class="sxs-lookup"><span data-stu-id="86a91-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="86a91-2505">La memoria temporal debe ser al menos de 512 a 1024 bytes más la memoria para el mapa de bits de FAT lógica, que requiere tantos bits como clústeres haya en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="86a91-2506">Por ejemplo, un dispositivo con 8000 clústeres requiere 1000 bytes para representarse y, por tanto, requiere un área temporal total del orden de los 2048 bytes.</span><span class="sxs-lookup"><span data-stu-id="86a91-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2507">*Solo se debe llamar a este servicio inmediatamente después de fx_media_open y sin ninguna otra actividad del sistema de archivos.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2508">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2508">Input Parameters</span></span>

- <span data-ttu-id="86a91-2509">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-2510">**scratch_memory_ptr**: puntero al principio de la memoria temporal.</span><span class="sxs-lookup"><span data-stu-id="86a91-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="86a91-2511">**scratch_memory_size**: tamaño de la memoria temporal en bytes.</span><span class="sxs-lookup"><span data-stu-id="86a91-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="86a91-2512">**error_correction_option**: bits de opción de corrección de errores, cuando se establece el bit, se realiza la corrección de errores.</span><span class="sxs-lookup"><span data-stu-id="86a91-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="86a91-2513">Los bits de la opción de corrección de errores se definen de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="86a91-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="86a91-2514">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="86a91-2515">FX_DIRECTORY_ERROR (0x02)</span><span class="sxs-lookup"><span data-stu-id="86a91-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="86a91-2516">FX_LOST_CLUSTER_ERROR (0x04) Simplemente se combinan mediante OR las opciones de corrección de errores necesarias.</span><span class="sxs-lookup"><span data-stu-id="86a91-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="86a91-2517">Si no se requiere ninguna corrección de errores, se debe proporcionar el valor 0.</span><span class="sxs-lookup"><span data-stu-id="86a91-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="86a91-2518">**errors_detected_ptr**: destino de los bits de detección de errores, tal y como se define a continuación:</span><span class="sxs-lookup"><span data-stu-id="86a91-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="86a91-2519">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="86a91-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="86a91-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span><span class="sxs-lookup"><span data-stu-id="86a91-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="86a91-2521">FX_FILE_SIZE_ERROR (0x08)</span><span class="sxs-lookup"><span data-stu-id="86a91-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2522">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2522">Return Values</span></span>

- <span data-ttu-id="86a91-2523">**FX_SUCCESS** (0x00) Comprobación correcta del medio, vea el destino de los errores detectados para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="86a91-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="86a91-2524">**FX_ACCESS_ERROR** (0x06) No puede realizar una comprobación con archivos abiertos.</span><span class="sxs-lookup"><span data-stu-id="86a91-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="86a91-2525">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-2526">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-2527">**FX_NO_MORE_SPACE** (0x0A) No hay más espacio en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="86a91-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) La memoria temporal proporcionada no es lo suficientemente grande.</span><span class="sxs-lookup"><span data-stu-id="86a91-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="86a91-2529">**FX_ERROR_NOT_FIXED** (0x93) Daños en el directorio raíz FAT32 que no se pudieron corregir.</span><span class="sxs-lookup"><span data-stu-id="86a91-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="86a91-2530">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2531">**FX_SECTOR_INVALID** (0x89) El sector no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="86a91-2532">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o memoria temporal.</span><span class="sxs-lookup"><span data-stu-id="86a91-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="86a91-2533">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="86a91-2534">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2534">Allowed From</span></span>

<span data-ttu-id="86a91-2535">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2536">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2536">Example</span></span>

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2537">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2537">See Also</span></span>

- <span data-ttu-id="86a91-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2539">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2541">fx_media_close</span></span>
- <span data-ttu-id="86a91-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2545">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2546">fx_media_format</span></span>
- <span data-ttu-id="86a91-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2547">fx_media_open</span></span>
- <span data-ttu-id="86a91-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2549">fx_media_read</span></span>
- <span data-ttu-id="86a91-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2550">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2553">fx_media_write</span></span>
- <span data-ttu-id="86a91-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="86a91-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2555">fx_media_close</span></span>

<span data-ttu-id="86a91-2556">Cierra el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2557">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="86a91-2558">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2558">Description</span></span>

<span data-ttu-id="86a91-2559">Este servicio cierra el medio especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2559">This service closes the specified media.</span></span> <span data-ttu-id="86a91-2560">En el proceso de cierre del medio, todos los archivos abiertos se cierran y el resto de los búferes se vacían en los medios físicos.</span><span class="sxs-lookup"><span data-stu-id="86a91-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2561">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2561">Input Parameters</span></span>

- <span data-ttu-id="86a91-2562">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2563">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2563">Return Values</span></span>

- <span data-ttu-id="86a91-2564">**FX_SUCCESS** (0x00) Cierre correcto del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="86a91-2565">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-2566">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2567">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-2568">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2569">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2569">Allowed From</span></span>

<span data-ttu-id="86a91-2570">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2571">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2572">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2572">See Also</span></span>

- <span data-ttu-id="86a91-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2574">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2576">fx_media_check</span></span>
- <span data-ttu-id="86a91-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2580">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2581">fx_media_format</span></span>
- <span data-ttu-id="86a91-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2582">fx_media_open</span></span>
- <span data-ttu-id="86a91-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2584">fx_media_read</span></span>
- <span data-ttu-id="86a91-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2585">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2588">fx_media_write</span></span>
- <span data-ttu-id="86a91-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="86a91-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="86a91-2591">Establece la función de notificación de cierre de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2592">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="86a91-2593">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2593">Description</span></span>

<span data-ttu-id="86a91-2594">Este servicio establece una función de devolución de llamada de notificación que se invocará después de que un medio se cierre correctamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2595">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2595">Input Parameters</span></span>

- <span data-ttu-id="86a91-2596">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-2597">**media_close_notify**: función de devolución de llamada de notificación de cierre del medio que se va a instalar.</span><span class="sxs-lookup"><span data-stu-id="86a91-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="86a91-2598">Pasar NULL como la función de devolución de llamada deshabilita la devolución de llamada de cierre del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2599">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2599">Return Values</span></span>

- <span data-ttu-id="86a91-2600">**FX_SUCCESS** (0x00) La función de devolución de llamada se ha instalado correctamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="86a91-2601">**FX_PTR_ERROR** (0x18) media_ptr es NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="86a91-2602">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2603">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2603">Allowed From</span></span>

<span data-ttu-id="86a91-2604">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2605">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="86a91-2606">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2606">See Also</span></span>

- <span data-ttu-id="86a91-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2608">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2610">fx_media_check</span></span>
- <span data-ttu-id="86a91-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2611">fx_media_close</span></span>
- <span data-ttu-id="86a91-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2614">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2615">fx_media_format</span></span>
- <span data-ttu-id="86a91-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2616">fx_media_open</span></span>
- <span data-ttu-id="86a91-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2618">fx_media_read</span></span>
- <span data-ttu-id="86a91-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2619">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2622">fx_media_write</span></span>
- <span data-ttu-id="86a91-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="86a91-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="86a91-2625">Formatea el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2626">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2626">Prototype</span></span>

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a><span data-ttu-id="86a91-2627">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2627">Description</span></span>

<span data-ttu-id="86a91-2628">Este servicio da formato al medio proporcionado en un modo compatible con exFAT basado en los parámetros proporcionados.</span><span class="sxs-lookup"><span data-stu-id="86a91-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="86a91-2629">Se debe llamar a este servicio antes de abrir el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2630">*El formato a un medio ya formateado borra eficazmente todos los archivos y directorios del medio.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-2631">*El tamaño del volumen exFAT debe coincidir con el tamaño de la partición (si hay un diseño MBR o GPT) o con el tamaño de todo el dispositivo si no hay diseño de partición (sin MBR o GPT). En Windows existe la limitación de que el disco exFAT si se formatea con algunos valores de sectores totales que sean inferiores a los sectores disponibles.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2631">*The exFAT volume size should match the size of the partition (if there is an MBR or GPT layout), or the size of the whole device if there is no partition layout (no MBR or GPT). There is a limitation on Windows that exFAT Disk will not be recoginzed if formatted with some values of total sectors that are less than available sectors*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2632">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2632">Input Parameters</span></span>

- <span data-ttu-id="86a91-2633">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2633">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="86a91-2634">Solo se utiliza para proporcionar un poco de información básica necesaria para que el controlador funcione.</span><span class="sxs-lookup"><span data-stu-id="86a91-2634">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="86a91-2635">**driver**: puntero al controlador de E/S para este medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2635">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="86a91-2636">Normalmente será el mismo controlador proporcionado a la siguiente llamada de fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="86a91-2636">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="86a91-2637">**driver_info_ptr**: puntero a información opcional que el controlador de E/S puede utilizar.</span><span class="sxs-lookup"><span data-stu-id="86a91-2637">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="86a91-2638">**memory_ptr**: puntero a la memoria de trabajo del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2638">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="86a91-2639">memory_size Especifica el tamaño de la memoria de medios de trabajo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2639">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="86a91-2640">El tamaño debe ser al menos tan grande como el tamaño del sector del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2640">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="86a91-2641">**volume_name**: puntero a la cadena de nombre de volumen, que tiene un máximo de 11 caracteres.</span><span class="sxs-lookup"><span data-stu-id="86a91-2641">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="86a91-2642">**number_of_fats**: número de FAT en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2642">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="86a91-2643">La implementación actual admite una FAT en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2643">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="86a91-2644">**hidden_sectors**: número de sectores ocultos antes del sector de arranque del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2644">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="86a91-2645">Esto es típico cuando hay varias particiones presentes.</span><span class="sxs-lookup"><span data-stu-id="86a91-2645">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="86a91-2646">**total_sectors**: número total de sectores en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2646">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="86a91-2647">**bytes_per_sector**: número de bytes por sector, que suele ser 512.</span><span class="sxs-lookup"><span data-stu-id="86a91-2647">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="86a91-2648">FileX requiere que sea un múltiplo de 32.</span><span class="sxs-lookup"><span data-stu-id="86a91-2648">FileX requires this to be a multiple of 32.</span></span>
> [!IMPORTANT]
> <span data-ttu-id="86a91-2649">*Con referencia a la especificación, los bytes por sector solo pueden tomar los siguientes valores: 512, 1024, 2048 o 4096.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2649">*With reference to the specification the bytes per sector may take on only the following values: 512, 1024, 2048 or 4096.*</span></span>

- <span data-ttu-id="86a91-2650">**sectors_per_cluster**: número de sectores en cada clúster.</span><span class="sxs-lookup"><span data-stu-id="86a91-2650">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="86a91-2651">El clúster es la unidad de asignación mínima en un sistema de archivos FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2651">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="86a91-2652">**volumne_serial_number**: número de serie que se va a usar para este volumen.</span><span class="sxs-lookup"><span data-stu-id="86a91-2652">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="86a91-2653">**boundary_unit**: tamaño de alineación del área de datos física, en número de sectores.</span><span class="sxs-lookup"><span data-stu-id="86a91-2653">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2654">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2654">Return Values</span></span>

- <span data-ttu-id="86a91-2655">**FX_SUCCESS** (0x00) Formato correcto del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2655">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="86a91-2656">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2656">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2657">**FX_PTR_ERROR** (0x18): Puntero no válido de medio, controlador o memoria.</span><span class="sxs-lookup"><span data-stu-id="86a91-2657">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="86a91-2658">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2658">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2659">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2659">Allowed From</span></span>

<span data-ttu-id="86a91-2660">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2660">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2661">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2661">Example</span></span>

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2662">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2662">See Also</span></span>

- <span data-ttu-id="86a91-2663">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2663">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2664">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2664">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2665">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2665">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2666">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2666">fx_media_check</span></span>
- <span data-ttu-id="86a91-2667">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2667">fx_media_close</span></span>
- <span data-ttu-id="86a91-2668">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2668">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2669">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2669">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2670">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2670">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2671">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2671">fx_media_format</span></span>
- <span data-ttu-id="86a91-2672">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2672">fx_media_open</span></span>
- <span data-ttu-id="86a91-2673">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2673">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2674">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2674">fx_media_read</span></span>
- <span data-ttu-id="86a91-2675">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2675">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2676">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2676">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2677">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2677">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2678">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2678">fx_media_write</span></span>
- <span data-ttu-id="86a91-2679">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2679">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="86a91-2680">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2680">fx_media_extended_space_available</span></span>

<span data-ttu-id="86a91-2681">Devuelve el espacio disponible en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2681">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2682">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2682">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="86a91-2683">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2683">Description</span></span>

<span data-ttu-id="86a91-2684">Este servicio devuelve el número de bytes disponibles en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2684">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="86a91-2685">Este servicio está diseñado para exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2685">This service is designed for exFAT.</span></span> <span data-ttu-id="86a91-2686">El puntero al parámetro *available_bytes* toma un valor entero de 64 bits, lo que permite al autor de la llamada trabajar con medios más allá del intervalo de 4 GB.</span><span class="sxs-lookup"><span data-stu-id="86a91-2686">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2687">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2687">Input Parameters</span></span>

- <span data-ttu-id="86a91-2688">**media_ptr**: puntero a un medio abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2688">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="86a91-2689">**available_bytes_ptr**: bytes disponibles que quedan en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2689">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2690">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2690">Return Values</span></span>

- <span data-ttu-id="86a91-2691">**FX_SUCCESS** (0x00) Se ha recuperado correctamente el espacio disponible en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2691">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="86a91-2692">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2692">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-2693">**FX_PTR_ERROR** (0x18) Puntero de medio no válido o el puntero de bytes disponibles es NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-2693">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="86a91-2694">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2694">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2695">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2695">Allowed From</span></span>

<span data-ttu-id="86a91-2696">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2696">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2697">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2697">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2698">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2698">See Also</span></span>

- <span data-ttu-id="86a91-2699">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2699">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2700">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2700">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2701">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2701">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2702">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2702">fx_media_check</span></span>
- <span data-ttu-id="86a91-2703">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2703">fx_media_close</span></span>
- <span data-ttu-id="86a91-2704">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2704">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2705">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2705">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2706">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2706">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2707">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2707">fx_media_format</span></span>
- <span data-ttu-id="86a91-2708">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2708">fx_media_open</span></span>
- <span data-ttu-id="86a91-2709">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2709">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2710">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2710">fx_media_read</span></span>
- <span data-ttu-id="86a91-2711">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2711">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2712">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2712">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2713">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2713">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2714">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2714">fx_media_write</span></span>
- <span data-ttu-id="86a91-2715">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2715">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="86a91-2716">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2716">fx_media_flush</span></span>

<span data-ttu-id="86a91-2717">Vacía los datos en medios físicos.</span><span class="sxs-lookup"><span data-stu-id="86a91-2717">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2718">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2718">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="86a91-2719">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2719">Description</span></span>

<span data-ttu-id="86a91-2720">Este servicio vacía todos los sectores almacenados en caché y las entradas de directorio de los archivos modificados en los medios físicos.</span><span class="sxs-lookup"><span data-stu-id="86a91-2720">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2721">*La aplicación puede llamar periódicamente a esta rutina para reducir el riesgo de daños en los archivos o la pérdida de datos en caso de una interrupción repentina de energía en el destino.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2721">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2722">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2722">Input Parameters</span></span>

- <span data-ttu-id="86a91-2723">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2723">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2724">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2724">Return Values</span></span>

- <span data-ttu-id="86a91-2725">**FX_SUCCESS** (0x00) Vaciado correcto del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2725">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="86a91-2726">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2726">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-2727">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2727">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="86a91-2728">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2728">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-2729">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2729">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2730">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-2730">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-2731">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2731">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-2732">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2732">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2733">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2733">Allowed From</span></span>

<span data-ttu-id="86a91-2734">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2734">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2735">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2735">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2736">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2736">See Also</span></span>

- <span data-ttu-id="86a91-2737">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2737">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2738">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2738">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2739">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2739">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2740">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2740">fx_media_check</span></span>
- <span data-ttu-id="86a91-2741">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2741">fx_media_close</span></span>
- <span data-ttu-id="86a91-2742">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2742">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2743">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2743">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2744">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2744">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2745">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2745">fx_media_format</span></span>
- <span data-ttu-id="86a91-2746">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2746">fx_media_open</span></span>
- <span data-ttu-id="86a91-2747">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2747">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2748">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2748">fx_media_read</span></span>
- <span data-ttu-id="86a91-2749">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2749">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2750">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2750">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2751">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2751">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2752">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2752">fx_media_write</span></span>
- <span data-ttu-id="86a91-2753">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2753">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="86a91-2754">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2754">fx_media_format</span></span>

<span data-ttu-id="86a91-2755">Formatea el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2755">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2756">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2756">Prototype</span></span>

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a><span data-ttu-id="86a91-2757">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2757">Description</span></span>

<span data-ttu-id="86a91-2758">Este servicio da formato al medio proporcionado en un modo compatible con FAT 12/16/32 basado en los parámetros proporcionados.</span><span class="sxs-lookup"><span data-stu-id="86a91-2758">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="86a91-2759">Se debe llamar a este servicio antes de abrir el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2759">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2760">*El formato a un medio ya formateado borra eficazmente todos los archivos y directorios del medio.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2760">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2761">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2761">Input Parameters</span></span>

- <span data-ttu-id="86a91-2762">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2762">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="86a91-2763">Solo se utiliza para proporcionar un poco de información básica necesaria para que el controlador funcione.</span><span class="sxs-lookup"><span data-stu-id="86a91-2763">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="86a91-2764">**driver**: puntero al controlador de E/S para este medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2764">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="86a91-2765">Normalmente será el mismo controlador proporcionado a la siguiente llamada de fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="86a91-2765">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="86a91-2766">**driver_info_ptr**: puntero a información opcional que el controlador de E/S puede utilizar.</span><span class="sxs-lookup"><span data-stu-id="86a91-2766">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="86a91-2767">**memory_ptr**: puntero a la memoria de trabajo del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2767">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="86a91-2768">**memory_size** Especifica el tamaño de la memoria de medios de trabajo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2768">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="86a91-2769">El tamaño debe ser al menos tan grande como el tamaño del sector del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2769">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="86a91-2770">**volume_name**: puntero a la cadena de nombre de volumen, que tiene un máximo de 11 caracteres.</span><span class="sxs-lookup"><span data-stu-id="86a91-2770">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="86a91-2771">**number_of_fats**: número de FAT en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2771">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="86a91-2772">El valor mínimo es 1 para la FAT principal.</span><span class="sxs-lookup"><span data-stu-id="86a91-2772">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="86a91-2773">Los valores mayores que 1 hacen que se mantengan copias de FAT adicionales en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="86a91-2773">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="86a91-2774">**directory_entries**: el número de entradas de directorio en el directorio raíz.</span><span class="sxs-lookup"><span data-stu-id="86a91-2774">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="86a91-2775">**hidden_sectors**: número de sectores ocultos antes del sector de arranque del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2775">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="86a91-2776">Esto es típico cuando hay varias particiones presentes.</span><span class="sxs-lookup"><span data-stu-id="86a91-2776">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="86a91-2777">**total_sectors**: número total de sectores en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2777">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="86a91-2778">**bytes_per_sector**: número de bytes por sector, que suele ser 512.</span><span class="sxs-lookup"><span data-stu-id="86a91-2778">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="86a91-2779">FileX requiere que sea un múltiplo de 32.</span><span class="sxs-lookup"><span data-stu-id="86a91-2779">FileX requires this to be a multiple of 32.</span></span>
> [!IMPORTANT]
> <span data-ttu-id="86a91-2780">*Con referencia a la especificación, los bytes por sector solo pueden tomar los siguientes valores: 512, 1024, 2048 o 4096.*</span><span class="sxs-lookup"><span data-stu-id="86a91-2780">*With reference to the specification the bytes per sector may take on only the following values: 512, 1024, 2048 or 4096.*</span></span>

- <span data-ttu-id="86a91-2781">**sectors_per_cluster**: número de sectores en cada clúster.</span><span class="sxs-lookup"><span data-stu-id="86a91-2781">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="86a91-2782">El clúster es la unidad de asignación mínima en un sistema de archivos FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-2782">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="86a91-2783">**heads**: número de encabezados físicos.</span><span class="sxs-lookup"><span data-stu-id="86a91-2783">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="86a91-2784">**sectors_per_track**: número de sectores por pista.</span><span class="sxs-lookup"><span data-stu-id="86a91-2784">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2785">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2785">Return Values</span></span>

- <span data-ttu-id="86a91-2786">**FX_SUCCESS** (0x00) Formato correcto del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2786">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="86a91-2787">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2787">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2788">**FX_PTR_ERROR** (0x18): Puntero no válido de medio, controlador o memoria.</span><span class="sxs-lookup"><span data-stu-id="86a91-2788">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="86a91-2789">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2789">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2790">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2790">Allowed From</span></span>

<span data-ttu-id="86a91-2791">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2791">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2792">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2792">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2793">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2793">See Also</span></span>

- <span data-ttu-id="86a91-2794">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2794">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2795">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2795">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2796">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2796">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2797">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2797">fx_media_check</span></span>
- <span data-ttu-id="86a91-2798">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2798">fx_media_close</span></span>
- <span data-ttu-id="86a91-2799">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2799">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2800">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2800">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2801">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2801">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2802">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2802">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2803">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2803">fx_media_open</span></span>
- <span data-ttu-id="86a91-2804">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2804">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2805">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2805">fx_media_read</span></span>
- <span data-ttu-id="86a91-2806">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2806">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2807">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2807">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2808">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2808">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2809">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2809">fx_media_write</span></span>
- <span data-ttu-id="86a91-2810">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2810">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="86a91-2811">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2811">fx_media_open</span></span>

<span data-ttu-id="86a91-2812">Abre el medio para el acceso a archivos.</span><span class="sxs-lookup"><span data-stu-id="86a91-2812">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2813">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2813">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="86a91-2814">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2814">Description</span></span>

<span data-ttu-id="86a91-2815">Este servicio abre un medio para el acceso a archivos mediante el controlador de E/S proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2815">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-2816">*La memoria suministrada a este servicio se usa para implementar una caché de sectores lógicos interna; por lo tanto, cuanto más memoria se suministra más se reduce la E/S física. FileX requiere una memoria caché de al menos un sector lógico (bytes por sector del medio).*</span><span class="sxs-lookup"><span data-stu-id="86a91-2816">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2817">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2817">Input Parameters</span></span>

- <span data-ttu-id="86a91-2818">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2818">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-2819">**media_name**: puntero al nombre del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2819">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="86a91-2820">**media_driver**: puntero al controlador de E/S para este medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2820">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="86a91-2821">El controlador de E/S debe cumplir los requisitos del controlador FileX definidos en el capítulo 5.</span><span class="sxs-lookup"><span data-stu-id="86a91-2821">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="86a91-2822">**driver_info_ptr**: puntero a información opcional que el controlador de E/S proporcionado puede utilizar.</span><span class="sxs-lookup"><span data-stu-id="86a91-2822">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="86a91-2823">**memory_ptr**: puntero a la memoria de trabajo del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2823">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="86a91-2824">**memory_size** Especifica el tamaño de la memoria de medios de trabajo.</span><span class="sxs-lookup"><span data-stu-id="86a91-2824">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="86a91-2825">El tamaño debe ser tan grande como el tamaño de sector del medio (normalmente 512 bytes).</span><span class="sxs-lookup"><span data-stu-id="86a91-2825">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2826">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2826">Return Values</span></span>

- <span data-ttu-id="86a91-2827">**FX_SUCCESS** (0x00) Apertura correcta del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2827">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="86a91-2828">**FX_BOOT_ERROR** (0x01) Error al leer el sector de arranque del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2828">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="86a91-2829">**FX_MEDIA_INVALID** (0x02) El sector de arranque del medio especificado está dañado o no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2829">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="86a91-2830">Además, este código de retorno se usa para indicar que el tamaño de la caché del sector lógico o el tamaño de la entrada de FAT no es una potencia de 2.</span><span class="sxs-lookup"><span data-stu-id="86a91-2830">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="86a91-2831">**FX_FAT_READ_ERROR** (0x03) Error al leer la FAT del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2831">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="86a91-2832">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2832">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2833">**FX_PTR_ERROR** (0x18) Uno o más punteros son NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-2833">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="86a91-2834">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2834">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2835">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2835">Allowed From</span></span>

<span data-ttu-id="86a91-2836">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2836">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2837">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2837">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2838">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2838">See Also</span></span>

- <span data-ttu-id="86a91-2839">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2839">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2840">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2840">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2841">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2841">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2842">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2842">fx_media_check</span></span>
- <span data-ttu-id="86a91-2843">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2843">fx_media_close</span></span>
- <span data-ttu-id="86a91-2844">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2844">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2845">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2845">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2846">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2846">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2847">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2847">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2848">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2848">fx_media_format</span></span>
- <span data-ttu-id="86a91-2849">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2849">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2850">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2850">fx_media_read</span></span>
- <span data-ttu-id="86a91-2851">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2851">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2852">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2852">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2853">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2853">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2854">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2854">fx_media_write</span></span>
- <span data-ttu-id="86a91-2855">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2855">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="86a91-2856">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2856">fx_media_open_notify_set</span></span>

<span data-ttu-id="86a91-2857">Establece la función de notificación de apertura del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2857">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2858">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2858">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="86a91-2859">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2859">Description</span></span>

<span data-ttu-id="86a91-2860">Este servicio establece una función de devolución de llamada de notificación que se invocará después de que un medio se abra correctamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2860">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2861">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2861">Input Parameters</span></span>

- <span data-ttu-id="86a91-2862">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2862">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-2863">**media_open_notify**: Función de devolución de llamada de notificación de apertura de medio que se va a instalar.</span><span class="sxs-lookup"><span data-stu-id="86a91-2863">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="86a91-2864">Pasar NULL como la función de devolución de llamada deshabilita la devolución de llamada de apertura del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2864">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2865">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2865">Return Values</span></span>


- <span data-ttu-id="86a91-2866">**FX_SUCCESS** (0x00) La función de devolución de llamada se ha instalado correctamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2866">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="86a91-2867">**FX_PTR_ERROR** (0x18) media_ptr es NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-2867">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="86a91-2868">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2868">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2869">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2869">Allowed From</span></span>

<span data-ttu-id="86a91-2870">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2871">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2871">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="86a91-2872">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2872">See Also</span></span>

- <span data-ttu-id="86a91-2873">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2873">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2874">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2874">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2875">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2875">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2876">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2876">fx_media_check</span></span>
- <span data-ttu-id="86a91-2877">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2877">fx_media_close</span></span>
- <span data-ttu-id="86a91-2878">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2878">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2879">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2879">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2880">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2880">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2881">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2881">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2882">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2882">fx_media_format</span></span>
- <span data-ttu-id="86a91-2883">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2883">fx_media_open</span></span>
- <span data-ttu-id="86a91-2884">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2884">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2885">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2885">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2886">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2886">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2887">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2887">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2888">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2888">fx_media_write</span></span>
- <span data-ttu-id="86a91-2889">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2889">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="86a91-2890">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2890">fx_media_read</span></span>

<span data-ttu-id="86a91-2891">Lee el sector lógico del medio</span><span class="sxs-lookup"><span data-stu-id="86a91-2891">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2892">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2892">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="86a91-2893">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2893">Description</span></span>

<span data-ttu-id="86a91-2894">Este servicio lee un sector lógico del medio y lo coloca en el búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2894">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2895">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2895">Input Parameters</span></span>

- <span data-ttu-id="86a91-2896">**media_ptr**: puntero a un medio abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2896">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="86a91-2897">**logical_sector**: sector lógico que se va a leer.</span><span class="sxs-lookup"><span data-stu-id="86a91-2897">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="86a91-2898">**buffer_ptr**: puntero al destino del sector lógico leído.</span><span class="sxs-lookup"><span data-stu-id="86a91-2898">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2899">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2899">Return Values</span></span>

- <span data-ttu-id="86a91-2900">**FX_SUCCESS** (0x00) Lectura correcta del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2900">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="86a91-2901">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2901">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-2902">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2902">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2903">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-2903">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-2904">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o búfer.</span><span class="sxs-lookup"><span data-stu-id="86a91-2904">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="86a91-2905">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2905">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2906">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2906">Allowed From</span></span>

<span data-ttu-id="86a91-2907">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2907">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2908">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2908">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-2909">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2909">See Also</span></span>

- <span data-ttu-id="86a91-2910">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2910">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2911">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2911">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2912">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2912">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2913">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2913">fx_media_check</span></span>
- <span data-ttu-id="86a91-2914">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2914">fx_media_close</span></span>
- <span data-ttu-id="86a91-2915">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2915">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2916">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2916">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2917">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2917">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2918">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2918">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2919">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2919">fx_media_format</span></span>
- <span data-ttu-id="86a91-2920">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2920">fx_media_open</span></span>
- <span data-ttu-id="86a91-2921">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2921">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2922">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2922">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-2923">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2923">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2924">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2924">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2925">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2925">fx_media_write</span></span>
- <span data-ttu-id="86a91-2926">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2926">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="86a91-2927">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2927">fx_media_space_available</span></span>

<span data-ttu-id="86a91-2928">Devuelve el espacio disponible en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2928">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2929">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2929">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="86a91-2930">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2930">Description</span></span>

<span data-ttu-id="86a91-2931">Este servicio devuelve el número de bytes disponibles en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2931">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="86a91-2932">Para trabajar con el medio mayor que 4 GB, la aplicación usará el servicio *fx_media_extended_space_available*.</span><span class="sxs-lookup"><span data-stu-id="86a91-2932">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2933">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2933">Input Parameters</span></span>

- <span data-ttu-id="86a91-2934">**media_ptr**: puntero a un medio abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2934">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="86a91-2935">**available_bytes_ptr**: bytes disponibles que quedan en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2935">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2936">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2936">Return Values</span></span>

- <span data-ttu-id="86a91-2937">**FX_SUCCESS** (0x00) Se devolvió correctamente el espacio disponible en el medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2937">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="86a91-2938">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2938">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-2939">**FX_PTR_ERROR** (0x18) Puntero de medio no válido o el puntero de bytes disponibles es NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-2939">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="86a91-2940">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2940">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2941">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2941">Allowed From</span></span>

<span data-ttu-id="86a91-2942">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2942">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2943">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2943">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2944">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2944">See Also</span></span>

- <span data-ttu-id="86a91-2945">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2945">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2946">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2946">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2947">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2947">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2948">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2948">fx_media_check</span></span>
- <span data-ttu-id="86a91-2949">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2949">fx_media_close</span></span>
- <span data-ttu-id="86a91-2950">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2950">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2951">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2951">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2952">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2952">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2953">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2953">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2954">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2954">fx_media_format</span></span>
- <span data-ttu-id="86a91-2955">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2955">fx_media_open</span></span>
- <span data-ttu-id="86a91-2956">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2956">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2957">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2957">fx_media_read</span></span>
- <span data-ttu-id="86a91-2958">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2958">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-2959">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2959">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-2960">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-2960">fx_media_write</span></span>
- <span data-ttu-id="86a91-2961">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-2961">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="86a91-2962">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-2962">fx_media_volume_get</span></span>

<span data-ttu-id="86a91-2963">Obtiene el nombre del volumen del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2963">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-2964">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-2964">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="86a91-2965">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-2965">Description</span></span>

<span data-ttu-id="86a91-2966">Este servicio recupera el nombre del volumen del medio abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-2966">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-2967">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-2967">Input Parameters</span></span>

- <span data-ttu-id="86a91-2968">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2968">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-2969">**volume_name**: puntero al destino del nombre del volumen.</span><span class="sxs-lookup"><span data-stu-id="86a91-2969">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="86a91-2970">Tenga en cuenta que el destino debe ser al menos lo suficientemente grande como para contener 12 caracteres.</span><span class="sxs-lookup"><span data-stu-id="86a91-2970">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="86a91-2971">**volume_source**: designa dónde recuperar el nombre, ya sea desde el sector de arranque o desde el directorio raíz.</span><span class="sxs-lookup"><span data-stu-id="86a91-2971">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="86a91-2972">Los valores válidos para este parámetro son:</span><span class="sxs-lookup"><span data-stu-id="86a91-2972">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="86a91-2973">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="86a91-2973">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="86a91-2974">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="86a91-2974">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-2975">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-2975">Return Values</span></span>

- <span data-ttu-id="86a91-2976">**FX_SUCCESS** (0x00) Obtención correcta del volumen del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2976">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="86a91-2977">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-2977">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-2978">**FX_NOT_FOUND** (0x04) Volumen no encontrado.</span><span class="sxs-lookup"><span data-stu-id="86a91-2978">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="86a91-2979">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-2979">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-2980">**FX_PTR_ERROR** (0x18) Puntero no válido de destino de volumen o medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-2980">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="86a91-2981">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-2981">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-2982">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-2982">Allowed From</span></span>

<span data-ttu-id="86a91-2983">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-2983">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-2984">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-2984">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="86a91-2985">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-2985">See Also</span></span>

- <span data-ttu-id="86a91-2986">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-2986">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-2987">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-2987">fx_media_abort</span></span>
- <span data-ttu-id="86a91-2988">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-2988">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-2989">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-2989">fx_media_check</span></span>
- <span data-ttu-id="86a91-2990">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-2990">fx_media_close</span></span>
- <span data-ttu-id="86a91-2991">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2991">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-2992">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2992">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-2993">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2993">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-2994">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-2994">fx_media_flush</span></span>
- <span data-ttu-id="86a91-2995">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-2995">fx_media_format</span></span>
- <span data-ttu-id="86a91-2996">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-2996">fx_media_open</span></span>
- <span data-ttu-id="86a91-2997">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-2997">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-2998">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-2998">fx_media_read</span></span>
- <span data-ttu-id="86a91-2999">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-2999">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-3000">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3000">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-3001">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3001">fx_media_write</span></span>
- <span data-ttu-id="86a91-3002">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-3002">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="86a91-3003">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="86a91-3003">fx_media_volume_get_extended</span></span>

<span data-ttu-id="86a91-3004">Obtiene el nombre del volumen de medio de los medios abiertos previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-3004">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3005">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3005">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="86a91-3006">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3006">Description</span></span>

<span data-ttu-id="86a91-3007">Este servicio recupera el nombre del volumen del medio abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-3007">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-3008">Este servicio es idéntico a \***fx_media_volume_get()** _ excepto en que el autor de la llamada pasa el tamaño del búfer _ \*volume_name\*\*.</span><span class="sxs-lookup"><span data-stu-id="86a91-3008">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3009">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3009">Input Parameters</span></span>


- <span data-ttu-id="86a91-3010">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3010">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-3011">**volume_name**: puntero al destino del nombre del volumen.</span><span class="sxs-lookup"><span data-stu-id="86a91-3011">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="86a91-3012">Tenga en cuenta que el destino debe ser al menos lo suficientemente grande como para contener 12 caracteres.</span><span class="sxs-lookup"><span data-stu-id="86a91-3012">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="86a91-3013">**volume_name_buffer_length**: tamaño del búfer volume_name.</span><span class="sxs-lookup"><span data-stu-id="86a91-3013">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="86a91-3014">**volume_source**: designa dónde recuperar el nombre, ya sea desde el sector de arranque o desde el directorio raíz.</span><span class="sxs-lookup"><span data-stu-id="86a91-3014">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="86a91-3015">Los valores válidos para este parámetro son:</span><span class="sxs-lookup"><span data-stu-id="86a91-3015">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="86a91-3016">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="86a91-3016">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="86a91-3017">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="86a91-3017">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3018">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3018">Return Values</span></span>

- <span data-ttu-id="86a91-3019">**FX_SUCCESS** (0x00) Obtención correcta del volumen del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3019">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="86a91-3020">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3020">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3021">**FX_NOT_FOUND** (0x04) Volumen no encontrado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3021">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="86a91-3022">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3022">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-3023">**FX_PTR_ERROR** (0x18) Puntero no válido de destino de volumen o medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3023">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="86a91-3024">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3024">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3025">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3025">Allowed From</span></span>

<span data-ttu-id="86a91-3026">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3026">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3027">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3027">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3028">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3028">See Also</span></span>

- <span data-ttu-id="86a91-3029">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-3029">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-3030">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-3030">fx_media_abort</span></span>
- <span data-ttu-id="86a91-3031">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-3031">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-3032">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-3032">fx_media_check</span></span>
- <span data-ttu-id="86a91-3033">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3033">fx_media_close</span></span>
- <span data-ttu-id="86a91-3034">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3034">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-3035">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-3035">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-3036">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-3036">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-3037">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-3037">fx_media_flush</span></span>
- <span data-ttu-id="86a91-3038">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-3038">fx_media_format</span></span>
- <span data-ttu-id="86a91-3039">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3039">fx_media_open</span></span>
- <span data-ttu-id="86a91-3040">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3040">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-3041">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3041">fx_media_read</span></span>
- <span data-ttu-id="86a91-3042">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-3042">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-3043">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3043">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-3044">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3044">fx_media_write</span></span>
- <span data-ttu-id="86a91-3045">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-3045">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="86a91-3046">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3046">fx_media_volume_set</span></span>

<span data-ttu-id="86a91-3047">Establece el nombre del volumen del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3047">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3048">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3048">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="86a91-3049">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3049">Description</span></span>

<span data-ttu-id="86a91-3050">Este servicio establece el nombre del volumen del medio abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-3050">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3051">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3051">Input Parameters</span></span>

- <span data-ttu-id="86a91-3052">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3052">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-3053">**volume_name**: puntero al nombre del volumen.</span><span class="sxs-lookup"><span data-stu-id="86a91-3053">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3054">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3054">Return Values</span></span>

- <span data-ttu-id="86a91-3055">**FX_SUCCESS** (0x00) Establecimiento correcto del volumen del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3055">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="86a91-3056">**FX_INVALID_NAME** (0x0C) Volume_name no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3056">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="86a91-3057">**FX_MEDIA_INVALID** (0x02) No se puede establecer el nombre del volumen.</span><span class="sxs-lookup"><span data-stu-id="86a91-3057">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="86a91-3058">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3058">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3059">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3059">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-3060">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-3060">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-3061">**FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre de volumen.</span><span class="sxs-lookup"><span data-stu-id="86a91-3061">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="86a91-3062">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3062">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3063">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3063">Allowed From</span></span>

<span data-ttu-id="86a91-3064">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3064">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3065">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3065">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3066">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3066">See Also</span></span>

- <span data-ttu-id="86a91-3067">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-3067">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-3068">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-3068">fx_media_abort</span></span>
- <span data-ttu-id="86a91-3069">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-3069">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-3070">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-3070">fx_media_check</span></span>
- <span data-ttu-id="86a91-3071">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3071">fx_media_close</span></span>
- <span data-ttu-id="86a91-3072">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3072">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-3073">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-3073">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-3074">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-3074">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-3075">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-3075">fx_media_flush</span></span>
- <span data-ttu-id="86a91-3076">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-3076">fx_media_format</span></span>
- <span data-ttu-id="86a91-3077">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3077">fx_media_open</span></span>
- <span data-ttu-id="86a91-3078">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3078">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-3079">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3079">fx_media_read</span></span>
- <span data-ttu-id="86a91-3080">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-3080">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-3081">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3081">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-3082">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3082">fx_media_write</span></span>
- <span data-ttu-id="86a91-3083">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-3083">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="86a91-3084">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3084">fx_media_write</span></span>

<span data-ttu-id="86a91-3085">Escribe el sector lógico.</span><span class="sxs-lookup"><span data-stu-id="86a91-3085">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3086">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3086">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="86a91-3087">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3087">Description</span></span>

<span data-ttu-id="86a91-3088">Este servicio escribe el búfer proporcionado en el sector lógico especificado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3088">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3089">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3089">Input Parameters</span></span>

- <span data-ttu-id="86a91-3090">**media_ptr**: puntero a un medio abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="86a91-3090">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="86a91-3091">**logical_sector**: sector lógico que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="86a91-3091">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="86a91-3092">**buffer_ptr**: puntero al origen de la escritura de sector lógico.</span><span class="sxs-lookup"><span data-stu-id="86a91-3092">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3093">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3093">Return Values</span></span>

- <span data-ttu-id="86a91-3094">**FX_SUCCESS** (0x00) Escritura correcta del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3094">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="86a91-3095">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3095">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3096">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3096">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-3097">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3097">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-3098">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-3098">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-3099">**FX_PTR_ERROR** (0x18) Puntero no válido de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3099">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="86a91-3100">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3100">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3101">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3101">Allowed From</span></span>

<span data-ttu-id="86a91-3102">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3102">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3103">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3103">Example</span></span>

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3104">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3104">See Also</span></span>

- <span data-ttu-id="86a91-3105">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="86a91-3105">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="86a91-3106">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="86a91-3106">fx_media_abort</span></span>
- <span data-ttu-id="86a91-3107">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="86a91-3107">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="86a91-3108">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="86a91-3108">fx_media_check</span></span>
- <span data-ttu-id="86a91-3109">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3109">fx_media_close</span></span>
- <span data-ttu-id="86a91-3110">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3110">fx_media_close_notify_set</span></span>
- <span data-ttu-id="86a91-3111">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="86a91-3111">fx_media_exFAT_format</span></span>
- <span data-ttu-id="86a91-3112">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-3112">fx_media_extended_space_available</span></span>
- <span data-ttu-id="86a91-3113">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="86a91-3113">fx_media_flush</span></span>
- <span data-ttu-id="86a91-3114">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="86a91-3114">fx_media_format</span></span>
- <span data-ttu-id="86a91-3115">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3115">fx_media_open</span></span>
- <span data-ttu-id="86a91-3116">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3116">fx_media_open_notify_set</span></span>
- <span data-ttu-id="86a91-3117">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3117">fx_media_read</span></span>
- <span data-ttu-id="86a91-3118">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="86a91-3118">fx_media_space_available</span></span>
- <span data-ttu-id="86a91-3119">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3119">fx_media_volume_get</span></span>
- <span data-ttu-id="86a91-3120">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3120">fx_media_volume_set</span></span>
- <span data-ttu-id="86a91-3121">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-3121">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="86a91-3122">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3122">fx_system_date_get</span></span>

<span data-ttu-id="86a91-3123">Obtiene la fecha del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="86a91-3123">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3124">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3124">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="86a91-3125">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3125">Description</span></span>

<span data-ttu-id="86a91-3126">Este servicio devuelve la fecha actual del sistema.</span><span class="sxs-lookup"><span data-stu-id="86a91-3126">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3127">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3127">Input Parameters</span></span>

- <span data-ttu-id="86a91-3128">**year**: puntero al destino del año.</span><span class="sxs-lookup"><span data-stu-id="86a91-3128">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="86a91-3129">**month**: puntero al destino del mes.</span><span class="sxs-lookup"><span data-stu-id="86a91-3129">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="86a91-3130">**day**: puntero al destino del día.</span><span class="sxs-lookup"><span data-stu-id="86a91-3130">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3131">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3131">Return Values</span></span>

- <span data-ttu-id="86a91-3132">**FX_SUCCESS** (0x00) Recuperación correcta de la fecha.</span><span class="sxs-lookup"><span data-stu-id="86a91-3132">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="86a91-3133">**FX_PTR_ERROR** (0x18) Uno o varios de los parámetros de entrada son NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-3133">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3134">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3134">Allowed From</span></span>

<span data-ttu-id="86a91-3135">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3135">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3136">Example</span></span>

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3137">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3137">See Also</span></span>

- <span data-ttu-id="86a91-3138">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3138">fx_system_date_set</span></span>
- <span data-ttu-id="86a91-3139">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-3139">fx_system_initialize</span></span>
- <span data-ttu-id="86a91-3140">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3140">fx_system_time_get</span></span>
- <span data-ttu-id="86a91-3141">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3141">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="86a91-3142">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3142">fx_system_date_set</span></span>

<span data-ttu-id="86a91-3143">Establece la fecha del sistema.</span><span class="sxs-lookup"><span data-stu-id="86a91-3143">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3144">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3144">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="86a91-3145">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3145">Description</span></span>

<span data-ttu-id="86a91-3146">Este servicio establece la fecha del sistema según se especifique.</span><span class="sxs-lookup"><span data-stu-id="86a91-3146">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-3147">*Se debe llamar a este servicio poco después de **fx_system_initialize** para establecer la fecha inicial del sistema. De forma predeterminada, la fecha del sistema es la de la versión genérica más reciente de FileX.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3147">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3148">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3148">Input Parameters</span></span>

- <span data-ttu-id="86a91-3149">**year**: nuevo año.</span><span class="sxs-lookup"><span data-stu-id="86a91-3149">**year**: New year.</span></span> <span data-ttu-id="86a91-3150">El intervalo válido es desde el año 1980 hasta 2107.</span><span class="sxs-lookup"><span data-stu-id="86a91-3150">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="86a91-3151">**mes**: nuevo mes.</span><span class="sxs-lookup"><span data-stu-id="86a91-3151">**month**: New month.</span></span> <span data-ttu-id="86a91-3152">El intervalo válido es de 1 a 12.</span><span class="sxs-lookup"><span data-stu-id="86a91-3152">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="86a91-3153">**day**: nuevo día.</span><span class="sxs-lookup"><span data-stu-id="86a91-3153">**day**: New day.</span></span> <span data-ttu-id="86a91-3154">El intervalo válido es entre 1 y 31, en función de las condiciones de año bisiesto y mes.</span><span class="sxs-lookup"><span data-stu-id="86a91-3154">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3155">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3155">Return Values</span></span>

- <span data-ttu-id="86a91-3156">**FX_SUCCESS** (0x00) Establecimiento correcto de la fecha.</span><span class="sxs-lookup"><span data-stu-id="86a91-3156">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="86a91-3157">**FX_INVALID_YEAR** (0x12) Se ha especificado un año no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3157">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="86a91-3158">**FX_INVALID_MONTH** (0x13) Se ha especificado un mes no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3158">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="86a91-3159">**FX_INVALID_DAY** (0x14) Se ha especificado un día no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3159">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3160">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3160">Allowed From</span></span>

<span data-ttu-id="86a91-3161">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3161">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3162">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3162">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3163">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3163">See Also</span></span>

- <span data-ttu-id="86a91-3164">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3164">fx_system_date_get</span></span>
- <span data-ttu-id="86a91-3165">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-3165">fx_system_initialize</span></span>
- <span data-ttu-id="86a91-3166">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3166">fx_system_time_get</span></span>
- <span data-ttu-id="86a91-3167">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3167">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="86a91-3168">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-3168">fx_system_initialize</span></span>

<span data-ttu-id="86a91-3169">Inicializa todo el sistema.</span><span class="sxs-lookup"><span data-stu-id="86a91-3169">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3170">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3170">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="86a91-3171">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3171">Description</span></span>

<span data-ttu-id="86a91-3172">Este servicio inicializa todas las estructuras de datos principales de FileX.</span><span class="sxs-lookup"><span data-stu-id="86a91-3172">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="86a91-3173">Se debe llamar en ***tx_application_define*** o tal vez desde un subproceso de inicialización y debe hacerse antes de usar cualquier otro servicio de FileX.</span><span class="sxs-lookup"><span data-stu-id="86a91-3173">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-3174">*Una vez inicializada mediante esta llamada, la aplicación debe llamar a ***fx_system_date_set** _ y _ *fx_system_time_set** para iniciar con una fecha y hora del sistema precisas.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3174">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3175">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3175">Input Parameters</span></span>

<span data-ttu-id="86a91-3176">Ninguno</span><span class="sxs-lookup"><span data-stu-id="86a91-3176">None</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3177">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3177">Return Values</span></span>

<span data-ttu-id="86a91-3178">Ninguno.</span><span class="sxs-lookup"><span data-stu-id="86a91-3178">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3179">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3179">Allowed From</span></span>

<span data-ttu-id="86a91-3180">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3180">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3181">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3181">Example</span></span>

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a><span data-ttu-id="86a91-3182">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3182">See Also</span></span>

- <span data-ttu-id="86a91-3183">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3183">fx_system_date_get</span></span>
- <span data-ttu-id="86a91-3184">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3184">fx_system_date_set</span></span>
- <span data-ttu-id="86a91-3185">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3185">fx_system_time_get</span></span>
- <span data-ttu-id="86a91-3186">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3186">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="86a91-3187">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3187">fx_system_time_get</span></span>

<span data-ttu-id="86a91-3188">Obtiene la hora actual del sistema.</span><span class="sxs-lookup"><span data-stu-id="86a91-3188">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3189">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3189">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="86a91-3190">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3190">Description</span></span>

<span data-ttu-id="86a91-3191">Este servicio recupera la hora actual del sistema.</span><span class="sxs-lookup"><span data-stu-id="86a91-3191">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3192">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3192">Input Parameters</span></span>

- <span data-ttu-id="86a91-3193">**hour**: puntero al destino de la hora.</span><span class="sxs-lookup"><span data-stu-id="86a91-3193">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="86a91-3194">**minute**: puntero al destino del minuto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3194">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="86a91-3195">**second**: puntero al destino del segundo.</span><span class="sxs-lookup"><span data-stu-id="86a91-3195">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3196">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3196">Return Values</span></span>

- <span data-ttu-id="86a91-3197">**FX_SUCCESS** (0x00) Recuperación correcta de la hora del sistema.</span><span class="sxs-lookup"><span data-stu-id="86a91-3197">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="86a91-3198">**FX_PTR_ERROR** (0x18) Uno o varios de los parámetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-3198">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3199">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3199">Allowed From</span></span>

<span data-ttu-id="86a91-3200">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3200">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3201">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3201">Example</span></span>

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3202">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3202">See Also</span></span>

- <span data-ttu-id="86a91-3203">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3203">fx_system_date_get</span></span>
- <span data-ttu-id="86a91-3204">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3204">fx_system_date_set</span></span>
- <span data-ttu-id="86a91-3205">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-3205">fx_system_initialize</span></span>
- <span data-ttu-id="86a91-3206">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3206">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="86a91-3207">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3207">fx_system_time_set</span></span>

<span data-ttu-id="86a91-3208">Establece la hora actual del sistema.</span><span class="sxs-lookup"><span data-stu-id="86a91-3208">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3209">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3209">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="86a91-3210">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3210">Description</span></span>

<span data-ttu-id="86a91-3211">Este servicio establece la hora actual del sistema en la especificada por los parámetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="86a91-3211">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-3212">*Se debe llamar a este servicio poco después de **fx_system_initialize** para establecer la hora inicial del sistema. De forma predeterminada, la hora del sistema es 0:0:0.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3212">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3213">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3213">Input Parameters</span></span>

- <span data-ttu-id="86a91-3214">**hour**: nueva hora (de 0 a 23).</span><span class="sxs-lookup"><span data-stu-id="86a91-3214">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="86a91-3215">**minute**: nuevo minuto (de 0 a 59).</span><span class="sxs-lookup"><span data-stu-id="86a91-3215">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="86a91-3216">**second**: nuevo segundo (de 0 a 59).</span><span class="sxs-lookup"><span data-stu-id="86a91-3216">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3217">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3217">Return Values</span></span>

- <span data-ttu-id="86a91-3218">**FX_SUCCESS** (0x00) Recuperación correcta de la hora del sistema.</span><span class="sxs-lookup"><span data-stu-id="86a91-3218">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="86a91-3219">**FX_INVALID_HOUR** (0x15) La nueva hora no es válida.</span><span class="sxs-lookup"><span data-stu-id="86a91-3219">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="86a91-3220">**FX_INVALID_MINUTE** (0x16) El nuevo minuto no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3220">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="86a91-3221">**FX_INVALID_SECOND** (0x17) El nuevo segundo no es válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3221">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3222">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3222">Allowed From</span></span>

<span data-ttu-id="86a91-3223">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3223">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3224">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3224">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3225">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3225">See Also</span></span>

- <span data-ttu-id="86a91-3226">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3226">fx_system_date_get</span></span>
- <span data-ttu-id="86a91-3227">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3227">fx_system_date_set</span></span>
- <span data-ttu-id="86a91-3228">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="86a91-3228">fx_system_initialize</span></span>
- <span data-ttu-id="86a91-3229">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3229">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="86a91-3230">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3230">fx_unicode_directory_create</span></span>

<span data-ttu-id="86a91-3231">Crea un directorio Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3231">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3232">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3232">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="86a91-3233">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3233">Description</span></span>

<span data-ttu-id="86a91-3234">Este servicio crea un subdirectorio con nombre Unicode en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre de origen Unicode).</span><span class="sxs-lookup"><span data-stu-id="86a91-3234">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="86a91-3235">Si es correcto, el servicio devuelve el nombre corto (formato 8.3) del subdirectorio Unicode recién creado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3235">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-3236">*Todas las operaciones en el subdirectorio Unicode (conversión en la ruta de acceso predeterminada, eliminación, etc.) deben realizarse proporcionando el nombre corto devuelto (formato 8.3) a los servicios de directorio de FileX estándar.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3236">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-3237">*Este servicio no es compatible con los medios exFAT.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3237">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3238">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3238">Input Parameters</span></span>

- <span data-ttu-id="86a91-3239">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3239">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-3240">**source_unicode_name**: puntero al nombre Unicode del nuevo subdirectorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3240">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="86a91-3241">**source_unicode_length**: longitud del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3241">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="86a91-3242">**short_name**: puntero al destino del nombre corto (formato 8.3) para el nuevo subdirectorio Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3242">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3243">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3243">Return Values</span></span>

- <span data-ttu-id="86a91-3244">**FX_SUCCESS** (0x00) Creación correcta de directorio Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3244">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="86a91-3245">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3245">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3246">**FX_ALREADY_CREATED** (0x0B) El directorio especificado ya existe.</span><span class="sxs-lookup"><span data-stu-id="86a91-3246">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="86a91-3247">**FX_NO_MORE_SPACE** (0x0A) no hay más clústeres disponibles en los medios para la entrada del nuevo directorio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3247">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="86a91-3248">**FX_NOT_IMPLEMENTED** (0x22) No se ha implementado el servicio para el sistema de archivos exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-3248">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="86a91-3249">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-3249">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-3250">**FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-3250">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="86a91-3251">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3251">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="86a91-3252">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3252">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3253">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3253">Allowed From</span></span>

<span data-ttu-id="86a91-3254">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3254">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3255">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3255">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3256">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3256">See Also</span></span>

- <span data-ttu-id="86a91-3257">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3257">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-3258">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3258">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-3259">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3259">fx_directory_create</span></span>
- <span data-ttu-id="86a91-3260">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3260">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-3261">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3261">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-3262">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-3262">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-3263">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-3263">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-3264">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-3264">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-3265">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3265">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-3266">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-3266">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-3267">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3267">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-3268">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-3268">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-3269">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3269">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-3270">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3270">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-3271">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-3271">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-3272">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-3272">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-3273">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-3273">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-3274">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3274">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-3275">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3275">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-3276">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3276">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="86a91-3277">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3277">fx_unicode_directory_rename</span></span>

<span data-ttu-id="86a91-3278">Cambia el nombre del directorio mediante la cadena Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3278">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3279">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3279">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="86a91-3280">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3280">Description</span></span>

<span data-ttu-id="86a91-3281">Este servicio cambia un subdirectorio con nombre Unicode al nuevo nombre Unicode especificado en el directorio de trabajo actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-3281">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="86a91-3282">Los parámetros de nombre Unicode no deben tener información de ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3282">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-3283">*Este servicio no es compatible con los medios exFAT.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3283">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3284">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3284">Input Parameters</span></span>

- <span data-ttu-id="86a91-3285">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3285">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-3286">**old_unicode_name**: puntero al nombre Unicode del archivo actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-3286">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="86a91-3287">**old_unicode_name_length**: longitud del nombre Unicode actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-3287">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="86a91-3288">**new_unicode_name**: puntero al nuevo nombre de archivo Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3288">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="86a91-3289">**old_unicode_name_length**: Longitud del nombre Unicode nuevo.</span><span class="sxs-lookup"><span data-stu-id="86a91-3289">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="86a91-3290">**new_short_name**: puntero al destino del nombre corto (formato 8.3) del archivo Unicode con el nombre cambiado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3290">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="86a91-3291">Cambie el nombre del directorio con Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3291">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3292">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3292">Return Values</span></span>

- <span data-ttu-id="86a91-3293">**FX_SUCCESS** (0x00) Apertura correcta del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3293">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="86a91-3294">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3294">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3295">**FX_ALREADY_CREATED** (0x0B) El nombre de directorio especificado ya existe.</span><span class="sxs-lookup"><span data-stu-id="86a91-3295">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="86a91-3296">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3296">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-3297">**FX_PTR_ERROR** (0x18) Uno o más punteros son NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-3297">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="86a91-3298">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3298">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="86a91-3299">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-3299">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3300">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3300">Allowed From</span></span>

<span data-ttu-id="86a91-3301">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3302">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3302">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3303">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3303">See Also</span></span>

- <span data-ttu-id="86a91-3304">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3304">fx_directory_attributes_read</span></span>
- <span data-ttu-id="86a91-3305">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3305">fx_directory_attributes_set</span></span>
- <span data-ttu-id="86a91-3306">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3306">fx_directory_create</span></span>
- <span data-ttu-id="86a91-3307">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3307">fx_directory_default_get</span></span>
- <span data-ttu-id="86a91-3308">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3308">fx_directory_default_set</span></span>
- <span data-ttu-id="86a91-3309">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-3309">fx_directory_delete</span></span>
- <span data-ttu-id="86a91-3310">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-3310">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="86a91-3311">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-3311">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="86a91-3312">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3312">fx_directory_information_get</span></span>
- <span data-ttu-id="86a91-3313">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="86a91-3313">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="86a91-3314">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3314">fx_directory_local_path_get</span></span>
- <span data-ttu-id="86a91-3315">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="86a91-3315">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="86a91-3316">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3316">fx_directory_local_path_set</span></span>
- <span data-ttu-id="86a91-3317">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3317">fx_directory_long_name_get</span></span>
- <span data-ttu-id="86a91-3318">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="86a91-3318">fx_directory_name_test</span></span>
- <span data-ttu-id="86a91-3319">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-3319">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="86a91-3320">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="86a91-3320">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="86a91-3321">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3321">fx_directory_rename</span></span>
- <span data-ttu-id="86a91-3322">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3322">fx_directory_short_name_get</span></span>
- <span data-ttu-id="86a91-3323">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3323">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="86a91-3324">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3324">fx_unicode_file_create</span></span>

<span data-ttu-id="86a91-3325">Crea un archivo Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3325">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3326">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3326">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="86a91-3327">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3327">Description</span></span>

<span data-ttu-id="86a91-3328">Este servicio crea un archivo con nombre Unicode en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre de origen Unicode).</span><span class="sxs-lookup"><span data-stu-id="86a91-3328">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="86a91-3329">Si es correcto, el servicio devuelve el nombre corto (formato 8.3) del archivo Unicode recién creado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3329">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="86a91-3330">*Todas las operaciones en el archivo Unicode (abrir, escribir, leer, cerrar, etc.) deben realizarse proporcionando el nombre corto devuelto (formato 8.3) a los servicios de archivo de FileX estándar.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3330">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3331">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3331">Input Parameters</span></span>


- <span data-ttu-id="86a91-3332">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3332">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-3333">**source_unicode_name**: puntero al nombre Unicode del nuevo archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-3333">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="86a91-3334">**source_unicode_length**: longitud del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3334">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="86a91-3335">**short_name**: puntero al destino del nombre corto (formato 8.3) para el nuevo archivo Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3335">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3336">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3336">Return Values</span></span>

- <span data-ttu-id="86a91-3337">**FX_SUCCESS** (0x00) Creación correcta de archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-3337">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="86a91-3338">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3338">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3339">**FX_ALREADY_CREATED** (0x0B) El archivo especificado ya existe.</span><span class="sxs-lookup"><span data-stu-id="86a91-3339">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="86a91-3340">**FX_NO_MORE_SPACE** (0x0A) No hay más clústeres disponibles en los medios para la entrada del nuevo archivo.</span><span class="sxs-lookup"><span data-stu-id="86a91-3340">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="86a91-3341">**FX_NOT_IMPLEMENTED** (0x22) No se ha implementado el servicio para el sistema de archivos exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-3341">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="86a91-3342">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3342">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-3343">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-3343">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="86a91-3344">**FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-3344">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="86a91-3345">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3345">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3346">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3346">Allowed From</span></span>

<span data-ttu-id="86a91-3347">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3347">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3348">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3348">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3349">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3349">See Also</span></span>

- <span data-ttu-id="86a91-3350">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3350">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-3351">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3351">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-3352">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3352">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-3353">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3353">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3354">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3354">fx_file_close</span></span>
- <span data-ttu-id="86a91-3355">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3355">fx_file_create</span></span>
- <span data-ttu-id="86a91-3356">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3356">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-3357">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-3357">fx_file_delete</span></span>
- <span data-ttu-id="86a91-3358">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3358">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-3359">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3359">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3360">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3360">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-3361">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3361">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-3362">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3362">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-3363">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3363">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-3364">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3364">fx_file_open</span></span>
- <span data-ttu-id="86a91-3365">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3365">fx_file_read</span></span>
- <span data-ttu-id="86a91-3366">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3366">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-3367">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3367">fx_file_rename</span></span>
- <span data-ttu-id="86a91-3368">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3368">fx_file_seek</span></span>
- <span data-ttu-id="86a91-3369">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3369">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-3370">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3370">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-3371">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3371">fx_file_write</span></span>
- <span data-ttu-id="86a91-3372">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3372">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-3373">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3373">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-3374">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3374">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-3375">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3375">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="86a91-3376">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3376">fx_unicode_file_rename</span></span>

<span data-ttu-id="86a91-3377">Cambia el nombre de un archivo mediante una cadena Unicode</span><span class="sxs-lookup"><span data-stu-id="86a91-3377">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3378">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3378">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="86a91-3379">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3379">Description</span></span>

<span data-ttu-id="86a91-3380">Este servicio cambia un nombre de archivo con nombre Unicode al nuevo nombre Unicode especificado en el directorio predeterminado actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-3380">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="86a91-3381">Los parámetros de nombre Unicode no deben tener información de ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3381">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-3382">*Este servicio no es compatible con los medios exFAT.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3382">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3383">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3383">Input Parameters</span></span>

- <span data-ttu-id="86a91-3384">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3384">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-3385">**old_unicode_name**: puntero al nombre Unicode del archivo actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-3385">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="86a91-3386">**old_unicode_name_length**: longitud del nombre Unicode actual.</span><span class="sxs-lookup"><span data-stu-id="86a91-3386">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="86a91-3387">**new_unicode_name**: puntero al nuevo nombre de archivo Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3387">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="86a91-3388">**new_unicode_name_length**: longitud del nombre Unicode nuevo.</span><span class="sxs-lookup"><span data-stu-id="86a91-3388">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="86a91-3389">**new_short_name**: puntero al destino del nombre corto (formato 8.3) del archivo Unicode con el nombre cambiado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3389">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3390">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3390">Return Values</span></span>


- <span data-ttu-id="86a91-3391">**FX_SUCCESS** (0x00) Apertura correcta del medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3391">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="86a91-3392">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3392">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3393">**FX_ALREADY_CREATED** (0x0B) El nombre de archivo especificado ya existe.</span><span class="sxs-lookup"><span data-stu-id="86a91-3393">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="86a91-3394">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3394">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-3395">**FX_PTR_ERROR** (0x18) Uno o más punteros son NULL.</span><span class="sxs-lookup"><span data-stu-id="86a91-3395">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="86a91-3396">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3396">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="86a91-3397">**FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.</span><span class="sxs-lookup"><span data-stu-id="86a91-3397">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3398">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3398">Allowed From</span></span>

<span data-ttu-id="86a91-3399">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3400">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3400">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3401">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3401">See Also</span></span>

- <span data-ttu-id="86a91-3402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3402">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-3403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3403">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-3404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3404">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-3405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3406">fx_file_close</span></span>
- <span data-ttu-id="86a91-3407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3407">fx_file_create</span></span>
- <span data-ttu-id="86a91-3408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3408">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-3409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-3409">fx_file_delete</span></span>
- <span data-ttu-id="86a91-3410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-3411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-3413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3413">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-3414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-3415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-3416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3416">fx_file_open</span></span>
- <span data-ttu-id="86a91-3417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3417">fx_file_read</span></span>
- <span data-ttu-id="86a91-3418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3418">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-3419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3419">fx_file_rename</span></span>
- <span data-ttu-id="86a91-3420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3420">fx_file_seek</span></span>
- <span data-ttu-id="86a91-3421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3421">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-3422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3422">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-3423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3423">fx_file_write</span></span>
- <span data-ttu-id="86a91-3424">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3424">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-3425">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3425">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-3426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3426">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-3427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3427">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="86a91-3428">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3428">fx_unicode_length_get</span></span>

<span data-ttu-id="86a91-3429">Obtiene la longitud del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3429">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3430">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3430">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="86a91-3431">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3431">Description</span></span>

<span data-ttu-id="86a91-3432">Este servicio determina la longitud del nombre Unicode proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3432">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="86a91-3433">Un carácter Unicode se representa mediante dos bytes.</span><span class="sxs-lookup"><span data-stu-id="86a91-3433">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="86a91-3434">Un nombre Unicode es una serie de caracteres Unicode de dos bytes terminada en dos bytes NULL (dos bytes de valor 0).</span><span class="sxs-lookup"><span data-stu-id="86a91-3434">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3435">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3435">Input Parameters</span></span>

<span data-ttu-id="86a91-3436">**unicode_name**: puntero al nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3436">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3437">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3437">Return Values</span></span>

<span data-ttu-id="86a91-3438">**length**: longitud del nombre Unicode (número de caracteres Unicode en el nombre).</span><span class="sxs-lookup"><span data-stu-id="86a91-3438">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3439">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3439">Allowed From</span></span>

<span data-ttu-id="86a91-3440">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3440">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3441">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3441">Example</span></span>

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3442">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3442">See Also</span></span>

- <span data-ttu-id="86a91-3443">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3443">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-3444">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3444">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-3445">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3445">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-3446">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3446">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3447">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3447">fx_file_close</span></span>
- <span data-ttu-id="86a91-3448">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3448">fx_file_create</span></span>
- <span data-ttu-id="86a91-3449">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3449">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-3450">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-3450">fx_file_delete</span></span>
- <span data-ttu-id="86a91-3451">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3451">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-3452">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3452">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3453">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3453">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-3454">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3454">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-3455">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3455">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-3456">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3456">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-3457">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3457">fx_file_open</span></span>
- <span data-ttu-id="86a91-3458">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3458">fx_file_read</span></span>
- <span data-ttu-id="86a91-3459">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3459">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-3460">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3460">fx_file_rename</span></span>
- <span data-ttu-id="86a91-3461">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3461">fx_file_seek</span></span>
- <span data-ttu-id="86a91-3462">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3462">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-3463">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3463">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-3464">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3464">fx_file_write</span></span>
- <span data-ttu-id="86a91-3465">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3465">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-3466">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3466">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-3467">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3467">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-3468">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3468">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-3469">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3469">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="86a91-3470">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="86a91-3470">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="86a91-3471">Obtiene la longitud del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3471">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3472">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3472">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="86a91-3473">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3473">Description</span></span>

<span data-ttu-id="86a91-3474">Este servicio obtiene la longitud del nombre Unicode proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3474">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="86a91-3475">Un carácter Unicode se representa mediante dos bytes.</span><span class="sxs-lookup"><span data-stu-id="86a91-3475">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="86a91-3476">Un nombre Unicode es una serie de caracteres Unicode de dos bytes terminada en dos bytes NULL (dos bytes de valor 0).</span><span class="sxs-lookup"><span data-stu-id="86a91-3476">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-3477">*Este servicio es idéntico a **fx_unicode_length_get ()** , excepto en que el autor de la llamada pasa el tamaño del búfer de **unicode_name**, incluidos los dos caracteres NULL.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3477">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3478">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3478">Input Parameters</span></span>

- <span data-ttu-id="86a91-3479">**unicode_name**: puntero al nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3479">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="86a91-3480">**buffer_length**: tamaño del búfer de nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3480">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3481">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3481">Return Values</span></span>

<span data-ttu-id="86a91-3482">**length**: longitud del nombre Unicode (número de caracteres Unicode en el nombre).</span><span class="sxs-lookup"><span data-stu-id="86a91-3482">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3483">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3483">Allowed From</span></span>

<span data-ttu-id="86a91-3484">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3484">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3485">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3485">Example</span></span>

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3486">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3486">See Also</span></span>

- <span data-ttu-id="86a91-3487">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3487">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-3488">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3488">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-3489">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3489">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-3490">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3490">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3491">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3491">fx_file_close</span></span>
- <span data-ttu-id="86a91-3492">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3492">fx_file_create</span></span>
- <span data-ttu-id="86a91-3493">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3493">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-3494">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-3494">fx_file_delete</span></span>
- <span data-ttu-id="86a91-3495">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3495">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-3496">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3496">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3497">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3497">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-3498">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3498">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-3499">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3499">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-3500">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3500">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-3501">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3501">fx_file_open</span></span>
- <span data-ttu-id="86a91-3502">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3502">fx_file_read</span></span>
- <span data-ttu-id="86a91-3503">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3503">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-3504">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3504">fx_file_rename</span></span>
- <span data-ttu-id="86a91-3505">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3505">fx_file_seek</span></span>
- <span data-ttu-id="86a91-3506">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3506">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-3507">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3507">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-3508">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3508">fx_file_write</span></span>
- <span data-ttu-id="86a91-3509">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3509">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-3510">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3510">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-3511">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3511">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-3512">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3512">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-3513">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3513">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="86a91-3514">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3514">fx_unicode_name_get</span></span>

<span data-ttu-id="86a91-3515">Obtiene el nombre Unicode del nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3515">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3516">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3516">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="86a91-3517">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3517">Description</span></span>

<span data-ttu-id="86a91-3518">Este servicio recupera el nombre Unicode asociado al nombre corto proporcionado (formato 8.3) en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre corto).</span><span class="sxs-lookup"><span data-stu-id="86a91-3518">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="86a91-3519">Si es correcto, el servicio devuelve el nombre Unicode asociado al nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3519">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-3520">*Este servicio se puede usar para obtener nombres Unicode para archivos y subdirectorios.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3520">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3521">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3521">Input Parameters</span></span>

- <span data-ttu-id="86a91-3522">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3522">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-3523">**short_name**: puntero al nombre corto (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="86a91-3523">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="86a91-3524">**destination_unicode_name**: puntero al destino para el nombre Unicode asociado al nombre corto proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3524">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="86a91-3525">**destination_unicode_length**: puntero a la longitud del nombre Unicode devuelto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3525">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3526">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3526">Return Values</span></span>

- <span data-ttu-id="86a91-3527">**FX_SUCCESS** (0x00) Recuperación correcta del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3527">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="86a91-3528">**FX_FAT_READ_ERROR** (0x03) No se puede leer la tabla FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-3528">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="86a91-3529">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3529">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-3530">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-3531">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3531">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3532">**FX_NOT_FOUND** (0x04) No se encontró el nombre corto o el tamaño de destino Unicode es demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="86a91-3532">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="86a91-3533">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3533">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-3534">**FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-3534">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="86a91-3535">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3535">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3536">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3536">Allowed From</span></span>

<span data-ttu-id="86a91-3537">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3537">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3538">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3538">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3539">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3539">See Also</span></span>

- <span data-ttu-id="86a91-3540">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3540">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-3541">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3541">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-3542">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3542">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-3543">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3543">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3544">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3544">fx_file_close</span></span>
- <span data-ttu-id="86a91-3545">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3545">fx_file_create</span></span>
- <span data-ttu-id="86a91-3546">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3546">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-3547">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-3547">fx_file_delete</span></span>
- <span data-ttu-id="86a91-3548">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3548">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-3549">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3549">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3550">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3550">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-3551">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3551">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-3552">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3552">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-3553">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3553">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-3554">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3554">fx_file_open</span></span>
- <span data-ttu-id="86a91-3555">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3555">fx_file_read</span></span>
- <span data-ttu-id="86a91-3556">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3556">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-3557">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3557">fx_file_rename</span></span>
- <span data-ttu-id="86a91-3558">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3558">fx_file_seek</span></span>
- <span data-ttu-id="86a91-3559">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3559">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-3560">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3560">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-3561">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3561">fx_file_write</span></span>
- <span data-ttu-id="86a91-3562">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3562">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-3563">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3563">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-3564">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3564">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-3565">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3565">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="86a91-3566">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="86a91-3566">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="86a91-3567">Obtiene el nombre Unicode del nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3567">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3568">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3568">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="86a91-3569">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3569">Description</span></span>

<span data-ttu-id="86a91-3570">Este servicio recupera el nombre Unicode asociado al nombre corto proporcionado (formato 8.3) en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre corto).</span><span class="sxs-lookup"><span data-stu-id="86a91-3570">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="86a91-3571">Si es correcto, el servicio devuelve el nombre Unicode asociado al nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3571">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-3572">\*Este servicio es idéntico a \***fx_unicode_name_get** _, salvo que el autor de la llamada proporciona el tamaño del búfer Unicode de destino como argumento de entrada. Esto permite al servicio garantizar que no sobrescribirá el búfer Unicode de destino_.</span><span class="sxs-lookup"><span data-stu-id="86a91-3572">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-3573">*Este servicio se puede usar para obtener nombres Unicode para archivos y subdirectorios.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3573">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3574">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3574">Input Parameters</span></span>

- <span data-ttu-id="86a91-3575">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3575">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-3576">**short_name**: puntero al nombre corto (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="86a91-3576">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="86a91-3577">**destination_unicode_name**: puntero al destino para el nombre Unicode asociado al nombre corto proporcionado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3577">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="86a91-3578">**destination_unicode_length**: puntero a la longitud del nombre Unicode devuelto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3578">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="86a91-3579">**unicode_name_buffer_length**: tamaño del búfer de nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3579">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="86a91-3580">Nota: Se requiere un terminador NULL, que es un byte adicional.</span><span class="sxs-lookup"><span data-stu-id="86a91-3580">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3581">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3581">Return Values</span></span>

- <span data-ttu-id="86a91-3582">**FX_SUCCESS** (0x00) Recuperación correcta del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3582">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="86a91-3583">**FX_FAT_READ_ERROR** (0x03) No se puede leer la tabla FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-3583">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="86a91-3584">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3584">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-3585">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3585">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-3586">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3586">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3587">**FX_NOT_FOUND** (0x04) No se encontró el nombre corto o el tamaño de destino Unicode es demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="86a91-3587">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="86a91-3588">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3588">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-3589">**FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-3589">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="86a91-3590">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3590">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3591">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3591">Allowed From</span></span>

<span data-ttu-id="86a91-3592">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3592">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3593">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3593">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3594">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3594">See Also</span></span>

- <span data-ttu-id="86a91-3595">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3595">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-3596">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3596">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-3597">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3597">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-3598">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3598">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3599">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3599">fx_file_close</span></span>
- <span data-ttu-id="86a91-3600">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3600">fx_file_create</span></span>
- <span data-ttu-id="86a91-3601">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3601">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-3602">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-3602">fx_file_delete</span></span>
- <span data-ttu-id="86a91-3603">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3603">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-3604">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3604">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3605">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3605">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-3606">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3606">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-3607">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3607">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-3608">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3608">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-3609">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3609">fx_file_open</span></span>
- <span data-ttu-id="86a91-3610">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3610">fx_file_read</span></span>
- <span data-ttu-id="86a91-3611">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3611">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-3612">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3612">fx_file_rename</span></span>
- <span data-ttu-id="86a91-3613">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3613">fx_file_seek</span></span>
- <span data-ttu-id="86a91-3614">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3614">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-3615">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3615">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-3616">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3616">fx_file_write</span></span>
- <span data-ttu-id="86a91-3617">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3617">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-3618">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3618">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-3619">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3619">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-3620">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3620">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="86a91-3621">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3621">fx_unicode_short_name_get</span></span>

<span data-ttu-id="86a91-3622">Obtiene el nombre corto del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3622">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3623">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3623">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="86a91-3624">Este servicio recupera el nombre corto (formato 8.3) asociado al nombre Unicode en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre Unicode).</span><span class="sxs-lookup"><span data-stu-id="86a91-3624">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="86a91-3625">Si es correcto, el servicio devuelve el nombre corto asociado al nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3625">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-3626">*Este servicio se puede usar para obtener nombres cortos para archivos y subdirectorios.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3626">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3627">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3627">Input Parameters</span></span>

- <span data-ttu-id="86a91-3628">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3628">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-3629">**source_unicode_name**: puntero al nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3629">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="86a91-3630">**source_unicode_length**: longitud del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3630">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="86a91-3631">**destination_short_name**: puntero al destino del nombre corto (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="86a91-3631">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="86a91-3632">Debe tener un tamaño mínimo de 13 bytes.</span><span class="sxs-lookup"><span data-stu-id="86a91-3632">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3633">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3633">Return Values</span></span>

- <span data-ttu-id="86a91-3634">**FX_SUCCESS** (0x00) Recuperación correcta de nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3634">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="86a91-3635">**FX_FAT_READ_ERROR** (0x03) No se puede leer la tabla FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-3635">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="86a91-3636">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3636">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="86a91-3637">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3637">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-3638">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3638">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3639">**FX_NOT_FOUND** (0x04) No se ha encontrado el nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3639">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="86a91-3640">**FX_NOT_IMPLEMENTED** (0x22) No se ha implementado el servicio para el sistema de archivos exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-3640">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="86a91-3641">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3641">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-3642">**FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-3642">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="86a91-3643">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3643">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3644">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3644">Allowed From</span></span>

<span data-ttu-id="86a91-3645">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3645">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3646">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3646">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3647">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3647">See Also</span></span>

- <span data-ttu-id="86a91-3648">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3648">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-3649">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3649">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-3650">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3650">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-3651">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3651">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3652">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3652">fx_file_close</span></span>
- <span data-ttu-id="86a91-3653">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3653">fx_file_create</span></span>
- <span data-ttu-id="86a91-3654">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3654">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-3655">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-3655">fx_file_delete</span></span>
- <span data-ttu-id="86a91-3656">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3656">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-3657">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3657">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3658">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3658">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-3659">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3659">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-3660">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3660">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-3661">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3661">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-3662">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3662">fx_file_open</span></span>
- <span data-ttu-id="86a91-3663">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3663">fx_file_read</span></span>
- <span data-ttu-id="86a91-3664">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3664">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-3665">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3665">fx_file_rename</span></span>
- <span data-ttu-id="86a91-3666">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3666">fx_file_seek</span></span>
- <span data-ttu-id="86a91-3667">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3667">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-3668">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3668">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-3669">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3669">fx_file_write</span></span>
- <span data-ttu-id="86a91-3670">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3670">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-3671">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3671">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-3672">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3672">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-3673">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3673">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="86a91-3674">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="86a91-3674">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="86a91-3675">Obtiene el nombre corto del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3675">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="86a91-3676">Prototipo</span><span class="sxs-lookup"><span data-stu-id="86a91-3676">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="86a91-3677">Descripción</span><span class="sxs-lookup"><span data-stu-id="86a91-3677">Description</span></span>

<span data-ttu-id="86a91-3678">Este servicio recupera el nombre corto (formato 8.3) asociado al nombre Unicode en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre Unicode).</span><span class="sxs-lookup"><span data-stu-id="86a91-3678">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="86a91-3679">Si es correcto, el servicio devuelve el nombre corto asociado al nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3679">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86a91-3680">*Este servicio es idéntico a **fx_unicode_name_get()** , salvo que el autor de la llamada proporciona el tamaño del búfer de destino como argumento de entrada. Esto permite al servicio garantizar que el nombre corto no supera el búfer de destino.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3680">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="86a91-3681">*Este servicio se puede usar para obtener nombres cortos para archivos y subdirectorios.*</span><span class="sxs-lookup"><span data-stu-id="86a91-3681">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="86a91-3682">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="86a91-3682">Input Parameters</span></span>

- <span data-ttu-id="86a91-3683">**media_ptr**: puntero al bloque de control de medio.</span><span class="sxs-lookup"><span data-stu-id="86a91-3683">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="86a91-3684">**source_unicode_name**: puntero al nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3684">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="86a91-3685">**source_unicode_length**: longitud del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3685">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="86a91-3686">**destination_short_name**: puntero al destino del nombre corto (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="86a91-3686">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="86a91-3687">Debe tener un tamaño mínimo de 13 bytes.</span><span class="sxs-lookup"><span data-stu-id="86a91-3687">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="86a91-3688">**short_name_buffer_length**: tamaño del búfer de destino.</span><span class="sxs-lookup"><span data-stu-id="86a91-3688">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="86a91-3689">El tamaño del búfer debe ser de 14 bytes como mínimo.</span><span class="sxs-lookup"><span data-stu-id="86a91-3689">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="86a91-3690">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="86a91-3690">Return Values</span></span>

- <span data-ttu-id="86a91-3691">**FX_SUCCESS** (0x00) Recuperación correcta de nombre corto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3691">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="86a91-3692">**FX_FAT_READ_ERROR** (0x03) No se puede leer la tabla FAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-3692">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="86a91-3693">**FX_FILE_CORRUPT** (0x08) El archivo está dañado.</span><span class="sxs-lookup"><span data-stu-id="86a91-3693">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="86a91-3694">**FX_IO_ERROR** (0x90) Error de E/S del controlador.</span><span class="sxs-lookup"><span data-stu-id="86a91-3694">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="86a91-3695">**FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.</span><span class="sxs-lookup"><span data-stu-id="86a91-3695">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="86a91-3696">**FX_NOT_FOUND** (0x04) No se ha encontrado el nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="86a91-3696">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="86a91-3697">**FX_NOT_IMPLEMENTED** (0x22) No se ha implementado el servicio para el sistema de archivos exFAT.</span><span class="sxs-lookup"><span data-stu-id="86a91-3697">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="86a91-3698">**FX_SECTOR_INVALID** (0x89) Sector no válido.</span><span class="sxs-lookup"><span data-stu-id="86a91-3698">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="86a91-3699">**FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.</span><span class="sxs-lookup"><span data-stu-id="86a91-3699">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="86a91-3700">**FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.</span><span class="sxs-lookup"><span data-stu-id="86a91-3700">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="86a91-3701">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="86a91-3701">Allowed From</span></span>

<span data-ttu-id="86a91-3702">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="86a91-3702">Threads</span></span>

### <a name="example"></a><span data-ttu-id="86a91-3703">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="86a91-3703">Example</span></span>

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="86a91-3704">Consulte también</span><span class="sxs-lookup"><span data-stu-id="86a91-3704">See Also</span></span>

- <span data-ttu-id="86a91-3705">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3705">fx_file_allocate</span></span>
- <span data-ttu-id="86a91-3706">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3706">fx_file_attributes_read</span></span>
- <span data-ttu-id="86a91-3707">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3707">fx_file_attributes_set</span></span>
- <span data-ttu-id="86a91-3708">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3708">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3709">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="86a91-3709">fx_file_close</span></span>
- <span data-ttu-id="86a91-3710">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3710">fx_file_create</span></span>
- <span data-ttu-id="86a91-3711">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3711">fx_file_date_time_set</span></span>
- <span data-ttu-id="86a91-3712">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="86a91-3712">fx_file_delete</span></span>
- <span data-ttu-id="86a91-3713">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3713">fx_file_extended_allocate</span></span>
- <span data-ttu-id="86a91-3714">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="86a91-3714">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="86a91-3715">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3715">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="86a91-3716">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3716">fx_file_extended_seek</span></span>
- <span data-ttu-id="86a91-3717">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3717">fx_file_extended_truncate</span></span>
- <span data-ttu-id="86a91-3718">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3718">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="86a91-3719">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="86a91-3719">fx_file_open</span></span>
- <span data-ttu-id="86a91-3720">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="86a91-3720">fx_file_read</span></span>
- <span data-ttu-id="86a91-3721">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3721">fx_file_relative_seek</span></span>
- <span data-ttu-id="86a91-3722">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3722">fx_file_rename</span></span>
- <span data-ttu-id="86a91-3723">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="86a91-3723">fx_file_seek</span></span>
- <span data-ttu-id="86a91-3724">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="86a91-3724">fx_file_truncate</span></span>
- <span data-ttu-id="86a91-3725">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="86a91-3725">fx_file_truncate_release</span></span>
- <span data-ttu-id="86a91-3726">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="86a91-3726">fx_file_write</span></span>
- <span data-ttu-id="86a91-3727">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="86a91-3727">fx_file_write_notify_set</span></span>
- <span data-ttu-id="86a91-3728">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="86a91-3728">fx_unicode_file_create</span></span>
- <span data-ttu-id="86a91-3729">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="86a91-3729">fx_unicode_file_rename</span></span>
- <span data-ttu-id="86a91-3730">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3730">fx_unicode_name_get</span></span>
- <span data-ttu-id="86a91-3731">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="86a91-3731">fx_unicode_short_name_get</span></span>
