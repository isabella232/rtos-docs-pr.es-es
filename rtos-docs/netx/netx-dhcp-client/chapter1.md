---
title: 'Capítulo 1: Introducción al cliente DHCP de Azure RTOS NetX'
description: En NetX, la dirección IP de la aplicación es uno de los parámetros proporcionados a la llamada de servicio nx_ip_create.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 44eb764c84a15a1bc96cf94bcbc8f81be7b41eef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815257"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-client"></a><span data-ttu-id="90107-103">Capítulo 1: Introducción al cliente DHCP de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="90107-103">Chapter 1 - Introduction to Azure RTOS NetX DHCP Client</span></span>

<span data-ttu-id="90107-104">En NetX, la dirección IP de la aplicación es uno de los parámetros proporcionados a la llamada de servicio *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="90107-104">In NetX, the application’s IP address is one of the supplied parameters to the *nx_ip_create* service call.</span></span> <span data-ttu-id="90107-105">Proporcionar la dirección IP no supone ningún problema si la aplicación conoce la dirección IP, ya sea de forma estática o a través de la configuración del usuario.</span><span class="sxs-lookup"><span data-stu-id="90107-105">Supplying the IP address poses no problem if the IP address is known to the application, either statically or through user configuration.</span></span> <span data-ttu-id="90107-106">Sin embargo, hay algunos casos en los que la aplicación no sabe ni se preocupa por saber cuál es su dirección IP.</span><span class="sxs-lookup"><span data-stu-id="90107-106">However, there are some instances where the application doesn’t know or care what its IP address is.</span></span> <span data-ttu-id="90107-107">En tales situaciones, se debe proporcionar una dirección IP cero a la función *nx_ip_create* y se debe usar el protocolo cliente DHCP de Azure RTOS para obtener dinámicamente una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="90107-107">In such situations, a zero IP address should be supplied to the *nx_ip_create* function and the Azure RTOS DHCP Client protocol should be used to dynamically obtain an IP address.</span></span>

## <a name="dynamic-ip-address-assignment"></a><span data-ttu-id="90107-108">Asignación de dirección IP dinámica</span><span class="sxs-lookup"><span data-stu-id="90107-108">Dynamic IP Address Assignment</span></span>

<span data-ttu-id="90107-109">El servicio básico usado para obtener una dirección IP dinámica de la red es el protocolo Reverse Address Recognition Protocol (RARP).</span><span class="sxs-lookup"><span data-stu-id="90107-109">The basic service used to obtain a dynamic IP address from the network is the Reverse Address Resolution Protocol (RARP).</span></span> <span data-ttu-id="90107-110">Este protocolo es similar a ARP, con la excepción de que está diseñado para obtener una dirección IP para sí mismo en lugar de encontrar la dirección MAC para otro nodo de red.</span><span class="sxs-lookup"><span data-stu-id="90107-110">This protocol is similar to ARP, except it is designed to obtain an IP address for itself instead of finding the MAC address for another network node.</span></span> <span data-ttu-id="90107-111">El mensaje RARP de bajo nivel se emite en la red local y es responsabilidad de un servidor de la red responder con una respuesta RARP, que contiene una dirección IP asignada dinámicamente.</span><span class="sxs-lookup"><span data-stu-id="90107-111">The low-level RARP message is broadcast on the local network and it is the responsibility of a server on the network to respond with an RARP response, which contains a dynamically allocated IP address.</span></span>

<span data-ttu-id="90107-112">Aunque RARP proporciona un servicio para asignar direcciones IP de forma dinámica, tiene varias limitaciones.</span><span class="sxs-lookup"><span data-stu-id="90107-112">Although RARP provides a service for dynamic allocation of IP addresses, it has several shortcomings.</span></span> <span data-ttu-id="90107-113">La limitación más evidente es que RARP solo proporciona una asignación dinámica de la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="90107-113">The most glaring deficiency is that RARP only provides dynamic allocation of the IP address.</span></span> <span data-ttu-id="90107-114">En la mayoría de los casos, es necesaria una mayor información para que un dispositivo pueda participar correctamente en una red.</span><span class="sxs-lookup"><span data-stu-id="90107-114">In most situations, more information is necessary in order for a device to properly participate on a network.</span></span> <span data-ttu-id="90107-115">Además de una dirección IP, la mayoría de los dispositivos necesitan la máscara de red y la dirección IP de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="90107-115">In addition to an IP address, most devices need the network mask and the gateway IP address.</span></span> <span data-ttu-id="90107-116">También es posible que se necesite la dirección IP de un servidor DNS y otra información de la red.</span><span class="sxs-lookup"><span data-stu-id="90107-116">The IP address of a DNS server and other network information may also be needed.</span></span> <span data-ttu-id="90107-117">RARP no tiene la capacidad de proporcionar esta información.</span><span class="sxs-lookup"><span data-stu-id="90107-117">RARP does not have the ability to provide this information.</span></span>

