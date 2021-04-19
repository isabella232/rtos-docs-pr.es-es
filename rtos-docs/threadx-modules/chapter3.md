---
title: 'Capítulo 3: Requisitos del Administrador de módulos'
description: Este artículo es una descripción de los pasos necesarios para crear el Administrador de módulos de ThreadX.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8ea1a05096b5975de203648fddfb19c1a6105e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815117"
---
# <a name="chapter-3---module-manager-requirements"></a>Capítulo 3: Requisitos del Administrador de módulos

El Administrador de módulos de ThreadX reside en la parte residente de la aplicación junto con ThreadX RTOS. Es responsable del inicio del módulo, así como el campo y el envío de todas las solicitudes de módulo para los servicios de API de ThreadX.

> [!NOTE]
> Los archivos de origen del **Administrador** de módulos ThreadX (C y ensamblado) se deben agregar al proyecto de biblioteca ThreadX "**tx**".

Los pasos siguientes son necesarios para compilar el Administrador de módulos de ThreadX (cada paso se describe con más detalle a continuación).

1. El bloque de control de **TX_THREAD** se debe extender para incluir información del módulo. La forma más fácil de lograr esto es reemplazar la definición de **TX_THREAD_EXTENSION_2** en el archivo **_tx_port.h_ *_ con el _* TX_THREAD_EXTENSION_2** que se encuentra en **_txm_module_port.h_**. Consulte el [apéndice](appendix.md) para extensiones específicas del puerto.

Ejemplos de extensión:

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   Las siguientes extensiones deben definirse en ***tx_port. h***.

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. Agregue todos los archivos C y de ensamblado ***txm_module_manager_ \**** al proyecto **_tx_** de la biblioteca ThreadX.
3. Recompile todas las bibliotecas y proyectos ejecutables. Si se requiere NetX Duo, todo el código C del administrador de módulos y módulos debe construirse con **TXM_MODULE_ENABLE_NETX_DUO** definido.

## <a name="module-manager-sources"></a>Orígenes del administrador de módulos

El administrador de módulos ThreadX tiene un conjunto de archivos de origen que están diseñados para vincularse y ubicarse directamente con el código ThreadX residente. Estos archivos proporcionan la capacidad de iniciar un módulo y las solicitudes de API de ThreadX subsiguientes del módulo. Los archivos del administrador de módulos son los siguientes.

