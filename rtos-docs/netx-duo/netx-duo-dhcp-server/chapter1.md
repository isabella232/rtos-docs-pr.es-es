---
title: 'Capítulo 1: Introducción al servidor DHCP de Azure RTOS NetX Duo'
description: En NetX Duo, la dirección IP de la aplicación es uno de los parámetros proporcionados a la llamada de servicio *nx_ip_create*.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 678b9ed77f07d0b526525c740f0fae7adc6d2c95
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814797"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcp-server"></a><span data-ttu-id="84782-103">Capítulo 1: Introducción al servidor DHCP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="84782-103">Chapter 1 - Introduction to Azure RTOS NetX Duo DHCP server</span></span>

<span data-ttu-id="84782-104">En NetX Duo, la dirección IP de la aplicación es uno de los parámetros proporcionados a la llamada de servicio *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="84782-104">In NetX Duo, the application’s IP address is one of the supplied parameters to the *nx_ip_create* service call.</span></span> <span data-ttu-id="84782-105">Proporcionar la dirección IP no supone ningún problema si la aplicación conoce la dirección IP, ya sea de forma estática o a través de la configuración del usuario.</span><span class="sxs-lookup"><span data-stu-id="84782-105">Supplying the IP address poses no problem if the IP address is known to the application, either statically or through user configuration.</span></span> <span data-ttu-id="84782-106">Sin embargo, hay algunos casos en los que la aplicación no sabe ni se preocupa por saber cuál es su dirección IP.</span><span class="sxs-lookup"><span data-stu-id="84782-106">However, there are some instances where the application doesn’t know or care what its IP address is.</span></span> <span data-ttu-id="84782-107">En tales situaciones, se debe proporcionar una dirección IP cero a la función *nx_ip_create* y la aplicación establece la comunicación con su servidor DHCP para solicitar y obtener una dirección IP de forma dinámica.</span><span class="sxs-lookup"><span data-stu-id="84782-107">In such situations, a zero IP address should be supplied to the *nx_ip_create* function and the application establishes communication with its DHCP server to dynamically request and obtain an IP address.</span></span>

## <a name="dynamic-ip-address-assignment"></a><span data-ttu-id="84782-108">Asignación de dirección IP dinámica</span><span class="sxs-lookup"><span data-stu-id="84782-108">Dynamic IP Address Assignment</span></span>

<span data-ttu-id="84782-109">El servicio básico usado para obtener una dirección IP dinámica de la red es el protocolo Reverse Address Recognition Protocol (RARP).</span><span class="sxs-lookup"><span data-stu-id="84782-109">The basic service used to obtain a dynamic IP address from the network is the Reverse Address Resolution Protocol (RARP).</span></span> <span data-ttu-id="84782-110">Este protocolo es similar a ARP, con la excepción de que está diseñado para obtener una dirección IP para sí mismo en lugar de encontrar la dirección MAC para otro nodo de red.</span><span class="sxs-lookup"><span data-stu-id="84782-110">This protocol is similar to ARP, except it is designed to obtain an IP address for itself instead of finding the MAC address for another network node.</span></span> <span data-ttu-id="84782-111">El mensaje RARP de bajo nivel se emite en la red local y es responsabilidad de un servidor de la red responder con una respuesta RARP, que contiene una dirección IP asignada dinámicamente.</span><span class="sxs-lookup"><span data-stu-id="84782-111">The low-level RARP message is broadcast on the local network and it is the responsibility of a server on the network to respond with an RARP response, which contains a dynamically allocated IP address.</span></span>

