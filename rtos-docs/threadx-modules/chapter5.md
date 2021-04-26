---
title: 'Capítulo 5: API del administrador de módulos'
author: philmea
description: Este artículo es un resumen de las API del administrador de módulos disponibles para la parte residente de la aplicación.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ca0fee443c23fd1bdd34651f4a7b31cf71f886f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814377"
---
# <a name="chapter-5---module-manager-apis"></a><span data-ttu-id="ea1a3-103">Capítulo 5: API del administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-103">Chapter 5 - Module Manager APIs</span></span>

## <a name="summary-of-module-manager-apis"></a><span data-ttu-id="ea1a3-104">Resumen de las API del administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-104">Summary of Module Manager APIs</span></span>

<span data-ttu-id="ea1a3-105">Hay varias API adicionales disponibles para la parte residente de la aplicación, como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-105">There are several additional APIs available to the resident portion of the application, as follows.</span></span>

- <span data-ttu-id="ea1a3-106">\***txm_module_manager_external_memory_enable**: habilita acceso al módulo a un espacio de memoria compartido\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-106">***txm_module_manager_external_memory_enable** _ - _Enable module access to a shared memory space*</span></span>
- <span data-ttu-id="ea1a3-107">\***txm_module_manager_file_load**: carga el módulo desde el archivo a través de FileX\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-107">***txm_module_manager_file_load** _ - _Load module from file via FileX*</span></span>
- <span data-ttu-id="ea1a3-108">\***txm_module_manager_in_place_load**: carga los datos del módulo, se ejecuta en contexto\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-108">***txm_module_manager_in_place_load** _ - _Load module data, execute in place*</span></span>
- <span data-ttu-id="ea1a3-109">\***txm_module_manager_initialize**: inicializa el administrador de módulos\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-109">***txm_module_manager_initialize** _ - _Initialize the module manager*</span></span>
- <span data-ttu-id="ea1a3-110">\***txm_module_manager_mm_initialize**: inicializa el hardware de administración de memoria\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-110">***txm_module_manager_mm_initialize** _ - _Initialize the memory management hardware*</span></span>
- <span data-ttu-id="ea1a3-111">\***txm_module_manager_maximum_module_priority_set**: establece la prioridad de subprocesos máxima permitida en un módulo\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-111">***txm_module_manager_maximum_module_priority_set** _ - _Set the maximum thread priority allowed in a module*</span></span>
- <span data-ttu-id="ea1a3-112">\***txm_module_manager_memory_fault_notify**: registra una devolución de llamada de aplicación en un error de memoria\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-112">***txm_module_manager_memory_fault_notify** _ - _Register an application callback on memory fault*</span></span>
- <span data-ttu-id="ea1a3-113">\***txm_module_manager_memory_load**: carga el módulo de la memoria\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-113">***txm_module_manager_memory_load** _ - _Load the module from memory*</span></span>
- <span data-ttu-id="ea1a3-114">\***txm_module_manager_object_pool_create**: crea un grupo de objetos para los módulos\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-114">***txm_module_manager_object_pool_create** _ - _Create an object pool for modules*</span></span>
- <span data-ttu-id="ea1a3-115">\***txm_module_manager_properties_get**: obtiene las propiedades del módulo\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-115">***txm_module_manager_properties_get** _ - _Get module properties*</span></span>
- <span data-ttu-id="ea1a3-116">\***txm_module_manager_start**: inicia la ejecución del módulo especificado\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-116">***txm_module_manager_start** _ - _Start execution of the specified module*</span></span>
- <span data-ttu-id="ea1a3-117">\***txm_module_manager_stop**: detiene la ejecución del módulo especificado\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-117">***txm_module_manager_stop** _ - _Stop execution of the specified module*</span></span>
- <span data-ttu-id="ea1a3-118">\***txm_module_manager_unload**: descarga el módulo\*.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-118">***txm_module_manager_unload** _ - _Unload the module*</span></span>

---

