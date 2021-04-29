---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS ThreadX SMP'
description: Este capítulo contiene una descripción de todos los servicios de Azure RTOS ThreadX SMP por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4432001b773b4ef4f99b1b34193e90863966aad4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816069"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-smp-services"></a><span data-ttu-id="bdbe0-103">Capítulo 4: Descripción de los servicios de Azure RTOS ThreadX SMP</span><span class="sxs-lookup"><span data-stu-id="bdbe0-103">Chapter 4 - Description of Azure RTOS ThreadX SMP Services</span></span>

<span data-ttu-id="bdbe0-104">Este capítulo contiene una descripción de todos los servicios de Azure RTOS ThreadX SMP por orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-104">This chapter contains a description of all Azure RTOS ThreadX SMP services in alphabetic order.</span></span> <span data-ttu-id="bdbe0-105">Sus nombres están diseñados de modo que todos los servicios similares quedan agrupados.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="bdbe0-106">En la sección “Valores devueltos” de las siguientes descripciones, los valores en **NEGRITA** no se ven afectados por la definición de **TX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-106">In the “Return Values” section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="bdbe0-107">Además, un "**Sí**" bajo el título "**Adelantamiento posible**" indica que la llamada al servicio puede reanudar un subproceso de mayor prioridad, de forma que se adelanta al subproceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-107">In addition, a “**Yes**” listed under the “**Preemption Possible**” heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

- <span data-ttu-id="bdbe0-108">**tx_block_allocate**: *asigna un bloque de memoria de tamaño fijo.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-108">**tx_block_allocate**: *Allocate fixed-size block of memory*</span></span> 
- <span data-ttu-id="bdbe0-109">**tx_block_pool_create**: *crea un grupo de bloques de memoria de tamaño fijo.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-109">**tx_block_pool_create**: *Create pool of fixed-size memory blocks*</span></span> 
- <span data-ttu-id="bdbe0-110">**tx_block_pool_delete**: *elimina un grupo de bloques de memoria.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-110">**tx_block_pool_delete**: *Delete memory block pool*</span></span> 
- <span data-ttu-id="bdbe0-111">**tx_block_pool_info_get**: *recupera información sobre el grupo de bloques.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-111">**tx_block_pool_info_get**: *Retrieve information about block pool*</span></span> 
- <span data-ttu-id="bdbe0-112">**tx_block_pool_performance_info_get**: *obtiene información sobre el rendimiento del grupo de bloques.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-112">**tx_block_pool_performance_info_get**: *Get block pool performance information*</span></span> 
- <span data-ttu-id="bdbe0-113">**tx_block_pool_performance_system_info_get**: *obtiene información sobre el rendimiento de todos los grupos de bloques del sistema.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-113">**tx_block_pool_performance_system_info_get**: *Get block pool system performance information*</span></span> 
- <span data-ttu-id="bdbe0-114">**tx_block_pool_prioritize**: *da prioridad a un grupo de bloques en la lista de suspensiones.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-114">**tx_block_pool_prioritize**: *Prioritize block pool suspension list*</span></span> 
- <span data-ttu-id="bdbe0-115">**tx_block_release**: *libera un bloque de memoria de tamaño fijo.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-115">**tx_block_release**: *Release fixed-size block of memory*</span></span>
- <span data-ttu-id="bdbe0-116">**tx_byte_allocate**: *asigna bytes de memoria.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-116">**tx_byte_allocate**: *Allocate bytes of memory*</span></span> 
- <span data-ttu-id="bdbe0-117">**tx_byte_pool_create**: *crea un grupo de bytes de memoria.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-117">**tx_byte_pool_create**: *Create memory pool of bytes*</span></span> 
- <span data-ttu-id="bdbe0-118">**tx_byte_pool_delete**: *elimina un grupo de bytes de memoria.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-118">**tx_byte_pool_delete**: *Delete memory byte pool*</span></span> 
- <span data-ttu-id="bdbe0-119">**tx_byte_pool_info_get**: *recupera información sobre el grupo de bytes.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-119">**tx_byte_pool_info_get**: *Retrieve information about byte pool*</span></span> 
- <span data-ttu-id="bdbe0-120">**tx_byte_pool_performance_info_get**: *obtiene información sobre el rendimiento del grupo de bytes.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-120">**tx_byte_pool_performance_info_get**: *Get byte pool performance information*</span></span> 
- <span data-ttu-id="bdbe0-121">**tx_byte_pool_performance_system_info_get**: *obtiene información sobre el rendimiento de todos los grupos de bytes del sistema.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-121">**tx_byte_pool_performance_system_info_get**: *Get byte pool system performance information*</span></span> 
- <span data-ttu-id="bdbe0-122">**tx_byte_pool_prioritize**: *da prioridad a un grupo de bytes en la lista de suspensiones.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-122">**tx_byte_pool_prioritize**: *Prioritize byte pool suspension list*</span></span> 
- <span data-ttu-id="bdbe0-123">**tx_byte_release**: *libera los bytes al grupo de memoria.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-123">**tx_byte_release**: *Release bytes back to memory pool*</span></span> 
- <span data-ttu-id="bdbe0-124">**tx_event_flags_create**: *crea un grupo de marcas de evento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-124">**tx_event_flags_create**: *Create event flags group*</span></span> 
- <span data-ttu-id="bdbe0-125">**tx_event_flags_delete**: *elimina un grupo de marcas de evento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-125">**tx_event_flags_delete**: *Delete event flags group*</span></span> 
- <span data-ttu-id="bdbe0-126">**tx_event_flags_get**: *obtiene marcas de evento del grupo de marcas de evento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-126">**tx_event_flags_get**: *Get event flags from event flags group*</span></span> 
- <span data-ttu-id="bdbe0-127">**tx_event_flags_info_get**: *recupera información sobre el grupo de marcas de evento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-127">**tx_event_flags_info_get**: *Retrieve information about event flags group*</span></span> 
- <span data-ttu-id="bdbe0-128">**tx_event_flags_performance_info_get**: *obtiene información sobre el rendimiento del grupo de marcas de evento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-128">**tx_event_flags_performance_info_get**: *Get event flags group performance information*</span></span> 
- <span data-ttu-id="bdbe0-129">**tx_event_flags_performance_system_info_get**: *recupera información sobre el rendimiento de todos los grupos de marcas de evento del sistema.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-129">**tx_event_flags_performance_system_info_get**: *Retrieve performance system information*</span></span> 
- <span data-ttu-id="bdbe0-130">**tx_event_flags_set**: *establece marcas de evento en el grupo de marcas de evento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-130">**tx_event_flags_set**: *Set event flags in an event flags group*</span></span> 
- <span data-ttu-id="bdbe0-131">**tx_event_flags_set_notify**: *notifica a la aplicación cuando se establecen marcas de evento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-131">**tx_event_flags_set_notify**: *Notify application when event flags are set*</span></span>
- <span data-ttu-id="bdbe0-132">**tx_interrupt_control**: *habilita y deshabilita interrupciones.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-132">**tx_interrupt_control**: *Enable and disable interrupts*</span></span> 
- <span data-ttu-id="bdbe0-133">**tx_mutex_create**: *crea una exclusión mutua.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-133">**tx_mutex_create**: *Create mutual exclusion mutex*</span></span> 
- <span data-ttu-id="bdbe0-134">**tx_mutex_delete**: *elimina una exclusión mutua.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-134">**tx_mutex_delete**: *Delete mutual exclusion mutex*</span></span> 
- <span data-ttu-id="bdbe0-135">**tx_mutex_get**: *obtiene la propiedad de la exclusión mutua.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-135">**tx_mutex_get**: *Obtain ownership of mutex*</span></span> 
- <span data-ttu-id="bdbe0-136">**tx_mutex_info_get**: *recupera información sobre la exclusión mutua.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-136">**tx_mutex_info_get**: *Retrieve information about mutex*</span></span> 
- <span data-ttu-id="bdbe0-137">**tx_mutex_performance_info_get**: *obtiene información sobre el rendimiento de la exclusión mutua.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-137">**tx_mutex_performance_info_get**: *Get mutex performance information*</span></span> 
- <span data-ttu-id="bdbe0-138">**tx_mutex_performance_system_info_get**: *obtiene información sobre el rendimiento de todas las exclusiones mutuas del sistema.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-138">**tx_mutex_performance_system_info_get**: *Get mutex system performance information*</span></span> 
- <span data-ttu-id="bdbe0-139">**tx_mutex_prioritize**: *da prioridad a una exclusión mutua en la lista de suspensiones.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-139">**tx_mutex_prioritize**: *Prioritize mutex suspension list*</span></span> 
- <span data-ttu-id="bdbe0-140">**tx_mutex_put**: *libera la propiedad de la exclusión mutua.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-140">**tx_mutex_put**: *Release ownership of mutex*</span></span> 
- <span data-ttu-id="bdbe0-141">**tx_queue_create**: *crea una cola de mensajes.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-141">**tx_queue_create**: *Create message queue*</span></span> 
- <span data-ttu-id="bdbe0-142">**tx_queue_delete**: *elimina una cola de mensajes.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-142">**tx_queue_delete**: *Delete message queue*</span></span> 
- <span data-ttu-id="bdbe0-143">**tx_queue_flush**: *vacía los mensajes de la cola de mensajes.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-143">**tx_queue_flush**: *Empty messages in message queue*</span></span> 
- <span data-ttu-id="bdbe0-144">**tx_queue_front_send**: *envía un mensaje al primer puesto de la cola.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-144">**tx_queue_front_send**: *Send message to the front of queue*</span></span> 
- <span data-ttu-id="bdbe0-145">**tx_queue_info_get**: *recupera información sobre la cola.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-145">**tx_queue_info_get**: *Retrieve information about queue*</span></span> 
- <span data-ttu-id="bdbe0-146">**tx_queue_performance_info_get**: *obtiene información sobre el rendimiento de la cola.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-146">**tx_queue_performance_info_get**: *Get queue performance information*</span></span> 
- <span data-ttu-id="bdbe0-147">**tx_queue_performance_system_info_get**: *obtiene información sobre el rendimiento de todas las colas del sistema.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-147">**tx_queue_performance_system_info_get**: *Get queue system performance information*</span></span>
- <span data-ttu-id="bdbe0-148">**tx_queue_prioritize**: *da prioridad a una cola en la lista de suspensiones.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-148">**tx_queue_prioritize**: *Prioritize queue suspension list*</span></span> 
- <span data-ttu-id="bdbe0-149">**tx_queue_receive**: *obtiene un mensaje de la cola de mensajes.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-149">**tx_queue_receive**: *Get message from message queue*</span></span> 
- <span data-ttu-id="bdbe0-150">**tx_queue_send**: *envía un mensaje a la cola de mensajes.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-150">**tx_queue_send**: *Send message to message queue*</span></span> 
- <span data-ttu-id="bdbe0-151">**tx_queue_send_notify**: *notifica a la aplicación cuando se envía un mensaje a la cola.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-151">**tx_queue_send_notify**: *Notify application when message is sent to queue*</span></span> 
- <span data-ttu-id="bdbe0-152">**tx_semaphore_ceiling_put**: *coloca una instancia en el semáforo de recuento con límite superior.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-152">**tx_semaphore_ceiling_put**: *Place an instance in counting semaphore with ceiling*</span></span> 
- <span data-ttu-id="bdbe0-153">**tx_semaphore_create**: *crea un semáforo de recuento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-153">**tx_semaphore_create**: *Create counting semaphore*</span></span> 
- <span data-ttu-id="bdbe0-154">**tx_semaphore_delete**: *elimina un semáforo de recuento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-154">**tx_semaphore_delete**: *Delete counting semaphore*</span></span> 
- <span data-ttu-id="bdbe0-155">**tx_semaphore_get**: *obtiene una instancia de un semáforo de recuento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-155">**tx_semaphore_get**: *Get instance from counting semaphore*</span></span> 
- <span data-ttu-id="bdbe0-156">**tx_semaphore_info_get**: *recupera información sobre el semáforo.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-156">**tx_semaphore_info_get**: *Retrieve information about semaphore*</span></span> 
- <span data-ttu-id="bdbe0-157">**tx_semaphore_performance_info_get**: *obtiene información sobre el rendimiento del semáforo.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-157">**tx_semaphore_performance_info_get**: *Get semaphore performance information*</span></span> 
- <span data-ttu-id="bdbe0-158">**tx_semaphore_performance_system_info_get**: *obtiene información sobre el rendimiento de todos los semáforos del sistema.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-158">**tx_semaphore_performance_system_info_get**: *Get semaphore system performance information*</span></span> 
- <span data-ttu-id="bdbe0-159">**tx_semaphore_prioritize**: *da prioridad a un semáforo en la lista de suspensiones.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-159">**tx_semaphore_prioritize**: *Prioritize semaphore suspension list*</span></span> 
- <span data-ttu-id="bdbe0-160">**tx_semaphore_put**: *coloca una instancia en el semáforo de recuento.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-160">**tx_semaphore_put**: *Place an instance in counting semaphore*</span></span> 
- <span data-ttu-id="bdbe0-161">**tx_semaphore_put_notify**: *notifica a la aplicación cuando se coloca un semáforo.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-161">**tx_semaphore_put_notify**: *Notify application when semaphore is put*</span></span> 
- <span data-ttu-id="bdbe0-162">**tx_thread_create**: *crea un subproceso de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-162">**tx_thread_create**: *Create application thread*</span></span> 
- <span data-ttu-id="bdbe0-163">**tx_thread_delete**: *elimina un subproceso de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-163">**tx_thread_delete**: *Delete application thread*</span></span>
- <span data-ttu-id="bdbe0-164">**tx_thread_entry_exit_notify**: *notifica a la aplicación la entrada y salida del subproceso.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-164">**tx_thread_entry_exit_notify**: *Notify application upon thread entry and exit*</span></span> 
- <span data-ttu-id="bdbe0-165">**tx_thread_identify**: *recupera el puntero al subproceso que se está ejecutando actualmente.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-165">**tx_thread_identify**: *Retrieves pointer to currently executing thread*</span></span> 
- <span data-ttu-id="bdbe0-166">**tx_thread_info_get**: *recupera información sobre el subproceso.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-166">**tx_thread_info_get**: *Retrieve information about thread*</span></span> 
- <span data-ttu-id="bdbe0-167">**tx_thread_performance_info_get**: *obtiene información sobre el rendimiento del subproceso.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-167">**tx_thread_performance_info_get**: *Get thread performance information*</span></span> 
- <span data-ttu-id="bdbe0-168">**tx_thread_performance_system_info_get**: *obtiene información sobre el rendimiento de todos los subprocesos del sistema.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-168">**tx_thread_performance_system_info_get**: *Get thread system performance information*</span></span> 
- <span data-ttu-id="bdbe0-169">**tx_thread_preemption_change**: *cambia el umbral de adelantamiento del subproceso de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-169">**tx_thread_preemption_change**: *Change preemption-threshold of application thread*</span></span> 
- <span data-ttu-id="bdbe0-170">**tx_thread_priority_change**: *cambia la prioridad del subproceso de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-170">**tx_thread_priority_change**: *Change priority of application thread*</span></span> 
- <span data-ttu-id="bdbe0-171">**tx_thread_relinquish**: *cede el control a otros subprocesos de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-171">**tx_thread_relinquish**: *Relinquish control to other application threads*</span></span> 
- <span data-ttu-id="bdbe0-172">**tx_thread_reset**: *restablece el subproceso.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-172">**tx_thread_reset**: *Reset thread*</span></span> 
- <span data-ttu-id="bdbe0-173">**tx_thread_resume**: *reanuda un subproceso de aplicación suspendido.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-173">**tx_thread_resume**: *Resume suspended application thread*</span></span> 
- <span data-ttu-id="bdbe0-174">**tx_thread_sleep**: *suspende el subproceso actual el tiempo especificado.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-174">**tx_thread_sleep**: *Suspend current thread for specified time*</span></span> 
- <span data-ttu-id="bdbe0-175">**tx_thread_smp_core_exclude**: *excluye la ejecución del subproceso de un conjunto de núcleos.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-175">**tx_thread_smp_core_exclude**: *Exclude thread execution on a set of cores*</span></span> 
- <span data-ttu-id="bdbe0-176">**tx_thread_smp_core_exclude_get**: *obtiene la exclusión de núcleos actual del subproceso.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-176">**tx_thread_smp_core_exclude_get**: *Gets the thread's current core exclusion*</span></span> 
- <span data-ttu-id="bdbe0-177">**tx_thread_smp_core_get**: *recupera el núcleo que se está ejecutando actualmente del autor de la llamada.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-177">**tx_thread_smp_core_get**: *Retrieve currently executing core of caller*</span></span> 
- <span data-ttu-id="bdbe0-178">**tx_thread_stack_error_notify**: *registra la devolución de llamada de notificación de errores en la pila de subprocesos.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-178">**tx_thread_stack_error_notify**: *Register thread stack error notification callback*</span></span> 
- <span data-ttu-id="bdbe0-179">**tx_thread_suspend**: *suspende un subproceso de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-179">**tx_thread_suspend**: *Suspend application thread*</span></span>
- <span data-ttu-id="bdbe0-180">**tx_thread_terminate**: *finaliza el subproceso de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-180">**tx_thread_terminate**: *Terminates application thread*</span></span> 
- <span data-ttu-id="bdbe0-181">**tx_thread_time_slice_change**: *cambia la porción de tiempo del subproceso de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-181">**tx_thread_time_slice_change**: *Changes time-slice of application thread*</span></span> 
- <span data-ttu-id="bdbe0-182">**tx_thread_wait_abort**: *anula la suspensión del subproceso especificado.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-182">**tx_thread_wait_abort**: *Abort suspension of specified thread*</span></span> 
- <span data-ttu-id="bdbe0-183">**tx_time_get**: *recupera la hora actual.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-183">**tx_time_get**: *Retrieves the current time*</span></span> 
- <span data-ttu-id="bdbe0-184">**tx_time_set**: *establece la hora actual.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-184">**tx_time_set**: *Sets the current time*</span></span> 
- <span data-ttu-id="bdbe0-185">**tx_timer_activate**: *activa un temporizador de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-185">**tx_timer_activate**: *Activate application timer*</span></span> 
- <span data-ttu-id="bdbe0-186">**tx_timer_change**: *cambia un temporizador de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-186">**tx_timer_change**: *Change application timer*</span></span> 
- <span data-ttu-id="bdbe0-187">**tx_timer_create**: *crea un temporizador de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-187">**tx_timer_create**: *Create application timer*</span></span> 
- <span data-ttu-id="bdbe0-188">**tx_timer_deactivate**: *desactiva un temporizador de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-188">**tx_timer_deactivate**: *Deactivate application timer*</span></span> 
- <span data-ttu-id="bdbe0-189">**tx_timer_delete**: *elimina un temporizador de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-189">**tx_timer_delete**: *Delete application timer*</span></span> 
- <span data-ttu-id="bdbe0-190">**tx_timer_info_get**: *recupera información sobre un temporizador de aplicación.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-190">**tx_timer_info_get**: *Retrieve information about an application timer*</span></span> 
- <span data-ttu-id="bdbe0-191">**tx_timer_performance_info_get**: *obtiene información sobre el rendimiento del temporizador.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-191">**tx_timer_performance_info_get**: *Get timer performance information*</span></span> 
- <span data-ttu-id="bdbe0-192">**tx_timer_performance_system_info_get**: *obtiene información sobre el rendimiento de todos los temporizadores del sistema.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-192">**tx_timer_performance_system_info_get**: *Get timer system performance information*</span></span> 
- <span data-ttu-id="bdbe0-193">**tx_timer_smp_core_exclude**: *excluye la ejecución del temporizador de un conjunto de núcleos.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-193">**tx_timer_smp_core_exclude**: *Exclude timer execution on a set of cores*</span></span> 
- <span data-ttu-id="bdbe0-194">**tx_timer_smp_core_exclude_get**: *obtiene la exclusión de núcleos actual del temporizador.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-194">**tx_timer_smp_core_exclude_get**: *Gets the timer's current core exclusion*</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="bdbe0-195">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-195">tx_block_allocate</span></span>
<span data-ttu-id="bdbe0-196">Asigna un bloque de memoria de tamaño fijo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-196">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-197">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-197">Prototype</span></span>

```C
UINT tx_block_allocate(TX_BLOCK_POOL *pool_ptr, VOID **block_ptr,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="bdbe0-198">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-198">Description</span></span>

<span data-ttu-id="bdbe0-199">Este servicio asigna un bloque de memoria de tamaño fijo del grupo de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-199">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="bdbe0-200">El tamaño real del bloque de memoria se determina durante la creación del grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-200">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!WARNING]
> <span data-ttu-id="bdbe0-201">Es importante asegurarse de que el código de aplicación no escriba fuera del bloque de memoria asignado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-201">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="bdbe0-202">Si esto ocurre, se producen daños en un bloque de memoria adyacente (normalmente posterior).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-202">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="bdbe0-203">Los resultados son imprevisibles y suelen ser graves.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-203">The results are unpredictable and are often fatal!</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-204">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-204">Parameters</span></span>

- <span data-ttu-id="bdbe0-205">**pool_ptr**: puntero a un grupo de bloques de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-205">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="bdbe0-206">**block_ptr**: puntero a un puntero del bloque de destino.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-206">**block_ptr**: Pointer to a destination block pointer.</span></span> <span data-ttu-id="bdbe0-207">Si la asignación es correcta, la dirección del bloque de memoria asignado se coloca donde señala este parámetro.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-207">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="bdbe0-208">**wait_option**: define el comportamiento del servicio si no hay ningún bloque de memoria disponible.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-208">**wait_option**: Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="bdbe0-209">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-209">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bdbe0-210">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-210">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="bdbe0-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="bdbe0-212">valor de tiempo de espera: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-212">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>  
    
    <span data-ttu-id="bdbe0-213">Cuando se selecciona TX_NO_WAIT, se produce una devolución inmediata desde este servicio, con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-213">Selecting TX_NO_WAIT results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="bdbe0-214">Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-214">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="bdbe0-215">Cuando se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya un bloque de memoria disponible.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-215">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a memory block is available.</span></span>

    <span data-ttu-id="bdbe0-216">Cuando se selecciona un valor numérico (de 1 a 0xFFFFFFFE), se está especificando el número máximo de tics del temporizador que el subproceso permanecerá suspendido mientras espera por un bloque de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-216">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-217">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-217">Return Values</span></span>

- <span data-ttu-id="bdbe0-218">**TX_SUCCESS**: (0x00) bloque de memoria asignado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-218">**TX_SUCCESS**: (0x00) Successful memory block allocation.</span></span>
- <span data-ttu-id="bdbe0-219">**TX_DELETED**: (0x01) el grupo de bloques de memoria se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-219">**TX_DELETED**: (0x01) Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="bdbe0-220">**TX_NO_MEMORY**: (0x10) el servicio no pudo asignar un bloque de memoria en el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-220">**TX_NO_MEMORY**: (0x10) Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="bdbe0-221">**TX_WAIT_ABORTED**: (0x1A) otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-221">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="bdbe0-222">TX_POOL_ERROR: (0x02) puntero del grupo de bloques de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-222">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="bdbe0-223">TX_PTR_ERROR: (0x03) puntero al puntero de destino no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-223">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="bdbe0-224">TX_WAIT_ERROR: (0x04) se especificó una opción de espera distinta de TX_NO_WAIT en una llamada desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-224">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-225">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-225">Allowed From</span></span>

<span data-ttu-id="bdbe0-226">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-226">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-227">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-227">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-228">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-228">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-229">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-229">Example</span></span>

```c
TX_BLOCK_POOL   my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a memory block from my_pool. Assume that the
   pool has already been created with a call to
   tx_block_pool_create. */
status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
                               TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="bdbe0-230">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-230">See Also</span></span>

- <span data-ttu-id="bdbe0-231">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-231">tx_block_pool_create</span></span>
- <span data-ttu-id="bdbe0-232">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-232">tx_block_pool_delete</span></span>
- <span data-ttu-id="bdbe0-233">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-233">tx_block_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-234">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-234">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-235">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-235">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-236">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-236">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-237">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-237">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="bdbe0-238">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-238">tx_block_pool_create</span></span>
<span data-ttu-id="bdbe0-239">Crea un grupo de bloques de memoria de tamaño fijo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-239">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-240">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-240">Prototype</span></span>

```C
UINT tx_block_pool_create(TX_BLOCK_POOL *pool_ptr,
                          CHAR *name_ptr, ULONG block_size,
                          VOID *pool_start, ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="bdbe0-241">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-241">Description</span></span>

<span data-ttu-id="bdbe0-242">Este servicio crea un grupo de bloques de memoria de tamaño fijo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-242">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="bdbe0-243">El área de memoria especificada se divide en tantos bloques de memoria de tamaño fijo como sea posible mediante la siguiente fórmula:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-243">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>    
<span data-ttu-id="bdbe0-244">**total de bloques** = (**total de bytes**)/(**tamaño de bloque** + sizeof(void \*))</span><span class="sxs-lookup"><span data-stu-id="bdbe0-244">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-245">Cada bloque de memoria contiene un puntero de sobrecarga que es invisible para el usuario y se representa mediante "sizeof(void \*)" en la fórmula anterior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-245">Each memory block contains one pointer of overhead that is invisible to the user and is represented by the “sizeof(void \*)” in the preceding formula.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-246">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-246">Parameters</span></span>

- <span data-ttu-id="bdbe0-247">**pool_ptr**: puntero al bloque de control de un grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-247">**pool_ptr**: Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="bdbe0-248">**name_ptr**: puntero al nombre del grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-248">**name_ptr**: Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="bdbe0-249">**block_size**: número de bytes de cada bloque de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-249">**block_size**: Number of bytes in each memory block.</span></span>
- <span data-ttu-id="bdbe0-250">**pool_start**: dirección inicial del grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-250">**pool_start**: Starting address of the memory block pool.</span></span> <span data-ttu-id="bdbe0-251">La dirección inicial debe corresponderse con el tamaño del tipo de datos ULONG.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-251">The starting address must be aligned to the size of the ULONG data type..</span></span>
- <span data-ttu-id="bdbe0-252">**pool_size**: número total de bytes disponibles para el grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-252">**pool_size**: Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-253">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-253">Return Values</span></span>

- <span data-ttu-id="bdbe0-254">**TX_SUCCESS**: (0x00) grupo de bloques de memoria creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-254">**TX_SUCCESS**: (0x00) Successful memory block pool creation.</span></span>
- <span data-ttu-id="bdbe0-255">TX_POOL_ERROR: (0x02) puntero del grupo de bloques de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-255">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span> <span data-ttu-id="bdbe0-256">El puntero es NULL o el grupo ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-256">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="bdbe0-257">TX_PTR_ERROR: (0x03) dirección inicial del grupo no válida.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-257">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="bdbe0-258">TX_SIZE_ERROR: (0x05) el tamaño del grupo no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-258">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="bdbe0-259">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-259">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-260">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-260">Allowed From</span></span>

<span data-ttu-id="bdbe0-261">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-261">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-262">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-262">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-263">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-263">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-264">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-264">Example</span></span>

```C
TX_BLOCK_POOL  my_pool;
UINT           status;

