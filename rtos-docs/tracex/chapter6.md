---
title: 'Capítulo 6: Eventos de seguimiento de Azure RTOS ThreadX'
description: En este capítulo se describen los eventos de Azure RTOS ThreadX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 9fefc43002d4e0d6df817ad56d79b3e41a3d649504be50f5a39f67c1896b2e9a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116800334"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a>Capítulo 6: Eventos de seguimiento de Azure RTOS ThreadX

En este capítulo se describen los eventos de Azure RTOS ThreadX. 

## <a name="list-of-events-and-icons"></a>Lista de eventos e iconos

En la siguiente lista se enumeran eventos de ThreadX mostrados por TraceX.

| **Icono**                         | **Significado** |
| -------------------------------- | ------------------------------------- |
| ![Icono de Reanudación de subprocesos internos](./media/user-guide/tx-events/image1.png)    | Reanudación de subprocesos internos  |
| ![Icono de Suspensión de subprocesos internos](./media/user-guide/tx-events/image2.png)    | Suspensión de subprocesos internos |
| ![Icono de Entrada de rutina de servicio de interrupción](./media/user-guide/tx-events/image3.png)    | Entrada de rutina de servicio de interrupción (ISR) |
| ![Icono de Salida de rutina de servicio de interrupción](./media/user-guide/tx-events/image4.png)    | Salida de rutina de servicio de interrupción (ISR)  |
| ![Icono de Intervalo de tiempo interno](./media/user-guide/tx-events/image5.png)    | Intervalo de tiempo interno |
| ![Icono de En ejecución](./media/user-guide/tx-events/image6.png)    | En ejecución |
| ![Icono de Asignación de grupo de bloques](./media/user-guide/tx-events/image7.png)    | **Asignación de grupo de bloques** (*tx_block_allocate*)  |
| ![Icono de Creación de grupo de bloques](./media/user-guide/tx-events/image8.png)    | **Creación de grupo de bloques** (*tx_block_pool_create*) |
| ![Icono de Eliminación de grupo de bloques](./media/user-guide/tx-events/image9.png)    | **Eliminación de grupo de bloques** (*tx_block_pool_delete*) |
| ![Icono de Obtención de información de grupo de bloques](./media/user-guide/tx-events/image10.png)    | **Obtención de información de grupo de bloques** (*tx_block_pool_info_get*) |
| ![Icono de Obtención de información de rendimiento de grupo de bloques](./media/user-guide/tx-events/image11.png)    | **Obtención de información de rendimiento de bloqueos** (*tx_block_pool_performance_info_get*) |
| ![Icono de Obtención de información de rendimiento del sistema de grupo de bloques](./media/user-guide/tx-events/image12.png)    | **Obtención de información de rendimiento del sistema de grupo de bloques** (*tx_block_pool_performance_system_info_get*) |
| ![Icono de Priorización de grupo de bloques](./media/user-guide/tx-events/image13.png)    | **Priorización de grupo de bloques** (*tx_block_pool_prioritize*) |
| ![Icono de Liberación del bloque al grupo](./media/user-guide/tx-events/image14.png)    | **Liberación del bloque al grupo** (*tx_block_release*) |
| ![Icono de Asignación de memoria del grupo de bytes](./media/user-guide/tx-events/image15.png)    | **Asignación de memoria del grupo de bytes** (*tx_byte_allocate*) |
| ![Icono de Creación de grupos de bytes](./media/user-guide/tx-events/image16.png)    | **Creación de grupos de bytes** (*tx_byte_pool_create*) |
| ![Icono de Eliminación de grupos de bloques](./media/user-guide/tx-events/image17.png)    | **Eliminación de grupos de bloques** (*tx_byte_pool_delete*) |
| ![Icono de Obtención de información de grupos de bytes](./media/user-guide/tx-events/image18.png)    | **Obtención de información de grupos de bytes** (*tx_byte_pool_info_get*) |
| ![Icono de Obtención de información de rendimiento de grupos de bytes](./media/user-guide/tx-events/image19.png)    | **Obtención de información de rendimiento de grupos de bytes** (*tx_byte_pool_performance_info_get*) |
| ![Icono de Obtención de información de rendimiento del sistema de grupos de bytes](./media/user-guide/tx-events/image20.png)    | **Obtención de información de rendimiento del sistema de grupos de bytes** (*tx_byte_pool_performance_info_get*) |
| ![*Icono de Priorización de grupos de bytes](./media/user-guide/tx-events/image21.png)    | **Priorización de grupos de bytes** (*tx_byte_pool_prioritize*) |
| ![Icono Liberación de memoria de bytes en el grupo](./media/user-guide/tx-events/image22.png)    | **Liberación de memoria de bytes en el grupo** (*tx_byte_release*) |
| ![Icono de Creación de marcas de evento](./media/user-guide/tx-events/image23.png)    | **Creación de marcas de evento** (*tx_event_flags_create*) |
| ![Icono de Eliminación de marcas de evento](./media/user-guide/tx-events/image24.png)    | **Eliminación de marcas de evento** (*tx_event_flags_delete*) |
| ![Icono de Obtención de marcas de evento](./media/user-guide/tx-events/image25.png)    | **Obtención de marcas de evento** (*tx_event_flags_get*) |
| ![Icono de Obtención de información de marcas de evento](./media/user-guide/tx-events/image26.png)    | **Obtención de información de marcas de evento** (*tx_event_flags_info_get*) |
| ![Icono de Obtención de información de rendimiento de marcas de evento](./media/user-guide/tx-events/image27.png)    | **Obtención de información de rendimiento de marcas de evento** (*tx_event_flags_performance_info_get*) |
| ![Icono de Obtención de información de rendimiento del sistema de marcas de evento](./media/user-guide/tx-events/image28.png)    | **Obtención de información de rendimiento del sistema de marcas de evento** (*tx_event_flags_performance_system_info_get*) |
| ![Icono de Establecimiento de marcas de evento](./media/user-guide/tx-events/image29.png)    | **Establecimiento de marcas de evento** (*tx_event_flags_set*) |
| ![Icono de Notificación de establecimiento de marcas de evento](./media/user-guide/tx-events/image30.png)    | **Notificación de establecimiento de marcas de evento** (*tx_event_flags_set_notify*) |
| ![Icono de Habilitar/deshabilitar interrupción](./media/user-guide/tx-events/image31.png)    | **Habilitar/deshabilitar interrupción** (*tx_interrupt_control*) |
| ![Icono de Creación de exclusión mutua](./media/user-guide/tx-events/image32.png)    | **Creación de exclusión mutua** (*tx_mutex_create*) |
| ![Icono de Eliminación de exclusión mutua](./media/user-guide/tx-events/image33.png)    | **Eliminación de exclusión mutua** (*tx_mutex_delete*) |
| ![Icono de Obtención de exclusión mutua](./media/user-guide/tx-events/image34.png)    | **Obtención de exclusión mutua** (*tx_mutex_get*) |
| ![Icono de Obtención de información de exclusión mutua](./media/user-guide/tx-events/image35.png)    | **Icono de Obtención de información de exclusión mutua** (*tx_mutex_info_get*) |
| ![Icono de Obtención de información de rendimiento de exclusión mutua](./media/user-guide/tx-events/image36.png)    | **Obtención de información de rendimiento de exclusión mutua** (*tx_mutex_performance_info_get*) |
| ![Icono de Obtención de información de rendimiento del sistema de exclusión mutua](./media/user-guide/tx-events/image37.png)    | **Obtención de información de rendimiento del sistema de exclusión mutua** (*tx_mutex_performance_system_info_get*) |
| ![Icono de Priorización de exclusión mutua](./media/user-guide/tx-events/image38.png)    | **Priorización de exclusión mutua** (*tx_mutex_prioritize*) |
| ![Icono de Colocación de exclusión mutua](./media/user-guide/tx-events/image39.png)    | **Colocación de exclusión mutua** (*tx_mutex_put*) |
| ![Icono de Creación de colas](./media/user-guide/tx-events/image40.png)    | **Creación de colas** (*tx_queue_create*) |
| ![Icono de Eliminación de colas](./media/user-guide/tx-events/image41.png)    | **Eliminación de colas** (*tx_queue_delete*) |
| ![Icono de Vaciado de colas](./media/user-guide/tx-events/image42.png)    | **Vaciado de colas** (*tx_queue_flush*) |
| ![Icono de Envío al inicio de cola](./media/user-guide/tx-events/image43.png)    | **Envío al inicio de cola** (*tx_queue_front_send*) |
| ![Icono de Obtención de información de cola](./media/user-guide/tx-events/image44.png)    | **Obtención de información de cola** (*tx_queue_info_get*) |
| ![Icono de Obtención de información de rendimiento de cola](./media/user-guide/tx-events/image45.png)    | **Obtención de información de rendimiento de cola** (*tx_queue_performance_info_get*) |
| ![Icono de Obtención de información de rendimiento del sistema de cola](./media/user-guide/tx-events/image46.png)    | **Obtención de información de rendimiento del sistema de cola** (*tx_queue_performance_system_info_get*) |
| ![Icono de Priorización de colas](./media/user-guide/tx-events/image47.png)    | **Priorización de colas** (*tx_queue_prioritize*) |
| ![Icono de Recepción de mensaje de cola](./media/user-guide/tx-events/image48.png)    | **Recepción de mensaje de cola** (*tx_queue_receive*) |
| ![Icono de Envío de mensaje de cola](./media/user-guide/tx-events/image49.png)    | **Envío de mensaje de cola** (*tx_queue_send*) |
| ![Icono Notificación de envío de cola](./media/user-guide/tx-events/image50.png)    | **Notificación de envío de cola** (*tx_queue_send_notify*) |
| ![Icono de Colocación del límite superior del semáforo](./media/user-guide/tx-events/image51.png)    | **Colocación del límite superior del semáforo** (*tx_semaphore_ceiling_put*) |
| ![Icono de Creación de semáforos](./media/user-guide/tx-events/image52.png)    | **Creación de semáforos** (*tx_semaphore_create*) |
| ![Icono de Eliminación de semáforos](./media/user-guide/tx-events/image53.png)    | **Eliminación de semáforos** (*tx_semaphore_delete*) |
| ![Icono de Obtención de semáforos](./media/user-guide/tx-events/image54.png)    | **Obtención de semáforos** (*tx_semaphore_get*) |
| ![Icono de Obtención de información de semáforos](./media/user-guide/tx-events/image55.png)    | **Obtención de información de semáforos** (*tx_semaphore_info_get*) |
| ![Icono de Obtención de información de rendimiento de semáforos](./media/user-guide/tx-events/image56.png)    | **Obtención de información de rendimiento de semáforos** (*tx_semaphroe_performance_info_get*) |
| ![Icono de Obtención de información de rendimiento del sistema de semáforos](./media/user-guide/tx-events/image57.png)    | **Obtención de información de rendimiento del sistema de semáforos** (*tx_semaphore_performance_system_info_get*) |
| ![Icono de Priorización de semáforos](./media/user-guide/tx-events/image58.png)    | **Priorización de semáforos** (*tx_semaphore_prioritize*) |
| ![Icono de Colocación de semáforos](./media/user-guide/tx-events/image59.png)    | **Colocación de semáforos** (*tx_semaphore_put*) |
| ![Icono de Notificación de colocación de semáforos](./media/user-guide/tx-events/image60.png)    | **Notificación de colocación de semáforos** (*tx_semaphore_put_notify*) |
| ![Icono de Creación de subprocesos](./media/user-guide/tx-events/image61.png)    | **Creación de subprocesos** (*tx_thread_create*) |
| ![Icono de Eliminación de subprocesos](./media/user-guide/tx-events/image62.png)    | **Eliminación de subprocesos** (*tx_thread_delete*) |
| ![Icono de Notificación de salida/entrada de subprocesos](./media/user-guide/tx-events/image63.png)    | **Notificación de salida/entrada de subprocesos** (*tx_thread_entry_exit_notify*) |
| ![Icono de Identificación de subprocesos](./media/user-guide/tx-events/image64.png)    | **Identificación de subprocesos** (*tx_thread_identify*) |
| ![Icono de Obtención de información de subprocesos](./media/user-guide/tx-events/image65.png)    | **Obtención de información de subprocesos** (*tx_thread_info_get*) |
| ![Icono de Obtención de información de rendimiento del subproceso](./media/user-guide/tx-events/image66.png)    | **Obtención de información de rendimiento del subproceso** (*tx_thread_performance_info_get*) |
| ![Icono de Obtención de información de sistema de rendimiento del subproceso](./media/user-guide/tx-events/image67.png)    | **Obtención de información de sistema de rendimiento del subproceso** (*tx_thread_performance_system_info_get*) |
| ![Icono de Cambio de adelantamiento de subprocesos](./media/user-guide/tx-events/image68.png)    | **Cambio de adelantamiento de subprocesos** (*tx_thread_preemption_change*) |
| ![Icono de Cambio de prioridad de subprocesos](./media/user-guide/tx-events/image69.png)    | **Cambio de prioridad de subprocesos** (*tx_thread_priority_change*) |
| ![Icono de Renuncia de subprocesos](./media/user-guide/tx-events/image70.png)    | **Renuncia de subprocesos** (*tx_thread_relinquish*) |
| ![Icono de Restablecimiento de subprocesos](./media/user-guide/tx-events/image71.png)    | **Restablecimiento de subprocesos** (*tx_thread_reset*) |
| ![*Icono de Reanudación de subprocesos](./media/user-guide/tx-events/image72.png)    | **Reanudación de subprocesos** (**tx_thread_resume*) |
| ![Icono de Pausa de subprocesos](./media/user-guide/tx-events/image73.png)    | **Pausa de subprocesos** (*tx_thread_sleep*)* |
| ![Icono de Notificación de error de pila de subprocesos](./media/user-guide/tx-events/image74.png)    | **Notificación de error de pila de subprocesos** (*tx_thread_stack_error_notify*) |
| ![Icono de Suspensión de subprocesos](./media/user-guide/tx-events/image75.png)    | **Suspensión de subprocesos** (*tx_thread_suspend*) |
| ![Icono de Finalización de subprocesos](./media/user-guide/tx-events/image76.png)    | **Finalización de subprocesos** (*tx_thread_terminate*) |
| ![Icono de Cambio de intervalo de tiempo](./media/user-guide/tx-events/image77.png)    | **Cambio de intervalo de tiempo** (*tx_thread_time_slice_change*) |
| ![Icono de Anulación de espera de subprocesos](./media/user-guide/tx-events/image78.png)    | **Anulación de espera de subprocesos** (*tx_thread_wait_abort*) |
| ![Icono de Obtención de hora](./media/user-guide/tx-events/image79.png)    | **Obtención de hora** (*tx_time_get*) |
| ![Icono de Establecimiento de hora](./media/user-guide/tx-events/image80.png)    | **Establecimiento de hora** (*tx_time_set*) |
| ![*Icono de Activación de temporizador](./media/user-guide/tx-events/image81.png)    | **Activación de temporizador** (*tx_timer_activate*) |
| ![Icono de Cambio del temporizador](./media/user-guide/tx-events/image82.png)    | **Cambio del temporizador** (*tx_timer_change*) |
| ![Icono de Creación del temporizador](./media/user-guide/tx-events/image83.png)    | **Creación del temporizador** (*tx_timer_create*) |
| ![Icono de Desactivación del temporizador](./media/user-guide/tx-events/image84.png)    | **Desactivación del temporizador** (*tx_timer_deactivate*) |
| ![Icono de Eliminación del temporizador](./media/user-guide/tx-events/image85.png)    | **Eliminación del temporizador** (*tx_timer_delete*) |
| ![Icono de Obtención de información del temporizador](./media/user-guide/tx-events/image86.png)    | **Obtención de información del temporizador** (*tx_timer_info_get*) |
| ![Icono de Obtención de información de rendimiento de la cola](./media/user-guide/tx-events/image87.png)    | **Obtención de información de rendimiento del temporizador** (*tx_timer_performance_info_get*) |
| ![*Icono de Obtención de información de sistema del rendimiento del temporizador](./media/user-guide/tx-events/image88.png)    | **Obtención de información de sistema del rendimiento del temporizador** (*tx_timer_performance_system_info_get*) |
| ![Evento definido por el usuario](./media/user-guide/tx-events/image0.png)    | **Evento definido por el usuario** (consulte el capítulo 10)    |

