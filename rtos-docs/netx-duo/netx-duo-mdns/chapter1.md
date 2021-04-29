---
title: 'Capítulo 1: Introducción a mDNS y DNS-SD de Azure RTOS NetX Duo'
description: MDN y DNS-SD de Azure RTOS NetX Duo aumentan el servicio DNS tradicional.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b46539ee4d502fa4c90fb3392e25cd3bee40dc5b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814670"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a>Capítulo 1: Introducción a mDNS y DNS-SD de Azure RTOS NetX Duo

mDNS y DNS-SD son protocolos diseñados para ampliar el servicio DNS tradicional. mDNS proporciona la búsqueda del servicio y el nombre de host a los nodos de la red local. Cada nodo usa el canal de multidifusión IPv4 o IPv6 para anunciar los servicios que ofrece a sus vecinos, responde a las consultas de sus vecinos y envía consultas sobre el comportamiento de sus aplicaciones. Por naturaleza, mDNS funciona en un entorno distribuido, por lo que elimina el concepto de centralización.

DNS-SD se basa en mDNS. DNS-SD permite que los nodos anuncien los servicios que proporcionan a la red local o detecten los servicios que ofrecen otros nodos en la red local. En todo el documento, el término *mDNS* hace referencia a los servicios que cubren las especificaciones mDNS y DNS-SD.

## <a name="mdns-standard"></a>Estándar mDNS

La implementación de mDNS y DNS-SD de NetX Duo cumple con los protocolos RFC siguientes:

- RFC 6762: especificación de mDNS
- RFC 6763: especificación de DNS-SD