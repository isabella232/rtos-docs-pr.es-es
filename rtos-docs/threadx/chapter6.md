---
title: 'Capítulo 6: Sistema de demostración de Azure RTOS ThreadX'
description: Este capítulo contiene una descripción del sistema de demostración que se entrega con todos los paquetes de soporte del procesador de Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be85ba77e5c27366f61899c0939be7cad1845bbe
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814354"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a><span data-ttu-id="be909-103">Capítulo 6: Sistema de demostración de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="be909-103">Chapter 6 - Demonstration System for Azure RTOS ThreadX</span></span>

<span data-ttu-id="be909-104">Este capítulo contiene una descripción del sistema de demostración que se entrega con todos los paquetes de soporte del procesador de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="be909-104">This chapter contains a description of the demonstration system that is delivered with all Azure RTOS ThreadX processor support packages.</span></span>

## <a name="overview"></a><span data-ttu-id="be909-105">Información general</span><span class="sxs-lookup"><span data-stu-id="be909-105">Overview</span></span>

<span data-ttu-id="be909-106">Cada distribución de productos de ThreadX contiene un sistema de demostración que se ejecuta en todos los microprocesadores admitidos.</span><span class="sxs-lookup"><span data-stu-id="be909-106">Each ThreadX product distribution contains a demonstration system that runs on all supported microprocessors.</span></span>

<span data-ttu-id="be909-107">Este sistema de ejemplo se define en el archivo de distribución ***demo_threadx.c*** y está diseñado para ilustrar cómo se usa ThreadX en un entorno multiproceso insertado.</span><span class="sxs-lookup"><span data-stu-id="be909-107">This example system is defined in the distribution file ***demo_threadx.c*** and is designed to illustrate how ThreadX is used in an embedded multithread environment.</span></span> <span data-ttu-id="be909-108">La demostración consiste en la inicialización, ocho subprocesos, un grupo de bytes, un grupo de bloques, una cola, un semáforo, una exclusión mutua y un grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="be909-108">The demonstration consists of initialization, eight threads, one byte pool, one block pool, one queue, one semaphore, one mutex, and one event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="be909-109">*Excepto en el caso del tamaño de pila del subproceso, la aplicación de demostración es idéntica en todos los procesadores compatibles con ThreadX.*</span><span class="sxs-lookup"><span data-stu-id="be909-109">*Except for the thread's stack size, the demonstration application is identical on all ThreadX supported processors.*</span></span>

<span data-ttu-id="be909-110">Lista completa de ***demo_threadx. c***, incluidos los números de línea a los que se hace referencia en el resto de este capítulo.</span><span class="sxs-lookup"><span data-stu-id="be909-110">The complete listing of ***demo_threadx.c***, including the line numbers referenced throughout the remainder of this chapter.</span></span>

## <a name="application-define"></a><span data-ttu-id="be909-111">Definición de la aplicación</span><span class="sxs-lookup"><span data-stu-id="be909-111">Application Define</span></span>

<span data-ttu-id="be909-112">La función ***tx_application_define*** se ejecuta después de que se complete la inicialización de ThreadX básica.</span><span class="sxs-lookup"><span data-stu-id="be909-112">The ***tx_application_define*** function executes after the basic ThreadX initialization is complete.</span></span> <span data-ttu-id="be909-113">Es responsable de configurar todos los recursos del sistema iniciales, incluidos los subprocesos, las colas, los semáforos, las exclusiones mutuas, las marcas de eventos y los grupos de memoria.</span><span class="sxs-lookup"><span data-stu-id="be909-113">It is responsible for setting up all of the initial system resources, including threads, queues, semaphores, mutexes, event flags, and memory pools.</span></span>

<span data-ttu-id="be909-114">El elemento ***tx_application_define** _ del sistema de demostración (_números de línea 60-164*) crea los objetos de demostración en el orden siguiente:</span><span class="sxs-lookup"><span data-stu-id="be909-114">The demonstration system's ***tx_application_define** _ (_line numbers 60-164*) creates the demonstration objects in the following order:</span></span>

