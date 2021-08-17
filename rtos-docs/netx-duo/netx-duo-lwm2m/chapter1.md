---
title: 'Capítulo 1: Introducción al cliente LWM2M de NetX Duo para Azure RTOS'
description: En este capítulo se incluye una introducción al cliente de protocolo ligero de máquina a máquina de NetX Duo para Azure RTOS.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a2722daac76632e492d0f9345103c45da9ba1b321e91c9c04e04c76463984c3a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783482"
---
# <a name="chapter-1--introduction-to-lwm2m-client"></a>Capítulo 1: Introducción al cliente LWM2M

El protocolo de cliente LWM2M de NetX Duo para Azure RTOS implementa la parte de cliente del estándar del protocolo ligero de máquina a máquina. (LWM2M 1.0-20170208A)

## <a name="netx-lwm2m-client-requirements"></a>Requisitos del cliente LWM2M de NetX

Para que funcione correctamente, la biblioteca en tiempo de ejecución de LWM2M de NetX requiere que ya se haya creado una instancia de IP de NetX. El paquete de cliente LWM2M de NetX no tiene ningún requisito adicional.

## <a name="netx-lwm2m-client-rfcs"></a>Documentos RFC del cliente LWM2M de NetX

El cliente LWM2M es compatible con OMA-TS-LightweightM2M-V1\_0-20170208-A y los siguientes documentos RFC relativos al protocolo de aplicación restringida (CoAP).

* RFC 7252: El protocolo de aplicación restringida (CoAP)

* RFC 7641: Observación de recursos en el protocolo de aplicación restringida (CoAP)

* RFC 6690: Formato de vínculo de entornos RESTful restringidos (CoRE)

Para más información, consulte [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).