---
title: 'Capítulo 3: Opciones de configuración del servidor DHCPv6 de Azure RTOS NetX Duo'
description: Hay varias opciones de configuración para compilar el servidor DHCPv6 de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5396b1c04581b5f79d337462368c4718ba9bb16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814778"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a><span data-ttu-id="9d9c1-103">Capítulo 3: Opciones de configuración del servidor DHCPv6 de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9d9c1-103">Chapter 3 - Azure RTOS NetX Duo DHCPv6 configuration options</span></span>

<span data-ttu-id="9d9c1-104">Hay varias opciones de configuración para compilar el servidor DHCPv6 de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-104">There are several configuration options for building Azure RTOS NetX Duo DHCPv6.</span></span> <span data-ttu-id="9d9c1-105">En la lista siguiente se describe cada una de forma detallada:</span><span class="sxs-lookup"><span data-stu-id="9d9c1-105">The following list describes each in detail:</span></span>  
  
  
- <span data-ttu-id="9d9c1-106">**NX_DHCPV6_THREAD_PRIORITY**: prioridad del subproceso del cliente.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-106">**NX_DHCPV6_THREAD_PRIORITY** Priority of the Client thread.</span></span> <span data-ttu-id="9d9c1-107">De forma predeterminada, este valor especifica que el subproceso del cliente se ejecuta con la prioridad 2.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-107">By   default, this value specifies that   the Client thread runs at priority   2.</span></span>

- <span data-ttu-id="9d9c1-108">**NX_DHCPV6_MUTEX_WAIT**: opción de tiempo de espera para obtener un bloqueo exclusivo en una exclusión mutua del cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-108">**NX_DHCPV6_MUTEX_WAIT** Time out option for obtaining an exclusive lock on a DHCPv6 Client mutex.</span></span> <span data-ttu-id="9d9c1-109">El valor predeterminado es TX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-109">The default value is TX_WAIT_FOREVER.</span></span>

- <span data-ttu-id="9d9c1-110">**NX_DHCPV6_TICKS_PER_SECOND**: relación entre tics y segundos.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-110">**NX_DHCPV6_TICKS_PER_SECOND** Ratio of ticks to seconds.</span></span> <span data-ttu-id="9d9c1-111">Esto depende del procesador.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-111">This is processor dependent.</span></span> <span data-ttu-id="9d9c1-112">El valor predeterminado es 100.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-112">The default value is 100.</span></span>

- <span data-ttu-id="9d9c1-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**: intervalo de tiempo en segundos en el que el temporizador de duración de IP actualiza la cantidad de tiempo que se ha asignado la dirección IP actual al cliente.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Time interval in seconds at which the IP lifetime timer updates the length of time the current IP address has been assigned to the Client.</span></span> <span data-ttu-id="9d9c1-114">De manera predeterminada, este valor es 1.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-114">By default, this value is 1.</span></span>

- <span data-ttu-id="9d9c1-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**: intervalo de tiempo en segundos en el que el temporizador de la sesión actualiza el tiempo durante el que el cliente ha estado en la sesión de comunicación con el servidor.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**  Time interval in seconds at which the session timer updates the length of time the Client has been in session communicating with the Server.</span></span> <span data-ttu-id="9d9c1-116">De manera predeterminada, este valor es 1.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-116">By default, this value is 1.</span></span>

- <span data-ttu-id="9d9c1-117">**NX_DHCPV6_MAX_IA_ADDRESS**: número máximo de direcciones IA que se pueden agregar al registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-117">**NX_DHCPV6_MAX_IA_ADDRESS** The maximum number of IA addresses that can be added to the Client record.</span></span> <span data-ttu-id="9d9c1-118">El valor predeterminado es 1.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-118">The default value is 1.</span></span> 

- <span data-ttu-id="9d9c1-119">**NX_DHCPV6_NUM_DNS_SERVERS**: número de servidores DNS que se van a almacenar en el registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-119">**NX_DHCPV6_NUM_DNS_SERVERS** Number of DNS servers to store to the client record.</span></span> <span data-ttu-id="9d9c1-120">El valor predeterminado es 2.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-120">The default value is 2.</span></span>