- <span data-ttu-id="be909-115">byte_pool_0</span><span class="sxs-lookup"><span data-stu-id="be909-115">byte_pool_0</span></span>
- <span data-ttu-id="be909-116">thread_0</span><span class="sxs-lookup"><span data-stu-id="be909-116">thread_0</span></span>
- <span data-ttu-id="be909-117">thread_1</span><span class="sxs-lookup"><span data-stu-id="be909-117">thread_1</span></span>
- <span data-ttu-id="be909-118">thread_2</span><span class="sxs-lookup"><span data-stu-id="be909-118">thread_2</span></span>
- <span data-ttu-id="be909-119">thread_3</span><span class="sxs-lookup"><span data-stu-id="be909-119">thread_3</span></span>
- <span data-ttu-id="be909-120">thread_4</span><span class="sxs-lookup"><span data-stu-id="be909-120">thread_4</span></span>
- <span data-ttu-id="be909-121">thread_5</span><span class="sxs-lookup"><span data-stu-id="be909-121">thread_5</span></span>
- <span data-ttu-id="be909-122">thread_6</span><span class="sxs-lookup"><span data-stu-id="be909-122">thread_6</span></span>
- <span data-ttu-id="be909-123">thread_7</span><span class="sxs-lookup"><span data-stu-id="be909-123">thread_7</span></span>
- <span data-ttu-id="be909-124">queue_0</span><span class="sxs-lookup"><span data-stu-id="be909-124">queue_0</span></span>
- <span data-ttu-id="be909-125">semaphore_0</span><span class="sxs-lookup"><span data-stu-id="be909-125">semaphore_0</span></span>
- <span data-ttu-id="be909-126">event_flags_0</span><span class="sxs-lookup"><span data-stu-id="be909-126">event_flags_0</span></span>
- <span data-ttu-id="be909-127">mutex_0</span><span class="sxs-lookup"><span data-stu-id="be909-127">mutex_0</span></span>
- <span data-ttu-id="be909-128">block_pool_0</span><span class="sxs-lookup"><span data-stu-id="be909-128">block_pool_0</span></span>

<span data-ttu-id="be909-129">El sistema de demostración no crea ningún otro objeto de ThreadX adicional.</span><span class="sxs-lookup"><span data-stu-id="be909-129">The demonstration system does not create any other additional ThreadX objects.</span></span> <span data-ttu-id="be909-130">Sin embargo, una aplicación real puede crear objetos del sistema durante el tiempo de ejecución dentro de los subprocesos en ejecución.</span><span class="sxs-lookup"><span data-stu-id="be909-130">However, an actual application may create system objects during runtime inside of executing threads.</span></span>

### <a name="initial-execution"></a><span data-ttu-id="be909-131">Ejecución inicial</span><span class="sxs-lookup"><span data-stu-id="be909-131">Initial Execution</span></span>

<span data-ttu-id="be909-132">Todos los subprocesos se crean con la opción **TX_AUTO_START**.</span><span class="sxs-lookup"><span data-stu-id="be909-132">All threads are created with the **TX_AUTO_START** option.</span></span> <span data-ttu-id="be909-133">Esto hace que estén preparados inicialmente para su ejecución.</span><span class="sxs-lookup"><span data-stu-id="be909-133">This makes them initially ready for execution.</span></span> <span data-ttu-id="be909-134">Una vez completado ***tx_application_define***, el control se transfiere al programador de subprocesos y desde allí a cada subproceso individual.</span><span class="sxs-lookup"><span data-stu-id="be909-134">After ***tx_application_define*** completes, control is transferred to the thread scheduler and from there to each individual thread.</span></span>