## <a name="txm_module_manager_external_memory_enable"></a><span data-ttu-id="ea1a3-119">txm_module_manager_external_memory_enable</span><span class="sxs-lookup"><span data-stu-id="ea1a3-119">txm_module_manager_external_memory_enable</span></span>

<span data-ttu-id="ea1a3-120">Habilitar el módulo para tener acceso a un espacio de memoria compartido</span><span class="sxs-lookup"><span data-stu-id="ea1a3-120">Enable module to access a shared memory space.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-121">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-121">Prototype</span></span>

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a><span data-ttu-id="ea1a3-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-122">Description</span></span>

<span data-ttu-id="ea1a3-123">Este servicio crea una entrada en la tabla de hardware de administración de memoria para una región de memoria compartida a la que el módulo puede tener acceso.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-123">This service creates an entry in the memory management hardware table for a shared memory region that the module can access.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-124">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-124">Input parameters</span></span>

- <span data-ttu-id="ea1a3-125">**module_instance** Puntero a la instancia del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-125">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="ea1a3-126">**start_address** Dirección inicial de la región de memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-126">**start_address** Starting address of shared memory region.</span></span>
- <span data-ttu-id="ea1a3-127">**lenght** Longitud de la región de memoria compartida.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-127">**length** Length of shared memory region.</span></span>
- <span data-ttu-id="ea1a3-128">**attributes** Atributos de la región de memoria (caché, lectura, escritura, etc.).</span><span class="sxs-lookup"><span data-stu-id="ea1a3-128">**attributes** Attributes of memory region (cache, read, write, etc.).</span></span> <span data-ttu-id="ea1a3-129">Los atributos son específicos del puerto. Consulte el [apéndice](appendix.md) para ver el formato de los atributos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-129">Attributes are port-specific; see [appendix](appendix.md) for attributes format.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-130">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-130">Return values</span></span>

- <span data-ttu-id="ea1a3-131">**TX_SUCCESS** (0x00) Entrada de memoria creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-131">**TX_SUCCESS** (0x00) Memory entry created successfully.</span></span>
- <span data-ttu-id="ea1a3-132">**TX_NOT_AVAILABLE** (0x1D) No se ha inicializado el administrador o la característica no está disponible.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-132">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized or feature not available.</span></span>
- <span data-ttu-id="ea1a3-133">**TX_PTR_ERROR** (0x03) Instancia de módulo no válida.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-133">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="ea1a3-134">**TX_START_ERROR** (0x10) El módulo no está en estado cargado.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-134">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>
- <span data-ttu-id="ea1a3-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alineación de dirección inicial no válida.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid start address alignment.</span></span>
- <span data-ttu-id="ea1a3-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Propiedades incompatibles.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-137">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-137">Allowed from</span></span>

<span data-ttu-id="ea1a3-138">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-138">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-139">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-139">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a><span data-ttu-id="ea1a3-140">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-140">txm_module_manager_file_load</span></span>

<span data-ttu-id="ea1a3-141">Cargar el módulo desde el archivo a través de FileX.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-141">Load module from file via FileX.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-142">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-142">Prototype</span></span>

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a><span data-ttu-id="ea1a3-143">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-143">Description</span></span>

<span data-ttu-id="ea1a3-144">Este servicio carga la imagen binaria del módulo incluida en el archivo especificado en el área de memoria del módulo y la prepara para su ejecución.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-144">This service loads the binary image of the module contained in the specified file into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="ea1a3-145">Se supone que el medio proporcionado ya está abierto.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-145">It is assumed that the supplied media is already opened.</span></span>

> [!NOTE]
> <span data-ttu-id="ea1a3-146">El sistema FileX se emplea para cargar el archivo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-146">The FileX system is utilized to load the file.</span></span> <span data-ttu-id="ea1a3-147">Para habilitar el acceso de FileX, el módulo, la biblioteca de módulos, el administrador de módulos y la biblioteca de ThreadX (con los orígenes del administrador de módulos) deben compilarse con **FX_FILEX_PRESENT** definido en los proyectos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-147">In order to enable FileX access, the module, module library, Module Manager and the ThreadX library (with the Module Manager sources) must be built with **FX_FILEX_PRESENT** defined in the projects.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-148">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-148">Input parameters</span></span>