| **Nombre de archivo** |  **Contents** |
|-------------- | ------------- |
| ***txm_module.h*** | Archivo de inclusión que define la información del módulo (también incluida en el código fuente del módulo). |
| ***txm_module_manager_dispatch.h*** | Archivo de inclusión que define las funciones auxiliares de distribución.|
| ***txm_module_manager_util.h*** | Archivo de inclusión que define las macros y funciones internas auxiliares. |
| ***txm_module_port.h*** | Archivo de inclusión que define la información del módulo específico del puerto (también incluida en el código fuente del módulo). |
| ***tx_initialize_low_level.\[s,S,68\]** _ | Reemplaza el archivo de biblioteca ThreadX existente. Tabla de vectores y controladores de vector adicionales actualizados para el administrador de módulos y las excepciones de memoria. _Este archivo solo está en Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.*|
| ***tx_thread_context_restore.s** _ | Reemplaza el archivo de biblioteca ThreadX existente. Restaure el contexto del subproceso después del procesamiento de interrupción. _Este archivo solo está en Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***tx_thread_schedule.\[s,S,68\]*** | Reemplaza el archivo de biblioteca ThreadX existente. Código de programador extendido, que en este caso se usa para actualizar los registros de administración de memoria. |
| ***tx_thread_stack_build.s** _ | Reemplaza el archivo de biblioteca ThreadX existente. Compila el marco de pila de un subproceso. _Este archivo solo está en Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***txm_module_manager_thread_stack_build.\[s,S,68\]*** | Compila todas las pilas iniciales del módulo, incluye el programa de instalación para el acceso a datos independiente de la posición. |
| ***txm_module_manager_user_mode_entry.\[s,S\]** _ | Permite al módulo entrar en modo kernel. _Este archivo solo está en Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***txm_module_manager_alignment_adjust.c*** | Controla los requisitos de alineación específicos del puerto.|
| ***txm_module_manager_application_request.c*** | Controla las solicitudes específicas de la aplicación al código residente. |
| ***txm_module_manager_callback_request.c*** | Envía una solicitud de devolución de llamada a un módulo. |
| ***txm_module_manager_event_flags_notify_trampoline.c*** | Procesa la llamada de notificación del conjunto de marcas de eventos desde ThreadX. |
| ***txm_module_manager_external_memory_enable.c*** | Crea una entrada en la tabla de administración de memoria para un espacio de memoria compartido al que el módulo puede tener acceso. |
| ***txm_module_manager_file_load.c*** | Asigna y carga un archivo de módulo binario en el área de memoria del módulo y lo prepara para su ejecución. |
| ***txm_module_manager_in_place_load.c*** | Asigna el área de datos del módulo y se prepara para la ejecución del módulo a partir de la dirección del código proporcionado. |
| ***txm_module_manager_initialize.c*** | Inicializa el administrador de módulos, incluida la especificación del área de memoria del módulo disponible para cargar y ejecutar módulos. |
| ***txm_module_manager_initialize_mmu.c** _ | Inicializar MMU. Los usuarios pueden editar este archivo en función de su asignación de memoria. _Este archivo solo está en Cortex-A7/ARM* |
| ***txm_module_manager_mm_initialize.c** _ | Inicialice MPU/MMU. Los usuarios pueden editar este archivo en función de su asignación de memoria. _Este archivo solo está en Cortex-A7/ARM* |
| ***txm_module_manager_kernel_dispatch.c*** | Controla las solicitudes de API de módulo, según el id. de solicitud. |
| ***txm_module_manager_maximum_module_priority_set.c*** | Establece la prioridad de subproceso máxima permitida en un módulo. |
| ***txm_module_manager_memory_fault_handler.c*** | Controla los errores de memoria detectados en un módulo en ejecución. |
| ***txm_module_manager_memory_fault_notify.c*** | Registra una devolución de llamada de notificación de aplicación cada vez que se produce un error de memoria. |
| ***txm_module_manager_memory_load.c*** | Asigna y carga el código y los datos de un módulo y prepara el módulo para su ejecución. |
| ***txm_module_manager_mm_register_setup.c*** | Configura registros de MPU/MMU para el módulo en función de dónde se cargan el código y los datos. |
| ***txm_module_manager_object_allocate.c*** | Asigna memoria para un objeto de módulo. |
| ***txm_module_manager_object_deallocate.c*** | Asigna memoria para un objeto de módulo. |
| ***txm_module_manager_object_pointer_get.c*** | Busca el tipo de objeto y el nombre proporcionados y, si los encuentra, devuelve el puntero de objeto. |
| ***txm_module_manager_object_pointer_get_extended.c*** | Busca el tipo de objeto y el nombre proporcionados y, si los encuentra, devuelve el puntero de objeto. Longitud de nombre especificada para la seguridad. |
| ***txm_module_manager_object_pool_create.c***  | Crea un grupo de objetos fuera del área de datos del módulo desde la que las aplicaciones de módulo pueden asignar. |
| ***txm_module_manager_properties_get.c*** | Obtiene las propiedades del módulo especificado. |
| ***txm_module_manager_queue_notify_trampoline.c*** | Procesa la llamada de notificación de cola desde ThreadX. |
| ***txm_module_manager_semaphore_notify_trampoline.c*** | Procesa la llamada de notificación de colocación de semáforo de ThreadX.|
| ***txm_module_manager_start.c*** | Inicia la ejecución de un módulo. |
| ***txm_module_manager_stop.c*** | Detiene la ejecución de un módulo. |
| ***txm_module_manager_thread_create.c*** | Crea todos los subprocesos del módulo. |
| ***txm_module_manager_thread_notify_trampoline.c*** | Procesa la llamada de notificación de entrada/salida de subproceso desde ThreadX. |
| ***txm_module_manager_thread_reset.c*** | Restablecer un subproceso de módulo. |
| ***txm_module_manager_timer_notify_trampoline.c*** | Procesa las expiraciones del temporizador desde ThreadX. |
| ***txm_module_manager_unload.c*** | Descarga el módulo del área de memoria del módulo. |
| ***txm_module_manager_util.c*** | Funciones auxiliares internas para el administrador. |

## <a name="module-manager-initialization"></a>Inicialización del administrador de módulos

La parte residente de la aplicación es responsable de llamar a la función de inicialización del administrador de módulos ***txm_module_manager_initialize***. Esta función configura las estructuras internas para cargar y descargar módulos, incluida la configuración del área de memoria que se usa para la asignación de memoria del módulo.

