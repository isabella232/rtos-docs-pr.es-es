---
title: Información general sobre Azure RTOS ThreadX
description: Azure ThreadX es un sistema operativo en tiempo real (RTOS) avanzado diseñado específicamente para aplicaciones profundamente insertadas.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0fb861c2291046c2ac6edf1d03014996daa09a8e
ms.sourcegitcommit: c1b00341e0c5ab71372f3d9cc4ee3bdd3702b805
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2021
ms.locfileid: "111988369"
---
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="9b472-103">Información general sobre Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="9b472-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="9b472-104">Azure RTOS ThreadX es el sistema operativo en tiempo real (RTOS) avanzado de nivel industrial de Microsoft diseñado específicamente para aplicaciones profundamente insertadas en tiempo real de IoT.</span><span class="sxs-lookup"><span data-stu-id="9b472-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="9b472-105">Azure RTOS ThreadX proporciona recursos avanzados de programación, comunicación, sincronización, temporización, administración de memoria y administración de interrupciones.</span><span class="sxs-lookup"><span data-stu-id="9b472-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="9b472-106">Además, Azure RTOS ThreadX tiene muchas características avanzadas, como su arquitectura picokernel™, la programación preemption-threshold™, event-chaining™, la generación de perfiles de ejecución, las métricas de rendimiento y el seguimiento de eventos del sistema.</span><span class="sxs-lookup"><span data-stu-id="9b472-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="9b472-107">En combinación con su excelente facilidad de uso, Azure RTOS ThreadX es la opción ideal para las aplicaciones insertadas más exigentes.</span><span class="sxs-lookup"><span data-stu-id="9b472-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="9b472-108">En 2017, Azure RTOS ThreadX presumía de más de 6200 millones de implementaciones en una amplia gama de productos, incluidos dispositivos de consumo, electrónica médica y equipos de control industrial.</span><span class="sxs-lookup"><span data-stu-id="9b472-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="9b472-109">Protocolos de API</span><span class="sxs-lookup"><span data-stu-id="9b472-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="9b472-110">Servicios de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="9b472-110">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="9b472-111">Creación de subprocesos dinámica</span><span class="sxs-lookup"><span data-stu-id="9b472-111">Dynamic thread creation</span></span>
* <span data-ttu-id="9b472-112">Sin límites en el número de subprocesos</span><span class="sxs-lookup"><span data-stu-id="9b472-112">No limits on the number of threads</span></span>
* <span data-ttu-id="9b472-113">Las API de subprocesos principales incluyen:</span><span class="sxs-lookup"><span data-stu-id="9b472-113">Main thread APIs include:</span></span>
  * <span data-ttu-id="9b472-114">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="9b472-114">tx_thread_create</span></span>
  * <span data-ttu-id="9b472-115">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="9b472-115">tx_thread_delete</span></span>
  * <span data-ttu-id="9b472-116">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="9b472-116">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="9b472-117">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="9b472-117">tx_thread_priority_change</span></span>
  * <span data-ttu-id="9b472-118">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="9b472-118">tx_thread_relinquish</span></span>
  * <span data-ttu-id="9b472-119">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="9b472-119">tx_thread_reset</span></span>
  * <span data-ttu-id="9b472-120">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="9b472-120">tx_thread_resume</span></span>
  * <span data-ttu-id="9b472-121">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="9b472-121">tx_thread_sleep</span></span>
  * <span data-ttu-id="9b472-122">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="9b472-122">tx_thread_suspend</span></span>
  * <span data-ttu-id="9b472-123">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="9b472-123">tx_thread_terminate</span></span>
  * <span data-ttu-id="9b472-124">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="9b472-124">tx_thread_wait_abort</span></span>
* <span data-ttu-id="9b472-125">API de información adicional y rendimiento</span><span class="sxs-lookup"><span data-stu-id="9b472-125">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="9b472-126">Colas de mensajes</span><span class="sxs-lookup"><span data-stu-id="9b472-126">Message Queues</span></span>

* <span data-ttu-id="9b472-127">Creación de colas dinámica</span><span class="sxs-lookup"><span data-stu-id="9b472-127">Dynamic queue creation</span></span>
* <span data-ttu-id="9b472-128">Sin límites en el número de colas</span><span class="sxs-lookup"><span data-stu-id="9b472-128">No limits on the number of queues</span></span>
* <span data-ttu-id="9b472-129">Mensajes copiados por valor (o por referencia mediante puntero)</span><span class="sxs-lookup"><span data-stu-id="9b472-129">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="9b472-130">Tamaños de mensaje de 1 a 16 palabras de 32 bits</span><span class="sxs-lookup"><span data-stu-id="9b472-130">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="9b472-131">Suspensión de subprocesos opcional en bloques vacíos o llenos</span><span class="sxs-lookup"><span data-stu-id="9b472-131">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="9b472-132">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="9b472-132">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9b472-133">Las principales API de colas de mensajes incluyen:</span><span class="sxs-lookup"><span data-stu-id="9b472-133">Main message queue APIs include:</span></span>
  * <span data-ttu-id="9b472-134">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="9b472-134">tx_queue_create</span></span>
  * <span data-ttu-id="9b472-135">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="9b472-135">tx_queue_delete</span></span>
  * <span data-ttu-id="9b472-136">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="9b472-136">tx_queue_flush</span></span>
  * <span data-ttu-id="9b472-137">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="9b472-137">tx_queue_front_send</span></span>
  * <span data-ttu-id="9b472-138">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="9b472-138">tx_queue_receive</span></span>
  * <span data-ttu-id="9b472-139">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="9b472-139">tx_queue_send_notify</span></span>
