---
title: 'Capítulo 1: Introducción a mDNS y DNS-SD de Azure RTOS NetX Duo'
description: MDN y DNS-SD de Azure RTOS NetX Duo aumentan el servicio DNS tradicional.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b46539ee4d502fa4c90fb3392e25cd3bee40dc5b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814670"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a><span data-ttu-id="1da32-103">Capítulo 1: Introducción a mDNS y DNS-SD de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="1da32-103">Chapter 1 - Introduction to Azure RTOS NetX Duo mDNS/DNS-SD</span></span>

<span data-ttu-id="1da32-104">mDNS y DNS-SD son protocolos diseñados para ampliar el servicio DNS tradicional.</span><span class="sxs-lookup"><span data-stu-id="1da32-104">The mDNS and DNS-SD are protocols designed to augment the traditional DNS service.</span></span> <span data-ttu-id="1da32-105">mDNS proporciona la búsqueda del servicio y el nombre de host a los nodos de la red local.</span><span class="sxs-lookup"><span data-stu-id="1da32-105">mDNS provides host name and service lookup to the nodes on the local network.</span></span> <span data-ttu-id="1da32-106">Cada nodo usa el canal de multidifusión IPv4 o IPv6 para anunciar los servicios que ofrece a sus vecinos, responde a las consultas de sus vecinos y envía consultas sobre el comportamiento de sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1da32-106">Each node uses IPv4 or IPv6 multicast channel to announce services it offers to its neighbors, responds to queries from its neighbors, and sends queries on behave of its applications.</span></span> <span data-ttu-id="1da32-107">Por naturaleza, mDNS funciona en un entorno distribuido, por lo que elimina el concepto de centralización.</span><span class="sxs-lookup"><span data-stu-id="1da32-107">By design, mDNS operates in a distributed environment, thus eliminates a centralized serve.</span></span>

<span data-ttu-id="1da32-108">DNS-SD se basa en mDNS.</span><span class="sxs-lookup"><span data-stu-id="1da32-108">DNS-SD is built on top of mDNS.</span></span> <span data-ttu-id="1da32-109">DNS-SD permite que los nodos anuncien los servicios que proporcionan a la red local o detecten los servicios que ofrecen otros nodos en la red local.</span><span class="sxs-lookup"><span data-stu-id="1da32-109">DNS-SD allows nodes to announce services they provide to the local network or to discover services offered by other nodes on the local network.</span></span> <span data-ttu-id="1da32-110">En todo el documento, el término *mDNS* hace referencia a los servicios que cubren las especificaciones mDNS y DNS-SD.</span><span class="sxs-lookup"><span data-stu-id="1da32-110">Throughout the document, the term *mDNS* refers to the services that cover both the mDNS specification and the DNS-SD specification.</span></span>

## <a name="mdns-standard"></a><span data-ttu-id="1da32-111">Estándar mDNS</span><span class="sxs-lookup"><span data-stu-id="1da32-111">mDNS Standard</span></span>

<span data-ttu-id="1da32-112">La implementación de mDNS y DNS-SD de NetX Duo cumple con los protocolos RFC siguientes:</span><span class="sxs-lookup"><span data-stu-id="1da32-112">NetX Duo mDNS/DNS-SD implementation conforms to the following RFCs:</span></span>

- <span data-ttu-id="1da32-113">RFC 6762: especificación de mDNS</span><span class="sxs-lookup"><span data-stu-id="1da32-113">RFC 6762: mDNS Specification</span></span>
- <span data-ttu-id="1da32-114">RFC 6763: especificación de DNS-SD</span><span class="sxs-lookup"><span data-stu-id="1da32-114">RFC 6763: DNS-SD Specification</span></span>