## <a name="module-manager-loading"></a>Carga del administrador de módulos

El administrador de módulos puede cargar módulos de forma dinámica en la memoria del módulo desde los archivos de módulo binario o desde una sección de código de módulo que ya está presente en el área de código residente. Además, el administrador de módulos puede ejecutar código en contexto, es decir, solo se asignan los datos del módulo en la memoria del módulo y la ejecución del código se realiza en su lugar. Están disponibles las siguientes funciones de la API de carga del administrador de módulos.

* ***txm_module_manager_file_load***

* ***txm_module_manager_in_place_load***

* ***txm_module_manager_memory_load***

La versión protegida en memoria del administrador de módulos también se asegura de que el módulo se carga con la alineación adecuada y los registros de administración de memoria se configuran correctamente para cada módulo. Cuando se habilita la protección de memoria a través de las opciones del preámbulo del módulo, el acceso a la memoria del módulo está restringido al código del módulo y a las áreas de datos.

## <a name="module-manager-starting"></a>Inicio del administrador de módulos

El administrador de módulos inicia la ejecución de un módulo cargado previamente a través de la función de API de ***txm_module_manager_start***. Para iniciar la ejecución del módulo, esta función crea un subproceso que entra en el módulo en la ubicación de inicio especificada en el preámbulo del módulo. La prioridad y el tamaño de pila de este subproceso también se especifican en el preámbulo del módulo.

## <a name="module-manager-stopping"></a>Detención del administrador de módulos

El administrador de módulos finaliza la ejecución de un módulo cargado previamente y en ejecución a través de la función ***txm_module_manager_stop***. Esta función de API finaliza primero y elimina el subproceso de inicio inicial. Si el preámbulo del módulo especifica un subproceso de detención, este subproceso se crea y se ejecuta. El administrador de módulos espera durante un período de tiempo fijo para que se complete el subproceso de detención. Una vez completado, se eliminan todos los recursos del sistema creados por el módulo y el módulo se coloca en un estado inactivo, desde el que puede reiniciarse o descargarse.

## <a name="module-manager-unloading"></a>Descarga del administrador de módulos

El administrador de módulos descarga un módulo cargado previamente pero que no se está ejecutando a través de la función ***txm_module_manager_unload***. Esta API libera toda la memoria asociada al módulo y la libera para su uso con otro módulo en el futuro.

## <a name="module-manager-requests"></a>Solicitudes del administrador de módulos

Las solicitudes realizadas por los módulos al administrador de módulos se realizan mediante macros en ***txm_module.h*** que asignan todas las llamadas a ThreadX para llamar a la función de distribución del administrador de módulos a través de un puntero de función proporcionado por el administrador de módulos.

Los servicios adicionales específicos de la aplicación que se realizan a través del módulo que llama a ***txm_module_application_request*** se controlan mediante el mismo mecanismo de macro que se usa para la API ThreadX. De manera predeterminada, esta función de control del administrador de módulos está vacía y está diseñada de modo que la aplicación agregue el código necesario para procesar las solicitudes específicas de la aplicación.

Si el administrador del módulo no implementa la solicitud, el administrador del módulo devuelve un valor de estado de error **TX_NOT_AVAILABLE**. También se devuelve este código de error si el módulo solicita una operación que está fuera del ámbito del acceso del módulo. Por ejemplo, un módulo no tiene permiso para crear un temporizador con el bloque de control del temporizador o la dirección de devolución de llamada fuera del área de código del módulo.

## <a name="module-manager-example"></a>Ejemplo de administrador de módulos

A continuación se presenta un ejemplo de código del administrador de módulos que inicia el módulo de ejemplo previamente definido en el capítulo 2. Se supone que el módulo ya está cargado, presumiblemente por el depurador, en la dirección ROM 0x00800000.

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a>Compilación del administrador de módulos

Los archivos de origen de ***txm_module_manager_ \**** se deben agregar a la biblioteca ThreadX.

Una aplicación del administrador de módulos ThreadX es realmente la misma que una aplicación ThreadX estándar, que es uno o varios archivos de aplicación vinculados junto con la biblioteca ThreadX ***tx.a***. La compilación de una aplicación del administrador de módulos depende de la cadena de herramientas utilizada. Consulte el [apéndice](appendix.md) para ver ejemplos específicos de puertos.
