---
title: 'Capítulo 6: Sistema de demostración de Azure RTOS ThreadX SMP'
description: Este capítulo contiene una descripción del sistema de demostración que se entrega con todos los paquetes de soporte del procesador de Azure RTOS ThreadX SMP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5da4c12cf3c035e59dcd1abef063d5ae40a657d6fd91bbd29f51cf7d46813154
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784060"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx-smp"></a>Capítulo 6: Sistema de demostración de Azure RTOS ThreadX SMP

Este capítulo contiene una descripción del sistema de demostración que se entrega con todos los paquetes de soporte del procesador de Azure RTOS ThreadX SMP. 

## <a name="overview"></a>Información general

Cada distribución de productos de ThreadX SMP contiene un sistema de demostración que se ejecuta en todos los microprocesadores admitidos.

Este sistema de ejemplo se define en el archivo de distribución ***demo_threadx.c*** y está diseñado para ilustrar cómo se usa ThreadX SMP en un entorno multiproceso insertado. La demostración consiste en la inicialización, ocho subprocesos, un grupo de bytes, un grupo de bloques, una cola, un semáforo, una exclusión mutua y un grupo de marcas de evento.

> [!IMPORTANT]
> Excepto en el caso del tamaño de pila del subproceso, la aplicación de demostración es idéntica en todos los procesadores compatibles con ThreadX SMP.

La lista completa de ***demo_threadx.c***, incluidos los números de línea a los que se hace referencia en el resto de este capítulo, se muestra en la página 324 y siguientes.

## <a name="application-define"></a>Definición de la aplicación

La función ***tx_application_define*** se ejecuta después de que se complete la inicialización de ThreadX SMP básica. Es responsable de configurar todos los recursos del sistema iniciales, incluidos los subprocesos, las colas, los semáforos, las exclusiones mutuas, las marcas de eventos y los grupos de memoria.

El elemento ***tx_application_define** _ del sistema de demostración (_números de línea 60-164*) crea los objetos de demostración en el orden siguiente:

```C
byte_pool_0
thread_0
thread_1
thread_2
thread_3
thread_4
thread_5
thread_6
thread_7
queue_0
semaphore_0
event_flags_0
mutex_0
block_pool_0
```
El sistema de demostración no crea ningún otro objeto de ThreadX SMP adicional. Sin embargo, una aplicación real puede crear objetos del sistema durante el tiempo de ejecución dentro de los subprocesos en ejecución.

### <a name="initial-execution"></a>Ejecución inicial 
Todos los subprocesos se crean con la opción **TX_AUTO_START**. Esto hace que estén preparados inicialmente para su ejecución. Una vez completado **_tx_application_define_**, el control se transfiere al programador de subprocesos y desde allí a cada subproceso individual.

El orden en el que se ejecutan los subprocesos viene determinado por su prioridad y el orden en que se crearon. En el sistema de demostración, ***thread_0** _ se ejecuta primero porque tiene la prioridad más alta (_se creó con una prioridad de 1*). Después de que ***thread_0**_ se suspenda, se ejecuta _*_thread_5_*_, seguido de la ejecución de _*_thread_3_*_, _*_thread_4_*_ , _*_thread_6_*_ , _*_thread_7_*_ , _*_thread_1_*_ y, por último, _*_thread_2_**.

> [!IMPORTANT]
> Aunque **thread_3** y **thread_4** tienen la misma prioridad (ambos creados con una prioridad de 8), **thread_3** se ejecuta primero. Esto se debe a que se creó **thread_3** y a que estaba listo antes que **thread_4**. Los subprocesos de igual prioridad se ejecutan de manera FIFO.

## <a name="thread-0"></a>Subproceso 0

La función ***thread_0_entry** _ marca el punto de entrada del subproceso _(líneas 167-190*). ***Thread_0**_ es el primer subproceso del sistema de demostración que se va a ejecutar. Su procesamiento es sencillo: incrementa su contador, se suspende durante 10 tics del temporizador, establece una marca de evento para reactivar _*_thread_5_** y, a continuación, repite la secuencia.

***Thread_0*** es el subproceso de prioridad más alta del sistema. Cuando expire la suspensión solicitada, adelantará a cualquier otro subproceso en ejecución de la demostración.

## <a name="thread-1"></a>Subproceso 1

La función ***thread_1_entry** _ marca el punto de entrada del subproceso _(líneas 193-216*). ***Thread_1**_ es el penúltimo subproceso del sistema de demostración que se va a ejecutar. Su procesamiento consiste en incrementar su contador, enviar un mensaje a _*_thread_2_*_ (_a través de* ***queue_0**_) y repetir la secuencia. Observe que _*_thread_1_*_ se suspende cada vez que _*_queue_0_*_ se llena (_línea 207*).

## <a name="thread-2"></a>Subproceso 2

La función ***thread_2_entry** _ marca el punto de entrada del subproceso _(líneas 219-243*). ***Thread_2**_ es el último subproceso del sistema de demostración que se va a ejecutar. Su procesamiento consiste en incrementar su contador, obtener un mensaje de _*_thread_1_*_ (a través de _*_queue_0_*_) y repetir la secuencia. Observe que _*_thread_2_*_ se suspende cada vez que _*_queue_0_*_ se queda vacío (_línea 233*).

Aunque ***thread_1** _ y _*_thread_2_*_ comparten la prioridad más baja en el sistema de demostración (_prioridad 16 *), son también los únicos subprocesos que están listos para su ejecución la mayor parte del tiempo. También son los únicos subprocesos creados con la segmentación temporal (* líneas 87 y 93*). Cada subproceso puede ejecutarse durante un máximo de 4 tics del temporizador antes de que se ejecute el otro subproceso.

## <a name="threads-3-and-4"></a>Subprocesos 3 y 4

La función ***thread_3_and_4_entry** _ marca el punto de entrada de _*_thread_3_*_ y _*_thread_4_*_ _(líneas 246-280*). Ambos subprocesos tienen una prioridad de 8, que hace que se ejecuten los subprocesos tercero y cuarto del sistema de demostración. El procesamiento de cada subproceso es el mismo: incrementar el contador, obtener ***semaphore_0**_, suspender 2 tics del temporizador, liberar _*_semaphore_0_*_ y repetir la secuencia. Observe que cada subproceso se suspende cada vez que _*_semaphore_0_*_ no está disponible (_línea 264*).

Además, ambos subprocesos usan la misma función para su procesamiento principal. Esto no supone ningún problema porque ambos tienen su propia pila única y C es un reentrante natural. Cada subproceso determina cuál es mediante el examen del parámetro de entrada del subproceso (*línea 258*), que se configura cuando se crean (*líneas 102 y 109*).

> [!IMPORTANT]
> También es razonable obtener el punto de subproceso actual durante la ejecución del subproceso y compararlo con la dirección del bloque de control para determinar la identidad del subproceso.

## <a name="thread-5"></a>Subproceso 5

La función ***thread_5_entry** _ marca el punto de entrada del subproceso _(líneas 283-305*). ***Thread_5**_ es el segundo subproceso del sistema de demostración que se va a ejecutar. Su procesamiento consiste en incrementar su contador, obtener una marca de evento de _*_thread_0_*_ (mediante _*_event_flags_0_*_) y repetir la secuencia. Observe que _*_thread_5_*_ se suspende siempre que la marca de evento de _*_event_flags_0_*_ no esté disponible (_línea 298*).

## <a name="threads-6-and-7"></a>Subprocesos 6 y 7

La función ***thread_6_and_7_entry** _ marca el punto de entrada de _*_thread_6_*_ y _*_thread_7_*_ _(líneas 307-358 *). Ambos subprocesos tienen una prioridad de 8, que hace que se ejecuten los subprocesos quinto y sexto del sistema de demostración. El procesamiento de cada subproceso es el mismo: incrementar el contador, obtener ***mutex_0**_ dos veces, suspender 2 tics del temporizador, liberar _*_mutex_0_*_ dos veces y repetir la secuencia. Observe que cada subproceso se suspende cada vez que _*_mutex_0_*_ no está disponible (_línea 325*).

Además, ambos subprocesos usan la misma función para su procesamiento principal. Esto no supone ningún problema porque ambos tienen su propia pila única y C es un reentrante natural. Cada subproceso determina cuál es mediante el examen del parámetro de entrada del subproceso (*línea 319*), que se configura cuando se crean (*líneas 126 y 133*).

## <a name="observing-the-demonstration"></a>Observación de la demostración

Cada uno de los subprocesos de demostración incrementa su propio contador único. Se pueden examinar los siguientes contadores para comprobar el funcionamiento de la demostración:

```C
thread_0_counter
thread_1_counter
thread_2_counter
thread_3_counter
thread_4_counter
thread_5_counter
thread_6_counter
thread_7_counter
```

Cada uno de estos contadores debe seguir aumentando a medida que se ejecuta la demostración, donde ***thread_1_counter** _ y _ *_thread_2_counter_** aumentan a la velocidad más rápida.

## <a name="distribution-file-demo_threadxc"></a>Archivo de distribución: demo_threadx.c

En esta sección se muestra la lista completa de ***demo_threadx.c***, incluidos los números de línea a los que se hace referencia en este capítulo.

```C
000 /* This is a small demo of the high-performance ThreadX SMP kernel. It includes examples of eight
001 threads of different priorities, using a message queue, semaphore, mutex, event flags group,
002 byte pool, and block pool. */
003
004 #include "tx_api.h"
005
006 #define DEMO_STACK_SIZE         1024
007 #define DEMO_BYTE_POOL_SIZE     9120
008 #define DEMO_BLOCK_POOL_SIZE    100
009 #define DEMO_QUEUE_SIZE         100
010
011 /* Define the ThreadX SMP object control blocks...  */
012
013 TX_THREAD               thread_0;
014 TX_THREAD               thread_1;
015 TX_THREAD               thread_2;
016 TX_THREAD               thread_3;
017 TX_THREAD               thread_4;
018 TX_THREAD               thread_5;
019 TX_THREAD               thread_6;
020 TX_THREAD               thread_7;
021 TX_QUEUE                queue_0;
022 TX_SEMAPHORE            semaphore_0;
023 TX_MUTEX                mutex_0;
024 TX_EVENT_FLAGS_GROUP    event_flags_0;
025 TX_BYTE_POOL            byte_pool_0;
026 TX_BLOCK_POOL           block_pool_0;
027
028 /* Define the counters used in the demo application...  */
029
030 ULONG                    thread_0_counter;
031 ULONG                    thread_1_counter;
032 ULONG                    thread_1_messages_sent;
033 ULONG                    thread_2_counter;
034 ULONG                    thread_2_messages_received;
035 ULONG                    thread_3_counter;
036 ULONG                    thread_4_counter;
037 ULONG                    thread_5_counter;
038 ULONG                    thread_6_counter;
039 ULONG                    thread_7_counter;
040
041 /* Define thread prototypes.  */
042
043 void    thread_0_entry(ULONG thread_input);
044 void    thread_1_entry(ULONG thread_input);
045 void    thread_2_entry(ULONG thread_input);
046 void    thread_3_and_4_entry(ULONG thread_input);
047 void    thread_5_entry(ULONG thread_input);
048 void    thread_6_and_7_entry(ULONG thread_input);
049
050
051 /* Define main entry point.  */
052
053 int main()
054 {
055
056     /* Enter the ThreadX SMP kernel. */
057     tx_kernel_enter();
058 }
059
060 /* Define what the initial system looks like. */
061 void    tx_application_define(void *first_unused_memory)
062 {
063
064 CHAR    *pointer;
065
066    /* Create a byte memory pool from which to allocate the thread stacks. */
067    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
068                               DEMO_BYTE_POOL_SIZE);
069
070    /* Put system definition stuff in here, e.g., thread creates and other assorted
071       create information. */
072
073    /* Allocate the stack for thread 0. */
074    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
075
076    /* Create the main thread. */
077    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
078                               pointer, DEMO_STACK_SIZE,
079                               1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
080
081    /* Allocate the stack for thread 1. */
082    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
083
084    /* Create threads 1 and 2. These threads pass information through a ThreadX SMP
085       message queue. It is also interesting to note that these threads have a time
086       slice. */
087    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
088                              pointer, DEMO_STACK_SIZE,
089                              16, 16, 4, TX_AUTO_START);
090
091    /* Allocate the stack for thread 2. */
092    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
093    tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
094                              pointer, DEMO_STACK_SIZE,
095                              16, 16, 4, TX_AUTO_START);
096
097    /* Allocate the stack for thread 3. */
098    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
099
100    /* Create threads 3 and 4. These threads compete for a ThreadX SMP counting semaphore.
101       An interesting thing here is that both threads share the same instruction area. */
102    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
103                              pointer, DEMO_STACK_SIZE,
104                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
105
106    /* Allocate the stack for thread 4. */
107    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
108
109    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
110                              pointer, DEMO_STACK_SIZE,
111                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
112
113    /* Allocate the stack for thread 5. */
114    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
115
116    /* Create thread 5. This thread simply pends on an event flag, which will be set
117       by thread_0. */
118    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
119                              pointer, DEMO_STACK_SIZE,
120                              4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
121
122    /* Allocate the stack for thread 6. */
123    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
124
125    /* Create threads 6 and 7. These threads compete for a ThreadX SMP mutex. */
126    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
127                              pointer, DEMO_STACK_SIZE,
128                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
129
130    /* Allocate the stack for thread 7. */
131    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
132
133    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
134                              pointer, DEMO_STACK_SIZE,
135                              8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);
136
137    /* Allocate the message queue. */
138    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);
139
140    /* Create the message queue shared by threads 1 and 2. */
141    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));
142
143    /* Create the semaphore used by threads 3 and 4. */
144    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);
145
146    /* Create the event flags group used by threads 1 and 5. */
147    tx_event_flags_create(&event_flags_0, "event flags 0");
148
149    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
150    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);
151
152    /* Allocate the memory for a small block pool. */
153    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);
154
155    /* Create a block memory pool to allocate a message buffer from. */
156    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
157                 DEMO_BLOCK_POOL_SIZE);
158
159    /* Allocate a block and release the block memory. */
160    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);
161
162    /* Release the block back to the pool. */
163    tx_block_release(pointer);
164 }
165
166    /* Define the test threads. */
167    void thread_0_entry(ULONG thread_input)
168 {
169
170 UINT status;
171
172
173    /* This thread simply sits in while-forever-sleep loop. */
174     while(1)
175    {
176
177    /* Increment the thread counter. */
178    thread_0_counter++;
179
180    /* Sleep for 10 ticks. */
181    tx_thread_sleep(10);
182
183    /* Set event flag 0 to wakeup thread 5. */
184    status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);
185
186    /* Check status. */
187    if (status != TX_SUCCESS)
188       break;
189    }
190 }
191
192
193 void    thread_1_entry(ULONG thread_input)
194 {
195
196 UINT    status;
197
198
199    /* This thread simply sends messages to a queue shared by thread 2. */
200    while(1)
201    {
202
203         /* Increment the thread counter. */
204         thread_1_counter++;
205
206         /* Send message to queue 0. */
207         status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);
208
209         /* Check completion status. */
210         if (status != TX_SUCCESS)
211            break;
212
213         /* Increment the message sent. */
214         thread_1_messages_sent++;
215    }
216 }
217
218
219 void     thread_2_entry(ULONG thread_input)
220 {
221
222 ULONG     received_message;
223 UINT      status;
224
225     /* This thread retrieves messages placed on the queue by thread 1. */
226     while(1)
227     {
228
229         /* Increment the thread counter. */
230         thread_2_counter++;
231
232         /* Retrieve a message from the queue. */
233         status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);
234
235         /* Check completion status and make sure the message is what we
236            expected. */
237         if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
238            break;
239
240         /* Otherwise, all is okay. Increment the received message count. */
241         thread_2_messages_received++;
242      }
243 }
244
245
246 void     thread_3_and_4_entry(ULONG thread_input)
247 {
248
249 UINT     status;
250
251
252     /* This function is executed from thread 3 and thread 4. As the loop
253        below shows, these function compete for ownership of semaphore_0. */
254     while(1)
255     {
256
257         /* Increment the thread counter. */
258         if (thread_input == 3)
259            thread_3_counter++;
260         else
261            thread_4_counter++;
262
263         /* Get the semaphore with suspension. */
264         status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);
265
266         /* Check status. */
267         if (status != TX_SUCCESS)
268            break;
269
270         /* Sleep for 2 ticks to hold the semaphore. */
271         tx_thread_sleep(2);
272
273         /* Release the semaphore. */
274         status = tx_semaphore_put(&semaphore_0);
275
276         /* Check status. */
277         if (status != TX_SUCCESS)
278             break;
279     }
280 }
281
282
283 void     thread_5_entry(ULONG thread_input)
284 {
285
286 UINT     status;
287 ULONG    actual_flags;
288
289
290     /* This thread simply waits for an event in a forever loop. */
291     while(1)
292     {
293
294         /* Increment the thread counter. */
295         thread_5_counter++;
296
297         /* Wait for event flag 0. */
298         status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
299                                &actual_flags, TX_WAIT_FOREVER);
300
301         /* Check status. */
302         if ((status != TX_SUCCESS) || (actual_flags != 0x1))
303            break;
304     }
305 }
306
307 void     thread_6_and_7_entry(ULONG thread_input)
308 {
309
310 UINT     status;
311
312
313     /* This function is executed from thread 6 and thread 7. As the loop
314         below shows, these function compete for ownership of mutex_0. */
315     while(1)
316     {
317
318         /* Increment the thread counter. */
319         if (thread_input == 6)
320            thread_6_counter++;
321         else
322            thread_7_counter++;
323
324         /* Get the mutex with suspension. */
325         status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);
326
327         /* Check status. */
328         if (status != TX_SUCCESS)
329            break;
330
331         /* Get the mutex again with suspension. This shows
332            that an owning thread may retrieve the mutex it
333            owns multiple times. */
334         status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);
335
336         /* Check status. */
337         if (status != TX_SUCCESS)
338             break;
339
340         /* Sleep for 2 ticks to hold the mutex. */
341         tx_thread_sleep(2);
342
343         /* Release the mutex. */
344         status = tx_mutex_put(&mutex_0);
345
346         /* Check status. */
347         if (status != TX_SUCCESS)
348            break;
349
350         /* Release the mutex again. This will actually
351            release ownership since it was obtained twice. */
352         status = tx_mutex_put(&mutex_0);
353
354         /* Check status. */
355         if (status != TX_SUCCESS)
356            break;
357     }
358 }
```