- <span data-ttu-id="ea1a3-149">**module_instance** Puntero a la instancia del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-149">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="ea1a3-150">**module_name** Nombre del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-150">**module_name** Name of the module.</span></span>
- <span data-ttu-id="ea1a3-151">**media_ptr** Puntero a un elemento multimedia de FileX ya abierto.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-151">**media_ptr** Pointer to already opened FileX media.</span></span>
- <span data-ttu-id="ea1a3-152">**file_name** Nombre del archivo binario del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-152">**file_name** Name of module's binary file.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-153">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-153">Return values</span></span>

- <span data-ttu-id="ea1a3-154">**TX_SUCCESS** (0x00) Carga correcta del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-154">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="ea1a3-155">**TX_CALLER_ERROR** (0x13) Autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-155">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="ea1a3-156">**TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-156">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="ea1a3-157">**TX_NO_MEMORY** (0x10) No hay suficiente memoria para cargar el módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-157">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="ea1a3-158">**TX_NOT_DONE** (0x20) No se pudo abrir el elemento multimedia: no se encontró el archivo o el archivo no es válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-158">**TX_NOT_DONE** (0x20) Media not open, file not found or file is invalid.</span></span>
- <span data-ttu-id="ea1a3-159">**TX_PTR_ERROR** (0x03) Instancia de módulo no válida.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-159">**TX_PTR_ERROR** (0x03) Invalid module pointer.</span></span>
- <span data-ttu-id="ea1a3-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alineación no válida.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="ea1a3-161">**TXM_MODULE_ALREADY_LOADED** (0xF1) Ya se cargó el módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-161">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="ea1a3-162">**TXM_MODULE_INVALID** (0xF2) | Preámbulo de módulo no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-162">**TXM_MODULE_INVALID** (0xF2) | Invalid module preamble.</span></span>
- <span data-ttu-id="ea1a3-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Propiedades incompatibles.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-164">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-164">Allowed from</span></span>

<span data-ttu-id="ea1a3-165">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-165">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-166">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-166">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="ea1a3-167">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea1a3-167">See also</span></span>

- <span data-ttu-id="ea1a3-168">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-168">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="ea1a3-169">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-169">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="ea1a3-170">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="ea1a3-170">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_in_place_load"></a><span data-ttu-id="ea1a3-171">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-171">txm_module_manager_in_place_load</span></span>

<span data-ttu-id="ea1a3-172">Cargar solo los datos del módulo, ejecutar el módulo en la ubicación existente.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-172">Load module data only, execute module in existing location.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-173">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-173">Prototype</span></span>

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="ea1a3-174">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-174">Description</span></span>

<span data-ttu-id="ea1a3-175">Este servicio carga el área de datos del módulo solo en el área de memoria del módulo y lo prepara para su ejecución.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-175">This service loads the module's data area only into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="ea1a3-176">La ejecución del código de módulo estará en contexto, es decir, desde el desplazamiento de dirección especificado por el preámbulo del módulo en la ubicación proporcionada.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-176">Module code execution will be in-place, that is, from the address offset specified by the module preamble at the supplied location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-177">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-177">Input parameters</span></span>

- <span data-ttu-id="ea1a3-178">**module_instance** Puntero a la instancia del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-178">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="ea1a3-179">**module_name** Nombre del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-179">**module_name** Name of the module.</span></span>
- <span data-ttu-id="ea1a3-180">**location** Puntero al área de código del módulo, preámbulo primero.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-180">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-181">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-181">Return values</span></span>

