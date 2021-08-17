---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS ThreadX'
description: Este capítulo contiene una descripción de todos los servicios de Azure RTOS ThreadX en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dabc1603423d8422ed6f8f540f8a06e80d14ec0098c886ca8731ac8ce981f15d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783414"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a>Capítulo 4: Descripción de los servicios de Azure RTOS ThreadX

Este capítulo contiene una descripción de todos los servicios de Azure RTOS ThreadX en orden alfabético. Sus nombres están diseñados de modo que todos los servicios similares están agrupados. En la sección "Valores devueltos" de las siguientes descripciones, los valores en **NEGRITA** no se ven afectados por la definición **TX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API. En cambio, los valores que no aparecen en negrita están completamente deshabilitados. Además, un "**Sí**" bajo el título "**Adelantamiento posible**" indica que la llamada al servicio puede reanudar un subproceso de mayor prioridad, de forma que se adelanta al subproceso que realiza la llamada.

## <a name="tx_block_allocate"></a>tx_block_allocate

Asigna un bloque de memoria de tamaño fijo.

### <a name="prototype"></a>Prototipo

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio asigna un bloque de memoria de tamaño fijo del grupo de memoria especificado. El tamaño real del bloque de memoria se determina durante la creación del grupo.

> [!IMPORTANT]
> *Es importante asegurarse de que el código de la aplicación no escribe fuera del bloque de memoria asignado. Si esto ocurre, se daña un bloque de memoria adyacente (normalmente posterior). Los resultados son imprevisibles y a menudo graves.*

### <a name="parameters"></a>Parámetros

- **pool_ptr** <br>Puntero a un grupo de bloques de memoria creado previamente.
- **block_ptr** <br>Puntero a un puntero del bloque de destino. Si la asignación es correcta, la dirección del bloque de memoria asignado se coloca donde señala este parámetro.
- **wait_option** <br>Define el comportamiento del servicio si no hay ningún bloque de memoria disponible. Las opciones de espera se definen de la siguiente forma:
  - **TX_NO_WAIT** (0x00000000): al seleccionar **TX_NO_WAIT**, se produce una devolución inmediata de este servicio, con independencia de si se realizó correctamente o no. *Esta es la única opción válida si se llama al servicio desde un elemento distinto de un _ _subproceso; por ejemplo, inicialización, temporizador o ISR*.
  - **TX_WAIT_FOREVER** (0xFFFFFFF): al seleccionar **TX_WAIT_FOREVER**, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya un bloque de memoria disponible.
  - *valor de tiempo de espera* (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando un bloque de memoria.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): bloque de memoria asignado correctamente.
- **TX_DELETED** (0x01): el grupo de bloques de memoria se eliminó mientras el subproceso estaba suspendido.
- **TX_NO_MEMORY** (0x10): el servicio no pudo asignar un bloque de memoria en el tiempo de espera especificado.
- **TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.
- **TX_POOL_ERROR** (0x02): puntero del grupo de bloques de memoria no válido.
- **TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada desde un elemento distinto de un subproceso.
- **TX_PTR_ERROR** (0x03): puntero al puntero de destino no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_create"></a>tx_block_pool_create

Crea un grupo de bloques de memoria de tamaño fijo.

### <a name="prototype"></a>Prototipo

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a>Descripción

Este servicio crea un grupo de bloques de memoria de tamaño fijo. El área de memoria especificada se divide en tantos bloques de memoria de tamaño fijo como sea posible mediante la siguiente fórmula:

**total de bloques** = (**total de bytes**)/(**tamaño de bloque** + sizeof(void *))

> [!NOTE]
>*Cada bloque de memoria contiene un puntero de sobrecarga que es invisible para el usuario y se representa mediante "sizeof(void )" *en la fórmula anterior.*

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un bloque de control del grupo de bloques de memoria.
- **name_ptr**: puntero al nombre del grupo de bloques de memoria.
- **block_size**: número de bytes de cada bloque de memoria.
- **pool_start**: dirección de inicio del grupo de bloques de memoria. La dirección de inicio debe alinearse con el tamaño del tipo de datos ULONG.
- **pool_size**: número total de bytes disponibles para el grupo de bloques de memoria.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): grupo de bloques de memoria creado correctamente.
- **TX_POOL_ERROR** (0x02): puntero del grupo de bloques de memoria no válido. El puntero tiene un valor NULL o el grupo ya se ha creado.
- **TX_PTR_ERROR** (0x03): dirección de inicio del grupo no válida.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.
- **TX_SIZE_ERROR** (0x05): el tamaño del grupo no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_block_allocate, tx_block_pool_delete
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_delete"></a>tx_block_pool_delete

Elimina un grupo de bloques de memoria.

### <a name="prototype"></a>Prototipo

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina el grupo de bloques de memoria especificado. Todos los subprocesos suspendidos en espera de un bloque de memoria de este grupo se reanudan y se les asigna un estado de devolución **TX_DELETED**.

> [!NOTE]
> *Es responsabilidad de la aplicación administrar el área de memoria asociada al grupo, que está disponible una vez que se complete este servicio. Además, la aplicación debe impedir el uso de un grupo eliminado o de sus bloques de memoria anteriores.*

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un grupo de bloques de memoria creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): grupo de bloques de memoria eliminado correctamente.
- **TX_POOL_ERROR** (0x02): puntero del grupo de bloques de memoria no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a>Consulte también

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

Recupera información acerca de un grupo de bloques.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio recupera información sobre el grupo de bloques de memoria especificado.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un grupo de bloques de memoria creado previamente.
- **name**: puntero al destino del puntero al nombre del grupo de bloques.
- **available**: puntero al destino del número de bloques disponibles en el grupo.
- **total_blocks**: puntero al destino del número total de bloques del grupo.
- **first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este grupo de bloques.
- **suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este grupo de bloques.
- **next_pool**: puntero al destino del puntero del siguiente grupo de bloques creado.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): información del grupo de bloques recuperada correctamente.
- **TX_POOL_ERROR** (0x02): puntero del grupo de bloques de memoria no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

Obtiene información acerca del rendimiento de un grupo de bloques.

### <a name="prototype"></a>Prototipo

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento del grupo de bloques de memoria especificado.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un grupo de bloques de memoria creado previamente.
- **allocates**: puntero al destino del número de solicitudes de asignación realizadas en este grupo.
- **releases**: puntero al destino del número de solicitudes de liberación realizadas en este grupo.
- **suspensions**: puntero al destino del número de suspensiones de asignación de subprocesos de este grupo.
- **timeouts**: puntero al destino del número de tiempos de espera de las suspensiones de asignación de este grupo.

>[!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento del grupo de bloques obtenido correctamente.
- **TX_PTR_ERROR** (0x03): puntero del grupo de bloques no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

Obtiene información acerca del rendimiento de los grupos de bloques del sistema.

### <a name="prototype"></a>Prototipo

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento de todos los grupos de bloques de memoria de la aplicación.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **allocates**: puntero al destino del número total de solicitudes de asignación realizadas en todos los grupos de bloques.
- **releases**: puntero al destino del número total de solicitudes de liberación realizadas en todos los grupos de bloques.
- **suspensions**: puntero al destino del número total de suspensiones de asignación de subprocesos de todos los grupos de bloques.
- **timeouts**: puntero al destino del número total de tiempos de espera de las suspensiones de asignación de todos los grupos de bloques.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento del sistema del grupo de bloques obtenido correctamente.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

Da prioridad a un subproceso de un bloque del grupo en la lista de suspensiones.

### <a name="prototype"></a>Prototipo

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>Descripción

Este servicio coloca el subproceso de prioridad más alta suspendido de un bloque de memoria de este grupo al principio de la lista de suspensiones. Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un bloque de control del grupo de bloques de memoria.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): grupo de bloques clasificado por orden de prioridad correctamente.
- **TX_POOL_ERROR** (0x02): puntero del grupo de bloques de memoria no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo
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

### <a name="see-also"></a>Consulte también

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_release"></a>tx_block_release

Libera un bloque de memoria de tamaño fijo.

### <a name="prototype"></a>Prototipo

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a>Descripción

Este servicio libera un bloque previamente asignado a su grupo de memoria asociado. Si hay uno o más subprocesos suspendidos en espera de bloques de memoria de este grupo, el primer subproceso suspendido recibe este bloque de memoria y se reanuda.

>[!IMPORTANT]
>*La aplicación debe impedir el uso de un área del bloque de memoria tras haberse liberado al grupo.*

### <a name="parameters"></a>Parámetros

- **block_ptr**: puntero al bloque de memoria asignado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): bloque de memoria liberado correctamente.
- **TX_PTR_ERROR** (0x03): puntero al bloque de memoria no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize

## <a name="tx_byte_allocate"></a>tx_byte_allocate

Asigna bytes de memoria.

### <a name="prototype"></a>Prototipo

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio asigna el número especificado de bytes del grupo de bytes de memoria indicado.

> [!IMPORTANT]
> *Es importante asegurarse de que el código de la aplicación no escribe fuera del bloque de memoria asignado. Si esto ocurre, se daña un bloque de memoria adyacente (normalmente posterior). Los resultados son imprevisibles y a menudo graves.*

> [!NOTE]
> *El rendimiento de este servicio es una función del tamaño del bloque y la cantidad de fragmentación del grupo. Por lo tanto, este servicio no se debe utilizar durante los subprocesos de ejecución urgentes.*

### <a name="parameters"></a>Parámetros

- **pool_ptr** <br>Puntero a un grupo de bloques de memoria creado previamente.
- **memory_ptr** <br>Puntero a un puntero de la memoria de destino. Si la asignación es correcta, la dirección del área de memoria asignada se coloca donde señala este parámetro.
- **memory_size** <br>Número de bytes solicitados.
- **wait_option** <br>Define el comportamiento del servicio si no hay suficiente memoria disponible. Las opciones de espera se definen de la siguiente forma:
  - **TX_NO_WAIT** (0x00000000): al seleccionar **TX_NO_WAIT**, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no. *Esta es la única opción válida si se llama al servicio desde la inicialización.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar **TX_WAIT_FOREVER**, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya suficiente memoria disponible.
  - *valor de tiempo de espera* (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la memoria.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): memoria asignada correctamente.
- **TX_DELETED** (0x01): el grupo de memoria se eliminó mientras el subproceso estaba suspendido.
- **TX_NO_MEMORY** (0x10) :el servicio no pudo asignar la memoria en el tiempo de espera especificado.
- **TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.
- **TX_POOL_ERROR** (0x02): puntero del grupo de memoria no válido.
- **TX_PTR_ERROR** (0x03): puntero al puntero de destino no válido.
- **TX_SIZE_ERROR** (0x05): el tamaño solicitado es cero o mayor que el grupo.
- **TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo
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

### <a name="see-also"></a>Consulte también

- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_create"></a>tx_byte_pool_create

