---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS ThreadX'
description: Este capítulo contiene una descripción de todos los servicios de Azure RTOS ThreadX en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 60ecc96df07b1f77b9b448814c4420133f3e2afc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814358"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a><span data-ttu-id="27c3f-103">Capítulo 4: Descripción de los servicios de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="27c3f-103">Chapter 4 - Description of Azure RTOS ThreadX Services</span></span>

<span data-ttu-id="27c3f-104">Este capítulo contiene una descripción de todos los servicios de Azure RTOS ThreadX en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="27c3f-104">This chapter contains a description of all Azure RTOS ThreadX services in alphabetic order.</span></span> <span data-ttu-id="27c3f-105">Sus nombres están diseñados de modo que todos los servicios similares están agrupados.</span><span class="sxs-lookup"><span data-stu-id="27c3f-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="27c3f-106">En la sección "Valores devueltos" de las siguientes descripciones, los valores en **NEGRITA** no se ven afectados por la definición **TX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API. En cambio, los valores que no aparecen en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="27c3f-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="27c3f-107">Además, un "**Sí**" bajo el título "**Adelantamiento posible**" indica que la llamada al servicio puede reanudar un subproceso de mayor prioridad, de forma que se adelanta al subproceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-107">In addition, a "**Yes**" listed under the "**Preemption Possible**" heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="27c3f-108">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-108">tx_block_allocate</span></span>

<span data-ttu-id="27c3f-109">Asignar un bloque de memoria de tamaño fijo</span><span class="sxs-lookup"><span data-stu-id="27c3f-109">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-110">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-110">Prototype</span></span>

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27c3f-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-111">Description</span></span>

<span data-ttu-id="27c3f-112">Este servicio asigna un bloque de memoria de tamaño fijo del grupo de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-112">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="27c3f-113">El tamaño real del bloque de memoria se determina durante la creación del grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-113">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-114">*Es importante asegurarse de que el código de la aplicación no escribe fuera del bloque de memoria asignado. Si esto ocurre, se daña un bloque de memoria adyacente (normalmente posterior). Los resultados son imprevisibles y a menudo graves.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-114">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-115">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-115">Parameters</span></span>

- <span data-ttu-id="27c3f-116">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-116">**pool_ptr**</span></span> <br><span data-ttu-id="27c3f-117">Puntero a un grupo de bloques de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-117">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="27c3f-118">**block_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-118">**block_ptr**</span></span> <br><span data-ttu-id="27c3f-119">Puntero a un puntero del bloque de destino.</span><span class="sxs-lookup"><span data-stu-id="27c3f-119">Pointer to a destination block pointer.</span></span> <span data-ttu-id="27c3f-120">Si la asignación es correcta, la dirección del bloque de memoria asignado se coloca donde señala este parámetro.</span><span class="sxs-lookup"><span data-stu-id="27c3f-120">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="27c3f-121">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27c3f-121">**wait_option**</span></span> <br><span data-ttu-id="27c3f-122">Define el comportamiento del servicio si no hay ningún bloque de memoria disponible.</span><span class="sxs-lookup"><span data-stu-id="27c3f-122">Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="27c3f-123">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="27c3f-123">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27c3f-124">**TX_NO_WAIT** (0x00000000): al seleccionar **TX_NO_WAIT**, se produce una devolución inmediata de este servicio, con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="27c3f-124">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="27c3f-125">*Esta es la única opción válida si se llama al servicio desde un elemento distinto de un _ _subproceso; por ejemplo, inicialización, temporizador o ISR*.</span><span class="sxs-lookup"><span data-stu-id="27c3f-125">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="27c3f-126">**TX_WAIT_FOREVER** (0xFFFFFFF): al seleccionar **TX_WAIT_FOREVER**, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya un bloque de memoria disponible.</span><span class="sxs-lookup"><span data-stu-id="27c3f-126">**TX_WAIT_FOREVER** (0xFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until a memory block is available.</span></span>
  - <span data-ttu-id="27c3f-127">*valor de tiempo de espera* (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando un bloque de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-127">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-128">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-128">Return Values</span></span>

- <span data-ttu-id="27c3f-129">**TX_SUCCESS** (0x00): bloque de memoria asignado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-129">**TX_SUCCESS**    (0x00)  Successful memory block allocation.</span></span>
- <span data-ttu-id="27c3f-130">**TX_DELETED** (0x01): el grupo de bloques de memoria se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-130">**TX_DELETED**    (0x01)  Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27c3f-131">**TX_NO_MEMORY** (0x10): el servicio no pudo asignar un bloque de memoria en el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-131">**TX_NO_MEMORY**  (0x10)  Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="27c3f-132">**TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="27c3f-132">**TX_WAIT_ABORTED**   (0x1A)  Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="27c3f-133">**TX_POOL_ERROR** (0x02): puntero del grupo de bloques de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-133">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="27c3f-134">**TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-134">**TX_WAIT_ERROR** (0x04)  A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="27c3f-135">**TX_PTR_ERROR** (0x03): puntero al puntero de destino no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-135">**TX_PTR_ERROR**  (0x03)  Invalid pointer to destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-136">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-136">Allowed From</span></span>

<span data-ttu-id="27c3f-137">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-137">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-138">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-138">Preemption Possible</span></span>

<span data-ttu-id="27c3f-139">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-140">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-140">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;

UINT status;

/* Allocate a memory block from my_pool. Assume that the pool has
already been created with a call to tx_block_pool_create. */

status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
  TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the address of
the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-141">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-141">See Also</span></span>

- <span data-ttu-id="27c3f-142">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-142">tx_block_pool_create</span></span>
- <span data-ttu-id="27c3f-143">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-143">tx_block_pool_delete</span></span>
- <span data-ttu-id="27c3f-144">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-144">tx_block_pool_info_get</span></span>
- <span data-ttu-id="27c3f-145">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-145">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-146">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-146">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-147">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-147">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="27c3f-148">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-148">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="27c3f-149">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-149">tx_block_pool_create</span></span>

<span data-ttu-id="27c3f-150">Crear un grupo de bloques de memoria de tamaño fijo</span><span class="sxs-lookup"><span data-stu-id="27c3f-150">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-151">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-151">Prototype</span></span>

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="27c3f-152">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-152">Description</span></span>

<span data-ttu-id="27c3f-153">Este servicio crea un grupo de bloques de memoria de tamaño fijo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-153">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="27c3f-154">El área de memoria especificada se divide en tantos bloques de memoria de tamaño fijo como sea posible mediante la siguiente fórmula:</span><span class="sxs-lookup"><span data-stu-id="27c3f-154">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>

<span data-ttu-id="27c3f-155">**total de bloques** = (**total de bytes**)/(**tamaño de bloque** + sizeof(void \*))</span><span class="sxs-lookup"><span data-stu-id="27c3f-155">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!NOTE]
><span data-ttu-id="27c3f-156">\*Cada bloque de memoria contiene un puntero de sobrecarga que es invisible para el usuario y se representa mediante "sizeof(void )" *en la fórmula anterior.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-156">\*Each memory block contains one pointer of overhead that is invisible to the user and is represented by the "sizeof(void *)" in the preceding formula.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-157">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-157">Parameters</span></span>

- <span data-ttu-id="27c3f-158">**pool_ptr**: puntero a un bloque de control del grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-158">**pool_ptr**  Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="27c3f-159">**name_ptr**: puntero al nombre del grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-159">**name_ptr**  Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="27c3f-160">**block_size**: número de bytes de cada bloque de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-160">**block_size**    Number of bytes in each memory block.</span></span>
- <span data-ttu-id="27c3f-161">**pool_start**: dirección de inicio del grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-161">**pool_start**    Starting address of the memory block pool.</span></span> <span data-ttu-id="27c3f-162">La dirección de inicio debe alinearse con el tamaño del tipo de datos ULONG.</span><span class="sxs-lookup"><span data-stu-id="27c3f-162">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="27c3f-163">**pool_size**: número total de bytes disponibles para el grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-163">**pool_size** Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-164">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-164">Return Values</span></span>

- <span data-ttu-id="27c3f-165">**TX_SUCCESS** (0x00): grupo de bloques de memoria creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-165">**TX_SUCCESS**    (0x00)  Successful memory block pool creation.</span></span>
- <span data-ttu-id="27c3f-166">**TX_POOL_ERROR** (0x02): puntero del grupo de bloques de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-166">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span> <span data-ttu-id="27c3f-167">El puntero tiene un valor NULL o el grupo ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-167">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="27c3f-168">**TX_PTR_ERROR** (0x03): dirección de inicio del grupo no válida.</span><span class="sxs-lookup"><span data-stu-id="27c3f-168">**TX_PTR_ERROR**  (0x03)  Invalid starting address of the pool.</span></span>
- <span data-ttu-id="27c3f-169">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-169">**TX_CALLER_ERROR**   (0x13)  Invalid caller of this service.</span></span>
- <span data-ttu-id="27c3f-170">**TX_SIZE_ERROR** (0x05): el tamaño del grupo no es válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-170">**TX_SIZE_ERROR** (0x05)  Size of pool is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-171">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-171">Allowed From</span></span>

<span data-ttu-id="27c3f-172">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-172">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-173">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-173">Preemption Possible</span></span>

<span data-ttu-id="27c3f-174">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-174">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-175">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-175">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT status;

/* Create a memory pool whose total size is 1000 bytes starting at
address 0x100000. Each block in this pool is defined to be 50 bytes
long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
  50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18 memory blocks
of 50 bytes each. The reason there are not 20 blocks in the pool is
because of the one overhead pointer associated with each block. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-176">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-176">See Also</span></span>

- <span data-ttu-id="27c3f-177">tx_block_allocate, tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-177">tx_block_allocate, tx_block_pool_delete</span></span>
- <span data-ttu-id="27c3f-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-179">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-179">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-180">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-180">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="27c3f-181">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-181">tx_block_pool_delete</span></span>

<span data-ttu-id="27c3f-182">Eliminar un grupo de bloques de memoria</span><span class="sxs-lookup"><span data-stu-id="27c3f-182">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-183">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-183">Prototype</span></span>

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-184">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-184">Description</span></span>

<span data-ttu-id="27c3f-185">Este servicio elimina el grupo de bloques de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-185">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="27c3f-186">Todos los subprocesos suspendidos en espera de un bloque de memoria de este grupo se reanudan y se les asigna un estado de devolución **TX_DELETED**.</span><span class="sxs-lookup"><span data-stu-id="27c3f-186">All threads suspended waiting for a memory block from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-187">*Es responsabilidad de la aplicación administrar el área de memoria asociada al grupo, que está disponible una vez que se complete este servicio. Además, la aplicación debe impedir el uso de un grupo eliminado o de sus bloques de memoria anteriores.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-187">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or its former memory blocks.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-188">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-188">Parameters</span></span>

- <span data-ttu-id="27c3f-189">**pool_ptr**: puntero a un grupo de bloques de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-189">**pool_ptr** Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-190">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-190">Return Values</span></span>

- <span data-ttu-id="27c3f-191">**TX_SUCCESS** (0x00): grupo de bloques de memoria eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-191">**TX_SUCCESS** (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="27c3f-192">**TX_POOL_ERROR** (0x02): puntero del grupo de bloques de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-192">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="27c3f-193">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-193">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-194">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-194">Allowed From</span></span>

<span data-ttu-id="27c3f-195">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-195">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-196">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-196">Preemption Possible</span></span>

<span data-ttu-id="27c3f-197">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-197">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-198">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-198">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a><span data-ttu-id="27c3f-199">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-199">See Also</span></span>

- <span data-ttu-id="27c3f-200">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-200">tx_block_allocate</span></span>
- <span data-ttu-id="27c3f-201">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-201">tx_block_pool_create</span></span>
- <span data-ttu-id="27c3f-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-203">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-203">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-204">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-204">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="27c3f-205">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-205">tx_block_pool_info_get</span></span>

<span data-ttu-id="27c3f-206">Recuperar información acerca de un grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="27c3f-206">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-207">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-207">Prototype</span></span>

```c
UINT tx_block_pool_info_get(
    TX_BLOCK_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *total_blocks,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BLOCK_POOL **next_pool);
```

### <a name="description"></a><span data-ttu-id="27c3f-208">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-208">Description</span></span>

<span data-ttu-id="27c3f-209">Este servicio recupera información sobre el grupo de bloques de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-209">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-210">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-210">Parameters</span></span>

- <span data-ttu-id="27c3f-211">**pool_ptr**: puntero a un grupo de bloques de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-211">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="27c3f-212">**name**: puntero al destino del puntero al nombre del grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="27c3f-212">**name**  Pointer to destination for the pointer to the block pool's name.</span></span>
- <span data-ttu-id="27c3f-213">**available**: puntero al destino del número de bloques disponibles en el grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-213">**available** Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="27c3f-214">**total_blocks**: puntero al destino del número total de bloques del grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-214">**total_blocks**  Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="27c3f-215">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="27c3f-215">**first_suspended**   Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="27c3f-216">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="27c3f-216">**suspended_count**   Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="27c3f-217">**next_pool**: puntero al destino del puntero del siguiente grupo de bloques creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-217">**next_pool** Pointer to destination for the pointer of the next created block pool.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-218">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-218">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-219">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-219">Return Values</span></span>

- <span data-ttu-id="27c3f-220">**TX_SUCCESS** (0x00): información del grupo de bloques recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-220">**TX_SUCCESS** (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="27c3f-221">**TX_POOL_ERROR** (0x02): puntero del grupo de bloques de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-221">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-222">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-222">Allowed From</span></span>

<span data-ttu-id="27c3f-223">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-223">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-224">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-224">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
CHAR *name;
ULONG available;
ULONG total_blocks;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BLOCK_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
  &available,&total_blocks,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-225">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-225">See Also</span></span>

- <span data-ttu-id="27c3f-226">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-226">tx_block_allocate</span></span>
- <span data-ttu-id="27c3f-227">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-227">tx_block_pool_create</span></span>
- <span data-ttu-id="27c3f-228">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-228">tx_block_pool_delete</span></span>
- <span data-ttu-id="27c3f-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-230">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-230">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-231">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-231">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="27c3f-232">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-232">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="27c3f-233">Obtener información acerca del rendimiento de un grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="27c3f-233">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-234">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-234">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="27c3f-235">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-235">Description</span></span>

<span data-ttu-id="27c3f-236">Este servicio recupera información sobre el rendimiento del grupo de bloques de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-236">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-237">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-237">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-238">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-238">Parameters</span></span>

- <span data-ttu-id="27c3f-239">**pool_ptr**: puntero a un grupo de bloques de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-239">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="27c3f-240">**allocates**: puntero al destino del número de solicitudes de asignación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-240">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="27c3f-241">**releases**: puntero al destino del número de solicitudes de liberación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-241">**releases**  Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="27c3f-242">**suspensions**: puntero al destino del número de suspensiones de asignación de subprocesos de este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-242">**suspensions**   Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="27c3f-243">**timeouts**: puntero al destino del número de tiempos de espera de las suspensiones de asignación de este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-243">**timeouts**  Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

>[!NOTE]
> <span data-ttu-id="27c3f-244">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-244">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-245">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-245">Return Values</span></span>

- <span data-ttu-id="27c3f-246">**TX_SUCCESS** (0x00): rendimiento del grupo de bloques obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-246">**TX_SUCCESS**    (0x00)  Successful block pool performance get.</span></span>
- <span data-ttu-id="27c3f-247">**TX_PTR_ERROR** (0x03): puntero del grupo de bloques no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-247">**TX_PTR_ERROR**  (0x03)  Invalid block pool pointer.</span></span>
- <span data-ttu-id="27c3f-248">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-248">**TX_FEATURE_NOT_ENABLED**    (0xFF)  The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-249">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-249">Allowed From</span></span>

<span data-ttu-id="27c3f-250">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-250">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-251">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-251">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created block
pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
  &releases,
  &suspensions,
  &timeouts);

/* If status is TX_SUCCESS the performance information was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-252">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-252">See Also</span></span>

- <span data-ttu-id="27c3f-253">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-253">tx_block_allocate</span></span>
- <span data-ttu-id="27c3f-254">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-254">tx_block_pool_create</span></span>
- <span data-ttu-id="27c3f-255">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-255">tx_block_pool_delete</span></span>
- <span data-ttu-id="27c3f-256">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-256">tx_block_pool_info_get</span></span>
- <span data-ttu-id="27c3f-257">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-257">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-258">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-258">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-259">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-259">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="27c3f-260">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-260">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="27c3f-261">Obtener información acerca del rendimiento del sistema de un grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="27c3f-261">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-262">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-262">Prototype</span></span>

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27c3f-263">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-263">Description</span></span>

<span data-ttu-id="27c3f-264">Este servicio recupera información sobre el rendimiento de todos los grupos de bloques de memoria de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-264">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-265">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-265">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-266">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-266">Parameters</span></span>

- <span data-ttu-id="27c3f-267">**allocates**: puntero al destino del número total de solicitudes de asignación realizadas en todos los grupos de bloques.</span><span class="sxs-lookup"><span data-stu-id="27c3f-267">**allocates** Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="27c3f-268">**releases**: puntero al destino del número total de solicitudes de liberación realizadas en todos los grupos de bloques.</span><span class="sxs-lookup"><span data-stu-id="27c3f-268">**releases**  Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="27c3f-269">**suspensions**: puntero al destino del número total de suspensiones de asignación de subprocesos de todos los grupos de bloques.</span><span class="sxs-lookup"><span data-stu-id="27c3f-269">**suspensions**   Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="27c3f-270">**timeouts**: puntero al destino del número total de tiempos de espera de las suspensiones de asignación de todos los grupos de bloques.</span><span class="sxs-lookup"><span data-stu-id="27c3f-270">**timeouts**  Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-271">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-271">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-272">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-272">Return Values</span></span>

- <span data-ttu-id="27c3f-273">**TX_SUCCESS** (0x00): rendimiento del sistema del grupo de bloques obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-273">**TX_SUCCESS** (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="27c3f-274">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-275">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-275">Allowed From</span></span>

<span data-ttu-id="27c3f-276">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-277">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-277">Example</span></span>

```c
ULONG       allocates;
ULONG       releases;
ULONG       suspensions;
ULONG       timeouts;

/* Retrieve performance information on all the block pools in
the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
    &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-278">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-278">See Also</span></span>

- <span data-ttu-id="27c3f-279">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-279">tx_block_allocate</span></span>
- <span data-ttu-id="27c3f-280">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-280">tx_block_pool_create</span></span>
- <span data-ttu-id="27c3f-281">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-281">tx_block_pool_delete</span></span>
- <span data-ttu-id="27c3f-282">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-282">tx_block_pool_info_get</span></span>
- <span data-ttu-id="27c3f-283">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-283">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-284">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-284">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="27c3f-285">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-285">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="27c3f-286">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-286">tx_block_pool_prioritize</span></span>

<span data-ttu-id="27c3f-287">Clasificar por orden de prioridad la lista de suspensiones de un grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="27c3f-287">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-288">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-288">Prototype</span></span>

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-289">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-289">Description</span></span>

<span data-ttu-id="27c3f-290">Este servicio coloca el subproceso de prioridad más alta suspendido para un bloque de memoria de este grupo al principio de la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-290">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="27c3f-291">Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.</span><span class="sxs-lookup"><span data-stu-id="27c3f-291">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-292">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-292">Parameters</span></span>

- <span data-ttu-id="27c3f-293">**pool_ptr**: puntero a un bloque de control del grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-293">**pool_ptr** Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-294">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-294">Return Values</span></span>

- <span data-ttu-id="27c3f-295">**TX_SUCCESS** (0x00): grupo de bloques clasificado por orden de prioridad correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-295">**TX_SUCCESS** (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="27c3f-296">**TX_POOL_ERROR** (0x02): puntero del grupo de bloques de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-296">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-297">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-297">Allowed From</span></span>

<span data-ttu-id="27c3f-298">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-298">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-299">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-299">Preemption Possible</span></span>

<span data-ttu-id="27c3f-300">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-300">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-301">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-301">Example</span></span>
```c
TX_BLOCK_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_block_release call will wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-302">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-302">See Also</span></span>

- <span data-ttu-id="27c3f-303">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-303">tx_block_allocate</span></span>
- <span data-ttu-id="27c3f-304">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-304">tx_block_pool_create</span></span>
- <span data-ttu-id="27c3f-305">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-305">tx_block_pool_delete</span></span>
- <span data-ttu-id="27c3f-306">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-306">tx_block_pool_info_get</span></span>
- <span data-ttu-id="27c3f-307">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-307">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-308">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-308">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-309">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-309">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="27c3f-310">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-310">tx_block_release</span></span>

<span data-ttu-id="27c3f-311">Liberar un bloque de memoria de tamaño fijo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-311">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-312">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-312">Prototype</span></span>

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a><span data-ttu-id="27c3f-313">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-313">Description</span></span>

<span data-ttu-id="27c3f-314">Este servicio libera un bloque previamente asignado a su grupo de memoria asociado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-314">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="27c3f-315">Si hay uno o más subprocesos suspendidos en espera de bloques de memoria de este grupo, el primer subproceso suspendido recibe este bloque de memoria y se reanuda.</span><span class="sxs-lookup"><span data-stu-id="27c3f-315">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="27c3f-316">*La aplicación debe impedir el uso de un área del bloque de memoria tras haberse liberado al grupo.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-316">*The application must prevent using a memory block area after it has been released back to the pool.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-317">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-317">Parameters</span></span>

- <span data-ttu-id="27c3f-318">**block_ptr**: puntero al bloque de memoria asignado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-318">**block_ptr** Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-319">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-319">Return Values</span></span>

- <span data-ttu-id="27c3f-320">**TX_SUCCESS** (0x00): bloque de memoria liberado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-320">**TX_SUCCESS** (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="27c3f-321">**TX_PTR_ERROR** (0x03): puntero al bloque de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-321">**TX_PTR_ERROR** (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-322">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-322">Allowed From</span></span>

<span data-ttu-id="27c3f-323">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-323">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-324">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-324">Preemption Possible</span></span>

<span data-ttu-id="27c3f-325">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-325">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-326">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-326">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;
UINT status;

/* Release a memory block back to my_pool. Assume that the
pool has been created and the memory block has been
allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
to by memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-327">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-327">See Also</span></span>

- <span data-ttu-id="27c3f-328">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-328">tx_block_allocate</span></span>
- <span data-ttu-id="27c3f-329">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-329">tx_block_pool_create</span></span>
- <span data-ttu-id="27c3f-330">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-330">tx_block_pool_delete</span></span>
- <span data-ttu-id="27c3f-331">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-331">tx_block_pool_info_get</span></span>
- <span data-ttu-id="27c3f-332">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-332">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-333">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-333">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-334">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-334">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="27c3f-335">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-335">tx_byte_allocate</span></span>

<span data-ttu-id="27c3f-336">Asignar bytes de memoria</span><span class="sxs-lookup"><span data-stu-id="27c3f-336">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-337">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-337">Prototype</span></span>

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27c3f-338">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-338">Description</span></span>

<span data-ttu-id="27c3f-339">Este servicio asigna el número especificado de bytes del grupo de bytes de memoria indicado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-339">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-340">*Es importante asegurarse de que el código de la aplicación no escribe fuera del bloque de memoria asignado. Si esto ocurre, se daña un bloque de memoria adyacente (normalmente posterior). Los resultados son imprevisibles y a menudo graves.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-340">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-341">*El rendimiento de este servicio es una función del tamaño del bloque y la cantidad de fragmentación del grupo. Por lo tanto, este servicio no se debe utilizar durante los subprocesos de ejecución urgentes.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-341">*The performance of this service is a function of the block size and the amount of fragmentation in the pool. Hence, this service should not be used during time-critical threads of execution.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-342">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-342">Parameters</span></span>

- <span data-ttu-id="27c3f-343">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-343">**pool_ptr**</span></span> <br><span data-ttu-id="27c3f-344">Puntero a un grupo de bloques de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-344">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="27c3f-345">**memory_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-345">**memory_ptr**</span></span> <br><span data-ttu-id="27c3f-346">Puntero a un puntero de la memoria de destino.</span><span class="sxs-lookup"><span data-stu-id="27c3f-346">Pointer to a destination memory pointer.</span></span> <span data-ttu-id="27c3f-347">Si la asignación es correcta, la dirección del área de memoria asignada se coloca donde señala este parámetro.</span><span class="sxs-lookup"><span data-stu-id="27c3f-347">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="27c3f-348">**memory_size**</span><span class="sxs-lookup"><span data-stu-id="27c3f-348">**memory_size**</span></span> <br><span data-ttu-id="27c3f-349">Número de bytes solicitados.</span><span class="sxs-lookup"><span data-stu-id="27c3f-349">Number of bytes requested.</span></span>
- <span data-ttu-id="27c3f-350">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27c3f-350">**wait_option**</span></span> <br><span data-ttu-id="27c3f-351">Define el comportamiento del servicio si no hay suficiente memoria disponible.</span><span class="sxs-lookup"><span data-stu-id="27c3f-351">Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="27c3f-352">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="27c3f-352">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27c3f-353">**TX_NO_WAIT** (0x00000000): al seleccionar **TX_NO_WAIT**, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="27c3f-353">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27c3f-354">*Esta es la única opción válida si se llama al servicio desde la inicialización.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-354">*This is the only valid option if the service is called from initialization.*</span></span>
  - <span data-ttu-id="27c3f-355">**TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar **TX_WAIT_FOREVER**, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya suficiente memoria disponible.</span><span class="sxs-lookup"><span data-stu-id="27c3f-355">**TX_WAIT_FOREVER** 0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until enough memory is available.</span></span>
  - <span data-ttu-id="27c3f-356">*valor de tiempo de espera* (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-356">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-357">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-357">Return Values</span></span>

- <span data-ttu-id="27c3f-358">**TX_SUCCESS** (0x00): memoria asignada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-358">**TX_SUCCESS** (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="27c3f-359">**TX_DELETED** (0x01): el grupo de memoria se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-359">**TX_DELETED** (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27c3f-360">**TX_NO_MEMORY** (0x10) :el servicio no pudo asignar la memoria en el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-360">**TX_NO_MEMORY** (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="27c3f-361">**TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="27c3f-361">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27c3f-362">**TX_POOL_ERROR** (0x02): puntero del grupo de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-362">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="27c3f-363">**TX_PTR_ERROR** (0x03): puntero al puntero de destino no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-363">**TX_PTR_ERROR** (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="27c3f-364">**TX_SIZE_ERROR** (0x05): el tamaño solicitado es cero o mayor que el grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-364">**TX_SIZE_ERROR** (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="27c3f-365">**TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-365">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="27c3f-366">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-366">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-367">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-367">Allowed From</span></span>

<span data-ttu-id="27c3f-368">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-368">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-369">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-369">Preemption Possible</span></span>

<span data-ttu-id="27c3f-370">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-370">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-371">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-371">Example</span></span>
```c
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT status;
/* Allocate a 112 byte memory area from my_pool. Assume
that the pool has already been created with a call to
tx_byte_pool_create. */
status = tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
    112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
address of the allocated memory area. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-372">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-372">See Also</span></span>

- <span data-ttu-id="27c3f-373">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-373">tx_byte_pool_create</span></span>
- <span data-ttu-id="27c3f-374">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-374">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27c3f-375">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-375">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27c3f-376">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-376">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-377">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-377">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-378">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-378">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27c3f-379">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-379">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="27c3f-380">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-380">tx_byte_pool_create</span></span>

<span data-ttu-id="27c3f-381">Crear un grupo de bytes de memoria</span><span class="sxs-lookup"><span data-stu-id="27c3f-381">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-382">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-382">Prototype</span></span>

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="27c3f-383">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-383">Description</span></span>

<span data-ttu-id="27c3f-384">Este servicio crea un grupo de bytes de memoria en el área especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-384">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="27c3f-385">En un principio, el grupo consta básicamente de un bloque libre muy grande.</span><span class="sxs-lookup"><span data-stu-id="27c3f-385">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="27c3f-386">Sin embargo, el grupo se divide en bloques más pequeños a medida que se realizan asignaciones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-386">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-387">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-387">Parameters</span></span>