* <span data-ttu-id="9b472-140">API de información adicional y rendimiento</span><span class="sxs-lookup"><span data-stu-id="9b472-140">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="9b472-141">Semáforos de recuento</span><span class="sxs-lookup"><span data-stu-id="9b472-141">Counting Semaphores</span></span>

* <span data-ttu-id="9b472-142">Creación dinámica de semáforos</span><span class="sxs-lookup"><span data-stu-id="9b472-142">Dynamic semaphore creation</span></span>
* <span data-ttu-id="9b472-143">Sin límites en el número de semáforos</span><span class="sxs-lookup"><span data-stu-id="9b472-143">No limits on the number of semaphores</span></span>
* <span data-ttu-id="9b472-144">Semáforos de recuento de 32 bits (de 0 a 4 294 967 295)</span><span class="sxs-lookup"><span data-stu-id="9b472-144">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="9b472-145">Compatibilidad con la protección de recursos o consumidor-productor</span><span class="sxs-lookup"><span data-stu-id="9b472-145">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="9b472-146">Suspensión de subprocesos opcional si no hay semáforos disponibles</span><span class="sxs-lookup"><span data-stu-id="9b472-146">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="9b472-147">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="9b472-147">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9b472-148">Las API de semáforos principales incluyen:</span><span class="sxs-lookup"><span data-stu-id="9b472-148">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="9b472-149">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="9b472-149">tx_semaphore_create</span></span>
  * <span data-ttu-id="9b472-150">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="9b472-150">tx_semaphore_delete</span></span>
  * <span data-ttu-id="9b472-151">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="9b472-151">tx_semaphore_get</span></span>
  * <span data-ttu-id="9b472-152">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="9b472-152">tx_semaphore_put</span></span>
  * <span data-ttu-id="9b472-153">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="9b472-153">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="9b472-154">API de información adicional y rendimiento</span><span class="sxs-lookup"><span data-stu-id="9b472-154">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="9b472-155">Mutexes</span><span class="sxs-lookup"><span data-stu-id="9b472-155">Mutexes</span></span>

* <span data-ttu-id="9b472-156">Creación de exclusiones mutuas dinámica</span><span class="sxs-lookup"><span data-stu-id="9b472-156">Dynamic mutex creation</span></span>
* <span data-ttu-id="9b472-157">Sin límites en el número de exclusiones mutuas</span><span class="sxs-lookup"><span data-stu-id="9b472-157">No limits on the number of mutexes</span></span>
* <span data-ttu-id="9b472-158">Compatibilidad con la protección de recursos anidados</span><span class="sxs-lookup"><span data-stu-id="9b472-158">Nested resource protection supported</span></span>
* <span data-ttu-id="9b472-159">Compatibilidad con la herencia de prioridad opcional</span><span class="sxs-lookup"><span data-stu-id="9b472-159">Optional priority inheritance supported</span></span>
* <span data-ttu-id="9b472-160">Suspensión de subprocesos opcional si no hay exclusiones mutuas disponibles</span><span class="sxs-lookup"><span data-stu-id="9b472-160">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="9b472-161">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="9b472-161">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9b472-162">Las principales API de exclusiones mutuas incluyen:</span><span class="sxs-lookup"><span data-stu-id="9b472-162">Main mutex APIs include:</span></span>
  * <span data-ttu-id="9b472-163">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="9b472-163">tx_mutex_create</span></span>
  * <span data-ttu-id="9b472-164">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="9b472-164">tx_mutex_delete</span></span>
  * <span data-ttu-id="9b472-165">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="9b472-165">tx_mutex_get</span></span>
  * <span data-ttu-id="9b472-166">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="9b472-166">tx_mutex_put</span></span>
* <span data-ttu-id="9b472-167">API de información adicional y rendimiento</span><span class="sxs-lookup"><span data-stu-id="9b472-167">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="9b472-168">Marcas de eventos</span><span class="sxs-lookup"><span data-stu-id="9b472-168">Event Flags</span></span>

* <span data-ttu-id="9b472-169">Creación de grupos de marcas de eventos dinámica</span><span class="sxs-lookup"><span data-stu-id="9b472-169">Dynamic event flag group creation</span></span>
* <span data-ttu-id="9b472-170">Sin límites en el número de grupos de marcas de eventos</span><span class="sxs-lookup"><span data-stu-id="9b472-170">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="9b472-171">Sincronización de un subproceso o de varios</span><span class="sxs-lookup"><span data-stu-id="9b472-171">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="9b472-172">Compatibilidad con la obtención y eliminación atómicas</span><span class="sxs-lookup"><span data-stu-id="9b472-172">Atomic get and clear supported</span></span>
* <span data-ttu-id="9b472-173">Suspensión de subprocesos opcional en conjunto de eventos AND/OR</span><span class="sxs-lookup"><span data-stu-id="9b472-173">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="9b472-174">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="9b472-174">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9b472-175">Las API de marcas de eventos principales incluyen:</span><span class="sxs-lookup"><span data-stu-id="9b472-175">Main event flag APIs include:</span></span>
  * <span data-ttu-id="9b472-176">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="9b472-176">tx_event_flags_create</span></span>
  * <span data-ttu-id="9b472-177">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="9b472-177">tx_event_flags_delete</span></span>
  * <span data-ttu-id="9b472-178">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="9b472-178">tx_event_flags_get</span></span>
  * <span data-ttu-id="9b472-179">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="9b472-179">tx_event_flags_set</span></span>
  * <span data-ttu-id="9b472-180">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="9b472-180">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="9b472-181">API de información adicional y rendimiento</span><span class="sxs-lookup"><span data-stu-id="9b472-181">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="9b472-182">Bloques de memoria de bloques</span><span class="sxs-lookup"><span data-stu-id="9b472-182">Block Memory Pools</span></span>