Crea un grupo de bytes de memoria.

### <a name="prototype"></a>Prototipo

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a>Descripción

Este servicio crea un grupo de bytes de memoria en el área especificada. En un principio, el grupo consta básicamente de un bloque libre muy grande. Sin embargo, el grupo se divide en bloques más pequeños a medida que se realizan asignaciones.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un bloque de control del grupo de memoria.
- **name_ptr**: puntero al nombre del grupo de memoria.
- **pool_start**: dirección de inicio del grupo de memoria. La dirección de inicio debe alinearse con el tamaño del tipo de datos ULONG.
- **pool_size**: número total de bytes disponibles para el grupo de memoria.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): grupo de memoria creado correctamente.
- **TX_POOL_ERROR** (0x02): puntero del grupo de memoria no válido. El puntero tiene un valor NULL o el grupo ya se ha creado.
- **TX_PTR_ERROR** (0x03): dirección de inicio del grupo no válida.
- **TX_SIZE_ERROR** (0x05): el tamaño del grupo no es válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_byte_allocate
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

Elimina un grupo de bytes de memoria.

### <a name="prototype"></a>Prototipo

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina el grupo de bytes de memoria especificado. Todos los subprocesos suspendidos en espera de memoria de este grupo se reanudan y se les asigna un estado de devolución **TX_DELETED**.

> [!IMPORTANT]
> *Es responsabilidad de la aplicación administrar el área de memoria asociada con el grupo, que está disponible una vez que se complete este servicio. Además, la aplicación debe impedir el uso de un grupo eliminado o de la memoria asignada previamente desde este.*

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un grupo de memoria creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): grupo de memoria eliminado correctamente.
- **TX_POOL_ERROR** (0x02): puntero del grupo de memoria no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a>Consulte también

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

Recupera información acerca de un grupo de bytes.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio recupera información sobre el grupo de bytes de memoria especificado.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un grupo de memoria creado previamente.
- **name**: puntero al destino del puntero al nombre del grupo de bytes.
- **available**: puntero al destino del número de bytes disponibles en el grupo.
- **fragments**: puntero al destino del número total de fragmentos de memoria del grupo de bytes.
- **first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este grupo de bytes.
- **suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este grupo de bytes.
- **next_pool**: puntero al destino del puntero del siguiente grupo de bytes creado.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): información del grupo recuperada correctamente.
- **TX_POOL_ERROR** (0x02): puntero del grupo de memoria no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_info_get"></a>tx_byte_pool_performance_info_get

Obtiene información acerca del rendimiento de un grupo de bytes.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento del grupo de bytes de memoria especificado.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un grupo de bytes de memoria creado previamente.
- **allocates**: puntero al destino del número de solicitudes de asignación realizadas en este grupo.
- **releases**: puntero al destino del número de solicitudes de liberación realizadas en este grupo.
- **fragments_searched**: puntero al destino del número de fragmentos de memoria interna buscados durante las solicitudes de asignación en este grupo.
- **merges**: puntero al destino del número de bloques de memoria interna combinados durante las solicitudes de asignación en este grupo.
- **splits**: puntero al destino del número de divisiones de bloques de memoria interna (fragmentos) creados durante las solicitudes de asignación en este grupo.
- **suspensions**: puntero al destino del número de suspensiones de asignación de subprocesos de este grupo.
- **timeouts**: puntero al destino del número de tiempos de espera de las suspensiones de asignación de este grupo.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS**: (0x00) obtención correcta del rendimiento del grupo de bytes.
- **TX_PTR_ERROR** (0x03): puntero del grupo de bytes no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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
### <a name="see-also"></a>Consulte también

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

Obtiene información acerca del rendimiento de los grupos de bytes del sistema.

### <a name="prototype"></a>Prototipo

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
### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento de todos los grupos de bytes de memoria del sistema.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **allocates**: puntero al destino del número de solicitudes de asignación realizadas en este grupo.
- **releases**: puntero al destino del número de solicitudes de liberación realizadas en este grupo.
- **fragments_searched**: puntero al destino del número total de fragmentos de memoria interna buscados durante las solicitudes de asignación en todos los grupos de bytes.
- **merges**: puntero al destino del número total de bloques de memoria interna combinados durante las solicitudes de asignación en todos los grupos de bytes.
- **splits**: puntero al destino del número total de divisiones de los bloques de memoria interna (fragmentos) creados durante las solicitudes de asignación en todos los grupos de bytes.
- **suspensions**: puntero al destino del número total de suspensiones de asignación de subprocesos en todos los grupos de bytes.
- **timeouts**: puntero al destino del número total de tiempos de espera de las suspensiones de asignación de todos los grupos de bytes.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS**: (0x00) obtención correcta del rendimiento del grupo de bytes.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

 Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

Da prioridad a un subproceso de un grupo de bytes en la lista de suspensiones.

### <a name="prototype"></a>Prototipo

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>Descripción

Este servicio coloca el subproceso de prioridad más alta suspendido en la memoria de este grupo al principio de la lista de suspensiones. Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.

### <a name="parameters"></a>Parámetros

- **pool_ptr**: puntero a un bloque de control del grupo de memoria.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): grupo de memoria clasificado por orden de prioridad correctamente.
- **TX_POOL_ERROR** (0x02): puntero del grupo de memoria no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_release

## <a name="tx_byte_release"></a>tx_byte_release

Libera bytes al grupo de memoria.

### <a name="prototype"></a>Prototipo

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a>Descripción

Este servicio libera un área de memoria previamente asignada a su grupo asociado. Si hay uno o más subprocesos suspendidos en espera de memoria de este grupo, se asigna memoria a cada subproceso suspendido y estos se reanudan hasta que la memoria se agote o no haya más subprocesos suspendidos. Este proceso de asignación de memoria a los subprocesos suspendidos siempre comienza con el subproceso que se suspendió primero.

> [!IMPORTANT]
> *La aplicación debe impedir el uso del área de memoria una vez que se libera.*

### <a name="parameters"></a>Parámetros

- **memory_ptr**: puntero al área de memoria asignada previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): memoria liberada correctamente.
- **TX_PTR_ERROR** (0x03): puntero del área de memoria no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>Consulte también

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize

## <a name="tx_event_flags_create"></a>tx_event_flags_create

Crea un grupo de marcas de evento.

### <a name="prototype"></a>Prototipo

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a>Descripción

Este servicio crea un grupo de 32 marcas de evento. Estas 32 marcas de evento del grupo se inicializan en cero. Cada marca de evento se representa con un solo bit.

### <a name="parameters"></a>Parámetros

- **group_ptr**: puntero a un bloque de control del grupo de marcas de eventos.
- **name_ptr**: puntero al nombre del grupo de marcas de eventos.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): grupo de eventos creado correctamente.
- **TX_GROUP_ERROR** (0x06): puntero del grupo de eventos no válido. El puntero es **NULL** o el grupo de eventos ya se ha creado.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a>Consulte también

- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_delete"></a>tx_event_flags_delete

Elimina un grupo de marcas de evento.

### <a name="prototype"></a>Prototipo

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina el grupo de marcas de evento especificado. Todos los subprocesos suspendidos en espera de eventos de este grupo se reanudan y se les asigna un estado de devolución TX_DELETED.

>[!IMPORTANT]
> *La aplicación debe asegurarse de que se complete (o deshabilite) una devolución de llamada de notificación de establecimiento para este grupo de marcas de eventos antes de eliminarlo. Además, la aplicación debe impedir el uso futuro de un grupo de marcas de eventos eliminado.*

### <a name="parameters"></a>Parámetros

- **group_ptr**: puntero a un grupo de marcas de eventos creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): grupo de marcas de eventos eliminado correctamente.
- **TX_GROUP_ERROR** (0x06): puntero del grupo de marcas de eventos no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_event_flags_create
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_get"></a>tx_event_flags_get

Obtiene marcas de evento de un grupo de marcas de evento.

### <a name="prototype"></a>Prototipo

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio recupera las marcas de evento del grupo de marcas de evento especificado. Cada grupo contiene 32 marcas de evento. Cada marca se representa con un solo bit. Este servicio puede recuperar diversas combinaciones de marcas de evento, según se seleccione mediante los parámetros de entrada.

### <a name="parameters"></a>Parámetros

- **group_ptr** <br>Puntero a un grupo de marcas de eventos creado previamente.
- **requested_flags** <br>Variable sin signo de 32 bits que representa las marcas de eventos solicitadas.
- **get_option** <br>Especifica si se necesitan todas o algunas de las marcas de eventos solicitadas. A continuación, se recogen selecciones válidas:

  - **TX_AND** (0x02)
  - **TX_AND_CLEAR** (0x03)
  - **TX_OR** (0x00)
  - **TX_OR_CLEAR** (0x01)

    Al seleccionar TX_AND o TX_AND_CLEAR, se especifica que todas las marcas de eventos deben estar presentes en el grupo. Al seleccionar TX_OR o TX_OR_CLEAR, se especifica que basta con alguna marca de eventos. Las marcas de eventos que atienden la solicitud se desactivan (se establecen en cero) si se especifica la selección TX_AND_CLEAR o TX_OR_CLEAR.

- **actual_flags_ptr** <br>Puntero al destino de donde se colocan las marcas de eventos recuperadas. Tenga en cuenta que las marcas reales obtenidas pueden contener marcas que no se hayan solicitado.
- **wait_option**  <br>Define el comportamiento del servicio si no se establecen las marcas de eventos seleccionadas. Las opciones de espera se definen de la siguiente forma:
  - **TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no. Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.
  - Valor de tiempo de espera **TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya marcas de eventos disponibles.
  - valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando las marcas de eventos.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): marcas de eventos obtenidas correctamente.
- **TX_DELETED** (0x01): el grupo de marcas de eventos se eliminó mientras el subproceso estaba suspendido.
- **TX_NO_EVENTS** (0x07): el servicio no pudo obtener los eventos indicados en el tiempo de espera especificado.
- **TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.
- **TX_GROUP_ERROR** (0x06): puntero del grupo de marcas de eventos no válido.
- **TX_PTR_ERROR** (0x03): puntero de las marcas de eventos reales no válido.
- **TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.
- **TX_OPTION_ERROR** (0x08): se especificó una opción Get no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

**Vea también**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

Recuperar la información acerca de un grupo de marcas de eventos

**Prototipo**

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

**Descripción**

Este servicio recupera información sobre el grupo de marcas de eventos especificado.

**Parámetros**

- **group_ptr**: puntero a un bloque de control del grupo de marcas de eventos.
- **name**: puntero al destino del puntero al nombre del grupo de marcas de eventos.
- **current_flags**: puntero al destino de las marcas actuales establecidas en el grupo de marcas de eventos.
- **first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este grupo de marcas de eventos.
- **suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este grupo de marcas de eventos.
- **next_group**: puntero al destino del puntero del siguiente grupo de marcas de eventos creado.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0X00): información del grupo de eventos recuperada correctamente.
- **TX_GROUP_ERROR** (0x06): puntero del grupo de eventos no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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
**Vea también**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

