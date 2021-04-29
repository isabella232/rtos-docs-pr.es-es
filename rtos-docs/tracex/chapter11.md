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
# <a name="chapter-11---format-of-event-trace-buffer"></a><span data-ttu-id="5b7cb-103">Capítulo 11: Formato del búfer de seguimiento de eventos</span><span class="sxs-lookup"><span data-stu-id="5b7cb-103">Chapter 11 - Format of event trace buffer</span></span>

<span data-ttu-id="5b7cb-104">Azure RTOS ThreadX proporciona compatibilidad integrada con el seguimiento de eventos para todos los servicios de ThreadX, cambios de estado de subprocesos y eventos definidos por el usuario.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-104">Azure RTOS ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="5b7cb-105">Para usar el seguimiento de eventos, simplemente compile las bibliotecas de ThreadX, NetX y FileX con **TX_ENABLE_EVENT_TRACE** definido y habilite el seguimiento mediante una llamada a la función **_tx_trace_enable_**.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-105">To use event trace, simply build the ThreadX, NetX, and FileX libraries with **TX_ENABLE_EVENT_TRACE** defined and enable tracing by calling the **_tx_trace_enable_** function.</span></span> <span data-ttu-id="5b7cb-106">En este capítulo se describe ese proceso.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-106">This chapter describes that process.</span></span>

## <a name="event-trace-format"></a><span data-ttu-id="5b7cb-107">Formato de seguimiento de eventos</span><span class="sxs-lookup"><span data-stu-id="5b7cb-107">Event Trace Format</span></span>

<span data-ttu-id="5b7cb-108">El formato del búfer de seguimiento de eventos de ThreadX se divide en tres secciones; es decir, las entradas de seguimiento, el registro de objeto y el encabezado de control.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-108">The format of the ThreadX event trace buffer is divided into three sections, namely the control header, object registry, and the trace entries.</span></span> <span data-ttu-id="5b7cb-109">A continuación se describe el diseño general del búfer de seguimiento de eventos de ThreadX:</span><span class="sxs-lookup"><span data-stu-id="5b7cb-109">The following describes the general layout of the ThreadX event trace buffer:</span></span>

<span data-ttu-id="5b7cb-110">**Encabezado de control**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-110">**Control Header**</span></span>

<span data-ttu-id="5b7cb-111">**Entrada del registro de objeto 0**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-111">**Object Registry Entry 0**</span></span>

<span data-ttu-id="5b7cb-112">**…**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-112">**…**</span></span>

<span data-ttu-id="5b7cb-113">**Entrada del registro de objeto "n"**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-113">**Object Register Entry "n"**</span></span>

<span data-ttu-id="5b7cb-114">**Entrada del seguimiento de eventos 0**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-114">**Event Trace Entry 0**</span></span>

<span data-ttu-id="5b7cb-115">**…**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-115">**…**</span></span>

<span data-ttu-id="5b7cb-116">**Entrada del seguimiento de eventos "n"**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-116">**Event Trace Entry "n"**</span></span>

### <a name="event-trace-control-header"></a><span data-ttu-id="5b7cb-117">Encabezado de control del seguimiento de eventos</span><span class="sxs-lookup"><span data-stu-id="5b7cb-117">Event Trace Control Header</span></span>

<span data-ttu-id="5b7cb-118">El encabezado de control define el diseño exacto del búfer de seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-118">The control header defines the exact layout of the event trace buffer.</span></span> <span data-ttu-id="5b7cb-119">Esto incluye el número de objeto ThreadX y de eventos que se pueden registrar.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-119">This includes how many ThreadX objects can be registered as well as how many events can be recorded.</span></span> <span data-ttu-id="5b7cb-120">Además, el encabezado de control define dónde reside cada uno de los elementos del búfer de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-120">In addition, the control header defines where each of the elements of the trace buffer resides.</span></span> <span data-ttu-id="5b7cb-121">La estructura de datos siguiente define el encabezado de control:</span><span class="sxs-lookup"><span data-stu-id="5b7cb-121">The following data structure defines the control header:</span></span>

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

### <a name="control-header-id"></a><span data-ttu-id="5b7cb-122">Id. de encabezado de control</span><span class="sxs-lookup"><span data-stu-id="5b7cb-122">Control Header ID</span></span>

