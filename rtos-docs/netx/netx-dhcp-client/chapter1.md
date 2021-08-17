---
title: 'Capítulo 1: Introducción al cliente DHCP de Azure RTOS NetX'
description: En NetX, la dirección IP de la aplicación es uno de los parámetros proporcionados a la llamada de servicio nx_ip_create.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 54853fd3677b8d60b7fbe1445ca67c7e7a4a6e832683f65cbfca86158cb7fbd3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788819"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-client"></a>Capítulo 1: Introducción al cliente DHCP de Azure RTOS NetX

En NetX, la dirección IP de la aplicación es uno de los parámetros proporcionados a la llamada de servicio *nx_ip_create*. Proporcionar la dirección IP no supone ningún problema si la aplicación conoce la dirección IP, ya sea de forma estática o a través de la configuración del usuario. Sin embargo, hay algunos casos en los que la aplicación no sabe ni se preocupa por saber cuál es su dirección IP. En tales situaciones, se debe proporcionar una dirección IP cero a la función *nx_ip_create* y se debe usar el protocolo cliente DHCP de Azure RTOS para obtener dinámicamente una dirección IP.

## <a name="dynamic-ip-address-assignment"></a>Asignación de dirección IP dinámica

El servicio básico usado para obtener una dirección IP dinámica de la red es el protocolo Reverse Address Recognition Protocol (RARP). Este protocolo es similar a ARP, con la excepción de que está diseñado para obtener una dirección IP para sí mismo en lugar de encontrar la dirección MAC para otro nodo de red. El mensaje RARP de bajo nivel se emite en la red local y es responsabilidad de un servidor de la red responder con una respuesta RARP, que contiene una dirección IP asignada dinámicamente.

Aunque RARP proporciona un servicio para asignar direcciones IP de forma dinámica, tiene varias limitaciones. La limitación más evidente es que RARP solo proporciona una asignación dinámica de la dirección IP. En la mayoría de los casos, es necesaria una mayor información para que un dispositivo pueda participar correctamente en una red. Además de una dirección IP, la mayoría de los dispositivos necesitan la máscara de red y la dirección IP de puerta de enlace. También es posible que se necesite la dirección IP de un servidor DNS y otra información de la red. RARP no tiene la capacidad de proporcionar esta información.

## <a name="rarp-alternatives"></a>Alternativas de RARP

Con el fin de superar las limitaciones de RARP, los investigadores han desarrollado un mecanismo para asignar direcciones IP más completo denominado protocolo de arranque (BOOTP). Este protocolo tiene la capacidad de asignar dinámicamente una dirección IP y también proporcionar información adicional sobre la red. Sin embargo, BOOTP tiene el inconveniente de estar diseñado para configuraciones de red estáticas. No permite asignar direcciones rápidas o automatizadas.

Aquí es donde el protocolo de configuración dinámica de host (DHCP) es muy útil. DHCP está diseñado para ampliar la funcionalidad básica de BOOTP con el fin de incluir la asignación de servidor IP totalmente automatizada y la asignación de direcciones IP completamente dinámicas a través de la "concesión" de una dirección IP a un cliente durante un período de tiempo especificado. DHCP también se puede configurar para asignar direcciones IP de forma estática como BOOTP.

## <a name="dhcp-messages"></a>Mensajes DHCP

Aunque DHCP mejora en gran medida la funcionalidad de BOOTP, DHCP usa el mismo formato de mensaje que BOOTP y admite las mismas opciones de proveedor que BOOTP. Para realizar su función, DHCP introduce siete nuevas opciones específicas de DHCP, como se indica a continuación:

- DISCOVER (1) (enviada por el cliente DHCP)

- OFFER (2) (enviada por el servidor DHCP)

- REQUEST (3) (enviada por el cliente DHCP)

- DECLINE (4) (enviada por el cliente DHCP)

- ACK (5) (enviada por el servidor DHCP)

- NACK (6) (enviada por el servidor DHCP)

- RELEASE (7) (enviada por el cliente DHCP)

- INFORM (8) (enviada por el cliente DHCP)

- FORCERENEW (9) (enviado por el cliente DHCP)

## <a name="dhcp-communication"></a>Comunicación DHCP

DHCP emplea el protocolo UDP para enviar solicitudes y respuestas de campo. Antes de tener una dirección IP, los mensajes UDP que llevan la información de DHCP se envían y se reciben mediante la dirección IP de difusión 255.255.255.255.

## <a name="dhcp-client-state-machine"></a>Máquina de estados de cliente DHCP

El cliente DHCP se implementa como una máquina de estados. La máquina de estados se procesa mediante un subproceso DHCP que se crea durante el procesamiento *nx_dhcp_create*. Los estados principales del cliente DHCP son los siguientes:


- **NX_DHCP_STATE_BOOT**: a partir de una dirección IP anterior

- **NX_DHCP_STATE_INIT**: sin ningún valor de dirección IP anterior inicial

- **NX_DHCP_STATE_SELECTING**: a la espera de una respuesta de un servidor DHCP

- **NX_DHCP_STATE_REQUESTING**: servidor DHCP identificado, solicitud de dirección IP enviada

- **NX_DHCP_STATE_BOUND**: concesión de dirección IP DHCP establecida

- **NX_DHCP_STATE_RENEWING**: tiempo de renovación de concesión de dirección IP DHCP transcurrido, renovación solicitada

- **NX_DHCP_STATE_REBINDING**: tiempo de reenlace de concesión de dirección IP DHCP transcurrido, renovación solicitada

- **NX_DHCP_STATE_FORCERENEW**: concesión de dirección IP DHCP establecida, forzar la renovación por servidor (actualmente no se admite) o por la aplicación mediante una llamada a nx_dhcp_force_renew

- **NX_DHCP_STATE_ADDRESS_PROBING**: sondeo de direcciones IP de DHCP, enviar el sondeo ARP para detectar conflictos de direcciones IP.

## <a name="dhcp-client-multiple-interface-support"></a>Compatibilidad con varias interfaces de cliente DHCP

El cliente DHCP se implementó previamente para ejecutarse en una sola interfaz de red. El comportamiento predeterminado era (y todavía es) que el cliente DHCP se ejecutara en la interfaz principal. Mediante una llamada a *nx_dhcp_set_interface_index*, la aplicación podía (y aún puede) ejecutar DHCP en una interfaz de red secundaria en lugar de hacerlo en la interfaz principal.

Ahora admite la ejecución de DHCP en varias interfaces en paralelo. Consulte **Cliente DHCP en varias interfaces simultáneamente** en el capítulo 2 para ver detalles específicos sobre cómo ejecutar el cliente DHCP en más de una interfaz física simultáneamente.

## <a name="dhcp-user-request"></a>Solicitud del usuario DHCP

Una vez que el servidor DHCP concede una dirección IP, el procesamiento del cliente DHCP puede solicitar parámetros adicionales, de uno en uno, mediante el servicio *nx_dhcp_user_option_request*.

## <a name="dhcp-client-socket-queue"></a>Cola de sockets de cliente DHCP 

El cliente DHCP borra automáticamente los paquetes de difusión de los servidores de DHCP destinados a otros clientes DHCP de su cola de recepción de socket mientras espera a que el servidor se responda a sí mismo. En una red ocupada, si no lo hace, podría provocar que se anularan paquetes destinados al cliente.

## <a name="dhcp-rfcs"></a>RFC de DHCP

NetX DHCP es compatible con la RFC2132, RFC2131 y RFC relacionadas.

