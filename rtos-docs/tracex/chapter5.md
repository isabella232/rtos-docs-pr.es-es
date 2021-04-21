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
# <a name="chapter-5---generating-trace-buffers"></a><span data-ttu-id="310c2-103">Capítulo 5: Generación de búferes de seguimiento</span><span class="sxs-lookup"><span data-stu-id="310c2-103">Chapter 5 - Generating trace buffers</span></span>

<span data-ttu-id="310c2-104">En este capítulo se incluye una descripción sobre cómo crear un búfer de eventos de Azure RTOS TraceX y también se describe el formato subyacente del búfer.</span><span class="sxs-lookup"><span data-stu-id="310c2-104">This chapter contains a description about how to build a Azure RTOS TraceX event buffer and also describes the underlying format of the buffer.</span></span>

## <a name="threadx-event-trace-support"></a><span data-ttu-id="310c2-105">Compatibilidad con el seguimiento de eventos de ThreadX</span><span class="sxs-lookup"><span data-stu-id="310c2-105">ThreadX Event Trace Support</span></span>

<span data-ttu-id="310c2-106">ThreadX proporciona compatibilidad integrada con el seguimiento de eventos para todos los servicios de ThreadX, cambios de estado de subprocesos y eventos definidos por el usuario.</span><span class="sxs-lookup"><span data-stu-id="310c2-106">ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="310c2-107">La funcionalidad de seguimiento de eventos de ThreadX se ha diseñado principalmente como una herramienta de análisis posterior para analizar las últimas actividades "n" en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="310c2-107">The ThreadX event-trace capability is primarily designed as a post-mortem tool to analyze the last "n" activities in the application.</span></span> <span data-ttu-id="310c2-108">A partir de esta información, el desarrollador puede detectar problemas y posibles objetivos de optimización.</span><span class="sxs-lookup"><span data-stu-id="310c2-108">From this information, the developer may spot problems and/or potential targets of optimization.</span></span>

<span data-ttu-id="310c2-109">TraceX muestra gráficamente el búfer de seguimiento de eventos compilado por ThreadX.</span><span class="sxs-lookup"><span data-stu-id="310c2-109">TraceX graphically displays the event trace buffer built by ThreadX.</span></span> <span data-ttu-id="310c2-110">A continuación se describe cómo compilar el búfer y se describe el formato subyacente del búfer.</span><span class="sxs-lookup"><span data-stu-id="310c2-110">The following describes how to build the buffer and describes the underlying format of the buffer.</span></span>

## <a name="enabling-event-trace"></a><span data-ttu-id="310c2-111">Activación del seguimiento de eventos</span><span class="sxs-lookup"><span data-stu-id="310c2-111">Enabling Event Trace</span></span>

<span data-ttu-id="310c2-112">Para habilitar el seguimiento de eventos, defina las constantes de marca de tiempo, compile la biblioteca ThreadX con **TX_ENABLE_EVENT_TRACE** definido y habilite el seguimiento llamando a la función **tx_trace_enable**.</span><span class="sxs-lookup"><span data-stu-id="310c2-112">To enable event trace, define the time-stamp constants, build the ThreadX library with **TX_ENABLE_EVENT_TRACE** defined, and enable tracing by calling the **tx_trace_enable** function.</span></span>

## <a name="defining-time-stamp-constants"></a><span data-ttu-id="310c2-113">Definición de constantes de marca de tiempo</span><span class="sxs-lookup"><span data-stu-id="310c2-113">Defining Time-Stamp Constants</span></span>

<span data-ttu-id="310c2-114">Las constantes de marca de tiempo están diseñadas para proporcionar al desarrollador el control sobre la marca de tiempo usada en las entradas de seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-114">The time-stamp constants are designed to provide the developer control over the time-stamp used in the event trace entries.</span></span> <span data-ttu-id="310c2-115">Las dos constantes de marca de tiempo y sus valores predeterminados son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="310c2-115">The two time-stamp constants and their default values are as follows:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

<span data-ttu-id="310c2-116">Las constantes anteriores se definen en **tx_port.h** y crean una marca de tiempo "falsa" que simplemente incrementa en uno en cada evento.</span><span class="sxs-lookup"><span data-stu-id="310c2-116">The above constants are defined in **tx_port.h** and create a "fake" time-stamp that simply increments by one on each event.</span></span> <span data-ttu-id="310c2-117">El siguiente es un ejemplo de una definición de marca de tiempo real:</span><span class="sxs-lookup"><span data-stu-id="310c2-117">The following is an example of an actual timestamp definition:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

<span data-ttu-id="310c2-118">Las constantes anteriores especifican un temporizador de 32 bits que se obtiene al leer la dirección 0x13000004.</span><span class="sxs-lookup"><span data-stu-id="310c2-118">The above constants specify a 32-bit timer that is obtained by reading the address 0x13000004.</span></span> <span data-ttu-id="310c2-119">La mayoría de las marcas de tiempo específicas de la aplicación se deben configurar de manera similar.</span><span class="sxs-lookup"><span data-stu-id="310c2-119">Most application specific time-stamps should be setup in a similar fashion.</span></span>

## <a name="exporting-the-trace-buffer"></a><span data-ttu-id="310c2-120">Exportación del búfer de seguimiento</span><span class="sxs-lookup"><span data-stu-id="310c2-120">Exporting the Trace Buffer</span></span>

<span data-ttu-id="310c2-121">TraceX necesita el búfer de seguimiento en un formato de archivo binario, Intel HEX o Motorola S-Record en el host.</span><span class="sxs-lookup"><span data-stu-id="310c2-121">TraceX needs the trace buffer in a binary, Intel HEX, or Motorola S-Record file format on the host.</span></span> <span data-ttu-id="310c2-122">La manera más sencilla de lograrlo es detener el destino e indicar al depurador que vuelque el área de memoria que proporcionó para la función ***tx_trace_enable*** en un archivo en el host.</span><span class="sxs-lookup"><span data-stu-id="310c2-122">The easiest way to accomplish this is to stop the target and instruct your debugger to dump the memory area you supplied to ***tx_trace_enable*** function into a file on the host.</span></span>

> [!WARNING]
><span data-ttu-id="310c2-123">***Tenga cuidado de no detener el destino dentro del propio código de recopilación de seguimiento. Si lo hace, puede producir información de seguimiento no válida. Si el programa se detiene dentro de ThreadX, es mejor desplazarse por las macros de inserción de seguimiento antes de volcar el búfer de seguimiento.***</span><span class="sxs-lookup"><span data-stu-id="310c2-123">***Be careful not to stop the target within a trace gathering code itself. Doing so can cause invalid trace information. If the program is halted within ThreadX, it is best to step over any trace insert macro before dumping the trace buffer.***</span></span>

> [!IMPORTANT]
> <span data-ttu-id="310c2-124">*En el apéndice D se muestra cómo volcar el búfer de seguimiento desde una variedad de herramientas de desarrollo.*</span><span class="sxs-lookup"><span data-stu-id="310c2-124">*Appendix D shows how to dump the trace buffer from within a variety of development tools.*</span></span>

## <a name="extended-event-trace-api"></a><span data-ttu-id="310c2-125">API de seguimiento de eventos extendidos</span><span class="sxs-lookup"><span data-stu-id="310c2-125">Extended Event Trace API</span></span>

<span data-ttu-id="310c2-126">Cuando ThreadX se compila con **TX_ENABLE_EVENT_TRACE** definido, las siguientes API de seguimiento de eventos están disponibles para la aplicación:</span><span class="sxs-lookup"><span data-stu-id="310c2-126">When ThreadX is built with **TX_ENABLE_EVENT_TRACE** defined, the following new event trace APIs are available to the application:</span></span>

- <span data-ttu-id="310c2-127">tx_trace_enable: *Activación del seguimiento de eventos*</span><span class="sxs-lookup"><span data-stu-id="310c2-127">tx_trace_enable: *Enable event tracing*</span></span>
- <span data-ttu-id="310c2-128">tx_trace_event_filter: *Filtrado de eventos especificados*</span><span class="sxs-lookup"><span data-stu-id="310c2-128">tx_trace_event_filter: *Filter specified event(s)*</span></span>
- <span data-ttu-id="310c2-129">tx_trace_event_unfilter: *Anulación del filtrado de eventos especificados*</span><span class="sxs-lookup"><span data-stu-id="310c2-129">tx_trace_event_unfilter: *Unfilter specified event(s)*</span></span>
- <span data-ttu-id="310c2-130">tx_trace_disable: *Desactivación del seguimiento de eventos*</span><span class="sxs-lookup"><span data-stu-id="310c2-130">tx_trace_disable: *Disable event tracing*</span></span>
- <span data-ttu-id="310c2-131">tx_trace_isr_enter_insert: *Inserción del evento de seguimiento de entrada de ISR*</span><span class="sxs-lookup"><span data-stu-id="310c2-131">tx_trace_isr_enter_insert: *Insert ISR enter trace event*</span></span>
- <span data-ttu-id="310c2-132">tx_trace_isr_exit_insert: *Inserción del evento de seguimiento de salida de ISR*</span><span class="sxs-lookup"><span data-stu-id="310c2-132">tx_trace_isr_exit_insert: *Insert ISR exit trace event*</span></span>
- <span data-ttu-id="310c2-133">tx_trace_buffer_full_notify: *Registro de la devolución de llamada de aplicación completa del búfer de seguimiento*</span><span class="sxs-lookup"><span data-stu-id="310c2-133">tx_trace_buffer_full_notify: *Register trace buffer full application callback*</span></span>
- <span data-ttu-id="310c2-134">tx_trace_user_event_insert: *Inserción de evento de usuario*</span><span class="sxs-lookup"><span data-stu-id="310c2-134">tx_trace_user_event_insert: *Insert user event*</span></span>

### <a name="tx_trace_enable"></a><span data-ttu-id="310c2-135">tx_trace_enable</span><span class="sxs-lookup"><span data-stu-id="310c2-135">tx_trace_enable</span></span>

<span data-ttu-id="310c2-136">Activación del seguimiento de eventos</span><span class="sxs-lookup"><span data-stu-id="310c2-136">Enable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="310c2-137">Prototipo</span><span class="sxs-lookup"><span data-stu-id="310c2-137">Prototype</span></span>

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a><span data-ttu-id="310c2-138">Descripción</span><span class="sxs-lookup"><span data-stu-id="310c2-138">Description</span></span>
<span data-ttu-id="310c2-139">Este servicio habilita el seguimiento de eventos dentro de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="310c2-139">This service enables event tracing inside ThreadX.</span></span> <span data-ttu-id="310c2-140">La aplicación suministra el búfer de seguimiento y el número máximo de objetos de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="310c2-140">The trace buffer and the maximum number of ThreadX objects are supplied by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="310c2-141">La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-141">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="310c2-142">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="310c2-142">Input Parameters</span></span>

- <span data-ttu-id="310c2-143">**trace_buffer_start**: puntero que señala al inicio del búfer de seguimiento proporcionado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="310c2-143">**trace_buffer_start**: Pointer to the start of the user-supplied trace buffer.</span></span>
- <span data-ttu-id="310c2-144">**trace_buffer_size**: número total de bytes en la memoria para el búfer de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="310c2-144">**trace_buffer_size**: Total number of bytes in the memory for the trace buffer.</span></span> <span data-ttu-id="310c2-145">Cuanto mayor sea el búfer de seguimiento, más entradas podrá almacenar.</span><span class="sxs-lookup"><span data-stu-id="310c2-145">The larger the trace buffer, the more entries it is able to store.</span></span>
- <span data-ttu-id="310c2-146">**registry_entries**: número de objetos de ThreadX de la aplicación que se conservarán en el registro de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="310c2-146">**registry_entries**: Number of application ThreadX objects to keep in the trace registry.</span></span> <span data-ttu-id="310c2-147">El registro se usa para correlacionar las direcciones de objeto con los nombres de objeto.</span><span class="sxs-lookup"><span data-stu-id="310c2-147">The registry is used to correlate object addresses with object names.</span></span> <span data-ttu-id="310c2-148">Esto es muy útil para las herramientas de análisis de seguimiento de GUI.</span><span class="sxs-lookup"><span data-stu-id="310c2-148">This is highly useful for GUI trace analysis tools.</span></span>

#### <a name="return-values"></a><span data-ttu-id="310c2-149">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="310c2-149">Return Values</span></span>

- <span data-ttu-id="310c2-150">**TX_SUCCESS** (0x00): el seguimiento de eventos se ha habilitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="310c2-150">**TX_SUCCESS** (0x00) Successful event trace enable.</span></span>
- <span data-ttu-id="310c2-151">**TX_SIZE_ERROR** (0x05): el tamaño del búfer de seguimiento especificado es demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="310c2-151">**TX_SIZE_ERROR** (0x05) Specified trace buffer size is too small.</span></span> <span data-ttu-id="310c2-152">Debe ser lo suficientemente grande para alojar el encabezado de seguimiento, el registro de objetos y al menos una entrada de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="310c2-152">It must be large enough for the trace header, the object registry, and at least one trace entry.</span></span>
- <span data-ttu-id="310c2-153">**TX_NOT_DONE** (0x20): el seguimiento de eventos ya estaba habilitado.</span><span class="sxs-lookup"><span data-stu-id="310c2-153">**TX_NOT_DONE** (0x20) Event tracing was already enabled.</span></span>
- <span data-ttu-id="310c2-154">**TX_FEATURE_NOT_ENABLED** (0xFF): no se compiló el sistema con el seguimiento habilitado.</span><span class="sxs-lookup"><span data-stu-id="310c2-154">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="310c2-155">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="310c2-155">Allowed From</span></span>

<span data-ttu-id="310c2-156">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="310c2-156">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="310c2-157">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="310c2-157">Example</span></span>

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a><span data-ttu-id="310c2-158">Consulte también</span><span class="sxs-lookup"><span data-stu-id="310c2-158">See Also</span></span>

<span data-ttu-id="310c2-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="310c2-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_filter"></a><span data-ttu-id="310c2-160">tx_trace_event_filter</span><span class="sxs-lookup"><span data-stu-id="310c2-160">tx_trace_event_filter</span></span>

<span data-ttu-id="310c2-161">Filtrado de eventos especificados.</span><span class="sxs-lookup"><span data-stu-id="310c2-161">Filter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="310c2-162">Prototipo</span><span class="sxs-lookup"><span data-stu-id="310c2-162">Prototype</span></span>

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a><span data-ttu-id="310c2-163">Descripción</span><span class="sxs-lookup"><span data-stu-id="310c2-163">Description</span></span>

<span data-ttu-id="310c2-164">Este servicio filtra los eventos especificados para que no se inserten en el búfer de seguimiento activo.</span><span class="sxs-lookup"><span data-stu-id="310c2-164">This service filters the specified event(s) from being inserted into the active trace buffer.</span></span> <span data-ttu-id="310c2-165">Tenga en cuenta que, de forma predeterminada, no se filtra ningún evento después de que se llame a *tx_trace_enable*.</span><span class="sxs-lookup"><span data-stu-id="310c2-165">Note that by default no events are filtered after *tx_trace_enable* is called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="310c2-166">La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-166">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="310c2-167">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="310c2-167">Input Parameters</span></span>

- <span data-ttu-id="310c2-168">**event_filter_bits**: bits que corresponden a los eventos que se van a filtrar.</span><span class="sxs-lookup"><span data-stu-id="310c2-168">**event_filter_bits**: Bits that correspond to events to filter.</span></span> <span data-ttu-id="310c2-169">Se pueden filtrar varios eventos simplemente juntando las constantes adecuadas con or-ing.</span><span class="sxs-lookup"><span data-stu-id="310c2-169">Multiple events may be filtered by simply oring together the appropriate constants.</span></span> <span data-ttu-id="310c2-170">Las constantes válidas para esta variable se definen de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="310c2-170">Valid constants for this variable are defined as follows:</span></span>

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

#### <a name="return-values"></a><span data-ttu-id="310c2-171">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="310c2-171">Return Values</span></span>

- <span data-ttu-id="310c2-172">**TX_SUCCESS** (0x00): filtro de evento correcto.</span><span class="sxs-lookup"><span data-stu-id="310c2-172">**TX_SUCCESS** (0x00) Successful event filter.</span></span>
- <span data-ttu-id="310c2-173">**TX_FEATURE_NOT_ENABLED** (0xFF): no se compiló el sistema con el seguimiento habilitado.</span><span class="sxs-lookup"><span data-stu-id="310c2-173">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="310c2-174">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="310c2-174">Allowed From</span></span>

<span data-ttu-id="310c2-175">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="310c2-175">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="310c2-176">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="310c2-176">Example</span></span>

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="310c2-177">Consulte también</span><span class="sxs-lookup"><span data-stu-id="310c2-177">See Also</span></span>

<span data-ttu-id="310c2-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="310c2-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_unfilter"></a><span data-ttu-id="310c2-179">tx_trace_event_unfilter</span><span class="sxs-lookup"><span data-stu-id="310c2-179">tx_trace_event_unfilter</span></span>

<span data-ttu-id="310c2-180">Anulación del filtrado de eventos especificados.</span><span class="sxs-lookup"><span data-stu-id="310c2-180">Unfilter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="310c2-181">Prototipo</span><span class="sxs-lookup"><span data-stu-id="310c2-181">Prototype</span></span>

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a><span data-ttu-id="310c2-182">Descripción</span><span class="sxs-lookup"><span data-stu-id="310c2-182">Description</span></span>

<span data-ttu-id="310c2-183">Este servicio quita el filtro de los eventos especificados para que se inserten en el búfer de seguimiento activo.</span><span class="sxs-lookup"><span data-stu-id="310c2-183">This service unfilters the specified event(s) such that they will be inserted into the active trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="310c2-184">La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-184">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="310c2-185">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="310c2-185">Input Parameters</span></span>

- <span data-ttu-id="310c2-186">**event_unfilter_bits**: bits que corresponden a los eventos cuyo filtro se va a anular.</span><span class="sxs-lookup"><span data-stu-id="310c2-186">**event_unfilter_bits**: Bits that correspond to events to unfilter.</span></span> <span data-ttu-id="310c2-187">Se puede anular el filtro de varios eventos simplemente juntando las constantes adecuadas con or-ing.</span><span class="sxs-lookup"><span data-stu-id="310c2-187">Multiple events may be unfiltered by simply or-ing together the appropriate constants.</span></span> <span data-ttu-id="310c2-188">Las constantes válidas para esta variable se definen de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="310c2-188">Valid constants for this variable are defined as follows:</span></span>

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

#### <a name="return-values"></a><span data-ttu-id="310c2-189">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="310c2-189">Return Values</span></span>

- <span data-ttu-id="310c2-190">**TX_SUCCESS** (0x00): anulación del filtrado de evento correcto.</span><span class="sxs-lookup"><span data-stu-id="310c2-190">**TX_SUCCESS** (0x00) Successful event unfilter.</span></span>
- <span data-ttu-id="310c2-191">**TX_FEATURE_NOT_ENABLED** (0xFF): no se compiló el sistema con el seguimiento habilitado.</span><span class="sxs-lookup"><span data-stu-id="310c2-191">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="310c2-192">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="310c2-192">Allowed From</span></span>

<span data-ttu-id="310c2-193">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="310c2-193">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="310c2-194">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="310c2-194">Example</span></span>

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="310c2-195">Consulte también</span><span class="sxs-lookup"><span data-stu-id="310c2-195">See Also</span></span>

<span data-ttu-id="310c2-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="310c2-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_disable"></a><span data-ttu-id="310c2-197">tx_trace_disable</span><span class="sxs-lookup"><span data-stu-id="310c2-197">tx_trace_disable</span></span>

#### <a name="disable-event-tracing"></a><span data-ttu-id="310c2-198">Desactivación del seguimiento de eventos</span><span class="sxs-lookup"><span data-stu-id="310c2-198">Disable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="310c2-199">Prototipo</span><span class="sxs-lookup"><span data-stu-id="310c2-199">Prototype</span></span>

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a><span data-ttu-id="310c2-200">Descripción</span><span class="sxs-lookup"><span data-stu-id="310c2-200">Description</span></span>

<span data-ttu-id="310c2-201">Este servicio deshabilita el seguimiento de eventos dentro de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="310c2-201">This service disables event tracing inside ThreadX.</span></span> <span data-ttu-id="310c2-202">Esto puede ser útil si la aplicación quiere inmovilizar el búfer de seguimiento de eventos actual y, posiblemente, transportarlo externamente durante el tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="310c2-202">This can be useful if the application wants to freeze the current event trace buffer and possibly transport it externally during run-time.</span></span> <span data-ttu-id="310c2-203">Una vez deshabilitado, se puede llamar a **tx_trace_enable** para volver a iniciar el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="310c2-203">Once disabled, the **tx_trace_enable** can be called to start tracing again.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="310c2-204">La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-204">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="310c2-205">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="310c2-205">Input Parameters</span></span>

<span data-ttu-id="310c2-206">Ninguno.</span><span class="sxs-lookup"><span data-stu-id="310c2-206">None.</span></span>

#### <a name="return-values"></a><span data-ttu-id="310c2-207">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="310c2-207">Return Values</span></span>

- <span data-ttu-id="310c2-208">**TX_SUCCESS** (0x00): el seguimiento de eventos se ha deshabilitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="310c2-208">**TX_SUCCESS** (0x00) Successful event trace disable.</span></span>
- <span data-ttu-id="310c2-209">**TX_NOT_DONE** (0x20): el seguimiento de eventos no estaba habilitado.</span><span class="sxs-lookup"><span data-stu-id="310c2-209">**TX_NOT_DONE** (0x20) Event tracing was not enabled.</span></span>
- <span data-ttu-id="310c2-210">**TX_FEATURE_NOT_ENABLED** (0xFF): no se compiló el sistema con el seguimiento habilitado.</span><span class="sxs-lookup"><span data-stu-id="310c2-210">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="310c2-211">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="310c2-211">Allowed From</span></span>

<span data-ttu-id="310c2-212">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="310c2-212">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="310c2-213">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="310c2-213">Example</span></span> 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a><span data-ttu-id="310c2-214">Consulte también</span><span class="sxs-lookup"><span data-stu-id="310c2-214">See Also</span></span>

<span data-ttu-id="310c2-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="310c2-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_enter_insert"></a><span data-ttu-id="310c2-216">tx_trace_isr_enter_insert</span><span class="sxs-lookup"><span data-stu-id="310c2-216">tx_trace_isr_enter_insert</span></span>

#### <a name="insert-isr-enter-event"></a><span data-ttu-id="310c2-217">Inserción del evento de entrada de ISR</span><span class="sxs-lookup"><span data-stu-id="310c2-217">Insert ISR enter event</span></span>

#### <a name="prototype"></a><span data-ttu-id="310c2-218">Prototipo</span><span class="sxs-lookup"><span data-stu-id="310c2-218">Prototype</span></span>

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="310c2-219">Descripción</span><span class="sxs-lookup"><span data-stu-id="310c2-219">Description</span></span>

<span data-ttu-id="310c2-220">Este servicio inserta el evento de entrada de ISR en el búfer de seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-220">This service inserts the ISR enter event into the event trace buffer.</span></span> <span data-ttu-id="310c2-221">La aplicación debe llamarla al principio del procesamiento de ISR.</span><span class="sxs-lookup"><span data-stu-id="310c2-221">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="310c2-222">El parámetro proporcionado debe identificar el ISR específico para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="310c2-222">The supplied parameter should identify the specific ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="310c2-223">La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-223">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="310c2-224">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="310c2-224">Input Parameters</span></span> 
- <span data-ttu-id="310c2-225">**isr_id**: valor específico de la aplicación para identificar el ISR.</span><span class="sxs-lookup"><span data-stu-id="310c2-225">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="310c2-226">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="310c2-226">Return Values</span></span>

<span data-ttu-id="310c2-227">**None**</span><span class="sxs-lookup"><span data-stu-id="310c2-227">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="310c2-228">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="310c2-228">Allowed From</span></span> 

<span data-ttu-id="310c2-229">ISR</span><span class="sxs-lookup"><span data-stu-id="310c2-229">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="310c2-230">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="310c2-230">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="310c2-231">Consulte también</span><span class="sxs-lookup"><span data-stu-id="310c2-231">See Also</span></span>

<span data-ttu-id="310c2-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="310c2-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_exit_insert"></a><span data-ttu-id="310c2-233">tx_trace_isr_exit_insert</span><span class="sxs-lookup"><span data-stu-id="310c2-233">tx_trace_isr_exit_insert</span></span>

#### <a name="insert-isr-exit-event"></a><span data-ttu-id="310c2-234">Inserción de evento de salida de ISR</span><span class="sxs-lookup"><span data-stu-id="310c2-234">Insert ISR exit event</span></span>

#### <a name="prototype"></a><span data-ttu-id="310c2-235">Prototipo</span><span class="sxs-lookup"><span data-stu-id="310c2-235">Prototype</span></span>

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="310c2-236">Descripción</span><span class="sxs-lookup"><span data-stu-id="310c2-236">Description</span></span>

