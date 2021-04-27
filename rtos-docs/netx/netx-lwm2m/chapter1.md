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
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a>Capítulo 1: Introducción a LWM2M de Azure RTOS NetX

El protocolo LWM2M de Azure RTOS NetX implementa la parte de cliente del estándar de protocolo ligero de máquina a máquina.

## <a name="netx-lwm2m-requirements"></a>Requisitos de LWM2M de NetX

Para que funcione correctamente, la biblioteca en tiempo de ejecución de LWM2M de NetX requiere que ya se haya creado una instancia de IP de NetX. El paquete de LWM2M de NetX no tiene ningún requisito adicional.

## <a name="netx-lwm2m-rfcs"></a>RFC de LWM2M de NetX

LWM2M de NetX es compatible con OMA-TS-LightweightM2M-V1_0-20170208-A y las siguientes RFC relacionadas con el protocolo de aplicación restringida (CoAP):

- **RFC 7252**: el protocolo de aplicación restringida (CoAP)

- **RFC 7641**: observación de recursos en el protocolo de aplicación restringida (CoAP)

- **RFC 6690**: formato de vínculo de entornos RESTful restringidos (CoRE)