/* Create a memory pool whose total size is 1000 bytes
   starting at address 0x100000. Each block in this
   pool is defined to be 50 bytes long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
               50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18
   memory blocks of 50 bytes each. The reason
   there are not 20 blocks in the pool is
   because of the one overhead pointer associated with each
   block. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-265">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-265">See Also</span></span>

- <span data-ttu-id="bdbe0-266">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-266">tx_block_allocate</span></span>
- <span data-ttu-id="bdbe0-267">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-267">tx_block_pool_delete</span></span>
- <span data-ttu-id="bdbe0-268">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-268">tx_block_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-269">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-269">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-270">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-270">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-271">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-271">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-272">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-272">tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="bdbe0-273">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-273">tx_block_pool_delete</span></span>

<span data-ttu-id="bdbe0-274">Elimina un grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-274">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-275">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-275">Prototype</span></span>

```C
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-276">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-276">Description</span></span>

<span data-ttu-id="bdbe0-277">Este servicio elimina el grupo de bloques de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-277">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="bdbe0-278">Todos los subprocesos suspendidos en espera de un bloque de memoria de este grupo se reanudan y se les asigna un estado de devolución TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-278">All threads suspended waiting for a memory block from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-279">Es responsabilidad de la aplicación administrar el área de memoria asociada al grupo, que está disponible una vez completado este servicio.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-279">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="bdbe0-280">Además, debe impedir el uso de un grupo eliminado o de sus anteriores bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-280">In addition, the application must prevent use of a deleted pool or its former memory blocks.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-281">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-281">Parameters</span></span>

- <span data-ttu-id="bdbe0-282">**pool_ptr**: puntero a un grupo de bloques de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-282">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-283">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-283">Return Values</span></span>

- <span data-ttu-id="bdbe0-284">**TX_SUCCESS**: (0x00) grupo de bloques de memoria eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-284">**TX_SUCCESS**: (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="bdbe0-285">TX_POOL_ERROR: (0x02) puntero del grupo de bloques de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-285">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="bdbe0-286">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-286">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-287">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-287">Allowed From</span></span>

<span data-ttu-id="bdbe0-288">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-288">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-289">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-289">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-290">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-290">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-291">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-291">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
UINT           status;

    /* Delete entire memory block pool. Assume that the pool
      has already been created with a call to
      tx_block_pool_create. */
    status =  tx_block_pool_delete(&my_pool);

    /* If status equals TX_SUCCESS, the memory block pool is
       deleted. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-292">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-292">See Also</span></span>

- <span data-ttu-id="bdbe0-293">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-293">tx_block_allocate</span></span>
- <span data-ttu-id="bdbe0-294">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-294">tx_block_pool_create</span></span>
- <span data-ttu-id="bdbe0-295">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-295">tx_block_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-296">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-296">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-297">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-297">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-298">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-298">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-299">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-299">tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="bdbe0-300">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-300">tx_block_pool_info_get</span></span>

<span data-ttu-id="bdbe0-301">Recupera información acerca de un grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-301">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-302">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-302">Prototype</span></span>

```C
UINT tx_block_pool_info_get(TX_BLOCK_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *total_blocks,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BLOCK_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="bdbe0-303">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-303">Description</span></span>

<span data-ttu-id="bdbe0-304">Este servicio recupera información sobre el grupo de bloques de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-304">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-305">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-305">Parameters</span></span>

- <span data-ttu-id="bdbe0-306">**pool_ptr**: puntero a un grupo de bloques de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-306">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="bdbe0-307">**name**: puntero al destino del puntero al nombre del grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-307">**name**: Pointer to destination for the pointer to the block pool’s name.</span></span>
- <span data-ttu-id="bdbe0-308">**available**: puntero al destino del número de bloques disponibles en el grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-308">**available**: Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="bdbe0-309">**total_blocks**: puntero al destino del número total de bloques del grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-309">**total_blocks**: Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="bdbe0-310">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-310">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="bdbe0-311">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-311">**suspended_count**: Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="bdbe0-312">**next_pool**: puntero al destino del puntero del siguiente grupo de bloques creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-312">**next_pool**: Pointer to destination for the pointer of the next created block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-313">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-313">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-314">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-314">Return Values</span></span>

- <span data-ttu-id="bdbe0-315">**TX_SUCCESS**: (0x00) información del grupo de bloques recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-315">**TX_SUCCESS**: (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="bdbe0-316">TX_POOL_ERROR: (0x02) puntero del grupo de bloques de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-316">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-317">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-317">Allowed From</span></span>

<span data-ttu-id="bdbe0-318">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-318">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-319">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-319">Example</span></span>

```C
TX_BLOCK_POOL    my_pool;
CHAR             *name;
ULONG            available;
ULONG            total_blocks;
TX_THREAD        *first_suspended;
ULONG            suspended_count;
TX_BLOCK_POOL    *next_pool;
UINT             status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
                &available,&total_blocks,
                &first_suspended, &suspended_count,
                &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-320">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-320">See Also</span></span>

- <span data-ttu-id="bdbe0-321">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-321">tx_block_allocate</span></span>
- <span data-ttu-id="bdbe0-322">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-322">tx_block_pool_create</span></span>
- <span data-ttu-id="bdbe0-323">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-323">tx_block_pool_delete</span></span>
- <span data-ttu-id="bdbe0-324">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-324">tx_block_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-325">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-325">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-326">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-326">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-327">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-327">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-328">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-328">tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="bdbe0-329">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-329">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="bdbe0-330">Obtiene información acerca del rendimiento de un grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-330">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-331">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-331">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(TX_BLOCK_POOL *pool_ptr,
       ULONG *allocates, ULONG *releases,
       ULONG *suspensions, ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="bdbe0-332">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-332">Description</span></span>

<span data-ttu-id="bdbe0-333">Este servicio recupera información sobre el rendimiento del grupo de bloques de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-333">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-334">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-334">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-335">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-335">Parameters</span></span>

- <span data-ttu-id="bdbe0-336">**pool_ptr**: puntero a un grupo de bloques de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-336">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="bdbe0-337">**allocates**: puntero al destino del número de solicitudes de asignación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-337">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="bdbe0-338">**releases**: puntero al destino del número de solicitudes de liberación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-338">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="bdbe0-339">**suspensions**: puntero al destino del número de suspensiones de asignación de subprocesos de este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-339">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="bdbe0-340">**timeouts**: puntero al destino del número de tiempos de espera de las suspensiones de asignación de este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-340">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-341">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-341">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-342">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-342">Return Values</span></span>

- <span data-ttu-id="bdbe0-343">**TX_SUCCESS**: (0x00) rendimiento del grupo de bloques obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-343">**TX_SUCCESS**: (0x00) Successful block pool performance get.</span></span>
- <span data-ttu-id="bdbe0-344">**TX_PTR_ERROR**: (0x03) puntero al grupo de bloques no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-344">**TX_PTR_ERROR**: (0x03) Invalid block pool pointer.</span></span>
- <span data-ttu-id="bdbe0-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-346">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-346">Allowed From</span></span>

<span data-ttu-id="bdbe0-347">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-347">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-348">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-348">Example</span></span>

```C
TX_BLOCK_POOL     my_pool;
ULONG             allocates;
ULONG             releases;
ULONG             suspensions;
ULONG             timeouts;

/* Retrieve performance information on the previously created block
   pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
                                            &releases,
                &suspensions,
                &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-349">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-349">See Also</span></span>

- <span data-ttu-id="bdbe0-350">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-350">tx_block_allocate</span></span>
- <span data-ttu-id="bdbe0-351">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-351">tx_block_pool_create</span></span>
- <span data-ttu-id="bdbe0-352">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-352">tx_block_pool_delete</span></span>
- <span data-ttu-id="bdbe0-353">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-353">tx_block_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-354">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-354">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-355">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-355">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-356">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-356">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="bdbe0-357">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-357">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="bdbe0-358">Obtiene información acerca del rendimiento de los grupos de bloques del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-358">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-359">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-359">Prototype</span></span>

```C
UINT tx_block_pool_performance_system_info_get(ULONG *allocates,
       ULONG *releases, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="bdbe0-360">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-360">Description</span></span>

<span data-ttu-id="bdbe0-361">Este servicio recupera información sobre el rendimiento de todos los grupos de bloques de memoria de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-361">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-362">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-362">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-363">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-363">Parameters</span></span>

- <span data-ttu-id="bdbe0-364">**allocates**: puntero al destino del número total de solicitudes de asignación realizadas en todos los grupos de bloques.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-364">**allocates**: Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="bdbe0-365">**releases**: puntero al destino del número total de solicitudes de liberación realizadas en todos los grupos de bloques.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-365">**releases**: Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="bdbe0-366">**suspensions**: puntero al destino del número total de suspensiones de asignación de subprocesos de todos los grupos de bloques.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-366">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="bdbe0-367">**timeouts**: puntero al destino del número total de tiempos de espera de las suspensiones de asignación de todos los grupos de bloques.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-367">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-368">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-368">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-369">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-369">Return Values</span></span>

- <span data-ttu-id="bdbe0-370">**TX_SUCCESS**: (0x00) rendimiento de los grupos de bloques del sistema obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-370">**TX_SUCCESS**: (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="bdbe0-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-372">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-372">Allowed From</span></span>

<span data-ttu-id="bdbe0-373">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-373">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-374">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-374">Example</span></span>

```C
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all the block pools in
   the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
                     &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-375">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-375">See Also</span></span>

- <span data-ttu-id="bdbe0-376">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-376">tx_block_allocate</span></span>
- <span data-ttu-id="bdbe0-377">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-377">tx_block_pool_create</span></span>
- <span data-ttu-id="bdbe0-378">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-378">tx_block_pool_delete</span></span>
- <span data-ttu-id="bdbe0-379">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-379">tx_block_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-380">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-380">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-381">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-381">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-382">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-382">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="bdbe0-383">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-383">tx_block_pool_prioritize</span></span>

<span data-ttu-id="bdbe0-384">Da prioridad a un subproceso de un bloque del grupo en la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-384">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-385">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-385">Prototype</span></span>

```C
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-386">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-386">Description</span></span>

<span data-ttu-id="bdbe0-387">Este servicio coloca el subproceso de prioridad más alta suspendido de un bloque de memoria de este grupo al principio de la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-387">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="bdbe0-388">Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-388">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-389">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-389">Parameters</span></span> 

- <span data-ttu-id="bdbe0-390">**pool_ptr**: puntero al bloque de control de un grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-390">**pool_ptr**: Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-391">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-391">Return Values</span></span>

- <span data-ttu-id="bdbe0-392">**TX_SUCCESS**: (0x00) prioridad del grupo de bloques establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-392">**TX_SUCCESS**: (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="bdbe0-393">TX_POOL_ERROR: (0x02) puntero del grupo de bloques de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-393">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-394">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-394">Allowed From</span></span>

<span data-ttu-id="bdbe0-395">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-395">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-396">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-396">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-397">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-397">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-398">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-398">Example</span></span>

```C
TX_BLOCK_POOL my_pool;
UINT          status;

/* Ensure that the highest priority thread will receive
   the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_block_release call will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-399">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-399">See Also</span></span>

- <span data-ttu-id="bdbe0-400">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-400">tx_block_allocate</span></span>
- <span data-ttu-id="bdbe0-401">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-401">tx_block_pool_create</span></span>
- <span data-ttu-id="bdbe0-402">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-402">tx_block_pool_delete</span></span>
- <span data-ttu-id="bdbe0-403">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-403">tx_block_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-404">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-404">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-405">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-405">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-406">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-406">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="bdbe0-407">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-407">tx_block_release</span></span>

<span data-ttu-id="bdbe0-408">Libera un bloque de memoria de tamaño fijo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-408">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-409">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-409">Prototype</span></span>

```C
UINT tx_block_release(VOID *block_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-410">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-410">Description</span></span>

<span data-ttu-id="bdbe0-411">Este servicio libera un bloque previamente asignado a su grupo de memoria asociado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-411">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="bdbe0-412">Si hay uno o más subprocesos suspendidos en espera de bloques de memoria de este grupo, el primer subproceso suspendido se asigna a este bloque de memoria y se reanuda.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-412">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-413">La aplicación debe impedir el uso de un área del bloque de memoria tras haberse liberado al grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-413">The application must prevent using a memory block area after it has been released back to the pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-414">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-414">Parameters</span></span>

- <span data-ttu-id="bdbe0-415">**block_ptr**: puntero al bloque de memoria asignado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-415">**block_ptr**: Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-416">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-416">Return Values</span></span>

- <span data-ttu-id="bdbe0-417">**TX_SUCCESS**: (0x00) bloque de memoria liberado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-417">**TX_SUCCESS**: (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="bdbe0-418">TX_PTR_ERROR: (0x03) puntero al bloque de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-418">TX_PTR_ERROR: (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-419">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-419">Allowed From</span></span>

<span data-ttu-id="bdbe0-420">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-420">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-421">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-421">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-422">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-422">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-423">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-423">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
unsigned char*memory_ptr;
UINT         status;

/* Release a memory block back to my_pool. Assume that the
   pool has been created and the memory block has been
   allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
   to by memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-424">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-424">See Also</span></span>

- <span data-ttu-id="bdbe0-425">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-425">tx_block_allocate</span></span>
- <span data-ttu-id="bdbe0-426">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-426">tx_block_pool_create</span></span>
- <span data-ttu-id="bdbe0-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-427">tx_block_pool_delete</span></span>
- <span data-ttu-id="bdbe0-428">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-428">tx_block_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-429">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-429">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-430">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-430">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-431">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-431">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="bdbe0-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-432">tx_byte_allocate</span></span>

<span data-ttu-id="bdbe0-433">Asigna bytes de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-433">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-434">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-434">Prototype</span></span>

```C
UINT tx_byte_allocate(TX_BYTE_POOL *pool_ptr,
                          VOID **memory_ptr, ULONG memory_size,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="bdbe0-435">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-435">Description</span></span>

<span data-ttu-id="bdbe0-436">Este servicio asigna el número especificado de bytes del grupo de bytes de memoria indicado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-436">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!WARNING]
> <span data-ttu-id="bdbe0-437">Es importante asegurarse de que el código de aplicación no escriba fuera del bloque de memoria asignado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-437">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="bdbe0-438">Si esto ocurre, se producen daños en un bloque de memoria adyacente (normalmente posterior).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-438">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="bdbe0-439">Los resultados son imprevisibles y suelen ser graves.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-439">The results are unpredictable and are often fatal!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-440">El rendimiento de este servicio es una función del tamaño de bloque y el nivel de fragmentación en el grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-440">The performance of this service is a function of the block size and the amount of fragmentation in the pool.</span></span> <span data-ttu-id="bdbe0-441">Por lo tanto, este servicio no se debe utilizar durante los subprocesos de ejecución críticos en el tiempo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-441">Hence, this service should not be used during time-critical threads of execution.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-442">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-442">Parameters</span></span>

- <span data-ttu-id="bdbe0-443">**pool_ptr**: puntero a un grupo de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-443">**pool_ptr**: Pointer to a previously created memory pool.</span></span>
- <span data-ttu-id="bdbe0-444">**memory_ptr**: puntero a un puntero de la memoria de destino.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-444">**memory_ptr**: Pointer to a destination memory pointer.</span></span> <span data-ttu-id="bdbe0-445">Si la asignación es correcta, la dirección del área de memoria asignada se coloca donde señala este parámetro.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-445">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="bdbe0-446">**memory_size**: número de bytes solicitados.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-446">**memory_size**: Number of bytes requested.</span></span>
- <span data-ttu-id="bdbe0-447">**wait_option**: define el comportamiento del servicio si no hay suficiente memoria disponible.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-447">**wait_option**: Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="bdbe0-448">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-448">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bdbe0-449">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-449">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="bdbe0-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="bdbe0-451">valor de tiempo de espera: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-451">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="bdbe0-452">Cuando se selecciona TX_NO_WAIT, se produce una devolución inmediata desde este servicio, con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-452">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="bdbe0-453">*Esta es la única opción válida si se llama al servicio desde la inicialización.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-453">*This is the only valid option if the service is called from initialization.*</span></span>

    <span data-ttu-id="bdbe0-454">Cuando se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya suficiente memoria disponible.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-454">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until enough memory is available.</span></span>

    <span data-ttu-id="bdbe0-455">Cuando se selecciona un valor numérico (de 1 a 0xFFFFFFFE), se está especificando el número máximo de tics del temporizador que el subproceso permanecerá suspendido mientras espera por la memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-455">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-456">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-456">Return Values</span></span>

- <span data-ttu-id="bdbe0-457">**TX_SUCCESS**: (0x00) memoria asignada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-457">**TX_SUCCESS**: (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="bdbe0-458">**TX_DELETED**: (0x01) el grupo de memoria se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-458">**TX_DELETED**: (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="bdbe0-459">**TX_NO_MEMORY**: (0x10) el servicio no pudo asignar la memoria en el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-459">**TX_NO_MEMORY**: (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="bdbe0-460">**TX_WAIT_ABORTED**: (0x1A) otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-460">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="bdbe0-461">TX_POOL_ERROR: (0x02) puntero del grupo de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-461">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="bdbe0-462">TX_PTR_ERROR: (0x03) puntero al puntero de destino no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-462">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="bdbe0-463">TX_SIZE_ERROR: (0x05) el tamaño solicitado es cero o mayor que el grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-463">TX_SIZE_ERROR: (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="bdbe0-464">TX_WAIT_ERROR: (0x04) se especificó una opción de espera distinta de TX_NO_WAIT en una llamada desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-464">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="bdbe0-465">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-465">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-466">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-466">Allowed From</span></span>

<span data-ttu-id="bdbe0-467">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-467">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-468">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-468">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-469">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-469">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-470">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-470">Example</span></span>

```C
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a 112 byte memory area from my_pool. Assume
   that the pool has already been created with a call to
   tx_byte_pool_create. */
status =  tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
                       112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated memory area. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-471">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-471">See Also</span></span>

- <span data-ttu-id="bdbe0-472">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-472">tx_byte_pool_create</span></span>
- <span data-ttu-id="bdbe0-473">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-473">tx_byte_pool_delete</span></span>
- <span data-ttu-id="bdbe0-474">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-474">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-475">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-475">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-476">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-476">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-477">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-477">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-478">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-478">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="bdbe0-479">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-479">tx_byte_pool_create</span></span>

<span data-ttu-id="bdbe0-480">Crea un grupo de bytes de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-480">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-481">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-481">Prototype</span></span>

```C
UINT tx_byte_pool_create(TX_BYTE_POOL *pool_ptr,
                          CHAR *name_ptr, VOID *pool_start,
                          ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="bdbe0-482">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-482">Description</span></span>

<span data-ttu-id="bdbe0-483">Este servicio crea un grupo de bytes de memoria en el área especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-483">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="bdbe0-484">En un principio, el grupo consta básicamente de un bloque libre muy grande.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-484">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="bdbe0-485">Sin embargo, el grupo se divide en bloques más pequeños a medida que se realizan asignaciones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-485">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-486">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-486">Parameters</span></span>

- <span data-ttu-id="bdbe0-487">**pool_ptr**: puntero al bloque de control de un grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-487">**pool_ptr**: Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="bdbe0-488">**name_ptr**: puntero al nombre del grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-488">**name_ptr**: Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="bdbe0-489">**pool_start**: dirección inicial del grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-489">**pool_start**: Starting address of the memory pool.</span></span> <span data-ttu-id="bdbe0-490">La dirección inicial debe corresponderse con el tamaño del tipo de datos ULONG.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-490">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="bdbe0-491">**pool_size**: número total de bytes disponibles para el grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-491">**pool_size**: Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-492">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-492">Return Values</span></span>

- <span data-ttu-id="bdbe0-493">**TX_SUCCESS**: (0x00) grupo de memoria creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-493">**TX_SUCCESS**: (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="bdbe0-494">TX_POOL_ERROR: (0x02) puntero del grupo de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-494">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="bdbe0-495">El puntero es NULL o el grupo ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-495">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="bdbe0-496">TX_PTR_ERROR: (0x03) dirección inicial del grupo no válida.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-496">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="bdbe0-497">TX_SIZE_ERROR: (0x05) el tamaño del grupo no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-497">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="bdbe0-498">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-498">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-499">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-499">Allowed From</span></span>

<span data-ttu-id="bdbe0-500">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-500">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-501">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-501">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-502">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-502">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-503">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-503">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Create a memory pool whose total size is 2000 bytes
   starting at address 0x500000. */
status =  tx_byte_pool_create(&my_pool, "my_pool_name",
             (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
   allocating memory. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-504">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-504">See Also</span></span>

- <span data-ttu-id="bdbe0-505">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-505">tx_byte_allocate</span></span>
- <span data-ttu-id="bdbe0-506">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-506">tx_byte_pool_delete</span></span>
- <span data-ttu-id="bdbe0-507">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-507">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-508">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-508">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-509">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-509">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-510">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-510">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-511">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-511">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="bdbe0-512">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-512">tx_byte_pool_delete</span></span>

<span data-ttu-id="bdbe0-513">Elimina un grupo de bytes de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-513">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-514">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-514">Prototype</span></span>

```C
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-515">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-515">Description</span></span>

<span data-ttu-id="bdbe0-516">Este servicio elimina el grupo de bytes de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-516">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="bdbe0-517">Todos los subprocesos suspendidos en espera de memoria de este grupo se reanudan y se les asigna un estado de devolución TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-517">All threads suspended waiting for memory from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-518">Es responsabilidad de la aplicación administrar el área de memoria asociada al grupo, que está disponible una vez completado este servicio.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-518">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="bdbe0-519">Además, debe impedir el uso de un grupo eliminado o de una memoria previamente asignada desde él.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-519">In addition, the application must prevent use of a deleted pool or memory previously allocated from it.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-520">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-520">Parameters</span></span> 

- <span data-ttu-id="bdbe0-521">**pool_ptr**: puntero a un grupo de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-521">**pool_ptr**: Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-522">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-522">Return Values</span></span>

- <span data-ttu-id="bdbe0-523">**TX_SUCCESS**: (0x00) grupo de memoria eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-523">**TX_SUCCESS**: (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="bdbe0-524">TX_POOL_ERROR: (0x02) puntero del grupo de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-524">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="bdbe0-525">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-525">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-526">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-526">Allowed From</span></span>

<span data-ttu-id="bdbe0-527">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-527">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-528">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-528">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-529">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-530">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-530">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Delete entire memory pool. Assume that the pool has already
   been created with a call to tx_byte_pool_create. */
status =   tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-531">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-531">See Also</span></span>

- <span data-ttu-id="bdbe0-532">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-532">tx_byte_allocate</span></span>
- <span data-ttu-id="bdbe0-533">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-533">tx_byte_pool_create</span></span>
- <span data-ttu-id="bdbe0-534">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-534">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-535">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-535">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-536">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-536">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-537">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-537">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-538">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-538">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="bdbe0-539">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-539">tx_byte_pool_info_get</span></span>

<span data-ttu-id="bdbe0-540">Recupera información acerca de un grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-540">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-541">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-541">Prototype</span></span>