<span data-ttu-id="be909-135">El orden en el que se ejecutan los subprocesos viene determinado por su prioridad y el orden en que se crearon.</span><span class="sxs-lookup"><span data-stu-id="be909-135">The order in which the threads execute is determined by their priority and the order that they were created.</span></span> <span data-ttu-id="be909-136">En el sistema de demostración, ***thread_0*** se ejecuta en primer lugar porque tiene la prioridad más alta (*se creó con una prioridad de 1*).</span><span class="sxs-lookup"><span data-stu-id="be909-136">In the demonstration system, ***thread_0*** executes first because it has the highest priority (*it was created with a priority of 1*).</span></span> <span data-ttu-id="be909-137">Una vez que ***thread_0*** se suspende, se ejecuta ***thread_5***, seguido de la ejecución de ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_,  _* _thread_7_\*\*, \***thread_1**_ y, por último, _\*_thread_2_\*\*.</span><span class="sxs-lookup"><span data-stu-id="be909-137">After ***thread_0*** suspends, ***thread_5*** is executed, followed by the execution of ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_\*\*, \***thread_1**_, and finally _\*_thread_2_\*\*.</span></span>

> [!NOTE]
> <span data-ttu-id="be909-138">*Aunque **thread_3** y **thread_4** tienen la misma prioridad (ambos creados con una prioridad de 8), **thread_3** se ejecuta primero. Esto se debe a que **thread_3** se creó y estaba listo antes de **thread_4**. Los subprocesos de igual prioridad se ejecutan de manera FIFO (PEPS).*</span><span class="sxs-lookup"><span data-stu-id="be909-138">*Even though **thread_3** and **thread_4** have the same priority (both created with a priority of 8), **thread_3** executes first. This is because **thread_3** was created and became ready before **thread_4**. Threads of equal priority execute in a FIFO fashion.*</span></span>

## <a name="thread-0"></a><span data-ttu-id="be909-139">Subproceso 0</span><span class="sxs-lookup"><span data-stu-id="be909-139">Thread 0</span></span>

<span data-ttu-id="be909-140">La función ***thread_0_entry*** marca el punto de entrada del subproceso *(líneas 167-190*).</span><span class="sxs-lookup"><span data-stu-id="be909-140">The function ***thread_0_entry*** marks the entry point of the thread *(lines 167-190*).</span></span> <span data-ttu-id="be909-141">***Thread_0*** es el primer subproceso del sistema de demostración que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="be909-141">***Thread_0*** is the first thread in the demonstration system to execute.</span></span> <span data-ttu-id="be909-142">Su procesamiento es sencillo: incrementa su contador, se suspende durante 10 tics del temporizador, establece una marca de evento para reactivar ***thread_5*** y, a continuación, repite la secuencia.</span><span class="sxs-lookup"><span data-stu-id="be909-142">Its processing is simple: it increments its counter, sleeps for 10 timer ticks, sets an event flag to wake up ***thread_5***, then repeats the sequence.</span></span>

<span data-ttu-id="be909-143">***Thread_0*** es el subproceso de prioridad más alta del sistema.</span><span class="sxs-lookup"><span data-stu-id="be909-143">***Thread_0*** is the highest priority thread in the system.</span></span> <span data-ttu-id="be909-144">Cuando expire la suspensión solicitada, adelantará a cualquier otro subproceso en ejecución de la demostración.</span><span class="sxs-lookup"><span data-stu-id="be909-144">When its requested sleep expires, it will preempt any other executing thread in the demonstration.</span></span>

## <a name="thread-1"></a><span data-ttu-id="be909-145">Subproceso 1</span><span class="sxs-lookup"><span data-stu-id="be909-145">Thread 1</span></span>

<span data-ttu-id="be909-146">La función \***thread_1_entry** _ marca el punto de entrada del subproceso _(líneas 193-216 *). ***Thread_1*** es el penúltimo subproceso que se va a ejecutar en el sistema de demostración. Su procesamiento consiste en incrementar el contador, enviar un mensaje a ***thread_2*** (* mediante \*\*\*\*queue_0\*\*\*) y repetir la secuencia. Tenga en cuenta que \***thread_1**_ se suspende cada vez que _*_queue_0_*_ se llena (_línea 207\*).</span><span class="sxs-lookup"><span data-stu-id="be909-146">The function ***thread_1_entry** _ marks the entry point of the thread _(lines 193-216 *). ***Thread_1*** is the second-to-last thread in the demonstration system to execute. Its processing consists of incrementing its counter, sending a message to ***thread_2*** (* through* ***queue_0***), and repeating the sequence. Notice that \***thread_1**_ suspends whenever _*_queue_0_*_ becomes full (_line 207\*).</span></span>