Obtener información acerca del rendimiento de un grupo de marcas de eventos.

### <a name="prototype"></a>Prototipo

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento del grupo de marcas de eventos especificado.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **group_ptr**: puntero a un grupo de marcas de eventos creado previamente.
- **sets**: puntero al destino del número de solicitudes de establecimiento de marcas de eventos realizadas en este grupo.
- **gets**: puntero al destino del número de solicitudes Get de marcas de eventos realizadas en este grupo.
- **suspensions**: puntero al destino del número de suspensiones de obtención de marcas de eventos de los subprocesos en este grupo.
- **timeouts**: puntero al destino del número de tiempos de espera de suspensiones de obtención de marcas de eventos en este grupo.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento del grupo de marcas de eventos obtenido correctamente.
- **TX_PTR_ERROR** (0x03): puntero del grupo de marcas de eventos no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

Recupera información acerca del rendimiento de todos los grupos de marcas de evento del sistema.

### <a name="prototype"></a>Prototipo

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento de todos los grupos de marcas de eventos del sistema.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **sets**: puntero al destino del número total de solicitudes de establecimiento de marcas de eventos realizadas en todos los grupos.
- **gets**: puntero al destino del número total de solicitudes Get de marcas de eventos realizadas en todos los grupos.
- **suspensions**: puntero al destino del número total de suspensiones de obtención de marcas de eventos de los subprocesos de todos los grupos.
- **timeouts**: puntero al destino del número total de tiempos de espera de suspensiones de obtención de marcas de eventos de todos los grupos.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento del sistema de marcas de eventos obtenido correctamente.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_set"></a>tx_event_flags_set

Establece marcas de evento en un grupo de marcas de evento.

### <a name="prototype"></a>Prototipo

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a>Descripción

Este servicio establece o borra las marcas de evento de un grupo de marcas de evento, en función del valor especificado en set_option. Se reanudan todos los subprocesos suspendidos cuya solicitud de marcas de evento se haya atendido.

### <a name="parameters"></a>Parámetros

- **group_ptr** <br>Puntero al bloque de control del grupo de marcas de eventos creado previamente.
- **flags_to_set** <br>Especifica las marcas de eventos que se van a establecer o borrar en función de la opción Set seleccionada.
- **set_option** <br>Especifica si se les aplica AND u OR a las marcas de eventos indicadas en las marcas de eventos actuales del grupo. A continuación, se recogen selecciones válidas:
  - **TX_AND** (0x02)
  - **TX_OR** (0x00)

  Al seleccionar TX_AND, se especifica que se aplica **AND** a las marcas de eventos indicadas en las marcas de eventos actuales del grupo. Esta opción se usa a menudo para borrar las marcas de eventos de un grupo. En cambio, si se especifica TX_OR, se aplica **OR** al agregar las marcas de evento indicadas con el evento actual del grupo.

### <a name="return-values"></a>Valores devueltos
- **TX_SUCCESS** (0x00): marcas de eventos establecidas correctamente.
- **TX_GROUP_ERROR** (0x06): puntero al grupo de marcas de eventos no válido.
- **TX_OPTION_ERROR** (0x08): la opción Set especificada no es válida.

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set_notify

## <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

Notifica a la aplicación cuando se establecen marcas de evento.

### <a name="prototype"></a>Prototipo

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se establecen una o varias marcas de eventos en el grupo de marcas de eventos especificado. El procesamiento de la devolución de llamada de notificación se define mediante

### <a name="parameters"></a>Parámetros
- **group_ptr**: puntero a un grupo de marcas de eventos creado previamente.
- **events_set_notify**: puntero a la función de notificación de establecimiento de marcas de eventos de la aplicación. Si este valor es TX_NULL, la notificación se deshabilita.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): notificación de establecimiento de marcas de eventos registrada correctamente.
- **TX_GROUP_ERROR** (0x06): puntero del grupo de marcas de eventos no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema se compiló con las funcionalidades de notificación deshabilitadas.

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set

## <a name="tx_interrupt_control"></a>tx_interrupt_control

Habilita y deshabilita interrupciones.

### <a name="prototype"></a>Prototipo

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a>Descripción

Este servicio habilita o deshabilita las interrupciones según se especifique mediante el parámetro de entrada *new_posture*.

> [!NOTE]
> *Si se llama a este servicio desde un subproceso de aplicación, la posición de interrupción sigue formando parte del contexto de ese subproceso. Por ejemplo, si el subproceso llama a esta rutina para deshabilitar las interrupciones y después se suspende, las interrupciones siguen deshabilitadas cuando se reanuda.*

> [!WARNING]
> *Este servicio no debe usarse para habilitar interrupciones durante la inicialización. Si lo hace, podrían producirse resultados imprevisibles.*

### <a name="parameters"></a>Parámetros

- **new_posture**: este parámetro especifica si las interrupciones están deshabilitadas o habilitadas. Entre los valores válidos se incluyen **TX_INT_DISABLE** y **TX_INT_ENABLE**. Los valores reales de estos parámetros son específicos del puerto. Además, algunas arquitecturas de procesamiento pueden admitir posiciones adicionales para deshabilitar interrupciones.

### <a name="return-values"></a>Valores devueltos
- **previous posture**: este servicio devuelve la posición de interrupción anterior al autor de la llamada. Esto permite a los usuarios del servicio restaurar la posición anterior tras deshabilitar las interrupciones.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a>Consulte también

Ninguno

## <a name="tx_mutex_create"></a>tx_mutex_create

Crea una exclusión mutua.

### <a name="prototype"></a>Prototipo

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a>Descripción

Este servicio crea una exclusión mutua entre subprocesos para la protección de los recursos.

### <a name="parameters"></a>Parámetros

- **mutex_ptr**: puntero a un bloque de control de la exclusión mutua.
- **name_ptr**: puntero al nombre de la exclusión mutua.
- **priority_inherit**: especifica si esta exclusión mutua admite o no la herencia de prioridad. Si este valor es TX_INHERIT, se admite la herencia de prioridad. Por el contrario, si se especifica TX_NO_INHERIT, la exclusión mutua no admite la herencia de prioridad.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): exclusión mutua creada correctamente.
- **TX_MUTEX_ERROR** (0x1C): puntero de la exclusión mutua no válido. El puntero tiene un valor NULL o la exclusión mutua ya se ha creado.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.
- **TX_INHERIT_ERROR** (0x1F): parámetro de herencia de prioridad no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_delete"></a>tx_mutex_delete

Elimina una exclusión mutua.

### <a name="prototype"></a>Prototipo

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina la exclusión mutua especificada. Todos los subprocesos suspendidos en espera de la exclusión mutua se reanudan y se les asigna un estado de devolución **TX_DELETED**.

> [!NOTE]
> *Es responsabilidad de la aplicación impedir el uso de una exclusión mutua eliminada.*

### <a name="parameters"></a>Parámetros

- **mutex_ptr**: puntero a una exclusión mutua creada previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): exclusión mutua eliminada correctamente.
- **TX_MUTEX_ERROR** (0x1C): puntero de la exclusión mutua no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a>Consulte también

- tx_mutex_create
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_get"></a>tx_mutex_get

Obtiene la propiedad de una exclusión mutua.

### <a name="prototype"></a>Prototipo

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta obtener la propiedad exclusiva de la exclusión mutua especificada. Si el subproceso que realiza la llamada ya es el propietario de la exclusión mutua, se incrementa un contador interno y se devuelve un estado correcto.

Si otro subproceso que tiene una prioridad más alta es el propietario de la exclusión mutua y se especificó la herencia de prioridad al crearla, la prioridad del subproceso de menor prioridad se elevará temporalmente al nivel de la del subproceso que realiza la llamada.

> [!NOTE]
> *La prioridad del subproceso de menor prioridad que posee una exclusión mutua con herencia de prioridad nunca debe ser modificada por un subproceso externo durante la propiedad de la exclusión mutua.*

### <a name="parameters"></a>Parámetros

- **mutex_ptr**   <br>Puntero a una exclusión mutua creada previamente.
- **wait_option** <br>Define el comportamiento del servicio si la exclusión mutua ya pertenece a otro subproceso. Las opciones de espera se definen de la siguiente forma:
  - **TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no. *Esta es la única opción válida si se llama al servicio desde la inicialización.*
  - Valor de tiempo de espera **TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar **TX_WAIT_FOREVER**, el subproceso que realiza la llamada se suspende indefinidamente hasta que la exclusión mutua esté disponible.
  - valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la exclusión mutua.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): operación Get de la exclusión mutua realizada correctamente.
- **TX_DELETED** (0x01): la exclusión mutua se eliminó mientras el subproceso estaba suspendido.
- **TX_NOT_AVAILABLE** (0x1D): el servicio no pudo obtener la propiedad de la exclusión mutua en el tiempo de espera especificado.
- **TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.
- **TX_MUTEX_ERROR** (0x1C): puntero de la exclusión mutua no válido.
- **TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a>Consulte también

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_info_get"></a>tx_mutex_info_get

Recupera información acerca de una exclusión mutua.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio recupera información sobre la exclusión mutua especificada.

### <a name="parameters"></a>Parámetros

- **mutex_ptr**: puntero a un bloque de control de la exclusión mutua.
- **name**: puntero al destino del puntero al nombre de la exclusión mutua.
- **count**: puntero al destino del recuento de propiedad de la exclusión mutua.
- **owner**: puntero al destino del puntero del subproceso propietario.
- **first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de esta exclusión mutua.
- **suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en esta exclusión mutua.
- **next_mutex**: puntero al destino del puntero de la siguiente exclusión mutua creada.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): información de la exclusión mutua recuperada correctamente.
- **TX_MUTEX_ERROR** (0x1C): puntero de la exclusión mutua no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

**Ejemplo**

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

### <a name="see-also"></a>Consulte también

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

Obtiene información acerca del rendimiento de una exclusión mutua.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento de la exclusión mutua especificada.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **mutex_ptr**: puntero a una exclusión mutua creada previamente.
- **puts**: puntero al destino del número de solicitudes Put realizadas en esta exclusión mutua.
- **gets**: puntero al destino del número de solicitudes Get realizadas en esta exclusión mutua.
- **suspensions**: puntero al destino del número de suspensiones de obtención de exclusiones mutuas de los subprocesos en esta exclusión mutua.
- **timeouts**: puntero al destino del número de tiempos de espera de suspensiones de obtención de exclusiones mutuas en esta exclusión mutua.
- **inversions**: puntero al destino del número de inversiones de prioridad de los subprocesos en esta exclusión mutua.
- **inheritances**: puntero al destino del número de operaciones de herencia de prioridad de los subprocesos en esta exclusión mutua.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento de la exclusión mutua obtenido correctamente.
- **TX_PTR_ERROR** (0x03): puntero de la exclusión mutua no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

