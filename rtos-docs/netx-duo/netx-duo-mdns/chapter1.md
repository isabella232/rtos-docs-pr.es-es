---
title: 'Capítulo 1: Introducción a mDNS y DNS-SD de Azure RTOS NetX Duo'
description: MDN y DNS-SD de Azure RTOS NetX Duo aumentan el servicio DNS tradicional.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7cde8e81809dcc74ee5d0b09d8e7a8d2ae96850cd84250a5bf003fdd5763925a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796453"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a>Capítulo 1: Introducción a mDNS y DNS-SD de Azure RTOS NetX Duo

mDNS y DNS-SD son protocolos diseñados para ampliar el servicio DNS tradicional. mDNS proporciona la búsqueda del servicio y el nombre de host a los nodos de la red local. Cada nodo usa el canal de multidifusión IPv4 o IPv6 para anunciar los servicios que ofrece a sus vecinos, responde a las consultas de sus vecinos y envía consultas sobre el comportamiento de sus aplicaciones. Por naturaleza, mDNS funciona en un entorno distribuido, por lo que elimina el concepto de centralización.

DNS-SD se basa en mDNS. DNS-SD permite que los nodos anuncien los servicios que proporcionan a la red local o detecten los servicios que ofrecen otros nodos en la red local. En todo el documento, el término *mDNS* hace referencia a los servicios que cubren las especificaciones mDNS y DNS-SD.

## <a name="mdns-standard"></a>Estándar mDNS

La implementación de mDNS y DNS-SD de NetX Duo cumple con los protocolos RFC siguientes:

- RFC 6762: especificación de mDNS
- RFC 6763: especificación de DNS-SD