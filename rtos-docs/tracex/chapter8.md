---
title: 'Capítulo 8: Eventos de seguimiento de Azure RTOS NetX'
description: Este capítulo contiene una descripción de los eventos de Azure RTOS NetX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: ce355d86d7db0b7e259ae58e306d990277b77a8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816289"
---
# <a name="chapter-8---azure-rtos-netx-trace-events"></a>Capítulo 8: Eventos de seguimiento de Azure RTOS NetX

Este capítulo contiene una descripción de los eventos de Azure RTOS NetX. 

## <a name="list-of-events-and-icons"></a>Lista de eventos e iconos

A continuación se muestra una lista de eventos de NetX mostrados por TraceX.

| Icono                                           | Significado                 |
| -------------------------------- | ------------------------------------- |
| ![Icono de recepción de solicitud A R P interna](./media/user-guide/netx-events/image1.png)    | Recepción de solicitud ARP interna |
| ![Icono de envío de solicitud A R P interno](./media/user-guide/netx-events/image2.png)    | Envío de solicitud ARP interno |
| ![Icono de recepción de respuesta A R P interna](./media/user-guide/netx-events/image3.png)    | Recepción de respuesta ARP interna |
| ![Icono de envío de respuesta A R P interno](./media/user-guide/netx-events/image4.png)    | Envío de respuesta ARP interno |
| ![Icono de recepción de I C M P interna](./media/user-guide/netx-events/image5.png)    | Recepción de ICMP interna |
| ![Icono de envío de I C M P interno](./media/user-guide/netx-events/image6.png)    | Envío de ICMP interno |
| ![Icono de recepción de I G M P de NetX interna](./media/user-guide/netx-events/image7.png)    | Recepción de IGMP de NetX interna |
| ![Icono de recepción de I P interna](./media/user-guide/netx-events/image8.png)    | Recepción de IP interna |
| ![Icono de envío de I P interno](./media/user-guide/netx-events/image9.png)    | Envío de IP interno |
| ![Icono de recepción de datos de T C P interna](./media/user-guide/netx-events/image10.png)    | Recepción de datos de TCP interna |
| ![Icono de envío de datos de T C P interno](./media/user-guide/netx-events/image11.png)    | Envío de datos de TCP interno |
| ![Icono de recepción de T C P F I N interna](./media/user-guide/netx-events/image12.png)    | Recepción de TCP FIN interna |
| ![Icono de envío de T C P F I N interno](./media/user-guide/netx-events/image13.png)    | Envío de TCP FIN interno |
| ![Icono de recepción de T C P R S T interna](./media/user-guide/netx-events/image14.png)    | Recepción de TCP RST interna |
| ![Icono de envío de T C P R S T interno](./media/user-guide/netx-events/image15.png)    | Envío de TCP RST interno |
| ![Icono de recepción de T C P S Y N interna](./media/user-guide/netx-events/image16.png)    | Recepción de TCP SYN interna |
| ![Icono de envío de T C P S Y N interno](./media/user-guide/netx-events/image17.png)    | Envío de TCP SYN interno |
| ![Icono de recepción de U D P interna](./media/user-guide/netx-events/image18.png)    | Recepción de UDP interna |
| ![Icono de envío de U D P interno](./media/user-guide/netx-events/image19.png)    | Envío de UDP interno |
| ![Icono de recepción de R A R P interna](./media/user-guide/netx-events/image20.png)    | Recepción de RARP interna |
| ![Icono de envío de R A R P interno](./media/user-guide/netx-events/image21.png)    | Envío de RARP interno |
| ![Icono de reintento de T C P interno](./media/user-guide/netx-events/image22.png)    | Reintento de TCP interno |
| ![Icono de cambio de estado de T C P interno](./media/user-guide/netx-events/image23.png)    | Cambio de estado de TCP interno |
| ![Icono de envío de paquete de controladores de E/S interno](./media/user-guide/netx-events/image24.png)    | Envío de paquete de controladores de E/S interno |
| ![icon](./media/user-guide/netx-events/image25.png)    | Inicialización de controlador de E/S interna |
| ![Icono de inicialización de controlador de E/S interna](./media/user-guide/netx-events/image26.png)    | Habilitación del vínculo de controlador de E/S interna |
| ![Icono de deshabilitación del vínculo de controlador de E/S interna](./media/user-guide/netx-events/image27.png)    | Deshabilitación del vínculo de controlador de E/S interna |
| ![Icono de difusión del paquete de controladores de E/S interna](./media/user-guide/netx-events/image28.png)    | Difusión del paquete de controladores de E/S interna |
| ![Icono de envío de A R P del controlador de E/S interno](./media/user-guide/netx-events/image29.png)    | Envío de ARP del controlador de E/S interno |
| ![Icono de envío de respuesta A R P del controlador de E/S interno](./media/user-guide/netx-events/image30.png)    | Envío de respuesta ARP del controlador de E/S interno |
| ![Icono de envío de R A R P del controlador de E/S interno](./media/user-guide/netx-events/image31.png)    | Envío de RARP del controlador de E/S interno |
| ![Icono de combinación de multidifusión del controlador de E/S interna](./media/user-guide/netx-events/image32.png)    | Combinación de multidifusión del controlador de E/S interna |
| ![Icono de salida de multidifusión del controlador de E/S interna](./media/user-guide/netx-events/image33.png)    | Salida de multidifusión del controlador de E/S interna |
| ![Icono de obtención de estado del controlador de E/S interna](./media/user-guide/netx-events/image34.png)    | Obtención de estado del controlador de E/S interna |
| ![Icono de obtención de velocidad del controlador de E/S interna](./media/user-guide/netx-events/image35.png)    | Obtención de velocidad del controlador de E/S interna |
| ![Icono de obtención de tipo dúplex del controlador de E/S interna](./media/user-guide/netx-events/image36.png)    | Obtención de tipo dúplex del controlador de E/S interna |
| ![Icono de obtención de número de errores del controlador de E/S interna](./media/user-guide/netx-events/image37.png)    | Obtención de número de errores del controlador de E/S interna |
| ![Icono de obtención de número de R X del controlador de E/S interna](./media/user-guide/netx-events/image38.png)    | Obtención de número de RX del controlador de E/S interna |
| ![Icono de obtención de número de T X del controlador de E/S interna](./media/user-guide/netx-events/image39.png)    | Obtención de número de TX del controlador de E/S interna |
| ![Icono de obtención de errores de asignación del controlador de E/S interna](./media/user-guide/netx-events/image40.png)    | Obtención de errores de asignación del controlador de E/S interna |
| ![Icono de anulación de inicialización del controlador de E/S interna](./media/user-guide/netx-events/image41.png)    | Anulación de inicialización del controlador de E/S interna |
| ![Icono de procesamiento diferido del controlador de E/S interno](./media/user-guide/netx-events/image42.png)    | Procesamiento diferido del controlador de E/S interno |
| ![Icono de invalidación de entradas dinámicas de A R P](./media/user-guide/netx-events/image43.png)    | **Invalidación de entradas dinámicas de ARP** (*nx_arp_dynamic_entries_invalidate*) |
| ![Icono de establecimiento de entrada dinámica de A R P](./media/user-guide/netx-events/image44.png)    | **Establecimiento de entrada dinámica de ARP** (*nx_arp_dynamic_entry_set*) |
| ![Icono de habilitación de A R P](./media/user-guide/netx-events/image45.png)    | **Habilitación de ARP** (*nx_arp_enable*) |
| ![Icono de envío gratuito de A R P](./media/user-guide/netx-events/image46.png)    | **Envío gratuito de ARP** (*nx_arp_gratuitous_send*) |
| ![Icono de búsqueda de dirección de hardware de A R P](./media/user-guide/netx-events/image47.png)    | **Búsqueda de dirección de hardware de ARP** (*nx_arp_hardware_address_find*) |
| ![Icono de obtención de información de A R P](./media/user-guide/netx-events/image48.png)    | **Obtención de información de ARP** (*nx_arp_info_get*) |
| ![Icono de búsqueda de dirección I P de A R P](./media/user-guide/netx-events/image49.png)    | **Búsqueda de dirección IP de ARP** (*nx_arp_ip_address_find*) |
| ![Icono de creación de entrada estática de A R P](./media/user-guide/netx-events/image50.png)    | **Creación de entrada estática de ARP** (*nx_arp_static_entry_create*) |
| ![Icono de eliminación de entradas estáticas de A R P](./media/user-guide/netx-events/image51.png)    | **Eliminación de entradas estáticas de ARP** (*nx_arp_static_entries_delete*) |
| ![Icono de eliminación de entrada estática de A R P](./media/user-guide/netx-events/image52.png)    | **Eliminación de entrada estática de ARP** (*nx_arp_static_entry_delete*) |
| ![Icono de eliminación de entrada de caché doble](./media/user-guide/netx-events/image53.png)    | **Eliminación de entrada de caché doble** (*nxd_nd_cache_entry_delete*) |
| ![Icono de establecimiento de entrada de caché doble](./media/user-guide/netx-events/image54.png)    | **Establecimiento de entrada de caché doble** (*nxd_nd_cache_entry_set*) |
| ![Icono de invalidación de caché doble](./media/user-guide/netx-events/image55.png)    | **Invalidación de caché doble** (*nxd_nd_cache_invalidate*) |
| ![Icono de búsqueda de dirección I P de caché doble](./media/user-guide/netx-events/image56.png)    | **Búsqueda de dirección IP de caché doble** (*nxd_nd_cache_ip_address_find*) |
| ![Icono de habilitación de I C M P doble](./media/user-guide/netx-events/image57.png)    | **Habilitación de ICMP doble** (*nxd_icmp_enable*) |
| ![Icono de ping de I P v 6 de I C M P doble](./media/user-guide/netx-events/image58.png)    | **Ping de IPv6 de ICMP doble** (*nxd_icmp_ping*) |
| ![Icono de búsqueda de tamaño máximo de carga de I P doble](./media/user-guide/netx-events/image59.png)    | **Búsqueda de tamaño máximo de carga de IP doble** (*nx_max_payload_size_find*) |
| ![Icono de envío de paquete sin formato de I P doble](./media/user-guide/netx-events/image60.png)    | **Envío de paquete sin formato de IP doble** (*nxd_ip_raw_packet_send*) |
| ![Icono de adición de enrutador predeterminado de I P v 6 doble](./media/user-guide/netx-events/image61.png)    | **Adición de enrutador predeterminado de IPv6 doble** (*nxd_ipv6_default_router_add*) |
| ![Icono de eliminación de enrutador predeterminado de I P v 6 doble](./media/user-guide/netx-events/image62.png)    | **Eliminación de enrutador predeterminado de IPv6 doble** (*nxd_ipv6_default_router_delete*) |
| ![Icono de habilitación de I P v 6 doble](./media/user-guide/netx-events/image63.png)    | **Habilitación de IPv6 doble** (*nxd_ipv6_enable)* |
| ![Icono de obtención de dirección global de I P v 6 doble](./media/user-guide/netx-events/image64.png)    | **Obtención de dirección global de IPv6 doble** (*nxd_ipv6_global_address_get*) |
| ![Icono de establecimiento de dirección global de I P v 6 doble](./media/user-guide/netx-events/image65.png)    | **Establecimiento de dirección global de IPv6 doble** (*nxd_ipv6_global_address_set*) |
| ![Icono de inicio de proceso D A D de I P v 6 doble](./media/user-guide/netx-events/image66.png)    | **Inicio de proceso DAD de IPv6 doble** (*nxd_ipv6_initiate_dad_process*) |
| ![Icono de obtención de dirección de interfaz de I P v 6 doble](./media/user-guide/netx-events/image67.png)    | **Obtención de dirección de interfaz de IPv6 doble** (*nxd_ipv6_interface_address_get*) |
| ![Icono de establecimiento de dirección de interfaz de I P v 6 doble](./media/user-guide/netx-events/image68.png)    | **Establecimiento de dirección de interfaz de IPv6 doble** (*nxd_ipv6_interface_address_set*) |
| ![Icono de obtención de dirección local de vínculo de I P v 6 doble](./media/user-guide/netx-events/image69.png)    | **Obtención de dirección local de vínculo de IPv6 doble** (*nxd_ipv6_linklocal_address_get*) |
| ![Icono de establecimiento de dirección local de vínculo de I P v 6 doble](./media/user-guide/netx-events/image70.png)    | **Establecimiento de dirección local de vínculo de IPv6 doble** (*nxd_ipv6_linklocal_address_get*) |
| ![Icono de envío de paquete sin formato de I P v 6 doble](./media/user-guide/netx-events/image71.png)    | **Envío de paquete sin formato de IPv6 doble** (*nxd_ipv6_raw_packet_send*) |
| ![Icono de obtención de información de nodo del mismo nivel de socket de T C P doble](./media/user-guide/netx-events/image72.png)    | **Obtención de información de nodo del mismo nivel de socket de TCP doble** (*nxd_tcp_socket_peer_info_get*) |
| ![Icono de establecimiento de interfaz de socket de T C P doble](./media/user-guide/netx-events/image73.png)    | **Establecimiento de interfaz de socket de TCP doble** (*nxd_tcp_socket_set_interface*) |
| ![Icono de envío de socket de U D P doble](./media/user-guide/netx-events/image74.png)    | **Envío de socket de UDP doble** (*nxd_udp_socket_send*) |
| ![Icono de establecimiento de interfaz de socket de U D P doble](./media/user-guide/netx-events/image75.png)    | **Establecimiento de interfaz de socket de UDP doble** (*nxd_udp_socket_set_interface*) |
| ![Icono de extracción de origen de U D P doble](./media/user-guide/netx-events/image76.png)    | **Extracción de origen de UDP doble** (*nxd_udp_source_extract*) |
| ![Icono de habilitación de I C M P](./media/user-guide/netx-events/image77.png)    | **Habilitación de ICMP** (*nx_icmp_enable*) |
| ![Icono de obtención de información de I C M P](./media/user-guide/netx-events/image78.png)    | **Obtención de información de ICMP** (*nx_icmp_info_get*) |
| ![Icono de ping de I C M P](./media/user-guide/netx-events/image79.png)    | **Ping de ICMP** (*nx_icmp_ping*) |
| ![Icono de habilitación de I G M P](./media/user-guide/netx-events/image80.png)    | **Habilitación de IGMP** (*nx_igmp_enable*) |
| ![Icono de obtención de información de I G M P](./media/user-guide/netx-events/image81.png)    | **Obtención de información de IGMP** (*nx_igmp_info_get*) |
| ![Icono de deshabilitación de bucle invertido de I G P M](./media/user-guide/netx-events/image82.png)    | **Deshabilitación de bucle invertido de IGMP** (*nx_igmp_loopback_disable*) |
| ![Icono de habilitación de bucle invertido de I G M P](./media/user-guide/netx-events/image83.png)    | **Habilitación de bucle invertido de IGMP** (*nx_igmp_loopback_enable*) |
| ![Icono de combinación de multidifusión de I G M P](./media/user-guide/netx-events/image84.png)    | **Combinación de multidifusión de IGMP** (*nx_igmp_multicast_join*) |
| ![Icono de salida de multidifusión de I G M P](./media/user-guide/netx-events/image85.png)    | **Salida de multidifusión de IGMP** (*nx_igmp_multicast_leave*) |
| ![Icono de notificación de cambio de dirección I P](./media/user-guide/netx-events/image86.png)    | **Notificación de cambio de dirección IP** (*nx_ip_address_change_notify*) |
| ![Icono de obtención de dirección I P](./media/user-guide/netx-events/image87.png)    | **Obtención de dirección IP** (*nx_ip_address_get*) |
| ![Icono de establecimiento de dirección I P](./media/user-guide/netx-events/image88.png)    | **Establecimiento de dirección IP** (*nx_ip_address_set*) |
| ![Icono de creación de I P](./media/user-guide/netx-events/image89.png)    | **Creación de IP** (*nx_ip_create*) |
| ![Icono de eliminación de I P](./media/user-guide/netx-events/image90.png)    | **Eliminación de IP** (*nx_ip_delete*) |
| ![Icono de comando directo de controlador de I P](./media/user-guide/netx-events/image91.png)    | **Comando directo de controlador de IP** (*nx_ip_driver_direct_command*) |
| ![Icono de deshabilitación de reenvío de I P](./media/user-guide/netx-events/image92.png)    | **Deshabilitación de reenvío de IP** (*nx_ip_forwarding_disable*) |
| ![Icono de habilitación de reenvío de I P](./media/user-guide/netx-events/image93.png)    | **Habilitación de reenvío de IP** (*nx_ip_forwarding_enable*) |
| ![Icono de deshabilitación de fragmento de I P](./media/user-guide/netx-events/image94.png)    | **Deshabilitación de fragmento de IP** (*nx_ip_fragment_disable*) |
| ![Icono de habilitación de fragmento de I P](./media/user-guide/netx-events/image95.png)    | **Habilitación de fragmento de IP** (*nx_ip_fragment_enable*)  |
| ![Icono de establecimiento de dirección de puerta de enlace de I P](./media/user-guide/netx-events/image96.png)    | **Establecimiento de dirección de puerta de enlace de IP** (*nx_ip_gateway_address_set*) |
| ![Icono de obtención de información de I P](./media/user-guide/netx-events/image97.png)    | **Obtención de información de IP** (*nx_ip_info_get*) |
| ![Icono de asociación de interfaz de I P](./media/user-guide/netx-events/image98.png)    | **Asociación de interfaz de IP** (*nx_ip_interface_attach*) |
| ![Icono de obtención de información de interfaz de I P](./media/user-guide/netx-events/image99.png)    | **Obtención de información de interfaz de IP** (*nx_ip_interface_info_get*) |
| ![Icono de deshabilitación de paquete sin formato de I P](./media/user-guide/netx-events/image100.png)    | **Deshabilitación de paquete sin formato de IP** (*nx_ip_raw_packet_disable*) |
| ![Icono de habilitación de paquete sin formato de I P](./media/user-guide/netx-events/image101.png)    | **Habilitación de paquete sin formato de IP** (*nx_ip_raw_packet_enable*) |
| ![Icono de recepción de paquete sin formato de I P](./media/user-guide/netx-events/image102.png)    | **Recepción de paquete sin formato de IP** (*nx_ip_raw_packet_receive*) |
| ![Icono de envío de paquete sin formato de I P](./media/user-guide/netx-events/image103.png)    | **Envío de paquete sin formato de IP** (*nx_ip_raw_packet_send*) |
| ![Icono de adición de ruta estática de I P](./media/user-guide/netx-events/image104.png)    | **Adición de ruta estática de IP** (*nx_ip_static_route_add*) |
| ![Icono de eliminación de ruta estática de I P](./media/user-guide/netx-events/image105.png)    | **Eliminación de ruta estática de IP** (*nx_ip_static_route_delete*) |
| ![Icono de comprobación de estado de I P](./media/user-guide/netx-events/image106.png)    | **Comprobación de estado de IP** (*nx_ip_status_check*)|
| ![Icono de habilitación de I P SEC](./media/user-guide/netx-events/image107.png)    | **Habilitación de IPsec** (*nx_ipsec_enable)* |
| ![Icono de asignación de paquete](./media/user-guide/netx-events/image108.png)    | **Asignación de paquete** (*nx_packet_allocate*) |
| ![Icono de copia de paquete](./media/user-guide/netx-events/image109.png)    | **Copia de paquete** (*nx_packet_copy*) |
| ![Icono de anexión de datos de paquete](./media/user-guide/netx-events/image110.png)    | **Anexión de datos de paquete** (*nx_packet_data_append*) |
| ![Icono de desplazamiento de extracción de datos de paquete](./media/user-guide/netx-events/image111.png)    | **Desplazamiento de extracción de datos de paquete** (*nx_packet_data_extract_offset*) |
| ![Icono de recuperación de datos de paquete](./media/user-guide/netx-events/image112.png)    | **Recuperación de datos de paquete** (*nx_packet_data_retrieve*) |
| ![Icono de obtención de longitud de paquete](./media/user-guide/netx-events/image113.png)    | **Obtención de longitud de paquete** (*nx_packet_length_get*) |
| ![Icono de creación de grupo de paquetes](./media/user-guide/netx-events/image114.png)    | **Creación de grupo de paquetes** (*nx_packet_pool_create*) |
| ![Icono de eliminación de grupo de paquetes](./media/user-guide/netx-events/image115.png)    | **Eliminación de grupo de paquetes** (*nx_packet_pool_delete*) |
| ![Icono de obtención de información de grupo de paquetes](./media/user-guide/netx-events/image116.png)    | **Obtención de información de grupo de paquetes** (*nx_packet_pool_info_get*) |
| ![Icono de liberación de paquete](./media/user-guide/netx-events/image117.png)    | **Liberación de paquete** (*nx_packet_release*) |
| ![Icono de liberación de transmisión de paquete](./media/user-guide/netx-events/image118.png)    | **Liberación de transmisión de paquete** (*nx_packet_transmit_release*) |
| ![Icono de deshabilitación de R A R P](./media/user-guide/netx-events/image119.png)    | **Deshabilitación de RARP** (*nx_rarp_disable*) |
| ![Icono de habilitación de R A R P](./media/user-guide/netx-events/image120.png)    | **Habilitación de RARP** (*nx_rarp_enable*) |
| ![Icono de obtención de información de R A R P](./media/user-guide/netx-events/image121.png)    | **Obtención de información de RARP** (*nx_rarp_info_get*) |
| ![Icono de inicialización del sistema](./media/user-guide/netx-events/image122.png)    | **Inicialización del sistema** (*nx_system_initialize*) |
| ![Icono de enlace de socket de cliente T C P](./media/user-guide/netx-events/image123.png)    | **Enlace de socket de cliente TCP** (*nx_tcp_client_socket_bind*) |
| ![Icono de conexión de socket de cliente T C P](./media/user-guide/netx-events/image124.png)    | **Conexión de socket de cliente TCP** (*nx_tcp_client_socket_connect*) |
| ![Icono de obtención de puerto de socket de cliente T C P](./media/user-guide/netx-events/image125.png)    | **Obtención de puerto de socket de cliente TCP** (*nx_tcp_client_socket_port_get*) |
| ![Icono de desenlace de socket de cliente T C P](./media/user-guide/netx-events/image126.png)    | **Desenlace de socket de cliente TCP** (*nx_tcp_client_socket_unbind*) |
| ![Icono de habilitación de T C P](./media/user-guide/netx-events/image127.png)    | **Habilitación de TCP** (*nx_tcp_enable*) |
| ![Icono de búsqueda de puerto libre de T C P](./media/user-guide/netx-events/image128.png)    | **Búsqueda de puerto libre de TCP** (*nx_tcp_free_port_find*) |
| ![Icono de obtención de información de T C P](./media/user-guide/netx-events/image129.png)    | **Obtención de información de TCP** (*nx_tcp_info_get*) |
| ![Icono de aceptación de socket de servidor T C P](./media/user-guide/netx-events/image130.png)    | **Aceptación de socket de servidor TCP** (*nx_tcp_server_socket_accept*) |
| ![Icono de escucha de socket de servidor T C P](./media/user-guide/netx-events/image131.png)    | **Escucha de socket de servidor TCP** (*nx_tcp_server_socket_listen*) |
| ![Icono de nueva escucha de socket de servidor T C P](./media/user-guide/netx-events/image132.png)    | **Nueva escucha de socket de servidor TCP** (*nx_tcp_server_socket_relisten*) |
| ![Icono de desaceptación de socket de servidor T C P](./media/user-guide/netx-events/image133.png)    | **Desaceptación de socket de servidor TCP** (*nx_tcp_server_socket_unaccept*) |
| ![Icono de abandono de escucha de socket de servidor T C P](./media/user-guide/netx-events/image134.png)    | **Abandono de escucha de socket de servidor TCP** (*nx_tcp_server_socket_unlisten*) |
| ![Icono de bytes disponibles de socket T C P](./media/user-guide/netx-events/image135.png)    | **Bytes disponibles de socket TCP** (*nx_tcp_socket_bytes_available*) |
| ![Icono de creación de socket T C P](./media/user-guide/netx-events/image136.png)    | **Creación de socket TCP** (*nx_tcp_socket_create*) |
| ![Icono de eliminación de socket T C P](./media/user-guide/netx-events/image137.png)    | **Eliminación de socket TCP** (*nx_tcp_socket_delete*) |
| ![Icono de desconexión de socket T C P](./media/user-guide/netx-events/image138.png)    | **Desconexión de socket TCP** (*nx_tcp_socket_disconnect*) |
| ![Icono de obtención de información de socket T C P](./media/user-guide/netx-events/image139.png)    | **Obtención de información de socket TCP** (*nx_tcp_socket_info_get*) |
| ![Icono de obtención de M S S de socket T C P](./media/user-guide/netx-events/image140.png)    | **Obtención de MSS de socket TCP** (*nx_tcp_socket_mss_get*) |
| ![Icono de obtención de M S S de nodo del mismo nivel de socket T C P](./media/user-guide/netx-events/image141.png)    | **Obtención de MSS de nodo del mismo nivel de socket TCP** (*nx_tcp_socket_mss_peer_get*) |
| ![Icono de establecimiento de M S S de socket T C P](./media/user-guide/netx-events/image142.png)    | **Establecimiento de MSS de socket TCP** (*nx_tcp_socket_mss_set*) |
| ![Icono de obtención de información de nodo del mismo nivel de socket T C P](./media/user-guide/netx-events/image143.png)    | **Obtención de información de nodo del mismo nivel de socket TCP** (*nxd_tcp_socket_peer_info_get*) |
| ![Icono de recepción de socket T C P](./media/user-guide/netx-events/image144.png)    | **Recepción de socket TCP** (*nx_tcp_socket_receive*) |
| ![Icono de notificación de recepción de socket T C P](./media/user-guide/netx-events/image145.png)    | **Notificación de recepción de socket TCP** (*nx_tcp_socket_receive_notify*) |
| ![Icono de envío de socket T C P](./media/user-guide/netx-events/image146.png)    | **Envío de socket TCP** (*nx_tcp_socket_send*) |
| ![Icono de espera de estado de socket T C P](./media/user-guide/netx-events/image147.png)    | **Espera de estado de socket TCP** (*nx_tcp_socket_state_wait*) |
| ![Icono de configuración de transmisión de socket T C P](./media/user-guide/netx-events/image148.png)    | **Configuración de transmisión de socket TCP** (*nx_tcp_socket_transmit_configure*) |
| ![Icono de establecimiento de notificación de actualización de ventana de socket T C P](./media/user-guide/netx-events/image149.png)    | **Establecimiento de notificación de actualización de ventana de socket TCP** (*nx_tcp_socket_window_update_notify_set*)  |
| ![Icono de habilitación de U D P](./media/user-guide/netx-events/image150.png)    | **Habilitación de UDP** (*nx_udp_enable*) |
| ![Icono de búsqueda de puerto libre de U D P](./media/user-guide/netx-events/image151.png)    | **Búsqueda de puerto libre de UDP** (*nx_udp_free_port_find*) |
| ![Icono de obtención de información de U D P](./media/user-guide/netx-events/image152.png)    | **Obtención de información de UDP** (*nx_udp_info_get*) |
| ![Icono de enlace de socket U D P](./media/user-guide/netx-events/image153.png)    | **Enlace de socket UDP** (*nx_udp_socket_bind*) |
| ![Icono de bytes disponibles de socket U D P](./media/user-guide/netx-events/image154.png)    | **Bytes disponibles de socket UDP** (*nx_udp_socket_bytes_available*) |
| ![Icono de deshabilitación de suma de comprobación de socket U D P](./media/user-guide/netx-events/image155.png)    | **Deshabilitación de suma de comprobación de socket UDP** (*nx_udp_socket_checksum_disable*) |
| ![Icono de habilitación de suma de comprobación de socket U D P](./media/user-guide/netx-events/image156.png)    | **Habilitación de suma de comprobación de socket UDP** (*nx_udp_socket_checksum_enable*) |
| ![Icono de creación de socket U D P](./media/user-guide/netx-events/image157.png)    | **Creación de socket UDP** (*nx_udp_socket_create*) |
| ![Icono de eliminación de socket U D P](./media/user-guide/netx-events/image158.png)    | **Eliminación de socket UDP** (*nx_udp_socket_delete*) |
| ![Icono de obtención de información de socket U D P](./media/user-guide/netx-events/image159.png)    | **Obtención de información de socket UDP** (*nx_udp_socket_info_get*) |
| ![Icono de establecimiento de interfaz de socket U D P](./media/user-guide/netx-events/image160.png)    | **Establecimiento de interfaz de socket UDP** (*nx_udp_socket_interface_set*) |
| ![Icono de obtención de puerto de socket U D P](./media/user-guide/netx-events/image161.png)    | **Obtención de puerto de socket UDP** (*nx_udp_socket_port_get*) |
| ![Icono de recepción de socket U D P](./media/user-guide/netx-events/image162.png)    | **Recepción de socket UDP** (*nx_udp_socket_receive*) |
| ![Icono de notificación de recepción de socket U D P](./media/user-guide/netx-events/image163.png)    | **Notificación de recepción de socket UDP** (*nx_udp_socket_receive_notify*) |
| ![Icono de envío de socket U D P](./media/user-guide/netx-events/image164.png)    | **Envío de socket UDP** (*nx_udp_socket_send*) |
| ![Icono de desenlace de socket U D P](./media/user-guide/netx-events/image165.png)    | **Desenlace de socket UDP** (*nx_udp_socket_unbind*) |
| ![Icono de extracción de origen de U D P](./media/user-guide/netx-events/image166.png)    | **Extracción de origen de UDP** (*nx_udp_source_extract*) |

