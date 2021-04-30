---
title: 'Capítulo 1: Introducción al cliente LWM2M de NetX Duo para Azure RTOS'
description: En este capítulo se incluye una introducción al cliente de protocolo ligero de máquina a máquina de NetX Duo para Azure RTOS.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 12f13c154668b3cadfae0924e59b55631dc27424
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814690"
---
# <a name="chapter-1--introduction-to-lwm2m-client"></a><span data-ttu-id="47848-103">Capítulo 1: Introducción al cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="47848-103">Chapter 1  Introduction to LWM2M Client</span></span>

<span data-ttu-id="47848-104">El protocolo de cliente LWM2M de NetX Duo para Azure RTOS implementa la parte de cliente del estándar del protocolo ligero de máquina a máquina.</span><span class="sxs-lookup"><span data-stu-id="47848-104">The Azure RTOS NetX Duo LWM2M Client Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span> <span data-ttu-id="47848-105">(LWM2M 1.0-20170208A)</span><span class="sxs-lookup"><span data-stu-id="47848-105">(LWM2M 1.0-20170208A)</span></span>

## <a name="netx-lwm2m-client-requirements"></a><span data-ttu-id="47848-106">Requisitos del cliente LWM2M de NetX</span><span class="sxs-lookup"><span data-stu-id="47848-106">NetX LWM2M Client Requirements</span></span>

<span data-ttu-id="47848-107">Para que funcione correctamente, la biblioteca en tiempo de ejecución de LWM2M de NetX requiere que ya se haya creado una instancia de IP de NetX.</span><span class="sxs-lookup"><span data-stu-id="47848-107">In order to function properly, the LWM2M Client run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="47848-108">El paquete de cliente LWM2M de NetX no tiene ningún requisito adicional.</span><span class="sxs-lookup"><span data-stu-id="47848-108">The NetX LWM2M Client package has no further requirements.</span></span>

## <a name="netx-lwm2m-client-rfcs"></a><span data-ttu-id="47848-109">Documentos RFC del cliente LWM2M de NetX</span><span class="sxs-lookup"><span data-stu-id="47848-109">NetX LWM2M Client RFCs</span></span>

<span data-ttu-id="47848-110">El cliente LWM2M es compatible con OMA-TS-LightweightM2M-V1\_0-20170208-A y los siguientes documentos RFC relativos al protocolo de aplicación restringida (CoAP).</span><span class="sxs-lookup"><span data-stu-id="47848-110">LWM2M Client is compliant with OMA-TS-LightweightM2M-V1\_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP).</span></span>

* <span data-ttu-id="47848-111">RFC 7252: El protocolo de aplicación restringida (CoAP)</span><span class="sxs-lookup"><span data-stu-id="47848-111">RFC 7252 The Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="47848-112">RFC 7641: Observación de recursos en el protocolo de aplicación restringida (CoAP)</span><span class="sxs-lookup"><span data-stu-id="47848-112">RFC 7641 Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="47848-113">RFC 6690: Formato de vínculo de entornos RESTful restringidos (CoRE)</span><span class="sxs-lookup"><span data-stu-id="47848-113">RFC 6690 Constrained RESTful Environments (CoRE) Link Format</span></span>

<span data-ttu-id="47848-114">Para más información, consulte [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).</span><span class="sxs-lookup"><span data-stu-id="47848-114">For more information, please see [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).</span></span>