## <a name="event-descriptions"></a>Descripciones de eventos

### <a name="internal-thread-resume"></a>Reanudación de subprocesos internos

#### <a name="internal-thread-resume"></a>Reanudación de subprocesos internos

**Icono** ![Icono de Reanudación de subprocesos internos](./media/user-guide/tx-events/image1.png)

**Descripción**

Este evento representa el procesamiento interno de ThreadX que reanuda un subproceso para su ejecución. Si el subproceso especificado es la prioridad más alta y el umbral de adelantamiento no bloquea su ejecución, el sistema comenzará a ejecutar este subproceso recién preparado.

**Campos de información**

- Campo de información 1: puntero que señala al subproceso que se va a reanudar.
- Campo de información 2: estado anterior del subproceso que se va a reanudar, como se indica a continuación:

  |  Estado del subproceso                     | Value        |
  |---------------------------------- | --------|
  |  TX_READY                         | 0       |
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- Campo de información 3: valor del puntero de pila durante la llamada. 
- Campo de información 4: puntero que señala al siguiente subproceso de prioridad más alta que se va a ejecutar.

### <a name="internal-thread-suspend"></a>Suspensión de subprocesos internos

#### <a name="internal-thread-suspend"></a>Suspensión de subprocesos internos

**Icono** ![Icono de Suspensión de subprocesos internos](./media/user-guide/tx-events/image2.png)