* <span data-ttu-id="9b472-183">Creación de bloques dinámica</span><span class="sxs-lookup"><span data-stu-id="9b472-183">Dynamic block pool creation</span></span>
* <span data-ttu-id="9b472-184">Sin límites en el número de bloques</span><span class="sxs-lookup"><span data-stu-id="9b472-184">No limits on the number of block pools</span></span>
* <span data-ttu-id="9b472-185">Sin límites en cuanto al tamaño de los bloques de tamaño fijo ni el tamaño del bloque</span><span class="sxs-lookup"><span data-stu-id="9b472-185">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="9b472-186">Asignación o desasignación de memoria lo más rápida posible</span><span class="sxs-lookup"><span data-stu-id="9b472-186">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="9b472-187">Suspensión de subprocesos opcional en bloques vacíos</span><span class="sxs-lookup"><span data-stu-id="9b472-187">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="9b472-188">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="9b472-188">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9b472-189">Las API de bloques principales incluyen:</span><span class="sxs-lookup"><span data-stu-id="9b472-189">Main block pool APIs include:</span></span>
  * <span data-ttu-id="9b472-190">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="9b472-190">tx_block_pool_create</span></span>
  * <span data-ttu-id="9b472-191">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="9b472-191">tx_block_pool_delete</span></span>
  * <span data-ttu-id="9b472-192">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="9b472-192">tx_block_allocate</span></span>
  * <span data-ttu-id="9b472-193">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="9b472-193">tx_block_release</span></span>
* <span data-ttu-id="9b472-194">API de información adicional y rendimiento</span><span class="sxs-lookup"><span data-stu-id="9b472-194">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="9b472-195">Bloques de memoria de bytes</span><span class="sxs-lookup"><span data-stu-id="9b472-195">Byte Memory Pools</span></span>

* <span data-ttu-id="9b472-196">Creación de bloques de bytes dinámica</span><span class="sxs-lookup"><span data-stu-id="9b472-196">Dynamic byte pool creation</span></span>
* <span data-ttu-id="9b472-197">Sin límites en el número de bloques de bytes</span><span class="sxs-lookup"><span data-stu-id="9b472-197">No limits on the number of byte pools</span></span>
* <span data-ttu-id="9b472-198">Sin límites en el tamaño del bloque de bytes</span><span class="sxs-lookup"><span data-stu-id="9b472-198">No limits on size of byte pool</span></span>
* <span data-ttu-id="9b472-199">Asignación o desasignación de memoria de longitud variable más flexible</span><span class="sxs-lookup"><span data-stu-id="9b472-199">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="9b472-200">Situación de tamaño de asignación compatible</span><span class="sxs-lookup"><span data-stu-id="9b472-200">Allocation size locality supported</span></span>
* <span data-ttu-id="9b472-201">Suspensión de subprocesos opcional en bloques vacíos</span><span class="sxs-lookup"><span data-stu-id="9b472-201">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="9b472-202">Tiempo de espera opcional en todas las suspensiones</span><span class="sxs-lookup"><span data-stu-id="9b472-202">Optional timeout on all suspension</span></span>
* <span data-ttu-id="9b472-203">Las API de bloques de bytes principales incluyen:</span><span class="sxs-lookup"><span data-stu-id="9b472-203">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="9b472-204">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="9b472-204">tx_byte_pool_create</span></span>
  * <span data-ttu-id="9b472-205">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="9b472-205">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="9b472-206">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="9b472-206">tx_byte_allocate</span></span>
  * <span data-ttu-id="9b472-207">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="9b472-207">tx_byte_release</span></span>
* <span data-ttu-id="9b472-208">API de información adicional y rendimiento</span><span class="sxs-lookup"><span data-stu-id="9b472-208">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="9b472-209">Temporizadores de aplicación</span><span class="sxs-lookup"><span data-stu-id="9b472-209">Application Timers</span></span>

* <span data-ttu-id="9b472-210">Creación dinámica de temporizadores</span><span class="sxs-lookup"><span data-stu-id="9b472-210">Dynamic timer creation</span></span>
* <span data-ttu-id="9b472-211">Sin límites en el número de temporizadores</span><span class="sxs-lookup"><span data-stu-id="9b472-211">No limits on the number of timers</span></span>
* <span data-ttu-id="9b472-212">Compatibilidad con temporizadores periódicos o monoestables</span><span class="sxs-lookup"><span data-stu-id="9b472-212">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="9b472-213">Los temporizadores periódicos pueden tener un valor de expiración inicial diferente</span><span class="sxs-lookup"><span data-stu-id="9b472-213">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="9b472-214">Sin búsqueda durante la activación o desactivación del temporizador</span><span class="sxs-lookup"><span data-stu-id="9b472-214">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="9b472-215">Todos los temporizadores se controlan desde una interrupción de temporizador de hardware</span><span class="sxs-lookup"><span data-stu-id="9b472-215">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="9b472-216">Las API de temporizadores principales incluyen:</span><span class="sxs-lookup"><span data-stu-id="9b472-216">Main timer APIs include:</span></span>
  * <span data-ttu-id="9b472-217">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="9b472-217">tx_timer_create</span></span>
  * <span data-ttu-id="9b472-218">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="9b472-218">tx_timer_delete</span></span>
  * <span data-ttu-id="9b472-219">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="9b472-219">tx_timer_activate</span></span>
  * <span data-ttu-id="9b472-220">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="9b472-220">tx_timer_change</span></span>
  * <span data-ttu-id="9b472-221">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="9b472-221">tx_timer_deactivate</span></span>