## <a name="thread-2"></a><span data-ttu-id="be909-147">Subproceso 2</span><span class="sxs-lookup"><span data-stu-id="be909-147">Thread 2</span></span>

<span data-ttu-id="be909-148">La función ***thread_2_entry*** marca el punto de entrada del subproceso *(líneas 219-243*).</span><span class="sxs-lookup"><span data-stu-id="be909-148">The function ***thread_2_entry*** marks the entry point of the thread *(lines 219-243*).</span></span> <span data-ttu-id="be909-149">***Thread_2*** es el último subproceso del sistema de demostración que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="be909-149">***Thread_2*** is the last thread in the demonstration system to execute.</span></span> <span data-ttu-id="be909-150">Su procesamiento consiste en incrementar su contador, obtener un mensaje de ***thread_1*** (a través de ***queue_0***) y repetir la secuencia.</span><span class="sxs-lookup"><span data-stu-id="be909-150">Its processing consists of incrementing its counter, getting a message from ***thread_1*** (through ***queue_0***), and repeating the sequence.</span></span> <span data-ttu-id="be909-151">Observe que ***thread_2** _ se suspende cada vez que _*_queue_0_*_ se queda vacío (_línea 233*).</span><span class="sxs-lookup"><span data-stu-id="be909-151">Notice that ***thread_2** _ suspends whenever _*_queue_0_*_ becomes empty (_line 233*).</span></span>

<span data-ttu-id="be909-152">Aunque ***thread_1** _ and _ *_thread_2_** comparten la prioridad más baja en el sistema de demostración (\* prioridad 16\*), los *subprocesos 3 y 4*</span><span class="sxs-lookup"><span data-stu-id="be909-152">Although ***thread_1** _ and _ *_thread_2_** share the lowest priority in the demonstration system (\* priority 16\*), they *Threads 3 and 4*</span></span>

<span data-ttu-id="be909-153">también son los únicos subprocesos que están listos para su ejecución la mayor parte del tiempo.</span><span class="sxs-lookup"><span data-stu-id="be909-153">are also the only threads that are ready for execution most of the time.</span></span> <span data-ttu-id="be909-154">También son los únicos subprocesos creados con la segmentación de tiempo (*líneas 87 y 93*).</span><span class="sxs-lookup"><span data-stu-id="be909-154">They are also the only threads created with time-slicing (*lines 87 and 93*).</span></span> <span data-ttu-id="be909-155">Cada subproceso puede ejecutarse durante un máximo de 4 tics del temporizador antes de que se ejecute el otro subproceso.</span><span class="sxs-lookup"><span data-stu-id="be909-155">Each thread is allowed to execute for a maximum of 4 timer ticks before the other thread is executed.</span></span>

## <a name="threads-3-and-4"></a><span data-ttu-id="be909-156">Subprocesos 3 y 4</span><span class="sxs-lookup"><span data-stu-id="be909-156">Threads 3 and 4</span></span>

