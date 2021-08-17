---
title: 'Apéndice F: servicios de enlace de RTOS de GUIX'
description: Obtenga información sobre los servicios de enlace de RTOS de GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7928e1781be03969de25901ebbe728e6554e96befb59c860f4ea53663c28932d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784604"
---
# <a name="appendix-f---guix-rtos-binding-services"></a>Apéndice F: servicios de enlace de RTOS de GUIX

GUIX requiere que el RTOS subyacente preste servicios de subprocesos o tareas, exclusión mutua, cola de eventos y control de tiempo. De forma predeterminada, GUIX está configurado para que el sistema operativo en tiempo real ThreadX preste estos servicios. Para migrar GUIX a otro sistema operativo, el desarrollador debe definir la directiva de preprocesador GX_DISABLE_THREADX_BINDING y recompilar la biblioteca de GUIX para eliminar las dependencias de ThreadX. Además, el desarrollador deberá proporcionar las siguientes definiciones de macro y funciones auxiliares. Pueden encontrarse ejemplos de estas definiciones de macro y funciones auxiliares en los archivos gx_system_rtos_bind.h y gx_system_rtos_bind.c, donde se proporciona un ejemplo de integración de RTOS genérica.

Macros de integración de sistemas:

**GX_RTOS_BINDING_INITIALIZE**

Esta macro se invoca durante la inicialización del sistema. La macro se debe definir con el fin de llamar a cualquier función necesaria para preparar los recursos o servicios del sistema del RTOS antes de usarlos. Esta es la oportunidad del enlace de preparar los recursos de RTOS que usará GUIX.

**GX_SYSTEM_THREAD_START**

Esta macro se invoca cuando debe empezar a ejecutarse la tarea o el subproceso de GUIX. Esta macro se debe definir para llamar a una función que iniciará la ejecución del subproceso de GUIX. El punto de entrada al subproceso de GUIX se pasa a la función llamada. La firma de la función llamada debe ser la siguiente:

**UINT *function_name*(VOID (thread_entry_point)(VOID));**

Esta función debe devolver GX_SUCCESS si el subproceso se ha iniciado correctamente o GX_FAILURE en caso contrario.

**GX_EVENT_PUSH**

Esta macro se invoca para insertar un evento en la cola de eventos FIFO que usa GUIX. Al migrar a un nuevo RTOS, es su responsabilidad implementar esta cola de eventos de una manera segura para los subprocesos. Es preciso copiar y eliminar estructuras GX_EVENT en la cola, es decir, una cola de punteros GX_EVENT no servirá, ya que los eventos de GUIX pueden ser variables automáticas desde el punto de vista del productor de eventos. La firma de la función a la que llama esta macro debe ser la siguiente:

**UINT *function_name* (GX_EVENT *event_ptr);**

Esta función debe devolver GX_SUCCESS si el evento se inserta en la cola de eventos o GX_FAILURE en caso contrario.

**GX_EVENT_POP**

Esta macro se invoca para eliminar el evento principal (el más antiguo) de la cola de eventos de GUIX y copiarlo en la ubicación solicitada. Esta función debe ser capaz de bloquear un evento u, opcionalmente, de esperar a que este se produzca, si no hay eventos en la cola en un momento dado. La firma de la función que invoca esta macro debe ser la siguiente:

UINT function_name(GX_EVENT *put_event, GX_BOOL wait)

Si el parámetro “wait” es GX_TRUE, la función no debe devolver nada hasta que no se proporcione un evento. Si el parámetro “wait” es GX_FALSE, la función debe devolver el estado inmediatamente, con o sin evento.

Si se recupera un evento de la cola, se debe copiar en la ubicación put_event. El estado devuelto será GX_SUCCESS. De lo contrario, el estado debe ser GX_FAILURE.

**GX_EVENT_FOLD**

GUIX invoca esta macro para plegar un evento en la cola de eventos FIFO. “Plegar” un evento significa que, si ya existe un evento del mismo tipo en la cola, esa entrada se actualiza para que contenga la carga del nuevo. Si no se encuentra en la cola un evento ya existente del mismo tipo, se inserta en ella uno nuevo. 

En el caso de los enlaces que no puedan implementar la característica de plegado de eventos, es admisible simplemente invocar GX_EVENT_PUSH.

**GX_TIMER_START**

Esta macro se invoca cuando GUIX necesita recibir una entrada periódica de temporizador. Esta macro debe invocar un servicio que inicie el servicio de temporizador periódico de RTOS de bajo nivel. Si el servicio de temporizador de RTOS no se puede detener e iniciar fácilmente, es admisible, pero menos eficaz, dejar este servicio en ejecución de manera continua.

Cada vez que el servicio de temporizador de RTOS de bajo nivel expire, el enlace debe llamar a la función del sistema GUIX _gx_system_timer_expiration (0);. La llamada periódica a esta función es lo que activa los servicios de temporizador del widget de temporizador de GUIX de alto nivel.

**GX_TIMER_STOP**

Esta macro se invoca cuando GUIX ya no necesita un temporizador periódico (es decir, no hay en ejecución temporizadores de GUIX activos). Si el servicio de temporizador de RTOS no se puede detener e iniciar fácilmente, es admisible, pero menos eficaz, dejar este servicio en ejecución de manera continua y definir esta macro para no hacer nada.

**GX_SYSTEM_MUTEX_LOCK**

GUIX invoca esta macro durante secciones de código críticas para impedir que otra tarea reemplace y modifique estructuras de datos comunes y puedan producirse daños. Esta macro debe llamar a una función que implemente el servicio de bloqueo de recursos de RTOS adecuado.

Si nunca usa servicios de API de GUIX fuera del subproceso de la solución, puede definir esta macro para no hacer nada.

**GX_SYSTEM_MUTEX_UNLOCK**

Esta macro se invoca al final de secciones de código críticas y debe desbloquear el recurso de GUIX mediante el servicio de RTOS subyacente adecuado. Si nunca usa servicios de API de GUIX fuera del subproceso de la solución, puede definir esta macro para no hacer nada.

**GX_SYSTEM_TIME_GET**

Esta macro debe llamar a una función que devuelva la hora del sistema en “tics”, que suele ser el número de interrupciones del temporizador de bajo nivel que se han producido desde el inicio del sistema. Este servicio se usa para calcular la velocidad del lápiz de eventos táctiles para los gestos de entrada táctil. La firma de la función que invoca esta macro debe ser la siguiente:

**ULONG *function_name*(VOID);**

**GX_CURRENT_THREAD**

Esta macro se invoca para identificar el subproceso que se está ejecutando. El servicio al que llama esta macro debe devolver un valor “void*”, lo que significa que el tipo de datos que usa el sistema operativo para identificar el subproceso en ejecución se debe convertir a un valor “void*” para que se devuelva a GUIX.

En los archivos gx_system_rtos_bind.h y gx_system_rtos_bind.c se implementa un ejemplo de enlace de RTOS genérico.