* <span data-ttu-id="9b472-222">API de información adicional y rendimiento</span><span class="sxs-lookup"><span data-stu-id="9b472-222">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="9b472-223">Programador principal de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="9b472-223">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="9b472-224">Superficie mínima de 2 KB FLASH y 1 KB RAM</span><span class="sxs-lookup"><span data-stu-id="9b472-224">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="9b472-225">Cambio de contexto rápido submicrosegundo</span><span class="sxs-lookup"><span data-stu-id="9b472-225">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="9b472-226">Totalmente determinista independientemente del número de subprocesos</span><span class="sxs-lookup"><span data-stu-id="9b472-226">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="9b472-227">Programación totalmente preventiva basada en prioridad</span><span class="sxs-lookup"><span data-stu-id="9b472-227">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="9b472-228">32 niveles de prioridad predeterminados, opcionalmente hasta 1024 niveles</span><span class="sxs-lookup"><span data-stu-id="9b472-228">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="9b472-229">Programación cooperativa en nivel de prioridad (FIFO)</span><span class="sxs-lookup"><span data-stu-id="9b472-229">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="9b472-230">Tecnología de umbral de prevención</span><span class="sxs-lookup"><span data-stu-id="9b472-230">Preemption-threshold technology</span></span>
* <span data-ttu-id="9b472-231">Servicios de temporizador opcionales, incluidos:</span><span class="sxs-lookup"><span data-stu-id="9b472-231">Optional timer services, including:</span></span>
  * <span data-ttu-id="9b472-232">Porción de tiempo opcional por subproceso</span><span class="sxs-lookup"><span data-stu-id="9b472-232">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="9b472-233">Tiempo de espera opcional en todos los bloqueos</span><span class="sxs-lookup"><span data-stu-id="9b472-233">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="9b472-234">Las API requieren interrupción de temporizador de hardware</span><span class="sxs-lookup"><span data-stu-id="9b472-234">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="9b472-235">Generación de perfiles de ejecución</span><span class="sxs-lookup"><span data-stu-id="9b472-235">Execution profiling</span></span>
* <span data-ttu-id="9b472-236">Seguimiento de nivel de sistema</span><span class="sxs-lookup"><span data-stu-id="9b472-236">System-level Trace</span></span>
* <span data-ttu-id="9b472-237">Seguridad certificada para muchos estándares</span><span class="sxs-lookup"><span data-stu-id="9b472-237">Safety certified to many standards</span></span>

## <a name="most-deployed-rtos"></a><span data-ttu-id="9b472-238">RTOS más implementado</span><span class="sxs-lookup"><span data-stu-id="9b472-238">Most deployed RTOS</span></span>

<span data-ttu-id="9b472-239">Azure RTOS ThreadX presume de más de 6200 millones de implementaciones en todo el mundo, de acuerdo con la principal empresa de inteligencia de mercado de M2M, VDC Research.</span><span class="sxs-lookup"><span data-stu-id="9b472-239">Azure RTOS ThreadX has over 6.2 billion deployments worldwide, according to the leading M2M market intelligence firm, VDC Research.</span></span> <span data-ttu-id="9b472-240">La popularidad de Azure RTOS ThreadX se debe a sus ventajas de confiabilidad, calidad, tamaño, rendimiento, características avanzadas, facilidad de uso y tiempo de comercialización general.</span><span class="sxs-lookup"><span data-stu-id="9b472-240">The popularity of Azure RTOS ThreadX is a testament to its reliability, quality, size, performance, advanced features, ease-of-use, and overall time-to-market advantages.</span></span>

> <span data-ttu-id="9b472-241">*"Hemos seguido la trayectoria de crecimiento de THREADX en los mercados inalámbricos y de IoT desde la fundación de la empresa y estamos cada vez más impresionados de la adopción de THREADX por parte del sector".*</span><span class="sxs-lookup"><span data-stu-id="9b472-241">*“We have followed the growth trajectory of THREADX in the wireless and IoT markets since the company’s founding, and are increasingly impressed by the widespread industry adoption of THREADX.”*</span></span> <span data-ttu-id="9b472-242">– Chris Rommel, Vicepresidente Ejecutivo, VDC Research.</span><span class="sxs-lookup"><span data-stu-id="9b472-242">– Chris Rommel, Executive Vice President, VDC Research</span></span>

## <a name="small-footprint"></a><span data-ttu-id="9b472-243">Superficie pequeña</span><span class="sxs-lookup"><span data-stu-id="9b472-243">Small footprint</span></span>

<span data-ttu-id="9b472-244">Azure RTOS ThreadX requiere un área de instrucciones increíblemente pequeña de 2 KB y 1 KB de RAM para su superficie mínima.</span><span class="sxs-lookup"><span data-stu-id="9b472-244">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="9b472-245">Esto se debe en gran medida a su arquitectura picokernel™ sin superposición y al escalado automático.</span><span class="sxs-lookup"><span data-stu-id="9b472-245">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="9b472-246">El escalado automático significa que solo los servicios (y la infraestructura de apoyo) que usa la aplicación se incluyen en la imagen final en tiempo de vínculo.</span><span class="sxs-lookup"><span data-stu-id="9b472-246">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="9b472-247">Estas son algunas de las características de tamaño típicas de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="9b472-247">Here are some typical Azure RTOS ThreadX size characteristics.</span></span>

