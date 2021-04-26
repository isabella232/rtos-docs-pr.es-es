---
title: 'Capítulo 2: requisitos de los módulos'
description: Este artículo es una descripción de los requisitos para compilar un módulo de ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 32288d78ceffb74ab088a1d720dbac657f6d3ed4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814382"
---
# <a name="chapter-2---module-requirements"></a><span data-ttu-id="7a622-103">Capítulo 2: requisitos de los módulos</span><span class="sxs-lookup"><span data-stu-id="7a622-103">Chapter 2 - Module requirements</span></span>

<span data-ttu-id="7a622-104">Un módulo de ThreadX contiene un preámbulo, que define las características básicas del módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-104">A ThreadX Module contains a preamble, which defines the basic characteristics of the module.</span></span> <span data-ttu-id="7a622-105">El preámbulo va seguido del área de instrucciones del módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-105">The preamble is followed by the instruction area of the module.</span></span> <span data-ttu-id="7a622-106">El administrador de módulos puede ejecutar los módulos en contexto o puede cargarlos en el área de memoria del módulo antes de su ejecución.</span><span class="sxs-lookup"><span data-stu-id="7a622-106">Modules may be executed in place or they may be loaded into the module memory area by the Module Manager prior to execution.</span></span> <span data-ttu-id="7a622-107">El único requisito es que el preámbulo siempre se encuentre en la primera dirección del módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-107">The only requirement is that the preamble is always located at the first address of the module.</span></span> <span data-ttu-id="7a622-108">En la ilustración 2 se muestra un diseño de módulo básico.</span><span class="sxs-lookup"><span data-stu-id="7a622-108">Figure 2 illustrates a basic module layout.</span></span>

| <span data-ttu-id="7a622-109">Diseño de módulo</span><span class="sxs-lookup"><span data-stu-id="7a622-109">Module Layout</span></span> |
|:---:|
| <span data-ttu-id="7a622-110">\[preámbulo del módulo\]</span><span class="sxs-lookup"><span data-stu-id="7a622-110">\[module preamble\]</span></span>         |
| <span data-ttu-id="7a622-111">\[área de instrucciones del módulo\]</span><span class="sxs-lookup"><span data-stu-id="7a622-111">\[module instruction area\]</span></span> |
| <span data-ttu-id="7a622-112">\[área RAM del módulo\]</span><span class="sxs-lookup"><span data-stu-id="7a622-112">\[module RAM area\]</span></span>         |

<span data-ttu-id="7a622-113">**Figura 2**: diseño de módulo</span><span class="sxs-lookup"><span data-stu-id="7a622-113">**Figure 2** - Module Layout</span></span>

> [!NOTE]
> <span data-ttu-id="7a622-114">Los módulos deben compilarse con el código independiente de la posición y las opciones del compilador o del enlazador de datos adecuados.</span><span class="sxs-lookup"><span data-stu-id="7a622-114">Modules must be built with the appropriate position independent code and data compiler/linker options.</span></span> <span data-ttu-id="7a622-115">Esto permite la ejecución del módulo en cualquier área de memoria.</span><span class="sxs-lookup"><span data-stu-id="7a622-115">This enables execution of the module in any memory area.</span></span>

<span data-ttu-id="7a622-116">Cuando se crea un subproceso de módulo, se asigna un segundo espacio de pila para su uso cuando el subproceso está en el kernel protegido por la memoria.</span><span class="sxs-lookup"><span data-stu-id="7a622-116">When a Module thread is created, a second stack space is allocated for use when the thread is in the memory-protected kernel.</span></span> <span data-ttu-id="7a622-117">El tamaño del espacio de pila del kernel del subproceso es configurable por el usuario mediante **TXM_MODULE_KERNEL_STACK_SIZE** en **_txm_module_port.h_ *_. Esto permite usar un tamaño de pila menor al crear un subproceso de módulo, ya que la pila especificada por el usuario al llamar a _* _tx_thread_create_** solo se usa en el módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-117">The size of the thread's kernel stack space is user-configurable using **TXM_MODULE_KERNEL_STACK_SIZE** in **_txm_module_port.h_*_. This allows a smaller stack size to be used when creating a Module thread, as the stack specified by the user when calling _*_tx_thread_create_** is only used in the module.</span></span>

> [!NOTE]
> <span data-ttu-id="7a622-118">La parte superior de una pila de subprocesos de módulo contiene la estructura de información de entrada de subproceso (**TXM_MODULE_THREAD_ENTRY_INFO**), por lo que el tamaño de pila disponible disminuye según el tamaño de esta estructura.</span><span class="sxs-lookup"><span data-stu-id="7a622-118">The top of a module thread stack contains the thread entry information structure (**TXM_MODULE_THREAD_ENTRY_INFO**), so the available stack size is decreased by the size of this structure.</span></span> <span data-ttu-id="7a622-119">Al crear un subproceso en un módulo, aumenta su tamaño de pila al menos en el equivalente al tamaño de esta estructura.</span><span class="sxs-lookup"><span data-stu-id="7a622-119">When creating a thread in a module, increase its stack size by at least this the size of this structure.</span></span>

