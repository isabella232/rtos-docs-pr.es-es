---
title: 'Capítulo 11: Formato del búfer de seguimiento de eventos'
description: ThreadX proporciona compatibilidad integrada con el seguimiento de eventos para todos los servicios de Azure RTOS ThreadX, cambios de estado de subprocesos y eventos definidos por el usuario.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815770"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a>Capítulo 11: Formato del búfer de seguimiento de eventos

Azure RTOS ThreadX proporciona compatibilidad integrada con el seguimiento de eventos para todos los servicios de ThreadX, cambios de estado de subprocesos y eventos definidos por el usuario. Para usar el seguimiento de eventos, simplemente compile las bibliotecas de ThreadX, NetX y FileX con **TX_ENABLE_EVENT_TRACE** definido y habilite el seguimiento mediante una llamada a la función **_tx_trace_enable_**. En este capítulo se describe ese proceso.

## <a name="event-trace-format"></a>Formato de seguimiento de eventos

El formato del búfer de seguimiento de eventos de ThreadX se divide en tres secciones; es decir, las entradas de seguimiento, el registro de objeto y el encabezado de control. A continuación se describe el diseño general del búfer de seguimiento de eventos de ThreadX:

**Encabezado de control**

**Entrada del registro de objeto 0**

**…**

**Entrada del registro de objeto "n"**

**Entrada del seguimiento de eventos 0**

**…**

**Entrada del seguimiento de eventos "n"**

### <a name="event-trace-control-header"></a>Encabezado de control del seguimiento de eventos

El encabezado de control define el diseño exacto del búfer de seguimiento de eventos. Esto incluye el número de objeto ThreadX y de eventos que se pueden registrar. Además, el encabezado de control define dónde reside cada uno de los elementos del búfer de seguimiento. La estructura de datos siguiente define el encabezado de control:

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a>Id. de encabezado de control

El id. de encabezado de control está formado por el valor hexadecimal 0x54585442 de 32 bits, que corresponde a los caracteres ASCII ***TXTB***. Puesto que este valor se escribe como una variable de 32 bits sin signo, también se puede usar para detectar el modo endian del búfer de seguimiento de eventos. Por ejemplo, si el valor de los cuatro primeros bytes de memoria es 0x54, 0x58, 0x54, 0x42, el búfer de seguimiento de eventos se escribió en formato big endian. Por el contrario, el búfer de seguimiento de eventos se escribió en formato little endian.

### <a name="timer-valid-mask"></a>Máscara válida de temporizador

La máscara válida de temporizador define cuántos bits de la marca de tiempo de las entradas de seguimiento de eventos reales son válidos. Por ejemplo, si el origen de la marca de tiempo tiene 16 bits, el valor de este campo debe ser 0xFFFF. Un origen de marca de tiempo de 32 bits tendría un valor de 0xFFFFFFFF. Este valor se define con la constante ***TX_TRACE_TIME_MASK** _ en _*_tx_port.h_**.

### <a name="trace-base-address"></a>Dirección base de seguimiento

La dirección base del búfer de seguimiento es la dirección que la aplicación especificó como el inicio del búfer de seguimiento en la llamada ***tx_trace_enable***. Esta dirección se mantiene para el uso exclusivo de la herramienta de análisis a fin de derivar compensaciones relativas al búfer para los distintos elementos del búfer. Por ejemplo, la compensación relativa al búfer del evento actual en el búfer de seguimiento se calcula mediante la resta simple de la dirección base de la dirección del evento actual.

### <a name="registry-start-and-end-pointers"></a>Punteros inicial y final del registro

El puntero inicial del registro apunta a la dirección de la primera entrada del registro de objeto, mientras que el puntero final del registro señala a la dirección inmediatamente después de la última entrada del registro. Estos valores se configuran durante el procesamiento de *tx_trace_enable* y no se modifican a lo largo de la duración del seguimiento.

### <a name="registry-name-size"></a>Tamaño del nombre del registro

El tamaño del nombre del registro define el tamaño máximo en bytes para cada nombre de objeto de la entrada del registro y se define mediante el símbolo ***TX_TRACE_OBJECT_REGISTRY_NAME** _. El valor predeterminado es 32 y se define en _*_tx_trace.h_*_. El nombre del objeto corresponde al nombre dado por la aplicación cuando se creó el objeto. Por ejemplo, el nombre del registro de objeto de un subproceso es el nombre que la aplicación proporciona a la llamada _*_tx_thread_create_**.

### <a name="buffer-start-and-end-pointers"></a>Punteros inicial y final del búfer