|<span data-ttu-id="9b472-248">Servicio de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="9b472-248">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="9b472-249">Tamaño típico en bytes</span><span class="sxs-lookup"><span data-stu-id="9b472-249">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="9b472-250">Servicios principales (requeridos)</span><span class="sxs-lookup"><span data-stu-id="9b472-250">Core Services (Require)</span></span> |<span data-ttu-id="9b472-251">2\.000</span><span class="sxs-lookup"><span data-stu-id="9b472-251">2,000</span></span>  |
|<span data-ttu-id="9b472-252">Servicios de colas</span><span class="sxs-lookup"><span data-stu-id="9b472-252">Queue Services</span></span>  |<span data-ttu-id="9b472-253">900</span><span class="sxs-lookup"><span data-stu-id="9b472-253">900</span></span>  |
|<span data-ttu-id="9b472-254">Servicios de marcas de eventos</span><span class="sxs-lookup"><span data-stu-id="9b472-254">Event Flag Services</span></span>  |<span data-ttu-id="9b472-255">900</span><span class="sxs-lookup"><span data-stu-id="9b472-255">900</span></span>  |
|<span data-ttu-id="9b472-256">Servicios de semáforos</span><span class="sxs-lookup"><span data-stu-id="9b472-256">Semaphore Services</span></span>  |<span data-ttu-id="9b472-257">450</span><span class="sxs-lookup"><span data-stu-id="9b472-257">450</span></span>  |
|<span data-ttu-id="9b472-258">Servicios de exclusiones mutuas</span><span class="sxs-lookup"><span data-stu-id="9b472-258">Mutex Services</span></span>  |<span data-ttu-id="9b472-259">1,200</span><span class="sxs-lookup"><span data-stu-id="9b472-259">1,200</span></span>  |
|<span data-ttu-id="9b472-260">Servicios de memoria de bloques</span><span class="sxs-lookup"><span data-stu-id="9b472-260">Block Memory Services</span></span>  |<span data-ttu-id="9b472-261">550</span><span class="sxs-lookup"><span data-stu-id="9b472-261">550</span></span>  |
|<span data-ttu-id="9b472-262">Servicios de memoria de bytes</span><span class="sxs-lookup"><span data-stu-id="9b472-262">Byte Memory Services</span></span>  |<span data-ttu-id="9b472-263">900</span><span class="sxs-lookup"><span data-stu-id="9b472-263">900</span></span>  |

## <a name="fast-execution"></a><span data-ttu-id="9b472-264">Ejecución rápida</span><span class="sxs-lookup"><span data-stu-id="9b472-264">Fast execution</span></span>

<span data-ttu-id="9b472-265">Azure RTOS ThreadX logra un cambio de contexto submicrosegundo en los procesadores más populares y, en general, es considerablemente más rápido que otros RTOS comerciales.</span><span class="sxs-lookup"><span data-stu-id="9b472-265">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="9b472-266">Además de ser rápido, Azure RTOS ThreadX también es muy determinista.</span><span class="sxs-lookup"><span data-stu-id="9b472-266">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="9b472-267">Consigue el mismo rendimiento rápido tanto si hay 200 subprocesos listos como si hay solo uno.</span><span class="sxs-lookup"><span data-stu-id="9b472-267">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="9b472-268">Estas son algunas características de rendimiento típicas de Azure RTOS ThreadX:</span><span class="sxs-lookup"><span data-stu-id="9b472-268">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="9b472-269">Arranque rápido: Azure RTOS ThreadX arranca en menos de 120 ciclos.</span><span class="sxs-lookup"><span data-stu-id="9b472-269">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="9b472-270">Eliminación opcional de comprobación de errores básica: la comprobación de errores básica de Azure RTOS ThreadX se puede omitir en tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="9b472-270">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="9b472-271">Esto puede ser útil cuando se ha verificado el código de la aplicación y ya no se requiere la comprobación de errores en cada parámetro.</span><span class="sxs-lookup"><span data-stu-id="9b472-271">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="9b472-272">Tenga en cuenta que esto puede hacerse en una unidad de compilación y no en todo el sistema.</span><span class="sxs-lookup"><span data-stu-id="9b472-272">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="9b472-273">Diseño picokernel™: los servicios no se superponen entre sí, con lo que se elimina la sobrecarga de llamadas a funciones innecesarias.</span><span class="sxs-lookup"><span data-stu-id="9b472-273">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="9b472-274">\*Procesamiento de interrupciones optimizado: solo se guardan o restauran registros desde cero tras la entrada o salida del ISR, a menos que se necesite prevención.</span><span class="sxs-lookup"><span data-stu-id="9b472-274">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="9b472-275">Procesamiento de API optimizado:</span><span class="sxs-lookup"><span data-stu-id="9b472-275">Optimized API Processing:</span></span>

    |<span data-ttu-id="9b472-276">Servicio de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="9b472-276">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="9b472-277">Tiempo de servicio en microsegundos\*</span><span class="sxs-lookup"><span data-stu-id="9b472-277">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="9b472-278">Suspensión de subproceso</span><span class="sxs-lookup"><span data-stu-id="9b472-278">Thread Suspend</span></span>  |<span data-ttu-id="9b472-279">0.6</span><span class="sxs-lookup"><span data-stu-id="9b472-279">0.6</span></span>  |
    |<span data-ttu-id="9b472-280">Reanudación de subproceso</span><span class="sxs-lookup"><span data-stu-id="9b472-280">Thread Resume</span></span>  |<span data-ttu-id="9b472-281">0.6</span><span class="sxs-lookup"><span data-stu-id="9b472-281">0.6</span></span>  |
    |<span data-ttu-id="9b472-282">Envío a la cola</span><span class="sxs-lookup"><span data-stu-id="9b472-282">Queue Send</span></span>  |<span data-ttu-id="9b472-283">0,3</span><span class="sxs-lookup"><span data-stu-id="9b472-283">0.3</span></span>  |
    |<span data-ttu-id="9b472-284">Recepción en la cola</span><span class="sxs-lookup"><span data-stu-id="9b472-284">Queue Receive</span></span>  |<span data-ttu-id="9b472-285">0,3</span><span class="sxs-lookup"><span data-stu-id="9b472-285">0.3</span></span>  |
    |<span data-ttu-id="9b472-286">Obtención de semáforo</span><span class="sxs-lookup"><span data-stu-id="9b472-286">Get Semaphore</span></span>  |<span data-ttu-id="9b472-287">0,2</span><span class="sxs-lookup"><span data-stu-id="9b472-287">0.2</span></span>  |
    |<span data-ttu-id="9b472-288">Colocación de semáforo</span><span class="sxs-lookup"><span data-stu-id="9b472-288">Put Semaphore</span></span>  |<span data-ttu-id="9b472-289">0,2</span><span class="sxs-lookup"><span data-stu-id="9b472-289">0.2</span></span>  |
    |<span data-ttu-id="9b472-290">Cambio de contexto</span><span class="sxs-lookup"><span data-stu-id="9b472-290">Context Switch</span></span>  |<span data-ttu-id="9b472-291">0,4</span><span class="sxs-lookup"><span data-stu-id="9b472-291">0.4</span></span>  |
    |<span data-ttu-id="9b472-292">Respuesta de interrupción</span><span class="sxs-lookup"><span data-stu-id="9b472-292">Interrupt Response</span></span>  |<span data-ttu-id="9b472-293">0,0 – 0,6</span><span class="sxs-lookup"><span data-stu-id="9b472-293">0.0 – 0.6</span></span>  |

    <span data-ttu-id="9b472-294">\**Cifras de rendimiento basadas en procesador típico que se ejecuta a 200 MHz*.</span><span class="sxs-lookup"><span data-stu-id="9b472-294">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="9b472-295">Tecnología avanzada</span><span class="sxs-lookup"><span data-stu-id="9b472-295">Advanced technology</span></span>

