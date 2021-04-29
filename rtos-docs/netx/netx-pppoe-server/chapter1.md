---
title: 'Capítulo 1: Introducción al servidor PPPoE de Azure RTOS NetX'
description: Este documento se centra en los detalles del módulo PPPoE de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 85a762f669e31c7e753f78b270ced15677a87c4c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815126"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-server"></a><span data-ttu-id="16a8a-103">Capítulo 1: Introducción al servidor PPPoE de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="16a8a-103">Chapter 1 - Introduction to Azure RTOS NetX PPPoE Server</span></span>

<span data-ttu-id="16a8a-104">PPP a través de Ethernet (PPPoE) permite que los hosts se conecten al servidor PPP a través de Ethernet en lugar de la comunicación de línea de serie tradicional basada en caracteres.</span><span class="sxs-lookup"><span data-stu-id="16a8a-104">PPP over Ethernet (PPPoE) allows hosts to connect to PPP server via Ethernet instead of the traditional character-based serial line communication.</span></span> <span data-ttu-id="16a8a-105">Los detalles técnicos de PPPoE se describen en RFC 2516: un método para transmitir PPP a través de Ethernet (PPPoE).</span><span class="sxs-lookup"><span data-stu-id="16a8a-105">The technical details of PPPoE are described in RFC 2516: A Method for Transmitting PPP over Ethernet (PPPoE).</span></span> <span data-ttu-id="16a8a-106">Este documento se centra en los detalles del módulo PPPoE de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="16a8a-106">This document focuses on the details of Azure RTOS NetX PPPoE module.</span></span>

<span data-ttu-id="16a8a-107">Para proporcionar una conexión punto a punto a través de Ethernet, cada sesión PPP debe conocer la dirección Ethernet del elemento remoto del mismo nivel, así como establecer un identificador de sesión único.</span><span class="sxs-lookup"><span data-stu-id="16a8a-107">To provide a point-to-point connection over Ethernet, each PPP session must learn the Ethernet address of the remote peer, as well as establish a unique session identifier.</span></span>

<span data-ttu-id="16a8a-108">Según RFC 2516, PPPoE consta de dos fases: la fase de detección y la fase de sesión de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="16a8a-108">According to RFC 2516, PPPoE consists of two stages: the Discovery stage, and PPPoE Session stage.</span></span> <span data-ttu-id="16a8a-109">Cuando un host (cliente) desea iniciar una sesión de PPP, primero debe realizar la detección para buscar el servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="16a8a-109">When a host (client) wishes to start a PPP session, it must first perform Discovery to find PPPoE server.</span></span> <span data-ttu-id="16a8a-110">Este paso también permite que el servidor y el cliente identifiquen las direcciones MAC de Ethernet y SESSION_ID, que se usarán para el resto de la sesión de PPP.</span><span class="sxs-lookup"><span data-stu-id="16a8a-110">This step also allows the server and the client to identify each other's Ethernet MAC address and SESSION_ID, which will be used for the rest of the PPP session.</span></span>

<span data-ttu-id="16a8a-111">Un marco Ethernet es lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="16a8a-111">An Ethernet frame is as follows:</span></span>

![Diagrama que muestra un marco Ethernet.](media/netx-pppoe-server-01.png)

<span data-ttu-id="16a8a-113">La carga de Ethernet para PPPoE es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="16a8a-113">The Ethernet payload for PPPoE is as follows:</span></span>

![Diagrama que muestra una carga de Ethernet para PPPoE.](media/netx-pppoe-server-02.png)

## <a name="pppoe-discovery-stage"></a><span data-ttu-id="16a8a-115">Fase de detección de PPPoE</span><span class="sxs-lookup"><span data-stu-id="16a8a-115">PPPoE Discovery Stage</span></span>

<span data-ttu-id="16a8a-116">La fase de detección de PPPoE permite a los clientes seleccionar un servidor de todos los servidores disponibles en la red, de forma eficaz, para crear una sesión antes de que se intercambien los marcos PPP.</span><span class="sxs-lookup"><span data-stu-id="16a8a-116">The PPPoE Discovery stage allows clients to select a server from all available servers on the network, effectively to create a session prior to PPP frames being exchanged.</span></span> <span data-ttu-id="16a8a-117">Al final de la fase de detección, tanto el cliente como el servidor deben estar de acuerdo en un identificador de sesión único y ambos lados deben conocer la dirección MAC del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="16a8a-117">At the end of the discovery stage, both the client and the server shall agree on a unique session ID, and both sides need to know peer's MAC address.</span></span>

| <span data-ttu-id="16a8a-118">Mensaje de detección</span><span class="sxs-lookup"><span data-stu-id="16a8a-118">Discovery Message</span></span>                                  | <span data-ttu-id="16a8a-119">Código</span><span class="sxs-lookup"><span data-stu-id="16a8a-119">Code</span></span> | <span data-ttu-id="16a8a-120">Dirección</span><span class="sxs-lookup"><span data-stu-id="16a8a-120">Direction</span></span>                                     |
| -------------------------------------------------- | ---- | --------------------------------------------- |
| <span data-ttu-id="16a8a-121">Inicio de detección activa de PPPoE (PADI)</span><span class="sxs-lookup"><span data-stu-id="16a8a-121">PPPoE Active Discovery Initiation (PADI)</span></span>           | <span data-ttu-id="16a8a-122">0x09</span><span class="sxs-lookup"><span data-stu-id="16a8a-122">0x09</span></span> | <span data-ttu-id="16a8a-123">De cliente a difusión</span><span class="sxs-lookup"><span data-stu-id="16a8a-123">From Client to broadcast</span></span>                      |
| <span data-ttu-id="16a8a-124">Oferta de detección activa de PPPoE (PADO)</span><span class="sxs-lookup"><span data-stu-id="16a8a-124">PPPoE Active Discovery Offer (PADO)</span></span>                | <span data-ttu-id="16a8a-125">0x07</span><span class="sxs-lookup"><span data-stu-id="16a8a-125">0x07</span></span> | <span data-ttu-id="16a8a-126">De servidor a cliente</span><span class="sxs-lookup"><span data-stu-id="16a8a-126">From Server to Client</span></span>                         |
| <span data-ttu-id="16a8a-127">Solicitud de detección activa de PPPoE (PADR)</span><span class="sxs-lookup"><span data-stu-id="16a8a-127">PPPoE Active Discovery Request (PADR)</span></span>              | <span data-ttu-id="16a8a-128">0x19</span><span class="sxs-lookup"><span data-stu-id="16a8a-128">0x19</span></span> | <span data-ttu-id="16a8a-129">De cliente a servidor</span><span class="sxs-lookup"><span data-stu-id="16a8a-129">From Client to Server</span></span>                         |
| <span data-ttu-id="16a8a-130">Sesión de detección activa de PPPOE: confirmación (PADS)</span><span class="sxs-lookup"><span data-stu-id="16a8a-130">PPPOE Active Discovery Session-confirmation (PADS)</span></span> | <span data-ttu-id="16a8a-131">0x65</span><span class="sxs-lookup"><span data-stu-id="16a8a-131">0x65</span></span> | <span data-ttu-id="16a8a-132">De servidor a cliente</span><span class="sxs-lookup"><span data-stu-id="16a8a-132">From Server to Client</span></span>                         |
| <span data-ttu-id="16a8a-133">Finalización de detección activa de PPPoE (PADT)</span><span class="sxs-lookup"><span data-stu-id="16a8a-133">PPPoE Active Discovery Terminate (PADT)</span></span>            | <span data-ttu-id="16a8a-134">0xa7</span><span class="sxs-lookup"><span data-stu-id="16a8a-134">0xa7</span></span> | <span data-ttu-id="16a8a-135">Se puede iniciar desde un servidor o un cliente</span><span class="sxs-lookup"><span data-stu-id="16a8a-135">Can be initiated from either server or client</span></span> |

<span data-ttu-id="16a8a-136">Todos los marcos de Ethernet de detección tienen el campo ETHER_TYPE establecido en el valor 0x8863.</span><span class="sxs-lookup"><span data-stu-id="16a8a-136">All Discovery Ethernet frames have the ETHER_TYPE field set to the value 0x8863.</span></span>

## <a name="pppoe-session-message"></a><span data-ttu-id="16a8a-137">Mensaje de sesión de PPPoE</span><span class="sxs-lookup"><span data-stu-id="16a8a-137">PPPoE Session Message</span></span>

<span data-ttu-id="16a8a-138">Una vez que el cliente y el servidor crean una sesión, las tramas PPP se pueden transferir como mensajes de sesión PPPoE.</span><span class="sxs-lookup"><span data-stu-id="16a8a-138">After the client and the server create a session, PPP frames can be transferred as PPPoE Session messages.</span></span> <span data-ttu-id="16a8a-139">Durante una sesión, el SESSION_ID no debe cambiar y debe ser el valor del servidor asignado durante la fase de detección.</span><span class="sxs-lookup"><span data-stu-id="16a8a-139">During a session, the SESSION_ID must not change and must be the value the server assigned during the Discovery stage.</span></span>

<span data-ttu-id="16a8a-140">Todos los marcos de Ethernet de sesión de PPPoE tienen el campo ETHER_TYPE establecido en el valor 0x8864.</span><span class="sxs-lookup"><span data-stu-id="16a8a-140">All PPPoE Session Ethernet frames have the ETHER_TYPE field set to the value 0x8864.</span></span>