- <span data-ttu-id="ea1a3-182">**TX_SUCCESS** (0x00) Carga correcta del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-182">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="ea1a3-183">**TX_CALLER_ERROR** (0x13) Autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-183">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="ea1a3-184">**TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-184">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="ea1a3-185">**TX_NO_MEMORY** (0x10) No hay suficiente memoria para cargar el módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-185">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="ea1a3-186">**TX_PTR_ERROR** (0x03) Puntero, instancia de módulo o preámbulo de módulo no válidos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-186">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="ea1a3-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alineación no válida.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="ea1a3-188">**TXM_MODULE_ALREADY_LOADED** (0xF1) Ya se cargó el módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-188">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="ea1a3-189">**TXM_MODULE_INVALID** (0xF2) Preámbulo de módulo no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-189">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="ea1a3-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Propiedades incompatibles.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-191">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-191">Allowed from</span></span>

<span data-ttu-id="ea1a3-192">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-192">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-193">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-193">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="ea1a3-194">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea1a3-194">See also</span></span>

- <span data-ttu-id="ea1a3-195">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-195">txm_module_manager_file_load</span></span>
- <span data-ttu-id="ea1a3-196">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-196">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="ea1a3-197">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="ea1a3-197">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_initialize"></a><span data-ttu-id="ea1a3-198">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="ea1a3-198">txm_module_manager_initialize</span></span>

<span data-ttu-id="ea1a3-199">Inicializar el administrador de módulos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-199">Initialize the module manager.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-200">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-200">Prototype</span></span>

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a><span data-ttu-id="ea1a3-201">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-201">Description</span></span>

<span data-ttu-id="ea1a3-202">Este servicio inicializa los recursos internos del administrador de módulos, incluida el área de memoria que se usa para cargar los módulos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-202">This service initializes the Module Manager's internal resources, including the memory area used for loading modules.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-203">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-203">Input parameters</span></span>

- <span data-ttu-id="ea1a3-204">**module_memory_start** Puntero al inicio de la memoria del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-204">**module_memory_start** Pointer to the start of module memory.</span></span>
- <span data-ttu-id="ea1a3-205">**module_memory_size** Tamaño en bytes de la memoria del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-205">**module_memory_size** Size in bytes of the module memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-206">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-206">Return values</span></span>

- <span data-ttu-id="ea1a3-207">**NX_SUCCESS** (0x00) Inicialización correcta.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-207">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="ea1a3-208">**TX_CALLER_ERROR** (0x13) Autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-208">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-209">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-209">Allowed from</span></span>

<span data-ttu-id="ea1a3-210">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-210">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-211">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-211">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="ea1a3-212">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea1a3-212">See also</span></span>

- <span data-ttu-id="ea1a3-213">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="ea1a3-213">txm_module_manager_object_pool_create</span></span>

---

## <a name="txm_module_manager_initialize_mmu"></a><span data-ttu-id="ea1a3-214">txm_module_manager_initialize_mmu</span><span class="sxs-lookup"><span data-stu-id="ea1a3-214">txm_module_manager_initialize_mmu</span></span>

<span data-ttu-id="ea1a3-215">Inicializar el hardware de administración de memoria.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-215">Initialize the memory management hardware.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-216">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-216">Prototype</span></span>

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a><span data-ttu-id="ea1a3-217">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-217">Description</span></span>

<span data-ttu-id="ea1a3-218">Este servicio inicializa la MMU.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-218">This service initializes the MMU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-219">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-219">Input parameters</span></span>

<span data-ttu-id="ea1a3-220">ninguno</span><span class="sxs-lookup"><span data-stu-id="ea1a3-220">none</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-221">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-221">Return values</span></span>

- <span data-ttu-id="ea1a3-222">**NX_SUCCESS** (0x00) Inicialización correcta.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-222">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="ea1a3-223">**TX_CALLER_ERROR** (0x13) Autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-223">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-224">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-224">Allowed from</span></span>

<span data-ttu-id="ea1a3-225">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-225">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-226">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-226">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a><span data-ttu-id="ea1a3-227">txm_module_manager_maximum_module_priority_set</span><span class="sxs-lookup"><span data-stu-id="ea1a3-227">txm_module_manager_maximum_module_priority_set</span></span>

<span data-ttu-id="ea1a3-228">Establecer la prioridad de subproceso máxima permitida en un módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-228">Set the maximum thread priority allowed in a module.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-229">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-229">Prototype</span></span>

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a><span data-ttu-id="ea1a3-230">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-230">Description</span></span>