```C
UINT tx_byte_pool_info_get(TX_BYTE_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *fragments,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BYTE_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="bdbe0-542">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-542">Description</span></span>

<span data-ttu-id="bdbe0-543">Este servicio recupera información sobre el grupo de bytes de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-543">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-544">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-544">Parameters</span></span>

- <span data-ttu-id="bdbe0-545">**pool_ptr**: puntero a un grupo de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-545">**pool_ptr**: Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="bdbe0-546">**name**: puntero al destino del puntero al nombre del grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-546">**name**: Pointer to destination for the pointer to the byte pool’s name.</span></span>
- <span data-ttu-id="bdbe0-547">**available**: puntero al destino del número de bytes disponibles en el grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-547">**available**: Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="bdbe0-548">**fragments**: puntero al destino del número total de fragmentos de memoria del grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-548">**fragments**: Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="bdbe0-549">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-549">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="bdbe0-550">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-550">**suspended_count**: Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="bdbe0-551">**next_pool**: puntero al destino del puntero del siguiente grupo de bytes creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-551">**next_pool**: Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-552">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-552">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-553">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-553">Return Values</span></span>

- <span data-ttu-id="bdbe0-554">**TX_SUCCESS**: (0x00) información del grupo recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-554">**TX_SUCCESS**: (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="bdbe0-555">TX_POOL_ERROR: (0x02) puntero del grupo de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-555">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-556">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-556">Allowed From</span></span>

<span data-ttu-id="bdbe0-557">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-557">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-558">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-558">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-559">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-559">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-560">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-560">Example</span></span>

```C
TX_BYTE_POOL my_pool;
CHAR         *name;
ULONG        available;
ULONG        fragments;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_BYTE_POOL *next_pool;
UINT         status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status =  tx_byte_pool_info_get(&my_pool, &name,
             &available, &fragments,
             &first_suspended, &suspended_count,
             &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-561">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-561">See Also</span></span>

- <span data-ttu-id="bdbe0-562">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-562">tx_byte_allocate</span></span>
- <span data-ttu-id="bdbe0-563">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-563">tx_byte_pool_create</span></span>
- <span data-ttu-id="bdbe0-564">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-564">tx_byte_pool_delete</span></span>
- <span data-ttu-id="bdbe0-565">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-565">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-566">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-566">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-567">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-567">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-568">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-568">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="bdbe0-569">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-569">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="bdbe0-570">Obtiene información acerca del rendimiento de un grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-570">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-571">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-571">Prototype</span></span>

```C
UINT tx_byte_pool_performance_info_get(TX_BYTE_POOL *pool_ptr,
        ULONG *allocates, ULONG *releases,
        ULONG *fragments_searched, ULONG *merges, ULONG *splits,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="bdbe0-572">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-572">Description</span></span>

<span data-ttu-id="bdbe0-573">Este servicio recupera información sobre el rendimiento del grupo de bytes de memoria especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-573">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-574">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-574">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-575">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-575">Parameters</span></span>

- <span data-ttu-id="bdbe0-576">**pool_ptr**: puntero a un grupo de bytes de memoria creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-576">**pool_ptr**: Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="bdbe0-577">**allocates**: puntero al destino del número de solicitudes de asignación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-577">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="bdbe0-578">**releases**: puntero al destino del número de solicitudes de liberación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-578">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="bdbe0-579">**fragments_searched**: puntero al destino del número de fragmentos de memoria interna buscados durante las solicitudes de asignación en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-579">**fragments_searched**: Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="bdbe0-580">**merges**: puntero al destino del número de bloques de memoria interna combinados durante las solicitudes de asignación en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-580">**merges**: Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="bdbe0-581">**splits**: puntero al destino del número de divisiones (fragmentos) de bloques de memoria interna creados durante las solicitudes de asignación en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-581">**splits**: Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="bdbe0-582">**suspensions**: puntero al destino del número de suspensiones de asignación de subprocesos de este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-582">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="bdbe0-583">**timeouts**: puntero al destino del número de tiempos de espera de las suspensiones de asignación de este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-583">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-584">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-584">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-585">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-585">Return Values</span></span>

- <span data-ttu-id="bdbe0-586">TX_SUCCESS: (0x00) rendimiento del grupo de bytes obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-586">TX_SUCCESS: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="bdbe0-587">**TX_PTR_ERROR**: (0x03) puntero del grupo de bytes no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-587">**TX_PTR_ERROR**: (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="bdbe0-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-589">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-589">Allowed From</span></span>

<span data-ttu-id="bdbe0-590">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-590">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-591">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-591">Example</span></span>

```C
TX_BYTE_POOL     my_pool;
ULONG            fragments_searched;
ULONG            merges;
ULONG            splits;
ULONG            allocates;
ULONG            releases;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created byte
   pool.  */
status =  tx_byte_pool_performance_info_get(&my_pool,
                &fragments_searched,
                &merges, &splits,
                &allocates, &releases,
                      &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-592">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-592">See Also</span></span>

- <span data-ttu-id="bdbe0-593">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-593">tx_byte_allocate</span></span>
- <span data-ttu-id="bdbe0-594">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-594">tx_byte_pool_create</span></span>
- <span data-ttu-id="bdbe0-595">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-595">tx_byte_pool_delete</span></span>
- <span data-ttu-id="bdbe0-596">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-596">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-597">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-597">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-598">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-598">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-599">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-599">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="bdbe0-600">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-600">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="bdbe0-601">Obtiene información acerca del rendimiento de los grupos de bytes del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-601">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-602">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-602">Prototype</span></span>

```C
UINT  tx_byte_pool_performance_system_info_get(ULONG *allocates,
        ULONG *releases, ULONG *fragments_searched, ULONG *merges,
        ULONG *splits, ULONG *suspensions, ULONG *timeouts);;
```
### <a name="description"></a><span data-ttu-id="bdbe0-603">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-603">Description</span></span>

<span data-ttu-id="bdbe0-604">Este servicio recupera información sobre el rendimiento de todos los grupos de bytes de memoria del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-604">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-605">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-605">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-606">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-606">Parameters</span></span>

- <span data-ttu-id="bdbe0-607">**allocates**: puntero al destino del número de solicitudes de asignación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-607">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="bdbe0-608">**releases**: puntero al destino del número de solicitudes de liberación realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-608">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="bdbe0-609">**fragments_searched**: puntero al destino del número total de fragmentos de memoria interna buscados durante las solicitudes de asignación en todos los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-609">**fragments_searched**: Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="bdbe0-610">**merges**: puntero al destino del número total de bloques de memoria interna combinados durante las solicitudes de asignación en todos los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-610">**merges**: Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="bdbe0-611">**splits**: puntero al destino del número total de divisiones (fragmentos) de bloques de memoria interna creados durante las solicitudes de asignación en todos los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-611">**splits**: Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="bdbe0-612">**suspensions**: puntero al destino del número total de suspensiones de asignación de subprocesos en todos los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-612">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="bdbe0-613">**timeouts**: puntero al destino del número total de tiempos de espera de las suspensiones de asignación de todos los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-613">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-614">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-614">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-615">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-615">Return Values</span></span>

- <span data-ttu-id="bdbe0-616">**TX_SUCCESS**: (0x00) rendimiento del grupo de bytes obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-616">**TX_SUCCESS**: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="bdbe0-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-618">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-618">Allowed From</span></span>

<span data-ttu-id="bdbe0-619">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-619">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-620">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-620">Example</span></span>

```C
ULONG         fragments_searched;
ULONG         merges;
ULONG         splits;
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all byte pools in the
   system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
                &merges, &splits, &allocates, &releases,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-621">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-621">See Also</span></span>

- <span data-ttu-id="bdbe0-622">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-622">tx_byte_allocate</span></span>
- <span data-ttu-id="bdbe0-623">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-623">tx_byte_pool_create</span></span>
- <span data-ttu-id="bdbe0-624">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-624">tx_byte_pool_delete</span></span>
- <span data-ttu-id="bdbe0-625">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-625">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-626">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-626">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-627">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-627">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="bdbe0-628">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-628">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="bdbe0-629">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-629">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="bdbe0-630">Da prioridad a un subproceso de un grupo de bytes en la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-630">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-631">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-631">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-632">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-632">Description</span></span>

<span data-ttu-id="bdbe0-633">Este servicio coloca el subproceso de prioridad más alta suspendido en la memoria de este grupo al principio de la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-633">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="bdbe0-634">Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-634">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-635">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-635">Parameters</span></span> 

- <span data-ttu-id="bdbe0-636">**pool_ptr**: puntero al bloque de control de un grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-636">**pool_ptr**: Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-637">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-637">Return Values</span></span>

- <span data-ttu-id="bdbe0-638">**TX_SUCCESS**: (0x00) prioridad del grupo de memoria establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-638">**TX_SUCCESS**: (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="bdbe0-639">TX_POOL_ERROR: (0x02) puntero del grupo de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-639">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-640">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-640">Allowed From</span></span>

<span data-ttu-id="bdbe0-641">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-641">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-642">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-642">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-643">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-643">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-644">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-644">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_byte_release call will wake up this thread,
   if there is enough memory to satisfy its request. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-645">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-645">See Also</span></span>

- <span data-ttu-id="bdbe0-646">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-646">tx_byte_allocate</span></span>
- <span data-ttu-id="bdbe0-647">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-647">tx_byte_pool_create</span></span>
- <span data-ttu-id="bdbe0-648">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-648">tx_byte_pool_delete</span></span>
- <span data-ttu-id="bdbe0-649">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-649">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-650">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-650">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-651">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-651">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-652">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-652">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="bdbe0-653">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="bdbe0-653">tx_byte_release</span></span>

<span data-ttu-id="bdbe0-654">Libera bytes al grupo de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-654">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-655">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-655">Prototype</span></span>

```C
UINT tx_byte_release(VOID *memory_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-656">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-656">Description</span></span>

<span data-ttu-id="bdbe0-657">Este servicio libera un área de memoria previamente asignada a su grupo asociado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-657">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="bdbe0-658">Si hay uno o más subprocesos suspendidos en espera de memoria de este grupo, se asigna memoria a cada subproceso suspendido y estos se reanudan hasta que la memoria se agote o no haya más subprocesos suspendidos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-658">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="bdbe0-659">Este proceso de asignación de memoria a los subprocesos suspendidos siempre comienza con el subproceso que se suspendió primero.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-659">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-660">La aplicación debe impedir el uso del área de memoria una vez que se libera.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-660">The application must prevent using the memory area after it is released.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-661">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-661">Parameters</span></span>

- <span data-ttu-id="bdbe0-662">**memory_ptr**: puntero al área de memoria asignada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-662">**memory_ptr**: Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-663">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-663">Return Values</span></span>

- <span data-ttu-id="bdbe0-664">**TX_SUCCESS**: (0x00) memoria liberada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-664">**TX_SUCCESS**: (0x00) Successful memory release.</span></span>
- <span data-ttu-id="bdbe0-665">TX_PTR_ERROR: (0x03) puntero del área de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-665">TX_PTR_ERROR: (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="bdbe0-666">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-666">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-667">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-667">Allowed From</span></span>

<span data-ttu-id="bdbe0-668">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-668">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-669">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-669">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-670">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-670">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-671">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-671">Example</span></span>

```C
unsigned char    *memory_ptr;
UINT             status;

/* Release a memory back to my_pool. Assume that the memory
   area was previously allocated from my_pool. */
status =  tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
   memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-672">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-672">See Also</span></span>

- <span data-ttu-id="bdbe0-673">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-673">tx_byte_allocate</span></span>
- <span data-ttu-id="bdbe0-674">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-674">tx_byte_pool_create</span></span>
- <span data-ttu-id="bdbe0-675">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-675">tx_byte_pool_delete</span></span>
- <span data-ttu-id="bdbe0-676">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-676">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="bdbe0-677">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-677">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-678">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-678">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-679">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-679">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="bdbe0-680">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-680">tx_event_flags_create</span></span>

<span data-ttu-id="bdbe0-681">Crea un grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-681">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-682">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-682">Prototype</span></span>

```c
UINT tx_event_flags_create(TX_EVENT_FLAGS_GROUP *group_ptr,
                          CHAR *name_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-683">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-683">Description</span></span>

<span data-ttu-id="bdbe0-684">Este servicio crea un grupo de 32 marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-684">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="bdbe0-685">Estas 32 marcas de evento del grupo se inicializan en cero.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-685">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="bdbe0-686">Cada marca de evento se representa con un solo bit.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-686">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-687">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-687">Parameters</span></span>

- <span data-ttu-id="bdbe0-688">**group_ptr**: puntero al bloque de control de un grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-688">**group_ptr**: Pointer to an event flags group control block.</span></span> 
- <span data-ttu-id="bdbe0-689">**name_ptr**: puntero al nombre del grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-689">**name_ptr**: Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-690">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-690">Return Values</span></span>

- <span data-ttu-id="bdbe0-691">**TX_SUCCESS**: (0x00) grupo de eventos creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-691">**TX_SUCCESS**: (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="bdbe0-692">TX_GROUP_ERROR: (0x06) puntero del grupo de eventos no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-692">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="bdbe0-693">El puntero es NULL o el grupo de eventos ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-693">Either the pointer is NULL or the event group is already created.</span></span>
- <span data-ttu-id="bdbe0-694">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-694">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-695">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-695">Allowed From</span></span>

<span data-ttu-id="bdbe0-696">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-696">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-697">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-697">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-698">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-698">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-699">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-699">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_group;
UINT         status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
            "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
   for get and set services. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-700">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-700">See Also</span></span>

- <span data-ttu-id="bdbe0-701">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-701">tx_event_flags_delete</span></span>
- <span data-ttu-id="bdbe0-702">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-702">tx_event_flags_get</span></span>
- <span data-ttu-id="bdbe0-703">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-703">tx_event_flags_info_get</span></span>
- <span data-ttu-id="bdbe0-704">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-704">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-705">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-705">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-706">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="bdbe0-706">tx_event_flags_set</span></span>
- <span data-ttu-id="bdbe0-707">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-707">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="bdbe0-708">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-708">tx_event_flags_delete</span></span>

<span data-ttu-id="bdbe0-709">Elimina un grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-709">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-710">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-710">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-711">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-711">Description</span></span>

<span data-ttu-id="bdbe0-712">Este servicio elimina el grupo de marcas de evento especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-712">This service deletes the specified event flags group.</span></span> <span data-ttu-id="bdbe0-713">Todos los subprocesos suspendidos en espera de eventos de este grupo se reanudan y se les asigna un estado de devolución TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-713">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-714">Antes de eliminar el grupo de marcas de evento, la aplicación debe asegurarse de que se complete (o se deshabilite) cualquier devolución de llamada de notificación de operación de establecimiento de este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-714">The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group.</span></span> <span data-ttu-id="bdbe0-715">Además, la aplicación debe impedir el uso futuro de un grupo de marcas de evento eliminado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-715">In addition, the application must prevent all future use of a deleted event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-716">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-716">Parameters</span></span> 

- <span data-ttu-id="bdbe0-717">**group_ptr**: puntero a un grupo de marcas de evento creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-717">**group_ptr**: Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-718">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-718">Return Values</span></span>

- <span data-ttu-id="bdbe0-719">**TX_SUCCESS**: (0x00) grupo de marcas de evento eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-719">**TX_SUCCESS**: (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="bdbe0-720">TX_GROUP_ERROR: (0x06) puntero del grupo de marcas de evento no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-720">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="bdbe0-721">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-721">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-722">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-722">Allowed From</span></span>

<span data-ttu-id="bdbe0-723">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-723">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-724">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-724">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-725">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-725">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-726">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-726">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT                 status;

/* Delete event flags group. Assume that the group has
   already been created with a call to
   tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-727">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-727">See Also</span></span>

- <span data-ttu-id="bdbe0-728">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-728">tx_event_flags_create</span></span>
- <span data-ttu-id="bdbe0-729">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-729">tx_event_flags_get</span></span>
- <span data-ttu-id="bdbe0-730">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-730">tx_event_flags_info_get</span></span>
- <span data-ttu-id="bdbe0-731">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-731">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-732">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-732">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-733">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="bdbe0-733">tx_event_flags_set</span></span>
- <span data-ttu-id="bdbe0-734">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-734">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="bdbe0-735">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-735">tx_event_flags_get</span></span>

<span data-ttu-id="bdbe0-736">Obtiene marcas de evento de un grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-736">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-737">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-737">Prototype</span></span>

```C
UINT tx_event_flags_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG requested_flags, UINT get_option,
                          ULONG *actual_flags_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="bdbe0-738">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-738">Description</span></span>

<span data-ttu-id="bdbe0-739">Este servicio recupera las marcas de evento del grupo de marcas de evento especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-739">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="bdbe0-740">Cada grupo contiene 32 marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-740">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="bdbe0-741">Cada marca se representa con un solo bit.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-741">Each flag is represented by a single bit.</span></span> <span data-ttu-id="bdbe0-742">Este servicio puede recuperar diversas combinaciones de marcas de evento, según se seleccione mediante los parámetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-742">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-743">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-743">Parameters</span></span>

- <span data-ttu-id="bdbe0-744">**group_ptr**: puntero a un grupo de marcas de evento creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-744">**group_ptr**: Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="bdbe0-745">**requested_flags**: variable sin signo de 32 bits que representa las marcas de evento solicitadas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-745">**requested_flags**: 32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="bdbe0-746">**get_option**: especifica si se necesitan todas o algunas de las marcas de evento solicitadas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-746">**get_option**: Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="bdbe0-747">A continuación se indican las selecciones válidas:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-747">The following are valid selections:</span></span>
    - <span data-ttu-id="bdbe0-748">**TX_AND**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-748">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="bdbe0-749">**TX_AND_CLEAR**: (0x03)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-749">**TX_AND_CLEAR**: (0x03)</span></span>
    - <span data-ttu-id="bdbe0-750">**TX_OR**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-750">**TX_OR**: (0x00)</span></span>
    - <span data-ttu-id="bdbe0-751">**TX_OR_CLEAR**: (0x01)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-751">**TX_OR_CLEAR**: (0x01)</span></span>

    <span data-ttu-id="bdbe0-752">Cuando se selecciona TX_AND o TX_AND_CLEAR, se especifica que todas las marcas de evento deben estar presentes en el grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-752">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="bdbe0-753">Cuando se selecciona TX_OR o TX_OR_CLEAR, se especifica que basta con alguna marca de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-753">Selecting TX_OR or TX_OR_CLEAR specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="bdbe0-754">Si se especifican TX_AND_CLEAR o TX_OR_CLEAR, las marcas de evento que atienden la solicitud se borran (se establecen en cero).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-754">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="bdbe0-755">**actual_flags_ptr**: puntero al destino donde se colocan las marcas de evento recuperadas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-755">**actual_flags_ptr**: Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="bdbe0-756">Tenga en cuenta que las marcas reales obtenidas pueden incluir marcas que no se hayan solicitado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-756">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="bdbe0-757">**wait_option**: define el comportamiento del servicio si no se establecen las marcas de evento seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-757">**wait_option**: Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="bdbe0-758">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-758">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bdbe0-759">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-759">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="bdbe0-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="bdbe0-761">valor de tiempo de espera: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-761">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="bdbe0-762">Cuando se selecciona TX_NO_WAIT, se produce una devolución inmediata desde este servicio, con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-762">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="bdbe0-763">Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-763">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="bdbe0-764">Cuando se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya marcas de evento disponibles.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-764">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>

    <span data-ttu-id="bdbe0-765">Cuando se selecciona un valor numérico (de 1 a 0xFFFFFFFE), se está especificando el número máximo de tics del temporizador que el subproceso permanecerá suspendido mientras espera por las marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-765">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-766">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-766">Return Values</span></span>

- <span data-ttu-id="bdbe0-767">**TX_SUCCESS**: (0x00) marcas de evento obtenidas correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-767">**TX_SUCCESS**: (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="bdbe0-768">**TX_DELETED**: (0x01) el grupo de marcas de evento se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-768">**TX_DELETED**: (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="bdbe0-769">**TX_NO_EVENTS**: (0x07) el servicio no pudo obtener los eventos indicados en el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-769">**TX_NO_EVENTS**: (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="bdbe0-770">**TX_WAIT_ABORTED**: (0x1A) otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-770">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="bdbe0-771">TX_GROUP_ERROR: (0x06) puntero del grupo de marcas de evento no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-771">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="bdbe0-772">TX_PTR_ERROR: (0x03) puntero de las marcas de evento reales no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-772">TX_PTR_ERROR: (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="bdbe0-773">TX_WAIT_ERROR: (0x04) se especificó una opción de espera distinta de TX_NO_WAIT en una llamada desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-773">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="bdbe0-774">TX_OPTION_ERROR: (0x08) se especificó un valor de get_option no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-774">TX_OPTION_ERROR: (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-775">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-775">Allowed From</span></span>

<span data-ttu-id="bdbe0-776">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-776">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-777">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-777">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-778">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-778">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-779">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-779">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG         actual_events;
UINT          status;

/* Request that event flags 0, 4, and 8 are all set. Also,
   if they are set they should be cleared. If the event
   flags are not set, this service suspends for a maximum of
   20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
                      TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
   actual events obtained. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-780">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-780">See Also</span></span>

- <span data-ttu-id="bdbe0-781">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-781">tx_event_flags_create</span></span>
- <span data-ttu-id="bdbe0-782">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-782">tx_event_flags_delete</span></span>
- <span data-ttu-id="bdbe0-783">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-783">tx_event_flags_info_get</span></span>
- <span data-ttu-id="bdbe0-784">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-784">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-785">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-785">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-786">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="bdbe0-786">tx_event_flags_set</span></span>
- <span data-ttu-id="bdbe0-787">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-787">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_info_get"></a><span data-ttu-id="bdbe0-788">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-788">tx_event_flags_info_get</span></span>

<span data-ttu-id="bdbe0-789">Recupera información acerca de un grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-789">Retrieve information about event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-790">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-790">Prototype</span></span>

```C
UINT tx_event_flags_info_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                         CHAR **name, ULONG *current_flags,
                         TX_THREAD **first_suspended,
                         ULONG *suspended_count,
                         TX_EVENT_FLAGS_GROUP **next_group);
```
### <a name="description"></a><span data-ttu-id="bdbe0-791">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-791">Description</span></span>

<span data-ttu-id="bdbe0-792">Este servicio recupera información sobre el grupo de marcas de evento especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-792">This service retrieves information about the specified event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-793">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-793">Parameters</span></span>

- <span data-ttu-id="bdbe0-794">**group_ptr**: puntero al bloque de control de un grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-794">**group_ptr**: Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="bdbe0-795">**name**: puntero al destino del puntero al nombre del grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-795">**name**: Pointer to destination for the pointer to the event flags group’s name.</span></span>
- <span data-ttu-id="bdbe0-796">**current_flags**: puntero al destino de las marcas establecidas actualmente en el grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-796">**current_flags**: Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="bdbe0-797">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-797">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="bdbe0-798">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-798">**suspended_count**: Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="bdbe0-799">**next_group**: puntero al destino del puntero del siguiente grupo de marcas de evento creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-799">**next_group**: Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-800">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-800">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-801">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-801">Return Values</span></span>

- <span data-ttu-id="bdbe0-802">**TX_SUCCESS**: (0x00) información del grupo de eventos recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-802">**TX_SUCCESS**: (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="bdbe0-803">TX_GROUP_ERROR: (0x06) puntero del grupo de eventos no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-803">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-804">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-804">Allowed From</span></span>

<span data-ttu-id="bdbe0-805">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-805">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-806">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-806">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-807">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-807">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-808">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-808">Example</span></span>

```c
TX_EVENT_FLAGS_GROUPmy_event_group;
CHAR          *name;
ULONG         current_flags;
TX_THREAD     *first_suspended;
ULONG         suspended_count;
TX_EVENT_FLAGS_GROUP*next_group;
UINT          status;

/* Retrieve information about the previously created
   event flags group "my_event_group." */
status =  tx_event_flags_info_get(&my_event_group, &name,
             &current_flags,
             &first_suspended, &suspended_count,
             &next_group);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-809">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-809">See Also</span></span>

- <span data-ttu-id="bdbe0-810">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-810">tx_event_flags_create</span></span>
- <span data-ttu-id="bdbe0-811">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-811">tx_event_flags_delete</span></span>
- <span data-ttu-id="bdbe0-812">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-812">tx_event_flags_get</span></span>
- <span data-ttu-id="bdbe0-813">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-813">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-814">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-814">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-815">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="bdbe0-815">tx_event_flags_set</span></span>
- <span data-ttu-id="bdbe0-816">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-816">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance-info_get"></a><span data-ttu-id="bdbe0-817">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-817">tx_event_flags_performance info_get</span></span>

<span data-ttu-id="bdbe0-818">Obtiene información acerca del rendimiento de un grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-818">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-819">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-819">Prototype</span></span>

```C
UINT tx_event_flags_performance_info_get(TX_EVENT_FLAGS_GROUP
                        *group_ptr, ULONG *sets, ULONG *gets,
                        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="bdbe0-820">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-820">Description</span></span>

<span data-ttu-id="bdbe0-821">Este servicio recupera información sobre el rendimiento del grupo de marcas de evento especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-821">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-822">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-822">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-823">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-823">Parameters</span></span>

- <span data-ttu-id="bdbe0-824">**group_ptr**: puntero a un grupo de marcas de evento creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-824">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="bdbe0-825">**sets**: puntero al destino del número de solicitudes Set de marcas de evento realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-825">**sets**: Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="bdbe0-826">**gets**: puntero al destino del número de solicitudes Get de marcas de evento realizadas en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-826">**gets**: Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="bdbe0-827">**suspensions**: puntero al destino del número de suspensiones de solicitudes Get de marcas de evento de los subprocesos en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-827">**suspensions**: Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="bdbe0-828">**timeouts**: puntero al destino del número de tiempos de espera de suspensiones de solicitudes Get de marcas de evento en este grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-828">**timeouts**: Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-829">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-829">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-830">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-830">Return Values</span></span>

- <span data-ttu-id="bdbe0-831">**TX_SUCCESS**: (0x00) rendimiento del grupo de marcas de evento obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-831">**TX_SUCCESS**: (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="bdbe0-832">**TX_PTR_ERROR**: (0x03) puntero del grupo de marcas de evento no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-832">**TX_PTR_ERROR**: (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="bdbe0-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-834">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-834">Allowed From</span></span>

<span data-ttu-id="bdbe0-835">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-835">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-836">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-836">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flag_group;
ULONG           sets;
ULONG           gets;
ULONG           suspensions;
ULONG           timeouts;

/* Retrieve performance information on the previously created event
   flag group. */
status =  tx_event_flags_performance_info_get(&my_event_flag_group,
   &sets, &gets, &suspensions,
   &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
   retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-837">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-837">See Also</span></span>

- <span data-ttu-id="bdbe0-838">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-838">tx_event_flags_create</span></span>
- <span data-ttu-id="bdbe0-839">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-839">tx_event_flags_delete</span></span>
- <span data-ttu-id="bdbe0-840">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-840">tx_event_flags_get</span></span>
- <span data-ttu-id="bdbe0-841">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-841">tx_event_flags_info_get</span></span>
- <span data-ttu-id="bdbe0-842">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-842">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-843">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="bdbe0-843">tx_event_flags_set</span></span>
- <span data-ttu-id="bdbe0-844">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-844">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="bdbe0-845">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-845">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="bdbe0-846">Recupera información acerca del rendimiento de todos los grupos de marcas de evento del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-846">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-847">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-847">Prototype</span></span>

```c
UINT  tx_event_flags_performance_system_info_get(ULONG *sets,
        ULONG *gets,ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="bdbe0-848">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-848">Description</span></span>

<span data-ttu-id="bdbe0-849">Este servicio recupera información sobre el rendimiento de todos los grupos de marcas de evento del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-849">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-850">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-850">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-851">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-851">Parameters</span></span>

- <span data-ttu-id="bdbe0-852">**sets**: puntero al destino del número total de solicitudes Set de marcas de evento realizadas en todos los grupos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-852">**sets**: Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="bdbe0-853">**gets**: puntero al destino del número total de solicitudes Get de marcas de evento realizadas en todos los grupos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-853">**gets**: Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="bdbe0-854">**suspensions**: puntero al destino del número total de suspensiones de solicitudes Get de marcas de evento de los subprocesos de todos los grupos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-854">**suspensions**: Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="bdbe0-855">**timeouts**: puntero al destino del número total de tiempos de espera de suspensiones de solicitudes Get de marcas de evento de todos los grupos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-855">**timeouts**: Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-856">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-856">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-857">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-857">Return Values</span></span>

- <span data-ttu-id="bdbe0-858">**TX_SUCCESS**: (0x00) rendimiento de las marcas de evento del sistema obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-858">**TX_SUCCESS**: (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="bdbe0-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-860">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-860">Allowed From</span></span>

<span data-ttu-id="bdbe0-861">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-861">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-862">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-862">Example</span></span>

```c
ULONG         sets;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created event
   flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-863">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-863">See Also</span></span>

- <span data-ttu-id="bdbe0-864">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-864">tx_event_flags_create</span></span>
- <span data-ttu-id="bdbe0-865">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-865">tx_event_flags_delete</span></span>
- <span data-ttu-id="bdbe0-866">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-866">tx_event_flags_get</span></span>
- <span data-ttu-id="bdbe0-867">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-867">tx_event_flags_info_get</span></span>
- <span data-ttu-id="bdbe0-868">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-868">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-869">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="bdbe0-869">tx_event_flags_set</span></span>
- <span data-ttu-id="bdbe0-870">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-870">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="bdbe0-871">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="bdbe0-871">tx_event_flags_set</span></span>

<span data-ttu-id="bdbe0-872">Establece marcas de evento en un grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-872">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-873">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-873">Prototype</span></span>

```C
UINT tx_event_flags_set(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG  flags_to_set,UINT set_option);
```
### <a name="description"></a><span data-ttu-id="bdbe0-874">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-874">Description</span></span>

<span data-ttu-id="bdbe0-875">Este servicio establece o borra las marcas de evento de un grupo de marcas de evento, en función del valor especificado en set_option.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-875">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="bdbe0-876">Se reanudan todos los subprocesos suspendidos cuya solicitud de marcas de evento se haya atendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-876">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-877">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-877">Parameters</span></span>

- <span data-ttu-id="bdbe0-878">**group_ptr**: puntero al bloque de control del grupo de marcas de evento creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-878">**group_ptr**: Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="bdbe0-879">**flags_to_set**: especifica las marcas de evento que se van a establecer o borrar en función del valor seleccionado en set_option.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-879">**flags_to_set**: Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="bdbe0-880">**set_option**: especifica si se aplica AND u OR a las marcas de evento agregadas a las marcas de evento actuales del grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-880">**set_option**: Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="bdbe0-881">A continuación se indican las selecciones válidas:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-881">The following are valid selections:</span></span>
    - <span data-ttu-id="bdbe0-882">**TX_AND**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-882">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="bdbe0-883">**TX_OR**: (0x00) cuando se selecciona TX_AND, se especifica que se aplica **AND** a las marcas de evento agregadas a las marcas de evento actuales del grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-883">**TX_OR**: (0x00) Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="bdbe0-884">Esta opción se usa a menudo para borrar las marcas de evento de un grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-884">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="bdbe0-885">En cambio, si se especifica TX_OR, se aplica **OR** al agregar las marcas de evento indicadas con el evento actual del grupo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-885">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-886">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-886">Return Values</span></span>

- <span data-ttu-id="bdbe0-887">**TX_SUCCESS**: (0x00) marcas de evento establecidas correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-887">**TX_SUCCESS**: (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="bdbe0-888">TX_GROUP_ERROR: (0x06) puntero al grupo de marcas de evento no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-888">TX_GROUP_ERROR: (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="bdbe0-889">TX_OPTION_ERROR: (0x08) el valor de set_option especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-889">TX_OPTION_ERROR: (0x08) Invalid set-option specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-890">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-890">Allowed From</span></span>

<span data-ttu-id="bdbe0-891">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-891">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-892">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-892">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-893">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-893">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-894">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-894">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flags_group;
UINT         status;

/* Set event flags 0, 4, and 8. */
status =  tx_event_flags_set(&my_event_flags_group,
                           0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
   set and any suspended thread whose request was satisfied
   has been resumed. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-895">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-895">See Also</span></span>

- <span data-ttu-id="bdbe0-896">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-896">tx_event_flags_create</span></span>
- <span data-ttu-id="bdbe0-897">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-897">tx_event_flags_delete</span></span>
- <span data-ttu-id="bdbe0-898">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-898">tx_event_flags_get</span></span>
- <span data-ttu-id="bdbe0-899">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-899">tx_event_flags_info_get</span></span>
- <span data-ttu-id="bdbe0-900">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-900">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-901">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-901">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-902">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-902">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="bdbe0-903">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-903">tx_event_flags_set_notify</span></span>

<span data-ttu-id="bdbe0-904">Notifica a la aplicación cuando se establecen marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-904">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-905">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-905">Prototype</span></span>

```C
UINT tx_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr,
       VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```
### <a name="description"></a><span data-ttu-id="bdbe0-906">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-906">Description</span></span>

<span data-ttu-id="bdbe0-907">Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se establecen una o varias marcas de evento en el grupo de marcas de evento especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-907">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="bdbe0-908">La aplicación define el procesamiento de la devolución de llamada de notificación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-908">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="bdbe0-909">La devolución de llamada de notificación de establecimiento de marcas de evento de la aplicación no puede llamar a ninguna API de ThreadX SMP con una opción de suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-909">The application’s event flags set notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-910">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-910">Parameters</span></span> 
- <span data-ttu-id="bdbe0-911">**group_ptr**: puntero a un grupo de marcas de evento creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-911">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="bdbe0-912">**events_set_notify**: puntero a la función de notificación de establecimiento de marcas de evento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-912">**events_set_notify**: Pointer to application’s event flags set notification function.</span></span> <span data-ttu-id="bdbe0-913">Si este valor es TX_NULL, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-913">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-914">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-914">Return Values</span></span>

- <span data-ttu-id="bdbe0-915">**TX_SUCCESS**: (0x00) notificación de establecimiento de marcas de evento registrada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-915">**TX_SUCCESS**: (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="bdbe0-916">TX_GROUP_ERROR: (0x06) puntero del grupo de marcas de evento no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-916">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="bdbe0-917">TX_FEATURE_NOT_ENABLED: (0xFF) el sistema se compiló con las funcionalidades de notificación deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-917">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-918">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-918">Allowed From</span></span>

<span data-ttu-id="bdbe0-919">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-919">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-920">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-920">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_group;

/* Register the "my_event_flags_set_notify" function for monitoring
   event flags set in the event flags group "my_group." */
status =  tx_event_flags_set_notify(&my_group,
                my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
   was successfully registered. */

void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)
   /* One or more event flags was set in this group! */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-921">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-921">See Also</span></span>

- <span data-ttu-id="bdbe0-922">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-922">tx_event_flags_create</span></span>
- <span data-ttu-id="bdbe0-923">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-923">tx_event_flags_delete</span></span>
- <span data-ttu-id="bdbe0-924">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-924">tx_event_flags_get</span></span>
- <span data-ttu-id="bdbe0-925">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-925">tx_event_flags_info_get</span></span>
- <span data-ttu-id="bdbe0-926">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-926">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-927">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-927">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-928">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="bdbe0-928">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="bdbe0-929">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="bdbe0-929">tx_interrupt_control</span></span>

<span data-ttu-id="bdbe0-930">Habilita y deshabilita interrupciones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-930">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-931">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-931">Prototype</span></span>

```C
UINT tx_interrupt_control(UINT new_posture);
```
### <a name="description"></a><span data-ttu-id="bdbe0-932">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-932">Description</span></span>

<span data-ttu-id="bdbe0-933">Este servicio habilita o deshabilita las interrupciones según especifique el parámetro de entrada **new_posture**.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-933">This service enables or disables interrupts as specified by the input parameter **new_posture**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-934">Si se llama a este servicio desde un subproceso de aplicación, la posición de interrupción sigue formando parte del contexto del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-934">If this service is called from an application thread, the interrupt posture remains part of that thread’s context.</span></span> <span data-ttu-id="bdbe0-935">Por ejemplo, si el subproceso llama a esta rutina para deshabilitar las interrupciones y a continuación se suspende, al reanudarse, las interrupciones se deshabilitan de nuevo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-935">For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.</span></span>

> [!WARNING]
> <span data-ttu-id="bdbe0-936">Este servicio no debe usarse para habilitar interrupciones durante la inicialización.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-936">This service should not be used to enable interrupts during initialization!</span></span> <span data-ttu-id="bdbe0-937">Esto podría provocar resultados imprevisibles.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-937">Doing so could cause unpredictable results.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-938">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-938">Parameters</span></span>

- <span data-ttu-id="bdbe0-939">**new_posture**: este parámetro especifica si las interrupciones están deshabilitadas o habilitadas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-939">**new_posture**: This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="bdbe0-940">Entre los valores válidos se incluyen **TX_INT_DISABLE y TX_INT_ENABLE**.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-940">Legal values include **TX_INT_DISABLE and TX_INT_ENABLE.**</span></span> <span data-ttu-id="bdbe0-941">Los valores reales de estos parámetros son específicos de la distribución.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-941">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="bdbe0-942">Además, algunas arquitecturas de procesamiento pueden admitir posiciones adicionales para deshabilitar interrupciones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-942">In addition, some processing architectures might support additional interrupt disable postures.</span></span> <span data-ttu-id="bdbe0-943">Para obtener más información, consulte la información del archivo **_readme_threadx.txt_** incluido en el disco de distribución.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-943">Please see the **_readme_threadx.txt_** information supplied on the distribution disk for more details.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-944">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-944">Return Values</span></span>

- <span data-ttu-id="bdbe0-945">posición anterior: este servicio devuelve la posición de interrupción anterior al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-945">previous posture: This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="bdbe0-946">Esto permite a los usuarios del servicio restaurar la posición anterior tras deshabilitar las interrupciones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-946">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-947">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-947">Allowed From</span></span>

<span data-ttu-id="bdbe0-948">Subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-948">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-949">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-949">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-950">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-950">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-951">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-951">Example</span></span>

```C
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture =  tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
   locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-952">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-952">See Also</span></span>

<span data-ttu-id="bdbe0-953">Ninguno</span><span class="sxs-lookup"><span data-stu-id="bdbe0-953">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="bdbe0-954">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-954">tx_mutex_create</span></span>

<span data-ttu-id="bdbe0-955">Crea una exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-955">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-956">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-956">Prototype</span></span>

```C
UINT tx_mutex_create(TX_MUTEX *mutex_ptr,
                          CHAR *name_ptr, UINT priority_inherit);
```
### <a name="description"></a><span data-ttu-id="bdbe0-957">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-957">Description</span></span>
    
<span data-ttu-id="bdbe0-958">Este servicio crea una exclusión mutua entre subprocesos para la protección de los recursos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-958">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-959">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-959">Parameters</span></span>

- <span data-ttu-id="bdbe0-960">**mutex_ptr**: puntero al bloque de control de una exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-960">**mutex_ptr**: Pointer to a mutex control block.</span></span>
- <span data-ttu-id="bdbe0-961">**name_ptr**: puntero al nombre de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-961">**name_ptr**: Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="bdbe0-962">**priority_inherit**: especifica si esta exclusión mutua admite o no la herencia de prioridad.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-962">**priority_inherit**: Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="bdbe0-963">Si este valor es TX_INHERIT, se admite la herencia de prioridad.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-963">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="bdbe0-964">Por el contrario, si se especifica TX_NO_INHERIT, la exclusión mutua no admite la herencia de prioridad.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-964">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-965">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-965">Return Values</span></span>

- <span data-ttu-id="bdbe0-966">**TX_SUCCESS**: (0x00) exclusión mutua creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-966">**TX_SUCCESS**: (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="bdbe0-967">TX_MUTEX_ERROR: (0x1C) puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-967">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="bdbe0-968">El puntero es NULL o la exclusión mutua ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-968">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="bdbe0-969">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-969">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="bdbe0-970">TX_INHERIT_ERROR: (0x1F) parámetro de herencia de prioridad no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-970">TX_INHERIT_ERROR: (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-971">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-971">Allowed From</span></span>

<span data-ttu-id="bdbe0-972">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-972">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-973">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-973">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-974">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-974">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-975">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-975">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Create a mutex to provide protection over a
   common resource. */
status =  tx_mutex_create(&my_mutex,"my_mutex_name",
                           TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-976">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-976">See Also</span></span>

- <span data-ttu-id="bdbe0-977">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-977">tx_mutex_delete</span></span>
- <span data-ttu-id="bdbe0-978">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-978">tx_mutex_get</span></span>
- <span data-ttu-id="bdbe0-979">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-979">tx_mutex_info_get</span></span>
- <span data-ttu-id="bdbe0-980">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-980">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-981">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-981">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-982">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-982">tx_mutex_prioritize</span></span>
- <span data-ttu-id="bdbe0-983">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-983">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="bdbe0-984">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-984">tx_mutex_delete</span></span>

<span data-ttu-id="bdbe0-985">Elimina una exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-985">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-986">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-986">Prototype</span></span>

```C
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-987">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-987">Description</span></span>

<span data-ttu-id="bdbe0-988">Este servicio elimina la exclusión mutua especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-988">This service deletes the specified mutex.</span></span> <span data-ttu-id="bdbe0-989">Todos los subprocesos suspendidos en espera de la exclusión mutua se reanudan y se les asigna un estado de devolución TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-989">All threads suspended waiting for the mutex are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-990">Es responsabilidad de la aplicación impedir el uso de una exclusión mutua eliminada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-990">It is the application’s responsibility to prevent use of a deleted mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-991">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-991">Parameters</span></span>

- <span data-ttu-id="bdbe0-992">**mutex_ptr**: puntero a una exclusión mutua creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-992">**mutex_ptr**: Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-993">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-993">Return Values</span></span>

- <span data-ttu-id="bdbe0-994">**TX_SUCCESS**: (0x00) exclusión mutua eliminada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-994">**TX_SUCCESS**: (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="bdbe0-995">TX_MUTEX_ERROR: (0x1C) puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-995">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="bdbe0-996">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-996">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-997">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-997">Allowed From</span></span>

<span data-ttu-id="bdbe0-998">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-998">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-999">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-999">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1000">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1000">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1001">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1001">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Delete a mutex. Assume that the mutex
   has already been created. */
status =  tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1002">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1002">See Also</span></span>

- <span data-ttu-id="bdbe0-1003">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1003">tx_mutex_create</span></span>
- <span data-ttu-id="bdbe0-1004">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1004">tx_mutex_get</span></span>
- <span data-ttu-id="bdbe0-1005">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1005">tx_mutex_info_get</span></span>
- <span data-ttu-id="bdbe0-1006">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1006">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1007">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1007">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1008">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1008">tx_mutex_prioritize</span></span>
- <span data-ttu-id="bdbe0-1009">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1009">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="bdbe0-1010">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1010">tx_mutex_get</span></span>

<span data-ttu-id="bdbe0-1011">Obtiene la propiedad de una exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1011">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1012">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1012">Prototype</span></span>

```C
UINT tx_mutex_get(TX_MUTEX *mutex_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1013">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1013">Description</span></span>

<span data-ttu-id="bdbe0-1014">Este servicio intenta obtener la propiedad exclusiva de la exclusión mutua especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1014">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="bdbe0-1015">Si el subproceso que realiza la llamada ya es el propietario de la exclusión mutua, se incrementa un contador interno y se devuelve un estado correcto.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1015">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="bdbe0-1016">Si otro subproceso con una prioridad más alta tiene la propiedad de la exclusión mutua y se especificó la herencia de prioridad al crear la exclusión, la prioridad del subproceso de menor prioridad se aumentará temporalmente al nivel de la del subproceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1016">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread’s priority will be temporarily raised to that of the calling thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1017">Un subproceso externo no debe modificar la prioridad del subproceso de menor prioridad que posee una exclusión mutua con herencia de prioridad mientras este es propietario de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1017">The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1018">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1018">Parameters</span></span>

- <span data-ttu-id="bdbe0-1019">**mutex_ptr**: puntero a una exclusión mutua creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1019">**mutex_ptr**: Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="bdbe0-1020">**wait_option**: define el comportamiento del servicio si la exclusión mutua ya pertenece a otro subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1020">**wait_option**: Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="bdbe0-1021">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1021">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bdbe0-1022">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1022">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="bdbe0-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="bdbe0-1024">valor de tiempo de espera: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1024">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="bdbe0-1025">Cuando se selecciona TX_NO_WAIT, se produce una devolución inmediata desde este servicio, con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1025">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="bdbe0-1026">*Esta es la única opción válida si se llama al servicio desde la inicialización.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1026">*This is the only valid option if the service is called from Initialization.*</span></span>

    <span data-ttu-id="bdbe0-1027">Cuando se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya una exclusión mutua disponible.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1027">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the mutex is available.</span></span>

    <span data-ttu-id="bdbe0-1028">Cuando se selecciona un valor numérico (de 1 a 0xFFFFFFFE), se está especificando el número máximo de tics del temporizador que el subproceso permanecerá suspendido mientras espera por la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1028">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1029">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1029">Return Values</span></span>

- <span data-ttu-id="bdbe0-1030">**TX_SUCCESS**: (0x00) operación Get de la exclusión mutua realizada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1030">**TX_SUCCESS**: (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="bdbe0-1031">**TX_DELETED**: (0x01) la exclusión mutua se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1031">**TX_DELETED**: (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="bdbe0-1032">**TX_NOT_AVAILABLE**: (0x1D) el servicio no pudo obtener la propiedad de la exclusión mutua en el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1032">**TX_NOT_AVAILABLE**: (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="bdbe0-1033">**TX_WAIT_ABORTED**: (0x1A) otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1033">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="bdbe0-1034">TX_MUTEX_ERROR: (0x1C) puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1034">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="bdbe0-1035">TX_WAIT_ERROR: (0x04) se especificó una opción de espera distinta de TX_NO_WAIT en una llamada desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1035">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="bdbe0-1036">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1036">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1037">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1037">Allowed From</span></span>

<span data-ttu-id="bdbe0-1038">Inicialización, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1038">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1039">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1039">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1040">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1040">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1041">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1041">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Obtain exclusive ownership of the mutex "my_mutex".
   If the mutex "my_mutex" is not available, suspend until it
   becomes available. */
status =  tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1042">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1042">See Also</span></span>

- <span data-ttu-id="bdbe0-1043">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1043">tx_mutex_create</span></span>
- <span data-ttu-id="bdbe0-1044">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1044">tx_mutex_delete</span></span>
- <span data-ttu-id="bdbe0-1045">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1045">tx_mutex_info_get</span></span>
- <span data-ttu-id="bdbe0-1046">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1046">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1047">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1047">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1048">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1048">tx_mutex_prioritize</span></span>
- <span data-ttu-id="bdbe0-1049">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1049">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="bdbe0-1050">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1050">tx_mutex_info_get</span></span>

<span data-ttu-id="bdbe0-1051">Recupera información acerca de una exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1051">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1052">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1052">Prototype</span></span>

```C
UINT tx_mutex_info_get(TX_MUTEX *mutex_ptr, CHAR **name,
                          ULONG *count, TX_THREAD **owner,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count, TX_MUTEX **next_mutex);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1053">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1053">Description</span></span>

<span data-ttu-id="bdbe0-1054">Este servicio recupera información sobre la exclusión mutua especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1054">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1055">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1055">Parameters</span></span>

- <span data-ttu-id="bdbe0-1056">**mutex_ptr**: puntero al bloque de control de una exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1056">**mutex_ptr**: Pointer to mutex control block.</span></span>
- <span data-ttu-id="bdbe0-1057">**name**: puntero al destino del puntero al nombre de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1057">**name**: Pointer to destination for the pointer to the mutex’s name.</span></span>
- <span data-ttu-id="bdbe0-1058">**count**: puntero al destino del recuento de propiedad de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1058">**count**: Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="bdbe0-1059">**owner**: puntero al destino del puntero del subproceso propietario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1059">**owner**: Pointer to destination for the owning thread’s pointer.</span></span>
- <span data-ttu-id="bdbe0-1060">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1060">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="bdbe0-1061">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1061">**suspended_count**: Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="bdbe0-1062">**next_mutex**: puntero al destino del puntero de la siguiente exclusión mutua creada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1062">**next_mutex**: Pointer to destination for the pointer of the next created mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1063">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1063">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1064">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1064">Return Values</span></span>

- <span data-ttu-id="bdbe0-1065">**TX_SUCCESS**: (0x00) información de la exclusión mutua recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1065">**TX_SUCCESS**: (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="bdbe0-1066">TX_MUTEX_ERROR: (0x1C) puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1066">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1067">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1067">Allowed From</span></span>

<span data-ttu-id="bdbe0-1068">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1068">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1069">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1069">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1070">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1070">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1071">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1071">Example</span></span>

```C
TX_MUTEX     my_mutex;
CHAR         *name;
ULONG        count;
TX_THREAD    *owner;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_MUTEX     *next_mutex;
UINT         status;

/* Retrieve information about the previously created
   mutex "my_mutex." */
status =  tx_mutex_info_get(&my_mutex, &name,
                          &count, &owner,
                          &first_suspended, &suspended_count,
                          &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1072">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1072">See Also</span></span>

- <span data-ttu-id="bdbe0-1073">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1073">tx_mutex_create</span></span>
- <span data-ttu-id="bdbe0-1074">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1074">tx_mutex_delete</span></span>
- <span data-ttu-id="bdbe0-1075">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1075">tx_mutex_get</span></span>
- <span data-ttu-id="bdbe0-1076">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1076">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1077">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1077">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1078">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1078">tx_mutex_prioritize</span></span>
- <span data-ttu-id="bdbe0-1079">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1079">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="bdbe0-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1080">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="bdbe0-1081">Obtiene información acerca del rendimiento de una exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1081">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1082">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1082">Prototype</span></span>

```C
UINT tx_mutex_performance_info_get(TX_MUTEX *mutex_ptr, ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts,
       ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1083">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1083">Description</span></span>

<span data-ttu-id="bdbe0-1084">Este servicio recupera información sobre el rendimiento de la exclusión mutua especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1084">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1085">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_MUTEX_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1085">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1086">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1086">Parameters</span></span>

- <span data-ttu-id="bdbe0-1087">**mutex_ptr**: puntero a una exclusión mutua creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1087">**mutex_ptr**: Pointer to previously created mutex.</span></span>
- <span data-ttu-id="bdbe0-1088">**puts**: puntero al destino del número de solicitudes Put realizadas en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1088">**puts**: Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="bdbe0-1089">**gets**: puntero al destino del número de solicitudes Get realizadas en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1089">**gets**: Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="bdbe0-1090">**suspensions**: puntero al destino del número de suspensiones de solicitudes Get de exclusiones mutuas de los subprocesos en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1090">**suspensions**: Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="bdbe0-1091">**timeouts**: puntero al destino del número de tiempos de espera de suspensiones de solicitudes Get de exclusiones mutuas en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1091">**timeouts**: Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="bdbe0-1092">**inversions**: puntero al destino del número de inversiones de prioridad de los subprocesos en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1092">**inversions**: Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="bdbe0-1093">**inheritances**: puntero al destino del número de operaciones de herencia de prioridad de los subprocesos en esta exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1093">**inheritances**: Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1094">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1094">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1095">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1095">Return Values</span></span>

- <span data-ttu-id="bdbe0-1096">**TX_SUCCESS**: (0x00) rendimiento de la exclusión mutua obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1096">**TX_SUCCESS**: (0x00) Successful mutex performance get.</span></span> 
- <span data-ttu-id="bdbe0-1097">**TX_PTR_ERROR**: (0x03) puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1097">**TX_PTR_ERROR**: (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="bdbe0-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1099">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1099">Allowed From</span></span>

<span data-ttu-id="bdbe0-1100">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1100">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1101">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1101">Example</span></span>

```C
TX_MUTEX     my_mutex;
ULONG        puts;
ULONG        gets;
ULONG        suspensions;
ULONG        timeouts;
ULONG        inversions;
ULONG        inheritances;

/* Retrieve performance information on the previously created
   mutex. */
status =  tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
                &suspensions, &timeouts, &inversions,
                &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1102">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1102">See Also</span></span>

- <span data-ttu-id="bdbe0-1103">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1103">tx_mutex_create</span></span>
- <span data-ttu-id="bdbe0-1104">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1104">tx_mutex_delete</span></span>
- <span data-ttu-id="bdbe0-1105">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1105">tx_mutex_get</span></span>
- <span data-ttu-id="bdbe0-1106">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1106">tx_mutex_info_get</span></span>
- <span data-ttu-id="bdbe0-1107">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1107">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1108">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1108">tx_mutex_prioritize</span></span>
- <span data-ttu-id="bdbe0-1109">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1109">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="bdbe0-1110">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1110">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="bdbe0-1111">Obtiene información acerca del rendimiento de las exclusiones mutuas del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1111">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1112">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1112">Prototype</span></span>

```C
UINT  tx_mutex_performance_system_info_get(ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts,
        ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1113">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1113">Description</span></span>

<span data-ttu-id="bdbe0-1114">Este servicio recupera información sobre el rendimiento de todas las exclusiones mutuas del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1114">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1115">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_MUTEX_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1115">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1116">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1116">Parameters</span></span>

- <span data-ttu-id="bdbe0-1117">**puts**: puntero al destino del número total de solicitudes Put realizadas en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1117">**puts**: Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="bdbe0-1118">**gets**: puntero al destino del número total de solicitudes Get realizadas en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1118">**gets**: Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="bdbe0-1119">**suspensions**: puntero al destino del número total de suspensiones de solicitudes Get de exclusiones mutuas de los subprocesos en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1119">**suspensions**: Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="bdbe0-1120">**timeouts**: puntero al destino del número total de tiempos de espera de suspensiones de solicitudes Get de exclusiones mutuas en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1120">**timeouts**: Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="bdbe0-1121">**inversions**: puntero al destino del número total de inversiones de prioridad de los subprocesos en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1121">**inversions**: Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="bdbe0-1122">**inheritances**: puntero al destino del número total de operaciones de herencia de prioridad de los subprocesos en todas las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1122">**inheritances**: Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1123">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1123">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1124">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1124">Return Values</span></span>

- <span data-ttu-id="bdbe0-1125">**TX_SUCCESS**: (0x00) rendimiento de las exclusiones mutuas del sistema obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1125">**TX_SUCCESS**: (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="bdbe0-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1127">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1127">Allowed From</span></span>

<span data-ttu-id="bdbe0-1128">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1128">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1129">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1129">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;
ULONG         inversions;
ULONG         inheritances;

/* Retrieve performance information on all previously created
   mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
                &suspensions, &timeouts,
                &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1130">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1130">See Also</span></span>

- <span data-ttu-id="bdbe0-1131">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1131">tx_mutex_create</span></span>
- <span data-ttu-id="bdbe0-1132">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1132">tx_mutex_delete</span></span>
- <span data-ttu-id="bdbe0-1133">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1133">tx_mutex_get</span></span>
- <span data-ttu-id="bdbe0-1134">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1134">tx_mutex_info_get</span></span>
- <span data-ttu-id="bdbe0-1135">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1135">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1136">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1136">tx_mutex_prioritize</span></span>
- <span data-ttu-id="bdbe0-1137">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1137">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="bdbe0-1138">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1138">tx_mutex_prioritize</span></span>

<span data-ttu-id="bdbe0-1139">Da la prioridad a una exclusión mutua en la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1139">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1140">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1140">Prototype</span></span>

```C
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1141">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1141">Description</span></span>

<span data-ttu-id="bdbe0-1142">Este servicio coloca el subproceso de prioridad más alta suspendido para obtener la propiedad de la exclusión mutua al principio de la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1142">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="bdbe0-1143">Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1143">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1144">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1144">Parameters</span></span> 

- <span data-ttu-id="bdbe0-1145">**mutex_ptr**: puntero a la exclusión mutua creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1145">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1146">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1146">Return Values</span></span>

- <span data-ttu-id="bdbe0-1147">**TX_SUCCESS**: (0x00) prioridad de la exclusión mutua establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1147">**TX_SUCCESS**: (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="bdbe0-1148">TX_MUTEX_ERROR: (0x1C) puntero de la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1148">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1149">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1149">Allowed From</span></span>

<span data-ttu-id="bdbe0-1150">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1150">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1151">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1151">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1152">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1152">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1153">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1153">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Ensure that the highest priority thread will receive
   ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_mutex_put call that releases ownership of the
   mutex will give ownership to this thread and wake it
   up. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1154">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1154">See Also</span></span>

- <span data-ttu-id="bdbe0-1155">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1155">tx_mutex_create</span></span>
- <span data-ttu-id="bdbe0-1156">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1156">tx_mutex_delete</span></span>
- <span data-ttu-id="bdbe0-1157">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1157">tx_mutex_get</span></span>
- <span data-ttu-id="bdbe0-1158">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1158">tx_mutex_info_get</span></span>
- <span data-ttu-id="bdbe0-1159">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1159">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1160">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1160">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1161">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1161">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="bdbe0-1162">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1162">tx_mutex_put</span></span>

<span data-ttu-id="bdbe0-1163">Libera la propiedad de una exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1163">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1164">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1164">Prototype</span></span>

```C
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1165">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1165">Description</span></span>

<span data-ttu-id="bdbe0-1166">Este servicio reduce el recuento de propiedad de la exclusión mutua especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1166">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="bdbe0-1167">Si el recuento de propiedad es cero, la exclusión mutua pasa a estar disponible.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1167">If the ownership count is zero, the mutex is made available.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1168">Si se seleccionó la herencia de prioridad durante la creación de la exclusión mutua, la prioridad del subproceso que la libera se restaurará a la que tenía cuando obtuvo originalmente la propiedad de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1168">If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex.</span></span> <span data-ttu-id="bdbe0-1169">Se puede deshacer cualquier otro cambio de prioridad realizado en el subproceso de liberación mientras tenía la propiedad de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1169">Any other priority changes made to the releasing thread during ownership of the mutex may be undone.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1170">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1170">Parameters</span></span>

- <span data-ttu-id="bdbe0-1171">**mutex_ptr**: puntero a la exclusión mutua creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1171">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1172">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1172">Return Values</span></span>

- <span data-ttu-id="bdbe0-1173">**TX_SUCCESS**: (0x00) exclusión mutua liberada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1173">**TX_SUCCESS**: (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="bdbe0-1174">**TX_NOT_OWNED**: (0x1E) el autor de la llamada no tiene la propiedad de la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1174">**TX_NOT_OWNED**: (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="bdbe0-1175">TX_MUTEX_ERROR: (0x1C) puntero a la exclusión mutua no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1175">TX_MUTEX_ERROR: (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="bdbe0-1176">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1176">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1177">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1177">Allowed From</span></span>

<span data-ttu-id="bdbe0-1178">Inicialización, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1178">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1179">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1179">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1180">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1180">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1181">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1181">Example</span></span>

```C
TX_MUTEX         my_mutex;
UINT             status;
/* Release ownership of "my_mutex." */
status =  tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
   count has been decremented and if zero, released. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1182">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1182">See Also</span></span>

- <span data-ttu-id="bdbe0-1183">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1183">tx_mutex_create</span></span>
- <span data-ttu-id="bdbe0-1184">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1184">tx_mutex_delete</span></span>
- <span data-ttu-id="bdbe0-1185">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1185">tx_mutex_get</span></span>
- <span data-ttu-id="bdbe0-1186">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1186">tx_mutex_info_get</span></span>
- <span data-ttu-id="bdbe0-1187">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1187">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1188">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1188">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1189">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1189">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="bdbe0-1190">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1190">tx_queue_create</span></span>

<span data-ttu-id="bdbe0-1191">Crea una cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1191">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1192">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1192">Prototype</span></span>

```c
UINT tx_queue_create(TX_QUEUE *queue_ptr, CHAR *name_ptr,
                          UINT message_size,
                          VOID *queue_start, ULONG queue_size);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1193">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1193">Description</span></span>

<span data-ttu-id="bdbe0-1194">Este servicio crea una cola de mensajes que se utiliza normalmente para la comunicación entre subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1194">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="bdbe0-1195">El número total de mensajes se calcula a partir del tamaño de mensaje especificado y del número total de bytes de la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1195">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1196">Si el número total de bytes especificado en el área de memoria de la cola no es divisible por el tamaño de mensaje indicado, los bytes restantes del área de memoria quedan sin usar.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1196">If the total number of bytes specified in the queue’s memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1197">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1197">Parameters</span></span>

- <span data-ttu-id="bdbe0-1198">**queue_ptr**: puntero al bloque de control de una cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1198">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="bdbe0-1199">**name_ptr**: puntero al nombre de la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1199">**name_ptr**: Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="bdbe0-1200">**message_size**: especifica el tamaño de cada mensaje de la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1200">**message_size**: Specifies the size of each message in the queue.</span></span> <span data-ttu-id="bdbe0-1201">El tamaño de los mensajes se sitúa entre una palabra de 32 bits y 16 palabras de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1201">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="bdbe0-1202">Las opciones de tamaño de mensaje válidas son valores numéricos entre 1 y 16, ambos incluidos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1202">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="bdbe0-1203">**queue_start**: dirección inicial de la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1203">**queue_start**: Starting address of the message queue.</span></span> <span data-ttu-id="bdbe0-1204">La dirección inicial debe corresponderse con el tamaño del tipo de datos ULONG.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1204">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="bdbe0-1205">**queue_size**: número total de bytes disponibles para la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1205">**queue_size**: Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1206">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1206">Return Values</span></span>

- <span data-ttu-id="bdbe0-1207">**TX_SUCCESS**: (0x00) cola de mensajes creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1207">**TX_SUCCESS**: (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="bdbe0-1208">TX_QUEUE_ERROR: (0x09) puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1208">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="bdbe0-1209">El puntero es NULL o la cola ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1209">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="bdbe0-1210">TX_PTR_ERROR: (0x03) dirección inicial de la cola de mensajes no válida.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1210">TX_PTR_ERROR: (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="bdbe0-1211">TX_SIZE_ERROR: (0x05) el tamaño de la cola de mensajes no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1211">TX_SIZE_ERROR: (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="bdbe0-1212">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1212">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1213">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1213">Allowed From</span></span>

<span data-ttu-id="bdbe0-1214">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1214">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1215">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1215">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1216">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1216">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1217">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1217">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Create a message queue whose total size is 2000 bytes
   starting at address 0x300000. Each message in this
   queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
            4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
   for storing 125 messages (2000 bytes/ 16 bytes per
   message). */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1218">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1218">See Also</span></span>

- <span data-ttu-id="bdbe0-1219">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1219">tx_queue_delete</span></span>
- <span data-ttu-id="bdbe0-1220">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1220">tx_queue_flush</span></span>
- <span data-ttu-id="bdbe0-1221">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1221">tx_queue_front_send</span></span>
- <span data-ttu-id="bdbe0-1222">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1222">tx_queue_info_get</span></span>
- <span data-ttu-id="bdbe0-1223">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1223">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1224">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1224">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1225">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1225">tx_queue_prioritize</span></span>
- <span data-ttu-id="bdbe0-1226">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1226">tx_queue_receive</span></span>
- <span data-ttu-id="bdbe0-1227">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1227">tx_queue_send</span></span>
- <span data-ttu-id="bdbe0-1228">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1228">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="bdbe0-1229">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1229">tx_queue_delete</span></span>

<span data-ttu-id="bdbe0-1230">Elimina una cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1230">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1231">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1231">Prototype</span></span>

```C
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1232">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1232">Description</span></span>

<span data-ttu-id="bdbe0-1233">Este servicio elimina la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1233">This service deletes the specified message queue.</span></span> <span data-ttu-id="bdbe0-1234">Todos los subprocesos suspendidos en espera de un mensaje de esta cola se reanudan y se les asigna un estado de devolución TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1234">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1235">Antes de eliminar la cola, la aplicación debe asegurarse de que se complete (o se deshabilite) cualquier devolución de llamada de notificación de envío de esta cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1235">The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue.</span></span> <span data-ttu-id="bdbe0-1236">Además, debe impedir el uso futuro de una cola eliminada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1236">In addition, the application must prevent any future use of a deleted queue.</span></span>

<span data-ttu-id="bdbe0-1237">*También es responsabilidad de la aplicación administrar el área de memoria asociada a la cola, que está disponible una vez completado este servicio.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1237">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1238">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1238">Parameters</span></span> 

- <span data-ttu-id="bdbe0-1239">**queue_ptr**: puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1239">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1240">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1240">Return Values</span></span>

- <span data-ttu-id="bdbe0-1241">**TX_SUCCESS**: (0x00) cola de mensajes eliminada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1241">**TX_SUCCESS**: (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="bdbe0-1242">TX_QUEUE_ERROR: (0x09) puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1242">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="bdbe0-1243">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1243">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1244">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1244">Allowed From</span></span>

<span data-ttu-id="bdbe0-1245">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1245">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1246">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1246">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1247">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1247">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1248">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1248">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Delete entire message queue. Assume that the queue
   has already been created with a call to
   tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1249">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1249">See Also</span></span>

- <span data-ttu-id="bdbe0-1250">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1250">tx_queue_create</span></span>
- <span data-ttu-id="bdbe0-1251">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1251">tx_queue_flush</span></span>
- <span data-ttu-id="bdbe0-1252">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1252">tx_queue_front_send</span></span>
- <span data-ttu-id="bdbe0-1253">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1253">tx_queue_info_get</span></span>
- <span data-ttu-id="bdbe0-1254">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1254">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1255">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1255">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1256">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1256">tx_queue_prioritize</span></span>
- <span data-ttu-id="bdbe0-1257">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1257">tx_queue_receive</span></span>
- <span data-ttu-id="bdbe0-1258">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1258">tx_queue_send</span></span>
- <span data-ttu-id="bdbe0-1259">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1259">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="bdbe0-1260">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1260">tx_queue_flush</span></span>

<span data-ttu-id="bdbe0-1261">Vacía los mensajes de la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1261">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1262">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1262">Prototype</span></span>

```C
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1263">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1263">Description</span></span>

<span data-ttu-id="bdbe0-1264">Este servicio elimina todos los mensajes almacenados en la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1264">This service deletes all messages stored in the specified message queue.</span></span> <span data-ttu-id="bdbe0-1265">Si la cola se llena, se descartan los mensajes de todos los subprocesos suspendidos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1265">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="bdbe0-1266">Cada subproceso suspendido se reanuda después con un estado de devolución que indica que el mensaje se envió correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1266">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="bdbe0-1267">Si la cola está vacía, este servicio no hace nada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1267">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1268">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1268">Parameters</span></span> 

- <span data-ttu-id="bdbe0-1269">**queue_ptr**: puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1269">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1270">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1270">Return Values</span></span>

- <span data-ttu-id="bdbe0-1271">**TX_SUCCESS**: (0x00) cola de mensajes vaciada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1271">**TX_SUCCESS**: (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="bdbe0-1272">TX_QUEUE_ERROR: (0x09) puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1272">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1273">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1273">Allowed From</span></span>

<span data-ttu-id="bdbe0-1274">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1274">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1275">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1275">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1276">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1276">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1277">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1277">Example</span></span>

```c
TX_QUEUE     my_queue;
UINT         status;

/* Flush out all pending messages in the specified message
   queue. Assume that the queue has already been created
   with a call to tx_queue_create. */
status =  tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
    empty. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1278">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1278">See Also</span></span>

- <span data-ttu-id="bdbe0-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1279">tx_queue_create</span></span>
- <span data-ttu-id="bdbe0-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1280">tx_queue_delete</span></span>
- <span data-ttu-id="bdbe0-1281">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1281">tx_queue_front_send</span></span>
- <span data-ttu-id="bdbe0-1282">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1282">tx_queue_info_get</span></span>
- <span data-ttu-id="bdbe0-1283">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1283">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="bdbe0-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1286">tx_queue_receive</span></span>
- <span data-ttu-id="bdbe0-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1287">tx_queue_send</span></span>
- <span data-ttu-id="bdbe0-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="bdbe0-1289">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1289">tx_queue_front_send</span></span>

<span data-ttu-id="bdbe0-1290">Envía un mensaje al principio de la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1290">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1291">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1291">Prototype</span></span>

```C
UINT tx_queue_front_send(TX_QUEUE *queue_ptr,
                           VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1292">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1292">Description</span></span>

<span data-ttu-id="bdbe0-1293">Este servicio envía un mensaje al principio de la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1293">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="bdbe0-1294">El mensaje se **copia** al principio de la cola desde el área de memoria especificada por el puntero de origen.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1294">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1295">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1295">Parameters</span></span>

- <span data-ttu-id="bdbe0-1296">**queue_ptr**: puntero al bloque de control de una cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1296">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="bdbe0-1297">**source_ptr**: puntero al mensaje.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1297">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="bdbe0-1298">**wait_option**: define el comportamiento del servicio si la cola de mensajes está llena.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1298">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="bdbe0-1299">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1299">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bdbe0-1300">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1300">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="bdbe0-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="bdbe0-1302">valor de tiempo de espera: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1302">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="bdbe0-1303">Cuando se selecciona TX_NO_WAIT, se produce una devolución inmediata desde este servicio, con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1303">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="bdbe0-1304">*Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1304">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="bdbe0-1305">Cuando se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya espacio en la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1305">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="bdbe0-1306">Cuando se selecciona un valor numérico (de 1 a 0xFFFFFFFE), se está especificando el número máximo de tics del temporizador que el subproceso permanecerá suspendido mientras espera a que haya espacio en la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1306">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1307">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1307">Return Values</span></span>

- <span data-ttu-id="bdbe0-1308">**TX_SUCCESS**: (0x00) mensaje enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1308">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="bdbe0-1309">**TX_DELETED**: (0x01) la cola de mensajes se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1309">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="bdbe0-1310">**TX_QUEUE_FULL**: (0x0B) el servicio no pudo enviar el mensaje porque la cola estaba llena durante el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1310">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="bdbe0-1311">**TX_WAIT_ABORTED**: (0x1A) otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1311">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="bdbe0-1312">TX_QUEUE_ERROR: (0x09) puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1312">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="bdbe0-1313">TX_PTR_ERROR: (0x03) puntero de origen no válido para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1313">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="bdbe0-1314">TX_WAIT_ERROR: (0x04) se especificó una opción de espera distinta de TX_NO_WAIT en una llamada desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1314">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1315">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1315">Allowed From</span></span>

<span data-ttu-id="bdbe0-1316">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1316">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1317">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1317">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1318">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1318">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1319">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1319">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG        my_message[4];

/* Send a message to the front of "my_queue." Return
   immediately, regardless of success. This wait
   option is used for calls from initialization, timers,
   and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
            TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
   of the specified queue. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1320">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1320">See Also</span></span>

- <span data-ttu-id="bdbe0-1321">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1321">tx_queue_create</span></span>
- <span data-ttu-id="bdbe0-1322">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1322">tx_queue_delete</span></span>
- <span data-ttu-id="bdbe0-1323">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1323">tx_queue_flush</span></span>
- <span data-ttu-id="bdbe0-1324">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1324">tx_queue_info_get</span></span>
- <span data-ttu-id="bdbe0-1325">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1325">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1326">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1326">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1327">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1327">tx_queue_prioritize</span></span>
- <span data-ttu-id="bdbe0-1328">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1328">tx_queue_receive</span></span>
- <span data-ttu-id="bdbe0-1329">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1329">tx_queue_send</span></span>
- <span data-ttu-id="bdbe0-1330">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1330">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="bdbe0-1331">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1331">tx_queue_info_get</span></span>

<span data-ttu-id="bdbe0-1332">Recupera información acerca de una cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1332">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1333">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1333">Prototype</span></span>

```C
UINT tx_queue_info_get(TX_QUEUE *queue_ptr, CHAR **name,
        ULONG *enqueued, ULONG *available_storage
        TX_THREAD **first_suspended, ULONG *suspended_count,
        TX_QUEUE **next_queue);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1334">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1334">Description</span></span>

<span data-ttu-id="bdbe0-1335">Este servicio recupera información sobre la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1335">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1336">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1336">Parameters</span></span>

- <span data-ttu-id="bdbe0-1337">**queue_ptr**: puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1337">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="bdbe0-1338">**name**: puntero al destino del puntero al nombre de la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1338">**name**: Pointer to destination for the pointer to the queue’s name.</span></span>
- <span data-ttu-id="bdbe0-1339">**enqueued**: puntero al destino del número de mensajes que hay actualmente en la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1339">**enqueued**: Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="bdbe0-1340">**available_storage**: puntero al destino del número de mensajes para los que actualmente hay espacio en la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1340">**available_storage**: Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="bdbe0-1341">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de esta cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1341">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="bdbe0-1342">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en esta cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1342">**suspended_count**: Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="bdbe0-1343">**next_queue**: puntero al destino del puntero de la siguiente cola creada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1343">**next_queue**: Pointer to destination for the pointer of the next created queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1344">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1344">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1345">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1345">Return Values</span></span>

- <span data-ttu-id="bdbe0-1346">**TX_SUCCESS**: (0x00) información de la cola obtenida correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1346">**TX_SUCCESS**: (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="bdbe0-1347">TX_QUEUE_ERROR: (0x09) puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1347">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1348">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1348">Allowed From</span></span>

<span data-ttu-id="bdbe0-1349">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1349">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1350">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1350">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1351">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1352">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1352">Example</span></span>

```C
TX_QUEUE     my_queue;
CHAR         *name;
ULONG        enqueued;
ULONG        available_storage;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_QUEUE     *next_queue;
UINT         status;

/* Retrieve information about the previously created
   message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
            &enqueued, &available_storage,
            &first_suspended, &suspended_count,
            &next_queue);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1353">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1353">See Also</span></span>

- <span data-ttu-id="bdbe0-1354">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1354">tx_queue_create</span></span>
- <span data-ttu-id="bdbe0-1355">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1355">tx_queue_delete</span></span>
- <span data-ttu-id="bdbe0-1356">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1356">tx_queue_flush</span></span>
- <span data-ttu-id="bdbe0-1357">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1357">tx_queue_front_send</span></span>
- <span data-ttu-id="bdbe0-1358">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1358">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1359">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1359">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1360">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1360">tx_queue_prioritize</span></span>
- <span data-ttu-id="bdbe0-1361">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1361">tx_queue_receive</span></span>
- <span data-ttu-id="bdbe0-1362">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1362">tx_queue_send</span></span>
- <span data-ttu-id="bdbe0-1363">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1363">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="bdbe0-1364">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1364">tx_queue_performance_info_get</span></span>

<span data-ttu-id="bdbe0-1365">Obtiene información acerca del rendimiento de una cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1365">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1366">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1366">Prototype</span></span>

```C
UINT  tx_queue_performance_info_get(TX_QUEUE *queue_ptr,
        ULONG *messages_sent, ULONG *messages_received,
        ULONG *empty_suspensions, ULONG *full_suspensions,
        ULONG *full_errors, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1367">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1367">Description</span></span>

<span data-ttu-id="bdbe0-1368">Este servicio recupera información sobre el rendimiento de la cola especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1368">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1369">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_QUEUE_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1369">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1370">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1370">Parameters</span></span>

- <span data-ttu-id="bdbe0-1371">**queue_ptr**: puntero a una cola creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1371">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="bdbe0-1372">**messages_sent**: puntero al destino del número de solicitudes de envío realizadas en esta cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1372">**messages_sent**: Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="bdbe0-1373">**messages_received**: puntero al destino del número de solicitudes de recepción realizadas en esta cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1373">**messages_received**: Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="bdbe0-1374">**empty_suspensions**: puntero al destino del número de suspensiones de cola vacías en esta cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1374">**empty_suspensions**: Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="bdbe0-1375">**full_suspensions**: puntero al destino del número de suspensiones de cola llena en esta cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1375">**full_suspensions**: Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="bdbe0-1376">**full_errors**: puntero al destino del número de errores de cola llena en esta cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1376">**full_errors**: Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="bdbe0-1377">**timeouts**: puntero al destino del número de tiempos de espera de suspensión de los subprocesos en esta cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1377">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1378">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1378">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1379">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1379">Return Values</span></span>

- <span data-ttu-id="bdbe0-1380">**TX_SUCCESS**: (0x00) rendimiento de la cola obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1380">**TX_SUCCESS**: (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="bdbe0-1381">**TX_PTR_ERROR**: (0x03) puntero de la cola no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1381">**TX_PTR_ERROR**: (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="bdbe0-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1383">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1383">Allowed From</span></span>

<span data-ttu-id="bdbe0-1384">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1384">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1385">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1385">Example</span></span>

```C
TX_QUEUE     my_queue;
ULONG        messages_sent;
ULONG        messages_received;
ULONG        empty_suspensions;
ULONG        full_suspensions;
ULONG        full_errors;
ULONG        timeouts;

/* Retrieve performance information on the previously created
   queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1386">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1386">See Also</span></span>

- <span data-ttu-id="bdbe0-1387">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1387">tx_queue_create</span></span>
- <span data-ttu-id="bdbe0-1388">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1388">tx_queue_delete</span></span>
- <span data-ttu-id="bdbe0-1389">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1389">tx_queue_flush</span></span>
- <span data-ttu-id="bdbe0-1390">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1390">tx_queue_front_send</span></span>
- <span data-ttu-id="bdbe0-1391">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1391">tx_queue_info_get</span></span>
- <span data-ttu-id="bdbe0-1392">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1392">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1393">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1393">tx_queue_prioritize</span></span>
- <span data-ttu-id="bdbe0-1394">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1394">tx_queue_receive</span></span>
- <span data-ttu-id="bdbe0-1395">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1395">tx_queue_send</span></span>
- <span data-ttu-id="bdbe0-1396">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1396">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="bdbe0-1397">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1397">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="bdbe0-1398">Obtiene información acerca del rendimiento de las colas del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1398">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1399">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1399">Prototype</span></span>

```C
UINT  tx_queue_performance_system_info_get(ULONG *messages_sent,
        ULONG *messages_received, ULONG *empty_suspensions,
        ULONG *full_suspensions, ULONG *full_errors,
        ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1400">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1400">Description</span></span>

<span data-ttu-id="bdbe0-1401">Este servicio recupera información sobre el rendimiento de todas las colas del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1401">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1402">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_QUEUE_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1402">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1403">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1403">Parameters</span></span>

- <span data-ttu-id="bdbe0-1404">**messages_sent**: puntero al destino del número total de solicitudes de envío realizadas en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1404">**messages_sent**: Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="bdbe0-1405">**messages_received**: puntero al destino del número total de solicitudes de recepción realizadas en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1405">**messages_received**: Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="bdbe0-1406">**empty_suspensions**: puntero al destino del número total de suspensiones de cola vacías en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1406">**empty_suspensions**: Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="bdbe0-1407">**full_suspensions**: puntero al destino del número total de suspensiones de cola llena en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1407">**full_suspensions**: Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="bdbe0-1408">**full_errors**: puntero al destino del número total de errores de cola llena en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1408">**full_errors**: Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="bdbe0-1409">**timeouts**: puntero al destino del número total de tiempos de espera de suspensión de los subprocesos en todas las colas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1409">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1410">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1410">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1411">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1411">Return Values</span></span>

- <span data-ttu-id="bdbe0-1412">**TX_SUCCESS**: (0x00) rendimiento de las colas del sistema obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1412">**TX_SUCCESS**: (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="bdbe0-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1414">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1414">Allowed From</span></span>

<span data-ttu-id="bdbe0-1415">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1415">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1416">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1416">Example</span></span>

```c
ULONG         messages_sent;
ULONG         messages_received;
ULONG         empty_suspensions;
ULONG         full_suspensions;
ULONG         full_errors;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1417">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1417">See Also</span></span>

- <span data-ttu-id="bdbe0-1418">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1418">tx_queue_create</span></span>
- <span data-ttu-id="bdbe0-1419">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1419">tx_queue_delete</span></span>
- <span data-ttu-id="bdbe0-1420">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1420">tx_queue_flush</span></span>
- <span data-ttu-id="bdbe0-1421">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1421">tx_queue_front_send</span></span>
- <span data-ttu-id="bdbe0-1422">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1422">tx_queue_info_get</span></span>
- <span data-ttu-id="bdbe0-1423">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1423">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1424">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1424">tx_queue_prioritize</span></span>
- <span data-ttu-id="bdbe0-1425">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1425">tx_queue_receive</span></span>
- <span data-ttu-id="bdbe0-1426">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1426">tx_queue_send</span></span>
- <span data-ttu-id="bdbe0-1427">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1427">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="bdbe0-1428">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1428">tx_queue_prioritize</span></span>

<span data-ttu-id="bdbe0-1429">Da prioridad a una cola en la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1429">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1430">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1430">Prototype</span></span>

```C
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="bdbe0-1431">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1431">Description</span></span>

<span data-ttu-id="bdbe0-1432">Este servicio coloca el subproceso de prioridad más alta suspendido de un mensaje (o para colocar un mensaje) de esta cola al principio de la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1432">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span> <span data-ttu-id="bdbe0-1433">Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1433">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1434">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1434">Parameters</span></span> 

- <span data-ttu-id="bdbe0-1435">**queue_ptr**: puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1435">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1436">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1436">Return Values</span></span>

- <span data-ttu-id="bdbe0-1437">**TX_SUCCESS**: (0x00) prioridad de la cola establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1437">**TX_SUCCESS**: (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="bdbe0-1438">TX_QUEUE_ERROR: (0x09) puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1438">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1439">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1439">Allowed From</span></span>

<span data-ttu-id="bdbe0-1440">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1440">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1441">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1441">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1442">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1442">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1443">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1443">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_queue_send or tx_queue_front_send call made
   to this queue will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1444">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1444">See Also</span></span>

- <span data-ttu-id="bdbe0-1445">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1445">tx_queue_create</span></span>
- <span data-ttu-id="bdbe0-1446">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1446">tx_queue_delete</span></span>
- <span data-ttu-id="bdbe0-1447">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1447">tx_queue_flush</span></span>
- <span data-ttu-id="bdbe0-1448">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1448">tx_queue_front_send</span></span>
- <span data-ttu-id="bdbe0-1449">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1449">tx_queue_info_get</span></span>
- <span data-ttu-id="bdbe0-1450">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1450">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1451">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1451">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1452">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1452">tx_queue_receive</span></span>
- <span data-ttu-id="bdbe0-1453">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1453">tx_queue_send</span></span>
- <span data-ttu-id="bdbe0-1454">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1454">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="bdbe0-1455">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1455">tx_queue_receive</span></span>

<span data-ttu-id="bdbe0-1456">Obtiene un mensaje de la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1456">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1457">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1457">Prototype</span></span>

```C
UINT tx_queue_receive(TX_QUEUE *queue_ptr,
                          VOID *destination_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1458">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1458">Description</span></span>

<span data-ttu-id="bdbe0-1459">Este servicio recupera un mensaje de la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1459">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="bdbe0-1460">El mensaje recuperado se **copia** de la cola en el área de memoria especificada por el puntero de destino.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1460">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="bdbe0-1461">A continuación, ese mensaje se quita de la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1461">That message is then removed from the queue.</span></span>

> [!WARNING]
> <span data-ttu-id="bdbe0-1462">El área de memoria de destino especificada debe ser lo suficientemente grande como para contener el mensaje; es decir, el destino del mensaje al que apunta **destination_ptr** debe tener al menos el mismo tamaño que el valor de tamaño de mensaje de esta cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1462">The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by **destination_ptr** must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="bdbe0-1463">De lo contrario, si el destino no es lo suficientemente grande, se producen daños en la siguiente área de memoria.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1463">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1464">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1464">Parameters</span></span>

- <span data-ttu-id="bdbe0-1465">**queue_ptr**: puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1465">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="bdbe0-1466">**destination_ptr**: ubicación donde se copiará el mensaje.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1466">**destination_ptr**: Location of where to copy the message.</span></span>
- <span data-ttu-id="bdbe0-1467">**wait_option**: define el comportamiento del servicio si la cola de mensajes está vacía.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1467">**wait_option**: Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="bdbe0-1468">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1468">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bdbe0-1469">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1469">**TX_NO_WAIT**: (0x00000000)</span></span> 
    - <span data-ttu-id="bdbe0-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span> 
    - <span data-ttu-id="bdbe0-1471">valor de tiempo de espera: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1471">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="bdbe0-1472">Cuando se selecciona TX_NO_WAIT, se produce una devolución inmediata desde este servicio, con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1472">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="bdbe0-1473">Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1473">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="bdbe0-1474">Cuando se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya un mensaje disponible.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1474">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>

    <span data-ttu-id="bdbe0-1475">Cuando se selecciona un valor numérico (de 1 a 0xFFFFFFFE), se está especificando el número máximo de tics del temporizador que el subproceso permanecerá suspendido mientras espera por un mensaje.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1475">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1476">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1476">Return Values</span></span>

- <span data-ttu-id="bdbe0-1477">**TX_SUCCESS**: (0x00) mensaje recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1477">**TX_SUCCESS**: (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="bdbe0-1478">**TX_DELETED**: (0x01) la cola de mensajes se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1478">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="bdbe0-1479">**TX_QUEUE_EMPTY**: (0x0A) el servicio no pudo recuperar un mensaje porque la cola estaba vacía durante el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1479">**TX_QUEUE_EMPTY**: (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="bdbe0-1480">**TX_WAIT_ABORTED**: (0x1A) otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1480">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="bdbe0-1481">TX_QUEUE_ERROR: (0x09) puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1481">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="bdbe0-1482">TX_PTR_ERROR: (0x03) puntero de destino no válido para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1482">TX_PTR_ERROR: (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="bdbe0-1483">TX_WAIT_ERROR: (0x04) se especificó una opción de espera distinta de TX_NO_WAIT en una llamada desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1483">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1484">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1484">Allowed From</span></span>

<span data-ttu-id="bdbe0-1485">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1485">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1486">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1486">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1487">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1487">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1488">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1488">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
   empty, suspend until a message is present. Note that
   this suspension is only possible from application
   threads. */
status =  tx_queue_receive(&my_queue, my_message,
                          TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
   "my_message." */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1489">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1489">See Also</span></span>

- <span data-ttu-id="bdbe0-1490">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1490">tx_queue_create</span></span>
- <span data-ttu-id="bdbe0-1491">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1491">tx_queue_delete</span></span>
- <span data-ttu-id="bdbe0-1492">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1492">tx_queue_flush</span></span>
- <span data-ttu-id="bdbe0-1493">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1493">tx_queue_front_send</span></span>
- <span data-ttu-id="bdbe0-1494">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1494">tx_queue_info_get</span></span>
- <span data-ttu-id="bdbe0-1495">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1495">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1496">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1496">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1497">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1497">tx_queue_prioritize</span></span>
- <span data-ttu-id="bdbe0-1498">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1498">tx_queue_send</span></span>
- <span data-ttu-id="bdbe0-1499">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1499">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="bdbe0-1500">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1500">tx_queue_send</span></span>

<span data-ttu-id="bdbe0-1501">Envía un mensaje a la cola de mensajes.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1501">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1502">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1502">Prototype</span></span>

```C
UINT tx_queue_send(TX_QUEUE *queue_ptr,
                          VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1503">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1503">Description</span></span>

<span data-ttu-id="bdbe0-1504">Este servicio envía un mensaje a la cola de mensajes especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1504">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="bdbe0-1505">El mensaje enviado se **copia** en la cola desde el área de memoria especificada por el puntero de origen.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1505">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1506">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1506">Parameters</span></span>

- <span data-ttu-id="bdbe0-1507">**queue_ptr**: puntero a una cola de mensajes creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1507">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="bdbe0-1508">**source_ptr**: puntero al mensaje.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1508">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="bdbe0-1509">**wait_option**: define el comportamiento del servicio si la cola de mensajes está llena.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1509">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="bdbe0-1510">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1510">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bdbe0-1511">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1511">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="bdbe0-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="bdbe0-1513">valor de tiempo de espera: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1513">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="bdbe0-1514">Cuando se selecciona TX_NO_WAIT, se produce una devolución inmediata desde este servicio, con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1514">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="bdbe0-1515">*Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1515">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="bdbe0-1516">Cuando se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya espacio en la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1516">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="bdbe0-1517">Cuando se selecciona un valor numérico (de 1 a 0xFFFFFFFE), se está especificando el número máximo de tics del temporizador que el subproceso permanecerá suspendido mientras espera a que haya espacio en la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1517">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1518">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1518">Return Values</span></span>

- <span data-ttu-id="bdbe0-1519">**TX_SUCCESS**: (0x00) mensaje enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1519">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="bdbe0-1520">**TX_DELETED**: (0x01) la cola de mensajes se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1520">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="bdbe0-1521">**TX_QUEUE_FULL**: (0x0B) el servicio no pudo enviar el mensaje porque la cola estaba llena durante el tiempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1521">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="bdbe0-1522">**TX_WAIT_ABORTED**: (0x1A) otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1522">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="bdbe0-1523">TX_QUEUE_ERROR: (0x09) puntero de la cola de mensajes no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1523">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="bdbe0-1524">TX_PTR_ERROR: (0x03) puntero de origen no válido para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1524">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="bdbe0-1525">TX_WAIT_ERROR: (0x04) se especificó una opción de espera distinta de TX_NO_WAIT en una llamada desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1525">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1526">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1526">Allowed From</span></span>

<span data-ttu-id="bdbe0-1527">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1527">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1528">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1528">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1529">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1530">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1530">Example</span></span>

```C
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
   regardless of success. This wait option is used for
   calls from initialization, timers, and ISRs. */
status =  tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
   queue. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1531">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1531">See Also</span></span>

- <span data-ttu-id="bdbe0-1532">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1532">tx_queue_create</span></span>
- <span data-ttu-id="bdbe0-1533">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1533">tx_queue_delete</span></span>
- <span data-ttu-id="bdbe0-1534">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1534">tx_queue_flush</span></span>
- <span data-ttu-id="bdbe0-1535">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1535">tx_queue_front_send</span></span>
- <span data-ttu-id="bdbe0-1536">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1536">tx_queue_info_get</span></span>
- <span data-ttu-id="bdbe0-1537">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1537">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1538">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1538">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1539">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1539">tx_queue_prioritize</span></span>
- <span data-ttu-id="bdbe0-1540">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1540">tx_queue_receive</span></span>
- <span data-ttu-id="bdbe0-1541">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1541">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="bdbe0-1542">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1542">tx_queue_send_notify</span></span> 

<span data-ttu-id="bdbe0-1543">Notifica a la aplicación cuando se envía un mensaje a la cola.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1543">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1544">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1544">Prototype</span></span>

```C
UINT  tx_queue_send_notify(TX_QUEUE *queue_ptr,
        VOID (*queue_send_notify)(TX_QUEUE *));
```
### <a name="description"></a><span data-ttu-id="bdbe0-1545">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1545">Description</span></span>

<span data-ttu-id="bdbe0-1546">Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se envía un mensaje a la cola especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1546">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="bdbe0-1547">La aplicación define el procesamiento de la devolución de llamada de notificación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1547">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="bdbe0-1548">La devolución de llamada de notificación de envío a la cola de la aplicación no puede llamar a ninguna API de ThreadX SMP con una opción de suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1548">The application’s queue send notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1549">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1549">Parameters</span></span> 

- <span data-ttu-id="bdbe0-1550">**queue_ptr**: puntero a una cola creada previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1550">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="bdbe0-1551">**queue_send_notify**: puntero a la función de notificación de envío a la cola de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1551">**queue_send_notify**: Pointer to application’s queue send notification function.</span></span> <span data-ttu-id="bdbe0-1552">Si este valor es TX_NULL, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1552">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1553">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1553">Return Values</span></span>

- <span data-ttu-id="bdbe0-1554">**TX_SUCCESS**: (0x00) notificación de envío a la cola registrada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1554">**TX_SUCCESS**: (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="bdbe0-1555">TX_QUEUE_ERROR: (0x09) puntero de cola no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1555">TX_QUEUE_ERROR: (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="bdbe0-1556">TX_FEATURE_NOT_ENABLED: (0xFF) el sistema se compiló con las funcionalidades de notificación deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1556">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1557">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1557">Allowed From</span></span>

<span data-ttu-id="bdbe0-1558">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1558">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1559">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1559">Example</span></span>

```C
TX_QUEUE         my_queue;

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
### <a name="see-also"></a><span data-ttu-id="bdbe0-1560">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1560">See Also</span></span>

- <span data-ttu-id="bdbe0-1561">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1561">tx_queue_create</span></span>
- <span data-ttu-id="bdbe0-1562">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1562">tx_queue_delete</span></span>
- <span data-ttu-id="bdbe0-1563">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1563">tx_queue_flush</span></span>
- <span data-ttu-id="bdbe0-1564">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1564">tx_queue_front_send</span></span>
- <span data-ttu-id="bdbe0-1565">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1565">tx_queue_info_get</span></span>
- <span data-ttu-id="bdbe0-1566">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1566">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1567">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1567">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1568">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1568">tx_queue_prioritize</span></span>
- <span data-ttu-id="bdbe0-1569">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1569">tx_queue_receive</span></span>
- <span data-ttu-id="bdbe0-1570">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1570">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="bdbe0-1571">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1571">tx_semaphore_ceiling_put</span></span> 

<span data-ttu-id="bdbe0-1572">Coloca una instancia en un semáforo de recuento con límite superior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1572">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1573">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1573">Prototype</span></span>

```C
UINT  tx_semaphore_ceiling_put(TX_SEMAPHORE *semaphore_ptr,
        ULONG ceiling);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1574">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1574">Description</span></span>

<span data-ttu-id="bdbe0-1575">Este servicio coloca una instancia en el semáforo de recuento especificado, lo que en realidad incrementa el semáforo de recuento en uno.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1575">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="bdbe0-1576">Si el valor actual del semáforo de recuento es mayor o igual que el límite superior especificado, la instancia no se colocará y se devolverá un error TX_CEILING_EXCEEDED.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1576">If the counting semaphore’s current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1577">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1577">Parameters</span></span> 

- <span data-ttu-id="bdbe0-1578">**semaphore_ptr**: puntero a un semáforo creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1578">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="bdbe0-1579">**ceiling**: límite máximo permitido para el semáforo (el rango de valores válidos se sitúa entre 1 y 0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1579">**ceiling**: Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1580">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1580">Return Values</span></span>

- <span data-ttu-id="bdbe0-1581">**TX_SUCCESS**: (0x00) colocación correcta en el semáforo con límite superior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1581">**TX_SUCCESS**: (0x00) Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="bdbe0-1582">**TX_CEILING_EXCEEDED**: (0x21) la solicitud Put supera el límite superior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1582">**TX_CEILING_EXCEEDED**: (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="bdbe0-1583">TX_INVALID_CEILING: (0x22) se proporcionó un valor no válido de cero para el límite superior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1583">TX_INVALID_CEILING: (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="bdbe0-1584">TX_SEMAPHORE_ERROR: (0x0C) puntero del semáforo no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1584">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1585">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1585">Allowed From</span></span>

<span data-ttu-id="bdbe0-1586">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1586">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1587">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1587">Example</span></span>

```c
TX_SEMAPHORE     my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
   that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1588">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1588">See Also</span></span>

- <span data-ttu-id="bdbe0-1589">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1589">tx_semaphore_create</span></span>
- <span data-ttu-id="bdbe0-1590">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1590">tx_semaphore_delete</span></span>
- <span data-ttu-id="bdbe0-1591">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1591">tx_semaphore_get</span></span>
- <span data-ttu-id="bdbe0-1592">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1592">tx_semaphore_info_get</span></span>
- <span data-ttu-id="bdbe0-1593">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1593">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1594">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1594">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1595">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1595">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="bdbe0-1596">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1596">tx_semaphore_put</span></span>
- <span data-ttu-id="bdbe0-1597">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1597">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="bdbe0-1598">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1598">tx_semaphore_create</span></span>

<span data-ttu-id="bdbe0-1599">Crea un semáforo de recuento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1599">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1600">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1600">Prototype</span></span>

```C
UINT tx_semaphore_create(TX_SEMAPHORE *semaphore_ptr,
                           CHAR *name_ptr, ULONG initial_count);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1601">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1601">Description</span></span>

<span data-ttu-id="bdbe0-1602">Este servicio crea un semáforo de recuento para la sincronización entre subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1602">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="bdbe0-1603">Se especifica como parámetro de entrada el recuento inicial del semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1603">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1604">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1604">Parameters</span></span> 

- <span data-ttu-id="bdbe0-1605">**semaphore_ptr**: puntero al bloque de control de un semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1605">**semaphore_ptr**: Pointer to a semaphore control block.</span></span> 
- <span data-ttu-id="bdbe0-1606">**name_ptr**: puntero al nombre del semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1606">**name_ptr**: Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="bdbe0-1607">**initial_count**: especifica el recuento inicial de este semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1607">**initial_count**: Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="bdbe0-1608">Los valores válidos se sitúan entre 0x00000000 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1608">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1609">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1609">Return Values</span></span>

- <span data-ttu-id="bdbe0-1610">**TX_SUCCESS**: (0x00) semáforo creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1610">**TX_SUCCESS**: (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="bdbe0-1611">TX_SEMAPHORE_ERROR: (0x0C) puntero del semáforo no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1611">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="bdbe0-1612">El puntero es NULL o el semáforo ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1612">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="bdbe0-1613">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1613">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1614">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1614">Allowed From</span></span>

<span data-ttu-id="bdbe0-1615">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1615">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1616">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1616">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1617">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1617">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1618">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1618">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Create a counting semaphore whose initial value is 1.
   This is typically the technique used to make a binary
   semaphore. Binary semaphores are used to provide
   protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
            "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1619">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1619">See Also</span></span>

- <span data-ttu-id="bdbe0-1620">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1620">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="bdbe0-1621">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1621">tx_semaphore_delete</span></span>
- <span data-ttu-id="bdbe0-1622">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1622">tx_semaphore_get</span></span>
- <span data-ttu-id="bdbe0-1623">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1623">tx_semaphore_info_get</span></span>
- <span data-ttu-id="bdbe0-1624">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1624">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1625">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1625">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1626">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1626">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="bdbe0-1627">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1627">tx_semaphore_put</span></span>
- <span data-ttu-id="bdbe0-1628">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1628">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="bdbe0-1629">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1629">tx_semaphore_delete</span></span>

<span data-ttu-id="bdbe0-1630">Elimina un semáforo de recuento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1630">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1631">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1631">Prototype</span></span>

```C
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1632">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1632">Description</span></span>

<span data-ttu-id="bdbe0-1633">Este servicio elimina el semáforo de recuento especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1633">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="bdbe0-1634">Todos los subprocesos suspendidos en espera de una instancia del semáforo se reanudan y se les asigna un estado de devolución TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1634">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1635">Antes de eliminar el semáforo, la aplicación debe asegurarse de que se complete (o se deshabilite) cualquier devolución de llamada de notificación de colocación de este semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1635">The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore.</span></span> <span data-ttu-id="bdbe0-1636">Además, debe impedir el uso futuro de un semáforo eliminado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1636">In addition, the application must prevent all future use of a deleted semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1637">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1637">Parameters</span></span> 

- <span data-ttu-id="bdbe0-1638">**semaphore_ptr**: puntero a un semáforo creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1638">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1639">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1639">Return Values</span></span>

- <span data-ttu-id="bdbe0-1640">**TX_SUCCESS**: (0x00) semáforo de recuento eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1640">**TX_SUCCESS**: (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="bdbe0-1641">TX_SEMAPHORE_ERROR: (0x0C) puntero del semáforo de recuento no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1641">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="bdbe0-1642">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1642">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1643">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1643">Allowed From</span></span>

<span data-ttu-id="bdbe0-1644">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1644">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1645">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1645">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1646">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1646">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1647">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1647">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Delete counting semaphore. Assume that the counting
   semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1648">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1648">See Also</span></span>

- <span data-ttu-id="bdbe0-1649">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1649">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="bdbe0-1650">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1650">tx_semaphore_create</span></span>
- <span data-ttu-id="bdbe0-1651">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1651">tx_semaphore_get</span></span>
- <span data-ttu-id="bdbe0-1652">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1652">tx_semaphore_info_get</span></span>
- <span data-ttu-id="bdbe0-1653">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1653">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1654">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1654">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1655">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1655">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="bdbe0-1656">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1656">tx_semaphore_put</span></span>
- <span data-ttu-id="bdbe0-1657">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1657">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="bdbe0-1658">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1658">tx_semaphore_get</span></span>

<span data-ttu-id="bdbe0-1659">Obtiene una instancia del semáforo de recuento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1659">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1660">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1660">Prototype</span></span>

```C
UINT tx_semaphore_get(TX_SEMAPHORE *semaphore_ptr,
                          ULONG wait_option)
```
### <a name="description"></a><span data-ttu-id="bdbe0-1661">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1661">Description</span></span>

<span data-ttu-id="bdbe0-1662">Este servicio recupera una instancia (un solo recuento) del semáforo de recuento especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1662">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="bdbe0-1663">Como resultado, el recuento del semáforo especificado se reduce en uno.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1663">As a result, the specified semaphore’s count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1664">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1664">Parameters</span></span>

- <span data-ttu-id="bdbe0-1665">**semaphore_ptr**: puntero a un semáforo de recuento creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1665">**semaphore_ptr**: Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="bdbe0-1666">**wait_option**: define el comportamiento del servicio si no hay ninguna instancia del semáforo disponible; es decir, si el recuento del semáforo es cero.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1666">**wait_option**: Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="bdbe0-1667">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1667">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bdbe0-1668">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1668">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="bdbe0-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="bdbe0-1670">valor de tiempo de espera: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1670">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="bdbe0-1671">Cuando se selecciona TX_NO_WAIT, se produce una devolución inmediata desde este servicio, con independencia de si se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1671">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="bdbe0-1672">*Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.*</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1672">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="bdbe0-1673">Cuando se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya una instancia del semáforo disponible.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1673">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span> 

    <span data-ttu-id="bdbe0-1674">Cuando se selecciona un valor numérico (de 1 a 0xFFFFFFFE), se está especificando el número máximo de tics del temporizador que el subproceso permanecerá suspendido mientras espera por una instancia del semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1674">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1675">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1675">Return Values</span></span>

- <span data-ttu-id="bdbe0-1676">**TX_SUCCESS**: (0x00) instancia del semáforo recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1676">**TX_SUCCESS**: (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="bdbe0-1677">**TX_DELETED**: (0x01) el semáforo de recuento se eliminó mientras el subproceso estaba suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1677">**TX_DELETED**: (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="bdbe0-1678">**TX_NO_INSTANCE**: (0x0D) el servicio no pudo recuperar una instancia del semáforo de recuento (el recuento del semáforo es cero en el tiempo de espera especificado).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1678">**TX_NO_INSTANCE**: (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="bdbe0-1679">**TX_WAIT_ABORTED**: (0x1A) otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1679">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="bdbe0-1680">TX_SEMAPHORE_ERROR: (0x0C) puntero del semáforo de recuento no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1680">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="bdbe0-1681">TX_WAIT_ERROR: (0x04) se especificó una opción de espera distinta de TX_NO_WAIT en una llamada desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1681">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1682">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1682">Allowed From</span></span>

<span data-ttu-id="bdbe0-1683">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1683">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1684">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1684">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1685">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1685">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1686">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1686">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Get a semaphore instance from the semaphore
   "my_semaphore." If the semaphore count is zero,
   suspend until an instance becomes available.
   Note that this suspension is only possible from
   application threads. */
status =  tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
   an instance of the semaphore. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1687">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1687">See Also</span></span>

- <span data-ttu-id="bdbe0-1688">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1688">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="bdbe0-1689">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1689">tx_semaphore_create</span></span>
- <span data-ttu-id="bdbe0-1690">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1690">tx_semahore_delete</span></span>
- <span data-ttu-id="bdbe0-1691">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1691">tx_semaphore_info_get</span></span>
- <span data-ttu-id="bdbe0-1692">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1692">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1693">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1693">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="bdbe0-1694">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1694">tx_semaphore_put</span></span>
- <span data-ttu-id="bdbe0-1695">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1695">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="bdbe0-1696">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1696">tx_semaphore_info_get</span></span>

<span data-ttu-id="bdbe0-1697">Recupera información acerca de un semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1697">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1698">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1698">Prototype</span></span>

```C
UINT tx_semaphore_info_get(TX_SEMAPHORE *semaphore_ptr,
                          CHAR **name, ULONG *current_value,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_SEMAPHORE **next_semaphore)
```
### <a name="description"></a><span data-ttu-id="bdbe0-1699">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1699">Description</span></span>

<span data-ttu-id="bdbe0-1700">Este servicio recupera información sobre el semáforo especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1700">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1701">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1701">Parameters</span></span>

- <span data-ttu-id="bdbe0-1702">**semaphore_ptr**: puntero al bloque de control de un semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1702">**semaphore_ptr**: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="bdbe0-1703">**name**: puntero al destino del puntero al nombre del semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1703">**name**: Pointer to destination for the pointer to the semaphore’s name.</span></span>
- <span data-ttu-id="bdbe0-1704">**current_value**: puntero al destino del recuento actual del semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1704">**current_value**: Pointer to destination for the current semaphore’s count.</span></span>
- <span data-ttu-id="bdbe0-1705">**first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1705">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="bdbe0-1706">**suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1706">**suspended_count**: Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="bdbe0-1707">**next_semaphore**: puntero al destino del puntero del siguiente semáforo creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1707">**next_semaphore**: Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1708">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1708">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1709">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1709">Return Values</span></span>

- <span data-ttu-id="bdbe0-1710">**TX_SUCCESS**: (0x00) información del semáforo recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1710">**TX_SUCCESS**: (0x00) Successful semaphore information retrieval.</span></span>
- <span data-ttu-id="bdbe0-1711">TX_SEMAPHORE_ERROR: (0x0C) puntero del semáforo no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1711">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1712">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1712">Allowed From</span></span>

<span data-ttu-id="bdbe0-1713">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1713">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1714">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1714">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1715">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1715">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1716">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1716">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR         *name;
ULONG        current_value;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT         status;

/* Retrieve information about the previously created
   semaphore "my_semaphore." */
status =  tx_semaphore_info_get(&my_semaphore, &name,
                      &current_value,
                      &first_suspended, &suspended_count,
                      &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1717">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1717">See Also</span></span>

- <span data-ttu-id="bdbe0-1718">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1718">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="bdbe0-1719">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1719">tx_semaphore_create</span></span>
- <span data-ttu-id="bdbe0-1720">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1720">tx_semaphore_delete</span></span>
- <span data-ttu-id="bdbe0-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="bdbe0-1722">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1722">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1723">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1723">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1724">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1724">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="bdbe0-1725">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1725">tx_semaphore_put</span></span>
- <span data-ttu-id="bdbe0-1726">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1726">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="bdbe0-1727">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1727">tx_semaphore_performance_info_get</span></span> 

<span data-ttu-id="bdbe0-1728">Obtiene información acerca del rendimiento del semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1728">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1729">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1729">Prototype</span></span>

```C
UINT  tx_semaphore_performance_info_get(TX_SEMAPHORE *semaphore_ptr,
        ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1730">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1730">Description</span></span>

<span data-ttu-id="bdbe0-1731">Este servicio recupera información sobre el rendimiento del semáforo especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1731">This service retrieves performance information about the specified semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="bdbe0-1732">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1732">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1733">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1733">Parameters</span></span>

- <span data-ttu-id="bdbe0-1734">**semaphore_ptr**: puntero a un semáforo creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1734">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="bdbe0-1735">**puts**: puntero al destino del número de solicitudes Put realizadas en este semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1735">**puts**: Pointer to destination for the number of put requests performed on this semaphore.</span></span>
- <span data-ttu-id="bdbe0-1736">**gets**: puntero al destino del número de solicitudes Get realizadas en este semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1736">**gets**: Pointer to destination for the number of get requests performed on this semaphore.</span></span>
- <span data-ttu-id="bdbe0-1737">**suspensions**: puntero al destino del número de suspensiones de los subprocesos de este semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1737">**suspensions**: Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
- <span data-ttu-id="bdbe0-1738">**timeouts**: puntero al destino del número de tiempos de espera de suspensión de los subprocesos en este semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1738">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1739">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1739">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1740">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1740">Return Values</span></span>

- <span data-ttu-id="bdbe0-1741">**TX_SUCCESS**: (0x00) rendimiento del semáforo obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1741">**TX_SUCCESS**: (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="bdbe0-1742">**TX_PTR_ERROR**: (0x03) puntero del semáforo no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1742">**TX_PTR_ERROR**: (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="bdbe0-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1744">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1744">Allowed From</span></span>

<span data-ttu-id="bdbe0-1745">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1745">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1746">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1746">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
ULONG            puts;
ULONG            gets;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created
   semaphore. */
status =  tx_semaphore_performance_info_get(&my_semaphore, &puts,
               &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1747">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1747">See Also</span></span>

- <span data-ttu-id="bdbe0-1748">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1748">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="bdbe0-1749">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1749">tx_semaphore_create</span></span>
- <span data-ttu-id="bdbe0-1750">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1750">tx_semaphore_delete</span></span>
- <span data-ttu-id="bdbe0-1751">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1751">tx_semaphore_get</span></span>
- <span data-ttu-id="bdbe0-1752">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1752">tx_semaphore_info_get</span></span>
- <span data-ttu-id="bdbe0-1753">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1753">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1754">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1754">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="bdbe0-1755">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1755">tx_semaphore_put</span></span>
- <span data-ttu-id="bdbe0-1756">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1756">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="bdbe0-1757">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1757">tx_semaphore_performance_system_info_get</span></span> 

<span data-ttu-id="bdbe0-1758">Obtiene información acerca del rendimiento de los semáforos del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1758">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1759">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1759">Prototype</span></span>

```C
UINT tx_semaphore_performance_system_info_get(ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1760">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1760">Description</span></span>

<span data-ttu-id="bdbe0-1761">Este servicio recupera información sobre el rendimiento de todos los semáforos del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1761">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1762">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1762">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1763">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1763">Parameters</span></span>

- <span data-ttu-id="bdbe0-1764">**puts**: puntero al destino del número total de solicitudes Put realizadas en todos los semáforos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1764">**puts**: Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="bdbe0-1765">**gets**: puntero al destino del número total de solicitudes Get realizadas en todos los semáforos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1765">**gets**: Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="bdbe0-1766">**suspensions**: puntero al destino del número total de suspensiones de los subprocesos de todos los semáforos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1766">**suspensions**: Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="bdbe0-1767">**timeouts**: puntero al destino del número total de tiempos de espera de suspensión de los subprocesos de todos los semáforos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1767">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1768">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1768">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1769">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1769">Return Values</span></span>

- <span data-ttu-id="bdbe0-1770">TX_SUCCESS: (0x00) rendimiento de los semáforos del sistema obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1770">TX_SUCCESS: (0x00) Successful semaphore system performance get.</span></span>
- <span data-ttu-id="bdbe0-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1772">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1772">Allowed From</span></span>

<span data-ttu-id="bdbe0-1773">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1773">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1774">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1774">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
               &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1775">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1775">See Also</span></span>

- <span data-ttu-id="bdbe0-1776">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1776">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="bdbe0-1777">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1777">tx_semaphore_create</span></span>
- <span data-ttu-id="bdbe0-1778">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1778">tx_semaphore_delete</span></span>
- <span data-ttu-id="bdbe0-1779">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1779">tx_semaphore_get</span></span>
- <span data-ttu-id="bdbe0-1780">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1780">tx_semaphore_info_get</span></span>
- <span data-ttu-id="bdbe0-1781">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1781">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1782">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1782">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="bdbe0-1783">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1783">tx_semaphore_put</span></span>
- <span data-ttu-id="bdbe0-1784">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1784">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="bdbe0-1785">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1785">tx_semaphore_prioritize</span></span>

<span data-ttu-id="bdbe0-1786">Da prioridad a un semáforo en la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1786">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1787">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1787">Prototype</span></span>

```C
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1788">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1788">Description</span></span>

<span data-ttu-id="bdbe0-1789">Este servicio coloca el subproceso de prioridad más alta suspendido para una instancia del semáforo al principio de la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1789">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="bdbe0-1790">Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1790">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1791">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1791">Parameters</span></span> 

- <span data-ttu-id="bdbe0-1792">**semaphore_ptr**: puntero a un semáforo creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1792">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1793">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1793">Return Values</span></span>

- <span data-ttu-id="bdbe0-1794">**TX_SUCCESS**: (0x00) prioridad del semáforo establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1794">**TX_SUCCESS**: (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="bdbe0-1795">TX_SEMAPHORE_ERROR: (0x0C) puntero del semáforo de recuento no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1795">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1796">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1796">Allowed From</span></span>

<span data-ttu-id="bdbe0-1797">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1797">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1798">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1798">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1799">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1799">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1800">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1800">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next instance of this semaphore. */
status =  tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_semaphore_put call made to this semaphore will
   wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1801">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1801">See Also</span></span>

- <span data-ttu-id="bdbe0-1802">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1802">tx_semaphore_create</span></span>
- <span data-ttu-id="bdbe0-1803">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1803">tx_semaphore_delete</span></span>
- <span data-ttu-id="bdbe0-1804">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1804">tx_semaphore_get</span></span>
- <span data-ttu-id="bdbe0-1805">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1805">tx_semaphore_info_get</span></span>
- <span data-ttu-id="bdbe0-1806">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1806">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="bdbe0-1807">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1807">tx_semaphore_put</span></span>

<span data-ttu-id="bdbe0-1808">Coloca una instancia en el semáforo de recuento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1808">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1809">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1809">Prototype</span></span>

```C
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1810">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1810">Description</span></span>

<span data-ttu-id="bdbe0-1811">Este servicio coloca una instancia en el semáforo de recuento especificado, lo que en realidad incrementa el semáforo de recuento en uno.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1811">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1812">Si se llama a este servicio cuando el semáforo es todo unos (OxFFFFFFFF), la nueva operación Put hará que el semáforo se restablezca a cero.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1812">If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1813">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1813">Parameters</span></span>

- <span data-ttu-id="bdbe0-1814">**semaphore_ptr**: puntero al bloque de control del semáforo de recuento creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1814">**semaphore_ptr**: Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1815">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1815">Return Values</span></span>

- <span data-ttu-id="bdbe0-1816">**TX_SUCCESS**: (0x00) operación Put realizada correctamente en el semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1816">**TX_SUCCESS**: (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="bdbe0-1817">TX_SEMAPHORE_ERROR: (0x0C) puntero no válido al semáforo de recuento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1817">TX_SEMAPHORE_ERROR: (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1818">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1818">Allowed From</span></span>

<span data-ttu-id="bdbe0-1819">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1819">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1820">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1820">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1821">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1821">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1822">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1822">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
UINT             status;

/* Increment the counting semaphore "my_semaphore." */
status =  tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
   been incremented. Of course, if a thread was waiting,
   it was given the semaphore instance and resumed. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1823">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1823">See Also</span></span>

- <span data-ttu-id="bdbe0-1824">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1824">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="bdbe0-1825">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1825">tx_semaphore_create</span></span>
- <span data-ttu-id="bdbe0-1826">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1826">tx_semaphore_delete</span></span>
- <span data-ttu-id="bdbe0-1827">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1827">tx_semaphore_info_get</span></span>
- <span data-ttu-id="bdbe0-1828">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1828">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1829">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1829">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1830">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1830">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="bdbe0-1831">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1831">tx_semaphore_get</span></span>
- <span data-ttu-id="bdbe0-1832">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1832">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="bdbe0-1833">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1833">tx_semaphore_put_notify</span></span>

<span data-ttu-id="bdbe0-1834">Notifica a la aplicación cuando se coloca el semáforo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1834">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1835">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1835">Prototype</span></span>

```C
UINT  tx_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr,
        VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```
### <a name="description"></a><span data-ttu-id="bdbe0-1836">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1836">Description</span></span>

<span data-ttu-id="bdbe0-1837">Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se coloca el semáforo especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1837">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="bdbe0-1838">La aplicación define el procesamiento de la devolución de llamada de notificación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1838">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="bdbe0-1839">La devolución de llamada de notificación del semáforo de la aplicación no puede llamar a ninguna API de ThreadX SMP con una opción de suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1839">The application’s semaphore notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1840">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1840">Parameters</span></span> 

- <span data-ttu-id="bdbe0-1841">**semaphore_ptr**: puntero a un semáforo creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1841">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="bdbe0-1842">**semaphore_put_notify**: puntero a la función de notificación de colocación del semáforo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1842">**semaphore_put_notify**: Pointer to application’s semaphore put notification function.</span></span> <span data-ttu-id="bdbe0-1843">Si este valor es TX_NULL, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1843">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1844">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1844">Return Values</span></span>

- <span data-ttu-id="bdbe0-1845">**TX_SUCCESS**: (0x00) notificación de colocación del semáforo registrada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1845">**TX_SUCCESS**: (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="bdbe0-1846">TX_SEMAPHORE_ERROR: (0x0C) puntero del semáforo no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1846">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="bdbe0-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema se compiló con las funcionalidades de notificación deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1848">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1848">Allowed From</span></span>

<span data-ttu-id="bdbe0-1849">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1849">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1850">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1850">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
   the put operations on the semaphore "my_semaphore." */
status =  tx_semaphore_put_notify(&my_semaphore,
                my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
   was successfully registered. */

void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
   /* The semaphore was just put! */
}
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1851">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1851">See Also</span></span>

- <span data-ttu-id="bdbe0-1852">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1852">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="bdbe0-1853">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1853">tx_semaphore_create</span></span>
- <span data-ttu-id="bdbe0-1854">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1854">tx_semaphore_delete</span></span>
- <span data-ttu-id="bdbe0-1855">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1855">tx_semaphore_get</span></span>
- <span data-ttu-id="bdbe0-1856">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1856">tx_semaphore_info_get</span></span>
- <span data-ttu-id="bdbe0-1857">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1857">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1858">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1858">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1859">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1859">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="bdbe0-1860">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1860">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="bdbe0-1861">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1861">tx_thread_create</span></span>

<span data-ttu-id="bdbe0-1862">Crea un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1862">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1863">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1863">Prototype</span></span>

```C
UINT tx_thread_create(TX_THREAD *thread_ptr,
                          CHAR *name_ptr, VOID (*entry_function)(ULONG),
                          ULONG entry_input, VOID *stack_start,
                          ULONG stack_size, UINT priority,
                          UINT preempt_threshold, ULONG time_slice,
                          UINT auto_start);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1864">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1864">Description</span></span>

<span data-ttu-id="bdbe0-1865">Este servicio crea un subproceso de aplicación que inicia la ejecución en la función de entrada de tarea especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1865">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="bdbe0-1866">Entre los atributos especificados por los parámetros de entrada se encuentran la pila, la prioridad, el umbral de adelantamiento y la porción de tiempo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1866">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="bdbe0-1867">Además, también se especifica el estado de ejecución inicial del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1867">In addition, the initial execution state of the thread is also specified.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1868">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1868">Parameters</span></span>

- <span data-ttu-id="bdbe0-1869">**thread_ptr**: puntero al bloque de control de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1869">**thread_ptr**: Pointer to a thread control block.</span></span>
- <span data-ttu-id="bdbe0-1870">**name_ptr**: puntero al nombre del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1870">**name_ptr**: Pointer to the name of the thread.</span></span>
- <span data-ttu-id="bdbe0-1871">**entry_function**: especifica la función de C inicial para la ejecución del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1871">**entry_function**: Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="bdbe0-1872">Cuando un subproceso vuelve de esta función de entrada, se le asigna un estado completado y se suspende indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1872">When a thread returns from this entry function, it is placed in a completed state and suspended indefinitely.</span></span>
- <span data-ttu-id="bdbe0-1873">**entry_input**: valor de 32 bits que se pasa a la función de entrada del subproceso cuando se ejecuta por primera vez.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1873">**entry_input**: A 32-bit value that is passed to the thread’s entry function when it first executes.</span></span> <span data-ttu-id="bdbe0-1874">La aplicación es la única que determina el uso de esta entrada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1874">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="bdbe0-1875">**stack_start**: dirección inicial del área de memoria de la pila.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1875">**stack_start**: Starting address of the stack’s memory area.</span></span> 
- <span data-ttu-id="bdbe0-1876">**stack_size**: número de bytes en el área de memoria de la pila.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1876">**stack_size**: Number bytes in the stack memory area.</span></span> <span data-ttu-id="bdbe0-1877">El área de la pila del subproceso debe ser lo suficientemente grande como para controlar el uso de las variables locales y el anidamiento de llamadas de función en el peor de los casos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1877">The thread’s stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="bdbe0-1878">**priority**: prioridad numérica del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1878">**priority**: Numerical priority of thread.</span></span> <span data-ttu-id="bdbe0-1879">Los valores válidos se sitúan entre 0 y (TX_MAX_PRIORITES-1), donde el valor 0 representa la prioridad más alta.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1879">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="bdbe0-1880">**preempt_threshold**: nivel de prioridad más alto, de 0 a (TX_MAX_PRIORITIES-1) del adelantamiento deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1880">**preempt_threshold**: Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="bdbe0-1881">Solo las prioridades superiores a este nivel pueden adelantar a este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1881">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="bdbe0-1882">Este valor debe ser menor o igual que la prioridad especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1882">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="bdbe0-1883">Un valor igual a la prioridad del subproceso deshabilita el umbral de adelantamiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1883">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="bdbe0-1884">**time_slice**: número de tics de temporizador durante los cuales se puede ejecutar este subproceso antes de que otros subprocesos preparados con la misma prioridad tengan la posibilidad de ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1884">**time_slice**: Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="bdbe0-1885">Tenga en cuenta que el uso del umbral de adelantamiento deshabilita las porciones de tiempo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1885">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="bdbe0-1886">Los valores de porción de tiempo válidos se sitúan entre 1 y 0xFFFFFFFF (ambos incluidos).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1886">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="bdbe0-1887">Un valor de **TX_NO_TIME_SLICE** (un valor de 0) deshabilita las porciones de tiempo de este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1887">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="bdbe0-1888">El uso de la segmentación temporal provoca una ligera sobrecarga del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1888">Using time-slicing results in a slight amount of system overhead.</span></span> <span data-ttu-id="bdbe0-1889">Dado que la segmentación temporal solo es útil en aquellos casos en que varios subprocesos comparten la misma prioridad, no se debe asignar ninguna porción de tiempo a los subprocesos con una prioridad única.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1889">Since time-slicing is only useful in cases where multiple threads share the same priority, threads having a unique priority should not be assigned a time-slice.</span></span>

- <span data-ttu-id="bdbe0-1890">**auto_start**: especifica si el subproceso se inicia inmediatamente o se coloca en un estado suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1890">**auto_start**: Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="bdbe0-1891">Las opciones válidas son **TX_AUTO_START** (0x01) y **TX_DONT_START** (0x00).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1891">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="bdbe0-1892">Si se especifica TX_DONT_START, la aplicación debe llamar posteriormente a tx_thread_resume para que se ejecute el subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1892">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1893">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1893">Return Values</span></span>

- <span data-ttu-id="bdbe0-1894">**TX_SUCCESS**: (0x00) subproceso creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1894">**TX_SUCCESS**: (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="bdbe0-1895">TX_THREAD_ERROR: (0x0E) puntero de control del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1895">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="bdbe0-1896">El puntero es NULL o el subproceso ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1896">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="bdbe0-1897">TX_PTR_ERROR: (0x03) la dirección inicial del punto de entrada o del área de la pila no es válida, normalmente es NULL.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1897">TX_PTR_ERROR: (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="bdbe0-1898">TX_SIZE_ERROR: (0x05) el tamaño del área de la pila no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1898">TX_SIZE_ERROR: (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="bdbe0-1899">Los subprocesos deben tener al menos **TX_MINIMUM_STACK** bytes para ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1899">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="bdbe0-1900">TX_PRIORITY_ERROR: (0x0F) prioridad del subproceso no válida. Es un valor fuera del rango de 0 a (TX_MAX_PRIORITIES-1).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1900">TX_PRIORITY_ERROR: (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="bdbe0-1901">TX_THRESH_ERROR: (0x18) el umbral de adelantamiento especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1901">TX_THRESH_ERROR: (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="bdbe0-1902">Este valor debe ser una prioridad válida menor o igual que la prioridad inicial del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1902">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="bdbe0-1903">TX_START_ERROR: (0x10) selección de inicio automático no válida.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1903">TX_START_ERROR: (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="bdbe0-1904">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1904">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1905">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1905">Allowed From</span></span>

<span data-ttu-id="bdbe0-1906">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1906">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1907">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1907">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1908">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1908">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1909">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1909">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Create a thread of priority 15 whose entry point is
   "my_thread_entry". This thread’s stack area is 1000
   bytes in size, starting at address 0x400000. The
   preemption-threshold is setup to allow preemption of threads
   with priorities ranging from 0 through 14. Time-slicing is
   disabled. This thread is automatically put into a ready
   condition. */
status =  tx_thread_create(&my_thread, "my_thread_name",
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
### <a name="see-also"></a><span data-ttu-id="bdbe0-1910">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1910">See Also</span></span>

- <span data-ttu-id="bdbe0-1911">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1911">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-1912">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1912">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-1913">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1913">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-1914">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1914">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-1915">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1915">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1916">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1916">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1917">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1917">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-1918">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1918">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-1919">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1919">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-1920">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1920">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-1921">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1921">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-1922">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1922">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-1923">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1923">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-1924">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1924">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-1925">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1925">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-1926">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1926">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-1927">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1927">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="bdbe0-1928">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1928">tx_thread_delete</span></span>

<span data-ttu-id="bdbe0-1929">Elimina un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1929">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1930">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1930">Prototype</span></span>

```C
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-1931">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1931">Description</span></span>

<span data-ttu-id="bdbe0-1932">Este servicio elimina el subproceso de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1932">This service deletes the specified application thread.</span></span> <span data-ttu-id="bdbe0-1933">Dado que el subproceso especificado debe estar en un estado finalizado o completado, no se puede llamar a este servicio desde un subproceso que intente eliminarse a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1933">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-1934">Es responsabilidad de la aplicación administrar el área de memoria asociada a la pila de la memoria, que está disponible una vez completado este servicio.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1934">It is the application’s responsibility to manage the memory area associated with the thread’s stack, which is available after this service completes.</span></span> <span data-ttu-id="bdbe0-1935">Además, debe evitar el uso de un subproceso eliminado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1935">In addition, the application must prevent use of a deleted thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1936">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1936">Parameters</span></span>

- <span data-ttu-id="bdbe0-1937">**thread_ptr**: puntero a un subproceso de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1937">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1938">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1938">Return Values</span></span>

- <span data-ttu-id="bdbe0-1939">**TX_SUCCESS**: (0x00) subproceso eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1939">**TX_SUCCESS**: (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="bdbe0-1940">TX_THREAD_ERROR: (0x0E) puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1940">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="bdbe0-1941">**TX_DELETE_ERROR**: (0x11) el subproceso especificado no se encuentra en un estado finalizado o completado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1941">**TX_DELETE_ERROR**: (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="bdbe0-1942">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1942">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1943">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1943">Allowed From</span></span>

<span data-ttu-id="bdbe0-1944">Subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1944">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-1945">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1945">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-1946">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1946">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1947">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1947">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Delete an application thread whose control block is
   "my_thread". Assume that the thread has already been
   created with a call to tx_thread_create. */
status =  tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-1948">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1948">See Also</span></span>

- <span data-ttu-id="bdbe0-1949">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1949">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-1950">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1950">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-1951">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1951">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-1952">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1952">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-1953">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1953">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1954">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1954">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1955">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1955">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-1956">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1956">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-1957">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1957">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-1958">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1958">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-1959">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1959">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-1960">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1960">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-1961">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1961">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-1962">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1962">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-1963">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1963">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-1964">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1964">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-1965">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1965">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="bdbe0-1966">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1966">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="bdbe0-1967">Notifica a la aplicación la entrada y salida de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1967">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-1968">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1968">Prototype</span></span>

```C
UINT  tx_thread_entry_exit_notify(TX_THREAD *thread_ptr,
        VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```
### <a name="description"></a><span data-ttu-id="bdbe0-1969">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1969">Description</span></span>

<span data-ttu-id="bdbe0-1970">Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se entra o sale del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1970">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="bdbe0-1971">La aplicación define el procesamiento de la devolución de llamada de notificación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1971">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="bdbe0-1972">La devolución de llamada de notificación de entrada o salida del subproceso de la aplicación no puede llamar a ninguna API de ThreadX SMP con una opción de suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1972">The application’s thread entry/exit notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-1973">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1973">Parameters</span></span>

- <span data-ttu-id="bdbe0-1974">**thread_ptr**: puntero a un subproceso creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1974">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="bdbe0-1975">**entry_exit_notify**: puntero a la función de notificación de entrada o salida del subproceso de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1975">**entry_exit_notify**: Pointer to application’s thread entry/exit notification function.</span></span> <span data-ttu-id="bdbe0-1976">El segundo parámetro para la función de notificación de entrada o salida designa si hay una entrada o una salida.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1976">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="bdbe0-1977">El valor TX_THREAD_ENTRY (0x00) indica que se entró en el subproceso, mientras que el valor TX_THREAD_EXIT (0x01) indica que se salió de él.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1977">The value TX_THREAD_ENTRY (0x00) indicates the thread was entered, while the value TX_THREAD_EXIT (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="bdbe0-1978">Si este valor es TX_NULL, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1978">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-1979">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1979">Return Values</span></span>

- <span data-ttu-id="bdbe0-1980">**TX_SUCCESS**: (0x00) registro correcto de la función de notificación de entrada o salida del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1980">**TX_SUCCESS**: (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="bdbe0-1981">TX_THREAD_ERROR: (0x0E) puntero del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1981">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="bdbe0-1982">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema se compiló con las funcionalidades de notificación deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1982">**TX_FEATURE_NOT_ENABLED(0xFF)** The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-1983">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1983">Allowed From</span></span>

<span data-ttu-id="bdbe0-1984">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1984">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-1985">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1985">Example</span></span>

```C
TX_THREAD         my_thread;

/* Register the "my_entry_exit_notify" function for monitoring
   the entry/exit of the thread "my_thread." */
status =  tx_thread_entry_exit_notify(&my_thread,
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

### <a name="see-also"></a><span data-ttu-id="bdbe0-1986">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1986">See Also</span></span>

- <span data-ttu-id="bdbe0-1987">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1987">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-1988">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1988">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-1989">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1989">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-1990">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1990">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-1991">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1991">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-1992">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1992">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-1993">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1993">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-1994">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1994">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-1995">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1995">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-1996">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1996">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-1997">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1997">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-1998">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1998">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-1999">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-1999">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2000">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2000">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2001">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2001">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2002">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2002">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2003">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2003">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2004">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2004">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="bdbe0-2005">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2005">tx_thread_identify</span></span>

<span data-ttu-id="bdbe0-2006">Recupera un puntero al subproceso que se está ejecutando actualmente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2006">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2007">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2007">Prototype</span></span>

```C
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2008">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2008">Description</span></span>

<span data-ttu-id="bdbe0-2009">Este servicio devuelve un puntero al subproceso que se está ejecutando actualmente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2009">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="bdbe0-2010">Si no se está ejecutando ningún subproceso, devuelve un puntero nulo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2010">If no thread is executing, this service returns a null pointer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2011">Si se llama a este servicio desde una ISR, el valor devuelto representa el subproceso que se estaba ejecutando antes que el controlador de interrupción en ejecución.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2011">If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2012">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2012">Parameters</span></span>

<span data-ttu-id="bdbe0-2013">Ninguno</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2013">None</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2014">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2014">Return Values</span></span>

- <span data-ttu-id="bdbe0-2015">puntero del subproceso: puntero al subproceso que se está ejecutando actualmente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2015">thread pointer: Pointer to the currently executing thread.</span></span> <span data-ttu-id="bdbe0-2016">Si no se está ejecutando ningún subproceso, el valor devuelto es TX_NULL.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2016">If no thread is executing, the return value is TX_NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2017">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2017">Allowed From</span></span>

<span data-ttu-id="bdbe0-2018">Subprocesos e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2018">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2019">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2019">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2020">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2020">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2021">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2021">Example</span></span>

```C
TX_THREAD     *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr =  tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
   from that thread or an ISR that interrupted that thread.
   Otherwise, this service was called
   from an ISR when no thread was running when the
   interrupt occurred.  */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2022">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2022">See Also</span></span>

- <span data-ttu-id="bdbe0-2023">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2023">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2024">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2024">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2025">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2025">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2026">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2026">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2027">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2027">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2028">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2028">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2029">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2029">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2030">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2030">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2031">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2031">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2032">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2032">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2033">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2033">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2034">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2034">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2035">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2035">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2036">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2036">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2037">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2037">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2038">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2038">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2039">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2039">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="bdbe0-2040">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2040">tx_thread_info_get</span></span>

<span data-ttu-id="bdbe0-2041">Recupera información acerca de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2041">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2042">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2042">Prototype</span></span>

```C
UINT tx_thread_info_get(TX_THREAD *thread_ptr, CHAR **name,
                          UINT *state, ULONG *run_count,
                          UINT *priority,
                          UINT *preemption_threshold,
                          ULONG *time_slice,
                          TX_THREAD **next_thread,
                          TX_THREAD **suspended_thread);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2043">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2043">Description</span></span>

<span data-ttu-id="bdbe0-2044">Este servicio recupera información sobre el subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2044">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2045">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2045">Parameters</span></span> 

- <span data-ttu-id="bdbe0-2046">**thread_ptr**: puntero al bloque de control de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2046">**thread_ptr**: Pointer to thread control block.</span></span>
- <span data-ttu-id="bdbe0-2047">**name**: puntero al destino del puntero al nombre del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2047">**name**: Pointer to destination for the pointer to the thread’s name.</span></span>
- <span data-ttu-id="bdbe0-2048">**state**: puntero al destino del estado de ejecución actual del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2048">**state**:  Pointer to destination for the thread’s current execution state.</span></span> <span data-ttu-id="bdbe0-2049">Los valores posibles son:</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2049">Possible values are as follows:</span></span>
    - <span data-ttu-id="bdbe0-2050">**TX_READY**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2050">**TX_READY**: (0x00)</span></span>
    - <span data-ttu-id="bdbe0-2051">**TX_COMPLETED**: (0x01)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2051">**TX_COMPLETED**: (0x01)</span></span>
    - <span data-ttu-id="bdbe0-2052">**TX_TERMINATED**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2052">**TX_TERMINATED**: (0x02)</span></span>
    - <span data-ttu-id="bdbe0-2053">**TX_SUSPENDED**: (0x03)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2053">**TX_SUSPENDED**: (0x03)</span></span>
    - <span data-ttu-id="bdbe0-2054">**TX_SLEEP**: (0x04)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2054">**TX_SLEEP**: (0x04)</span></span>
    - <span data-ttu-id="bdbe0-2055">**TX_QUEUE_SUSP**: (0x05)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2055">**TX_QUEUE_SUSP**: (0x05)</span></span>
    - <span data-ttu-id="bdbe0-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span></span>
    - <span data-ttu-id="bdbe0-2057">**TX_EVENT_FLAG**: (0x07)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2057">**TX_EVENT_FLAG**: (0x07)</span></span>
    - <span data-ttu-id="bdbe0-2058">**TX_BLOCK_MEMORY**: (0x08)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2058">**TX_BLOCK_MEMORY**: (0x08)</span></span>
    - <span data-ttu-id="bdbe0-2059">**TX_BYTE_MEMORY**: (0x09)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2059">**TX_BYTE_MEMORY**: (0x09)</span></span>
    - <span data-ttu-id="bdbe0-2060">**TX_MUTEX_SUSP**: (0x0D)</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2060">**TX_MUTEX_SUSP**: (0x0D)</span></span>

- <span data-ttu-id="bdbe0-2061">**run_count**: puntero al destino del recuento de ejecuciones del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2061">**run_count**: Pointer to destination for the thread’s run count.</span></span> 
- <span data-ttu-id="bdbe0-2062">**priority**: puntero al destino de la prioridad del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2062">**priority**: Pointer to destination for the thread’s priority.</span></span>
- <span data-ttu-id="bdbe0-2063">**preemption_threshold**: puntero al destino del umbral de adelantamiento del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2063">**preemption_threshold**: Pointer to destination for the thread’s preemption-threshold.</span></span>
- <span data-ttu-id="bdbe0-2064">**time_slice**: puntero al destino de la porción de tiempo del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2064">**time_slice**: Pointer to destination for the thread’s time-slice.</span></span> 
- <span data-ttu-id="bdbe0-2065">**next_thread**: puntero al destino del puntero del siguiente subproceso creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2065">**next_thread**: Pointer to destination for next created thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2066">**suspended_thread**: puntero al destino del puntero al siguiente subproceso en la lista de suspensiones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2066">**suspended_thread**: Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2067">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2067">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2068">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2068">Return Values</span></span>

- <span data-ttu-id="bdbe0-2069">**TX_SUCCESS**: (0x00) información del subproceso recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2069">**TX_SUCCESS**: (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="bdbe0-2070">TX_THREAD_ERROR: (0x0E) puntero de control del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2070">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2071">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2071">Allowed From</span></span>

<span data-ttu-id="bdbe0-2072">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2072">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2073">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2073">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2074">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2074">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2075">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2075">Example</span></span>

```C
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
status =  tx_thread_info_get(&my_thread, &name,
                  &state, &run_count,
            &priority, &preemption_threshold,
                  &time_slice, &next_thread,&suspended_thread);
/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2076">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2076">See Also</span></span>

- <span data-ttu-id="bdbe0-2077">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2077">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2078">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2078">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2079">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2079">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2080">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2080">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2081">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2081">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2082">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2082">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2083">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2083">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2084">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2084">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2085">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2085">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2086">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2086">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2087">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2087">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2088">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2088">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2089">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2089">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2090">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2090">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2091">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2091">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2092">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2092">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2093">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2093">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="bdbe0-2094">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2094">tx_thread_performance_info_get</span></span> 

<span data-ttu-id="bdbe0-2095">Obtiene información acerca del rendimiento de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2095">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2096">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2096">Prototype</span></span>

```C
UINT  tx_thread_performance_info_get(TX_THREAD *thread_ptr,
        ULONG *resumptions, ULONG *suspensions,
        ULONG *solicited_preemptions, ULONG *interrupt_preemptions,
        ULONG *priority_inversions, ULONG *time_slices,
        ULONG *relinquishes, ULONG *timeouts, ULONG *wait_aborts,
        TX_THREAD **last_preempted_by);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2097">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2097">Description</span></span>

<span data-ttu-id="bdbe0-2098">Este servicio recupera información sobre el rendimiento del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2098">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2099">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_THREAD_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2099">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2100">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2100">Parameters</span></span> 

- <span data-ttu-id="bdbe0-2101">**thread_ptr**: puntero a un subproceso creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2101">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="bdbe0-2102">**resumptions**: puntero al destino del número de reanudaciones de este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2102">**resumptions**: Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="bdbe0-2103">**suspensions**: puntero al destino del número de suspensiones de este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2103">**suspensions**: Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="bdbe0-2104">**solicited_preemptions**: puntero al destino del número de adelantamientos como resultado de una llamada a un servicio de la API de ThreadX realizada por este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2104">**solicited_preemptions**: Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="bdbe0-2105">**interrupt_preemptions**: puntero al destino del número de adelantamientos de este subproceso como resultado del procesamiento de las interrupciones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2105">**interrupt_preemptions**: Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="bdbe0-2106">**priority_inversions**: puntero al destino del número de inversiones de prioridad de este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2106">**priority_inversions**: Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="bdbe0-2107">**time_slices**: puntero al destino del número de porciones de tiempo de este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2107">**time_slices**: Pointer to destination for the number of timeslices of this thread.</span></span>
- <span data-ttu-id="bdbe0-2108">**relinquishes**: puntero al destino del número de cesiones de subproceso realizadas por este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2108">**relinquishes**: Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="bdbe0-2109">**timeouts**: puntero al destino del número de tiempos de espera de suspensión en este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2109">**timeouts**: Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="bdbe0-2110">**wait_aborts**: puntero al destino del número de anulaciones de espera realizadas en este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2110">**wait_aborts**: Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="bdbe0-2111">**last_preempted_by**: puntero al destino del puntero del último subproceso que ha adelantado a este subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2111">**last_preempted_by**: Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2112">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2112">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2113">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2113">Return Values</span></span>

- <span data-ttu-id="bdbe0-2114">**TX_SUCCESS**: (0x00) rendimiento del subproceso obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2114">**TX_SUCCESS**: (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="bdbe0-2115">**TX_PTR_ERROR**: (0x03) puntero del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2115">**TX_PTR_ERROR**: (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2117">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2117">Allowed From</span></span>

<span data-ttu-id="bdbe0-2118">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2118">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2119">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2119">Example</span></span>

```c
TX_THREAD     my_thread;
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
TX_THREAD     *last_preempted_by;

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
### <a name="see-also"></a><span data-ttu-id="bdbe0-2120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2120">See Also</span></span>

- <span data-ttu-id="bdbe0-2121">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2121">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2122">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2122">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2123">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2123">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2124">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2124">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2125">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2125">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2126">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2126">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2127">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2127">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2128">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2128">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2129">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2129">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2130">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2130">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2131">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2131">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2132">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2132">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2133">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2133">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2134">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2134">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2135">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2135">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2136">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2136">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2137">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2137">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="bdbe0-2138">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2138">tx_thread_performance_system_info_get</span></span> 

<span data-ttu-id="bdbe0-2139">Obtiene información acerca del rendimiento de los subprocesos del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2139">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2140">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2140">Prototype</span></span>

```C
UINT tx_thread_performance_system_info_get(ULONG *resumptions,
       ULONG *suspensions, ULONG *solicited_preemptions,
       ULONG *interrupt_preemptions, ULONG *priority_inversions,
       ULONG *time_slices, ULONG *relinquishes, ULONG *timeouts,
       ULONG *wait_aborts, ULONG *non_idle_returns,
       ULONG *idle_returns);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2141">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2141">Description</span></span>

<span data-ttu-id="bdbe0-2142">Este servicio recupera información sobre el rendimiento de todos los subprocesos del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2142">This service retrieves performance information about all the threads in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2143">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_THREAD_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2143">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2144">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2144">Parameters</span></span>

- <span data-ttu-id="bdbe0-2145">**resumptions**: puntero al destino del número total de reanudaciones de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2145">**resumptions**: Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="bdbe0-2146">**suspensions**: puntero al destino del número total de suspensiones de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2146">**suspensions**: Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="bdbe0-2147">**solicited_preemptions**: puntero al destino del número total de adelantamientos de los subprocesos como resultado de una llamada de un subproceso a un servicio de API de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2147">**solicited_preemptions**: Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="bdbe0-2148">**interrupt_preemptions**: puntero al destino del número total de adelantamientos de los subprocesos como resultado del procesamiento de interrupciones.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2148">**interrupt_preemptions**: Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="bdbe0-2149">**priority_inversions**: puntero al destino del número total de inversiones de prioridad de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2149">**priority_inversions**: Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="bdbe0-2150">**time_slices**: puntero al destino del número total de porciones de tiempo de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2150">**time_slices**: Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="bdbe0-2151">**relinquishes**: puntero al destino del número total de cesiones de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2151">**relinquishes**: Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="bdbe0-2152">**timeouts**: puntero al destino del número total de tiempos de espera de suspensión de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2152">**timeouts**: Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="bdbe0-2153">**wait_aborts**: puntero al destino del número total de anulaciones de espera de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2153">**wait_aborts**: Pointer to destination for the total number of thread wait aborts.</span></span> 
- <span data-ttu-id="bdbe0-2154">**non_idle_returns**: puntero al destino del número de veces que un subproceso vuelve al sistema cuando hay otro subproceso preparado para ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2154">**non_idle_returns**: Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span> 
- <span data-ttu-id="bdbe0-2155">**idle_returns**: puntero al destino del número de veces que un subproceso vuelve al sistema cuando no hay otro subproceso preparado para ejecutarse (sistema inactivo).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2155">**idle_returns**: Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2156">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2156">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2157">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2157">Return Values</span></span>

- <span data-ttu-id="bdbe0-2158">**TX_SUCCESS**: (0x00) rendimiento de los subprocesos del sistema obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2158">**TX_SUCCESS**: (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="bdbe0-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2160">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2160">Allowed From</span></span>

<span data-ttu-id="bdbe0-2161">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2161">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2162">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2162">Example</span></span>

```C
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
ULONG         non_idle_returns;
ULONG         idle_returns;

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
### <a name="see-also"></a><span data-ttu-id="bdbe0-2163">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2163">See Also</span></span>

- <span data-ttu-id="bdbe0-2164">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2164">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2165">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2165">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2166">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2166">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2167">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2167">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2168">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2168">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2169">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2169">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2170">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2170">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2171">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2171">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2172">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2172">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2173">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2173">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2174">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2174">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2175">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2175">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2176">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2176">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2177">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2177">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2178">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2178">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2179">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2179">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2180">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2180">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="bdbe0-2181">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2181">tx_thread_preemption_change</span></span>

<span data-ttu-id="bdbe0-2182">Cambia el umbral de adelantamiento de un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2182">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2183">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2183">Prototype</span></span>

```C
UINT tx_thread_preemption_change(TX_THREAD *thread_ptr,
                          UINT new_threshold, UINT *old_threshold);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2184">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2184">Description</span></span>

<span data-ttu-id="bdbe0-2185">Este servicio cambia el umbral de adelantamiento del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2185">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="bdbe0-2186">El umbral de adelantamiento impide que los subprocesos con un valor igual o inferior a este umbral adelanten al subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2186">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2187">El uso del umbral de adelantamiento deshabilita la segmentación temporal en el subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2187">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2188">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2188">Parameters</span></span>

- <span data-ttu-id="bdbe0-2189">**thread_ptr**: puntero a un subproceso de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2189">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="bdbe0-2190">**new_threshold**: nuevo nivel de prioridad del umbral de adelantamiento, de 0 a (TX_MAX_PRIORITIES-1).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2190">**new_threshold**: New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="bdbe0-2191">**old_threshold**: puntero a una ubicación para devolver el umbral de adelantamiento anterior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2191">**old_threshold**: Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2192">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2192">Return Values</span></span>

- <span data-ttu-id="bdbe0-2193">**TX_SUCCESS**: (0x00) umbral de adelantamiento cambiado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2193">**TX_SUCCESS**: (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="bdbe0-2194">TX_THREAD_ERROR: (0x0E) puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2194">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2195">**TX_THRESH_ERROR**: (0x18) el nuevo umbral de adelantamiento especificado no es una prioridad de subproceso válida (un valor distinto del intervalo de 0 a (TX_MAX_PRIORITIES-1) o mayor que la prioridad inferior) de la prioridad actual del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2195">**TX_THRESH_ERROR**: (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (TX_MAX_PRIORITIES-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="bdbe0-2196">TX_PTR_ERROR: (0x03) puntero no válido a la ubicación de almacenamiento del umbral de adelantamiento anterior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2196">TX_PTR_ERROR: (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="bdbe0-2197">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2197">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2198">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2198">Allowed From</span></span>

<span data-ttu-id="bdbe0-2199">Subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2199">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2200">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2200">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2201">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2201">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2202">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2202">Example</span></span>

```c
TX_THREAD     my_thread;
UINT          my_old_threshold;
UINT          status;

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
### <a name="see-also"></a><span data-ttu-id="bdbe0-2203">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2203">See Also</span></span>

- <span data-ttu-id="bdbe0-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2204">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2205">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2207">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2210">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2210">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2211">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2211">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2212">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2212">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2213">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2213">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2214">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="bdbe0-2221">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2221">tx_thread_priority_change</span></span>

<span data-ttu-id="bdbe0-2222">Cambia la prioridad de un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2222">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2223">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2223">Prototype</span></span>

```C
UINT tx_thread_priority_change(TX_THREAD *thread_ptr,
                          UINT new_priority, UINT *old_priority);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2224">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2224">Description</span></span>

<span data-ttu-id="bdbe0-2225">Este servicio cambia la prioridad del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2225">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="bdbe0-2226">Las prioridades válidas se sitúan entre 0 y (TX_MAX_PRIORITES-1), donde 0 representa el nivel de prioridad más alto.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2226">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2227">El umbral de adelantamiento del subproceso especificado se establece automáticamente en la nueva prioridad.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2227">The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="bdbe0-2228">Si se desea un nuevo umbral, se debe usar el servicio **tx_thread_preemption_change** después de esta llamada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2228">If a new threshold is desired, the **tx_thread_preemption_change** service must be used after this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2229">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2229">Parameters</span></span>

- <span data-ttu-id="bdbe0-2230">**thread_ptr**: puntero a un subproceso de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2230">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="bdbe0-2231">**new_priority**: nuevo nivel de prioridad del subproceso, de 0 a (TX_MAX_PRIORITIES-1).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2231">**new_priority**: New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="bdbe0-2232">**old_priority**: puntero a una ubicación para devolver la prioridad anterior del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2232">**old_priority**: Pointer to a location to return the thread’s previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2233">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2233">Return Values</span></span>

- <span data-ttu-id="bdbe0-2234">**TX_SUCCESS**: (0x00) prioridad cambiada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2234">**TX_SUCCESS**: (0x00) Successful priority change.</span></span>
- <span data-ttu-id="bdbe0-2235">TX_THREAD_ERROR: (0x0E) puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2235">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2236">TX_PRIORITY_ERROR: (0x0F) la nueva prioridad especificada no es válida (un valor no incluido en el intervalo de 0 a (TX_MAX_PRIORITIES-1).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2236">TX_PRIORITY_ERROR: (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="bdbe0-2237">TX_PTR_ERROR: (0x03) puntero no válido a la ubicación de almacenamiento de la prioridad anterior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2237">TX_PTR_ERROR: (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="bdbe0-2238">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2238">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2239">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2239">Allowed From</span></span>

<span data-ttu-id="bdbe0-2240">Subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2240">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2241">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2241">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2242">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2242">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2243">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2243">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          my_old_priority;
UINT          status;

/* Change the thread represented by "my_thread" to priority
   0. */
status = tx_thread_priority_change(&my_thread,
                            0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
   now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2244">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2244">See Also</span></span>

- <span data-ttu-id="bdbe0-2245">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2245">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2246">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2246">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2247">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2247">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2248">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2248">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2249">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2249">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2250">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2250">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2251">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2251">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2252">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2252">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2253">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2253">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2254">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2254">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2255">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2255">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2256">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2256">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2257">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2257">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2258">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2258">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2259">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2259">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2260">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2260">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2261">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2261">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="bdbe0-2262">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2262">tx_thread_relinquish</span></span>

<span data-ttu-id="bdbe0-2263">Cede el control a otros subprocesos de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2263">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2264">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2264">Prototype</span></span>

```C
VOID tx_thread_relinquish(VOID);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2265">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2265">Description</span></span>

<span data-ttu-id="bdbe0-2266">Este servicio cede el control del procesador a otros subprocesos preparados para ejecutarse con prioridad igual o superior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2266">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2267">Además de ceder el control a los subprocesos con la misma prioridad, este servicio también se lo cede al subproceso de prioridad más alta que no se haya podido ejecutar debido a la configuración del umbral de adelantamiento del subproceso actual.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2267">In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2268">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2268">Parameters</span></span>

<span data-ttu-id="bdbe0-2269">Ninguno</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2269">None</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2270">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2270">Return Values</span></span>

<span data-ttu-id="bdbe0-2271">Ninguno</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2271">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2272">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2272">Allowed From</span></span>

<span data-ttu-id="bdbe0-2273">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2274">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2274">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2275">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2276">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2276">Example</span></span>

```C
ULONG run_counter_1 =  0;
ULONG run_counter_2 =  0;

/* Example of two threads relinquishing control to
   each other in an infinite loop. Assume that
   both of these threads are ready and have the same
   priority. The run counters will always stay within one
   of each other. */

VOID  my_first_thread(ULONG thread_input)
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
### <a name="see-also"></a><span data-ttu-id="bdbe0-2277">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2277">See Also</span></span>

- <span data-ttu-id="bdbe0-2278">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2278">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2279">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2279">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2280">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2280">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2281">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2281">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2282">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2282">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2283">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2283">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2284">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2284">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2285">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2285">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2286">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2286">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2287">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2288">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2289">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2289">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2290">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2290">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2291">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2291">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2292">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2292">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2293">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2293">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2294">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2294">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="bdbe0-2295">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2295">tx_thread_reset</span></span>

<span data-ttu-id="bdbe0-2296">Restablece un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2296">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2297">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2297">Prototype</span></span>

```C
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2298">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2298">Description</span></span>

<span data-ttu-id="bdbe0-2299">Este servicio restablece el subproceso especificado para que se ejecute en el punto de entrada definido al crearlo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2299">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="bdbe0-2300">El subproceso debe estar en un estado **TX_COMPLETED** o **TX_TERMINATED** para que se pueda restablecer.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2300">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2301">El subproceso se debe reanudar para que se pueda ejecutar de nuevo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2301">The thread must be resumed for it to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2302">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2302">Parameters</span></span> 

- <span data-ttu-id="bdbe0-2303">**thread_ptr**: puntero a un subproceso creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2303">**thread_ptr**: Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2304">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2304">Return Values</span></span>

- <span data-ttu-id="bdbe0-2305">**TX_SUCCESS**: (0x00) subproceso restablecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2305">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="bdbe0-2306">**TX_NOT_DONE**: (0x20) el subproceso especificado no se encuentra en un estado TX_COMPLETED o TX_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2306">**TX_NOT_DONE**: (0x20) Specified thread is not in a TX_COMPLETED or TX_TERMINATED state.</span></span>
- <span data-ttu-id="bdbe0-2307">TX_THREAD_ERROR: (0x0E) puntero del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2307">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2308">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2308">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2309">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2309">Allowed From</span></span>

<span data-ttu-id="bdbe0-2310">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2311">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2311">Example</span></span>

```C
TX_THREAD     my_thread;

/* Reset the previously created thread "my_thread." */
status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2312">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2312">See Also</span></span>

- <span data-ttu-id="bdbe0-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2313">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2314">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2316">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2319">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2319">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2323">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2323">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2324">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2324">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2325">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2325">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="bdbe0-2330">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2330">tx_thread_resume</span></span>

<span data-ttu-id="bdbe0-2331">Reanuda un subproceso de aplicación suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2331">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2332">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2332">Prototype</span></span>

```C
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2333">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2333">Description</span></span>

<span data-ttu-id="bdbe0-2334">Este servicio reanuda o prepara para su ejecución un subproceso suspendido anteriormente mediante una llamada a ***tx_thread_suspend***.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2334">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="bdbe0-2335">Además, este servicio reanuda los subprocesos que se crearon sin un inicio automático.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2335">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2336">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2336">Parameters</span></span>

- <span data-ttu-id="bdbe0-2337">**thread_ptr**: puntero a un subproceso de aplicación suspendido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2337">**thread_ptr**: Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2338">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2338">Return Values</span></span>

- <span data-ttu-id="bdbe0-2339">**TX_SUCCESS**: (0x00) subproceso reanudado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2339">**TX_SUCCESS**: (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="bdbe0-2340">**TX_SUSPEND_LIFTED**: (0x19) se eliminó la suspensión retrasada establecida previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2340">**TX_SUSPEND_LIFTED**: (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="bdbe0-2341">TX_THREAD_ERROR: (0x0E) puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2341">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2342">**TX_RESUME_ERROR**: (0x12) el subproceso especificado no está suspendido o se suspendió previamente mediante un servicio distinto a **_tx_thread_suspend_**.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2342">**TX_RESUME_ERROR**: (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2343">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2343">Allowed From</span></span>

<span data-ttu-id="bdbe0-2344">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2344">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2345">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2345">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2346">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2346">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2347">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2347">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Resume the thread represented by "my_thread". */
status =  tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   now ready to execute. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2348">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2348">See Also</span></span>

- <span data-ttu-id="bdbe0-2349">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2349">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2350">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2350">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2351">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2351">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2352">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2352">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2353">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2353">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2354">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2354">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2355">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2355">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2356">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2356">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2357">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2357">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2358">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2358">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2359">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2359">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2360">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2360">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2361">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2361">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2362">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2362">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2363">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2363">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2364">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2364">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2365">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2365">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="bdbe0-2366">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2366">tx_thread_sleep</span></span>

<span data-ttu-id="bdbe0-2367">Suspende el subproceso actual durante el tiempo especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2367">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2368">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2368">Prototype</span></span>

```C
UINT tx_thread_sleep(ULONG timer_ticks);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2369">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2369">Description</span></span>

<span data-ttu-id="bdbe0-2370">Este servicio hace que el subproceso que realiza la llamada se suspenda durante el número especificado de tics de temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2370">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="bdbe0-2371">La cantidad de tiempo físico asociada a un tic de temporizador es específica de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2371">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="bdbe0-2372">Solo se puede llamar a este servicio desde un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2372">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2373">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2373">Parameters</span></span>

- <span data-ttu-id="bdbe0-2374">**timer_ticks**: número de tics de temporizador para suspender el subproceso de la aplicación que realiza la llamada, comprendido entre 0 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2374">**timer_ticks**: The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="bdbe0-2375">Si se especifica 0, el servicio se devuelve inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2375">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2376">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2376">Return Values</span></span>

- <span data-ttu-id="bdbe0-2377">**TX_SUCCESS**: (0x00) subproceso suspendido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2377">**TX_SUCCESS**: (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="bdbe0-2378">**TX_WAIT_ABORTED**: (0x1A) otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2378">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="bdbe0-2379">**TX_CALLER_ERROR**: (0x13) se llamó al servicio desde un elemento distinto de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2379">**TX_CALLER_ERROR**: (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2380">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2380">Allowed From</span></span>

<span data-ttu-id="bdbe0-2381">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2381">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2382">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2382">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2383">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2383">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2384">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2384">Example</span></span>

```C
UINT status;

/* Make the calling thread sleep for 100
   timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
   application thread slept for the specified number of
   timer-ticks. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2385">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2385">See Also</span></span>

- <span data-ttu-id="bdbe0-2386">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2386">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2387">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2387">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2388">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2388">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2389">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2389">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2390">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2390">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2391">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2391">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2392">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2392">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2393">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2393">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2394">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2394">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2395">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2395">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2396">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2396">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2397">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2397">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2398">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2398">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2399">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2399">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2400">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2400">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2401">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2401">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2402">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2402">tx_thread_wait_abort</span></span>

## <a name="tx_thread_smp_core_exclude"></a><span data-ttu-id="bdbe0-2403">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2403">tx_thread_smp_core_exclude</span></span>

<span data-ttu-id="bdbe0-2404">Excluye la ejecución de un subproceso de un conjunto de núcleos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2404">Exclude thread execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2405">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2405">Prototype</span></span>

```C
UINT  tx_thread_smp_core_exclude(TX_THREAD *thread_ptr,
                          ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2406">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2406">Description</span></span>

<span data-ttu-id="bdbe0-2407">Esta función excluye la ejecución del subproceso especificado de los núcleos especificados en el mapa de bits denominado "*exclusion_map*".</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2407">This function excludes the specified thread from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="bdbe0-2408">Cada bit de "*exclusion_map*" representa un núcleo (el bit 0 representa el núcleo 0, etc.).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2408">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="bdbe0-2409">Si se establece el bit, el núcleo correspondiente se excluye de la ejecución del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2409">If the bit is set, the corresponding core is excluded from executing the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2410">El uso de exclusiones en el procesador puede provocar un procesamiento adicional de la lógica de asignación de subprocesos a núcleos con el fin de encontrar la correspondencia óptima.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2410">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="bdbe0-2411">Este procesamiento está limitado por el número de subprocesos listos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2411">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2412">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2412">Parameters</span></span> 

- <span data-ttu-id="bdbe0-2413">**thread_ptr**: puntero al subproceso para cambiar la exclusión de núcleos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2413">**thread_ptr**: Pointer to thread to change the core exclusion.</span></span>
- <span data-ttu-id="bdbe0-2414">**exclusion_map**: mapa de bits donde un bit establecido indica que se excluye ese núcleo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2414">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="bdbe0-2415">Si se indica un valor 0, el subproceso se puede ejecute en cualquier núcleo (es el valor predeterminado).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2415">Supplying a 0 value enables the thread to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2416">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2416">Return Values</span></span>

- <span data-ttu-id="bdbe0-2417">TX_SUCCESS: (0x00) exclusión de núcleos correcta.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2417">TX_SUCCESS: (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="bdbe0-2418">TX_THREAD_ERROR: (0x0E) puntero del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2418">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2419">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2419">Allowed From</span></span>

<span data-ttu-id="bdbe0-2420">Inicialización, ISR, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2420">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2421">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2421">Example</span></span>

```C
/* Exclude core 0 for "Thread 0". */
tx_thread_smp_core_exclude(&thread_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="bdbe0-2422">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2422">See Also</span></span>

- <span data-ttu-id="bdbe0-2423">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2423">tx_thread_smp_core_exclude_get</span></span>
- <span data-ttu-id="bdbe0-2424">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2424">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_exclude_get"></a><span data-ttu-id="bdbe0-2425">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2425">tx_thread_smp_core_exclude_get</span></span>

<span data-ttu-id="bdbe0-2426">Obtiene la exclusión actual de núcleos del subproceso.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2426">Gets the thread's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2427">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2427">Prototype</span></span>

```C
UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2428">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2428">Description</span></span>

<span data-ttu-id="bdbe0-2429">Esta función devuelve la lista de exclusión actual de núcleos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2429">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2430">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2430">Parameters</span></span>

- <span data-ttu-id="bdbe0-2431">**thread_ptr**: puntero al subproceso del que se va a recuperar la exclusión de núcleos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2431">**thread_ptr**: Pointer to thread from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="bdbe0-2432">**exclusion_map_ptr**: destino del mapa de bits de exclusión actual de núcleos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2432">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2433">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2433">Return Values</span></span>

- <span data-ttu-id="bdbe0-2434">TX_SUCCESS: (0x00) exclusión de núcleos del subproceso recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2434">TX_SUCCESS: (0x00) Successful retrieval of thread's core exclusion.</span></span>
- <span data-ttu-id="bdbe0-2435">TX_THREAD_ERROR: (0x0E) puntero del subproceso no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2435">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2436">TX_PTR_ERROR: (0x03) puntero del destino de exclusión no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2436">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2437">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2437">Allowed From</span></span>

<span data-ttu-id="bdbe0-2438">Inicialización, ISR, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2438">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2439">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2439">Example</span></span>

```C
ULONGexcluded_cores;
/* Retrieve the core exclusion for "Thread 0". */
tx_thread_smp_core_exclude_get(&thread_0, &excluded_cores);
```

### <a name="see-also"></a><span data-ttu-id="bdbe0-2440">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2440">See Also</span></span>

- <span data-ttu-id="bdbe0-2441">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2441">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="bdbe0-2442">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2442">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_get"></a><span data-ttu-id="bdbe0-2443">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2443">tx_thread_smp_core_get</span></span>

<span data-ttu-id="bdbe0-2444">Recupera el núcleo que se está ejecutando actualmente del autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2444">Retrieve currently executing core of caller</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2445">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2445">Prototype</span></span>

```C
UINT  tx_thread_smp_core_get(void);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2446">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2446">Description</span></span>

<span data-ttu-id="bdbe0-2447">Esta función devuelve el identificador del núcleo que ejecuta este servicio.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2447">This function returns the core ID of the core executing this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2448">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2448">Parameters</span></span>

<span data-ttu-id="bdbe0-2449">Ninguno</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2449">None</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2450">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2450">Return Values</span></span>

- <span data-ttu-id="bdbe0-2451">core_id: identificador del núcleo que se está ejecutando actualmente, de 0 a TX_THREAD_SMP_MAX_CORES-1.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2451">core_id: ID of currently executing core, (0 through TX_THREAD_SMP_MAX_CORES-1)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2452">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2452">Allowed From</span></span>

<span data-ttu-id="bdbe0-2453">Inicialización, ISR, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2453">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2454">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2454">Example</span></span>

```C
UINTcore;
/* Pickup the currently executing core. */
core = tx_thread_smp_core_get();

/* At this point, “core” contains the executing core ID. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2455">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2455">See Also</span></span>

- <span data-ttu-id="bdbe0-2456">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2456">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="bdbe0-2457">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2457">tx_thread_smp_core_exclude_get</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="bdbe0-2458">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2458">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="bdbe0-2459">Registra una devolución de llamada de notificación de error de la pila de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2459">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2460">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2460">Prototype</span></span>

```C
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```
### <a name="description"></a><span data-ttu-id="bdbe0-2461">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2461">Description</span></span>

<span data-ttu-id="bdbe0-2462">Este servicio registra una función de devolución de llamada de notificación para controlar los errores de la pila de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2462">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="bdbe0-2463">Cuando ThreadX SMP detecta un error en la pila de subprocesos durante la ejecución, llama a esta función de notificación para procesar el error.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2463">When ThreadX SMP detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="bdbe0-2464">La aplicación es la única que define el procesamiento del error.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2464">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="bdbe0-2465">Se puede realizar cualquier acción, desde suspender el subproceso infractor hasta restablecer todo el sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2465">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2466">La biblioteca de ThreadX SMP se debe compilar con **TX_ENABLE_STACK_CHECKING** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2466">The ThreadX SMP library must be built with **TX_ENABLE_STACK_CHECKING** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2467">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2467">Parameters</span></span>

- <span data-ttu-id="bdbe0-2468">**error_handler**: puntero a la función de control de errores de la pila de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2468">**error_handler**: Pointer to application’s stack error handling function.</span></span> <span data-ttu-id="bdbe0-2469">Si este valor es TX_NULL, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2469">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2470">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2470">Return Values</span></span>

- <span data-ttu-id="bdbe0-2471">**TX_SUCCESS**: (0x00) subproceso restablecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2471">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="bdbe0-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2473">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2473">Allowed From</span></span>

<span data-ttu-id="bdbe0-2474">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2474">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2475">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2475">Example</span></span>

```C
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX SMP
   so that thread stack errors can be handled by the application. */
status =  tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2476">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2476">See Also</span></span>

- <span data-ttu-id="bdbe0-2477">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2477">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2478">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2478">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2479">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2479">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2480">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2480">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2481">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2481">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2482">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2482">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2483">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2483">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2484">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2484">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2485">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2485">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2486">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2486">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2487">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2487">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2488">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2488">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2489">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2489">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2490">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2490">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2491">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2491">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2492">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2492">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2493">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2493">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="bdbe0-2494">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2494">tx_thread_suspend</span></span>

<span data-ttu-id="bdbe0-2495">Suspende un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2495">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2496">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2496">Prototype</span></span>

```C
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2497">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2497">Description</span></span>

<span data-ttu-id="bdbe0-2498">Este servicio suspende el subproceso de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2498">This service suspends the specified application thread.</span></span> <span data-ttu-id="bdbe0-2499">Un subproceso puede llamar a este servicio para suspenderse a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2499">A thread may call this service to suspend itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2500">Si el subproceso especificado ya está suspendido por otra razón, esta suspensión se retiene internamente hasta que se levanta la suspensión anterior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2500">If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted.</span></span> <span data-ttu-id="bdbe0-2501">Cuando esto sucede, se lleva a cabo esta suspensión incondicional del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2501">When that happens, this unconditional suspension of the specified thread is performed.</span></span> <span data-ttu-id="bdbe0-2502">Las demás solicitudes de suspensión incondicional no tienen ningún efecto.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2502">Further unconditional suspension requests have no effect.</span></span>

<span data-ttu-id="bdbe0-2503">Tras la suspensión del subproceso, este debe reanudarse mediante ***tx_thread_resume*** para volver a ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2503">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

## <a name="parameters"></a><span data-ttu-id="bdbe0-2504">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2504">Parameters</span></span>

- <span data-ttu-id="bdbe0-2505">**thread_ptr**: puntero a un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2505">**thread_ptr**: Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2506">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2506">Return Values</span></span>

- <span data-ttu-id="bdbe0-2507">**TX_SUCCESS**: (0x00) subproceso suspendido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2507">**TX_SUCCESS**: (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="bdbe0-2508">TX_THREAD_ERROR: (0x0E) puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2508">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2509">**TX_SUSPEND_ERROR**: (0x14) el subproceso especificado se encuentra en un estado finalizado o completado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2509">**TX_SUSPEND_ERROR**: (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="bdbe0-2510">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2510">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2511">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2511">Allowed From</span></span>

<span data-ttu-id="bdbe0-2512">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2512">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2513">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2513">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2514">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2514">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2515">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2515">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   unconditionally suspended. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2516">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2516">See Also</span></span>

- <span data-ttu-id="bdbe0-2517">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2517">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2518">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2518">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2519">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2519">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2520">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2520">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2521">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2521">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2522">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2522">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2523">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2523">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2524">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2524">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2525">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2525">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2526">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2526">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2527">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2527">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2528">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2528">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2529">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2529">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2530">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2530">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2531">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2531">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2532">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2532">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2533">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2533">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="bdbe0-2534">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2534">tx_thread_terminate</span></span>

<span data-ttu-id="bdbe0-2535">Finaliza un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2535">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2536">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2536">Prototype</span></span>

```C
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2537">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2537">Description</span></span>

<span data-ttu-id="bdbe0-2538">Este servicio finaliza el subproceso de aplicación especificado, independientemente de si está suspendido o no.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2538">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="bdbe0-2539">Un subproceso puede llamar a este servicio para finalizarse a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2539">A thread may call this service to terminate itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2540">Tras la finalización del subproceso, este debe restablecerse para que se pueda ejecutar de nuevo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2540">After being terminated, the thread must be reset for it to execute again.</span></span>

> [!WARNING]
> <span data-ttu-id="bdbe0-2541">Es responsabilidad de la aplicación asegurarse de que el subproceso está en un estado adecuado para la terminación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2541">It is the application's responsibility to ensure the thread is in a state suitable for termination.</span></span> <span data-ttu-id="bdbe0-2542">Por ejemplo, un subproceso no debe terminarse durante el procesamiento de aplicaciones críticas o dentro de otros componentes de middleware, donde podría dejar ese procesamiento en un estado desconocido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2542">For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2543">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2543">Parameters</span></span>

- <span data-ttu-id="bdbe0-2544">**thread_ptr**: puntero a un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2544">**thread_ptr**: Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2545">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2545">Return Values</span></span>

- <span data-ttu-id="bdbe0-2546">**TX_SUCCESS**: (0x00) subproceso finalizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2546">**TX_SUCCESS**: (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="bdbe0-2547">TX_THREAD_ERROR: (0x0E) puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2547">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2548">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2548">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2549">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2549">Allowed From</span></span>

<span data-ttu-id="bdbe0-2550">Subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2550">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2551">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2551">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2552">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2552">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2553">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2553">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Terminate the thread represented by "my_thread". */
status =  tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
   and cannot execute again until it is reset. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2554">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2554">See Also</span></span>

- <span data-ttu-id="bdbe0-2555">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2555">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2556">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2556">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2557">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2557">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2558">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2558">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2559">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2559">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2560">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2560">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2561">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2561">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2562">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2562">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2563">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2563">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2564">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2564">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2565">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2565">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2566">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2566">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2567">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2567">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2568">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2568">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2569">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2569">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2570">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2570">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="bdbe0-2571">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2571">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="bdbe0-2572">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2572">tx_thread_time_slice_change</span></span>

<span data-ttu-id="bdbe0-2573">Cambia la porción de tiempo de un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2573">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2574">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2574">Prototype</span></span>

```C
UINT tx_thread_time_slice_change(TX_THREAD *thread_ptr,
                          ULONG new_time_slice, ULONG *old_time_slice);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2575">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2575">Description</span></span>

<span data-ttu-id="bdbe0-2576">Este servicio cambia la porción de tiempo del subproceso de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2576">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="bdbe0-2577">Cuando se selecciona una porción de tiempo para un subproceso, se garantiza que no se ejecutará más que el número especificado de tics de temporizador antes de que otros subprocesos con prioridades iguales o superiores tengan la posibilidad de ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2577">Selecting a time-slice for a thread insures that it won’t execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2578">El uso del umbral de adelantamiento deshabilita la segmentación temporal en el subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2578">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2579">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2579">Parameters</span></span>

- <span data-ttu-id="bdbe0-2580">**thread_ptr**: puntero a un subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2580">**thread_ptr**: Pointer to application thread.</span></span>
- <span data-ttu-id="bdbe0-2581">**new_time_slice**: nuevo valor de porción de tiempo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2581">**new_time_slice**: New time slice value.</span></span> <span data-ttu-id="bdbe0-2582">Los valores válidos incluyen TX_NO_TIME_SLICE y los valores numéricos de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2582">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="bdbe0-2583">**old_time_slice**: puntero a la ubicación para almacenar el valor de la porción de tiempo anterior del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2583">**old_time_slice**: Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2584">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2584">Return Values</span></span>

- <span data-ttu-id="bdbe0-2585">**TX_SUCCESS**: (0x00) porción de tiempo cambiada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2585">**TX_SUCCESS**: (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="bdbe0-2586">TX_THREAD_ERROR: (0x0E) puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2586">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2587">TX_PTR_ERROR: (0x03) puntero no válido a la ubicación de almacenamiento de la porción de tiempo anterior.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2587">TX_PTR_ERROR: (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="bdbe0-2588">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2588">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2589">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2589">Allowed From</span></span>

<span data-ttu-id="bdbe0-2590">Subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2590">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2591">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2591">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2592">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2592">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2593">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2593">Example</span></span>

```C
TX_THREAD     my_thread;
ULONG         my_old_time_slice;
UINT          status;

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
### <a name="see-also"></a><span data-ttu-id="bdbe0-2594">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2594">See Also</span></span>

- <span data-ttu-id="bdbe0-2595">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2595">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2596">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2596">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2597">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2597">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2598">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2598">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2599">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2599">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2600">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2600">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2601">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2601">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2602">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2602">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2603">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2603">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2604">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2604">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2605">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2605">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2606">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2606">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2607">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2607">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2608">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2608">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2609">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2609">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2610">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2610">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2611">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2611">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="bdbe0-2612">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2612">tx_thread_wait_abort</span></span>

<span data-ttu-id="bdbe0-2613">Anula la suspensión de un subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2613">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2614">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2614">Prototype</span></span>

```C
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="bdbe0-2615">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2615">Description</span></span>

<span data-ttu-id="bdbe0-2616">Este servicio anula cualquier tipo de suspensión de objeto del subproceso especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2616">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="bdbe0-2617">Si se anula la espera, se devuelve un valor TX_WAIT_ABORTED desde el servicio en el que el subproceso estaba esperando.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2617">If the wait is aborted, a TX_WAIT_ABORTED value is returned from the service that the thread was waiting on.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2618">Este servicio no libera la suspensión explícita realizada por el servicio tx_thread_suspend.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2618">This service does not release explicit suspension that is made by the tx_thread_suspend service.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2619">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2619">Parameters</span></span>

- <span data-ttu-id="bdbe0-2620">**thread_ptr**: puntero a un subproceso de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2620">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2621">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2621">Return Values</span></span>

- <span data-ttu-id="bdbe0-2622">**TX_SUCCESS**: (0x00) espera del subproceso anulada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2622">**TX_SUCCESS**: (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="bdbe0-2623">TX_THREAD_ERROR: (0x0E) puntero del subproceso de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2623">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="bdbe0-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) el subproceso especificado no está en estado de espera.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2625">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2625">Allowed From</span></span>

<span data-ttu-id="bdbe0-2626">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2626">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2627">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2627">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2628">Sí</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2628">Yes</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2629">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2629">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Abort the suspension condition of "my_thread." */
status =  tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
   again, with a return value showing its suspension
   was aborted (TX_WAIT_ABORTED). */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2630">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2630">See Also</span></span>

- <span data-ttu-id="bdbe0-2631">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2631">tx_thread_create</span></span>
- <span data-ttu-id="bdbe0-2632">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2632">tx_thread_delete</span></span>
- <span data-ttu-id="bdbe0-2633">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2633">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="bdbe0-2634">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2634">tx_thread_identify</span></span>
- <span data-ttu-id="bdbe0-2635">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2635">tx_thread_info_get</span></span>
- <span data-ttu-id="bdbe0-2636">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2636">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2637">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2637">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="bdbe0-2638">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2638">tx_thread_preemption_change</span></span>
- <span data-ttu-id="bdbe0-2639">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2639">tx_thread_priority_change</span></span>
- <span data-ttu-id="bdbe0-2640">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2640">tx_thread_relinquish</span></span>
- <span data-ttu-id="bdbe0-2641">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2641">tx_thread_reset</span></span>
- <span data-ttu-id="bdbe0-2642">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2642">tx_thread_resume</span></span>
- <span data-ttu-id="bdbe0-2643">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2643">tx_thread_sleep</span></span>
- <span data-ttu-id="bdbe0-2644">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2644">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="bdbe0-2645">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2645">tx_thread_suspend</span></span>
- <span data-ttu-id="bdbe0-2646">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2646">tx_thread_terminate</span></span>
- <span data-ttu-id="bdbe0-2647">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2647">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="bdbe0-2648">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2648">tx_time_get</span></span>

<span data-ttu-id="bdbe0-2649">Recupera la hora actual.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2649">Retrieves the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2650">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2650">Prototype</span></span>

```C
ULONG tx_time_get(VOID);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2651">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2651">Description</span></span>

<span data-ttu-id="bdbe0-2652">Este servicio devuelve el contenido del reloj interno del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2652">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="bdbe0-2653">Cada tic del temporizador aumenta el reloj interno del sistema en uno.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2653">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="bdbe0-2654">El reloj del sistema se establece en cero durante la inicialización y se puede cambiar a un valor específico mediante el servicio ***tx_time_set***.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2654">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2655">El tiempo real que representa cada tic del temporizador es específico de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2655">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2656">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2656">Parameters</span></span>

<span data-ttu-id="bdbe0-2657">Ninguno</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2657">None</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2658">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2658">Return Values</span></span>

- <span data-ttu-id="bdbe0-2659">tics del reloj del sistema: valor del reloj interno del sistema de ejecución libre.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2659">system clock ticks: Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2660">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2660">Allowed From</span></span>

<span data-ttu-id="bdbe0-2661">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2661">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2662">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2662">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2663">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2663">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2664">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2664">Example</span></span>

```C
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time =  tx_time_get();

/* Current time now contains a copy of the internal system
   clock. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2665">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2665">See Also</span></span>

- <span data-ttu-id="bdbe0-2666">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2666">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="bdbe0-2667">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2667">tx_time_set</span></span>

<span data-ttu-id="bdbe0-2668">Establece la hora actual.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2668">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2669">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2669">Prototype</span></span>

```C
VOID tx_time_set(ULONG new_time);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2670">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2670">Description</span></span>

<span data-ttu-id="bdbe0-2671">Este servicio establece el reloj interno del sistema en el valor especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2671">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="bdbe0-2672">Cada tic del temporizador aumenta el reloj interno del sistema en uno.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2672">Each timer-tick increases the internal system clock by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2673">El tiempo real que representa cada tic del temporizador es específico de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2673">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2674">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2674">Parameters</span></span>

- <span data-ttu-id="bdbe0-2675">**new_time**: hora nueva que se va a establecer en el reloj del sistema. Los valores válidos se sitúan entre 0 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2675">**new_time**: New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2676">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2676">Return Values</span></span>

<span data-ttu-id="bdbe0-2677">Ninguno</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2677">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2678">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2678">Allowed From</span></span>

<span data-ttu-id="bdbe0-2679">Subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2679">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2680">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2680">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2681">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2681">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2682">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2682">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
   interrupt. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2683">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2683">See Also</span></span>

- <span data-ttu-id="bdbe0-2684">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2684">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="bdbe0-2685">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2685">tx_timer_activate</span></span>

<span data-ttu-id="bdbe0-2686">Activa un temporizador de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2686">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2687">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2687">Prototype</span></span>

```C
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2688">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2688">Description</span></span>

<span data-ttu-id="bdbe0-2689">Este servicio activa el temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2689">This service activates the specified application timer.</span></span> <span data-ttu-id="bdbe0-2690">Las rutinas de expiración de los temporizadores que expiran al mismo tiempo se ejecutan en el orden en el que se activaron.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2690">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="bdbe0-2691">Un temporizador monoestable expirado se debe restablecer mediante **tx_timer_change** antes de que se pueda volver a activar.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2691">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2692">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2692">Parameters</span></span>

- <span data-ttu-id="bdbe0-2693">**timer_ptr**: puntero a un temporizador de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2693">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2694">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2694">Return Values</span></span>

- <span data-ttu-id="bdbe0-2695">**TX_SUCCESS**: (0x00) temporizador de aplicación activado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2695">**TX_SUCCESS**: (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="bdbe0-2696">**TX_TIMER_ERROR**: (0x15) puntero del temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2696">**TX_TIMER_ERROR**: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="bdbe0-2697">**TX_ACTIVATE_ERROR**: (0x17) el temporizador ya estaba activo o es un temporizador monoestable que ya ha expirado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2697">**TX_ACTIVATE_ERROR**: (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2698">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2698">Allowed From</span></span>

<span data-ttu-id="bdbe0-2699">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2699">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2700">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2700">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2701">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2701">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2702">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2702">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Activate an application timer. Assume that the
   application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now active. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2703">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2703">See Also</span></span>

- <span data-ttu-id="bdbe0-2704">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2704">tx_timer_change</span></span>
- <span data-ttu-id="bdbe0-2705">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2705">tx_timer_create</span></span>
- <span data-ttu-id="bdbe0-2706">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2706">tx_timer_deactivate</span></span>
- <span data-ttu-id="bdbe0-2707">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2707">tx_timer_delete</span></span>
- <span data-ttu-id="bdbe0-2708">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2708">tx_timer_info_get</span></span>
- <span data-ttu-id="bdbe0-2709">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2709">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2710">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2710">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="bdbe0-2711">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2711">tx_timer_change</span></span>

<span data-ttu-id="bdbe0-2712">Cambia un temporizador de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2712">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2713">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2713">Prototype</span></span>

```C
UINT tx_timer_change(TX_TIMER *timer_ptr,
                          ULONG initial_ticks, ULONG reschedule_ticks);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2714">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2714">Description</span></span>

<span data-ttu-id="bdbe0-2715">Este servicio cambia las características de expiración del temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2715">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="bdbe0-2716">El temporizador debe desactivarse antes de llamar a este servicio.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2716">The timer must be deactivated prior to calling this service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2717">Para poder iniciar el temporizador de nuevo después de este servicio, es necesario llamar al servicio **tx_timer_activate**.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2717">A call to the **tx_timer_activate** service is required after this service in order to start the timer again.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2718">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2718">Parameters</span></span>

- <span data-ttu-id="bdbe0-2719">**timer_ptr**: puntero al bloque de control de un temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2719">**timer_ptr**: Pointer to a timer control block.</span></span>
- <span data-ttu-id="bdbe0-2720">**initial_ticks**: especifica el número inicial de tics para la expiración del temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2720">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="bdbe0-2721">Los valores válidos se sitúan entre 1 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2721">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="bdbe0-2722">**reschedule_ticks**: especifica el número de tics para todas las expiraciones del temporizador después de la primera.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2722">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="bdbe0-2723">Un cero en este parámetro convierte el temporizador en monoestable.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2723">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="bdbe0-2724">De lo contrario, en los temporizadores periódicos, los valores válidos se sitúan entre 1 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2724">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="bdbe0-2725">Un temporizador monoestable expirado se debe restablecer mediante **tx_timer_change** antes de que se pueda volver a activar.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2725">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2726">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2726">Return Values</span></span>

- <span data-ttu-id="bdbe0-2727">**TX_SUCCESS**: (0x00) temporizador de aplicación cambiado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2727">**TX_SUCCESS**: (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="bdbe0-2728">TX_TIMER_ERROR: (0x15) puntero del temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2728">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="bdbe0-2729">TX_TICK_ERROR: (0x16) se ha proporcionado un valor no válido (cero) de tics iniciales.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2729">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="bdbe0-2730">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2730">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2731">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2731">Allowed From</span></span>

<span data-ttu-id="bdbe0-2732">Subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2732">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2733">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2733">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2734">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2734">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2735">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2735">Example</span></span>

```C
TX_TIMER         my_timer;
UINT             status;

/* Change a previously created and now deactivated timer
   to expire every 50 timer ticks, including the initial
   expiration. */
status =  tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
   changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2736">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2736">See Also</span></span>

- <span data-ttu-id="bdbe0-2737">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2737">tx_timer_activate</span></span>
- <span data-ttu-id="bdbe0-2738">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2738">tx_timer_create</span></span>
- <span data-ttu-id="bdbe0-2739">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2739">tx_timer_deactivate</span></span>
- <span data-ttu-id="bdbe0-2740">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2740">tx_timer_delete</span></span>
- <span data-ttu-id="bdbe0-2741">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2741">tx_timer_info_get</span></span>
- <span data-ttu-id="bdbe0-2742">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2742">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2743">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2743">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="bdbe0-2744">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2744">tx_timer_create</span></span>

<span data-ttu-id="bdbe0-2745">Crea un temporizador de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2745">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2746">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2746">Prototype</span></span>

```C
UINT tx_timer_create(TX_TIMER *timer_ptr, CHAR *name_ptr,
                          VOID (*expiration_function)(ULONG),
                          ULONG expiration_input, ULONG initial_ticks,
                          ULONG reschedule_ticks, UINT auto_activate)
```
### <a name="description"></a><span data-ttu-id="bdbe0-2747">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2747">Description</span></span>

<span data-ttu-id="bdbe0-2748">Este servicio crea un temporizador de aplicación periódico con la función de expiración especificada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2748">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2749">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2749">Parameters</span></span>

- <span data-ttu-id="bdbe0-2750">**timer_ptr**: puntero al bloque de control de un temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2750">**timer_ptr**: Pointer to a timer control block</span></span>
- <span data-ttu-id="bdbe0-2751">**name_ptr**: puntero al nombre del temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2751">**name_ptr**: Pointer to the name of the timer.</span></span>
- <span data-ttu-id="bdbe0-2752">**expiration_function**: función de la aplicación a la que se va a llamar cuando expire el temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2752">**expiration_function**: Application function to call when the timer expires.</span></span>
- <span data-ttu-id="bdbe0-2753">**expiration_input**: entrada que se va a pasar a la función de expiración cuando expire el temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2753">**expiration_input**: Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="bdbe0-2754">**initial_ticks**: especifica el número inicial de tics para la expiración del temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2754">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="bdbe0-2755">Los valores válidos se sitúan entre 1 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2755">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="bdbe0-2756">**reschedule_ticks**: especifica el número de tics para todas las expiraciones del temporizador después de la primera.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2756">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="bdbe0-2757">Un cero en este parámetro convierte el temporizador en monoestable.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2757">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="bdbe0-2758">De lo contrario, en los temporizadores periódicos, los valores válidos se sitúan entre 1 y 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2758">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="bdbe0-2759">Cuando un temporizador monoestable expira, se debe restablecer mediante tx_timer_change antes de que se pueda volver a activar.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2759">After a one-shot timer expires, it must be reset via tx_timer_change before it can be activated again.</span></span>

- <span data-ttu-id="bdbe0-2760">**auto_activate**: determina si el temporizador se activa automáticamente durante la creación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2760">**auto_activate**: Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="bdbe0-2761">Si este valor es **TX_AUTO_ACTIVATE** (0x01), el temporizador se activa.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2761">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="bdbe0-2762">De lo contrario, si se selecciona el valor **TX_NO_ACTIVATE** (0x00), el temporizador se crea en un estado no activo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2762">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="bdbe0-2763">En este caso, es necesario llamar después al servicio **_tx_timer_activate_** para que el temporizador se inicie.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2763">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2764">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2764">Return Values</span></span>

- <span data-ttu-id="bdbe0-2765">**TX_SUCCESS**: (0x00) temporizador de aplicación creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2765">**TX_SUCCESS**: (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="bdbe0-2766">TX_TIMER_ERROR: (0x15) puntero del temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2766">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="bdbe0-2767">El puntero es NULL o el temporizador ya se ha creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2767">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="bdbe0-2768">TX_TICK_ERROR: (0x16) se ha proporcionado un valor no válido (cero) de tics iniciales.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2768">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="bdbe0-2769">TX_ACTIVATE_ERROR: (0x17) la activación seleccionada no es válida.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2769">TX_ACTIVATE_ERROR: (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="bdbe0-2770">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2770">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2771">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2771">Allowed From</span></span>

<span data-ttu-id="bdbe0-2772">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2772">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2773">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2773">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2774">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2774">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2775">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2775">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Create an application timer that executes
   "my_timer_function" after 100 ticks initially and then
   after every 25 ticks. This timer is specified to start
   immediately! */
status =  tx_timer_create(&my_timer,"my_timer_name",
                my_timer_function, 0x1234, 100, 25,
                TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
   be called 100 timer ticks later and then called every
   25 timer ticks. Note that the value 0x1234 is passed to
   my_timer_function every time it is called. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2776">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2776">See Also</span></span>

- <span data-ttu-id="bdbe0-2777">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2777">tx_timer_activate</span></span>
- <span data-ttu-id="bdbe0-2778">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2778">tx_timer_change</span></span>
- <span data-ttu-id="bdbe0-2779">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2779">tx_timer_deactivate</span></span>
- <span data-ttu-id="bdbe0-2780">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2780">tx_timer_delete</span></span>
- <span data-ttu-id="bdbe0-2781">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2781">tx_timer_info_get</span></span>
- <span data-ttu-id="bdbe0-2782">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2782">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2783">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2783">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="bdbe0-2784">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2784">tx_timer_deactivate</span></span>

<span data-ttu-id="bdbe0-2785">Desactiva un temporizador de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2785">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2786">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2786">Prototype</span></span>

```C
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="bdbe0-2787">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2787">Description</span></span>

<span data-ttu-id="bdbe0-2788">Este servicio desactiva el temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2788">This service deactivates the specified application timer.</span></span> <span data-ttu-id="bdbe0-2789">Si el temporizador ya está desactivado, este servicio no tiene ningún efecto.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2789">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2790">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2790">Parameters</span></span> 

- <span data-ttu-id="bdbe0-2791">**timer_ptr**: puntero a un temporizador de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2791">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2792">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2792">Return Values</span></span>

- <span data-ttu-id="bdbe0-2793">**TX_SUCCESS**: (0x00) temporizador de aplicación desactivado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2793">**TX_SUCCESS**: (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="bdbe0-2794">TX_TIMER_ERROR: (0x15) puntero del temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2794">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2795">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2795">Allowed From</span></span>

<span data-ttu-id="bdbe0-2796">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2796">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2797">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2797">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2798">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2798">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2799">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2799">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Deactivate an application timer. Assume that the
   application timer has already been created. */
status =  tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now deactivated. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2800">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2800">See Also</span></span>

- <span data-ttu-id="bdbe0-2801">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2801">tx_timer_activate</span></span>
- <span data-ttu-id="bdbe0-2802">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2802">tx_timer_change</span></span>
- <span data-ttu-id="bdbe0-2803">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2803">tx_timer_create</span></span>
- <span data-ttu-id="bdbe0-2804">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2804">tx_timer_delete</span></span>
- <span data-ttu-id="bdbe0-2805">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2805">tx_timer_info_get</span></span>
- <span data-ttu-id="bdbe0-2806">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2806">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2807">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2807">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="bdbe0-2808">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2808">tx_timer_delete</span></span>

<span data-ttu-id="bdbe0-2809">Elimina un temporizador de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2809">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2810">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2810">Prototype</span></span>

```C
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2811">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2811">Description</span></span>

<span data-ttu-id="bdbe0-2812">Este servicio elimina el temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2812">This service deletes the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2813">Es responsabilidad de la aplicación impedir el uso de un temporizador eliminado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2813">It is the application’s responsibility to prevent use of a deleted timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2814">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2814">Parameters</span></span> 

- <span data-ttu-id="bdbe0-2815">**timer_ptr**: puntero a un temporizador de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2815">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2816">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2816">Return Values</span></span>

- <span data-ttu-id="bdbe0-2817">**TX_SUCCESS**: (0x00) temporizador de aplicación eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2817">**TX_SUCCESS**: (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="bdbe0-2818">TX_TIMER_ERROR: (0x15) puntero del temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2818">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="bdbe0-2819">TX_CALLER_ERROR: (0x13) el autor de la llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2819">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2820">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2820">Allowed From</span></span>

<span data-ttu-id="bdbe0-2821">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2821">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2822">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2822">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2823">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2823">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2824">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2824">Example</span></span>

```c
TX_TIMER     my_timer;
UINT         status;

/* Delete application timer. Assume that the application
   timer has already been created. */
status =  tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2825">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2825">See Also</span></span>

- <span data-ttu-id="bdbe0-2826">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2826">tx_timer_activate</span></span>
- <span data-ttu-id="bdbe0-2827">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2827">tx_timer_change</span></span>
- <span data-ttu-id="bdbe0-2828">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2828">tx_timer_create</span></span>
- <span data-ttu-id="bdbe0-2829">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2829">tx_timer_deactivate</span></span>
- <span data-ttu-id="bdbe0-2830">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2830">tx_timer_info_get</span></span>
- <span data-ttu-id="bdbe0-2831">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2831">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2832">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2832">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="bdbe0-2833">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2833">tx_timer_info_get</span></span>

<span data-ttu-id="bdbe0-2834">Recupera información acerca de un temporizador de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2834">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2835">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2835">Prototype</span></span>

```C
UINT tx_timer_info_get(TX_TIMER *timer_ptr, CHAR **name,
                          UINT *active, ULONG *remaining_ticks,
                          ULONG *reschedule_ticks,
                          TX_TIMER **next_timer)
```
### <a name="description"></a><span data-ttu-id="bdbe0-2836">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2836">Description</span></span>

<span data-ttu-id="bdbe0-2837">Este servicio recupera información sobre el temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2837">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2838">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2838">Parameters</span></span>

- <span data-ttu-id="bdbe0-2839">**timer_ptr**: puntero a un temporizador de aplicación creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2839">**timer_ptr**: Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="bdbe0-2840">**name**: puntero al destino del puntero al nombre del temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2840">**name**: Pointer to destination for the pointer to the timer’s name.</span></span>
- <span data-ttu-id="bdbe0-2841">**active**: puntero al destino de la indicación de temporizador activo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2841">**active**: Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="bdbe0-2842">Si el temporizador está inactivo o se llama a este servicio desde el propio temporizador, se devuelve un valor TX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2842">If the timer is inactive or this service is called from the timer itself, a TX_FALSE value is returned.</span></span> <span data-ttu-id="bdbe0-2843">De lo contrario, si el temporizador está activo, se devuelve un valor TX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2843">Otherwise, if the timer is active, a TX_TRUE value is returned.</span></span>
- <span data-ttu-id="bdbe0-2844">**remaining_ticks**: puntero al destino del número de tics de temporizador que quedan antes de que expire.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2844">**remaining_ticks**: Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="bdbe0-2845">**reschedule_ticks**: puntero al destino del número de tics de temporizador que se usarán para volver a programarlo automáticamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2845">**reschedule_ticks**: Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="bdbe0-2846">Si el valor es cero, el temporizador es monoestable y no se volverá a programar.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2846">If the value is zero, then the timer is a one-shot and won’t be rescheduled.</span></span>
- <span data-ttu-id="bdbe0-2847">**next_timer**: puntero al destino del puntero del siguiente temporizador de aplicación creado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2847">**next_timer**: Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="bdbe0-2848">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2848">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2849">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2849">Return Values</span></span>

- <span data-ttu-id="bdbe0-2850">**TX_SUCCESS**: (0x00) información del temporizador recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2850">**TX_SUCCESS**: (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="bdbe0-2851">TX_TIMER_ERROR: (0x15) puntero del temporizador de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2851">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2852">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2852">Allowed From</span></span>

<span data-ttu-id="bdbe0-2853">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2853">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="bdbe0-2854">Adelantamiento posible</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2854">Preemption Possible</span></span>

<span data-ttu-id="bdbe0-2855">No</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2855">No</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2856">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2856">Example</span></span>

```C
TX_TIMER     my_timer;
CHAR         *name;
UINT         active;
ULONG        remaining_ticks;
ULONG        reschedule_ticks;
TX_TIMER     *next_timer;
UINT         status;

/* Retrieve information about the previously created
   application timer "my_timer." */
status =  tx_timer_info_get(&my_timer, &name,
                          &active,&remaining_ticks,
                &reschedule_ticks,
                         &next_timer);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2857">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2857">See Also</span></span>

- <span data-ttu-id="bdbe0-2858">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2858">tx_timer_activate</span></span>
- <span data-ttu-id="bdbe0-2859">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2859">tx_timer_change</span></span>
- <span data-ttu-id="bdbe0-2860">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2860">tx_timer_create</span></span>
- <span data-ttu-id="bdbe0-2861">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2861">tx_timer_deactivate</span></span>
- <span data-ttu-id="bdbe0-2862">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2862">tx_timer_delete</span></span>
- <span data-ttu-id="bdbe0-2863">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2863">tx_timer_info_get</span></span>
- <span data-ttu-id="bdbe0-2864">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2864">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="bdbe0-2865">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2865">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="bdbe0-2866">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2866">tx_timer_performance_info_get</span></span> 

<span data-ttu-id="bdbe0-2867">Obtiene información acerca del rendimiento de un temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2867">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2868">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2868">Prototype</span></span>

```C
UINT  tx_timer_performance_info_get(TX_TIMER *timer_ptr,
        ULONG *activates, ULONG *reactivates,
        ULONG *deactivates, ULONG *expirations,
        ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2869">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2869">Description</span></span>

<span data-ttu-id="bdbe0-2870">Este servicio recupera información sobre el rendimiento del temporizador de aplicación especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2870">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2871">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_TIMER_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2871">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2872">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2872">Parameters</span></span> 

- <span data-ttu-id="bdbe0-2873">**timer_ptr**: puntero a un temporizador creado previamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2873">**timer_ptr**: Pointer to previously created timer.</span></span>
- <span data-ttu-id="bdbe0-2874">**activates**: puntero al destino del número de solicitudes de activación realizadas en este temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2874">**activates**: Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="bdbe0-2875">**reactivates**: puntero al destino del número de reactivaciones automáticas realizadas en este temporizador periódico.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2875">**reactivates**: Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="bdbe0-2876">**deactivates**: puntero al destino del número de solicitudes de desactivación realizadas en este temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2876">**deactivates**: Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="bdbe0-2877">**expirations**: puntero al destino del número de expiraciones de este temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2877">**expirations**: Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="bdbe0-2878">**expiration_adjusts**: puntero al destino del número de ajustes de expiración internos realizados en este temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2878">**expiration_adjusts**: Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="bdbe0-2879">Estos ajustes se realizan en el procesamiento de interrupciones del temporizador para los temporizadores mayores que el tamaño predeterminado de la lista de temporizadores (de manera predeterminada, los temporizadores con expiraciones superiores a 32 tics).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2879">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2880">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2880">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2881">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2881">Return Values</span></span>

- <span data-ttu-id="bdbe0-2882">**TX_SUCCESS**: (0x00) rendimiento del temporizador obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2882">**TX_SUCCESS**: (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="bdbe0-2883">**TX_PTR_ERROR**: (0x03) puntero del temporizador no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2883">**TX_PTR_ERROR**: (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="bdbe0-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2885">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2885">Allowed From</span></span>

<span data-ttu-id="bdbe0-2886">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2886">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2887">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2887">Example</span></span>

```C
TX_TIMER     my_timer;
ULONG        activates;
ULONG        reactivates;
ULONG        deactivates;
ULONG        expirations;
ULONG        expiration_adjusts;

/* Retrieve performance information on the previously created
   timer.  */
status =  tx_timer_performance_info_get(&my_timer, &activates,
                &reactivates,&deactivates, &expirations,
                &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2888">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2888">See Also</span></span>

- <span data-ttu-id="bdbe0-2889">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2889">tx_timer_activate</span></span>
- <span data-ttu-id="bdbe0-2890">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2890">tx_timer_change</span></span>
- <span data-ttu-id="bdbe0-2891">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2891">tx_timer_create</span></span>
- <span data-ttu-id="bdbe0-2892">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2892">tx_timer_deactivate</span></span>
- <span data-ttu-id="bdbe0-2893">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2893">tx_timer_delete</span></span>
- <span data-ttu-id="bdbe0-2894">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2894">tx_timer_info_get</span></span>
- <span data-ttu-id="bdbe0-2895">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2895">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="bdbe0-2896">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2896">tx_timer_performance_system_info_get</span></span> 

<span data-ttu-id="bdbe0-2897">Obtiene información acerca del rendimiento de los temporizadores del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2897">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2898">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2898">Prototype</span></span>

```C
UINT  tx_timer_performance_system_info_get(ULONG *activates,
        ULONG *reactivates, ULONG *deactivates,
        ULONG *expirations, ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2899">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2899">Description</span></span>

<span data-ttu-id="bdbe0-2900">Este servicio recupera información sobre el rendimiento de todos los temporizadores de aplicación del sistema.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2900">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2901">La biblioteca y la aplicación de ThreadX SMP se deben compilar con **TX_TIMER_ENABLE_PERFORMANCE_INFO** definido para que este servicio devuelva información sobre el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2901">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2902">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2902">Parameters</span></span>

- <span data-ttu-id="bdbe0-2903">**activates**: puntero al destino del número total de solicitudes de activación realizadas en todos los temporizadores.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2903">**activates**: Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="bdbe0-2904">**reactivates**: puntero al destino del número total de reactivaciones automáticas realizadas en todos los temporizadores periódicos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2904">**reactivates**: Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="bdbe0-2905">**deactivates**: puntero al destino del número total de solicitudes de desactivación realizadas en todos los temporizadores.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2905">**deactivates**: Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="bdbe0-2906">**expirations**: puntero al destino del número total de expiraciones de todos los temporizadores.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2906">**expirations**: Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="bdbe0-2907">**expiration_adjusts**: puntero al destino del número total de ajustes de expiración internos realizados en todos los temporizadores.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2907">**expiration_adjusts**: Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="bdbe0-2908">Estos ajustes se realizan en el procesamiento de interrupciones del temporizador para los temporizadores mayores que el tamaño predeterminado de la lista de temporizadores (de manera predeterminada, los temporizadores con expiraciones superiores a 32 tics).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2908">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2909">La especificación de un valor TX_NULL en cualquier parámetro indica que este no es necesario.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2909">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2910">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2910">Return Values</span></span>

- <span data-ttu-id="bdbe0-2911">**TX_SUCCESS**: (0x00) rendimiento de los temporizadores del sistema obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2911">**TX_SUCCESS**: (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="bdbe0-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) el sistema no se compiló con la información de rendimiento habilitada.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2913">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2913">Allowed From</span></span>

<span data-ttu-id="bdbe0-2914">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2914">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2915">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2915">Example</span></span>

```C
ULONG     activates;
ULONG     reactivates;
ULONG     deactivates;
ULONG     expirations;
ULONG     expiration_adjusts;

/* Retrieve performance information on all previously created
   timers.  */
status =  tx_timer_performance_system_info_get(&activates,
                &reactivates, &deactivates, &expirations,
                &expiration_adjusts);
/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2916">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2916">See Also</span></span>

- <span data-ttu-id="bdbe0-2917">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2917">tx_timer_activate</span></span>
- <span data-ttu-id="bdbe0-2918">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2918">tx_timer_change</span></span>
- <span data-ttu-id="bdbe0-2919">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2919">tx_timer_create</span></span>
- <span data-ttu-id="bdbe0-2920">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2920">tx_timer_deactivate</span></span>
- <span data-ttu-id="bdbe0-2921">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2921">tx_timer_delete</span></span>
- <span data-ttu-id="bdbe0-2922">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2922">tx_timer_info_get</span></span>
- <span data-ttu-id="bdbe0-2923">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2923">tx_timer_performance_info_get</span></span>

## <a name="tx_timer_smp_core_exclude"></a><span data-ttu-id="bdbe0-2924">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2924">tx_timer_smp_core_exclude</span></span>

<span data-ttu-id="bdbe0-2925">Excluye la ejecución del temporizador en un conjunto de núcleos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2925">Exclude timer execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2926">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2926">Prototype</span></span>

```C
UINT  tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2927">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2927">Description</span></span>

<span data-ttu-id="bdbe0-2928">Esta función excluye la ejecución del temporizador especificado de los núcleos especificados en el mapa de bits denominado "*exclusion_map*".</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2928">This function excludes the specified timer from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="bdbe0-2929">Cada bit de "*exclusion_map*" representa un núcleo (el bit 0 representa el núcleo 0, etc.).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2929">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="bdbe0-2930">Si se establece el bit, el núcleo correspondiente se excluye de la ejecución del temporizador especificado.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2930">If the bit is set, the corresponding core is excluded from executing the specified timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdbe0-2931">El uso de exclusiones en el procesador puede provocar un procesamiento adicional de la lógica de asignación de subprocesos a núcleos con el fin de encontrar la correspondencia óptima.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2931">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="bdbe0-2932">Este procesamiento está limitado por el número de subprocesos listos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2932">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2933">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2933">Parameters</span></span>

- <span data-ttu-id="bdbe0-2934">**timer_ptr**: puntero al temporizador para cambiar la exclusión de núcleos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2934">**timer_ptr**: Pointer to timer to change the core exclusion.</span></span>
- <span data-ttu-id="bdbe0-2935">**exclusion_map**: mapa de bits donde un bit establecido indica que se excluye ese núcleo.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2935">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="bdbe0-2936">Si se indica un valor 0, el temporizador se puede ejecutar en cualquier núcleo (es el valor predeterminado).</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2936">Supplying a 0 value enables the timer to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2937">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2937">Return Values</span></span>

- <span data-ttu-id="bdbe0-2938">**TX_SUCCESS**: (0x00) exclusión de núcleos correcta.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2938">**TX_SUCCESS** (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="bdbe0-2939">**TX_TIMER_ERROR** (0x0E) puntero del temporizador no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2939">**TX_TIMER_ERROR** (0x0E) Invalid timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2940">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2940">Allowed From</span></span>

<span data-ttu-id="bdbe0-2941">Inicialización, ISR, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2941">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2942">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2942">Example</span></span>

```C
/* Exclude core 0 for "Timer 0". */
tx_timer_smp_core_exclude(&timer_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="bdbe0-2943">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2943">See Also</span></span>

- <span data-ttu-id="bdbe0-2944">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2944">tx_timer_smp_core_exclude_get</span></span>

## <a name="tx_timer_smp_core_exclude_get"></a><span data-ttu-id="bdbe0-2945">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2945">tx_timer_smp_core_exclude_get</span></span>

<span data-ttu-id="bdbe0-2946">Obtiene la exclusión actual de núcleos del temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2946">Gets the timer's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="bdbe0-2947">Prototipo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2947">Prototype</span></span>

```C
UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="bdbe0-2948">Descripción</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2948">Description</span></span>

<span data-ttu-id="bdbe0-2949">Esta función devuelve la lista de exclusión actual de núcleos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2949">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="bdbe0-2950">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2950">Parameters</span></span>

- <span data-ttu-id="bdbe0-2951">**thread_ptr**: puntero al temporizador del que se va a recuperar la exclusión de núcleos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2951">**timer_ptr**: Pointer to timer from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="bdbe0-2952">**exclusion_map_ptr**: destino del mapa de bits de exclusión actual de núcleos.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2952">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="bdbe0-2953">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2953">Return Values</span></span>

- <span data-ttu-id="bdbe0-2954">TX_SUCCESS: (0x00) recuperación correcta de la exclusión de núcleos del temporizador.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2954">TX_SUCCESS: (0x00) Successful retrieval of timer's core exclusion.</span></span>
- <span data-ttu-id="bdbe0-2955">TX_TIMER_ERROR: (0x0E) puntero del temporizador no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2955">TX_TIMER_ERROR: (0x0E) Invalid timer pointer.</span></span>
- <span data-ttu-id="bdbe0-2956">TX_PTR_ERROR: (0x03) puntero del destino de exclusión no válido.</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2956">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bdbe0-2957">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2957">Allowed From</span></span>

<span data-ttu-id="bdbe0-2958">Inicialización, ISR, subprocesos y temporizadores</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2958">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="bdbe0-2959">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2959">Example</span></span>

```C
ULONGexcluded_cores;

/* Retrieve the core exclusion for "Timer 0". */
tx_timer_smp_core_exclude_get(&timer_0,&excluded_cores);
```
### <a name="see-also"></a><span data-ttu-id="bdbe0-2960">Consulte también</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2960">See Also</span></span>

- <span data-ttu-id="bdbe0-2961">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="bdbe0-2961">tx_timer_smp_core_exclude</span></span>