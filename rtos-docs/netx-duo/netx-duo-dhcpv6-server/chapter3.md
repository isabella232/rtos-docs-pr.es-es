---
title: 'Capítulo 3: Opciones de configuración del servidor DHCPv6 de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de las opciones de configuración del servidor DHCPv6 de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 30f6e1c657eb62ebec48d6bb8caafac320727146
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815389"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-server-configuration-options"></a>Capítulo 3: Opciones de configuración del servidor DHCPv6 de Azure RTOS NetX Duo

Hay varias opciones de configuración para compilar una aplicación de servidor DHCPv6 de NetX Duo. En la lista siguiente se describe cada una de forma detallada:
  
- **NX_DISABLE_ERROR_CHECKING** Esta opción quita la comprobación de errores de DHCPv6. Se suele habilitar cuando se depura la aplicación.  
  
- **NX_DHCPV6_SERVER_THREAD_STACK_SIZE** Define el tamaño de la pila de subprocesos de DHCPv6. De manera predeterminada, el tamaño es de 4096 bytes, que es más que suficiente para la mayoría de las aplicaciones de NetX Duo.

- **NX_DHCPV6_SERVER_THREAD_PRIORITY** Define la prioridad de subprocesos del servidor DHCPv6. Debe ser inferior a la prioridad de tareas de subprocesos de IP del servidor DHCPv6. El valor predeterminado es 2.

- **NX_DHCPV6_IP_LEASE_TIMER_INTERVAL** Intervalo del temporizador en segundos cuando el programador de ThreadX llama a la función de entrada del temporizador de concesión. La función de entrada define una marca para que el servidor DHCPv6 incremente el tiempo acumulado de los clientes concedido por el intervalo del temporizador. De manera predeterminada, este valor es 60.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL** Intervalo del temporizador en segundos cuando el programador de ThreadX llama a la función de entrada del temporizador de sesión. La función de entrada define una marca para que el servidor DHCPv6 incremente el tiempo de sesión de los clientes activos acumulado por el intervalo del temporizador. De manera predeterminada, este valor es 3.

Las siguientes definiciones se aplican al tipo de mensaje de la opción de estado y al mensaje configurable por el usuario. La opción de estado indica el resultado de una solicitud de cliente:

- **NX_DHCPV6_STATUS_MESSAGE_SUCCESS** *"IA OPTION GRANTED"*

- **NX_DHCPV6_STATUS_NO_ADDRS_AVAILABLE** *"IA OPTION NOT GRANTED-NO ADDRESSES AVAILABLE”*

- **NX_DHCPV6_STATUS_MESSAGE_NO_BINDING** *"IA OPTION NOT GRANTED-INVALID CLIENT REQUEST"*

- **NX_DHCPV6_STATUS_MESSAGE_NOT_ON_LINK** *"IA OPTION NOT GRANTED-CLIENT NOT ON LINK"*

- **NX_DHCPV6_STATUS_MESSAGE_USE_MULTICAST** *"IA OPTION NOT GRANTED-CLIENT MUST USE MULTICAST"*

- **NX_DHCPV6_STATUS_MESSAGE_NO_ADDRS_AVAILABLE** *IA OPTION NOT GRANTED-NO ADDRESSES AVAILABLE*

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID** Crea un DUID de servidor con un id. asignado por el proveedor. Tenga en cuenta que el tipo de DUID se debe definir como NX_DHCPV6_DUID_TYPE_VENDOR_ASSIGNED.

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_LENGTH** Establece el límite superior del id. asignado por el proveedor. El valor predeterminado es 48.

- **NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID** Establece el tipo de empresa del DUID en tipo de proveedor privado.

- **NX_DHCPV6_PACKET_WAIT_OPTION** Define la opción de espera de la llamada *nx_udp_socket_receive* del servidor. Es indiferente, ya que el socket tiene una devolución de llamada de notificación de recepción de NetX Duo, por lo que el paquete ya está en cola cuando el servidor DHCPv6 llama a la función de recepción. El valor predeterminado es 1 segundo (1 * NX_IP_PERIODIC_RATE).

- **NX_DHCPV6_SERVER_DUID_TYPE** Define el tipo de DUID de servidor que el servidor incluye en todos los mensajes a los clientes. El valor predeterminado es nivel de vínculo más tiempo (NX_DHCPV6_SERVER_DUID_TYPE_LINK_TIME).

- **NX_DHCPV6_SERVER_HW_TYPE** Define el tipo de hardware en las opciones de nivel de vínculo de DUID y nivel de vínculo más tiempo. El valor predeterminado es NX_DHCPV6_SERVER_HARDWARE_TYPE_ETHERNET.