<span data-ttu-id="ea1a3-231">Este servicio establece la prioridad de subproceso máxima permitida en un módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-231">This service sets the maximum thread priority allowed in a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-232">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-232">Input parameters</span></span>

- <span data-ttu-id="ea1a3-233">**module_instance** Puntero a la instancia del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-233">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="ea1a3-234">**priority** Prioridad máxima del subproceso.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-234">**priority** Maximum thread priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-235">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-235">Return values</span></span>

- <span data-ttu-id="ea1a3-236">**NX_SUCCESS** (0x00) Inicialización correcta.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-236">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="ea1a3-237">**TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-237">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="ea1a3-238">**TX_PTR_ERROR** (0x03) Instancia de módulo no válida.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-238">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="ea1a3-239">**TX_START_ERROR** (0x10) El módulo no está en estado cargado.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-239">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-240">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-240">Allowed from</span></span>

<span data-ttu-id="ea1a3-241">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-241">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-242">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-242">Example</span></span>

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a><span data-ttu-id="ea1a3-243">txm_module_manager_memory_fault_notify</span><span class="sxs-lookup"><span data-stu-id="ea1a3-243">txm_module_manager_memory_fault_notify</span></span>

<span data-ttu-id="ea1a3-244">Registrar una devolución de llamada de la aplicación en un error de memoria.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-244">Register an application callback on memory fault.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-245">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-245">Prototype</span></span>

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a><span data-ttu-id="ea1a3-246">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-246">Description</span></span>

<span data-ttu-id="ea1a3-247">Este servicio registra la función de devolución de llamada de notificación de errores de memoria de la aplicación especificada con el administrador de módulos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-247">This service registers the specified application memory fault notification callback function with the Module Manager.</span></span> <span data-ttu-id="ea1a3-248">Si se produce un error de memoria, se llama a esta función con un puntero al subproceso infractor y la instancia de módulo correspondiente al subproceso infractor.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-248">If a memory fault occurs, this function is called with a pointer to the offending thread and the module instance corresponding to the offending thread.</span></span> <span data-ttu-id="ea1a3-249">El procesamiento del administrador de módulos finaliza automáticamente el subproceso infractor, pero deja los demás subprocesos del módulo sin tocar.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-249">The Module Manager processing automatically terminates the offending thread, but leaves any other threads in the module untouched.</span></span> <span data-ttu-id="ea1a3-250">Depende de la aplicación decidir qué hacer con el módulo asociado al error de memoria.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-250">It is up to the application to decide what to do with the module associated with the memory fault.</span></span>

<span data-ttu-id="ea1a3-251">Vea el struct interno **_txm_module_manager_memory_fault_info** para obtener información específica sobre el propio error de memoria.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-251">Please see the internal **_txm_module_manager_memory_fault_info** struct for specific information on the memory fault itself.</span></span>

> [!NOTE]
> <span data-ttu-id="ea1a3-252">La función de devolución de llamada de notificación de error de memoria se ejecuta directamente desde la excepción de error de memoria, de modo que solo se puede llamar a las API de ThreadX que se permiten desde las rutinas de servicio de interrupción.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-252">The memory fault notification callback function is executed directly from the memory fault exception, so only ThreadX APIs Allowed from interrupt service routines can be called.</span></span> <span data-ttu-id="ea1a3-253">Por lo tanto, para detener y descargar el módulo infractor, la devolución de llamada de notificación de aplicación debe enviar una señal a una tarea de aplicación para que el módulo se pueda detener y descargar.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-253">Thus, in order to stop and unload the offending module, the application notification callback must send a signal to an application task so that the module can be stopped and unloaded.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-254">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-254">Input parameters</span></span>

- <span data-ttu-id="ea1a3-255">**notify_function** Puntero de función a la devolución de llamada de notificación de errores de memoria de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-255">**notify_function** Function pointer to the application's memory fault notification callback.</span></span> <span data-ttu-id="ea1a3-256">Si se proporciona un valor NULL, se deshabilita la notificación de error de memoria.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-256">Supplying a NULL value disables the memory fault notification.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-257">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-257">Return values</span></span>