<span data-ttu-id="9b472-296">Azure RTOS ThreadX es una tecnología avanzada cuya característica más notable es la programación de umbral de prevención.</span><span class="sxs-lookup"><span data-stu-id="9b472-296">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="9b472-297">Esta característica es exclusiva de Azure RTOS ThreadX y ha sido objeto de una extensa investigación académica.</span><span class="sxs-lookup"><span data-stu-id="9b472-297">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="9b472-298">Por ejemplo, vea [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), de Yun Wang, Universidad Concordia, y Manas Saksena, Universidad de Pittsburgh.</span><span class="sxs-lookup"><span data-stu-id="9b472-298">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="9b472-299">Considere las funcionalidades de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="9b472-299">Consider the capabilities of Azure RTOS ThreadX.</span></span>

* <span data-ttu-id="9b472-300">Recursos multitarea completos y generales</span><span class="sxs-lookup"><span data-stu-id="9b472-300">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="9b472-301">Subprocesos, temporizadores de aplicación, colas de mensajes, semáforos de recuento, exclusiones mutuas, marcas de eventos, bloques de memoria de bloques y de bytes</span><span class="sxs-lookup"><span data-stu-id="9b472-301">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="9b472-302">Programación preventiva basada en prioridad</span><span class="sxs-lookup"><span data-stu-id="9b472-302">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="9b472-303">Flexibilidad de prioridad: hasta 1024 niveles de prioridad</span><span class="sxs-lookup"><span data-stu-id="9b472-303">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="9b472-304">Programación cooperativa</span><span class="sxs-lookup"><span data-stu-id="9b472-304">Cooperative Scheduling</span></span>
* <span data-ttu-id="9b472-305">Preemption-Threshold™: exclusivo de Azure RTOS ThreadX, ayuda a reducir los cambios de contexto y a garantizar la programación (según la investigación académica)</span><span class="sxs-lookup"><span data-stu-id="9b472-305">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="9b472-306">Protección de memoria por medio de Azure RTOS ThreadX MODULES</span><span class="sxs-lookup"><span data-stu-id="9b472-306">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="9b472-307">Totalmente determinista</span><span class="sxs-lookup"><span data-stu-id="9b472-307">Fully Deterministic</span></span>
* <span data-ttu-id="9b472-308">Seguimiento de eventos: capture los últimos *n* eventos del sistema o la aplicación</span><span class="sxs-lookup"><span data-stu-id="9b472-308">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="9b472-309">Event Chaining™: registre una función de devolución de llamada "notify" específica de la aplicación para cada objeto de comunicación o sincronización de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="9b472-309">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="9b472-310">Azure RTOS ThreadX MODULES con protección de memoria opcional</span><span class="sxs-lookup"><span data-stu-id="9b472-310">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="9b472-311">Métricas de rendimiento en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="9b472-311">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="9b472-312">Número de reanudaciones de subprocesos</span><span class="sxs-lookup"><span data-stu-id="9b472-312">Number of thread resumptions</span></span>
  * <span data-ttu-id="9b472-313">Número de suspensiones de subprocesos</span><span class="sxs-lookup"><span data-stu-id="9b472-313">Number of thread suspensions</span></span>
  * <span data-ttu-id="9b472-314">Número de prevenciones de subprocesos solicitadas</span><span class="sxs-lookup"><span data-stu-id="9b472-314">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="9b472-315">Número de prevenciones de interrupción de subprocesos asincrónicos</span><span class="sxs-lookup"><span data-stu-id="9b472-315">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="9b472-316">Número de inversiones de prioridad de subprocesos</span><span class="sxs-lookup"><span data-stu-id="9b472-316">Number of thread priority inversions</span></span>
  * <span data-ttu-id="9b472-317">Número de cesiones de subprocesos</span><span class="sxs-lookup"><span data-stu-id="9b472-317">Number of thread relinquishes</span></span>
