---
title: 'Capítulo 5: Generación de búferes de seguimiento'
description: En este capítulo se incluye una descripción sobre cómo crear un búfer de eventos de Azure RTOS TraceX y también se describe el formato subyacente del búfer.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f296137d23b9f3c1c4fd115947bb50a32b768123
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815734"
---
# <a name="chapter-5---generating-trace-buffers"></a>Capítulo 5: Generación de búferes de seguimiento

En este capítulo se incluye una descripción sobre cómo crear un búfer de eventos de Azure RTOS TraceX y también se describe el formato subyacente del búfer.

## <a name="threadx-event-trace-support"></a>Compatibilidad con el seguimiento de eventos de ThreadX

ThreadX proporciona compatibilidad integrada con el seguimiento de eventos para todos los servicios de ThreadX, cambios de estado de subprocesos y eventos definidos por el usuario. La funcionalidad de seguimiento de eventos de ThreadX se ha diseñado principalmente como una herramienta de análisis posterior para analizar las últimas actividades "n" en la aplicación. A partir de esta información, el desarrollador puede detectar problemas y posibles objetivos de optimización.

TraceX muestra gráficamente el búfer de seguimiento de eventos compilado por ThreadX. A continuación se describe cómo compilar el búfer y se describe el formato subyacente del búfer.

## <a name="enabling-event-trace"></a>Activación del seguimiento de eventos

Para habilitar el seguimiento de eventos, defina las constantes de marca de tiempo, compile la biblioteca ThreadX con **TX_ENABLE_EVENT_TRACE** definido y habilite el seguimiento llamando a la función **tx_trace_enable**.

## <a name="defining-time-stamp-constants"></a>Definición de constantes de marca de tiempo

Las constantes de marca de tiempo están diseñadas para proporcionar al desarrollador el control sobre la marca de tiempo usada en las entradas de seguimiento de eventos. Las dos constantes de marca de tiempo y sus valores predeterminados son los siguientes:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

Las constantes anteriores se definen en **tx_port.h** y crean una marca de tiempo "falsa" que simplemente incrementa en uno en cada evento. El siguiente es un ejemplo de una definición de marca de tiempo real:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

Las constantes anteriores especifican un temporizador de 32 bits que se obtiene al leer la dirección 0x13000004. La mayoría de las marcas de tiempo específicas de la aplicación se deben configurar de manera similar.

## <a name="exporting-the-trace-buffer"></a>Exportación del búfer de seguimiento

TraceX necesita el búfer de seguimiento en un formato de archivo binario, Intel HEX o Motorola S-Record en el host. La manera más sencilla de lograrlo es detener el destino e indicar al depurador que vuelque el área de memoria que proporcionó para la función ***tx_trace_enable*** en un archivo en el host.

> [!WARNING]
>***Tenga cuidado de no detener el destino dentro del propio código de recopilación de seguimiento. Si lo hace, puede producir información de seguimiento no válida. Si el programa se detiene dentro de ThreadX, es mejor desplazarse por las macros de inserción de seguimiento antes de volcar el búfer de seguimiento.***

> [!IMPORTANT]
> *En el apéndice D se muestra cómo volcar el búfer de seguimiento desde una variedad de herramientas de desarrollo.*

## <a name="extended-event-trace-api"></a>API de seguimiento de eventos extendidos

Cuando ThreadX se compila con **TX_ENABLE_EVENT_TRACE** definido, las siguientes API de seguimiento de eventos están disponibles para la aplicación:

- tx_trace_enable: *Activación del seguimiento de eventos*
- tx_trace_event_filter: *Filtrado de eventos especificados*
- tx_trace_event_unfilter: *Anulación del filtrado de eventos especificados*
- tx_trace_disable: *Desactivación del seguimiento de eventos*
- tx_trace_isr_enter_insert: *Inserción del evento de seguimiento de entrada de ISR*
- tx_trace_isr_exit_insert: *Inserción del evento de seguimiento de salida de ISR*
- tx_trace_buffer_full_notify: *Registro de la devolución de llamada de aplicación completa del búfer de seguimiento*
- tx_trace_user_event_insert: *Inserción de evento de usuario*

### <a name="tx_trace_enable"></a>tx_trace_enable

Activación del seguimiento de eventos