- <span data-ttu-id="ea1a3-258">**TX_SUCCESS** (0x00) Registro de la función de notificación correcto.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-258">**TX_SUCCESS** (0x00) Successful notification function registration.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-259">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-259">Allowed from</span></span>

<span data-ttu-id="ea1a3-260">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-260">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-261">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-261">Example</span></span>

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a><span data-ttu-id="ea1a3-262">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-262">txm_module_manager_memory_load</span></span>

<span data-ttu-id="ea1a3-263">Cargue el módulo desde la memoria.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-263">Load module from memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-264">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-264">Prototype</span></span>

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="ea1a3-265">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-265">Description</span></span>

<span data-ttu-id="ea1a3-266">Este servicio carga el código y el área de datos del módulo en el área de memoria del módulo configurada por ***txm_module_manager_initialize*** y lo prepara para su ejecución.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-266">This service loads the module's code and data area into the module memory area set up by ***txm_module_manager_initialize*** and prepares it for execution.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-267">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-267">Input parameters</span></span>

- <span data-ttu-id="ea1a3-268">**module_instance** Puntero a la instancia del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-268">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="ea1a3-269">**module_name** Nombre del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-269">**module_name** Name of the module.</span></span>
- <span data-ttu-id="ea1a3-270">**location** Puntero al área de código del módulo, preámbulo primero.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-270">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-271">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-271">Return values</span></span>

- <span data-ttu-id="ea1a3-272">**TX_SUCCESS** (0x00) Carga correcta del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-272">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="ea1a3-273">**TX_CALLER_ERROR** (0x13) Autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-273">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="ea1a3-274">**TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-274">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="ea1a3-275">**TX_NO_MEMORY** (0x10) No hay suficiente memoria para cargar el módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-275">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="ea1a3-276">**TX_PTR_ERROR** (0x03) Puntero, instancia de módulo o preámbulo de módulo no válidos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-276">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="ea1a3-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alineación no válida.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="ea1a3-278">**TXM_MODULE_ALREADY_LOADED** (0xF1) Ya se cargó el módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-278">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="ea1a3-279">**TXM_MODULE_INVALID** (0xF2) Preámbulo de módulo no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-279">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="ea1a3-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Propiedades incompatibles.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-281">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-281">Allowed from</span></span>

<span data-ttu-id="ea1a3-282">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-282">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-283">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-283">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a><span data-ttu-id="ea1a3-284">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea1a3-284">See also</span></span>

- <span data-ttu-id="ea1a3-285">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-285">txm_module_manager_file_load</span></span>
- <span data-ttu-id="ea1a3-286">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-286">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="ea1a3-287">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="ea1a3-287">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_object_pool_create"></a><span data-ttu-id="ea1a3-288">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="ea1a3-288">txm_module_manager_object_pool_create</span></span>

<span data-ttu-id="ea1a3-289">Cree un grupo de objetos para los módulos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-289">Create an object pool for modules.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-290">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-290">Prototype</span></span>

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a><span data-ttu-id="ea1a3-291">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-291">Description</span></span>

<span data-ttu-id="ea1a3-292">Este servicio crea un grupo de memoria de objetos del administrador de módulos al que los módulos pueden asignar objetos de ThreadX/NetX, manteniendo el objeto del sistema fuera del área de memoria del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-292">This service creates a Module Manager object memory pool that the modules can allocate ThreadX/NetX objects from, thereby keeping the system object out of the module's memory area.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-293">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-293">Input parameters</span></span>

- <span data-ttu-id="ea1a3-294">**pool_memory_start** Puntero al inicio de la memoria del objeto.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-294">**pool_memory_start** Pointer to the start of object memory.</span></span>
- <span data-ttu-id="ea1a3-295">**pool_memory_size** Tamaño en bytes del grupo de memoria de objetos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-295">**pool_memory_size** Size in bytes of the object memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-296">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-296">Return values</span></span>

