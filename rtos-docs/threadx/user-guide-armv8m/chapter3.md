---
title: 'Capítulo 3: API de ThreadX para ARMv8-M'
description: En este capítulo se describe la descripción de los servicios de ThreadX específicos de ARMv8-M.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14bdfab3d56476d52ba91f859cec4af4ab7f4bef
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377540"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a><span data-ttu-id="78f56-103">Capítulo 3: API de ThreadX para ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="78f56-103">Chapter 3  ThreadX APIs for ARMv8-M</span></span>

<span data-ttu-id="78f56-104">Este capítulo contiene una descripción de los servicios de ThreadX específicos de ARMv8-M en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="78f56-104">This chapter contains a description of the ARMv8-M-specific ThreadX services in alphabetic order.</span></span> <span data-ttu-id="78f56-105">Los nombres de los servicios están diseñados de modo que todos los servicios similares están agrupados.</span><span class="sxs-lookup"><span data-stu-id="78f56-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="78f56-106">En la sección "Valores devueltos" de las siguientes descripciones, los valores en **NEGRITA** no se ven afectados por la definición **TX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API. En cambio, los valores que no aparecen en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="78f56-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in non-bold are completely disabled.</span></span>

- <span data-ttu-id="78f56-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate): asigna una pila de subprocesos en la memoria segura.</span><span class="sxs-lookup"><span data-stu-id="78f56-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Allocate a thread stack in secure memory.</span></span>
- <span data-ttu-id="78f56-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free): libera la pila de subprocesos en la memoria segura</span><span class="sxs-lookup"><span data-stu-id="78f56-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Free thread stack in secure memory</span></span>

## <a name="tx_thread_secure_stack_allocate"></a><span data-ttu-id="78f56-109">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="78f56-109">tx_thread_secure_stack_allocate</span></span>

<span data-ttu-id="78f56-110">Asigna una pila de subprocesos en la memoria segura.</span><span class="sxs-lookup"><span data-stu-id="78f56-110">Allocate a thread stack in secure memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="78f56-111">Prototipo</span><span class="sxs-lookup"><span data-stu-id="78f56-111">Prototype</span></span>

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="78f56-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="78f56-112">Description</span></span>

<span data-ttu-id="78f56-113">Este servicio asigna una pila de stack_size bytes de tamaño en la memoria segura.</span><span class="sxs-lookup"><span data-stu-id="78f56-113">This service allocates a stack of size stack_size bytes in secure memory.</span></span> <span data-ttu-id="78f56-114">Se debe llamar a esta función para cada subproceso que llame a funciones seguras.</span><span class="sxs-lookup"><span data-stu-id="78f56-114">This function should be called for every thread that calls secure functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="78f56-115">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="78f56-115">Input Parameters</span></span>

- <span data-ttu-id="78f56-116">**thread_ptr**: puntero a un subproceso creado previamente.</span><span class="sxs-lookup"><span data-stu-id="78f56-116">**thread_ptr** Pointer to previously created thread.</span></span>

- <span data-ttu-id="78f56-117">**stack_size**: tamaño de la pila segura.</span><span class="sxs-lookup"><span data-stu-id="78f56-117">**stack_size** Size of secure stack.</span></span>

### <a name="return-values"></a><span data-ttu-id="78f56-118">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="78f56-118">Return Values</span></span>

- <span data-ttu-id="78f56-119">**TX_SUCCESS** (0x00): solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="78f56-119">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="78f56-120">**TX_SIZE_ERROR** (0x05): tamaño de la pila fuera del intervalo.</span><span class="sxs-lookup"><span data-stu-id="78f56-120">**TX_SIZE_ERROR** (0x05) Stack size out of range.</span></span>

- <span data-ttu-id="78f56-121">**TX_THREAD_ERROR** (0x0E): puntero del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="78f56-121">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="78f56-122">**TX_NO_MEMORY** (0x10): no se puede asignar memoria.</span><span class="sxs-lookup"><span data-stu-id="78f56-122">**TX_NO_MEMORY** (0x10) Unable to allocate memory.</span></span>

- <span data-ttu-id="78f56-123">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="78f56-123">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="78f56-124">**TX_FEATURE_NOT_ENABLED** (0Xff): el sistema se compiló para ejecutarse en modo seguro.</span><span class="sxs-lookup"><span data-stu-id="78f56-124">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="78f56-125">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="78f56-125">Allowed From</span></span>

<span data-ttu-id="78f56-126">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="78f56-126">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="78f56-127">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="78f56-127">Example</span></span>

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a><span data-ttu-id="78f56-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="78f56-128">See Also</span></span>

<span data-ttu-id="78f56-129">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="78f56-129">tx_thread_secure_stack_free</span></span>

##  <a name="tx_thread_secure_stack_free"></a><span data-ttu-id="78f56-130">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="78f56-130">tx_thread_secure_stack_free</span></span>

<span data-ttu-id="78f56-131">Libera la pila de subprocesos en la memoria segura.</span><span class="sxs-lookup"><span data-stu-id="78f56-131">Free a thread stack in secure memory.</span></span> 

### <a name="prototype"></a><span data-ttu-id="78f56-132">Prototipo</span><span class="sxs-lookup"><span data-stu-id="78f56-132">Prototype</span></span>

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="78f56-133">Descripción</span><span class="sxs-lookup"><span data-stu-id="78f56-133">Description</span></span>

<span data-ttu-id="78f56-134">Este servicio libera la pila segura de un subproceso en la memoria segura.</span><span class="sxs-lookup"><span data-stu-id="78f56-134">This service frees a thread's secure stack in secure memory.</span></span> <span data-ttu-id="78f56-135">Se debe llamar a esta función si un subproceso tiene una pila segura y cuando el subproceso ya no necesita llamar a funciones seguras o se elimina el subproceso.</span><span class="sxs-lookup"><span data-stu-id="78f56-135">This function should be called if a thread has a secure stack and when the thread no longer needs to call secure functions or the thread is deleted.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="78f56-136">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="78f56-136">Input Parameters</span></span>

- <span data-ttu-id="78f56-137">**thread_ptr**: puntero a un subproceso creado previamente.</span><span class="sxs-lookup"><span data-stu-id="78f56-137">**thread_ptr** Pointer to previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="78f56-138">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="78f56-138">Return Values</span></span>

- <span data-ttu-id="78f56-139">**TX_SUCCESS** (0x00): solicitud correcta.</span><span class="sxs-lookup"><span data-stu-id="78f56-139">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="78f56-140">**TX_THREAD_ERROR** (0x0E): puntero del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="78f56-140">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="78f56-141">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="78f56-141">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="78f56-142">**TX_FEATURE_NOT_ENABLED** (0Xff): el sistema se compiló para ejecutarse en modo seguro.</span><span class="sxs-lookup"><span data-stu-id="78f56-142">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="78f56-143">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="78f56-143">Allowed From</span></span>

<span data-ttu-id="78f56-144">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="78f56-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="78f56-145">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="78f56-145">Example</span></span>

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a><span data-ttu-id="78f56-146">Consulte también</span><span class="sxs-lookup"><span data-stu-id="78f56-146">See Also</span></span>

<span data-ttu-id="78f56-147">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="78f56-147">tx_thread_secure_stack_allocate</span></span>