Obtiene información acerca del rendimiento de las exclusiones mutuas del sistema.

### <a name="prototype"></a>Prototipo

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento de todas las exclusiones mutuas del sistema.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **puts**: puntero al destino del número total de solicitudes Put realizadas en todas las exclusiones mutuas.
- **gets**: puntero al destino del número total de solicitudes Get realizadas en todas las exclusiones mutuas.
- **suspensions**: puntero al destino del número total de suspensiones de obtención de exclusiones mutuas de los subprocesos en todas las exclusiones mutuas.
- **timeouts**: puntero al destino del número total de tiempos de espera de suspensiones de obtención de exclusiones mutuas en todas las exclusiones mutuas.
- **inversions**: puntero al destino del número total de inversiones de prioridad de los subprocesos en todas las exclusiones mutuas.
- **inheritances**: puntero al destino del número total de operaciones de herencia de prioridad de los subprocesos en todas las exclusiones mutuas.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento del sistema de la exclusión mutua obtenido correctamente.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

Da la prioridad a una exclusión mutua en la lista de suspensiones.

### <a name="prototype"></a>Prototipo

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Descripción

Este servicio coloca el subproceso de prioridad más alta suspendido para obtener la propiedad de la exclusión mutua al principio de la lista de suspensiones. Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.

### <a name="parameters"></a>Parámetros

- **mutex_ptr**: puntero a la exclusión mutua creada previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): exclusión mutua clasificada por orden de prioridad correctamente.
- **TX_MUTEX_ERROR** (0x1C): puntero de la exclusión mutua no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_put

## <a name="tx_mutex_put"></a>tx_mutex_put

Libera la propiedad de una exclusión mutua.

### <a name="prototype"></a>Prototipo

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Descripción

Este servicio reduce el recuento de propiedad de la exclusión mutua especificada. Si el recuento de propiedad es cero, la exclusión mutua estará disponible.

> [!NOTE]
> *Si se seleccionó la herencia de prioridad durante la creación de la exclusión mutua, la prioridad del subproceso de liberación se restaurará a la que tenía cuando obtuvo originalmente la propiedad de la exclusión mutua. Se puede deshacer cualquier otro cambio de prioridad realizado en el subproceso de liberación durante la propiedad de la exclusión mutua.*

### <a name="parameters"></a>Parámetros
- mutex_ptr: puntero a la exclusión mutua creada previamente.

### <a name="return-values"></a>Valores devueltos
- **TX_SUCCESS** (0x00): exclusión mutua liberada correctamente.
- **TX_NOT_OWNED** (0x1E): el autor de llamada no tiene la propiedad de la exclusión mutua.
- **TX_MUTEX_ERROR** (0x1C): puntero a la exclusión mutua no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a>Consulte también

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize

## <a name="tx_queue_create"></a>tx_queue_create

Crea una cola de mensajes.

### <a name="prototype"></a>Prototipo

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a>Descripción

Este servicio crea una cola de mensajes que se utiliza normalmente para la comunicación entre subprocesos. El número total de mensajes se calcula a partir del tamaño de mensaje especificado y el número total de bytes de la cola.

> [!NOTE]
> *Si el número total de bytes especificado en el área de memoria de la cola no es divisible en partes iguales por el tamaño de mensaje indicado, no se usan los bytes restantes en el área de memoria.*

### <a name="parameters"></a>Parámetros

- **queue_ptr**: puntero a un bloque de control de la cola de mensajes.
- **name_ptr**: puntero al nombre de la cola de mensajes.
- **message_size**: especifica el tamaño de cada mensaje de la cola. El tamaño de los mensajes oscila entre 1 y 16 palabras de 32 bits. Las opciones de tamaño de mensaje válidas son valores numéricos entre 1 y 16, ambos incluidos.
- **queue_start**: dirección de inicio de la cola de mensajes. La dirección de inicio debe alinearse con el tamaño del tipo de datos ULONG.
- **pool_size**: número total de bytes disponibles para la cola de mensajes.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): cola de mensajes creada correctamente.
- **TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido. El puntero tiene un valor NULL o la cola de mensajes ya se ha creado.
- **TX_PTR_ERROR** (0x03): dirección de inicio de la cola de mensajes no válida.
- **TX_SIZE_ERROR** (0x05): el tamaño de la cola de mensajes no es válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_delete"></a>tx_queue_delete

Elimina una cola de mensajes.

### <a name="prototype"></a>Prototipo

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina la cola de mensajes especificada. Todos los subprocesos suspendidos en espera de un mensaje de esta cola se reanudan y se les asigna un estado de devolución TX_DELETED.

>[!IMPORTANT]
> *La aplicación debe asegurarse de que se complete (o deshabilite) cualquier devolución de llamada de notificación de envío para esta cola antes de eliminarla. Además, la aplicación debe impedir el uso futuro de una cola eliminada.* <br><br>*También es responsabilidad de la aplicación administrar el área de memoria asociada a la cola, que está disponible una vez completado este servicio.*

### <a name="parameters"></a>Parámetros

- **queue_ptr**: puntero a una cola de mensajes creada previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): cola de mensajes eliminada correctamente.
- **TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_queue_create
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_flush"></a>tx_queue_flush

Vacía los mensajes de la cola de mensajes.

### <a name="prototype"></a>Prototipo

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina todos los mensajes almacenados en la cola de mensajes especificada.

Si la cola se llena, se descartan los mensajes de todos los subprocesos suspendidos. Cada subproceso suspendido se reanuda después con un estado de devolución que indica que el mensaje se envió correctamente. Si la cola está vacía, este servicio no hace nada.

### <a name="parameters"></a>Parámetros

- **queue_ptr**: puntero a una cola de mensajes creada previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): cola de mensajes vaciada correctamente.
- **TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_queue_create
- tx_queue_delete
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_front_send"></a>tx_queue_front_send

Envía un mensaje al principio de la cola.

### <a name="prototype"></a>Prototipo

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía un mensaje al principio de la cola de mensajes especificada. El mensaje se **copia** al principio de la cola desde el área de memoria especificada por el puntero de origen.

### <a name="parameters"></a>Parámetros

- **queue_ptr** <br>Puntero a un bloque de control de la cola de mensajes.
- **source_ptr** <br>Puntero al mensaje.
- **wait_option**  <br>Define el comportamiento del servicio si la cola de mensajes está llena. Las opciones de espera se definen de la siguiente forma:
  - **TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no. *Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya espacio en la cola.
  - valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido a la espera de que haya espacio en la cola.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): mensaje enviado correctamente.
- **TX_DELETED** (0x01): la cola de mensajes se eliminó mientras el subproceso estaba suspendido.
- **TX_QUEUE_FULL** (0x0B): el servicio no pudo enviar el mensaje porque la cola estaba llena durante el tiempo de espera especificado.
- **TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.
- **TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.
- **TX_PTR_ERROR** (0x03): puntero de origen no válido para el mensaje.
- **TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_info_get"></a>tx_queue_info_get

Recupera información acerca de una cola.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio recupera información sobre la cola de mensajes especificada.

### <a name="parameters"></a>Parámetros

- **queue_ptr**: puntero a una cola de mensajes creada previamente.
- **name**: puntero al destino del puntero al nombre de la cola.
- **enqueued**: puntero al destino del número de mensajes que hay actualmente en la cola.
- **available_storage**: puntero al destino del número de mensajes para los que actualmente hay espacio en la cola.
- **first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de esta cola.
- **suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en esta cola.
- **next_queue**: puntero al destino del puntero de la siguiente cola creada.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): información de la cola obtenida correctamente.
- **TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

Obtiene información acerca del rendimiento de una cola.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento de la cola especificada.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **queue_ptr**: puntero a una cola creada previamente.
- **messages_sent**: puntero al destino del número de solicitudes de envío realizadas en esta cola.
- **messages_received**: puntero al destino del número de solicitudes de recepción realizadas en esta cola.
- **empty_suspensions**: puntero al destino del número de suspensiones de cola vacías en esta cola.
- **full_suspensions**: puntero al destino del número de suspensiones de cola completas en esta cola.
- **full_errors**: puntero al destino del número de errores de cola completos en esta cola.
- **timeouts**: puntero al destino del número de tiempos de espera de suspensión de los subprocesos en esta cola.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento de la cola obtenido correctamente.
- **TX_PTR_ERROR** (0x03): puntero de la cola no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

Obtiene información acerca del rendimiento de las colas del sistema.

### <a name="prototype"></a>Prototipo

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento de todas las colas del sistema.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **messages_sent**: puntero al destino del número total de solicitudes de envío realizadas en todas las colas.
- **messages_received**: puntero al destino del número total de solicitudes de recepción realizadas en todas las colas.
- **empty_suspensions**: puntero al destino del número total de suspensiones de cola vacías en todas las colas.
- **full_suspensions**: puntero al destino del número total de suspensiones de cola completas en todas las colas.
- **full_errors**: puntero al destino del número total de errores de cola completos en todas las colas.
- **timeouts**: puntero al destino del número total de tiempos de espera de suspensión de los subprocesos en todas las colas.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

**Valores devueltos**

- **TX_SUCCESS** (0x00): rendimiento del sistema de la cola obtenido correctamente.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_prioritize"></a>tx_queue_prioritize

Da prioridad a una cola en la lista de suspensiones.

### <a name="prototype"></a>Prototipo

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Descripción

Este servicio coloca el subproceso de prioridad más alta suspendido de un mensaje (o para colocar un mensaje) de esta cola al principio de la lista de suspensiones.

Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.

### <a name="parameters"></a>Parámetros

- **queue_ptr**: puntero a una cola de mensajes creada previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): cola clasificada por orden de prioridad correctamente.
- **TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_receive"></a>tx_queue_receive

Obtiene un mensaje de la cola de mensajes.

### <a name="prototype"></a>Prototipo

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio recupera un mensaje de la cola de mensajes especificada. El mensaje recuperado se **copia** de la cola en el área de memoria especificada por el puntero de destino. A continuación, ese mensaje se quita de la cola.

> [!IMPORTANT]
> *El área de memoria de destino especificada debe ser lo suficientemente grande como para contener el mensaje; es decir, el destino del mensaje al que apunta* ***destination_ptr** _ _debe ser al menos tan grande como el tamaño de mensaje de esta cola. De lo contrario, si el destino no es lo suficientemente grande, se producen daños en la memoria de la siguiente área de memoria.*

### <a name="parameters"></a>Parámetros

- **queue_ptr** <br>Puntero a una cola de mensajes creada previamente.
- **destination_ptr** <br>Ubicación donde se va a copiar el mensaje.
- **wait_option** <br>Define el comportamiento del servicio si la cola de mensajes está vacía. Las opciones de espera se definen de la siguiente forma:
  - **TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no. Esta es la única opción válida si se llama al servicio desde un elemento que no es un subproceso; por ejemplo, inicialización, temporizador o ISR.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya un mensaje disponible.
  - valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido a la espera de un mensaje.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): mensaje recuperado correctamente.