- <span data-ttu-id="ea1a3-297">**NX_SUCCESS** (0x00) Inicialización correcta.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-297">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="ea1a3-298">**TX_CALLER_ERROR** (0x13) Autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-298">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-299">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-299">Allowed from</span></span>

<span data-ttu-id="ea1a3-300">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-300">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-301">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-301">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="ea1a3-302">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea1a3-302">See also</span></span>

- <span data-ttu-id="ea1a3-303">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="ea1a3-303">txm_module_manager_initialize</span></span>

---

## <a name="txm_module_manager_properties_get"></a><span data-ttu-id="ea1a3-304">txm_module_manager_properties_get</span><span class="sxs-lookup"><span data-stu-id="ea1a3-304">txm_module_manager_properties_get</span></span>

<span data-ttu-id="ea1a3-305">Obtenga las propiedades del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-305">Get module properties.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-306">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-306">Prototype</span></span>

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a><span data-ttu-id="ea1a3-307">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-307">Description</span></span>

<span data-ttu-id="ea1a3-308">Este servicio devuelve las propiedades (especificadas en el preámbulo) de un módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-308">This service returns the properties (specified in the preamble) of a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-309">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-309">Input parameters</span></span>

- <span data-ttu-id="ea1a3-310">**module_instance** Puntero a la instancia del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-310">**module_instance** Pointer to the module instance.</span></span>
- <span data-ttu-id="ea1a3-311">**module_properties_ptr** Puntero al destino de las propiedades del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-311">**module_properties_ptr** Pointer to destination for module's properties.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-312">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-312">Return values</span></span>

- <span data-ttu-id="ea1a3-313">**TX_SUCCESS** (0x00) Inicialización correcta.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-313">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="ea1a3-314">**TX_PTR_ERROR** (0x03) Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-314">**TX_PTR_ERROR** (0x03) Invalid pointer.</span></span>
- <span data-ttu-id="ea1a3-315">**TX_CALLER_ERROR** (0x13) Autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-315">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-316">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-316">Allowed from</span></span>

<span data-ttu-id="ea1a3-317">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-317">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-318">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-318">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a><span data-ttu-id="ea1a3-319">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="ea1a3-319">txm_module_manager_start</span></span>

<span data-ttu-id="ea1a3-320">Inicie la ejecución de un módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-320">Start execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-321">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-321">Prototype</span></span>

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="ea1a3-322">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-322">Description</span></span>

<span data-ttu-id="ea1a3-323">Este servicio inicia la ejecución del módulo especificado, ya cargado.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-323">This service starts execution of the specified, already loaded module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-324">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-324">Input parameters</span></span>

- <span data-ttu-id="ea1a3-325">**module_instance** Puntero a la instancia de módulo cargada previamente.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-325">**module_instance** Pointer to previously loaded module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-326">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-326">Return values</span></span>

- <span data-ttu-id="ea1a3-327">**TX_SUCCESS** (0x00) Inicio correcto del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-327">**TX_SUCCESS** (0x00) Successful module start.</span></span>
- <span data-ttu-id="ea1a3-328">**TX_CALLER_ERROR** (0x13) Autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-328">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="ea1a3-329">**TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-329">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="ea1a3-330">**TX_PTR_ERROR** (0x03) Puntero o instancia de módulo no válidos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-330">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="ea1a3-331">**TX_START_ERROR** (0x10) El módulo ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-331">**TX_START_ERROR** (0x10) Module already started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-332">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-332">Allowed from</span></span>

<span data-ttu-id="ea1a3-333">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-333">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-334">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-334">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="ea1a3-335">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea1a3-335">See also</span></span>

- <span data-ttu-id="ea1a3-336">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="ea1a3-336">txm_module_manager_stop</span></span>

---

## <a name="txm_module_manager_stop"></a><span data-ttu-id="ea1a3-337">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="ea1a3-337">txm_module_manager_stop</span></span>

