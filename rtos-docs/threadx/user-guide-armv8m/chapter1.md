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
# <a name="chapter-1--overview"></a>Capítulo 1: Información general

La arquitectura ARMv8-M incorpora nuevas características de seguridad, entre las que se incluye TrustZone, que permite etiquetar la memoria como segura o no segura. Siguiendo las directrices de ARM, ThreadX (y la aplicación de usuario) están diseñadas para ejecutarse en modo no seguro. ThreadX (y la aplicación de usuario) también se pueden ejecutar en modo seguro. Para interactuar con el software de modo seguro se necesitan algunas API de ThreadX nuevas. En este documento se describen estos servicios de ThreadX que son específicos de la arquitectura ARMv8-M, entre los que se incluyen Cortex-M23, Cortex-M33, Cortex-M35P y Cortex-M55.