- **TX_DELETED** (0x01): la cola de mensajes se eliminó mientras el subproceso estaba suspendido.
- **TX_QUEUE_EMPTY** (0x0A): el servicio no pudo recuperar un mensaje porque la cola estaba vacía durante el tiempo de espera especificado.
- **TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.
- **TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.
- **TX_PTR_ERROR** (0x03): puntero de destino no válido para el mensaje.
- **TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_send"></a>tx_queue_send

Envía un mensaje a la cola de mensajes.

### <a name="prototype"></a>Prototipo

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía un mensaje a la cola de mensajes especificada. El mensaje enviado se **copia** en la cola desde el área de memoria especificada por el puntero de origen.

### <a name="parameters"></a>Parámetros
- **queue_ptr** <br>Puntero a una cola de mensajes creada previamente.
- **source_ptr** <br>Puntero al mensaje.
- **wait_option** <br>Define el comportamiento del servicio si la cola de mensajes está llena. Las opciones de espera se definen de la siguiente forma:
  - **TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no. *Esta es la única opción válida si se llama al servicio desde un elemento distinto de un _ _subproceso; por ejemplo, inicialización, temporizador o ISR*.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya espacio en la cola.
  - valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido a la espera de que haya espacio en la cola.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): mensaje enviado correctamente.
- **TX_DELETED** (0x01): la cola de mensajes se eliminó mientras el subproceso estaba suspendido.
- **TX_QUEUE_FULL** (0x0B): el servicio no pudo enviar el mensaje porque la cola estaba llena durante el tiempo de espera especificado.
- **TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.
- **TX_QUEUE_ERROR** (0x09): puntero de la cola de mensajes no válido.
- **TX_PTR_ERROR** (0x03): puntero de origen no válido para el mensaje.
- **TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

**Vea también**

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send_notify

## <a name="tx_queue_send_notify"></a>tx_queue_send_notify

Notifica a la aplicación cuando se envía un mensaje a la cola.

### <a name="prototype"></a>Prototipo

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se envía un mensaje a la cola especificada. La aplicación define el procesamiento de la devolución de llamada de notificación.

>[!NOTE]
> *La devolución de llamada de notificación de envío a la cola de la aplicación no puede llamar a ninguna API de ThreadX con una opción de suspensión.*

### <a name="parameters"></a>Parámetros

- **queue_ptr**: puntero a una cola creada previamente.
- **queue_send_notify**: puntero a la función de notificación de envío a la cola de la aplicación. Si este valor es TX_NULL, la notificación se deshabilita.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): notificación de envío a la cola registrada correctamente.
- **TX_QUEUE_ERROR** (0x09): puntero de cola no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema se compiló con las funcionalidades de notificación deshabilitadas.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send

## <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

Coloca una instancia en un semáforo de recuento con límite superior.

### <a name="prototype"></a>Prototipo

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a>Descripción

Este servicio coloca una instancia en el semáforo de recuento especificado, lo que en realidad incrementa el semáforo de recuento en uno. Si el valor actual del semáforo de recuento es mayor o igual que el límite superior especificado, la instancia no se colocará y se devolverá un error TX_CEILING_EXCEEDED.

### <a name="parameters"></a>Parámetros

- **semaphore_ptr**: puntero a un semáforo creado previamente.
- **ceiling**: límite máximo permitido para el semáforo (el rango de valores válidos oscila entre 1 y 0xFFFFFFFF).

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): límite superior del semáforo colocado correctamente.
- **TX_CEILING_EXCEEDED** (0x21): la solicitud Put excede el límite superior.
- **TX_INVALID_CEILING** (0x22): se proporcionó un valor no válido de cero para el límite superior.
- **TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a>Consulte también

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_create"></a>tx_semaphore_create

Crea un semáforo de recuento.

### <a name="prototype"></a>Prototipo

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a>Descripción

Este servicio crea un semáforo de recuento para la sincronización entre subprocesos. Se especifica como parámetro de entrada el recuento inicial del semáforo.

### <a name="parameters"></a>Parámetros

- **semaphore_ptr**: puntero a un bloque de control del semáforo.
- **name_ptr**: puntero al nombre del semáforo.
- **initial_count**: especifica el recuento inicial de este semáforo. Los valores válidos oscilan entre 0x00000000 y 0xFFFFFFFF.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): semáforo creado correctamente.
- **TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo no válido. El puntero tiene un valor NULL o el semáforo ya se ha creado.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_semaphore_ceiling_put
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_delete"></a>tx_semaphore_delete

Elimina un semáforo de recuento.

### <a name="prototype"></a>Prototipo
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina el semáforo de recuento especificado. Todos los subprocesos suspendidos en espera de una instancia del semáforo se reanudan y se les asigna un estado de devolución TX_DELETED.

> [!IMPORTANT]
> *La aplicación debe asegurarse de que se complete (o deshabilite) una devolución de llamada de notificación de colocación para este semáforo antes de eliminarlo. Además, la aplicación debe impedir cualquier uso futuro de los semáforos eliminados.*

### <a name="parameters"></a>Parámetros

- **semaphore_ptr**: puntero a un semáforo creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): semáforo de recuento eliminado correctamente.
- **TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo de recuento no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

**Vea también**

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_get"></a>tx_semaphore_get

Obtiene una instancia del semáforo de recuento.

### <a name="prototype"></a>Prototipo

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio recupera una instancia (un solo recuento) del semáforo de recuento especificado. Como resultado, el recuento del semáforo especificado se reduce en uno.

### <a name="parameters"></a>Parámetros

- **semaphore_ptr** <br>Puntero a un semáforo de recuento creado previamente.
- **wait_option** <br>Define el comportamiento del servicio si no hay ninguna instancia del semáforo disponible; es decir, el recuento del semáforo es cero. Las opciones de espera se definen de la siguiente forma:
  - **TX_NO_WAIT** (0x00000000): al seleccionar TX_NO_WAIT, se produce una devolución inmediata de este servicio con independencia de si se realizó correctamente o no. *Esta es la única opción válida si se llama al servicio desde un elemento distinto de un subproceso; por ejemplo, inicialización, temporizador o ISR.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que haya una instancia del semáforo disponible.
  - valor de tiempo de espera (0x00000001 a 0xFFFFFFFE): al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando una instancia del semáforo.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): instancia del semáforo recuperada correctamente.
- **TX_DELETED** (0x01): el semáforo de recuento se eliminó mientras el subproceso estaba suspendido.
- **TX_NO_INSTANCE**: (0x0D) el servicio no pudo recuperar una instancia del semáforo de recuento (el recuento del semáforo es cero en el tiempo de espera especificado).
- **TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.
- **TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo de recuento no válido.
- **TX_WAIT_ERROR** (0x04): se especificó una opción de espera distinta de TX_NO_WAIT en una llamada de un elemento distinto de un subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semahore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

Recupera información acerca de un semáforo.

### <a name="prototype"></a>Prototipo

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el semáforo especificado.

### <a name="parameters"></a>Parámetros

- **semaphore_ptr**: puntero a un bloque de control del semáforo.
- **name**: puntero al destino del puntero al nombre del semáforo.
- **current_value**: puntero al destino del recuento actual del semáforo.
- **first_suspended**: puntero al destino del puntero al subproceso que se encuentra en primer lugar en la lista de suspensiones de este semáforo.
- **suspended_count**: puntero al destino del número de subprocesos suspendidos actualmente en este semáforo.
- **next_semaphore**: puntero al destino del puntero del siguiente semáforo creado.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): recuperación de la información.

- **TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

Obtiene información acerca del rendimiento del semáforo.

### <a name="prototype"></a>Prototipo

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento del semáforo especificado.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*

**Parámetros**

-  **semaphore_ptr**: puntero a un semáforo creado previamente.
-  **puts**: puntero al destino del número de solicitudes Put realizadas en este semáforo.
-  **gets**: puntero al destino del número de solicitudes Get realizadas en este semáforo.
-  **suspensions**: puntero al destino del número de suspensiones de los subprocesos de este semáforo.
-  **timeouts**: puntero al destino del número de tiempos de espera de suspensión de los subprocesos en este semáforo.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento del semáforo obtenido correctamente.
- **TX_PTR_ERROR** (0x03): puntero del semáforo no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

Obtiene información acerca del rendimiento de los semáforos del sistema.

### <a name="prototype"></a>Prototipo

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento de todos los semáforos del sistema.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **puts**: puntero al destino del número total de solicitudes Put realizadas en todos los semáforos.
- **gets**: puntero al destino del número total de solicitudes Get realizadas en todos los semáforos.
- **suspensions**: puntero al destino del número total de suspensiones de los subprocesos de todos los semáforos.
- **timeouts**: puntero al destino del número total de tiempos de espera de suspensión de los subprocesos de todos los semáforos.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): obtención del rendimiento del sistema.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

Da prioridad a un semáforo en la lista de suspensiones.

### <a name="prototype"></a>Prototipo

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Descripción

Este servicio coloca el subproceso de prioridad más alta suspendido para una instancia del semáforo al principio de la lista de suspensiones. Todos los demás subprocesos permanecen en el mismo orden FIFO en el que se suspendieron.

### <a name="parameters"></a>Parámetros

- **semaphore_ptr**: puntero a un semáforo creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): semáforo clasificado correctamente.
- **TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo de recuento no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_put

## <a name="tx_semaphore_put"></a>tx_semaphore_put

Coloca una instancia en el semáforo de recuento.

### <a name="prototype"></a>Prototipo

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Descripción

Este servicio coloca una instancia en el semáforo de recuento especificado, lo que en realidad incrementa el semáforo de recuento en uno.

> [!NOTE]
> *Si se llama a este servicio cuando el semáforo es todo unos (OxFFFFFFFF), la nueva operación Put hará que el semáforo se restablezca a cero.*

### <a name="parameters"></a>Parámetros

- **semaphore_ptr**: puntero al bloque de control del semáforo de recuento creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): semáforo colocado correctamente.
- **TX_SEMAPHORE_ERROR** (0x0C): puntero al semáforo de recuento no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a>Consulte también

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_get
- tx_semaphore_put_notify

## <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

Notifica a la aplicación cuando se coloca el semáforo.

### <a name="prototype"></a>Prototipo

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se coloca el semáforo especificado. La aplicación define el procesamiento de la devolución de llamada de notificación.

> [!NOTE]
> *La devolución de llamada de notificación del semáforo de la aplicación no puede llamar a ninguna API de ThreadX con una opción de suspensión.*

### <a name="parameters"></a>Parámetros