<span data-ttu-id="ea1a3-338">Detenga la ejecución de un módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-338">Stop execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-339">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-339">Prototype</span></span>

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="ea1a3-340">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-340">Description</span></span>

<span data-ttu-id="ea1a3-341">Este servicio detiene un módulo que se cargó e inició previamente.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-341">This service stops a module that was previously loaded and started.</span></span> <span data-ttu-id="ea1a3-342">La detención de un módulo incluye la ejecución del subproceso de detención opcional del módulo, la finalización de todos los subprocesos y la eliminación de todos los recursos asociados al módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-342">Stopping a module includes executing the module's optional stop thread, terminating all threads, and deleting all resources associated with the module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-343">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-343">Input parameters</span></span>

- <span data-ttu-id="ea1a3-344">**module_instance** Puntero a la instancia del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-344">**module_instance** Pointer to module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-345">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-345">Return values</span></span>

- <span data-ttu-id="ea1a3-346">**TX_SUCCESS** (0x00) Detención correcta del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-346">**TX_SUCCESS** (0x00) Successful module stop.</span></span>
- <span data-ttu-id="ea1a3-347">**TX_CALLER_ERROR** (0x13) Autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-347">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="ea1a3-348">**TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-348">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="ea1a3-349">**TX_PTR_ERROR** (0x03) Puntero o instancia de módulo no válidos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-349">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="ea1a3-350">**TX_START_ERROR** (0x10) No se ha iniciado el módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-350">**TX_START_ERROR** (0x10) Module not started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-351">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-351">Allowed from</span></span>

<span data-ttu-id="ea1a3-352">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-352">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-353">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-353">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="ea1a3-354">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea1a3-354">See also</span></span>

- <span data-ttu-id="ea1a3-355">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="ea1a3-355">txm_module_manager_start</span></span>

---

## <a name="txm_module_manager_unload"></a><span data-ttu-id="ea1a3-356">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="ea1a3-356">txm_module_manager_unload</span></span>

<span data-ttu-id="ea1a3-357">Descargue el módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-357">Unload the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea1a3-358">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-358">Prototype</span></span>

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="ea1a3-359">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea1a3-359">Description</span></span>

<span data-ttu-id="ea1a3-360">Este servicio descarga el módulo previamente cargado y detenido, liberando todos los recursos de memoria del módulo asociados.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-360">This service unloads the previously loaded and stopped module, freeing all the associated module memory resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea1a3-361">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ea1a3-361">Input parameters</span></span>

- <span data-ttu-id="ea1a3-362">**module_instance** Puntero a la instancia del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-362">**module_instance** Pointer to the instance of the module.</span></span>

### <a name="return-values"></a><span data-ttu-id="ea1a3-363">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-363">Return values</span></span>

- <span data-ttu-id="ea1a3-364">**TX_SUCCESS** (0x00) Descarga correcta del módulo.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-364">**TX_SUCCESS** 0x00) Successful module unload.</span></span>
- <span data-ttu-id="ea1a3-365">**TX_CALLER_ERROR** (0x13) Autor de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-365">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="ea1a3-366">**TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-366">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="ea1a3-367">**TX_NOT_DONE** (0x20) No se ha detenido el módulo o no es válido.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-367">**TX_NOT_DONE** (0x20) Invalid module or module not stopped.</span></span>
- <span data-ttu-id="ea1a3-368">**TX_PTR_ERROR** (0x03) Puntero o instancia de módulo no válidos.</span><span class="sxs-lookup"><span data-stu-id="ea1a3-368">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea1a3-369">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ea1a3-369">Allowed from</span></span>

<span data-ttu-id="ea1a3-370">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="ea1a3-370">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="ea1a3-371">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea1a3-371">Example</span></span>

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="ea1a3-372">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea1a3-372">See also</span></span>

- <span data-ttu-id="ea1a3-373">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-373">txm_module_manager_file_load</span></span>
- <span data-ttu-id="ea1a3-374">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-374">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="ea1a3-375">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="ea1a3-375">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="ea1a3-376">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="ea1a3-376">txm_module_manager_stop</span></span>