**Descripción**

Este evento representa el procesamiento interno de ThreadX que suspende la ejecución de un subproceso. El siguiente subproceso de prioridad más alta preparado para la ejecución se coloca en el cuarto campo de información. Si este valor es NULL, no hay ningún otro subproceso listo para la ejecución y el sistema está inactivo.

**Campos de información**

- Campo de información 1: puntero que señala al subproceso que se va a suspender.
- Campo de información 2: nuevo estado del subproceso que se va a suspender, como se indica a continuación:

  |  Estado del subproceso                     | Value        |
  |---------------------------------- | --------|
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- Campo de información 3: valor del puntero de pila durante la llamada. Campo de información 4: puntero que señala al siguiente subproceso de prioridad más alta que se va a ejecutar. Si es NULL, el sistema está inactivo.

### <a name="interrupt-service-routine-isr-enter"></a>Entrada de rutina de servicio de interrupción (ISR) 

#### <a name="enter-isr"></a>Entrada de ISR 

**Icono** ![Icono de Entrada ISR](./media/user-guide/tx-events/image3.png)

**Descripción**

Este evento representa la entrada de una rutina de servicio de interrupción (ISR) en la aplicación. La ejecución de la rutina de interrupción del servicio continúa hasta que se produce el evento de salida de ISR.

**Campos de información**

- Campo de información 1: valor de puntero de pila durante la llamada.
- Campo de información 2: número de ISR definido por la aplicación (opcional).
- Campo de información 3: recuento de interrupciones anidadas.
- Campo de información 4: marca de desactivación de adelantamiento interno.

### <a name="interrupt-service-routine-isr-exit"></a>Salida de rutina de servicio de interrupción (ISR) 

#### <a name="exit-isr"></a>Salida de ISR

**Icono** ![Icono de salida de ISR](./media/user-guide/tx-events/image4.png)

**Descripción**

Este evento representa la salida de una rutina de servicio de interrupción (ISR) en la aplicación.

**Campos de información**

- Campo de información 1: valor de puntero de pila durante la llamada.
- Campo de información 2: número de ISR definido por la aplicación (opcional).
- Campo de información 3: recuento de interrupciones anidadas.
- Campo de información 4: marca de desactivación de adelantamiento interno.

### <a name="internal-time-slice"></a>Intervalo de tiempo interno

#### <a name="internal-time-slice"></a>Intervalo de tiempo interno

**Icono** ![Icono de Intervalo de tiempo interno](./media/user-guide/tx-events/image5.png)

**Descripción**

Este evento representa el procesamiento interno en ThreadX que realiza la operación de intervalo de tiempo. El siguiente subproceso de la misma prioridad se coloca en el primer campo de información. Si este valor es el mismo que el subproceso actual, no se realizó ningún intervalo de tiempo.

- Campo de información 1: puntero que señala al siguiente subproceso que se va a ejecutar.
- Campo de información 2: recuento de interrupciones anidadas.
- Campo de información 3: marca de desactivación de adelantamiento interno.
- Campo de información 4: valor de puntero de pila durante la llamada.

### <a name="running"></a>En ejecución

#### <a name="running-in-context"></a>Ejecución en contexto

**Icono** ![Icono En ejecución](./media/user-guide/tx-events/image6.png)

**Descripción**

Este evento representa la ejecución en un contexto de subproceso o un sistema inactivo. Se usa para mostrar los cambios subsiguientes en el contexto como resultado de una interrupción.

**Campos de información**
- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="block-allocate"></a>Asignación de bloques 

#### <a name="tx_block_allocate"></a>tx_block_allocate

**Icono** ![Icono de Asignación de bloques](./media/user-guide/tx-events/image7.png)

**Descripción**

Este evento representa la asignación de un bloque de memoria mediante tx_block_allocate. Si se realiza correctamente, se devuelve la dirección del bloque asignado en el segundo campo de información.

**Campos de información**
- Campo de información 1: puntero que señala al grupo de bloques correspondiente.
- Campo de información 2: puntero que señala al grupo de bloques devuelto (si se realiza correctamente).
- Campo de información 3: opción de espera proporcionada a la llamada tx_block_allocate.
- Campo de información 4: bloques disponibles restantes en el grupo después de esta asignación.

### <a name="block-pool-create"></a>Creación de grupo de bloques

#### <a name="tx_block_pool_create"></a>tx_block_pool_create

**Icono** ![Icono de Creación de grupo de bloques](./media/user-guide/tx-events/image8.png)

**Descripción**

Este evento representa la creación de un grupo de bloques de memoria mediante tx_block_pool_create.

**Campos de información**

- Campo de información 1: puntero que señala al bloque de control del grupo de bloques correspondiente.
- Campo de información 2: puntero que señala al área de memoria de inicio del grupo.
- Campo de información 3: número de bloques del grupo. Campo de información 4: tamaño de cada bloque en el grupo en bytes.

### <a name="block-pool-delete"></a>Eliminación de grupo de bloques

#### <a name="tx_block_pool_delete"></a>tx_block_pool_delete

**Icono** ![Icono de Eliminación de grupo de bloques](./media/user-guide/tx-events/image9.png)

