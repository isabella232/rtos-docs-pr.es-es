---
title: 'Capítulo 1: Introducción a Azure RTOS ThreadX para ARMv8-M'
description: Este capítulo es el punto de partida de lectura sobre el anexo de Azure RTOS ThreadX para ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 486466f41e64adb9e32ebbd21a22629221ffa9c1
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377537"
---
# <a name="chapter-1--overview"></a><span data-ttu-id="a77f0-103">Capítulo 1: Información general</span><span class="sxs-lookup"><span data-stu-id="a77f0-103">Chapter 1  Overview</span></span>

<span data-ttu-id="a77f0-104">La arquitectura ARMv8-M incorpora nuevas características de seguridad, entre las que se incluye TrustZone, que permite etiquetar la memoria como segura o no segura.</span><span class="sxs-lookup"><span data-stu-id="a77f0-104">The ARMv8-M architecture introduces new security features, including TrustZone, which allows memory to be tagged as secure or non-secure.</span></span> <span data-ttu-id="a77f0-105">Siguiendo las directrices de ARM, ThreadX (y la aplicación de usuario) están diseñadas para ejecutarse en modo no seguro.</span><span class="sxs-lookup"><span data-stu-id="a77f0-105">Following ARM's guidelines, ThreadX (and the user application) is designed to be run in non-secure mode.</span></span> <span data-ttu-id="a77f0-106">ThreadX (y la aplicación de usuario) también se pueden ejecutar en modo seguro.</span><span class="sxs-lookup"><span data-stu-id="a77f0-106">ThreadX (and the user application) can also be run in secure mode.</span></span> <span data-ttu-id="a77f0-107">Para interactuar con el software de modo seguro se necesitan algunas API de ThreadX nuevas.</span><span class="sxs-lookup"><span data-stu-id="a77f0-107">In order to interface with secure mode software, some new ThreadX APIs are necessary.</span></span> <span data-ttu-id="a77f0-108">En este documento se describen estos servicios de ThreadX que son específicos de la arquitectura ARMv8-M, entre los que se incluyen Cortex-M23, Cortex-M33, Cortex-M35P y Cortex-M55.</span><span class="sxs-lookup"><span data-stu-id="a77f0-108">This document describes these ThreadX services that are specific to the ARMv8-M architecture, including the Cortex-M23, Cortex-M33, Cortex-M35P, and Cortex-M55.</span></span>