## <a name="event-descriptions"></a>Descripciones de eventos

En las secciones siguientes se describen los eventos de seguimiento de NetX.

### <a name="internal-arp-request-receive"></a>Recepción de solicitud ARP interna 

#### <a name="internal-arp-request-receive"></a>Recepción de solicitud ARP interna

**Icono** ![Icono de recepción de solicitud A R P interna](./media/user-guide/netx-events/image1.png)

**Descripción**

Este evento representa un evento interno de recepción de solicitud ARP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de origen
- Campo de información 3: puntero al paquete
- Campo de información 4: no se usa

### <a name="internal-arp-request-send"></a>Envío de solicitud ARP interno 

#### <a name="internal-arp-request-send"></a>Envío de solicitud ARP interno

**Icono** ![Icono de envío de solicitud A R P interno](./media/user-guide/netx-events/image2.png)

**Descripción**

Este evento representa un evento interno de envío de solicitud ARP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de destino
- Campo de información 3: puntero al paquete
- Campo de información 4: no se usa

### <a name="internal-arp-response-receive"></a>Recepción de respuesta ARP interna 

#### <a name="internal-arp-request-receive"></a>Recepción de solicitud ARP interna

**Icono** ![Icono de recepción de solicitud A R P interna](./media/user-guide/netx-events/image3.png)