- <span data-ttu-id="27c3f-388">**pool_ptr**: puntero a un bloque de control del grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-388">**pool_ptr** Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="27c3f-389">**name_ptr**: puntero al nombre del grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-389">**name_ptr** Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="27c3f-390">**pool_start**: dirección de inicio del grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-390">**pool_start** Starting address of the memory pool.</span></span> <span data-ttu-id="27c3f-391">La dirección de inicio debe alinearse con el tamaño del tipo de datos ULONG.</span><span class="sxs-lookup"><span data-stu-id="27c3f-391">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="27c3f-392">**pool_size**: número total de bytes disponibles para el grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-392">**pool_size** Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-393">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-393">Return Values</span></span>

- <span data-ttu-id="27c3f-394">**TX_SUCCESS** (0x00): grupo de memoria creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-394">**TX_SUCCESS** (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="27c3f-395">**TX_POOL_ERROR** (0x02): puntero del grupo de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-395">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="27c3f-396">El puntero tiene un valor NULL o el grupo ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-396">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="27c3f-397">**TX_PTR_ERROR** (0x03): dirección de inicio del grupo no válida.</span><span class="sxs-lookup"><span data-stu-id="27c3f-397">**TX_PTR_ERROR** (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="27c3f-398">**TX_SIZE_ERROR** (0x05): el tamaño del grupo no es válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-398">**TX_SIZE_ERROR** (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="27c3f-399">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-399">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-400">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-400">Allowed From</span></span>

<span data-ttu-id="27c3f-401">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-401">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-402">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-402">Preemption Possible</span></span>

<span data-ttu-id="27c3f-403">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-403">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-404">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-404">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Create a memory pool whose total size is 2000 bytes
starting at address 0x500000. */
status = tx_byte_pool_create(&my_pool, "my_pool_name",
    (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
allocating memory. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-405">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-405">See Also</span></span>

- <span data-ttu-id="27c3f-406">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-406">tx_byte_allocate</span></span>
- <span data-ttu-id="27c3f-407">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-407">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27c3f-408">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-408">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27c3f-409">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-409">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-410">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-410">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-411">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-411">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27c3f-412">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-412">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="27c3f-413">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-413">tx_byte_pool_delete</span></span>

<span data-ttu-id="27c3f-414">Eliminar un grupo de bytes de memoria</span><span class="sxs-lookup"><span data-stu-id="27c3f-414">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-415">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-415">Prototype</span></span>

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-416">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-416">Description</span></span>

<span data-ttu-id="27c3f-417">Este servicio elimina el grupo de bytes de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-417">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="27c3f-418">Todos los subprocesos suspendidos en espera de memoria de este grupo se reanudan y se les asigna un estado de devolución **TX_DELETED**.</span><span class="sxs-lookup"><span data-stu-id="27c3f-418">All threads suspended waiting for memory from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-419">*Es responsabilidad de la aplicación administrar el área de memoria asociada con el grupo, que está disponible una vez que se complete este servicio. Además, la aplicación debe impedir el uso de un grupo eliminado o de la memoria asignada previamente desde este.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-419">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or memory previously allocated from it.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-420">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-420">Parameters</span></span>

- <span data-ttu-id="27c3f-421">**pool_ptr**: puntero a un grupo de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-421">**pool_ptr** Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-422">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-422">Return Values</span></span>

- <span data-ttu-id="27c3f-423">**TX_SUCCESS** (0x00): grupo de memoria eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-423">**TX_SUCCESS** (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="27c3f-424">**TX_POOL_ERROR** (0x02): puntero del grupo de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-424">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="27c3f-425">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-425">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-426">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-426">Allowed From</span></span>

<span data-ttu-id="27c3f-427">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-427">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-428">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-428">Preemption Possible</span></span>

<span data-ttu-id="27c3f-429">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-429">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-430">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-430">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-431">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-431">See Also</span></span>

- <span data-ttu-id="27c3f-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-432">tx_byte_allocate</span></span>
- <span data-ttu-id="27c3f-433">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-433">tx_byte_pool_create</span></span>
- <span data-ttu-id="27c3f-434">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-434">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27c3f-435">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-435">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-436">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-436">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-437">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-437">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27c3f-438">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-438">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="27c3f-439">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-439">tx_byte_pool_info_get</span></span>

<span data-ttu-id="27c3f-440">Recuperar la información acerca de un grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="27c3f-440">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-441">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-441">Prototype</span></span>

```c
UINT tx_byte_pool_info_get(
    TX_BYTE_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *fragments,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BYTE_POOL **next_pool);
```

### <a name="description"></a><span data-ttu-id="27c3f-442">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-442">Description</span></span>

<span data-ttu-id="27c3f-443">Este servicio recupera información sobre el grupo de bytes de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-443">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-444">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-444">Parameters</span></span>

- <span data-ttu-id="27c3f-445">**pool_ptr**: puntero a un grupo de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-445">**pool_ptr** Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="27c3f-446">**name**: puntero al destino del puntero al nombre del grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-446">**name** Pointer to destination for the pointer to the byte pool's name.</span></span>
- <span data-ttu-id="27c3f-447">**available**: puntero al destino del número de bytes disponibles en el grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-447">**available** Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="27c3f-448">**fragments**: puntero al destino del número total de fragmentos de memoria del grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-448">**fragments** Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="27c3f-449">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-449">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="27c3f-450">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-450">**suspended_count** Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="27c3f-451">**next_pool**: puntero al destino del puntero del siguiente grupo de bytes creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-451">**next_pool** Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-452">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-452">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-453">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-453">Return Values</span></span>

- <span data-ttu-id="27c3f-454">**TX_SUCCESS** (0x00): información del grupo recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-454">**TX_SUCCESS** (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="27c3f-455">**TX_POOL_ERROR** (0x02): puntero del grupo de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-455">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-456">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-456">Allowed From</span></span>

<span data-ttu-id="27c3f-457">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-457">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-458">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-458">Preemption Possible</span></span>

<span data-ttu-id="27c3f-459">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-459">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-460">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-460">Example</span></span>

```c
TX_BYTE_POOL my_pool;
CHAR *name;
ULONG available;
ULONG fragments;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BYTE_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_byte_pool_info_get(&my_pool, &name,
  &available, &fragments,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-461">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-461">See Also</span></span>

- <span data-ttu-id="27c3f-462">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-462">tx_byte_allocate</span></span>
- <span data-ttu-id="27c3f-463">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-463">tx_byte_pool_create</span></span>
- <span data-ttu-id="27c3f-464">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-464">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27c3f-465">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-465">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-466">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-466">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-467">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-467">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27c3f-468">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-468">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="27c3f-469">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-469">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="27c3f-470">Obtener información acerca del rendimiento de un grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="27c3f-470">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-471">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-471">Prototype</span></span>

```c
UINT tx_byte_pool_performance_info_get(
    TX_BYTE_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *fragments_searched, 
    ULONG *merges, 
    ULONG *splits,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27c3f-472">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-472">Description</span></span>

<span data-ttu-id="27c3f-473">Este servicio recupera información sobre el rendimiento del grupo de bytes de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-473">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-474">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-474">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-475">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-475">Parameters</span></span>

- <span data-ttu-id="27c3f-476">**pool_ptr**: puntero a un grupo de bytes de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-476">**pool_ptr** Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="27c3f-477">**allocates**: puntero al destino del número de solicitudes de asignación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-477">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="27c3f-478">**releases**: puntero al destino del número de solicitudes de liberación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-478">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="27c3f-479">**fragments_searched**: puntero al destino del número de fragmentos de memoria interna buscados durante las solicitudes de asignación en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-479">**fragments_searched** Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="27c3f-480">**merges**: puntero al destino del número de bloques de memoria interna combinados durante las solicitudes de asignación en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-480">**merges** Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="27c3f-481">**splits**: puntero al destino del número de divisiones de bloques de memoria interna (fragmentos) creados durante las solicitudes de asignación en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-481">**splits** Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="27c3f-482">**suspensions**: puntero al destino del número de suspensiones de asignación de subprocesos de este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-482">**suspensions** Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="27c3f-483">**timeouts**: puntero al destino del número de tiempos de espera de las suspensiones de asignación de este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-483">**timeouts** Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-484">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-484">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-485">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-485">Return Values</span></span>

- <span data-ttu-id="27c3f-486">**TX_SUCCESS**: (0x00) obtención correcta del rendimiento del grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-486">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="27c3f-487">**TX_PTR_ERROR** (0x03): puntero del grupo de bytes no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-487">**TX_PTR_ERROR** (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="27c3f-488">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-488">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-489">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-489">Allowed From</span></span>

<span data-ttu-id="27c3f-490">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-490">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-491">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-491">Example</span></span>

```c
TX_BYTE_POOL my_pool;
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created byte
pool. */
status = tx_byte_pool_performance_info_get(&my_pool,
  &fragments_searched,
  &merges, &splits,
  &allocates, &releases,
  &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="27c3f-492">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-492">See Also</span></span>

- <span data-ttu-id="27c3f-493">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-493">tx_byte_allocate</span></span>
- <span data-ttu-id="27c3f-494">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-494">tx_byte_pool_create</span></span>
- <span data-ttu-id="27c3f-495">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-495">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27c3f-496">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-496">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27c3f-497">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-497">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-498">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-498">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27c3f-499">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-499">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="27c3f-500">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-500">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="27c3f-501">Obtener información acerca del rendimiento del sistema de un grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="27c3f-501">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-502">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-502">Prototype</span></span>

```c
UINT tx_byte_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *fragments_searched, 
    ULONG *merges,
    ULONG *splits, 
    ULONG *suspensions, 
    ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="27c3f-503">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-503">Description</span></span>

<span data-ttu-id="27c3f-504">Este servicio recupera información sobre el rendimiento de todos los grupos de bytes de memoria del sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-504">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-505">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-505">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-506">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-506">Parameters</span></span>

- <span data-ttu-id="27c3f-507">**allocates**: puntero al destino del número de solicitudes de asignación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-507">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="27c3f-508">**releases**: puntero al destino del número de solicitudes de liberación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-508">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="27c3f-509">**fragments_searched**: puntero al destino del número total de fragmentos de memoria interna buscados durante las solicitudes de asignación en todos los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-509">**fragments_searched** Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="27c3f-510">**merges**: puntero al destino del número total de bloques de memoria interna combinados durante las solicitudes de asignación en todos los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-510">**merges** Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="27c3f-511">**splits**: puntero al destino del número total de divisiones de los bloques de memoria interna (fragmentos) creados durante las solicitudes de asignación en todos los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-511">**splits** Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="27c3f-512">**suspensions**: puntero al destino del número total de suspensiones de asignación de subprocesos en todos los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-512">**suspensions** Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="27c3f-513">**timeouts**: puntero al destino del número total de tiempos de espera de las suspensiones de asignación de todos los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-513">**timeouts** Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-514">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-514">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-515">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-515">Return Values</span></span>

- <span data-ttu-id="27c3f-516">**TX_SUCCESS**: (0x00) obtención correcta del rendimiento del grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-516">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="27c3f-517">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-517">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-518">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-518">Allowed From</span></span>

 <span data-ttu-id="27c3f-519">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-519">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-520">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-520">Example</span></span>

```c
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all byte pools in the
system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
  &merges, &splits, &allocates, &releases,
  &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-521">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-521">See Also</span></span>

- <span data-ttu-id="27c3f-522">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-522">tx_byte_allocate</span></span>
- <span data-ttu-id="27c3f-523">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-523">tx_byte_pool_create</span></span>
- <span data-ttu-id="27c3f-524">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-524">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27c3f-525">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-525">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27c3f-526">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-526">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-527">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-527">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27c3f-528">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-528">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="27c3f-529">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-529">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="27c3f-530">Clasificar por orden de prioridad la lista de suspensiones de un grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="27c3f-530">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-531">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-531">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="27c3f-532">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-532">Description</span></span>

<span data-ttu-id="27c3f-533">Este servicio coloca el subproceso de prioridad más alta suspendido para la memoria de este grupo al principio de la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-533">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="27c3f-534">Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.</span><span class="sxs-lookup"><span data-stu-id="27c3f-534">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-535">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-535">Parameters</span></span>

- <span data-ttu-id="27c3f-536">**pool_ptr**: puntero a un bloque de control del grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-536">**pool_ptr** Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-537">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-537">Return Values</span></span>

- <span data-ttu-id="27c3f-538">**TX_SUCCESS** (0x00): grupo de memoria clasificado por orden de prioridad correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-538">**TX_SUCCESS** (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="27c3f-539">**TX_POOL_ERROR** (0x02): puntero del grupo de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-539">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-540">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-540">Allowed From</span></span>

<span data-ttu-id="27c3f-541">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-542">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-542">Preemption Possible</span></span>

<span data-ttu-id="27c3f-543">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-543">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-544">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-544">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_byte_release call will wake up this thread,
if there is enough memory to satisfy its request. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-545">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-545">See Also</span></span>

- <span data-ttu-id="27c3f-546">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-546">tx_byte_allocate</span></span>
- <span data-ttu-id="27c3f-547">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-547">tx_byte_pool_create</span></span>
- <span data-ttu-id="27c3f-548">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-548">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27c3f-549">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-549">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27c3f-550">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-550">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-551">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-551">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-552">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-552">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="27c3f-553">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27c3f-553">tx_byte_release</span></span>

<span data-ttu-id="27c3f-554">Liberar bytes de vuelta al grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="27c3f-554">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-555">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-555">Prototype</span></span>

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-556">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-556">Description</span></span>

<span data-ttu-id="27c3f-557">Este servicio libera un área de memoria previamente asignada a su grupo asociado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-557">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="27c3f-558">Si hay uno o más subprocesos suspendidos en espera de memoria de este grupo, cada subproceso suspendido recibe memoria y se reanuda hasta que esta se agote o no haya más subprocesos suspendidos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-558">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="27c3f-559">Este proceso de asignación de memoria a los subprocesos suspendidos siempre comienza con el subproceso que se suspendió primero.</span><span class="sxs-lookup"><span data-stu-id="27c3f-559">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-560">*La aplicación debe impedir el uso del área de memoria una vez que se libera.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-560">*The application must prevent using the memory area after it is released.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-561">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-561">Parameters</span></span>

- <span data-ttu-id="27c3f-562">**memory_ptr**: puntero al área de memoria asignada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-562">**memory_ptr** Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-563">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-563">Return Values</span></span>

- <span data-ttu-id="27c3f-564">**TX_SUCCESS** (0x00): memoria liberada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-564">**TX_SUCCESS** (0x00) Successful memory release.</span></span>
- <span data-ttu-id="27c3f-565">**TX_PTR_ERROR** (0x03): puntero del área de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-565">**TX_PTR_ERROR** (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="27c3f-566">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-566">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-567">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-567">Allowed From</span></span>

<span data-ttu-id="27c3f-568">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-568">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-569">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-569">Preemption Possible</span></span>

<span data-ttu-id="27c3f-570">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-570">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-571">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-571">Example</span></span>

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-572">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-572">See Also</span></span>

- <span data-ttu-id="27c3f-573">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27c3f-573">tx_byte_allocate</span></span>
- <span data-ttu-id="27c3f-574">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-574">tx_byte_pool_create</span></span>
- <span data-ttu-id="27c3f-575">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-575">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27c3f-576">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-576">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27c3f-577">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-577">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27c3f-578">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-578">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-579">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-579">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="27c3f-580">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-580">tx_event_flags_create</span></span>

<span data-ttu-id="27c3f-581">Crear un grupo de marcas de eventos</span><span class="sxs-lookup"><span data-stu-id="27c3f-581">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-582">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-582">Prototype</span></span>

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-583">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-583">Description</span></span>

<span data-ttu-id="27c3f-584">Este servicio crea un grupo de 32 marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-584">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="27c3f-585">Estas 32 marcas de eventos del grupo se inicializan en cero.</span><span class="sxs-lookup"><span data-stu-id="27c3f-585">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="27c3f-586">Cada marca de evento se representa con un solo bit.</span><span class="sxs-lookup"><span data-stu-id="27c3f-586">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-587">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-587">Parameters</span></span>

- <span data-ttu-id="27c3f-588">**group_ptr**: puntero a un bloque de control del grupo de marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-588">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="27c3f-589">**name_ptr**: puntero al nombre del grupo de marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-589">**name_ptr** Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-590">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-590">Return Values</span></span>

- <span data-ttu-id="27c3f-591">**TX_SUCCESS** (0x00): grupo de eventos creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-591">**TX_SUCCESS** (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="27c3f-592">**TX_GROUP_ERROR** (0x06): puntero del grupo de eventos no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-592">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="27c3f-593">El puntero es **NULL** o el grupo de eventos ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-593">Either the pointer is **NULL** or the event group is already created.</span></span>
- <span data-ttu-id="27c3f-594">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-594">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-595">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-595">Allowed From</span></span>

<span data-ttu-id="27c3f-596">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-596">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-597">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-597">Preemption Possible</span></span>

<span data-ttu-id="27c3f-598">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-598">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-599">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-599">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-600">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-600">See Also</span></span>

- <span data-ttu-id="27c3f-601">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-601">tx_event_flags_delete</span></span>
- <span data-ttu-id="27c3f-602">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-602">tx_event_flags_get</span></span>
- <span data-ttu-id="27c3f-603">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-603">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27c3f-604">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-604">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27c3f-605">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-605">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-606">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27c3f-606">tx_event_flags_set</span></span>
- <span data-ttu-id="27c3f-607">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-607">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="27c3f-608">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-608">tx_event_flags_delete</span></span>

<span data-ttu-id="27c3f-609">Eliminar un grupo de marcas de eventos</span><span class="sxs-lookup"><span data-stu-id="27c3f-609">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-610">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-610">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-611">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-611">Description</span></span>

<span data-ttu-id="27c3f-612">Este servicio elimina el grupo de marcas de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-612">This service deletes the specified event flags group.</span></span> <span data-ttu-id="27c3f-613">Todos los subprocesos suspendidos en espera de eventos de este grupo se reanudan y se les asigna un estado de devolución TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="27c3f-613">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="27c3f-614">*La aplicación debe asegurarse de que se complete (o deshabilite) una devolución de llamada de notificación de establecimiento para este grupo de marcas de eventos antes de eliminarlo. Además, la aplicación debe impedir el uso futuro de un grupo de marcas de eventos eliminado.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-614">*The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group. In addition, the application must prevent all future use of a deleted event flags group.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-615">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-615">Parameters</span></span>

- <span data-ttu-id="27c3f-616">**group_ptr**: puntero a un grupo de marcas de eventos creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-616">**group_ptr** Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-617">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-617">Return Values</span></span>

- <span data-ttu-id="27c3f-618">**TX_SUCCESS** (0x00): grupo de marcas de eventos eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-618">**TX_SUCCESS** (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="27c3f-619">**TX_GROUP_ERROR** (0x06): puntero del grupo de marcas de eventos no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-619">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="27c3f-620">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-620">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-621">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-621">Allowed From</span></span>

<span data-ttu-id="27c3f-622">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-622">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-623">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-623">Preemption Possible</span></span>

<span data-ttu-id="27c3f-624">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-624">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-625">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-625">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Delete event flags group. Assume that the group has
already been created with a call to
tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-626">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-626">See Also</span></span>

- <span data-ttu-id="27c3f-627">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-627">tx_event_flags_create</span></span>
- <span data-ttu-id="27c3f-628">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-628">tx_event_flags_get</span></span>
- <span data-ttu-id="27c3f-629">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-629">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27c3f-630">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-630">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27c3f-631">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-631">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-632">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27c3f-632">tx_event_flags_set</span></span>
- <span data-ttu-id="27c3f-633">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-633">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="27c3f-634">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-634">tx_event_flags_get</span></span>

<span data-ttu-id="27c3f-635">Obtener marcas de eventos de un grupo de marcas de eventos</span><span class="sxs-lookup"><span data-stu-id="27c3f-635">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-636">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-636">Prototype</span></span>

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27c3f-637">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-637">Description</span></span>

<span data-ttu-id="27c3f-638">Este servicio recupera las marcas de eventos del grupo de marcas de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-638">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="27c3f-639">Cada grupo contiene 32 marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-639">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="27c3f-640">Cada marca se representa con un solo bit.</span><span class="sxs-lookup"><span data-stu-id="27c3f-640">Each flag is represented by a single bit.</span></span> <span data-ttu-id="27c3f-641">Este servicio puede recuperar diversas combinaciones de marcas de eventos, según la selección de los parámetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-641">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-642">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-642">Parameters</span></span>

- <span data-ttu-id="27c3f-643">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-643">**group_ptr**</span></span> <br><span data-ttu-id="27c3f-644">Puntero a un grupo de marcas de eventos creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-644">Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="27c3f-645">**requested_flags**</span><span class="sxs-lookup"><span data-stu-id="27c3f-645">**requested_flags**</span></span> <br><span data-ttu-id="27c3f-646">Variable sin signo de 32 bits que representa las marcas de eventos solicitadas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-646">32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="27c3f-647">**get_option**</span><span class="sxs-lookup"><span data-stu-id="27c3f-647">**get_option**</span></span> <br><span data-ttu-id="27c3f-648">Especifica si se necesitan todas o algunas de las marcas de eventos solicitadas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-648">Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="27c3f-649">A continuación, se recogen selecciones válidas:</span><span class="sxs-lookup"><span data-stu-id="27c3f-649">The following are valid selections:</span></span>

  - <span data-ttu-id="27c3f-650">**TX_AND** (0x02)</span><span class="sxs-lookup"><span data-stu-id="27c3f-650">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="27c3f-651">**TX_AND_CLEAR** (0x03)</span><span class="sxs-lookup"><span data-stu-id="27c3f-651">**TX_AND_CLEAR** (0x03)</span></span>
  - <span data-ttu-id="27c3f-652">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="27c3f-652">**TX_OR** (0x00)</span></span>
  - <span data-ttu-id="27c3f-653">**TX_OR_CLEAR** (0x01)</span><span class="sxs-lookup"><span data-stu-id="27c3f-653">**TX_OR_CLEAR** (0x01)</span></span>

    <span data-ttu-id="27c3f-654">Al seleccionar TX_AND o TX_AND_CLEAR, se especifica que todas las marcas de eventos deben estar presentes en el grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-654">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="27c3f-655">Al seleccionar TX_OR o TX_OR_CLEAR, se especifica que basta con alguna marca de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-655">Selecting TX_OR or TX_OR_CLEAR     specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="27c3f-656">Las marcas de eventos que atienden la solicitud se desactivan (se establecen en cero) si se especifica la selección TX_AND_CLEAR o TX_OR_CLEAR.</span><span class="sxs-lookup"><span data-stu-id="27c3f-656">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="27c3f-657">**actual_flags_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-657">**actual_flags_ptr**</span></span> <br><span data-ttu-id="27c3f-658">Puntero al destino de donde se colocan las marcas de eventos recuperadas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-658">Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="27c3f-659">Tenga en cuenta que las marcas reales obtenidas pueden contener marcas que no se hayan solicitado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-659">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="27c3f-660">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27c3f-660">**wait_option**</span></span>  <br><span data-ttu-id="27c3f-661">Define el comportamiento del servicio si no se establecen las marcas de eventos seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-661">Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="27c3f-662">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="27c3f-662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27c3f-663">**TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="27c3f-663">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27c3f-664">Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.</span><span class="sxs-lookup"><span data-stu-id="27c3f-664">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="27c3f-665">Valor de tiempo de espera **TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya marcas de eventos disponibles.</span><span class="sxs-lookup"><span data-stu-id="27c3f-665">**TX_WAIT_FOREVER** timeout value  (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>
  - <span data-ttu-id="27c3f-666">valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando las marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-666">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-667">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-667">Return Values</span></span>

- <span data-ttu-id="27c3f-668">**TX_SUCCESS** (0x00): marcas de eventos obtenidas correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-668">**TX_SUCCESS** (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="27c3f-669">**TX_DELETED** (0x01): el grupo de marcas de eventos se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-669">**TX_DELETED** (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27c3f-670">**TX_NO_EVENTS** (0x07): el servicio no pudo obtener los eventos indicados en el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-670">**TX_NO_EVENTS** (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="27c3f-671">**TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="27c3f-671">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27c3f-672">**TX_GROUP_ERROR** (0x06): puntero del grupo de marcas de eventos no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-672">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="27c3f-673">**TX_PTR_ERROR** (0x03): puntero de las marcas de eventos reales no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-673">**TX_PTR_ERROR** (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="27c3f-674">**TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-674">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="27c3f-675">**TX_OPTION_ERROR** (0x08): se especificó una opción Get no válida.</span><span class="sxs-lookup"><span data-stu-id="27c3f-675">**TX_OPTION_ERROR** (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-676">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-676">Allowed From</span></span>

<span data-ttu-id="27c3f-677">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-677">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-678">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-678">Preemption Possible</span></span>

<span data-ttu-id="27c3f-679">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-679">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-680">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-680">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG actual_events;
UINT status;

/* Request that event flags 0, 4, and 8 are all set. Also,
if they are set they should be cleared. If the event
flags are not set, this service suspends for a maximum of
20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
    TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
actual events obtained. */
```

<span data-ttu-id="27c3f-681">**Vea también**</span><span class="sxs-lookup"><span data-stu-id="27c3f-681">**See Also**</span></span>

- <span data-ttu-id="27c3f-682">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-682">tx_event_flags_create</span></span>
- <span data-ttu-id="27c3f-683">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-683">tx_event_flags_delete</span></span>
- <span data-ttu-id="27c3f-684">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-684">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27c3f-685">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-685">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27c3f-686">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-686">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-687">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27c3f-687">tx_event_flags_set</span></span>
- <span data-ttu-id="27c3f-688">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-688">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_info_get"></a><span data-ttu-id="27c3f-689">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-689">tx_event_flags_info_get</span></span>

<span data-ttu-id="27c3f-690">Recuperar la información acerca de un grupo de marcas de eventos</span><span class="sxs-lookup"><span data-stu-id="27c3f-690">Retrieve information about event flags group</span></span>

<span data-ttu-id="27c3f-691">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="27c3f-691">**Prototype**</span></span>

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

<span data-ttu-id="27c3f-692">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="27c3f-692">**Description**</span></span>

<span data-ttu-id="27c3f-693">Este servicio recupera información sobre el grupo de marcas de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-693">This service retrieves information about the specified event flags group.</span></span>

<span data-ttu-id="27c3f-694">**Parámetros**</span><span class="sxs-lookup"><span data-stu-id="27c3f-694">**Parameters**</span></span>

- <span data-ttu-id="27c3f-695">**group_ptr**: puntero a un bloque de control del grupo de marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-695">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="27c3f-696">**name**: puntero al destino del puntero al nombre del grupo de marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-696">**name** Pointer to destination for the pointer to the event flags group's name.</span></span>
- <span data-ttu-id="27c3f-697">**current_flags**: puntero al destino de las marcas actuales establecidas en el grupo de marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-697">**current_flags** Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="27c3f-698">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este grupo de marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-698">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="27c3f-699">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este grupo de marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-699">**suspended_count** Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="27c3f-700">**next_group**: puntero al destino del puntero del siguiente grupo de marcas de eventos creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-700">**next_group** Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-701">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-701">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-702">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-702">Return Values</span></span>

- <span data-ttu-id="27c3f-703">**TX_SUCCESS** (0X00): información del grupo de eventos recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-703">**TX_SUCCESS** (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="27c3f-704">**TX_GROUP_ERROR** (0x06): puntero del grupo de eventos no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-704">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-705">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-705">Allowed From</span></span>

<span data-ttu-id="27c3f-706">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-706">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-707">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-707">Preemption Possible</span></span>

<span data-ttu-id="27c3f-708">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-708">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-709">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-709">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
CHAR *name;
ULONG current_flags;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_EVENT_FLAGS_GROUP *next_group;
UINT status;

/* Retrieve information about the previously created
event flags group "my_event_group." */
status = tx_event_flags_info_get(&my_event_group, &name,
    &current_flags,
    &first_suspended, &suspended_count,
    &next_group);
/* If status equals TX_SUCCESS, the information requested is
valid. */
```
<span data-ttu-id="27c3f-710">**Vea también**</span><span class="sxs-lookup"><span data-stu-id="27c3f-710">**See Also**</span></span>

- <span data-ttu-id="27c3f-711">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-711">tx_event_flags_create</span></span>
- <span data-ttu-id="27c3f-712">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-712">tx_event_flags_delete</span></span>
- <span data-ttu-id="27c3f-713">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-713">tx_event_flags_get</span></span>
- <span data-ttu-id="27c3f-714">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-714">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27c3f-715">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-715">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-716">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27c3f-716">tx_event_flags_set</span></span>
- <span data-ttu-id="27c3f-717">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-717">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="27c3f-718">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-718">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="27c3f-719">Obtener información acerca del rendimiento de un grupo de marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-719">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-720">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-720">Prototype</span></span>

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27c3f-721">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-721">Description</span></span>

<span data-ttu-id="27c3f-722">Este servicio recupera información sobre el rendimiento del grupo de marcas de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-722">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-723">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-723">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-724">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-724">Parameters</span></span>

- <span data-ttu-id="27c3f-725">**group_ptr**: puntero a un grupo de marcas de eventos creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-725">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="27c3f-726">**sets**: puntero al destino del número de solicitudes de establecimiento de marcas de eventos realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-726">**sets** Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="27c3f-727">**gets**: puntero al destino del número de solicitudes Get de marcas de eventos realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-727">**gets** Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="27c3f-728">**suspensions**: puntero al destino del número de suspensiones de obtención de marcas de eventos de los subprocesos en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-728">**suspensions** Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="27c3f-729">**timeouts**: puntero al destino del número de tiempos de espera de suspensiones de obtención de marcas de eventos en este grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-729">**timeouts** Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-730">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-730">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-731">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-731">Return Values</span></span>

- <span data-ttu-id="27c3f-732">**TX_SUCCESS** (0x00): rendimiento del grupo de marcas de eventos obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-732">**TX_SUCCESS** (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="27c3f-733">**TX_PTR_ERROR** (0x03): puntero del grupo de marcas de eventos no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-733">**TX_PTR_ERROR** (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="27c3f-734">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-734">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-735">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-735">Allowed From</span></span>

<span data-ttu-id="27c3f-736">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-736">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-737">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-737">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flag_group;
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created event
flag group. */
status = tx_event_flags_performance_info_get(&my_event_flag_group,
    &sets, &gets, &suspensions,
    &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-738">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-738">See Also</span></span>

- <span data-ttu-id="27c3f-739">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-739">tx_event_flags_create</span></span>
- <span data-ttu-id="27c3f-740">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-740">tx_event_flags_delete</span></span>
- <span data-ttu-id="27c3f-741">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-741">tx_event_flags_get</span></span>
- <span data-ttu-id="27c3f-742">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-742">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27c3f-743">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-743">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-744">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27c3f-744">tx_event_flags_set</span></span>
- <span data-ttu-id="27c3f-745">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-745">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="27c3f-746">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-746">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="27c3f-747">Recuperar información acerca del rendimiento del sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-747">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-748">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-748">Prototype</span></span>

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27c3f-749">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-749">Description</span></span>

<span data-ttu-id="27c3f-750">Este servicio recupera información sobre el rendimiento de todos los grupos de marcas de eventos del sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-750">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-751">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-751">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-752">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-752">Parameters</span></span>

- <span data-ttu-id="27c3f-753">**sets**: puntero al destino del número total de solicitudes de establecimiento de marcas de eventos realizadas en todos los grupos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-753">**sets** Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="27c3f-754">**gets**: puntero al destino del número total de solicitudes Get de marcas de eventos realizadas en todos los grupos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-754">**gets** Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="27c3f-755">**suspensions**: puntero al destino del número total de suspensiones de obtención de marcas de eventos de los subprocesos de todos los grupos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-755">**suspensions** Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="27c3f-756">**timeouts**: puntero al destino del número total de tiempos de espera de suspensiones de obtención de marcas de eventos de todos los grupos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-756">**timeouts** Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-757">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-757">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-758">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-758">Return Values</span></span>

- <span data-ttu-id="27c3f-759">**TX_SUCCESS** (0x00): rendimiento del sistema de marcas de eventos obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-759">**TX_SUCCESS** (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="27c3f-760">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-760">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-761">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-761">Example</span></span>

```c
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created event
flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-762">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-762">See Also</span></span>

- <span data-ttu-id="27c3f-763">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-763">tx_event_flags_create</span></span>
- <span data-ttu-id="27c3f-764">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-764">tx_event_flags_delete</span></span>
- <span data-ttu-id="27c3f-765">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-765">tx_event_flags_get</span></span>
- <span data-ttu-id="27c3f-766">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-766">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27c3f-767">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-767">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27c3f-768">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27c3f-768">tx_event_flags_set</span></span>
- <span data-ttu-id="27c3f-769">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-769">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="27c3f-770">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27c3f-770">tx_event_flags_set</span></span>

<span data-ttu-id="27c3f-771">Establecer marcas de eventos en un grupo de marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-771">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-772">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-772">Prototype</span></span>

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a><span data-ttu-id="27c3f-773">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-773">Description</span></span>

<span data-ttu-id="27c3f-774">Este servicio establece o borra las marcas de eventos de un grupo de marcas de eventos, en función de la opción Set especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-774">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="27c3f-775">Se reanudan todos los subprocesos suspendidos cuya solicitud de marcas de eventos se ha atendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-775">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-776">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-776">Parameters</span></span>

- <span data-ttu-id="27c3f-777">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-777">**group_ptr**</span></span> <br><span data-ttu-id="27c3f-778">Puntero al bloque de control del grupo de marcas de eventos creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-778">Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="27c3f-779">**flags_to_set**</span><span class="sxs-lookup"><span data-stu-id="27c3f-779">**flags_to_set**</span></span> <br><span data-ttu-id="27c3f-780">Especifica las marcas de eventos que se van a establecer o borrar en función de la opción Set seleccionada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-780">Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="27c3f-781">**set_option**</span><span class="sxs-lookup"><span data-stu-id="27c3f-781">**set_option**</span></span> <br><span data-ttu-id="27c3f-782">Especifica si se les aplica AND u OR a las marcas de eventos indicadas en las marcas de eventos actuales del grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-782">Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="27c3f-783">A continuación, se recogen selecciones válidas:</span><span class="sxs-lookup"><span data-stu-id="27c3f-783">The following are valid selections:</span></span>
  - <span data-ttu-id="27c3f-784">**TX_AND** (0x02)</span><span class="sxs-lookup"><span data-stu-id="27c3f-784">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="27c3f-785">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="27c3f-785">**TX_OR** (0x00)</span></span>

  <span data-ttu-id="27c3f-786">Al seleccionar TX_AND, se especifica que se aplica **AND** a las marcas de eventos indicadas en las marcas de eventos actuales del grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-786">Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="27c3f-787">Esta opción se usa a menudo para borrar las marcas de eventos de un grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-787">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="27c3f-788">En cambio, si se especifica TX_OR, se aplica **OR** a las marcas de eventos indicadas con el evento actual en el grupo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-788">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-789">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-789">Return Values</span></span>
- <span data-ttu-id="27c3f-790">**TX_SUCCESS** (0x00): marcas de eventos establecidas correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-790">**TX_SUCCESS** (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="27c3f-791">**TX_GROUP_ERROR** (0x06): puntero al grupo de marcas de eventos no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-791">**TX_GROUP_ERROR** (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="27c3f-792">**TX_OPTION_ERROR** (0x08): la opción Set especificada no es válida.</span><span class="sxs-lookup"><span data-stu-id="27c3f-792">**TX_OPTION_ERROR** (0x08) Invalid set-option specified.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-793">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-793">Preemption Possible</span></span>

<span data-ttu-id="27c3f-794">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-794">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-795">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-795">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Set event flags 0, 4, and 8. */
status = tx_event_flags_set(&my_event_flags_group,
    0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
set and any suspended thread whose request was satisfied
has been resumed. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-796">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-796">See Also</span></span>

- <span data-ttu-id="27c3f-797">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-797">tx_event_flags_create</span></span>
- <span data-ttu-id="27c3f-798">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-798">tx_event_flags_delete</span></span>
- <span data-ttu-id="27c3f-799">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-799">tx_event_flags_get</span></span>
- <span data-ttu-id="27c3f-800">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-800">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27c3f-801">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-801">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27c3f-802">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-802">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-803">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-803">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="27c3f-804">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-804">tx_event_flags_set_notify</span></span>

<span data-ttu-id="27c3f-805">Notificar a la aplicación al establecer marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-805">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-806">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-806">Prototype</span></span>

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a><span data-ttu-id="27c3f-807">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-807">Description</span></span>

<span data-ttu-id="27c3f-808">Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se establecen una o varias marcas de eventos en el grupo de marcas de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-808">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="27c3f-809">El procesamiento de la devolución de llamada de notificación se define mediante</span><span class="sxs-lookup"><span data-stu-id="27c3f-809">The processing of the notification callback is defined by the</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-810">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-810">Parameters</span></span>
- <span data-ttu-id="27c3f-811">**group_ptr**: puntero a un grupo de marcas de eventos creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-811">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="27c3f-812">**events_set_notify**: puntero a la función de notificación de establecimiento de marcas de eventos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-812">**events_set_notify** Pointer to application's event flags set notification function.</span></span> <span data-ttu-id="27c3f-813">Si este valor es TX_NULL, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="27c3f-813">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-814">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-814">Return Values</span></span>

- <span data-ttu-id="27c3f-815">**TX_SUCCESS** (0x00): notificación de establecimiento de marcas de eventos registrada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-815">**TX_SUCCESS** (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="27c3f-816">**TX_GROUP_ERROR** (0x06): puntero del grupo de marcas de eventos no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-816">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="27c3f-817">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema se compiló con las funcionalidades de notificación deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-817">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-818">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-818">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_group;

/* Register the "my_event_flags_set_notify" function for monitoring
event flags set in the event flags group "my_group." */
status = tx_event_flags_set_notify(&my_group, my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
was successfully registered. */
void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)

/* One or more event flags was set in this group! */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-819">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-819">See Also</span></span>

- <span data-ttu-id="27c3f-820">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-820">tx_event_flags_create</span></span>
- <span data-ttu-id="27c3f-821">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-821">tx_event_flags_delete</span></span>
- <span data-ttu-id="27c3f-822">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-822">tx_event_flags_get</span></span>
- <span data-ttu-id="27c3f-823">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-823">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27c3f-824">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-824">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27c3f-825">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-825">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-826">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27c3f-826">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="27c3f-827">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="27c3f-827">tx_interrupt_control</span></span>

<span data-ttu-id="27c3f-828">Habilitar y deshabilitar interrupciones</span><span class="sxs-lookup"><span data-stu-id="27c3f-828">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-829">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-829">Prototype</span></span>

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a><span data-ttu-id="27c3f-830">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-830">Description</span></span>

<span data-ttu-id="27c3f-831">Este servicio habilita o deshabilita las interrupciones según se especifique mediante el parámetro de entrada *new_posture*.</span><span class="sxs-lookup"><span data-stu-id="27c3f-831">This service enables or disables interrupts as specified by the input parameter *new_posture*.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-832">*Si se llama a este servicio desde un subproceso de aplicación, la posición de interrupción sigue formando parte del contexto de ese subproceso. Por ejemplo, si el subproceso llama a esta rutina para deshabilitar las interrupciones y después se suspende, las interrupciones siguen deshabilitadas cuando se reanuda.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-832">*If this service is called from an application thread, the interrupt posture remains part of that thread's context. For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.*</span></span>

> [!WARNING]
> <span data-ttu-id="27c3f-833">*Este servicio no debe usarse para habilitar interrupciones durante la inicialización. Si lo hace, podrían producirse resultados imprevisibles.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-833">*This service should not be used to enable interrupts during initialization! Doing so could cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-834">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-834">Parameters</span></span>

- <span data-ttu-id="27c3f-835">**new_posture**: este parámetro especifica si las interrupciones están deshabilitadas o habilitadas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-835">**new_posture** This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="27c3f-836">Entre los valores válidos se incluyen **TX_INT_DISABLE** y **TX_INT_ENABLE**.</span><span class="sxs-lookup"><span data-stu-id="27c3f-836">Legal values include **TX_INT_DISABLE** and **TX_INT_ENABLE**.</span></span> <span data-ttu-id="27c3f-837">Los valores reales de estos parámetros son específicos del puerto.</span><span class="sxs-lookup"><span data-stu-id="27c3f-837">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="27c3f-838">Además, algunas arquitecturas de procesamiento pueden admitir posiciones adicionales para deshabilitar interrupciones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-838">In addition, some processing architectures might support additional interrupt disable postures.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-839">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-839">Return Values</span></span>
- <span data-ttu-id="27c3f-840">**previous posture**: este servicio devuelve la posición de interrupción anterior al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-840">**previous posture** This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="27c3f-841">Esto permite a los usuarios del servicio restaurar la posición anterior tras deshabilitar las interrupciones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-841">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-842">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-842">Allowed From</span></span>

<span data-ttu-id="27c3f-843">Subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-843">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-844">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-844">Preemption Possible</span></span>

<span data-ttu-id="27c3f-845">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-845">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-846">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-846">Example</span></span>

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a><span data-ttu-id="27c3f-847">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-847">See Also</span></span>

<span data-ttu-id="27c3f-848">Ninguno</span><span class="sxs-lookup"><span data-stu-id="27c3f-848">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="27c3f-849">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-849">tx_mutex_create</span></span>

<span data-ttu-id="27c3f-850">Crear una exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="27c3f-850">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-851">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-851">Prototype</span></span>

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a><span data-ttu-id="27c3f-852">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-852">Description</span></span>

<span data-ttu-id="27c3f-853">Este servicio crea una exclusión entre subprocesos para la protección de los recursos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-853">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-854">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-854">Parameters</span></span>

- <span data-ttu-id="27c3f-855">**mutex_ptr**: puntero a un bloque de control de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-855">**mutex_ptr** Pointer to a mutex control block.</span></span>
- <span data-ttu-id="27c3f-856">**name_ptr**: puntero al nombre de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-856">**name_ptr** Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="27c3f-857">**priority_inherit**: especifica si esta exclusión mutua admite o no la herencia de prioridad.</span><span class="sxs-lookup"><span data-stu-id="27c3f-857">**priority_inherit** Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="27c3f-858">Si este valor es TX_INHERIT, se admite la herencia de prioridad.</span><span class="sxs-lookup"><span data-stu-id="27c3f-858">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="27c3f-859">Sin embargo, si se especifica TX_NO_INHERIT, esta exclusión mutua no admite la herencia de prioridad.</span><span class="sxs-lookup"><span data-stu-id="27c3f-859">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-860">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-860">Return Values</span></span>

- <span data-ttu-id="27c3f-861">**TX_SUCCESS** (0x00): exclusión mutua creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-861">**TX_SUCCESS** (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="27c3f-862">**TX_MUTEX_ERROR** (0x1C): puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-862">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="27c3f-863">El puntero tiene un valor NULL o la exclusión mutua ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-863">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="27c3f-864">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-864">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="27c3f-865">**TX_INHERIT_ERROR** (0x1F): parámetro de herencia de prioridad no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-865">**TX_INHERIT_ERROR** (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-866">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-866">Allowed From</span></span>

<span data-ttu-id="27c3f-867">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-867">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-868">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-868">Preemption Possible</span></span>

<span data-ttu-id="27c3f-869">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-869">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-870">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-870">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Create a mutex to provide protection over a
common resource. */
status = tx_mutex_create(&my_mutex,"my_mutex_name",
    TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
use. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-871">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-871">See Also</span></span>

- <span data-ttu-id="27c3f-872">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-872">tx_mutex_delete</span></span>
- <span data-ttu-id="27c3f-873">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-873">tx_mutex_get</span></span>
- <span data-ttu-id="27c3f-874">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-874">tx_mutex_info_get</span></span>
- <span data-ttu-id="27c3f-875">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-875">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27c3f-876">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-876">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-877">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-877">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27c3f-878">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-878">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="27c3f-879">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-879">tx_mutex_delete</span></span>

<span data-ttu-id="27c3f-880">Eliminar una exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="27c3f-880">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-881">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-881">Prototype</span></span>

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-882">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-882">Description</span></span>

<span data-ttu-id="27c3f-883">Este servicio elimina la exclusión mutua especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-883">This service deletes the specified mutex.</span></span> <span data-ttu-id="27c3f-884">Todos los subprocesos suspendidos en espera de la exclusión mutua se reanudan y se les asigna un estado de devolución **TX_DELETED**.</span><span class="sxs-lookup"><span data-stu-id="27c3f-884">All threads suspended waiting for the mutex are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-885">*Es responsabilidad de la aplicación impedir el uso de una exclusión mutua eliminada.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-885">*It is the application's responsibility to prevent use of a deleted mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-886">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-886">Parameters</span></span>

- <span data-ttu-id="27c3f-887">**mutex_ptr**: puntero a una exclusión mutua creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-887">**mutex_ptr** Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-888">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-888">Return Values</span></span>

- <span data-ttu-id="27c3f-889">**TX_SUCCESS** (0x00): exclusión mutua eliminada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-889">**TX_SUCCESS** (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="27c3f-890">**TX_MUTEX_ERROR** (0x1C): puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-890">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="27c3f-891">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-891">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-892">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-892">Allowed From</span></span>

<span data-ttu-id="27c3f-893">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-893">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-894">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-894">Preemption Possible</span></span>

<span data-ttu-id="27c3f-895">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-895">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-896">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-896">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-897">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-897">See Also</span></span>

- <span data-ttu-id="27c3f-898">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-898">tx_mutex_create</span></span>
- <span data-ttu-id="27c3f-899">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-899">tx_mutex_get</span></span>
- <span data-ttu-id="27c3f-900">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-900">tx_mutex_info_get</span></span>
- <span data-ttu-id="27c3f-901">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-901">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27c3f-902">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-902">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-903">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-903">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27c3f-904">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-904">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="27c3f-905">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-905">tx_mutex_get</span></span>

<span data-ttu-id="27c3f-906">Obtener la propiedad de una exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="27c3f-906">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-907">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-907">Prototype</span></span>

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27c3f-908">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-908">Description</span></span>

<span data-ttu-id="27c3f-909">Este servicio intenta obtener la propiedad exclusiva de la exclusión mutua especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-909">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="27c3f-910">Si el subproceso que realiza la llamada ya es el propietario de la exclusión mutua, se incrementa un contador interno y se devuelve un estado correcto.</span><span class="sxs-lookup"><span data-stu-id="27c3f-910">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="27c3f-911">Si otro subproceso que tiene una prioridad más alta es el propietario de la exclusión mutua y se especificó la herencia de prioridad al crearla, la prioridad del subproceso de menor prioridad se elevará temporalmente al nivel de la del subproceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-911">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread's priority will be temporarily raised to that of the calling thread.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-912">*La prioridad del subproceso de menor prioridad que posee una exclusión mutua con herencia de prioridad nunca debe ser modificada por un subproceso externo durante la propiedad de la exclusión mutua.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-912">*The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-913">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-913">Parameters</span></span>

- <span data-ttu-id="27c3f-914">**mutex_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-914">**mutex_ptr**</span></span>   <br><span data-ttu-id="27c3f-915">Puntero a una exclusión mutua creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-915">Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="27c3f-916">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27c3f-916">**wait_option**</span></span> <br><span data-ttu-id="27c3f-917">Define el comportamiento del servicio si la exclusión mutua ya pertenece a otro subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-917">Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="27c3f-918">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="27c3f-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27c3f-919">**TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="27c3f-919">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27c3f-920">*Esta es la única opción válida si se llama al servicio desde la inicialización.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-920">*This is the only valid option if the service is called from Initialization.*</span></span>
  - <span data-ttu-id="27c3f-921">Valor de tiempo de espera **TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar **TX_WAIT_FOREVER**, el subproceso que realiza la llamada se suspende indefinidamente hasta que la exclusión mutua esté disponible.</span><span class="sxs-lookup"><span data-stu-id="27c3f-921">**TX_WAIT_FOREVER** timeout value (0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until the mutex is available.</span></span>
  - <span data-ttu-id="27c3f-922">valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-922">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-923">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-923">Return Values</span></span>

- <span data-ttu-id="27c3f-924">**TX_SUCCESS** (0x00): operación Get de la exclusión mutua realizada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-924">**TX_SUCCESS** (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="27c3f-925">**TX_DELETED** (0x01): la exclusión mutua se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-925">**TX_DELETED** (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27c3f-926">**TX_NOT_AVAILABLE** (0x1D): el servicio no pudo obtener la propiedad de la exclusión mutua en el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-926">**TX_NOT_AVAILABLE** (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="27c3f-927">**TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="27c3f-927">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27c3f-928">**TX_MUTEX_ERROR** (0x1C): puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-928">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="27c3f-929">**TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-929">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>
- <span data-ttu-id="27c3f-930">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-930">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-931">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-931">Allowed From</span></span>

<span data-ttu-id="27c3f-932">Inicialización, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="27c3f-932">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-933">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-933">Preemption Possible</span></span>

<span data-ttu-id="27c3f-934">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-934">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-935">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-935">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="27c3f-936">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-936">See Also</span></span>

- <span data-ttu-id="27c3f-937">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-937">tx_mutex_create</span></span>
- <span data-ttu-id="27c3f-938">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-938">tx_mutex_delete</span></span>
- <span data-ttu-id="27c3f-939">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-939">tx_mutex_info_get</span></span>
- <span data-ttu-id="27c3f-940">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-940">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27c3f-941">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-941">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-942">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-942">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27c3f-943">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-943">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="27c3f-944">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-944">tx_mutex_info_get</span></span>

<span data-ttu-id="27c3f-945">Recuperar información acerca de una exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="27c3f-945">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-946">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-946">Prototype</span></span>

```c
UINT tx_mutex_info_get(
    TX_MUTEX *mutex_ptr, 
    CHAR **name,
    ULONG *count, 
    TX_THREAD **owner,
    TX_THREAD **first_suspended,
    ULONG *suspended_count, 
    TX_MUTEX **next_mutex);
```

### <a name="description"></a><span data-ttu-id="27c3f-947">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-947">Description</span></span>

<span data-ttu-id="27c3f-948">Este servicio recupera información de la exclusión mutua especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-948">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-949">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-949">Parameters</span></span>

- <span data-ttu-id="27c3f-950">**mutex_ptr**: puntero a un bloque de control de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-950">**mutex_ptr** Pointer to mutex control block.</span></span>
- <span data-ttu-id="27c3f-951">**name**: puntero al destino del puntero al nombre de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-951">**name** Pointer to destination for the pointer to the mutex's name.</span></span>
- <span data-ttu-id="27c3f-952">**count**: puntero al destino del recuento de propiedad de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-952">**count** Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="27c3f-953">**owner**: puntero al destino del puntero del subproceso propietario.</span><span class="sxs-lookup"><span data-stu-id="27c3f-953">**owner** Pointer to destination for the owning thread's pointer.</span></span>
- <span data-ttu-id="27c3f-954">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-954">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="27c3f-955">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-955">**suspended_count** Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="27c3f-956">**next_mutex**: puntero al destino del puntero de la siguiente exclusión mutua creada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-956">**next_mutex** Pointer to destination for the pointer of the next created mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-957">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-957">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-958">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-958">Return Values</span></span>

- <span data-ttu-id="27c3f-959">**TX_SUCCESS** (0x00): información de la exclusión mutua recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-959">**TX_SUCCESS** (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="27c3f-960">**TX_MUTEX_ERROR** (0x1C): puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-960">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-961">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-961">Allowed From</span></span>

<span data-ttu-id="27c3f-962">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-962">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-963">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-963">Preemption Possible</span></span>

<span data-ttu-id="27c3f-964">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-964">No</span></span>

<span data-ttu-id="27c3f-965">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="27c3f-965">**Example**</span></span>

```c
TX_MUTEX my_mutex;
CHAR *name;
ULONG count;
TX_THREAD *owner;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_MUTEX *next_mutex;
UINT status;

/* Retrieve information about the previously created
mutex "my_mutex." */
status = tx_mutex_info_get(&my_mutex, &name,
    &count, &owner,
    &first_suspended, &suspended_count,
    &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-966">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-966">See Also</span></span>

- <span data-ttu-id="27c3f-967">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-967">tx_mutex_create</span></span>
- <span data-ttu-id="27c3f-968">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-968">tx_mutex_delete</span></span>
- <span data-ttu-id="27c3f-969">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-969">tx_mutex_get</span></span>
- <span data-ttu-id="27c3f-970">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-970">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27c3f-971">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-971">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-972">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-972">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27c3f-973">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-973">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="27c3f-974">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-974">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="27c3f-975">Obtener información acerca del rendimiento de una exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="27c3f-975">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-976">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-976">Prototype</span></span>

```c
UINT tx_mutex_performance_info_get(
    TX_MUTEX *mutex_ptr, 
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="27c3f-977">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-977">Description</span></span>

<span data-ttu-id="27c3f-978">Este servicio recupera información sobre el rendimiento de la exclusión mutua especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-978">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-979">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-979">*The ThreadX library and application must be built with* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-980">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-980">Parameters</span></span>

- <span data-ttu-id="27c3f-981">**mutex_ptr**: puntero a una exclusión mutua creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-981">**mutex_ptr** Pointer to previously created mutex.</span></span>
- <span data-ttu-id="27c3f-982">**puts**: puntero al destino del número de solicitudes Put realizadas en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-982">**puts** Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="27c3f-983">**gets**: puntero al destino del número de solicitudes Get realizadas en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-983">**gets** Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="27c3f-984">**suspensions**: puntero al destino del número de suspensiones de obtención de exclusiones mutuas de los subprocesos en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-984">**suspensions** Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="27c3f-985">**timeouts**: puntero al destino del número de tiempos de espera de suspensiones de obtención de exclusiones mutuas en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-985">**timeouts** Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="27c3f-986">**inversions**: puntero al destino del número de inversiones de prioridad de los subprocesos en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-986">**inversions** Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="27c3f-987">**inheritances**: puntero al destino del número de operaciones de herencia de prioridad de los subprocesos en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-987">**inheritances** Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-988">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-988">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-989">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-989">Return Values</span></span>

- <span data-ttu-id="27c3f-990">**TX_SUCCESS** (0x00): rendimiento de la exclusión mutua obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-990">**TX_SUCCESS** (0x00) Successful mutex performance get.</span></span>
- <span data-ttu-id="27c3f-991">**TX_PTR_ERROR** (0x03): puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-991">**TX_PTR_ERROR** (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="27c3f-992">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-992">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-993">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-993">Allowed From</span></span>

<span data-ttu-id="27c3f-994">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-994">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-995">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-995">Example</span></span>

```c
TX_MUTEX my_mutex;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on the previously created
mutex. */
status = tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
    &suspensions, &timeouts, &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-996">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-996">See Also</span></span>

- <span data-ttu-id="27c3f-997">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-997">tx_mutex_create</span></span>
- <span data-ttu-id="27c3f-998">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-998">tx_mutex_delete</span></span>
- <span data-ttu-id="27c3f-999">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-999">tx_mutex_get</span></span>
- <span data-ttu-id="27c3f-1000">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1000">tx_mutex_info_get</span></span>
- <span data-ttu-id="27c3f-1001">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1001">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1002">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1002">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27c3f-1003">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1003">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="27c3f-1004">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1004">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="27c3f-1005">Obtener información acerca del rendimiento del sistema de una exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1005">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1006">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1006">Prototype</span></span>

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="27c3f-1007">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1007">Description</span></span>

<span data-ttu-id="27c3f-1008">Este servicio recupera información sobre el rendimiento de todas las exclusiones mutuas del sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1008">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-1009">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1009">*The ThreadX library and application must be built with* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1010">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1010">Parameters</span></span>

- <span data-ttu-id="27c3f-1011">**puts**: puntero al destino del número total de solicitudes Put realizadas en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1011">**puts** Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="27c3f-1012">**gets**: puntero al destino del número total de solicitudes Get realizadas en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1012">**gets** Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="27c3f-1013">**suspensions**: puntero al destino del número total de suspensiones de obtención de exclusiones mutuas de los subprocesos en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1013">**suspensions** Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="27c3f-1014">**timeouts**: puntero al destino del número total de tiempos de espera de suspensiones de obtención de exclusiones mutuas en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1014">**timeouts** Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="27c3f-1015">**inversions**: puntero al destino del número total de inversiones de prioridad de los subprocesos en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1015">**inversions** Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="27c3f-1016">**inheritances**: puntero al destino del número total de operaciones de herencia de prioridad de los subprocesos en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1016">**inheritances** Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1017">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1017">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1018">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1018">Return Values</span></span>

- <span data-ttu-id="27c3f-1019">**TX_SUCCESS** (0x00): rendimiento del sistema de la exclusión mutua obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1019">**TX_SUCCESS** (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="27c3f-1020">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1021">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1021">Allowed From</span></span>

<span data-ttu-id="27c3f-1022">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1022">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1023">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1023">Example</span></span>

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on all previously created
mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts,
    &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1024">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1024">See Also</span></span>

- <span data-ttu-id="27c3f-1025">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1025">tx_mutex_create</span></span>
- <span data-ttu-id="27c3f-1026">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1026">tx_mutex_delete</span></span>
- <span data-ttu-id="27c3f-1027">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1027">tx_mutex_get</span></span>
- <span data-ttu-id="27c3f-1028">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1028">tx_mutex_info_get</span></span>
- <span data-ttu-id="27c3f-1029">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1029">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1030">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1030">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27c3f-1031">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1031">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="27c3f-1032">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1032">tx_mutex_prioritize</span></span>

<span data-ttu-id="27c3f-1033">Clasificar por orden de prioridad la lista de suspensiones de una exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="27c3f-1033">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1034">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1034">Prototype</span></span>

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-1035">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1035">Description</span></span>

<span data-ttu-id="27c3f-1036">Este servicio coloca el subproceso de prioridad más alta suspendido para la propiedad de la exclusión mutua al principio de la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1036">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="27c3f-1037">Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1037">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1038">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1038">Parameters</span></span>

- <span data-ttu-id="27c3f-1039">**mutex_ptr**: puntero a la exclusión mutua creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1039">**mutex_ptr** Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1040">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1040">Return Values</span></span>

- <span data-ttu-id="27c3f-1041">**TX_SUCCESS** (0x00): exclusión mutua clasificada por orden de prioridad correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1041">**TX_SUCCESS** (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="27c3f-1042">**TX_MUTEX_ERROR** (0x1C): puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1042">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1043">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1043">Allowed From</span></span>

<span data-ttu-id="27c3f-1044">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1044">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1045">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1045">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1046">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-1046">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1047">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1047">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Ensure that the highest priority thread will receive
ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_mutex_put call that releases ownership of the
mutex will give ownership to this thread and wake it
up. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1048">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1048">See Also</span></span>

- <span data-ttu-id="27c3f-1049">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1049">tx_mutex_create</span></span>
- <span data-ttu-id="27c3f-1050">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1050">tx_mutex_delete</span></span>
- <span data-ttu-id="27c3f-1051">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1051">tx_mutex_get</span></span>
- <span data-ttu-id="27c3f-1052">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1052">tx_mutex_info_get</span></span>
- <span data-ttu-id="27c3f-1053">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1053">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1054">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1054">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1055">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1055">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="27c3f-1056">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1056">tx_mutex_put</span></span>

<span data-ttu-id="27c3f-1057">Liberar la propiedad de una exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="27c3f-1057">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1058">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1058">Prototype</span></span>

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-1059">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1059">Description</span></span>

<span data-ttu-id="27c3f-1060">Este servicio reduce el recuento de propiedad de la exclusión mutua especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1060">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="27c3f-1061">Si el recuento de propiedad es cero, la exclusión mutua estará disponible.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1061">If the ownership count is zero, the mutex is made available.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1062">*Si se seleccionó la herencia de prioridad durante la creación de la exclusión mutua, la prioridad del subproceso de liberación se restaurará a la que tenía cuando obtuvo originalmente la propiedad de la exclusión mutua. Se puede deshacer cualquier otro cambio de prioridad realizado en el subproceso de liberación durante la propiedad de la exclusión mutua.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1062">*If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex. Any other priority changes made to the releasing thread during ownership of the mutex may be undone.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1063">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1063">Parameters</span></span>
- <span data-ttu-id="27c3f-1064">mutex_ptr: puntero a la exclusión mutua creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1064">mutex_ptr Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1065">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1065">Return Values</span></span>
- <span data-ttu-id="27c3f-1066">**TX_SUCCESS** (0x00): exclusión mutua liberada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1066">**TX_SUCCESS** (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="27c3f-1067">**TX_NOT_OWNED** (0x1E): el autor de llamada no tiene la propiedad de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1067">**TX_NOT_OWNED** (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="27c3f-1068">**TX_MUTEX_ERROR** (0x1C): puntero a la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1068">**TX_MUTEX_ERROR** (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="27c3f-1069">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1069">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1070">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1070">Allowed From</span></span>

<span data-ttu-id="27c3f-1071">Inicialización, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="27c3f-1071">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1072">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1072">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1073">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-1073">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1074">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1074">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1075">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1075">See Also</span></span>

- <span data-ttu-id="27c3f-1076">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1076">tx_mutex_create</span></span>
- <span data-ttu-id="27c3f-1077">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1077">tx_mutex_delete</span></span>
- <span data-ttu-id="27c3f-1078">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1078">tx_mutex_get</span></span>
- <span data-ttu-id="27c3f-1079">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1079">tx_mutex_info_get</span></span>
- <span data-ttu-id="27c3f-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1080">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1081">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1081">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1082">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1082">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="27c3f-1083">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1083">tx_queue_create</span></span>

<span data-ttu-id="27c3f-1084">Crear una cola de mensajes</span><span class="sxs-lookup"><span data-stu-id="27c3f-1084">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1085">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1085">Prototype</span></span>

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a><span data-ttu-id="27c3f-1086">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1086">Description</span></span>

<span data-ttu-id="27c3f-1087">Este servicio crea una cola de mensajes que se utiliza normalmente para la comunicación entre subprocesos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1087">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="27c3f-1088">El número total de mensajes se calcula a partir del tamaño de mensaje especificado y el número total de bytes de la cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1088">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1089">*Si el número total de bytes especificado en el área de memoria de la cola no es divisible en partes iguales por el tamaño de mensaje indicado, no se usan los bytes restantes en el área de memoria.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1089">*If the total number of bytes specified in the queue's memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1090">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1090">Parameters</span></span>

- <span data-ttu-id="27c3f-1091">**queue_ptr**: puntero a un bloque de control de la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1091">**queue_ptr** Pointer to a message queue control block.</span></span>
- <span data-ttu-id="27c3f-1092">**name_ptr**: puntero al nombre de la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1092">**name_ptr** Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="27c3f-1093">**message_size**: especifica el tamaño de cada mensaje de la cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1093">**message_size** Specifies the size of each message in the queue.</span></span> <span data-ttu-id="27c3f-1094">El tamaño de los mensajes oscila entre 1 y 16 palabras de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1094">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="27c3f-1095">Las opciones de tamaño de mensaje válidas son valores numéricos entre 1 y 16, ambos incluidos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1095">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="27c3f-1096">**queue_start**: dirección de inicio de la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1096">**queue_start** Starting address of the message queue.</span></span> <span data-ttu-id="27c3f-1097">La dirección de inicio debe alinearse con el tamaño del tipo de datos ULONG.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1097">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="27c3f-1098">**pool_size**: número total de bytes disponibles para la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1098">**queue_size** Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1099">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1099">Return Values</span></span>

- <span data-ttu-id="27c3f-1100">**TX_SUCCESS** (0x00): cola de mensajes creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1100">**TX_SUCCESS** (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="27c3f-1101">**TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1101">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="27c3f-1102">El puntero tiene un valor NULL o la cola de mensajes ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1102">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="27c3f-1103">**TX_PTR_ERROR** (0x03): dirección de inicio de la cola de mensajes no válida.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1103">**TX_PTR_ERROR** (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="27c3f-1104">**TX_SIZE_ERROR** (0x05): el tamaño de la cola de mensajes no es válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1104">**TX_SIZE_ERROR** (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="27c3f-1105">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1105">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1106">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1106">Allowed From</span></span>

<span data-ttu-id="27c3f-1107">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1107">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1108">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1108">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1109">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-1109">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1110">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Create a message queue whose total size is 2000 bytes
starting at address 0x300000. Each message in this
queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
    4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
for storing 125 messages (2000 bytes/ 16 bytes per
message). */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1111">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1111">See Also</span></span>

- <span data-ttu-id="27c3f-1112">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1112">tx_queue_delete</span></span>
- <span data-ttu-id="27c3f-1113">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1113">tx_queue_flush</span></span>
- <span data-ttu-id="27c3f-1114">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1114">tx_queue_front_send</span></span>
- <span data-ttu-id="27c3f-1115">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1115">tx_queue_info_get</span></span>
- <span data-ttu-id="27c3f-1116">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1116">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1117">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1117">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1118">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1118">tx_queue_prioritize</span></span>
- <span data-ttu-id="27c3f-1119">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1119">tx_queue_receive</span></span>
- <span data-ttu-id="27c3f-1120">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1120">tx_queue_send</span></span>
- <span data-ttu-id="27c3f-1121">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1121">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="27c3f-1122">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1122">tx_queue_delete</span></span>

<span data-ttu-id="27c3f-1123">Eliminar una cola de mensajes</span><span class="sxs-lookup"><span data-stu-id="27c3f-1123">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1124">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1124">Prototype</span></span>

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-1125">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1125">Description</span></span>

<span data-ttu-id="27c3f-1126">Este servicio elimina la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1126">This service deletes the specified message queue.</span></span> <span data-ttu-id="27c3f-1127">Todos los subprocesos suspendidos en espera de un mensaje de esta cola se reanudan y se les asigna un estado de devolución TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1127">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="27c3f-1128">*La aplicación debe asegurarse de que se complete (o deshabilite) cualquier devolución de llamada de notificación de envío para esta cola antes de eliminarla. Además, la aplicación debe impedir el uso futuro de una cola eliminada.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1128">*The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue. In addition, the application must prevent any future use of a deleted queue.*</span></span> <br><br><span data-ttu-id="27c3f-1129">*También es responsabilidad de la aplicación administrar el área de memoria asociada a la cola, que está disponible una vez completado este servicio.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1129">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1130">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1130">Parameters</span></span>

- <span data-ttu-id="27c3f-1131">**queue_ptr**: puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1131">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1132">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1132">Return Values</span></span>

- <span data-ttu-id="27c3f-1133">**TX_SUCCESS** (0x00): cola de mensajes eliminada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1133">**TX_SUCCESS** (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="27c3f-1134">**TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1134">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="27c3f-1135">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1135">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1136">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1136">Allowed From</span></span>

<span data-ttu-id="27c3f-1137">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1138">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1138">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1139">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-1139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1140">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1140">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Delete entire message queue. Assume that the queue
has already been created with a call to
tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1141">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1141">See Also</span></span>

- <span data-ttu-id="27c3f-1142">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1142">tx_queue_create</span></span>
- <span data-ttu-id="27c3f-1143">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1143">tx_queue_flush</span></span>
- <span data-ttu-id="27c3f-1144">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1144">tx_queue_front_send</span></span>
- <span data-ttu-id="27c3f-1145">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1145">tx_queue_info_get</span></span>
- <span data-ttu-id="27c3f-1146">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1146">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1147">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1147">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1148">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1148">tx_queue_prioritize</span></span>
- <span data-ttu-id="27c3f-1149">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1149">tx_queue_receive</span></span>
- <span data-ttu-id="27c3f-1150">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1150">tx_queue_send</span></span>
- <span data-ttu-id="27c3f-1151">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1151">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="27c3f-1152">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1152">tx_queue_flush</span></span>

<span data-ttu-id="27c3f-1153">Vaciar los mensajes de la cola de mensajes</span><span class="sxs-lookup"><span data-stu-id="27c3f-1153">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1154">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1154">Prototype</span></span>

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-1155">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1155">Description</span></span>

<span data-ttu-id="27c3f-1156">Este servicio elimina todos los mensajes almacenados en la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1156">This service deletes all messages stored in the specified message queue.</span></span>

<span data-ttu-id="27c3f-1157">Si la cola está llena, se descartan los mensajes de todos los subprocesos suspendidos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1157">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="27c3f-1158">Cada subproceso suspendido se reanuda después con un estado de devolución que indica que el mensaje se envió correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1158">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="27c3f-1159">Si la cola está vacía, este servicio no hace nada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1159">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1160">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1160">Parameters</span></span>

- <span data-ttu-id="27c3f-1161">**queue_ptr**: puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1161">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1162">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1162">Return Values</span></span>

- <span data-ttu-id="27c3f-1163">**TX_SUCCESS** (0x00): cola de mensajes vaciada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1163">**TX_SUCCESS** (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="27c3f-1164">**TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1164">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1165">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1165">Allowed From</span></span>

<span data-ttu-id="27c3f-1166">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1166">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1167">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1167">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1168">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-1168">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1169">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1169">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Flush out all pending messages in the specified message
queue. Assume that the queue has already been created
with a call to tx_queue_create. */
status = tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
empty. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1170">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1170">See Also</span></span>

- <span data-ttu-id="27c3f-1171">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1171">tx_queue_create</span></span>
- <span data-ttu-id="27c3f-1172">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1172">tx_queue_delete</span></span>
- <span data-ttu-id="27c3f-1173">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1173">tx_queue_front_send</span></span>
- <span data-ttu-id="27c3f-1174">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1174">tx_queue_info_get</span></span>
- <span data-ttu-id="27c3f-1175">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1175">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1176">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1176">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1177">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1177">tx_queue_prioritize</span></span>
- <span data-ttu-id="27c3f-1178">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1178">tx_queue_receive</span></span>
- <span data-ttu-id="27c3f-1179">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1179">tx_queue_send</span></span>
- <span data-ttu-id="27c3f-1180">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1180">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="27c3f-1181">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1181">tx_queue_front_send</span></span>

<span data-ttu-id="27c3f-1182">Enviar un mensaje al principio de la cola</span><span class="sxs-lookup"><span data-stu-id="27c3f-1182">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1183">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1183">Prototype</span></span>

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27c3f-1184">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1184">Description</span></span>

<span data-ttu-id="27c3f-1185">Este servicio envía un mensaje a la ubicación de inicio de la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1185">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="27c3f-1186">El mensaje se **copia** al principio de la cola desde el área de memoria especificada por el puntero de origen.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1186">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1187">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1187">Parameters</span></span>

- <span data-ttu-id="27c3f-1188">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1188">**queue_ptr**</span></span> <br><span data-ttu-id="27c3f-1189">Puntero a un bloque de control de la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1189">Pointer to a message queue control block.</span></span>
- <span data-ttu-id="27c3f-1190">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1190">**source_ptr**</span></span> <br><span data-ttu-id="27c3f-1191">Puntero al mensaje.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1191">Pointer to the message.</span></span>
- <span data-ttu-id="27c3f-1192">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1192">**wait_option**</span></span>  <br><span data-ttu-id="27c3f-1193">Define el comportamiento del servicio si la cola de mensajes está llena.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1193">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="27c3f-1194">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="27c3f-1194">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27c3f-1195">**TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1195">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27c3f-1196">*Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1196">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="27c3f-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya espacio en la cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="27c3f-1198">valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando a que haya espacio en la cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1198">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1199">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1199">Return Values</span></span>

- <span data-ttu-id="27c3f-1200">**TX_SUCCESS** (0x00): mensaje enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1200">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="27c3f-1201">**TX_DELETED** (0x01): la cola de mensajes se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1201">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27c3f-1202">**TX_QUEUE_FULL** (0x0B): el servicio no pudo enviar el mensaje porque la cola estaba llena durante el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1202">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="27c3f-1203">**TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1203">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27c3f-1204">**TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1204">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="27c3f-1205">**TX_PTR_ERROR** (0x03): puntero de origen no válido para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1205">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="27c3f-1206">**TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1206">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1207">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1207">Allowed From</span></span>

<span data-ttu-id="27c3f-1208">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1208">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1209">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1209">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1210">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-1210">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1211">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1211">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to the front of "my_queue." Return
immediately, regardless of success. This wait
option is used for calls from initialization, timers,
and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
    TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
of the specified queue. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1212">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1212">See Also</span></span>

- <span data-ttu-id="27c3f-1213">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1213">tx_queue_create</span></span>
- <span data-ttu-id="27c3f-1214">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1214">tx_queue_delete</span></span>
- <span data-ttu-id="27c3f-1215">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1215">tx_queue_flush</span></span>
- <span data-ttu-id="27c3f-1216">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1216">tx_queue_info_get</span></span>
- <span data-ttu-id="27c3f-1217">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1217">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1218">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1218">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1219">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1219">tx_queue_prioritize</span></span>
- <span data-ttu-id="27c3f-1220">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1220">tx_queue_receive</span></span>
- <span data-ttu-id="27c3f-1221">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1221">tx_queue_send</span></span>
- <span data-ttu-id="27c3f-1222">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1222">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="27c3f-1223">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1223">tx_queue_info_get</span></span>

<span data-ttu-id="27c3f-1224">Recuperar información acerca de una cola</span><span class="sxs-lookup"><span data-stu-id="27c3f-1224">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1225">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1225">Prototype</span></span>

```c
UINT tx_queue_info_get(
    TX_QUEUE *queue_ptr, 
    CHAR **name,
    ULONG *enqueued, 
    ULONG *available_storage
    TX_THREAD **first_suspended, 
    ULONG *suspended_count,
    TX_QUEUE **next_queue);
```

### <a name="description"></a><span data-ttu-id="27c3f-1226">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1226">Description</span></span>

<span data-ttu-id="27c3f-1227">Este servicio recupera información sobre la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1227">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1228">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1228">Parameters</span></span>

- <span data-ttu-id="27c3f-1229">**queue_ptr**: puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1229">**queue_ptr** Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="27c3f-1230">**name**: puntero al destino del puntero al nombre de la cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1230">**name** Pointer to destination for the pointer to the queue's name.</span></span>
- <span data-ttu-id="27c3f-1231">**enqueued**: puntero al destino del número de mensajes que hay actualmente en la cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1231">**enqueued** Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="27c3f-1232">**available_storage**: puntero al destino del número de mensajes para los que actualmente hay espacio en la cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1232">**available_storage** Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="27c3f-1233">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de esta cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1233">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="27c3f-1234">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en esta cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1234">**suspended_count** Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="27c3f-1235">**next_queue**: puntero al destino del puntero de la siguiente cola creada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1235">**next_queue** Pointer to destination for the pointer of the next created queue.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1236">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1236">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1237">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1237">Return Values</span></span>

- <span data-ttu-id="27c3f-1238">**TX_SUCCESS** (0x00): información de la cola obtenida correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1238">**TX_SUCCESS** (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="27c3f-1239">**TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1239">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1240">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1240">Allowed From</span></span>

<span data-ttu-id="27c3f-1241">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1241">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1242">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1242">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1243">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-1243">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1244">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1244">Example</span></span>

```c
TX_QUEUE my_queue;
CHAR *name;
ULONG enqueued;
ULONG available_storage;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_QUEUE *next_queue;
UINT status;

/* Retrieve information about the previously created
message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
    &enqueued, &available_storage,
    &first_suspended, &suspended_count,
    &next_queue);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1245">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1245">See Also</span></span>

- <span data-ttu-id="27c3f-1246">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1246">tx_queue_create</span></span>
- <span data-ttu-id="27c3f-1247">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1247">tx_queue_delete</span></span>
- <span data-ttu-id="27c3f-1248">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1248">tx_queue_flush</span></span>
- <span data-ttu-id="27c3f-1249">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1249">tx_queue_front_send</span></span>
- <span data-ttu-id="27c3f-1250">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1250">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1251">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1251">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1252">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1252">tx_queue_prioritize</span></span>
- <span data-ttu-id="27c3f-1253">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1253">tx_queue_receive</span></span>
- <span data-ttu-id="27c3f-1254">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1254">tx_queue_send</span></span>
- <span data-ttu-id="27c3f-1255">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1255">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="27c3f-1256">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1256">tx_queue_performance_info_get</span></span>

<span data-ttu-id="27c3f-1257">Obtener información acerca del rendimiento de una cola</span><span class="sxs-lookup"><span data-stu-id="27c3f-1257">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1258">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1258">Prototype</span></span>

```c
UINT tx_queue_performance_info_get(
    TX_QUEUE *queue_ptr,
    ULONG *messages_sent, 
    ULONG *messages_received,
    ULONG *empty_suspensions, 
    ULONG *full_suspensions,
    ULONG *full_errors, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27c3f-1259">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1259">Description</span></span>

<span data-ttu-id="27c3f-1260">Este servicio recupera información sobre el rendimiento de la cola especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1260">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-1261">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1261">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1262">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1262">Parameters</span></span>

- <span data-ttu-id="27c3f-1263">**queue_ptr**: puntero a una cola creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1263">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="27c3f-1264">**messages_sent**: puntero al destino del número de solicitudes de envío realizadas en esta cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1264">**messages_sent** Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="27c3f-1265">**messages_received**: puntero al destino del número de solicitudes de recepción realizadas en esta cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1265">**messages_received** Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="27c3f-1266">**empty_suspensions**: puntero al destino del número de suspensiones de cola vacías en esta cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1266">**empty_suspensions** Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="27c3f-1267">**full_suspensions**: puntero al destino del número de suspensiones de cola completas en esta cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1267">**full_suspensions** Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="27c3f-1268">**full_errors**: puntero al destino del número de errores de cola completos en esta cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1268">**full_errors** Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="27c3f-1269">**timeouts**: puntero al destino del número de tiempos de espera de suspensión de los subprocesos en esta cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1269">**timeouts** Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1270">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1270">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1271">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1271">Return Values</span></span>

- <span data-ttu-id="27c3f-1272">**TX_SUCCESS** (0x00): rendimiento de la cola obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1272">**TX_SUCCESS** (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="27c3f-1273">**TX_PTR_ERROR** (0x03): puntero de la cola no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1273">**TX_PTR_ERROR** (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="27c3f-1274">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1275">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1275">Allowed From</span></span>

<span data-ttu-id="27c3f-1276">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1277">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1277">Example</span></span>

```c
TX_QUEUE my_queue;
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on the previously created
queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1278">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1278">See Also</span></span>

- <span data-ttu-id="27c3f-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1279">tx_queue_create</span></span>
- <span data-ttu-id="27c3f-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1280">tx_queue_delete</span></span>
- <span data-ttu-id="27c3f-1281">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1281">tx_queue_flush</span></span>
- <span data-ttu-id="27c3f-1282">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1282">tx_queue_front_send</span></span>
- <span data-ttu-id="27c3f-1283">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1283">tx_queue_info_get</span></span>
- <span data-ttu-id="27c3f-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="27c3f-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1286">tx_queue_receive</span></span>
- <span data-ttu-id="27c3f-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1287">tx_queue_send</span></span>
- <span data-ttu-id="27c3f-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="27c3f-1289">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1289">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="27c3f-1290">Obtener información acerca del rendimiento del sistema de una cola</span><span class="sxs-lookup"><span data-stu-id="27c3f-1290">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1291">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1291">Prototype</span></span>

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27c3f-1292">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1292">Description</span></span>

<span data-ttu-id="27c3f-1293">Este servicio recupera información sobre el rendimiento de todas las colas del sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1293">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-1294">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1294">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1295">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1295">Parameters</span></span>

- <span data-ttu-id="27c3f-1296">**messages_sent**: puntero al destino del número total de solicitudes de envío realizadas en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1296">**messages_sent** Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="27c3f-1297">**messages_received**: puntero al destino del número total de solicitudes de recepción realizadas en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1297">**messages_received** Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="27c3f-1298">**empty_suspensions**: puntero al destino del número total de suspensiones de cola vacías en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1298">**empty_suspensions** Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="27c3f-1299">**full_suspensions**: puntero al destino del número total de suspensiones de cola completas en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1299">**full_suspensions** Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="27c3f-1300">**full_errors**: puntero al destino del número total de errores de cola completos en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1300">**full_errors** Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="27c3f-1301">**timeouts**: puntero al destino del número total de tiempos de espera de suspensión de los subprocesos en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1301">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1302">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1302">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

<span data-ttu-id="27c3f-1303">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1303">**Return Values**</span></span>

- <span data-ttu-id="27c3f-1304">**TX_SUCCESS** (0x00): rendimiento del sistema de la cola obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1304">**TX_SUCCESS** (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="27c3f-1305">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1306">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1306">Allowed From</span></span>

<span data-ttu-id="27c3f-1307">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1307">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1308">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1308">Example</span></span>

```c
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on all previously created
queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1309">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1309">See Also</span></span>

- <span data-ttu-id="27c3f-1310">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1310">tx_queue_create</span></span>
- <span data-ttu-id="27c3f-1311">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1311">tx_queue_delete</span></span>
- <span data-ttu-id="27c3f-1312">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1312">tx_queue_flush</span></span>
- <span data-ttu-id="27c3f-1313">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1313">tx_queue_front_send</span></span>
- <span data-ttu-id="27c3f-1314">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1314">tx_queue_info_get</span></span>
- <span data-ttu-id="27c3f-1315">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1315">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1316">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1316">tx_queue_prioritize</span></span>
- <span data-ttu-id="27c3f-1317">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1317">tx_queue_receive</span></span>
- <span data-ttu-id="27c3f-1318">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1318">tx_queue_send</span></span>
- <span data-ttu-id="27c3f-1319">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1319">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="27c3f-1320">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1320">tx_queue_prioritize</span></span>

<span data-ttu-id="27c3f-1321">Clasificar por orden de prioridad la lista de suspensiones de una cola</span><span class="sxs-lookup"><span data-stu-id="27c3f-1321">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1322">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1322">Prototype</span></span>

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-1323">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1323">Description</span></span>

<span data-ttu-id="27c3f-1324">Este servicio coloca el subproceso de prioridad más alta suspendido para un mensaje (o para colocar un mensaje) en esta cola al principio de la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1324">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span>

<span data-ttu-id="27c3f-1325">Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1325">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1326">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1326">Parameters</span></span>

- <span data-ttu-id="27c3f-1327">**queue_ptr**: puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1327">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1328">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1328">Return Values</span></span>

- <span data-ttu-id="27c3f-1329">**TX_SUCCESS** (0x00): cola clasificada por orden de prioridad correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1329">**TX_SUCCESS** (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="27c3f-1330">**TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1330">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1331">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1331">Allowed From</span></span>

<span data-ttu-id="27c3f-1332">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1332">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1333">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1333">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1334">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-1334">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1335">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1335">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Ensure that the highest priority thread will receive
the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_queue_send or tx_queue_front_send call made
to this queue will wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1336">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1336">See Also</span></span>

- <span data-ttu-id="27c3f-1337">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1337">tx_queue_create</span></span>
- <span data-ttu-id="27c3f-1338">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1338">tx_queue_delete</span></span>
- <span data-ttu-id="27c3f-1339">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1339">tx_queue_flush</span></span>
- <span data-ttu-id="27c3f-1340">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1340">tx_queue_front_send</span></span>
- <span data-ttu-id="27c3f-1341">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1341">tx_queue_info_get</span></span>
- <span data-ttu-id="27c3f-1342">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1342">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1343">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1343">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1344">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1344">tx_queue_receive</span></span>
- <span data-ttu-id="27c3f-1345">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1345">tx_queue_send</span></span>
- <span data-ttu-id="27c3f-1346">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1346">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="27c3f-1347">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1347">tx_queue_receive</span></span>

<span data-ttu-id="27c3f-1348">Obtener un mensaje de la cola de mensajes</span><span class="sxs-lookup"><span data-stu-id="27c3f-1348">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1349">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1349">Prototype</span></span>

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27c3f-1350">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1350">Description</span></span>

<span data-ttu-id="27c3f-1351">Este servicio recupera un mensaje de la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1351">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="27c3f-1352">El mensaje recuperado se **copia** de la cola en el área de memoria especificada por el puntero de destino.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1352">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="27c3f-1353">A continuación, ese mensaje se quita de la cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1353">That message is then removed from the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-1354">*El área de memoria de destino especificada debe ser lo suficientemente grande como para contener el mensaje; es decir, el destino del mensaje al que apunta* \***destination_ptr** _ _debe ser al menos tan grande como el tamaño de mensaje de esta cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1354">*The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by* \***destination_ptr** _ _must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="27c3f-1355">De lo contrario, si el destino no es lo suficientemente grande, se producen daños en la memoria de la siguiente área de memoria.\*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1355">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1356">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1356">Parameters</span></span>

- <span data-ttu-id="27c3f-1357">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1357">**queue_ptr**</span></span> <br><span data-ttu-id="27c3f-1358">Puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1358">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="27c3f-1359">**destination_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1359">**destination_ptr**</span></span> <br><span data-ttu-id="27c3f-1360">Ubicación donde se va a copiar el mensaje.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1360">Location of where to copy the message.</span></span>
- <span data-ttu-id="27c3f-1361">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1361">**wait_option**</span></span> <br><span data-ttu-id="27c3f-1362">Define el comportamiento del servicio si la cola de mensajes está vacía.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1362">Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="27c3f-1363">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="27c3f-1363">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27c3f-1364">**TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1364">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27c3f-1365">Esta es la única opción válida si se llama al servicio desde un elemento que no es un subproceso; por ejemplo, inicialización, temporizador o ISR.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1365">This is the only valid option if the service is called from a non-thread; e.g.,  Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="27c3f-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya un mensaje disponible.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>
  - <span data-ttu-id="27c3f-1367">valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido a la espera de un mensaje.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1367">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1368">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1368">Return Values</span></span>

- <span data-ttu-id="27c3f-1369">**TX_SUCCESS** (0x00): mensaje recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1369">**TX_SUCCESS** (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="27c3f-1370">**TX_DELETED** (0x01): la cola de mensajes se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1370">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27c3f-1371">**TX_QUEUE_EMPTY** (0x0A): el servicio no pudo recuperar un mensaje porque la cola estaba vacía durante el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1371">**TX_QUEUE_EMPTY** (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="27c3f-1372">**TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1372">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27c3f-1373">**TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1373">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="27c3f-1374">**TX_PTR_ERROR** (0x03): puntero de destino no válido para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1374">**TX_PTR_ERROR** (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="27c3f-1375">**TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1375">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1376">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1376">Allowed From</span></span>

<span data-ttu-id="27c3f-1377">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1377">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1378">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1378">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1379">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-1379">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1380">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1380">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
empty, suspend until a message is present. Note that
this suspension is only possible from application
threads. */
status = tx_queue_receive(&my_queue, my_message,
    TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
"my_message." */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1381">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1381">See Also</span></span>

- <span data-ttu-id="27c3f-1382">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1382">tx_queue_create</span></span>
- <span data-ttu-id="27c3f-1383">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1383">tx_queue_delete</span></span>
- <span data-ttu-id="27c3f-1384">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1384">tx_queue_flush</span></span>
- <span data-ttu-id="27c3f-1385">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1385">tx_queue_front_send</span></span>
- <span data-ttu-id="27c3f-1386">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1386">tx_queue_info_get</span></span>
- <span data-ttu-id="27c3f-1387">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1387">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1388">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1388">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1389">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1389">tx_queue_prioritize</span></span>
- <span data-ttu-id="27c3f-1390">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1390">tx_queue_send</span></span>
- <span data-ttu-id="27c3f-1391">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1391">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="27c3f-1392">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1392">tx_queue_send</span></span>

<span data-ttu-id="27c3f-1393">Enviar un mensaje a la cola de mensajes</span><span class="sxs-lookup"><span data-stu-id="27c3f-1393">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1394">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1394">Prototype</span></span>

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27c3f-1395">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1395">Description</span></span>

<span data-ttu-id="27c3f-1396">Este servicio envía un mensaje a la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1396">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="27c3f-1397">El mensaje enviado se **copia** en la cola desde el área de memoria especificada por el puntero de origen.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1397">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1398">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1398">Parameters</span></span>
- <span data-ttu-id="27c3f-1399">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1399">**queue_ptr**</span></span> <br><span data-ttu-id="27c3f-1400">Puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1400">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="27c3f-1401">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1401">**source_ptr**</span></span> <br><span data-ttu-id="27c3f-1402">Puntero al mensaje.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1402">Pointer to the message.</span></span>
- <span data-ttu-id="27c3f-1403">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1403">**wait_option**</span></span> <br><span data-ttu-id="27c3f-1404">Define el comportamiento del servicio si la cola de mensajes está llena.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1404">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="27c3f-1405">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="27c3f-1405">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27c3f-1406">**TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1406">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27c3f-1407">*Esta es la única opción válida si se llama al servicio desde un elemento distinto de un _ _subproceso; por ejemplo, inicialización, temporizador o ISR*.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1407">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="27c3f-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya espacio en la cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="27c3f-1409">valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido a la espera de que haya espacio en la cola.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1409">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1410">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1410">Return Values</span></span>

- <span data-ttu-id="27c3f-1411">**TX_SUCCESS** (0x00): mensaje enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1411">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="27c3f-1412">**TX_DELETED** (0x01): la cola de mensajes se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1412">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27c3f-1413">**TX_QUEUE_FULL** (0x0B): el servicio no pudo enviar el mensaje porque la cola estaba llena durante el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1413">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="27c3f-1414">**TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1414">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27c3f-1415">**TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1415">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="27c3f-1416">**TX_PTR_ERROR** (0x03): puntero de origen no válido para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1416">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="27c3f-1417">**TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1417">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1418">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1418">Allowed From</span></span>

<span data-ttu-id="27c3f-1419">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1419">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1420">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1420">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1421">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-1421">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1422">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1422">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
regardless of success. This wait option is used for
calls from initialization, timers, and ISRs. */
status = tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
queue. */
```

<span data-ttu-id="27c3f-1423">**Vea también**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1423">**See Also**</span></span>

- <span data-ttu-id="27c3f-1424">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1424">tx_queue_create</span></span>
- <span data-ttu-id="27c3f-1425">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1425">tx_queue_delete</span></span>
- <span data-ttu-id="27c3f-1426">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1426">tx_queue_flush</span></span>
- <span data-ttu-id="27c3f-1427">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1427">tx_queue_front_send</span></span>
- <span data-ttu-id="27c3f-1428">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1428">tx_queue_info_get</span></span>
- <span data-ttu-id="27c3f-1429">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1429">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1430">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1430">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1431">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1431">tx_queue_prioritize</span></span>
- <span data-ttu-id="27c3f-1432">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1432">tx_queue_receive</span></span>
- <span data-ttu-id="27c3f-1433">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1433">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="27c3f-1434">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1434">tx_queue_send_notify</span></span>

<span data-ttu-id="27c3f-1435">Notificar a la aplicación al enviar un mensaje a la cola</span><span class="sxs-lookup"><span data-stu-id="27c3f-1435">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1436">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1436">Prototype</span></span>

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a><span data-ttu-id="27c3f-1437">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1437">Description</span></span>

<span data-ttu-id="27c3f-1438">Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se envía un mensaje a la cola especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1438">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="27c3f-1439">La aplicación define el procesamiento de la devolución de llamada de notificación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1439">The processing of the notification callback is defined by the application.</span></span>

>[!NOTE]
> <span data-ttu-id="27c3f-1440">*La devolución de llamada de notificación de envío a la cola de la aplicación no puede llamar a ninguna API de ThreadX con una opción de suspensión.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1440">*The application's queue send notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1441">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1441">Parameters</span></span>

- <span data-ttu-id="27c3f-1442">**queue_ptr**: puntero a una cola creada previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1442">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="27c3f-1443">**queue_send_notify**: puntero a la función de notificación de envío a la cola de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1443">**queue_send_notify** Pointer to application's queue send notification function.</span></span> <span data-ttu-id="27c3f-1444">Si este valor es TX_NULL, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1444">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1445">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1445">Return Values</span></span>

- <span data-ttu-id="27c3f-1446">**TX_SUCCESS** (0x00): notificación de envío a la cola registrada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1446">**TX_SUCCESS** (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="27c3f-1447">**TX_QUEUE_ERROR** (0x09): puntero de cola no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1447">**TX_QUEUE_ERROR** (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="27c3f-1448">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema se compiló con las funcionalidades de notificación deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1449">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1449">Allowed From</span></span>

<span data-ttu-id="27c3f-1450">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1450">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1451">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1451">Example</span></span>

```c
TX_QUEUE my_queue;
/* Register the "my_queue_send_notify" function for monitoring
messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
    /* A message was just sent to this queue! */
}
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1452">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1452">See Also</span></span>

- <span data-ttu-id="27c3f-1453">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1453">tx_queue_create</span></span>
- <span data-ttu-id="27c3f-1454">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1454">tx_queue_delete</span></span>
- <span data-ttu-id="27c3f-1455">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27c3f-1455">tx_queue_flush</span></span>
- <span data-ttu-id="27c3f-1456">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1456">tx_queue_front_send</span></span>
- <span data-ttu-id="27c3f-1457">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1457">tx_queue_info_get</span></span>
- <span data-ttu-id="27c3f-1458">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1458">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1459">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1459">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1460">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1460">tx_queue_prioritize</span></span>
- <span data-ttu-id="27c3f-1461">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27c3f-1461">tx_queue_receive</span></span>
- <span data-ttu-id="27c3f-1462">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27c3f-1462">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="27c3f-1463">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1463">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="27c3f-1464">Colocar una instancia en el semáforo de recuento con límite superior</span><span class="sxs-lookup"><span data-stu-id="27c3f-1464">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1465">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1465">Prototype</span></span>

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a><span data-ttu-id="27c3f-1466">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1466">Description</span></span>

<span data-ttu-id="27c3f-1467">Este servicio coloca una instancia en el semáforo de recuento especificado, lo que en realidad incrementa el semáforo de recuento en uno.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1467">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="27c3f-1468">Si el valor actual del semáforo de recuento es mayor o igual que el límite superior especificado, la instancia no se colocará y se devolverá un error TX_CEILING_EXCEEDED.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1468">If the counting semaphore's current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1469">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1469">Parameters</span></span>

- <span data-ttu-id="27c3f-1470">**semaphore_ptr**: puntero a un semáforo creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1470">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="27c3f-1471">**ceiling**: límite máximo permitido para el semáforo (el rango de valores válidos oscila entre 1 y 0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="27c3f-1471">**ceiling** Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1472">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1472">Return Values</span></span>

- <span data-ttu-id="27c3f-1473">**TX_SUCCESS** (0x00): límite superior del semáforo colocado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1473">**TX_SUCCESS (0x00)** Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="27c3f-1474">**TX_CEILING_EXCEEDED** (0x21): la solicitud Put excede el límite superior.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1474">**TX_CEILING_EXCEEDED** (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="27c3f-1475">**TX_INVALID_CEILING** (0x22): se proporcionó un valor no válido de cero para el límite superior.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1475">**TX_INVALID_CEILING** (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="27c3f-1476">**TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1476">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1477">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1477">Allowed From</span></span>

<span data-ttu-id="27c3f-1478">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1478">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1479">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1479">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1480">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1480">See Also</span></span>

- <span data-ttu-id="27c3f-1481">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1481">tx_semaphore_create</span></span>
- <span data-ttu-id="27c3f-1482">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1482">tx_semaphore_delete</span></span>
- <span data-ttu-id="27c3f-1483">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1483">tx_semaphore_get</span></span>
- <span data-ttu-id="27c3f-1484">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1484">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27c3f-1485">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1485">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1486">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1486">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1487">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1487">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27c3f-1488">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1488">tx_semaphore_put</span></span>
- <span data-ttu-id="27c3f-1489">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1489">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="27c3f-1490">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1490">tx_semaphore_create</span></span>

<span data-ttu-id="27c3f-1491">Crear un semáforo de recuento</span><span class="sxs-lookup"><span data-stu-id="27c3f-1491">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1492">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1492">Prototype</span></span>

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a><span data-ttu-id="27c3f-1493">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1493">Description</span></span>

<span data-ttu-id="27c3f-1494">Este servicio crea un semáforo de recuento para la sincronización entre subprocesos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1494">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="27c3f-1495">El recuento inicial del semáforo se especifica como un parámetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1495">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1496">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1496">Parameters</span></span>

- <span data-ttu-id="27c3f-1497">**semaphore_ptr**: puntero a un bloque de control del semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1497">**semaphore_ptr** Pointer to a semaphore control block.</span></span>
- <span data-ttu-id="27c3f-1498">**name_ptr**: puntero al nombre del semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1498">**name_ptr** Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="27c3f-1499">**initial_count**: especifica el recuento inicial de este semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1499">**initial_count** Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="27c3f-1500">Los valores válidos oscilan entre 0x00000000 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1500">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1501">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1501">Return Values</span></span>

- <span data-ttu-id="27c3f-1502">**TX_SUCCESS** (0x00): semáforo creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1502">**TX_SUCCESS** (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="27c3f-1503">**TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1503">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="27c3f-1504">El puntero tiene un valor NULL o el semáforo ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1504">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="27c3f-1505">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1505">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1506">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1506">Allowed From</span></span>

<span data-ttu-id="27c3f-1507">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1508">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1508">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1509">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-1509">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1510">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1510">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Create a counting semaphore whose initial value is 1.
This is typically the technique used to make a binary
semaphore. Binary semaphores are used to provide
protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
    "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
use. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1511">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1511">See Also</span></span>

- <span data-ttu-id="27c3f-1512">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1512">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27c3f-1513">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1513">tx_semaphore_delete</span></span>
- <span data-ttu-id="27c3f-1514">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1514">tx_semaphore_get</span></span>
- <span data-ttu-id="27c3f-1515">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1515">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27c3f-1516">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1516">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1517">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1517">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1518">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1518">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27c3f-1519">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1519">tx_semaphore_put</span></span>
- <span data-ttu-id="27c3f-1520">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1520">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="27c3f-1521">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1521">tx_semaphore_delete</span></span>

<span data-ttu-id="27c3f-1522">Eliminar un semáforo de recuento</span><span class="sxs-lookup"><span data-stu-id="27c3f-1522">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1523">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1523">Prototype</span></span>
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-1524">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1524">Description</span></span>

<span data-ttu-id="27c3f-1525">Este servicio elimina el semáforo de recuento especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1525">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="27c3f-1526">Todos los subprocesos suspendidos en espera de una instancia del semáforo se reanudan y se les asigna un estado de devolución TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1526">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-1527">*La aplicación debe asegurarse de que se complete (o deshabilite) una devolución de llamada de notificación de colocación para este semáforo antes de eliminarlo. Además, la aplicación debe impedir cualquier uso futuro de los semáforos eliminados.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1527">*The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore. In addition, the application must prevent all future use of a deleted semaphore.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1528">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1528">Parameters</span></span>

- <span data-ttu-id="27c3f-1529">**semaphore_ptr**: puntero a un semáforo creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1529">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1530">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1530">Return Values</span></span>

- <span data-ttu-id="27c3f-1531">**TX_SUCCESS** (0x00): semáforo de recuento eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1531">**TX_SUCCESS** (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="27c3f-1532">**TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo de recuento no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1532">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="27c3f-1533">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1533">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1534">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1534">Allowed From</span></span>

<span data-ttu-id="27c3f-1535">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1535">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1536">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1536">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1537">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-1537">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1538">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1538">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

<span data-ttu-id="27c3f-1539">**Vea también**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1539">**See Also**</span></span>

- <span data-ttu-id="27c3f-1540">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1540">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27c3f-1541">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1541">tx_semaphore_create</span></span>
- <span data-ttu-id="27c3f-1542">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1542">tx_semaphore_get</span></span>
- <span data-ttu-id="27c3f-1543">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1543">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27c3f-1544">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1544">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1545">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1545">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1546">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1546">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27c3f-1547">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1547">tx_semaphore_put</span></span>
- <span data-ttu-id="27c3f-1548">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1548">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="27c3f-1549">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1549">tx_semaphore_get</span></span>

<span data-ttu-id="27c3f-1550">Obtener una instancia del semáforo de recuento</span><span class="sxs-lookup"><span data-stu-id="27c3f-1550">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1551">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1551">Prototype</span></span>

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27c3f-1552">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1552">Description</span></span>

<span data-ttu-id="27c3f-1553">Este servicio recupera una instancia (un solo recuento) del semáforo de recuento especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1553">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="27c3f-1554">Como resultado, el recuento del semáforo especificado se reduce en uno.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1554">As a result, the specified semaphore's count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1555">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1555">Parameters</span></span>

- <span data-ttu-id="27c3f-1556">**semaphore_ptr**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1556">**semaphore_ptr**</span></span> <br><span data-ttu-id="27c3f-1557">Puntero a un semáforo de recuento creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1557">Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="27c3f-1558">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1558">**wait_option**</span></span> <br><span data-ttu-id="27c3f-1559">Define el comportamiento del servicio si no hay ninguna instancia del semáforo disponible; es decir, el recuento del semáforo es cero.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1559">Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="27c3f-1560">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="27c3f-1560">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27c3f-1561">**TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1561">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27c3f-1562">*Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1562">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="27c3f-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya una instancia del semáforo disponible.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span>
  - <span data-ttu-id="27c3f-1564">valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando una instancia del semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1564">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1565">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1565">Return Values</span></span>

- <span data-ttu-id="27c3f-1566">**TX_SUCCESS** (0x00): instancia del semáforo recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1566">**TX_SUCCESS** (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="27c3f-1567">**TX_DELETED** (0x01): el semáforo de recuento se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1567">**TX_DELETED** (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27c3f-1568">**TX_NO_INSTANCE**: (0x0D) el servicio no pudo recuperar una instancia del semáforo de recuento (el recuento del semáforo es cero en el tiempo de espera especificado).</span><span class="sxs-lookup"><span data-stu-id="27c3f-1568">**TX_NO_INSTANCE** (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="27c3f-1569">**TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1569">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27c3f-1570">**TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo de recuento no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1570">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="27c3f-1571">**TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1571">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1572">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1572">Allowed From</span></span>

<span data-ttu-id="27c3f-1573">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1573">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1574">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1574">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1575">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-1575">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1576">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1576">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Get a semaphore instance from the semaphore
"my_semaphore." If the semaphore count is zero,
suspend until an instance becomes available.
Note that this suspension is only possible from
application threads. */
status = tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
an instance of the semaphore. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1577">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1577">See Also</span></span>

- <span data-ttu-id="27c3f-1578">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1578">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27c3f-1579">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1579">tx_semaphore_create</span></span>
- <span data-ttu-id="27c3f-1580">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1580">tx_semahore_delete</span></span>
- <span data-ttu-id="27c3f-1581">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1581">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27c3f-1582">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1582">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1583">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1583">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27c3f-1584">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1584">tx_semaphore_put</span></span>
- <span data-ttu-id="27c3f-1585">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1585">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="27c3f-1586">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1586">tx_semaphore_info_get</span></span>

<span data-ttu-id="27c3f-1587">Recuperar información acerca de un semáforo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1587">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1588">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1588">Prototype</span></span>

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a><span data-ttu-id="27c3f-1589">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1589">Description</span></span>

<span data-ttu-id="27c3f-1590">Este servicio recupera información sobre el semáforo especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1590">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1591">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1591">Parameters</span></span>

- <span data-ttu-id="27c3f-1592">**semaphore_ptr**: puntero a un bloque de control del semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1592">**semaphore_ptr** Pointer to semaphore control block.</span></span>
- <span data-ttu-id="27c3f-1593">**name**: puntero al destino del puntero al nombre del semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1593">**name** Pointer to destination for the pointer to the semaphore's name.</span></span>
- <span data-ttu-id="27c3f-1594">**current_value**: puntero al destino del recuento actual del semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1594">**current_value** Pointer to destination for the current semaphore's count.</span></span>
- <span data-ttu-id="27c3f-1595">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1595">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="27c3f-1596">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1596">**suspended_count** Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="27c3f-1597">**next_semaphore**: puntero al destino del puntero del siguiente semáforo creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1597">**next_semaphore** Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1598">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1598">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1599">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1599">Return Values</span></span>

- <span data-ttu-id="27c3f-1600">**TX_SUCCESS** (0x00): recuperación de la información.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1600">**TX_SUCCESS** (0x00) information retrieval.</span></span>

- <span data-ttu-id="27c3f-1601">**TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1601">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1602">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1602">Allowed From</span></span>

<span data-ttu-id="27c3f-1603">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1603">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1604">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1604">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1605">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-1605">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1606">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1606">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR *name;
ULONG current_value;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT status;

/* Retrieve information about the previously created
semaphore "my_semaphore." */
status = tx_semaphore_info_get(&my_semaphore, &name,
    &current_value,
    &first_suspended, &suspended_count,
    &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1607">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1607">See Also</span></span>

- <span data-ttu-id="27c3f-1608">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1608">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27c3f-1609">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1609">tx_semaphore_create</span></span>
- <span data-ttu-id="27c3f-1610">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1610">tx_semaphore_delete</span></span>
- <span data-ttu-id="27c3f-1611">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1611">tx_semaphore_get</span></span>
- <span data-ttu-id="27c3f-1612">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1612">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1613">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1613">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1614">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1614">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27c3f-1615">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1615">tx_semaphore_put</span></span>
- <span data-ttu-id="27c3f-1616">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1616">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="27c3f-1617">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1617">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="27c3f-1618">Obtener información acerca del rendimiento del semáforo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1618">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1619">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1619">Prototype</span></span>

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27c3f-1620">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1620">Description</span></span>

<span data-ttu-id="27c3f-1621">Este servicio recupera información sobre el rendimiento del semáforo especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1621">This service retrieves performance information about the specified semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-1622">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1622">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

<span data-ttu-id="27c3f-1623">**Parámetros**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1623">**Parameters**</span></span>

-  <span data-ttu-id="27c3f-1624">**semaphore_ptr**: puntero a un semáforo creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1624">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
-  <span data-ttu-id="27c3f-1625">**puts**: puntero al destino del número de solicitudes Put realizadas en este semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1625">**puts** Pointer to destination for the number of put requests performed on this semaphore.</span></span>
-  <span data-ttu-id="27c3f-1626">**gets**: puntero al destino del número de solicitudes Get realizadas en este semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1626">**gets** Pointer to destination for the number of get requests performed on this semaphore.</span></span>
-  <span data-ttu-id="27c3f-1627">**suspensions**: puntero al destino del número de suspensiones de los subprocesos de este semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1627">**suspensions** Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
-  <span data-ttu-id="27c3f-1628">**timeouts**: puntero al destino del número de tiempos de espera de suspensión de los subprocesos en este semáforo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1628">**timeouts** Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1629">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1629">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1630">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1630">Return Values</span></span>

- <span data-ttu-id="27c3f-1631">**TX_SUCCESS** (0x00): rendimiento del semáforo obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1631">**TX_SUCCESS** (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="27c3f-1632">**TX_PTR_ERROR** (0x03): puntero del semáforo no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1632">**TX_PTR_ERROR** (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="27c3f-1633">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1634">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1634">Allowed From</span></span>

<span data-ttu-id="27c3f-1635">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1635">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1636">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1636">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created
semaphore. */
status = tx_semaphore_performance_info_get(&my_semaphore, &puts,
    &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1637">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1637">See Also</span></span>

- <span data-ttu-id="27c3f-1638">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1638">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27c3f-1639">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1639">tx_semaphore_create</span></span>
- <span data-ttu-id="27c3f-1640">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1640">tx_semaphore_delete</span></span>
- <span data-ttu-id="27c3f-1641">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1641">tx_semaphore_get</span></span>
- <span data-ttu-id="27c3f-1642">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1642">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27c3f-1643">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1643">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1644">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1644">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27c3f-1645">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1645">tx_semaphore_put</span></span>
- <span data-ttu-id="27c3f-1646">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1646">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="27c3f-1647">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1647">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="27c3f-1648">Obtener información acerca del rendimiento del sistema de un semáforo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1648">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1649">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1649">Prototype</span></span>

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27c3f-1650">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1650">Description</span></span>

<span data-ttu-id="27c3f-1651">Este servicio recupera información sobre el rendimiento de todos los semáforos del sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1651">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-1652">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1652">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1653">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1653">Parameters</span></span>

- <span data-ttu-id="27c3f-1654">**puts**: puntero al destino del número total de solicitudes Put realizadas en todos los semáforos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1654">**puts** Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="27c3f-1655">**gets**: puntero al destino del número total de solicitudes Get realizadas en todos los semáforos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1655">**gets** Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="27c3f-1656">**suspensions**: puntero al destino del número total de suspensiones de los subprocesos de todos los semáforos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1656">**suspensions** Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="27c3f-1657">**timeouts**: puntero al destino del número total de tiempos de espera de suspensión de los subprocesos de todos los semáforos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1657">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1658">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1658">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1659">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1659">Return Values</span></span>

- <span data-ttu-id="27c3f-1660">**TX_SUCCESS** (0x00): obtención del rendimiento del sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1660">**TX_SUCCESS** (0x00) system performance get.</span></span>
- <span data-ttu-id="27c3f-1661">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1662">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1662">Allowed From</span></span>

<span data-ttu-id="27c3f-1663">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1663">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1664">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1664">Example</span></span>

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created
semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1665">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1665">See Also</span></span>

- <span data-ttu-id="27c3f-1666">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1666">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27c3f-1667">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1667">tx_semaphore_create</span></span>
- <span data-ttu-id="27c3f-1668">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1668">tx_semaphore_delete</span></span>
- <span data-ttu-id="27c3f-1669">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1669">tx_semaphore_get</span></span>
- <span data-ttu-id="27c3f-1670">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1670">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27c3f-1671">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1671">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1672">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1672">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27c3f-1673">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1673">tx_semaphore_put</span></span>
- <span data-ttu-id="27c3f-1674">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1674">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="27c3f-1675">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1675">tx_semaphore_prioritize</span></span>

<span data-ttu-id="27c3f-1676">Clasificar por orden de prioridad la lista de suspensiones de un semáforo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1676">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1677">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1677">Prototype</span></span>

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-1678">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1678">Description</span></span>

<span data-ttu-id="27c3f-1679">Este servicio coloca el subproceso de prioridad más alta suspendido para una instancia del semáforo al principio de la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1679">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="27c3f-1680">Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1680">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1681">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1681">Parameters</span></span>

- <span data-ttu-id="27c3f-1682">**semaphore_ptr**: puntero a un semáforo creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1682">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1683">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1683">Return Values</span></span>

- <span data-ttu-id="27c3f-1684">**TX_SUCCESS** (0x00): semáforo clasificado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1684">**TX_SUCCESS** (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="27c3f-1685">**TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo de recuento no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1685">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1686">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1686">Allowed From</span></span>

<span data-ttu-id="27c3f-1687">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1687">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1688">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1688">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1689">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-1689">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1690">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1690">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Ensure that the highest priority thread will receive
the next instance of this semaphore. */
status = tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_semaphore_put call made to this semaphore will
wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1691">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1691">See Also</span></span>

- <span data-ttu-id="27c3f-1692">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1692">tx_semaphore_create</span></span>
- <span data-ttu-id="27c3f-1693">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1693">tx_semaphore_delete</span></span>
- <span data-ttu-id="27c3f-1694">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1694">tx_semaphore_get</span></span>
- <span data-ttu-id="27c3f-1695">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1695">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27c3f-1696">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1696">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="27c3f-1697">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1697">tx_semaphore_put</span></span>

<span data-ttu-id="27c3f-1698">Colocar una instancia en el semáforo de recuento</span><span class="sxs-lookup"><span data-stu-id="27c3f-1698">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1699">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1699">Prototype</span></span>

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-1700">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1700">Description</span></span>

<span data-ttu-id="27c3f-1701">Este servicio coloca una instancia en el semáforo de recuento especificado, lo que en realidad incrementa el semáforo de recuento en uno.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1701">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1702">*Si se llama a este servicio cuando el semáforo es todo unos (OxFFFFFFFF), la nueva operación Put hará que el semáforo se restablezca a cero.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1702">*If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1703">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1703">Parameters</span></span>

- <span data-ttu-id="27c3f-1704">**semaphore_ptr**: puntero al bloque de control del semáforo de recuento creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1704">**semaphore_ptr** Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1705">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1705">Return Values</span></span>

- <span data-ttu-id="27c3f-1706">**TX_SUCCESS** (0x00): semáforo colocado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1706">**TX_SUCCESS** (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="27c3f-1707">**TX_SEMAPHORE_ERROR** (0x0C): puntero al semáforo de recuento no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1707">**TX_SEMAPHORE_ERROR** (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1708">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1708">Allowed From</span></span>

<span data-ttu-id="27c3f-1709">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1709">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1710">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1710">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1711">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-1711">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1712">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1712">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1713">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1713">See Also</span></span>

- <span data-ttu-id="27c3f-1714">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1714">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27c3f-1715">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1715">tx_semaphore_create</span></span>
- <span data-ttu-id="27c3f-1716">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1716">tx_semaphore_delete</span></span>
- <span data-ttu-id="27c3f-1717">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1717">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27c3f-1718">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1718">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1719">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1719">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1720">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1720">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27c3f-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="27c3f-1722">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1722">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="27c3f-1723">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1723">tx_semaphore_put_notify</span></span>

<span data-ttu-id="27c3f-1724">Notificar a la aplicación cuando se coloque el semáforo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1724">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1725">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1725">Prototype</span></span>

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a><span data-ttu-id="27c3f-1726">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1726">Description</span></span>

<span data-ttu-id="27c3f-1727">Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se coloca el semáforo especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1727">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="27c3f-1728">La aplicación define el procesamiento de la devolución de llamada de notificación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1728">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1729">*La devolución de llamada de notificación del semáforo de la aplicación no puede llamar a ninguna API de ThreadX con una opción de suspensión.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1729">*The application's semaphore notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1730">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1730">Parameters</span></span>

- <span data-ttu-id="27c3f-1731">**semaphore_ptr**: puntero a un semáforo creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1731">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="27c3f-1732">**semaphore_put_notify**: puntero a la función de notificación de colocación del semáforo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1732">**semaphore_put_notify** Pointer to application's semaphore put notification function.</span></span> <span data-ttu-id="27c3f-1733">Si este valor es TX_NULL, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1733">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1734">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1734">Return Values</span></span>

- <span data-ttu-id="27c3f-1735">**TX_SUCCESS** (0x00): notificación de colocación del semáforo registrada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1735">**TX_SUCCESS** (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="27c3f-1736">**TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1736">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="27c3f-1737">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema se compiló con las funcionalidades de notificación deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1738">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1738">Allowed From</span></span>

<span data-ttu-id="27c3f-1739">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1739">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1740">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1740">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
the put operations on the semaphore "my_semaphore." */
status = tx_semaphore_put_notify(&my_semaphore, my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
was successfully registered. */
void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
    /* The semaphore was just put! */
}
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1741">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1741">See Also</span></span>

- <span data-ttu-id="27c3f-1742">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1742">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27c3f-1743">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1743">tx_semaphore_create</span></span>
- <span data-ttu-id="27c3f-1744">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1744">tx_semaphore_delete</span></span>
- <span data-ttu-id="27c3f-1745">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1745">tx_semaphore_get</span></span>
- <span data-ttu-id="27c3f-1746">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1746">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27c3f-1747">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1747">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1748">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1748">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1749">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27c3f-1749">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27c3f-1750">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27c3f-1750">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="27c3f-1751">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1751">tx_thread_create</span></span>

<span data-ttu-id="27c3f-1752">Crear un subproceso de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-1752">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1753">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1753">Prototype</span></span>

```c
UINT tx_thread_create(
    TX_THREAD *thread_ptr,
    CHAR *name_ptr, 
    VOID (*entry_function)(ULONG),
    ULONG entry_input, 
    VOID *stack_start,
    ULONG stack_size, 
    UINT priority,
    UINT preempt_threshold, 
    ULONG time_slice,
    UINT auto_start);
```

### <a name="description"></a><span data-ttu-id="27c3f-1754">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1754">Description</span></span>

<span data-ttu-id="27c3f-1755">Este servicio crea un subproceso de aplicación que inicia la ejecución en la función de entrada de tarea especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1755">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="27c3f-1756">La pila, la prioridad, el umbral de adelantamiento y la porción de tiempo se encuentran entre los atributos especificados por los parámetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1756">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="27c3f-1757">Además, también se especifica el estado de ejecución inicial del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1757">In addition, the initial execution state of the thread is also specified.</span></span>

<span data-ttu-id="27c3f-1758">**Parámetros**</span><span class="sxs-lookup"><span data-stu-id="27c3f-1758">**Parameters**</span></span>

- <span data-ttu-id="27c3f-1759">**thread_ptr**: puntero a un bloque de control del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1759">**thread_ptr** Pointer to a thread control block.</span></span>
- <span data-ttu-id="27c3f-1760">**name_ptr**: puntero al nombre del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1760">**name_ptr** Pointer to the name of the thread.</span></span>
- <span data-ttu-id="27c3f-1761">**entry_function**: especifica la función de C inicial para la ejecución del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1761">**entry_function** Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="27c3f-1762">Cuando un subproceso vuelve de esta función de entrada, se le asigna un estado *completado* y se suspende indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1762">When a thread returns from this entry function, it is placed in a *completed* state and suspended indefinitely.</span></span>
- <span data-ttu-id="27c3f-1763">**entry_input**: valor de 32 bits que se pasa a la función de entrada del subproceso cuando se ejecuta por primera vez.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1763">**entry_input** A 32-bit value that is passed to the thread's entry function when it first executes.</span></span> <span data-ttu-id="27c3f-1764">Exclusivamente la aplicación determina el uso de esta entrada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1764">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="27c3f-1765">**stack_start**: dirección de inicio del área de memoria de la pila.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1765">**stack_start** Starting address of the stack's memory area.</span></span>
- <span data-ttu-id="27c3f-1766">**stack_size**: número de bytes en el área de memoria de la pila.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1766">**stack_size** Number bytes in the stack memory area.</span></span> <span data-ttu-id="27c3f-1767">El área de la pila del subproceso debe ser lo suficientemente grande como para controlar el uso de la variable local y el anidamiento de llamadas de función en el peor de los casos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1767">The thread's stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="27c3f-1768">**priority**: prioridad numérica del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1768">**priority** Numerical priority of thread.</span></span> <span data-ttu-id="27c3f-1769">Los valores válidos oscilan entre 0 y (TX_MAX_PRIORITES-1), donde un valor de 0 representa la prioridad más alta.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1769">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="27c3f-1770">**preempt_threshold**: nivel de prioridad más alto (0 a (TX_MAX_PRIORITIES-1)) de adelantamiento deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1770">**preempt_threshold** Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="27c3f-1771">Solo se permite que prioridades superiores a este nivel adelanten a este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1771">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="27c3f-1772">Este valor debe ser menor o igual que la prioridad especificada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1772">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="27c3f-1773">Un valor igual a la prioridad del subproceso deshabilita el umbral de adelantamiento.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1773">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="27c3f-1774">**time_slice**: número de tics de temporizador que este subproceso puede ejecutar antes de que otros subprocesos preparados con la misma prioridad tengan la posibilidad de ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1774">**time_slice** Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="27c3f-1775">Tenga en cuenta que, si se usa el umbral de adelantamiento, se deshabilitan las porciones de tiempo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1775">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="27c3f-1776">Los valores de porción de tiempo válidos oscilan entre 1 y 0xFFFFFFFF (ambos incluidos).</span><span class="sxs-lookup"><span data-stu-id="27c3f-1776">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="27c3f-1777">Un valor de **TX_NO_TIME_SLICE** (un valor de 0) deshabilita las porciones de tiempo de este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1777">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

  > [!NOTE]
  > <span data-ttu-id="27c3f-1778">*El uso de porciones de tiempo provoca una ligera sobrecarga del sistema. Dado que solo son útiles en los casos en los que varios subprocesos comparten la misma prioridad, no se debe asignar una porción de tiempo a los subprocesos que tienen una prioridad única.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1778">*Using time-slicing results in a slight amount of system overhead.   Since time-slicing is only useful in cases where multiple threads   share the same priority, threads having a unique priority should not   be assigned a time-slice.*</span></span>

- <span data-ttu-id="27c3f-1779">**auto_start**: especifica si el subproceso se inicia inmediatamente o se coloca en un estado suspendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1779">**auto_start** Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="27c3f-1780">Las opciones válidas son **TX_AUTO_START** (0x01) y **TX_DONT_START** (0x00).</span><span class="sxs-lookup"><span data-stu-id="27c3f-1780">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="27c3f-1781">Si se especifica TX_DONT_START, la aplicación debe llamar posteriormente a tx_thread_resume para que se ejecute el subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1781">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1782">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1782">Return Values</span></span>

- <span data-ttu-id="27c3f-1783">**TX_SUCCESS** (0x00): subproceso creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1783">**TX_SUCCESS** (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="27c3f-1784">**TX_THREAD_ERROR** (0x0E): puntero de control del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1784">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="27c3f-1785">El puntero tiene un valor NULL o el subproceso ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1785">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="27c3f-1786">**TX_PTR_ERROR** (0x03): la dirección de inicio del punto de entrada o del área de la pila no es válida; normalmente, es NULL.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1786">**TX_PTR_ERROR** (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="27c3f-1787">**TX_SIZE_ERROR** (0x05): el tamaño del área de la pila no es válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1787">**TX_SIZE_ERROR** (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="27c3f-1788">Los subprocesos deben tener al menos **TX_MINIMUM_STACK** bytes para ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1788">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="27c3f-1789">**TX_PRIORITY_ERROR** (0x0F): prioridad del subproceso no válida. Es un valor fuera del rango de (0 a (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="27c3f-1789">**TX_PRIORITY_ERROR** (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="27c3f-1790">**TX_THRESH_ERROR** (0x18): el umbral de adelantamiento especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1790">**TX_THRESH_ERROR** (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="27c3f-1791">Este valor debe ser una prioridad válida menor o igual que la prioridad inicial del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1791">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="27c3f-1792">**TX_START_ERROR** (0x10): selección de inicio automático no válida.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1792">**TX_START_ERROR** (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="27c3f-1793">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1793">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1794">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1794">Allowed From</span></span>

<span data-ttu-id="27c3f-1795">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1795">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1796">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1796">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1797">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-1797">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1798">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1798">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Create a thread of priority 15 whose entry point is
"my_thread_entry". This thread’s stack area is 1000
bytes in size, starting at address 0x400000. The
preemption-threshold is setup to allow preemption of threads
with priorities ranging from 0 through 14. Time-slicing is
disabled. This thread is automatically put into a ready
condition. */
status = tx_thread_create(&my_thread, "my_thread_name",
    my_thread_entry, 0x1234,
    (VOID *) 0x400000, 1000,
    15, 15, TX_NO_TIME_SLICE,
    TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
for execution! */

...

/* Thread’s entry function. When "my_thread" actually
begins execution, control is transferred to this
function. */

VOID my_thread_entry (ULONG initial_input)
{
    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */
    /* The real work of the thread, including calls to
    other function should be called from here! */
    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1799">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1799">See Also</span></span>

- <span data-ttu-id="27c3f-1800">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1800">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-1801">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1801">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-1802">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1802">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-1803">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1803">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-1804">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1804">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1805">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1805">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1806">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1806">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-1807">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1807">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-1808">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-1808">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-1809">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-1809">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-1810">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-1810">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-1811">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-1811">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-1812">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1812">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-1813">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-1813">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-1814">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-1814">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-1815">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1815">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-1816">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-1816">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="27c3f-1817">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1817">tx_thread_delete</span></span>

<span data-ttu-id="27c3f-1818">Eliminar un subproceso de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-1818">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1819">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1819">Prototype</span></span>

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-1820">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1820">Description</span></span>

<span data-ttu-id="27c3f-1821">Este servicio elimina el subproceso de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1821">This service deletes the specified application thread.</span></span> <span data-ttu-id="27c3f-1822">Dado que el subproceso especificado debe estar en un estado finalizado o completado, no se puede llamar a este servicio desde un subproceso que intente eliminarse a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1822">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1823">*Es responsabilidad de la aplicación administrar el área de memoria asociada a la pila del subproceso, que está disponible una vez que se complete este servicio. Además, la aplicación debe impedir el uso de un subproceso eliminado.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1823">*It is the application's responsibility to manage the memory area associated with the thread's stack, which is available after this service completes. In addition, the application must prevent use of a deleted thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1824">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1824">Parameters</span></span>

- <span data-ttu-id="27c3f-1825">**thread_ptr**: puntero a un subproceso de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1825">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1826">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1826">Return Values</span></span>

- <span data-ttu-id="27c3f-1827">**TX_SUCCESS** (0x00): subproceso eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1827">**TX_SUCCESS** (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="27c3f-1828">**TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1828">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27c3f-1829">**TX_DELETE_ERROR** (0x11): el subproceso especificado no se encuentra en un estado finalizado o completado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1829">**TX_DELETE_ERROR** (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="27c3f-1830">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1830">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1831">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1831">Allowed From</span></span>

<span data-ttu-id="27c3f-1832">Subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="27c3f-1832">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1833">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1833">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1834">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-1834">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1835">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1835">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Delete an application thread whose control block is
"my_thread". Assume that the thread has already been
created with a call to tx_thread_create. */
status = tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1836">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1836">See Also</span></span>

- <span data-ttu-id="27c3f-1837">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1837">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-1838">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1838">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-1839">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1839">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-1840">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1840">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-1841">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1841">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1842">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1842">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1843">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1843">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-1844">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1844">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-1845">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-1845">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-1846">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-1846">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-1847">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-1847">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-1848">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-1848">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-1849">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1849">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-1850">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-1850">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-1851">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-1851">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-1852">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1852">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-1853">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-1853">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="27c3f-1854">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1854">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="27c3f-1855">Notificar a la aplicación la entrada y salida de un subproceso</span><span class="sxs-lookup"><span data-stu-id="27c3f-1855">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1856">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1856">Prototype</span></span>

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a><span data-ttu-id="27c3f-1857">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1857">Description</span></span>

<span data-ttu-id="27c3f-1858">Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se entra o sale del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1858">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="27c3f-1859">La aplicación define el procesamiento de la devolución de llamada de notificación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1859">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1860">La devolución de llamada de notificación de entrada o salida del subproceso de la aplicación no puede llamar a ninguna API de ThreadX con una opción de suspensión.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1860">The application's thread entry/exit notification callback is not allowed to call any ThreadX API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1861">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1861">Parameters</span></span>

- <span data-ttu-id="27c3f-1862">**thread_ptr**: puntero a un subproceso creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1862">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="27c3f-1863">**entry_exit_notify**: puntero a la función de notificación de entrada o salida del subproceso de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1863">**entry_exit_notify** Pointer to application's thread entry/exit notification function.</span></span> <span data-ttu-id="27c3f-1864">El segundo parámetro para la función de notificación de entrada o salida designa si hay una entrada o una salida.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1864">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="27c3f-1865">El valor **TX_THREAD_ENTRY** (0x00) indica que se entró en el subproceso, mientras que el valor **TX_THREAD_EXIT** (0x01) indica que se salió de él.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1865">The value **TX_THREAD_ENTRY** (0x00) indicates the thread was entered, while the value **TX_THREAD_EXIT** (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="27c3f-1866">Si este valor es **TX_NULL**, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1866">If this value is **TX_NULL**, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1867">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1867">Return Values</span></span>

- <span data-ttu-id="27c3f-1868">**TX_SUCCESS** (0x00): registro correcto de la función de notificación de entrada o salida del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1868">**TX_SUCCESS** (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="27c3f-1869">**TX_THREAD_ERROR** (0x0E): puntero del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1869">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="27c3f-1870">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema se compiló con las funcionalidades de notificación deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1871">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1871">Allowed From</span></span>

<span data-ttu-id="27c3f-1872">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1872">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1873">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1873">Example</span></span>

```c
TX_THREAD my_thread;
/* Register the "my_entry_exit_notify" function for monitoring
the entry/exit of the thread "my_thread." */
status = tx_thread_entry_exit_notify(&my_thread,
    my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{
    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
        /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
        /* Thread exit! */
}
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1874">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1874">See Also</span></span>

- <span data-ttu-id="27c3f-1875">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1875">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-1876">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1876">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-1877">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1877">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-1878">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1878">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-1879">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1879">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-1880">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1880">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1881">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1881">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1882">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1882">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-1883">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1883">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-1884">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-1884">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-1885">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-1885">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-1886">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-1886">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-1887">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-1887">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-1888">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1888">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-1889">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-1889">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-1890">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-1890">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-1891">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1891">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-1892">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-1892">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="27c3f-1893">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1893">tx_thread_identify</span></span>

<span data-ttu-id="27c3f-1894">Recuperar un puntero al subproceso que se está ejecutando actualmente</span><span class="sxs-lookup"><span data-stu-id="27c3f-1894">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1895">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1895">Prototype</span></span>

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="27c3f-1896">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1896">Description</span></span>

<span data-ttu-id="27c3f-1897">Este servicio devuelve un puntero al subproceso que se está ejecutando actualmente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1897">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="27c3f-1898">Si no se está ejecutando ningún subproceso, este servicio devuelve un puntero con un valor null.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1898">If no thread is executing, this service returns a null pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1899">*Si se llama a este servicio desde un ISR, el valor devuelto representa el subproceso que se ejecuta antes que el controlador de interrupción en ejecución.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1899">*If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1900">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1900">Parameters</span></span>

<span data-ttu-id="27c3f-1901">Ninguno</span><span class="sxs-lookup"><span data-stu-id="27c3f-1901">None</span></span>

### <a name="retuen-values"></a><span data-ttu-id="27c3f-1902">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1902">Retuen Values</span></span>

- <span data-ttu-id="27c3f-1903">**thread pointer**: puntero al subproceso que se está ejecutando actualmente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1903">**thread pointer** Pointer to the currently executing thread.</span></span> <span data-ttu-id="27c3f-1904">Si no se está ejecutando ningún subproceso, el valor devuelto es **TX_NULL**.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1904">If no thread is executing, the return value is **TX_NULL**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1905">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1905">Allowed From</span></span>

<span data-ttu-id="27c3f-1906">Subprocesos e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1906">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1907">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1907">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1908">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-1908">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1909">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1909">Example</span></span>

<span data-ttu-id="27c3f-1910">TX_THREAD \*my_thread_ptr;</span><span class="sxs-lookup"><span data-stu-id="27c3f-1910">TX_THREAD \*my_thread_ptr;</span></span>

```c
TX_THREAD *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr = tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
from that thread or an ISR that interrupted that thread.
Otherwise, this service was called
from an ISR when no thread was running when the
interrupt occurred. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1911">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1911">See Also</span></span>

- <span data-ttu-id="27c3f-1912">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1912">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-1913">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1913">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-1914">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1914">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-1915">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1915">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-1916">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1916">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1917">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1917">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1918">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1918">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-1919">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1919">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-1920">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-1920">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-1921">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-1921">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-1922">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-1922">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-1923">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-1923">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-1924">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1924">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-1925">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-1925">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-1926">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-1926">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-1927">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1927">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-1928">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-1928">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="27c3f-1929">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1929">tx_thread_info_get</span></span>

<span data-ttu-id="27c3f-1930">Recuperar información acerca de un subproceso</span><span class="sxs-lookup"><span data-stu-id="27c3f-1930">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1931">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1931">Prototype</span></span>

```c
UINT tx_thread_info_get(
    TX_THREAD *thread_ptr, 
    CHAR **name,
    UINT *state, 
    ULONG *run_count,
    UINT *priority,
    UINT *preemption_threshold,
    ULONG *time_slice,
    TX_THREAD **next_thread,
    TX_THREAD **suspended_thread);
```

### <a name="description"></a><span data-ttu-id="27c3f-1932">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1932">Description</span></span>

<span data-ttu-id="27c3f-1933">Este servicio recupera información sobre el subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1933">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1934">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1934">Parameters</span></span>
- <span data-ttu-id="27c3f-1935">**thread_ptr**: puntero a un bloque de control del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1935">**thread_ptr** Pointer to thread control block.</span></span>
- <span data-ttu-id="27c3f-1936">**name**: puntero al destino del puntero al nombre del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1936">**name** Pointer to destination for the pointer to the thread's name.</span></span>
- <span data-ttu-id="27c3f-1937">**state**: puntero al destino del estado de ejecución actual del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1937">**state** Pointer to destination for the thread's current execution state.</span></span> <span data-ttu-id="27c3f-1938">Los valores posibles son los siguientes.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1938">Possible values are as follows.</span></span>
    - <span data-ttu-id="27c3f-1939">**TX_READY** (0x00)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1939">**TX_READY** (0x00)</span></span>
    - <span data-ttu-id="27c3f-1940">**TX_COMPLETED** (0x01)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1940">**TX_COMPLETED** (0x01)</span></span>
    - <span data-ttu-id="27c3f-1941">**TX_TERMINATED** (0x02)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1941">**TX_TERMINATED** (0x02)</span></span>
    - <span data-ttu-id="27c3f-1942">**TX_SUSPENDED** (0x03)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1942">**TX_SUSPENDED** (0x03)</span></span>
    - <span data-ttu-id="27c3f-1943">**TX_SLEEP** (0x04)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1943">**TX_SLEEP** (0x04)</span></span>
    - <span data-ttu-id="27c3f-1944">**TX_QUEUE_SUSP** (0x05)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1944">**TX_QUEUE_SUSP** (0x05)</span></span>
    - <span data-ttu-id="27c3f-1945">**TX_SEMAPHORE_SUSP** (0x06)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1945">**TX_SEMAPHORE_SUSP** (0x06)</span></span>
    - <span data-ttu-id="27c3f-1946">**TX_EVENT_FLAG** (0x07)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1946">**TX_EVENT_FLAG** (0x07)</span></span>
    - <span data-ttu-id="27c3f-1947">**TX_BLOCK_MEMORY** (0x08)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1947">**TX_BLOCK_MEMORY** (0x08)</span></span>
    - <span data-ttu-id="27c3f-1948">**TX_BYTE_MEMORY** (0x09)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1948">**TX_BYTE_MEMORY** (0x09)</span></span>
    - <span data-ttu-id="27c3f-1949">**TX_MUTEX_SUSP** (0x0D)</span><span class="sxs-lookup"><span data-stu-id="27c3f-1949">**TX_MUTEX_SUSP** (0x0D)</span></span>  

- <span data-ttu-id="27c3f-1950">**run_count**: puntero al destino del recuento de ejecuciones del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1950">**run_count** Pointer to destination for the thread's run count.</span></span>
- <span data-ttu-id="27c3f-1951">**priority**: puntero al destino de la prioridad del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1951">**priority** Pointer to destination for the thread's priority.</span></span>
- <span data-ttu-id="27c3f-1952">**preemption_threshold**: puntero al destino del umbral de adelantamiento del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1952">**preemption_threshold** Pointer to destination for the thread's preemption-threshold.</span></span>
<span data-ttu-id="27c3f-1953">**time_slice**: puntero al destino de la porción de tiempo del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1953">**time_slice** Pointer to destination for the thread's time-slice.</span></span>
<span data-ttu-id="27c3f-1954">**next_thread**: puntero al destino del siguiente puntero de subproceso creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1954">**next_thread** Pointer to destination for next created thread pointer.</span></span>

<span data-ttu-id="27c3f-1955">**suspended_thread**: puntero al destino del puntero al siguiente subproceso en la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1955">**suspended_thread** Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-1956">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1956">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-1957">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-1957">Return Values</span></span>

- <span data-ttu-id="27c3f-1958">**TX_SUCCESS** (0x00): información del subproceso recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1958">**TX_SUCCESS** (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="27c3f-1959">**TX_THREAD_ERROR** (0x0E): puntero de control del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1959">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-1960">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-1960">Allowed From</span></span>

<span data-ttu-id="27c3f-1961">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-1961">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-1962">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-1962">Preemption Possible</span></span>

<span data-ttu-id="27c3f-1963">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-1963">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-1964">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1964">Example</span></span>

```c
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
thread "my_thread." */

status = tx_thread_info_get(&my_thread, &name,
    &state, &run_count,
    &priority, &preemption_threshold,
    &time_slice, &next_thread,&suspended_thread);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-1965">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-1965">See Also</span></span>

- <span data-ttu-id="27c3f-1966">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-1966">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-1967">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-1967">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-1968">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1968">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-1969">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1969">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-1970">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1970">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-1971">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1971">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-1972">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1972">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-1973">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1973">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-1974">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-1974">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-1975">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-1975">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-1976">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-1976">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-1977">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-1977">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-1978">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-1978">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-1979">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-1979">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-1980">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-1980">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-1981">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-1981">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-1982">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-1982">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="27c3f-1983">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-1983">tx_thread_performance_info_get</span></span>

<span data-ttu-id="27c3f-1984">Obtener información acerca del rendimiento de un subproceso</span><span class="sxs-lookup"><span data-stu-id="27c3f-1984">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-1985">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-1985">Prototype</span></span>

```c
UINT tx_thread_performance_info_get(
    TX_THREAD *thread_ptr,
    LONG *resumptions, 
    ULONG *suspensions,
    ULONG *solicited_preemptions, 
    ULONG *interrupt_preemptions,
    ULONG *priority_inversions, 
    ULONG *time_slices,
    ULONG *relinquishes, 
    ULONG *timeouts, 
    ULONG *wait_aborts,
    TX_THREAD **last_preempted_by);
```

### <a name="description"></a><span data-ttu-id="27c3f-1986">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-1986">Description</span></span>

<span data-ttu-id="27c3f-1987">Este servicio recupera información sobre el rendimiento del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1987">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-1988">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-1988">*The ThreadX library and application must be built with* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-1989">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-1989">Parameters</span></span>
- <span data-ttu-id="27c3f-1990">**thread_ptr**: puntero a un subproceso creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1990">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="27c3f-1991">**resumptions**: puntero al destino del número de reanudaciones de este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1991">**resumptions** Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="27c3f-1992">**suspensions**: puntero al destino del número de suspensiones de este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1992">**suspensions** Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="27c3f-1993">**solicited_preemptions**: puntero al destino del número de adelantamientos como resultado de una llamada a un servicio de la API de ThreadX realizada por este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1993">**solicited_preemptions** Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="27c3f-1994">**interrupt_preemptions**: puntero al destino del número de adelantamientos de este subproceso como resultado del procesamiento de las interrupciones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1994">**interrupt_preemptions** Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="27c3f-1995">**priority_inversions**: puntero al destino del número de inversiones de prioridad de este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1995">**priority_inversions** Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="27c3f-1996">**time_slices**: puntero al destino del número de porciones de tiempo de este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1996">**time_slices** Pointer to destination for the number of time-slices of this thread.</span></span>
- <span data-ttu-id="27c3f-1997">**relinquishes**: puntero al destino del número de renuncias de subproceso realizadas por este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1997">**relinquishes** Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="27c3f-1998">**timeouts**: puntero al destino del número de tiempos de espera de suspensión en este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1998">**timeouts** Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="27c3f-1999">**wait_aborts**: puntero al destino del número de anulaciones de espera realizadas en este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-1999">**wait_aborts** Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="27c3f-2000">**last_preempted_by**: puntero al destino del puntero del subproceso que ha adelantado por última vez a este subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2000">**last_preempted_by** Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2001">*La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2001">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2002">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2002">Return Values</span></span>

- <span data-ttu-id="27c3f-2003">**TX_SUCCESS** (0x00): rendimiento del subproceso obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2003">**TX_SUCCESS** (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="27c3f-2004">**TX_PTR_ERROR** (0x03): puntero del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2004">**TX_PTR_ERROR** (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="27c3f-2005">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2006">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2006">Allowed From</span></span>

<span data-ttu-id="27c3f-2007">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2007">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2008">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2008">Example</span></span>

```c
TX_THREAD my_thread;
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
TX_THREAD *last_preempted_by;

/* Retrieve performance information on the previously created
thread. */

status = tx_thread_performance_info_get(&my_thread, &resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices,
    &relinquishes, &timeouts,
    &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2009">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2009">See Also</span></span>

- <span data-ttu-id="27c3f-2010">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2010">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2011">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2011">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2012">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2012">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2013">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2013">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2014">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2014">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2015">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2015">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2016">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2016">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2017">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2017">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2018">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2018">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2019">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2019">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2020">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2020">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2021">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2021">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2022">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2022">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2023">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2023">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2024">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2024">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2025">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2025">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2026">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2026">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="27c3f-2027">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2027">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="27c3f-2028">Obtener información acerca del rendimiento del sistema de un subproceso</span><span class="sxs-lookup"><span data-stu-id="27c3f-2028">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2029">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2029">Prototype</span></span>

```c
UINT tx_thread_performance_system_info_get(
    ULONG *resumptions,
    ULONG *suspensions, 
    ULONG *solicited_preemptions,
    ULONG *interrupt_preemptions, 
    ULONG *priority_inversions,
    ULONG *time_slices, 
    ULONG *relinquishes, 
    ULONG *timeouts,
    ULONG *wait_aborts, 
    ULONG *non_idle_returns,
    ULONG *idle_returns);
```

### <a name="description"></a><span data-ttu-id="27c3f-2030">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2030">Description</span></span>

<span data-ttu-id="27c3f-2031">Este servicio recupera información sobre el rendimiento de todos los subprocesos del sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2031">This service retrieves performance information about all the threads in the system.</span></span>

<span data-ttu-id="27c3f-2032">*La biblioteca y la aplicación de ThreadX se deben compilar con el servicio*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2032">*The ThreadX library and application must be built with*</span></span>

<span data-ttu-id="27c3f-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2034">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2034">Parameters</span></span>

- <span data-ttu-id="27c3f-2035">**resumptions**: puntero al destino del número total de reanudaciones de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2035">**resumptions** Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="27c3f-2036">**suspensions**: puntero al destino del número total de suspensiones de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2036">**suspensions** Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="27c3f-2037">**solicited_preemptions**: puntero al destino del número total de adelantamientos de los subprocesos como resultado de una llamada de un subproceso a un servicio de la API de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2037">**solicited_preemptions** Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="27c3f-2038">**interrupt_preemptions**: puntero al destino del número total de adelantamientos de los subprocesos como resultado del procesamiento de interrupciones.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2038">**interrupt_preemptions** Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="27c3f-2039">**priority_inversions**: puntero al destino del número total de inversiones de prioridad de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2039">**priority_inversions** Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="27c3f-2040">**time_slices**: puntero al destino del número total de porciones de tiempo de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2040">**time_slices** Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="27c3f-2041">**relinquishes**: puntero al destino del número total de renuncias de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2041">**relinquishes** Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="27c3f-2042">**timeouts**: puntero al destino del número total de tiempos de espera de suspensión de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2042">**timeouts** Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="27c3f-2043">**wait_aborts**: puntero al destino del número total de anulaciones de espera de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2043">**wait_aborts** Pointer to destination for the total number of thread wait aborts.</span></span>
- <span data-ttu-id="27c3f-2044">**non_idle_returns**: puntero al destino del número de veces que un subproceso vuelve al sistema cuando hay otro subproceso preparado para ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2044">**non_idle_returns** Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span>
- <span data-ttu-id="27c3f-2045">**idle_returns**: puntero al destino del número de veces que un subproceso vuelve al sistema cuando no hay otro subproceso preparado para ejecutarse (sistema inactivo).</span><span class="sxs-lookup"><span data-stu-id="27c3f-2045">**idle_returns** Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2046">*La especificación de un valor **TX_NULL** para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2046">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2047">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2047">Return Values</span></span>

- <span data-ttu-id="27c3f-2048">**TX_SUCCESS** (0x00): rendimiento del sistema del subproceso obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2048">**TX_SUCCESS** (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="27c3f-2049">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2050">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2050">Allowed From</span></span>

<span data-ttu-id="27c3f-2051">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2051">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2052">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2052">Example</span></span>

```c
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
ULONG non_idle_returns;
ULONG idle_returns;

/* Retrieve performance information on all previously created
thread. */

status = tx_thread_performance_system_info_get(&resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices, &relinquishes,
    &timeouts, &wait_aborts, &non_idle_returns,
    &idle_returns);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2053">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2053">See Also</span></span>

- <span data-ttu-id="27c3f-2054">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2054">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2055">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2055">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2056">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2056">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2057">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2057">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2058">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2058">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2059">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2059">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2060">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2060">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2061">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2061">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2062">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2062">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2063">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2063">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2064">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2064">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2065">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2065">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2066">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2066">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2067">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2067">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2068">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2068">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2069">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2069">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2070">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2070">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="27c3f-2071">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2071">tx_thread_preemption_change</span></span>

<span data-ttu-id="27c3f-2072">Cambiar el umbral de adelantamiento de un subproceso de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2072">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2073">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2073">Prototype</span></span>

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a><span data-ttu-id="27c3f-2074">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2074">Description</span></span>

<span data-ttu-id="27c3f-2075">Este servicio cambia el umbral de adelantamiento del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2075">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="27c3f-2076">El umbral de adelantamiento impide que los subprocesos con un valor igual o inferior a este umbral adelanten al subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2076">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

>[!NOTE]
> <span data-ttu-id="27c3f-2077">*Al usar el umbral de adelantamiento, se deshabilitan las porciones de tiempo para el subproceso especificado.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2077">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2078">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2078">Parameters</span></span>
- <span data-ttu-id="27c3f-2079">**thread_ptr**: puntero a un subproceso de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2079">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="27c3f-2080">**new_threshold**: nuevo nivel de prioridad del umbral de adelantamiento (0 a (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="27c3f-2080">**new_threshold** New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="27c3f-2081">**old_threshold**: puntero a una ubicación para devolver el umbral de adelantamiento anterior.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2081">**old_threshold** Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2082">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2082">Return Values</span></span>

- <span data-ttu-id="27c3f-2083">**TX_SUCCESS** (0x00): umbral de adelantamiento cambiado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2083">**TX_SUCCESS** (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="27c3f-2084">**TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2084">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27c3f-2085">**TX_THRESH_ERROR** (0X18): el nuevo umbral de adelantamiento especificado no es una prioridad de subproceso válida (un valor distinto de (0 a (**TX_MAX_PRIORITIES**-1)) o es mayor que (prioridad inferior) que la prioridad actual del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2085">**TX_THRESH_ERROR** (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (**TX_MAX_PRIORITIES**-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="27c3f-2086">**TX_PTR_ERROR** (0x03): puntero no válido a la ubicación de almacenamiento del umbral de adelantamiento anterior.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2086">**TX_PTR_ERROR** (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="27c3f-2087">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2087">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2088">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2088">Allowed From</span></span>

<span data-ttu-id="27c3f-2089">Subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="27c3f-2089">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2090">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2090">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2091">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-2091">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2092">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2092">Example</span></span>

```c
TX_THREAD my_thread;
UINT my_old_threshold;
UINT status;

/* Disable all preemption of the specified thread. The
current preemption-threshold is returned in
"my_old_threshold". Assume that "my_thread" has
already been created. */

status = tx_thread_preemption_change(&my_thread,
    0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
non-preemptable by another thread. Note that ISRs are
not prevented by preemption disabling. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2093">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2093">See Also</span></span>

- <span data-ttu-id="27c3f-2094">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2094">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2095">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2095">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2096">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2096">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2097">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2097">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2098">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2098">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2099">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2099">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2100">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2100">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2101">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2101">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2102">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2102">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2103">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2103">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2104">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2104">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2105">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2105">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2106">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2106">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2107">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2107">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2108">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2108">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2109">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2109">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2110">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2110">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="27c3f-2111">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2111">tx_thread_priority_change</span></span>

<span data-ttu-id="27c3f-2112">Cambiar la prioridad de un subproceso de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2112">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2113">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2113">Prototype</span></span>

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a><span data-ttu-id="27c3f-2114">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2114">Description</span></span>

<span data-ttu-id="27c3f-2115">Este servicio cambia la prioridad del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2115">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="27c3f-2116">Las prioridades válidas oscilan entre 0 y (TX_MAX_PRIORITES-1), donde 0 representa el nivel de prioridad más alto.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2116">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-2117">\*El umbral de adelantamiento del subproceso especificado se establece automáticamente en la nueva prioridad.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2117">\*The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="27c3f-2118">Si se desea un nuevo umbral, se debe usar el servicio \***tx_thread_preemption_change** _ después de esta llamada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2118">If a new threshold is desired, the \***tx_thread_preemption_change** _ service must be used after this call._</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2119">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2119">Parameters</span></span>

- <span data-ttu-id="27c3f-2120">**thread_ptr**: puntero a un subproceso de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2120">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="27c3f-2121">**new_priority**: nuevo nivel de prioridad del subproceso (0 a (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="27c3f-2121">**new_priority** New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="27c3f-2122">**old_priority**: puntero a una ubicación para devolver la prioridad anterior del subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2122">**old_priority** Pointer to a location to return the thread's previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2123">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2123">Return Values</span></span>

- <span data-ttu-id="27c3f-2124">**TX_SUCCESS** (0X00): prioridad cambiada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2124">**TX_SUCCESS** (0x00) Successful priority change.</span></span>
- <span data-ttu-id="27c3f-2125">**TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2125">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27c3f-2126">**TX_PRIORITY_ERROR** (0x0F): la nueva prioridad especificada no es válida (un valor distinto de (0 a (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="27c3f-2126">**TX_PRIORITY_ERROR** (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="27c3f-2127">**TX_PTR_ERROR** (0x03): puntero no válido a la ubicación de almacenamiento de la prioridad anterior.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2127">**TX_PTR_ERROR** (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="27c3f-2128">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2128">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2129">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2129">Allowed From</span></span>

<span data-ttu-id="27c3f-2130">Subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="27c3f-2130">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2131">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2131">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2132">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-2132">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2133">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2133">Example</span></span>

```c
TX_THREAD my_thread;
UINT my_old_priority;
UINT status;

/* Change the thread represented by "my_thread" to priority
0. */

status = tx_thread_priority_change(&my_thread,
    0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="27c3f-2134">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2134">See Also</span></span>

- <span data-ttu-id="27c3f-2135">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2135">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2136">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2136">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2137">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2137">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2138">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2138">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2139">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2139">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2140">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2140">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2141">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2141">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2142">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2142">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2143">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2143">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2144">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2144">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2145">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2145">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2146">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2146">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2147">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2147">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2148">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2148">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2149">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2149">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2150">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2150">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2151">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2151">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="27c3f-2152">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2152">tx_thread_relinquish</span></span>

<span data-ttu-id="27c3f-2153">Ceder el control a otros subprocesos de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2153">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2154">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2154">Prototype</span></span>

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a><span data-ttu-id="27c3f-2155">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2155">Description</span></span>

<span data-ttu-id="27c3f-2156">Este servicio cede el control del procesador a otros subprocesos preparados para ejecutarse con prioridad igual o superior.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2156">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2157">*Además de ceder el control a los subprocesos con la misma prioridad, este servicio también se lo cede al subproceso de prioridad más alta que no se haya podido ejecutar debido a la configuración del umbral de adelantamiento del subproceso actual.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2157">*In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2158">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2158">Parameters</span></span>

<span data-ttu-id="27c3f-2159">Ninguno</span><span class="sxs-lookup"><span data-stu-id="27c3f-2159">None</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2160">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2160">Return Values</span></span>

<span data-ttu-id="27c3f-2161">Ninguno</span><span class="sxs-lookup"><span data-stu-id="27c3f-2161">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2162">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2162">Allowed From</span></span>

<span data-ttu-id="27c3f-2163">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2163">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2164">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2164">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2165">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-2165">Yes</span></span>

### <a name="examples"></a><span data-ttu-id="27c3f-2166">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2166">Examples</span></span>

```c
ULONG run_counter_1 = 0;
ULONG run_counter_2 = 0;

/* Example of two threads relinquishing control to
each other in an infinite loop. Assume that
both of these threads are ready and have the same
priority. The run counters will always stay within one
of each other. */

VOID my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{

    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2167">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2167">See Also</span></span>

- <span data-ttu-id="27c3f-2168">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2168">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2169">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2169">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2170">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2170">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2171">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2171">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2172">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2172">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2173">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2173">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2174">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2174">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2175">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2175">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2176">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2176">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2177">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2177">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2178">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2178">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2179">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2179">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2180">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2180">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2181">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2181">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2182">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2182">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2183">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2183">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2184">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2184">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="27c3f-2185">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2185">tx_thread_reset</span></span>

<span data-ttu-id="27c3f-2186">Restablecer un subproceso</span><span class="sxs-lookup"><span data-stu-id="27c3f-2186">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2187">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2187">Prototype</span></span>

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-2188">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2188">Description</span></span>

<span data-ttu-id="27c3f-2189">Este servicio restablece el subproceso especificado para que se ejecute en el punto de entrada definido al crear el subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2189">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="27c3f-2190">El subproceso debe estar en un estado **TX_COMPLETED** o **TX_TERMINATED** para que se pueda restablecer.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2190">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-2191">*Se debe reanudar el subproceso para que se pueda ejecutar de nuevo.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2191">*The thread must be resumed for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2192">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2192">Parameters</span></span>

- <span data-ttu-id="27c3f-2193">**thread_ptr**: puntero a un subproceso creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2193">**thread_ptr** Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2194">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2194">Return Values</span></span>

- <span data-ttu-id="27c3f-2195">**TX_SUCCESS** (0x00): subproceso restablecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2195">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="27c3f-2196">**TX_NOT_DONE** (0x20): el subproceso especificado no se encuentra en un estado **TX_COMPLETED** o **TX_TERMINATED**.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2196">**TX_NOT_DONE** (0x20) Specified thread is not in a **TX_COMPLETED** or **TX_TERMINATED** state.</span></span>
- <span data-ttu-id="27c3f-2197">**TX_THREAD_ERROR** (0x0E): puntero del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2197">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="27c3f-2198">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2198">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2199">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2199">Allowed From</span></span>

<span data-ttu-id="27c3f-2200">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2200">Threads</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2201">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2201">Example</span></span>

<span data-ttu-id="27c3f-2202">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="27c3f-2202">TX_THREAD my_thread;</span></span>

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2203">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2203">See Also</span></span>

- <span data-ttu-id="27c3f-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2204">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2205">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2207">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2210">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2210">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2211">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2211">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2212">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2212">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2213">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2213">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2214">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="27c3f-2221">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2221">tx_thread_resume</span></span>

<span data-ttu-id="27c3f-2222">Reanudar un subproceso de aplicación suspendido</span><span class="sxs-lookup"><span data-stu-id="27c3f-2222">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2223">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2223">Prototype</span></span>

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-2224">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2224">Description</span></span>

<span data-ttu-id="27c3f-2225">Este servicio reanuda o prepara para su ejecución un subproceso suspendido anteriormente mediante una llamada a ***tx_thread_suspend***.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2225">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="27c3f-2226">Además, este servicio reanuda los subprocesos que se crearon sin un inicio automático.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2226">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2227">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2227">Parameters</span></span>

- <span data-ttu-id="27c3f-2228">**thread_ptr**: puntero a un subproceso de aplicación suspendido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2228">**thread_ptr** Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2229">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2229">Return Values</span></span>

- <span data-ttu-id="27c3f-2230">**TX_SUCCESS** (0x00): subproceso reanudado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2230">**TX_SUCCESS** (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="27c3f-2231">**TX_SUSPEND_LIFTED** (0x19): se elevó la suspensión retrasada establecida previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2231">**TX_SUSPEND_LIFTED** (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="27c3f-2232">**TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2232">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27c3f-2233">**TX_RESUME_ERROR** (0X12): el subproceso especificado no está suspendido o se suspendió previamente mediante un servicio distinto a **_tx_thread_suspend_**.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2233">**TX_RESUME_ERROR** (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2234">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2234">Allowed From</span></span>

<span data-ttu-id="27c3f-2235">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2235">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2236">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2236">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2237">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-2237">Yes</span></span>

<span data-ttu-id="27c3f-2238">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="27c3f-2238">TX_THREAD my_thread;</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2239">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2239">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2240">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2240">See Also</span></span>

- <span data-ttu-id="27c3f-2241">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2241">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2242">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2242">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2243">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2243">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2244">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2244">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2245">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2245">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2246">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2246">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2247">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2247">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2248">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2248">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2249">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2249">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2250">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2250">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2251">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2251">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2252">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2252">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2253">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2253">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2254">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2254">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2255">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2255">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2256">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2256">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2257">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2257">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="27c3f-2258">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2258">tx_thread_sleep</span></span>

<span data-ttu-id="27c3f-2259">Suspender el subproceso actual durante el tiempo especificado</span><span class="sxs-lookup"><span data-stu-id="27c3f-2259">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2260">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2260">Prototype</span></span>

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a><span data-ttu-id="27c3f-2261">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2261">Description</span></span>

<span data-ttu-id="27c3f-2262">Este servicio hace que el subproceso que realiza la llamada se suspenda durante el número especificado de tics de temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2262">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="27c3f-2263">La cantidad de tiempo físico asociada a un tic de temporizador es específica de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2263">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="27c3f-2264">Solo se puede llamar a este servicio desde un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2264">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2265">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2265">Parameters</span></span>

- <span data-ttu-id="27c3f-2266">**timer_ticks**: número de tics de temporizador para suspender el subproceso de la aplicación que realiza la llamada, comprendido entre 0 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2266">**timer_ticks** The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="27c3f-2267">Si se especifica 0, el servicio se devuelve inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2267">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2268">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2268">Return Values</span></span>

- <span data-ttu-id="27c3f-2269">**TX_SUCCESS** (0x00): subproceso suspendido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2269">**TX_SUCCESS** (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="27c3f-2270">**TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2270">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27c3f-2271">**TX_CALLER_ERROR** (0x13): se llamó al servicio desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2271">**TX_CALLER_ERROR** (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2272">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2272">Allowed From</span></span>

<span data-ttu-id="27c3f-2273">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2274">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2274">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2275">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2276">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2276">Example</span></span>

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2277">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2277">See Also</span></span>

- <span data-ttu-id="27c3f-2278">tx_thread_create, tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2278">tx_thread_create, tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2279">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2279">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2280">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2280">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2281">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2281">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2282">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2282">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2283">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2283">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2284">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2284">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2285">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2285">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2286">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2286">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2287">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2288">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2289">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2289">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2290">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2290">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2291">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2291">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2292">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2292">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2293">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2293">tx_thread_wait_abort</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="27c3f-2294">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2294">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="27c3f-2295">Registrar una devolución de llamada de notificación de error de la pila de un subproceso</span><span class="sxs-lookup"><span data-stu-id="27c3f-2295">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2296">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2296">Prototype</span></span>

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a><span data-ttu-id="27c3f-2297">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2297">Description</span></span>

<span data-ttu-id="27c3f-2298">Este servicio registra una función de devolución de llamada de notificación para controlar los errores de la pila de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2298">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="27c3f-2299">Cuando ThreadX detecta un error en la pila de un subproceso durante la ejecución, llamará a esta función de notificación para procesarlo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2299">When ThreadX detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="27c3f-2300">La aplicación define al completo el procesamiento del error.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2300">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="27c3f-2301">Es posible que se realice cualquier acción, desde suspender el subproceso infractor hasta restablecer todo el sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2301">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-2302">*La biblioteca ThreadX se debe compilar con el servicio* **TX_ENABLE_STACK_CHECKING** *definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2302">*The ThreadX library must be built with* **TX_ENABLE_STACK_CHECKING** *defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2303">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2303">Parameters</span></span>
- <span data-ttu-id="27c3f-2304">**error_handler**: puntero a la función de control de errores de pila de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2304">**error_handler** Pointer to application's stack error handling function.</span></span> <span data-ttu-id="27c3f-2305">Si este valor es TX_NULL, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2305">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2306">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2306">Return Values</span></span>

- <span data-ttu-id="27c3f-2307">**TX_SUCCESS** (0x00): subproceso restablecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2307">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="27c3f-2308">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2309">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2309">Allowed From</span></span>

<span data-ttu-id="27c3f-2310">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2310">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2311">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2311">Example</span></span>

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2312">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2312">See Also</span></span>

- <span data-ttu-id="27c3f-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2313">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2314">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2316">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2319">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2319">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2323">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2323">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2324">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2324">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2325">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2325">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="27c3f-2330">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2330">tx_thread_suspend</span></span>

<span data-ttu-id="27c3f-2331">Suspender un subproceso de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2331">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2332">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2332">Prototype</span></span>

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-2333">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2333">Description</span></span>

<span data-ttu-id="27c3f-2334">Este servicio suspende el subproceso de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2334">This service suspends the specified application thread.</span></span> <span data-ttu-id="27c3f-2335">Un subproceso puede llamar a este servicio para suspenderse a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2335">A thread may call this service to suspend itself.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2336">*Si el subproceso especificado ya está suspendido por otro motivo, esta suspensión se mantiene internamente hasta que se levanta la anterior. Cuando esto sucede, se realiza esta suspensión incondicional del subproceso especificado. Ninguna otra solicitud de suspensión incondicional tendrá efecto.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2336">*If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted. When that happens, this unconditional suspension of the specified thread is performed. Further unconditional suspension requests have no effect.*</span></span>

<span data-ttu-id="27c3f-2337">Tras su suspensión, el subproceso debe reanudarse mediante ***tx_thread_resume*** para volver a ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2337">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2338">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2338">Parameters</span></span>

- <span data-ttu-id="27c3f-2339">**thread_ptr**: puntero a un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2339">**thread_ptr** Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2340">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2340">Return Values</span></span>

- <span data-ttu-id="27c3f-2341">**TX_SUCCESS** (0x00): subproceso suspendido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2341">**TX_SUCCESS** (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="27c3f-2342">**TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2342">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27c3f-2343">**TX_SUSPEND_ERROR** (0x14): el subproceso especificado se encuentra en un estado finalizado o completado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2343">**TX_SUSPEND_ERROR** (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="27c3f-2344">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2344">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2345">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2345">Allowed From</span></span>

<span data-ttu-id="27c3f-2346">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2346">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2347">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2347">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2348">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-2348">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2349">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2349">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2350">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2350">See Also</span></span>

- <span data-ttu-id="27c3f-2351">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2351">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2352">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2352">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2353">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2353">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2354">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2354">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2355">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2355">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2356">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2356">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2357">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2357">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2358">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2358">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2359">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2359">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2360">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2360">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2361">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2361">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2362">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2362">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2363">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2363">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2364">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2364">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2365">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2365">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2366">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2366">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2367">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2367">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="27c3f-2368">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2368">tx_thread_terminate</span></span>

<span data-ttu-id="27c3f-2369">Finalizar un subproceso de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2369">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2370">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2370">Prototype</span></span>

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="27c3f-2371">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2371">Description</span></span>

<span data-ttu-id="27c3f-2372">Este servicio finaliza el subproceso de aplicación especificado, independientemente de si está suspendido o no.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2372">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="27c3f-2373">Un subproceso puede llamar a este servicio para finalizarse a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2373">A thread may call this service to terminate itself.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2374">*Es responsabilidad de la aplicación asegurarse de que el subproceso está en un estado adecuado para la terminación. Por ejemplo, un subproceso no debe terminarse durante el procesamiento crítico de aplicaciones o dentro de otros componentes de middleware, donde podría dejar dicho procesamiento en un estado desconocido.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2374">*It is the application's responsibility to ensure that the thread is in a state suitable for termination. For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-2375">*Tras su finalización, el subproceso debe restablecerse para que se pueda ejecutar de nuevo.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2375">*After being terminated, the thread must be reset for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2376">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2376">Parameters</span></span>

- <span data-ttu-id="27c3f-2377">**thread_ptr**: puntero a un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2377">**thread_ptr** Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2378">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2378">Return Values</span></span>
- <span data-ttu-id="27c3f-2379">**TX_SUCCESS** (0x00): subproceso terminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2379">**TX_SUCCESS** (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="27c3f-2380">**TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2380">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27c3f-2381">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2381">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2382">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2382">Allowed From</span></span>

<span data-ttu-id="27c3f-2383">Subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="27c3f-2383">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2384">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2384">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2385">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-2385">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2386">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2386">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2387">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2387">See Also</span></span>

- <span data-ttu-id="27c3f-2388">tx_thread_create tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2388">tx_thread_create tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2389">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2389">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2390">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2390">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2391">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2391">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2392">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2392">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2393">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2393">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2394">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2394">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2395">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2395">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2396">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2396">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2397">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2397">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2398">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2398">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2399">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2399">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2400">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2400">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2401">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2401">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2402">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2402">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27c3f-2403">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2403">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="27c3f-2404">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2404">tx_thread_time_slice_change</span></span>

<span data-ttu-id="27c3f-2405">Cambiar la porción de tiempo de un subproceso de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2405">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2406">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2406">Prototype</span></span>

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a><span data-ttu-id="27c3f-2407">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2407">Description</span></span>

<span data-ttu-id="27c3f-2408">Este servicio cambia la porción de tiempo del subproceso de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2408">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="27c3f-2409">Al seleccionar una porción de tiempo para un subproceso, se asegura de que no se ejecutará más que el número especificado de tics de temporizador antes de que otros subprocesos con prioridades iguales o superiores tengan la posibilidad de ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2409">Selecting a time-slice for a thread insures that it won't execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2410">*Al usar el umbral de adelantamiento, se deshabilitan las porciones de tiempo para el subproceso especificado.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2410">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2411">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2411">Parameters</span></span>

- <span data-ttu-id="27c3f-2412">**thread_ptr**: puntero a un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2412">**thread_ptr** Pointer to application thread.</span></span>
- <span data-ttu-id="27c3f-2413">**new_time_slice**: nuevo valor de porción de tiempo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2413">**new_time_slice** New time slice value.</span></span> <span data-ttu-id="27c3f-2414">Entre los valores válidos se incluyen TX_NO_TIME_SLICE y valores numéricos del 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2414">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="27c3f-2415">**old_time_slice**: puntero a la ubicación para almacenar el valor de la porción de tiempo anterior del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2415">**old_time_slice** Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2416">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2416">Return Values</span></span>

- <span data-ttu-id="27c3f-2417">**TX_SUCCESS** (0x00): porción de tiempo cambiada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2417">**TX_SUCCESS** (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="27c3f-2418">**TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2418">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27c3f-2419">**TX_PTR_ERROR** (0x03): puntero no válido a la ubicación de almacenamiento de la porción de tiempo anterior.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2419">**TX_PTR_ERROR** (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="27c3f-2420">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2420">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2421">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2421">Allowed From</span></span>

<span data-ttu-id="27c3f-2422">Subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="27c3f-2422">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2423">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2423">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2424">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-2424">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2425">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2425">Example</span></span>

```c
TX_THREAD my_thread;
ULONG my_old_time_slice;
UINT status;

/* Change the time-slice of the thread associated with
"my_thread" to 20. This will mean that "my_thread"
can only run for 20 timer-ticks consecutively before
other threads of equal or higher priority get a chance
to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
    &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
has been changed to 20 and the previous time-slice is
in "my_old_time_slice." */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2426">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2426">See Also</span></span>

- <span data-ttu-id="27c3f-2427">tx_thread_create tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2427">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2428">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2428">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2429">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2429">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2430">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2430">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2431">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2431">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2432">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2432">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2433">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2433">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2434">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2434">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2435">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2435">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2436">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2436">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2437">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2437">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2438">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2438">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2439">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2439">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2440">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2440">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2441">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2441">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2442">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2442">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2443">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2443">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="27c3f-2444">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27c3f-2444">tx_thread_wait_abort</span></span>

<span data-ttu-id="27c3f-2445">Anular una suspensión de un subproceso especificado</span><span class="sxs-lookup"><span data-stu-id="27c3f-2445">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2446">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2446">Prototype</span></span>

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-2447">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2447">Description</span></span>

<span data-ttu-id="27c3f-2448">Este servicio anula cualquier tipo de suspensión de objeto del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2448">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="27c3f-2449">Si se anula la espera, se devuelve un valor **TX_WAIT_ABORTED** desde el servicio en el que el subproceso estaba esperando.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2449">If the wait is aborted, a **TX_WAIT_ABORTED** value is returned from the service that the thread was waiting on.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2450">*Este servicio no libera la suspensión explícita realizada por el servicio tx_thread_suspend.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2450">*This service does not release explicit suspension that is made by the tx_thread_suspend service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2451">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2451">Parameters</span></span>

- <span data-ttu-id="27c3f-2452">**thread_ptr**: puntero a un subproceso de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2452">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2453">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2453">Return Values</span></span>

- <span data-ttu-id="27c3f-2454">**TX_SUCCESS**: (0x00) espera del subproceso anulada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2454">**TX_SUCCESS** (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="27c3f-2455">**TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2455">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27c3f-2456">**TX_WAIT_ABORT_ERROR** (0x1B): el subproceso especificado no está en estado de espera.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2456">**TX_WAIT_ABORT_ERROR** (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2457">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2457">Allowed From</span></span>

<span data-ttu-id="27c3f-2458">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2458">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2459">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2459">Preemption Possible</span></span>
<span data-ttu-id="27c3f-2460">Sí</span><span class="sxs-lookup"><span data-stu-id="27c3f-2460">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2461">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2461">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2462">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2462">See Also</span></span>

- <span data-ttu-id="27c3f-2463">tx_thread_create tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2463">tx_thread_create</span></span>
- <span data-ttu-id="27c3f-2464">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2464">tx_thread_delete</span></span>
- <span data-ttu-id="27c3f-2465">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2465">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27c3f-2466">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2466">tx_thread_identify</span></span>
- <span data-ttu-id="27c3f-2467">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2467">tx_thread_info_get</span></span>
- <span data-ttu-id="27c3f-2468">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2468">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2469">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2469">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27c3f-2470">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2470">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27c3f-2471">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2471">tx_thread_priority_change</span></span>
- <span data-ttu-id="27c3f-2472">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27c3f-2472">tx_thread_relinquish</span></span>
- <span data-ttu-id="27c3f-2473">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27c3f-2473">tx_thread_reset</span></span>
- <span data-ttu-id="27c3f-2474">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27c3f-2474">tx_thread_resume</span></span>
- <span data-ttu-id="27c3f-2475">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27c3f-2475">tx_thread_sleep</span></span>
- <span data-ttu-id="27c3f-2476">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27c3f-2476">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27c3f-2477">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27c3f-2477">tx_thread_suspend</span></span>
- <span data-ttu-id="27c3f-2478">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2478">tx_thread_terminate</span></span>
- <span data-ttu-id="27c3f-2479">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2479">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="27c3f-2480">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2480">tx_time_get</span></span>

<span data-ttu-id="27c3f-2481">Recuperar la hora actual</span><span class="sxs-lookup"><span data-stu-id="27c3f-2481">Retrieves the current time</span></span>

<span data-ttu-id="27c3f-2482">Temporizadores de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2482">Application Timers</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2483">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2483">Prototype</span></span>

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a><span data-ttu-id="27c3f-2484">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2484">Description</span></span>

<span data-ttu-id="27c3f-2485">Este servicio devuelve el contenido del reloj interno del sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2485">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="27c3f-2486">Cada tic del temporizador aumenta el reloj interno del sistema en uno.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2486">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="27c3f-2487">El reloj del sistema se establece en cero durante la inicialización y se puede cambiar a un valor específico mediante el servicio ***tx_time_set***.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2487">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2488">*El tiempo real que representa cada tic del temporizador es específico de la aplicación.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2488">*The actual time each timer-tick represents is application specific.*</span></span>

<span data-ttu-id="27c3f-2489">**Parámetros**</span><span class="sxs-lookup"><span data-stu-id="27c3f-2489">**Parameters**</span></span>

<span data-ttu-id="27c3f-2490">Ninguno</span><span class="sxs-lookup"><span data-stu-id="27c3f-2490">None</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2491">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2491">Return Values</span></span>

- <span data-ttu-id="27c3f-2492">**system clock ticks**: valor del reloj interno del sistema de ejecución libre.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2492">**system clock ticks** Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2493">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2493">Allowed From</span></span>

<span data-ttu-id="27c3f-2494">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2494">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2495">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2495">Preemption Possible</span></span>
<span data-ttu-id="27c3f-2496">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-2496">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2497">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2497">Example</span></span>

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2498">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2498">See Also</span></span>

- <span data-ttu-id="27c3f-2499">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="27c3f-2499">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="27c3f-2500">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="27c3f-2500">tx_time_set</span></span>

<span data-ttu-id="27c3f-2501">Establecer la hora actual</span><span class="sxs-lookup"><span data-stu-id="27c3f-2501">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2502">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2502">Prototype</span></span>

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a><span data-ttu-id="27c3f-2503">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2503">Description</span></span>

<span data-ttu-id="27c3f-2504">Este servicio establece el reloj interno del sistema en el valor especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2504">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="27c3f-2505">Cada tic del temporizador aumenta el reloj interno del sistema en uno.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2505">Each timer-tick increases the internal system clock by one.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2506">*El tiempo real que representa cada tic del temporizador es específico de la aplicación.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2506">*The actual time each timer-tick represents is application specific.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2507">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2507">Parameters</span></span>

- <span data-ttu-id="27c3f-2508">**new_time**: hora nueva que se va a establecer en el reloj del sistema. Los valores válidos oscilan entre 0 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2508">**new_time** New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2509">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2509">Return Values</span></span>

<span data-ttu-id="27c3f-2510">Ninguno</span><span class="sxs-lookup"><span data-stu-id="27c3f-2510">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2511">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2511">Allowed From</span></span>

<span data-ttu-id="27c3f-2512">Subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2512">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2513">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2513">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2514">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-2514">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2515">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2515">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2516">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2516">See Also</span></span>

- <span data-ttu-id="27c3f-2517">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2517">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="27c3f-2518">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2518">tx_timer_activate</span></span>

<span data-ttu-id="27c3f-2519">Activar un temporizador de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2519">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2520">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2520">Prototype</span></span>

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-2521">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2521">Description</span></span>

<span data-ttu-id="27c3f-2522">Este servicio activa el temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2522">This service activates the specified application timer.</span></span> <span data-ttu-id="27c3f-2523">Las rutinas de expiración de los temporizadores que expiran al mismo tiempo se ejecutan en el orden en el que se activaron.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2523">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2524">*Un temporizador monoestable expirado se debe restablecer mediante* ***tx_timer_change** _ _para que se pueda volver a activar.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2524">*An expired one-shot timer must be reset via* ***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2525">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2525">Parameters</span></span>

- <span data-ttu-id="27c3f-2526">**timer_ptr**: puntero a un temporizador de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2526">**timer_ptr** Pointer to a previously created application timer.</span></span>

<span data-ttu-id="27c3f-2527">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="27c3f-2527">**Return Values**</span></span>

- <span data-ttu-id="27c3f-2528">**TX_SUCCESS** (0x00): temporizador de aplicación activado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2528">**TX_SUCCESS** (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="27c3f-2529">**TX_TIMER_ERROR** (0x15): puntero de temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2529">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="27c3f-2530">**TX_ACTIVATE_ERROR** (0x17): el temporizador ya estaba activo o es un temporizador monoestable que ya ha expirado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2530">**TX_ACTIVATE_ERROR** (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2531">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2531">Allowed From</span></span>

<span data-ttu-id="27c3f-2532">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2532">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2533">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2533">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2534">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-2534">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2535">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2535">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2536">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2536">See Also</span></span>

- <span data-ttu-id="27c3f-2537">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2537">tx_timer_change</span></span>
- <span data-ttu-id="27c3f-2538">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2538">tx_timer_create</span></span>
- <span data-ttu-id="27c3f-2539">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2539">tx_timer_deactivate</span></span>
- <span data-ttu-id="27c3f-2540">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2540">tx_timer_delete</span></span>
- <span data-ttu-id="27c3f-2541">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2541">tx_timer_info_get</span></span>
- <span data-ttu-id="27c3f-2542">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2542">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2543">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2543">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="27c3f-2544">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2544">tx_timer_change</span></span>

<span data-ttu-id="27c3f-2545">Cambiar un temporizador de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2545">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2546">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2546">Prototype</span></span>

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a><span data-ttu-id="27c3f-2547">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2547">Description</span></span>

<span data-ttu-id="27c3f-2548">Este servicio cambia las características de expiración del temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2548">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="27c3f-2549">El temporizador debe desactivarse antes de llamar a este servicio.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2549">The timer must be deactivated prior to calling this service.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2550">*Es necesaria una llamada al servicio* ***tx_timer_activate_** _ _tras este servicio para poder iniciar el temporizador de nuevo.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2550">*A call to the* ***tx_timer_activate** _ _service is required after this service in order to start the timer again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2551">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2551">Parameters</span></span>

- <span data-ttu-id="27c3f-2552">**timer_ptr**: puntero a un bloque de control del temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2552">**timer_ptr** Pointer to a timer control block.</span></span>
- <span data-ttu-id="27c3f-2553">**initial_ticks**: especifica el número inicial de tics para la expiración del temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2553">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="27c3f-2554">Los valores válidos oscilan entre 1 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2554">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="27c3f-2555">**reschedule_ticks**: especifica el número de tics para todas las expiraciones del temporizador después de la primera.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2555">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="27c3f-2556">Un cero para este parámetro convierte el temporizador en *monoestable*.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2556">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="27c3f-2557">En cambio, para los temporizadores periódicos, los valores válidos oscilan entre 1 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2557">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2558">*Un temporizador monoestable expirado se debe restablecer mediante*
***tx_timer_change** _ _para que se pueda volver a activar.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2558">*An expired one-shot timer must be reset via*
***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2559">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2559">Return Values</span></span>

- <span data-ttu-id="27c3f-2560">**TX_SUCCESS** (0x00): temporizador de aplicación cambiado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2560">**TX_SUCCESS** (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="27c3f-2561">**TX_TIMER_ERROR** (0x15): puntero de temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2561">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="27c3f-2562">**TX_TICK_ERROR** (0x16): el valor (cero) proporcionado para los tics iniciales no es válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2562">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="27c3f-2563">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2563">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2564">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2564">Allowed From</span></span>

<span data-ttu-id="27c3f-2565">Subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2565">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2566">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2566">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2567">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-2567">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2568">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2568">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Change a previously created and now deactivated timer
to expire every 50 timer ticks, including the initial
expiration. */
status = tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2569">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2569">See Also</span></span>

- <span data-ttu-id="27c3f-2570">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2570">tx_timer_activate</span></span>
- <span data-ttu-id="27c3f-2571">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2571">tx_timer_create</span></span>
- <span data-ttu-id="27c3f-2572">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2572">tx_timer_deactivate</span></span>
- <span data-ttu-id="27c3f-2573">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2573">tx_timer_delete</span></span>
- <span data-ttu-id="27c3f-2574">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2574">tx_timer_info_get</span></span>
- <span data-ttu-id="27c3f-2575">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2575">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2576">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2576">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="27c3f-2577">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2577">tx_timer_create</span></span>

<span data-ttu-id="27c3f-2578">Crear un temporizador de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2578">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2579">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2579">Prototype</span></span>

```c
UINT tx_timer_create(
    TX_TIMER *timer_ptr, 
    CHAR *name_ptr,
    VOID (*expiration_function)(ULONG),
    ULONG expiration_input, 
    ULONG initial_ticks,
    ULONG reschedule_ticks, 
    UINT auto_activate);
```

### <a name="description"></a><span data-ttu-id="27c3f-2580">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2580">Description</span></span>

<span data-ttu-id="27c3f-2581">Este servicio crea un temporizador de aplicación periódico con la función de expiración especificada y periódico.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2581">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2582">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2582">Parameters</span></span>

- <span data-ttu-id="27c3f-2583">**timer_ptr**: puntero a un bloque de control del temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2583">**timer_ptr** Pointer to a timer control block</span></span>
- <span data-ttu-id="27c3f-2584">**name_ptr**: puntero al nombre del temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2584">**name_ptr** Pointer to the name of the timer.</span></span>
- <span data-ttu-id="27c3f-2585">**expiration_function**: función de la aplicación que se va a llamar cuando expire el temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2585">**expiration_function** Application function to call when the timer expires.</span></span>
- <span data-ttu-id="27c3f-2586">**expiration_input**: entrada que se va a pasar a la función de expiración cuando expire el temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2586">**expiration_input** Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="27c3f-2587">**initial_ticks**: especifica el número inicial de tics para la expiración del temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2587">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="27c3f-2588">Los valores válidos oscilan entre 1 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2588">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="27c3f-2589">**reschedule_ticks**: especifica el número de tics para todas las expiraciones del temporizador después de la primera.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2589">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="27c3f-2590">Un cero para este parámetro convierte el temporizador en *monoestable*.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2590">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="27c3f-2591">En cambio, para los temporizadores periódicos, los valores válidos oscilan entre 1 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2591">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

  > [!NOTE]
  > <span data-ttu-id="27c3f-2592">*Cuando un temporizador monoestable expira, se debe restablecer mediante tx_timer_change para que se pueda volver a activar.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2592">*After a one-shot timer expires, it must be reset via   tx_timer_change before it can be activated again.*</span></span>

- <span data-ttu-id="27c3f-2593">**auto_activate**: determina si el temporizador se activa automáticamente durante la creación.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2593">**auto_activate** Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="27c3f-2594">Si este valor es **TX_AUTO_ACTIVATE** (0x01), el temporizador se activa.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2594">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="27c3f-2595">De lo contrario, si se selecciona el valor **TX_NO_ACTIVATE** (0x00), el temporizador se crea en un estado no activo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2595">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="27c3f-2596">En este caso, es necesario llamar con posterioridad al servicio **_tx_timer_activate_** para que realmente empiece el temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2596">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2597">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2597">Return Values</span></span>

- <span data-ttu-id="27c3f-2598">**TX_SUCCESS** (0x00): temporizador de aplicación creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2598">**TX_SUCCESS** (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="27c3f-2599">**TX_TIMER_ERROR** (0x15): puntero del temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2599">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="27c3f-2600">El puntero tiene un valor NULL o el temporizador ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2600">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="27c3f-2601">**TX_TICK_ERROR** (0x16): el valor (cero) proporcionado para los tics iniciales no es válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2601">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="27c3f-2602">**TX_ACTIVATE_ERROR** (0x17): la activación seleccionada no es válida.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2602">**TX_ACTIVATE_ERROR** (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="27c3f-2603">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2603">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2604">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2604">Allowed From</span></span>

<span data-ttu-id="27c3f-2605">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2605">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2606">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2606">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2607">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-2607">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2608">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2608">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Create an application timer that executes
"my_timer_function" after 100 ticks initially and then
after every 25 ticks. This timer is specified to start
immediately! */
status = tx_timer_create(&my_timer,"my_timer_name",
    my_timer_function, 0x1234, 100, 25,
    TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
be called 100 timer ticks later and then called every
25 timer ticks. Note that the value 0x1234 is passed to
my_timer_function every time it is called. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2609">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2609">See Also</span></span>

- <span data-ttu-id="27c3f-2610">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2610">tx_timer_activate</span></span>
- <span data-ttu-id="27c3f-2611">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2611">tx_timer_change</span></span>
- <span data-ttu-id="27c3f-2612">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2612">tx_timer_deactivate</span></span>
- <span data-ttu-id="27c3f-2613">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2613">tx_timer_delete</span></span>
- <span data-ttu-id="27c3f-2614">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2614">tx_timer_info_get</span></span>
- <span data-ttu-id="27c3f-2615">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2615">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2616">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2616">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="27c3f-2617">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2617">tx_timer_deactivate</span></span>

<span data-ttu-id="27c3f-2618">Desactivar un temporizador de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2618">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2619">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2619">Prototype</span></span>

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-2620">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2620">Description</span></span>

<span data-ttu-id="27c3f-2621">Este servicio desactiva el temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2621">This service deactivates the specified application timer.</span></span> <span data-ttu-id="27c3f-2622">Si el temporizador ya está desactivado, este servicio no tiene ningún efecto.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2622">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2623">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2623">Parameters</span></span>

- <span data-ttu-id="27c3f-2624">**timer_ptr**: puntero a un temporizador de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2624">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2625">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2625">Return Values</span></span>

- <span data-ttu-id="27c3f-2626">**TX_SUCCESS** (0x00): temporizador de aplicación desactivado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2626">**TX_SUCCESS** (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="27c3f-2627">**TX_TIMER_ERROR** (0x15): puntero del temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2627">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2628">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2628">Allowed From</span></span>

<span data-ttu-id="27c3f-2629">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2629">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2630">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2630">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2631">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-2631">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2632">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2632">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2633">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2633">See Also</span></span>

- <span data-ttu-id="27c3f-2634">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2634">tx_timer_activate</span></span>
- <span data-ttu-id="27c3f-2635">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2635">tx_timer_change</span></span>
- <span data-ttu-id="27c3f-2636">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2636">tx_timer_create</span></span>
- <span data-ttu-id="27c3f-2637">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2637">tx_timer_delete</span></span>
- <span data-ttu-id="27c3f-2638">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2638">tx_timer_info_get</span></span>
- <span data-ttu-id="27c3f-2639">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2639">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2640">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2640">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="27c3f-2641">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2641">tx_timer_delete</span></span>

<span data-ttu-id="27c3f-2642">Eliminar un temporizador de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2642">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2643">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2643">Prototype</span></span>

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="27c3f-2644">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2644">Description</span></span>

<span data-ttu-id="27c3f-2645">Este servicio elimina el temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2645">This service deletes the specified application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2646">*Es responsabilidad de la aplicación impedir el uso de un temporizador eliminado.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2646">*It is the application's responsibility to prevent use of a deleted timer.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2647">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2647">Parameters</span></span>

- <span data-ttu-id="27c3f-2648">**timer_ptr**: puntero a un temporizador de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2648">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2649">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2649">Return Values</span></span>

- <span data-ttu-id="27c3f-2650">**TX_SUCCESS** (0x00): temporizador de aplicación eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2650">**TX_SUCCESS** (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="27c3f-2651">**TX_TIMER_ERROR** (0x15): puntero del temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2651">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="27c3f-2652">**TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2652">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2653">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2653">Allowed From</span></span>

<span data-ttu-id="27c3f-2654">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2654">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2655">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2655">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2656">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-2656">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2657">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2657">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2658">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2658">See Also</span></span>

- <span data-ttu-id="27c3f-2659">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2659">tx_timer_activate</span></span>
- <span data-ttu-id="27c3f-2660">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2660">tx_timer_change</span></span>
- <span data-ttu-id="27c3f-2661">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2661">tx_timer_create</span></span>
- <span data-ttu-id="27c3f-2662">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2662">tx_timer_deactivate</span></span>
- <span data-ttu-id="27c3f-2663">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2663">tx_timer_info_get</span></span>
- <span data-ttu-id="27c3f-2664">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2664">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2665">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2665">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="27c3f-2666">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2666">tx_timer_info_get</span></span>

<span data-ttu-id="27c3f-2667">Recuperar información acerca de un temporizador de aplicación</span><span class="sxs-lookup"><span data-stu-id="27c3f-2667">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2668">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2668">Prototype</span></span>

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a><span data-ttu-id="27c3f-2669">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2669">Description</span></span>

<span data-ttu-id="27c3f-2670">Este servicio recupera información sobre el temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2670">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2671">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2671">Parameters</span></span>

- <span data-ttu-id="27c3f-2672">**timer_ptr**: puntero a un temporizador de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2672">**timer_ptr** Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="27c3f-2673">**name**: puntero al destino del puntero al nombre del temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2673">**name** Pointer to destination for the pointer to the timer's name.</span></span>
- <span data-ttu-id="27c3f-2674">**active**: puntero al destino de la indicación de temporizador activo.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2674">**active** Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="27c3f-2675">Si el temporizador está inactivo o se llama a este servicio desde el propio temporizador, se devuelve un valor **TX_FALSE**.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2675">If the timer is inactive or this service is called from the timer itself, a **TX_FALSE** value is returned.</span></span> <span data-ttu-id="27c3f-2676">En cambio, si el temporizador está activo, se devuelve un valor **TX_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2676">Otherwise, if the timer is active, a **TX_TRUE** value is returned.</span></span>
- <span data-ttu-id="27c3f-2677">**remaining_ticks**: puntero al destino del número de tics de temporizador que quedan antes de que expire.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2677">**remaining_ticks** Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="27c3f-2678">**reschedule_ticks**: puntero al destino del número de tics de temporizador que se usarán para volver a programarlo automáticamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2678">**reschedule_ticks** Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="27c3f-2679">Si el valor es cero, el temporizador es monoestable y no se volverá a programar.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2679">If the value is zero, then the timer is a one-shot and won't be rescheduled.</span></span>
- <span data-ttu-id="27c3f-2680">**next_timer**: puntero al destino del puntero del siguiente temporizador de aplicación creado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2680">**next_timer** Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2681">*La especificación de un valor **TX_NULL** para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2681">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2682">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2682">Return Values</span></span>

- <span data-ttu-id="27c3f-2683">**TX_SUCCESS** (0x00): información del temporizador recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2683">**TX_SUCCESS** (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="27c3f-2684">**TX_TIMER_ERROR** (0x15): puntero del temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2684">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2685">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2685">Allowed From</span></span>

<span data-ttu-id="27c3f-2686">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2686">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27c3f-2687">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="27c3f-2687">Preemption Possible</span></span>

<span data-ttu-id="27c3f-2688">No</span><span class="sxs-lookup"><span data-stu-id="27c3f-2688">No</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2689">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2689">Example</span></span>

```c
TX_TIMER my_timer;
CHAR *name;
UINT active;
ULONG remaining_ticks;
ULONG reschedule_ticks;
TX_TIMER *next_timer;
UINT status;

/* Retrieve information about the previously created
application timer "my_timer." */
status = tx_timer_info_get(&my_timer, &name,
    &active,&remaining_ticks,
    &reschedule_ticks,
    &next_timer);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2690">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2690">See Also</span></span>

- <span data-ttu-id="27c3f-2691">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2691">tx_timer_activate</span></span>
- <span data-ttu-id="27c3f-2692">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2692">tx_timer_change</span></span>
- <span data-ttu-id="27c3f-2693">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2693">tx_timer_create</span></span>
- <span data-ttu-id="27c3f-2694">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2694">tx_timer_deactivate</span></span>
- <span data-ttu-id="27c3f-2695">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2695">tx_timer_delete</span></span>
- <span data-ttu-id="27c3f-2696">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2696">tx_timer_info_get</span></span>
- <span data-ttu-id="27c3f-2697">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2697">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27c3f-2698">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2698">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="27c3f-2699">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2699">tx_timer_performance_info_get</span></span>

<span data-ttu-id="27c3f-2700">Obtener información acerca del rendimiento de un temporizador</span><span class="sxs-lookup"><span data-stu-id="27c3f-2700">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2701">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2701">Prototype</span></span>

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="27c3f-2702">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2702">Description</span></span>

<span data-ttu-id="27c3f-2703">Este servicio recupera información sobre el rendimiento del temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2703">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-2704">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2704">*The ThreadX library and application must be built with* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27c3f-2705">Parámetros</span><span class="sxs-lookup"><span data-stu-id="27c3f-2705">Parameters</span></span>
- <span data-ttu-id="27c3f-2706">**timer_ptr**: puntero a un temporizador creado previamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2706">**timer_ptr** Pointer to previously created timer.</span></span>
- <span data-ttu-id="27c3f-2707">**activates**: puntero al destino del número de solicitudes de activación realizadas en este temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2707">**activates** Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="27c3f-2708">**reactivates**: puntero al destino del número de reactivaciones automáticas realizadas en este temporizador periódico.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2708">**reactivates** Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="27c3f-2709">**deactivates**: puntero al destino del número de solicitudes de desactivación realizadas en este temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2709">**deactivates** Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="27c3f-2710">**expirations**: puntero al destino del número de expiraciones de este temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2710">**expirations** Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="27c3f-2711">**expiration_adjusts**: puntero al destino del número de ajustes de expiración internos realizados en este temporizador.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2711">**expiration_adjusts** Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="27c3f-2712">Estos ajustes se realizan en el procesamiento de interrupciones del temporizador para los temporizadores mayores que el tamaño predeterminado de la lista de temporizadores (de manera predeterminada, los temporizadores con expiraciones superiores a 32 tics).</span><span class="sxs-lookup"><span data-stu-id="27c3f-2712">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> <span data-ttu-id="27c3f-2713">[NOTA] *La especificación de un valor TX_NULL para cualquier parámetro indica que el parámetro no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2713">[NOTE] *Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2714">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2714">Return Values</span></span>

- <span data-ttu-id="27c3f-2715">**TX_SUCCESS** (0x00): rendimiento del temporizador obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2715">**TX_SUCCESS** (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="27c3f-2716">**TX_PTR_ERROR** (0x03): puntero del temporizador no válido.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2716">**TX_PTR_ERROR** (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="27c3f-2717">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2718">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2718">Allowed From</span></span>

<span data-ttu-id="27c3f-2719">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2719">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2720">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2720">Example</span></span>

```c
TX_TIMER my_timer;
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on the previously created
timer. */
status = tx_timer_performance_info_get(&my_timer, &activates,
    &reactivates,&deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2721">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2721">See Also</span></span>

- <span data-ttu-id="27c3f-2722">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2722">tx_timer_activate</span></span>
- <span data-ttu-id="27c3f-2723">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2723">tx_timer_change</span></span>
- <span data-ttu-id="27c3f-2724">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2724">tx_timer_create</span></span>
- <span data-ttu-id="27c3f-2725">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2725">tx_timer_deactivate</span></span>
- <span data-ttu-id="27c3f-2726">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2726">tx_timer_delete</span></span>
- <span data-ttu-id="27c3f-2727">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2727">tx_timer_info_get</span></span>
- <span data-ttu-id="27c3f-2728">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2728">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="27c3f-2729">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2729">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="27c3f-2730">Obtener información acerca del rendimiento del sistema de un temporizador</span><span class="sxs-lookup"><span data-stu-id="27c3f-2730">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27c3f-2731">Prototipo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2731">Prototype</span></span>

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="27c3f-2732">Descripción</span><span class="sxs-lookup"><span data-stu-id="27c3f-2732">Description</span></span>

<span data-ttu-id="27c3f-2733">Este servicio recupera información sobre el rendimiento de todos los temporizadores de aplicación del sistema.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2733">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27c3f-2734">*La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_TIMER_ENABLE_PERFORMANCE_INFO**  *definido para que devuelva información sobre el rendimiento.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2734">*The ThreadX library and application must be built with* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

<span data-ttu-id="27c3f-2735">**Parámetros**</span><span class="sxs-lookup"><span data-stu-id="27c3f-2735">**Parameters**</span></span>

- <span data-ttu-id="27c3f-2736">**activates**: puntero al destino del número total de solicitudes de activación realizadas en todos los temporizadores.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2736">**activates** Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="27c3f-2737">**reactivates**: puntero al destino del número total de reactivaciones automáticas realizadas en todos los temporizadores periódicos.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2737">**reactivates** Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="27c3f-2738">**deactivates**: puntero al destino del número total de solicitudes de desactivación realizadas en todos los temporizadores.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2738">**deactivates** Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="27c3f-2739">**expirations**: puntero al destino del número total de expiraciones de todos los temporizadores.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2739">**expirations** Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="27c3f-2740">**expiration_adjusts**: puntero al destino del número total de ajustes de expiración internos realizados en todos los temporizadores.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2740">**expiration_adjusts** Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="27c3f-2741">Estos ajustes se realizan en el procesamiento de interrupciones del temporizador para los temporizadores mayores que el tamaño predeterminado de la lista de temporizadores (de manera predeterminada, los temporizadores con expiraciones superiores a 32 tics).</span><span class="sxs-lookup"><span data-stu-id="27c3f-2741">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!NOTE]
> <span data-ttu-id="27c3f-2742">*La especificación de un valor **TX_NULL** para cualquier parámetro indica que este no es necesario.*</span><span class="sxs-lookup"><span data-stu-id="27c3f-2742">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27c3f-2743">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="27c3f-2743">Return Values</span></span>

- <span data-ttu-id="27c3f-2744">**TX_SUCCESS**: (0x00): rendimiento del sistema del temporizador obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2744">**TX_SUCCESS** (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="27c3f-2745">**TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="27c3f-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27c3f-2746">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="27c3f-2746">Allowed From</span></span>

<span data-ttu-id="27c3f-2747">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="27c3f-2747">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27c3f-2748">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27c3f-2748">Example</span></span>

```c
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on all previously created
timers. */
status = tx_timer_performance_system_info_get(&activates,
    &reactivates, &deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="27c3f-2749">Consulte también</span><span class="sxs-lookup"><span data-stu-id="27c3f-2749">See Also</span></span>

- <span data-ttu-id="27c3f-2750">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2750">tx_timer_activate</span></span>
- <span data-ttu-id="27c3f-2751">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27c3f-2751">tx_timer_change</span></span>
- <span data-ttu-id="27c3f-2752">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27c3f-2752">tx_timer_create</span></span>
- <span data-ttu-id="27c3f-2753">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27c3f-2753">tx_timer_deactivate</span></span>
- <span data-ttu-id="27c3f-2754">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27c3f-2754">tx_timer_delete</span></span>
- <span data-ttu-id="27c3f-2755">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2755">tx_timer_info_get</span></span>
- <span data-ttu-id="27c3f-2756">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27c3f-2756">tx_timer_performance_info_get</span></span>
