---
title: 'Capítulo 1: Introducción a LWM2M de Azure RTOS NetX'
description: El protocolo LWM2M de Azure RTOS NetX implementa la parte de cliente del estándar de protocolo ligero de máquina a máquina.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c29af430975266eed684bd1de38d9e5d7e2586a6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815193"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a><span data-ttu-id="ee97b-103">Capítulo 1: Introducción a LWM2M de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="ee97b-103">Chapter 1 - Introduction to Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="ee97b-104">El protocolo LWM2M de Azure RTOS NetX implementa la parte de cliente del estándar de protocolo ligero de máquina a máquina.</span><span class="sxs-lookup"><span data-stu-id="ee97b-104">The Azure RTOS NetX LWM2M Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span>

## <a name="netx-lwm2m-requirements"></a><span data-ttu-id="ee97b-105">Requisitos de LWM2M de NetX</span><span class="sxs-lookup"><span data-stu-id="ee97b-105">NetX LWM2M Requirements</span></span>

<span data-ttu-id="ee97b-106">Para que funcione correctamente, la biblioteca en tiempo de ejecución de LWM2M de NetX requiere que ya se haya creado una instancia de IP de NetX.</span><span class="sxs-lookup"><span data-stu-id="ee97b-106">In order to function properly, the NetX LWM2M run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="ee97b-107">El paquete de LWM2M de NetX no tiene ningún requisito adicional.</span><span class="sxs-lookup"><span data-stu-id="ee97b-107">The NetX LWM2M package has no further requirements.</span></span>

## <a name="netx-lwm2m-rfcs"></a><span data-ttu-id="ee97b-108">RFC de LWM2M de NetX</span><span class="sxs-lookup"><span data-stu-id="ee97b-108">NetX LWM2M RFCs</span></span>

<span data-ttu-id="ee97b-109">LWM2M de NetX es compatible con OMA-TS-LightweightM2M-V1_0-20170208-A y las siguientes RFC relacionadas con el protocolo de aplicación restringida (CoAP):</span><span class="sxs-lookup"><span data-stu-id="ee97b-109">NetX LWM2M is compliant with OMA-TS-LightweightM2M-V1_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP):</span></span>

- <span data-ttu-id="ee97b-110">**RFC 7252**: el protocolo de aplicación restringida (CoAP)</span><span class="sxs-lookup"><span data-stu-id="ee97b-110">**RFC 7252**: The Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="ee97b-111">**RFC 7641**: observación de recursos en el protocolo de aplicación restringida (CoAP)</span><span class="sxs-lookup"><span data-stu-id="ee97b-111">**RFC 7641**: Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="ee97b-112">**RFC 6690**: formato de vínculo de entornos RESTful restringidos (CoRE)</span><span class="sxs-lookup"><span data-stu-id="ee97b-112">**RFC 6690**: Constrained RESTful Environments (CoRE) Link Format</span></span>