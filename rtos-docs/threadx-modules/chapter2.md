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
# <a name="chapter-2---module-requirements"></a>Capítulo 2: requisitos de los módulos

Un módulo de ThreadX contiene un preámbulo, que define las características básicas del módulo. El preámbulo va seguido del área de instrucciones del módulo. El administrador de módulos puede ejecutar los módulos en contexto o puede cargarlos en el área de memoria del módulo antes de su ejecución. El único requisito es que el preámbulo siempre se encuentre en la primera dirección del módulo. En la ilustración 2 se muestra un diseño de módulo básico.

| Diseño de módulo |
|:---:|
| \[preámbulo del módulo\]         |
| \[área de instrucciones del módulo\] |
| \[área RAM del módulo\]         |

**Figura 2**: diseño de módulo

> [!NOTE]
> Los módulos deben compilarse con el código independiente de la posición y las opciones del compilador o del enlazador de datos adecuados. Esto permite la ejecución del módulo en cualquier área de memoria.

Cuando se crea un subproceso de módulo, se asigna un segundo espacio de pila para su uso cuando el subproceso está en el kernel protegido por la memoria. El tamaño del espacio de pila del kernel del subproceso es configurable por el usuario mediante **TXM_MODULE_KERNEL_STACK_SIZE** en **_txm_module_port.h_ *_. Esto permite usar un tamaño de pila menor al crear un subproceso de módulo, ya que la pila especificada por el usuario al llamar a _* _tx_thread_create_** solo se usa en el módulo.

> [!NOTE]
> La parte superior de una pila de subprocesos de módulo contiene la estructura de información de entrada de subproceso (**TXM_MODULE_THREAD_ENTRY_INFO**), por lo que el tamaño de pila disponible disminuye según el tamaño de esta estructura. Al crear un subproceso en un módulo, aumenta su tamaño de pila al menos en el equivalente al tamaño de esta estructura.

Los siguientes pasos son necesarios para crear y compilar un módulo de ThreadX (cada paso se describe con más detalle a continuación).

1. Todos los archivos de C de un módulo deben aplicar #define **TXM_MODULE** antes de incluir **_txm_module.h_**. Esto puede realizarse en el archivo de código fuente que se está compilando o como parte de la configuración del proyecto. Al hacerlo, se reasignan las llamadas a la API de ThreadX a la versión específica del módulo de la API que invoca la función de distribución en el administrador de módulos residente para realizar la llamada a la función de API real.
2. Cada módulo debe tener un preámbulo en su primera dirección de área de instrucciones que defina las características y las necesidades de recursos del módulo.
3. Cada módulo debe vincular el preámbulo al principio del área de instrucciones del módulo.
4. Cada módulo debe vincularse a una biblioteca de módulos (***tmx.a***), que contiene funciones específicas del módulo que se usan para interactuar con ThreadX.

## <a name="module-sources"></a>Orígenes de los módulos

Los módulos de ThreadX tienen su propio conjunto de archivos de código fuente que están diseñados para vincularse y ubicarse directamente con el código fuente del módulo. Estos archivos proporcionan el puente entre el módulo independiente y el administrador de módulos residente. Los archivos del módulo son los siguientes:

| Nombre de archivo | Contenido |
|---|---|
| **txm_module.h** | Archivo de inclusión que define la información del módulo. |
| **txm_module_port.h** | Archivo de inclusión que define la información del módulo específico del puerto. |
| **txm_module_user.h** | Definiciones y valores que el usuario puede personalizar. |
| **txm_module_initialize.s [1][3]** | Llama a funciones intrínsecas para el módulo de inicio. |
| **txm_module_preamble.\{s/S/68\}** | Archivo de ensamblado del preámbulo del módulo. Este archivo define varios atributos específicos del módulo y está vinculado con el código de aplicación del módulo. |
| **txm_module_application_request.c [1]** | La función de solicitud de aplicación de módulo envía una solicitud específica de la aplicación al código residente. |
| **txm_module_callback_request_thread_entry.c&nbsp;[1]** | Subproceso de devolución de llamada de módulo que es responsable de procesar las devoluciones de llamada solicitadas por el módulo, incluidos temporizadores y devoluciones de llamada de notificación. |
| **txm_*.c [1][2]** | Los servicios estándar de la API de ThreadX llaman al distribuidor del kernel.
| **txm_module_object_allocate.c [1]** | Función de módulo para asignar memoria para los objetos de módulo ubicados en el grupo de memoria del administrador. |
| **txm_module_object_deallocate.c [1]** | Función de módulo para desasignar memoria para los objetos de módulo ubicados en el bloque de memoria del administrador. |
| **txm_module_object_pointer_get.c [1]** | Función de módulo para recuperar un puntero a un objeto del sistema. |
| **txm_module_object_pointer_get_extended.c [1]** | Función de módulo para recuperar un puntero a un objeto del sistema, seguridad de la longitud del nombre. |
| **txm_module_thread_shell_entry.c [1]** | Función de entrada de subprocesos de módulo. |
| **txm_module_thread_system_suspend.c [1]** | Función de módulo para suspender un subproceso. |