**Descripción**

Este evento representa un evento interno de recepción de respuesta ARP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de origen
- Campo de información 3: puntero al paquete
- Campo de información 4: no se usa

### <a name="internal-arp-response-send"></a>Envío de respuesta ARP interno 

#### <a name="internal-arp-request-send"></a>Envío de solicitud ARP interno

**Icono** ![Icono de envío de solicitud A R P interno](./media/user-guide/netx-events/image4.png)

**Descripción**

Este evento representa un evento interno de envío de respuesta de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de destino
- Campo de información 3: puntero al paquete
- Campo de información 4: no se usa

### <a name="internal-icmp-receive"></a>Recepción de ICMP interna 

#### <a name="internal-icmp-receive"></a>Recepción de ICMP interna

**Icono** ![Icono de recepción de I C M P interna](./media/user-guide/netx-events/image5.png)

**Descripción**

Este evento representa un evento interno de recepción de ICMP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de origen
- Campo de información 3: puntero al paquete
- Campo de información 4: palabra 0 del encabezado ICMP

### <a name="internal-icmp-send"></a>Envío de ICMP interno 

#### <a name="internal-icmp-send"></a>Envío de ICMP interno

**Icono** ![Icono de envío de I C M P interno](./media/user-guide/netx-events/image6.png)

**Descripción**

Este evento representa un evento interno de envío de ICMP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de destino
- Campo de información 3: puntero al paquete
- Campo de información 4: palabra 0 del encabezado ICMP

### <a name="internal-igmp-receive"></a>Recepción de IGMP interna 

#### <a name="internal-igmp-receive"></a>Recepción de IGMP interna

**Icono** ![Icono de recepción de I G M P interna](./media/user-guide/netx-events/image7.png)

**Descripción**

Este evento representa un evento interno de recepción de IGMP de NetX.

**Campos de información**

- Campo de información 1: puntero de IP
- Campo de información 2: dirección IP de origen
- Campo de información 3: puntero al paquete
- Campo de información 4: palabra 0 del encabezado IGMP

### <a name="internal-ip-receive"></a>Recepción de IP interna 

#### <a name="internal-ip-receive"></a>Recepción de IP interna

**Icono** ![Icono de recepción de I P interna](./media/user-guide/netx-events/image8.png)

**Descripción**

Este evento representa un evento interno de recepción de IP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de origen
- Campo de información 3: puntero al paquete
- Campo de información 4: longitud del paquete

### <a name="internal-ip-send"></a>Envío de IP interno

#### <a name="internal-ip-send"></a>Envío de IP interno

**Icono** ![Icono de envío de I P interno](./media/user-guide/netx-events/image9.png)

**Descripción**

Este evento representa un evento interno de envío de IP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de destino
- Campo de información 3: puntero al paquete
- Campo de información 4: longitud del paquete

### <a name="internal-tcp-data-receive"></a>Recepción de datos de TCP interna 

#### <a name="internal-tcp-data-receive"></a>Recepción de datos de TCP interna

**Icono** ![Icono de recepción de datos de T C P interna](./media/user-guide/netx-events/image10.png)

**Descripción**

Este evento representa un evento interno de recepción de datos TCP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de origen
- Campo de información 3: puntero al paquete
- Campo de información 4: número de secuencia de recepción

### <a name="internal-tcp-data-send"></a>Envío de datos de TCP interno 

#### <a name="internal-tcp-data-send"></a>Envío de datos de TCP interno

**Icono** ![Icono de envío de datos de T C P interno](./media/user-guide/netx-events/image11.png)

**Descripción**

Este evento representa un evento interno de envío de datos TCP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero al paquete
- Campo de información 4: número de secuencia de transmisión

### <a name="internal-tcp-fin-receive"></a>Recepción de TCP FIN interna 

#### <a name="internal-tcp-fin-receive"></a>Recepción de TCP FIN interna

**Icono** ![Icono de recepción de T C P F I N interna](./media/user-guide/netx-events/image12.png)

**Descripción**

Este evento representa un evento interno de recepción de TCP FIN de NetX.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero al paquete
- Campo de información 4: número de secuencia de recepción

### <a name="internal-tcp-fin-send"></a>Envío de TCP FIN interno 

#### <a name="internal-tcp-fin-send"></a>Envío de TCP FIN interno

**Icono** ![Icono de envío de T C P F I N interno](./media/user-guide/netx-events/image13.png)

**Descripción**

Este evento representa un evento interno de envío de TCP FIN de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero al paquete
- Campo de información 4: número de secuencia de transmisión

### <a name="internal-tcp-rst-receive"></a>Recepción de TCP RST interna 

#### <a name="internal-tcp-rst-receive"></a>Recepción de TCP RST interna

**Icono** ![Icono de recepción de T C P R S T interna](./media/user-guide/netx-events/image14.png)

**Descripción**

Este evento representa un evento interno de recepción de TCP RST de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero al paquete
- Campo de información 4: número de secuencia de recepción

### <a name="internal-tcp-rst-send"></a>Envío de TCP RST interno 

#### <a name="internal-tcp-rst-send"></a>Envío de TCP RST interno

**Icono** ![Icono de envío de T C P R S T interno](./media/user-guide/netx-events/image15.png)

**Descripción**

Este evento representa un evento interno de envío de TCP RST de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero al paquete
- Campo de información 4: número de secuencia de transmisión

### <a name="internal-tcp-syn-receive"></a>Recepción de TCP SYN interna 

#### <a name="internal-tcp-syn-receive"></a>Recepción de TCP SYN interna

**Icono** ![Icono de recepción de T C P S Y N interna](./media/user-guide/netx-events/image16.png)

**Descripción**

Este evento representa un evento interno de recepción de TCP SYN de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero al paquete
- Campo de información 4: número de secuencia de recepción

### <a name="internal-tcp-syn-send"></a>Envío de TCP SYN interno 

#### <a name="internal-tcp-syn-send"></a>Envío de TCP SYN interno

**Icono** ![Icono de envío de T C P S Y N interno](./media/user-guide/netx-events/image17.png)

**Descripción**

Este evento representa un evento interno de envío de TCP SYN de NetX.

Campos de información 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero al paquete Campo de información 4: número de secuencia de transmisión

### <a name="internal-udp-receive"></a>Recepción de UDP interna 

#### <a name="internal-udp-receive"></a>Recepción de UDP interna

**Icono** ![Icono de recepción de U D P interna](./media/user-guide/netx-events/image18.png)

**Descripción**

Este evento representa un evento interno de recepción de UDP de NetX.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero al paquete
- Campo de información 4: palabra 0 del encabezado UDP

### <a name="internal-udp-send"></a>Envío de UDP interno 

#### <a name="internal-udp-send"></a>Envío de UDP interno

**Icono** ![Icono de envío de U D P interno](./media/user-guide/netx-events/image19.png)

**Descripción**

Este evento representa un evento interno de envío de UDP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero al paquete
- Campo de información 4: palabra 0 del encabezado UDP

### <a name="internal-rarp-receive"></a>Recepción de RARP interna 

#### <a name="internal-rarp-receive"></a>Recepción de RARP interna 

**Icono** ![Icono de recepción de R A R P interna](./media/user-guide/netx-events/image20.png)

**Descripción**

Este evento representa un evento interno de recepción de RARP de NetX.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de destino
- Campo de información 3: puntero al paquete
- Campo de información 4: palabra 1 del encabezado RARP

### <a name="internal-rarp-send"></a>Envío de RARP interno 

#### <a name="internal-rarp-send"></a>Envío de RARP interno 

**Icono** ![Icono de envío de R A R P interno](./media/user-guide/netx-events/image21.png)

**Descripción**

Este evento representa un evento interno de envío de RARP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de destino
- Campo de información 3: puntero al paquete
- Campo de información 4: palabra 1 del encabezado RARP