## <a name="rarp-alternatives"></a><span data-ttu-id="90107-118">Alternativas de RARP</span><span class="sxs-lookup"><span data-stu-id="90107-118">RARP Alternatives</span></span>

<span data-ttu-id="90107-119">Con el fin de superar las limitaciones de RARP, los investigadores han desarrollado un mecanismo para asignar direcciones IP más completo denominado protocolo de arranque (BOOTP).</span><span class="sxs-lookup"><span data-stu-id="90107-119">In order to overcome the deficiencies of RARP, researchers developed a more comprehensive IP address allocation mechanism called the Bootstrap Protocol (BOOTP).</span></span> <span data-ttu-id="90107-120">Este protocolo tiene la capacidad de asignar dinámicamente una dirección IP y también proporcionar información adicional sobre la red.</span><span class="sxs-lookup"><span data-stu-id="90107-120">This protocol has the ability to dynamically allocate an IP address and also provide additional important network information.</span></span> <span data-ttu-id="90107-121">Sin embargo, BOOTP tiene el inconveniente de estar diseñado para configuraciones de red estáticas.</span><span class="sxs-lookup"><span data-stu-id="90107-121">However, BOOTP has the drawback of being designed for static network configurations.</span></span> <span data-ttu-id="90107-122">No permite asignar direcciones rápidas o automatizadas.</span><span class="sxs-lookup"><span data-stu-id="90107-122">It does not allow for quick or automated address assignment.</span></span>

<span data-ttu-id="90107-123">Aquí es donde el protocolo de configuración dinámica de host (DHCP) es muy útil.</span><span class="sxs-lookup"><span data-stu-id="90107-123">This is where the Dynamic Host Configuration Protocol (DHCP) is extremely useful.</span></span> <span data-ttu-id="90107-124">DHCP está diseñado para ampliar la funcionalidad básica de BOOTP con el fin de incluir la asignación de servidor IP totalmente automatizada y la asignación de direcciones IP completamente dinámicas a través de la "concesión" de una dirección IP a un cliente durante un período de tiempo especificado.</span><span class="sxs-lookup"><span data-stu-id="90107-124">DHCP is designed to extend the basic functionality of BOOTP to include completely automated IP server allocation and completely dynamic IP address allocation through “leasing” an IP address to a client for a specified period of time.</span></span> <span data-ttu-id="90107-125">DHCP también se puede configurar para asignar direcciones IP de forma estática como BOOTP.</span><span class="sxs-lookup"><span data-stu-id="90107-125">DHCP can also be configured to allocate IP addresses in a static manner like BOOTP.</span></span>

## <a name="dhcp-messages"></a><span data-ttu-id="90107-126">Mensajes DHCP</span><span class="sxs-lookup"><span data-stu-id="90107-126">DHCP Messages</span></span>

<span data-ttu-id="90107-127">Aunque DHCP mejora en gran medida la funcionalidad de BOOTP, DHCP usa el mismo formato de mensaje que BOOTP y admite las mismas opciones de proveedor que BOOTP.</span><span class="sxs-lookup"><span data-stu-id="90107-127">Although DHCP greatly enhances the functionality of BOOTP, DHCP uses the same message format as BOOTP and supports the same vendor options as BOOTP.</span></span> <span data-ttu-id="90107-128">Para realizar su función, DHCP introduce siete nuevas opciones específicas de DHCP, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="90107-128">In order to perform its function, DHCP introduces seven new DHCP-specific options, as follows:</span></span>

- <span data-ttu-id="90107-129">DISCOVER (1) (enviada por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="90107-129">DISCOVER (1) (sent by DHCP Client)</span></span>

- <span data-ttu-id="90107-130">OFFER (2) (enviada por el servidor DHCP)</span><span class="sxs-lookup"><span data-stu-id="90107-130">OFFER (2) (sent by DHCP Server)</span></span>

- <span data-ttu-id="90107-131">REQUEST (3) (enviada por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="90107-131">REQUEST (3) (sent by DHCP Client)</span></span>

- <span data-ttu-id="90107-132">DECLINE (4) (enviada por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="90107-132">DECLINE (4) (sent by DHCP Client)</span></span>

- <span data-ttu-id="90107-133">ACK (5) (enviada por el servidor DHCP)</span><span class="sxs-lookup"><span data-stu-id="90107-133">ACK (5) (sent by DHCP Server)</span></span>

- <span data-ttu-id="90107-134">NACK (6) (enviada por el servidor DHCP)</span><span class="sxs-lookup"><span data-stu-id="90107-134">NACK (6) (sent by DHCP Server)</span></span>

- <span data-ttu-id="90107-135">RELEASE (7) (enviada por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="90107-135">RELEASE (7) (sent by DHCP Client)</span></span>

- <span data-ttu-id="90107-136">INFORM (8) (enviada por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="90107-136">INFORM (8) (sent by DHCP Client)</span></span>

- <span data-ttu-id="90107-137">FORCERENEW (9) (enviado por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="90107-137">FORCERENEW (9) (sent by DHCP Client)</span></span>

## <a name="dhcp-communication"></a><span data-ttu-id="90107-138">Comunicación DHCP</span><span class="sxs-lookup"><span data-stu-id="90107-138">DHCP Communication</span></span>

<span data-ttu-id="90107-139">DHCP emplea el protocolo UDP para enviar solicitudes y respuestas de campo.</span><span class="sxs-lookup"><span data-stu-id="90107-139">DHCP utilizes the UDP protocol to send requests and field responses.</span></span> <span data-ttu-id="90107-140">Antes de tener una dirección IP, los mensajes UDP que llevan la información de DHCP se envían y se reciben mediante la dirección IP de difusión 255.255.255.255.</span><span class="sxs-lookup"><span data-stu-id="90107-140">Prior to having an IP address, UDP messages carrying the DHCP information are sent and received by utilizing the IP broadcast address of 255.255.255.255.</span></span>

## <a name="dhcp-client-state-machine"></a><span data-ttu-id="90107-141">Máquina de estados de cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="90107-141">DHCP Client State Machine</span></span>

<span data-ttu-id="90107-142">El cliente DHCP se implementa como una máquina de estados.</span><span class="sxs-lookup"><span data-stu-id="90107-142">The DHCP Client is implemented as a state machine.</span></span> <span data-ttu-id="90107-143">La máquina de estados se procesa mediante un subproceso DHCP que se crea durante el procesamiento *nx_dhcp_create*.</span><span class="sxs-lookup"><span data-stu-id="90107-143">The state machine is processed by an internal DHCP thread that is created during *nx_dhcp_create* processing.</span></span> <span data-ttu-id="90107-144">Los estados principales del cliente DHCP son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="90107-144">The main states of DHCP Client are as follows:</span></span>


- <span data-ttu-id="90107-145">**NX_DHCP_STATE_BOOT**: a partir de una dirección IP anterior</span><span class="sxs-lookup"><span data-stu-id="90107-145">**NX_DHCP_STATE_BOOT** Starting with a previous IP address</span></span>

- <span data-ttu-id="90107-146">**NX_DHCP_STATE_INIT**: sin ningún valor de dirección IP anterior inicial</span><span class="sxs-lookup"><span data-stu-id="90107-146">**NX_DHCP_STATE_INIT** Starting with no previous   IP address value</span></span>

- <span data-ttu-id="90107-147">**NX_DHCP_STATE_SELECTING**: a la espera de una respuesta de un servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="90107-147">**NX_DHCP_STATE_SELECTING** Waiting for a response from any DHCP server</span></span>

- <span data-ttu-id="90107-148">**NX_DHCP_STATE_REQUESTING**: servidor DHCP identificado, solicitud de dirección IP enviada</span><span class="sxs-lookup"><span data-stu-id="90107-148">**NX_DHCP_STATE_REQUESTING** DHCP Server identified, IP address request sent</span></span>

- <span data-ttu-id="90107-149">**NX_DHCP_STATE_BOUND**: concesión de dirección IP DHCP establecida</span><span class="sxs-lookup"><span data-stu-id="90107-149">**NX_DHCP_STATE_BOUND** DHCP IP Address lease established</span></span>

- <span data-ttu-id="90107-150">**NX_DHCP_STATE_RENEWING**: tiempo de renovación de concesión de dirección IP DHCP transcurrido, renovación solicitada</span><span class="sxs-lookup"><span data-stu-id="90107-150">**NX_DHCP_STATE_RENEWING** DHCP IP Address lease renewal time elapsed, renewal requested</span></span>

- <span data-ttu-id="90107-151">**NX_DHCP_STATE_REBINDING**: tiempo de reenlace de concesión de dirección IP DHCP transcurrido, renovación solicitada</span><span class="sxs-lookup"><span data-stu-id="90107-151">**NX_DHCP_STATE_REBINDING** DHCP IP Address lease rebind time elapsed, renewal requested</span></span>

- <span data-ttu-id="90107-152">**NX_DHCP_STATE_FORCERENEW**: concesión de dirección IP DHCP establecida, forzar la renovación por servidor (actualmente no se admite) o por la aplicación mediante una llamada a nx_dhcp_force_renew</span><span class="sxs-lookup"><span data-stu-id="90107-152">**NX_DHCP_STATE_FORCERENEW** DHCP IP Address lease established, force renewal by server (currently not supported) or by the application calling nx_dhcp_force_renew</span></span>

- <span data-ttu-id="90107-153">**NX_DHCP_STATE_ADDRESS_PROBING**: sondeo de direcciones IP de DHCP, enviar el sondeo ARP para detectar conflictos de direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="90107-153">**NX_DHCP_STATE_ADDRESS_PROBING** DHCP IP Address probing, send the ARP probe to detect IP address conflict.</span></span>

## <a name="dhcp-client-multiple-interface-support"></a><span data-ttu-id="90107-154">Compatibilidad con varias interfaces de cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="90107-154">DHCP Client Multiple Interface Support</span></span>

<span data-ttu-id="90107-155">El cliente DHCP se implementó previamente para ejecutarse en una sola interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="90107-155">The DHCP Client was previously implemented to run on only a single network interface.</span></span> <span data-ttu-id="90107-156">El comportamiento predeterminado era (y todavía es) que el cliente DHCP se ejecutara en la interfaz principal.</span><span class="sxs-lookup"><span data-stu-id="90107-156">The default behavior was (and still is) for the DHCP Client to run on the primary interface.</span></span> <span data-ttu-id="90107-157">Mediante una llamada a *nx_dhcp_set_interface_index*, la aplicación podía (y aún puede) ejecutar DHCP en una interfaz de red secundaria en lugar de hacerlo en la interfaz principal.</span><span class="sxs-lookup"><span data-stu-id="90107-157">By calling *nx_dhcp_set_interface_index*, the application could (and still can) run DHCP on a secondary network interface instead of the primary interface.</span></span>

<span data-ttu-id="90107-158">Ahora admite la ejecución de DHCP en varias interfaces en paralelo.</span><span class="sxs-lookup"><span data-stu-id="90107-158">It now supports DHCP running on multiple interfaces in parallel.</span></span> <span data-ttu-id="90107-159">Consulte **Cliente DHCP en varias interfaces simultáneamente** en el capítulo 2 para ver detalles específicos sobre cómo ejecutar el cliente DHCP en más de una interfaz física simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="90107-159">See **DHCP Client on Multiple Interfaces Simultaneously** in Chapter Two for specific details how to run DHCP Client on more than one physical interface simultaneously.</span></span>

## <a name="dhcp-user-request"></a><span data-ttu-id="90107-160">Solicitud del usuario DHCP</span><span class="sxs-lookup"><span data-stu-id="90107-160">DHCP User Request</span></span>

<span data-ttu-id="90107-161">Una vez que el servidor DHCP concede una dirección IP, el procesamiento del cliente DHCP puede solicitar parámetros adicionales, de uno en uno, mediante el servicio *nx_dhcp_user_option_request*.</span><span class="sxs-lookup"><span data-stu-id="90107-161">Once the DHCP server grants an IP address, the DHCP client processing can request additional parameters — one at a time — by using the *nx_dhcp_user_option_request* service.</span></span>

## <a name="dhcp-client-socket-queue"></a><span data-ttu-id="90107-162">Cola de sockets de cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="90107-162">DHCP Client Socket Queue</span></span> 

<span data-ttu-id="90107-163">El cliente DHCP borra automáticamente los paquetes de difusión de los servidores de DHCP destinados a otros clientes DHCP de su cola de recepción de socket mientras espera a que el servidor se responda a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="90107-163">The DHCP Client automatically clears broadcast packets from DHCP Servers intended for other DHCP Clients from its socket receive queue while waiting for Server to respond to itself.</span></span> <span data-ttu-id="90107-164">En una red ocupada, si no lo hace, podría provocar que se anularan paquetes destinados al cliente.</span><span class="sxs-lookup"><span data-stu-id="90107-164">In a busy network, not doing so could cause packets intended for the Client to be dropped.</span></span>

## <a name="dhcp-rfcs"></a><span data-ttu-id="90107-165">RFC de DHCP</span><span class="sxs-lookup"><span data-stu-id="90107-165">DHCP RFCs</span></span>

<span data-ttu-id="90107-166">NetX DHCP es compatible con la RFC2132, RFC2131 y RFC relacionadas.</span><span class="sxs-lookup"><span data-stu-id="90107-166">NetX DHCP is compliant with RFC2132, RFC2131, and related RFCs.</span></span>