<span data-ttu-id="84782-112">Aunque RARP proporciona un servicio para la asignación dinámica de direcciones IP, tiene varias limitaciones.</span><span class="sxs-lookup"><span data-stu-id="84782-112">Although RARP provides a service for dynamic allocation of IP addresses, it has several shortcomings.</span></span> <span data-ttu-id="84782-113">La limitación más evidente es que RARP solo proporciona una asignación dinámica de la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="84782-113">The most glaring deficiency is that RARP only provides dynamic allocation of the IP address.</span></span> <span data-ttu-id="84782-114">En la mayoría de los casos, es necesaria una mayor información para que un dispositivo pueda participar correctamente en una red.</span><span class="sxs-lookup"><span data-stu-id="84782-114">In most situations, more information is necessary in order for a device to properly participate on a network.</span></span> <span data-ttu-id="84782-115">Además de una dirección IP, la mayoría de los dispositivos necesitan la máscara de red y la dirección IP de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="84782-115">In addition to an IP address, most devices need the network mask and the gateway IP address.</span></span> <span data-ttu-id="84782-116">También es posible que se necesite la dirección IP de un servidor DNS y otra información de la red.</span><span class="sxs-lookup"><span data-stu-id="84782-116">The IP address of a DNS server and other network information may also be needed.</span></span> <span data-ttu-id="84782-117">RARP no tiene la capacidad de proporcionar esta información.</span><span class="sxs-lookup"><span data-stu-id="84782-117">RARP does not have the ability to provide this information.</span></span>

## <a name="rarp-alternatives"></a><span data-ttu-id="84782-118">Alternativas de RARP</span><span class="sxs-lookup"><span data-stu-id="84782-118">RARP Alternatives</span></span>

<span data-ttu-id="84782-119">Con el fin de superar las limitaciones de RARP, los investigadores han desarrollado un mecanismo de asignación de direcciones IP más completo denominado protocolo de arranque (BOOTP).</span><span class="sxs-lookup"><span data-stu-id="84782-119">In order to overcome the deficiencies of RARP, researchers developed a more comprehensive IP address allocation mechanism called the Bootstrap Protocol (BOOTP).</span></span> <span data-ttu-id="84782-120">Este protocolo tiene la capacidad de asignar dinámicamente una dirección IP y también proporcionar información adicional sobre la red.</span><span class="sxs-lookup"><span data-stu-id="84782-120">This protocol has the ability to dynamically allocate an IP address and also provide additional important network information.</span></span> <span data-ttu-id="84782-121">Sin embargo, BOOTP tiene el inconveniente de estar diseñado para configuraciones de red estáticas.</span><span class="sxs-lookup"><span data-stu-id="84782-121">However, BOOTP has the drawback of being designed for static network configurations.</span></span> <span data-ttu-id="84782-122">No permite la asignación de direcciones rápidas o automatizadas.</span><span class="sxs-lookup"><span data-stu-id="84782-122">It does not allow for quick or automated address assignment.</span></span>

<span data-ttu-id="84782-123">Aquí es donde el protocolo de configuración dinámica de host (DHCP) es muy útil.</span><span class="sxs-lookup"><span data-stu-id="84782-123">This is where the Dynamic Host Configuration Protocol (DHCP) is extremely useful.</span></span> <span data-ttu-id="84782-124">DHCP está diseñado para ampliar la funcionalidad básica de BOOTP con el fin de incluir la asignación de servidor IP totalmente automatizada y la asignación de direcciones IP completamente dinámicas a través de la "concesión" de una dirección IP a un cliente durante un período de tiempo especificado.</span><span class="sxs-lookup"><span data-stu-id="84782-124">DHCP is designed to extend the basic functionality of BOOTP to include completely automated IP server allocation and completely dynamic IP address allocation through “leasing” an IP address to a client for a specified period of time.</span></span> <span data-ttu-id="84782-125">DHCP también se puede configurar para asignar direcciones IP de forma estática como BOOTP.</span><span class="sxs-lookup"><span data-stu-id="84782-125">DHCP can also be configured to allocate IP addresses in a static manner like BOOTP.</span></span>

## <a name="dhcp-messages"></a><span data-ttu-id="84782-126">Mensajes DHCP</span><span class="sxs-lookup"><span data-stu-id="84782-126">DHCP Messages</span></span>

<span data-ttu-id="84782-127">Aunque DHCP mejora en gran medida la funcionalidad de BOOTP, DHCP usa el mismo formato de mensaje que BOOTP y admite las mismas opciones de proveedor que BOOTP.</span><span class="sxs-lookup"><span data-stu-id="84782-127">Although DHCP greatly enhances the functionality of BOOTP, DHCP uses the same message format as BOOTP and supports the same vendor options as BOOTP.</span></span> <span data-ttu-id="84782-128">Para realizar su función, DHCP introduce siete nuevas opciones específicas de DHCP, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="84782-128">In order to perform its function, DHCP introduces seven new DHCP-specific options, as follows:</span></span>

- <span data-ttu-id="84782-129">DISCOVER (1) (enviada por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="84782-129">DISCOVER (1) (sent by DHCP Client)</span></span>
- <span data-ttu-id="84782-130">OFFER (2) (enviada por el servidor DHCP)</span><span class="sxs-lookup"><span data-stu-id="84782-130">OFFER (2) (sent by DHCP Server)</span></span>
- <span data-ttu-id="84782-131">REQUEST (3) (enviada por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="84782-131">REQUEST (3) (sent by DHCP Client)</span></span>
- <span data-ttu-id="84782-132">DECLINE (4) (enviada por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="84782-132">DECLINE (4) (sent by DHCP Client)</span></span>
- <span data-ttu-id="84782-133">ACK (5) (enviada por el servidor DHCP)</span><span class="sxs-lookup"><span data-stu-id="84782-133">ACK (5) (sent by DHCP Server)</span></span>
- <span data-ttu-id="84782-134">NACK (6) (enviada por el servidor DHCP)</span><span class="sxs-lookup"><span data-stu-id="84782-134">NACK (6) (sent by DHCP Server)</span></span>
- <span data-ttu-id="84782-135">RELEASE (7) (enviada por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="84782-135">RELEASE (7) (sent by DHCP Client)</span></span>
- <span data-ttu-id="84782-136">INFORM (8) (enviada por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="84782-136">INFORM (8) (sent by DHCP Client)</span></span>
- <span data-ttu-id="84782-137">FORCERENEW (9) (enviado por el cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="84782-137">FORCERENEW (9) (sent by DHCP Client)</span></span>

## <a name="dhcp-communication"></a><span data-ttu-id="84782-138">Comunicación DHCP</span><span class="sxs-lookup"><span data-stu-id="84782-138">DHCP Communication</span></span>

<span data-ttu-id="84782-139">El servidor DHCP emplea el protocolo UDP para recibir solicitudes de cliente DHCP y transmitir respuestas.</span><span class="sxs-lookup"><span data-stu-id="84782-139">The DHCP Server utilizes the UDP protocol to receive DHCP Client requests and transmit responses.</span></span> <span data-ttu-id="84782-140">Antes de tener una dirección IP, los mensajes UDP que llevan la información de DHCP se envían y se reciben mediante la dirección IP de difusión 255.255.255.255.</span><span class="sxs-lookup"><span data-stu-id="84782-140">Prior to having an IP address, UDP messages carrying the DHCP information are sent and received by utilizing the IP broadcast address of 255.255.255.255.</span></span> <span data-ttu-id="84782-141">Sin embargo, si el cliente conoce la dirección del servidor DHCP, puede enviar mensajes DHCP mediante mensajes de unidifusión.</span><span class="sxs-lookup"><span data-stu-id="84782-141">However, if the Client knows the address of the DHCP Server it may send DHCP messages using unicast messages.</span></span>

## <a name="dhcp-server-state-machine"></a><span data-ttu-id="84782-142">Máquina de estados del servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="84782-142">DHCP Server State Machine</span></span>

<span data-ttu-id="84782-143">El servidor DHCP se implementa como una máquina de estados de dos pasos procesada por un subproceso DHCP interno que se crea durante el procesamiento de *nx_dhcp_server_create*.</span><span class="sxs-lookup"><span data-stu-id="84782-143">The DHCP Server is implemented as a two-step state machine processed by an internal DHCP thread that is created during *nx_dhcp_server_create* processing.</span></span> <span data-ttu-id="84782-144">Los estados principales del servidor DHCP son 1) la recepción de un mensaje DISCOVER de un cliente DHCP y 2) la recepción de un mensaje REQUEST.</span><span class="sxs-lookup"><span data-stu-id="84782-144">The main states of DHCP Server are 1) receiving a DISCOVER message from a DHCP client and 2) receiving a REQUEST message.</span></span>

<span data-ttu-id="84782-145">A continuación se indican los estados de cliente DHCP correspondientes:</span><span class="sxs-lookup"><span data-stu-id="84782-145">Below are the corresponding DHCP Client states:</span></span>

- <span data-ttu-id="84782-146">**NX_DHCP_STATE_BOOT**: a partir de una dirección IP anterior</span><span class="sxs-lookup"><span data-stu-id="84782-146">**NX_DHCP_STATE_BOOT** Starting with a previous IP address</span></span>
- <span data-ttu-id="84782-147">**NX_DHCP_STATE_INIT**: sin ningún valor de dirección IP anterior inicial</span><span class="sxs-lookup"><span data-stu-id="84782-147">**NX_DHCP_STATE_INIT** Starting with no previous IP address value</span></span>
- <span data-ttu-id="84782-148">**NX_DHCP_STATE_SELECTING**: a la espera de una respuesta de un servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="84782-148">**NX_DHCP_STATE_SELECTING** Waiting for a response from any DHCP server</span></span>
- <span data-ttu-id="84782-149">**NX_DHCP_STATE_REQUESTING**: servidor DHCP identificado, solicitud de dirección IP enviada</span><span class="sxs-lookup"><span data-stu-id="84782-149">**NX_DHCP_STATE_REQUESTING** DHCP Server identified, IP address request sent</span></span>
- <span data-ttu-id="84782-150">**NX_DHCP_STATE_BOUND**: concesión de dirección IP DHCP establecida</span><span class="sxs-lookup"><span data-stu-id="84782-150">**NX_DHCP_STATE_BOUND** DHCP IP Address lease established</span></span>
- <span data-ttu-id="84782-151">**NX_DHCP_STATE_RENEWING**: tiempo de renovación de concesión de dirección IP DHCP transcurrido, renovación solicitada</span><span class="sxs-lookup"><span data-stu-id="84782-151">**NX_DHCP_STATE_RENEWING** DHCP IP Address lease renewal time elapsed, renewal requested</span></span>
- <span data-ttu-id="84782-152">**NX_DHCP_STATE_REBINDING**: tiempo de reenlace de concesión de dirección IP DHCP transcurrido, renovación solicitada</span><span class="sxs-lookup"><span data-stu-id="84782-152">**NX_DHCP_STATE_REBINDING** DHCP IP Address lease rebind time elapsed, renewal requested</span></span>
- <span data-ttu-id="84782-153">**NX_DHCP_STATE_FORCERENEW**: concesión de la dirección IP DHCP establecida, forzar la renovación por servidor o por aplicación</span><span class="sxs-lookup"><span data-stu-id="84782-153">**NX_DHCP_STATE_FORCERENEW** DHCP IP Address lease established, force renewal by server or by application</span></span>
- <span data-ttu-id="84782-154">**NX_DHCP_STATE_FAILED**: no se ha encontrado ningún servidor o no se ha recibido respuesta del servidor</span><span class="sxs-lookup"><span data-stu-id="84782-154">**NX_DHCP_STATE_FAILED** No server found or no response from server received</span></span>

## <a name="dhcp-additional-parameters"></a><span data-ttu-id="84782-155">Parámetros adicionales de DHCP</span><span class="sxs-lookup"><span data-stu-id="84782-155">DHCP Additional Parameters</span></span>

<span data-ttu-id="84782-156">El servidor DHCP de NetX Duo tiene una lista predeterminada de parámetros de opciones que se establece en la opción configurable NX_DHCP_DEFAULT_SERVER_OPTION_LIST *en nx_dhcp_server.h* para proporcionar a los clientes DHCP parámetros de configuración de red comunes o críticos, como la dirección de puerta de enlace o ruta y el servidor DNS para el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="84782-156">The NetX Duo DHCP Server has a default list of option parameters which is set in the configurable option NX_DHCP_DEFAULT_SERVER_OPTION_LIST in *nxd_dhcp_server.h* to supply DHCP Clients with common/critical network configuration parameters e.g. router or gateway address and DNS server for the DHCP Client.</span></span>

## <a name="dhcp-rfcs"></a><span data-ttu-id="84782-157">RFC de DHCP</span><span class="sxs-lookup"><span data-stu-id="84782-157">DHCP RFCs</span></span>

<span data-ttu-id="84782-158">El servidor DHCP de NetX Duo es compatible con RFC2132, RFC2131 y RFC relacionados.</span><span class="sxs-lookup"><span data-stu-id="84782-158">NetX Duo DHCP Server is compliant with RFC2132, RFC2131, and related RFCs.</span></span>