<span data-ttu-id="be909-157">La función ***thread_3_and_4_entry*** marca el punto de entrada de ***thread_3** _ y _ *_thread_4_** (líneas 246-280).</span><span class="sxs-lookup"><span data-stu-id="be909-157">The function ***thread_3_and_4_entry*** marks the entry point of both ***thread_3** _ and _ *_thread_4_** (lines 246-280).</span></span> <span data-ttu-id="be909-158">Ambos subprocesos tienen una prioridad de 8, que hace que se ejecuten en el orden tercero y cuarto de los subprocesos del sistema de demostración.</span><span class="sxs-lookup"><span data-stu-id="be909-158">Both threads have a priority of 8, which makes them the third and fourth threads in the demonstration system to execute.</span></span> <span data-ttu-id="be909-159">El procesamiento de cada subproceso es el mismo: incrementar el contador, obtener ***semaphore_0***, ponerse en suspensión durante dos tics del temporizador, liberar ***semaphore_0*** y repetir la secuencia.</span><span class="sxs-lookup"><span data-stu-id="be909-159">The processing for each thread is the same: incrementing its counter, getting ***semaphore_0***, sleeping for 2 timer ticks, releasing ***semaphore_0***, and repeating the sequence.</span></span> <span data-ttu-id="be909-160">Observe que cada subproceso se suspende cada vez que ***semaphore_0*** no está disponible (línea 264).</span><span class="sxs-lookup"><span data-stu-id="be909-160">Notice that each thread suspends whenever ***semaphore_0*** is unavailable (line 264).</span></span>

<span data-ttu-id="be909-161">Además, ambos subprocesos usan la misma función para su procesamiento principal.</span><span class="sxs-lookup"><span data-stu-id="be909-161">Also both threads use the same function for their main processing.</span></span>
<span data-ttu-id="be909-162">Esto no supone ningún problema porque ambos tienen su propia pila única y C es un reentrante natural.</span><span class="sxs-lookup"><span data-stu-id="be909-162">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span> <span data-ttu-id="be909-163">Cada subproceso determina cuál es mediante el examen del parámetro de entrada del subproceso (línea 258), que se configura cuando se crean (líneas 102 y 109).</span><span class="sxs-lookup"><span data-stu-id="be909-163">Each thread determines which one it is by examination of the thread input parameter (line 258), which is setup when they are created (lines 102 and 109).</span></span>

> [!NOTE]
> <span data-ttu-id="be909-164">*También es razonable obtener el punto de subproceso actual durante la ejecución del subproceso y compararlo con la dirección del bloque de control para determinar la identidad del subproceso.*</span><span class="sxs-lookup"><span data-stu-id="be909-164">*It is also reasonable to obtain the current thread point during thread execution and compare it with the control block's address to determine thread identity.*</span></span>

## <a name="thread-5"></a><span data-ttu-id="be909-165">Subproceso 5</span><span class="sxs-lookup"><span data-stu-id="be909-165">Thread 5</span></span>

<span data-ttu-id="be909-166">La función ***thread_5_entry*** marca el punto de entrada del subproceso (líneas 283-305).</span><span class="sxs-lookup"><span data-stu-id="be909-166">The function ***thread_5_entry*** marks the entry point of the thread (lines 283-305).</span></span> <span data-ttu-id="be909-167">***Thread_5*** es el segundo subproceso del sistema de demostración que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="be909-167">***Thread_5*** is the second thread in the demonstration system to execute.</span></span> <span data-ttu-id="be909-168">Su procesamiento consiste en incrementar su contador, obtener una marca de evento de ***thread_0*** (mediante ***event_flags_0***) y repetir la secuencia.</span><span class="sxs-lookup"><span data-stu-id="be909-168">Its processing consists of incrementing its counter, getting an event flag from ***thread_0*** (through ***event_flags_0***), and repeating the sequence.</span></span> <span data-ttu-id="be909-169">Observe que ***thread_5*** se suspende siempre que la marca de evento de ***event_flags_0*** no esté disponible (línea 298).</span><span class="sxs-lookup"><span data-stu-id="be909-169">Notice that ***thread_5*** suspends whenever the event flag in ***event_flags_0*** is not available (line 298).</span></span>

## <a name="threads-6-and-7"></a><span data-ttu-id="be909-170">Subprocesos 6 y 7</span><span class="sxs-lookup"><span data-stu-id="be909-170">Threads 6 and 7</span></span>

