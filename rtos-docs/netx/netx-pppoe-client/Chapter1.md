---
title: 'Capítulo 1: Introducción al cliente PPPoE de Azure RTOS NetX'
description: Este capítulo contiene los detalles del módulo PPPoE de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bbf1e064bb38754bd67b279a0fd60d46d3d6d557
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815149"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-client"></a>Capítulo 1: Introducción al cliente PPPoE de Azure RTOS NetX

PPP a través de Ethernet (PPPoE) permite que los hosts se conecten al servidor PPP a través de Ethernet en lugar de la comunicación de línea de serie tradicional basada en caracteres.  Los detalles técnicos de PPPoE se describen en RFC 2516: un método para transmitir PPP a través de Ethernet (PPPoE). Este documento se centra en los detalles del módulo PPPoE de Azure RTOS NetX.

Para proporcionar una conexión punto a punto a través de Ethernet, cada sesión PPP debe conocer la dirección Ethernet del elemento remoto del mismo nivel, así como establecer un identificador de sesión único.

Según RFC 2516, PPPoE consta de dos fases: la fase de detección y la fase de sesión de PPPoE. Cuando un host (cliente) desea iniciar una sesión de PPP, primero debe realizar la detección para buscar el servidor PPPoE. Este paso también permite que el servidor y el cliente identifiquen las direcciones MAC de Ethernet y SESSION_ID, que se usarán para el resto de la sesión de PPP.

Un marco Ethernet es lo siguiente:

![Marco Ethernet](media/ethernet-frame.png)

La carga de Ethernet para PPPoE es la siguiente:

![Carga de Ethernet](media/ethernet-payload.png)

## <a name="pppoe-discovery-stage"></a>Fase de detección de PPPoE

La fase de detección de PPPoE permite a los clientes seleccionar un servidor de todos los servidores disponibles en la red, de forma eficaz, para crear una sesión antes de que se intercambien los marcos PPP.  Al final de la fase de detección, tanto el cliente como el servidor deben estar de acuerdo en un identificador de sesión único y ambos lados deben conocer la dirección MAC del mismo nivel.

| Mensaje de detección | Código | Dirección |
| ----------------- | ---- | --------- |
| Inicio de detección activa de PPPoE (PADI) | 0x09 | De cliente a difusión |
| Oferta de detección activa de PPPoE (PADO) | 0x07 | De servidor a cliente |
| Solicitud de detección activa de PPPoE (PADR) | 0x19 | De cliente a servidor |
| Sesión de detección activa de PPPOE: confirmación (PADS) | 0x65 | De servidor a cliente |
| Finalización de detección activa de PPPoE (PADT) | 0xa7 | Se puede iniciar desde un servidor o un cliente |

Todos los marcos de Ethernet de detección tienen el campo ETHER_TYPE establecido en el valor 0x8863.

## <a name="pppoe-session-message"></a>Mensaje de sesión de PPPoE

Una vez que el cliente y el servidor crean una sesión, las tramas PPP se pueden transferir como mensajes de sesión PPPoE.  Durante una sesión, el SESSION_ID no debe cambiar y debe ser el valor del servidor asignado durante la fase de detección.

Todos los marcos de Ethernet de sesión de PPPoE tienen el campo ETHER_TYPE establecido en el valor 0x8864.