<span data-ttu-id="5b7cb-123">El id. de encabezado de control está formado por el valor hexadecimal 0x54585442 de 32 bits, que corresponde a los caracteres ASCII ***TXTB***.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-123">The control header ID consists of the 32-bit HEX value of 0x54585442, which corresponds to the ASCII characters ***TXTB***.</span></span> <span data-ttu-id="5b7cb-124">Puesto que este valor se escribe como una variable de 32 bits sin signo, también se puede usar para detectar el modo endian del búfer de seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-124">Since this value is written as a 32-bit unsigned variable, it can also be used to detect the endianness of the event trace buffer.</span></span> <span data-ttu-id="5b7cb-125">Por ejemplo, si el valor de los cuatro primeros bytes de memoria es 0x54, 0x58, 0x54, 0x42, el búfer de seguimiento de eventos se escribió en formato big endian.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-125">For example, if the value in the first four byes of memory is 0x54, 0x58, 0x54, 0x42, the event trace buffer was written in big endian format.</span></span> <span data-ttu-id="5b7cb-126">Por el contrario, el búfer de seguimiento de eventos se escribió en formato little endian.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-126">Otherwise, the event trace buffer was written in little endian format.</span></span>

### <a name="timer-valid-mask"></a><span data-ttu-id="5b7cb-127">Máscara válida de temporizador</span><span class="sxs-lookup"><span data-stu-id="5b7cb-127">Timer Valid Mask</span></span>

<span data-ttu-id="5b7cb-128">La máscara válida de temporizador define cuántos bits de la marca de tiempo de las entradas de seguimiento de eventos reales son válidos.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-128">The timer valid mask defines how many bits of the timestamp in the actual event trace entries are valid.</span></span> <span data-ttu-id="5b7cb-129">Por ejemplo, si el origen de la marca de tiempo tiene 16 bits, el valor de este campo debe ser 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-129">For example, if the time-stamp source has 16-bits, the value in this field should be 0xFFFF.</span></span> <span data-ttu-id="5b7cb-130">Un origen de marca de tiempo de 32 bits tendría un valor de 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-130">A 32-bit time-stamp source would have a value of 0xFFFFFFFF.</span></span> <span data-ttu-id="5b7cb-131">Este valor se define con la constante ***TX_TRACE_TIME_MASK** _ en _*_tx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-131">This value is defined by the ***TX_TRACE_TIME_MASK** _ constant in _*_tx_port.h_\*\*.</span></span>

### <a name="trace-base-address"></a><span data-ttu-id="5b7cb-132">Dirección base de seguimiento</span><span class="sxs-lookup"><span data-stu-id="5b7cb-132">Trace Base Address</span></span>

<span data-ttu-id="5b7cb-133">La dirección base del búfer de seguimiento es la dirección que la aplicación especificó como el inicio del búfer de seguimiento en la llamada ***tx_trace_enable***.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-133">The trace buffer base address is the address the application specified as the start of the trace buffer in the ***tx_trace_enable*** call.</span></span> <span data-ttu-id="5b7cb-134">Esta dirección se mantiene para el uso exclusivo de la herramienta de análisis a fin de derivar compensaciones relativas al búfer para los distintos elementos del búfer.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-134">This address is maintained for the sole use of the analysis tool to derive bufferrelative offsets for the various elements in the buffer.</span></span> <span data-ttu-id="5b7cb-135">Por ejemplo, la compensación relativa al búfer del evento actual en el búfer de seguimiento se calcula mediante la resta simple de la dirección base de la dirección del evento actual.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-135">For example, the buffer relative offset of the current event in the trace buffer is calculated by simple subtraction of the base address from the current event address.</span></span>

### <a name="registry-start-and-end-pointers"></a><span data-ttu-id="5b7cb-136">Punteros inicial y final del registro</span><span class="sxs-lookup"><span data-stu-id="5b7cb-136">Registry Start and End Pointers</span></span>

<span data-ttu-id="5b7cb-137">El puntero inicial del registro apunta a la dirección de la primera entrada del registro de objeto, mientras que el puntero final del registro señala a la dirección inmediatamente después de la última entrada del registro.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-137">The registry start pointer points to the address of the first object registry entry, while the registry end pointer points to the address im../mediately following the last register entry.</span></span> <span data-ttu-id="5b7cb-138">Estos valores se configuran durante el procesamiento de *tx_trace_enable* y no se modifican a lo largo de la duración del seguimiento.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-138">These values are setup during the *tx_trace_enable* processing and are not changed throughout the duration of tracing.</span></span>

### <a name="registry-name-size"></a><span data-ttu-id="5b7cb-139">Tamaño del nombre del registro</span><span class="sxs-lookup"><span data-stu-id="5b7cb-139">Registry Name Size</span></span>