**Descripción**

Este evento representa la eliminación de un grupo de bloques de memoria mediante tx_block_pool_delete.

**Campos de información**

- Campo de información 1: puntero que señala al bloque de control del grupo de bloques.
- Campo de información 2: valor del puntero de pila durante la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="block-pool-information-get"></a>Obtención de información de grupo de bloques 

#### <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

**Icono** ![Icono de Obtención de información de grupo de bloques](./media/user-guide/tx-events/image10.png)

**Descripción**

Este evento representa la obtención de información sobre un grupo de bloques de memoria mediante tx_block_pool_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al bloque de control del grupo de bloques.
- Campo de información 2: valor del puntero de pila durante la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="block-pool-performance-information-get"></a>Obtención de información de rendimiento de grupo de bloques

#### <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

**Icono** ![Icono de Obtención de información de rendimiento de grupo de bloques](./media/user-guide/tx-events/image11.png)

**Descripción**

Este evento representa la obtención de información de rendimiento sobre un grupo de bloques de memoria mediante tx_block_pool_performance_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al bloque de control del grupo de bloques.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="block-pool-performance-system-information-get"></a>Obtención de información de sistema del rendimiento del grupo de bloques

#### <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

**Icono** ![Icono de Obtención de información de sistema del rendimiento del grupo de bloques](./media/user-guide/tx-events/image12.png)

**Descripción**

Este evento representa la obtención de información de rendimiento sobre un grupo de bloques de memoria mediante tx_block_pool_performance_system_info_get.

**Campos de información**
- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="block-pool-prioritize"></a>Priorización de grupo de bloques

#### <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

**Icono** ![Icono de Priorización de grupo de bloques](./media/user-guide/tx-events/image13.png)

**Descripción**

Este evento representa la colocación del subproceso suspendido de prioridad más alta al principio de la lista de suspensión del grupo de bloques. Si esto se hace antes de llamar a tx_block_release, el subproceso suspendido de prioridad más alta recibirá el bloque liberado.

**Campos de información**
- Campo de información 1: puntero que señala al grupo de bloques de memoria.
- Campo de información 2: número de subprocesos suspendidos en este grupo de bloques.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="block-release"></a>Liberación de bloques 

#### <a name="tx_block_release"></a>tx_block_release

**Icono** ![Icono de Liberación de bloques](./media/user-guide/tx-events/image14.png)

**Descripción**

Este evento representa la liberación de un bloque previamente asignado al grupo de bloques.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de bloques de memoria.
- Campo de información 2: puntero que señala al bloque que se va a liberar.
- Campo de información 3: número de subprocesos suspendidos en este grupo de bloques.
- Campo de información 4: puntero de pila en el momento de la llamada.

### <a name="byte-allocate"></a>Asignación de bytes 

#### <a name="tx_byte_allocate"></a>tx_byte_allocate

**Icono** ![Icono de Asignación de bytes](./media/user-guide/tx-events/image15.png)

**Descripción**

Este evento representa la asignación de memoria mediante tx_byte_allocate. Si se realiza correctamente, se devuelve la dirección de la memoria asignada en el segundo campo de información.

**Campos de información**
- Campo de información 1: puntero que señala al grupo de bytes correspondiente.
- Campo de información 2: puntero que señala a la memoria devuelta (si se realiza correctamente).
- Campo de información 3: número de bytes solicitados. Campo de información 4: opción de espera proporcionada a la llamada tx_byte_allocate.

### <a name="byte-pool-create"></a>Creación de grupo de bytes

#### <a name="tx_byte_pool_create"></a>tx_byte_pool_create

**Icono** ![Icono de Creación de grupo de bytes](./media/user-guide/tx-events/image16.png)

**Descripción**

Este evento representa la creación de un grupo de bytes mediante tx_byte_pool_create.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de bytes correspondiente.
- Campo de información 2: puntero que señala al inicio del área de memoria. Campo de información 3: número de bytes en el grupo de bytes.
- Campo de información 4: puntero de pila en el momento de la llamada.

### <a name="byte-pool-delete"></a>Eliminación de grupo de bytes 

#### <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

**Icono** ![Icono de Eliminación de grupo de bytes](./media/user-guide/tx-events/image17.png)

**Descripción**

Este evento representa la eliminación de un grupo de bytes mediante tx_byte_pool_delete.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de bytes correspondiente.
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="byte-pool-information-get"></a>Obtención de información de grupo de bytes

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Icono** ![Icono de Obtención de información de grupo de bytes](./media/user-guide/tx-events/image18.png)

**Descripción**

Este evento representa la obtención de información del grupo de bytes mediante tx_byte_pool_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de bytes correspondiente.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="byte-pool-performance-info-get"></a>Obtención de información de rendimiento del grupo de bytes 

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Icono** ![Icono de Obtención de información de rendimiento del grupo de bytes](./media/user-guide/tx-events/image19.png)

**Descripción**

Este evento representa la obtención de información de rendimiento del grupo de bytes mediante tx_byte_pool_performance_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de bytes correspondiente.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="byte-pool-performance-system-info-get"></a>Obtención de información de rendimiento del sistema del grupo de bytes 

#### <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

**Icono** ![Icono de Obtención de información de rendimiento del sistema del grupo de bytes](./media/user-guide/tx-events/image20.png)

**Descripción**

Este evento representa la obtención de información de rendimiento del sistema del grupo de bytes mediante tx_byte_pool_performance_system_info_get.

**Campos de información**

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="byte-pool-prioritize"></a>Priorización de grupos de bytes

#### <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

**Icono** ![Icono de Priorización de grupos de bytes](./media/user-guide/tx-events/image21.png)

**Descripción**

Este evento representa la priorización de la lista de suspensiones del grupo de bytes mediante tx_byte_pool_prioritize.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de bytes correspondiente.
- Campo de información 2: número de subprocesos suspendidos actualmente en el grupo de bytes.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="byte-release"></a>Liberación de bytes

#### <a name="tx_byte_release"></a>tx_byte_release

**Icono** ![Icono de Liberación de bytes](./media/user-guide/tx-events/image22.png)

**Descripción**

Este evento representa la liberación de un bloque de memoria asignado a un grupo de bytes mediante tx_byte_release.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de bytes correspondiente.
- Campo de información 2: puntero que señala a la memoria de grupo de bytes previamente asignada.
- Campo de información 3: número de subprocesos suspendidos en este grupo de bytes.
- Campo de información 4: número de bytes de memoria disponibles.

### <a name="event-flags-create"></a>Creación de marcas de evento 

#### <a name="tx_event_flags_create"></a>tx_event_flags_create

**Icono** ![Icono de Creación de marcas de evento](./media/user-guide/tx-events/image23.png)

**Descripción**

Este evento representa la creación de un nuevo grupo de marcas de evento mediante tx_event_flags_create.

**Campos de información** 
- Campo de información 1: puntero que señala al bloque de control de grupo de marcas de evento.
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="event-flags-delete"></a>Eliminación de marcas de evento 

#### <a name="tx_event_flags_delete"></a>tx_event_flags_delete

**Icono** ![Icono de Eliminación de marcas de evento](./media/user-guide/tx-events/image24.png)

**Descripción**

Este evento representa la eliminación de un grupo de marcas de evento mediante tx_event_flags_delete.

**Campos de información** 

- Campo de información 1: puntero que señala al grupo de marcas de evento.
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="event-flags-get"></a>Obtención de marcas de evento 

#### <a name="tx_event_flags_get"></a>tx_event_flags_get

**Icono** ![Icono de Obtención de marcas de evento](./media/user-guide/tx-events/image25.png)

**Descripción**

Este evento representa la recuperación de marcas de evento de un grupo de marcas de evento existente mediante tx_event_flags_get.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de marcas de evento.
- Campo de información 2: marcas de evento solicitadas.
- Campo de información 3: marcas de evento establecidas actualmente en el grupo.
- Campo de información 4: opción solicitada en la obtención de marcas de evento.

### <a name="event-flags-information-get"></a>Obtención de información de marcas de evento

#### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

**Icono** ![Icono de Obtención de información de marcas de evento](./media/user-guide/tx-events/image26.png)

**Descripción**

Este evento representa la recuperación de información relacionada con un grupo de marcas de evento existente mediante tx_event_flags_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de marcas de evento.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="event-flags-performance-information-get"></a>Obtención de información de rendimiento de marcas de evento 

#### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

**Icono** ![Icono de Obtención de información de rendimiento de marcas de evento](./media/user-guide/tx-events/image27.png)

**Descripción**

Este evento representa la recuperación de información de rendimiento relacionada con un grupo de marcas de evento existente mediante tx_event_flags_performance_info_get.

**Campos de información** 
- Campo de información 1: puntero que señala al grupo de marcas de evento.
- Campo de información 2: sin usar.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="event-flags-performance-system-info-get"></a>Obtención de información de rendimiento del sistema de marcas de evento

#### <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

**Icono** ![Icono de Obtención de información de rendimiento del sistema de marcas de evento](./media/user-guide/tx-events/image28.png)

**Descripción**

Este evento representa la recuperación de información de rendimiento relacionada con un grupo de marcas de evento existente mediante tx_event_flags_performance_system_info_get.

**Campos de información**
- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="event-flags-set"></a>Establecimiento de marcas de evento 

#### <a name="tx_event_flags_set"></a>tx_event_flags_set

**Icono** ![Icono de Establecimiento de marcas de evento](./media/user-guide/tx-events/image29.png)

**Descripción**

Este evento representa el establecimiento (o borrado) de marcas de evento en un grupo de marcas de evento existente mediante tx_event_flags_set.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de marcas de evento.
- Campo de información 2: marcas de evento que se van a establecer (o borrar).
- Campo de información 3: opción de marca de evento AND u OR.
- Campo de información 4: número de subprocesos suspendidos en este grupo de marca de evento.

### <a name="event-flags-set-notify"></a>Notificación de establecimiento de marcas de evento

#### <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

**Icono** ![Icono de Notificación de establecimiento de marcas de evento](./media/user-guide/tx-events/image30.png)

**Descripción**

Este evento representa el registro de una devolución de llamada de notificación para cualquier operación de establecimiento de marcas de evento en un grupo de marcas de evento existente mediante tx_event_flags_set_notify.

**Campos de información**

- Campo de información 1: puntero que señala al grupo de marcas de evento.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="interrupt-control"></a>Control de interrupción 

#### <a name="tx_interrupt_control"></a>tx_interrupt_control

**Icono** ![Icono de Control de interrupción](./media/user-guide/tx-events/image31.png)

**Descripción**

Este evento representa el cambio de la posición de bloqueo de interrupción del procesador mediante tx_interrupt_control.

**Campos de información**

- Campo de información 1: nueva postura de interrupción.
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="mutex-create"></a>Creación de exclusión mutua 

#### <a name="tx_mutex_create"></a>tx_mutex_create

**Icono** ![Icono de Creación de exclusión mutua](./media/user-guide/tx-events/image32.png)

**Descripción**

Este evento representa la creación de una exclusión mutua mediante tx_mutex_create.

**Campos de información**

- Campo de información 1: puntero que señala al bloque de control de exclusión mutua.
- Campo de información 2: opción de herencia de prioridad.
- (TX_INHERIT o TX_NO_INHERIT).
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="mutex-delete"></a>Eliminación de exclusión mutua 

#### <a name="tx_mutex_delete"></a>tx_mutex_delete

**Icono** ![Icono de Eliminación de exclusión mutua](./media/user-guide/tx-events/image33.png)

**Descripción**

Este evento representa la eliminación de una exclusión mutua mediante tx_mutex_delete.

**Campos de información** 

- Campo de información 1: puntero que señala a la exclusión mutua.
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="mutex-get"></a>Obtención de exclusión mutua 

#### <a name="tx_mutex_get"></a>tx_mutex_get

**Icono** ![Icono de Obtención de exclusión mutua](./media/user-guide/tx-events/image34.png)

**Descripción**

Este evento representa la obtención de una exclusión mutua mediante tx_mutex_get.

**Campos de información**

- Campo de información 1: puntero que señala a la exclusión mutua.
- Campo de información 2: opción de espera proporcionada a la llamada tx_mutex_get.
- Campo de información 3: puntero que señala al subproceso que posee la exclusión mutua (NULL implica que la exclusión mutua no es de su propiedad).
- Campo de información 4: número de veces que el subproceso propietario ha llamado a tx_mutex_get.

### <a name="mutex-information-get"></a>Obtención de información de exclusión mutua

#### <a name="tx_mutex_info_get"></a>tx_mutex_info_get

**Icono** ![Icono de Obtención de información de exclusión mutua](./media/user-guide/tx-events/image35.png)

**Descripción**

Este evento representa la recuperación de información de exclusión mutua mediante tx_mutex_info_get.

**Campos de información**

- Campo de información 1: puntero que señala a la exclusión mutua.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="mutex-performance-information-get"></a>Obtención de información de rendimiento de exclusión mutua 

#### <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

**Icono** ![Icono de Obtención de información de rendimiento de exclusión mutua](./media/user-guide/tx-events/image36.png)

**Descripción**

Este evento representa la recuperación de información de rendimiento de exclusión mutua mediante tx_mutex_performance_info_get.

**Campos de información**

- Campo de información 1: puntero que señala a la exclusión mutua.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="mutex-performance-system-info-get"></a>Obtención de información de rendimiento del sistema de exclusión mutua

#### <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

**Icono** ![Icono de Obtención de información de rendimiento del sistema de exclusión mutua](./media/user-guide/tx-events/image37.png)

**Descripción**

Este evento representa la recuperación de información de rendimiento del sistema de exclusión mutua mediante tx_mutex_performance_system_info_get.

**Campos de información**

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="mutex-prioritize"></a>Priorización de exclusión mutua 

#### <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

**Icono** ![Icono de Priorización de exclusión mutua](./media/user-guide/tx-events/image38.png)

**Descripción**

Este evento representa la prioridad de la lista de suspensiones de exclusión mutua mediante tx_mutex_prioritize.

**Campos de información**

- Campo de información 1: puntero que señala a la exclusión mutua correspondiente.
- Campo de información 2: número de subprocesos suspendidos actualmente en la exclusión mutua.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="mutex-put"></a>Colocación de exclusión mutua 

#### <a name="tx_mutex_put"></a>tx_mutex_put

**Icono** ![Icono de Colocación de exclusión mutua](./media/user-guide/tx-events/image39.png)

**Descripción**

Este evento representa la liberación de una exclusión mutua previamente en propiedad mediante tx_mutex_put.

**Campos de información**

- Campo de información 1: puntero que señala a la exclusión mutua correspondiente.
- Campo de información 2: puntero de subproceso que posee la exclusión mutua.
- Campo de información 3: número de solicitudes de obtención de exclusión mutua pendientes.
- Campo de información 4: puntero de pila en el momento de la llamada.

### <a name="queue-create"></a>Creación de colas 

#### <a name="tx_queue_create"></a>tx_queue_create

**Icono** ![Icono de Creación de colas](./media/user-guide/tx-events/image40.png)

**Descripción**

Este evento representa la creación de una cola de mensajes mediante tx_queue_create.

**Campos de información**

