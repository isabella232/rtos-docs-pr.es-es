---
title: 'Capítulo 3: Opciones de configuración de NAT'
description: En la lista siguiente se incluyen todas las opciones y su función descrita en detalle
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9c10d6f0d2f36d2794ab1229081799f0032cada8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814626"
---
# <a name="chapter-3---nat-configuration-options"></a>Capítulo 3: Opciones de configuración de NAT

Las opciones configurables para la API de NAT de NetX Duo se pueden encontrar en *nx_nat.h* con la excepción de la primera, **NX_DISABLE_ERROR_CHECKING**, que se encuentra en *nx_nat.c*. En la lista siguiente se incluyen todas las opciones y su función descrita en detalle:

- **NX_NAT_DISABLE_ERROR_CHECKING** Esta opción, si se define, quita la comprobación de errores básica de NAT. Normalmente se utiliza después de depurar la aplicación. El estado predeterminado de la NAT de NetX Duo es definido (habilitado).
- **NX_NAT_ENABLE_REPLACEMENT** Esta opción, si se define, habilita la sustitución automática cuando la memoria caché de NAT está llena.
  > [!NOTE]
  > Reemplaza solo la sesión que no es de TCP más antigua.
- **NX_NAT_MIN_ENTRY_COUNT** Esta opción establece el número mínimo de entradas de traducción. El número predeterminado es 3.
- **NX_NAT_TCP_SESSION_TIMEOUT** Esta opción establece el tiempo de espera para la entrada de traducción para las sesiones de TCP. El tiempo de espera predeterminado es de 24 horas.
- **NX_NAT_NON_TCP_SESSION_TIMEOUT** Esta opción establece el tiempo de espera para la entrada de traducción para sesiones que no son de TCP. El tiempo de espera predeterminado es de 240 segundos.
- **NX_NAT_START_TCP_PORT** Esta opción establece el valor inicial para buscar un puerto TCP no utilizado para asignar un paquete TCP saliente. El valor predeterminado es 20 000.
- **NX_NAT_END_TCP_PORT** Esta opción establece el límite superior del puerto TCP para asignar un paquete TCP saliente. El valor predeterminado es 30 000.
- **NX_NAT_START_UDP_PORT** Esta opción establece el valor inicial para buscar un puerto UDP sin usar para asignar un paquete UDP saliente. El valor predeterminado es 20 000.
- **NX_NAT_END_UDP_PORT** Esta opción establece el límite superior del puerto UDP para asignar un paquete UDP saliente. El valor predeterminado es 30 000.
- **NX_NAT_START_ICMP_QUERY_ID** Esta opción establece el valor inicial para buscar un identificador de consulta no utilizado para asignar un paquete de consulta de ICMP saliente. El valor predeterminado es 20 000.
- **NX_NAT_END_ICMP_QUERY_ID** Esta opción establece el límite superior de los identificadores de consulta para asignar un paquete de consulta de ICMP saliente. El valor predeterminado es 30 000.