<span data-ttu-id="5b7cb-140">El tamaño del nombre del registro define el tamaño máximo en bytes para cada nombre de objeto de la entrada del registro y se define mediante el símbolo \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-140">The registry name size defines maximum size in bytes for each object name in the registry entry and is defined by the symbol \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span></span> <span data-ttu-id="5b7cb-141">El valor predeterminado es 32 y se define en _*_tx_trace.h_*_.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-141">The default value is 32 and is defined in _*_tx_trace.h_*_.</span></span> <span data-ttu-id="5b7cb-142">El nombre del objeto corresponde al nombre dado por la aplicación cuando se creó el objeto.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-142">The object name corresponds to the name given by the application when the object was created.</span></span> <span data-ttu-id="5b7cb-143">Por ejemplo, el nombre del registro de objeto de un subproceso es el nombre que la aplicación proporciona a la llamada _\*_tx_thread_create_\*\*.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-143">For example, the object registry name for a thread is the name supplied by the application to the _\*_tx_thread_create_\*\*call.</span></span>

### <a name="buffer-start-and-end-pointers"></a><span data-ttu-id="5b7cb-144">Punteros inicial y final del búfer</span><span class="sxs-lookup"><span data-stu-id="5b7cb-144">Buffer Start and End Pointers</span></span>