### <a name="internal-tcp-retry"></a>Reintento de TCP interno 

#### <a name="internal-tcp-retry"></a>Reintento de TCP interno 

**Icono** ![Icono de reintento de T C P interno](./media/user-guide/netx-events/image22.png)

**Descripción**

Este evento representa un evento interno de reintento de TCP de NetX.

**Campos de información**
- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero al paquete
- Campo de información 4: número de reintentos

### <a name="internal-tcp-state-change"></a>Cambio de estado de TCP interno 

#### <a name="internal-tcp-state-change"></a>Cambio de estado de TCP interno 

**Icono** ![Icono de cambio de estado de T C P interno](./media/user-guide/netx-events/image23.png)

**Descripción**

Este evento representa un evento interno de cambio de estado de socket TCP de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: estado anterior
- Campo de información 4: nuevo estado

### <a name="internal-io-driver-packet-send"></a>Envío de paquete de controladores de E/S interno 

#### <a name="internal-io-driver-packet-send"></a>Envío de paquete de controladores de E/S interno

**Icono** ![Icono de envío de paquete de controladores de E/S interno](./media/user-guide/netx-events/image24.png)

**Descripción**

Este evento representa un evento interno de envío de paquete de controladores de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al paquete
- Campo de información 3: tamaño del paquete
- Campo de información 4: no se usa

### <a name="internal-io-driver-initialize"></a>Inicialización de controlador de E/S interna 

#### <a name="internal-io-driver-initialize"></a>Inicialización de controlador de E/S interna

**Icono** ![Icono de inicialización de controlador de E/S interna](./media/user-guide/netx-events/image25.png)

**Descripción**

Este evento representa un evento interno de inicialización del controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-link-enable"></a>Habilitación del vínculo de controlador de E/S interna 

#### <a name="internal-io-driver-link-enable"></a>Habilitación del vínculo de controlador de E/S interna

**Icono** ![Icono de habilitación del vínculo de controlador de E/S interna](./media/user-guide/netx-events/image26.png)

**Descripción**

Este evento representa un evento interno de habilitación del vínculo de controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-link-disable"></a>Deshabilitación del vínculo de controlador de E/S interna 

#### <a name="internal-io-driver-link-disable"></a>Deshabilitación del vínculo de controlador de E/S interna

**Icono** ![Icono de deshabilitación del vínculo de controlador de E/S interna](./media/user-guide/netx-events/image27.png)

**Descripción**

Este evento representa un evento interno de deshabilitación del vínculo de controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-packet-broadcast"></a>Difusión del paquete de controladores de E/S interna 

#### <a name="internal-io-driver-packet-broadcast"></a>Difusión del paquete de controladores de E/S interna

**Icono** ![Icono de difusión de paquete de controladores de E/S interna](./media/user-guide/netx-events/image28.png)

**Descripción**

Este evento representa un evento interno de difusión del paquete de controladores de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al paquete
- Campo de información 3: tamaño del paquete
- Campo de información 4: no se usa

### <a name="internal-io-driver-arp-send"></a>Envío de ARP del controlador de E/S interno 

#### <a name="internal-io-driver-arp-send"></a>Envío de ARP del controlador de E/S interno

**Icono** ![Icono de envío de A R P del controlador de E/S interno](./media/user-guide/netx-events/image29.png)

**Descripción**

Este evento representa un evento interno de envío de ARP del controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al paquete
- Campo de información 3: tamaño del paquete
- Campo de información 4: no se usa

### <a name="internal-io-driver-arp-response-send"></a>Envío de respuesta ARP del controlador de E/S interno 

#### <a name="internal-io-driver-arp-response-send"></a>Envío de respuesta ARP del controlador de E/S interno

**Icono** ![Icono de envío de respuesta A R P del controlador de E/S interno](./media/user-guide/netx-events/image30.png)

**Descripción**

Este evento representa un evento interno de envío de respuesta ARP del controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al paquete
- Campo de información 3: tamaño del paquete
- Campo de información 4: no se usa

### <a name="internal-io-driver-rarp-send"></a>Envío de RARP del controlador de E/S interno 

#### <a name="internal-io-driver-rarp-send"></a>Envío de RARP del controlador de E/S interno

**Icono** ![Icono de envío de R A R P del controlador de E/S interno](./media/user-guide/netx-events/image31.png)

**Descripción**

Este evento representa un evento interno de envío de RARP del controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al paquete
- Campo de información 3: tamaño del paquete
- Campo de información 4: no se usa

### <a name="internal-io-driver-multicast-join"></a>Combinación de multidifusión del controlador de E/S interna 

#### <a name="internal-io-driver-multicast-join"></a>Combinación de multidifusión del controlador de E/S interna

**Icono** ![Icono de combinación de multidifusión del controlador de E/S interna](./media/user-guide/netx-events/image32.png)

**Descripción**

Este evento representa un evento interno de combinación de multidifusión del controlador de E/S de NetX.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-multicast-leave"></a>Salida de multidifusión del controlador de E/S interna 

#### <a name="internal-io-driver-multicast-leave"></a>Salida de multidifusión del controlador de E/S interna

**Icono** ![Icono de salida de multidifusión del controlador de E/S interna](./media/user-guide/netx-events/image33.png)

**Descripción**

Este evento representa un evento interno de salida de multidifusión del controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-get-status"></a>Obtención de estado del controlador de E/S interna 

#### <a name="internal-io-driver-get-status"></a>Obtención de estado del controlador de E/S interna

**Icono** ![Icono de obtención de estado del controlador de E/S interna](./media/user-guide/netx-events/image34.png)

**Descripción**

Este evento representa un evento interno de obtención de estado del controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-get-speed"></a>Obtención de velocidad del controlador de E/S interna 

#### <a name="internal-io-driver-get-speed"></a>Obtención de velocidad del controlador de E/S interna

**Icono** ![Icono de obtención de velocidad del controlador de E/S interna](./media/user-guide/netx-events/image35.png)

**Descripción**

Este evento representa un evento interno de obtención de velocidad del controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-get-duplex-type"></a>Obtención de tipo dúplex del controlador de E/S interna 

#### <a name="internal-io-driver-get-duplex-type"></a>Obtención de tipo dúplex del controlador de E/S interna

**Icono** ![Icono de obtención de tipo dúplex del controlador de E/S interna](./media/user-guide/netx-events/image36.png)

**Descripción**

Este evento representa un evento interno de obtención de tipo dúplex del controlador de E/S de NetX.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-get-error-count"></a>Obtención de número de errores del controlador de E/S interna

#### <a name="internal-io-driver-get-error-count"></a>Obtención de número de errores del controlador de E/S interna

**Icono** ![Icono de obtención de número de errores del controlador de E/S interna](./media/user-guide/netx-events/image37.png)

**Descripción**

Este evento representa un evento interno de obtención de número de errores del controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-get-rx-count"></a>Obtención de número de RX del controlador de E/S interna 

#### <a name="internal-io-driver-get-rx-count"></a>Obtención de número de RX del controlador de E/S interna

**Icono** ![Icono de obtención de número de R X del controlador de E/S interna](./media/user-guide/netx-events/image38.png)

**Descripción**

Este evento representa un evento interno de obtención de número de RX del controlador de E/S de NetX.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-get-tx-count"></a>Obtención de número de TX del controlador de E/S interna 

#### <a name="internal-io-driver-get-tx-count"></a>Obtención de número de TX del controlador de E/S interna

**Icono** ![Icono de obtención de número de T X del controlador de E/S interna](./media/user-guide/netx-events/image39.png)

**Descripción**

Este evento representa un evento interno de obtención de número de TX del controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-get-allocation-errors"></a>Obtención de errores de asignación del controlador de E/S interna 

#### <a name="internal-io-driver-get-allocation-errors"></a>Obtención de errores de asignación del controlador de E/S interna

**Icono** ![Icono de obtención de errores de asignación del controlador de E/S interna](./media/user-guide/netx-events/image40.png)

**Descripción**

Este evento representa un evento interno de obtención de errores de asignación del controlador de E/S de NetX.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-un-initialize"></a>Anulación de inicialización del controlador de E/S interna 

#### <a name="internal-io-driver-un-initialize"></a>Anulación de inicialización del controlador de E/S interna 

**Icono** ![Icono de anulación de inicialización del controlador de E/S interna](./media/user-guide/netx-events/image41.png)

**Descripción**

Este evento representa un evento interno de anulación de inicialización del controlador de E/S de NetX.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="internal-io-driver-deferred-processing"></a>Procesamiento diferido del controlador de E/S interno 

#### <a name="internal-io-driver-deferred-processing"></a>Procesamiento diferido del controlador de E/S interno 

**Icono** ![Icono de procesamiento diferido del controlador de E/S interno](./media/user-guide/netx-events/image42.png)

**Descripción**

Este evento representa un evento interno de procesamiento diferido del controlador de E/S de NetX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al paquete
- Campo de información 3: longitud del paquete
- Campo de información 4: no se usa

### <a name="arp-dynamic-entries-invalidate"></a>Invalidación de entradas dinámicas de ARP 

#### <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

**Icono** ![Icono de invalidación de entradas dinámicas de A R P](./media/user-guide/netx-events/image43.png)

**Descripción**

Este evento representa la invalidación de todas las entradas dinámicas de ARP por medio de nx_arp_dynamic_entries_invalidate.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: entradas invalidadas
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="arp-dynamic-entry-set"></a>Establecimiento de entrada dinámica de ARP 

#### <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

**Icono** ![Icono de establecimiento de entrada dinámica de A R P](./media/user-guide/netx-events/image44.png)

**Descripción**

Este evento representa la configuración de una entrada dinámica de ARP por medio de nx_arp_dynamic_entry_set.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP
- Campo de información 3: dirección física (MSW)
- Campo de información 4: dirección física (LSW)

### <a name="arp-enable"></a>Habilitación de ARP 

#### <a name="nx_arp_enable"></a>nx_arp_enable

**Icono** ![Icono de habilitación de A R P](./media/user-guide/netx-events/image45.png)

**Descripción**

Este evento representa la habilitación de ARP por medio de nx_arp_enable.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero a la memoria caché de ARP
- Campo de información 3: tamaño de la memoria caché de ARP
- Campo de información 4: no se usa

### <a name="arp-gratuitous-send"></a>Envío gratuito de ARP 

#### <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

**Icono** ![Icono de envío gratuito de A R P](./media/user-guide/netx-events/image46.png)

**Descripción**

Este evento representa un envío gratuito de ARP por medio de nx_arp_gratuitous_send.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="arp-hardware-address-find"></a>Búsqueda de la dirección de hardware de ARP 

#### <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

**Icono** ![Icono de búsqueda de dirección de hardware de A R P](./media/user-guide/netx-events/image47.png)

**Descripción**

Este evento representa la búsqueda de una dirección física por medio de nx_arp_hardware_address_find.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP
- Campo de información 3: dirección física (MSW)
- Campo de información 4: dirección física (LSW)

### <a name="arp-information-get"></a>Obtención de información de ARP 

#### <a name="nx_arp_info_get"></a>nx_arp_info_get

**Icono** ![Icono de obtención de información de A R P](./media/user-guide/netx-events/image48.png)

**Descripción**

Este evento representa la obtención de información por medio de nx_arp_info_get.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: ARP enviados
- Campo de información 3: respuestas ARP
- Campo de información 4: ARP recibidos

### <a name="arp-ip-address-find"></a>Búsqueda de dirección IP de ARP 

#### <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

**Icono** ![Icono de búsqueda de dirección I P de A R P](./media/user-guide/netx-events/image49.png)

**Descripción**

Este evento representa la búsqueda de una dirección IP asociada a la dirección física proporcionada por medio de nx_arp_ip_address_find.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP
- Campo de información 3: dirección física (MSW)
- Campo de información 4: dirección física (LSW)

### <a name="arp-static-entry-create"></a>Creación de entrada estática de ARP 

#### <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

**Icono** ![Icono de creación de entrada estática de A R P](./media/user-guide/netx-events/image50.png)

**Descripción**

Este evento representa la creación de una entrada estática de ARP por medio de nx_arp_static_entry_create.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP
- Campo de información 3: dirección física (MSW)
- Campo de información 4: dirección física (LSW)

### <a name="arp-static-entries-delete"></a>Eliminación de entradas estáticas de ARP 

#### <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

**Icono** ![Icono de eliminación de entradas estáticas de A R P](./media/user-guide/netx-events/image51.png)

**Descripción**

Este evento representa la eliminación de todas las entradas estáticas de ARP por medio de nx_arp_static_entries_delete.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: entradas eliminadas
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="arp-static-entry-delete"></a>Eliminación de entrada estática de ARP 

### <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

**Icono** ![Icono de eliminación de entrada estática de A R P](./media/user-guide/netx-events/image52.png)

**Descripción**

Este evento representa la eliminación de una entrada estática de ARP por medio de nx_arp_static_entry_delete.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP
- Campo de información 3: dirección física (MSW)
- Campo de información 4: dirección física (LSW)

