---
title: 'Apéndice A: Códigos de opciones DHCPv6 de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del servidor DHCPv6 de NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 58b6e36fab4de02a9fb973894500a48f2656809ec2baa3dfc65fcd80ae33b832
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791844"
---
# <a name="appendix-a--azure-rtos-netx-duo-dhcpv6-option-codes"></a>Apéndice A: Códigos de opciones DHCPv6 de Azure RTOS NetX Duo

| Opción              | Código            | Descripción |
| ------------------- | ------------------- | --------------- |
| Identificador del cliente (DUID) | 1 | Identifica de forma única un host de cliente en la red |
| Identificador del servidor (DUID) | 2 | Identifica de forma única el host de DHCPv6Server en la red |
| Asociación de identidad para direcciones no temporales (IANA) | 3 | Parámetros para una asignación de direcciones IP no temporal |
| Asociación de identidad para direcciones temporales (IATA) | 4 | Parámetros para una asignación de direcciones IP temporales |
| Dirección IA | 5 | La dirección IPv6 real y la duración de las direcciones IPv6 que se van a asignar al cliente |
| Solicitud de opción | 6 | Una lista de solicitudes de información para obtener información de red como el servidor DNS y otros parámetros de configuración de red. |
| Referencia | 7 | Se incluye en el mensaje ADVERTISE del servidor al cliente para influir en la elección de servidores del cliente. El cliente debe elegir un servidor con mayor valor de preferencia sobre otros servidores. 255 es el valor máximo, mientras que cero indica que el cliente puede elegir cualquier servidor que responda a ellos. |
| Tiempo transcurrido | 8 | Contiene la hora (en 0,01 segundos) en que el cliente inicia el intercambio DHCPv6 con el servidor. Lo usan los servidores secundarios para determinar si el servidor principal responde en el tiempo a la solicitud del cliente. |
| Mensaje de retransmisión | 9 | Contiene el mensaje original en el mensaje de retransmisión | 
| Authentication | 11 | Contiene información para autenticar la identidad y el contenido de los mensajes DHCPv6 |
| Unidifusión del servidor | 12 | El servidor envía esta opción para permitir que el cliente sepa que el servidor aceptará mensajes de unidifusión directamente del cliente en lugar de multidifusión. |

No se admiten las opciones de IATA, de mensajes de retransmisión, de autenticación y de unidifusión del servidor en esta versión del servidor DHCPv6 Duo. La opción de protocolo DHCPv6 actual (código 10) se deja sin definir en RFC 3315.