- <span data-ttu-id="9d9c1-121">**NX_DHCPV6_NUM_TIME_SERVERS**: número de servidores de tiempo que se almacenan en el registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-121">**NX_DHCPV6_NUM_TIME_SERVERS** Number of time servers to store to the client record.</span></span> <span data-ttu-id="9d9c1-122">El valor predeterminado es 1.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-122">The default value is 1.</span></span>

- <span data-ttu-id="9d9c1-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**: tamaño del búfer en el registro de cliente para contener el nombre de dominio de red del cliente.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Size of the buffer in the Client record to hold the client’s network domain name.</span></span> <span data-ttu-id="9d9c1-124">El valor predeterminado es 30.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-124">The default value is 30.</span></span>

- <span data-ttu-id="9d9c1-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**: tamaño del búfer en el registro de cliente para almacenar la zona horaria del cliente.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Size of the buffer in the Client record to hold the Client’s time zone.</span></span> <span data-ttu-id="9d9c1-126">El valor predeterminado es 10.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-126">The default value is 10.</span></span>

- <span data-ttu-id="9d9c1-127">**NX_DHCPV6_MAX_MESSAGE_SIZE**: tamaño del búfer en el registro del cliente para contener el mensaje de estado de la opción en una respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Size of the buffer in the Client record to hold the option status message in a Server reply.</span></span> <span data-ttu-id="9d9c1-128">El valor predeterminado es 100 bytes.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-128">The default value is 100 bytes.</span></span>

- <span data-ttu-id="9d9c1-129">**NX_DHCPV6_PACKET_TIME_OUT**: tiempo de espera en segundos para la asignación de un paquete desde el grupo de paquetes del cliente.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-129">**NX_DHCPV6_PACKET_TIME_OUT** Time out in seconds for allocating a packet from the Client packet pool.</span></span> <span data-ttu-id="9d9c1-130">El valor predeterminado es 3 segundos.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-130">The default value is 3 seconds.</span></span>

- <span data-ttu-id="9d9c1-131">**NX_DHCPV6_TYPE_OF_SERVICE**: define el tipo de servicio para la transmisión de paquetes UDP desde el socket del cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-131">**NX_DHCPV6_TYPE_OF_SERVICE** This defines the type of service for UDP packet transmission from the DHCPv6 Client socket.</span></span> <span data-ttu-id="9d9c1-132">El valor predeterminado es **NX_IP_NORMAL**.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-132">The default value is **NX_IP_NORMAL**.</span></span>

- <span data-ttu-id="9d9c1-133">**NX_DHCPV6_TIME_TO_LIVE**: número de veces que un enrutador de red reenvía un paquete de cliente antes de que se descarte el paquete.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-133">**NX_DHCPV6_TIME_TO_LIVE** The number of times a Client packet is forwarded by a network router before the packet is discarded.</span></span> <span data-ttu-id="9d9c1-134">El valor predeterminado es 0x80.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-134">The default value is 0x80.</span></span>

- <span data-ttu-id="9d9c1-135">**NX_DHCPV6_QUEUE_DEPTH** Especifica el número de paquetes que se van a mantener en la cola de recepción del socket UDP del cliente antes de que NetX Duo descarte los paquetes.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-135">**NX_DHCPV6_QUEUE_DEPTH** Specifies the number of packets to keep in the Client UDP socket receive queue before NetX Duo discards packets.</span></span> <span data-ttu-id="9d9c1-136">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-136">The default value is 5.</span></span>

## <a name="dhcpv6-message-transmission"></a><span data-ttu-id="9d9c1-137">Transmisión de mensajes DHCPv6</span><span class="sxs-lookup"><span data-stu-id="9d9c1-137">DHCPv6 Message Transmission</span></span>

<span data-ttu-id="9d9c1-138">Hay un conjunto de opciones del cliente DHCPv6 para establecer parámetros en la transmisión de mensajes DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-138">There are a set of DHCPv6 Client options for setting parameters on DHCPv6 message transmission.</span></span> <span data-ttu-id="9d9c1-139">Dichos componentes son:</span><span class="sxs-lookup"><span data-stu-id="9d9c1-139">These are:</span></span> 

  - <span data-ttu-id="9d9c1-140">tiempo de espera inicial</span><span class="sxs-lookup"><span data-stu-id="9d9c1-140">initial timeout</span></span>

  - <span data-ttu-id="9d9c1-141">retraso máximo en la primera transmisión</span><span class="sxs-lookup"><span data-stu-id="9d9c1-141">maximum delay on the first transmission</span></span>

  - <span data-ttu-id="9d9c1-142">tiempo máximo de retransmisión</span><span class="sxs-lookup"><span data-stu-id="9d9c1-142">maximum retransmission timeout</span></span> 

  - <span data-ttu-id="9d9c1-143">número máximo de retransmisiones</span><span class="sxs-lookup"><span data-stu-id="9d9c1-143">maximum number of retransmissions</span></span> 

  - <span data-ttu-id="9d9c1-144">duración máxima de espera para la respuesta del servidor</span><span class="sxs-lookup"><span data-stu-id="9d9c1-144">maximum duration to wait for server response</span></span>

<span data-ttu-id="9d9c1-145">Estos parámetros se aplican a cada uno de los mensajes de cliente DHCPv6:</span><span class="sxs-lookup"><span data-stu-id="9d9c1-145">These parameters apply to each of the DHCPv6 Client messages:</span></span>

- <span data-ttu-id="9d9c1-146">SOLICIT</span><span class="sxs-lookup"><span data-stu-id="9d9c1-146">SOLICIT</span></span>

- <span data-ttu-id="9d9c1-147">REQUEST</span><span class="sxs-lookup"><span data-stu-id="9d9c1-147">REQUEST</span></span>

- <span data-ttu-id="9d9c1-148">RENEW</span><span class="sxs-lookup"><span data-stu-id="9d9c1-148">RENEW</span></span>

- <span data-ttu-id="9d9c1-149">REBIND</span><span class="sxs-lookup"><span data-stu-id="9d9c1-149">REBIND</span></span>

- <span data-ttu-id="9d9c1-150">RELEASE</span><span class="sxs-lookup"><span data-stu-id="9d9c1-150">RELEASE</span></span>

- <span data-ttu-id="9d9c1-151">DECLINE</span><span class="sxs-lookup"><span data-stu-id="9d9c1-151">DECLINE</span></span>

- <span data-ttu-id="9d9c1-152">CONFIRMAR</span><span class="sxs-lookup"><span data-stu-id="9d9c1-152">CONFIRM</span></span>

- <span data-ttu-id="9d9c1-153">INFORM</span><span class="sxs-lookup"><span data-stu-id="9d9c1-153">INFORM</span></span>

<span data-ttu-id="9d9c1-154">A continuación se muestra una lista completa de estas opciones configurables y su valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-154">The following is a complete list of these configurable options and their default</span></span> 

<span data-ttu-id="9d9c1-155">values:</span><span class="sxs-lookup"><span data-stu-id="9d9c1-155">values:</span></span>

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

<span data-ttu-id="9d9c1-156">Para no limitar el tiempo de espera de la retransmisión, establezca el número de retransmisión de mensajes en 0.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-156">For no limit on a retransmission timeout, set the message retransmission count to 0.</span></span> <span data-ttu-id="9d9c1-157">Para no limitar el número de veces que se retransmite un mensaje del cliente DHCPv6 (reintentos), establezca el recuento de retransmisión de mensajes en 0.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-157">For no limit on the number of times a DHCPv6 Client message is retransmitted (retries), set the message retransmission count to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="9d9c1-158">Independientemente de la duración del tiempo de espera o el número de reintentos, cuando expire la duración válida de una dirección IPv6, se quitará de la tabla de direcciones IP y el cliente ya no podrá utilizarla.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-158">Regardless of length of timeout or number of retries, when an IPv6 address valid lifetime expires, it is removed from the IP address table and can no longer be used by the Client.</span></span> <span data-ttu-id="9d9c1-159">El cliente DHCPv6 de NetX Duo iniciará automáticamente el envío de mensajes SOLICIT que solicitan una nueva dirección IPv6.</span><span class="sxs-lookup"><span data-stu-id="9d9c1-159">The NetX Duo DHCPv6 Client will automatically begin sending SOLICIT messages requesting a new IPv6 address.</span></span>