<span data-ttu-id="7a622-120">Los siguientes pasos son necesarios para crear y compilar un módulo de ThreadX (cada paso se describe con más detalle a continuación).</span><span class="sxs-lookup"><span data-stu-id="7a622-120">The following steps are required for creating and building a ThreadX Module (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="7a622-121">Todos los archivos de C de un módulo deben aplicar #define **TXM_MODULE** antes de incluir **_txm_module.h_**.</span><span class="sxs-lookup"><span data-stu-id="7a622-121">All C files in a module must #define **TXM_MODULE** prior to including **_txm_module.h_**.</span></span> <span data-ttu-id="7a622-122">Esto puede realizarse en el archivo de código fuente que se está compilando o como parte de la configuración del proyecto.</span><span class="sxs-lookup"><span data-stu-id="7a622-122">This can be accomplished in the source file being compiled or as part of the project settings.</span></span> <span data-ttu-id="7a622-123">Al hacerlo, se reasignan las llamadas a la API de ThreadX a la versión específica del módulo de la API que invoca la función de distribución en el administrador de módulos residente para realizar la llamada a la función de API real.</span><span class="sxs-lookup"><span data-stu-id="7a622-123">Doing so remaps the ThreadX API calls to the module-specific version of the API that invokes the dispatch function in the resident Module Manager to perform the call to the actual API function.</span></span>
2. <span data-ttu-id="7a622-124">Cada módulo debe tener un preámbulo en su primera dirección de área de instrucciones que defina las características y las necesidades de recursos del módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-124">Each module must have a preamble at its first instruction area address which defines the characteristics and the resource needs of the module.</span></span>
3. <span data-ttu-id="7a622-125">Cada módulo debe vincular el preámbulo al principio del área de instrucciones del módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-125">Each module must link the preamble at the beginning of the module instruction area.</span></span>
4. <span data-ttu-id="7a622-126">Cada módulo debe vincularse a una biblioteca de módulos (***tmx.a***), que contiene funciones específicas del módulo que se usan para interactuar con ThreadX.</span><span class="sxs-lookup"><span data-stu-id="7a622-126">Each module must link against a module library (***txm.a***), which contains module-specific functions used to interact with ThreadX.</span></span>

## <a name="module-sources"></a><span data-ttu-id="7a622-127">Orígenes de los módulos</span><span class="sxs-lookup"><span data-stu-id="7a622-127">Module sources</span></span>

<span data-ttu-id="7a622-128">Los módulos de ThreadX tienen su propio conjunto de archivos de código fuente que están diseñados para vincularse y ubicarse directamente con el código fuente del módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-128">ThreadX Modules have their own set of source files that are designed to be linked and located directly with the module source code.</span></span> <span data-ttu-id="7a622-129">Estos archivos proporcionan el puente entre el módulo independiente y el administrador de módulos residente.</span><span class="sxs-lookup"><span data-stu-id="7a622-129">These files provide the bridge between the separate module and resident Module Manager.</span></span> <span data-ttu-id="7a622-130">Los archivos del módulo son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="7a622-130">The Module files are as follows.</span></span>

| <span data-ttu-id="7a622-131">Nombre de archivo</span><span class="sxs-lookup"><span data-stu-id="7a622-131">File Name</span></span> | <span data-ttu-id="7a622-132">Contenido</span><span class="sxs-lookup"><span data-stu-id="7a622-132">Contents</span></span> |
|---|---|
| <span data-ttu-id="7a622-133">**txm_module.h**</span><span class="sxs-lookup"><span data-stu-id="7a622-133">**txm_module.h**</span></span> | <span data-ttu-id="7a622-134">Archivo de inclusión que define la información del módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-134">Include file that defines module information.</span></span> |
| <span data-ttu-id="7a622-135">**txm_module_port.h**</span><span class="sxs-lookup"><span data-stu-id="7a622-135">**txm_module_port.h**</span></span> | <span data-ttu-id="7a622-136">Archivo de inclusión que define la información del módulo específico del puerto.</span><span class="sxs-lookup"><span data-stu-id="7a622-136">Include file that defines port-specific module information.</span></span> |
| <span data-ttu-id="7a622-137">**txm_module_user.h**</span><span class="sxs-lookup"><span data-stu-id="7a622-137">**txm_module_user.h**</span></span> | <span data-ttu-id="7a622-138">Definiciones y valores que el usuario puede personalizar.</span><span class="sxs-lookup"><span data-stu-id="7a622-138">Defines and values the user can customize.</span></span> |
| <span data-ttu-id="7a622-139">**txm_module_initialize.s [1][3]**</span><span class="sxs-lookup"><span data-stu-id="7a622-139">**txm_module_initialize.s [1][3]**</span></span> | <span data-ttu-id="7a622-140">Llama a funciones intrínsecas para el módulo de inicio.</span><span class="sxs-lookup"><span data-stu-id="7a622-140">Calls intrinsic functions to startup module.</span></span> |
| <span data-ttu-id="7a622-141">**txm_module_preamble.\{s/S/68\}**</span><span class="sxs-lookup"><span data-stu-id="7a622-141">**txm_module_preamble.\{s/S/68\}**</span></span> | <span data-ttu-id="7a622-142">Archivo de ensamblado del preámbulo del módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-142">Module preamble assembly file.</span></span> <span data-ttu-id="7a622-143">Este archivo define varios atributos específicos del módulo y está vinculado con el código de aplicación del módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-143">This file defines various module-specific attributes and is linked with the module application code.</span></span> |
| <span data-ttu-id="7a622-144">**txm_module_application_request.c [1]**</span><span class="sxs-lookup"><span data-stu-id="7a622-144">**txm_module_application_request.c [1]**</span></span> | <span data-ttu-id="7a622-145">La función de solicitud de aplicación de módulo envía una solicitud específica de la aplicación al código residente.</span><span class="sxs-lookup"><span data-stu-id="7a622-145">Module application request function sends an application-specific request to the resident code.</span></span> |
| <span data-ttu-id="7a622-146">**txm_module_callback_request_thread_entry.c&nbsp;[1]**</span><span class="sxs-lookup"><span data-stu-id="7a622-146">**txm_module_callback_request_thread_entry.c&nbsp;[1]**</span></span> | <span data-ttu-id="7a622-147">Subproceso de devolución de llamada de módulo que es responsable de procesar las devoluciones de llamada solicitadas por el módulo, incluidos temporizadores y devoluciones de llamada de notificación.</span><span class="sxs-lookup"><span data-stu-id="7a622-147">Module callback thread that is responsible for processing callbacks requested by the module, including timers and notification callbacks.</span></span> |
| <span data-ttu-id="7a622-148">**txm_\*.c [1][2]**</span><span class="sxs-lookup"><span data-stu-id="7a622-148">**txm_\*.c [1][2]**</span></span> | <span data-ttu-id="7a622-149">Los servicios estándar de la API de ThreadX llaman al distribuidor del kernel.</span><span class="sxs-lookup"><span data-stu-id="7a622-149">The standard ThreadX API services, these call the kernel dispatcher.</span></span>
| <span data-ttu-id="7a622-150">**txm_module_object_allocate.c [1]**</span><span class="sxs-lookup"><span data-stu-id="7a622-150">**txm_module_object_allocate.c [1]**</span></span> | <span data-ttu-id="7a622-151">Función de módulo para asignar memoria para los objetos de módulo ubicados en el grupo de memoria del administrador.</span><span class="sxs-lookup"><span data-stu-id="7a622-151">Module function to allocate memory for module objects located in the manager memory pool.</span></span> |
| <span data-ttu-id="7a622-152">**txm_module_object_deallocate.c [1]**</span><span class="sxs-lookup"><span data-stu-id="7a622-152">**txm_module_object_deallocate.c [1]**</span></span> | <span data-ttu-id="7a622-153">Función de módulo para desasignar memoria para los objetos de módulo ubicados en el bloque de memoria del administrador.</span><span class="sxs-lookup"><span data-stu-id="7a622-153">Module function to deallocate memory for module objects located in the manager memory pool.</span></span> |
| <span data-ttu-id="7a622-154">**txm_module_object_pointer_get.c [1]**</span><span class="sxs-lookup"><span data-stu-id="7a622-154">**txm_module_object_pointer_get.c [1]**</span></span> | <span data-ttu-id="7a622-155">Función de módulo para recuperar un puntero a un objeto del sistema.</span><span class="sxs-lookup"><span data-stu-id="7a622-155">Module function to retrieve a pointer to a system object.</span></span> |
| <span data-ttu-id="7a622-156">**txm_module_object_pointer_get_extended.c [1]**</span><span class="sxs-lookup"><span data-stu-id="7a622-156">**txm_module_object_pointer_get_extended.c [1]**</span></span> | <span data-ttu-id="7a622-157">Función de módulo para recuperar un puntero a un objeto del sistema, seguridad de la longitud del nombre.</span><span class="sxs-lookup"><span data-stu-id="7a622-157">Module function to retrieve a pointer to a system object, name length safety.</span></span> |
| <span data-ttu-id="7a622-158">**txm_module_thread_shell_entry.c [1]**</span><span class="sxs-lookup"><span data-stu-id="7a622-158">**txm_module_thread_shell_entry.c [1]**</span></span> | <span data-ttu-id="7a622-159">Función de entrada de subprocesos de módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-159">Module thread entry function.</span></span> |
| <span data-ttu-id="7a622-160">**txm_module_thread_system_suspend.c [1]**</span><span class="sxs-lookup"><span data-stu-id="7a622-160">**txm_module_thread_system_suspend.c [1]**</span></span> | <span data-ttu-id="7a622-161">Función de módulo para suspender un subproceso.</span><span class="sxs-lookup"><span data-stu-id="7a622-161">Module function to suspend a thread.</span></span> |

<span data-ttu-id="7a622-162">**[1]** Ubicado en la biblioteca **_tmx.a_**.</span><span class="sxs-lookup"><span data-stu-id="7a622-162">**[1]** Located in library **_txm.a_**.</span></span>

<span data-ttu-id="7a622-163">**[2]** Estos archivos tienen el mismo nombre que los archivos de la API de ThreadX, con el prefijo **txm_** en lugar del prefijo **tx_** .</span><span class="sxs-lookup"><span data-stu-id="7a622-163">**[2]** These files have the same name as the ThreadX API files, with **txm_** prefix instead of **tx_** prefix.</span></span>

<span data-ttu-id="7a622-164">**[3]** El archivo **txm_module_initialize.s** solo es para puertos que usan herramientas ARM.</span><span class="sxs-lookup"><span data-stu-id="7a622-164">**[3]** The **txm_module_initialize.s** file is only for ports using ARM tools.</span></span>

## <a name="module-preamble"></a><span data-ttu-id="7a622-165">Preámbulo del módulo</span><span class="sxs-lookup"><span data-stu-id="7a622-165">Module preamble</span></span>

<span data-ttu-id="7a622-166">El preámbulo del módulo define las características y los recursos del módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-166">The Module Preamble defines characteristics and resources of the module.</span></span> <span data-ttu-id="7a622-167">Información como la función de entrada de subproceso inicial y el área de memoria inicial asociada al subproceso se definen en el preámbulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-167">Information such as the initial thread entry function and the initial memory area associated with the thread are defined in the preamble.</span></span> <span data-ttu-id="7a622-168">Los ejemplos de preámbulos específicos del puerto se encuentran en el [apéndice](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="7a622-168">Port-specific preamble examples are in the [appendix](appendix.md).</span></span> <span data-ttu-id="7a622-169">En la figura 3 se muestra un ejemplo de preámbulo de un módulo de ThreadX para un destino genérico (las líneas que comienzan con \* son valores que la aplicación suele modificar):</span><span class="sxs-lookup"><span data-stu-id="7a622-169">Figure 3 shows an example ThreadX module preamble for a generic target (the lines starting with \* are values typically modified by the application):</span></span>

```c
    AREA Init, CODE, READONLY

    /* Define public symbols. */
    EXPORT __txm_module_preamble

    /* Define application-specific start/stop entry points for the module. */
    IMPORT demo_module_start

    /* Define common external refrences. */
    IMPORT _txm_module_thread_shell_entry
    IMPORT _txm_module_callback_request_thread_entry
    IMPORT |Image$$ER_RO$$Length|
    IMPORT |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                  ; Module ID
    DCD     0x6                                         ; Module Major Version
    DCD     0x1                                         ; Module Minor Version
    DCD     32                                          ; Module Preamble Size in 32-bit words
*   DCD     0x12345678                                  ; Module ID (application defined)
*   DCD     0x01000001                                  ; Module Properties where:
                                                        ; Bits 31-24: Compiler ID
                                                        ;   0 -> IAR
                                                        ;   1 -> ARM
                                                        ;   2 -> GNU
                                                        ;   Bits 23-1: Reserved
                                                        ;   Bit 0: 0 -> Privileged mode execution (no MMU protection)
                                                        ;          1 -> User mode execution (MMU protection)
    DCD     _txm_module_thread_shell_entry - . + .      ; Module Shell Entry Point
*   DCD     demo_module_start - . + .                   ; Module Start Thread Entry Point
    DCD     0                                           ; Module Stop Thread Entry Point
*   DCD     1                                           ; Module Start/Stop Thread Priority
*   DCD     2048                                        ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD     1                                            ; Module Callback Thread Priority
    DCD     2048                                         ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length|                       ; Module Code Size
    DCD     |Image$$ER_RW$$Length|                       ; Module Data Size
    DCD     0                                            ; Reserved 0
    DCD     0                                            ; Reserved 1
    DCD     0                                            ; Reserved 2
    DCD     0                                            ; Reserved 3
    DCD     0                                            ; Reserved 4
    DCD     0                                            ; Reserved 5
    DCD     0                                            ; Reserved 6
    DCD     0                                            ; Reserved 7
    DCD     0                                            ; Reserved 8
    DCD     0                                            ; Reserved 9
    DCD     0                                            ; Reserved 10
    DCD     0                                            ; Reserved 11
    DCD     0                                            ; Reserved 12
    DCD     0                                            ; Reserved 13
    DCD     0                                            ; Reserved 14
    DCD     0                                            ; Reserved 15
    END
```

<span data-ttu-id="7a622-170">**Ilustración 3**</span><span class="sxs-lookup"><span data-stu-id="7a622-170">**Figure 3**</span></span>

<span data-ttu-id="7a622-171">En la mayoría de los casos, el desarrollador solo necesita definir el subproceso de inicio del módulo (desplazamiento 0x1C), el identificador de módulo (desplazamiento 0x10), la prioridad de subprocesos de inicio o detención (desplazamiento 0x24) y el tamaño de la pila de subprocesos de inicio o detención (desplazamiento 0x28).</span><span class="sxs-lookup"><span data-stu-id="7a622-171">In most cases, the developer only needs to define the module's starting thread (offset 0x1C), module ID (offset 0x10), start/stop thread priority (offset 0x24), and start/stop thread stack size (offset 0x28).</span></span> <span data-ttu-id="7a622-172">La demostración anterior está configurada de modo que el subproceso inicial del módulo es ***demo_module_start** _, el identificador de módulo es _*_0x12345678_*_ y el subproceso de inicio tiene una prioridad de _*_1_\*_ y un tamaño de pila de _ \*_2048_\*\* bytes.</span><span class="sxs-lookup"><span data-stu-id="7a622-172">The demonstration above is set up such that the starting thread of the module is ***demo_module_start** _, the module ID is _*_0x12345678_*_, and the starting thread has a priority of _*_1_*_, and a stack size of _ *_2048_** bytes.</span></span>

<span data-ttu-id="7a622-173">Algunas aplicaciones pueden definir opcionalmente un subproceso de detención, que se ejecuta cuando el administrador de módulos detiene el módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-173">Some applications may optionally define a stopping thread, which is executed as the Module Manager stops the module.</span></span> <span data-ttu-id="7a622-174">Además, algunas aplicaciones pueden emplear el campo propiedades del módulo, que se define de la siguiente manera.</span><span class="sxs-lookup"><span data-stu-id="7a622-174">In addition, some applications might utilize the Module Properties field, defined as follows.</span></span>

## <a name="module-properties-bit-map"></a><span data-ttu-id="7a622-175">Mapa de bits de las propiedades del módulo</span><span class="sxs-lookup"><span data-stu-id="7a622-175">Module properties bit map</span></span>

<span data-ttu-id="7a622-176">En la siguiente tabla se muestra un ejemplo de mapa de bits de las propiedades.</span><span class="sxs-lookup"><span data-stu-id="7a622-176">The table below shows an example of the properties bit map.</span></span> <span data-ttu-id="7a622-177">Los mapas de bits de las propiedades específicas del puerto se encuentran en el [apéndice](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="7a622-177">Port-specific properties bitmaps are in the [appendix](appendix.md).</span></span>

| <span data-ttu-id="7a622-178">bit</span><span class="sxs-lookup"><span data-stu-id="7a622-178">Bit</span></span> | <span data-ttu-id="7a622-179">Value</span><span class="sxs-lookup"><span data-stu-id="7a622-179">Value</span></span> | <span data-ttu-id="7a622-180">Significado</span><span class="sxs-lookup"><span data-stu-id="7a622-180">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="7a622-181">0</span><span class="sxs-lookup"><span data-stu-id="7a622-181">0</span></span> | <span data-ttu-id="7a622-182">0</span><span class="sxs-lookup"><span data-stu-id="7a622-182">0</span></span><br /><span data-ttu-id="7a622-183">1</span><span class="sxs-lookup"><span data-stu-id="7a622-183">1</span></span> | <span data-ttu-id="7a622-184">Ejecución en modo privilegiado</span><span class="sxs-lookup"><span data-stu-id="7a622-184">Privileged mode execution</span></span><br /><span data-ttu-id="7a622-185">Ejecución en modo de usuario</span><span class="sxs-lookup"><span data-stu-id="7a622-185">User mode execution</span></span> |
| <span data-ttu-id="7a622-186">1</span><span class="sxs-lookup"><span data-stu-id="7a622-186">1</span></span> | <span data-ttu-id="7a622-187">0</span><span class="sxs-lookup"><span data-stu-id="7a622-187">0</span></span><br /><span data-ttu-id="7a622-188">1</span><span class="sxs-lookup"><span data-stu-id="7a622-188">1</span></span> | <span data-ttu-id="7a622-189">Sin protección de MPU</span><span class="sxs-lookup"><span data-stu-id="7a622-189">No MPU protection</span></span><br /><span data-ttu-id="7a622-190">Protección de MPU (debe estar seleccionado el modo de usuario)</span><span class="sxs-lookup"><span data-stu-id="7a622-190">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="7a622-191">2</span><span class="sxs-lookup"><span data-stu-id="7a622-191">2</span></span> | <span data-ttu-id="7a622-192">0</span><span class="sxs-lookup"><span data-stu-id="7a622-192">0</span></span><br /><span data-ttu-id="7a622-193">1</span><span class="sxs-lookup"><span data-stu-id="7a622-193">1</span></span> | <span data-ttu-id="7a622-194">Deshabilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="7a622-194">Disable shared/external memory access</span></span><br /><span data-ttu-id="7a622-195">Habilitar el acceso a la memoria compartida/externa</span><span class="sxs-lookup"><span data-stu-id="7a622-195">Enable shared/external memory access</span></span> |
| <span data-ttu-id="7a622-196">[23-3]</span><span class="sxs-lookup"><span data-stu-id="7a622-196">[23-3]</span></span> | <span data-ttu-id="7a622-197">0</span><span class="sxs-lookup"><span data-stu-id="7a622-197">0</span></span> | <span data-ttu-id="7a622-198">Reservado</span><span class="sxs-lookup"><span data-stu-id="7a622-198">Reserved</span></span>
| <span data-ttu-id="7a622-199">[31-24]</span><span class="sxs-lookup"><span data-stu-id="7a622-199">[31-24]</span></span> | <br /><span data-ttu-id="7a622-200">0x01</span><span class="sxs-lookup"><span data-stu-id="7a622-200">0x01</span></span><br /><span data-ttu-id="7a622-201">0x02</span><span class="sxs-lookup"><span data-stu-id="7a622-201">0x02</span></span><br /><span data-ttu-id="7a622-202">0x03</span><span class="sxs-lookup"><span data-stu-id="7a622-202">0x03</span></span> | <span data-ttu-id="7a622-203">**Identificador de compilador**</span><span class="sxs-lookup"><span data-stu-id="7a622-203">**Compiler ID**</span></span><br /><span data-ttu-id="7a622-204">IAR</span><span class="sxs-lookup"><span data-stu-id="7a622-204">IAR</span></span><br /><span data-ttu-id="7a622-205">ARM</span><span class="sxs-lookup"><span data-stu-id="7a622-205">ARM</span></span><br /><span data-ttu-id="7a622-206">GNU</span><span class="sxs-lookup"><span data-stu-id="7a622-206">GNU</span></span> |


## <a name="module-linker-control-file"></a><span data-ttu-id="7a622-207">Archivo de control del vinculador del módulo</span><span class="sxs-lookup"><span data-stu-id="7a622-207">Module linker control file</span></span>

<span data-ttu-id="7a622-208">Al compilar un módulo, el preámbulo del módulo debe colocarse antes que cualquier otra sección de código.</span><span class="sxs-lookup"><span data-stu-id="7a622-208">When building a module, the module preamble must be placed before any other code section.</span></span> <span data-ttu-id="7a622-209">Un módulo se debe compilar con secciones de datos y código independiente de la posición.</span><span class="sxs-lookup"><span data-stu-id="7a622-209">A module must be built with position-independent code and data sections.</span></span> <span data-ttu-id="7a622-210">Los archivos del enlazador de ejemplo específicos del puerto se encuentran en el [apéndice](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="7a622-210">Port-specific example linker files are in the [appendix](appendix.md).</span></span>

## <a name="module-threadx-library"></a><span data-ttu-id="7a622-211">Biblioteca de módulos de ThreadX</span><span class="sxs-lookup"><span data-stu-id="7a622-211">Module ThreadX library</span></span>

<span data-ttu-id="7a622-212">Cada módulo debe vincularse a una biblioteca especial de ThreadX centrada en módulos.</span><span class="sxs-lookup"><span data-stu-id="7a622-212">Each module must link against a special, module-centric ThreadX library.</span></span> <span data-ttu-id="7a622-213">Esta biblioteca proporciona acceso a los servicios de ThreadX en el código residente.</span><span class="sxs-lookup"><span data-stu-id="7a622-213">This library provides access to ThreadX services in the resident code.</span></span> <span data-ttu-id="7a622-214">La mayor parte del acceso se realiza a través de los archivos ***txm_\*.c***.</span><span class="sxs-lookup"><span data-stu-id="7a622-214">Most of the access is accomplished via the ***txm_\*.c*** files.</span></span> <span data-ttu-id="7a622-215">El siguiente es un ejemplo de la llamada de acceso al módulo para la función de API de ThreadX **_tx_thread_relinquish_* _ (en _*_ \_txm_thread_relinquish.c\*\*\*\*).</span><span class="sxs-lookup"><span data-stu-id="7a622-215">The following is an example of the module access call for the ThreadX API function **_tx_thread_relinquish_* _ (in _*_\_txm_thread_relinquish.c\*\*\*\*).</span></span>

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

<span data-ttu-id="7a622-216">En este ejemplo, el puntero de función proporcionado por el administrador de módulos se usa para llamar a la función de distribución del administrador de módulos con el identificador asociado con el servicio ***tx_thread_relinquish***.</span><span class="sxs-lookup"><span data-stu-id="7a622-216">In this example, the function pointer supplied by the Module Manager is used to call the Module Manager dispatch function with the ID associated with the ***tx_thread_relinquish*** service.</span></span> <span data-ttu-id="7a622-217">Este servicio no toma ningún parámetro.</span><span class="sxs-lookup"><span data-stu-id="7a622-217">This service takes no parameters.</span></span>

## <a name="module-example"></a><span data-ttu-id="7a622-218">Ejemplo de módulo</span><span class="sxs-lookup"><span data-stu-id="7a622-218">Module example</span></span>

<span data-ttu-id="7a622-219">El siguiente es un ejemplo de la demostración estándar de ThreadX en forma de módulo.</span><span class="sxs-lookup"><span data-stu-id="7a622-219">The following is an example of the standard ThreadX demonstration in the form of a module.</span></span> <span data-ttu-id="7a622-220">Las principales diferencias entre la demostración estándar de ThreadX y la demostración del módulo son:</span><span class="sxs-lookup"><span data-stu-id="7a622-220">The main differences between the standard ThreadX demonstration and the module demonstration are.</span></span>

1. <span data-ttu-id="7a622-221">Reemplazo de ***tx_api.h** _ con _ *_txm_module.h_**</span><span class="sxs-lookup"><span data-stu-id="7a622-221">Replacement of ***tx_api.h** _ with _ *_txm_module.h_**</span></span>
2. <span data-ttu-id="7a622-222">Adición de **#define TXM_MODULE** antes de **_txm_module.h_**</span><span class="sxs-lookup"><span data-stu-id="7a622-222">Addition of **#define TXM_MODULE** prior to **_txm_module.h_**</span></span>
3. <span data-ttu-id="7a622-223">Reemplazo de ***main** _ y _ *tx_application_define** con **_demo_module_start_**</span><span class="sxs-lookup"><span data-stu-id="7a622-223">Replacement of ***main** _ and _ *tx_application_define** with **_demo_module_start_**</span></span>
4. <span data-ttu-id="7a622-224">Declaración de *punteros* a objetos de ThreadX en lugar de a los propios objetos.</span><span class="sxs-lookup"><span data-stu-id="7a622-224">Declaring *pointers* to ThreadX objects rather than the objects themselves.</span></span>

```c
/* Specify that this is a module! */
#define TXM_MODULE

/* Include the ThreadX module header. */
#include "txm_module.h"

/* Define constants. */
#define DEMO_STACK_SIZE         1024
#define DEMO_BYTE_POOL_SIZE     9120
#define DEMO_BLOCK_POOL_SIZE    100
#define DEMO_QUEUE_SIZE         100

/* Define the pool space in the bss section of the module. ULONG is used to
   get word alignment. */
   
ULONG                   demo_module_pool_space[DEMO_BYTE_POOL_SIZE / 4];

/* Define the ThreadX object control block pointers. */

TX_THREAD               *thread_0;
TX_THREAD               *thread_1;
TX_THREAD               *thread_2;
TX_THREAD               *thread_3;
TX_THREAD               *thread_4;
TX_THREAD               *thread_5;
TX_THREAD               *thread_6;
TX_THREAD               *thread_7;
TX_QUEUE                *queue_0;
TX_SEMAPHORE            *semaphore_0;
TX_MUTEX                *mutex_0;
TX_EVENT_FLAGS_GROUP    *event_flags_0;
TX_BYTE_POOL            *byte_pool_0;
TX_BLOCK_POOL           *block_pool_0;


/* Define the counters used in the demo application. */
ULONG       thread_0_counter;
ULONG       thread_1_counter;
ULONG       thread_1_messages_sent;
ULONG       thread_2_counter;
ULONG       thread_2_messages_received;
ULONG       thread_3_counter;
ULONG       thread_4_counter;
ULONG       thread_5_counter;
ULONG       thread_6_counter;
ULONG       thread_7_counter;
ULONG       semaphore_0_puts;
ULONG       event_0_sets;
ULONG       queue_0_sends;

/* Define thread prototypes. */

void    thread_0_entry(ULONG thread_input);
void    thread_1_entry(ULONG thread_input);
void    thread_2_entry(ULONG thread_input);
void    thread_3_and_4_entry(ULONG thread_input);
void    thread_5_entry(ULONG thread_input);
void    thread_6_and_7_entry(ULONG thread_input);

/* Define notify functions. */

void semaphore_0_notify(TX_SEMAPHORE *semaphore_ptr)
{
    if (semaphore_ptr == semaphore_0)
        semaphore_0_puts++;
}


void event_0_notify(TX_EVENT_FLAGS_GROUP *event_flag_group_ptr)
{
    if (event_flag_group_ptr == event_flags_0)
        event_0_sets++;
}


void queue_0_notify(TX_QUEUE *queue_ptr)
{
    if (queue_ptr == queue_0)
        queue_0_sends++;
}

/* Define the module start function. */
void demo_module_start(ULONG id)
{
    CHAR *pointer;

    /* Allocate all the objects. In memory protection mode,
        modules cannot allocate control blocks within their
        own memory area so they cannot corrupt the resident
        portion of ThreadX by corrupting the control block(s). */
    txm_module_object_allocate(&thread_0, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_1, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_2, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_3, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_4, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_5, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_6, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_7, sizeof(TX_THREAD));
    txm_module_object_allocate(&queue_0, sizeof(TX_QUEUE));
    txm_module_object_allocate(&semaphore_0, sizeof(TX_SEMAPHORE));
    txm_module_object_allocate(&mutex_0, sizeof(TX_MUTEX));
    txm_module_object_allocate(&event_flags_0, sizeof(TX_EVENT_FLAGS_GROUP));
    txm_module_object_allocate(&byte_pool_0, sizeof(TX_BYTE_POOL));
    txm_module_object_allocate(&block_pool_0, sizeof(TX_BLOCK_POOL));

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(byte_pool_0, "module byte pool 0",
        demo_module_pool_space, DEMO_BYTE_POOL_SIZE);

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 0. */
    tx_thread_create(thread_0, "module thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through
        a ThreadX message queue. It is also interesting to note that
        these threads have a time slice. */
    tx_thread_create(thread_1, "module thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack and create thread 2. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_2, "module thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX
        counting semaphore. An interesting thing here is that both threads
        share the same instruction area. */
    tx_thread_create(thread_3, "module thread 3",
        thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 4. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_4, "module thread 4",
        thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag which
        will be set by thread 0. */
    tx_thread_create(thread_5, "module thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(thread_6, "module thread 6",
        thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 7. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_7, "module thread 7",
        thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(queue_0, "module queue 0", TX_1_ULONG, pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Register queue send callback. */
    tx_queue_send_notify(queue_0, queue_0_notify);

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(semaphore_0, "module semaphore 0", 1);

    /* Register semaphore put callback. */
    tx_semaphore_put_notify(semaphore_0, semaphore_0_notify);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(event_flags_0, "module event flags 0");

    /* Register event flag set callback. */
    tx_event_flags_set_notify(event_flags_0, event_0_notify);

    /* Create the mutex used by thread 6 and 7 without priority
        inheritance. */
    tx_mutex_create(mutex_0, "module mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool. */
    tx_block_pool_create(block_pool_0, "module block pool 0",
        sizeof(ULONG), pointer, DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block. */
    tx_block_allocate(block_pool_0, (VOID **) &pointer,
        TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);

}

/* Define all the threads. */

void thread_0_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wake up thread 5. */
        status = tx_event_flags_set(event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_1_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sends messages to a queue shared by
       thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(queue_0, &thread_1_messages_sent,
            TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}

void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what
           we expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}

void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 3 and thread 4. As the loop
       below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;

    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(event_flags_0, 0x1, TX_OR_CLEAR,
                                        &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
       below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows that an
           owning thread may retrieve the mutex it owns multiple times. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually release ownership
           since it was obtained twice. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```

## <a name="building-modules"></a><span data-ttu-id="7a622-225">Compilación de módulos</span><span class="sxs-lookup"><span data-stu-id="7a622-225">Building Modules</span></span>

<span data-ttu-id="7a622-226">La compilación de un módulo depende de la cadena de herramientas utilizada.</span><span class="sxs-lookup"><span data-stu-id="7a622-226">Building a module is dependent on the tool chain being used.</span></span> <span data-ttu-id="7a622-227">Consulte el [apéndice](appendix.md) para ver ejemplos específicos de puertos.</span><span class="sxs-lookup"><span data-stu-id="7a622-227">See [appendix](appendix.md) for port-specific examples.</span></span> <span data-ttu-id="7a622-228">Entre las actividades comunes para todos los puertos se incluyen las siguientes:</span><span class="sxs-lookup"><span data-stu-id="7a622-228">Common activities to all ports include the following.</span></span>

- <span data-ttu-id="7a622-229">Compilación de una biblioteca de módulos</span><span class="sxs-lookup"><span data-stu-id="7a622-229">Building a module library</span></span>
- <span data-ttu-id="7a622-230">Creación de la aplicación de módulo</span><span class="sxs-lookup"><span data-stu-id="7a622-230">Building the module application</span></span>

<span data-ttu-id="7a622-231">Cada módulo debe tener un **txm_module_preamble** (configurado específicamente para el módulo) y la biblioteca de módulos (por ejemplo, **_tmx.a_**).</span><span class="sxs-lookup"><span data-stu-id="7a622-231">Each module is required to have a **txm_module_preamble** (setup specifically for the module) and the module library (for example, **_txm.a_**).</span></span>
