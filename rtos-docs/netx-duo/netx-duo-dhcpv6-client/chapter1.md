---
title: 'Capítulo 1: Introducción al cliente DHCPv6 de Azure RTOS NetX Duo'
description: En redes IPv6, DHCPv6 reemplaza a DHCP para la asignación de direcciones IP globales dinámicas de un servidor DHCPv6 y ofrece la mayoría de las características, así como muchas mejoras.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3bf3b52c53bb26e2c9c2c736ae35817eb967f609
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814785"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-client"></a>Capítulo 1: Introducción al cliente DHCPv6 de Azure RTOS NetX Duo

En redes IPv6, DHCPv6 reemplaza a DHCP para la asignación de direcciones IP globales dinámicas de un servidor DHCPv6 y ofrece la mayoría de las características, así como muchas mejoras. En este documento se explica con detalle cómo se usa la API del cliente DHCPv6 de Azure RTOS NetX Duo para obtener direcciones IPv6.

## <a name="dhcpv6-communication"></a>Comunicación de DHCPv6

El protocolo DHCPv6 usa UDP. El cliente utiliza el puerto 546 y el servidor usa el puerto 547 para intercambiar mensajes DHCPv6. El cliente usa la dirección local del vínculo para que una dirección de origen inicie las solicitudes DHCPv6 en los servidores DHCPv6 disponibles. Cuando el cliente envía mensajes destinados a todos los servidores DHCPv6 de la red, utiliza la dirección de multidifusión *All_DHCP_Relay_Agents_and_Servers* *FF02::01:02*. Esta es una dirección multidifusión reservada de ámbito de vínculo.

## <a name="dhcpv6-process-of-requesting-an-ipv6-address"></a>Proceso de solicitud de una dirección IPv6 en DHCPv6

Para comenzar el proceso de solicitud de una asignación de dirección IPv6 global, un cliente envía primero un mensaje de solicitud mediante el servicio *nx_dhcpv6_send_solicit*:

**UINT nx_dhcpv6_request_solicit(NX_DHCPV6 \*dhcpv6_ptr)**

Este mensaje se envía a todos los servidores mediante la dirección *All_DHCP_Relay_Agents_and_Servers*. En la solicitud SOLICIT, el cliente puede solicitar la asignación de direcciones IPv6 específicas como una sugerencia para el servidor. También puede solicitar otra información de configuración de red del servidor, como el servidor DNS, el servidor NTP y otras opciones de la solicitud de opciones en el mensaje SOLICIT.

Un servidor DHCPv6 que puede atender una solicitud del cliente responde con un mensaje ADVERTISE que contiene las direcciones IPv6 que puede asignar al cliente, el tiempo de la concesión de la dirección IPv6 y cualquier información adicional solicitada por el cliente. El protocolo de cliente DHCPv6 requiere que el cliente espere un período de tiempo para recibir mensajes ADVERTISE de todos los servidores DHCPv6 de la red. Realiza un procesamiento previo de cada mensaje ADVERTISE para que sea un mensaje válido y examina los datos de opciones de varios parámetros DHCPv6. También comprueba el valor de preferencia en la opción de preferencia, si lo proporciona el servidor. Si se recibe más de un mensaje ADVERTISE, el cliente DHCPv6 de NetX elige el servidor con el valor de preferencia más alto recibido al final del período de espera.

La excepción es si el cliente recibe un mensaje ADVERTISE con un valor de preferencia de 255. Acepta el mensaje inmediatamente y descarta todos los mensajes ADVERTISE posteriores.

El período de espera se define como el período de retransmisión que el cliente DHCPv6 espera antes de enviar otro mensaje SOLICIT si no ha recibido una respuesta de ningún servidor. El tiempo de espera de retransmisión inicial en el estado de la solicitud se define mediante el protocolo DHCPv6 descrito en RFC 3315 como 1 segundo. Los intervalos de retransmisión posteriores, si el cliente DHCPv6 no recibe una respuesta de servidor válida, se duplican hasta 120 segundos.

Una vez elegido el servidor, el cliente extrae los datos del mensaje ADVERTISE y envía un mensaje REQUEST al servidor para aceptar la información de la dirección asignada y los tiempos de la concesión. El servidor responde con un mensaje REPLY para confirmar que las direcciones IPv6 del cliente se registran con el servidor como asignado al cliente.

El cliente DHCPv6 registra las direcciones IPv6 asignadas con la instancia de IP (por ejemplo, NetX Duo). Si está configurado para el protocolo de detección de direcciones duplicadas (DAD) (habilitado de forma predeterminada), NetX Duo enviará automáticamente mensajes Solicit de vecinos para comprobar que las direcciones asignadas son únicas en la red. Si es así, notifica al cliente DHCPv6 cuando la dirección asignada se ha promocionado de TENTATIVE a VALID. El cliente DHCPv6 se promueve al estado BOUND y el dispositivo puede usar esa dirección IPv6 para enviar y transmitir mensajes. Si se produce un error en el protocolo DAD, NetX Duo notifica al cliente DHCPv6 y el cliente DHCPv6 envía un mensaje DECLINE para las direcciones IPv6 que se asignan al servidor y restablece el estado del cliente DHCPv6 al estado INIT.