- **NX_DHCPV6_PREFERENCE_VALUE** Define el valor de la opción de preferencia entre 0 y 255, donde cuanto mayor sea el valor, mayor será la preferencia, en la opción DHCPv6 del mismo nombre. Esto indica al cliente qué preferencia dar a la oferta de este servidor cuando hay varios servidores DHCPv6 disponibles para asignar direcciones IP. Un valor de 255 indica al cliente que elija este servidor. Un valor de cero indica que el cliente puede elegir libremente. El valor predeterminado es cero.

- **NX_DHCPV6_MAX_OPTION_REQUEST_OPTIONS** Define el número máximo de solicitudes de opción de una solicitud de cliente que se pueden guardar en un registro de cliente. El valor predeterminado es 6.

- **NX_DHCPV6_DEFAULT_T1_TIME** Tiempo en segundos asignado por el servidor a una concesión de dirección de cliente para cuando el cliente deba comenzar a renovar su dirección IP. El valor predeterminado es 2000 segundos.

- **NX_DHCPV6_DEFAULT_T2_TIME** Tiempo en segundos asignado por el servidor a una concesión de dirección de cliente para cuando el cliente deba comenzar a reenlazar su dirección IP debido al error de su intento de renovación. El valor predeterminado es 3000 segundos.

- **NX_DHCPV6_DEFAULT_PREFERRED_TIME** Define el tiempo en segundos asignado por el servidor para cuando una concesión de dirección IP de cliente asignada queda en desuso. El valor predeterminado es 2 NX_DHCPV6_DEFAULT_T1_TIME.

- **NX_DHCPV6_DEFAULT_VALID_TIME** Define la expiración de tiempo en segundos asignada por el servidor a una concesión de dirección IP de cliente asignada. Una vez transcurrido este tiempo, la dirección IP de cliente no es válida. El valor predeterminado es 2 NX_DHCPV6_DEFAULT_PREFERRED_TIME.

- **NX_DHCPV6_STATUS_MESSAGE_MAX** Define el tamaño máximo del mensaje de servidor en el campo de mensaje de la opción de estado. El valor predeterminado es 100 bytes.

- **NX_DHCPV6_MAX_LEASES** Define el tamaño de la tabla de concesiones IP del servidor (por ejemplo, el número máximo de direcciones IPv6 disponibles para la concesión que se pueden almacenar). De manera predeterminada, este valor es 100.

- **NX_DHCPV6_MAX_CLIENTS** Define el tamaño de la tabla de registros de cliente del servidor (por ejemplo, el número máximo de clientes que se pueden almacenar). Este valor debe ser menor o igual que el valor NX_DHCPV6_MAX_LEASES. De manera predeterminada, este valor es 120.

- **NX_DHCPV6_PACKET_TIME_OUT** Define la opción de espera en tics de temporizador para que el servidor DHCPv6 espere asignaciones de paquetes. El valor predeterminado es 3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND.

- **NX_DHCPV6_PACKET_RECEIVE_WAIT** Define la opción de espera en llamadas de asignación de paquetes en el grupo de paquetes del servidor. El valor predeterminado es (3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND) o 3 segundos.

- **NX_DHCPV6_PACKET_SIZE** Define la carga de paquetes de los paquetes del grupo de paquetes del servidor. El valor predeterminado es 500 bytes.

- **NX_DHCPV6_PACKET_POOL_SIZE** Define el tamaño del grupo de paquetes del servidor para los paquetes que el servidor va a asignar para enviar mensajes de DHCPv6. El valor predeterminado es (10 * NX_DHCPV6_PACKET_SIZE).

- **NX_DHCPV6_TYPE_OF_SERVICE** Define el tipo de servicio para la transmisión de paquetes UDP. De manera predeterminada, este valor es NX_IP_NORMAL.

- **NX_DHCPV6_FRAGMENT_OPTION** Define la opción de fragmentación de sockets del servidor. El valor predeterminado es NX_DON’T_FRAGMENT.

- **NX_DHCPV6_TIME_TO_LIVE** Especifica el número de enrutadores que los paquetes DHCPv6 del servidor pueden "saltar" antes de descartar los paquetes. El valor predeterminado se define en 0 x 80.

- **NX_DHCPV6_QUEUE_DEPTH** Especifica el número de paquetes que se van a mantener en la cola de recepción del socket UDP del servidor antes de que NetX Duo descarte los paquetes.