<span data-ttu-id="be909-171">La función ***thread_6_and_7_entry*** marca el punto de entrada de ***thread_6** _ y _ *_thread_7_** (líneas 307-358).</span><span class="sxs-lookup"><span data-stu-id="be909-171">The function ***thread_6_and_7_entry*** marks the entry point of both ***thread_6** _ and _ *_thread_7_** (lines 307-358).</span></span> <span data-ttu-id="be909-172">Ambos subprocesos tienen una prioridad de 8, que hace que se ejecuten en el orden quinto y sexto de los subprocesos del sistema de demostración.</span><span class="sxs-lookup"><span data-stu-id="be909-172">Both threads have a priority of 8, which makes them the fifth and sixth threads in the demonstration system to execute.</span></span> <span data-ttu-id="be909-173">El procesamiento de cada subproceso es el mismo: incrementar el contador, obtener ***mutex_0*** dos veces, ponerse en suspensión durante dos tics del temporizador, liberar ***mutex_0*** dos veces y repetir la secuencia.</span><span class="sxs-lookup"><span data-stu-id="be909-173">The processing for each thread is the same: incrementing its counter, getting ***mutex_0*** twice, sleeping for 2 timer ticks, releasing ***mutex_0*** twice, and repeating the sequence.</span></span> <span data-ttu-id="be909-174">Observe que cada subproceso se suspende cada vez que ***mutex_0*** no está disponible (línea 325).</span><span class="sxs-lookup"><span data-stu-id="be909-174">Notice that each thread suspends whenever ***mutex_0*** is unavailable (line 325).</span></span>

<span data-ttu-id="be909-175">Además, ambos subprocesos usan la misma función para su procesamiento principal.</span><span class="sxs-lookup"><span data-stu-id="be909-175">Also both threads use the same function for their main processing.</span></span> <span data-ttu-id="be909-176">Esto no supone ningún problema porque ambos tienen su propia pila única y C es un reentrante natural.</span><span class="sxs-lookup"><span data-stu-id="be909-176">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span>
<span data-ttu-id="be909-177">Cada subproceso determina cuál es mediante el examen del parámetro de entrada del subproceso (línea 319), que se configura cuando se crean (líneas 126 y 133).</span><span class="sxs-lookup"><span data-stu-id="be909-177">Each thread determines which one it is by examination of the thread input parameter (line 319), which is setup when they are created (lines 126 and 133).</span></span>

## <a name="observing-the-demonstration"></a><span data-ttu-id="be909-178">Observación de la demostración</span><span class="sxs-lookup"><span data-stu-id="be909-178">Observing the Demonstration</span></span>

<span data-ttu-id="be909-179">Cada uno de los subprocesos de demostración incrementa su propio contador único.</span><span class="sxs-lookup"><span data-stu-id="be909-179">Each of the demonstration threads increments its own unique counter.</span></span>
<span data-ttu-id="be909-180">Se pueden examinar los siguientes contadores para comprobar el funcionamiento de la demostración:</span><span class="sxs-lookup"><span data-stu-id="be909-180">The following counters may be examined to check on the demo's operation:</span></span>

- <span data-ttu-id="be909-181">thread_0_counter</span><span class="sxs-lookup"><span data-stu-id="be909-181">thread_0_counter</span></span>
- <span data-ttu-id="be909-182">thread_1_counter</span><span class="sxs-lookup"><span data-stu-id="be909-182">thread_1_counter</span></span>
- <span data-ttu-id="be909-183">thread_2_counter</span><span class="sxs-lookup"><span data-stu-id="be909-183">thread_2_counter</span></span>
- <span data-ttu-id="be909-184">thread_3_counter</span><span class="sxs-lookup"><span data-stu-id="be909-184">thread_3_counter</span></span>
- <span data-ttu-id="be909-185">thread_4_counter</span><span class="sxs-lookup"><span data-stu-id="be909-185">thread_4_counter</span></span>
- <span data-ttu-id="be909-186">thread_5_counter</span><span class="sxs-lookup"><span data-stu-id="be909-186">thread_5_counter</span></span>
- <span data-ttu-id="be909-187">thread_6_counter</span><span class="sxs-lookup"><span data-stu-id="be909-187">thread_6_counter</span></span>
- <span data-ttu-id="be909-188">thread_7_counter</span><span class="sxs-lookup"><span data-stu-id="be909-188">thread_7_counter</span></span>