- Campo de información 1: puntero que señala al bloque de control de colas.
- Campo de información 2: tamaño del mensaje en términos de palabras de 32 bits.
- Campo de información 3: puntero que señala al inicio del área de memoria de la cola.
- Campo de información 4: número de bytes en el área de memoria de la cola.

### <a name="queue-delete"></a>Eliminación de colas 

#### <a name="tx_queue_delete"></a>tx_queue_delete

**Icono** ![Icono de Eliminación de colas](./media/user-guide/tx-events/image41.png)

**Descripción**

Este evento representa la eliminación de una cola mediante tx_queue_delete.

**Campos de información**

- Campo de información 1: puntero que señala a la cola.
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="queue-flush"></a>Vaciado de colas 

#### <a name="tx_queue_flush"></a>tx_queue_flush

**Icono** ![Icono de Vaciado de colas](./media/user-guide/tx-events/image42.png)

**Descripción**

Este evento representa el vaciado (borrar todo el contenido de la cola) de una cola mediante tx_queue_flush.

**Campos de información**

- Campo de información 1: puntero que señala a la cola.
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="queue-front-send"></a>Envío al inicio de cola 

#### <a name="tx_queue_front_send"></a>tx_queue_front_send

**Icono** ![Icono de Envío al inicio de cola](./media/user-guide/tx-events/image43.png)

**Descripción**

Este evento representa el envío de un mensaje al principio de la cola mediante tx_queue_front_send.

**Campos de información**

- Campo de información 1: puntero que señala a la cola.
- Campo de información 2: puntero que señala al inicio del mensaje.
- Campo de información 3: opción de espera proporcionada a
- la llamada tx_queue_front_send.
- Campo de información 4: número de mensajes ya puestos en cola.

### <a name="queue-information-get"></a>Obtención de información de cola 

#### <a name="tx_queue_info_get"></a>tx_queue_info_get

**Icono** ![Icono de Obtención de información de cola](./media/user-guide/tx-events/image44.png)

**Descripción**

Este evento representa la obtención de información sobre una cola mediante tx_queue_info_get.

**Campos de información** 
- Campo de información 1: puntero que señala a la cola.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="queue-performance-info-get"></a>Obtención de información de rendimiento de cola 

#### <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

**Icono** ![Icono de Obtención de información de rendimiento de cola](./media/user-guide/tx-events/image45.png)

**Descripción**

Este evento representa la obtención de información de rendimiento sobre una cola mediante tx_queue_performance_info_get.

**Campos de información** 

- Campo de información 1: puntero que señala a la cola.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="queue-performance-system-info-get"></a>Obtención de información de rendimiento del sistema de cola 

#### <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

**Icono** ![Icono de Obtención de información de rendimiento del sistema de cola](./media/user-guide/tx-events/image46.png)

**Descripción**

Este evento representa la obtención de información de rendimiento del sistema acerca de todas las colas del sistema.

**Campos de información**

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="queue-prioritize"></a>Priorización de colas 

#### <a name="tx_queue_prioritize"></a>tx_queue_prioritize

**Icono** ![Icono de Priorización de colas](./media/user-guide/tx-events/image47.png)

**Descripción**

Este evento representa la prioridad de la lista de suspensiones de cola mediante tx_queue_prioritize.

**Campos de información** 

- Campo de información 1: puntero que señala a la cola correspondiente.
- Campo de información 2: número de subprocesos suspendidos actualmente en la cola.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

#### <a name="queue-receive"></a>Recepción en la cola 

##### <a name="tx_queue_receive"></a>tx_queue_receive

**Icono** ![Icono de Recepción en la cola](./media/user-guide/tx-events/image48.png)

**Descripción**

Este evento representa la recepción de un mensaje de una cola mediante tx_queue_receive.

**Campos de información** 

- Campo de información 1: puntero que señala a la cola.
- Campo de información 2: puntero que señala al destino del mensaje. Campo de información 3: opción de espera proporcionada a la llamada.
- Campo de información 4: número de mensajes actualmente en cola.

### <a name="queue-send"></a>Envío a la cola 

#### <a name="tx_queue_send"></a>tx_queue_send

**Icono** ![Icono de Envío a la cola](./media/user-guide/tx-events/image49.png)

**Descripción**

Este evento representa el envío de un mensaje a una cola mediante tx_queue_send.

**Campos de información** 

- Campo de información 1: puntero que señala a la cola.
- Campo de información 2: puntero que señala al mensaje.
- Campo de información 3: opción de espera proporcionada a la llamada.
- Campo de información 4: número de mensajes actualmente en cola.

### <a name="queue-send-notify"></a>Notificación de envío de cola 

#### <a name="tx_queue_send_notify"></a>tx_queue_send_notify

**Icono** ![Icono de Notificación de envío de cola](./media/user-guide/tx-events/image50.png)

**Descripción**

<p>Este evento representa el registro de una devolución de llamada mediante tx_queue_send_notify a la que se llama cada vez que se envía un mensaje a una cola.

**Campos de información** 

- Campo de información 1: puntero que señala a la cola.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="semaphore-ceiling-put"></a>Colocación del límite superior del semáforo 

#### <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

**Icono** ![Icono de Colocación del límite superior del semáforo](./media/user-guide/tx-events/image51.png)

**Descripción**

Este evento representa la colocación en un semáforo mediante tx_semaphore_ceiling_put. Esto difiere de tx_semaphore_put en que se examina el valor máximo del semáforo, de modo que la operación de colocación no puede superar el valor máximo o el límite superior.

**Campos de información**

- Campo de información 1: puntero que señala al semáforo.
- Campo de información 2: recuento actual de semáforos.
- Campo de información 3: número de subprocesos suspendidos en el semáforo.
- Campo de información 4: límite del límite superior proporcionado a la llamada.

#### <a name="semaphore-create"></a>Creación de semáforos 

##### <a name="tx_semaphore_create"></a>tx_semaphore_create

**Icono** ![Icono de Creación de semáforos](./media/user-guide/tx-events/image52.png)

**Descripción**

Este evento representa la creación de un semáforo mediante tx_semaphore_create.

**Campos de información**

- Campo de información 1: puntero que señala a un bloque de control del semáforo.
- Campo de información 2: recuento inicial de semáforos.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="semaphore-delete"></a>Eliminación de semáforos 

#### <a name="tx_semaphore_delete"></a>tx_semaphore_delete

**Icono** ![Icono de Eliminación de semáforos](./media/user-guide/tx-events/image53.png)

**Descripción**

Este evento representa la eliminación de un semáforo mediante tx_semaphore_delete.

**Campos de información**

- Campo de información 1: puntero que señala al semáforo.
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="semaphore-get"></a>Obtención de semáforos 

#### <a name="tx_semaphore_get"></a>tx_semaphore_get

**Icono** ![Icono de Obtención de semáforos](./media/user-guide/tx-events/image54.png)

**Descripción**

Este evento representa la obtención de un semáforo mediante tx_semaphore_get.

**Campos de información**

- Campo de información 1: puntero que señala al semáforo.
- Campo de información 2: opción de espera proporcionada a la llamada.
- Campo de información 3: recuento actual de semáforos.
- Campo de información 4: puntero de pila en el momento de la llamada.

### <a name="semaphore-information-get"></a>Obtención de información de semáforos 

#### <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

**Icono** ![Icono de Obtención de información de semáforos](./media/user-guide/tx-events/image55.png)

**Descripción**

Este evento representa la obtención de información sobre un semáforo mediante tx_semaphore_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al semáforo.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="semaphore-performance-info-get"></a>Obtención de información de rendimiento de semáforos 

#### <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

**Icono** ![Icono de Obtención de información de rendimiento de semáforos](./media/user-guide/tx-events/image56.png)

