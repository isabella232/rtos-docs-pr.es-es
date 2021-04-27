---
title: 'Capítulo 1: Introducción a BSD de Azure RTOS NetX Duo'
description: El contenedor de cumplimiento de la API de socket BSD es compatible con algunas de las llamadas API de socket BSD básicas, con algunas limitaciones, y usan primitivas de Azure RTOS NetX Duo debajo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e89018dffd2f9f9065efab2ecabdf4364c4f89a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814826"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a>Capítulo 1: Introducción a BSD de Azure RTOS NetX Duo

El contenedor de cumplimiento de la API de socket BSD es compatible con algunas de las llamadas API de socket BSD básicas, con algunas limitaciones, y usan primitivas de Azure RTOS NetX Duo debajo.

## <a name="bsd-socket-api-compliancy-wrapper-source"></a>Origen del contenedor de cumplimiento de la API de socket BSD

El código fuente del contenedor está diseñado pensando en la sencillez y se compone de dos archivos, *nxd_bsd.h* y *nxd_bsd.c*. El archivo *nxd_bsd.h* define todas las constantes y los prototipos de subrutinas del contenedor de la API de socket BSD necesarios, mientras que *nxd_bsd.c* contiene el código fuente de compatibilidad de la API de socket BSD real. Estos archivos de código fuente del contenedor son comunes a todos los paquetes de soporte de NetX Duo.

El paquete consta de:

- **nxd_bsd.c**: código fuente del contenedor
- **nxd_bsd.h**: archivo de encabezado principal

Programas de demostración de ejemplo:

- **bsd_demo_udp.c**: *demo con dos nodos UDP del mismo nivel (solo IPv4)*
- **bsd_demo_tcp.c**: *demo con un solo cliente y servidor TCP*
- **bsd_demo_raw.c**: *demo con dos nodos del mismo nivel sin procesar*