* <span data-ttu-id="9b472-318">Kit de perfil de ejecución (EPK)</span><span class="sxs-lookup"><span data-stu-id="9b472-318">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="9b472-319">Pila de interrupciones independiente</span><span class="sxs-lookup"><span data-stu-id="9b472-319">Separate Interrupt Stack</span></span>
* <span data-ttu-id="9b472-320">Análisis de la pila en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="9b472-320">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="9b472-321">Procesamiento de interrupciones del temporizador optimizado</span><span class="sxs-lookup"><span data-stu-id="9b472-321">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="9b472-322">Compatibilidad con varios núcleos (AMP y SMP)</span><span class="sxs-lookup"><span data-stu-id="9b472-322">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="9b472-323">Azure RTOS ThreadX estándar se suele usar en modo de multiproceso asimétrico (AMP), en el que una copia independiente de Azure RTOS ThreadX y la aplicación (o Linux) se ejecutan en cada núcleo y se comunican entre sí por medio de la memoria compartida o un mecanismo de comunicación entre procesadores, como OpenAMP (Azure RTOS ThreadX es compatible con OpenAMP).</span><span class="sxs-lookup"><span data-stu-id="9b472-323">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="9b472-324">Esta es la configuración de varios núcleos más típica con Azure RTOS ThreadX y puede ser la más eficaz si la aplicación es capaz de cargar realmente los procesadores.</span><span class="sxs-lookup"><span data-stu-id="9b472-324">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="9b472-325">En los entornos en los que la carga de los procesadores es muy dinámica, el multiproceso simétrico (SMP) de Azure RTOS ThreadX está disponible para las siguientes familias de procesadores:</span><span class="sxs-lookup"><span data-stu-id="9b472-325">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="9b472-326">ARM Cortex-Ax</span><span class="sxs-lookup"><span data-stu-id="9b472-326">ARM Cortex-Ax</span></span>
* <span data-ttu-id="9b472-327">ARM Cortex-Rx</span><span class="sxs-lookup"><span data-stu-id="9b472-327">ARM Cortex-Rx</span></span>
* <span data-ttu-id="9b472-328">ARM Cortex-A5x 64-bit</span><span class="sxs-lookup"><span data-stu-id="9b472-328">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="9b472-329">MIPS 34K, 1004K e interAptiv</span><span class="sxs-lookup"><span data-stu-id="9b472-329">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="9b472-330">PowerPC</span><span class="sxs-lookup"><span data-stu-id="9b472-330">PowerPC</span></span>
* <span data-ttu-id="9b472-331">Synopsys ARC HS</span><span class="sxs-lookup"><span data-stu-id="9b472-331">Synopsys ARC HS</span></span>
* <span data-ttu-id="9b472-332">x86</span><span class="sxs-lookup"><span data-stu-id="9b472-332">x86</span></span>

<span data-ttu-id="9b472-333">Azure RTOS ThreadX SMP realiza el equilibrio de carga dinámico en *n* procesadores y permite que cualquier subproceso de cualquier núcleo acceda a todos los recursos de ThreadX (colas, semáforos, marcas de eventos, bloques de memoria, etc.).</span><span class="sxs-lookup"><span data-stu-id="9b472-333">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="9b472-334">Azure RTOS ThreadX SMP habilita todas las API de Azure RTOS ThreadX en todos los núcleos e incorpora las siguientes API nuevas aplicables a la actividad de SMP:</span><span class="sxs-lookup"><span data-stu-id="9b472-334">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="9b472-335">Protección de memoria por medio de Azure RTOS ThreadX MODULES</span><span class="sxs-lookup"><span data-stu-id="9b472-335">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="9b472-336">Un producto complementario denominado Azure RTOS ThreadX MODULES permite que uno o más subprocesos de la aplicación se agrupen en un "módulo" que se puede cargar y ejecutar dinámicamente (o ejecutarse en contexto) en el destino.</span><span class="sxs-lookup"><span data-stu-id="9b472-336">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="9b472-337">Los módulos habilitan la actualización de campos, la corrección de errores y la creación de particiones de programa para permitir que las aplicaciones grandes ocupen solo la memoria que necesitan los subprocesos activos.</span><span class="sxs-lookup"><span data-stu-id="9b472-337">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="9b472-338">Los módulos también tienen un espacio de direcciones completamente independiente de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="9b472-338">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="9b472-339">De esta manera, Azure RTOS ThreadX puede colocar la protección de memoria (mediante MPU o MMU) en torno al módulo, de forma que el acceso accidental fuera del módulo no pueda dañar ningún otro componente de software.</span><span class="sxs-lookup"><span data-stu-id="9b472-339">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>

## <a name="misra-compliant"></a><span data-ttu-id="9b472-340">Conforme con MISRA</span><span class="sxs-lookup"><span data-stu-id="9b472-340">MISRA compliant</span></span>

