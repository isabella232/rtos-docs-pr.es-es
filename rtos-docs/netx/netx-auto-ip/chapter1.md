---
title: 'Capítulo 1: Introducción a AutoIP de Azure RTOS NetX'
description: El protocolo AutoIP de Azure RTOS NetX es un protocolo diseñado para configurar dinámicamente las direcciones IPv4 en una red local.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c26b4112814bb586e056246d68c2597d56df6085
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815286"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-autoip"></a>Capítulo 1: Introducción a AutoIP de Azure RTOS NetX
  
El protocolo AutoIP de Azure RTOS NetX es un protocolo diseñado para configurar dinámicamente las direcciones IPv4 en una red local. AutoIP es un protocolo simple que emplea las funciones ARP para realizar su función de asignación automática de direcciones IP. AutoIP asigna direcciones en el intervalo de 169.254.1.0 a 169.254.254.255.

## <a name="autoip-requirements"></a>Requisitos de AutoIP

Para que funcione correctamente, el paquete AutoIP de NetX requiere que ya se haya creado una instancia de IP NetX. Además, ARP debe estar habilitado en la misma instancia de IP. El paquete AutoIP de NetX no tiene ningún requisito adicional.

## <a name="autoip-constraints"></a>Restricciones de AutoIP 

El protocolo AutoIP de NetX implementa los requisitos del estándar RFC3927. Sin embargo, se aplican las restricciones siguientes:

1. Si se usa DHCP de NetX, el subproceso DHCP debe crearse con una prioridad más alta que el subproceso de instancia de IP y el subproceso de AutoIP de NetX.
1. AutoIP de NetX no proporciona un mecanismo para que las direcciones IP antiguas sigan utilizándose.
1. Cuando la dirección IP cambia, la aplicación es responsable de anular las conexiones TCP existentes y volver a establecerlas en la nueva dirección IP.

## <a name="autoip-protocol-implementation"></a>Implementación del protocolo AutoIP

En primer lugar, el protocolo AutoIP de NetX selecciona una dirección aleatoria dentro del intervalo de direcciones IPv4 de AutoIP de 169.254.1.0 a 169.254.254.255. Como alternativa, la aplicación puede forzar una dirección IP de inicio proporcionándola en la función ***nx_auto_ip_start***. Esto resulta útil en situaciones en las que una dirección AutoIP se ha usado correctamente en una ejecución anterior.

Una vez que se selecciona una dirección AutoIP, AutoIP de NetX envía una serie de sondeos ARP para la dirección seleccionada. Un sondeo ARP consta de un mensaje de solicitud ARP con la dirección del remitente establecida en 0.0.0.0 y la dirección de destino establecida en la dirección AutoIP deseada. Se envía una serie de estos sondeos ARP (el número real viene determinado por la definición NX_AUTO_IP_PROBE_NUM). Si otro nodo de red responde a este sondeo o envía un sondeo idéntico para la misma dirección, se selecciona aleatoriamente una nueva dirección AutoIP en el intervalo de direcciones IPv4 de AutoIP y se repite el procesamiento del sondeo.

Si se envían los sondeos NX_AUTO_IP_PROBE_NUM sin ninguna respuesta, AutoIP de NetX emite una serie de anuncios ARP para la dirección seleccionada. Un anuncio ARP consta de un mensaje de solicitud ARP con el remitente y la dirección de destino del mensaje ARP establecidos en la dirección AutoIP seleccionada. Se envía una serie de mensajes de anuncio ARP, correspondientes a la definición NX_AUTO_IP_ANNOUNCE_NUM. Si otro nodo de red responde a un mensaje de anuncio o envía un anuncio idéntico para la misma dirección, se selecciona aleatoriamente una nueva dirección AutoIP en el intervalo de direcciones IPv4 de AutoIP y el procesamiento del sondeo empieza de nuevo.

Cuando el sondeo y el anuncio se completan sin conflictos detectados, la dirección de AutoIP seleccionada se considera válida y la instancia de IP asociada se configura con esta dirección.

## <a name="autoip-address-change"></a>Cambio de dirección en AutoIP

Como se ha mencionado anteriormente, AutoIP de NetX cambia la dirección de la instancia de IP después del sondeo y el procesamiento del anuncio correctos. La supervisión en este caso no tiene mucha importancia. Sin embargo, es posible que la dirección de AutoIP cambie en el futuro. Entre las posibles causas se incluyen conflictos de direcciones de AutoIP en el futuro, así como la resolución de direcciones DHCP. Con el fin de procesar estas posibles situaciones correctamente, la aplicación debe usar la siguiente API de NetX para alertar de cualquier cambio de dirección IP:

```c
nx_ip_address_change_notify(NX_IP *ip_ptr,
                            VOID (*ip_address_change_notify)(NX_IP *,VOID*),
                            VOID *additional_info);
```

El procesamiento de la función *ip_address_change_notify* proporcionada debe reiniciar el procesador de AutoIP de NetX o deshabilitarlo si DHCP ha resuelto posteriormente la dirección IP. Consulte en la sección *Sistema de ejemplo pequeño* el procesamiento de ejemplo.

## <a name="autoip-rfcs"></a>RFC de AutoIP

AutoIP de NetX es compatible con la RFC3927 y RFC relacionadas.