**Descripción**

Este evento representa la obtención de información de rendimiento sobre un semáforo mediante tx_semaphore_performance_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al semáforo.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="semaphore-performance-system-info"></a>Obtención de información de rendimiento del sistema de semáforos 

#### <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

**Icono** ![Icono de Obtención de información de rendimiento del sistema de semáforos](./media/user-guide/tx-events/image57.png)

**Descripción**

Este evento representa la obtención de información de rendimiento sobre todos los semáforos del sistema mediante tx_semaphore_performance_system_info_get.

**Campos de información** 

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="semaphore-prioritize"></a>Priorización de semáforos 

#### <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

**Icono** ![Icono de Priorización de semáforos](./media/user-guide/tx-events/image58.png)

**Descripción**

Este evento representa la prioridad de la lista de suspensiones de semáforos mediante tx_semaphore_prioritize.

**Campos de información**

- Campo de información 1: puntero que señala al semáforo correspondiente.
- Campo de información 2: número de subprocesos suspendidos actualmente en el semáforo.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="semaphore-put"></a>Colocación de semáforos 

#### <a name="tx_semaphore_put"></a>tx_semaphore_put

**Icono** ![Icono de Colocación de semáforos](./media/user-guide/tx-events/image59.png)

**Descripción**

Este evento representa la liberación de una instancia de semáforo mediante tx_semaphore_put.

**Campos de información** 

- Campo de información 1: puntero que señala al semáforo correspondiente. Campo de información 2: recuento actual de semáforos.
- Campo de información 3: número de subprocesos suspendidos en el semáforo.
- Campo de información 4: puntero de pila en el momento de la llamada.

### <a name="semaphore-put-notify"></a>Notificación de colocación de semáforos 

#### <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

**Icono** ![Icono de Notificación de colocación de semáforos](./media/user-guide/tx-events/image60.png)

**Descripción**

Este evento representa el registro de una devolución de llamada mediante tx_semaphore_put_notify a la que se llama cada vez que se coloca una instancia de semáforo.

**Campos de información** 

- Campo de información 1: puntero que señala al semáforo.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="thread-create"></a>Creación de subprocesos 

#### <a name="tx_thread_create"></a>tx_thread_create

**Icono** ![Icono de Creación de subprocesos](./media/user-guide/tx-events/image61.png)

**Descripción**

Este evento representa la creación de un subproceso mediante tx_thread_create.

**Campos de información**

- Campo de información 1: puntero que señala al bloque de control de subprocesos.
- Campo de información 2: prioridad del subproceso.
- Campo de información 3: puntero de pila para subprocesos.
- Campo de información 4: tamaño de la pila en bytes.

### <a name="thread-delete"></a>Eliminación de subprocesos 

#### <a name="tx_thread_delete"></a>tx_thread_delete

**Icono** ![Icono de Eliminación de subprocesos](./media/user-guide/tx-events/image62.png)

**Descripción**

Este evento representa la eliminación de un subproceso mediante tx_thread_delete.

**Campos de información** 

- Campo de información 1: puntero que señala al subproceso.
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="thread-entryexit-notify"></a>Notificación de entrada o salida de subprocesos 

#### <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

**Icono** ![Icono de Notificación de entrada o salida de subprocesos](./media/user-guide/tx-events/image63.png)

**Descripción**

Este evento representa el registro de una devolución de llamada mediante tx_thread_entry_exit_notify a la que se llama cada vez que se entra o sale de un subproceso.

**Campos de información** 

- Campo de información 1: puntero que señala al subproceso.
- Campo de información 2: estado del subproceso en el momento del registro.
- Campo de información 3: puntero que señala a la pila en el momento de la llamada.
- Campo de información 4: sin usar.

#### <a name="thread-identify"></a>Identificación de subprocesos 

##### <a name="tx_thread_identify"></a>tx_thread_identify

**Icono** ![Icono de Identificación de subprocesos](./media/user-guide/tx-events/image64.png)

**Descripción**

Este evento representa la obtención del puntero del subproceso actual mediante tx_thread_identify.

**Campos de información**

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="thread-information-get"></a>Obtención de información de subprocesos 

#### <a name="tx_thread_info_get"></a>tx_thread_info_get

**Icono** ![Icono de Obtención de información de subprocesos](./media/user-guide/tx-events/image65.png)

**Descripción**

Este evento representa la obtención de información sobre el subproceso especificado mediante tx_thread_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al subproceso.
- Campo de información 2: estado del subproceso en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

#### <a name="thread-performance-information-get"></a>Obtención de información de rendimiento del subproceso 

##### <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

**Icono** ![Icono de Obtención de información de rendimiento del subproceso](./media/user-guide/tx-events/image66.png)

**Descripción**

Este evento representa la obtención de información de rendimiento sobre el subproceso especificado mediante tx_thread_performance_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al subproceso.
- Campo de información 2: estado del subproceso en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="thread-performance-system-info-get"></a>Obtención de información de rendimiento del sistema de subprocesos 

#### <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

**Icono** ![Icono de Obtención de información de rendimiento del sistema de subprocesos](./media/user-guide/tx-events/image67.png)

**Descripción**

Este evento representa la obtención de información de rendimiento sobre todos los subprocesos mediante tx_thread_performance_system_info_get.

**Campos de información** 

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="thread-preemption-change"></a>Cambio de adelantamiento de subprocesos 

#### <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

**Icono** ![Icono de Cambio de adelantamiento de subprocesos](./media/user-guide/tx-events/image68.png)

**Descripción**

Este evento representa el cambio del umbral de adelantamiento de un subproceso mediante tx_thread_preemption_change.

**Campos de información** 

- Campo de información 1: puntero que señala al subproceso.
- Campo de información 2: nuevo umbral de adelantamiento.
- Campo de información 3: anterior umbral de adelantamiento.
- Campo de información 4: estado del subproceso en el momento de la llamada.

### <a name="thread-priority-change"></a>Cambio de prioridad de subprocesos 

#### <a name="tx_thread_priority_change"></a>tx_thread_priority_change

**Icono** ![Icono de Cambio de prioridad de subprocesos](./media/user-guide/tx-events/image69.png)

**Descripción**

Este evento representa el cambio de la prioridad de un subproceso mediante tx_thread_priority_change.

- Campos de información 
- Campo de información 1: puntero que señala al subproceso.
- Campo de información 2: nueva prioridad.
- Campo de información 3: anterior prioridad.
- Campo de información 4: estado del subproceso en el momento de la llamada.

### <a name="thread-relinquish"></a>Renuncia de subprocesos 

#### <a name="tx_thread_relinquish"></a>tx_thread_relinquish

**Icono** ![Icono de Renuncia de subprocesos](./media/user-guide/tx-events/image70.png)

**Descripción**

Este evento representa la renuncia del procesador de un subproceso mediante tx_thread_relinquish.

**Campos de información**

- Campo de información 1: puntero de pila en el momento de la llamada.
- Campo de información 2: puntero que señala al siguiente subproceso que se va a ejecutar.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="thread-reset"></a>Restablecimiento de subprocesos 

#### <a name="tx_thread_reset"></a>tx_thread_reset

**Icono** ![Icono de Restablecimiento de subprocesos](./media/user-guide/tx-events/image71.png)

**Descripción**

Este evento representa el restablecimiento de un subproceso completado o terminado mediante tx_thread_reset.

**Campos de información**

- Campo de información 1: puntero que señala al subproceso.
- Campo de información 2: estado del subproceso en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

#### <a name="thread-resume"></a>Reanudación de subprocesos 

##### <a name="tx_thread_resume"></a>tx_thread_resume