### <a name="duo-cache-entry-delete"></a>Eliminación de entrada de caché doble 

#### <a name="nxd_und_cache_entry_delete"></a>nxd_und_cache_entry_delete

**Icono** ![Icono de eliminación de entrada de caché doble](./media/user-guide/netx-events/image53.png)

**Descripción**

Este evento representa la eliminación de una entrada en la tabla de caché vecina por medio de nx_udp_socket_create.

**Campos de información** 

- Campo de información 1: cuarta palabra (menos significativa) de la dirección local del vínculo IPv6 que se va a eliminar
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="duo-cache-entry-set"></a>Establecimiento de entrada de caché doble 

#### <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set

**Icono** ![Icono de establecimiento de entrada de caché doble](./media/user-guide/netx-events/image54.png)

**Descripción**

Este evento representa la creación de una entrada de caché y su adición a la tabla de caché vecina por medio de nxd_nd_cache_entry_set.

**Campos de información** 

- Campo de información 1: cuarta palabra (menos significativa) de la dirección IPv6 que se va a agregar
- Campo de información 2: MSB de la dirección física
- Campo de información 3: LSB de la dirección física
- Campo de información 4: no se usa

### <a name="duo-cache-invalidate"></a>Invalidación de caché doble 

#### <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate

**Icono** ![Icono de invalidación de caché doble](./media/user-guide/netx-events/image55.png)

**Descripción**

Este evento representa la invalidación de toda la tabla de caché vecina por medio de nxd_nd_cache_invalidate.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="duo-cache-ip-address-find"></a>Búsqueda de dirección IP de caché doble 

#### <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find

**Icono** ![Icono de búsqueda de dirección I P de caché doble](./media/user-guide/netx-events/image56.png)

**Descripción**

Este evento representa la recuperación de una dirección IP que coincide con la dirección física proporcionada de la tabla de caché por medio de nxd_nd_cache_ip_address_find.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: cuarta palabra (menos significativa) de la dirección IPv6
- Campo de información 3: MSB de la dirección física
- Campo de información 4: LSB de la dirección física

### <a name="duo-icmp-enable"></a>Habilitación de ICMP doble 

#### <a name="nxd_icmp_enable"></a>nxd_icmp_enable

**Icono** ![Icono de habilitación de I C M P doble](./media/user-guide/netx-events/image57.png)

**Descripción**

Este evento representa la habilitación de los servicios ICMPv4 y ICMPv6 en la instancia de IP especificada por medio de nxd_icmp_enable.

**Campos de información**
- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="duo-icmp-ping"></a>Ping de ICMP doble 

#### <a name="nxd_icmp_ping"></a>nxd_icmp_ping

**Icono** ![Icono de ping de I C M P doble](./media/user-guide/netx-events/image58.png)

**Descripción**

Este evento representa el envío de un ping (solicitud de eco) a un host IPv6 por medio de nxd_icmp_ping.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IPv6
- Campo de información 3: puntero a los datos de eco
- Campo de información 4: tamaño de los datos de eco

### <a name="duo-ip-max-payload-size-find"></a>Búsqueda de tamaño máximo de carga de IP doble 

#### <a name="nxd_ip_max_payload_size"></a>nxd_ip_max_payload_size

**Icono** ![Icono de búsqueda de tamaño máximo de carga de I P doble](./media/user-guide/netx-events/image59.png)

**Descripción**

Este evento calcula la carga máxima que el paquete especificado puede llevar a cabo sin necesidad de fragmentación.

**Campos de información**

- Campo de información 1: puntero al socket
- Campo de información 2: dirección IP del nodo del mismo nivel
- Campo de información 3: puerto del nodo del mismo nivel Campo de información 4: no se usa

### <a name="duo-ip-raw-packet-send"></a>Envío de paquete sin formato de IP doble 

#### <a name="nxd_ip_max_packet_send"></a>nxd_ip_max_packet_send

**Icono** ![Icono de envío de paquete sin formato de I P doble](./media/user-guide/netx-events/image60.png)

**Descripción**

Este evento representa el envío de un paquete de IP sin formato desde la interfaz de red especificada a la dirección de destino IP indicada por medio de nxd_ip_raw_packet_send.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al paquete que se va a enviar
- Campo de información 3: puntero a la dirección de destino
- Campo de información 4: protocolo del paquete

### <a name="duo-ipv6-default-router-add"></a>Adición de enrutador predeterminado de IPv6 doble 

#### <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add

**Icono** ![Icono de adición de enrutador predeterminado de I P v 6 doble](./media/user-guide/netx-events/image61.png)

**Descripción**

Este evento representa la adición de un enrutador predeterminado a la tabla de enrutamiento IPv6 de la instancia de IP por medio de nxd_ipv6_default_router_add.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección de red de destino
- Campo de información 3: información de tiempo de vida
- Campo de información 4: no se usa

### <a name="duo-ipv6-default-router-delete"></a>Eliminación de enrutador predeterminado de IPv6 doble 

#### <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete

**Icono** ![Icono de eliminación de enrutador predeterminado de I P v 6 doble](./media/user-guide/netx-events/image62.png)

**Descripción**

Este evento representa la eliminación de un enrutador predeterminado de la tabla de enrutamiento IPv6 de la instancia de IP por medio de nxd_ipv6_default_router_delete.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: cuarta palabra (menos significativa) de la dirección IPv6 del enrutador predeterminado
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="duo-ipv6-enable"></a>Habilitación de IPv6 doble 

#### <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable

**Icono** ![Icono de habilitación de I P v 6 doble](./media/user-guide/netx-events/image63.png)

**Descripción**

Este evento representa la habilitación de servicios IPv6 en la instancia de IP proporcionada por medio de nxd_ipv6_enable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="duo-ipv6-global-address-get"></a>Obtención de dirección global de IPv6 doble 

#### <a name="nxd_ipv6_global_address_get"></a>nxd_ipv6_global_address_get

**Icono** ![Icono de obtención de dirección global de I P v 6 doble](./media/user-guide/netx-events/image64.png)

**Descripción**

Este evento representa la recuperación de la dirección IP global (principal) de la instancia de IP que se encuentra en el índice 1 de la tabla de interfaces de instancia de IP por medio de nxd_ipv6_global_address_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: cuarta palabra (menos significativa) de la dirección global
- Campo de información 3: longitud del prefijo de la dirección IPv6
- Campo de información 4: índice en la tabla de interfaces de IP (1).

### <a name="duo-ipv6-global-address-set"></a>Establecimiento de dirección global de IPv6 doble 

#### <a name="nxd_ipv6_global_address_set"></a>nxd_ipv6_global_address_set

**Icono** ![Icono de establecimiento de dirección global de I P v 6 doble](./media/user-guide/netx-events/image65.png)

**Descripción**

Este evento representa el establecimiento de la dirección IP global (principal) en la instancia de IP que se encuentra en el índice 1 de la tabla de interfaces de instancia de IP por medio de nxd_ipv6_global_address_set.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: cuarta palabra (menos significativa) de la dirección global
- Campo de información 3: longitud del prefijo de la dirección IPv6
- Campo de información 4: índice en la tabla de interfaces de IP (1)

### <a name="duo-ipv6-initiate-dad-process"></a>Inicio de proceso DAD de IPv6 doble 

#### <a name="nxd_ipv6_initiate_dad_process"></a>nxd_ipv6_initiate_dad_process

**Icono** ![Icono de inicio de proceso D A D de I P v 6 doble](./media/user-guide/netx-events/image66.png)

**Descripción**

Este evento representa el inicio del proceso de detección de direcciones duplicadas (DAD) cuando se asigna un vínculo local o una dirección de interfaz de IP a la instancia de IP por medio de nxd_ipv6_initiate_dad_process.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="duo-ipv6-interface-address-get"></a>Obtención de dirección de interfaz de IPv6 doble 

#### <a name="nxd_ipv6_interface_address_get"></a>nxd_ipv6_interface_address_get

**Icono** ![Icono de obtención de dirección de interfaz de I P v 6 doble](./media/user-guide/netx-events/image67.png)

**Descripción**

Este evento representa la recuperación de la dirección IP y el prefijo en el índice especificado de la tabla de direcciones de interfaz de instancia IP por medio de nxd_ipv6_interface_address_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: cuarta palabra (menos significativa) de la dirección IPv6 que se va a devolver
- Campo de información 4: índice de la interfaz en la tabla de interfaces de instancia de IP

### <a name="duo-ipv6-interface-address-set"></a>Establecimiento de dirección de interfaz de IPv6 doble 

### <a name="nxd_ipv6_interface_address_set"></a>nxd_ipv6_interface_address_set

**Icono** ![Icono de establecimiento de dirección de interfaz de I P v 6 doble](./media/user-guide/netx-events/image68.png)

**Descripción**

Este evento representa el establecimiento de la dirección IP y el prefijo en el índice especificado de la tabla de direcciones de interfaz de instancia IP por medio de nxd_ipv6_interface_address_set. No se permite en el índice cero (dirección local del vínculo).

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: cuarta palabra (menos significativa) de la dirección IPv6 que se va a devolver
- Campo de información 3: longitud del prefijo
- Campo de información 4: índice de la interfaz en la tabla de interfaces de instancia de IP

### <a name="duo-ipv6-link-local-address-get"></a>Obtención de dirección local de vínculo de IPv6 doble 

#### <a name="nxd_ipv6_linklocal_address_get"></a>nxd_ipv6_linklocal_address_get

**Icono** ![Icono de obtención de dirección local de vínculo de I P v 6 doble](./media/user-guide/netx-events/image69.png)

**Descripción**

Este evento representa la recuperación de la dirección local del vínculo de la instancia de IP especificada por medio de nxd_ipv6_linklocal_address_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: cuarta palabra (menos significativa) de la dirección local del vínculo de IPv6
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="duo-ipv6-link-local-address-set"></a>Establecimiento de dirección local de vínculo de IPv6 doble 

#### <a name="nxd_ipv6_linklocal_address_set"></a>nxd_ipv6_linklocal_address_set

**Icono** ![Icono de establecimiento de dirección local de vínculo de I P v 6 doble](./media/user-guide/netx-events/image70.png)

**Descripción**

Este evento representa el establecimiento de la dirección local del vínculo de la instancia de IP por medio de nxd_ipv6_linklocal_address_set.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: cuarta palabra (menos significativa) de la dirección local del vínculo IPv6
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="duo-ipv6-raw-packet-send"></a>Envío de paquete sin formato de IPv6 doble 

#### <a name="nxd_ipv6_raw_packet_send"></a>nxd_ipv6_raw_packet_send

**Icono** ![Icono de envío de paquete sin formato de I P v 6 doble](./media/user-guide/netx-events/image71.png)

**Descripción**

Este evento representa el envío de un paquete IP sin formato a través de la interfaz IP principal al destino especificado por medio de nxd_ip_raw_packet_send.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al paquete que se va a enviar
- Campo de información 3: dirección IP de destino
- Campo de información 4: no se usa

### <a name="duo-tcp-socket-peer-info-get"></a>Obtención de información de nodo del mismo nivel de socket de TCP doble 

#### <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get

**Icono** ![Icono de obtención de información de nodo del mismo nivel de socket de T C P doble](./media/user-guide/netx-events/image72.png)

**Descripción**

Este evento extrae los datos del remitente de un paquete TCP recibido en el socket especificado. Devuelve la dirección IP y el puerto del remitente.

**Campos de información**

- Campo de información 1: puntero al socket
- Campo de información 2: dirección IP del nodo del mismo nivel
- Campo de información 3: puerto del nodo del mismo nivel
- Campo de información 4: el bit menos significativo de la dirección IP de 32 bits

### <a name="duo-tcp-socket-set-interface"></a>Establecimiento de interfaz de socket de TCP doble 

#### <a name="nxd_tcp_socket_set_interface"></a>nxd_tcp_socket_set_interface

**Icono** ![Icono de establecimiento de interfaz de socket de T C P doble](./media/user-guide/netx-events/image73.png)

**Descripción**

Este evento representa el establecimiento de la interfaz de socket saliente después de que un cliente se conecta con un servidor TCP en la dirección IP del servidor especificada por medio de nxd_tcp_client_socket_connect.

**Campos de información** 

- Campo de información 1: puntero al socket TCP
- Campo de información 2: identificador de la interfaz
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="duo-udp-socket-send"></a>Envío de socket de UDP doble 

#### <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send

**Icono** ![Icono de envío de socket de U D P doble](./media/user-guide/netx-events/image74.png)

**Descripción**

Este evento representa el envío de un paquete UDP a través del socket especificado con la dirección IP y el puerto de entrada por medio de nxd_udp_socket_send.

**Campos de información** 

- Campo de información 1: puntero al socket UDP
- Campo de información 2: puntero al paquete UDP
- Campo de información 3: longitud del paquete
- Campo de información 4: no se usa


