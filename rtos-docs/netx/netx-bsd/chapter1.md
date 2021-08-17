---
title: 'Capítulo 1: Introducción a Azure RTOS NetX BSD'
description: El contenedor de cumplimiento de la API de sockets de Azure RTOS NetX BSD es compatible con algunas de las llamadas API de sockets de BSD básicas, con algunas limitaciones, y usan primitivas de NetX debajo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b58283a38a25ffdd438d7853999f3b6e390f280a947aa45101d8df86447bf3dd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796728"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a>Capítulo 1: Introducción a Azure RTOS NetX BSD

El contenedor de cumplimiento de la API de sockets de NetX BSD es compatible con algunas de las llamadas API de sockets de BSD básicas, con algunas limitaciones, y usan primitivas de NetX debajo. Esta capa de API de sockets de BSD debe funcionar igual de rápido o ligeramente más rápido que las implementaciones de BSD típicas, ya que este contenedor emplea primitivas de NetX internas y omite la comprobación básica de errores de NetX.

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a>Origen del contenedor de cumplimiento de la API de sockets de BSD

El código fuente del contenedor de está diseñado pensando en la sencillez y solo consta de dos archivos, *nx_bsd.c* y *nx_bsd.c*. El archivo *nx_bsd.h* define todas las constantes del contenedor de la API de sockets de BSD y los prototipos de subrutinas necesarios, mientras que *nx_bsd.c* contiene el código fuente de compatibilidad de la API de sockets de BSD real. Estos archivos de origen del contenedor de BSD son comunes a todos los paquetes de soporte de NetX.

El paquete consta de:

- **nxd_bsd.c**: código fuente del contenedor
- **nxd_bsd.h**: archivo de encabezado principal

Programas de demostración de ejemplo:

- **bsd_demo_tcp.c**: *demo con un solo cliente y servidor TCP*
- **bsd_demo_udp. c**: *demo con dos clientes UDP y un servidor UDP*