#### <a name="prototype"></a>Prototipo

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a>Descripción
Este servicio habilita el seguimiento de eventos dentro de ThreadX. La aplicación suministra el búfer de seguimiento y el número máximo de objetos de ThreadX.

> [!IMPORTANT]
> La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.

#### <a name="input-parameters"></a>Parámetros de entrada

- **trace_buffer_start**: puntero que señala al inicio del búfer de seguimiento proporcionado por el usuario.
- **trace_buffer_size**: número total de bytes en la memoria para el búfer de seguimiento. Cuanto mayor sea el búfer de seguimiento, más entradas podrá almacenar.
- **registry_entries**: número de objetos de ThreadX de la aplicación que se conservarán en el registro de seguimiento. El registro se usa para correlacionar las direcciones de objeto con los nombres de objeto. Esto es muy útil para las herramientas de análisis de seguimiento de GUI.

#### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): el seguimiento de eventos se ha habilitado correctamente.
- **TX_SIZE_ERROR** (0x05): el tamaño del búfer de seguimiento especificado es demasiado pequeño. Debe ser lo suficientemente grande para alojar el encabezado de seguimiento, el registro de objetos y al menos una entrada de seguimiento.
- **TX_NOT_DONE** (0x20): el seguimiento de eventos ya estaba habilitado.
- **TX_FEATURE_NOT_ENABLED** (0xFF): no se compiló el sistema con el seguimiento habilitado.

#### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

#### <a name="example"></a>Ejemplo

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a>Consulte también

tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_event_filter"></a>tx_trace_event_filter

Filtrado de eventos especificados.

#### <a name="prototype"></a>Prototipo

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a>Descripción

Este servicio filtra los eventos especificados para que no se inserten en el búfer de seguimiento activo. Tenga en cuenta que, de forma predeterminada, no se filtra ningún evento después de que se llame a *tx_trace_enable*.

> [!IMPORTANT]
> La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.

#### <a name="input-parameters"></a>Parámetros de entrada

- **event_filter_bits**: bits que corresponden a los eventos que se van a filtrar. Se pueden filtrar varios eventos simplemente juntando las constantes adecuadas con or-ing. Las constantes válidas para esta variable se definen de la siguiente manera:

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): filtro de evento correcto.
- **TX_FEATURE_NOT_ENABLED** (0xFF): no se compiló el sistema con el seguimiento habilitado.

#### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

#### <a name="example"></a>Ejemplo

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a>Consulte también

tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_event_unfilter"></a>tx_trace_event_unfilter

Anulación del filtrado de eventos especificados.

#### <a name="prototype"></a>Prototipo

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a>Descripción

Este servicio quita el filtro de los eventos especificados para que se inserten en el búfer de seguimiento activo.

> [!IMPORTANT]
> La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.

#### <a name="input-parameters"></a>Parámetros de entrada

- **event_unfilter_bits**: bits que corresponden a los eventos cuyo filtro se va a anular. Se puede anular el filtro de varios eventos simplemente juntando las constantes adecuadas con or-ing. Las constantes válidas para esta variable se definen de la siguiente manera:

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): anulación del filtrado de evento correcto.
- **TX_FEATURE_NOT_ENABLED** (0xFF): no se compiló el sistema con el seguimiento habilitado.

#### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

#### <a name="example"></a>Ejemplo

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a>Consulte también

tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_disable"></a>tx_trace_disable

#### <a name="disable-event-tracing"></a>Desactivación del seguimiento de eventos

#### <a name="prototype"></a>Prototipo

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a>Descripción

Este servicio deshabilita el seguimiento de eventos dentro de ThreadX. Esto puede ser útil si la aplicación quiere inmovilizar el búfer de seguimiento de eventos actual y, posiblemente, transportarlo externamente durante el tiempo de ejecución. Una vez deshabilitado, se puede llamar a **tx_trace_enable** para volver a iniciar el seguimiento.

> [!IMPORTANT]
> La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.

#### <a name="input-parameters"></a>Parámetros de entrada

Ninguno.

#### <a name="return-values"></a>Valores devueltos

- **TX_SUCCESS** (0x00): el seguimiento de eventos se ha deshabilitado correctamente.
- **TX_NOT_DONE** (0x20): el seguimiento de eventos no estaba habilitado.
- **TX_FEATURE_NOT_ENABLED** (0xFF): no se compiló el sistema con el seguimiento habilitado.

#### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

#### <a name="example"></a>Ejemplo 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a>Consulte también

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_enter_insert"></a>tx_trace_isr_enter_insert

#### <a name="insert-isr-enter-event"></a>Inserción del evento de entrada de ISR

#### <a name="prototype"></a>Prototipo

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a>Descripción

Este servicio inserta el evento de entrada de ISR en el búfer de seguimiento de eventos. La aplicación debe llamarla al principio del procesamiento de ISR. El parámetro proporcionado debe identificar el ISR específico para la aplicación.

> [!IMPORTANT]
> La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.

#### <a name="input-parameters"></a>Parámetros de entrada 
- **isr_id**: valor específico de la aplicación para identificar el ISR.

#### <a name="return-values"></a>Valores devueltos

**None**

#### <a name="allowed-from"></a>Permitido desde 

ISR

#### <a name="example"></a>Ejemplo

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a>Consulte también

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_exit_insert"></a>tx_trace_isr_exit_insert

#### <a name="insert-isr-exit-event"></a>Inserción de evento de salida de ISR

#### <a name="prototype"></a>Prototipo

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a>Descripción

Este servicio inserta el evento de salida de ISR en el búfer de seguimiento de eventos. La aplicación debe llamarla al principio del procesamiento de ISR. El parámetro proporcionado debe identificar el ISR para la aplicación.

> [!IMPORTANT]
> La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.

#### <a name="input-parameters"></a>Parámetros de entrada 

- **isr_id**: valor específico de la aplicación para identificar el ISR.

#### <a name="return-values"></a>Valores devueltos

**None**

#### <a name="allowed-from"></a>Permitido desde

ISR

#### <a name="example"></a>Ejemplo

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a>Consulte también

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_buffer_full_notify"></a>tx_trace_buffer_full_notify

#### <a name="register-trace-buffer-full-application-callback"></a>Registro de la devolución de llamada de aplicación completa del búfer de seguimiento

#### <a name="prototype"></a>Prototipo

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada de aplicación llamada por ThreadX cuando el búfer de seguimiento se llena. A continuación, la aplicación puede optar por deshabilitar el seguimiento o configurar un nuevo búfer de seguimiento.

> [!IMPORTANT]
> La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.

#### <a name="input-parameters"></a>Parámetros de entrada

- **full_buffer_callback**: función de aplicación que se va a llamar cuando el búfer de seguimiento esté lleno. El valor NULL deshabilita la devolución de llamada de notificación.

#### <a name="return-values"></a>Valores devueltos

**None**

#### <a name="allowed-from"></a>Permitido desde

ISR

#### <a name="example"></a>Ejemplo

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a>Consulte también

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert

### <a name="tx_trace_user_event_insert"></a>tx_trace_user_event_insert

#### <a name="insert-user-event"></a>Inserción de evento de usuario

#### <a name="prototype"></a>Prototipo

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a>Descripción

Este servicio inserta el evento de usuario en el búfer de seguimiento. Los identificadores de evento de usuario deben ser mayores que la constante **TX_TRACE_USER_EVENT_START**, que se establece en 4096. El evento de usuario máximo se define mediante la constante **TX_TRACE_USER_EVENT_END**, que se establece en 65535. Todos los eventos de este intervalo están disponibles para la aplicación. Los campos de información son específicos de la aplicación.

> [!IMPORTANT]
> La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.

#### <a name="input-parameters"></a>Parámetros de entrada

- **event_id**: identificación de eventos específicos de la aplicación que debe iniciarse en un valor mayor que **TX_TRACE_USER_EVENT_START** y menor o igual que **TX_TRACE_USER_EVENT_END**.
- **info_field_1**: campo de información específica de la aplicación.
- **info_field_2**: campo de información específica de la aplicación.
- **info_field_3**: campo de información específica de la aplicación.
- **info_field_4**: campo de información específica de la aplicación.

#### <a name="return-values"></a>Valores devueltos
- **TX_SUCCESS** (0x00): inserción de evento de usuario correcta.
- **TX_NOT_DONE** (0x20): el seguimiento de eventos no está habilitado.
- **TX_FEATURE_NOT_ENABLED** (0xFF): no se ha compilado el sistema con el seguimiento habilitado.

#### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

#### <a name="example"></a>Ejemplo

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a>Consulte también

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify