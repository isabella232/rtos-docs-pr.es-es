---
title: 'Capítulo 1: Introducción al cliente PTP de Azure RTOS NetX Duo'
description: Este capítulo contiene una introducción al cliente PTP de Azure RTOS NetX Duo.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5beec64bd6d74e3bed06be15255d6bd4a940ba64
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814590"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a><span data-ttu-id="3408f-103">Capítulo 1: Introducción al cliente PTP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3408f-103">Chapter 1 - Introduction to Azure RTOS NetX Duo PTP Client</span></span>

<span data-ttu-id="3408f-104">El componente PTP de Azure RTOS NetX Duo implementa la parte de cliente de la versión 2 del Protocolo de tiempo de precisión (PTP), IEEE 1588-2008.</span><span class="sxs-lookup"><span data-stu-id="3408f-104">The Azure RTOS NetX Duo PTP implements the client part of the Precision Time Protocol (PTP) version 2, IEEE 1588-2008.</span></span> <span data-ttu-id="3408f-105">Se usa para sincronizar los relojes entre los MCU de la red local al comunicarse entre sí a través de paquetes de multidifusión IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="3408f-105">It is used to synchronize clocks among MCUs on the local network by communicating each other via IPv4 or IPv6 multicast packets.</span></span>

## <a name="netx-duo-ptp-client-setup"></a><span data-ttu-id="3408f-106">Configuración del cliente PTP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3408f-106">NetX Duo PTP Client Setup</span></span>

<span data-ttu-id="3408f-107">Para que funcione correctamente, el paquete del cliente PTP requiere que ya se haya creado una instancia de IP de NetX DUO.</span><span class="sxs-lookup"><span data-stu-id="3408f-107">In order to function properly, the PTP client package requires that a NetX Duo IP instance has already been created.</span></span>

<span data-ttu-id="3408f-108">De forma predeterminada, el cliente PTP se une al grupo de multidifusión de IPv4.</span><span class="sxs-lookup"><span data-stu-id="3408f-108">By default, the PTP client joins IPv4 multicast group.</span></span> <span data-ttu-id="3408f-109">Para ejecutar el cliente PTP en una red IPv6, `NX_ENABLE_IPV6_MULTICAST` debe definirse al compilar la biblioteca de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3408f-109">In order to run the PTP client on an IPv6 network, `NX_ENABLE_IPV6_MULTICAST` must be defined when building NetX Duo library.</span></span>

<span data-ttu-id="3408f-110">Al crear el cliente PTP, la aplicación debe proporcionar una función de devolución de llamada para controlar las marcas de tiempo de los paquetes entrantes y salientes.</span><span class="sxs-lookup"><span data-stu-id="3408f-110">When creating the PTP client, the application must provide a callback function to handle timestamps of incoming and outgoing packets.</span></span> <span data-ttu-id="3408f-111">Para lograr una alta resolución, recomendamos que las aplicaciones generen marcas de tiempo mediante un temporizador de alta resolución.</span><span class="sxs-lookup"><span data-stu-id="3408f-111">To achieve high resolution, we recommend applications to generate timestamps using a high resolution timer.</span></span> <span data-ttu-id="3408f-112">Para ejecutar PTP en el simulador, se proporciona una implementación basada en software `nx_ptp_client_soft_clock_callback`.</span><span class="sxs-lookup"><span data-stu-id="3408f-112">To run the PTP on simulator, a software-based implementation `nx_ptp_client_soft_clock_callback` is provided.</span></span>

<span data-ttu-id="3408f-113">El cliente PTP requiere un grupo de paquetes para la transmisión de mensajes de PTP.</span><span class="sxs-lookup"><span data-stu-id="3408f-113">The PTP client requires a packet pool for transmitting PTP messages.</span></span> <span data-ttu-id="3408f-114">El tamaño de carga del grupo de paquetes no debe ser inferior a `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE`, que es 108 bytes para IPv4 y 128 bytes si IPv6 está habilitado.</span><span class="sxs-lookup"><span data-stu-id="3408f-114">The payload size of packet pool must be no less than `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE`, which is 108 bytes for IPv4, and 128 bytes if IPv6 is enabled.</span></span>

<span data-ttu-id="3408f-115">Después de crear el cliente PTP, la aplicación puede iniciarlo.</span><span class="sxs-lookup"><span data-stu-id="3408f-115">After creating the PTP Client, the application can start the PTP client.</span></span> <span data-ttu-id="3408f-116">La sincronización se realiza en el subproceso auxiliar de PTP.</span><span class="sxs-lookup"><span data-stu-id="3408f-116">The synchronization is done in the PTP helper thread.</span></span> <span data-ttu-id="3408f-117">Se puede especificar una función de devolución de llamada del evento.</span><span class="sxs-lookup"><span data-stu-id="3408f-117">An event callback function can be specified.</span></span> <span data-ttu-id="3408f-118">Se invocará cuando se produzca cualquiera de los siguientes eventos.</span><span class="sxs-lookup"><span data-stu-id="3408f-118">It will be invoked when any one of the following events happen.</span></span>
* <span data-ttu-id="3408f-119">Se selecciona un maestro.</span><span class="sxs-lookup"><span data-stu-id="3408f-119">A master is selected;</span></span> 
* <span data-ttu-id="3408f-120">Se calibra la hora.</span><span class="sxs-lookup"><span data-stu-id="3408f-120">The time is calibrated.</span></span>
* <span data-ttu-id="3408f-121">Un maestro agota el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="3408f-121">A master times out.</span></span>

## <a name="netx-duo-ptp-client-messages"></a><span data-ttu-id="3408f-122">Mensajes del cliente PTP de en NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3408f-122">NetX Duo PTP Client Messages</span></span>

<span data-ttu-id="3408f-123">El cliente PTP de Next Duo implementa solo el mecanismo de retraso de solicitud-respuesta.</span><span class="sxs-lookup"><span data-stu-id="3408f-123">The NetX Duo PTP client implements the delay request-response mechanism only.</span></span> <span data-ttu-id="3408f-124">El cliente PTP abre dos puertos UDP.</span><span class="sxs-lookup"><span data-stu-id="3408f-124">The PTP client  opens two UDP ports.</span></span> <span data-ttu-id="3408f-125">*319* para el mensaje de **evento** y *320* para el mensaje **general**.</span><span class="sxs-lookup"><span data-stu-id="3408f-125">*319* for **event** message and *320* for **general** message.</span></span> <span data-ttu-id="3408f-126">Hay cinco tipos de mensajes para este mecanismo.</span><span class="sxs-lookup"><span data-stu-id="3408f-126">There are five types of message for this mechanism.</span></span>

* <span data-ttu-id="3408f-127">**Announce**.</span><span class="sxs-lookup"><span data-stu-id="3408f-127">**Announce**.</span></span> <span data-ttu-id="3408f-128">Se trata de un mensaje de evento.</span><span class="sxs-lookup"><span data-stu-id="3408f-128">This is an event message.</span></span> <span data-ttu-id="3408f-129">Se utiliza para la selección del reloj principal.</span><span class="sxs-lookup"><span data-stu-id="3408f-129">It is used for master clock selection.</span></span>
* <span data-ttu-id="3408f-130">**Sync**. Se trata de un mensaje de evento.</span><span class="sxs-lookup"><span data-stu-id="3408f-130">**Sync**. This is an event message.</span></span> <span data-ttu-id="3408f-131">Se utiliza para enviar la marca de tiempo de origen y calcular el retraso de la ruta de maestro a cliente.</span><span class="sxs-lookup"><span data-stu-id="3408f-131">It is used to send origin timestamp and calculate the path delay from master to client.</span></span>
* <span data-ttu-id="3408f-132">**Follow_Up**.</span><span class="sxs-lookup"><span data-stu-id="3408f-132">**Follow_Up**.</span></span> <span data-ttu-id="3408f-133">Se trata de un mensaje general.</span><span class="sxs-lookup"><span data-stu-id="3408f-133">This is a general message.</span></span> <span data-ttu-id="3408f-134">Es opcional y se usa para corregir la marca de tiempo de origen en el mensaje Sync relacionado.</span><span class="sxs-lookup"><span data-stu-id="3408f-134">It is optional and used to correct the origin timestamp in related Sync message.</span></span> <span data-ttu-id="3408f-135">Solo se envía cuando el bit de dos pasos de la marca Sync está activado.</span><span class="sxs-lookup"><span data-stu-id="3408f-135">It is sent only when the two step bit in Sync flag is set.</span></span>
* <span data-ttu-id="3408f-136">**Delay_Req**.</span><span class="sxs-lookup"><span data-stu-id="3408f-136">**Delay_Req**.</span></span> <span data-ttu-id="3408f-137">Se trata de un mensaje de evento.</span><span class="sxs-lookup"><span data-stu-id="3408f-137">This is an event message.</span></span> <span data-ttu-id="3408f-138">Se envía desde el cliente PTP para calcular el retraso de la ruta de cliente a maestro, al recibir Delay_Resp.</span><span class="sxs-lookup"><span data-stu-id="3408f-138">It is sent from PTP client to calculate the path delay from client to master, on receiving Delay_Resp.</span></span>
* <span data-ttu-id="3408f-139">**Delay_Resp**.</span><span class="sxs-lookup"><span data-stu-id="3408f-139">**Delay_Resp**.</span></span> <span data-ttu-id="3408f-140">Se trata de un mensaje de evento.</span><span class="sxs-lookup"><span data-stu-id="3408f-140">This is an event message.</span></span> <span data-ttu-id="3408f-141">Se envía desde el maestro al cliente para calcular el retraso de la ruta de cliente a maestro.</span><span class="sxs-lookup"><span data-stu-id="3408f-141">It is sent from master to client to calculate the path delay from client to master.</span></span>

<span data-ttu-id="3408f-142">*Tenga en cuenta que el algoritmo de "mejor reloj maestro" no está implementado. Solo se acepta el primer reloj maestro cuando el cliente PTP está en estado de escucha.*</span><span class="sxs-lookup"><span data-stu-id="3408f-142">*Note, "best master clock" algorithm is not implemented. Only the first master clock is accepted when the PTP client is in listening state.*</span></span>

## <a name="netx-duo-ptp-client-clock-callback"></a><span data-ttu-id="3408f-143">Devolución de llamada del reloj del cliente PTP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3408f-143">NetX Duo PTP Client Clock Callback</span></span>
<span data-ttu-id="3408f-144">Para sincronizar el reloj desde el maestro, el cliente PTP necesita un reloj local.</span><span class="sxs-lookup"><span data-stu-id="3408f-144">To synchronize clock from master, PTP client needs a local clock.</span></span> <span data-ttu-id="3408f-145">Se pasa una función de devolución de llamada del reloj al cliente PTP durante la creación.</span><span class="sxs-lookup"><span data-stu-id="3408f-145">A clock callback function is passed into PTP client during creation.</span></span> <span data-ttu-id="3408f-146">El formato de la rutina de devolución de llamada del reloj se define a continuación.</span><span class="sxs-lookup"><span data-stu-id="3408f-146">The format of the clock callback routine is  defined below.</span></span>
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
<span data-ttu-id="3408f-147">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="3408f-147">The input parameters are defined as follows:</span></span>
* <span data-ttu-id="3408f-148">*client_ptr* apunta al cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="3408f-148">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="3408f-149">*operation* especifica la operación de devolución de llamada. Los valores válidos se definen como se muestra en la lista siguiente.</span><span class="sxs-lookup"><span data-stu-id="3408f-149">*operation* specifies the callback operation, valid values are defined as shown in the list below.</span></span>
  * <span data-ttu-id="3408f-150">**NX_PTP_CLIENT_CLOCK_INIT** Inicializa el reloj.</span><span class="sxs-lookup"><span data-stu-id="3408f-150">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="3408f-151">**NX_PTP_CLIENT_CLOCK_SET** Establece la marca de tiempo actual especificada por `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="3408f-151">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="3408f-152">**NX_PTP_CLIENT_CLOCK_GET** Devuelve la marca de tiempo actual a `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="3408f-152">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="3408f-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extrae la marca de tiempo de `packet_ptr` en `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="3408f-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="3408f-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Ajusta la marca de tiempo actual menos de *1* segundo.</span><span class="sxs-lookup"><span data-stu-id="3408f-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="3408f-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Marque el `packet_ptr` que necesita para notificar al cliente PTP la marca de tiempo cuando se transmita.</span><span class="sxs-lookup"><span data-stu-id="3408f-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="3408f-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Actualiza el temporizador de software.</span><span class="sxs-lookup"><span data-stu-id="3408f-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="3408f-157">El reloj de hardware puede pasarlo por alto.</span><span class="sxs-lookup"><span data-stu-id="3408f-157">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="3408f-158">*time_ptr* apunta a la marca de tiempo.</span><span class="sxs-lookup"><span data-stu-id="3408f-158">*time_ptr* points to timestamp.</span></span>
* <span data-ttu-id="3408f-159">*packet_ptr* apunta al paquete.</span><span class="sxs-lookup"><span data-stu-id="3408f-159">*packet_ptr* points to packet.</span></span>
* <span data-ttu-id="3408f-160">*callback_data* apunta a los datos de devolución de llamada opacos.</span><span class="sxs-lookup"><span data-stu-id="3408f-160">*callback_data* points to opaque callback data.</span></span>

<span data-ttu-id="3408f-161">El tipo de datos NX_PTP_TIME se define como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="3408f-161">The NX_PTP_TIME data type is defined as follows.</span></span>
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a><span data-ttu-id="3408f-162">Devolución de llamada de evento de cliente PTP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3408f-162">NetX Duo PTP Client Event Callback</span></span>
<span data-ttu-id="3408f-163">La función de devolución de llamada de evento puede configurarse para notificar a la aplicación el estado del cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="3408f-163">The event callback function can be setup to notify application the state of PTP client.</span></span> <span data-ttu-id="3408f-164">El formato de la rutina de devolución de llamada de evento se define como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="3408f-164">The format of the event callback routine is defined as shown below.</span></span>
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
<span data-ttu-id="3408f-165">Los parámetros de entrada son.</span><span class="sxs-lookup"><span data-stu-id="3408f-165">The input parameters are.</span></span>
* <span data-ttu-id="3408f-166">*client_ptr* apunta al cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="3408f-166">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="3408f-167">*Event* especifica el evento de devolución de llamada. Los valores válidos se definen como:</span><span class="sxs-lookup"><span data-stu-id="3408f-167">*event* specifies the callback event, valid values are defined as:</span></span>
  * <span data-ttu-id="3408f-168">**NX_PTP_CLIENT_EVENT_MASTER** Se selecciona un reloj maestro.</span><span class="sxs-lookup"><span data-stu-id="3408f-168">**NX_PTP_CLIENT_EVENT_MASTER** A master clock is selected.</span></span>
  * <span data-ttu-id="3408f-169">**NX_PTP_CLIENT_EVENT_SYNC** El cliente PTP está calibrado.</span><span class="sxs-lookup"><span data-stu-id="3408f-169">**NX_PTP_CLIENT_EVENT_SYNC** PTP client is calibrated.</span></span>
  * <span data-ttu-id="3408f-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** El reloj maestro ha agotado el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="3408f-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** Master clock is timeout.</span></span>
* <span data-ttu-id="3408f-171">*event_data* especifica los datos relacionados con el evento.</span><span class="sxs-lookup"><span data-stu-id="3408f-171">*event_data* specifies the data related to event.</span></span> <span data-ttu-id="3408f-172">Cuando el evento es **NX_PTP_CLIENT_EVENT_MASTER**, los datos del evento apuntan a la instancia `NX_PTP_CLIENT_MASTER`.</span><span class="sxs-lookup"><span data-stu-id="3408f-172">When event is **NX_PTP_CLIENT_EVENT_MASTER**, event_data points to `NX_PTP_CLIENT_MASTER` instance.</span></span> <span data-ttu-id="3408f-173">Cuando el evento es **NX_PTP_CLIENT_EVENT_SYNC**, los datos del evento apuntan a la instancia `NX_PTP_CLIENT_SYNC`.</span><span class="sxs-lookup"><span data-stu-id="3408f-173">When event is **NX_PTP_CLIENT_EVENT_SYNC**, event data points to `NX_PTP_CLIENT_SYNC` instance.</span></span>

## <a name="netx-duo-ptp-client-communication"></a><span data-ttu-id="3408f-174">Comunicación de cliente PTP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3408f-174">NetX Duo PTP Client Communication</span></span>
<span data-ttu-id="3408f-175">Como se mencionó anteriormente, el cliente PTP de NetX Duo solo admite el mecanismo de retraso de solicitud-respuesta.</span><span class="sxs-lookup"><span data-stu-id="3408f-175">As mentioned previously, NetX Duo PTP client only supports delay request-response mechanism.</span></span> <span data-ttu-id="3408f-176">Este mecanismo mide el retraso de la ruta media entre el cliente y el reloj maestro como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="3408f-176">This mechanism measures the mean path delay between the client and the master clock as below:</span></span>
1. <span data-ttu-id="3408f-177">El cliente recibe el mensaje *Announce* del maestro y lo selecciona como "mejor maestro".</span><span class="sxs-lookup"><span data-stu-id="3408f-177">Client receives *Announce* message from master and select it as best master.</span></span>
1. <span data-ttu-id="3408f-178">El cliente recibe el mensaje *Sync* del maestro.</span><span class="sxs-lookup"><span data-stu-id="3408f-178">Client receives *Sync* message from master.</span></span> <span data-ttu-id="3408f-179">La marca de tiempo *t1* es la marca de tiempo de origen en este mensaje.</span><span class="sxs-lookup"><span data-stu-id="3408f-179">The timestamp *t1* is the origin timestamp in this message.</span></span> <span data-ttu-id="3408f-180">La marca de tiempo *t2* se lee desde el reloj local cuando se recibe este mensaje.</span><span class="sxs-lookup"><span data-stu-id="3408f-180">The timestamp *t2* is read from local clock when this message is received.</span></span>
1. <span data-ttu-id="3408f-181">El cliente recibe el mensaje *Follow_Up* del maestro.</span><span class="sxs-lookup"><span data-stu-id="3408f-181">Client receives *Follow_Up* message from master.</span></span> <span data-ttu-id="3408f-182">Este mensaje es opcional y solo es válido cuando se establecen dos pasos en la marca *Sync*.</span><span class="sxs-lookup"><span data-stu-id="3408f-182">This message is optional and valid only when two step in *Sync* flag is set.</span></span> <span data-ttu-id="3408f-183">A continuación, la marca de tiempo *t1* se actualiza a la marca de tiempo de origen en este mensaje.</span><span class="sxs-lookup"><span data-stu-id="3408f-183">Then the timestamp *t1* is updated to the origin timestamp in this message.</span></span>
1. <span data-ttu-id="3408f-184">El cliente envía el mensaje *Delay_Req* al maestro.</span><span class="sxs-lookup"><span data-stu-id="3408f-184">Client sends *Delay_Req* message to master.</span></span> <span data-ttu-id="3408f-185">La marca de tiempo *t3* se lee desde el reloj local cuando se transmite el mensaje.</span><span class="sxs-lookup"><span data-stu-id="3408f-185">The timestamp *t3* is read from local clock when the message is transmitted.</span></span>
1. <span data-ttu-id="3408f-186">El cliente recibe el mensaje *Delay_Resp* del maestro.</span><span class="sxs-lookup"><span data-stu-id="3408f-186">Client receives *Delay_Resp* message from master.</span></span> <span data-ttu-id="3408f-187">La marca de tiempo *t4* es la marca de tiempo de recepción de este mensaje.</span><span class="sxs-lookup"><span data-stu-id="3408f-187">The timestamp *t4* is the receive timestamp in this message.</span></span>

<span data-ttu-id="3408f-188">El retraso de la ruta media se calcula como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="3408f-188">The mean path delay is computed as shown below.</span></span>
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
<span data-ttu-id="3408f-189">El desplazamiento desde el maestro se calcula como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="3408f-189">The offset from master is computed as shown below.</span></span>
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> <span data-ttu-id="3408f-190">\*\*\*\*correctionField\*\* _ se omite durante el cálculo._</span><span class="sxs-lookup"><span data-stu-id="3408f-190">\*The \***correctionField** _ is ignored during the calculation._</span></span>