<span data-ttu-id="9b472-341">El código fuente de Azure RTOS ThreadX y Azure RTOS ThreadX SMP es conforme con MISRA-C:2004 y MISRA-C:2012.</span><span class="sxs-lookup"><span data-stu-id="9b472-341">Azure RTOS ThreadX and Azure RTOS ThreadX SMP souce code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="9b472-342">MISRA-C es un conjunto de instrucciones de programación para sistemas críticos que usan el lenguaje de programación C.</span><span class="sxs-lookup"><span data-stu-id="9b472-342">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="9b472-343">Las instrucciones de MISRA-C originales se destinaban principalmente a aplicaciones de automoción; sin embargo, en la actualidad, MISRA-C se considera una herramienta aplicable a cualquier aplicación crítica para la seguridad.</span><span class="sxs-lookup"><span data-stu-id="9b472-343">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="9b472-344">Azure RTOS ThreadX es conforme con todas las normas requeridas y obligatorias de MISRA-C:2004 y MISRA-C:2012.</span><span class="sxs-lookup"><span data-stu-id="9b472-344">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certificación Misra":::

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="9b472-346">Compatible con las arquitecturas más populares</span><span class="sxs-lookup"><span data-stu-id="9b472-346">Supports most popular architectures</span></span>

<span data-ttu-id="9b472-347">Azure RTOS ThreadX se ejecuta en los microprocesadores de 32 o 64 bits más populares, de serie, totalmente probado y totalmente compatible, lo que incluye lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9b472-347">Azure RTOS ThreadX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

* <span data-ttu-id="9b472-348">Dispositivos analógicos: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="9b472-348">Analog Devices: SHARC, Blackfin, CM4xx</span></span>
* <span data-ttu-id="9b472-349">Andes Core: RISC-V</span><span class="sxs-lookup"><span data-stu-id="9b472-349">Andes Core: RISC-V</span></span>
* <span data-ttu-id="9b472-350">Ambiqmicro: Apollo MCUs</span><span class="sxs-lookup"><span data-stu-id="9b472-350">Ambiqmicro: Apollo MCUs</span></span>
* <span data-ttu-id="9b472-351">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-BI/A7x 64 bits/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="9b472-351">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>
* <span data-ttu-id="9b472-352">Cadence: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="9b472-352">Cadence: Xtensa, Diamond</span></span>
* <span data-ttu-id="9b472-353">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="9b472-353">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>
* <span data-ttu-id="9b472-354">Cypress: RISC-V</span><span class="sxs-lookup"><span data-stu-id="9b472-354">Cypress: RISC-V</span></span>
* <span data-ttu-id="9b472-355">EnSilica: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="9b472-355">EnSilica: eSi-RISC</span></span>
* <span data-ttu-id="9b472-356">Infineon: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="9b472-356">Infineon: XMC1000, XMC4000, TriCore</span></span>
* <span data-ttu-id="9b472-357">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="9b472-357">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>
* <span data-ttu-id="9b472-358">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="9b472-358">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>
* <span data-ttu-id="9b472-359">Microsemi: RISC-V</span><span class="sxs-lookup"><span data-stu-id="9b472-359">Microsemi: RISC-V</span></span>
* <span data-ttu-id="9b472-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="9b472-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>
* <span data-ttu-id="9b472-361">Renesas: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="9b472-361">Renesas: SH, HS, V850, RX, RZ, Synergy</span></span>
* <span data-ttu-id="9b472-362">Silicon Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="9b472-362">Silicon Labs: EFM32</span></span>
* <span data-ttu-id="9b472-363">Synopsys: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="9b472-363">Synopsys: ARC 600, 700, ARC EM, ARC HS</span></span>
* <span data-ttu-id="9b472-364">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="9b472-364">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>
* <span data-ttu-id="9b472-365">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="9b472-365">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>
* <span data-ttu-id="9b472-366">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="9b472-366">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>
* <span data-ttu-id="9b472-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="9b472-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

## <a name="supports-most-popular-tools"></a><span data-ttu-id="9b472-368">Compatible con las herramientas más populares</span><span class="sxs-lookup"><span data-stu-id="9b472-368">Supports most popular tools</span></span>

<span data-ttu-id="9b472-369">Azure RTOS ThreadX es compatible con las herramientas de desarrollo insertadas más populares, incluido Embedded Workbench™ de IAR, que también tiene disponible el reconocimiento del kernel de Azure RTOS ThreadX más completo.</span><span class="sxs-lookup"><span data-stu-id="9b472-369">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="9b472-370">La integración de herramientas adicionales incluye GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore y todos los dispositivos análogos.</span><span class="sxs-lookup"><span data-stu-id="9b472-370">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>

## <a name="adaptation-layer-for-threadx"></a><span data-ttu-id="9b472-371">Capa de adaptación de ThreadX</span><span class="sxs-lookup"><span data-stu-id="9b472-371">Adaptation layer for ThreadX</span></span>

<span data-ttu-id="9b472-372">Azure RTOS ThreadX es un sistema operativo en tiempo real (RTOS) avanzado, diseñado específicamente para aplicaciones profundamente insertadas.</span><span class="sxs-lookup"><span data-stu-id="9b472-372">Azure RTOS ThreadX is an advanced real-time operating system (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="9b472-373">Para facilitar la migración de aplicaciones a Auzre RTOS, ThreadX proporciona [capas de adaptación](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) para varias API de RTOS heredadas (FreeRTOS, POSIX, OSEK, etc.)</span><span class="sxs-lookup"><span data-stu-id="9b472-373">To help ease application migration to Auzre RTOS, ThreadX provides [adaption layers](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) for various legacy RTOS APIs (FreeRTOS, POSIX, OSEK, etc.)</span></span>