- **semaphore_ptr**: puntero a un semáforo creado previamente.
- **semaphore_put_notify**: puntero a la función de notificación de colocación del semáforo de la aplicación. Si este valor es TX_NULL, la notificación se deshabilita.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): notificación de colocación del semáforo registrada correctamente.
- **TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema se compiló con las funcionalidades de notificación deshabilitadas.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put

## <a name="tx_thread_create"></a>tx_thread_create

Crea un subproceso de aplicación.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio crea un subproceso de aplicación que inicia la ejecución en la función de entrada de tarea especificada. Entre los atributos especificados por los parámetros de entrada se encuentran la pila, la prioridad, el umbral de adelantamiento y la porción de tiempo. Además, también se especifica el estado de ejecución inicial del subproceso.

**Parámetros**

- **thread_ptr**: puntero a un bloque de control del subproceso.
- **name_ptr**: puntero al nombre del subproceso.
- **entry_function**: especifica la función de C inicial para la ejecución del subproceso. Cuando un subproceso vuelve de esta función de entrada, se le asigna un estado *completado* y se suspende indefinidamente.
- **entry_input**: valor de 32 bits que se pasa a la función de entrada del subproceso cuando se ejecuta por primera vez. Exclusivamente la aplicación determina el uso de esta entrada.
- **stack_start**: dirección de inicio del área de memoria de la pila.
- **stack_size**: número de bytes en el área de memoria de la pila. El área de la pila del subproceso debe ser lo suficientemente grande como para controlar el uso de la variable local y el anidamiento de llamadas de función en el peor de los casos.
- **priority**: prioridad numérica del subproceso. Los valores válidos oscilan entre 0 y (TX_MAX_PRIORITES-1), donde un valor de 0 representa la prioridad más alta.
- **preempt_threshold**: nivel de prioridad más alto (0 a (TX_MAX_PRIORITIES-1)) de adelantamiento deshabilitado. Solo se permite que prioridades superiores a este nivel adelanten a este subproceso. Este valor debe ser menor o igual que la prioridad especificada. Un valor igual a la prioridad del subproceso deshabilita el umbral de adelantamiento.
- **time_slice**: número de tics de temporizador que este subproceso puede ejecutar antes de que otros subprocesos preparados con la misma prioridad tengan la posibilidad de ejecutarse. Tenga en cuenta que, si se usa el umbral de adelantamiento, se deshabilitan las porciones de tiempo. Los valores de porción de tiempo válidos se sitúan entre 1 y 0xFFFFFFFF (ambos incluidos). Un valor de **TX_NO_TIME_SLICE** (un valor de 0) deshabilita las porciones de tiempo de este subproceso.

  > [!NOTE]
  > *El uso de porciones de tiempo provoca una ligera sobrecarga del sistema. Dado que solo son útiles en los casos en los que varios subprocesos comparten la misma prioridad, no se debe asignar una porción de tiempo a los subprocesos que tienen una prioridad única.*

- **auto_start**: especifica si el subproceso se inicia inmediatamente o se coloca en un estado suspendido. Las opciones válidas son **TX_AUTO_START** (0x01) y **TX_DONT_START** (0x00). Si se especifica TX_DONT_START, la aplicación debe llamar posteriormente a tx_thread_resume para que se ejecute el subproceso.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): subproceso creado correctamente.
- **TX_THREAD_ERROR** (0x0E): puntero de control del subproceso no válido. El puntero tiene un valor NULL o el subproceso ya se ha creado.
- **TX_PTR_ERROR** (0x03): la dirección de inicio del punto de entrada o del área de la pila no es válida; normalmente, es NULL.
- **TX_SIZE_ERROR** (0x05): el tamaño del área de la pila no es válido. Los subprocesos deben tener al menos **TX_MINIMUM_STACK** bytes para ejecutarse.
- **TX_PRIORITY_ERROR** (0x0F): prioridad del subproceso no válida. Es un valor fuera del rango de (0 a (TX_MAX_PRIORITIES-1)).
- **TX_THRESH_ERROR** (0x18): el umbral de adelantamiento especificado no es válido. Este valor debe ser una prioridad válida menor o igual que la prioridad inicial del subproceso.
- **TX_START_ERROR** (0x10): selección de inicio automático no válida.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_delete"></a>tx_thread_delete

Elimina un subproceso de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina el subproceso de aplicación especificado. Dado que el subproceso especificado debe estar en un estado finalizado o completado, no se puede llamar a este servicio desde un subproceso que intente eliminarse a sí mismo.

> [!NOTE]
> *Es responsabilidad de la aplicación administrar el área de memoria asociada a la pila del subproceso, que está disponible una vez que se complete este servicio. Además, la aplicación debe impedir el uso de un subproceso eliminado.*

### <a name="parameters"></a>Parámetros

- **thread_ptr**: puntero a un subproceso de aplicación creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): subproceso eliminado correctamente.
- **TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.
- **TX_DELETE_ERROR** (0x11): el subproceso especificado no se encuentra en un estado finalizado o completado.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

Notifica a la aplicación la entrada y salida de un subproceso.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada de notificación a la que se llama cada vez que se entra o sale del subproceso especificado. La aplicación define el procesamiento de la devolución de llamada de notificación.

> [!NOTE]
> La devolución de llamada de notificación de entrada o salida del subproceso de la aplicación no puede llamar a ninguna API de ThreadX con una opción de suspensión.

### <a name="parameters"></a>Parámetros

- **thread_ptr**: puntero a un subproceso creado previamente.
- **entry_exit_notify**: puntero a la función de notificación de entrada o salida del subproceso de la aplicación. El segundo parámetro para la función de notificación de entrada o salida designa si hay una entrada o una salida. El valor **TX_THREAD_ENTRY** (0x00) indica que se entró en el subproceso, mientras que el valor **TX_THREAD_EXIT** (0x01) indica que se salió de él. Si este valor es **TX_NULL**, la notificación se deshabilita.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): registro correcto de la función de notificación de entrada o salida del subproceso.
- **TX_THREAD_ERROR** (0x0E): puntero del subproceso no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema se compiló con las funcionalidades de notificación deshabilitadas.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_identify"></a>tx_thread_identify

Recupera un puntero al subproceso que se está ejecutando actualmente.

### <a name="prototype"></a>Prototipo

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a>Descripción

Este servicio devuelve un puntero al subproceso que se está ejecutando actualmente. Si no se está ejecutando ningún subproceso, este servicio devuelve un puntero con un valor null.

> [!NOTE]
> *Si se llama a este servicio desde un ISR, el valor devuelto representa el subproceso que se ejecuta antes que el controlador de interrupción en ejecución.*

### <a name="parameters"></a>Parámetros

Ninguno

### <a name="retuen-values"></a>Valores devueltos

- **thread pointer**: puntero al subproceso que se está ejecutando actualmente. Si no se está ejecutando ningún subproceso, el valor devuelto es **TX_NULL**.

### <a name="allowed-from"></a>Permitido desde

Subprocesos e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

TX_THREAD *my_thread_ptr;

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

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_info_get"></a>tx_thread_info_get

Recupera información acerca de un subproceso.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio recupera información sobre el subproceso especificado.

### <a name="parameters"></a>Parámetros
- **thread_ptr**: puntero a un bloque de control del subproceso.
- **name**: puntero al destino del puntero al nombre del subproceso.
- **state**: puntero al destino del estado de ejecución actual del subproceso. Los valores posibles son los siguientes.
    - **TX_READY** (0x00)
    - **TX_COMPLETED** (0x01)
    - **TX_TERMINATED** (0x02)
    - **TX_SUSPENDED** (0x03)
    - **TX_SLEEP** (0x04)
    - **TX_QUEUE_SUSP** (0x05)
    - **TX_SEMAPHORE_SUSP** (0x06)
    - **TX_EVENT_FLAG** (0x07)
    - **TX_BLOCK_MEMORY** (0x08)
    - **TX_BYTE_MEMORY** (0x09)
    - **TX_MUTEX_SUSP** (0x0D)  

- **run_count**: puntero al destino del recuento de ejecuciones del subproceso.
- **priority**: puntero al destino de la prioridad del subproceso.
- **preemption_threshold**: puntero al destino del umbral de adelantamiento del subproceso.
**time_slice**: puntero al destino de la porción de tiempo del subproceso.
**next_thread**: puntero al destino del siguiente puntero de subproceso creado.

**suspended_thread**: puntero al destino del puntero al siguiente subproceso en la lista de suspensiones.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): información del subproceso recuperada correctamente.
- **TX_THREAD_ERROR** (0x0E): puntero de control del subproceso no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

Obtiene información acerca del rendimiento de un subproceso.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento del subproceso especificado.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros
- **thread_ptr**: puntero a un subproceso creado previamente.
- **resumptions**: puntero al destino del número de reanudaciones de este subproceso.
- **suspensions**: puntero al destino del número de suspensiones de este subproceso.
- **solicited_preemptions**: puntero al destino del número de adelantamientos como resultado de una llamada a un servicio de la API de ThreadX realizada por este subproceso.
- **interrupt_preemptions**: puntero al destino del número de adelantamientos de este subproceso como resultado del procesamiento de las interrupciones.
- **priority_inversions**: puntero al destino del número de inversiones de prioridad de este subproceso.
- **time_slices**: puntero al destino del número de porciones de tiempo de este subproceso.
- **relinquishes**: puntero al destino del número de renuncias de subproceso realizadas por este subproceso.
- **timeouts**: puntero al destino del número de tiempos de espera de suspensión en este subproceso.
- **wait_aborts**: puntero al destino del número de anulaciones de espera realizadas en este subproceso.
- **last_preempted_by**: puntero al destino del puntero del subproceso que ha adelantado por última vez a este subproceso.

> [!NOTE]
> *La especificación de un valor TX_NULL para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento del subproceso obtenido correctamente.
- **TX_PTR_ERROR** (0x03): puntero del subproceso no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

Obtiene información acerca del rendimiento de los subprocesos del sistema.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento de todos los subprocesos del sistema.

*La biblioteca y la aplicación de ThreadX se deben compilar con el servicio*

***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros

- **resumptions**: puntero al destino del número total de reanudaciones de los subprocesos.
- **suspensions**: puntero al destino del número total de suspensiones de los subprocesos.
- **solicited_preemptions**: puntero al destino del número total de adelantamientos de los subprocesos como resultado de una llamada de un subproceso a un servicio de la API de ThreadX.
- **interrupt_preemptions**: puntero al destino del número total de adelantamientos de los subprocesos como resultado del procesamiento de interrupciones.
- **priority_inversions**: puntero al destino del número total de inversiones de prioridad de los subprocesos.
- **time_slices**: puntero al destino del número total de porciones de tiempo de los subprocesos.
- **relinquishes**: puntero al destino del número total de renuncias de los subprocesos.
- **timeouts**: puntero al destino del número total de tiempos de espera de suspensión de los subprocesos.
- **wait_aborts**: puntero al destino del número total de anulaciones de espera de los subprocesos.
- **non_idle_returns**: puntero al destino del número de veces que un subproceso vuelve al sistema cuando hay otro subproceso preparado para ejecutarse.
- **idle_returns**: puntero al destino del número de veces que un subproceso vuelve al sistema cuando no hay otro subproceso preparado para ejecutarse (sistema inactivo).