### <a name="notification-of-successful-address-assignment-and-validation"></a>Notificación de validación y asignación de dirección correcta

La aplicación puede determinar el resultado de la solicitud de la dirección del cliente DHCPv6 desde los cambios de estado si el cliente DHCPv6 está configurado con la devolución de llamada de cambio de estado en el servicio *nx_dhcpv6_client_create*. Si no recibe ninguna respuesta del servidor, el cambio de estado observado es de SOLICIT a INIT. Si recibe una respuesta del servidor, pero el servidor no puede asignar la dirección, la aplicación recibirá una notificación por la devolución de llamada de error del servidor del cliente DHCPv6 si se configura con una (también en *nx_dhcpv6_client_create).* Si el cliente ha alcanzado el estado BOUND, pero no ha superado la comprobación de DAD, verá un cambio de estado de BOUND a INIT. Tenga en cuenta que una aplicación habilitada para DAD debe dejar tiempo para la comprobación de DAD después de iniciar el proceso de solicitud. Normalmente, aproximadamente entre 400 y 500 tics (4-5 segundos en la mayoría de los casos).

### <a name="relinquishing-an-ipv6-address"></a>Renuncia a una dirección IPv6

Cuando el cliente necesita liberar una dirección IPv6 asignada, informa al servidor DHCPv6 llamando al servicio *nx_dhcpv6_request_release*:

### <a name="uint-nx_dhcpv6_request_releasenx_dhcpv6-dhcpv6_ptr"></a>UINT nx_dhcpv6_request_release(NX_DHCPV6 \*dhcpv6_ptr)

El cliente DHCPv6 envía un mensaje RELEASE de unidifusión que contiene las direcciones asignadas al servidor que asignó la dirección y espera a que un mensaje REPLY confirme que el servidor ha recibido el mensaje.

Nota: Hay un proceso diferente para el cliente que se está apagando, pero que tiene previsto seguir usando las direcciones IPv6 asignadas durante el reinicio. No envía el mensaje RELEASE durante el apagado a menos que planee solicitar una nueva dirección en el encendido. Consulte "Requisitos de la memoria no volátil" para obtener una explicación de esta situación.

### <a name="dhcpv6-lease-timeouts"></a>Tiempos de espera de la concesión de DHCPv6

La concesión de IPv6 asignada por el servidor contiene dos parámetros de tiempo de espera, T1 y T2, en cada bloque de asociación de identidades de direcciones no temporales (IANA). Una IANA se describe en cualquier parte de este manual del usuario. Si el tiempo transcurrido desde que el cliente DHCPv6 estaba enlazado a la dirección IPv6 asignada es igual a T1, el cliente DHCPv6 inicia automáticamente la renovación de las direcciones IPv6 mediante el envío de un mensaje RENEW. Si el tiempo transcurrido es igual a T2, el cliente DHCPv6 envía automáticamente un mensaje REBIND si no ha recibido ninguna respuesta a sus solicitudes RENEW.

Otros dos parámetros de concesión de IPv6, duraciones preferida y válida, se asignan con cada bloque de asociación de identidades (IA) incluido en el bloque de IANA. Las duraciones preferida y válida se asignan cuando la dirección IPv6 asignada está en desuso o no es válida, respectivamente. T1 debe ser menor que la duración preferida. T2 debe ser menor que la duración válida.

### <a name="ip-thread-task-requirements"></a>Requisitos de la tarea de subprocesos de IP

El cliente DHCPv6 de NetX Duo requiere la creación de una instancia de IP de NetX Duo anterior a la creación del cliente DHCPv6 para usar los servicios del cliente DHCPv6.

UDP, IPv6 e ICMPv6 deben estar habilitados en la instancia de IP antes de usar el cliente DHCPv6.

  - *nx_udp_enable*

  - *nxd_ipv6_enable*

  - *nxd_icmp_enable*

### <a name="packet-pool-requirements"></a>Requisitos de grupos de paquetes

La creación del cliente DHCPv6 de NetX Duo requiere un grupo de paquetes creado previamente para enviar mensajes DHCPv6. El tamaño del grupo de paquetes en términos de carga de paquetes y el número de paquetes disponibles es configurable por el usuario, y depende del volumen previsto de mensajes DHCPv6 y otras transmisiones que va a enviar la aplicación.

Un mensaje DHCPv6 típico tiene aproximadamente 200 bytes, según el número de direcciones IA y las opciones de DHCPv6 solicitadas por el cliente.

### <a name="network-requirements"></a>Requisitos de red