<span data-ttu-id="310c2-237">Este servicio inserta el evento de salida de ISR en el búfer de seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-237">This service inserts the ISR entry event into the event trace buffer.</span></span> <span data-ttu-id="310c2-238">La aplicación debe llamarla al principio del procesamiento de ISR.</span><span class="sxs-lookup"><span data-stu-id="310c2-238">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="310c2-239">El parámetro proporcionado debe identificar el ISR para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="310c2-239">The supplied parameter should identify the ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="310c2-240">La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-240">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="310c2-241">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="310c2-241">Input Parameters</span></span> 

- <span data-ttu-id="310c2-242">**isr_id**: valor específico de la aplicación para identificar el ISR.</span><span class="sxs-lookup"><span data-stu-id="310c2-242">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="310c2-243">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="310c2-243">Return Values</span></span>

<span data-ttu-id="310c2-244">**None**</span><span class="sxs-lookup"><span data-stu-id="310c2-244">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="310c2-245">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="310c2-245">Allowed From</span></span>

<span data-ttu-id="310c2-246">ISR</span><span class="sxs-lookup"><span data-stu-id="310c2-246">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="310c2-247">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="310c2-247">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="310c2-248">Consulte también</span><span class="sxs-lookup"><span data-stu-id="310c2-248">See Also</span></span>

<span data-ttu-id="310c2-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="310c2-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_buffer_full_notify"></a><span data-ttu-id="310c2-250">tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="310c2-250">tx_trace_buffer_full_notify</span></span>

#### <a name="register-trace-buffer-full-application-callback"></a><span data-ttu-id="310c2-251">Registro de la devolución de llamada de aplicación completa del búfer de seguimiento</span><span class="sxs-lookup"><span data-stu-id="310c2-251">Register trace buffer full application callback</span></span>

#### <a name="prototype"></a><span data-ttu-id="310c2-252">Prototipo</span><span class="sxs-lookup"><span data-stu-id="310c2-252">Prototype</span></span>

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a><span data-ttu-id="310c2-253">Descripción</span><span class="sxs-lookup"><span data-stu-id="310c2-253">Description</span></span>

<span data-ttu-id="310c2-254">Este servicio registra una función de devolución de llamada de aplicación llamada por ThreadX cuando el búfer de seguimiento se llena.</span><span class="sxs-lookup"><span data-stu-id="310c2-254">This service registers an application callback function that is called by ThreadX when the trace buffer becomes full.</span></span> <span data-ttu-id="310c2-255">A continuación, la aplicación puede optar por deshabilitar el seguimiento o configurar un nuevo búfer de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="310c2-255">The application can then choose to disable tracing and/or possibly setup a new trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="310c2-256">La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-256">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="310c2-257">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="310c2-257">Input Parameters</span></span>

- <span data-ttu-id="310c2-258">**full_buffer_callback**: función de aplicación que se va a llamar cuando el búfer de seguimiento esté lleno.</span><span class="sxs-lookup"><span data-stu-id="310c2-258">**full_buffer_callback**: Application function to call when the trace buffer is full.</span></span> <span data-ttu-id="310c2-259">El valor NULL deshabilita la devolución de llamada de notificación.</span><span class="sxs-lookup"><span data-stu-id="310c2-259">A value of NULL disables the notification callback.</span></span>

#### <a name="return-values"></a><span data-ttu-id="310c2-260">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="310c2-260">Return Values</span></span>

<span data-ttu-id="310c2-261">**None**</span><span class="sxs-lookup"><span data-stu-id="310c2-261">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="310c2-262">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="310c2-262">Allowed From</span></span>

<span data-ttu-id="310c2-263">ISR</span><span class="sxs-lookup"><span data-stu-id="310c2-263">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="310c2-264">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="310c2-264">Example</span></span>

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a><span data-ttu-id="310c2-265">Consulte también</span><span class="sxs-lookup"><span data-stu-id="310c2-265">See Also</span></span>

<span data-ttu-id="310c2-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="310c2-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_user_event_insert"></a><span data-ttu-id="310c2-267">tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="310c2-267">tx_trace_user_event_insert</span></span>

#### <a name="insert-user-event"></a><span data-ttu-id="310c2-268">Inserción de evento de usuario</span><span class="sxs-lookup"><span data-stu-id="310c2-268">Insert user event</span></span>

#### <a name="prototype"></a><span data-ttu-id="310c2-269">Prototipo</span><span class="sxs-lookup"><span data-stu-id="310c2-269">Prototype</span></span>

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a><span data-ttu-id="310c2-270">Descripción</span><span class="sxs-lookup"><span data-stu-id="310c2-270">Description</span></span>

<span data-ttu-id="310c2-271">Este servicio inserta el evento de usuario en el búfer de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="310c2-271">This service inserts the user event into the trace buffer.</span></span> <span data-ttu-id="310c2-272">Los identificadores de evento de usuario deben ser mayores que la constante **TX_TRACE_USER_EVENT_START**, que se establece en 4096.</span><span class="sxs-lookup"><span data-stu-id="310c2-272">User event IDs must be greater than the constant **TX_TRACE_USER_EVENT_START**, which is defined to be 4096.</span></span> <span data-ttu-id="310c2-273">El evento de usuario máximo se define mediante la constante **TX_TRACE_USER_EVENT_END**, que se establece en 65535.</span><span class="sxs-lookup"><span data-stu-id="310c2-273">The maximum user event is defined by the constant **TX_TRACE_USER_EVENT_END**, which is defined to be 65535.</span></span> <span data-ttu-id="310c2-274">Todos los eventos de este intervalo están disponibles para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="310c2-274">All events within this range are available to the application.</span></span> <span data-ttu-id="310c2-275">Los campos de información son específicos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="310c2-275">The information fields are application specific.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="310c2-276">La biblioteca y la aplicación de ThreadX se deben compilar con **TX_ENABLE_EVENT_TRACE** definido para poder usar el seguimiento de eventos.</span><span class="sxs-lookup"><span data-stu-id="310c2-276">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="310c2-277">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="310c2-277">Input Parameters</span></span>

- <span data-ttu-id="310c2-278">**event_id**: identificación de eventos específicos de la aplicación que debe iniciarse en un valor mayor que **TX_TRACE_USER_EVENT_START** y menor o igual que **TX_TRACE_USER_EVENT_END**.</span><span class="sxs-lookup"><span data-stu-id="310c2-278">**event_id**: Application-specific event identification and must start be greater than **TX_TRACE_USER_EVENT_START** and less than or equal to **TX_TRACE_USER_EVENT_END**.</span></span>
- <span data-ttu-id="310c2-279">**info_field_1**: campo de información específica de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="310c2-279">**info_field_1**: Application-specific information field.</span></span>
- <span data-ttu-id="310c2-280">**info_field_2**: campo de información específica de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="310c2-280">**info_field_2**: Application-specific information field.</span></span>
- <span data-ttu-id="310c2-281">**info_field_3**: campo de información específica de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="310c2-281">**info_field_3**: Application-specific information field.</span></span>
- <span data-ttu-id="310c2-282">**info_field_4**: campo de información específica de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="310c2-282">**info_field_4**: Application-specific information field.</span></span>

#### <a name="return-values"></a><span data-ttu-id="310c2-283">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="310c2-283">Return Values</span></span>
- <span data-ttu-id="310c2-284">**TX_SUCCESS** (0x00): inserción de evento de usuario correcta.</span><span class="sxs-lookup"><span data-stu-id="310c2-284">**TX_SUCCESS** (0x00) Successful user event insert.</span></span>
- <span data-ttu-id="310c2-285">**TX_NOT_DONE** (0x20): el seguimiento de eventos no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="310c2-285">**TX_NOT_DONE** (0x20) Event tracing is not enabled.</span></span>
- <span data-ttu-id="310c2-286">**TX_FEATURE_NOT_ENABLED** (0xFF): no se ha compilado el sistema con el seguimiento habilitado.</span><span class="sxs-lookup"><span data-stu-id="310c2-286">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="310c2-287">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="310c2-287">Allowed From</span></span>

<span data-ttu-id="310c2-288">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="310c2-288">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="310c2-289">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="310c2-289">Example</span></span>

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="310c2-290">Consulte también</span><span class="sxs-lookup"><span data-stu-id="310c2-290">See Also</span></span>

<span data-ttu-id="310c2-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="310c2-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span></span>