El puntero inicial del búfer de seguimiento de eventos apunta a la dirección de la primera entrada del seguimiento, mientras que el puntero final del registro señala a la dirección inmediatamente después de la última entrada del seguimiento. Estos valores se configuran durante el procesamiento de ***tx_trace_enable</*** y no se modifican a lo largo de la duración del seguimiento.

### <a name="current-buffer-pointer"></a>Puntero actual del búfer

El puntero actual del búfer de seguimiento de eventos apunta a la dirección de la entrada de seguimiento más antigua. Dado que las entradas de seguimiento se mantienen en una lista circular, el puntero actual del búfer también representa la entrada de seguimiento siguiente que se va a escribir. |

## <a name="event-trace-object-registry"></a>Registro de objeto del seguimiento de eventos

El registro de objeto del seguimiento de eventos contiene ***n** _ entradas del registro de objeto que corresponden a los objetos creados por la aplicación. El propósito principal del registro de objeto es que las herramientas de análisis externo correlacionen los nombres de objetos reales con las direcciones de objetos de las entradas del búfer de seguimiento. La aplicación especifica el número de entradas del registro en la llamada _ *_tx_trace_enable_**.

Cada entrada del registro de objeto contiene información sobre un objeto ThreadX específico que la aplicación creó previamente. La estructura de datos siguiente define cada entrada del registro de objeto:

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a>Marca de objeto disponible

La marca de objeto disponible está establecida en 1 si la entrada del registro de objeto está disponible. De lo contrario, si el valor no es 1, la entrada del registro de objeto no está disponible. Tenga en cuenta que la entrada todavía puede contener información válida, aunque esté disponible.

### <a name="object-entry-type"></a>Tipo de entrada de objeto

El tipo de entrada de objeto identifica el tipo de objeto de esta entrada. A continuación se muestra una lista de los tipos de objetos válidos:

| **Valor** | **Tipo de objeto** |
|---------- | --------------- |
| 0         | No válido       |
| 1         | Thread          |
| 2         | Temporizador |
| 3         | Cola |
| 4         | Semaphore |
| 5         | Mutex |
| 6         | Grupo de marcas de eventos |
| 7         | Grupo de bloques |
| 8         | Grupo de bytes |
| 9         | ../media |
| 10        | Archivo |
| 11        | IP |
| 12        | Grupo de paquetes |
| 13        | Socket TCP |
| 14        | Socket UDP |
| 15-20     | Reservado |  
| 21        | API de pila de host USB |
| 22        | Interfaz de pila de host USB |
| 23        | Punto de conexión de host USB |
| 24        | Clase de host USB |
| 25        | Dispositivo USB |
| 26        | Interfaz del dispositivo USB |
| 27        | Punto de conexión de dispositivo USB |
| 28        | Clase de dispositivo USB |

### <a name="object-pointer"></a>Puntero de objeto

El puntero de objeto especifica la dirección del objeto que se usa para obtener acceso al objeto mediante la API ThreadX.

### <a name="object-reserved-fields"></a>Campos reservados del objeto

Para todos los objetos que no son subprocesos, estos campos reservados deben ser 0. En el caso de los subprocesos, la prioridad del subproceso en el momento en que se escribe en el registro se coloca en estos dos campos reservados.

### <a name="object-parameters"></a>Parámetros del objeto

Los parámetros del objeto contienen información complementaria sobre el objeto. A continuación se describe la información complementaria para cada objeto ThreadX:

| **Tipo de objeto**        | **Parámetro 1**  | **Parámetro 2** |
|----------------------- | ---------------- | --------------- |
| Thread                 | Inicio de la pila      | Tamaño de la pila |
| Temporizador                  | Tics iniciales | Reprogramación de tics |
| Cola                  | Tamaño de cola | Tamaño de los mensajes |
| Semaphore              | Instancias iniciales | - |
| Mutex                  | Marca de herencia | - |
| Grupo de marcas de eventos      | - | - |
| Grupo de bloques             | Total de bloques | Tamaño de bloque |
| Grupo de bytes              | Número total de bytes | - |
| ../media                  | Tamaño de la caché FAT | Tamaño de la caché de sector |
| Archivo                   | - | - |
| IP                     | Inicio de la pila | Tamaño de la pila |
| Grupo de paquetes            | Tamaño del paquete | Número de paquetes |
| Socket TCP             | IP address (Dirección IP) | Tamaño de ventana |
| Socket UDP             | IP address (Dirección IP) | Cola RX máxima |

### <a name="object-name"></a>Nombre de objeto

El nombre de objeto contiene el nombre del objeto ThreadX. El nombre es el nombre que se proporcionó a ThreadX en el momento en que se creó el objeto. De manera predeterminada, el nombre del objeto tiene un máximo de 32 caracteres. Los nombres reales con más de 32 caracteres se truncan.

## <a name="event-trace-entries"></a>Entradas del seguimiento de eventos

Las entradas de seguimiento de eventos se encuentran en la parte inferior del búfer de seguimiento de eventos. Las entradas se mantienen en una lista circular, con el puntero de entrada actual apuntando a la entrada más antigua. La llamada ***tx_trace_enable*** calcula el número de entradas de la lista.

Cada entrada del registro de objeto contiene información sobre un evento de seguimiento ThreadX específico. La estructura de datos siguiente define cada entrada de evento de seguimiento:

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a>Puntero de subproceso

El puntero de subproceso contiene la dirección del subproceso que se ejecuta en el momento de este evento. Si el evento se produjo durante la inicialización (sin ningún subproceso en ejecución), el valor de este puntero es 0xF0F0F0F0. Si el evento se produjo durante una rutina de servicio de interrupción (ISR), el valor de este puntero es 0xFFFFFFFF. Si todavía no se usa la entrada, el valor de este puntero es 0.

### <a name="thread-priority"></a>Prioridad del subproceso

El campo de prioridad del subproceso contiene la prioridad del subproceso y el umbral de preferencia del subproceso que estaba en ejecución en el momento de este evento. Si hay un contexto de interrupción (el puntero de subproceso es 0xFFFFFFFF), la prioridad no es el valor de este campo sino que, en su lugar, el valor de ***_tx_thread_current_ptr*** en el momento del evento. De lo contrario, el valor de este campo es 0.

### <a name="event-id"></a>Id. de evento

El id. de evento especifica el evento que tuvo lugar. Los id. de evento de seguimiento ThreadX válidos van de 1 a 1024. Los valores que comienzan en 1025 y superiores están reservados para los eventos específicos del usuario. Consulte el archivo ***tx_trace.h*** para obtener la definición completa de los id. de evento ThreadX.</td>

### <a name="information-fields-1-4"></a>Campos de información (1 a 4)

Los campos de información contienen información adicional sobre el evento específico. Consulte el archivo ***tx_trace. h*** para obtener una descripción completa de los campos de información de cada uno de los id. de evento ThreadX definidos.