**[1]** Ubicado en la biblioteca **_tmx.a_**.

**[2]** Estos archivos tienen el mismo nombre que los archivos de la API de ThreadX, con el prefijo **txm_** en lugar del prefijo **tx_** .

**[3]** El archivo **txm_module_initialize.s** solo es para puertos que usan herramientas ARM.

## <a name="module-preamble"></a>Preámbulo del módulo

El preámbulo del módulo define las características y los recursos del módulo. Información como la función de entrada de subproceso inicial y el área de memoria inicial asociada al subproceso se definen en el preámbulo. Los ejemplos de preámbulos específicos del puerto se encuentran en el [apéndice](appendix.md). En la figura 3 se muestra un ejemplo de preámbulo de un módulo de ThreadX para un destino genérico (las líneas que comienzan con * son valores que la aplicación suele modificar):

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

**Ilustración 3**

En la mayoría de los casos, el desarrollador solo necesita definir el subproceso de inicio del módulo (desplazamiento 0x1C), el identificador de módulo (desplazamiento 0x10), la prioridad de subprocesos de inicio o detención (desplazamiento 0x24) y el tamaño de la pila de subprocesos de inicio o detención (desplazamiento 0x28). La demostración anterior está configurada de modo que el subproceso inicial del módulo es ***demo_module_start** _, el identificador de módulo es _*_0x12345678_*_ y el subproceso de inicio tiene una prioridad de _*_1_*_ y un tamaño de pila de _ *_2048_** bytes.

Algunas aplicaciones pueden definir opcionalmente un subproceso de detención, que se ejecuta cuando el administrador de módulos detiene el módulo. Además, algunas aplicaciones pueden emplear el campo propiedades del módulo, que se define de la siguiente manera.

## <a name="module-properties-bit-map"></a>Mapa de bits de las propiedades del módulo

En la siguiente tabla se muestra un ejemplo de mapa de bits de las propiedades. Los mapas de bits de las propiedades específicas del puerto se encuentran en el [apéndice](appendix.md).

| bit | Value | Significado |
|---|---|---|
| 0 | 0<br />1 | Ejecución en modo privilegiado<br />Ejecución en modo de usuario |
| 1 | 0<br />1 | Sin protección de MPU<br />Protección de MPU (debe estar seleccionado el modo de usuario) |
| 2 | 0<br />1 | Deshabilitar el acceso a la memoria compartida/externa<br />Habilitar el acceso a la memoria compartida/externa |
| [23-3] | 0 | Reservado
| [31-24] | <br />0x01<br />0x02<br />0x03 | **Identificador de compilador**<br />IAR<br />ARM<br />GNU |


## <a name="module-linker-control-file"></a>Archivo de control del vinculador del módulo

Al compilar un módulo, el preámbulo del módulo debe colocarse antes que cualquier otra sección de código. Un módulo se debe compilar con secciones de datos y código independiente de la posición. Los archivos del enlazador de ejemplo específicos del puerto se encuentran en el [apéndice](appendix.md).

## <a name="module-threadx-library"></a>Biblioteca de módulos de ThreadX

Cada módulo debe vincularse a una biblioteca especial de ThreadX centrada en módulos. Esta biblioteca proporciona acceso a los servicios de ThreadX en el código residente. La mayor parte del acceso se realiza a través de los archivos ***txm_\*.c***. El siguiente es un ejemplo de la llamada de acceso al módulo para la función de API de ThreadX **_tx_thread_relinquish_* _ (en _*_ \_txm_thread_relinquish.c\****).

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

En este ejemplo, el puntero de función proporcionado por el administrador de módulos se usa para llamar a la función de distribución del administrador de módulos con el identificador asociado con el servicio ***tx_thread_relinquish***. Este servicio no toma ningún parámetro.

## <a name="module-example"></a>Ejemplo de módulo

El siguiente es un ejemplo de la demostración estándar de ThreadX en forma de módulo. Las principales diferencias entre la demostración estándar de ThreadX y la demostración del módulo son:

1. Reemplazo de ***tx_api.h** _ con _ *_txm_module.h_**
2. Adición de **#define TXM_MODULE** antes de **_txm_module.h_**
3. Reemplazo de ***main** _ y _ *tx_application_define** con **_demo_module_start_**
4. Declaración de *punteros* a objetos de ThreadX en lugar de a los propios objetos.

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

## <a name="building-modules"></a>Compilación de módulos

La compilación de un módulo depende de la cadena de herramientas utilizada. Consulte el [apéndice](appendix.md) para ver ejemplos específicos de puertos. Entre las actividades comunes para todos los puertos se incluyen las siguientes:

- Compilación de una biblioteca de módulos
- Creación de la aplicación de módulo

Cada módulo debe tener un **txm_module_preamble** (configurado específicamente para el módulo) y la biblioteca de módulos (por ejemplo, **_tmx.a_**).