El cliente DHCPv6 de NetX Duo requiere la creación de un socket UDP enlazado al puerto 546. El socket se crea cuando se crea la tarea del cliente DHCPv6.

### <a name="non-volatile-memory-requirements"></a>Requisitos de la memoria no volátil

Si un cliente DHCPv6 libera su concesión de IPv6 con el servidor DHCPv6 al apagarse y solicita nuevas direcciones IPv6 en el reinicio, no es necesario el almacenamiento de memoria no volátil. Si un cliente desea seguir usando su concesión asignada, debe almacenar determinada información sobre el cliente DHCPv6 en la memoria no volátil a lo largo de los reinicios.

Los requisitos de la memoria no volátil y la API del cliente DHCPv6 se describen con más detalle en la sección **Uso del cliente DHCPv6 de NetX Duo** del capítulo dos.

### <a name="netx-duo-dhcpv6-client-limitations"></a>Limitaciones del cliente DHCPv6 de NetX Duo

La versión actual del cliente DHCPv6 de NetX Duo tiene las siguientes limitaciones:

  - El cliente DHCPv6 de NetX Duo no admite la opción de unidifusión del servidor para enviar mensajes DHCPv6 de unidifusión al servidor DHCPv6, incluso si el servidor indica que se permite.

  - El cliente DHCPv6 de NetX Duo no admite la solicitud de reconfiguración en la que un servidor inicia los cambios de la dirección IPv6 en los clientes de la red.

  - El cliente DHCPv6 de NetX Duo no admite el formato de empresa para el bloque de control de identificador único de DHCPv6. Solo admite el formato de nivel de vínculo y de nivel de vínculo más tiempo.

  - El cliente DHCPv6 de NetX Duo no admite solicitudes de direcciones de asociación temporal (TA), pero sí admite solicitudes de opciones no temporales (IANA).

## <a name="multihome-and-multiple-address-support"></a>Compatibilidad con varias direcciones y host múltiple

El cliente DHCPv6 admite varias interfaces y direcciones por interfaz. El servicio del cliente DHCPv6, *nx_dhcpv6_client_set_interface*, habilita la aplicación cliente para establecer la interfaz de red en la que la aplicación se comunicará con el servidor DHCPv6. El cliente DHCPv6 tiene como valor predeterminado la interfaz principal (índice cero).

En el caso de varias direcciones por interfaz, el cliente DHCPv6 mantiene una lista interna de direcciones a partir del índice 0. Tenga en cuenta que es posible que la misma dirección registrada con el cliente DHCPv6 no se encuentre necesariamente en el mismo índice de la tabla de IP de direcciones de interfaz.

En el caso de los servicios del cliente DHCPv6 que recuperan información sobre la concesión de las direcciones IPv6 del cliente, algunos requieren que se especifique un índice de dirección. A continuación se muestra un ejemplo para obtener las duraciones preferida y válida:

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                              UINT address_index, 
                                              NXD_ADDRESS *ip_address,
                                              ULONG preferred_lifetime, 
                                              ULONG *valid_lifetime)
```

La aplicación cliente también puede recuperar el número de direcciones IPv6 válidas asignadas desde el servicio *nx_dhcpv6_get_valid_ip_address_count*:

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count)
```

Los servicios del cliente DHCPv6 heredados que se crearon antes de que se admitieran varias direcciones en NetX Duo no toman un índice de direcciones. Por lo tanto, con estos servicios, los datos solicitados se toman de la dirección IA global principal, independientemente de cuántas direcciones IA estén asignadas al cliente. A continuación se muestra un ejemplo:

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address)
```

## <a name="netx-duo-dhcpv6-client-callback-functions"></a>Funciones de devolución de llamada del cliente DHCPv6 de NetX Duo

*nx_dhcpv6_state_change_callback*

Cuando el cliente DHCPv6 cambia a un nuevo estado DHCPv6 como resultado del procesamiento de una solicitud DHCPv6, lo notifica a la aplicación con esta función de devolución de llamada.

*nx_dhcpv6_server_error_handler*

Cuando el cliente DHCPv6 recibe una respuesta de servidor que contiene una opción *Status* con un estado distinto de cero (no correcto), se lo notifica a la aplicación con esta devolución de llamada, que incluye el código de estado de error del servidor.

Nota: Dado que estas funciones de devolución de llamada se llaman desde la tarea de subproceso del cliente DHCPv6, la aplicación cliente no debe llamar a ningún servicio del cliente DHCPv6 de NetX Duo que requiera el control de exclusión mutua del cliente DHCPv6, como *nx_dhcpv6_start, nx_dhcpv6_stop* y cualquiera de las API que envíen mensajes directamente desde la devolución de llamada; por ejemplo, *nx_dhcpv6_request_release*.

## <a name="dhcpv6-rfcs"></a>RFC de DHCPv6

El cliente DHCP de NetX Duo es compatible con RFC3315, RFC3646 y RFC relacionados.