### <a name="duo-udp-socket-set-interface"></a>Establecimiento de interfaz de socket de UDP doble 

#### <a name="nxd_udp_socket_set_interface"></a>nxd_udp_socket_set_interface

**Icono** ![Icono de establecimiento de interfaz de socket de U D P doble](./media/user-guide/netx-events/image75.png)

**Descripción**

Este evento representa el establecimiento de la interfaz de salida del socket UDP especificado en la interfaz correspondiente al identificador de interfaz de entrada por medio de nxd_udp_socket_set_interface.

**Campos de información** 

- Campo de información 1: puntero al socket UDP
- Campo de información 2: identificador de la interfaz
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="duo-udp-source-extract"></a>Extracción de origen de UDP doble 

#### <a name="nxd_udp_socket_extract"></a>nxd_udp_socket_extract

**Icono** ![Icono de extracción de origen de U D P doble](./media/user-guide/netx-events/image76.png)

**Descripción**

Este evento representa la extracción de la dirección IP y el puerto de origen de un paquete recibido (ya sea IPv4 o IPv6). Si es IPv6, la cuarta palabra (menos significativa) de la dirección IP se devuelve por medio de nxd_udp_source_extract.

**Campos de información**

- Campo de información 1: puntero al paquete
- Campo de información 2: versión de IP
- Campo de información 3: dirección IP de origen (IPv4 o IPv6)
- Campo de información 4: puerto de origen

### <a name="icmp-enable"></a>Habilitación de ICMP 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Icono** ![Icono de habilitación de I C M P](./media/user-guide/netx-events/image77.png)

**Descripción**

Este evento representa la habilitación de ICMP por medio de nx_icmp_enable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="icmp-information-get"></a>Obtención de información de ICMP 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Icono** ![Icono de obtención de información de I C M P](./media/user-guide/netx-events/image78.png)

**Descripción**

Este evento representa la obtención de información por medio de nx_icmp_info_get.

**Campos de información**
- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: pings enviados
- Campo de información 3: respuestas de ping
- Campo de información 4: pings recibidos

### <a name="icmp-ping"></a>Ping de ICMP 

#### <a name="nx_icmp_ping"></a>nx_icmp_ping

**Icono** ![Icono de ping de I C M P](./media/user-guide/netx-events/image79.png)

**Descripción**

Este evento representa el envío de ping a una dirección IP de destino por medio de nx_icmp_ping.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP
- Campo de información 3: puntero a los datos
- Campo de información 4: tamaño de los datos

### <a name="igmp-enable"></a>Habilitación de IGMP 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Icono** ![Icono de habilitación de I G M P](./media/user-guide/netx-events/image80.png)

**Descripción**

Este evento representa la habilitación de IGMP por medio de nx_igmp_enable.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="igmp-information-get"></a>Obtención de información de IGMP 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Icono** ![Icono de obtención de información de I G M P](./media/user-guide/netx-events/image81.png)

**Descripción**

Este evento representa la obtención de información por medio de nx_igmp_info_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: informes enviados
- Campo de información 3: consultas recibidas
- Campo de información 4: grupos combinados

### <a name="igmp-loopback-disable"></a>Deshabilitación de bucle invertido de IGMP 

#### <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

**Icono** ![Icono de deshabilitación de bucle invertido de I G M P](./media/user-guide/netx-events/image82.png)

**Descripción**

Este evento representa la deshabilitación del bucle invertido de IGMP por medio de nx_igmp_loopback_disable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="igmp-loopback-enable"></a>Habilitación de bucle invertido de IGMP 

#### <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

**Icono** ![Icono de habilitación de bucle invertido de I G M P](./media/user-guide/netx-events/image83.png)

**Descripción**

Este evento representa la habilitación del bucle invertido de IGMP por medio de nx_igmp_loopback_enable.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="igmp-multicast-join"></a>Combinación de multidifusión de IGMP 

#### <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

**Icono** ![Icono de combinación de multidifusión de I G M P](./media/user-guide/netx-events/image84.png)

**Descripción**

Este evento representa la combinación de un grupo de multidifusión por medio de nx_igmp_multicast_join.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP del grupo
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="igmp-multicast-leave"></a>Salida de multidifusión de IGMP 

#### <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

**Icono** ![Icono de salida de multidifusión de I G M P](./media/user-guide/netx-events/image85.png)

**Descripción**

Este evento representa la salida de un grupo de multidifusión por medio de nx_igmp_multicast_leave.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP del grupo
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="ip-address-change-notify"></a>Notificación de cambio de dirección IP 

#### <a name="nx_ip_address_change_notify"></a>nx_ip_address_change_notify

**Icono** ![Icono de notificación de cambio de dirección I P](./media/user-guide/netx-events/image86.png)

**Descripción**

Este evento representa el registro de la notificación de cambio de IP por medio de nx_ip_address_change_notify.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero a la función de devolución de llamada
- Campo de información 3: puntero a información adicional
- Campo de información 4: no se usa

### <a name="ip-address-get"></a>Obtención de dirección IP 

#### <a name="nx_ip_address_get"></a>nx_ip_address_get

**Icono** ![Icono de obtención de dirección I P](./media/user-guide/netx-events/image87.png)

**Descripción**

Este evento representa la obtención de la dirección IP por medio de nx_ip_address_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP
- Campo de información 3: máscara de red
- Campo de información 4: no se usa

### <a name="ip-address-set"></a>Establecimiento de dirección IP 

#### <a name="nx_ip_address_set"></a>nx_ip_address_set

**Icono** ![Icono de establecimiento de dirección I P](./media/user-guide/netx-events/image88.png)

**Descripción**

Este evento representa el establecimiento de la dirección IP por medio de nx_ip_address_set.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP
- Campo de información 3: máscara de red
- Campo de información 4: no se usa

### <a name="ip-create"></a>Creación de IP 

#### <a name="nx_ip_create"></a>nx_ip_create

**Icono** ![Icono de creación de I P](./media/user-guide/netx-events/image89.png)

**Descripción**

Este evento representa la creación de una instancia de IP por medio de nx_ip_create.

**Campos de información** 
- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP
- Campo de información 3: máscara de red
- Campo de información 4: puntero al grupo de paquetes predeterminado

### <a name="ip-delete"></a>Eliminación de IP 

#### <a name="nx_ip_delete"></a>nx_ip_delete

**Icono** ![Icono de eliminación de I P](./media/user-guide/netx-events/image90.png)

**Descripción**

Este evento representa la eliminación de una instancia de IP por medio de nx_ip_delete.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="ip-driver-direct-command"></a>Comando directo de controlador de IP 

#### <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

**Icono** ![Icono de comando directo de controlador de I P](./media/user-guide/netx-events/image91.png)

**Descripción**

Este evento representa un comando de controlador de E/S directo por medio de nx_ip_driver_direct_command.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: comando del controlador
- Campo de información 3: valor devuelto
- Campo de información 4: no se usa

### <a name="ip-forwarding-disable"></a>Deshabilitación del reenvío de IP 

#### <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

**Icono** ![Icono de deshabilitación de reenvío de I P](./media/user-guide/netx-events/image92.png)

**Descripción**

Este evento representa la deshabilitación del reenvío IP por medio de nx_ip_forwarding_disable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="ip-forwarding-enable"></a>Habilitación del reenvío de IP 

#### <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

**Icono** ![Icono de habilitación de reenvío de I P](./media/user-guide/netx-events/image93.png)

**Descripción**

Este evento representa la habilitación del reenvío de IP por medio de nx_ip_forwarding_enable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="ip-fragment-disable"></a>Deshabilitación de fragmento de IP 

#### <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

**Icono** ![Icono de deshabilitación de fragmento de I P](./media/user-guide/netx-events/image94.png)

**Descripción**

Este evento representa la deshabilitación de la fragmentación de IP por medio de nx_ip_fragment_disable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="ip-fragment-enable"></a>Habilitación de fragmento de IP 

#### <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

**Icono** ![Icono de habilitación de fragmento de I P](./media/user-guide/netx-events/image95.png)

**Descripción**

Este evento representa la habilitación de la fragmentación de IP por medio de nx_ip_fragment_enable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="ip-gateway-address-set"></a>Establecimiento de dirección de puerta de enlace de IP 

#### <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

**Icono** ![Icono de establecimiento de dirección de puerta de enlace de I P](./media/user-guide/netx-events/image96.png)

**Descripción**

Este evento representa el establecimiento de la dirección IP de puerta de enlace por medio de nx_ip_gateway_address_set.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de puerta de enlace
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="ip-information-get"></a>Obtención de información de IP 

#### <a name="nx_ip_info_get"></a>nx_ip_info_get

**Icono** ![Icono de obtención de información de I P](./media/user-guide/netx-events/image97.png)

**Descripción** Este evento representa la obtención de información de IP por medio de nx_ip_info_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: bytes de IP enviados
- Campo de información 3: bytes de IP recibidos
- Campo de información 4: paquetes de IP descartados

### <a name="ip-interface-attach"></a>Asociación de interfaz de IP 

#### <a name="nx_interface_attach"></a>nx_interface_attach

**Icono** ![Icono de asociación de interfaz de I P](./media/user-guide/netx-events/image98.png)

**Descripción**

Este evento representa la asociación de una interfaz de red secundaria a la instancia de IP por medio de nx_ip_interface_attach.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de la interfaz
- Campo de información 3: índice en la tabla de interfaces de IP
- Campo de información 4: no se usa

### <a name="ip-interface-info-get"></a>Obtención de información de interfaz de IP 

#### <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

**Icono** ![Icono de obtención de información de interfaz de I P](./media/user-guide/netx-events/image99.png)

**Descripción**

Este evento representa la recuperación de información de la interfaz de red especificada por medio de nx_ip_interface_info_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección IP de la interfaz
- Campo de información 3: MSB de la dirección MAC de la interfaz
- Campo de información 4: LSB de la dirección MAC de la interfaz

### <a name="ip-raw-packet-disable"></a>Deshabilitación de paquete sin formato de IP 

#### <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

**Icono** ![Icono de deshabilitación de paquete sin formato de I P](./media/user-guide/netx-events/image100.png)

**Descripción**

Este evento representa la deshabilitación de la comunicación de paquetes de IP sin formato por medio de nx_ip_raw_packet_disable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="ip-raw-packet-enable"></a>Habilitación de paquete sin formato de IP 

#### <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

**Icono** ![Icono de habilitación de paquete sin formato de I P](./media/user-guide/netx-events/image101.png)

**Descripción**

Este evento representa la habilitación de la comunicación de paquetes de IP sin formato por medio de nx_ip_raw_packet_enable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="ip-raw-packet-receive"></a>Recepción de paquete sin formato de IP 

#### <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

**Icono** ![Icono de recepción de paquete sin formato de I P](./media/user-guide/netx-events/image102.png)

**Descripción**

Este evento representa la recepción de un paquete de IP sin formato por medio de nx_ip_raw_packet_receive.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al paquete
- Campo de información 3: opción de espera
- Campo de información 4: no se usa

### <a name="ip-raw-packet-send"></a>Envío de paquete sin formato de IP 

#### <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

**Icono** ![Icono de envío de paquete sin formato de I P](./media/user-guide/netx-events/image103.png)

**Descripción**

Este evento representa el envío de un paquete de IP sin formato por medio de nx_ip_raw_packet_send.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al paquete
- Campo de información 3: dirección IP de destino
- Campo de información 4: tipo de servicio

### <a name="ip-static-route-add"></a>Adición de ruta estática de IP 

#### <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

**Icono** ![Icono de adición de ruta estática de I P](./media/user-guide/netx-events/image104.png)

**Descripción**

Este evento representa la adición de una ruta estática a la tabla de enrutamiento de la instancia de IP por medio de nx_ip_static_route_add.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección de red
- Campo de información 3: máscara de red
- Campo de información 4: próximo salto

### <a name="ip-static-route-delete"></a>Eliminación de ruta estática de IP 

#### <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

**Icono** ![Icono de eliminación de ruta estática de I P](./media/user-guide/netx-events/image105.png)

**Descripción**

Este evento representa la eliminación de una ruta estática de la tabla de enrutamiento de la instancia de IP por medio de nx_ip_static_route_delete.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: dirección de red
- Campo de información 3: máscara de red
- Campo de información 4: no se usa

### <a name="ip-status-check"></a>Comprobación de estado de IP 

#### <a name="nx_ip_status_check"></a>nx_ip_status_check

**Icono** ![Icono de comprobación de estado de I P](./media/user-guide/netx-events/image106.png)

**Descripción**

Este evento representa la comprobación de un estado de IP por medio de nx_ip_status_check.

Campos de información 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: estado solicitado
- Campo de información 3: estado real
- Campo de información 4: opción de espera

### <a name="ipsec-enable"></a>Habilitación de IPsec 

#### <a name="nx_ipsec_enable"></a>nx_ipsec_enable

**Icono** ![Icono de habilitación de I P SEC](./media/user-guide/netx-events/image107.png)

**Descripción**

