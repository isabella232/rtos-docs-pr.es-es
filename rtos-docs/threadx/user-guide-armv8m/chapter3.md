---
title: 'Capítulo 3: API de ThreadX para ARMv8-M'
description: En este capítulo se describe la descripción de los servicios de ThreadX específicos de ARMv8-M.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99633db55a5d93eb32ce4fb5429f3fe2f9ab5137cffc30b27982f702cece1ca5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791506"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a>Capítulo 3: API de ThreadX para ARMv8-M

Este capítulo contiene una descripción de los servicios de ThreadX específicos de ARMv8-M en orden alfabético. Los nombres de los servicios están diseñados de modo que todos los servicios similares están agrupados. En la sección "Valores devueltos" de las siguientes descripciones, los valores en **NEGRITA** no se ven afectados por la definición **TX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API. En cambio, los valores que no aparecen en negrita están completamente deshabilitados.

- [tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate): asigna una pila de subprocesos en la memoria segura.
- [tx_thread_secure_stack_free](#tx_thread_secure_stack_free): libera la pila de subprocesos en la memoria segura

## <a name="tx_thread_secure_stack_allocate"></a>tx_thread_secure_stack_allocate

Asigna una pila de subprocesos en la memoria segura.

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a>Descripción

Este servicio asigna una pila de stack_size bytes de tamaño en la memoria segura. Se debe llamar a esta función para cada subproceso que llame a funciones seguras.

### <a name="input-parameters"></a>Parámetros de entrada

- **thread_ptr**: puntero a un subproceso creado previamente.

- **stack_size**: tamaño de la pila segura.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): solicitud correcta.

- **TX_SIZE_ERROR** (0x05): tamaño de la pila fuera del intervalo.

- **TX_THREAD_ERROR** (0x0E): puntero del subproceso no válido.

- **TX_NO_MEMORY** (0x10): no se puede asignar memoria.

- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

- **TX_FEATURE_NOT_ENABLED** (0Xff): el sistema se compiló para ejecutarse en modo seguro.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a>Consulte también

tx_thread_secure_stack_free

##  <a name="tx_thread_secure_stack_free"></a>tx_thread_secure_stack_free

Libera la pila de subprocesos en la memoria segura. 

### <a name="prototype"></a>Prototipo

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Descripción

Este servicio libera la pila segura de un subproceso en la memoria segura. Se debe llamar a esta función si un subproceso tiene una pila segura y cuando el subproceso ya no necesita llamar a funciones seguras o se elimina el subproceso.

### <a name="input-parameters"></a>Parámetros de entrada

- **thread_ptr**: puntero a un subproceso creado previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): solicitud correcta.

- **TX_THREAD_ERROR** (0x0E): puntero del subproceso no válido.

- **TX_CALLER_ERROR** (0x13): autor de llamada de este servicio no válido.

- **TX_FEATURE_NOT_ENABLED** (0Xff): el sistema se compiló para ejecutarse en modo seguro.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a>Consulte también

tx_thread_secure_stack_allocate
