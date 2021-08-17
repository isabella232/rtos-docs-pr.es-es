---
title: 'Capítulo 1: Introducción a LWM2M de Azure RTOS NetX'
description: El protocolo LWM2M de Azure RTOS NetX implementa la parte de cliente del estándar de protocolo ligero de máquina a máquina.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fe9c90ec10b241c72c71882b28b5fe0e3e60e3913435ec27f797eade4ca4eca5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784927"
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