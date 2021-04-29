---
title: 'Capítulo 3: Opciones de configuración del servidor DHCPv6 de Azure RTOS NetX Duo'
description: Hay varias opciones de configuración para compilar el servidor DHCPv6 de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5396b1c04581b5f79d337462368c4718ba9bb16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814778"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a>Capítulo 3: Opciones de configuración del servidor DHCPv6 de Azure RTOS NetX Duo

Hay varias opciones de configuración para compilar el servidor DHCPv6 de Azure RTOS NetX Duo. En la lista siguiente se describe cada una de forma detallada:  
  
  
- **NX_DHCPV6_THREAD_PRIORITY**: prioridad del subproceso del cliente. De forma predeterminada, este valor especifica que el subproceso del cliente se ejecuta con la prioridad 2.

- **NX_DHCPV6_MUTEX_WAIT**: opción de tiempo de espera para obtener un bloqueo exclusivo en una exclusión mutua del cliente DHCPv6. El valor predeterminado es TX_WAIT_FOREVER.

- **NX_DHCPV6_TICKS_PER_SECOND**: relación entre tics y segundos. Esto depende del procesador. El valor predeterminado es 100.

- **NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**: intervalo de tiempo en segundos en el que el temporizador de duración de IP actualiza la cantidad de tiempo que se ha asignado la dirección IP actual al cliente. De manera predeterminada, este valor es 1.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL**: intervalo de tiempo en segundos en el que el temporizador de la sesión actualiza el tiempo durante el que el cliente ha estado en la sesión de comunicación con el servidor. De manera predeterminada, este valor es 1.

- **NX_DHCPV6_MAX_IA_ADDRESS**: número máximo de direcciones IA que se pueden agregar al registro del cliente. El valor predeterminado es 1. 

- **NX_DHCPV6_NUM_DNS_SERVERS**: número de servidores DNS que se van a almacenar en el registro del cliente. El valor predeterminado es 2.

- **NX_DHCPV6_NUM_TIME_SERVERS**: número de servidores de tiempo que se almacenan en el registro del cliente. El valor predeterminado es 1.

- **NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**: tamaño del búfer en el registro de cliente para contener el nombre de dominio de red del cliente. El valor predeterminado es 30.

- **NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**: tamaño del búfer en el registro de cliente para almacenar la zona horaria del cliente. El valor predeterminado es 10.

- **NX_DHCPV6_MAX_MESSAGE_SIZE**: tamaño del búfer en el registro del cliente para contener el mensaje de estado de la opción en una respuesta del servidor. El valor predeterminado es 100 bytes.

- **NX_DHCPV6_PACKET_TIME_OUT**: tiempo de espera en segundos para la asignación de un paquete desde el grupo de paquetes del cliente. El valor predeterminado es 3 segundos.

- **NX_DHCPV6_TYPE_OF_SERVICE**: define el tipo de servicio para la transmisión de paquetes UDP desde el socket del cliente DHCPv6. El valor predeterminado es **NX_IP_NORMAL**.

- **NX_DHCPV6_TIME_TO_LIVE**: número de veces que un enrutador de red reenvía un paquete de cliente antes de que se descarte el paquete. El valor predeterminado es 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Especifica el número de paquetes que se van a mantener en la cola de recepción del socket UDP del cliente antes de que NetX Duo descarte los paquetes. El valor predeterminado es 5.

## <a name="dhcpv6-message-transmission"></a>Transmisión de mensajes DHCPv6

Hay un conjunto de opciones del cliente DHCPv6 para establecer parámetros en la transmisión de mensajes DHCPv6. Dichos componentes son: 

  - tiempo de espera inicial

  - retraso máximo en la primera transmisión

  - tiempo máximo de retransmisión 

  - número máximo de retransmisiones 

  - duración máxima de espera para la respuesta del servidor

Estos parámetros se aplican a cada uno de los mensajes de cliente DHCPv6:

- SOLICIT

- REQUEST

- RENEW

- REBIND

- RELEASE

- DECLINE

- CONFIRMAR

- INFORM

A continuación se muestra una lista completa de estas opciones configurables y su valor predeterminado. 

values:

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

Para no limitar el tiempo de espera de la retransmisión, establezca el número de retransmisión de mensajes en 0. Para no limitar el número de veces que se retransmite un mensaje del cliente DHCPv6 (reintentos), establezca el recuento de retransmisión de mensajes en 0.

> [!NOTE]
> Independientemente de la duración del tiempo de espera o el número de reintentos, cuando expire la duración válida de una dirección IPv6, se quitará de la tabla de direcciones IP y el cliente ya no podrá utilizarla. El cliente DHCPv6 de NetX Duo iniciará automáticamente el envío de mensajes SOLICIT que solicitan una nueva dirección IPv6.