**Icono** ![Icono de Reanudación de subprocesos](./media/user-guide/tx-events/image72.png)

**Descripción**

Este evento representa la reanudación de un subproceso suspendido mediante tx_thread_resume.

**Campos de información**

- Campo de información 1: puntero que señala al subproceso.
- Campo de información 2: estado del subproceso en el momento de la llamada.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="thread-sleep"></a>Pausa de subprocesos 

#### <a name="tx_thread_sleep"></a>tx_thread_sleep

**Icono** ![Icono de Pausa de subprocesos](./media/user-guide/tx-events/image73.png)

**Descripción**

Este evento representa la pausa del subproceso actual durante un número especificado de tics del temporizador mediante tx_thread_sleep.

**Campos de información**

- Campo de información 1: número de tics por los que suspender.
- Campo de información 2: estado del subproceso en el momento de la llamada.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="thread-stack-error-notify"></a>Notificación de error de pila de subprocesos 

#### <a name="tx_thread_stack_error_notify_event"></a>tx_thread_stack_error_notify_event

**Icono** ![Icono de Notificación de error de pila de subprocesos](./media/user-guide/tx-events/image74.png)

**Descripción**

Este evento representa el registro de una rutina de notificación de errores de pila de subprocesos mediante tx_thread_stack_error_notify_event.

**Campos de información** 

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="thread-suspend"></a>Suspensión de subprocesos 

#### <a name="tx_thread_suspend"></a>tx_thread_suspend

**Icono** ![Icono de Suspensión de subprocesos](./media/user-guide/tx-events/image75.png)

**Descripción**

Este evento representa la suspensión de un subproceso mediante tx_thread_suspend.

**Campos de información** 

- Campo de información 1: puntero que señala al subproceso que se va a suspender.
- Campo de información 2: estado del subproceso en el momento de la llamada.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="thread-terminate"></a>Finalización de subprocesos 

#### <a name="tx_thread_terminate"></a>tx_thread_terminate

**Icono** ![Icono de Finalización de subprocesos](./media/user-guide/tx-events/image76.png)

**Descripción**

Este evento representa la finalización de un subproceso mediante tx_thread_terminate.

**Campos de información** 

- Campo de información 1: puntero que señala al subproceso que se va a finalizar.
- Campo de información 2: estado del subproceso en el momento de la llamada.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="thread-time-slice-change"></a>Cambio de intervalo de tiempo 

#### <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

**Icono** ![Icono de Cambio de intervalo de tiempo](./media/user-guide/tx-events/image77.png)

**Descripción**

Este evento representa el cambio del intervalo de tiempo de un subproceso mediante tx_thread_time_slice_change.

**Campos de información**

- Campo de información 1: puntero que señala al subproceso.
- Campo de información 2: nuevo intervalo de tiempo.
- Campo de información 3: anterior intervalo de tiempo.
- Campo de información 4: sin usar.

### <a name="thread-wait-abort"></a>Anulación de espera de subprocesos 

#### <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

**Icono** ![Icono de Anulación de espera de subprocesos](./media/user-guide/tx-events/image78.png)

**Descripción**

Este evento representa la anulación de la suspensión de un subproceso mediante tx_thread_wait_abort.

**Campos de información**

- Campo de información 1: puntero que señala al subproceso.
- Campo de información 2: estado del subproceso en el momento de la llamada.
- Campo de información 3: puntero de pila en el momento de la llamada.
- Campo de información 4: sin usar.

### <a name="time-get"></a>Obtención de hora 

#### <a name="tx_time_get"></a>tx_time_get

**Icono** ![Icono de Obtención de hora](./media/user-guide/tx-events/image79.png)

**Descripción**

Este evento representa la obtención del número actual de tics del temporizador mediante tx_time_get.

**Campos de información**

- Campo de información 1: número actual de tics del temporizador.
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="time-set"></a>Establecimiento de hora 

#### <a name="tx_time_set"></a>tx_time_set

**Icono** ![Icono de establecimiento de hora](./media/user-guide/tx-events/image80.png)

**Descripción**

Este evento representa el establecimiento del número actual de tics del temporizador mediante tx_time_set.

**Campos de información**

- Campo de información 1: número nuevo de tics del temporizador.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="timer-activate"></a>Activación del temporizador 

#### <a name="tx_timer_activate"></a>tx_timer_activate

**Icono** ![Icono de Activación del temporizador](./media/user-guide/tx-events/image81.png)

**Descripción**

Este evento representa la activación del temporizador especificado mediante tx_timer_activate.

**Campos de información**

- Campo de información 1: puntero que señala al temporizador
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="timer-change"></a>Cambio del temporizador 

#### <a name="tx_timer_change"></a>tx_timer_change

**Icono** ![Icono de Cambio del temporizador](./media/user-guide/tx-events/image82.png)

**Descripción**

Este evento representa el cambio del temporizador especificado mediante tx_timer_change.

**Campos de información**

- Campo de información 1: puntero que señala al temporizador
- Campo de información 2: tics de expiración iniciales.
- Campo de información 3: reprogramación de tics de expiración.
- Campo de información 4: sin usar.

### <a name="timer-create"></a>Creación del temporizador 

#### <a name="tx_timer_create"></a>tx_timer_create

**Icono** ![Icono de Creación del temporizador](./media/user-guide/tx-events/image83.png)

**Descripción**

Este evento representa la creación de un temporizador mediante tx_timer_create.

**Campos de información**

- Campo de información 1: puntero que señala al bloque de control del temporizador.
- Campo de información 2: tics de expiración iniciales.
- Campo de información 3: reprogramación de tics de expiración.
- Campo de información 4: valor de habilitación automática, TX_AUTO_ACTIVATE (1) o TX_NO_ACTIVATE (0).

### <a name="timer-deactivate"></a>Desactivación del temporizador 

#### <a name="tx_timer_deactivate"></a>tx_timer_deactivate

**Icono** ![Icono de Desactivación del temporizador](./media/user-guide/tx-events/image84.png)

**Descripción**

Este evento representa la desactivación de un temporizador mediante tx_timer_deactivate.

**Campos de información**

- Campo de información 1: puntero que señala al temporizador
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="timer-delete"></a>Eliminación del temporizador 

#### <a name="tx_timer_delete"></a>tx_timer_delete

**Icono** ![Icono de Eliminación del temporizador](./media/user-guide/tx-events/image85.png)

**Descripción**

Este evento representa la eliminación de un temporizador mediante tx_timer_delete.

**Campos de información** 

- Campo de información 1: puntero que señala al temporizador
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="timer-information-get"></a>Obtención de información del temporizador 

#### <a name="tx_timer_info_get"></a>tx_timer_info_get

**Icono** ![Icono Obtención de información del temporizador](./media/user-guide/tx-events/image86.png)

**Descripción**

Este evento representa la obtención de información del temporizador mediante tx_timer_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al temporizador
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="timer-performance-information-get"></a>Obtención de información de rendimiento del temporizador 

#### <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

**Icono** ![Icono de Obtención de información de rendimiento del temporizador](./media/user-guide/tx-events/image87.png)

**Descripción** 

Este evento representa la obtención de información de rendimiento del temporizador mediante tx_timer_performance_info_get.

**Campos de información**

- Campo de información 1: puntero que señala al temporizador
- Campo de información 2: puntero de pila en el momento de la llamada.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="timer-system-performance-info-get"></a>Obtención de información de rendimiento del sistema del temporizador 

#### <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

**Icono** ![Icono de Obtención de información de rendimiento del sistema del temporizador](./media/user-guide/tx-events/image88.png)


**Descripción** 

Este evento representa la obtención de toda la información de rendimiento de los temporizadores mediante tx_timer_performance_system_info_get.

**Campos de información**

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa