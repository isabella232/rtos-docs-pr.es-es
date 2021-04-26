---
title: 'Apéndice B: códigos de estado de servidor DHCPv6 de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los códigos de estado de servidor DHCPv6 de NetX Duo
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c79a0c0bc9acfcfca69c7333d30cd7cab35ba5f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814758"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a><span data-ttu-id="5403a-103">Apéndice B: códigos de estado de servidor DHCPv6 de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="5403a-103">Appendix B - Azure RTOS NetX Duo DHCPv6 server status codes</span></span>

| <span data-ttu-id="5403a-104">Nombre</span><span class="sxs-lookup"><span data-stu-id="5403a-104">Name</span></span>              | <span data-ttu-id="5403a-105">Código</span><span class="sxs-lookup"><span data-stu-id="5403a-105">Code</span></span>            | <span data-ttu-id="5403a-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="5403a-106">Description</span></span> |
| ------------------- | ------------------- | --------------- |
| <span data-ttu-id="5403a-107">Correcto</span><span class="sxs-lookup"><span data-stu-id="5403a-107">Success</span></span> | <span data-ttu-id="5403a-108">0</span><span class="sxs-lookup"><span data-stu-id="5403a-108">0</span></span> | <span data-ttu-id="5403a-109">Correcto</span><span class="sxs-lookup"><span data-stu-id="5403a-109">Success</span></span> |
| <span data-ttu-id="5403a-110">Error no especificado</span><span class="sxs-lookup"><span data-stu-id="5403a-110">Unspecified Failure</span></span> | <span data-ttu-id="5403a-111">1</span><span class="sxs-lookup"><span data-stu-id="5403a-111">1</span></span> | <span data-ttu-id="5403a-112">Error, motivo sin especificar; este código de estado se establece mediante el servidor para indicar un error general al conceder la solicitud de cliente que no coincide con los demás códigos.</span><span class="sxs-lookup"><span data-stu-id="5403a-112">Failure, reason unspecified; this status code is set by the Server to indicate a general failure in granting the Client request not matching the other codes</span></span> |
| <span data-ttu-id="5403a-113">NoAddress Available</span><span class="sxs-lookup"><span data-stu-id="5403a-113">NoAddress Available</span></span> | <span data-ttu-id="5403a-114">2</span><span class="sxs-lookup"><span data-stu-id="5403a-114">2</span></span> | <span data-ttu-id="5403a-115">El servidor no tiene direcciones disponibles para asignar al cliente.</span><span class="sxs-lookup"><span data-stu-id="5403a-115">Server has no addresses available to assign to the Client</span></span> |
| <span data-ttu-id="5403a-116">NoBinding</span><span class="sxs-lookup"><span data-stu-id="5403a-116">NoBinding</span></span> | <span data-ttu-id="5403a-117">3</span><span class="sxs-lookup"><span data-stu-id="5403a-117">3</span></span> | <span data-ttu-id="5403a-118">La dirección de IA del cliente (enlace) no está disponible; por ejemplo, la dirección IP solicitada no está disponible para el servidor que se va a conceder o asignar a otro cliente.</span><span class="sxs-lookup"><span data-stu-id="5403a-118">Client IA address (binding) is not available e.g. the requested IP address is not available for the Server to lease or assigned to another Client.</span></span> |
| <span data-ttu-id="5403a-119">NotOnLink</span><span class="sxs-lookup"><span data-stu-id="5403a-119">NotOnLink</span></span> | <span data-ttu-id="5403a-120">4</span><span class="sxs-lookup"><span data-stu-id="5403a-120">4</span></span> | <span data-ttu-id="5403a-121">El prefijo de la dirección indica que la dirección IP no es una dirección en un vínculo.</span><span class="sxs-lookup"><span data-stu-id="5403a-121">The prefix for the address indicates the IP address is not an on link address</span></span> |
| <span data-ttu-id="5403a-122">UseMulticast</span><span class="sxs-lookup"><span data-stu-id="5403a-122">UseMulticast</span></span> | <span data-ttu-id="5403a-123">5</span><span class="sxs-lookup"><span data-stu-id="5403a-123">5</span></span> | <span data-ttu-id="5403a-124">Enviado por un servidor en respuesta a la recepción de un mensaje del cliente mediante la dirección de unidifusión del servidor en lugar de la dirección de multidifusión *All_DHCP_Relay_Agents_and_Servers*.</span><span class="sxs-lookup"><span data-stu-id="5403a-124">Sent by a Server in response to receiving a Client message using the Server’s unicast address instead of the *All_DHCP_Relay_Agents_and_Servers* multicast address</span></span> |