<span data-ttu-id="be909-189">Cada uno de estos contadores debe seguir aumentando a medida que se ejecuta la demostración, donde ***thread_1_counter** _ y _ *_thread_2_counter_** aumentan a la velocidad más rápida.</span><span class="sxs-lookup"><span data-stu-id="be909-189">Each of these counters should continue to increase as the demonstration executes, with ***thread_1_counter** _ and _ *_thread_2_counter_** increasing at the fastest rate.</span></span>

## <a name="distribution-file-demo_threadxc"></a><span data-ttu-id="be909-190">Archivo de distribución: demo_threadx.c</span><span class="sxs-lookup"><span data-stu-id="be909-190">Distribution file: demo_threadx.c</span></span>

<span data-ttu-id="be909-191">En esta sección se muestra la lista completa de ***demo_threadx. c***, incluidos los números de línea a los que se hace referencia en este capítulo.</span><span class="sxs-lookup"><span data-stu-id="be909-191">This section displays the complete listing of ***demo_threadx.c***, including the line numbers referenced throughout this chapter.</span></span>

```c
/* This is a small demo of the high-performance ThreadX kernel. It includes examples of eight
threads of different priorities, using a message queue, semaphore, mutex, event flags group,
byte pool, and block pool. */

#include "tx_api.h"

#define DEMO_STACK_SIZE 1024
#define DEMO_BYTE_POOL_SIZE 9120
#define DEMO_BLOCK_POOL_SIZE 100
#define DEMO_QUEUE_SIZE 100

/* Define the ThreadX object control blocks... */

TX_THREAD thread_0;
TX_THREAD thread_1;
TX_THREAD thread_2;
TX_THREAD thread_3;
TX_THREAD thread_4;
TX_THREAD thread_5;
TX_THREAD thread_6;
TX_THREAD thread_7;
TX_QUEUE queue_0;
TX_SEMAPHORE semaphore_0;
TX_MUTEX mutex_0;
TX_EVENT_FLAGS_GROUP event_flags_0;
TX_BYTE_POOL byte_pool_0;
TX_BLOCK_POOL block_pool_0;

/* Define the counters used in the demo application... */

ULONG thread_0_counter;
ULONG thread_1_counter;
ULONG thread_1_messages_sent;
ULONG thread_2_counter;
ULONG thread_2_messages_received;
ULONG thread_3_counter;
ULONG thread_4_counter;
ULONG thread_5_counter;
ULONG thread_6_counter;
ULONG thread_7_counter;

/* Define thread prototypes. */

void thread_0_entry(ULONG thread_input);
void thread_1_entry(ULONG thread_input);
void thread_2_entry(ULONG thread_input);
void thread_3_and_4_entry(ULONG thread_input);
void thread_5_entry(ULONG thread_input);
void thread_6_and_7_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

    CHAR *pointer;

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
        DEMO_BYTE_POOL_SIZE);

    /* Put system definition stuff in here, e.g., thread creates and other assorted
        create information. */

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through a ThreadX
        message queue. It is also interesting to note that these threads have a time
        slice. */
    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 2. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
        tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX counting semaphore.
        An interesting thing here is that both threads share the same instruction area. */
    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 4. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag, which will be set
        by thread_0. */
    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 7. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(&event_flags_0, "event flags 0");

    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool to allocate a message buffer from. */
    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
        DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block and release the block memory. */
    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);
}

/* Define the test threads. */
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

        /* Set event flag 0 to wakeup thread 5. */
        status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_1_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sends messages to a queue shared by thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);

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
        status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what we
        expected. */
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
        status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(&semaphore_0);

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
        status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
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
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows
            that an owning thread may retrieve the mutex it
            owns multiple times. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually
            release ownership since it was obtained twice. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```
