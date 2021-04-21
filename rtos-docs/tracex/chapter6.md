---
title: 'Capítulo 6: Eventos de seguimiento de Azure RTOS ThreadX'
description: En este capítulo se describen los eventos de Azure RTOS ThreadX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8f0ff03d112597371059d925f64b7511454e123c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815757"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a><span data-ttu-id="058bb-103">Capítulo 6: Eventos de seguimiento de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="058bb-103">Chapter 6 - Azure RTOS ThreadX trace events</span></span>

<span data-ttu-id="058bb-104">En este capítulo se describen los eventos de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="058bb-104">This chapter describes the Azure RTOS ThreadX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="058bb-105">Lista de eventos e iconos</span><span class="sxs-lookup"><span data-stu-id="058bb-105">List of Events and Icons</span></span>

<span data-ttu-id="058bb-106">En la siguiente lista se enumeran eventos de ThreadX mostrados por TraceX.</span><span class="sxs-lookup"><span data-stu-id="058bb-106">The following is a list of ThreadX events displayed by TraceX:</span></span>

| <span data-ttu-id="058bb-107">**Icono**</span><span class="sxs-lookup"><span data-stu-id="058bb-107">**Icon**</span></span>                         | <span data-ttu-id="058bb-108">**Significado**</span><span class="sxs-lookup"><span data-stu-id="058bb-108">**Meaning**</span></span> |
| -------------------------------- | ------------------------------------- |
| ![Icono de Reanudación de subprocesos internos](./media/user-guide/tx-events/image1.png)    | <span data-ttu-id="058bb-110">Reanudación de subprocesos internos</span><span class="sxs-lookup"><span data-stu-id="058bb-110">Internal thread resume</span></span>  |
| ![Icono de Suspensión de subprocesos internos](./media/user-guide/tx-events/image2.png)    | <span data-ttu-id="058bb-112">Suspensión de subprocesos internos</span><span class="sxs-lookup"><span data-stu-id="058bb-112">Internal thread suspend</span></span> |
| ![Icono de Entrada de rutina de servicio de interrupción](./media/user-guide/tx-events/image3.png)    | <span data-ttu-id="058bb-114">Entrada de rutina de servicio de interrupción (ISR)</span><span class="sxs-lookup"><span data-stu-id="058bb-114">Interrupt Service Routine (ISR) Enter</span></span> |
| ![Icono de Salida de rutina de servicio de interrupción](./media/user-guide/tx-events/image4.png)    | <span data-ttu-id="058bb-116">Salida de rutina de servicio de interrupción (ISR)</span><span class="sxs-lookup"><span data-stu-id="058bb-116">Interrupt Service Routine (ISR) Exit</span></span>  |
| ![Icono de Intervalo de tiempo interno](./media/user-guide/tx-events/image5.png)    | <span data-ttu-id="058bb-118">Intervalo de tiempo interno</span><span class="sxs-lookup"><span data-stu-id="058bb-118">Internal time-slice</span></span> |
| ![Icono de En ejecución](./media/user-guide/tx-events/image6.png)    | <span data-ttu-id="058bb-120">En ejecución</span><span class="sxs-lookup"><span data-stu-id="058bb-120">Running</span></span> |
| ![Icono de Asignación de grupo de bloques](./media/user-guide/tx-events/image7.png)    | <span data-ttu-id="058bb-122">**Asignación de grupo de bloques** (*tx_block_allocate*)</span><span class="sxs-lookup"><span data-stu-id="058bb-122">**Block pool allocate** (*tx_block_allocate*)</span></span>  |
| ![Icono de Creación de grupo de bloques](./media/user-guide/tx-events/image8.png)    | <span data-ttu-id="058bb-124">**Creación de grupo de bloques** (*tx_block_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="058bb-124">**Block pool create** (*tx_block_pool_create*)</span></span> |
| ![Icono de Eliminación de grupo de bloques](./media/user-guide/tx-events/image9.png)    | <span data-ttu-id="058bb-126">**Eliminación de grupo de bloques** (*tx_block_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="058bb-126">**Block pool delete** (*tx_block_pool_delete*)</span></span> |
| ![Icono de Obtención de información de grupo de bloques](./media/user-guide/tx-events/image10.png)    | <span data-ttu-id="058bb-128">**Obtención de información de grupo de bloques** (*tx_block_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-128">**Block pool information get** (*tx_block_pool_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento de grupo de bloques](./media/user-guide/tx-events/image11.png)    | <span data-ttu-id="058bb-130">**Obtención de información de rendimiento de bloqueos** (*tx_block_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-130">**Block pool performance information get** (*tx_block_pool_performance_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento del sistema de grupo de bloques](./media/user-guide/tx-events/image12.png)    | <span data-ttu-id="058bb-132">**Obtención de información de rendimiento del sistema de grupo de bloques** (*tx_block_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-132">**Block pool system performance information get** (*tx_block_pool_performance_system_info_get*)</span></span> |
| ![Icono de Priorización de grupo de bloques](./media/user-guide/tx-events/image13.png)    | <span data-ttu-id="058bb-134">**Priorización de grupo de bloques** (*tx_block_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="058bb-134">**Block pool prioritize** (*tx_block_pool_prioritize*)</span></span> |
| ![Icono de Liberación del bloque al grupo](./media/user-guide/tx-events/image14.png)    | <span data-ttu-id="058bb-136">**Liberación del bloque al grupo** (*tx_block_release*)</span><span class="sxs-lookup"><span data-stu-id="058bb-136">**Block release to pool** (*tx_block_release*)</span></span> |
| ![Icono de Asignación de memoria del grupo de bytes](./media/user-guide/tx-events/image15.png)    | <span data-ttu-id="058bb-138">**Asignación de memoria del grupo de bytes** (*tx_byte_allocate*)</span><span class="sxs-lookup"><span data-stu-id="058bb-138">**Byte pool allocate memory** (*tx_byte_allocate*)</span></span> |
| ![Icono de Creación de grupos de bytes](./media/user-guide/tx-events/image16.png)    | <span data-ttu-id="058bb-140">**Creación de grupos de bytes** (*tx_byte_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="058bb-140">**Byte pool create** (*tx_byte_pool_create*)</span></span> |
| ![Icono de Eliminación de grupos de bloques](./media/user-guide/tx-events/image17.png)    | <span data-ttu-id="058bb-142">**Eliminación de grupos de bloques** (*tx_byte_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="058bb-142">**Byte pool delete** (*tx_byte_pool_delete*)</span></span> |
| ![Icono de Obtención de información de grupos de bytes](./media/user-guide/tx-events/image18.png)    | <span data-ttu-id="058bb-144">**Obtención de información de grupos de bytes** (*tx_byte_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-144">**Byte pool information get** (*tx_byte_pool_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento de grupos de bytes](./media/user-guide/tx-events/image19.png)    | <span data-ttu-id="058bb-146">**Obtención de información de rendimiento de grupos de bytes** (*tx_byte_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-146">**Byte pool performance information get** (*tx_byte_pool_performance_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento del sistema de grupos de bytes](./media/user-guide/tx-events/image20.png)    | <span data-ttu-id="058bb-148">**Obtención de información de rendimiento del sistema de grupos de bytes** (*tx_byte_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-148">**Byte pool system performance information get** (*tx_byte_pool_performance_system_info_get*)</span></span> |
| ![\*Icono de Priorización de grupos de bytes](./media/user-guide/tx-events/image21.png)    | <span data-ttu-id="058bb-150">**Priorización de grupos de bytes** (*tx_byte_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="058bb-150">**Byte pool prioritize** (*tx_byte_pool_prioritize*)</span></span> |
| ![Icono Liberación de memoria de bytes en el grupo](./media/user-guide/tx-events/image22.png)    | <span data-ttu-id="058bb-152">**Liberación de memoria de bytes en el grupo** (*tx_byte_release*)</span><span class="sxs-lookup"><span data-stu-id="058bb-152">**Byte memory release to pool** (*tx_byte_release*)</span></span> |
| ![Icono de Creación de marcas de evento](./media/user-guide/tx-events/image23.png)    | <span data-ttu-id="058bb-154">**Creación de marcas de evento** (*tx_event_flags_create*)</span><span class="sxs-lookup"><span data-stu-id="058bb-154">**Event flags create** (*tx_event_flags_create*)</span></span> |
| ![Icono de Eliminación de marcas de evento](./media/user-guide/tx-events/image24.png)    | <span data-ttu-id="058bb-156">**Eliminación de marcas de evento** (*tx_event_flags_delete*)</span><span class="sxs-lookup"><span data-stu-id="058bb-156">**Event flags delete** (*tx_event_flags_delete*)</span></span> |
| ![Icono de Obtención de marcas de evento](./media/user-guide/tx-events/image25.png)    | <span data-ttu-id="058bb-158">**Obtención de marcas de evento** (*tx_event_flags_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-158">**Event flags get** (*tx_event_flags_get*)</span></span> |
| ![Icono de Obtención de información de marcas de evento](./media/user-guide/tx-events/image26.png)    | <span data-ttu-id="058bb-160">**Obtención de información de marcas de evento** (*tx_event_flags_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-160">**Event flags information get** (*tx_event_flags_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento de marcas de evento](./media/user-guide/tx-events/image27.png)    | <span data-ttu-id="058bb-162">**Obtención de información de rendimiento de marcas de evento** (*tx_event_flags_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-162">**Event flags performance information get** (*tx_event_flags_performance_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento del sistema de marcas de evento](./media/user-guide/tx-events/image28.png)    | <span data-ttu-id="058bb-164">**Obtención de información de rendimiento del sistema de marcas de evento** (*tx_event_flags_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-164">**Event flags system performance information get** (*tx_event_flags_performance_system_info_get*)</span></span> |
| ![Icono de Establecimiento de marcas de evento](./media/user-guide/tx-events/image29.png)    | <span data-ttu-id="058bb-166">**Establecimiento de marcas de evento** (*tx_event_flags_set*)</span><span class="sxs-lookup"><span data-stu-id="058bb-166">**Event flags set** (*tx_event_flags_set*)</span></span> |
| ![Icono de Notificación de establecimiento de marcas de evento](./media/user-guide/tx-events/image30.png)    | <span data-ttu-id="058bb-168">**Notificación de establecimiento de marcas de evento** (*tx_event_flags_set_notify*)</span><span class="sxs-lookup"><span data-stu-id="058bb-168">**Event flags set notify** (*tx_event_flags_set_notify*)</span></span> |
| ![Icono de Habilitar/deshabilitar interrupción](./media/user-guide/tx-events/image31.png)    | <span data-ttu-id="058bb-170">**Habilitar/deshabilitar interrupción** (*tx_interrupt_control*)</span><span class="sxs-lookup"><span data-stu-id="058bb-170">**Interrupt enable/disable** (*tx_interrupt_control*)</span></span> |
| ![Icono de Creación de exclusión mutua](./media/user-guide/tx-events/image32.png)    | <span data-ttu-id="058bb-172">**Creación de exclusión mutua** (*tx_mutex_create*)</span><span class="sxs-lookup"><span data-stu-id="058bb-172">**Mutex create** (*tx_mutex_create*)</span></span> |
| ![Icono de Eliminación de exclusión mutua](./media/user-guide/tx-events/image33.png)    | <span data-ttu-id="058bb-174">**Eliminación de exclusión mutua** (*tx_mutex_delete*)</span><span class="sxs-lookup"><span data-stu-id="058bb-174">**Mutex delete** (*tx_mutex_delete*)</span></span> |
| ![Icono de Obtención de exclusión mutua](./media/user-guide/tx-events/image34.png)    | <span data-ttu-id="058bb-176">**Obtención de exclusión mutua** (*tx_mutex_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-176">**Mutex get** (*tx_mutex_get*)</span></span> |
| ![Icono de Obtención de información de exclusión mutua](./media/user-guide/tx-events/image35.png)    | <span data-ttu-id="058bb-178">**Icono de Obtención de información de exclusión mutua** (*tx_mutex_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-178">**Mutex information get** (*tx_mutex_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento de exclusión mutua](./media/user-guide/tx-events/image36.png)    | <span data-ttu-id="058bb-180">**Obtención de información de rendimiento de exclusión mutua** (*tx_mutex_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-180">**Mutex performance information get** (*tx_mutex_performance_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento del sistema de exclusión mutua](./media/user-guide/tx-events/image37.png)    | <span data-ttu-id="058bb-182">**Obtención de información de rendimiento del sistema de exclusión mutua** (*tx_mutex_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-182">**Mutex system performance information get** (*tx_mutex_performance_system_info_get*)</span></span> |
| ![Icono de Priorización de exclusión mutua](./media/user-guide/tx-events/image38.png)    | <span data-ttu-id="058bb-184">**Priorización de exclusión mutua** (*tx_mutex_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="058bb-184">**Mutex prioritize** (*tx_mutex_prioritize*)</span></span> |
| ![Icono de Colocación de exclusión mutua](./media/user-guide/tx-events/image39.png)    | <span data-ttu-id="058bb-186">**Colocación de exclusión mutua** (*tx_mutex_put*)</span><span class="sxs-lookup"><span data-stu-id="058bb-186">**Mutex put** (*tx_mutex_put*)</span></span> |
| ![Icono de Creación de colas](./media/user-guide/tx-events/image40.png)    | <span data-ttu-id="058bb-188">**Creación de colas** (*tx_queue_create*)</span><span class="sxs-lookup"><span data-stu-id="058bb-188">**Queue create** (*tx_queue_create*)</span></span> |
| ![Icono de Eliminación de colas](./media/user-guide/tx-events/image41.png)    | <span data-ttu-id="058bb-190">**Eliminación de colas** (*tx_queue_delete*)</span><span class="sxs-lookup"><span data-stu-id="058bb-190">**Queue delete** (*tx_queue_delete*)</span></span> |
| ![Icono de Vaciado de colas](./media/user-guide/tx-events/image42.png)    | <span data-ttu-id="058bb-192">**Vaciado de colas** (*tx_queue_flush*)</span><span class="sxs-lookup"><span data-stu-id="058bb-192">**Queue flush** (*tx_queue_flush*)</span></span> |
| ![Icono de Envío al inicio de cola](./media/user-guide/tx-events/image43.png)    | <span data-ttu-id="058bb-194">**Envío al inicio de cola** (*tx_queue_front_send*)</span><span class="sxs-lookup"><span data-stu-id="058bb-194">**Queue front send** (*tx_queue_front_send*)</span></span> |
| ![Icono de Obtención de información de cola](./media/user-guide/tx-events/image44.png)    | <span data-ttu-id="058bb-196">**Obtención de información de cola** (*tx_queue_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-196">**Queue information get** (*tx_queue_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento de cola](./media/user-guide/tx-events/image45.png)    | <span data-ttu-id="058bb-198">**Obtención de información de rendimiento de cola** (*tx_queue_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-198">**Queue performance information get** (*tx_queue_performance_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento del sistema de cola](./media/user-guide/tx-events/image46.png)    | <span data-ttu-id="058bb-200">**Obtención de información de rendimiento del sistema de cola** (*tx_queue_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-200">**Queue system performance information get** (*tx_queue_performance_system_info_get*)</span></span> |
| ![Icono de Priorización de colas](./media/user-guide/tx-events/image47.png)    | <span data-ttu-id="058bb-202">**Priorización de colas** (*tx_queue_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="058bb-202">**Queue prioritize** (*tx_queue_prioritize*)</span></span> |
| ![Icono de Recepción de mensaje de cola](./media/user-guide/tx-events/image48.png)    | <span data-ttu-id="058bb-204">**Recepción de mensaje de cola** (*tx_queue_receive*)</span><span class="sxs-lookup"><span data-stu-id="058bb-204">**Queue receive message** (*tx_queue_receive*)</span></span> |
| ![Icono de Envío de mensaje de cola](./media/user-guide/tx-events/image49.png)    | <span data-ttu-id="058bb-206">**Envío de mensaje de cola** (*tx_queue_send*)</span><span class="sxs-lookup"><span data-stu-id="058bb-206">**Queue send message** (*tx_queue_send*)</span></span> |
| ![Icono Notificación de envío de cola](./media/user-guide/tx-events/image50.png)    | <span data-ttu-id="058bb-208">**Notificación de envío de cola** (*tx_queue_send_notify*)</span><span class="sxs-lookup"><span data-stu-id="058bb-208">**Queue send notify** (*tx_queue_send_notify*)</span></span> |
| ![Icono de Colocación del límite superior del semáforo](./media/user-guide/tx-events/image51.png)    | <span data-ttu-id="058bb-210">**Colocación del límite superior del semáforo** (*tx_semaphore_ceiling_put*)</span><span class="sxs-lookup"><span data-stu-id="058bb-210">**Semaphore ceiling put** (*tx_semaphore_ceiling_put*)</span></span> |
| ![Icono de Creación de semáforos](./media/user-guide/tx-events/image52.png)    | <span data-ttu-id="058bb-212">**Creación de semáforos** (*tx_semaphore_create*)</span><span class="sxs-lookup"><span data-stu-id="058bb-212">**Semaphore create** (*tx_semaphore_create*)</span></span> |
| ![Icono de Eliminación de semáforos](./media/user-guide/tx-events/image53.png)    | <span data-ttu-id="058bb-214">**Eliminación de semáforos** (*tx_semaphore_delete*)</span><span class="sxs-lookup"><span data-stu-id="058bb-214">**Semaphore delete** (*tx_semaphore_delete*)</span></span> |
| ![Icono de Obtención de semáforos](./media/user-guide/tx-events/image54.png)    | <span data-ttu-id="058bb-216">**Obtención de semáforos** (*tx_semaphore_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-216">**Semaphore get** (*tx_semaphore_get*)</span></span> |
| ![Icono de Obtención de información de semáforos](./media/user-guide/tx-events/image55.png)    | <span data-ttu-id="058bb-218">**Obtención de información de semáforos** (*tx_semaphore_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-218">**Semaphore information get** (*tx_semaphore_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento de semáforos](./media/user-guide/tx-events/image56.png)    | <span data-ttu-id="058bb-220">**Obtención de información de rendimiento de semáforos** (*tx_semaphroe_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-220">**Semaphore performance information get** (*tx_semaphroe_performance_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento del sistema de semáforos](./media/user-guide/tx-events/image57.png)    | <span data-ttu-id="058bb-222">**Obtención de información de rendimiento del sistema de semáforos** (*tx_semaphore_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-222">**Semaphore system performance information get** (*tx_semaphore_performance_system_info_get*)</span></span> |
| ![Icono de Priorización de semáforos](./media/user-guide/tx-events/image58.png)    | <span data-ttu-id="058bb-224">**Priorización de semáforos** (*tx_semaphore_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="058bb-224">**Semaphore prioritize** (*tx_semaphore_prioritize*)</span></span> |
| ![Icono de Colocación de semáforos](./media/user-guide/tx-events/image59.png)    | <span data-ttu-id="058bb-226">**Colocación de semáforos** (*tx_semaphore_put*)</span><span class="sxs-lookup"><span data-stu-id="058bb-226">**Semaphore put** (*tx_semaphore_put*)</span></span> |
| ![Icono de Notificación de colocación de semáforos](./media/user-guide/tx-events/image60.png)    | <span data-ttu-id="058bb-228">**Notificación de colocación de semáforos** (*tx_semaphore_put_notify*)</span><span class="sxs-lookup"><span data-stu-id="058bb-228">**Semaphore put notify** (*tx_semaphore_put_notify*)</span></span> |
| ![Icono de Creación de subprocesos](./media/user-guide/tx-events/image61.png)    | <span data-ttu-id="058bb-230">**Creación de subprocesos** (*tx_thread_create*)</span><span class="sxs-lookup"><span data-stu-id="058bb-230">**Thread create** (*tx_thread_create*)</span></span> |
| ![Icono de Eliminación de subprocesos](./media/user-guide/tx-events/image62.png)    | <span data-ttu-id="058bb-232">**Eliminación de subprocesos** (*tx_thread_delete*)</span><span class="sxs-lookup"><span data-stu-id="058bb-232">**Thread delete** (*tx_thread_delete*)</span></span> |
| ![Icono de Notificación de salida/entrada de subprocesos](./media/user-guide/tx-events/image63.png)    | <span data-ttu-id="058bb-234">**Notificación de salida/entrada de subprocesos** (*tx_thread_entry_exit_notify*)</span><span class="sxs-lookup"><span data-stu-id="058bb-234">**Thread exit/entry notify** (*tx_thread_entry_exit_notify*)</span></span> |
| ![Icono de Identificación de subprocesos](./media/user-guide/tx-events/image64.png)    | <span data-ttu-id="058bb-236">**Identificación de subprocesos** (*tx_thread_identify*)</span><span class="sxs-lookup"><span data-stu-id="058bb-236">**Thread identify** (*tx_thread_identify*)</span></span> |
| ![Icono de Obtención de información de subprocesos](./media/user-guide/tx-events/image65.png)    | <span data-ttu-id="058bb-238">**Obtención de información de subprocesos** (*tx_thread_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-238">**Thread information get** (*tx_thread_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento del subproceso](./media/user-guide/tx-events/image66.png)    | <span data-ttu-id="058bb-240">**Obtención de información de rendimiento del subproceso** (*tx_thread_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-240">**Thread performance information get** (*tx_thread_performance_info_get*)</span></span> |
| ![Icono de Obtención de información de sistema de rendimiento del subproceso](./media/user-guide/tx-events/image67.png)    | <span data-ttu-id="058bb-242">**Obtención de información de sistema de rendimiento del subproceso** (*tx_thread_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-242">**Thread performance system information get** (*tx_thread_performance_system_info_get*)</span></span> |
| ![Icono de Cambio de adelantamiento de subprocesos](./media/user-guide/tx-events/image68.png)    | <span data-ttu-id="058bb-244">**Cambio de adelantamiento de subprocesos** (*tx_thread_preemption_change*)</span><span class="sxs-lookup"><span data-stu-id="058bb-244">**Thread preemption change** (*tx_thread_preemption_change*)</span></span> |
| ![Icono de Cambio de prioridad de subprocesos](./media/user-guide/tx-events/image69.png)    | <span data-ttu-id="058bb-246">**Cambio de prioridad de subprocesos** (*tx_thread_priority_change*)</span><span class="sxs-lookup"><span data-stu-id="058bb-246">**Thread priority change** (*tx_thread_priority_change*)</span></span> |
| ![Icono de Renuncia de subprocesos](./media/user-guide/tx-events/image70.png)    | <span data-ttu-id="058bb-248">**Renuncia de subprocesos** (*tx_thread_relinquish*)</span><span class="sxs-lookup"><span data-stu-id="058bb-248">**Thread relinquish** (*tx_thread_relinquish*)</span></span> |
| ![Icono de Restablecimiento de subprocesos](./media/user-guide/tx-events/image71.png)    | <span data-ttu-id="058bb-250">**Restablecimiento de subprocesos** (*tx_thread_reset*)</span><span class="sxs-lookup"><span data-stu-id="058bb-250">**Thread reset** (*tx_thread_reset*)</span></span> |
| ![\*Icono de Reanudación de subprocesos](./media/user-guide/tx-events/image72.png)    | <span data-ttu-id="058bb-252">**Reanudación de subprocesos** (\**tx_thread_resume*)</span><span class="sxs-lookup"><span data-stu-id="058bb-252">**Thread resume** (\**tx_thread_resume*)</span></span> |
| ![Icono de Pausa de subprocesos](./media/user-guide/tx-events/image73.png)    | <span data-ttu-id="058bb-254">**Pausa de subprocesos** (*tx_thread_sleep*)\*</span><span class="sxs-lookup"><span data-stu-id="058bb-254">**Thread Sleep** (*tx_thread_sleep*)\*</span></span> |
| ![Icono de Notificación de error de pila de subprocesos](./media/user-guide/tx-events/image74.png)    | <span data-ttu-id="058bb-256">**Notificación de error de pila de subprocesos** (*tx_thread_stack_error_notify*)</span><span class="sxs-lookup"><span data-stu-id="058bb-256">**Thread stack error notify** (*tx_thread_stack_error_notify*)</span></span> |
| ![Icono de Suspensión de subprocesos](./media/user-guide/tx-events/image75.png)    | <span data-ttu-id="058bb-258">**Suspensión de subprocesos** (*tx_thread_suspend*)</span><span class="sxs-lookup"><span data-stu-id="058bb-258">**Thread suspend** (*tx_thread_suspend*)</span></span> |
| ![Icono de Finalización de subprocesos](./media/user-guide/tx-events/image76.png)    | <span data-ttu-id="058bb-260">**Finalización de subprocesos** (*tx_thread_terminate*)</span><span class="sxs-lookup"><span data-stu-id="058bb-260">**Thread terminate** (*tx_thread_terminate*)</span></span> |
| ![Icono de Cambio de intervalo de tiempo](./media/user-guide/tx-events/image77.png)    | <span data-ttu-id="058bb-262">**Cambio de intervalo de tiempo** (*tx_thread_time_slice_change*)</span><span class="sxs-lookup"><span data-stu-id="058bb-262">**Thread time-slice change** (*tx_thread_time_slice_change*)</span></span> |
| ![Icono de Anulación de espera de subprocesos](./media/user-guide/tx-events/image78.png)    | <span data-ttu-id="058bb-264">**Anulación de espera de subprocesos** (*tx_thread_wait_abort*)</span><span class="sxs-lookup"><span data-stu-id="058bb-264">**Thread wait abort** (*tx_thread_wait_abort*)</span></span> |
| ![Icono de Obtención de hora](./media/user-guide/tx-events/image79.png)    | <span data-ttu-id="058bb-266">**Obtención de hora** (*tx_time_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-266">**Time get** (*tx_time_get*)</span></span> |
| ![Icono de Establecimiento de hora](./media/user-guide/tx-events/image80.png)    | <span data-ttu-id="058bb-268">**Establecimiento de hora** (*tx_time_set*)</span><span class="sxs-lookup"><span data-stu-id="058bb-268">**Time set** (*tx_time_set*)</span></span> |
| ![\*Icono de Activación de temporizador](./media/user-guide/tx-events/image81.png)    | <span data-ttu-id="058bb-270">**Activación de temporizador** (*tx_timer_activate*)</span><span class="sxs-lookup"><span data-stu-id="058bb-270">**Timer activate** (*tx_timer_activate*)</span></span> |
| ![Icono de Cambio del temporizador](./media/user-guide/tx-events/image82.png)    | <span data-ttu-id="058bb-272">**Cambio del temporizador** (*tx_timer_change*)</span><span class="sxs-lookup"><span data-stu-id="058bb-272">**Timer change** (*tx_timer_change*)</span></span> |
| ![Icono de Creación del temporizador](./media/user-guide/tx-events/image83.png)    | <span data-ttu-id="058bb-274">**Creación del temporizador** (*tx_timer_create*)</span><span class="sxs-lookup"><span data-stu-id="058bb-274">**Timer create** (*tx_timer_create*)</span></span> |
| ![Icono de Desactivación del temporizador](./media/user-guide/tx-events/image84.png)    | <span data-ttu-id="058bb-276">**Desactivación del temporizador** (*tx_timer_deactivate*)</span><span class="sxs-lookup"><span data-stu-id="058bb-276">**Timer deactivate** (*tx_timer_deactivate*)</span></span> |
| ![Icono de Eliminación del temporizador](./media/user-guide/tx-events/image85.png)    | <span data-ttu-id="058bb-278">**Eliminación del temporizador** (*tx_timer_delete*)</span><span class="sxs-lookup"><span data-stu-id="058bb-278">**Timer delete** (*tx_timer_delete*)</span></span> |
| ![Icono de Obtención de información del temporizador](./media/user-guide/tx-events/image86.png)    | <span data-ttu-id="058bb-280">**Obtención de información del temporizador** (*tx_timer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-280">**Timer information get** (*tx_timer_info_get*)</span></span> |
| ![Icono de Obtención de información de rendimiento de la cola](./media/user-guide/tx-events/image87.png)    | <span data-ttu-id="058bb-282">**Obtención de información de rendimiento del temporizador** (*tx_timer_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-282">**Timer performance information get** (*tx_timer_performance_info_get*)</span></span> |
| ![\*Icono de Obtención de información de sistema del rendimiento del temporizador](./media/user-guide/tx-events/image88.png)    | <span data-ttu-id="058bb-284">**Obtención de información de sistema del rendimiento del temporizador** (*tx_timer_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="058bb-284">**Timer performance system information get** (*tx_timer_performance_system_info_get*)</span></span> |
| ![Evento definido por el usuario](./media/user-guide/tx-events/image0.png)    | <span data-ttu-id="058bb-286">**Evento definido por el usuario** (consulte el capítulo 10)</span><span class="sxs-lookup"><span data-stu-id="058bb-286">**User-Defined Event** (See Chapter 10)</span></span>    |

## <a name="event-descriptions"></a><span data-ttu-id="058bb-287">Descripciones de eventos</span><span class="sxs-lookup"><span data-stu-id="058bb-287">Event Descriptions</span></span>

### <a name="internal-thread-resume"></a><span data-ttu-id="058bb-288">Reanudación de subprocesos internos</span><span class="sxs-lookup"><span data-stu-id="058bb-288">Internal thread resume</span></span>

#### <a name="internal-thread-resume"></a><span data-ttu-id="058bb-289">Reanudación de subprocesos internos</span><span class="sxs-lookup"><span data-stu-id="058bb-289">Internal thread resume</span></span>

<span data-ttu-id="058bb-290">**Icono** ![Icono de Reanudación de subprocesos internos](./media/user-guide/tx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-290">**Icon** ![Internal thread resume icon](./media/user-guide/tx-events/image1.png)</span></span>

<span data-ttu-id="058bb-291">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-291">**Description**</span></span>

<span data-ttu-id="058bb-292">Este evento representa el procesamiento interno de ThreadX que reanuda un subproceso para su ejecución.</span><span class="sxs-lookup"><span data-stu-id="058bb-292">This event represents the internal processing in ThreadX that resumes a thread for execution.</span></span> <span data-ttu-id="058bb-293">Si el subproceso especificado es la prioridad más alta y el umbral de adelantamiento no bloquea su ejecución, el sistema comenzará a ejecutar este subproceso recién preparado.</span><span class="sxs-lookup"><span data-stu-id="058bb-293">If the specified thread is the highest priority and preemption-threshold does not block its execution, the system will start executing this newly ready thread.</span></span>

<span data-ttu-id="058bb-294">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-294">**Information Fields**</span></span>

- <span data-ttu-id="058bb-295">Campo de información 1: puntero que señala al subproceso que se va a reanudar.</span><span class="sxs-lookup"><span data-stu-id="058bb-295">Info Field 1: Pointer to the thread being resumed.</span></span>
- <span data-ttu-id="058bb-296">Campo de información 2: estado anterior del subproceso que se va a reanudar, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="058bb-296">Info Field 2: Previous state of the thread being resumed, as follows:</span></span>

  |  <span data-ttu-id="058bb-297">Estado del subproceso</span><span class="sxs-lookup"><span data-stu-id="058bb-297">Thread state</span></span>                     | <span data-ttu-id="058bb-298">Value</span><span class="sxs-lookup"><span data-stu-id="058bb-298">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="058bb-299">TX_READY</span><span class="sxs-lookup"><span data-stu-id="058bb-299">TX_READY</span></span>                         | <span data-ttu-id="058bb-300">0</span><span class="sxs-lookup"><span data-stu-id="058bb-300">0</span></span>       |
  |  <span data-ttu-id="058bb-301">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="058bb-301">TX_COMPLETED</span></span>                     | <span data-ttu-id="058bb-302">1</span><span class="sxs-lookup"><span data-stu-id="058bb-302">1</span></span>       |
  |  <span data-ttu-id="058bb-303">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="058bb-303">TX_TERMINATED</span></span>                    | <span data-ttu-id="058bb-304">2</span><span class="sxs-lookup"><span data-stu-id="058bb-304">2</span></span>       |
  |  <span data-ttu-id="058bb-305">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="058bb-305">TX_SUSPENDED</span></span>                     | <span data-ttu-id="058bb-306">3</span><span class="sxs-lookup"><span data-stu-id="058bb-306">3</span></span>       |
  |  <span data-ttu-id="058bb-307">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="058bb-307">TX_SLEEP</span></span>                         | <span data-ttu-id="058bb-308">4</span><span class="sxs-lookup"><span data-stu-id="058bb-308">4</span></span>       |
  |  <span data-ttu-id="058bb-309">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="058bb-309">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="058bb-310">5</span><span class="sxs-lookup"><span data-stu-id="058bb-310">5</span></span>       |
  |  <span data-ttu-id="058bb-311">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="058bb-311">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="058bb-312">6</span><span class="sxs-lookup"><span data-stu-id="058bb-312">6</span></span>       |
  |  <span data-ttu-id="058bb-313">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="058bb-313">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="058bb-314">7</span><span class="sxs-lookup"><span data-stu-id="058bb-314">7</span></span>       |
  |  <span data-ttu-id="058bb-315">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="058bb-315">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="058bb-316">8</span><span class="sxs-lookup"><span data-stu-id="058bb-316">8</span></span>       |
  |  <span data-ttu-id="058bb-317">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="058bb-317">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="058bb-318">9</span><span class="sxs-lookup"><span data-stu-id="058bb-318">9</span></span>       |
  |  <span data-ttu-id="058bb-319">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="058bb-319">TX_TCP_IP</span></span>                        | <span data-ttu-id="058bb-320">12</span><span class="sxs-lookup"><span data-stu-id="058bb-320">12</span></span>      |
  |  <span data-ttu-id="058bb-321">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="058bb-321">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="058bb-322">13</span><span class="sxs-lookup"><span data-stu-id="058bb-322">13</span></span>      |

- <span data-ttu-id="058bb-323">Campo de información 3: valor del puntero de pila durante la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-323">Info Field 3: Stack pointer value during the call.</span></span> 
- <span data-ttu-id="058bb-324">Campo de información 4: puntero que señala al siguiente subproceso de prioridad más alta que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="058bb-324">Info Field 4: Pointer to next highest priority thread to execute.</span></span>

### <a name="internal-thread-suspend"></a><span data-ttu-id="058bb-325">Suspensión de subprocesos internos</span><span class="sxs-lookup"><span data-stu-id="058bb-325">Internal thread suspend</span></span>

#### <a name="internal-thread-suspend"></a><span data-ttu-id="058bb-326">Suspensión de subprocesos internos</span><span class="sxs-lookup"><span data-stu-id="058bb-326">Internal thread suspend</span></span>

<span data-ttu-id="058bb-327">**Icono** ![Icono de Suspensión de subprocesos internos](./media/user-guide/tx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-327">**Icon** ![Internal thread suspend icon](./media/user-guide/tx-events/image2.png)</span></span>

<span data-ttu-id="058bb-328">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-328">**Description**</span></span>

<span data-ttu-id="058bb-329">Este evento representa el procesamiento interno de ThreadX que suspende la ejecución de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-329">This event represents the internal processing in ThreadX that suspends a thread's execution.</span></span> <span data-ttu-id="058bb-330">El siguiente subproceso de prioridad más alta preparado para la ejecución se coloca en el cuarto campo de información.</span><span class="sxs-lookup"><span data-stu-id="058bb-330">The next highest priority thread ready for execution is placed in the fourth information field.</span></span> <span data-ttu-id="058bb-331">Si este valor es NULL, no hay ningún otro subproceso listo para la ejecución y el sistema está inactivo.</span><span class="sxs-lookup"><span data-stu-id="058bb-331">If this value is NULL, there is no other thread ready for execution and the system is idle.</span></span>

<span data-ttu-id="058bb-332">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-332">**Information Fields**</span></span>

- <span data-ttu-id="058bb-333">Campo de información 1: puntero que señala al subproceso que se va a suspender.</span><span class="sxs-lookup"><span data-stu-id="058bb-333">Info Field 1: Pointer to the thread being suspended.</span></span>
- <span data-ttu-id="058bb-334">Campo de información 2: nuevo estado del subproceso que se va a suspender, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="058bb-334">Info Field 2: New state of the thread being suspended, as follows:</span></span>

  |  <span data-ttu-id="058bb-335">Estado del subproceso</span><span class="sxs-lookup"><span data-stu-id="058bb-335">Thread state</span></span>                     | <span data-ttu-id="058bb-336">Value</span><span class="sxs-lookup"><span data-stu-id="058bb-336">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="058bb-337">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="058bb-337">TX_COMPLETED</span></span>                     | <span data-ttu-id="058bb-338">1</span><span class="sxs-lookup"><span data-stu-id="058bb-338">1</span></span>       |
  |  <span data-ttu-id="058bb-339">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="058bb-339">TX_TERMINATED</span></span>                    | <span data-ttu-id="058bb-340">2</span><span class="sxs-lookup"><span data-stu-id="058bb-340">2</span></span>       |
  |  <span data-ttu-id="058bb-341">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="058bb-341">TX_SUSPENDED</span></span>                     | <span data-ttu-id="058bb-342">3</span><span class="sxs-lookup"><span data-stu-id="058bb-342">3</span></span>       |
  |  <span data-ttu-id="058bb-343">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="058bb-343">TX_SLEEP</span></span>                         | <span data-ttu-id="058bb-344">4</span><span class="sxs-lookup"><span data-stu-id="058bb-344">4</span></span>       |
  |  <span data-ttu-id="058bb-345">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="058bb-345">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="058bb-346">5</span><span class="sxs-lookup"><span data-stu-id="058bb-346">5</span></span>       |
  |  <span data-ttu-id="058bb-347">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="058bb-347">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="058bb-348">6</span><span class="sxs-lookup"><span data-stu-id="058bb-348">6</span></span>       |
  |  <span data-ttu-id="058bb-349">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="058bb-349">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="058bb-350">7</span><span class="sxs-lookup"><span data-stu-id="058bb-350">7</span></span>       |
  |  <span data-ttu-id="058bb-351">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="058bb-351">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="058bb-352">8</span><span class="sxs-lookup"><span data-stu-id="058bb-352">8</span></span>       |
  |  <span data-ttu-id="058bb-353">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="058bb-353">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="058bb-354">9</span><span class="sxs-lookup"><span data-stu-id="058bb-354">9</span></span>       |
  |  <span data-ttu-id="058bb-355">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="058bb-355">TX_TCP_IP</span></span>                        | <span data-ttu-id="058bb-356">12</span><span class="sxs-lookup"><span data-stu-id="058bb-356">12</span></span>      |
  |  <span data-ttu-id="058bb-357">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="058bb-357">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="058bb-358">13</span><span class="sxs-lookup"><span data-stu-id="058bb-358">13</span></span>      |

- <span data-ttu-id="058bb-359">Campo de información 3: valor del puntero de pila durante la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-359">Info Field 3: Stack pointer value during the call.</span></span> <span data-ttu-id="058bb-360">Campo de información 4: puntero que señala al siguiente subproceso de prioridad más alta que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="058bb-360">Info Field 4: Pointer to next highest priority thread to execute.</span></span> <span data-ttu-id="058bb-361">Si es NULL, el sistema está inactivo.</span><span class="sxs-lookup"><span data-stu-id="058bb-361">If NULL, the system is idle.</span></span>

### <a name="interrupt-service-routine-isr-enter"></a><span data-ttu-id="058bb-362">Entrada de rutina de servicio de interrupción (ISR)</span><span class="sxs-lookup"><span data-stu-id="058bb-362">Interrupt Service Routine (ISR) enter</span></span> 

#### <a name="enter-isr"></a><span data-ttu-id="058bb-363">Entrada de ISR</span><span class="sxs-lookup"><span data-stu-id="058bb-363">Enter ISR</span></span> 

<span data-ttu-id="058bb-364">**Icono** ![Icono de Entrada ISR](./media/user-guide/tx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-364">**Icon** ![Enter I S R icon](./media/user-guide/tx-events/image3.png)</span></span>

<span data-ttu-id="058bb-365">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-365">**Description**</span></span>

<span data-ttu-id="058bb-366">Este evento representa la entrada de una rutina de servicio de interrupción (ISR) en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="058bb-366">This event represents entering an Interrupt Service Routine (ISR) in the application.</span></span> <span data-ttu-id="058bb-367">La ejecución de la rutina de interrupción del servicio continúa hasta que se produce el evento de salida de ISR.</span><span class="sxs-lookup"><span data-stu-id="058bb-367">The interrupt service routine execution continues until the ISR exit event takes place.</span></span>

<span data-ttu-id="058bb-368">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-368">**Information Fields**</span></span>

- <span data-ttu-id="058bb-369">Campo de información 1: valor de puntero de pila durante la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-369">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="058bb-370">Campo de información 2: número de ISR definido por la aplicación (opcional).</span><span class="sxs-lookup"><span data-stu-id="058bb-370">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="058bb-371">Campo de información 3: recuento de interrupciones anidadas.</span><span class="sxs-lookup"><span data-stu-id="058bb-371">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="058bb-372">Campo de información 4: marca de desactivación de adelantamiento interno.</span><span class="sxs-lookup"><span data-stu-id="058bb-372">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="interrupt-service-routine-isr-exit"></a><span data-ttu-id="058bb-373">Salida de rutina de servicio de interrupción (ISR)</span><span class="sxs-lookup"><span data-stu-id="058bb-373">Interrupt Service Routine (ISR) exit</span></span> 

#### <a name="exit-isr"></a><span data-ttu-id="058bb-374">Salida de ISR</span><span class="sxs-lookup"><span data-stu-id="058bb-374">Exit ISR</span></span>

<span data-ttu-id="058bb-375">**Icono** ![Icono de salida de ISR](./media/user-guide/tx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-375">**Icon** ![Exit I S R icon](./media/user-guide/tx-events/image4.png)</span></span>

<span data-ttu-id="058bb-376">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-376">**Description**</span></span>

<span data-ttu-id="058bb-377">Este evento representa la salida de una rutina de servicio de interrupción (ISR) en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="058bb-377">This event represents exiting an Interrupt Service Routine (ISR) in the application.</span></span>

<span data-ttu-id="058bb-378">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-378">**Information Fields**</span></span>

- <span data-ttu-id="058bb-379">Campo de información 1: valor de puntero de pila durante la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-379">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="058bb-380">Campo de información 2: número de ISR definido por la aplicación (opcional).</span><span class="sxs-lookup"><span data-stu-id="058bb-380">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="058bb-381">Campo de información 3: recuento de interrupciones anidadas.</span><span class="sxs-lookup"><span data-stu-id="058bb-381">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="058bb-382">Campo de información 4: marca de desactivación de adelantamiento interno.</span><span class="sxs-lookup"><span data-stu-id="058bb-382">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="internal-time-slice"></a><span data-ttu-id="058bb-383">Intervalo de tiempo interno</span><span class="sxs-lookup"><span data-stu-id="058bb-383">Internal time-slice</span></span>

#### <a name="internal-time-slice"></a><span data-ttu-id="058bb-384">Intervalo de tiempo interno</span><span class="sxs-lookup"><span data-stu-id="058bb-384">Internal time-slice</span></span>

<span data-ttu-id="058bb-385">**Icono** ![Icono de Intervalo de tiempo interno](./media/user-guide/tx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-385">**Icon** ![Internal time-slice icon](./media/user-guide/tx-events/image5.png)</span></span>

<span data-ttu-id="058bb-386">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-386">**Description**</span></span>

<span data-ttu-id="058bb-387">Este evento representa el procesamiento interno en ThreadX que realiza la operación de intervalo de tiempo.</span><span class="sxs-lookup"><span data-stu-id="058bb-387">This event represents the internal processing in ThreadX that performs the time-slice operation.</span></span> <span data-ttu-id="058bb-388">El siguiente subproceso de la misma prioridad se coloca en el primer campo de información.</span><span class="sxs-lookup"><span data-stu-id="058bb-388">The next thread of the same priority is placed in the first information field.</span></span> <span data-ttu-id="058bb-389">Si este valor es el mismo que el subproceso actual, no se realizó ningún intervalo de tiempo.</span><span class="sxs-lookup"><span data-stu-id="058bb-389">If this value is the same as the current thread, no time-slice was performed.</span></span>

- <span data-ttu-id="058bb-390">Campo de información 1: puntero que señala al siguiente subproceso que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="058bb-390">Info Field 1: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="058bb-391">Campo de información 2: recuento de interrupciones anidadas.</span><span class="sxs-lookup"><span data-stu-id="058bb-391">Info Field 2: Nested interrupt count.</span></span>
- <span data-ttu-id="058bb-392">Campo de información 3: marca de desactivación de adelantamiento interno.</span><span class="sxs-lookup"><span data-stu-id="058bb-392">Info Field 3: Internal preemption disable flag.</span></span>
- <span data-ttu-id="058bb-393">Campo de información 4: valor de puntero de pila durante la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-393">Info Field 4: Stack pointer value during the call.</span></span>

### <a name="running"></a><span data-ttu-id="058bb-394">En ejecución</span><span class="sxs-lookup"><span data-stu-id="058bb-394">Running</span></span>

#### <a name="running-in-context"></a><span data-ttu-id="058bb-395">Ejecución en contexto</span><span class="sxs-lookup"><span data-stu-id="058bb-395">Running in context</span></span>

<span data-ttu-id="058bb-396">**Icono** ![Icono En ejecución](./media/user-guide/tx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-396">**Icon** ![Running icon](./media/user-guide/tx-events/image6.png)</span></span>

<span data-ttu-id="058bb-397">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-397">**Description**</span></span>

<span data-ttu-id="058bb-398">Este evento representa la ejecución en un contexto de subproceso o un sistema inactivo.</span><span class="sxs-lookup"><span data-stu-id="058bb-398">This event represents running within a thread context or idle system.</span></span> <span data-ttu-id="058bb-399">Se usa para mostrar los cambios subsiguientes en el contexto como resultado de una interrupción.</span><span class="sxs-lookup"><span data-stu-id="058bb-399">It is used to illustrate subsequent changes in context as a result of an interrupt.</span></span>

<span data-ttu-id="058bb-400">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-400">**Information Fields**</span></span>
- <span data-ttu-id="058bb-401">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-401">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-402">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-402">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-403">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-403">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-404">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-404">Info Field 4: Not used.</span></span>

### <a name="block-allocate"></a><span data-ttu-id="058bb-405">Asignación de bloques</span><span class="sxs-lookup"><span data-stu-id="058bb-405">Block Allocate</span></span> 

#### <a name="tx_block_allocate"></a><span data-ttu-id="058bb-406">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="058bb-406">tx_block_allocate</span></span>

<span data-ttu-id="058bb-407">**Icono** ![Icono de Asignación de bloques](./media/user-guide/tx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-407">**Icon** ![Block allocate icon](./media/user-guide/tx-events/image7.png)</span></span>

<span data-ttu-id="058bb-408">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-408">**Description**</span></span>

<span data-ttu-id="058bb-409">Este evento representa la asignación de un bloque de memoria mediante tx_block_allocate.</span><span class="sxs-lookup"><span data-stu-id="058bb-409">This event represents allocating a memory block via tx_block_allocate.</span></span> <span data-ttu-id="058bb-410">Si se realiza correctamente, se devuelve la dirección del bloque asignado en el segundo campo de información.</span><span class="sxs-lookup"><span data-stu-id="058bb-410">If successful, the address of the block allocated is returned in the second information field.</span></span>

<span data-ttu-id="058bb-411">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-411">**Information Fields**</span></span>
- <span data-ttu-id="058bb-412">Campo de información 1: puntero que señala al grupo de bloques correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-412">Info Field 1: Pointer to the corresponding block pool.</span></span>
- <span data-ttu-id="058bb-413">Campo de información 2: puntero que señala al grupo de bloques devuelto (si se realiza correctamente).</span><span class="sxs-lookup"><span data-stu-id="058bb-413">Info Field 2: Pointer to the memory block returned (if successful).</span></span>
- <span data-ttu-id="058bb-414">Campo de información 3: opción de espera proporcionada a la llamada tx_block_allocate.</span><span class="sxs-lookup"><span data-stu-id="058bb-414">Info Field 3: The wait option supplied to the tx_block_allocate call.</span></span>
- <span data-ttu-id="058bb-415">Campo de información 4: bloques disponibles restantes en el grupo después de esta asignación.</span><span class="sxs-lookup"><span data-stu-id="058bb-415">Info Field 4: Remaining available blocks in the pool after this allocation.</span></span>

### <a name="block-pool-create"></a><span data-ttu-id="058bb-416">Creación de grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="058bb-416">Block Pool Create</span></span>

#### <a name="tx_block_pool_create"></a><span data-ttu-id="058bb-417">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="058bb-417">tx_block_pool_create</span></span>

<span data-ttu-id="058bb-418">**Icono** ![Icono de Creación de grupo de bloques](./media/user-guide/tx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-418">**Icon** ![Block pool create icon](./media/user-guide/tx-events/image8.png)</span></span>

<span data-ttu-id="058bb-419">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-419">**Description**</span></span>

<span data-ttu-id="058bb-420">Este evento representa la creación de un grupo de bloques de memoria mediante tx_block_pool_create.</span><span class="sxs-lookup"><span data-stu-id="058bb-420">This event represents creating a memory block pool via tx_block_pool_create.</span></span>

<span data-ttu-id="058bb-421">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-421">**Information Fields**</span></span>

- <span data-ttu-id="058bb-422">Campo de información 1: puntero que señala al bloque de control del grupo de bloques correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-422">Info Field 1: Pointer to the corresponding block pool control block.</span></span>
- <span data-ttu-id="058bb-423">Campo de información 2: puntero que señala al área de memoria de inicio del grupo.</span><span class="sxs-lookup"><span data-stu-id="058bb-423">Info Field 2: Pointer to the starting memory area of the pool.</span></span>
- <span data-ttu-id="058bb-424">Campo de información 3: número de bloques del grupo.</span><span class="sxs-lookup"><span data-stu-id="058bb-424">Info Field 3: The number of blocks in the pool.</span></span> <span data-ttu-id="058bb-425">Campo de información 4: tamaño de cada bloque en el grupo en bytes.</span><span class="sxs-lookup"><span data-stu-id="058bb-425">Info Field 4: The size of each block in the pool in bytes.</span></span>

### <a name="block-pool-delete"></a><span data-ttu-id="058bb-426">Eliminación de grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="058bb-426">Block Pool Delete</span></span>

#### <a name="tx_block_pool_delete"></a><span data-ttu-id="058bb-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="058bb-427">tx_block_pool_delete</span></span>

<span data-ttu-id="058bb-428">**Icono** ![Icono de Eliminación de grupo de bloques](./media/user-guide/tx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-428">**Icon** ![Block pool delete icon](./media/user-guide/tx-events/image9.png)</span></span>

<span data-ttu-id="058bb-429">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-429">**Description**</span></span>

<span data-ttu-id="058bb-430">Este evento representa la eliminación de un grupo de bloques de memoria mediante tx_block_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="058bb-430">This event represents deleting a memory block pool via tx_block_pool_delete.</span></span>

<span data-ttu-id="058bb-431">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-431">**Information Fields**</span></span>

- <span data-ttu-id="058bb-432">Campo de información 1: puntero que señala al bloque de control del grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="058bb-432">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="058bb-433">Campo de información 2: valor del puntero de pila durante la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-433">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="058bb-434">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-434">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-435">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-435">Info Field 4: Not used.</span></span>

### <a name="block-pool-information-get"></a><span data-ttu-id="058bb-436">Obtención de información de grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="058bb-436">Block Pool Information Get</span></span> 

#### <a name="tx_block_pool_info_get"></a><span data-ttu-id="058bb-437">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-437">tx_block_pool_info_get</span></span>

<span data-ttu-id="058bb-438">**Icono** ![Icono de Obtención de información de grupo de bloques](./media/user-guide/tx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-438">**Icon** ![Block pool information get icon](./media/user-guide/tx-events/image10.png)</span></span>

<span data-ttu-id="058bb-439">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-439">**Description**</span></span>

<span data-ttu-id="058bb-440">Este evento representa la obtención de información sobre un grupo de bloques de memoria mediante tx_block_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-440">This event represents getting information about a memory block pool via tx_block_pool_info_get.</span></span>

<span data-ttu-id="058bb-441">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-441">**Information Fields**</span></span>

- <span data-ttu-id="058bb-442">Campo de información 1: puntero que señala al bloque de control del grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="058bb-442">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="058bb-443">Campo de información 2: valor del puntero de pila durante la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-443">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="058bb-444">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-444">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-445">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-445">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-information-get"></a><span data-ttu-id="058bb-446">Obtención de información de rendimiento de grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="058bb-446">Block Pool Performance Information Get</span></span>

#### <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="058bb-447">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-447">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="058bb-448">**Icono** ![Icono de Obtención de información de rendimiento de grupo de bloques](./media/user-guide/tx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-448">**Icon** ![Block pool performance information get icon](./media/user-guide/tx-events/image11.png)</span></span>

<span data-ttu-id="058bb-449">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-449">**Description**</span></span>

<span data-ttu-id="058bb-450">Este evento representa la obtención de información de rendimiento sobre un grupo de bloques de memoria mediante tx_block_pool_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-450">This event represents getting performance information about a memory block pool via tx_block_pool_performance_info_get.</span></span>

<span data-ttu-id="058bb-451">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-451">**Information Fields**</span></span>

- <span data-ttu-id="058bb-452">Campo de información 1: puntero que señala al bloque de control del grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="058bb-452">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="058bb-453">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-453">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-454">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-454">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-455">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-455">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-system-information-get"></a><span data-ttu-id="058bb-456">Obtención de información de sistema del rendimiento del grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="058bb-456">Block Pool Performance System Information Get</span></span>

#### <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="058bb-457">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-457">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="058bb-458">**Icono** ![Icono de Obtención de información de sistema del rendimiento del grupo de bloques](./media/user-guide/tx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-458">**Icon** ![Block pool performance system information get icon](./media/user-guide/tx-events/image12.png)</span></span>

<span data-ttu-id="058bb-459">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-459">**Description**</span></span>

<span data-ttu-id="058bb-460">Este evento representa la obtención de información de rendimiento sobre un grupo de bloques de memoria mediante tx_block_pool_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-460">This event represents getting performance information about all memory block pools via tx_block_pool_performance_system_info_get.</span></span>

<span data-ttu-id="058bb-461">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-461">**Information Fields**</span></span>
- <span data-ttu-id="058bb-462">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-462">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-463">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-463">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-464">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-464">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-465">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-465">Info Field 4: Not used.</span></span>

### <a name="block-pool-prioritize"></a><span data-ttu-id="058bb-466">Priorización de grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="058bb-466">Block Pool Prioritize</span></span>

#### <a name="tx_block_pool_prioritize"></a><span data-ttu-id="058bb-467">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="058bb-467">tx_block_pool_prioritize</span></span>

<span data-ttu-id="058bb-468">**Icono** ![Icono de Priorización de grupo de bloques](./media/user-guide/tx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-468">**Icon** ![Block pool prioritize icon](./media/user-guide/tx-events/image13.png)</span></span>

<span data-ttu-id="058bb-469">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-469">**Description**</span></span>

<span data-ttu-id="058bb-470">Este evento representa la colocación del subproceso suspendido de prioridad más alta al principio de la lista de suspensión del grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="058bb-470">This event represents placing the highestpriority suspended thread at the front of the block pool suspension list.</span></span> <span data-ttu-id="058bb-471">Si esto se hace antes de llamar a tx_block_release, el subproceso suspendido de prioridad más alta recibirá el bloque liberado.</span><span class="sxs-lookup"><span data-stu-id="058bb-471">If this is done prior to calling tx_block_release, the highest priority suspended thread will receive the released block.</span></span>

<span data-ttu-id="058bb-472">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-472">**Information Fields**</span></span>
- <span data-ttu-id="058bb-473">Campo de información 1: puntero que señala al grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="058bb-473">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="058bb-474">Campo de información 2: número de subprocesos suspendidos en este grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="058bb-474">Info Field 2: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="058bb-475">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-475">Info Field 3: Stack pointer at the time of the call.</span></span>
- <span data-ttu-id="058bb-476">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-476">Info Field 4: Not used.</span></span>

### <a name="block-release"></a><span data-ttu-id="058bb-477">Liberación de bloques</span><span class="sxs-lookup"><span data-stu-id="058bb-477">Block Release</span></span> 

#### <a name="tx_block_release"></a><span data-ttu-id="058bb-478">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="058bb-478">tx_block_release</span></span>

<span data-ttu-id="058bb-479">**Icono** ![Icono de Liberación de bloques](./media/user-guide/tx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-479">**Icon** ![Block release icon](./media/user-guide/tx-events/image14.png)</span></span>

<span data-ttu-id="058bb-480">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-480">**Description**</span></span>

<span data-ttu-id="058bb-481">Este evento representa la liberación de un bloque previamente asignado al grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="058bb-481">This event represents releasing a previously allocated block back to the block pool.</span></span>

<span data-ttu-id="058bb-482">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-482">**Information Fields**</span></span>

- <span data-ttu-id="058bb-483">Campo de información 1: puntero que señala al grupo de bloques de memoria.</span><span class="sxs-lookup"><span data-stu-id="058bb-483">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="058bb-484">Campo de información 2: puntero que señala al bloque que se va a liberar.</span><span class="sxs-lookup"><span data-stu-id="058bb-484">Info Field 2: Pointer to block to release.</span></span>
- <span data-ttu-id="058bb-485">Campo de información 3: número de subprocesos suspendidos en este grupo de bloques.</span><span class="sxs-lookup"><span data-stu-id="058bb-485">Info Field 3: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="058bb-486">Campo de información 4: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-486">Info Field 4: Stack pointer at the time of the call.</span></span>

### <a name="byte-allocate"></a><span data-ttu-id="058bb-487">Asignación de bytes</span><span class="sxs-lookup"><span data-stu-id="058bb-487">Byte Allocate</span></span> 

#### <a name="tx_byte_allocate"></a><span data-ttu-id="058bb-488">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="058bb-488">tx_byte_allocate</span></span>

<span data-ttu-id="058bb-489">**Icono** ![Icono de Asignación de bytes](./media/user-guide/tx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-489">**Icon** ![Byte allocate icon](./media/user-guide/tx-events/image15.png)</span></span>

<span data-ttu-id="058bb-490">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-490">**Description**</span></span>

<span data-ttu-id="058bb-491">Este evento representa la asignación de memoria mediante tx_byte_allocate.</span><span class="sxs-lookup"><span data-stu-id="058bb-491">This event represents allocating memory via tx_byte_allocate.</span></span> <span data-ttu-id="058bb-492">Si se realiza correctamente, se devuelve la dirección de la memoria asignada en el segundo campo de información.</span><span class="sxs-lookup"><span data-stu-id="058bb-492">If successful, the address of the memory allocated is returned in the second information field.</span></span>

<span data-ttu-id="058bb-493">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-493">**Information Fields**</span></span>
- <span data-ttu-id="058bb-494">Campo de información 1: puntero que señala al grupo de bytes correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-494">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="058bb-495">Campo de información 2: puntero que señala a la memoria devuelta (si se realiza correctamente).</span><span class="sxs-lookup"><span data-stu-id="058bb-495">Info Field 2: Pointer to the memory returned (if successful).</span></span>
- <span data-ttu-id="058bb-496">Campo de información 3: número de bytes solicitados.</span><span class="sxs-lookup"><span data-stu-id="058bb-496">Info Field 3: Number of bytes requested.</span></span> <span data-ttu-id="058bb-497">Campo de información 4: opción de espera proporcionada a la llamada tx_byte_allocate.</span><span class="sxs-lookup"><span data-stu-id="058bb-497">Info Field 4: The wait option supplied to the tx_byte_allocate call.</span></span>

### <a name="byte-pool-create"></a><span data-ttu-id="058bb-498">Creación de grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="058bb-498">Byte Pool Create</span></span>

#### <a name="tx_byte_pool_create"></a><span data-ttu-id="058bb-499">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="058bb-499">tx_byte_pool_create</span></span>

<span data-ttu-id="058bb-500">**Icono** ![Icono de Creación de grupo de bytes](./media/user-guide/tx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-500">**Icon** ![Byte pool create icon](./media/user-guide/tx-events/image16.png)</span></span>

<span data-ttu-id="058bb-501">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-501">**Description**</span></span>

<span data-ttu-id="058bb-502">Este evento representa la creación de un grupo de bytes mediante tx_byte_pool_create.</span><span class="sxs-lookup"><span data-stu-id="058bb-502">This event represents creating a byte pool via tx_byte_pool_create.</span></span>

<span data-ttu-id="058bb-503">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-503">**Information Fields**</span></span>

- <span data-ttu-id="058bb-504">Campo de información 1: puntero que señala al grupo de bytes correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-504">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="058bb-505">Campo de información 2: puntero que señala al inicio del área de memoria.</span><span class="sxs-lookup"><span data-stu-id="058bb-505">Info Field 2: Pointer to the start of the memory area.</span></span> <span data-ttu-id="058bb-506">Campo de información 3: número de bytes en el grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="058bb-506">Info Field 3: Number of bytes in the byte pool.</span></span>
- <span data-ttu-id="058bb-507">Campo de información 4: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-507">Info Field 4: The stack pointer at the time of the call.</span></span>

### <a name="byte-pool-delete"></a><span data-ttu-id="058bb-508">Eliminación de grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="058bb-508">Byte Pool Delete</span></span> 

#### <a name="tx_byte_pool_delete"></a><span data-ttu-id="058bb-509">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="058bb-509">tx_byte_pool_delete</span></span>

<span data-ttu-id="058bb-510">**Icono** ![Icono de Eliminación de grupo de bytes](./media/user-guide/tx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-510">**Icon** ![Byte pool delete icon](./media/user-guide/tx-events/image17.png)</span></span>

<span data-ttu-id="058bb-511">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-511">**Description**</span></span>

<span data-ttu-id="058bb-512">Este evento representa la eliminación de un grupo de bytes mediante tx_byte_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="058bb-512">This event represents deleting a byte pool via tx_byte_pool_delete.</span></span>

<span data-ttu-id="058bb-513">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-513">**Information Fields**</span></span>

- <span data-ttu-id="058bb-514">Campo de información 1: puntero que señala al grupo de bytes correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-514">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="058bb-515">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-515">Info Field 2: The stack pointer at the time of the call.</span></span>
- <span data-ttu-id="058bb-516">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-516">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-517">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-517">Info Field 4: Not used.</span></span>

### <a name="byte-pool-information-get"></a><span data-ttu-id="058bb-518">Obtención de información de grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="058bb-518">Byte Pool Information Get</span></span>

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="058bb-519">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-519">tx_byte_pool_info_get</span></span>

<span data-ttu-id="058bb-520">**Icono** ![Icono de Obtención de información de grupo de bytes](./media/user-guide/tx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-520">**Icon** ![Byte pool information get icon](./media/user-guide/tx-events/image18.png)</span></span>

<span data-ttu-id="058bb-521">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-521">**Description**</span></span>

<span data-ttu-id="058bb-522">Este evento representa la obtención de información del grupo de bytes mediante tx_byte_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-522">This event represents getting byte pool information via tx_byte_pool_info_get.</span></span>

<span data-ttu-id="058bb-523">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-523">**Information Fields**</span></span>

- <span data-ttu-id="058bb-524">Campo de información 1: puntero que señala al grupo de bytes correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-524">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="058bb-525">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-525">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-526">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-526">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-527">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-527">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-info-get"></a><span data-ttu-id="058bb-528">Obtención de información de rendimiento del grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="058bb-528">Byte Pool Performance Info Get</span></span> 

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="058bb-529">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-529">tx_byte_pool_info_get</span></span>

<span data-ttu-id="058bb-530">**Icono** ![Icono de Obtención de información de rendimiento del grupo de bytes](./media/user-guide/tx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-530">**Icon** ![Byte pool performance info get icon](./media/user-guide/tx-events/image19.png)</span></span>

<span data-ttu-id="058bb-531">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-531">**Description**</span></span>

<span data-ttu-id="058bb-532">Este evento representa la obtención de información de rendimiento del grupo de bytes mediante tx_byte_pool_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-532">This event represents getting byte pool performance information via tx_byte_pool_performance_info_get.</span></span>

<span data-ttu-id="058bb-533">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-533">**Information Fields**</span></span>

- <span data-ttu-id="058bb-534">Campo de información 1: puntero que señala al grupo de bytes correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-534">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="058bb-535">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-535">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-536">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-536">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-537">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-537">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-system-info-get"></a><span data-ttu-id="058bb-538">Obtención de información de rendimiento del sistema del grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="058bb-538">Byte Pool Performance System Info Get</span></span> 

#### <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="058bb-539">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-539">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="058bb-540">**Icono** ![Icono de Obtención de información de rendimiento del sistema del grupo de bytes](./media/user-guide/tx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-540">**Icon** ![Byte pool performance system info get icon](./media/user-guide/tx-events/image20.png)</span></span>

<span data-ttu-id="058bb-541">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-541">**Description**</span></span>

<span data-ttu-id="058bb-542">Este evento representa la obtención de información de rendimiento del sistema del grupo de bytes mediante tx_byte_pool_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-542">This event represents getting byte pool performance system information via tx_byte_pool_performance_system_info_get.</span></span>

<span data-ttu-id="058bb-543">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-543">**Information Fields**</span></span>

- <span data-ttu-id="058bb-544">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-544">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-545">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-545">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-546">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-546">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-547">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-547">Info Field 4: Not used.</span></span>

### <a name="byte-pool-prioritize"></a><span data-ttu-id="058bb-548">Priorización de grupos de bytes</span><span class="sxs-lookup"><span data-stu-id="058bb-548">Byte Pool Prioritize</span></span>

#### <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="058bb-549">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="058bb-549">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="058bb-550">**Icono** ![Icono de Priorización de grupos de bytes](./media/user-guide/tx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-550">**Icon** ![Byte pool prioritize icon](./media/user-guide/tx-events/image21.png)</span></span>

<span data-ttu-id="058bb-551">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-551">**Description**</span></span>

<span data-ttu-id="058bb-552">Este evento representa la priorización de la lista de suspensiones del grupo de bytes mediante tx_byte_pool_prioritize.</span><span class="sxs-lookup"><span data-stu-id="058bb-552">This event represents prioritizing the byte pool's suspension list via tx_byte_pool_prioritize.</span></span>

<span data-ttu-id="058bb-553">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-553">**Information Fields**</span></span>

- <span data-ttu-id="058bb-554">Campo de información 1: puntero que señala al grupo de bytes correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-554">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="058bb-555">Campo de información 2: número de subprocesos suspendidos actualmente en el grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="058bb-555">Info Field 2: Number of threads currently suspended on byte pool.</span></span>
- <span data-ttu-id="058bb-556">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-556">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-557">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-557">Info Field 4: Not used.</span></span>

### <a name="byte-release"></a><span data-ttu-id="058bb-558">Liberación de bytes</span><span class="sxs-lookup"><span data-stu-id="058bb-558">Byte Release</span></span>

#### <a name="tx_byte_release"></a><span data-ttu-id="058bb-559">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="058bb-559">tx_byte_release</span></span>

<span data-ttu-id="058bb-560">**Icono** ![Icono de Liberación de bytes](./media/user-guide/tx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-560">**Icon** ![Byte release icon](./media/user-guide/tx-events/image22.png)</span></span>

<span data-ttu-id="058bb-561">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-561">**Description**</span></span>

<span data-ttu-id="058bb-562">Este evento representa la liberación de un bloque de memoria asignado a un grupo de bytes mediante tx_byte_release.</span><span class="sxs-lookup"><span data-stu-id="058bb-562">This event represents releasing a block of memory allocated from a byte pool via tx_byte_release.</span></span>

<span data-ttu-id="058bb-563">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-563">**Information Fields**</span></span>

- <span data-ttu-id="058bb-564">Campo de información 1: puntero que señala al grupo de bytes correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-564">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="058bb-565">Campo de información 2: puntero que señala a la memoria de grupo de bytes previamente asignada.</span><span class="sxs-lookup"><span data-stu-id="058bb-565">Info Field 2: Pointer to previously allocated byte pool memory.</span></span>
- <span data-ttu-id="058bb-566">Campo de información 3: número de subprocesos suspendidos en este grupo de bytes.</span><span class="sxs-lookup"><span data-stu-id="058bb-566">Info Field 3: Number of threads suspended on this byte pool.</span></span>
- <span data-ttu-id="058bb-567">Campo de información 4: número de bytes de memoria disponibles.</span><span class="sxs-lookup"><span data-stu-id="058bb-567">Info Field 4: Number of available bytes of memory.</span></span>

### <a name="event-flags-create"></a><span data-ttu-id="058bb-568">Creación de marcas de evento</span><span class="sxs-lookup"><span data-stu-id="058bb-568">Event Flags Create</span></span> 

#### <a name="tx_event_flags_create"></a><span data-ttu-id="058bb-569">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="058bb-569">tx_event_flags_create</span></span>

<span data-ttu-id="058bb-570">**Icono** ![Icono de Creación de marcas de evento](./media/user-guide/tx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-570">**Icon** ![Event flags create icon](./media/user-guide/tx-events/image23.png)</span></span>

<span data-ttu-id="058bb-571">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-571">**Description**</span></span>

<span data-ttu-id="058bb-572">Este evento representa la creación de un nuevo grupo de marcas de evento mediante tx_event_flags_create.</span><span class="sxs-lookup"><span data-stu-id="058bb-572">This event represents creating a new event flags group via tx_event_flags_create.</span></span>

<span data-ttu-id="058bb-573">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-573">**Information Fields**</span></span> 
- <span data-ttu-id="058bb-574">Campo de información 1: puntero que señala al bloque de control de grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="058bb-574">Info Field 1: Pointer to event flags group control block.</span></span>
- <span data-ttu-id="058bb-575">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-575">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-576">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-576">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-577">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-577">Info Field 4: Not used.</span></span>

### <a name="event-flags-delete"></a><span data-ttu-id="058bb-578">Eliminación de marcas de evento</span><span class="sxs-lookup"><span data-stu-id="058bb-578">Event Flags Delete</span></span> 

#### <a name="tx_event_flags_delete"></a><span data-ttu-id="058bb-579">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="058bb-579">tx_event_flags_delete</span></span>

<span data-ttu-id="058bb-580">**Icono** ![Icono de Eliminación de marcas de evento](./media/user-guide/tx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-580">**Icon** ![Event flags delete icon](./media/user-guide/tx-events/image24.png)</span></span>

<span data-ttu-id="058bb-581">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-581">**Description**</span></span>

<span data-ttu-id="058bb-582">Este evento representa la eliminación de un grupo de marcas de evento mediante tx_event_flags_delete.</span><span class="sxs-lookup"><span data-stu-id="058bb-582">This event represents deleting an event flags group via tx_event_flags_delete.</span></span>

<span data-ttu-id="058bb-583">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-583">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-584">Campo de información 1: puntero que señala al grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="058bb-584">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="058bb-585">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-585">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-586">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-586">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-587">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-587">Info Field 4: Not used.</span></span>

### <a name="event-flags-get"></a><span data-ttu-id="058bb-588">Obtención de marcas de evento</span><span class="sxs-lookup"><span data-stu-id="058bb-588">Event Flags Get</span></span> 

#### <a name="tx_event_flags_get"></a><span data-ttu-id="058bb-589">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="058bb-589">tx_event_flags_get</span></span>

<span data-ttu-id="058bb-590">**Icono** ![Icono de Obtención de marcas de evento](./media/user-guide/tx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-590">**Icon** ![Event flags gt icon](./media/user-guide/tx-events/image25.png)</span></span>

<span data-ttu-id="058bb-591">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-591">**Description**</span></span>

<span data-ttu-id="058bb-592">Este evento representa la recuperación de marcas de evento de un grupo de marcas de evento existente mediante tx_event_flags_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-592">This event represents retrieving event flags from an existing event flags group via tx_event_flags_get.</span></span>

<span data-ttu-id="058bb-593">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-593">**Information Fields**</span></span>

- <span data-ttu-id="058bb-594">Campo de información 1: puntero que señala al grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="058bb-594">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="058bb-595">Campo de información 2: marcas de evento solicitadas.</span><span class="sxs-lookup"><span data-stu-id="058bb-595">Info Field 2: Event flags requested.</span></span>
- <span data-ttu-id="058bb-596">Campo de información 3: marcas de evento establecidas actualmente en el grupo.</span><span class="sxs-lookup"><span data-stu-id="058bb-596">Info Field 3: Event flags currently set in the group.</span></span>
- <span data-ttu-id="058bb-597">Campo de información 4: opción solicitada en la obtención de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="058bb-597">Info Field 4: Option requested on the event flags get.</span></span>

### <a name="event-flags-information-get"></a><span data-ttu-id="058bb-598">Obtención de información de marcas de evento</span><span class="sxs-lookup"><span data-stu-id="058bb-598">Event Flags Information Get</span></span>

#### <a name="tx_event_flags_info_get"></a><span data-ttu-id="058bb-599">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-599">tx_event_flags_info_get</span></span>

<span data-ttu-id="058bb-600">**Icono** ![Icono de Obtención de información de marcas de evento](./media/user-guide/tx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-600">**Icon** ![Event flags information get icon](./media/user-guide/tx-events/image26.png)</span></span>

<span data-ttu-id="058bb-601">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-601">**Description**</span></span>

<span data-ttu-id="058bb-602">Este evento representa la recuperación de información relacionada con un grupo de marcas de evento existente mediante tx_event_flags_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-602">This event represents retrieving information regarding an existing event flags group via tx_event_flags_info_get.</span></span>

<span data-ttu-id="058bb-603">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-603">**Information Fields**</span></span>

- <span data-ttu-id="058bb-604">Campo de información 1: puntero que señala al grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="058bb-604">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="058bb-605">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-605">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-606">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-606">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-607">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-607">Info Field 4: Not used.</span></span>

### <a name="event-flags-performance-information-get"></a><span data-ttu-id="058bb-608">Obtención de información de rendimiento de marcas de evento</span><span class="sxs-lookup"><span data-stu-id="058bb-608">Event Flags Performance Information Get</span></span> 

#### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="058bb-609">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-609">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="058bb-610">**Icono** ![Icono de Obtención de información de rendimiento de marcas de evento](./media/user-guide/tx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-610">**Icon** ![Event flags performance information get icon](./media/user-guide/tx-events/image27.png)</span></span>

<span data-ttu-id="058bb-611">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-611">**Description**</span></span>

<span data-ttu-id="058bb-612">Este evento representa la recuperación de información de rendimiento relacionada con un grupo de marcas de evento existente mediante tx_event_flags_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-612">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_info_get.</span></span>

<span data-ttu-id="058bb-613">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-613">**Information Fields**</span></span> 
- <span data-ttu-id="058bb-614">Campo de información 1: puntero que señala al grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="058bb-614">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="058bb-615">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-615">Info Field 2: Not used</span></span>
- <span data-ttu-id="058bb-616">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-616">Info Field 3: Not used</span></span>
- <span data-ttu-id="058bb-617">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-617">Info Field 4: Not Used</span></span>

### <a name="event-flags-performance-system-info-get"></a><span data-ttu-id="058bb-618">Obtención de información de rendimiento del sistema de marcas de evento</span><span class="sxs-lookup"><span data-stu-id="058bb-618">Event Flags Performance System Info Get</span></span>

#### <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="058bb-619">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-619">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="058bb-620">**Icono** ![Icono de Obtención de información de rendimiento del sistema de marcas de evento](./media/user-guide/tx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-620">**Icon** ![Event flags performance system info get icon](./media/user-guide/tx-events/image28.png)</span></span>

<span data-ttu-id="058bb-621">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-621">**Description**</span></span>

<span data-ttu-id="058bb-622">Este evento representa la recuperación de información de rendimiento relacionada con un grupo de marcas de evento existente mediante tx_event_flags_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-622">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_system_info_get.</span></span>

<span data-ttu-id="058bb-623">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-623">**Information Fields**</span></span>
- <span data-ttu-id="058bb-624">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-624">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-625">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-625">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-626">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-626">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-627">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-627">Info Field 4: Not used.</span></span>

### <a name="event-flags-set"></a><span data-ttu-id="058bb-628">Establecimiento de marcas de evento</span><span class="sxs-lookup"><span data-stu-id="058bb-628">Event Flags Set</span></span> 

#### <a name="tx_event_flags_set"></a><span data-ttu-id="058bb-629">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="058bb-629">tx_event_flags_set</span></span>

<span data-ttu-id="058bb-630">**Icono** ![Icono de Establecimiento de marcas de evento](./media/user-guide/tx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-630">**Icon** ![Event flags set icon](./media/user-guide/tx-events/image29.png)</span></span>

<span data-ttu-id="058bb-631">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-631">**Description**</span></span>

<span data-ttu-id="058bb-632">Este evento representa el establecimiento (o borrado) de marcas de evento en un grupo de marcas de evento existente mediante tx_event_flags_set.</span><span class="sxs-lookup"><span data-stu-id="058bb-632">This event represents setting (or clearing) event flags in an existing event flags group via tx_event_flags_set.</span></span>

<span data-ttu-id="058bb-633">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-633">**Information Fields**</span></span>

- <span data-ttu-id="058bb-634">Campo de información 1: puntero que señala al grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="058bb-634">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="058bb-635">Campo de información 2: marcas de evento que se van a establecer (o borrar).</span><span class="sxs-lookup"><span data-stu-id="058bb-635">Info Field 2: Event flags to set (or clear).</span></span>
- <span data-ttu-id="058bb-636">Campo de información 3: opción de marca de evento AND u OR.</span><span class="sxs-lookup"><span data-stu-id="058bb-636">Info Field 3: AND or OR event flag option.</span></span>
- <span data-ttu-id="058bb-637">Campo de información 4: número de subprocesos suspendidos en este grupo de marca de evento.</span><span class="sxs-lookup"><span data-stu-id="058bb-637">Info Field 4: Number of threads suspended on event flag group.</span></span>

### <a name="event-flags-set-notify"></a><span data-ttu-id="058bb-638">Notificación de establecimiento de marcas de evento</span><span class="sxs-lookup"><span data-stu-id="058bb-638">Event Flags Set Notify</span></span>

#### <a name="tx_event_flags_set_notify"></a><span data-ttu-id="058bb-639">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="058bb-639">tx_event_flags_set_notify</span></span>

<span data-ttu-id="058bb-640">**Icono** ![Icono de Notificación de establecimiento de marcas de evento](./media/user-guide/tx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-640">**Icon** ![Event flags set notify icon](./media/user-guide/tx-events/image30.png)</span></span>

<span data-ttu-id="058bb-641">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-641">**Description**</span></span>

<span data-ttu-id="058bb-642">Este evento representa el registro de una devolución de llamada de notificación para cualquier operación de establecimiento de marcas de evento en un grupo de marcas de evento existente mediante tx_event_flags_set_notify.</span><span class="sxs-lookup"><span data-stu-id="058bb-642">This event represents registering a notification callback for any event flag set operation on an existing event flags group via tx_event_flags_set_notify.</span></span>

<span data-ttu-id="058bb-643">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-643">**Information Fields**</span></span>

- <span data-ttu-id="058bb-644">Campo de información 1: puntero que señala al grupo de marcas de evento.</span><span class="sxs-lookup"><span data-stu-id="058bb-644">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="058bb-645">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-645">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-646">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-646">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-647">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-647">Info Field 4: Not used.</span></span>

### <a name="interrupt-control"></a><span data-ttu-id="058bb-648">Control de interrupción</span><span class="sxs-lookup"><span data-stu-id="058bb-648">Interrupt Control</span></span> 

#### <a name="tx_interrupt_control"></a><span data-ttu-id="058bb-649">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="058bb-649">tx_interrupt_control</span></span>

<span data-ttu-id="058bb-650">**Icono** ![Icono de Control de interrupción](./media/user-guide/tx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-650">**Icon** ![Interrupt control icon](./media/user-guide/tx-events/image31.png)</span></span>

<span data-ttu-id="058bb-651">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-651">**Description**</span></span>

<span data-ttu-id="058bb-652">Este evento representa el cambio de la posición de bloqueo de interrupción del procesador mediante tx_interrupt_control.</span><span class="sxs-lookup"><span data-stu-id="058bb-652">This event represents changing the interrupt lockout posture of the processor via tx_interrupt_control.</span></span>

<span data-ttu-id="058bb-653">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-653">**Information Fields**</span></span>

- <span data-ttu-id="058bb-654">Campo de información 1: nueva postura de interrupción.</span><span class="sxs-lookup"><span data-stu-id="058bb-654">Info Field 1: New interrupt posture.</span></span>
- <span data-ttu-id="058bb-655">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-655">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-656">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-656">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-657">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-657">Info Field 4: Not used.</span></span>

### <a name="mutex-create"></a><span data-ttu-id="058bb-658">Creación de exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="058bb-658">Mutex Create</span></span> 

#### <a name="tx_mutex_create"></a><span data-ttu-id="058bb-659">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="058bb-659">tx_mutex_create</span></span>

<span data-ttu-id="058bb-660">**Icono** ![Icono de Creación de exclusión mutua](./media/user-guide/tx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-660">**Icon** ![Mutex create icon](./media/user-guide/tx-events/image32.png)</span></span>

<span data-ttu-id="058bb-661">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-661">**Description**</span></span>

<span data-ttu-id="058bb-662">Este evento representa la creación de una exclusión mutua mediante tx_mutex_create.</span><span class="sxs-lookup"><span data-stu-id="058bb-662">This event represents creating a mutex via tx_mutex_create.</span></span>

<span data-ttu-id="058bb-663">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-663">**Information Fields**</span></span>

- <span data-ttu-id="058bb-664">Campo de información 1: puntero que señala al bloque de control de exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="058bb-664">Info Field 1: Pointer to mutex control block.</span></span>
- <span data-ttu-id="058bb-665">Campo de información 2: opción de herencia de prioridad.</span><span class="sxs-lookup"><span data-stu-id="058bb-665">Info Field 2: Priority inheritance option</span></span>
- <span data-ttu-id="058bb-666">(TX_INHERIT o TX_NO_INHERIT).</span><span class="sxs-lookup"><span data-stu-id="058bb-666">(TX_INHERIT or TX_NO_INHERIT).</span></span>
- <span data-ttu-id="058bb-667">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-667">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-668">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-668">Info Field 4: Not used.</span></span>

### <a name="mutex-delete"></a><span data-ttu-id="058bb-669">Eliminación de exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="058bb-669">Mutex Delete</span></span> 

#### <a name="tx_mutex_delete"></a><span data-ttu-id="058bb-670">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="058bb-670">tx_mutex_delete</span></span>

<span data-ttu-id="058bb-671">**Icono** ![Icono de Eliminación de exclusión mutua](./media/user-guide/tx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-671">**Icon** ![Mutex delete icon](./media/user-guide/tx-events/image33.png)</span></span>

<span data-ttu-id="058bb-672">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-672">**Description**</span></span>

<span data-ttu-id="058bb-673">Este evento representa la eliminación de una exclusión mutua mediante tx_mutex_delete.</span><span class="sxs-lookup"><span data-stu-id="058bb-673">This event represents deleting a mutex via tx_mutex_delete.</span></span>

<span data-ttu-id="058bb-674">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-674">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-675">Campo de información 1: puntero que señala a la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="058bb-675">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="058bb-676">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-676">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-677">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-677">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-678">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-678">Info Field 4: Not used.</span></span>

### <a name="mutex-get"></a><span data-ttu-id="058bb-679">Obtención de exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="058bb-679">Mutex Get</span></span> 

#### <a name="tx_mutex_get"></a><span data-ttu-id="058bb-680">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="058bb-680">tx_mutex_get</span></span>

<span data-ttu-id="058bb-681">**Icono** ![Icono de Obtención de exclusión mutua](./media/user-guide/tx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-681">**Icon** ![Mutex get icon](./media/user-guide/tx-events/image34.png)</span></span>

<span data-ttu-id="058bb-682">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-682">**Description**</span></span>

<span data-ttu-id="058bb-683">Este evento representa la obtención de una exclusión mutua mediante tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-683">This event represents obtaining a mutex via tx_mutex_get.</span></span>

<span data-ttu-id="058bb-684">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-684">**Information Fields**</span></span>

- <span data-ttu-id="058bb-685">Campo de información 1: puntero que señala a la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="058bb-685">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="058bb-686">Campo de información 2: opción de espera proporcionada a la llamada tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-686">Info Field 2: The wait option supplied to the tx_mutex_get call.</span></span>
- <span data-ttu-id="058bb-687">Campo de información 3: puntero que señala al subproceso que posee la exclusión mutua (NULL implica que la exclusión mutua no es de su propiedad).</span><span class="sxs-lookup"><span data-stu-id="058bb-687">Info Field 3: Pointer to thread that owns the mutex (NULL implies the mutex is not owned).</span></span>
- <span data-ttu-id="058bb-688">Campo de información 4: número de veces que el subproceso propietario ha llamado a tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-688">Info Field 4: Number of times the owning thread has called tx_mutex_get.</span></span>

### <a name="mutex-information-get"></a><span data-ttu-id="058bb-689">Obtención de información de exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="058bb-689">Mutex Information Get</span></span>

#### <a name="tx_mutex_info_get"></a><span data-ttu-id="058bb-690">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-690">tx_mutex_info_get</span></span>

<span data-ttu-id="058bb-691">**Icono** ![Icono de Obtención de información de exclusión mutua](./media/user-guide/tx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-691">**Icon** ![Mutex information get icon](./media/user-guide/tx-events/image35.png)</span></span>

<span data-ttu-id="058bb-692">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-692">**Description**</span></span>

<span data-ttu-id="058bb-693">Este evento representa la recuperación de información de exclusión mutua mediante tx_mutex_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-693">This event represents retrieving mutex information via tx_mutex_info_get.</span></span>

<span data-ttu-id="058bb-694">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-694">**Information Fields**</span></span>

- <span data-ttu-id="058bb-695">Campo de información 1: puntero que señala a la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="058bb-695">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="058bb-696">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-696">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-697">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-697">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-698">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-698">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-information-get"></a><span data-ttu-id="058bb-699">Obtención de información de rendimiento de exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="058bb-699">Mutex Performance Information Get</span></span> 

#### <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="058bb-700">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-700">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="058bb-701">**Icono** ![Icono de Obtención de información de rendimiento de exclusión mutua](./media/user-guide/tx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-701">**Icon** ![Mutex performance information get icon](./media/user-guide/tx-events/image36.png)</span></span>

<span data-ttu-id="058bb-702">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-702">**Description**</span></span>

<span data-ttu-id="058bb-703">Este evento representa la recuperación de información de rendimiento de exclusión mutua mediante tx_mutex_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-703">This event represents retrieving mutex performance information via tx_mutex_performance_info_get.</span></span>

<span data-ttu-id="058bb-704">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-704">**Information Fields**</span></span>

- <span data-ttu-id="058bb-705">Campo de información 1: puntero que señala a la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="058bb-705">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="058bb-706">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-706">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-707">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-707">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-708">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-708">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-system-info-get"></a><span data-ttu-id="058bb-709">Obtención de información de rendimiento del sistema de exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="058bb-709">Mutex Performance System Info Get</span></span>

#### <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="058bb-710">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-710">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="058bb-711">**Icono** ![Icono de Obtención de información de rendimiento del sistema de exclusión mutua](./media/user-guide/tx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-711">**Icon** ![Mutex performance system info get icon](./media/user-guide/tx-events/image37.png)</span></span>

<span data-ttu-id="058bb-712">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-712">**Description**</span></span>

<span data-ttu-id="058bb-713">Este evento representa la recuperación de información de rendimiento del sistema de exclusión mutua mediante tx_mutex_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-713">This event represents retrieving mutex system performance information via tx_mutex_performance_system_info_get.</span></span>

<span data-ttu-id="058bb-714">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-714">**Information Fields**</span></span>

- <span data-ttu-id="058bb-715">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-715">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-716">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-716">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-717">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-717">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-718">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-718">Info Field 4: Not used.</span></span>

### <a name="mutex-prioritize"></a><span data-ttu-id="058bb-719">Priorización de exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="058bb-719">Mutex Prioritize</span></span> 

#### <a name="tx_mutex_prioritize"></a><span data-ttu-id="058bb-720">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="058bb-720">tx_mutex_prioritize</span></span>

<span data-ttu-id="058bb-721">**Icono** ![Icono de Priorización de exclusión mutua](./media/user-guide/tx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-721">**Icon** ![Mutex prioritize icon](./media/user-guide/tx-events/image38.png)</span></span>

<span data-ttu-id="058bb-722">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-722">**Description**</span></span>

<span data-ttu-id="058bb-723">Este evento representa la prioridad de la lista de suspensiones de exclusión mutua mediante tx_mutex_prioritize.</span><span class="sxs-lookup"><span data-stu-id="058bb-723">This event represents prioritizing the mutex's suspension list via tx_mutex_prioritize.</span></span>

<span data-ttu-id="058bb-724">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-724">**Information Fields**</span></span>

- <span data-ttu-id="058bb-725">Campo de información 1: puntero que señala a la exclusión mutua correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-725">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="058bb-726">Campo de información 2: número de subprocesos suspendidos actualmente en la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="058bb-726">Info Field 2: Number of threads currently suspended on the mutex.</span></span>
- <span data-ttu-id="058bb-727">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-727">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-728">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-728">Info Field 4: Not used.</span></span>

### <a name="mutex-put"></a><span data-ttu-id="058bb-729">Colocación de exclusión mutua</span><span class="sxs-lookup"><span data-stu-id="058bb-729">Mutex Put</span></span> 

#### <a name="tx_mutex_put"></a><span data-ttu-id="058bb-730">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="058bb-730">tx_mutex_put</span></span>

<span data-ttu-id="058bb-731">**Icono** ![Icono de Colocación de exclusión mutua](./media/user-guide/tx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-731">**Icon** ![Mutex put icon](./media/user-guide/tx-events/image39.png)</span></span>

<span data-ttu-id="058bb-732">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-732">**Description**</span></span>

<span data-ttu-id="058bb-733">Este evento representa la liberación de una exclusión mutua previamente en propiedad mediante tx_mutex_put.</span><span class="sxs-lookup"><span data-stu-id="058bb-733">This event represents releasing a previously owned mutex via tx_mutex_put.</span></span>

<span data-ttu-id="058bb-734">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-734">**Information Fields**</span></span>

- <span data-ttu-id="058bb-735">Campo de información 1: puntero que señala a la exclusión mutua correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-735">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="058bb-736">Campo de información 2: puntero de subproceso que posee la exclusión mutua.</span><span class="sxs-lookup"><span data-stu-id="058bb-736">Info Field 2: Pointer of thread owning the mutex.</span></span>
- <span data-ttu-id="058bb-737">Campo de información 3: número de solicitudes de obtención de exclusión mutua pendientes.</span><span class="sxs-lookup"><span data-stu-id="058bb-737">Info Field 3: Number of outstanding mutex get requests.</span></span>
- <span data-ttu-id="058bb-738">Campo de información 4: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-738">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="queue-create"></a><span data-ttu-id="058bb-739">Creación de colas</span><span class="sxs-lookup"><span data-stu-id="058bb-739">Queue Create</span></span> 

#### <a name="tx_queue_create"></a><span data-ttu-id="058bb-740">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="058bb-740">tx_queue_create</span></span>

<span data-ttu-id="058bb-741">**Icono** ![Icono de Creación de colas](./media/user-guide/tx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-741">**Icon** ![Queue create icon](./media/user-guide/tx-events/image40.png)</span></span>

<span data-ttu-id="058bb-742">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-742">**Description**</span></span>

<span data-ttu-id="058bb-743">Este evento representa la creación de una cola de mensajes mediante tx_queue_create.</span><span class="sxs-lookup"><span data-stu-id="058bb-743">This event represents creating a message queue via tx_queue_create.</span></span>

<span data-ttu-id="058bb-744">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-744">**Information Fields**</span></span>

- <span data-ttu-id="058bb-745">Campo de información 1: puntero que señala al bloque de control de colas.</span><span class="sxs-lookup"><span data-stu-id="058bb-745">Info Field 1: Pointer to queue control block.</span></span>
- <span data-ttu-id="058bb-746">Campo de información 2: tamaño del mensaje en términos de palabras de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="058bb-746">Info Field 2: Size of message – in terms of 32-bit words.</span></span>
- <span data-ttu-id="058bb-747">Campo de información 3: puntero que señala al inicio del área de memoria de la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-747">Info Field 3: Pointer to start of queue memory area.</span></span>
- <span data-ttu-id="058bb-748">Campo de información 4: número de bytes en el área de memoria de la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-748">Info Field 4: Number of bytes in the queue memory area.</span></span>

### <a name="queue-delete"></a><span data-ttu-id="058bb-749">Eliminación de colas</span><span class="sxs-lookup"><span data-stu-id="058bb-749">Queue Delete</span></span> 

#### <a name="tx_queue_delete"></a><span data-ttu-id="058bb-750">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="058bb-750">tx_queue_delete</span></span>

<span data-ttu-id="058bb-751">**Icono** ![Icono de Eliminación de colas](./media/user-guide/tx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-751">**Icon** ![Queue delete icon](./media/user-guide/tx-events/image41.png)</span></span>

<span data-ttu-id="058bb-752">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-752">**Description**</span></span>

<span data-ttu-id="058bb-753">Este evento representa la eliminación de una cola mediante tx_queue_delete.</span><span class="sxs-lookup"><span data-stu-id="058bb-753">This event represents deleting a queue via tx_queue_delete.</span></span>

<span data-ttu-id="058bb-754">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-754">**Information Fields**</span></span>

- <span data-ttu-id="058bb-755">Campo de información 1: puntero que señala a la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-755">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="058bb-756">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-756">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-757">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-757">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-758">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-758">Info Field 4: Not used.</span></span>

### <a name="queue-flush"></a><span data-ttu-id="058bb-759">Vaciado de colas</span><span class="sxs-lookup"><span data-stu-id="058bb-759">Queue Flush</span></span> 

#### <a name="tx_queue_flush"></a><span data-ttu-id="058bb-760">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="058bb-760">tx_queue_flush</span></span>

<span data-ttu-id="058bb-761">**Icono** ![Icono de Vaciado de colas](./media/user-guide/tx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-761">**Icon** ![Queue flush icon](./media/user-guide/tx-events/image42.png)</span></span>

<span data-ttu-id="058bb-762">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-762">**Description**</span></span>

<span data-ttu-id="058bb-763">Este evento representa el vaciado (borrar todo el contenido de la cola) de una cola mediante tx_queue_flush.</span><span class="sxs-lookup"><span data-stu-id="058bb-763">This event represents flushing (clearing all queue contents) of a queue via tx_queue_flush.</span></span>

<span data-ttu-id="058bb-764">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-764">**Information Fields**</span></span>

- <span data-ttu-id="058bb-765">Campo de información 1: puntero que señala a la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-765">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="058bb-766">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-766">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-767">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-767">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-768">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-768">Info Field 4: Not used.</span></span>

### <a name="queue-front-send"></a><span data-ttu-id="058bb-769">Envío al inicio de cola</span><span class="sxs-lookup"><span data-stu-id="058bb-769">Queue Front Send</span></span> 

#### <a name="tx_queue_front_send"></a><span data-ttu-id="058bb-770">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="058bb-770">tx_queue_front_send</span></span>

<span data-ttu-id="058bb-771">**Icono** ![Icono de Envío al inicio de cola](./media/user-guide/tx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-771">**Icon** ![Queue front send icon](./media/user-guide/tx-events/image43.png)</span></span>

<span data-ttu-id="058bb-772">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-772">**Description**</span></span>

<span data-ttu-id="058bb-773">Este evento representa el envío de un mensaje al principio de la cola mediante tx_queue_front_send.</span><span class="sxs-lookup"><span data-stu-id="058bb-773">This event represents sending a message to the front of a queue via tx_queue_front_send.</span></span>

<span data-ttu-id="058bb-774">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-774">**Information Fields**</span></span>

- <span data-ttu-id="058bb-775">Campo de información 1: puntero que señala a la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-775">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="058bb-776">Campo de información 2: puntero que señala al inicio del mensaje.</span><span class="sxs-lookup"><span data-stu-id="058bb-776">Info Field 2: Pointer to start of message.</span></span>
- <span data-ttu-id="058bb-777">Campo de información 3: opción de espera proporcionada a</span><span class="sxs-lookup"><span data-stu-id="058bb-777">Info Field 3: Wait option supplied to the</span></span>
- <span data-ttu-id="058bb-778">la llamada tx_queue_front_send.</span><span class="sxs-lookup"><span data-stu-id="058bb-778">tx_queue_front_send call.</span></span>
- <span data-ttu-id="058bb-779">Campo de información 4: número de mensajes ya puestos en cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-779">Info Field 4: Number of messages already enqueued.</span></span>

### <a name="queue-information-get"></a><span data-ttu-id="058bb-780">Obtención de información de cola</span><span class="sxs-lookup"><span data-stu-id="058bb-780">Queue Information Get</span></span> 

#### <a name="tx_queue_info_get"></a><span data-ttu-id="058bb-781">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-781">tx_queue_info_get</span></span>

<span data-ttu-id="058bb-782">**Icono** ![Icono de Obtención de información de cola](./media/user-guide/tx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-782">**Icon** ![Queue information get icon](./media/user-guide/tx-events/image44.png)</span></span>

<span data-ttu-id="058bb-783">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-783">**Description**</span></span>

<span data-ttu-id="058bb-784">Este evento representa la obtención de información sobre una cola mediante tx_queue_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-784">This event represents getting information about a queue via tx_queue_info_get.</span></span>

<span data-ttu-id="058bb-785">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-785">**Information Fields**</span></span> 
- <span data-ttu-id="058bb-786">Campo de información 1: puntero que señala a la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-786">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="058bb-787">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-787">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-788">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-788">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-789">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-789">Info Field 4: Not used.</span></span>

### <a name="queue-performance-info-get"></a><span data-ttu-id="058bb-790">Obtención de información de rendimiento de cola</span><span class="sxs-lookup"><span data-stu-id="058bb-790">Queue Performance Info Get</span></span> 

#### <a name="tx_queue_performance_info_get"></a><span data-ttu-id="058bb-791">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-791">tx_queue_performance_info_get</span></span>

<span data-ttu-id="058bb-792">**Icono** ![Icono de Obtención de información de rendimiento de cola](./media/user-guide/tx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-792">**Icon** ![Queue performance info get icon](./media/user-guide/tx-events/image45.png)</span></span>

<span data-ttu-id="058bb-793">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-793">**Description**</span></span>

<span data-ttu-id="058bb-794">Este evento representa la obtención de información de rendimiento sobre una cola mediante tx_queue_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-794">This event represents getting performance information about a queue via tx_queue_performance_info_get.</span></span>

<span data-ttu-id="058bb-795">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-795">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-796">Campo de información 1: puntero que señala a la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-796">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="058bb-797">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-797">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-798">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-798">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-799">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-799">Info Field 4: Not used.</span></span>

### <a name="queue-performance-system-info-get"></a><span data-ttu-id="058bb-800">Obtención de información de rendimiento del sistema de cola</span><span class="sxs-lookup"><span data-stu-id="058bb-800">Queue Performance System Info Get</span></span> 

#### <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="058bb-801">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-801">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="058bb-802">**Icono** ![Icono de Obtención de información de rendimiento del sistema de cola](./media/user-guide/tx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-802">**Icon** ![Queue performance system info get icon](./media/user-guide/tx-events/image46.png)</span></span>

<span data-ttu-id="058bb-803">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-803">**Description**</span></span>

<span data-ttu-id="058bb-804">Este evento representa la obtención de información de rendimiento del sistema acerca de todas las colas del sistema.</span><span class="sxs-lookup"><span data-stu-id="058bb-804">This event represents getting system performance information about all the queues in the system.</span></span>

<span data-ttu-id="058bb-805">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-805">**Information Fields**</span></span>

- <span data-ttu-id="058bb-806">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-806">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-807">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-807">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-808">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-808">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-809">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-809">Info Field 4: Not used.</span></span>

### <a name="queue-prioritize"></a><span data-ttu-id="058bb-810">Priorización de colas</span><span class="sxs-lookup"><span data-stu-id="058bb-810">Queue Prioritize</span></span> 

#### <a name="tx_queue_prioritize"></a><span data-ttu-id="058bb-811">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="058bb-811">tx_queue_prioritize</span></span>

<span data-ttu-id="058bb-812">**Icono** ![Icono de Priorización de colas](./media/user-guide/tx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-812">**Icon** ![Queue prioritize icon](./media/user-guide/tx-events/image47.png)</span></span>

<span data-ttu-id="058bb-813">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-813">**Description**</span></span>

<span data-ttu-id="058bb-814">Este evento representa la prioridad de la lista de suspensiones de cola mediante tx_queue_prioritize.</span><span class="sxs-lookup"><span data-stu-id="058bb-814">This event represents prioritizing the queue's suspension list via tx_queue_prioritize.</span></span>

<span data-ttu-id="058bb-815">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-815">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-816">Campo de información 1: puntero que señala a la cola correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-816">Info Field 1: Pointer to corresponding queue.</span></span>
- <span data-ttu-id="058bb-817">Campo de información 2: número de subprocesos suspendidos actualmente en la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-817">Info Field 2: Number of threads currently suspended on the queue.</span></span>
- <span data-ttu-id="058bb-818">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-818">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-819">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-819">Info Field 4: Not used.</span></span>

#### <a name="queue-receive"></a><span data-ttu-id="058bb-820">Recepción en la cola</span><span class="sxs-lookup"><span data-stu-id="058bb-820">Queue Receive</span></span> 

##### <a name="tx_queue_receive"></a><span data-ttu-id="058bb-821">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="058bb-821">tx_queue_receive</span></span>

<span data-ttu-id="058bb-822">**Icono** ![Icono de Recepción en la cola](./media/user-guide/tx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-822">**Icon** ![Queue receive icon](./media/user-guide/tx-events/image48.png)</span></span>

<span data-ttu-id="058bb-823">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-823">**Description**</span></span>

<span data-ttu-id="058bb-824">Este evento representa la recepción de un mensaje de una cola mediante tx_queue_receive.</span><span class="sxs-lookup"><span data-stu-id="058bb-824">This event represents receiving a message from a queue via tx_queue_receive.</span></span>

<span data-ttu-id="058bb-825">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-825">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-826">Campo de información 1: puntero que señala a la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-826">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="058bb-827">Campo de información 2: puntero que señala al destino del mensaje.</span><span class="sxs-lookup"><span data-stu-id="058bb-827">Info Field 2: Pointer to destination for message.</span></span> <span data-ttu-id="058bb-828">Campo de información 3: opción de espera proporcionada a la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-828">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="058bb-829">Campo de información 4: número de mensajes actualmente en cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-829">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send"></a><span data-ttu-id="058bb-830">Envío a la cola</span><span class="sxs-lookup"><span data-stu-id="058bb-830">Queue Send</span></span> 

#### <a name="tx_queue_send"></a><span data-ttu-id="058bb-831">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="058bb-831">tx_queue_send</span></span>

<span data-ttu-id="058bb-832">**Icono** ![Icono de Envío a la cola](./media/user-guide/tx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-832">**Icon** ![Queue send icon](./media/user-guide/tx-events/image49.png)</span></span>

<span data-ttu-id="058bb-833">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-833">**Description**</span></span>

<span data-ttu-id="058bb-834">Este evento representa el envío de un mensaje a una cola mediante tx_queue_send.</span><span class="sxs-lookup"><span data-stu-id="058bb-834">This event represents sending a message to a queue via tx_queue_send.</span></span>

<span data-ttu-id="058bb-835">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-835">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-836">Campo de información 1: puntero que señala a la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-836">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="058bb-837">Campo de información 2: puntero que señala al mensaje.</span><span class="sxs-lookup"><span data-stu-id="058bb-837">Info Field 2: Pointer to message.</span></span>
- <span data-ttu-id="058bb-838">Campo de información 3: opción de espera proporcionada a la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-838">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="058bb-839">Campo de información 4: número de mensajes actualmente en cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-839">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send-notify"></a><span data-ttu-id="058bb-840">Notificación de envío de cola</span><span class="sxs-lookup"><span data-stu-id="058bb-840">Queue Send Notify</span></span> 

#### <a name="tx_queue_send_notify"></a><span data-ttu-id="058bb-841">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="058bb-841">tx_queue_send_notify</span></span>

<span data-ttu-id="058bb-842">**Icono** ![Icono de Notificación de envío de cola](./media/user-guide/tx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-842">**Icon** ![Queue send notify icon](./media/user-guide/tx-events/image50.png)</span></span>

<span data-ttu-id="058bb-843">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-843">**Description**</span></span>

<p><span data-ttu-id="058bb-844">Este evento representa el registro de una devolución de llamada mediante tx_queue_send_notify a la que se llama cada vez que se envía un mensaje a una cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-844">This event represents registering a callback via tx_queue_send_notify which is called whenever a message is sent to a queue.</span></span>

<span data-ttu-id="058bb-845">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-845">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-846">Campo de información 1: puntero que señala a la cola.</span><span class="sxs-lookup"><span data-stu-id="058bb-846">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="058bb-847">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-847">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-848">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-848">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-849">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-849">Info Field 4: Not used.</span></span>

### <a name="semaphore-ceiling-put"></a><span data-ttu-id="058bb-850">Colocación del límite superior del semáforo</span><span class="sxs-lookup"><span data-stu-id="058bb-850">Semaphore Ceiling Put</span></span> 

#### <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="058bb-851">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="058bb-851">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="058bb-852">**Icono** ![Icono de Colocación del límite superior del semáforo](./media/user-guide/tx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-852">**Icon** ![Semaphore ceiling put icon](./media/user-guide/tx-events/image51.png)</span></span>

<span data-ttu-id="058bb-853">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-853">**Description**</span></span>

<span data-ttu-id="058bb-854">Este evento representa la colocación en un semáforo mediante tx_semaphore_ceiling_put.</span><span class="sxs-lookup"><span data-stu-id="058bb-854">This event represents putting to a semaphore via tx_semaphore_ceiling_put.</span></span> <span data-ttu-id="058bb-855">Esto difiere de tx_semaphore_put en que se examina el valor máximo del semáforo, de modo que la operación de colocación no puede superar el valor máximo o el límite superior.</span><span class="sxs-lookup"><span data-stu-id="058bb-855">This differs from tx_semaphore_put in that the maximum value of the semaphore is examined such that the put operation is not allowed to exceed the maximum value or ceiling.</span></span>

<span data-ttu-id="058bb-856">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-856">**Information Fields**</span></span>

- <span data-ttu-id="058bb-857">Campo de información 1: puntero que señala al semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-857">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="058bb-858">Campo de información 2: recuento actual de semáforos.</span><span class="sxs-lookup"><span data-stu-id="058bb-858">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="058bb-859">Campo de información 3: número de subprocesos suspendidos en el semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-859">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="058bb-860">Campo de información 4: límite del límite superior proporcionado a la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-860">Info Field 4: Ceiling limit supplied to the call.</span></span>

#### <a name="semaphore-create"></a><span data-ttu-id="058bb-861">Creación de semáforos</span><span class="sxs-lookup"><span data-stu-id="058bb-861">Semaphore Create</span></span> 

##### <a name="tx_semaphore_create"></a><span data-ttu-id="058bb-862">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="058bb-862">tx_semaphore_create</span></span>

<span data-ttu-id="058bb-863">**Icono** ![Icono de Creación de semáforos](./media/user-guide/tx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-863">**Icon** ![Semaphore create icon](./media/user-guide/tx-events/image52.png)</span></span>

<span data-ttu-id="058bb-864">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-864">**Description**</span></span>

<span data-ttu-id="058bb-865">Este evento representa la creación de un semáforo mediante tx_semaphore_create.</span><span class="sxs-lookup"><span data-stu-id="058bb-865">This event represents creating a semaphore via tx_semaphore_create.</span></span>

<span data-ttu-id="058bb-866">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-866">**Information Fields**</span></span>

- <span data-ttu-id="058bb-867">Campo de información 1: puntero que señala a un bloque de control del semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-867">Info Field 1: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="058bb-868">Campo de información 2: recuento inicial de semáforos.</span><span class="sxs-lookup"><span data-stu-id="058bb-868">Info Field 2: Initial semaphore count.</span></span>
- <span data-ttu-id="058bb-869">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-869">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-870">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-870">Info Field 4: Not used.</span></span>

### <a name="semaphore-delete"></a><span data-ttu-id="058bb-871">Eliminación de semáforos</span><span class="sxs-lookup"><span data-stu-id="058bb-871">Semaphore Delete</span></span> 

#### <a name="tx_semaphore_delete"></a><span data-ttu-id="058bb-872">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="058bb-872">tx_semaphore_delete</span></span>

<span data-ttu-id="058bb-873">**Icono** ![Icono de Eliminación de semáforos](./media/user-guide/tx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-873">**Icon** ![Semaphore delete icon](./media/user-guide/tx-events/image53.png)</span></span>

<span data-ttu-id="058bb-874">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-874">**Description**</span></span>

<span data-ttu-id="058bb-875">Este evento representa la eliminación de un semáforo mediante tx_semaphore_delete.</span><span class="sxs-lookup"><span data-stu-id="058bb-875">This event represents deleting a semaphore via tx_semaphore_delete.</span></span>

<span data-ttu-id="058bb-876">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-876">**Information Fields**</span></span>

- <span data-ttu-id="058bb-877">Campo de información 1: puntero que señala al semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-877">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="058bb-878">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-878">nfo Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-879">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-879">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-880">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-880">Info Field 4: Not used.</span></span>

### <a name="semaphore-get"></a><span data-ttu-id="058bb-881">Obtención de semáforos</span><span class="sxs-lookup"><span data-stu-id="058bb-881">Semaphore Get</span></span> 

#### <a name="tx_semaphore_get"></a><span data-ttu-id="058bb-882">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="058bb-882">tx_semaphore_get</span></span>

<span data-ttu-id="058bb-883">**Icono** ![Icono de Obtención de semáforos](./media/user-guide/tx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-883">**Icon** ![Semaphore get icon](./media/user-guide/tx-events/image54.png)</span></span>

<span data-ttu-id="058bb-884">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-884">**Description**</span></span>

<span data-ttu-id="058bb-885">Este evento representa la obtención de un semáforo mediante tx_semaphore_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-885">This event represents obtaining a semaphore via tx_semaphore_get.</span></span>

<span data-ttu-id="058bb-886">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-886">**Information Fields**</span></span>

- <span data-ttu-id="058bb-887">Campo de información 1: puntero que señala al semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-887">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="058bb-888">Campo de información 2: opción de espera proporcionada a la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-888">Info Field 2: Wait option supplied to the call.</span></span>
- <span data-ttu-id="058bb-889">Campo de información 3: recuento actual de semáforos.</span><span class="sxs-lookup"><span data-stu-id="058bb-889">Info Field 3: Current semaphore count.</span></span>
- <span data-ttu-id="058bb-890">Campo de información 4: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-890">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-information-get"></a><span data-ttu-id="058bb-891">Obtención de información de semáforos</span><span class="sxs-lookup"><span data-stu-id="058bb-891">Semaphore Information Get</span></span> 

#### <a name="tx_semaphore_info_get"></a><span data-ttu-id="058bb-892">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-892">tx_semaphore_info_get</span></span>

<span data-ttu-id="058bb-893">**Icono** ![Icono de Obtención de información de semáforos](./media/user-guide/tx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-893">**Icon** ![Semaphore information get icon](./media/user-guide/tx-events/image55.png)</span></span>

<span data-ttu-id="058bb-894">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-894">**Description**</span></span>

<span data-ttu-id="058bb-895">Este evento representa la obtención de información sobre un semáforo mediante tx_semaphore_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-895">This event represents obtaining information about a semaphore via tx_semaphore_info_get.</span></span>

<span data-ttu-id="058bb-896">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-896">**Information Fields**</span></span>

- <span data-ttu-id="058bb-897">Campo de información 1: puntero que señala al semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-897">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="058bb-898">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-898">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-899">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-899">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-900">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-900">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-info-get"></a><span data-ttu-id="058bb-901">Obtención de información de rendimiento de semáforos</span><span class="sxs-lookup"><span data-stu-id="058bb-901">Semaphore Performance Info Get</span></span> 

#### <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="058bb-902">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-902">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="058bb-903">**Icono** ![Icono de Obtención de información de rendimiento de semáforos](./media/user-guide/tx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-903">**Icon** ![Semaphore performance info get icon](./media/user-guide/tx-events/image56.png)</span></span>

<span data-ttu-id="058bb-904">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-904">**Description**</span></span>

<span data-ttu-id="058bb-905">Este evento representa la obtención de información de rendimiento sobre un semáforo mediante tx_semaphore_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-905">This event represents obtaining performance information about a semaphore via tx_semaphore_performance_info_get.</span></span>

<span data-ttu-id="058bb-906">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-906">**Information Fields**</span></span>

- <span data-ttu-id="058bb-907">Campo de información 1: puntero que señala al semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-907">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="058bb-908">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-908">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-909">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-909">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-910">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-910">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-system-info"></a><span data-ttu-id="058bb-911">Obtención de información de rendimiento del sistema de semáforos</span><span class="sxs-lookup"><span data-stu-id="058bb-911">Semaphore Performance System Info</span></span> 

#### <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="058bb-912">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-912">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="058bb-913">**Icono** ![Icono de Obtención de información de rendimiento del sistema de semáforos](./media/user-guide/tx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-913">**Icon** ![Semaphore performance system info icon](./media/user-guide/tx-events/image57.png)</span></span>

<span data-ttu-id="058bb-914">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-914">**Description**</span></span>

<span data-ttu-id="058bb-915">Este evento representa la obtención de información de rendimiento sobre todos los semáforos del sistema mediante tx_semaphore_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-915">This event represents obtaining performance information about all semaphores in the system via tx_semaphore_performance_system_info_get.</span></span>

<span data-ttu-id="058bb-916">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-916">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-917">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-917">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-918">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-918">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-919">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-919">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-920">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-920">Info Field 4: Not used.</span></span>

### <a name="semaphore-prioritize"></a><span data-ttu-id="058bb-921">Priorización de semáforos</span><span class="sxs-lookup"><span data-stu-id="058bb-921">Semaphore Prioritize</span></span> 

#### <a name="tx_semaphore_prioritize"></a><span data-ttu-id="058bb-922">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="058bb-922">tx_semaphore_prioritize</span></span>

<span data-ttu-id="058bb-923">**Icono** ![Icono de Priorización de semáforos](./media/user-guide/tx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-923">**Icon** ![Semaphore prioritize icon](./media/user-guide/tx-events/image58.png)</span></span>

<span data-ttu-id="058bb-924">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-924">**Description**</span></span>

<span data-ttu-id="058bb-925">Este evento representa la prioridad de la lista de suspensiones de semáforos mediante tx_semaphore_prioritize.</span><span class="sxs-lookup"><span data-stu-id="058bb-925">This event represents prioritizing the semaphore's suspension list via tx_semaphore_prioritize.</span></span>

<span data-ttu-id="058bb-926">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-926">**Information Fields**</span></span>

- <span data-ttu-id="058bb-927">Campo de información 1: puntero que señala al semáforo correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-927">Info Field 1: Pointer to corresponding semaphore.</span></span>
- <span data-ttu-id="058bb-928">Campo de información 2: número de subprocesos suspendidos actualmente en el semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-928">Info Field 2: Number of threads currently suspended on the semaphore.</span></span>
- <span data-ttu-id="058bb-929">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-929">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-930">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-930">Info Field 4: Not used.</span></span>

### <a name="semaphore-put"></a><span data-ttu-id="058bb-931">Colocación de semáforos</span><span class="sxs-lookup"><span data-stu-id="058bb-931">Semaphore Put</span></span> 

#### <a name="tx_semaphore_put"></a><span data-ttu-id="058bb-932">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="058bb-932">tx_semaphore_put</span></span>

<span data-ttu-id="058bb-933">**Icono** ![Icono de Colocación de semáforos](./media/user-guide/tx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-933">**Icon** ![Semaphore put icon](./media/user-guide/tx-events/image59.png)</span></span>

<span data-ttu-id="058bb-934">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-934">**Description**</span></span>

<span data-ttu-id="058bb-935">Este evento representa la liberación de una instancia de semáforo mediante tx_semaphore_put.</span><span class="sxs-lookup"><span data-stu-id="058bb-935">This event represents releasing a semaphore instance via tx_semaphore_put.</span></span>

<span data-ttu-id="058bb-936">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-936">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-937">Campo de información 1: puntero que señala al semáforo correspondiente.</span><span class="sxs-lookup"><span data-stu-id="058bb-937">Info Field 1: Pointer to corresponding semaphore.</span></span> <span data-ttu-id="058bb-938">Campo de información 2: recuento actual de semáforos.</span><span class="sxs-lookup"><span data-stu-id="058bb-938">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="058bb-939">Campo de información 3: número de subprocesos suspendidos en el semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-939">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="058bb-940">Campo de información 4: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-940">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-put-notify"></a><span data-ttu-id="058bb-941">Notificación de colocación de semáforos</span><span class="sxs-lookup"><span data-stu-id="058bb-941">Semaphore Put Notify</span></span> 

#### <a name="tx_semaphore_put_notify"></a><span data-ttu-id="058bb-942">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="058bb-942">tx_semaphore_put_notify</span></span>

<span data-ttu-id="058bb-943">**Icono** ![Icono de Notificación de colocación de semáforos](./media/user-guide/tx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-943">**Icon** ![Semaphore put notify icon](./media/user-guide/tx-events/image60.png)</span></span>

<span data-ttu-id="058bb-944">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-944">**Description**</span></span>

<span data-ttu-id="058bb-945">Este evento representa el registro de una devolución de llamada mediante tx_semaphore_put_notify a la que se llama cada vez que se coloca una instancia de semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-945">This event represents registering a callback via tx_semaphore_put_notify that is called whenever a semaphore instance is put.</span></span>

<span data-ttu-id="058bb-946">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-946">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-947">Campo de información 1: puntero que señala al semáforo.</span><span class="sxs-lookup"><span data-stu-id="058bb-947">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="058bb-948">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-948">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-949">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-949">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-950">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-950">Info Field 4: Not used.</span></span>

### <a name="thread-create"></a><span data-ttu-id="058bb-951">Creación de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-951">Thread Create</span></span> 

#### <a name="tx_thread_create"></a><span data-ttu-id="058bb-952">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="058bb-952">tx_thread_create</span></span>

<span data-ttu-id="058bb-953">**Icono** ![Icono de Creación de subprocesos](./media/user-guide/tx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-953">**Icon** ![Thread create icon](./media/user-guide/tx-events/image61.png)</span></span>

<span data-ttu-id="058bb-954">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-954">**Description**</span></span>

<span data-ttu-id="058bb-955">Este evento representa la creación de un subproceso mediante tx_thread_create.</span><span class="sxs-lookup"><span data-stu-id="058bb-955">This event represents creating a thread via tx_thread_create.</span></span>

<span data-ttu-id="058bb-956">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-956">**Information Fields**</span></span>

- <span data-ttu-id="058bb-957">Campo de información 1: puntero que señala al bloque de control de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="058bb-957">Info Field 1: Pointer to thread control block.</span></span>
- <span data-ttu-id="058bb-958">Campo de información 2: prioridad del subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-958">Info Field 2: Priority of thread.</span></span>
- <span data-ttu-id="058bb-959">Campo de información 3: puntero de pila para subprocesos.</span><span class="sxs-lookup"><span data-stu-id="058bb-959">Info Field 3: Stack pointer for thread.</span></span>
- <span data-ttu-id="058bb-960">Campo de información 4: tamaño de la pila en bytes.</span><span class="sxs-lookup"><span data-stu-id="058bb-960">nfo Field 4: Size of stack in bytes.</span></span>

### <a name="thread-delete"></a><span data-ttu-id="058bb-961">Eliminación de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-961">Thread Delete</span></span> 

#### <a name="tx_thread_delete"></a><span data-ttu-id="058bb-962">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="058bb-962">tx_thread_delete</span></span>

<span data-ttu-id="058bb-963">**Icono** ![Icono de Eliminación de subprocesos](./media/user-guide/tx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-963">**Icon** ![Thread delete icon](./media/user-guide/tx-events/image62.png)</span></span>

<span data-ttu-id="058bb-964">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-964">**Description**</span></span>

<span data-ttu-id="058bb-965">Este evento representa la eliminación de un subproceso mediante tx_thread_delete.</span><span class="sxs-lookup"><span data-stu-id="058bb-965">This event represents deleting a thread via tx_thread_delete.</span></span>

<span data-ttu-id="058bb-966">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-966">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-967">Campo de información 1: puntero que señala al subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-967">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="058bb-968">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-968">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-969">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-969">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-970">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-970">Info Field 4: Not used.</span></span>

### <a name="thread-entryexit-notify"></a><span data-ttu-id="058bb-971">Notificación de entrada o salida de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-971">Thread Entry/Exit Notify</span></span> 

#### <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="058bb-972">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="058bb-972">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="058bb-973">**Icono** ![Icono de Notificación de entrada o salida de subprocesos](./media/user-guide/tx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-973">**Icon** ![Thread entry/exit notify icon](./media/user-guide/tx-events/image63.png)</span></span>

<span data-ttu-id="058bb-974">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-974">**Description**</span></span>

<span data-ttu-id="058bb-975">Este evento representa el registro de una devolución de llamada mediante tx_thread_entry_exit_notify a la que se llama cada vez que se entra o sale de un subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-975">This event represents registering a callback via tx_thread_entry_exit_notify that is called whenever a thread is entered or exits.</span></span>

<span data-ttu-id="058bb-976">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-976">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-977">Campo de información 1: puntero que señala al subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-977">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="058bb-978">Campo de información 2: estado del subproceso en el momento del registro.</span><span class="sxs-lookup"><span data-stu-id="058bb-978">Info Field 2: Thread state at time of the registration.</span></span>
- <span data-ttu-id="058bb-979">Campo de información 3: puntero que señala a la pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-979">Info Field 3: Pointer to stack at time of call.</span></span>
- <span data-ttu-id="058bb-980">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-980">Info Field 4: Not used.</span></span>

#### <a name="thread-identify"></a><span data-ttu-id="058bb-981">Identificación de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-981">Thread Identify</span></span> 

##### <a name="tx_thread_identify"></a><span data-ttu-id="058bb-982">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="058bb-982">tx_thread_identify</span></span>

<span data-ttu-id="058bb-983">**Icono** ![Icono de Identificación de subprocesos](./media/user-guide/tx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-983">**Icon** ![Thread identify icon](./media/user-guide/tx-events/image64.png)</span></span>

<span data-ttu-id="058bb-984">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-984">**Description**</span></span>

<span data-ttu-id="058bb-985">Este evento representa la obtención del puntero del subproceso actual mediante tx_thread_identify.</span><span class="sxs-lookup"><span data-stu-id="058bb-985">This event represents getting the current thread pointer via tx_thread_identify.</span></span>

<span data-ttu-id="058bb-986">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-986">**Information Fields**</span></span>

- <span data-ttu-id="058bb-987">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-987">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-988">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-988">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-989">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-989">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-990">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-990">Info Field 4: Not used.</span></span>

### <a name="thread-information-get"></a><span data-ttu-id="058bb-991">Obtención de información de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-991">Thread Information Get</span></span> 

#### <a name="tx_thread_info_get"></a><span data-ttu-id="058bb-992">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-992">tx_thread_info_get</span></span>

<span data-ttu-id="058bb-993">**Icono** ![Icono de Obtención de información de subprocesos](./media/user-guide/tx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-993">**Icon** ![Thread information get icon](./media/user-guide/tx-events/image65.png)</span></span>

<span data-ttu-id="058bb-994">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-994">**Description**</span></span>

<span data-ttu-id="058bb-995">Este evento representa la obtención de información sobre el subproceso especificado mediante tx_thread_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-995">This event represents getting information about the specified thread via tx_thread_info_get.</span></span>

<span data-ttu-id="058bb-996">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-996">**Information Fields**</span></span>

- <span data-ttu-id="058bb-997">Campo de información 1: puntero que señala al subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-997">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="058bb-998">Campo de información 2: estado del subproceso en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-998">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="058bb-999">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-999">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1000">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1000">Info Field 4: Not used.</span></span>

#### <a name="thread-performance-information-get"></a><span data-ttu-id="058bb-1001">Obtención de información de rendimiento del subproceso</span><span class="sxs-lookup"><span data-stu-id="058bb-1001">Thread Performance Information Get</span></span> 

##### <a name="tx_thread_performance_info_get"></a><span data-ttu-id="058bb-1002">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-1002">tx_thread_performance_info_get</span></span>

<span data-ttu-id="058bb-1003">**Icono** ![Icono de Obtención de información de rendimiento del subproceso](./media/user-guide/tx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1003">**Icon** ![Thread performance information get icon](./media/user-guide/tx-events/image66.png)</span></span>

<span data-ttu-id="058bb-1004">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1004">**Description**</span></span>

<span data-ttu-id="058bb-1005">Este evento representa la obtención de información de rendimiento sobre el subproceso especificado mediante tx_thread_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-1005">This event represents getting performance information about the specified thread via tx_thread_performance_info_get.</span></span>

<span data-ttu-id="058bb-1006">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1006">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1007">Campo de información 1: puntero que señala al subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-1007">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="058bb-1008">Campo de información 2: estado del subproceso en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1008">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="058bb-1009">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1009">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1010">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1010">Info Field 4: Not used.</span></span>

### <a name="thread-performance-system-info-get"></a><span data-ttu-id="058bb-1011">Obtención de información de rendimiento del sistema de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1011">Thread Performance System Info Get</span></span> 

#### <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="058bb-1012">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-1012">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="058bb-1013">**Icono** ![Icono de Obtención de información de rendimiento del sistema de subprocesos](./media/user-guide/tx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1013">**Icon** ![Thread performance system info get icon](./media/user-guide/tx-events/image67.png)</span></span>

<span data-ttu-id="058bb-1014">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1014">**Description**</span></span>

<span data-ttu-id="058bb-1015">Este evento representa la obtención de información de rendimiento sobre todos los subprocesos mediante tx_thread_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-1015">This event represents getting performance information about all threads via tx_thread_performance_system_info_get.</span></span>

<span data-ttu-id="058bb-1016">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1016">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-1017">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1017">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-1018">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1018">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-1019">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1019">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1020">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1020">Info Field 4: Not used.</span></span>

### <a name="thread-preemption-change"></a><span data-ttu-id="058bb-1021">Cambio de adelantamiento de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1021">Thread Preemption Change</span></span> 

#### <a name="tx_thread_preemption_change"></a><span data-ttu-id="058bb-1022">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="058bb-1022">tx_thread_preemption_change</span></span>

<span data-ttu-id="058bb-1023">**Icono** ![Icono de Cambio de adelantamiento de subprocesos](./media/user-guide/tx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1023">**Icon** ![Thread preemption change icon](./media/user-guide/tx-events/image68.png)</span></span>

<span data-ttu-id="058bb-1024">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1024">**Description**</span></span>

<span data-ttu-id="058bb-1025">Este evento representa el cambio del umbral de adelantamiento de un subproceso mediante tx_thread_preemption_change.</span><span class="sxs-lookup"><span data-stu-id="058bb-1025">This event represents changing a thread's preemption-threshold via tx_thread_preemption_change.</span></span>

<span data-ttu-id="058bb-1026">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1026">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-1027">Campo de información 1: puntero que señala al subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-1027">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="058bb-1028">Campo de información 2: nuevo umbral de adelantamiento.</span><span class="sxs-lookup"><span data-stu-id="058bb-1028">Info Field 2: New preemption-threshold.</span></span>
- <span data-ttu-id="058bb-1029">Campo de información 3: anterior umbral de adelantamiento.</span><span class="sxs-lookup"><span data-stu-id="058bb-1029">Info Field 3: Previous preemption-threshold.</span></span>
- <span data-ttu-id="058bb-1030">Campo de información 4: estado del subproceso en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1030">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-priority-change"></a><span data-ttu-id="058bb-1031">Cambio de prioridad de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1031">Thread Priority Change</span></span> 

#### <a name="tx_thread_priority_change"></a><span data-ttu-id="058bb-1032">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="058bb-1032">tx_thread_priority_change</span></span>

<span data-ttu-id="058bb-1033">**Icono** ![Icono de Cambio de prioridad de subprocesos](./media/user-guide/tx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1033">**Icon** ![Thread priority change icon](./media/user-guide/tx-events/image69.png)</span></span>

<span data-ttu-id="058bb-1034">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1034">**Description**</span></span>

<span data-ttu-id="058bb-1035">Este evento representa el cambio de la prioridad de un subproceso mediante tx_thread_priority_change.</span><span class="sxs-lookup"><span data-stu-id="058bb-1035">This event represents changing a thread's priority via tx_thread_priority_change.</span></span>

- <span data-ttu-id="058bb-1036">Campos de información</span><span class="sxs-lookup"><span data-stu-id="058bb-1036">Information Fields</span></span> 
- <span data-ttu-id="058bb-1037">Campo de información 1: puntero que señala al subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-1037">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="058bb-1038">Campo de información 2: nueva prioridad.</span><span class="sxs-lookup"><span data-stu-id="058bb-1038">Info Field 2: New priority.</span></span>
- <span data-ttu-id="058bb-1039">Campo de información 3: anterior prioridad.</span><span class="sxs-lookup"><span data-stu-id="058bb-1039">Info Field 3: Previous priority.</span></span>
- <span data-ttu-id="058bb-1040">Campo de información 4: estado del subproceso en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1040">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-relinquish"></a><span data-ttu-id="058bb-1041">Renuncia de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1041">Thread Relinquish</span></span> 

#### <a name="tx_thread_relinquish"></a><span data-ttu-id="058bb-1042">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="058bb-1042">tx_thread_relinquish</span></span>

<span data-ttu-id="058bb-1043">**Icono** ![Icono de Renuncia de subprocesos](./media/user-guide/tx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1043">**Icon** ![Thread relinquish icon](./media/user-guide/tx-events/image70.png)</span></span>

<span data-ttu-id="058bb-1044">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1044">**Description**</span></span>

<span data-ttu-id="058bb-1045">Este evento representa la renuncia del procesador de un subproceso mediante tx_thread_relinquish.</span><span class="sxs-lookup"><span data-stu-id="058bb-1045">This event represents relinquishing the processor from a thread via tx_thread_relinquish.</span></span>

<span data-ttu-id="058bb-1046">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1046">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1047">Campo de información 1: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1047">Info Field 1: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-1048">Campo de información 2: puntero que señala al siguiente subproceso que se va a ejecutar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1048">Info Field 2: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="058bb-1049">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1049">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1050">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1050">Info Field 4: Not used.</span></span>

### <a name="thread-reset"></a><span data-ttu-id="058bb-1051">Restablecimiento de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1051">Thread Reset</span></span> 

#### <a name="tx_thread_reset"></a><span data-ttu-id="058bb-1052">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="058bb-1052">tx_thread_reset</span></span>

<span data-ttu-id="058bb-1053">**Icono** ![Icono de Restablecimiento de subprocesos](./media/user-guide/tx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1053">**Icon** ![Thread reset icon](./media/user-guide/tx-events/image71.png)</span></span>

<span data-ttu-id="058bb-1054">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1054">**Description**</span></span>

<span data-ttu-id="058bb-1055">Este evento representa el restablecimiento de un subproceso completado o terminado mediante tx_thread_reset.</span><span class="sxs-lookup"><span data-stu-id="058bb-1055">This event represents resetting a completed or terminated thread via tx_thread_reset.</span></span>

<span data-ttu-id="058bb-1056">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1056">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1057">Campo de información 1: puntero que señala al subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-1057">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="058bb-1058">Campo de información 2: estado del subproceso en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1058">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="058bb-1059">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1060">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1060">Info Field 4: Not used.</span></span>

#### <a name="thread-resume"></a><span data-ttu-id="058bb-1061">Reanudación de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1061">Thread Resume</span></span> 

##### <a name="tx_thread_resume"></a><span data-ttu-id="058bb-1062">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="058bb-1062">tx_thread_resume</span></span>

<span data-ttu-id="058bb-1063">**Icono** ![Icono de Reanudación de subprocesos](./media/user-guide/tx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1063">**Icon** ![Thread resume icon](./media/user-guide/tx-events/image72.png)</span></span>

<span data-ttu-id="058bb-1064">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1064">**Description**</span></span>

<span data-ttu-id="058bb-1065">Este evento representa la reanudación de un subproceso suspendido mediante tx_thread_resume.</span><span class="sxs-lookup"><span data-stu-id="058bb-1065">This event represents resuming a suspended thread via tx_thread_resume.</span></span>

<span data-ttu-id="058bb-1066">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1066">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1067">Campo de información 1: puntero que señala al subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-1067">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="058bb-1068">Campo de información 2: estado del subproceso en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1068">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="058bb-1069">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1069">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-1070">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1070">Info Field 4: Not used.</span></span>

### <a name="thread-sleep"></a><span data-ttu-id="058bb-1071">Pausa de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1071">Thread Sleep</span></span> 

#### <a name="tx_thread_sleep"></a><span data-ttu-id="058bb-1072">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="058bb-1072">tx_thread_sleep</span></span>

<span data-ttu-id="058bb-1073">**Icono** ![Icono de Pausa de subprocesos](./media/user-guide/tx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1073">**Icon** ![Thread sleep icon](./media/user-guide/tx-events/image73.png)</span></span>

<span data-ttu-id="058bb-1074">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1074">**Description**</span></span>

<span data-ttu-id="058bb-1075">Este evento representa la pausa del subproceso actual durante un número especificado de tics del temporizador mediante tx_thread_sleep.</span><span class="sxs-lookup"><span data-stu-id="058bb-1075">This event represents suspending the current thread for a specified number of timer ticks via tx_thread_sleep.</span></span>

<span data-ttu-id="058bb-1076">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1076">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1077">Campo de información 1: número de tics por los que suspender.</span><span class="sxs-lookup"><span data-stu-id="058bb-1077">Info Field 1: Number of ticks to suspend for.</span></span>
- <span data-ttu-id="058bb-1078">Campo de información 2: estado del subproceso en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1078">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="058bb-1079">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1079">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-1080">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1080">Info Field 4: Not used.</span></span>

### <a name="thread-stack-error-notify"></a><span data-ttu-id="058bb-1081">Notificación de error de pila de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1081">Thread Stack Error Notify</span></span> 

#### <a name="tx_thread_stack_error_notify_event"></a><span data-ttu-id="058bb-1082">tx_thread_stack_error_notify_event</span><span class="sxs-lookup"><span data-stu-id="058bb-1082">tx_thread_stack_error_notify_event</span></span>

<span data-ttu-id="058bb-1083">**Icono** ![Icono de Notificación de error de pila de subprocesos](./media/user-guide/tx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1083">**Icon** ![Thread stack error notify icon](./media/user-guide/tx-events/image74.png)</span></span>

<span data-ttu-id="058bb-1084">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1084">**Description**</span></span>

<span data-ttu-id="058bb-1085">Este evento representa el registro de una rutina de notificación de errores de pila de subprocesos mediante tx_thread_stack_error_notify_event.</span><span class="sxs-lookup"><span data-stu-id="058bb-1085">This event represents registering a thread stack error notification routine via tx_thread_stack_error_notify_event.</span></span>

<span data-ttu-id="058bb-1086">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1086">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-1087">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1087">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-1088">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1088">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-1089">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1089">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1090">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1090">Info Field 4: Not used.</span></span>

### <a name="thread-suspend"></a><span data-ttu-id="058bb-1091">Suspensión de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1091">Thread Suspend</span></span> 

#### <a name="tx_thread_suspend"></a><span data-ttu-id="058bb-1092">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="058bb-1092">tx_thread_suspend</span></span>

<span data-ttu-id="058bb-1093">**Icono** ![Icono de Suspensión de subprocesos](./media/user-guide/tx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1093">**Icon** ![Thread suspend icon](./media/user-guide/tx-events/image75.png)</span></span>

<span data-ttu-id="058bb-1094">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1094">**Description**</span></span>

<span data-ttu-id="058bb-1095">Este evento representa la suspensión de un subproceso mediante tx_thread_suspend.</span><span class="sxs-lookup"><span data-stu-id="058bb-1095">This event represents suspending a thread via tx_thread_suspend.</span></span>

<span data-ttu-id="058bb-1096">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1096">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-1097">Campo de información 1: puntero que señala al subproceso que se va a suspender.</span><span class="sxs-lookup"><span data-stu-id="058bb-1097">Info Field 1: Pointer to thread to suspend.</span></span>
- <span data-ttu-id="058bb-1098">Campo de información 2: estado del subproceso en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1098">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="058bb-1099">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1099">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-1100">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1100">Info Field 4: Not used.</span></span>

### <a name="thread-terminate"></a><span data-ttu-id="058bb-1101">Finalización de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1101">Thread Terminate</span></span> 

#### <a name="tx_thread_terminate"></a><span data-ttu-id="058bb-1102">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="058bb-1102">tx_thread_terminate</span></span>

<span data-ttu-id="058bb-1103">**Icono** ![Icono de Finalización de subprocesos](./media/user-guide/tx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1103">**Icon** ![Thread terminate icon](./media/user-guide/tx-events/image76.png)</span></span>

<span data-ttu-id="058bb-1104">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1104">**Description**</span></span>

<span data-ttu-id="058bb-1105">Este evento representa la finalización de un subproceso mediante tx_thread_terminate.</span><span class="sxs-lookup"><span data-stu-id="058bb-1105">This event represents terminating a thread via tx_thread_terminate.</span></span>

<span data-ttu-id="058bb-1106">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1106">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-1107">Campo de información 1: puntero que señala al subproceso que se va a finalizar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1107">Info Field 1: Pointer to thread to terminate.</span></span>
- <span data-ttu-id="058bb-1108">Campo de información 2: estado del subproceso en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1108">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="058bb-1109">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1109">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-1110">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1110">Info Field 4: Not used.</span></span>

### <a name="thread-time-slice-change"></a><span data-ttu-id="058bb-1111">Cambio de intervalo de tiempo</span><span class="sxs-lookup"><span data-stu-id="058bb-1111">Thread Time-Slice Change</span></span> 

#### <a name="tx_thread_time_slice_change"></a><span data-ttu-id="058bb-1112">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="058bb-1112">tx_thread_time_slice_change</span></span>

<span data-ttu-id="058bb-1113">**Icono** ![Icono de Cambio de intervalo de tiempo](./media/user-guide/tx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1113">**Icon** ![Thread time-slice change icon](./media/user-guide/tx-events/image77.png)</span></span>

<span data-ttu-id="058bb-1114">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1114">**Description**</span></span>

<span data-ttu-id="058bb-1115">Este evento representa el cambio del intervalo de tiempo de un subproceso mediante tx_thread_time_slice_change.</span><span class="sxs-lookup"><span data-stu-id="058bb-1115">This event represents changing a thread's time-slice via tx_thread_time_slice_change.</span></span>

<span data-ttu-id="058bb-1116">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1116">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1117">Campo de información 1: puntero que señala al subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-1117">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="058bb-1118">Campo de información 2: nuevo intervalo de tiempo.</span><span class="sxs-lookup"><span data-stu-id="058bb-1118">Info Field 2: New time-slice.</span></span>
- <span data-ttu-id="058bb-1119">Campo de información 3: anterior intervalo de tiempo.</span><span class="sxs-lookup"><span data-stu-id="058bb-1119">Info Field 3: Previous time-slice.</span></span>
- <span data-ttu-id="058bb-1120">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1120">Info Field 4: Not used.</span></span>

### <a name="thread-wait-abort"></a><span data-ttu-id="058bb-1121">Anulación de espera de subprocesos</span><span class="sxs-lookup"><span data-stu-id="058bb-1121">Thread Wait Abort</span></span> 

#### <a name="tx_thread_wait_abort"></a><span data-ttu-id="058bb-1122">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="058bb-1122">tx_thread_wait_abort</span></span>

<span data-ttu-id="058bb-1123">**Icono** ![Icono de Anulación de espera de subprocesos](./media/user-guide/tx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1123">**Icon** ![Thread wait abort icon](./media/user-guide/tx-events/image78.png)</span></span>

<span data-ttu-id="058bb-1124">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1124">**Description**</span></span>

<span data-ttu-id="058bb-1125">Este evento representa la anulación de la suspensión de un subproceso mediante tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="058bb-1125">This event represents aborting a thread's suspension via tx_thread_wait_abort.</span></span>

<span data-ttu-id="058bb-1126">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1126">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1127">Campo de información 1: puntero que señala al subproceso.</span><span class="sxs-lookup"><span data-stu-id="058bb-1127">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="058bb-1128">Campo de información 2: estado del subproceso en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1128">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="058bb-1129">Campo de información 3: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1129">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-1130">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1130">Info Field 4: Not used.</span></span>

### <a name="time-get"></a><span data-ttu-id="058bb-1131">Obtención de hora</span><span class="sxs-lookup"><span data-stu-id="058bb-1131">Time Get</span></span> 

#### <a name="tx_time_get"></a><span data-ttu-id="058bb-1132">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="058bb-1132">tx_time_get</span></span>

<span data-ttu-id="058bb-1133">**Icono** ![Icono de Obtención de hora](./media/user-guide/tx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1133">**Icon** ![Time get icon](./media/user-guide/tx-events/image79.png)</span></span>

<span data-ttu-id="058bb-1134">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1134">**Description**</span></span>

<span data-ttu-id="058bb-1135">Este evento representa la obtención del número actual de tics del temporizador mediante tx_time_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-1135">This event represents getting the current number of timer ticks via tx_time_get.</span></span>

<span data-ttu-id="058bb-1136">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1136">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1137">Campo de información 1: número actual de tics del temporizador.</span><span class="sxs-lookup"><span data-stu-id="058bb-1137">Info Field 1: Current number of timer ticks.</span></span>
- <span data-ttu-id="058bb-1138">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1138">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-1139">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1139">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1140">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1140">Info Field 4: Not used.</span></span>

### <a name="time-set"></a><span data-ttu-id="058bb-1141">Establecimiento de hora</span><span class="sxs-lookup"><span data-stu-id="058bb-1141">Time Set</span></span> 

#### <a name="tx_time_set"></a><span data-ttu-id="058bb-1142">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="058bb-1142">tx_time_set</span></span>

<span data-ttu-id="058bb-1143">**Icono** ![Icono de establecimiento de hora](./media/user-guide/tx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1143">**Icon** ![Time set icon](./media/user-guide/tx-events/image80.png)</span></span>

<span data-ttu-id="058bb-1144">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1144">**Description**</span></span>

<span data-ttu-id="058bb-1145">Este evento representa el establecimiento del número actual de tics del temporizador mediante tx_time_set.</span><span class="sxs-lookup"><span data-stu-id="058bb-1145">This event represents setting the current number of timer ticks via tx_time_set.</span></span>

<span data-ttu-id="058bb-1146">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1146">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1147">Campo de información 1: número nuevo de tics del temporizador.</span><span class="sxs-lookup"><span data-stu-id="058bb-1147">Info Field 1: New number of timer ticks.</span></span>
- <span data-ttu-id="058bb-1148">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1148">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-1149">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1149">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1150">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1150">Info Field 4: Not used.</span></span>

### <a name="timer-activate"></a><span data-ttu-id="058bb-1151">Activación del temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1151">Timer Activate</span></span> 

#### <a name="tx_timer_activate"></a><span data-ttu-id="058bb-1152">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="058bb-1152">tx_timer_activate</span></span>

<span data-ttu-id="058bb-1153">**Icono** ![Icono de Activación del temporizador](./media/user-guide/tx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1153">**Icon** ![Timer activate icon](./media/user-guide/tx-events/image81.png)</span></span>

<span data-ttu-id="058bb-1154">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1154">**Description**</span></span>

<span data-ttu-id="058bb-1155">Este evento representa la activación del temporizador especificado mediante tx_timer_activate.</span><span class="sxs-lookup"><span data-stu-id="058bb-1155">This event represents activating the specified timer via tx_timer_activate.</span></span>

<span data-ttu-id="058bb-1156">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1156">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1157">Campo de información 1: puntero que señala al temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1157">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="058bb-1158">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1158">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-1159">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1159">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1160">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1160">Info Field 4: Not used.</span></span>

### <a name="timer-change"></a><span data-ttu-id="058bb-1161">Cambio del temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1161">Timer Change</span></span> 

#### <a name="tx_timer_change"></a><span data-ttu-id="058bb-1162">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="058bb-1162">tx_timer_change</span></span>

<span data-ttu-id="058bb-1163">**Icono** ![Icono de Cambio del temporizador](./media/user-guide/tx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1163">**Icon** ![Timer change icon](./media/user-guide/tx-events/image82.png)</span></span>

<span data-ttu-id="058bb-1164">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1164">**Description**</span></span>

<span data-ttu-id="058bb-1165">Este evento representa el cambio del temporizador especificado mediante tx_timer_change.</span><span class="sxs-lookup"><span data-stu-id="058bb-1165">This event represents changing the specified timer via tx_timer_change.</span></span>

<span data-ttu-id="058bb-1166">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1166">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1167">Campo de información 1: puntero que señala al temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1167">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="058bb-1168">Campo de información 2: tics de expiración iniciales.</span><span class="sxs-lookup"><span data-stu-id="058bb-1168">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="058bb-1169">Campo de información 3: reprogramación de tics de expiración.</span><span class="sxs-lookup"><span data-stu-id="058bb-1169">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="058bb-1170">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1170">Info Field 4: Not used.</span></span>

### <a name="timer-create"></a><span data-ttu-id="058bb-1171">Creación del temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1171">Timer Create</span></span> 

#### <a name="tx_timer_create"></a><span data-ttu-id="058bb-1172">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="058bb-1172">tx_timer_create</span></span>

<span data-ttu-id="058bb-1173">**Icono** ![Icono de Creación del temporizador](./media/user-guide/tx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1173">**Icon** ![Timer create icon](./media/user-guide/tx-events/image83.png)</span></span>

<span data-ttu-id="058bb-1174">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1174">**Description**</span></span>

<span data-ttu-id="058bb-1175">Este evento representa la creación de un temporizador mediante tx_timer_create.</span><span class="sxs-lookup"><span data-stu-id="058bb-1175">This event represents creating a timer via tx_timer_create.</span></span>

<span data-ttu-id="058bb-1176">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1176">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1177">Campo de información 1: puntero que señala al bloque de control del temporizador.</span><span class="sxs-lookup"><span data-stu-id="058bb-1177">Info Field 1: Pointer to timer control block.</span></span>
- <span data-ttu-id="058bb-1178">Campo de información 2: tics de expiración iniciales.</span><span class="sxs-lookup"><span data-stu-id="058bb-1178">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="058bb-1179">Campo de información 3: reprogramación de tics de expiración.</span><span class="sxs-lookup"><span data-stu-id="058bb-1179">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="058bb-1180">Campo de información 4: valor de habilitación automática, TX_AUTO_ACTIVATE (1) o TX_NO_ACTIVATE (0).</span><span class="sxs-lookup"><span data-stu-id="058bb-1180">Info Field 4: Automatic enable value—either TX_AUTO_ACTIVATE (1) or TX_NO_ACTIVATE (0).</span></span>

### <a name="timer-deactivate"></a><span data-ttu-id="058bb-1181">Desactivación del temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1181">Timer Deactivate</span></span> 

#### <a name="tx_timer_deactivate"></a><span data-ttu-id="058bb-1182">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="058bb-1182">tx_timer_deactivate</span></span>

<span data-ttu-id="058bb-1183">**Icono** ![Icono de Desactivación del temporizador](./media/user-guide/tx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1183">**Icon** ![Timer deactivate icon](./media/user-guide/tx-events/image84.png)</span></span>

<span data-ttu-id="058bb-1184">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1184">**Description**</span></span>

<span data-ttu-id="058bb-1185">Este evento representa la desactivación de un temporizador mediante tx_timer_deactivate.</span><span class="sxs-lookup"><span data-stu-id="058bb-1185">This event represents deactivating a timer via tx_timer_deactivate.</span></span>

<span data-ttu-id="058bb-1186">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1186">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1187">Campo de información 1: puntero que señala al temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1187">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="058bb-1188">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1188">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-1189">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1189">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1190">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1190">Info Field 4: Not used.</span></span>

### <a name="timer-delete"></a><span data-ttu-id="058bb-1191">Eliminación del temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1191">Timer Delete</span></span> 

#### <a name="tx_timer_delete"></a><span data-ttu-id="058bb-1192">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="058bb-1192">tx_timer_delete</span></span>

<span data-ttu-id="058bb-1193">**Icono** ![Icono de Eliminación del temporizador](./media/user-guide/tx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1193">**Icon** ![Timer delete icon](./media/user-guide/tx-events/image85.png)</span></span>

<span data-ttu-id="058bb-1194">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1194">**Description**</span></span>

<span data-ttu-id="058bb-1195">Este evento representa la eliminación de un temporizador mediante tx_timer_delete.</span><span class="sxs-lookup"><span data-stu-id="058bb-1195">This event represents deleting a timer via tx_timer_delete.</span></span>

<span data-ttu-id="058bb-1196">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1196">**Information Fields**</span></span> 

- <span data-ttu-id="058bb-1197">Campo de información 1: puntero que señala al temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1197">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="058bb-1198">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1198">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-1199">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1199">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1200">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1200">Info Field 4: Not used.</span></span>

### <a name="timer-information-get"></a><span data-ttu-id="058bb-1201">Obtención de información del temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1201">Timer Information Get</span></span> 

#### <a name="tx_timer_info_get"></a><span data-ttu-id="058bb-1202">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-1202">tx_timer_info_get</span></span>

<span data-ttu-id="058bb-1203">**Icono** ![Icono Obtención de información del temporizador](./media/user-guide/tx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1203">**Icon** ![Timer get information icon](./media/user-guide/tx-events/image86.png)</span></span>

<span data-ttu-id="058bb-1204">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1204">**Description**</span></span>

<span data-ttu-id="058bb-1205">Este evento representa la obtención de información del temporizador mediante tx_timer_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-1205">This event represents getting timer information via tx_timer_info_get.</span></span>

<span data-ttu-id="058bb-1206">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1206">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1207">Campo de información 1: puntero que señala al temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1207">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="058bb-1208">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1208">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-1209">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1209">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1210">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1210">Info Field 4: Not used.</span></span>

### <a name="timer-performance-information-get"></a><span data-ttu-id="058bb-1211">Obtención de información de rendimiento del temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1211">Timer Performance Information Get</span></span> 

#### <a name="tx_timer_performance_info_get"></a><span data-ttu-id="058bb-1212">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-1212">tx_timer_performance_info_get</span></span>

<span data-ttu-id="058bb-1213">**Icono** ![Icono de Obtención de información de rendimiento del temporizador](./media/user-guide/tx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1213">**Icon** ![Timer performance information get icon](./media/user-guide/tx-events/image87.png)</span></span>

<span data-ttu-id="058bb-1214">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1214">**Description**</span></span> 

<span data-ttu-id="058bb-1215">Este evento representa la obtención de información de rendimiento del temporizador mediante tx_timer_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-1215">This event represents getting timer performance information via tx_timer_performance_info_get.</span></span>

<span data-ttu-id="058bb-1216">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1216">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1217">Campo de información 1: puntero que señala al temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1217">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="058bb-1218">Campo de información 2: puntero de pila en el momento de la llamada.</span><span class="sxs-lookup"><span data-stu-id="058bb-1218">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="058bb-1219">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1219">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1220">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1220">Info Field 4: Not used.</span></span>

### <a name="timer-system-performance-info-get"></a><span data-ttu-id="058bb-1221">Obtención de información de rendimiento del sistema del temporizador</span><span class="sxs-lookup"><span data-stu-id="058bb-1221">Timer System Performance Info Get</span></span> 

#### <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="058bb-1222">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="058bb-1222">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="058bb-1223">**Icono** ![Icono de Obtención de información de rendimiento del sistema del temporizador](./media/user-guide/tx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="058bb-1223">**Icon** ![Timer system performance info get icon](./media/user-guide/tx-events/image88.png)</span></span>


<span data-ttu-id="058bb-1224">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="058bb-1224">**Description**</span></span> 

<span data-ttu-id="058bb-1225">Este evento representa la obtención de toda la información de rendimiento de los temporizadores mediante tx_timer_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="058bb-1225">This event represents getting all timer performance information via tx_timer_performance_system_info_get.</span></span>

<span data-ttu-id="058bb-1226">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="058bb-1226">**Information Fields**</span></span>

- <span data-ttu-id="058bb-1227">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1227">Info Field 1: Not used.</span></span>
- <span data-ttu-id="058bb-1228">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1228">Info Field 2: Not used.</span></span>
- <span data-ttu-id="058bb-1229">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1229">Info Field 3: Not used.</span></span>
- <span data-ttu-id="058bb-1230">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="058bb-1230">Info Field 4: Not used.</span></span>