Este evento representa la habilitación de servicios IPsec en la instancia de IP proporcionada por medio de nx_ipsec_enable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="packet-allocate"></a>Asignación de paquete 

#### <a name="nx_packet_allocate"></a>nx_packet_allocate

**Icono** ![Icono de asignación de paquete](./media/user-guide/netx-events/image108.png)

**Descripción**

Este evento representa la asignación de un paquete por medio de nx_packet_allocate.

**Campos de información**

- Campo de información 1: puntero al grupo de paquetes
- Campo de información 2: puntero al paquete asignado
- Campo de información 3: tipo de paquete
- Campo de información 4: paquetes disponibles

### <a name="packet-copy"></a>Copia de paquete 

#### <a name="nx_packet_copy"></a>nx_packet_copy

**Icono** ![Icono de copia de paquete](./media/user-guide/netx-events/image109.png)

**Descripción**

Este evento representa la copia de un paquete por medio de nx_packet_copy.

**Campos de información**

- Campo de información 2: puntero al nuevo paquete
- Campo de información 3: puntero al grupo de paquetes
- Campo de información 4: opción de espera

### <a name="packet-data-append"></a>Anexión de datos de paquete 

#### <a name="nx_packet_data_append"></a>nx_packet_data_append

**Icono** ![Icono de anexión de datos de paquete](./media/user-guide/netx-events/image110.png)

**Descripción**

Este evento representa la anexión de datos a un paquete por medio de nx_packet_data_append.

**Campos de información**

- Campo de información 1: puntero al paquete
- Campo de información 2: puntero a los datos
- Campo de información 3: tamaño de los datos
- Campo de información 4: puntero al grupo de paquetes

### <a name="packet-data-extract-offset"></a>Desplazamiento de extracción de datos de paquete 

#### <a name="nx_udp_source_extract_offset"></a>nx_udp_source_extract_offset

**Icono** ![Icono de desplazamiento de extracción de datos de paquete](./media/user-guide/netx-events/image111.png)

**Descripción**

Este evento representa la extracción de datos de un paquete a un búfer proporcionado por medio de nx_udp_source_extract_offset.

**Campos de información**

- Campo de información 1: puntero al paquete
- Campo de información 2: tamaño del búfer especificado
- Campo de información 3: número de bytes copiados
- Campo de información 4: no se usa

### <a name="packet-data-retrieve"></a>Recuperación de datos de paquete 

#### <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

**Icono** ![Icono de recuperación de datos de paquete](./media/user-guide/netx-events/image112.png)

**Descripción**

Este evento representa la recuperación de datos de un paquete por medio de nx_packet_data_retrieve.

**Campos de información** 

- Campo de información 1: puntero al paquete
- Campo de información 2: puntero al inicio del búfer
- Campo de información 3: bytes copiados
- Campo de información 4: no se usa

### <a name="packet-length-get"></a>Obtención de longitud de paquete 

#### <a name="nx_packet_length_get"></a>nx_packet_length_get

**Icono** ![Icono de obtención de longitud de paquete](./media/user-guide/netx-events/image113.png)

**Descripción**

Este evento representa la obtención de la longitud de un paquete por medio de nx_packet_length_get.

**Campos de información**

- Campo de información 1: puntero al paquete
- Campo de información 2: longitud del paquete
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="packet-pool-create"></a>Creación de grupo de paquetes 

#### <a name="nx_packet_pool_create"></a>nx_packet_pool_create

**Icono** ![Icono de creación de grupo de paquetes](./media/user-guide/netx-events/image114.png)

**Descripción**

Este evento representa la creación de un grupo de paquetes por medio de nx_packet_pool_create.

**Campos de información** 

- Campo de información 1: puntero al grupo de paquetes
- Campo de información 2: tamaño de carga del paquete
- Campo de información 3: puntero al área de memoria del grupo
- Campo de información 4: tamaño del área de memoria del grupo

### <a name="packet-pool-delete"></a>Eliminación de grupo de paquetes 

#### <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

**Icono** ![Icono de eliminación de grupo de paquetes](./media/user-guide/netx-events/image115.png)

**Descripción**

Este evento representa la eliminación de un grupo de paquetes por medio de nx_packet_pool_delete.

**Campos de información** 

- Campo de información 1: puntero al grupo de paquetes
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

#### <a name="packet-pool-information-get"></a>Obtención de información de grupo de paquetes 

#### <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

**Icono** ![Icono de obtención de información de grupo de paquetes](./media/user-guide/netx-events/image116.png)

**Descripción**

Este evento representa la obtención de información del grupo de paquetes por medio de nx_packet_pool_info_get.

**Campos de información**

- Campo de información 1: puntero al grupo de paquetes
- Campo de información 2: total de paquetes
- Campo de información 3: paquetes disponibles
- Campo de información 4: solicitudes vacías

### <a name="packet-release"></a>Liberación de paquete 

#### <a name="nx_packet_data_release"></a>nx_packet_data_release

**Icono** ![Icono de liberación de paquete](./media/user-guide/netx-events/image117.png)

**Descripción**

Este evento representa la liberación de un paquete por medio de nx_packet_release.

**Campos de información**

- Campo de información 1: puntero al paquete
- Campo de información 2: estado del paquete
- Campo de información 3: paquetes disponibles
- Campo de información 4: no se usa

### <a name="packet-transmit-release"></a>Liberación de transmisión de paquete 

#### <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

**Icono** ![Icono de liberación de transmisión de paquete](./media/user-guide/netx-events/image118.png)

**Descripción**

Este evento representa la liberación de un paquete de transmisión por medio de nx_packet_transmit_release.

**Campos de información**

- Campo de información 1: puntero al paquete
- Campo de información 2: estado del paquete
- Campo de información 3: paquetes disponibles
- Campo de información 4: no se usa

### <a name="rarp-disable"></a>Deshabilitación de RARP 

#### <a name="nx_rarp_disable"></a>nx_rarp_disable

**Icono** ![Icono de deshabilitación de R A R P](./media/user-guide/netx-events/image119.png)

**Descripción**

Este evento representa la deshabilitación de RARP por medio de nx_rarp_disable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="rarp-enable"></a>Habilitación de RARP 

#### <a name="nx_rarp_enable"></a>nx_rarp_enable

**Icono** ![Icono de habilitación de R A R P](./media/user-guide/netx-events/image120.png)

**Descripción**

Este evento representa la habilitación de RARP por medio de nx_rarp_enable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="rarp-information-get"></a>Obtención de información de RARP 

#### <a name="nx_rarp_info_get"></a>nx_rarp_info_get

**Icono** ![Icono de obtención de información de R A R P](./media/user-guide/netx-events/image121.png)

**Descripción**

Este evento representa la obtención de información de RARP por medio de nx_rarp_info_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: solicitudes enviadas
- Campo de información 3: respuestas recibidas
- Campo de información 4: respuestas no válidas

### <a name="system-initialize"></a>Inicialización del sistema 

#### <a name="nx_system_initialize"></a>nx_system_initialize

**Icono** ![Icono de inicialización del sistema](./media/user-guide/netx-events/image122.png)

**Descripción**

Este evento representa la inicialización de NetX por medio de nx_system_initialize.

**Campos de información**

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="tcp-client-socket-bind"></a>Enlace de socket de cliente TCP 

#### <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

**Icono** ![Icono de enlace de socket de cliente T C P](./media/user-guide/netx-events/image123.png)

**Descripción**

Este evento representa el enlace de un socket de cliente a un puerto por medio de nx_tcp_client_socket_bind.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puerto solicitado
- Campo de información 4: opción de espera

### <a name="tcp-client-socket-connect"></a>Conexión de socket de cliente TCP 

#### <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

**Icono** ![Icono de conexión de socket de cliente T C P](./media/user-guide/netx-events/image124.png)

**Descripción**

Este evento representa la creación de una conexión de socket de cliente por medio de nx_tcp_client_socket_connect.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: dirección IP del servidor
- Campo de información 4: puerto de servidor solicitado

### <a name="tcp-client-socket-port-get"></a>Obtención de puerto de socket de cliente TCP 

#### <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

**Icono** ![Icono de obtención de puerto de socket de cliente T C P](./media/user-guide/netx-events/image125.png)

**Descripción**

Este evento representa la obtención del número de puerto del socket de cliente por medio de nx_tcp_client_socket_port_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: número del puerto
- Campo de información 4: no se usa

### <a name="tcp-client-socket-unbind"></a>Desenlace de socket de cliente TCP 

#### <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

**Icono** ![Icono de desenlace de socket de cliente T C P](./media/user-guide/netx-events/image126.png)

**Descripción**

Este evento representa el desenlace del puerto asociado al socket por medio de nx_tcp_client_socket_unbind.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="tcp-enable"></a>Habilitación de TCP 

#### <a name="nx_tcp_enable"></a>nx_tcp_enable

**Icono** ![Icono de habilitación de T C P](./media/user-guide/netx-events/image127.png)

**Descripción**

Este evento representa la habilitación de TCP por medio de nx_tcp_enable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

###  <a name="tcp-free-port-find-tcp-free-port-find"></a>Búsqueda de puerto libre de TCP 

#### <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

**Icono** ![Icono de búsqueda de puerto libre de T C P](./media/user-guide/netx-events/image128.png)

**Descripción**

Este evento representa la búsqueda de un puerto TCP libre por medio de nx_tcp_free_port_find.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: número de puerto de inicio de búsqueda
- Campo de información 3: número de puerto libre
- Campo de información 4: no se usa

###  <a name="tcp-infomation-get"></a>Obtención de información de TCP 

#### <a name="nx_tcp_info_get"></a>nx_tcp_info_get

**Icono** ![Icono de obtención de información de T C P](./media/user-guide/netx-events/image129.png)

**Descripción**

Este evento representa la recuperación de información de TCP para la instancia de IP especificada por medio de nx_tcp_info_get.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: número de bytes enviados
- Campo de información 3: número de bytes recibidos
- Campo de información 4: número de paquetes no válidos

###  <a name="tcp-server-socket-accept"></a>Aceptación de socket de servidor TCP 

#### <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

**Icono** ![Icono de aceptación de socket de servidor T C P](./media/user-guide/netx-events/image130.png)

**Descripción**

Este evento representa la configuración del socket de servidor después de que se haya recibido una solicitud de conexión activa por medio de nx_tcp_server_socket_accept.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: opción de espera
- Campo de información 4: estado del socket

###  <a name="tcp-server-socket-listen"></a>Escucha de socket de servidor TCP 

#### <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

**Icono** ![Icono de escucha de socket de servidor T C P](./media/user-guide/netx-events/image131.png)

**Descripción**

Este evento representa el registro de una solicitud de escucha y un socket de servidor para el puerto TCP especificado por medio de nx_tcp_server_socket_listen.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: número de puerto TCP
- Campo de información 3: puntero al socket
- Campo de información 4: número máximo de conexiones que se pueden poner en cola

###  <a name="tcp-server-socket-relisten"></a>Nueva escucha de socket de servidor TCP 

#### <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

**Icono** ![Icono de nueva escucha de socket de servidor T C P](./media/user-guide/netx-events/image132.png)

**Descripción**

Este evento representa el registro de otro socket de servidor para una solicitud de escucha existente en el puerto TCP especificado por medio de nx_tcp_server_socket_relisten.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: número de puerto TCP
- Campo de información 3: puntero al socket
- Campo de información 4: estado del socket

###  <a name="tcp-server-socket-unaccept"></a>Desaceptación de socket de servidor TCP 

#### <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

**Icono** ![Icono de desaceptación de socket de servidor T C P](./media/user-guide/netx-events/image133.png)

**Descripción**

Este evento representa la eliminación del socket de servidor de la asociación con el puerto que recibe una conexión pasiva anterior por medio de nx_tcp_server_socket_unaccept.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: estado del socket
- Campo de información 4: no se usa

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a>Abandono de escucha de socket de servidor TCP 

#### <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

**Icono** ![Icono de abandono de escucha de socket de servidor T C P](./media/user-guide/netx-events/image134.png)

**Descripción**

Este evento representa la eliminación de una solicitud de escucha anterior para el puerto TCP especificado por medio de nx_tcp_server_socket_unlisten.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: número de puerto TCP
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="tcp-socket-bytes-available"></a>Bytes disponibles de socket TCP 

#### <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

**Icono** ![Icono de bytes disponibles de socket T C P](./media/user-guide/netx-events/image135.png)

**Descripción**

Este evento representa el número de bytes disponibles actualmente en el socket de recepción TCP especificado por medio de nx_tcp_socket_bytes_available.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket TCP
- Campo de información 3: bytes recibidos en el socket
- Campo de información 4: no se usa

### <a name="tcp-socket-create"></a>Creación de socket TCP 

#### <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

**Icono** ![Icono de creación de socket T C P](./media/user-guide/netx-events/image136.png)

**Descripción**

Este evento representa la creación de un socket TCP por medio de nx_tcp_socket_create.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: tipo de servicio
- Campo de información 4: tamaño de la ventana de recepción

