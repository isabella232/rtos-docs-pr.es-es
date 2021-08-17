---
title: 'Apéndice A: códigos de error irrecuperables de SNTP de Azure RTOS NetX Duo'
description: Los siguientes códigos de error provocarán que el cliente SNTP de Azure RTOS NetX Duo anule las actualizaciones de tiempo con el servidor actual.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e0152c1342b3edffd42f7442c51e7c5d62b199a5b38085dac06b4c0dbee9e9a8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790112"
---
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a>Apéndice A: Códigos de error irrecuperables de SNTP de Azure RTOS NetX Duo

Los siguientes códigos de error provocarán que el cliente SNTP de Azure RTOS NetX Duo anule las actualizaciones de tiempo con el servidor actual. La aplicación será la que decidirá si el servidor debe quitarse de la lista que tiene disponibles el cliente SNTP o simplemente se debe cambiar al siguiente servidor disponible en la lista. La definición de cada estado de error se establece en *nxd_sntp_client.h. *

Cuando el cliente SNTP devuelve un error de la lista siguiente a la aplicación, es probable que el servidor deba reemplazarse por otro. Tenga en cuenta que el estado de error NX_SNTP_KOD_REMOVE_SERVER se deja para que lo establezca el controlador que desencadena errores de tipo KOD (beso de la muerte) del cliente SNTP (función de devolución de llamada):

- NX_SNTP_KOD_REMOVE_SERVER 0xD0C  
- NX_SNTP_SERVER_AUTH_FAIL 0xD0D  
- NX_SNTP_INVALID_NTP_VERSION 0xD11  
- NX_SNTP_INVALID_SERVER_MODE 0xD12  
- NX_SNTP_INVALID_SERVER_STRATUM 0xD15  

Cuando el cliente SNTP devuelve un error de la lista siguiente a la aplicación, es posible que no pueda proporcionar actualizaciones de hora válidas solo temporalmente y que no sea necesario eliminarlo:

- HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09  
- NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B  
- NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17  
- NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16  
- NX_SNTP_INVALID_RTT_TIME 0xD21  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24