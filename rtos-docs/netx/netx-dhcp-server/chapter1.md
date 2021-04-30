---
title: 'Capítulo 1: Introducción al servidor DHCP de Azure RTOS NetX'
description: La aplicación establece la comunicación con su servidor DHCP de Azure RTOS NetX para solicitar y obtener una dirección IP de forma dinámica.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 17438a20ad3da64c88c3d6bb19a4887c2c6e354e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815249"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-server"></a>Capítulo 1: Introducción al servidor DHCP de Azure RTOS NetX

En NetX, la dirección IP de la aplicación es uno de los parámetros proporcionados a la llamada de servicio a *nx_ip_create*. Proporcionar la dirección IP no supone ningún problema si la aplicación conoce la dirección IP, ya sea de forma estática o a través de la configuración del usuario. Sin embargo, hay algunos casos en los que la aplicación no sabe ni se preocupa por saber cuál es su dirección IP. En tales situaciones, se debe proporcionar una dirección IP cero a la función *nx_ip_create* y la aplicación establece la comunicación con su servidor DHCP de Azure RTOS NetX para solicitar y obtener una dirección IP de forma dinámica.

## <a name="dynamic-ip-address-assignment"></a>Asignación de dirección IP dinámica

El servicio básico usado para obtener una dirección IP dinámica de la red es el protocolo Reverse Address Recognition Protocol (RARP). Este protocolo es similar a ARP, con la excepción de que está diseñado para obtener una dirección IP para sí mismo en lugar de encontrar la dirección MAC para otro nodo de red. El mensaje RARP de bajo nivel se emite en la red local y es responsabilidad de un servidor de la red responder con una respuesta RARP, que contiene una dirección IP asignada dinámicamente.

Aunque RARP proporciona un servicio para asignar direcciones IP de forma dinámica, tiene varias limitaciones. La limitación más evidente es que RARP solo proporciona una asignación dinámica de la dirección IP. En la mayoría de los casos, es necesaria una mayor información para que un dispositivo pueda participar correctamente en una red. Además de una dirección IP, la mayoría de los dispositivos necesitan la máscara de red y la dirección IP de puerta de enlace. También es posible que se necesite la dirección IP de un servidor DNS y otra información de la red. RARP no tiene la capacidad de proporcionar esta información.

## <a name="rarp-alternatives"></a>Alternativas de RARP

Con el fin de superar las limitaciones de RARP, los investigadores han desarrollado un mecanismo para asignar direcciones IP más completo denominado protocolo de arranque (BOOTP). Este protocolo tiene la capacidad de asignar dinámicamente una dirección IP y también proporcionar información adicional sobre la red. Sin embargo, BOOTP tiene el inconveniente de estar diseñado para configuraciones de red estáticas. No permite asignar direcciones rápidas o automatizadas.

Aquí es donde el protocolo de configuración dinámica de host (DHCP) es muy útil. DHCP está diseñado para ampliar la funcionalidad básica de BOOTP con el fin de incluir la asignación de servidor IP totalmente automatizada y la asignación de direcciones IP completamente dinámicas a través de la "concesión" de una dirección IP a un cliente durante un período de tiempo especificado. DHCP también se puede configurar para asignar direcciones IP de forma estática como BOOTP.

## <a name="dhcp-messages"></a>Mensajes DHCP

Aunque DHCP mejora en gran medida la funcionalidad de BOOTP, DHCP usa el mismo formato de mensaje que BOOTP y admite las mismas opciones de proveedor que BOOTP. Para realizar su función, DHCP introduce siete nuevas opciones específicas de DHCP, como se indica a continuación:

| Opción     | Value | Origen                |
| ---------- | ----- | --------------------- |
| DISCOVER   | (1)   | (enviado por el cliente DHCP) |
| OFFER      | (2)   | (enviado por el servidor DHCP) |
| REQUEST    | (3)   | (enviado por el cliente DHCP) |
| DECLINE    | (4)   | (enviado por el cliente DHCP) |
| ACK        | (5)   | (enviado por el servidor DHCP) |
| NACK       |  (6)   | (enviado por el servidor DHCP) |
| RELEASE    | (7)   | (enviado por el cliente DHCP) |
| INFORM     | (8)   | (enviado por el cliente DHCP) |
| FORCERENEW | (9)   | (enviado por el cliente DHCP) |

## <a name="dhcp-communication"></a>Comunicación DHCP

El servidor DHCP emplea el protocolo UDP para recibir solicitudes de cliente DHCP y transmitir respuestas. Antes de tener una dirección IP, los mensajes UDP que llevan la información de DHCP se envían y se reciben mediante la dirección IP de difusión 255.255.255.255. Sin embargo, si el cliente conoce la dirección del servidor DHCP, puede enviar mensajes DHCP mediante mensajes de unidifusión.

## <a name="dhcp-server-state-machine"></a>Máquina de estados del servidor DHCP

El servidor DHCP se implementa como una máquina de estados de dos pasos procesada por un subproceso DHCP interno que se crea durante el procesamiento de *nx_dhcp_server_create*. Los estados principales del servidor DHCP son 1) la recepción de un mensaje DISCOVER de un cliente DHCP y 2) la recepción de un mensaje REQUEST.

A continuación se indican los estados de cliente DHCP correspondientes:

- **NX_DHCP_STATE_BOOT**: a partir de una dirección IP anterior
- **NX_DHCP_STATE_INIT**: sin ningún valor de dirección IP anterior inicial
- **NX_DHCP_STATE_SELECTING**: a la espera de una respuesta de un servidor DHCP
- **NX_DHCP_STATE_REQUESTING**: servidor DHCP identificado, solicitud de dirección IP enviada
- **NX_DHCP_STATE_BOUND**: concesión de dirección IP DHCP establecida
- **NX_DHCP_STATE_RENEWING**: tiempo de renovación de concesión de dirección IP DHCP transcurrido, renovación solicitada
- **NX_DHCP_STATE_REBINDING**: tiempo de reenlace de concesión de dirección IP DHCP transcurrido, renovación solicitada
- **NX_DHCP_STATE_FORCERENEW**: concesión de la dirección IP DHCP establecida, forzar la renovación por servidor o por aplicación
- **NX_DHCP_STATE_FAILED**: no se ha encontrado ningún servidor o no se ha recibido respuesta del servidor

## <a name="dhcp-additional-parameters"></a>Parámetros adicionales de DHCP

El servidor NetX DHCP tiene una lista predeterminada de parámetros de opciones que se establece en la opción configurable NX_DHCP_DEFAULT_SERVER_OPTION_LIST *en nx_dhcp_server.h* para proporcionar a los clientes DHCP parámetros de configuración de red comunes o críticos, como la dirección de puerta de enlace o ruta y el servidor DNS para el cliente DHCP.

## <a name="dhcp-rfcs"></a>RFC de DHCP

El servidor NetX DHCP es compatible con la RFC2132, RFC2131 y RFC relacionadas.
