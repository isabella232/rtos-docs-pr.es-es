---
title: 'Capítulo 4: API de módulo'
author: philmea
ms.author: philmea
description: Este artículo es un resumen de las API adicionales disponibles para un módulo.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1c7590d0ccddc606a6cacdfeb3b3a99631e125554b524c4ce65c8154e65a20ee
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799139"
---
# <a name="chapter-4---module-apis"></a>Capítulo 4: API de módulo

## <a name="summary-of-module-apis"></a>Resumen de las API de un módulo

Hay varias funciones API adicionales disponibles para un módulo, como se indica a continuación:

- ***txm_module_application_request**: solicitud específica de una aplicación al código residente*.
- ***txm_module_object_allocate**: asignar memoria fuera del módulo para el objeto*.
- ***txm_module_object_deallocate**: desasignar memoria de objeto asignada previamente*.
- ***txm_module_object_pointer_get**: buscar un objeto del sistema y recuperar un puntero de objeto*.
- ***txm_module_object_pointer_get_extended**: buscar un objeto del sistema y recuperar un puntero de objeto, seguridad de la longitud del nombre*.

## <a name="return-values"></a>Valores devueltos

Se devuelven códigos de error adicionales para algunas API de Azure RTOS. Estos códigos de error adicionales se definen de la siguiente manera:

- **TXM_MODULE_INVALID_PROPERTIES** (0xF3): indica que el módulo no tiene las propiedades correctas para realizar una llamada de API. Por ejemplo, llamar a las API de seguimiento en modo de usuario.
- **TXM_MODULE_INVALID_MEMORY** (0xF4): indica que la memoria suministrada por el módulo no es válida o está en una ubicación no válida. Por ejemplo, en los módulos protegidos en memoria, no se permite que los bloques de control de objetos estén ubicados en la memoria a la que puede tener acceso el módulo.
- **TXM_MODULE_INVALID_CALLBACK** (0xF5): la devolución de llamada especificada en la API está fuera del intervalo del código del módulo y, por lo tanto, no es válida.

---

## <a name="txm_module_application_request"></a>txm_module_application_request

Solicitud específica de la aplicación para el código residente.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a>Descripción

Este servicio realiza la solicitud especificada a la parte residente de la aplicación. Se supone que la estructura de la solicitud está preparada antes de la llamada. El procesamiento real de la solicitud tiene lugar en el código residente en la función ***_txm_module_manager_application_request***. De forma predeterminada, esta función se deja vacía y está diseñada para que la modifique el desarrollador de la aplicación residente.

### <a name="input-parameters"></a>Parámetros de entrada

- **request** Id. de solicitud (aplicación definida)
- **param_1** Primer parámetro
- **param_2** Segundo parámetro
- **param_3** Tercer parámetro

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Solicitud correcta.
- **TX_NOT_AVAILABLE** (0x1D) La solicitud no es compatible con el código residente.

### <a name="allowed-from"></a>Permitido desde

Subprocesos de módulo

### <a name="example"></a>Ejemplo

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a>txm_module_object_allocate

Asigne memoria en el grupo de objetos (creado por la aplicación residente) para un bloque de control de objeto de módulo.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a>Descripción

Este servicio asigna memoria para un objeto de módulo de la memoria fuera del módulo, lo que ayuda a evitar que el código del módulo dañe el bloque de control de objetos. En los sistemas protegidos en memoria, todos los bloques de control de objetos se deben asignar con esta API para poder crearlos.

### <a name="input-parameters"></a>Parámetros de entrada

- **object_ptr** Destino del puntero de objeto en una asignación correcta.
- **object_size** Tamaño en bytes del objeto que se va a asignar.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Asignación correcta de objeto.
- **TX_NO_MEMORY** (0x10) No hay suficiente memoria.
- **TX_NOT_AVAILABLE** (0x1D) El administrador de módulos no ha creado un grupo de objetos del que asignar

### <a name="allowed-from"></a>Permitido desde

Subprocesos de módulo

### <a name="example"></a>Ejemplo

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a>Vea también

- txm_module_object_deallocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_deallocate"></a>txm_module_object_deallocate

Desasigne la memoria de objetos previamente asignados.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a>Descripción

***Este servicio está en desuso porque ya no es necesario***.

La memoria que se asignó previamente a través de *txm_module_object_allocate* ***_ se ha desasignado en el \__servicio de eliminación*** _* _tx_.

### <a name="input-parameters"></a>Parámetros de entrada

- **object_ptr** Puntero de objeto que se va a desasignar.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Asignación correcta de objeto.

### <a name="allowed-from"></a>Permitido desde

Subprocesos de módulo

### <a name="example"></a>Ejemplo

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a>Vea también

- txm_module_object_allocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_pointer_get"></a>txm_module_object_pointer_get

Busque un objeto del sistema y recupere un puntero de objeto.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el puntero de objeto de un tipo determinado con un nombre determinado. Si no se encuentra el objeto, se devuelve un error. De lo contrario, si se encuentra el objeto, la dirección de ese objeto se coloca en "object_ptr". Este puntero se puede usar para realizar llamadas de servicio de sistema, para interactuar con el código residente u otros módulos cargados en el sistema.

### <a name="input-parameters"></a>Parámetros de entrada

- **object_type** Tipo de objeto de ThreadX solicitado. Los tipos válidos son los siguientes:
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **name** Nombre de objeto específico de la aplicación tal y como se definió al crear el objeto.
- **object_ptr** Destino del puntero de objeto.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Obtención correcta de objeto.
- **TX_OPTION_ERROR** (0x08) Tipo de objeto no válido.
- **TX_PTR_ERROR** (0x03) Destino no válido.
- **TX_SIZE_ERROR** (0x05) Tamaño no válido.
- **TX_NO_INSTANCE** (0x0D) No se encontró el objeto.

### <a name="allowed-from"></a>Permitido desde

Subprocesos de módulo

### <a name="example"></a>Ejemplo

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>Vea también

- txm_module_manager_object_pointer_get_extended

---

## <a name="txm_module_object_pointer_get_extended"></a>txm_module_object_pointer_get_extended

Busque un objeto del sistema y recupere un puntero de objeto.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el puntero de objeto de un tipo determinado con un nombre determinado. Si no se encuentra el objeto, se devuelve un error. De lo contrario, si se encuentra el objeto, la dirección de ese objeto se coloca en "object_ptr". Este puntero se puede usar para realizar llamadas de servicio de sistema, para interactuar con el código residente u otros módulos cargados en el sistema.

### <a name="input-parameters"></a>Parámetros de entrada

- **object_type** Tipo de objeto de ThreadX solicitado. Los tipos válidos son los siguientes:
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **name** Nombre de objeto específico de la aplicación tal y como se definió al crear el objeto.
- **name_length** Longitud del nombre.
- **object_ptr** Destino del puntero de objeto.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Obtención correcta de objeto.
- **TX_OPTION_ERROR** (0x08) Tipo de objeto no válido.
- **TX_PTR_ERROR** (0x03) Destino no válido.
- **TX_SIZE_ERROR** (0x05) Tamaño no válido.
- **TX_NO_INSTANCE** (0x0D) No se encontró el objeto.

### <a name="allowed-from"></a>Permitido desde

Subprocesos de módulo

### <a name="example"></a>Ejemplo

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>Vea también

- txm_module_manager_object_pointer_get
