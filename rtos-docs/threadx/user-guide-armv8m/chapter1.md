---
title: 'Capítulo 1: Introducción a Azure RTOS ThreadX para ARMv8-M'
description: Este capítulo es el punto de partida de lectura sobre el anexo de Azure RTOS ThreadX para ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f0d87ec562c7fcfa6af5d2240655ef526f6e0611d509fe60c745436371413d7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798255"
---
# <a name="chapter-1--overview"></a>Capítulo 1: Información general

La arquitectura ARMv8-M incorpora nuevas características de seguridad, entre las que se incluye TrustZone, que permite etiquetar la memoria como segura o no segura. Siguiendo las directrices de ARM, ThreadX (y la aplicación de usuario) están diseñadas para ejecutarse en modo no seguro. ThreadX (y la aplicación de usuario) también se pueden ejecutar en modo seguro. Para interactuar con el software de modo seguro se necesitan algunas API de ThreadX nuevas. En este documento se describen estos servicios de ThreadX que son específicos de la arquitectura ARMv8-M, entre los que se incluyen Cortex-M23, Cortex-M33, Cortex-M35P y Cortex-M55.
