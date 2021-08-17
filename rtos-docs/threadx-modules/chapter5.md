---
title: 'Capítulo 5: API del administrador de módulos'
author: philmea
description: Este artículo es un resumen de las API del administrador de módulos disponibles para la parte residente de la aplicación.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8e4da0f9591fd0b5d6249292f00266d96ccb67923c42632a4cfd8c39fa1f129
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799122"
---
# <a name="chapter-5---module-manager-apis"></a>Capítulo 5: API del administrador de módulos

## <a name="summary-of-module-manager-apis"></a>Resumen de las API del administrador de módulos

Hay varias API adicionales disponibles para la parte residente de la aplicación, como se indica a continuación.

- ***txm_module_manager_external_memory_enable**: habilita acceso al módulo a un espacio de memoria compartido*.
- ***txm_module_manager_file_load**: carga el módulo desde el archivo a través de FileX*.
- ***txm_module_manager_in_place_load**: carga los datos del módulo, se ejecuta en contexto*.
- ***txm_module_manager_initialize**: inicializa el administrador de módulos*.
- ***txm_module_manager_mm_initialize**: inicializa el hardware de administración de memoria*.
- ***txm_module_manager_maximum_module_priority_set**: establece la prioridad de subprocesos máxima permitida en un módulo*.
- ***txm_module_manager_memory_fault_notify**: registra una devolución de llamada de aplicación en un error de memoria*.
- ***txm_module_manager_memory_load**: carga el módulo de la memoria*.
- ***txm_module_manager_object_pool_create**: crea un grupo de objetos para los módulos*.
- ***txm_module_manager_properties_get**: obtiene las propiedades del módulo*.
- ***txm_module_manager_start**: inicia la ejecución del módulo especificado*.
- ***txm_module_manager_stop**: detiene la ejecución del módulo especificado*.
- ***txm_module_manager_unload**: descarga el módulo*.

---

## <a name="txm_module_manager_external_memory_enable"></a>txm_module_manager_external_memory_enable

Habilitar el módulo para tener acceso a un espacio de memoria compartido

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a>Descripción

Este servicio crea una entrada en la tabla de hardware de administración de memoria para una región de memoria compartida a la que el módulo puede tener acceso.

### <a name="input-parameters"></a>Parámetros de entrada

- **module_instance** Puntero a la instancia del módulo.
- **start_address** Dirección inicial de la región de memoria compartida.
- **lenght** Longitud de la región de memoria compartida.
- **attributes** Atributos de la región de memoria (caché, lectura, escritura, etc.). Los atributos son específicos del puerto. Consulte el [apéndice](appendix.md) para ver el formato de los atributos.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Entrada de memoria creada correctamente.
- **TX_NOT_AVAILABLE** (0x1D) No se ha inicializado el administrador o la característica no está disponible.
- **TX_PTR_ERROR** (0x03) Instancia de módulo no válida.
- **TX_START_ERROR** (0x10) El módulo no está en estado cargado.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alineación de dirección inicial no válida.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Propiedades incompatibles.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a>txm_module_manager_file_load

Cargar el módulo desde el archivo a través de FileX.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a>Descripción

Este servicio carga la imagen binaria del módulo incluida en el archivo especificado en el área de memoria del módulo y la prepara para su ejecución. Se supone que el medio proporcionado ya está abierto.

> [!NOTE]
> El sistema FileX se emplea para cargar el archivo. Para habilitar el acceso de FileX, el módulo, la biblioteca de módulos, el administrador de módulos y la biblioteca de ThreadX (con los orígenes del administrador de módulos) deben compilarse con **FX_FILEX_PRESENT** definido en los proyectos.

### <a name="input-parameters"></a>Parámetros de entrada

- **module_instance** Puntero a la instancia del módulo.
- **module_name** Nombre del módulo.
- **media_ptr** Puntero a un elemento multimedia de FileX ya abierto.
- **file_name** Nombre del archivo binario del módulo.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Carga correcta del módulo.
- **TX_CALLER_ERROR** (0x13) Autor de llamada no válido.
- **TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.
- **TX_NO_MEMORY** (0x10) No hay suficiente memoria para cargar el módulo.
- **TX_NOT_DONE** (0x20) No se pudo abrir el elemento multimedia: no se encontró el archivo o el archivo no es válido.
- **TX_PTR_ERROR** (0x03) Instancia de módulo no válida.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alineación no válida.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) Ya se cargó el módulo.
- **TXM_MODULE_INVALID** (0xF2) | Preámbulo de módulo no válido.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Propiedades incompatibles.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>Vea también

- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_in_place_load"></a>txm_module_manager_in_place_load

Cargar solo los datos del módulo, ejecutar el módulo en la ubicación existente.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Descripción

Este servicio carga el área de datos del módulo solo en el área de memoria del módulo y lo prepara para su ejecución. La ejecución del código de módulo estará en contexto, es decir, desde el desplazamiento de dirección especificado por el preámbulo del módulo en la ubicación proporcionada.

### <a name="input-parameters"></a>Parámetros de entrada

- **module_instance** Puntero a la instancia del módulo.
- **module_name** Nombre del módulo.
- **location** Puntero al área de código del módulo, preámbulo primero.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Carga correcta del módulo.
- **TX_CALLER_ERROR** (0x13) Autor de llamada no válido.
- **TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.
- **TX_NO_MEMORY** (0x10) No hay suficiente memoria para cargar el módulo.
- **TX_PTR_ERROR** (0x03) Puntero, instancia de módulo o preámbulo de módulo no válidos.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alineación no válida.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) Ya se cargó el módulo.
- **TXM_MODULE_INVALID** (0xF2) Preámbulo de módulo no válido.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Propiedades incompatibles.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>Vea también

- txm_module_manager_file_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_initialize"></a>txm_module_manager_initialize

Inicializar el administrador de módulos.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a>Descripción

Este servicio inicializa los recursos internos del administrador de módulos, incluida el área de memoria que se usa para cargar los módulos.

### <a name="input-parameters"></a>Parámetros de entrada

- **module_memory_start** Puntero al inicio de la memoria del módulo.
- **module_memory_size** Tamaño en bytes de la memoria del módulo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Inicialización correcta.
- **TX_CALLER_ERROR** (0x13) Autor de llamada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a>Vea también

- txm_module_manager_object_pool_create

---

## <a name="txm_module_manager_initialize_mmu"></a>txm_module_manager_initialize_mmu

Inicializar el hardware de administración de memoria.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a>Descripción

Este servicio inicializa la MMU.

### <a name="input-parameters"></a>Parámetros de entrada

ninguno

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Inicialización correcta.
- **TX_CALLER_ERROR** (0x13) Autor de llamada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a>txm_module_manager_maximum_module_priority_set

Establecer la prioridad de subproceso máxima permitida en un módulo.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a>Descripción

Este servicio establece la prioridad de subproceso máxima permitida en un módulo.

### <a name="input-parameters"></a>Parámetros de entrada

- **module_instance** Puntero a la instancia del módulo.
- **priority** Prioridad máxima del subproceso.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Inicialización correcta.
- **TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.
- **TX_PTR_ERROR** (0x03) Instancia de módulo no válida.
- **TX_START_ERROR** (0x10) El módulo no está en estado cargado.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a>txm_module_manager_memory_fault_notify

Registrar una devolución de llamada de la aplicación en un error de memoria.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a>Descripción

Este servicio registra la función de devolución de llamada de notificación de errores de memoria de la aplicación especificada con el administrador de módulos. Si se produce un error de memoria, se llama a esta función con un puntero al subproceso infractor y la instancia de módulo correspondiente al subproceso infractor. El procesamiento del administrador de módulos finaliza automáticamente el subproceso infractor, pero deja los demás subprocesos del módulo sin tocar. Depende de la aplicación decidir qué hacer con el módulo asociado al error de memoria.

Vea el struct interno **_txm_module_manager_memory_fault_info** para obtener información específica sobre el propio error de memoria.

> [!NOTE]
> La función de devolución de llamada de notificación de error de memoria se ejecuta directamente desde la excepción de error de memoria, de modo que solo se puede llamar a las API de ThreadX que se permiten desde las rutinas de servicio de interrupción. Por lo tanto, para detener y descargar el módulo infractor, la devolución de llamada de notificación de aplicación debe enviar una señal a una tarea de aplicación para que el módulo se pueda detener y descargar.

### <a name="input-parameters"></a>Parámetros de entrada

- **notify_function** Puntero de función a la devolución de llamada de notificación de errores de memoria de la aplicación. Si se proporciona un valor NULL, se deshabilita la notificación de error de memoria.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Registro de la función de notificación correcto.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a>txm_module_manager_memory_load

Cargue el módulo desde la memoria.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Descripción

