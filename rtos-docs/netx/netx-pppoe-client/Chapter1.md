---
title: 'Capítulo 1: Introducción al cliente PPPoE de Azure RTOS NetX'
description: Este capítulo contiene los detalles del módulo PPPoE de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bbf1e064bb38754bd67b279a0fd60d46d3d6d557
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815149"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-client"></a><span data-ttu-id="cd8b5-103">Capítulo 1: Introducción al cliente PPPoE de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="cd8b5-103">Chapter 1 - Introduction to Azure RTOS NetX PPPoE Client</span></span>

<span data-ttu-id="cd8b5-104">PPP a través de Ethernet (PPPoE) permite que los hosts se conecten al servidor PPP a través de Ethernet en lugar de la comunicación de línea de serie tradicional basada en caracteres.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-104">PPP over Ethernet (PPPoE) allows hosts to connect to PPP server via Ethernet instead of the traditional character-based serial line communication.</span></span>  <span data-ttu-id="cd8b5-105">Los detalles técnicos de PPPoE se describen en RFC 2516: un método para transmitir PPP a través de Ethernet (PPPoE).</span><span class="sxs-lookup"><span data-stu-id="cd8b5-105">The technical details of PPPoE are described in RFC 2516:  A Method for Transmitting PPP over Ethernet (PPPoE).</span></span> <span data-ttu-id="cd8b5-106">Este documento se centra en los detalles del módulo PPPoE de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-106">This document focuses on the details of  Azure RTOS NetX PPPoE module.</span></span>

<span data-ttu-id="cd8b5-107">Para proporcionar una conexión punto a punto a través de Ethernet, cada sesión PPP debe conocer la dirección Ethernet del elemento remoto del mismo nivel, así como establecer un identificador de sesión único.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-107">To provide a point-to-point connection over Ethernet, each PPP session must learn the Ethernet address of the remote peer, as well as establish a unique session identifier.</span></span>

<span data-ttu-id="cd8b5-108">Según RFC 2516, PPPoE consta de dos fases: la fase de detección y la fase de sesión de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-108">According to RFC 2516, PPPoE consists of two stages: the Discovery stage, and PPPoE Session stage.</span></span> <span data-ttu-id="cd8b5-109">Cuando un host (cliente) desea iniciar una sesión de PPP, primero debe realizar la detección para buscar el servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-109">When a host (client) wishes to start a PPP session, it must first perform Discovery to find PPPoE server.</span></span> <span data-ttu-id="cd8b5-110">Este paso también permite que el servidor y el cliente identifiquen las direcciones MAC de Ethernet y SESSION_ID, que se usarán para el resto de la sesión de PPP.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-110">This step also allows the server and the client to identify each other’s Ethernet MAC address and SESSION_ID, which will be used for the rest of the PPP session.</span></span>

<span data-ttu-id="cd8b5-111">Un marco Ethernet es lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="cd8b5-111">An Ethernet frame is as follows:</span></span>

![Marco Ethernet](media/ethernet-frame.png)

<span data-ttu-id="cd8b5-113">La carga de Ethernet para PPPoE es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="cd8b5-113">The Ethernet payload for PPPoE is as follows:</span></span>

![Carga de Ethernet](media/ethernet-payload.png)

## <a name="pppoe-discovery-stage"></a><span data-ttu-id="cd8b5-115">Fase de detección de PPPoE</span><span class="sxs-lookup"><span data-stu-id="cd8b5-115">PPPoE Discovery Stage</span></span>

<span data-ttu-id="cd8b5-116">La fase de detección de PPPoE permite a los clientes seleccionar un servidor de todos los servidores disponibles en la red, de forma eficaz, para crear una sesión antes de que se intercambien los marcos PPP.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-116">The PPPoE Discovery stage allows clients to select a server from all available servers on the network, effectively to create a session prior to PPP frames being exchanged.</span></span>  <span data-ttu-id="cd8b5-117">Al final de la fase de detección, tanto el cliente como el servidor deben estar de acuerdo en un identificador de sesión único y ambos lados deben conocer la dirección MAC del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-117">At the end of the discovery stage, both the client and the server shall agree on a unique session ID, and both sides need to know peer’s MAC address.</span></span>

| <span data-ttu-id="cd8b5-118">Mensaje de detección</span><span class="sxs-lookup"><span data-stu-id="cd8b5-118">Discovery Message</span></span> | <span data-ttu-id="cd8b5-119">Código</span><span class="sxs-lookup"><span data-stu-id="cd8b5-119">Code</span></span> | <span data-ttu-id="cd8b5-120">Dirección</span><span class="sxs-lookup"><span data-stu-id="cd8b5-120">Direction</span></span> |
| ----------------- | ---- | --------- |
| <span data-ttu-id="cd8b5-121">Inicio de detección activa de PPPoE (PADI)</span><span class="sxs-lookup"><span data-stu-id="cd8b5-121">PPPoE Active Discovery Initiation (PADI)</span></span> | <span data-ttu-id="cd8b5-122">0x09</span><span class="sxs-lookup"><span data-stu-id="cd8b5-122">0x09</span></span> | <span data-ttu-id="cd8b5-123">De cliente a difusión</span><span class="sxs-lookup"><span data-stu-id="cd8b5-123">From Client to broadcast</span></span> |
| <span data-ttu-id="cd8b5-124">Oferta de detección activa de PPPoE (PADO)</span><span class="sxs-lookup"><span data-stu-id="cd8b5-124">PPPoE Active Discovery Offer (PADO)</span></span> | <span data-ttu-id="cd8b5-125">0x07</span><span class="sxs-lookup"><span data-stu-id="cd8b5-125">0x07</span></span> | <span data-ttu-id="cd8b5-126">De servidor a cliente</span><span class="sxs-lookup"><span data-stu-id="cd8b5-126">From Server to Client</span></span> |
| <span data-ttu-id="cd8b5-127">Solicitud de detección activa de PPPoE (PADR)</span><span class="sxs-lookup"><span data-stu-id="cd8b5-127">PPPoE Active Discovery Request (PADR)</span></span> | <span data-ttu-id="cd8b5-128">0x19</span><span class="sxs-lookup"><span data-stu-id="cd8b5-128">0x19</span></span> | <span data-ttu-id="cd8b5-129">De cliente a servidor</span><span class="sxs-lookup"><span data-stu-id="cd8b5-129">From Client to Server</span></span> |
| <span data-ttu-id="cd8b5-130">Sesión de detección activa de PPPOE: confirmación (PADS)</span><span class="sxs-lookup"><span data-stu-id="cd8b5-130">PPPOE Active Discovery Session-confirmation (PADS)</span></span> | <span data-ttu-id="cd8b5-131">0x65</span><span class="sxs-lookup"><span data-stu-id="cd8b5-131">0x65</span></span> | <span data-ttu-id="cd8b5-132">De servidor a cliente</span><span class="sxs-lookup"><span data-stu-id="cd8b5-132">From Server to Client</span></span> |
| <span data-ttu-id="cd8b5-133">Finalización de detección activa de PPPoE (PADT)</span><span class="sxs-lookup"><span data-stu-id="cd8b5-133">PPPoE Active Discovery Terminate (PADT)</span></span> | <span data-ttu-id="cd8b5-134">0xa7</span><span class="sxs-lookup"><span data-stu-id="cd8b5-134">0xa7</span></span> | <span data-ttu-id="cd8b5-135">Se puede iniciar desde un servidor o un cliente</span><span class="sxs-lookup"><span data-stu-id="cd8b5-135">Can be initiated from either server or client</span></span> |

<span data-ttu-id="cd8b5-136">Todos los marcos de Ethernet de detección tienen el campo ETHER_TYPE establecido en el valor 0x8863.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-136">All Discovery Ethernet frames have the ETHER_TYPE field set to the value 0x8863.</span></span>

## <a name="pppoe-session-message"></a><span data-ttu-id="cd8b5-137">Mensaje de sesión de PPPoE</span><span class="sxs-lookup"><span data-stu-id="cd8b5-137">PPPoE Session Message</span></span>

<span data-ttu-id="cd8b5-138">Una vez que el cliente y el servidor crean una sesión, las tramas PPP se pueden transferir como mensajes de sesión PPPoE.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-138">After the client and the server create a session, PPP frames can be transferred as PPPoE Session messages.</span></span>  <span data-ttu-id="cd8b5-139">Durante una sesión, el SESSION_ID no debe cambiar y debe ser el valor del servidor asignado durante la fase de detección.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-139">During a session, the SESSION_ID must not change and must be the value the server assigned during the Discovery stage.</span></span>

<span data-ttu-id="cd8b5-140">Todos los marcos de Ethernet de sesión de PPPoE tienen el campo ETHER_TYPE establecido en el valor 0x8864.</span><span class="sxs-lookup"><span data-stu-id="cd8b5-140">All PPPoE Session Ethernet frames have the ETHER_TYPE field set to the value 0x8864.</span></span>
