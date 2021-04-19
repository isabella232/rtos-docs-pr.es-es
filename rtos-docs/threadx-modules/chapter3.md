---
title: 'Capítulo 3: Requisitos del Administrador de módulos'
description: Este artículo es una descripción de los pasos necesarios para crear el Administrador de módulos de ThreadX.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8ea1a05096b5975de203648fddfb19c1a6105e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815117"
---
# <a name="chapter-3---module-manager-requirements"></a><span data-ttu-id="00d03-103">Capítulo 3: Requisitos del Administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="00d03-103">Chapter 3 - Module Manager requirements</span></span>

<span data-ttu-id="00d03-104">El Administrador de módulos de ThreadX reside en la parte residente de la aplicación junto con ThreadX RTOS.</span><span class="sxs-lookup"><span data-stu-id="00d03-104">The ThreadX Module Manager resides in the resident portion of the application along with the ThreadX RTOS.</span></span> <span data-ttu-id="00d03-105">Es responsable del inicio del módulo, así como el campo y el envío de todas las solicitudes de módulo para los servicios de API de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="00d03-105">It is responsible for starting the module as well as fielding and dispatching all module requests for ThreadX API services.</span></span>

> [!NOTE]
> <span data-ttu-id="00d03-106">Los archivos de origen del **Administrador** de módulos ThreadX (C y ensamblado) se deben agregar al proyecto de biblioteca ThreadX "**tx**".</span><span class="sxs-lookup"><span data-stu-id="00d03-106">The ThreadX Module **Manager** source files (C and assembly) should be added to the ThreadX library project "**tx**".</span></span>