<span data-ttu-id="5b7cb-145">El puntero inicial del búfer de seguimiento de eventos apunta a la dirección de la primera entrada del seguimiento, mientras que el puntero final del registro señala a la dirección inmediatamente después de la última entrada del seguimiento.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-145">The event trace buffer start pointer points to the address of the first trace entry, while the registry end pointer points to the address im../mediately following the last trace entry.</span></span> <span data-ttu-id="5b7cb-146">Estos valores se configuran durante el procesamiento de ***tx_trace_enable</*** y no se modifican a lo largo de la duración del seguimiento.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-146">These values are setup during the ***tx_trace_enable</*** processing and are not changed throughout the duration of tracing.</span></span>

### <a name="current-buffer-pointer"></a><span data-ttu-id="5b7cb-147">Puntero actual del búfer</span><span class="sxs-lookup"><span data-stu-id="5b7cb-147">Current Buffer Pointer</span></span>

<span data-ttu-id="5b7cb-148">El puntero actual del búfer de seguimiento de eventos apunta a la dirección de la entrada de seguimiento más antigua.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-148">The event trace buffer current pointer points to the address of the oldest trace entry.</span></span> <span data-ttu-id="5b7cb-149">Dado que las entradas de seguimiento se mantienen en una lista circular, el puntero actual del búfer también representa la entrada de seguimiento siguiente que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-149">Since the trace entries are maintained in a circular list, the current buffer pointer is also represents the next trace entry to be written.</span></span> |

## <a name="event-trace-object-registry"></a><span data-ttu-id="5b7cb-150">Registro de objeto del seguimiento de eventos</span><span class="sxs-lookup"><span data-stu-id="5b7cb-150">Event Trace Object Registry</span></span>

<span data-ttu-id="5b7cb-151">El registro de objeto del seguimiento de eventos contiene \***n** _ entradas del registro de objeto que corresponden a los objetos creados por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-151">The event trace object registry contains \***n** _ object registry entries that correspond to the objects created by the application.</span></span> <span data-ttu-id="5b7cb-152">El propósito principal del registro de objeto es que las herramientas de análisis externo correlacionen los nombres de objetos reales con las direcciones de objetos de las entradas del búfer de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-152">The main purpose of the object registry is for external analysis tools to correlate actual object names with the object addresses of the trace buffer entries.</span></span> <span data-ttu-id="5b7cb-153">La aplicación especifica el número de entradas del registro en la llamada _ \*_tx_trace_enable_\*\*.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-153">The number of registry entries is specified by the application in the _ *_tx_trace_enable_*\* call.</span></span>

<span data-ttu-id="5b7cb-154">Cada entrada del registro de objeto contiene información sobre un objeto ThreadX específico que la aplicación creó previamente.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-154">Each object register entry contains information about a specific ThreadX object previously created by the application.</span></span> <span data-ttu-id="5b7cb-155">La estructura de datos siguiente define cada entrada del registro de objeto:</span><span class="sxs-lookup"><span data-stu-id="5b7cb-155">The following data structure defines each object registry entry:</span></span>

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

### <a name="object-available-flag"></a><span data-ttu-id="5b7cb-156">Marca de objeto disponible</span><span class="sxs-lookup"><span data-stu-id="5b7cb-156">Object Available Flag</span></span>

<span data-ttu-id="5b7cb-157">La marca de objeto disponible está establecida en 1 si la entrada del registro de objeto está disponible.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-157">The object available flag is set to 1 if the object registry entry is available.</span></span> <span data-ttu-id="5b7cb-158">De lo contrario, si el valor no es 1, la entrada del registro de objeto no está disponible.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-158">Otherwise, if the value is not 1, the object registry entry is not available.</span></span> <span data-ttu-id="5b7cb-159">Tenga en cuenta que la entrada todavía puede contener información válida, aunque esté disponible.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-159">Note that the entry could still contain valid information even though it is available.</span></span>

### <a name="object-entry-type"></a><span data-ttu-id="5b7cb-160">Tipo de entrada de objeto</span><span class="sxs-lookup"><span data-stu-id="5b7cb-160">Object Entry Type</span></span>

<span data-ttu-id="5b7cb-161">El tipo de entrada de objeto identifica el tipo de objeto de esta entrada.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-161">The object entry type identifies the type of object in this entry.</span></span> <span data-ttu-id="5b7cb-162">A continuación se muestra una lista de los tipos de objetos válidos:</span><span class="sxs-lookup"><span data-stu-id="5b7cb-162">The following is a list of the valid object types:</span></span>

| <span data-ttu-id="5b7cb-163">**Valor**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-163">**Value**</span></span> | <span data-ttu-id="5b7cb-164">**Tipo de objeto**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-164">**Object Type**</span></span> |
|---------- | --------------- |
| <span data-ttu-id="5b7cb-165">0</span><span class="sxs-lookup"><span data-stu-id="5b7cb-165">0</span></span>         | <span data-ttu-id="5b7cb-166">No válido</span><span class="sxs-lookup"><span data-stu-id="5b7cb-166">Not Valid</span></span>       |
| <span data-ttu-id="5b7cb-167">1</span><span class="sxs-lookup"><span data-stu-id="5b7cb-167">1</span></span>         | <span data-ttu-id="5b7cb-168">Thread</span><span class="sxs-lookup"><span data-stu-id="5b7cb-168">Thread</span></span>          |
| <span data-ttu-id="5b7cb-169">2</span><span class="sxs-lookup"><span data-stu-id="5b7cb-169">2</span></span>         | <span data-ttu-id="5b7cb-170">Temporizador</span><span class="sxs-lookup"><span data-stu-id="5b7cb-170">Timer</span></span> |
| <span data-ttu-id="5b7cb-171">3</span><span class="sxs-lookup"><span data-stu-id="5b7cb-171">3</span></span>         | <span data-ttu-id="5b7cb-172">Cola</span><span class="sxs-lookup"><span data-stu-id="5b7cb-172">Queue</span></span> |
| <span data-ttu-id="5b7cb-173">4</span><span class="sxs-lookup"><span data-stu-id="5b7cb-173">4</span></span>         | <span data-ttu-id="5b7cb-174">Semaphore</span><span class="sxs-lookup"><span data-stu-id="5b7cb-174">Semaphore</span></span> |
| <span data-ttu-id="5b7cb-175">5</span><span class="sxs-lookup"><span data-stu-id="5b7cb-175">5</span></span>         | <span data-ttu-id="5b7cb-176">Mutex</span><span class="sxs-lookup"><span data-stu-id="5b7cb-176">Mutex</span></span> |
| <span data-ttu-id="5b7cb-177">6</span><span class="sxs-lookup"><span data-stu-id="5b7cb-177">6</span></span>         | <span data-ttu-id="5b7cb-178">Grupo de marcas de eventos</span><span class="sxs-lookup"><span data-stu-id="5b7cb-178">Event Flags Group</span></span> |
| <span data-ttu-id="5b7cb-179">7</span><span class="sxs-lookup"><span data-stu-id="5b7cb-179">7</span></span>         | <span data-ttu-id="5b7cb-180">Grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="5b7cb-180">Block Pool</span></span> |
| <span data-ttu-id="5b7cb-181">8</span><span class="sxs-lookup"><span data-stu-id="5b7cb-181">8</span></span>         | <span data-ttu-id="5b7cb-182">Grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="5b7cb-182">Byte Pool</span></span> |
| <span data-ttu-id="5b7cb-183">9</span><span class="sxs-lookup"><span data-stu-id="5b7cb-183">9</span></span>         | <span data-ttu-id="5b7cb-184">../media</span><span class="sxs-lookup"><span data-stu-id="5b7cb-184">../media</span></span> |
| <span data-ttu-id="5b7cb-185">10</span><span class="sxs-lookup"><span data-stu-id="5b7cb-185">10</span></span>        | <span data-ttu-id="5b7cb-186">Archivo</span><span class="sxs-lookup"><span data-stu-id="5b7cb-186">File</span></span> |
| <span data-ttu-id="5b7cb-187">11</span><span class="sxs-lookup"><span data-stu-id="5b7cb-187">11</span></span>        | <span data-ttu-id="5b7cb-188">IP</span><span class="sxs-lookup"><span data-stu-id="5b7cb-188">IP</span></span> |
| <span data-ttu-id="5b7cb-189">12</span><span class="sxs-lookup"><span data-stu-id="5b7cb-189">12</span></span>        | <span data-ttu-id="5b7cb-190">Grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="5b7cb-190">Packet Pool</span></span> |
| <span data-ttu-id="5b7cb-191">13</span><span class="sxs-lookup"><span data-stu-id="5b7cb-191">13</span></span>        | <span data-ttu-id="5b7cb-192">Socket TCP</span><span class="sxs-lookup"><span data-stu-id="5b7cb-192">TCP Socket</span></span> |
| <span data-ttu-id="5b7cb-193">14</span><span class="sxs-lookup"><span data-stu-id="5b7cb-193">14</span></span>        | <span data-ttu-id="5b7cb-194">Socket UDP</span><span class="sxs-lookup"><span data-stu-id="5b7cb-194">UDP Socket</span></span> |
| <span data-ttu-id="5b7cb-195">15-20</span><span class="sxs-lookup"><span data-stu-id="5b7cb-195">15-20</span></span>     | <span data-ttu-id="5b7cb-196">Reservado</span><span class="sxs-lookup"><span data-stu-id="5b7cb-196">Reserved</span></span> |  
| <span data-ttu-id="5b7cb-197">21</span><span class="sxs-lookup"><span data-stu-id="5b7cb-197">21</span></span>        | <span data-ttu-id="5b7cb-198">API de pila de host USB</span><span class="sxs-lookup"><span data-stu-id="5b7cb-198">USB Host Stack Device</span></span> |
| <span data-ttu-id="5b7cb-199">22</span><span class="sxs-lookup"><span data-stu-id="5b7cb-199">22</span></span>        | <span data-ttu-id="5b7cb-200">Interfaz de pila de host USB</span><span class="sxs-lookup"><span data-stu-id="5b7cb-200">USB Host Stack Interface</span></span> |
| <span data-ttu-id="5b7cb-201">23</span><span class="sxs-lookup"><span data-stu-id="5b7cb-201">23</span></span>        | <span data-ttu-id="5b7cb-202">Punto de conexión de host USB</span><span class="sxs-lookup"><span data-stu-id="5b7cb-202">USB Host Endpoint</span></span> |
| <span data-ttu-id="5b7cb-203">24</span><span class="sxs-lookup"><span data-stu-id="5b7cb-203">24</span></span>        | <span data-ttu-id="5b7cb-204">Clase de host USB</span><span class="sxs-lookup"><span data-stu-id="5b7cb-204">USB Host Class</span></span> |
| <span data-ttu-id="5b7cb-205">25</span><span class="sxs-lookup"><span data-stu-id="5b7cb-205">25</span></span>        | <span data-ttu-id="5b7cb-206">Dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="5b7cb-206">USB Device</span></span> |
| <span data-ttu-id="5b7cb-207">26</span><span class="sxs-lookup"><span data-stu-id="5b7cb-207">26</span></span>        | <span data-ttu-id="5b7cb-208">Interfaz del dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="5b7cb-208">USB Device Interface</span></span> |
| <span data-ttu-id="5b7cb-209">27</span><span class="sxs-lookup"><span data-stu-id="5b7cb-209">27</span></span>        | <span data-ttu-id="5b7cb-210">Punto de conexión de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="5b7cb-210">USB Device Endpoint</span></span> |
| <span data-ttu-id="5b7cb-211">28</span><span class="sxs-lookup"><span data-stu-id="5b7cb-211">28</span></span>        | <span data-ttu-id="5b7cb-212">Clase de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="5b7cb-212">USB Device Class</span></span> |

### <a name="object-pointer"></a><span data-ttu-id="5b7cb-213">Puntero de objeto</span><span class="sxs-lookup"><span data-stu-id="5b7cb-213">Object Pointer</span></span>

<span data-ttu-id="5b7cb-214">El puntero de objeto especifica la dirección del objeto que se usa para obtener acceso al objeto mediante la API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-214">The object pointer specifies the object address that is used for accessing the object using the ThreadX API.</span></span>

### <a name="object-reserved-fields"></a><span data-ttu-id="5b7cb-215">Campos reservados del objeto</span><span class="sxs-lookup"><span data-stu-id="5b7cb-215">Object Reserved Fields</span></span>

<span data-ttu-id="5b7cb-216">Para todos los objetos que no son subprocesos, estos campos reservados deben ser 0.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-216">For all objects other than threads, these reserved fields should be 0.</span></span> <span data-ttu-id="5b7cb-217">En el caso de los subprocesos, la prioridad del subproceso en el momento en que se escribe en el registro se coloca en estos dos campos reservados.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-217">For threads, the priority of the thread at the time it is entered into the registry is placed in these two reserved fields.</span></span>

### <a name="object-parameters"></a><span data-ttu-id="5b7cb-218">Parámetros del objeto</span><span class="sxs-lookup"><span data-stu-id="5b7cb-218">Object Parameters</span></span>

<span data-ttu-id="5b7cb-219">Los parámetros del objeto contienen información complementaria sobre el objeto.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-219">The object parameters contain supplemental information about the object.</span></span> <span data-ttu-id="5b7cb-220">A continuación se describe la información complementaria para cada objeto ThreadX:</span><span class="sxs-lookup"><span data-stu-id="5b7cb-220">The following describes the supplemental information for each ThreadX object:</span></span>

| <span data-ttu-id="5b7cb-221">**Tipo de objeto**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-221">**Object Type**</span></span>        | <span data-ttu-id="5b7cb-222">**Parámetro 1**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-222">**Parameter 1**</span></span>  | <span data-ttu-id="5b7cb-223">**Parámetro 2**</span><span class="sxs-lookup"><span data-stu-id="5b7cb-223">**Parameter 2**</span></span> |
|----------------------- | ---------------- | --------------- |
| <span data-ttu-id="5b7cb-224">Thread</span><span class="sxs-lookup"><span data-stu-id="5b7cb-224">Thread</span></span>                 | <span data-ttu-id="5b7cb-225">Inicio de la pila</span><span class="sxs-lookup"><span data-stu-id="5b7cb-225">Stack Start</span></span>      | <span data-ttu-id="5b7cb-226">Tamaño de la pila</span><span class="sxs-lookup"><span data-stu-id="5b7cb-226">Stack Size</span></span> |
| <span data-ttu-id="5b7cb-227">Temporizador</span><span class="sxs-lookup"><span data-stu-id="5b7cb-227">Timer</span></span>                  | <span data-ttu-id="5b7cb-228">Tics iniciales</span><span class="sxs-lookup"><span data-stu-id="5b7cb-228">Initial Ticks</span></span> | <span data-ttu-id="5b7cb-229">Reprogramación de tics</span><span class="sxs-lookup"><span data-stu-id="5b7cb-229">Reschedule Ticks</span></span> |
| <span data-ttu-id="5b7cb-230">Cola</span><span class="sxs-lookup"><span data-stu-id="5b7cb-230">Queue</span></span>                  | <span data-ttu-id="5b7cb-231">Tamaño de cola</span><span class="sxs-lookup"><span data-stu-id="5b7cb-231">Queue Size</span></span> | <span data-ttu-id="5b7cb-232">Tamaño de los mensajes</span><span class="sxs-lookup"><span data-stu-id="5b7cb-232">Message Size</span></span> |
| <span data-ttu-id="5b7cb-233">Semaphore</span><span class="sxs-lookup"><span data-stu-id="5b7cb-233">Semaphore</span></span>              | <span data-ttu-id="5b7cb-234">Instancias iniciales</span><span class="sxs-lookup"><span data-stu-id="5b7cb-234">Initial Instances</span></span> | - |
| <span data-ttu-id="5b7cb-235">Mutex</span><span class="sxs-lookup"><span data-stu-id="5b7cb-235">Mutex</span></span>                  | <span data-ttu-id="5b7cb-236">Marca de herencia</span><span class="sxs-lookup"><span data-stu-id="5b7cb-236">Inheritance Flag</span></span> | - |
| <span data-ttu-id="5b7cb-237">Grupo de marcas de eventos</span><span class="sxs-lookup"><span data-stu-id="5b7cb-237">Event Flags Group</span></span>      | - | - |
| <span data-ttu-id="5b7cb-238">Grupo de bloques</span><span class="sxs-lookup"><span data-stu-id="5b7cb-238">Block Pool</span></span>             | <span data-ttu-id="5b7cb-239">Total de bloques</span><span class="sxs-lookup"><span data-stu-id="5b7cb-239">Total Blocks</span></span> | <span data-ttu-id="5b7cb-240">Tamaño de bloque</span><span class="sxs-lookup"><span data-stu-id="5b7cb-240">Block Size</span></span> |
| <span data-ttu-id="5b7cb-241">Grupo de bytes</span><span class="sxs-lookup"><span data-stu-id="5b7cb-241">Byte Pool</span></span>              | <span data-ttu-id="5b7cb-242">Número total de bytes</span><span class="sxs-lookup"><span data-stu-id="5b7cb-242">Total Bytes</span></span> | - |
| <span data-ttu-id="5b7cb-243">../media</span><span class="sxs-lookup"><span data-stu-id="5b7cb-243">../media</span></span>                  | <span data-ttu-id="5b7cb-244">Tamaño de la caché FAT</span><span class="sxs-lookup"><span data-stu-id="5b7cb-244">Fat Cache Size</span></span> | <span data-ttu-id="5b7cb-245">Tamaño de la caché de sector</span><span class="sxs-lookup"><span data-stu-id="5b7cb-245">Sector Cache Size</span></span> |
| <span data-ttu-id="5b7cb-246">Archivo</span><span class="sxs-lookup"><span data-stu-id="5b7cb-246">File</span></span>                   | - | - |
| <span data-ttu-id="5b7cb-247">IP</span><span class="sxs-lookup"><span data-stu-id="5b7cb-247">IP</span></span>                     | <span data-ttu-id="5b7cb-248">Inicio de la pila</span><span class="sxs-lookup"><span data-stu-id="5b7cb-248">Stack Start</span></span> | <span data-ttu-id="5b7cb-249">Tamaño de la pila</span><span class="sxs-lookup"><span data-stu-id="5b7cb-249">Stack Size</span></span> |
| <span data-ttu-id="5b7cb-250">Grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="5b7cb-250">Packet Pool</span></span>            | <span data-ttu-id="5b7cb-251">Tamaño del paquete</span><span class="sxs-lookup"><span data-stu-id="5b7cb-251">Packet Size</span></span> | <span data-ttu-id="5b7cb-252">Número de paquetes</span><span class="sxs-lookup"><span data-stu-id="5b7cb-252">Number of Packets</span></span> |
| <span data-ttu-id="5b7cb-253">Socket TCP</span><span class="sxs-lookup"><span data-stu-id="5b7cb-253">TCP Socket</span></span>             | <span data-ttu-id="5b7cb-254">IP address (Dirección IP)</span><span class="sxs-lookup"><span data-stu-id="5b7cb-254">IP address</span></span> | <span data-ttu-id="5b7cb-255">Tamaño de ventana</span><span class="sxs-lookup"><span data-stu-id="5b7cb-255">Window Size</span></span> |
| <span data-ttu-id="5b7cb-256">Socket UDP</span><span class="sxs-lookup"><span data-stu-id="5b7cb-256">UDP Socket</span></span>             | <span data-ttu-id="5b7cb-257">IP address (Dirección IP)</span><span class="sxs-lookup"><span data-stu-id="5b7cb-257">IP address</span></span> | <span data-ttu-id="5b7cb-258">Cola RX máxima</span><span class="sxs-lookup"><span data-stu-id="5b7cb-258">RX Queue Max</span></span> |

### <a name="object-name"></a><span data-ttu-id="5b7cb-259">Nombre de objeto</span><span class="sxs-lookup"><span data-stu-id="5b7cb-259">Object Name</span></span>

<span data-ttu-id="5b7cb-260">El nombre de objeto contiene el nombre del objeto ThreadX.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-260">The object name contains the name of the ThreadX object.</span></span> <span data-ttu-id="5b7cb-261">El nombre es el nombre que se proporcionó a ThreadX en el momento en que se creó el objeto.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-261">The name is the name provided to ThreadX at the time the object was created.</span></span> <span data-ttu-id="5b7cb-262">De manera predeterminada, el nombre del objeto tiene un máximo de 32 caracteres.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-262">By default, the object name has a maximum of 32 characters.</span></span> <span data-ttu-id="5b7cb-263">Los nombres reales con más de 32 caracteres se truncan.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-263">Actual names greater than 32 characters are truncated.</span></span>

## <a name="event-trace-entries"></a><span data-ttu-id="5b7cb-264">Entradas del seguimiento de eventos</span><span class="sxs-lookup"><span data-stu-id="5b7cb-264">Event Trace Entries</span></span>

<span data-ttu-id="5b7cb-265">Las entradas de seguimiento de eventos se encuentran en la parte inferior del búfer de seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-265">The event trace entries are found in the bottom portion of the event trace buffer.</span></span> <span data-ttu-id="5b7cb-266">Las entradas se mantienen en una lista circular, con el puntero de entrada actual apuntando a la entrada más antigua.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-266">The entries are maintained in a circular list, with the current entry pointer pointing to the oldest entry.</span></span> <span data-ttu-id="5b7cb-267">La llamada ***tx_trace_enable*** calcula el número de entradas de la lista.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-267">The number of entries in the list is calculated by the ***tx_trace_enable*** call.</span></span>

<span data-ttu-id="5b7cb-268">Cada entrada del registro de objeto contiene información sobre un evento de seguimiento ThreadX específico.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-268">Each object register entry contains information about a specific ThreadX trace event.</span></span> <span data-ttu-id="5b7cb-269">La estructura de datos siguiente define cada entrada de evento de seguimiento:</span><span class="sxs-lookup"><span data-stu-id="5b7cb-269">The following data structure defines each trace event entry:</span></span>

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

### <a name="thread-pointer"></a><span data-ttu-id="5b7cb-270">Puntero de subproceso</span><span class="sxs-lookup"><span data-stu-id="5b7cb-270">Thread Pointer</span></span>

<span data-ttu-id="5b7cb-271">El puntero de subproceso contiene la dirección del subproceso que se ejecuta en el momento de este evento.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-271">The thread pointer contains the address of the thread running at the time of this event.</span></span> <span data-ttu-id="5b7cb-272">Si el evento se produjo durante la inicialización (sin ningún subproceso en ejecución), el valor de este puntero es 0xF0F0F0F0.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-272">If the event occurred during initialization (no thread running), the value of this pointer is 0xF0F0F0F0.</span></span> <span data-ttu-id="5b7cb-273">Si el evento se produjo durante una rutina de servicio de interrupción (ISR), el valor de este puntero es 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-273">If the event occurred during an Interrupt Service Routine (ISR), the value of this pointer is 0xFFFFFFFF.</span></span> <span data-ttu-id="5b7cb-274">Si todavía no se usa la entrada, el valor de este puntero es 0.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-274">If the entry has not yet been used, the value of this pointer is 0.</span></span>

### <a name="thread-priority"></a><span data-ttu-id="5b7cb-275">Prioridad del subproceso</span><span class="sxs-lookup"><span data-stu-id="5b7cb-275">Thread Priority</span></span>

<span data-ttu-id="5b7cb-276">El campo de prioridad del subproceso contiene la prioridad del subproceso y el umbral de preferencia del subproceso que estaba en ejecución en el momento de este evento.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-276">The thread priority field contains the thread priority and preemption-threshold of the thread that was running at the time of this event.</span></span> <span data-ttu-id="5b7cb-277">Si hay un contexto de interrupción (el puntero de subproceso es 0xFFFFFFFF), la prioridad no es el valor de este campo sino que, en su lugar, el valor de ***_tx_thread_current_ptr*** en el momento del evento.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-277">If an interrupt context is present (thread pointer is 0xFFFFFFFF), the value of this field is not the priority but instead the value of ***_tx_thread_current_ptr*** at the time of the event.</span></span> <span data-ttu-id="5b7cb-278">De lo contrario, el valor de este campo es 0.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-278">Otherwise, the value of this field is 0.</span></span>

### <a name="event-id"></a><span data-ttu-id="5b7cb-279">Id. de evento</span><span class="sxs-lookup"><span data-stu-id="5b7cb-279">Event ID</span></span>

<span data-ttu-id="5b7cb-280">El id. de evento especifica el evento que tuvo lugar.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-280">The event ID specifies the event that took place.</span></span> <span data-ttu-id="5b7cb-281">Los id. de evento de seguimiento ThreadX válidos van de 1 a 1024.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-281">Valid ThreadX trace event IDs range from 1 through 1024.</span></span> <span data-ttu-id="5b7cb-282">Los valores que comienzan en 1025 y superiores están reservados para los eventos específicos del usuario.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-282">Values starting at 1025 and above are reserved for user-specific events.</span></span> <span data-ttu-id="5b7cb-283">Consulte el archivo ***tx_trace.h*** para obtener la definición completa de los id. de evento ThreadX.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-283">Please refer to the ***tx_trace.h*** file for the complete definition of ThreadX event IDs.</span></span></td>

### <a name="information-fields-1-4"></a><span data-ttu-id="5b7cb-284">Campos de información (1 a 4)</span><span class="sxs-lookup"><span data-stu-id="5b7cb-284">Information Fields (1-4)</span></span>

<span data-ttu-id="5b7cb-285">Los campos de información contienen información adicional sobre el evento específico.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-285">The information fields contain additional information about the specific event.</span></span> <span data-ttu-id="5b7cb-286">Consulte el archivo ***tx_trace. h*** para obtener una descripción completa de los campos de información de cada uno de los id. de evento ThreadX definidos.</span><span class="sxs-lookup"><span data-stu-id="5b7cb-286">Please refer to the ***tx_trace.h*** file for the complete description of the information fields for each of the defined ThreadX event IDs.</span></span>