### <a name="tcp-socket-delete"></a>Eliminación de socket TCP 

#### <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

**Icono** ![Icono de eliminación de socket T C P](./media/user-guide/netx-events/image137.png)

**Descripción**

Este evento representa la eliminación de un socket por medio de nx_tcp_socket_delete.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: estado del socket
- Campo de información 4: no se usa

### <a name="tcp-socket-disconnect"></a>Desconexión de socket TCP 

#### <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

**Icono** ![Icono de desconexión de socket T C P](./media/user-guide/netx-events/image138.png)

**Descripción**

Este evento representa la desconexión de un socket por medio de nx_tcp_socket_disconnect.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: opción de espera
- Campo de información 4: estado del socket

### <a name="tcp-socket-information-get"></a>Obtención de información de socket TCP 

#### <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

**Icono** ![Icono de obtención de información de socket T C P](./media/user-guide/netx-events/image139.png)

**Descripción**

Este evento representa la obtención de información sobre un socket por medio de nx_tcp_socket_info_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: bytes enviados a través de este socket
- Campo de información 4: bytes recibidos a través de este socket

### <a name="tcp-socket-mss-get"></a>Obtención de MSS de socket TCP 

#### <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

**Icono** ![Icono de obtención de M S S de socket T C P](./media/user-guide/netx-events/image140.png)

**Descripción**

Este evento representa la obtención del MSS del socket por medio de nx_tcp_socket_mss_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: tamaño máximo de segmento (MSS)
- Campo de información 4: estado del socket

### <a name="tcp-socket-mss-peer-get"></a>Obtención de MSS de nodo del mismo nivel de socket TCP 

#### <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

**Icono** ![Icono de obtención de M S S de nodo del mismo nivel de socket T C P](./media/user-guide/netx-events/image141.png)

**Descripción**

Este evento representa la obtención del valor de MSS del nodo del mismo nivel del socket por medio de nx_tcp_socket_mss_peer_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: MSS del nodo del mismo nivel
- Campo de información 4: estado del socket

### <a name="tcp-socket-mss-set"></a>Establecimiento de MSS de socket TCP 

#### <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

**Icono** ![Icono de establecimiento de M S S de socket T C P](./media/user-guide/netx-events/image142.png)

**Descripción**

Este evento representa el establecimiento del MSS de un socket por medio de nx_tcp_socket_mss_set.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: MSS
- Campo de información 4: estado del socket

### <a name="tcp-socket-peer-info-get"></a>Obtención de información de nodo del mismo nivel de socket TCP 

#### <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

**Icono** ![Icono de obtención de información de nodo del mismo nivel de socket T C P](./media/user-guide/netx-events/image143.png)

**Descripción**

Este evento representa la información recuperada del socket TCP en relación con la dirección IP (por ejemplo, >host de conexión) y el puerto del nodo del mismo nivel por medio de nx_tcp_socket_peer_info_get.

**Campos de información**

- Campo de información 1: puntero al socket TCP
- Campo de información 2: dirección IP del nodo del mismo nivel
- Campo de información 3: número de puerto del nodo del mismo nivel
- Campo de información 4: no se usa

### <a name="tcp-socket-receive"></a>Recepción de socket TCP 

#### <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

**Icono** ![Icono de recepción de socket T C P](./media/user-guide/netx-events/image144.png)

**Descripción**

Este evento representa la recepción de datos de un socket por medio de nx_tcp_socket_receive.

**Campos de información**

- Campo de información 1: puntero al socket
- Campo de información 2: puntero al paquete recibido
- Campo de información 3: longitud del paquete recibido
- Campo de información 4: número de secuencia de recepción

### <a name="tcp-socket-receive-notify"></a>Notificación de recepción de socket TCP 

#### <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

**Icono** ![Icono de notificación de recepción de socket T C P](./media/user-guide/netx-events/image145.png)

**Descripción**

Este evento representa el registro de una devolución de llamada de notificación de recepción para un socket por medio de nx_tcp_socket_receive_notify.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero para recibir la devolución de llamada de notificación Campo de información 4: no se usa

### <a name="tcp-socket-send"></a>Envío de socket TCP 

#### <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

**Icono** ![Icono de envío de socket T C P](./media/user-guide/netx-events/image146.png)

**Descripción**

Este evento representa el envío de datos en un socket por medio de nx_tcp_socket_send.

**Campos de información**

- Campo de información 1: puntero al socket
- Campo de información 2: puntero al paquete
- Campo de información 3: longitud del paquete
- Campo de información 4: número de secuencia de transmisión

### <a name="tcp-socket-state-wait"></a>Espera de estado de socket TCP 

#### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

**Icono** ![Icono de espera de estado de socket T C P](./media/user-guide/netx-events/image147.png)

**Descripción**

Este evento representa la espera hasta que un socket entre en un estado determinado por medio de nx_tcp_socket_state_wait.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: estado de socket deseado
- Campo de información 4: estado de socket anterior

### <a name="tcp-socket-transmit-configure"></a>Configuración de transmisión de socket TCP 

#### <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

**Icono** ![Icono de configuración de transmisión de socket T C P](./media/user-guide/netx-events/image148.png)

**Descripción**

Este evento representa la configuración de las opciones de transmisión para un socket por medio de nx_tcp_socket_transmit_configure.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: profundidad de la cola de transmisión
- Campo de información 4: valor de tiempo de espera

### <a name="tcp-socket-window-update-notify-set"></a>Establecimiento de notificación de actualización de ventana de socket TCP 

#### <a name="nx_tcp_window_update_notify_set"></a>nx_tcp_window_update_notify_set

**Icono** ![Icono de establecimiento de notificación de actualización de ventana de socket T C P](./media/user-guide/netx-events/image149.png)

**Descripción**

Este evento representa la recepción de una notificación en un socket TCP sobre un aumento en la ventana de recepción del host remoto por medio de nx_tcp_window_update_notify_set.

**Campos de información** 

- Campo de información 1: puntero al socket TCP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="udp-enable"></a>Habilitación de UDP 

#### <a name="nx_udp_enable"></a>nx_udp_enable

**Icono** ![Icono de habilitación de U D P](./media/user-guide/netx-events/image150.png)

**Descripción**

Este evento representa la habilitación de UDP por medio de nx_udp_enable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="udp-free-port-find"></a>Búsqueda de puerto libre de UDP 

#### <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

**Icono** ![Icono de búsqueda de puerto libre de U D P](./media/user-guide/netx-events/image151.png)

**Descripción**

Este evento representa la búsqueda de un puerto UDP libre por medio de nx_udp_free_port_find.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puerto inicial a partir del cual se hace la búsqueda
- Campo de información 3: puerto libre
- Campo de información 4: no se usa

### <a name="udp-information-get"></a>Obtención de información de UDP 

#### <a name="nx_udp_info_get"></a>nx_udp_info_get

**Icono** ![Icono de obtención de información de U D P](./media/user-guide/netx-events/image152.png)

**Descripción**

Este evento representa la obtención de información por medio de nx_udp_info_get.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: bytes UDP enviados
- Campo de información 3: bytes UDP recibidos
- Campo de información 4: paquetes no válidos

### <a name="udp-socket-bind"></a>Enlace de socket UDP 

#### <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

**Icono** ![Icono de enlace de socket U D P](./media/user-guide/netx-events/image153.png)

**Descripción**

Este evento representa el enlace de un socket UDP a un puerto por medio de nx_udp_socket_bind.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: número del puerto
- Campo de información 4: opción de espera

### <a name="udp-socket-bytes-available"></a>Bytes disponibles de socket UDP 

#### <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

**Icono** ![Icono de bytes disponibles de socket U D P](./media/user-guide/netx-events/image154.png)

**Descripción**

Este evento representa el número actual de bytes recibidos en el socket UDP por medio de nx_udp_socket_bytes_available.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: bytes recibidos en el socket
- Campo de información 4: no se usa

### <a name="udp-socket-checksum-disable"></a>Deshabilitación de suma de comprobación de socket UDP 

#### <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

**Icono** ![Icono de deshabilitación de suma de comprobación de socket U D P](./media/user-guide/netx-events/image155.png)

**Descripción**

Este evento representa la deshabilitación de la suma de comprobación para los datos de un socket UDP por medio de nx_udp_socket_checksum_disable.

**Campos de información** 

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="udp-socket-checksum-enable"></a>Habilitación de suma de comprobación de socket UDP 

#### <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

**Icono** ![Icono de habilitación de suma de comprobación de socket U D P](./media/user-guide/netx-events/image156.png)

**Descripción**

Este evento representa la habilitación del procesamiento de suma de comprobación en un socket por medio de nx_udp_socket_checksum_enable.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="udp-socket-create"></a>Creación de socket UDP 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Icono** ![Icono de creación de socket U D P](./media/user-guide/netx-events/image157.png)

**Descripción**

Este evento representa la creación de un socket UDP por medio de nx_udp_socket_create.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: tipo de servicio
- Campo de información 4: cola de recepción máxima

### <a name="udp-socket-delete-event"></a>Evento de eliminación de socket UDP 

#### <a name="nx_udp_socket_delete-event"></a>nx_udp_socket_delete

**Icono** ![Icono de evento de eliminación de socket U D P](./media/user-guide/netx-events/image158.png)

**Descripción**

Este evento representa la eliminación de un socket UDP por medio de nx_udp_socket_delete.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="udp-socket-information-get-event"></a>Evento de obtención de información de socket UDP 

#### <a name="nx_udp_socket_info_get-event"></a>nx_udp_socket_info_get

**Icono** ![Icono de evento de obtención de información de socket U D P](./media/user-guide/netx-events/image159.png)

**Descripción**

Este evento representa la obtención de información acerca de un socket UDP por medio de nx_udp_socket_info_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: bytes enviados a través del socket
- Campo de información 4: bytes recibidos a través del socket

### <a name="udp-socket-interface-set"></a>Establecimiento de interfaz de socket UDP 

#### <a name="nx_udp_socket_interface_set-event"></a>nx_udp_socket_interface_set

**Icono** ![Icono de establecimiento de interfaz de socket U D P](./media/user-guide/netx-events/image160.png)

**Descripción**

Este evento representa el establecimiento de la interfaz de salida del socket UDP especificado con la interfaz especificada por medio de nx_udp_socket_interface_set.

**Campos de información**

- Campo de información 1: puntero al socket UDP
- Campo de información 2: índice correspondiente a la interfaz para el socket
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="udp-socket-port-get"></a>Obtención de puerto de socket UDP 

#### <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

**Icono** ![Icono de obtención de puerto de socket U D P](./media/user-guide/netx-events/image161.png)

**Descripción**

Este evento representa la recuperación del puerto UDP al que está enlazado el socket UDP especificado por medio de nx_udp_socket_port_get.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket UDP
- Campo de información 3: número del puerto
- Campo de información 4: no se usa

### <a name="udp-socket-receive"></a>Recepción de socket UDP 

#### <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

**Icono** ![Icono de recepción de socket U D P](./media/user-guide/netx-events/image162.png)

**Descripción**

Este evento representa la recepción de datos en el socket UDP especificado por medio de nx_udp_socket_receive.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket UDP
- Campo de información 3: puntero al paquete recibido
- Campo de información 4: tamaño de paquete recibido

### <a name="udp-socket-receive-notify"></a>Notificación de recepción de socket UDP 

#### <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

**Icono** ![Icono de notificación de recepción de socket U D P](./media/user-guide/netx-events/image163.png) **Descripción**

Este evento representa el registro de una devolución de llamada de notificación de recepción por medio de nx_udp_socket_receive_notify.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: puntero a la función de notificación de recepción Campo de información 4: no se usa

### <a name="udp-socket-send"></a>Envío de socket UDP 

#### <a name="nx_udp_socket_send"></a>nx_udp_socket_send

**Icono** ![Icono de envío de socket U D P](./media/user-guide/netx-events/image164.png)

**Descripción**

Este evento representa el envío de datos a través de un socket UDP por medio de nx_udp_socket_send.

**Campos de información**

- Campo de información 1: puntero al socket
- Campo de información 2: puntero al paquete
- Campo de información 3: longitud del paquete
- Campo de información 4: dirección IP de destino

### <a name="udp-socket-unbind"></a>Desenlace de socket UDP 

#### <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

**Icono** ![Icono de desenlace de socket U D P](./media/user-guide/netx-events/image165.png)

**Descripción**

Este evento representa el desenlace de un puerto UDP con un socket por medio de nx_udp_socket_unbind.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: número del puerto
- Campo de información 4: no se usa

### <a name="udp-source-extract"></a>Extracción de origen de UDP 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Icono** ![Icono de extracción de origen de U D P](./media/user-guide/netx-events/image166.png)

**Descripción**

Este evento representa la obtención de la dirección IP y el número de puerto de un paquete UDP recibido por medio de nx_udp_source_extract.

**Campos de información**

- Campo de información 1: puntero al paquete
- Campo de información 2: dirección IP del remitente
- Campo de información 3: número de puerto del remitente
- Campo de información 4: no se usa