<span data-ttu-id="00d03-107">Los pasos siguientes son necesarios para compilar el Administrador de módulos de ThreadX (cada paso se describe con más detalle a continuación).</span><span class="sxs-lookup"><span data-stu-id="00d03-107">The following steps are required for building the ThreadX Module Manager (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="00d03-108">El bloque de control de **TX_THREAD** se debe extender para incluir información del módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-108">The **TX_THREAD** control block must be extended to include module information.</span></span> <span data-ttu-id="00d03-109">La forma más fácil de lograr esto es reemplazar la definición de **TX_THREAD_EXTENSION_2** en el archivo **_tx_port.h_ *_ con el _* TX_THREAD_EXTENSION_2** que se encuentra en **_txm_module_port.h_**.</span><span class="sxs-lookup"><span data-stu-id="00d03-109">The easiest way to accomplish this is to replace the definition of **TX_THREAD_EXTENSION_2** in the **_tx_port.h_*_ file with the _\* TX_THREAD_EXTENSION_2*\* found in **_txm_module_port.h_**.</span></span> <span data-ttu-id="00d03-110">Consulte el [apéndice](appendix.md) para extensiones específicas del puerto.</span><span class="sxs-lookup"><span data-stu-id="00d03-110">See [appendix](appendix.md) for port-specific extensions.</span></span>

<span data-ttu-id="00d03-111">Ejemplos de extensión:</span><span class="sxs-lookup"><span data-stu-id="00d03-111">Example extension:</span></span>

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   <span data-ttu-id="00d03-112">Las siguientes extensiones deben definirse en ***tx_port. h***.</span><span class="sxs-lookup"><span data-stu-id="00d03-112">The following extensions must be defined in ***tx_port.h***.</span></span>

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. <span data-ttu-id="00d03-113">Agregue todos los archivos C y de ensamblado ***txm_module_manager_ \**** al proyecto **_tx_** de la biblioteca ThreadX.</span><span class="sxs-lookup"><span data-stu-id="00d03-113">Add all the ***txm_module_manager_\**** C and assembly files to the ThreadX library project **_tx_**.</span></span>
3. <span data-ttu-id="00d03-114">Recompile todas las bibliotecas y proyectos ejecutables.</span><span class="sxs-lookup"><span data-stu-id="00d03-114">Rebuild all libraries and executable projects.</span></span> <span data-ttu-id="00d03-115">Si se requiere NetX Duo, todo el código C del administrador de módulos y módulos debe construirse con **TXM_MODULE_ENABLE_NETX_DUO** definido.</span><span class="sxs-lookup"><span data-stu-id="00d03-115">If NetX Duo is required, all Module and Module Manager C code should be built with **TXM_MODULE_ENABLE_NETX_DUO** defined.</span></span>

## <a name="module-manager-sources"></a><span data-ttu-id="00d03-116">Orígenes del administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="00d03-116">Module Manager sources</span></span>

<span data-ttu-id="00d03-117">El administrador de módulos ThreadX tiene un conjunto de archivos de origen que están diseñados para vincularse y ubicarse directamente con el código ThreadX residente.</span><span class="sxs-lookup"><span data-stu-id="00d03-117">The ThreadX Module Manager has a set of source files that are designed to be linked and located directly with the resident ThreadX code.</span></span> <span data-ttu-id="00d03-118">Estos archivos proporcionan la capacidad de iniciar un módulo y las solicitudes de API de ThreadX subsiguientes del módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-118">These files provide the ability to launch a module and field subsequent ThreadX API requests from the module.</span></span> <span data-ttu-id="00d03-119">Los archivos del administrador de módulos son los siguientes.</span><span class="sxs-lookup"><span data-stu-id="00d03-119">The module manager files are as follows.</span></span>

| <span data-ttu-id="00d03-120">**Nombre de archivo**</span><span class="sxs-lookup"><span data-stu-id="00d03-120">**File Name**</span></span> |  <span data-ttu-id="00d03-121">**Contents**</span><span class="sxs-lookup"><span data-stu-id="00d03-121">**Contents**</span></span> |
|-------------- | ------------- |
| <span data-ttu-id="00d03-122">***txm_module.h***</span><span class="sxs-lookup"><span data-stu-id="00d03-122">***txm_module.h***</span></span> | <span data-ttu-id="00d03-123">Archivo de inclusión que define la información del módulo (también incluida en el código fuente del módulo).</span><span class="sxs-lookup"><span data-stu-id="00d03-123">Include file that defines module information (also included in the module source code).</span></span> |
| <span data-ttu-id="00d03-124">***txm_module_manager_dispatch.h***</span><span class="sxs-lookup"><span data-stu-id="00d03-124">***txm_module_manager_dispatch.h***</span></span> | <span data-ttu-id="00d03-125">Archivo de inclusión que define las funciones auxiliares de distribución.</span><span class="sxs-lookup"><span data-stu-id="00d03-125">Include file that defines dispatch helper functions.</span></span>|
| <span data-ttu-id="00d03-126">***txm_module_manager_util.h***</span><span class="sxs-lookup"><span data-stu-id="00d03-126">***txm_module_manager_util.h***</span></span> | <span data-ttu-id="00d03-127">Archivo de inclusión que define las macros y funciones internas auxiliares.</span><span class="sxs-lookup"><span data-stu-id="00d03-127">Include file that defines internal utility helper macros & functions.</span></span> |
| <span data-ttu-id="00d03-128">***txm_module_port.h***</span><span class="sxs-lookup"><span data-stu-id="00d03-128">***txm_module_port.h***</span></span> | <span data-ttu-id="00d03-129">Archivo de inclusión que define la información del módulo específico del puerto (también incluida en el código fuente del módulo).</span><span class="sxs-lookup"><span data-stu-id="00d03-129">Include file that defines port-specific module information (also included in the module source code).</span></span> |
| <span data-ttu-id="00d03-130">\***tx_initialize_low_level.\[s,S,68\]** _</span><span class="sxs-lookup"><span data-stu-id="00d03-130">\***tx_initialize_low_level.\[s,S,68\]** _</span></span> | <span data-ttu-id="00d03-131">Reemplaza el archivo de biblioteca ThreadX existente.</span><span class="sxs-lookup"><span data-stu-id="00d03-131">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="00d03-132">Tabla de vectores y controladores de vector adicionales actualizados para el administrador de módulos y las excepciones de memoria.</span><span class="sxs-lookup"><span data-stu-id="00d03-132">Updated vector table and additional vector handlers for module manager and memory exceptions.</span></span> <span data-ttu-id="00d03-133">_Este archivo solo está en Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="00d03-133">_This file is only in Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.\*</span></span>|
| <span data-ttu-id="00d03-134">\***tx_thread_context_restore.s** _</span><span class="sxs-lookup"><span data-stu-id="00d03-134">\***tx_thread_context_restore.s** _</span></span> | <span data-ttu-id="00d03-135">Reemplaza el archivo de biblioteca ThreadX existente.</span><span class="sxs-lookup"><span data-stu-id="00d03-135">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="00d03-136">Restaure el contexto del subproceso después del procesamiento de interrupción.</span><span class="sxs-lookup"><span data-stu-id="00d03-136">Restore thread context after interrupt processing.</span></span> <span data-ttu-id="00d03-137">_Este archivo solo está en Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="00d03-137">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="00d03-138">***tx_thread_schedule.\[s,S,68\]***</span><span class="sxs-lookup"><span data-stu-id="00d03-138">***tx_thread_schedule.\[s,S,68\]***</span></span> | <span data-ttu-id="00d03-139">Reemplaza el archivo de biblioteca ThreadX existente.</span><span class="sxs-lookup"><span data-stu-id="00d03-139">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="00d03-140">Código de programador extendido, que en este caso se usa para actualizar los registros de administración de memoria.</span><span class="sxs-lookup"><span data-stu-id="00d03-140">Extended scheduler code, which in this case is used to update memory management registers.</span></span> |
| <span data-ttu-id="00d03-141">\***tx_thread_stack_build.s** _</span><span class="sxs-lookup"><span data-stu-id="00d03-141">\***tx_thread_stack_build.s** _</span></span> | <span data-ttu-id="00d03-142">Reemplaza el archivo de biblioteca ThreadX existente.</span><span class="sxs-lookup"><span data-stu-id="00d03-142">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="00d03-143">Compila el marco de pila de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="00d03-143">Builds the stack frame of a thread.</span></span> <span data-ttu-id="00d03-144">_Este archivo solo está en Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="00d03-144">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="00d03-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span><span class="sxs-lookup"><span data-stu-id="00d03-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span></span> | <span data-ttu-id="00d03-146">Compila todas las pilas iniciales del módulo, incluye el programa de instalación para el acceso a datos independiente de la posición.</span><span class="sxs-lookup"><span data-stu-id="00d03-146">Builds all module initial stacks, includes setup for position-independent data access.</span></span> |
| <span data-ttu-id="00d03-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span><span class="sxs-lookup"><span data-stu-id="00d03-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span></span> | <span data-ttu-id="00d03-148">Permite al módulo entrar en modo kernel.</span><span class="sxs-lookup"><span data-stu-id="00d03-148">Allows the module to enter kernel mode.</span></span> <span data-ttu-id="00d03-149">_Este archivo solo está en Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="00d03-149">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="00d03-150">***txm_module_manager_alignment_adjust.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-150">***txm_module_manager_alignment_adjust.c***</span></span> | <span data-ttu-id="00d03-151">Controla los requisitos de alineación específicos del puerto.</span><span class="sxs-lookup"><span data-stu-id="00d03-151">Handles port-specific alignment requirements.</span></span>|
| <span data-ttu-id="00d03-152">***txm_module_manager_application_request.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-152">***txm_module_manager_application_request.c***</span></span> | <span data-ttu-id="00d03-153">Controla las solicitudes específicas de la aplicación al código residente.</span><span class="sxs-lookup"><span data-stu-id="00d03-153">Handles the application-specific requests to the resident code.</span></span> |
| <span data-ttu-id="00d03-154">***txm_module_manager_callback_request.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-154">***txm_module_manager_callback_request.c***</span></span> | <span data-ttu-id="00d03-155">Envía una solicitud de devolución de llamada a un módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-155">Sends a callback request to a module.</span></span> |
| <span data-ttu-id="00d03-156">***txm_module_manager_event_flags_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-156">***txm_module_manager_event_flags_notify_trampoline.c***</span></span> | <span data-ttu-id="00d03-157">Procesa la llamada de notificación del conjunto de marcas de eventos desde ThreadX.</span><span class="sxs-lookup"><span data-stu-id="00d03-157">Processes the event flags set notification call from ThreadX.</span></span> |
| <span data-ttu-id="00d03-158">***txm_module_manager_external_memory_enable.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-158">***txm_module_manager_external_memory_enable.c***</span></span> | <span data-ttu-id="00d03-159">Crea una entrada en la tabla de administración de memoria para un espacio de memoria compartido al que el módulo puede tener acceso.</span><span class="sxs-lookup"><span data-stu-id="00d03-159">Creates an entry in the memory management table for a shared memory space the module can access.</span></span> |
| <span data-ttu-id="00d03-160">***txm_module_manager_file_load.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-160">***txm_module_manager_file_load.c***</span></span> | <span data-ttu-id="00d03-161">Asigna y carga un archivo de módulo binario en el área de memoria del módulo y lo prepara para su ejecución.</span><span class="sxs-lookup"><span data-stu-id="00d03-161">Allocates and loads a binary module file into the module memory area and prepares it for execution.</span></span> |
| <span data-ttu-id="00d03-162">***txm_module_manager_in_place_load.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-162">***txm_module_manager_in_place_load.c***</span></span> | <span data-ttu-id="00d03-163">Asigna el área de datos del módulo y se prepara para la ejecución del módulo a partir de la dirección del código proporcionado.</span><span class="sxs-lookup"><span data-stu-id="00d03-163">Allocates the module data area and prepares for module execution from the supplied code address.</span></span> |
| <span data-ttu-id="00d03-164">***txm_module_manager_initialize.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-164">***txm_module_manager_initialize.c***</span></span> | <span data-ttu-id="00d03-165">Inicializa el administrador de módulos, incluida la especificación del área de memoria del módulo disponible para cargar y ejecutar módulos.</span><span class="sxs-lookup"><span data-stu-id="00d03-165">Initializes the Module Manager, including specification of the module memory area available for loading and running modules.</span></span> |
| <span data-ttu-id="00d03-166">\***txm_module_manager_initialize_mmu.c** _</span><span class="sxs-lookup"><span data-stu-id="00d03-166">\***txm_module_manager_initialize_mmu.c** _</span></span> | <span data-ttu-id="00d03-167">Inicializar MMU.</span><span class="sxs-lookup"><span data-stu-id="00d03-167">Initialize MMU.</span></span> <span data-ttu-id="00d03-168">Los usuarios pueden editar este archivo en función de su asignación de memoria.</span><span class="sxs-lookup"><span data-stu-id="00d03-168">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="00d03-169">_Este archivo solo está en Cortex-A7/ARM\*</span><span class="sxs-lookup"><span data-stu-id="00d03-169">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="00d03-170">\***txm_module_manager_mm_initialize.c** _</span><span class="sxs-lookup"><span data-stu-id="00d03-170">\***txm_module_manager_mm_initialize.c** _</span></span> | <span data-ttu-id="00d03-171">Inicialice MPU/MMU.</span><span class="sxs-lookup"><span data-stu-id="00d03-171">Initialize MPU/MMU.</span></span> <span data-ttu-id="00d03-172">Los usuarios pueden editar este archivo en función de su asignación de memoria.</span><span class="sxs-lookup"><span data-stu-id="00d03-172">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="00d03-173">_Este archivo solo está en Cortex-A7/ARM\*</span><span class="sxs-lookup"><span data-stu-id="00d03-173">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="00d03-174">***txm_module_manager_kernel_dispatch.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-174">***txm_module_manager_kernel_dispatch.c***</span></span> | <span data-ttu-id="00d03-175">Controla las solicitudes de API de módulo, según el id. de solicitud.</span><span class="sxs-lookup"><span data-stu-id="00d03-175">Handles the module API requests, based on the request ID.</span></span> |
| <span data-ttu-id="00d03-176">***txm_module_manager_maximum_module_priority_set.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-176">***txm_module_manager_maximum_module_priority_set.c***</span></span> | <span data-ttu-id="00d03-177">Establece la prioridad de subproceso máxima permitida en un módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-177">Sets the maximum thread priority allowed in a module.</span></span> |
| <span data-ttu-id="00d03-178">***txm_module_manager_memory_fault_handler.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-178">***txm_module_manager_memory_fault_handler.c***</span></span> | <span data-ttu-id="00d03-179">Controla los errores de memoria detectados en un módulo en ejecución.</span><span class="sxs-lookup"><span data-stu-id="00d03-179">Handles memory faults detected in an executing module.</span></span> |
| <span data-ttu-id="00d03-180">***txm_module_manager_memory_fault_notify.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-180">***txm_module_manager_memory_fault_notify.c***</span></span> | <span data-ttu-id="00d03-181">Registra una devolución de llamada de notificación de aplicación cada vez que se produce un error de memoria.</span><span class="sxs-lookup"><span data-stu-id="00d03-181">Registers an application notification callback whenever a memory fault occurs.</span></span> |
| <span data-ttu-id="00d03-182">***txm_module_manager_memory_load.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-182">***txm_module_manager_memory_load.c***</span></span> | <span data-ttu-id="00d03-183">Asigna y carga el código y los datos de un módulo y prepara el módulo para su ejecución.</span><span class="sxs-lookup"><span data-stu-id="00d03-183">Allocates and loads a module's code and data and prepares the module for execution.</span></span> |
| <span data-ttu-id="00d03-184">***txm_module_manager_mm_register_setup.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-184">***txm_module_manager_mm_register_setup.c***</span></span> | <span data-ttu-id="00d03-185">Configura registros de MPU/MMU para el módulo en función de dónde se cargan el código y los datos.</span><span class="sxs-lookup"><span data-stu-id="00d03-185">Sets up MPU/MMU registers for the module based on where the code and data are loaded.</span></span> |
| <span data-ttu-id="00d03-186">***txm_module_manager_object_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-186">***txm_module_manager_object_allocate.c***</span></span> | <span data-ttu-id="00d03-187">Asigna memoria para un objeto de módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-187">Allocates memory for a module object.</span></span> |
| <span data-ttu-id="00d03-188">***txm_module_manager_object_deallocate.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-188">***txm_module_manager_object_deallocate.c***</span></span> | <span data-ttu-id="00d03-189">Asigna memoria para un objeto de módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-189">Deallocates memory for a module object.</span></span> |
| <span data-ttu-id="00d03-190">***txm_module_manager_object_pointer_get.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-190">***txm_module_manager_object_pointer_get.c***</span></span> | <span data-ttu-id="00d03-191">Busca el tipo de objeto y el nombre proporcionados y, si los encuentra, devuelve el puntero de objeto.</span><span class="sxs-lookup"><span data-stu-id="00d03-191">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> |
| <span data-ttu-id="00d03-192">***txm_module_manager_object_pointer_get_extended.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-192">***txm_module_manager_object_pointer_get_extended.c***</span></span> | <span data-ttu-id="00d03-193">Busca el tipo de objeto y el nombre proporcionados y, si los encuentra, devuelve el puntero de objeto.</span><span class="sxs-lookup"><span data-stu-id="00d03-193">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> <span data-ttu-id="00d03-194">Longitud de nombre especificada para la seguridad.</span><span class="sxs-lookup"><span data-stu-id="00d03-194">Name length specified for safety.</span></span> |
| <span data-ttu-id="00d03-195">***txm_module_manager_object_pool_create.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-195">***txm_module_manager_object_pool_create.c***</span></span>  | <span data-ttu-id="00d03-196">Crea un grupo de objetos fuera del área de datos del módulo desde la que las aplicaciones de módulo pueden asignar.</span><span class="sxs-lookup"><span data-stu-id="00d03-196">Creates a pool of objects outside the module's data area that module applications can allocate from.</span></span> |
| <span data-ttu-id="00d03-197">***txm_module_manager_properties_get.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-197">***txm_module_manager_properties_get.c***</span></span> | <span data-ttu-id="00d03-198">Obtiene las propiedades del módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="00d03-198">Gets the properties of the specified module.</span></span> |
| <span data-ttu-id="00d03-199">***txm_module_manager_queue_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-199">***txm_module_manager_queue_notify_trampoline.c***</span></span> | <span data-ttu-id="00d03-200">Procesa la llamada de notificación de cola desde ThreadX.</span><span class="sxs-lookup"><span data-stu-id="00d03-200">Processes the queue notification call from ThreadX.</span></span> |
| <span data-ttu-id="00d03-201">***txm_module_manager_semaphore_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-201">***txm_module_manager_semaphore_notify_trampoline.c***</span></span> | <span data-ttu-id="00d03-202">Procesa la llamada de notificación de colocación de semáforo de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="00d03-202">Processes the semaphore put notification call from ThreadX.</span></span>|
| <span data-ttu-id="00d03-203">***txm_module_manager_start.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-203">***txm_module_manager_start.c***</span></span> | <span data-ttu-id="00d03-204">Inicia la ejecución de un módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-204">Starts execution of a module.</span></span> |
| <span data-ttu-id="00d03-205">***txm_module_manager_stop.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-205">***txm_module_manager_stop.c***</span></span> | <span data-ttu-id="00d03-206">Detiene la ejecución de un módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-206">Stops execution of a module.</span></span> |
| <span data-ttu-id="00d03-207">***txm_module_manager_thread_create.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-207">***txm_module_manager_thread_create.c***</span></span> | <span data-ttu-id="00d03-208">Crea todos los subprocesos del módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-208">Creates all module threads.</span></span> |
| <span data-ttu-id="00d03-209">***txm_module_manager_thread_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-209">***txm_module_manager_thread_notify_trampoline.c***</span></span> | <span data-ttu-id="00d03-210">Procesa la llamada de notificación de entrada/salida de subproceso desde ThreadX.</span><span class="sxs-lookup"><span data-stu-id="00d03-210">Processes the thread entry/exit notification call from ThreadX.</span></span> |
| <span data-ttu-id="00d03-211">***txm_module_manager_thread_reset.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-211">***txm_module_manager_thread_reset.c***</span></span> | <span data-ttu-id="00d03-212">Restablecer un subproceso de módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-212">Reset a module thread.</span></span> |
| <span data-ttu-id="00d03-213">***txm_module_manager_timer_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-213">***txm_module_manager_timer_notify_trampoline.c***</span></span> | <span data-ttu-id="00d03-214">Procesa las expiraciones del temporizador desde ThreadX.</span><span class="sxs-lookup"><span data-stu-id="00d03-214">Processes timer expirations from ThreadX.</span></span> |
| <span data-ttu-id="00d03-215">***txm_module_manager_unload.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-215">***txm_module_manager_unload.c***</span></span> | <span data-ttu-id="00d03-216">Descarga el módulo del área de memoria del módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-216">Unloads the module from the module memory area.</span></span> |
| <span data-ttu-id="00d03-217">***txm_module_manager_util.c***</span><span class="sxs-lookup"><span data-stu-id="00d03-217">***txm_module_manager_util.c***</span></span> | <span data-ttu-id="00d03-218">Funciones auxiliares internas para el administrador.</span><span class="sxs-lookup"><span data-stu-id="00d03-218">Internal helper functions for manager.</span></span> |

## <a name="module-manager-initialization"></a><span data-ttu-id="00d03-219">Inicialización del administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="00d03-219">Module Manager initialization</span></span>

<span data-ttu-id="00d03-220">La parte residente de la aplicación es responsable de llamar a la función de inicialización del administrador de módulos ***txm_module_manager_initialize***.</span><span class="sxs-lookup"><span data-stu-id="00d03-220">The resident portion of the application is responsible for calling the Module Manager initialization function ***txm_module_manager_initialize***.</span></span> <span data-ttu-id="00d03-221">Esta función configura las estructuras internas para cargar y descargar módulos, incluida la configuración del área de memoria que se usa para la asignación de memoria del módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-221">This function sets up the internal structures for loading and unloading modules, including setting up the memory area used for allocating module memory.</span></span>

## <a name="module-manager-loading"></a><span data-ttu-id="00d03-222">Carga del administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="00d03-222">Module Manager loading</span></span>

<span data-ttu-id="00d03-223">El administrador de módulos puede cargar módulos de forma dinámica en la memoria del módulo desde los archivos de módulo binario o desde una sección de código de módulo que ya está presente en el área de código residente.</span><span class="sxs-lookup"><span data-stu-id="00d03-223">The Module Manager can load modules dynamically into the module memory from binary module files or from a module code section that is already present in the resident code area.</span></span> <span data-ttu-id="00d03-224">Además, el administrador de módulos puede ejecutar código en contexto, es decir, solo se asignan los datos del módulo en la memoria del módulo y la ejecución del código se realiza en su lugar.</span><span class="sxs-lookup"><span data-stu-id="00d03-224">In addition, the module manager can execute code in place, that is, only the module data is allocated in the module memory and the code execution is done in place.</span></span> <span data-ttu-id="00d03-225">Están disponibles las siguientes funciones de la API de carga del administrador de módulos.</span><span class="sxs-lookup"><span data-stu-id="00d03-225">The following Module Manager load API functions are available.</span></span>

* <span data-ttu-id="00d03-226">***txm_module_manager_file_load***</span><span class="sxs-lookup"><span data-stu-id="00d03-226">***txm_module_manager_file_load***</span></span>

* <span data-ttu-id="00d03-227">***txm_module_manager_in_place_load***</span><span class="sxs-lookup"><span data-stu-id="00d03-227">***txm_module_manager_in_place_load***</span></span>

* <span data-ttu-id="00d03-228">***txm_module_manager_memory_load***</span><span class="sxs-lookup"><span data-stu-id="00d03-228">***txm_module_manager_memory_load***</span></span>

<span data-ttu-id="00d03-229">La versión protegida en memoria del administrador de módulos también se asegura de que el módulo se carga con la alineación adecuada y los registros de administración de memoria se configuran correctamente para cada módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-229">The memory protected version of the Module Manager also makes sure that the module is loaded with the proper alignment and the memory management registers are set up properly for each module.</span></span> <span data-ttu-id="00d03-230">Cuando se habilita la protección de memoria a través de las opciones del preámbulo del módulo, el acceso a la memoria del módulo está restringido al código del módulo y a las áreas de datos.</span><span class="sxs-lookup"><span data-stu-id="00d03-230">When memory protection is enabled via the module preamble options, module memory access is restricted to the module code and data areas.</span></span>

## <a name="module-manager-starting"></a><span data-ttu-id="00d03-231">Inicio del administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="00d03-231">Module Manager starting</span></span>

<span data-ttu-id="00d03-232">El administrador de módulos inicia la ejecución de un módulo cargado previamente a través de la función de API de ***txm_module_manager_start***.</span><span class="sxs-lookup"><span data-stu-id="00d03-232">The Module Manager initiates execution of a previously-loaded module via the ***txm_module_manager_start*** API function.</span></span> <span data-ttu-id="00d03-233">Para iniciar la ejecución del módulo, esta función crea un subproceso que entra en el módulo en la ubicación de inicio especificada en el preámbulo del módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-233">To initiate module execution, this function creates a thread that enters the module at the starting location specified in the module preamble.</span></span> <span data-ttu-id="00d03-234">La prioridad y el tamaño de pila de este subproceso también se especifican en el preámbulo del módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-234">The priority and stack size of this thread is also specified in the module preamble.</span></span>

## <a name="module-manager-stopping"></a><span data-ttu-id="00d03-235">Detención del administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="00d03-235">Module Manager stopping</span></span>

<span data-ttu-id="00d03-236">El administrador de módulos finaliza la ejecución de un módulo cargado previamente y en ejecución a través de la función ***txm_module_manager_stop***.</span><span class="sxs-lookup"><span data-stu-id="00d03-236">The Module Manager terminates execution of a previously-loaded and executing module via the ***txm_module_manager_stop*** function.</span></span> <span data-ttu-id="00d03-237">Esta función de API finaliza primero y elimina el subproceso de inicio inicial.</span><span class="sxs-lookup"><span data-stu-id="00d03-237">This API function first terminates and deletes the initial starting thread.</span></span> <span data-ttu-id="00d03-238">Si el preámbulo del módulo especifica un subproceso de detención, este subproceso se crea y se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="00d03-238">If the module preamble specifies a stop thread, this thread is created and executed.</span></span> <span data-ttu-id="00d03-239">El administrador de módulos espera durante un período de tiempo fijo para que se complete el subproceso de detención.</span><span class="sxs-lookup"><span data-stu-id="00d03-239">The Module Manager waits for a fixed period of time for the stop thread to complete.</span></span> <span data-ttu-id="00d03-240">Una vez completado, se eliminan todos los recursos del sistema creados por el módulo y el módulo se coloca en un estado inactivo, desde el que puede reiniciarse o descargarse.</span><span class="sxs-lookup"><span data-stu-id="00d03-240">Once complete, all system resources created by the module are deleted and the module is placed in a dormant state, from which it can be either restarted or unloaded.</span></span>

## <a name="module-manager-unloading"></a><span data-ttu-id="00d03-241">Descarga del administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="00d03-241">Module Manager unloading</span></span>

<span data-ttu-id="00d03-242">El administrador de módulos descarga un módulo cargado previamente pero que no se está ejecutando a través de la función ***txm_module_manager_unload***.</span><span class="sxs-lookup"><span data-stu-id="00d03-242">The Module Manager unloads a previously-loaded but not executing module via the ***txm_module_manager_unload*** function.</span></span> <span data-ttu-id="00d03-243">Esta API libera toda la memoria asociada al módulo y la libera para su uso con otro módulo en el futuro.</span><span class="sxs-lookup"><span data-stu-id="00d03-243">This API releases all memory associated with the module, freeing it for use with another module in the future.</span></span>

## <a name="module-manager-requests"></a><span data-ttu-id="00d03-244">Solicitudes del administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="00d03-244">Module Manager requests</span></span>

<span data-ttu-id="00d03-245">Las solicitudes realizadas por los módulos al administrador de módulos se realizan mediante macros en ***txm_module.h*** que asignan todas las llamadas a ThreadX para llamar a la función de distribución del administrador de módulos a través de un puntero de función proporcionado por el administrador de módulos.</span><span class="sxs-lookup"><span data-stu-id="00d03-245">Requests made by modules to the Module Manager are done via macros in ***txm_module.h*** that map all ThreadX calls to call the Module Manager dispatch function via a function pointer supplied to the module by the Module Manager.</span></span>

<span data-ttu-id="00d03-246">Los servicios adicionales específicos de la aplicación que se realizan a través del módulo que llama a ***txm_module_application_request*** se controlan mediante el mismo mecanismo de macro que se usa para la API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="00d03-246">Additional application-specific services made via the module calling ***txm_module_application_request*** are handled by the same macro mechanism used for the ThreadX API.</span></span> <span data-ttu-id="00d03-247">De manera predeterminada, esta función de control del administrador de módulos está vacía y está diseñada de modo que la aplicación agregue el código necesario para procesar las solicitudes específicas de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="00d03-247">By default, this handling function in the Module Manager is empty and designed such that the application adds the necessary code to process the application-specific requests.</span></span>

<span data-ttu-id="00d03-248">Si el administrador del módulo no implementa la solicitud, el administrador del módulo devuelve un valor de estado de error **TX_NOT_AVAILABLE**.</span><span class="sxs-lookup"><span data-stu-id="00d03-248">If the request is not implemented by the Module Manager, a value of **TX_NOT_AVAILABLE** error status is returned by the Module Manager.</span></span> <span data-ttu-id="00d03-249">También se devuelve este código de error si el módulo solicita una operación que está fuera del ámbito del acceso del módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-249">This error code is also returned if the module requests an operation that is outside the scope of the module's access.</span></span> <span data-ttu-id="00d03-250">Por ejemplo, un módulo no tiene permiso para crear un temporizador con el bloque de control del temporizador o la dirección de devolución de llamada fuera del área de código del módulo.</span><span class="sxs-lookup"><span data-stu-id="00d03-250">For example, a module is not allowed to create a timer with the timer control block or callback address outside of the module's code area.</span></span>

## <a name="module-manager-example"></a><span data-ttu-id="00d03-251">Ejemplo de administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="00d03-251">Module Manager example</span></span>

<span data-ttu-id="00d03-252">A continuación se presenta un ejemplo de código del administrador de módulos que inicia el módulo de ejemplo previamente definido en el capítulo 2.</span><span class="sxs-lookup"><span data-stu-id="00d03-252">The following is an example of Module Manager code that launches the example module previously defined in Chapter 2.</span></span> <span data-ttu-id="00d03-253">Se supone que el módulo ya está cargado, presumiblemente por el depurador, en la dirección ROM 0x00800000.</span><span class="sxs-lookup"><span data-stu-id="00d03-253">It is assumed that the module is already loaded, presumably by the debugger, at ROM address 0x00800000.</span></span>

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a><span data-ttu-id="00d03-254">Compilación del administrador de módulos</span><span class="sxs-lookup"><span data-stu-id="00d03-254">Module Manager building</span></span>

<span data-ttu-id="00d03-255">Los archivos de origen de ***txm_module_manager_ \**** se deben agregar a la biblioteca ThreadX.</span><span class="sxs-lookup"><span data-stu-id="00d03-255">The ***txm_module_manager_\**** source files must be added to the ThreadX library.</span></span>

<span data-ttu-id="00d03-256">Una aplicación del administrador de módulos ThreadX es realmente la misma que una aplicación ThreadX estándar, que es uno o varios archivos de aplicación vinculados junto con la biblioteca ThreadX ***tx.a***.</span><span class="sxs-lookup"><span data-stu-id="00d03-256">A ThreadX Module Manager application is effectively the same as a standard ThreadX application, which is one or more application files linked together with the ThreadX library ***tx.a***.</span></span> <span data-ttu-id="00d03-257">La compilación de una aplicación del administrador de módulos depende de la cadena de herramientas utilizada.</span><span class="sxs-lookup"><span data-stu-id="00d03-257">Building a module manager application is dependent on the tool chain being used.</span></span> <span data-ttu-id="00d03-258">Consulte el [apéndice](appendix.md) para ver ejemplos específicos de puertos.</span><span class="sxs-lookup"><span data-stu-id="00d03-258">See [appendix](appendix.md) for port-specific examples.</span></span>