Este servicio carga el código y el área de datos del módulo en el área de memoria del módulo configurada por ***txm_module_manager_initialize*** y lo prepara para su ejecución.

### <a name="input-parameters"></a>Parámetros de entrada

- **module_instance** Puntero a la instancia del módulo.
- **module_name** Nombre del módulo.
- **location** Puntero al área de código del módulo, preámbulo primero.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Carga correcta del módulo.
- **TX_CALLER_ERROR** (0x13) Autor de llamada no válido.
- **TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.
- **TX_NO_MEMORY** (0x10) No hay suficiente memoria para cargar el módulo.
- **TX_PTR_ERROR** (0x03) Puntero, instancia de módulo o preámbulo de módulo no válidos.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alineación no válida.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) Ya se cargó el módulo.
- **TXM_MODULE_INVALID** (0xF2) Preámbulo de módulo no válido.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Propiedades incompatibles.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a>Vea también

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_object_pool_create"></a>txm_module_manager_object_pool_create

Cree un grupo de objetos para los módulos.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a>Descripción

Este servicio crea un grupo de memoria de objetos del administrador de módulos al que los módulos pueden asignar objetos de ThreadX/NetX, manteniendo el objeto del sistema fuera del área de memoria del módulo.

### <a name="input-parameters"></a>Parámetros de entrada

- **pool_memory_start** Puntero al inicio de la memoria del objeto.
- **pool_memory_size** Tamaño en bytes del grupo de memoria de objetos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Inicialización correcta.
- **TX_CALLER_ERROR** (0x13) Autor de llamada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a>Vea también

- txm_module_manager_initialize

---

## <a name="txm_module_manager_properties_get"></a>txm_module_manager_properties_get

Obtenga las propiedades del módulo.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a>Descripción

Este servicio devuelve las propiedades (especificadas en el preámbulo) de un módulo.

### <a name="input-parameters"></a>Parámetros de entrada

- **module_instance** Puntero a la instancia del módulo.
- **module_properties_ptr** Puntero al destino de las propiedades del módulo.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Inicialización correcta.
- **TX_PTR_ERROR** (0x03) Puntero no válido.
- **TX_CALLER_ERROR** (0x13) Autor de llamada no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a>txm_module_manager_start

Inicie la ejecución de un módulo.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Descripción

Este servicio inicia la ejecución del módulo especificado, ya cargado.

### <a name="input-parameters"></a>Parámetros de entrada

- **module_instance** Puntero a la instancia de módulo cargada previamente.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Inicio correcto del módulo.
- **TX_CALLER_ERROR** (0x13) Autor de llamada no válido.
- **TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.
- **TX_PTR_ERROR** (0x03) Puntero o instancia de módulo no válidos.
- **TX_START_ERROR** (0x10) El módulo ya se ha iniciado.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Vea también

- txm_module_manager_stop

---

## <a name="txm_module_manager_stop"></a>txm_module_manager_stop

Detenga la ejecución de un módulo.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Descripción

Este servicio detiene un módulo que se cargó e inició previamente. La detención de un módulo incluye la ejecución del subproceso de detención opcional del módulo, la finalización de todos los subprocesos y la eliminación de todos los recursos asociados al módulo.

### <a name="input-parameters"></a>Parámetros de entrada

- **module_instance** Puntero a la instancia del módulo.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Detención correcta del módulo.
- **TX_CALLER_ERROR** (0x13) Autor de llamada no válido.
- **TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.
- **TX_PTR_ERROR** (0x03) Puntero o instancia de módulo no válidos.
- **TX_START_ERROR** (0x10) No se ha iniciado el módulo.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Vea también

- txm_module_manager_start

---

## <a name="txm_module_manager_unload"></a>txm_module_manager_unload

Descargue el módulo.

### <a name="prototype"></a>Prototipo

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Descripción

Este servicio descarga el módulo previamente cargado y detenido, liberando todos los recursos de memoria del módulo asociados.

### <a name="input-parameters"></a>Parámetros de entrada

- **module_instance** Puntero a la instancia del módulo.

### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00) Descarga correcta del módulo.
- **TX_CALLER_ERROR** (0x13) Autor de llamada no válido.
- **TX_NOT_AVAILABLE** (0x1D) No se inicializó el administrador.
- **TX_NOT_DONE** (0x20) No se ha detenido el módulo o no es válido.
- **TX_PTR_ERROR** (0x03) Puntero o instancia de módulo no válidos.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Vea también

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_stop
