---
title: 'Apéndice B: códigos de estado de servidor DHCPv6 de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los códigos de estado de servidor DHCPv6 de NetX Duo
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c79a0c0bc9acfcfca69c7333d30cd7cab35ba5f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814758"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a>Apéndice B: códigos de estado de servidor DHCPv6 de Azure RTOS NetX Duo

| Nombre              | Código            | Descripción |
| ------------------- | ------------------- | --------------- |
| Correcto | 0 | Correcto |
| Error no especificado | 1 | Error, motivo sin especificar; este código de estado se establece mediante el servidor para indicar un error general al conceder la solicitud de cliente que no coincide con los demás códigos. |
| NoAddress Available | 2 | El servidor no tiene direcciones disponibles para asignar al cliente. |
| NoBinding | 3 | La dirección de IA del cliente (enlace) no está disponible; por ejemplo, la dirección IP solicitada no está disponible para el servidor que se va a conceder o asignar a otro cliente. |
| NotOnLink | 4 | El prefijo de la dirección indica que la dirección IP no es una dirección en un vínculo. |
| UseMulticast | 5 | Enviado por un servidor en respuesta a la recepción de un mensaje del cliente mediante la dirección de unidifusión del servidor en lugar de la dirección de multidifusión *All_DHCP_Relay_Agents_and_Servers*. |