> [!NOTE]
> *La especificación de un valor **TX_NULL** para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento del sistema del subproceso obtenido correctamente.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

Cambia el umbral de adelantamiento de un subproceso de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a>Descripción

Este servicio cambia el umbral de adelantamiento del subproceso especificado. El umbral de adelantamiento impide que los subprocesos con un valor igual o inferior a este umbral adelanten al subproceso especificado.

>[!NOTE]
> *Al usar el umbral de adelantamiento, se deshabilitan las porciones de tiempo para el subproceso especificado.*

### <a name="parameters"></a>Parámetros
- **thread_ptr**: puntero a un subproceso de aplicación creado previamente.
- **new_threshold**: nuevo nivel de prioridad del umbral de adelantamiento (0 a (TX_MAX_PRIORITIES-1)).
- **old_threshold**: puntero a una ubicación para devolver el umbral de adelantamiento anterior.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): umbral de adelantamiento cambiado correctamente.
- **TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.
- **TX_THRESH_ERROR** (0X18): el nuevo umbral de adelantamiento especificado no es una prioridad de subproceso válida (un valor distinto de (0 a (**TX_MAX_PRIORITIES**-1)) o es mayor que (prioridad inferior) que la prioridad actual del subproceso.
- **TX_PTR_ERROR** (0x03): puntero no válido a la ubicación de almacenamiento del umbral de adelantamiento anterior.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_priority_change"></a>tx_thread_priority_change

Cambia la prioridad de un subproceso de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a>Descripción

Este servicio cambia la prioridad del subproceso especificado. Las prioridades válidas oscilan entre 0 y (TX_MAX_PRIORITES-1), donde 0 representa el nivel de prioridad más alto.

> [!IMPORTANT]
> *El umbral de adelantamiento del subproceso especificado se establece automáticamente en la nueva prioridad. Si se desea un nuevo umbral, se debe usar el servicio ***tx_thread_preemption_change** _ después de esta llamada.

### <a name="parameters"></a>Parámetros

- **thread_ptr**: puntero a un subproceso de aplicación creado previamente.
- **new_priority**: nuevo nivel de prioridad del subproceso (0 a (TX_MAX_PRIORITIES-1)).
- **old_priority**: puntero a una ubicación para devolver la prioridad anterior del subproceso.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0X00): prioridad cambiada correctamente.
- **TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.
- **TX_PRIORITY_ERROR** (0x0F): la nueva prioridad especificada no es válida (un valor distinto de (0 a (TX_MAX_PRIORITIES-1)).
- **TX_PTR_ERROR** (0x03): puntero no válido a la ubicación de almacenamiento de la prioridad anterior.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

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
### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_relinquish"></a>tx_thread_relinquish

Cede el control a otros subprocesos de aplicación.

### <a name="prototype"></a>Prototipo

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a>Descripción

Este servicio cede el control del procesador a otros subprocesos preparados para ejecutarse con prioridad igual o superior.

> [!NOTE]
> *Además de ceder el control a los subprocesos con la misma prioridad, este servicio también se lo cede al subproceso de prioridad más alta que no se haya podido ejecutar debido a la configuración del umbral de adelantamiento del subproceso actual.*

### <a name="parameters"></a>Parámetros

Ninguno

### <a name="return-values"></a>Valores devueltos

Ninguno

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="examples"></a>Ejemplos

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

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_reset"></a>tx_thread_reset

Restablece un subproceso.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Descripción

Este servicio restablece el subproceso especificado para que se ejecute en el punto de entrada definido al crearlo. El subproceso debe estar en un estado **TX_COMPLETED** o **TX_TERMINATED** para que se pueda restablecer.

> [!IMPORTANT]
> *Se debe reanudar el subproceso para que se pueda ejecutar de nuevo.*

### <a name="parameters"></a>Parámetros

- **thread_ptr**: puntero a un subproceso creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): subproceso restablecido correctamente.
- **TX_NOT_DONE** (0x20): el subproceso especificado no se encuentra en un estado **TX_COMPLETED** o **TX_TERMINATED**.
- **TX_THREAD_ERROR** (0x0E): puntero del subproceso no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

TX_THREAD my_thread;

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_resume"></a>tx_thread_resume

Reanuda un subproceso de aplicación suspendido.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Descripción

Este servicio reanuda o prepara para su ejecución un subproceso suspendido anteriormente mediante una llamada a ***tx_thread_suspend***. Además, este servicio reanuda los subprocesos que se crearon sin un inicio automático.

### <a name="parameters"></a>Parámetros

- **thread_ptr**: puntero a un subproceso de aplicación suspendido.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): subproceso reanudado correctamente.
- **TX_SUSPEND_LIFTED** (0x19): se elevó la suspensión retrasada establecida previamente.
- **TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.
- **TX_RESUME_ERROR** (0X12): el subproceso especificado no está suspendido o se suspendió previamente mediante un servicio distinto a **_tx_thread_suspend_**.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

TX_THREAD my_thread;

### <a name="example"></a>Ejemplo

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_sleep"></a>tx_thread_sleep

Suspende el subproceso actual durante el tiempo especificado.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a>Descripción

Este servicio hace que el subproceso que realiza la llamada se suspenda durante el número especificado de tics de temporizador. La cantidad de tiempo físico asociada a un tic de temporizador es específica de la aplicación. Solo se puede llamar a este servicio desde un subproceso de aplicación.

### <a name="parameters"></a>Parámetros

- **timer_ticks**: número de tics de temporizador para suspender el subproceso de la aplicación que realiza la llamada, comprendido entre 0 y 0xFFFFFFFF. Si se especifica 0, el servicio se devuelve inmediatamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): subproceso suspendido correctamente.
- **TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.
- **TX_CALLER_ERROR** (0x13): se llamó al servicio desde un elemento distinto de un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a>Consulte también

- tx_thread_create, tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_stack_error_notify"></a>tx_thread_stack_error_notify

Registra una devolución de llamada de notificación de error de la pila de subprocesos.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada de notificación para controlar los errores de la pila de un subproceso. Cuando ThreadX detecta un error en la pila de un subproceso durante la ejecución, llamará a esta función de notificación para procesarlo. La aplicación define al completo el procesamiento del error. Es posible que se realice cualquier acción, desde suspender el subproceso infractor hasta restablecer todo el sistema.

> [!IMPORTANT]
> *La biblioteca ThreadX se debe compilar con el servicio* **TX_ENABLE_STACK_CHECKING** *definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros
- **error_handler**: puntero a la función de control de errores de pila de la aplicación. Si este valor es TX_NULL, la notificación se deshabilita.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): subproceso restablecido correctamente.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_suspend"></a>tx_thread_suspend

Suspende un subproceso de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Descripción

Este servicio suspende el subproceso de aplicación especificado. Un subproceso puede llamar a este servicio para suspenderse a sí mismo.

> [!NOTE]
> *Si el subproceso especificado ya está suspendido por otro motivo, esta suspensión se mantiene internamente hasta que se levanta la anterior. Cuando esto sucede, se realiza esta suspensión incondicional del subproceso especificado. Ninguna otra solicitud de suspensión incondicional tendrá efecto.*

Tras su suspensión, el subproceso debe reanudarse mediante ***tx_thread_resume*** para volver a ejecutarse.

### <a name="parameters"></a>Parámetros

- **thread_ptr**: puntero a un subproceso de aplicación.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): subproceso suspendido correctamente.
- **TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.
- **TX_SUSPEND_ERROR** (0x14): el subproceso especificado se encuentra en un estado finalizado o completado.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_terminate"></a>tx_thread_terminate

Finaliza un subproceso de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Descripción

Este servicio finaliza el subproceso de aplicación especificado, independientemente de si está suspendido o no. Un subproceso puede llamar a este servicio para finalizarse a sí mismo.

> [!NOTE]
> *Es responsabilidad de la aplicación asegurarse de que el subproceso está en un estado adecuado para la terminación. Por ejemplo, un subproceso no debe terminarse durante el procesamiento crítico de aplicaciones o dentro de otros componentes de middleware, donde podría dejar dicho procesamiento en un estado desconocido.*

> [!IMPORTANT]
> *Tras su finalización, el subproceso debe restablecerse para que se pueda ejecutar de nuevo.*

### <a name="parameters"></a>Parámetros

- **thread_ptr**: puntero a un subproceso de aplicación.

### <a name="return-values"></a>Valores devueltos
- **TX_SUCCESS** (0x00): subproceso terminado correctamente.
- **TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

Sí

### <a name="example"></a>Ejemplo

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a>Consulte también

- tx_thread_create tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

Cambia la porción de tiempo de un subproceso de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a>Descripción

Este servicio cambia la porción de tiempo del subproceso de aplicación especificado. Al seleccionar una porción de tiempo para un subproceso, se asegura de que no se ejecutará más que el número especificado de tics de temporizador antes de que otros subprocesos con prioridades iguales o superiores tengan la posibilidad de ejecutarse.

> [!NOTE]
> *Al usar el umbral de adelantamiento, se deshabilitan las porciones de tiempo para el subproceso especificado.*

### <a name="parameters"></a>Parámetros

- **thread_ptr**: puntero a un subproceso de aplicación.
- **new_time_slice**: nuevo valor de porción de tiempo. Entre los valores válidos se incluyen TX_NO_TIME_SLICE y valores numéricos del 1 a 0xFFFFFFFF.
- **old_time_slice**: puntero a la ubicación para almacenar el valor de la porción de tiempo anterior del subproceso especificado.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): porción de tiempo cambiada correctamente.
- **TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.
- **TX_PTR_ERROR** (0x03): puntero no válido a la ubicación de almacenamiento de la porción de tiempo anterior.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos y temporizadores

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_wait_abort

## <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

Anula la suspensión de un subproceso especificado.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Descripción

Este servicio anula cualquier tipo de suspensión de objeto del subproceso especificado. Si se anula la espera, se devuelve un valor **TX_WAIT_ABORTED** desde el servicio en el que el subproceso estaba esperando.

> [!NOTE]
> *Este servicio no libera la suspensión explícita realizada por el servicio tx_thread_suspend.*

### <a name="parameters"></a>Parámetros

- **thread_ptr**: puntero a un subproceso de aplicación creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS**: (0x00) espera del subproceso anulada correctamente.
- **TX_THREAD_ERROR** (0x0E): puntero del subproceso de aplicación no válido.
- **TX_WAIT_ABORT_ERROR** (0x1B): el subproceso especificado no está en estado de espera.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible
Sí

### <a name="example"></a>Ejemplo

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a>Consulte también

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change

## <a name="tx_time_get"></a>tx_time_get

Recuperar la hora actual

Temporizadores de aplicación

### <a name="prototype"></a>Prototipo

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a>Descripción

Este servicio devuelve el contenido del reloj interno del sistema. Cada tic del temporizador aumenta el reloj interno del sistema en uno. El reloj del sistema se establece en cero durante la inicialización y se puede cambiar a un valor específico mediante el servicio ***tx_time_set***.

> [!NOTE]
> *El tiempo real que representa cada tic del temporizador es específico de la aplicación.*

**Parámetros**

Ninguno

### <a name="return-values"></a>Valores devueltos

- **system clock ticks**: valor del reloj interno del sistema de ejecución libre.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible
No

### <a name="example"></a>Ejemplo

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a>Consulte también

- tx_time_set

## <a name="tx_time_set"></a>tx_time_set

Establece la hora actual.

### <a name="prototype"></a>Prototipo

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a>Descripción

Este servicio establece el reloj interno del sistema en el valor especificado. Cada tic del temporizador aumenta el reloj interno del sistema en uno.

> [!NOTE]
> *El tiempo real que representa cada tic del temporizador es específico de la aplicación.*

### <a name="parameters"></a>Parámetros

- **new_time**: hora nueva que se va a establecer en el reloj del sistema. Los valores válidos oscilan entre 0 y 0xFFFFFFFF.

### <a name="return-values"></a>Valores devueltos

Ninguno

### <a name="allowed-from"></a>Permitido desde

Subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a>Consulte también

- tx_time_get

## <a name="tx_timer_activate"></a>tx_timer_activate

Activa un temporizador de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Descripción

Este servicio activa el temporizador de aplicación especificado. Las rutinas de expiración de los temporizadores que expiran al mismo tiempo se ejecutan en el orden en el que se activaron.

> [!NOTE]
> *Un temporizador monoestable expirado se debe restablecer mediante* ***tx_timer_change** _ _para que se pueda volver a activar.*

### <a name="parameters"></a>Parámetros

- **timer_ptr**: puntero a un temporizador de aplicación creado previamente.

**Valores devueltos**

- **TX_SUCCESS** (0x00): temporizador de aplicación activado correctamente.
- **TX_TIMER_ERROR** (0x15): puntero de temporizador de aplicación no válido.
- **TX_ACTIVATE_ERROR** (0x17): el temporizador ya estaba activo o es un temporizador monoestable que ya ha expirado.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a>Consulte también

- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_change"></a>tx_timer_change

Cambia un temporizador de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a>Descripción

Este servicio cambia las características de expiración del temporizador de aplicación especificado. El temporizador debe desactivarse antes de llamar a este servicio.

> [!NOTE]
> *Es necesaria una llamada al servicio* ***tx_timer_activate_** _ _tras este servicio para poder iniciar el temporizador de nuevo.*

### <a name="parameters"></a>Parámetros

- **timer_ptr**: puntero a un bloque de control del temporizador.
- **initial_ticks**: especifica el número inicial de tics para la expiración del temporizador. Los valores válidos oscilan entre 1 y 0xFFFFFFFF.
- **reschedule_ticks**: especifica el número de tics para todas las expiraciones del temporizador después de la primera. Un cero para este parámetro convierte el temporizador en *monoestable*. En cambio, para los temporizadores periódicos, los valores válidos oscilan entre 1 y 0xFFFFFFFF.

> [!NOTE]
> *Un temporizador monoestable expirado se debe restablecer mediante*
***tx_timer_change** _ _para que se pueda volver a activar.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): temporizador de aplicación cambiado correctamente.
- **TX_TIMER_ERROR** (0x15): puntero de temporizador de aplicación no válido.
- **TX_TICK_ERROR** (0x16): el valor (cero) proporcionado para los tics iniciales no es válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_timer_activate
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_create"></a>tx_timer_create

Crea un temporizador de aplicación.

### <a name="prototype"></a>Prototipo

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

### <a name="description"></a>Descripción

Este servicio crea un temporizador de aplicación periódico con la función de expiración especificada.

### <a name="parameters"></a>Parámetros

- **timer_ptr**: puntero a un bloque de control del temporizador.
- **name_ptr**: puntero al nombre del temporizador.
- **expiration_function**: función de la aplicación que se va a llamar cuando expire el temporizador.
- **expiration_input**: entrada que se va a pasar a la función de expiración cuando expire el temporizador.
- **initial_ticks**: especifica el número inicial de tics para la expiración del temporizador. Los valores válidos oscilan entre 1 y 0xFFFFFFFF.
- **reschedule_ticks**: especifica el número de tics para todas las expiraciones del temporizador después de la primera. Un cero para este parámetro convierte el temporizador en *monoestable*. En cambio, para los temporizadores periódicos, los valores válidos oscilan entre 1 y 0xFFFFFFFF.

  > [!NOTE]
  > *Cuando un temporizador monoestable expira, se debe restablecer mediante tx_timer_change para que se pueda volver a activar.*

- **auto_activate**: determina si el temporizador se activa automáticamente durante la creación. Si este valor es **TX_AUTO_ACTIVATE** (0x01), el temporizador se activa. De lo contrario, si se selecciona el valor **TX_NO_ACTIVATE** (0x00), el temporizador se crea en un estado no activo. En este caso, es necesario llamar después al servicio **_tx_timer_activate_** para que el temporizador se inicie.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): temporizador de aplicación creado correctamente.
- **TX_TIMER_ERROR** (0x15): puntero del temporizador de aplicación no válido. El puntero tiene un valor NULL o el temporizador ya se ha creado.
- **TX_TICK_ERROR** (0x16): el valor (cero) proporcionado para los tics iniciales no es válido.
- **TX_ACTIVATE_ERROR** (0x17): la activación seleccionada no es válida.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_timer_activate
- tx_timer_change
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_deactivate"></a>tx_timer_deactivate

Desactiva un temporizador de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Descripción

Este servicio desactiva el temporizador de aplicación especificado. Si el temporizador ya está desactivado, este servicio no tiene ningún efecto.

### <a name="parameters"></a>Parámetros

- **timer_ptr**: puntero a un temporizador de aplicación creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): temporizador de aplicación desactivado correctamente.
- **TX_TIMER_ERROR** (0x15): puntero del temporizador de aplicación no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a>Consulte también

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_delete"></a>tx_timer_delete

Elimina un temporizador de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina el temporizador de aplicación especificado.

> [!NOTE]
> *Es responsabilidad de la aplicación impedir el uso de un temporizador eliminado.*

### <a name="parameters"></a>Parámetros

- **timer_ptr**: puntero a un temporizador de aplicación creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): temporizador de aplicación eliminado correctamente.
- **TX_TIMER_ERROR** (0x15): puntero del temporizador de aplicación no válido.
- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a>Consulte también

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_info_get"></a>tx_timer_info_get

Recupera información acerca de un temporizador de aplicación.

### <a name="prototype"></a>Prototipo

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el temporizador de aplicación especificado.

### <a name="parameters"></a>Parámetros

- **timer_ptr**: puntero a un temporizador de aplicación creado previamente.
- **name**: puntero al destino del puntero al nombre del temporizador.
- **active**: puntero al destino de la indicación de temporizador activo. Si el temporizador está inactivo o se llama a este servicio desde el propio temporizador, se devuelve un valor **TX_FALSE**. En cambio, si el temporizador está activo, se devuelve un valor **TX_TRUE**.
- **remaining_ticks**: puntero al destino del número de tics de temporizador que quedan antes de que expire.
- **reschedule_ticks**: puntero al destino del número de tics de temporizador que se usarán para volver a programarlo automáticamente. Si el valor es cero, el temporizador es monoestable y no se volverá a programar.
- **next_timer**: puntero al destino del puntero del siguiente temporizador de aplicación creado.

> [!NOTE]
> *La especificación de un valor **TX_NULL** para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): información del temporizador recuperada correctamente.
- **TX_TIMER_ERROR** (0x15): puntero del temporizador de aplicación no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="preemption-possible"></a>Adelantamiento posible

No

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

Obtiene información acerca del rendimiento de un temporizador.

### <a name="prototype"></a>Prototipo

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento del temporizador de aplicación especificado.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _definido para que devuelva información sobre el rendimiento.*

### <a name="parameters"></a>Parámetros
- **timer_ptr**: puntero a un temporizador creado previamente.
- **activates**: puntero al destino del número de solicitudes de activación realizadas en este temporizador.
- **reactivates**: puntero al destino del número de reactivaciones automáticas realizadas en este temporizador periódico.
- **deactivates**: puntero al destino del número de solicitudes de desactivación realizadas en este temporizador.
- **expirations**: puntero al destino del número de expiraciones de este temporizador.
- **expiration_adjusts**: puntero al destino del número de ajustes de expiración internos realizados en este temporizador. Estos ajustes se realizan en el procesamiento de interrupciones del temporizador para los temporizadores mayores que el tamaño predeterminado de la lista de temporizadores (de manera predeterminada, los temporizadores con expiraciones superiores a 32 tics).

> [NOTA] *La especificación de un valor TX_NULL para cualquier parámetro indica que el parámetro no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): rendimiento del temporizador obtenido correctamente.
- **TX_PTR_ERROR** (0x03): puntero del temporizador no válido.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

Obtiene información acerca del rendimiento de los temporizadores del sistema.

### <a name="prototype"></a>Prototipo

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a>Descripción

Este servicio recupera información sobre el rendimiento de todos los temporizadores de aplicación del sistema.

> [!IMPORTANT]
> *La biblioteca y la aplicación ThreadX se deben compilar con el servicio* **TX_TIMER_ENABLE_PERFORMANCE_INFO**  *definido para que devuelva información sobre el rendimiento.*

**Parámetros**

- **activates**: puntero al destino del número total de solicitudes de activación realizadas en todos los temporizadores.
- **reactivates**: puntero al destino del número total de reactivaciones automáticas realizadas en todos los temporizadores periódicos.
- **deactivates**: puntero al destino del número total de solicitudes de desactivación realizadas en todos los temporizadores.
- **expirations**: puntero al destino del número total de expiraciones de todos los temporizadores.
- **expiration_adjusts**: puntero al destino del número total de ajustes de expiración internos realizados en todos los temporizadores. Estos ajustes se realizan en el procesamiento de interrupciones del temporizador para los temporizadores mayores que el tamaño predeterminado de la lista de temporizadores (de manera predeterminada, los temporizadores con expiraciones superiores a 32 tics).

> [!NOTE]
> *La especificación de un valor **TX_NULL** para cualquier parámetro indica que este no es necesario.*

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS**: (0x00): rendimiento del sistema del temporizador obtenido correctamente.
- **TX_FEATURE_NOT_ENABLED** (0XFF): el sistema no se compiló con la información de rendimiento habilitada.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

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

### <a name="see-also"></a>Consulte también

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
