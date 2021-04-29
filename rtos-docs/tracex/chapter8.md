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
# <a name="chapter-8---azure-rtos-netx-trace-events"></a><span data-ttu-id="09389-103">Capítulo 8: Eventos de seguimiento de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="09389-103">Chapter 8 - Azure RTOS NetX trace events</span></span>

<span data-ttu-id="09389-104">Este capítulo contiene una descripción de los eventos de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-104">This chapter contains a description of the Azure RTOS NetX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="09389-105">Lista de eventos e iconos</span><span class="sxs-lookup"><span data-stu-id="09389-105">List of Events and Icons</span></span>

<span data-ttu-id="09389-106">A continuación se muestra una lista de eventos de NetX mostrados por TraceX.</span><span class="sxs-lookup"><span data-stu-id="09389-106">The following is a list of NetX events displayed by TraceX.</span></span>

| <span data-ttu-id="09389-107">Icono</span><span class="sxs-lookup"><span data-stu-id="09389-107">Icon</span></span>                                           | <span data-ttu-id="09389-108">Significado</span><span class="sxs-lookup"><span data-stu-id="09389-108">Meaning</span></span>                 |
| -------------------------------- | ------------------------------------- |
| ![Icono de recepción de solicitud A R P interna](./media/user-guide/netx-events/image1.png)    | <span data-ttu-id="09389-110">Recepción de solicitud ARP interna</span><span class="sxs-lookup"><span data-stu-id="09389-110">Internal ARP Request Receive</span></span> |
| ![Icono de envío de solicitud A R P interno](./media/user-guide/netx-events/image2.png)    | <span data-ttu-id="09389-112">Envío de solicitud ARP interno</span><span class="sxs-lookup"><span data-stu-id="09389-112">Internal ARP Request Send</span></span> |
| ![Icono de recepción de respuesta A R P interna](./media/user-guide/netx-events/image3.png)    | <span data-ttu-id="09389-114">Recepción de respuesta ARP interna</span><span class="sxs-lookup"><span data-stu-id="09389-114">Internal ARP Response Receive</span></span> |
| ![Icono de envío de respuesta A R P interno](./media/user-guide/netx-events/image4.png)    | <span data-ttu-id="09389-116">Envío de respuesta ARP interno</span><span class="sxs-lookup"><span data-stu-id="09389-116">Internal ARP Response Send</span></span> |
| ![Icono de recepción de I C M P interna](./media/user-guide/netx-events/image5.png)    | <span data-ttu-id="09389-118">Recepción de ICMP interna</span><span class="sxs-lookup"><span data-stu-id="09389-118">Internal ICMP Receive</span></span> |
| ![Icono de envío de I C M P interno](./media/user-guide/netx-events/image6.png)    | <span data-ttu-id="09389-120">Envío de ICMP interno</span><span class="sxs-lookup"><span data-stu-id="09389-120">Internal ICMP Send</span></span> |
| ![Icono de recepción de I G M P de NetX interna](./media/user-guide/netx-events/image7.png)    | <span data-ttu-id="09389-122">Recepción de IGMP de NetX interna</span><span class="sxs-lookup"><span data-stu-id="09389-122">Internal NetX IGMP Receive</span></span> |
| ![Icono de recepción de I P interna](./media/user-guide/netx-events/image8.png)    | <span data-ttu-id="09389-124">Recepción de IP interna</span><span class="sxs-lookup"><span data-stu-id="09389-124">Internal IP Receive</span></span> |
| ![Icono de envío de I P interno](./media/user-guide/netx-events/image9.png)    | <span data-ttu-id="09389-126">Envío de IP interno</span><span class="sxs-lookup"><span data-stu-id="09389-126">Internal IP Send</span></span> |
| ![Icono de recepción de datos de T C P interna](./media/user-guide/netx-events/image10.png)    | <span data-ttu-id="09389-128">Recepción de datos de TCP interna</span><span class="sxs-lookup"><span data-stu-id="09389-128">Internal TCP Data Receive</span></span> |
| ![Icono de envío de datos de T C P interno](./media/user-guide/netx-events/image11.png)    | <span data-ttu-id="09389-130">Envío de datos de TCP interno</span><span class="sxs-lookup"><span data-stu-id="09389-130">Internal TCP Data Send</span></span> |
| ![Icono de recepción de T C P F I N interna](./media/user-guide/netx-events/image12.png)    | <span data-ttu-id="09389-132">Recepción de TCP FIN interna</span><span class="sxs-lookup"><span data-stu-id="09389-132">Internal TCP FIN Receive</span></span> |
| ![Icono de envío de T C P F I N interno](./media/user-guide/netx-events/image13.png)    | <span data-ttu-id="09389-134">Envío de TCP FIN interno</span><span class="sxs-lookup"><span data-stu-id="09389-134">Internal TCP FIN Send</span></span> |
| ![Icono de recepción de T C P R S T interna](./media/user-guide/netx-events/image14.png)    | <span data-ttu-id="09389-136">Recepción de TCP RST interna</span><span class="sxs-lookup"><span data-stu-id="09389-136">Internal TCP RST Receive</span></span> |
| ![Icono de envío de T C P R S T interno](./media/user-guide/netx-events/image15.png)    | <span data-ttu-id="09389-138">Envío de TCP RST interno</span><span class="sxs-lookup"><span data-stu-id="09389-138">Internal TCP RST Send</span></span> |
| ![Icono de recepción de T C P S Y N interna](./media/user-guide/netx-events/image16.png)    | <span data-ttu-id="09389-140">Recepción de TCP SYN interna</span><span class="sxs-lookup"><span data-stu-id="09389-140">Internal TCP SYN Receive</span></span> |
| ![Icono de envío de T C P S Y N interno](./media/user-guide/netx-events/image17.png)    | <span data-ttu-id="09389-142">Envío de TCP SYN interno</span><span class="sxs-lookup"><span data-stu-id="09389-142">Internal TCP SYN Send</span></span> |
| ![Icono de recepción de U D P interna](./media/user-guide/netx-events/image18.png)    | <span data-ttu-id="09389-144">Recepción de UDP interna</span><span class="sxs-lookup"><span data-stu-id="09389-144">Internal UDP Receive</span></span> |
| ![Icono de envío de U D P interno](./media/user-guide/netx-events/image19.png)    | <span data-ttu-id="09389-146">Envío de UDP interno</span><span class="sxs-lookup"><span data-stu-id="09389-146">Internal UDP Send</span></span> |
| ![Icono de recepción de R A R P interna](./media/user-guide/netx-events/image20.png)    | <span data-ttu-id="09389-148">Recepción de RARP interna</span><span class="sxs-lookup"><span data-stu-id="09389-148">Internal RARP Receive</span></span> |
| ![Icono de envío de R A R P interno](./media/user-guide/netx-events/image21.png)    | <span data-ttu-id="09389-150">Envío de RARP interno</span><span class="sxs-lookup"><span data-stu-id="09389-150">Internal RARP Send</span></span> |
| ![Icono de reintento de T C P interno](./media/user-guide/netx-events/image22.png)    | <span data-ttu-id="09389-152">Reintento de TCP interno</span><span class="sxs-lookup"><span data-stu-id="09389-152">Internal TCP Retry</span></span> |
| ![Icono de cambio de estado de T C P interno](./media/user-guide/netx-events/image23.png)    | <span data-ttu-id="09389-154">Cambio de estado de TCP interno</span><span class="sxs-lookup"><span data-stu-id="09389-154">Internal TCP State Change</span></span> |
| ![Icono de envío de paquete de controladores de E/S interno](./media/user-guide/netx-events/image24.png)    | <span data-ttu-id="09389-156">Envío de paquete de controladores de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-156">Internal I/O Driver Packet Send</span></span> |
| ![icon](./media/user-guide/netx-events/image25.png)    | <span data-ttu-id="09389-158">Inicialización de controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-158">Internal I/O Driver Initialize</span></span> |
| ![Icono de inicialización de controlador de E/S interna](./media/user-guide/netx-events/image26.png)    | <span data-ttu-id="09389-160">Habilitación del vínculo de controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-160">Internal I/O Driver Link Enable</span></span> |
| ![Icono de deshabilitación del vínculo de controlador de E/S interna](./media/user-guide/netx-events/image27.png)    | <span data-ttu-id="09389-162">Deshabilitación del vínculo de controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-162">Internal I/O Driver Link Disable</span></span> |
| ![Icono de difusión del paquete de controladores de E/S interna](./media/user-guide/netx-events/image28.png)    | <span data-ttu-id="09389-164">Difusión del paquete de controladores de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-164">Internal I/O Driver Packet Broadcast</span></span> |
| ![Icono de envío de A R P del controlador de E/S interno](./media/user-guide/netx-events/image29.png)    | <span data-ttu-id="09389-166">Envío de ARP del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-166">Internal I/O Driver ARP Send</span></span> |
| ![Icono de envío de respuesta A R P del controlador de E/S interno](./media/user-guide/netx-events/image30.png)    | <span data-ttu-id="09389-168">Envío de respuesta ARP del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-168">Internal I/O Driver ARP Response Send</span></span> |
| ![Icono de envío de R A R P del controlador de E/S interno](./media/user-guide/netx-events/image31.png)    | <span data-ttu-id="09389-170">Envío de RARP del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-170">Internal I/O Driver RARP Send</span></span> |
| ![Icono de combinación de multidifusión del controlador de E/S interna](./media/user-guide/netx-events/image32.png)    | <span data-ttu-id="09389-172">Combinación de multidifusión del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-172">Internal I/O Driver Multicast Join</span></span> |
| ![Icono de salida de multidifusión del controlador de E/S interna](./media/user-guide/netx-events/image33.png)    | <span data-ttu-id="09389-174">Salida de multidifusión del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-174">Internal I/O Driver Multicast Leave</span></span> |
| ![Icono de obtención de estado del controlador de E/S interna](./media/user-guide/netx-events/image34.png)    | <span data-ttu-id="09389-176">Obtención de estado del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-176">Internal I/O Driver Get Status</span></span> |
| ![Icono de obtención de velocidad del controlador de E/S interna](./media/user-guide/netx-events/image35.png)    | <span data-ttu-id="09389-178">Obtención de velocidad del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-178">Internal I/O Driver Get Speed</span></span> |
| ![Icono de obtención de tipo dúplex del controlador de E/S interna](./media/user-guide/netx-events/image36.png)    | <span data-ttu-id="09389-180">Obtención de tipo dúplex del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-180">Internal I/O Driver Get Duplex Type</span></span> |
| ![Icono de obtención de número de errores del controlador de E/S interna](./media/user-guide/netx-events/image37.png)    | <span data-ttu-id="09389-182">Obtención de número de errores del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-182">Internal I/O Driver Get Error Count</span></span> |
| ![Icono de obtención de número de R X del controlador de E/S interna](./media/user-guide/netx-events/image38.png)    | <span data-ttu-id="09389-184">Obtención de número de RX del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-184">Internal I/O Driver Get RX Count</span></span> |
| ![Icono de obtención de número de T X del controlador de E/S interna](./media/user-guide/netx-events/image39.png)    | <span data-ttu-id="09389-186">Obtención de número de TX del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-186">Internal I/O Driver Get TX Count</span></span> |
| ![Icono de obtención de errores de asignación del controlador de E/S interna](./media/user-guide/netx-events/image40.png)    | <span data-ttu-id="09389-188">Obtención de errores de asignación del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-188">Internal I/O Driver Get Allocation Errors</span></span> |
| ![Icono de anulación de inicialización del controlador de E/S interna](./media/user-guide/netx-events/image41.png)    | <span data-ttu-id="09389-190">Anulación de inicialización del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-190">Internal I/O Driver Un-initialize</span></span> |
| ![Icono de procesamiento diferido del controlador de E/S interno](./media/user-guide/netx-events/image42.png)    | <span data-ttu-id="09389-192">Procesamiento diferido del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-192">Internal I/O Driver Deferred Processing</span></span> |
| ![Icono de invalidación de entradas dinámicas de A R P](./media/user-guide/netx-events/image43.png)    | <span data-ttu-id="09389-194">**Invalidación de entradas dinámicas de ARP** (*nx_arp_dynamic_entries_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="09389-194">**ARP Dynamic Entries Invalidate** (*nx_arp_dynamic_entries_invalidate*)</span></span> |
| ![Icono de establecimiento de entrada dinámica de A R P](./media/user-guide/netx-events/image44.png)    | <span data-ttu-id="09389-196">**Establecimiento de entrada dinámica de ARP** (*nx_arp_dynamic_entry_set*)</span><span class="sxs-lookup"><span data-stu-id="09389-196">**ARP Dynamic Entry Set** (*nx_arp_dynamic_entry_set*)</span></span> |
| ![Icono de habilitación de A R P](./media/user-guide/netx-events/image45.png)    | <span data-ttu-id="09389-198">**Habilitación de ARP** (*nx_arp_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-198">**ARP Enable** (*nx_arp_enable*)</span></span> |
| ![Icono de envío gratuito de A R P](./media/user-guide/netx-events/image46.png)    | <span data-ttu-id="09389-200">**Envío gratuito de ARP** (*nx_arp_gratuitous_send*)</span><span class="sxs-lookup"><span data-stu-id="09389-200">**ARP Gratuitous Send** (*nx_arp_gratuitous_send*)</span></span> |
| ![Icono de búsqueda de dirección de hardware de A R P](./media/user-guide/netx-events/image47.png)    | <span data-ttu-id="09389-202">**Búsqueda de dirección de hardware de ARP** (*nx_arp_hardware_address_find*)</span><span class="sxs-lookup"><span data-stu-id="09389-202">**ARP Hardware Address Find** (*nx_arp_hardware_address_find*)</span></span> |
| ![Icono de obtención de información de A R P](./media/user-guide/netx-events/image48.png)    | <span data-ttu-id="09389-204">**Obtención de información de ARP** (*nx_arp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-204">**ARP Information Get** (*nx_arp_info_get*)</span></span> |
| ![Icono de búsqueda de dirección I P de A R P](./media/user-guide/netx-events/image49.png)    | <span data-ttu-id="09389-206">**Búsqueda de dirección IP de ARP** (*nx_arp_ip_address_find*)</span><span class="sxs-lookup"><span data-stu-id="09389-206">**ARP IP Address Find** (*nx_arp_ip_address_find*)</span></span> |
| ![Icono de creación de entrada estática de A R P](./media/user-guide/netx-events/image50.png)    | <span data-ttu-id="09389-208">**Creación de entrada estática de ARP** (*nx_arp_static_entry_create*)</span><span class="sxs-lookup"><span data-stu-id="09389-208">**ARP Static Entry Create** (*nx_arp_static_entry_create*)</span></span> |
| ![Icono de eliminación de entradas estáticas de A R P](./media/user-guide/netx-events/image51.png)    | <span data-ttu-id="09389-210">**Eliminación de entradas estáticas de ARP** (*nx_arp_static_entries_delete*)</span><span class="sxs-lookup"><span data-stu-id="09389-210">**ARP Static Entries Delete** (*nx_arp_static_entries_delete*)</span></span> |
| ![Icono de eliminación de entrada estática de A R P](./media/user-guide/netx-events/image52.png)    | <span data-ttu-id="09389-212">**Eliminación de entrada estática de ARP** (*nx_arp_static_entry_delete*)</span><span class="sxs-lookup"><span data-stu-id="09389-212">**ARP Static Entry Delete** (*nx_arp_static_entry_delete*)</span></span> |
| ![Icono de eliminación de entrada de caché doble](./media/user-guide/netx-events/image53.png)    | <span data-ttu-id="09389-214">**Eliminación de entrada de caché doble** (*nxd_nd_cache_entry_delete*)</span><span class="sxs-lookup"><span data-stu-id="09389-214">**Duo Cache Entry Delete** (*nxd_nd_cache_entry_delete*)</span></span> |
| ![Icono de establecimiento de entrada de caché doble](./media/user-guide/netx-events/image54.png)    | <span data-ttu-id="09389-216">**Establecimiento de entrada de caché doble** (*nxd_nd_cache_entry_set*)</span><span class="sxs-lookup"><span data-stu-id="09389-216">**Duo Cache Entry Set** (*nxd_nd_cache_entry_set*)</span></span> |
| ![Icono de invalidación de caché doble](./media/user-guide/netx-events/image55.png)    | <span data-ttu-id="09389-218">**Invalidación de caché doble** (*nxd_nd_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="09389-218">**Duo Cache Invalidate** (*nxd_nd_cache_invalidate*)</span></span> |
| ![Icono de búsqueda de dirección I P de caché doble](./media/user-guide/netx-events/image56.png)    | <span data-ttu-id="09389-220">**Búsqueda de dirección IP de caché doble** (*nxd_nd_cache_ip_address_find*)</span><span class="sxs-lookup"><span data-stu-id="09389-220">**Duo Cache IP Address Find** (*nxd_nd_cache_ip_address_find*)</span></span> |
| ![Icono de habilitación de I C M P doble](./media/user-guide/netx-events/image57.png)    | <span data-ttu-id="09389-222">**Habilitación de ICMP doble** (*nxd_icmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-222">**Duo ICMP Enable** (*nxd_icmp_enable*)</span></span> |
| ![Icono de ping de I P v 6 de I C M P doble](./media/user-guide/netx-events/image58.png)    | <span data-ttu-id="09389-224">**Ping de IPv6 de ICMP doble** (*nxd_icmp_ping*)</span><span class="sxs-lookup"><span data-stu-id="09389-224">**Duo ICMP IPv6 Ping** (*nxd_icmp_ping*)</span></span> |
| ![Icono de búsqueda de tamaño máximo de carga de I P doble](./media/user-guide/netx-events/image59.png)    | <span data-ttu-id="09389-226">**Búsqueda de tamaño máximo de carga de IP doble** (*nx_max_payload_size_find*)</span><span class="sxs-lookup"><span data-stu-id="09389-226">**Duo IP Max Payload Size Find** (*nx_max_payload_size_find*)</span></span> |
| ![Icono de envío de paquete sin formato de I P doble](./media/user-guide/netx-events/image60.png)    | <span data-ttu-id="09389-228">**Envío de paquete sin formato de IP doble** (*nxd_ip_raw_packet_send*)</span><span class="sxs-lookup"><span data-stu-id="09389-228">**Duo IP Raw Packet Send** (*nxd_ip_raw_packet_send*)</span></span> |
| ![Icono de adición de enrutador predeterminado de I P v 6 doble](./media/user-guide/netx-events/image61.png)    | <span data-ttu-id="09389-230">**Adición de enrutador predeterminado de IPv6 doble** (*nxd_ipv6_default_router_add*)</span><span class="sxs-lookup"><span data-stu-id="09389-230">**Duo IPv6 Default Router Add** (*nxd_ipv6_default_router_add*)</span></span> |
| ![Icono de eliminación de enrutador predeterminado de I P v 6 doble](./media/user-guide/netx-events/image62.png)    | <span data-ttu-id="09389-232">**Eliminación de enrutador predeterminado de IPv6 doble** (*nxd_ipv6_default_router_delete*)</span><span class="sxs-lookup"><span data-stu-id="09389-232">**Duo IPv6 Default Router Delete** (*nxd_ipv6_default_router_delete)*</span></span> |
| ![Icono de habilitación de I P v 6 doble](./media/user-guide/netx-events/image63.png)    | <span data-ttu-id="09389-234">**Habilitación de IPv6 doble** (*nxd_ipv6_enable)*</span><span class="sxs-lookup"><span data-stu-id="09389-234">**Duo IPv6 Enable** (*nxd_ipv6_enable)*</span></span> |
| ![Icono de obtención de dirección global de I P v 6 doble](./media/user-guide/netx-events/image64.png)    | <span data-ttu-id="09389-236">**Obtención de dirección global de IPv6 doble** (*nxd_ipv6_global_address_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-236">**Duo IPv6 Global Address Get** (*nxd_ipv6_global_address_get*)</span></span> |
| ![Icono de establecimiento de dirección global de I P v 6 doble](./media/user-guide/netx-events/image65.png)    | <span data-ttu-id="09389-238">**Establecimiento de dirección global de IPv6 doble** (*nxd_ipv6_global_address_set*)</span><span class="sxs-lookup"><span data-stu-id="09389-238">**Duo IPv6 Global Address Set** (*nxd_ipv6_global_address_set*)</span></span> |
| ![Icono de inicio de proceso D A D de I P v 6 doble](./media/user-guide/netx-events/image66.png)    | <span data-ttu-id="09389-240">**Inicio de proceso DAD de IPv6 doble** (*nxd_ipv6_initiate_dad_process*)</span><span class="sxs-lookup"><span data-stu-id="09389-240">**Duo IPv6 Initiate Dad Process** (*nxd_ipv6_initiate_dad_process*)</span></span> |
| ![Icono de obtención de dirección de interfaz de I P v 6 doble](./media/user-guide/netx-events/image67.png)    | <span data-ttu-id="09389-242">**Obtención de dirección de interfaz de IPv6 doble** (*nxd_ipv6_interface_address_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-242">**Duo IPv6 Interface Address Get** (*nxd_ipv6_interface_address_get*)</span></span> |
| ![Icono de establecimiento de dirección de interfaz de I P v 6 doble](./media/user-guide/netx-events/image68.png)    | <span data-ttu-id="09389-244">**Establecimiento de dirección de interfaz de IPv6 doble** (*nxd_ipv6_interface_address_set*)</span><span class="sxs-lookup"><span data-stu-id="09389-244">**Duo IPv6 Interface Address Set** (*nxd_ipv6_interface_address_set*)</span></span> |
| ![Icono de obtención de dirección local de vínculo de I P v 6 doble](./media/user-guide/netx-events/image69.png)    | <span data-ttu-id="09389-246">**Obtención de dirección local de vínculo de IPv6 doble** (*nxd_ipv6_linklocal_address_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-246">**Duo IPv6 Link Local Address Get** (*nxd_ipv6_linklocal_address_get*)</span></span> |
| ![Icono de establecimiento de dirección local de vínculo de I P v 6 doble](./media/user-guide/netx-events/image70.png)    | <span data-ttu-id="09389-248">**Establecimiento de dirección local de vínculo de IPv6 doble** (*nxd_ipv6_linklocal_address_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-248">**Duo IPv6 Link Local Address Set** (*nxd_ipv6_linklocal_address_set*)</span></span> |
| ![Icono de envío de paquete sin formato de I P v 6 doble](./media/user-guide/netx-events/image71.png)    | <span data-ttu-id="09389-250">**Envío de paquete sin formato de IPv6 doble** (*nxd_ipv6_raw_packet_send*)</span><span class="sxs-lookup"><span data-stu-id="09389-250">**Duo IPv6 Raw Packet Send** (*nxd_ipv6_raw_packet_send)*</span></span> |
| ![Icono de obtención de información de nodo del mismo nivel de socket de T C P doble](./media/user-guide/netx-events/image72.png)    | <span data-ttu-id="09389-252">**Obtención de información de nodo del mismo nivel de socket de TCP doble** (*nxd_tcp_socket_peer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-252">**Duo TCP Socket Peer Info Get** (*nxd_tcp_socket_peer_info_get*)</span></span> |
| ![Icono de establecimiento de interfaz de socket de T C P doble](./media/user-guide/netx-events/image73.png)    | <span data-ttu-id="09389-254">**Establecimiento de interfaz de socket de TCP doble** (*nxd_tcp_socket_set_interface*)</span><span class="sxs-lookup"><span data-stu-id="09389-254">**Duo TCP Socket Set Interface** (*nxd_tcp_socket_set_interface*)</span></span> |
| ![Icono de envío de socket de U D P doble](./media/user-guide/netx-events/image74.png)    | <span data-ttu-id="09389-256">**Envío de socket de UDP doble** (*nxd_udp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="09389-256">**Duo UDP Socket Send** (*nxd_udp_socket_send*)</span></span> |
| ![Icono de establecimiento de interfaz de socket de U D P doble](./media/user-guide/netx-events/image75.png)    | <span data-ttu-id="09389-258">**Establecimiento de interfaz de socket de UDP doble** (*nxd_udp_socket_set_interface*)</span><span class="sxs-lookup"><span data-stu-id="09389-258">**Duo UDP Socket Set Interface** (*nxd_udp_socket_set_interface*)</span></span> |
| ![Icono de extracción de origen de U D P doble](./media/user-guide/netx-events/image76.png)    | <span data-ttu-id="09389-260">**Extracción de origen de UDP doble** (*nxd_udp_source_extract*)</span><span class="sxs-lookup"><span data-stu-id="09389-260">**Duo UDP Source Extract** (*nxd_udp_source_extract*)</span></span> |
| ![Icono de habilitación de I C M P](./media/user-guide/netx-events/image77.png)    | <span data-ttu-id="09389-262">**Habilitación de ICMP** (*nx_icmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-262">**ICMP Enable** (*nx_icmp_enable*)</span></span> |
| ![Icono de obtención de información de I C M P](./media/user-guide/netx-events/image78.png)    | <span data-ttu-id="09389-264">**Obtención de información de ICMP** (*nx_icmp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-264">**ICMP Information Get** (*nx_icmp_info_get*)</span></span> |
| ![Icono de ping de I C M P](./media/user-guide/netx-events/image79.png)    | <span data-ttu-id="09389-266">**Ping de ICMP** (*nx_icmp_ping*)</span><span class="sxs-lookup"><span data-stu-id="09389-266">**ICMP Ping** (*nx_icmp_ping*)</span></span> |
| ![Icono de habilitación de I G M P](./media/user-guide/netx-events/image80.png)    | <span data-ttu-id="09389-268">**Habilitación de IGMP** (*nx_igmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-268">**IGMP Enable** (*nx_igmp_enable*)</span></span> |
| ![Icono de obtención de información de I G M P](./media/user-guide/netx-events/image81.png)    | <span data-ttu-id="09389-270">**Obtención de información de IGMP** (*nx_igmp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-270">**IGMP Information Get** (*nx_igmp_info_get*)</span></span> |
| ![Icono de deshabilitación de bucle invertido de I G P M](./media/user-guide/netx-events/image82.png)    | <span data-ttu-id="09389-272">**Deshabilitación de bucle invertido de IGMP** (*nx_igmp_loopback_disable*)</span><span class="sxs-lookup"><span data-stu-id="09389-272">**IGMP Loopback Disable** (*nx_igmp_loopback_disable*)</span></span> |
| ![Icono de habilitación de bucle invertido de I G M P](./media/user-guide/netx-events/image83.png)    | <span data-ttu-id="09389-274">**Habilitación de bucle invertido de IGMP** (*nx_igmp_loopback_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-274">**IGMP Loopback Enable** (*nx_igmp_loopback_enable*)</span></span> |
| ![Icono de combinación de multidifusión de I G M P](./media/user-guide/netx-events/image84.png)    | <span data-ttu-id="09389-276">**Combinación de multidifusión de IGMP** (*nx_igmp_multicast_join*)</span><span class="sxs-lookup"><span data-stu-id="09389-276">**IGMP Multicast Join** (*nx_igmp_multicast_join*)</span></span> |
| ![Icono de salida de multidifusión de I G M P](./media/user-guide/netx-events/image85.png)    | <span data-ttu-id="09389-278">**Salida de multidifusión de IGMP** (*nx_igmp_multicast_leave*)</span><span class="sxs-lookup"><span data-stu-id="09389-278">**IGMP Multicast Leave** (*nx_igmp_multicast_leave*)</span></span> |
| ![Icono de notificación de cambio de dirección I P](./media/user-guide/netx-events/image86.png)    | <span data-ttu-id="09389-280">**Notificación de cambio de dirección IP** (*nx_ip_address_change_notify*)</span><span class="sxs-lookup"><span data-stu-id="09389-280">**IP Address Change Notify** (*nx_ip_address_change_notify*)</span></span> |
| ![Icono de obtención de dirección I P](./media/user-guide/netx-events/image87.png)    | <span data-ttu-id="09389-282">**Obtención de dirección IP** (*nx_ip_address_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-282">**IP Address Get** (*nx_ip_address_get*)</span></span> |
| ![Icono de establecimiento de dirección I P](./media/user-guide/netx-events/image88.png)    | <span data-ttu-id="09389-284">**Establecimiento de dirección IP** (*nx_ip_address_set*)</span><span class="sxs-lookup"><span data-stu-id="09389-284">**IP Address Set** (*nx_ip_address_set*)</span></span> |
| ![Icono de creación de I P](./media/user-guide/netx-events/image89.png)    | <span data-ttu-id="09389-286">**Creación de IP** (*nx_ip_create*)</span><span class="sxs-lookup"><span data-stu-id="09389-286">**IP Create** (*nx_ip_create*)</span></span> |
| ![Icono de eliminación de I P](./media/user-guide/netx-events/image90.png)    | <span data-ttu-id="09389-288">**Eliminación de IP** (*nx_ip_delete*)</span><span class="sxs-lookup"><span data-stu-id="09389-288">**IP Delete** (*nx_ip_delete*)</span></span> |
| ![Icono de comando directo de controlador de I P](./media/user-guide/netx-events/image91.png)    | <span data-ttu-id="09389-290">**Comando directo de controlador de IP** (*nx_ip_driver_direct_command*)</span><span class="sxs-lookup"><span data-stu-id="09389-290">**IP Driver Direct Command** (*nx_ip_driver_direct_command*)</span></span> |
| ![Icono de deshabilitación de reenvío de I P](./media/user-guide/netx-events/image92.png)    | <span data-ttu-id="09389-292">**Deshabilitación de reenvío de IP** (*nx_ip_forwarding_disable*)</span><span class="sxs-lookup"><span data-stu-id="09389-292">**IP Forwarding Disable** (*nx_ip_forwarding_disable*)</span></span> |
| ![Icono de habilitación de reenvío de I P](./media/user-guide/netx-events/image93.png)    | <span data-ttu-id="09389-294">**Habilitación de reenvío de IP** (*nx_ip_forwarding_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-294">**IP Forwarding Enable** (*nx_ip_forwarding_enable*)</span></span> |
| ![Icono de deshabilitación de fragmento de I P](./media/user-guide/netx-events/image94.png)    | <span data-ttu-id="09389-296">**Deshabilitación de fragmento de IP** (*nx_ip_fragment_disable*)</span><span class="sxs-lookup"><span data-stu-id="09389-296">**IP Fragment Disable** (*nx_ip_fragment_disable*)</span></span> |
| ![Icono de habilitación de fragmento de I P](./media/user-guide/netx-events/image95.png)    | <span data-ttu-id="09389-298">**Habilitación de fragmento de IP** (*nx_ip_fragment_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-298">**IP Fragment Enable** (*nx_ip_fragment_enable*)</span></span>  |
| ![Icono de establecimiento de dirección de puerta de enlace de I P](./media/user-guide/netx-events/image96.png)    | <span data-ttu-id="09389-300">**Establecimiento de dirección de puerta de enlace de IP** (*nx_ip_gateway_address_set*)</span><span class="sxs-lookup"><span data-stu-id="09389-300">**IP Gateway Address Set** (*nx_ip_gateway_address_set*)</span></span> |
| ![Icono de obtención de información de I P](./media/user-guide/netx-events/image97.png)    | <span data-ttu-id="09389-302">**Obtención de información de IP** (*nx_ip_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-302">**IP Information Get** (*nx_ip_info_get*)</span></span> |
| ![Icono de asociación de interfaz de I P](./media/user-guide/netx-events/image98.png)    | <span data-ttu-id="09389-304">**Asociación de interfaz de IP** (*nx_ip_interface_attach*)</span><span class="sxs-lookup"><span data-stu-id="09389-304">**IP Interface Attach** (*nx_ip_interface_attach*)</span></span> |
| ![Icono de obtención de información de interfaz de I P](./media/user-guide/netx-events/image99.png)    | <span data-ttu-id="09389-306">**Obtención de información de interfaz de IP** (*nx_ip_interface_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-306">**IP Interface Info Get** (*nx_ip_interface_info_get*)</span></span> |
| ![Icono de deshabilitación de paquete sin formato de I P](./media/user-guide/netx-events/image100.png)    | <span data-ttu-id="09389-308">**Deshabilitación de paquete sin formato de IP** (*nx_ip_raw_packet_disable*)</span><span class="sxs-lookup"><span data-stu-id="09389-308">**IP Raw Packet Disable** (*nx_ip_raw_packet_disable*)</span></span> |
| ![Icono de habilitación de paquete sin formato de I P](./media/user-guide/netx-events/image101.png)    | <span data-ttu-id="09389-310">**Habilitación de paquete sin formato de IP** (*nx_ip_raw_packet_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-310">**IP Raw Packet Enable** (*nx_ip_raw_packet_enable*)</span></span> |
| ![Icono de recepción de paquete sin formato de I P](./media/user-guide/netx-events/image102.png)    | <span data-ttu-id="09389-312">**Recepción de paquete sin formato de IP** (*nx_ip_raw_packet_receive*)</span><span class="sxs-lookup"><span data-stu-id="09389-312">**IP Raw Packet Receive** (*nx_ip_raw_packet_receive*)</span></span> |
| ![Icono de envío de paquete sin formato de I P](./media/user-guide/netx-events/image103.png)    | <span data-ttu-id="09389-314">**Envío de paquete sin formato de IP** (*nx_ip_raw_packet_send*)</span><span class="sxs-lookup"><span data-stu-id="09389-314">**IP Raw Packet Send** (*nx_ip_raw_packet_send*)</span></span> |
| ![Icono de adición de ruta estática de I P](./media/user-guide/netx-events/image104.png)    | <span data-ttu-id="09389-316">**Adición de ruta estática de IP** (*nx_ip_static_route_add*)</span><span class="sxs-lookup"><span data-stu-id="09389-316">**IP Static Route Add** (*nx_ip_static_route_add*)</span></span> |
| ![Icono de eliminación de ruta estática de I P](./media/user-guide/netx-events/image105.png)    | <span data-ttu-id="09389-318">**Eliminación de ruta estática de IP** (*nx_ip_static_route_delete*)</span><span class="sxs-lookup"><span data-stu-id="09389-318">**IP Static Route Delete** (*nx_ip_static_route_delete)*</span></span> |
| ![Icono de comprobación de estado de I P](./media/user-guide/netx-events/image106.png)    | <span data-ttu-id="09389-320">**Comprobación de estado de IP** (*nx_ip_status_check*)</span><span class="sxs-lookup"><span data-stu-id="09389-320">**IP Status Check** (*nx_ip_status_check*)</span></span>|
| ![Icono de habilitación de I P SEC](./media/user-guide/netx-events/image107.png)    | <span data-ttu-id="09389-322">**Habilitación de IPsec** (*nx_ipsec_enable)*</span><span class="sxs-lookup"><span data-stu-id="09389-322">**IPSEC Enable** (*nx_ipsec_enable)*</span></span> |
| ![Icono de asignación de paquete](./media/user-guide/netx-events/image108.png)    | <span data-ttu-id="09389-324">**Asignación de paquete** (*nx_packet_allocate*)</span><span class="sxs-lookup"><span data-stu-id="09389-324">**Packet Allocate** (*nx_packet_allocate*)</span></span> |
| ![Icono de copia de paquete](./media/user-guide/netx-events/image109.png)    | <span data-ttu-id="09389-326">**Copia de paquete** (*nx_packet_copy*)</span><span class="sxs-lookup"><span data-stu-id="09389-326">**Packet Copy** (*nx_packet_copy*)</span></span> |
| ![Icono de anexión de datos de paquete](./media/user-guide/netx-events/image110.png)    | <span data-ttu-id="09389-328">**Anexión de datos de paquete** (*nx_packet_data_append*)</span><span class="sxs-lookup"><span data-stu-id="09389-328">**Packet Data Append** (*nx_packet_data_append*)</span></span> |
| ![Icono de desplazamiento de extracción de datos de paquete](./media/user-guide/netx-events/image111.png)    | <span data-ttu-id="09389-330">**Desplazamiento de extracción de datos de paquete** (*nx_packet_data_extract_offset*)</span><span class="sxs-lookup"><span data-stu-id="09389-330">**Packet Data Extract Offset** (*nx_packet_data_extract_offset*)</span></span> |
| ![Icono de recuperación de datos de paquete](./media/user-guide/netx-events/image112.png)    | <span data-ttu-id="09389-332">**Recuperación de datos de paquete** (*nx_packet_data_retrieve*)</span><span class="sxs-lookup"><span data-stu-id="09389-332">**Packet Data Retrieve** (*nx_packet_data_retrieve*)</span></span> |
| ![Icono de obtención de longitud de paquete](./media/user-guide/netx-events/image113.png)    | <span data-ttu-id="09389-334">**Obtención de longitud de paquete** (*nx_packet_length_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-334">**Packet Length Get** (*nx_packet_length_get*)</span></span> |
| ![Icono de creación de grupo de paquetes](./media/user-guide/netx-events/image114.png)    | <span data-ttu-id="09389-336">**Creación de grupo de paquetes** (*nx_packet_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="09389-336">**Packet Pool Create** (*nx_packet_pool_create*)</span></span> |
| ![Icono de eliminación de grupo de paquetes](./media/user-guide/netx-events/image115.png)    | <span data-ttu-id="09389-338">**Eliminación de grupo de paquetes** (*nx_packet_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="09389-338">**Packet Pool Delete** (*nx_packet_pool_delete*)</span></span> |
| ![Icono de obtención de información de grupo de paquetes](./media/user-guide/netx-events/image116.png)    | <span data-ttu-id="09389-340">**Obtención de información de grupo de paquetes** (*nx_packet_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-340">**Packet Pool Information Get** (*nx_packet_pool_info_get*)</span></span> |
| ![Icono de liberación de paquete](./media/user-guide/netx-events/image117.png)    | <span data-ttu-id="09389-342">**Liberación de paquete** (*nx_packet_release*)</span><span class="sxs-lookup"><span data-stu-id="09389-342">**Packet Release** (*nx_packet_release*)</span></span> |
| ![Icono de liberación de transmisión de paquete](./media/user-guide/netx-events/image118.png)    | <span data-ttu-id="09389-344">**Liberación de transmisión de paquete** (*nx_packet_transmit_release*)</span><span class="sxs-lookup"><span data-stu-id="09389-344">**Packet Transmit Release** (*nx_packet_transmit_release*)</span></span> |
| ![Icono de deshabilitación de R A R P](./media/user-guide/netx-events/image119.png)    | <span data-ttu-id="09389-346">**Deshabilitación de RARP** (*nx_rarp_disable*)</span><span class="sxs-lookup"><span data-stu-id="09389-346">**RARP Disable** (*nx_rarp_disable*)</span></span> |
| ![Icono de habilitación de R A R P](./media/user-guide/netx-events/image120.png)    | <span data-ttu-id="09389-348">**Habilitación de RARP** (*nx_rarp_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-348">**RARP Enable** (*nx_rarp_enable*)</span></span> |
| ![Icono de obtención de información de R A R P](./media/user-guide/netx-events/image121.png)    | <span data-ttu-id="09389-350">**Obtención de información de RARP** (*nx_rarp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-350">**RARP Information Get** (*nx_rarp_info_get*)</span></span> |
| ![Icono de inicialización del sistema](./media/user-guide/netx-events/image122.png)    | <span data-ttu-id="09389-352">**Inicialización del sistema** (*nx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="09389-352">**System Initialize** (*nx_system_initialize*)</span></span> |
| ![Icono de enlace de socket de cliente T C P](./media/user-guide/netx-events/image123.png)    | <span data-ttu-id="09389-354">**Enlace de socket de cliente TCP** (*nx_tcp_client_socket_bind*)</span><span class="sxs-lookup"><span data-stu-id="09389-354">**TCP Client Socket Bind** (*nx_tcp_client_socket_bind*)</span></span> |
| ![Icono de conexión de socket de cliente T C P](./media/user-guide/netx-events/image124.png)    | <span data-ttu-id="09389-356">**Conexión de socket de cliente TCP** (*nx_tcp_client_socket_connect*)</span><span class="sxs-lookup"><span data-stu-id="09389-356">**TCP Client Socket Connect** (*nx_tcp_client_socket_connect*)</span></span> |
| ![Icono de obtención de puerto de socket de cliente T C P](./media/user-guide/netx-events/image125.png)    | <span data-ttu-id="09389-358">**Obtención de puerto de socket de cliente TCP** (*nx_tcp_client_socket_port_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-358">**TCP Client Socket Port Get** (*nx_tcp_client_socket_port_get*)</span></span> |
| ![Icono de desenlace de socket de cliente T C P](./media/user-guide/netx-events/image126.png)    | <span data-ttu-id="09389-360">**Desenlace de socket de cliente TCP** (*nx_tcp_client_socket_unbind*)</span><span class="sxs-lookup"><span data-stu-id="09389-360">**TCP Client Socket Unbind** (*nx_tcp_client_socket_unbind*)</span></span> |
| ![Icono de habilitación de T C P](./media/user-guide/netx-events/image127.png)    | <span data-ttu-id="09389-362">**Habilitación de TCP** (*nx_tcp_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-362">**TCP Enable** (*nx_tcp_enable*)</span></span> |
| ![Icono de búsqueda de puerto libre de T C P](./media/user-guide/netx-events/image128.png)    | <span data-ttu-id="09389-364">**Búsqueda de puerto libre de TCP** (*nx_tcp_free_port_find*)</span><span class="sxs-lookup"><span data-stu-id="09389-364">**TCP Free Port Find** (*nx_tcp_free_port_find*)</span></span> |
| ![Icono de obtención de información de T C P](./media/user-guide/netx-events/image129.png)    | <span data-ttu-id="09389-366">**Obtención de información de TCP** (*nx_tcp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-366">**TCP Information Get** (*nx_tcp_info_get*)</span></span> |
| ![Icono de aceptación de socket de servidor T C P](./media/user-guide/netx-events/image130.png)    | <span data-ttu-id="09389-368">**Aceptación de socket de servidor TCP** (*nx_tcp_server_socket_accept*)</span><span class="sxs-lookup"><span data-stu-id="09389-368">**TCP Server Socket Accept** (*nx_tcp_server_socket_accept*)</span></span> |
| ![Icono de escucha de socket de servidor T C P](./media/user-guide/netx-events/image131.png)    | <span data-ttu-id="09389-370">**Escucha de socket de servidor TCP** (*nx_tcp_server_socket_listen*)</span><span class="sxs-lookup"><span data-stu-id="09389-370">**TCP Server Socket Listen** (*nx_tcp_server_socket_listen*)</span></span> |
| ![Icono de nueva escucha de socket de servidor T C P](./media/user-guide/netx-events/image132.png)    | <span data-ttu-id="09389-372">**Nueva escucha de socket de servidor TCP** (*nx_tcp_server_socket_relisten*)</span><span class="sxs-lookup"><span data-stu-id="09389-372">**TCP Server Socket Relisten** (*nx_tcp_server_socket_relisten*)</span></span> |
| ![Icono de desaceptación de socket de servidor T C P](./media/user-guide/netx-events/image133.png)    | <span data-ttu-id="09389-374">**Desaceptación de socket de servidor TCP** (*nx_tcp_server_socket_unaccept*)</span><span class="sxs-lookup"><span data-stu-id="09389-374">**TCP Server Socket Unaccept** (*nx_tcp_server_socket_unaccept*)</span></span> |
| ![Icono de abandono de escucha de socket de servidor T C P](./media/user-guide/netx-events/image134.png)    | <span data-ttu-id="09389-376">**Abandono de escucha de socket de servidor TCP** (*nx_tcp_server_socket_unlisten*)</span><span class="sxs-lookup"><span data-stu-id="09389-376">**TCP Server Socket Unlisten** (*nx_tcp_server_socket_unlisten*)</span></span> |
| ![Icono de bytes disponibles de socket T C P](./media/user-guide/netx-events/image135.png)    | <span data-ttu-id="09389-378">**Bytes disponibles de socket TCP** (*nx_tcp_socket_bytes_available*)</span><span class="sxs-lookup"><span data-stu-id="09389-378">**TCP Socket Bytes Available** (*nx_tcp_socket_bytes_available*)</span></span> |
| ![Icono de creación de socket T C P](./media/user-guide/netx-events/image136.png)    | <span data-ttu-id="09389-380">**Creación de socket TCP** (*nx_tcp_socket_create*)</span><span class="sxs-lookup"><span data-stu-id="09389-380">**TCP Socket Create** (*nx_tcp_socket_create*)</span></span> |
| ![Icono de eliminación de socket T C P](./media/user-guide/netx-events/image137.png)    | <span data-ttu-id="09389-382">**Eliminación de socket TCP** (*nx_tcp_socket_delete*)</span><span class="sxs-lookup"><span data-stu-id="09389-382">**TCP Socket Delete** (*nx_tcp_socket_delete*)</span></span> |
| ![Icono de desconexión de socket T C P](./media/user-guide/netx-events/image138.png)    | <span data-ttu-id="09389-384">**Desconexión de socket TCP** (*nx_tcp_socket_disconnect*)</span><span class="sxs-lookup"><span data-stu-id="09389-384">**TCP Socket Disconnect** (*nx_tcp_socket_disconnect*)</span></span> |
| ![Icono de obtención de información de socket T C P](./media/user-guide/netx-events/image139.png)    | <span data-ttu-id="09389-386">**Obtención de información de socket TCP** (*nx_tcp_socket_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-386">**TCP Socket Information Get** (*nx_tcp_socket_info_get*)</span></span> |
| ![Icono de obtención de M S S de socket T C P](./media/user-guide/netx-events/image140.png)    | <span data-ttu-id="09389-388">**Obtención de MSS de socket TCP** (*nx_tcp_socket_mss_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-388">**TCP Socket MSS Get** (*nx_tcp_socket_mss_get*)</span></span> |
| ![Icono de obtención de M S S de nodo del mismo nivel de socket T C P](./media/user-guide/netx-events/image141.png)    | <span data-ttu-id="09389-390">**Obtención de MSS de nodo del mismo nivel de socket TCP** (*nx_tcp_socket_mss_peer_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-390">**TCP Socket MSS Peer Get** (*nx_tcp_socket_mss_peer_get*)</span></span> |
| ![Icono de establecimiento de M S S de socket T C P](./media/user-guide/netx-events/image142.png)    | <span data-ttu-id="09389-392">**Establecimiento de MSS de socket TCP** (*nx_tcp_socket_mss_set*)</span><span class="sxs-lookup"><span data-stu-id="09389-392">**TCP Socket MSS Set** (*nx_tcp_socket_mss_set*)</span></span> |
| ![Icono de obtención de información de nodo del mismo nivel de socket T C P](./media/user-guide/netx-events/image143.png)    | <span data-ttu-id="09389-394">**Obtención de información de nodo del mismo nivel de socket TCP** (*nxd_tcp_socket_peer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-394">**TCP Socket Peer Info Get** (*nx_tcp_socket_peer_info_get*)</span></span> |
| ![Icono de recepción de socket T C P](./media/user-guide/netx-events/image144.png)    | <span data-ttu-id="09389-396">**Recepción de socket TCP** (*nx_tcp_socket_receive*)</span><span class="sxs-lookup"><span data-stu-id="09389-396">**TCP Socket Receive** (*nx_tcp_socket_receive*)</span></span> |
| ![Icono de notificación de recepción de socket T C P](./media/user-guide/netx-events/image145.png)    | <span data-ttu-id="09389-398">**Notificación de recepción de socket TCP** (*nx_tcp_socket_receive_notify*)</span><span class="sxs-lookup"><span data-stu-id="09389-398">**TCP Socket Receive Notify** (*nx_tcp_socket_receive_notify*)</span></span> |
| ![Icono de envío de socket T C P](./media/user-guide/netx-events/image146.png)    | <span data-ttu-id="09389-400">**Envío de socket TCP** (*nx_tcp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="09389-400">**TCP Socket Send** (*nx_tcp_socket_send*)</span></span> |
| ![Icono de espera de estado de socket T C P](./media/user-guide/netx-events/image147.png)    | <span data-ttu-id="09389-402">**Espera de estado de socket TCP** (*nx_tcp_socket_state_wait*)</span><span class="sxs-lookup"><span data-stu-id="09389-402">**TCP Socket State Wait** (*nx_tcp_socket_state_wait*)</span></span> |
| ![Icono de configuración de transmisión de socket T C P](./media/user-guide/netx-events/image148.png)    | <span data-ttu-id="09389-404">**Configuración de transmisión de socket TCP** (*nx_tcp_socket_transmit_configure*)</span><span class="sxs-lookup"><span data-stu-id="09389-404">**TCP Socket Transmit Configure** (*nx_tcp_socket_transmit_configure*)</span></span> |
| ![Icono de establecimiento de notificación de actualización de ventana de socket T C P](./media/user-guide/netx-events/image149.png)    | <span data-ttu-id="09389-406">**Establecimiento de notificación de actualización de ventana de socket TCP** (*nx_tcp_socket_window_update_notify_set*)</span><span class="sxs-lookup"><span data-stu-id="09389-406">**TCP Socket Window Update Notify Set** (*nx_tcp_socket_window_update_notify_set*)</span></span>  |
| ![Icono de habilitación de U D P](./media/user-guide/netx-events/image150.png)    | <span data-ttu-id="09389-408">**Habilitación de UDP** (*nx_udp_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-408">**UDP Enable** (*nx_udp_enable*)</span></span> |
| ![Icono de búsqueda de puerto libre de U D P](./media/user-guide/netx-events/image151.png)    | <span data-ttu-id="09389-410">**Búsqueda de puerto libre de UDP** (*nx_udp_free_port_find*)</span><span class="sxs-lookup"><span data-stu-id="09389-410">**UDP Free Port Find** (*nx_udp_free_port_find*)</span></span> |
| ![Icono de obtención de información de U D P](./media/user-guide/netx-events/image152.png)    | <span data-ttu-id="09389-412">**Obtención de información de UDP** (*nx_udp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-412">**UDP Information Get** (*nx_udp_info_get*)</span></span> |
| ![Icono de enlace de socket U D P](./media/user-guide/netx-events/image153.png)    | <span data-ttu-id="09389-414">**Enlace de socket UDP** (*nx_udp_socket_bind*)</span><span class="sxs-lookup"><span data-stu-id="09389-414">**UDP Socket Bind** (*nx_udp_socket_bind*)</span></span> |
| ![Icono de bytes disponibles de socket U D P](./media/user-guide/netx-events/image154.png)    | <span data-ttu-id="09389-416">**Bytes disponibles de socket UDP** (*nx_udp_socket_bytes_available*)</span><span class="sxs-lookup"><span data-stu-id="09389-416">**UDP Socket Bytes Available** (*nx_udp_socket_bytes_available*)</span></span> |
| ![Icono de deshabilitación de suma de comprobación de socket U D P](./media/user-guide/netx-events/image155.png)    | <span data-ttu-id="09389-418">**Deshabilitación de suma de comprobación de socket UDP** (*nx_udp_socket_checksum_disable*)</span><span class="sxs-lookup"><span data-stu-id="09389-418">**UDP Socket Checksum Disable** (*nx_udp_socket_checksum_disable*)</span></span> |
| ![Icono de habilitación de suma de comprobación de socket U D P](./media/user-guide/netx-events/image156.png)    | <span data-ttu-id="09389-420">**Habilitación de suma de comprobación de socket UDP** (*nx_udp_socket_checksum_enable*)</span><span class="sxs-lookup"><span data-stu-id="09389-420">**UDP Socket Checksum Enable** *(nx_udp_socket_checksum_enable)*</span></span> |
| ![Icono de creación de socket U D P](./media/user-guide/netx-events/image157.png)    | <span data-ttu-id="09389-422">**Creación de socket UDP** (*nx_udp_socket_create*)</span><span class="sxs-lookup"><span data-stu-id="09389-422">**UDP Socket Create** (*nx_udp_socket_create*)</span></span> |
| ![Icono de eliminación de socket U D P](./media/user-guide/netx-events/image158.png)    | <span data-ttu-id="09389-424">**Eliminación de socket UDP** (*nx_udp_socket_delete*)</span><span class="sxs-lookup"><span data-stu-id="09389-424">**UDP Socket Delete** (*nx_udp_socket_delete*)</span></span> |
| ![Icono de obtención de información de socket U D P](./media/user-guide/netx-events/image159.png)    | <span data-ttu-id="09389-426">**Obtención de información de socket UDP** (*nx_udp_socket_info_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-426">**UDP Socket Information Get** (*nx_udp_socket_info_get*)</span></span> |
| ![Icono de establecimiento de interfaz de socket U D P](./media/user-guide/netx-events/image160.png)    | <span data-ttu-id="09389-428">**Establecimiento de interfaz de socket UDP** (*nx_udp_socket_interface_set*)</span><span class="sxs-lookup"><span data-stu-id="09389-428">**UDP Socket Interface Set** (*nx_udp_socket_interface_set*)</span></span> |
| ![Icono de obtención de puerto de socket U D P](./media/user-guide/netx-events/image161.png)    | <span data-ttu-id="09389-430">**Obtención de puerto de socket UDP** (*nx_udp_socket_port_get*)</span><span class="sxs-lookup"><span data-stu-id="09389-430">**UDP Socket Port Get** (*nx_udp_socket_port_get*)</span></span> |
| ![Icono de recepción de socket U D P](./media/user-guide/netx-events/image162.png)    | <span data-ttu-id="09389-432">**Recepción de socket UDP** (*nx_udp_socket_receive*)</span><span class="sxs-lookup"><span data-stu-id="09389-432">**UDP Socket Receive** (*nx_udp_socket_receive*)</span></span> |
| ![Icono de notificación de recepción de socket U D P](./media/user-guide/netx-events/image163.png)    | <span data-ttu-id="09389-434">**Notificación de recepción de socket UDP** (*nx_udp_socket_receive_notify*)</span><span class="sxs-lookup"><span data-stu-id="09389-434">**UDP Socket Receive Notify** (*nx_udp_socket_receive_notify*)</span></span> |
| ![Icono de envío de socket U D P](./media/user-guide/netx-events/image164.png)    | <span data-ttu-id="09389-436">**Envío de socket UDP** (*nx_udp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="09389-436">**UDP Socket Send** (*nx_udp_socket_send*)</span></span> |
| ![Icono de desenlace de socket U D P](./media/user-guide/netx-events/image165.png)    | <span data-ttu-id="09389-438">**Desenlace de socket UDP** (*nx_udp_socket_unbind*)</span><span class="sxs-lookup"><span data-stu-id="09389-438">**UDP Socket Unbind** (*nx_udp_socket_unbind*)</span></span> |
| ![Icono de extracción de origen de U D P](./media/user-guide/netx-events/image166.png)    | <span data-ttu-id="09389-440">**Extracción de origen de UDP** (*nx_udp_source_extract*)</span><span class="sxs-lookup"><span data-stu-id="09389-440">**UDP Source Extract** (*nx_udp_source_extract*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="09389-441">Descripciones de eventos</span><span class="sxs-lookup"><span data-stu-id="09389-441">Event Descriptions</span></span>

<span data-ttu-id="09389-442">En las secciones siguientes se describen los eventos de seguimiento de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-442">The following pages describe the NetX Trace Events.</span></span>

### <a name="internal-arp-request-receive"></a><span data-ttu-id="09389-443">Recepción de solicitud ARP interna</span><span class="sxs-lookup"><span data-stu-id="09389-443">Internal ARP Request Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="09389-444">Recepción de solicitud ARP interna</span><span class="sxs-lookup"><span data-stu-id="09389-444">Internal ARP request receive</span></span>

<span data-ttu-id="09389-445">**Icono** ![Icono de recepción de solicitud A R P interna](./media/user-guide/netx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="09389-445">**Icon** ![Internal ARP request receive icon](./media/user-guide/netx-events/image1.png)</span></span>

<span data-ttu-id="09389-446">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-446">**Description**</span></span>

<span data-ttu-id="09389-447">Este evento representa un evento interno de recepción de solicitud ARP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-447">This event represents an internal NetX ARP request receive event.</span></span>

<span data-ttu-id="09389-448">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-448">**Information Fields**</span></span>

- <span data-ttu-id="09389-449">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-449">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-450">Campo de información 2: dirección IP de origen</span><span class="sxs-lookup"><span data-stu-id="09389-450">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="09389-451">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-451">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-452">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-452">Info Field 4: Not used</span></span>

### <a name="internal-arp-request-send"></a><span data-ttu-id="09389-453">Envío de solicitud ARP interno</span><span class="sxs-lookup"><span data-stu-id="09389-453">Internal ARP Request Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="09389-454">Envío de solicitud ARP interno</span><span class="sxs-lookup"><span data-stu-id="09389-454">Internal ARP request send</span></span>

<span data-ttu-id="09389-455">**Icono** ![Icono de envío de solicitud A R P interno](./media/user-guide/netx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="09389-455">**Icon** ![Internal ARP request send icon](./media/user-guide/netx-events/image2.png)</span></span>

<span data-ttu-id="09389-456">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-456">**Description**</span></span>

<span data-ttu-id="09389-457">Este evento representa un evento interno de envío de solicitud ARP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-457">This event represents an internal NetX ARP request send event.</span></span>

<span data-ttu-id="09389-458">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-458">**Information Fields**</span></span>

- <span data-ttu-id="09389-459">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-459">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-460">Campo de información 2: dirección IP de destino</span><span class="sxs-lookup"><span data-stu-id="09389-460">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="09389-461">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-461">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-462">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-462">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-receive"></a><span data-ttu-id="09389-463">Recepción de respuesta ARP interna</span><span class="sxs-lookup"><span data-stu-id="09389-463">Internal ARP Response Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="09389-464">Recepción de solicitud ARP interna</span><span class="sxs-lookup"><span data-stu-id="09389-464">Internal ARP request receive</span></span>

<span data-ttu-id="09389-465">**Icono** ![Icono de recepción de solicitud A R P interna](./media/user-guide/netx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="09389-465">**Icon** ![The Internal ARP request receive icon](./media/user-guide/netx-events/image3.png)</span></span>

<span data-ttu-id="09389-466">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-466">**Description**</span></span>

<span data-ttu-id="09389-467">Este evento representa un evento interno de recepción de respuesta ARP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-467">This event represents an internal NetX ARP response receive event.</span></span>

<span data-ttu-id="09389-468">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-468">**Information Fields**</span></span>

- <span data-ttu-id="09389-469">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-469">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-470">Campo de información 2: dirección IP de origen</span><span class="sxs-lookup"><span data-stu-id="09389-470">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="09389-471">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-471">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-472">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-472">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-send"></a><span data-ttu-id="09389-473">Envío de respuesta ARP interno</span><span class="sxs-lookup"><span data-stu-id="09389-473">Internal ARP Response Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="09389-474">Envío de solicitud ARP interno</span><span class="sxs-lookup"><span data-stu-id="09389-474">Internal ARP request send</span></span>

<span data-ttu-id="09389-475">**Icono** ![Icono de envío de solicitud A R P interno](./media/user-guide/netx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="09389-475">**Icon** ![The Internal ARP request send icon](./media/user-guide/netx-events/image4.png)</span></span>

<span data-ttu-id="09389-476">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-476">**Description**</span></span>

<span data-ttu-id="09389-477">Este evento representa un evento interno de envío de respuesta de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-477">This event represents an internal NetX response send event.</span></span>

<span data-ttu-id="09389-478">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-478">**Information Fields**</span></span>

- <span data-ttu-id="09389-479">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-479">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-480">Campo de información 2: dirección IP de destino</span><span class="sxs-lookup"><span data-stu-id="09389-480">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="09389-481">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-481">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-482">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-482">Info Field 4: Not used</span></span>

### <a name="internal-icmp-receive"></a><span data-ttu-id="09389-483">Recepción de ICMP interna</span><span class="sxs-lookup"><span data-stu-id="09389-483">Internal ICMP Receive</span></span> 

#### <a name="internal-icmp-receive"></a><span data-ttu-id="09389-484">Recepción de ICMP interna</span><span class="sxs-lookup"><span data-stu-id="09389-484">Internal ICMP receive</span></span>

<span data-ttu-id="09389-485">**Icono** ![Icono de recepción de I C M P interna](./media/user-guide/netx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="09389-485">**Icon** ![Internal I C M P receive icon](./media/user-guide/netx-events/image5.png)</span></span>

<span data-ttu-id="09389-486">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-486">**Description**</span></span>

<span data-ttu-id="09389-487">Este evento representa un evento interno de recepción de ICMP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-487">This event represents an internal NetX ICMP receive event.</span></span>

<span data-ttu-id="09389-488">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-488">**Information Fields**</span></span>

- <span data-ttu-id="09389-489">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-489">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-490">Campo de información 2: dirección IP de origen</span><span class="sxs-lookup"><span data-stu-id="09389-490">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="09389-491">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-491">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-492">Campo de información 4: palabra 0 del encabezado ICMP</span><span class="sxs-lookup"><span data-stu-id="09389-492">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-icmp-send"></a><span data-ttu-id="09389-493">Envío de ICMP interno</span><span class="sxs-lookup"><span data-stu-id="09389-493">Internal ICMP Send</span></span> 

#### <a name="internal-icmp-send"></a><span data-ttu-id="09389-494">Envío de ICMP interno</span><span class="sxs-lookup"><span data-stu-id="09389-494">Internal ICMP send</span></span>

<span data-ttu-id="09389-495">**Icono** ![Icono de envío de I C M P interno](./media/user-guide/netx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="09389-495">**Icon** ![Internal I C M P send icon](./media/user-guide/netx-events/image6.png)</span></span>

<span data-ttu-id="09389-496">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-496">**Description**</span></span>

<span data-ttu-id="09389-497">Este evento representa un evento interno de envío de ICMP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-497">This event represents an internal NetX ICMP send event.</span></span>

<span data-ttu-id="09389-498">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-498">**Information Fields**</span></span>

- <span data-ttu-id="09389-499">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-499">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-500">Campo de información 2: dirección IP de destino</span><span class="sxs-lookup"><span data-stu-id="09389-500">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="09389-501">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-501">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-502">Campo de información 4: palabra 0 del encabezado ICMP</span><span class="sxs-lookup"><span data-stu-id="09389-502">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-igmp-receive"></a><span data-ttu-id="09389-503">Recepción de IGMP interna</span><span class="sxs-lookup"><span data-stu-id="09389-503">Internal IGMP Receive</span></span> 

#### <a name="internal-igmp-receive"></a><span data-ttu-id="09389-504">Recepción de IGMP interna</span><span class="sxs-lookup"><span data-stu-id="09389-504">Internal IGMP receive</span></span>

<span data-ttu-id="09389-505">**Icono** ![Icono de recepción de I G M P interna](./media/user-guide/netx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="09389-505">**Icon** ![Internal I G M P receive icon](./media/user-guide/netx-events/image7.png)</span></span>

<span data-ttu-id="09389-506">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-506">**Description**</span></span>

<span data-ttu-id="09389-507">Este evento representa un evento interno de recepción de IGMP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-507">This event represents an internal NetX IGMP receive event.</span></span>

<span data-ttu-id="09389-508">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-508">**Information Fields**</span></span>

- <span data-ttu-id="09389-509">Campo de información 1: puntero de IP</span><span class="sxs-lookup"><span data-stu-id="09389-509">Info Field 1: IP Pointer</span></span>
- <span data-ttu-id="09389-510">Campo de información 2: dirección IP de origen</span><span class="sxs-lookup"><span data-stu-id="09389-510">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="09389-511">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-511">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-512">Campo de información 4: palabra 0 del encabezado IGMP</span><span class="sxs-lookup"><span data-stu-id="09389-512">Info Field 4: Word 0 of IGMP header</span></span>

### <a name="internal-ip-receive"></a><span data-ttu-id="09389-513">Recepción de IP interna</span><span class="sxs-lookup"><span data-stu-id="09389-513">Internal IP Receive</span></span> 

#### <a name="internal-ip-receive"></a><span data-ttu-id="09389-514">Recepción de IP interna</span><span class="sxs-lookup"><span data-stu-id="09389-514">Internal IP receive</span></span>

<span data-ttu-id="09389-515">**Icono** ![Icono de recepción de I P interna](./media/user-guide/netx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="09389-515">**Icon** ![Internal I P receive icon](./media/user-guide/netx-events/image8.png)</span></span>

<span data-ttu-id="09389-516">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-516">**Description**</span></span>

<span data-ttu-id="09389-517">Este evento representa un evento interno de recepción de IP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-517">This event represents an internal NetX IP receive event.</span></span>

<span data-ttu-id="09389-518">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-518">**Information Fields**</span></span>

- <span data-ttu-id="09389-519">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-519">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-520">Campo de información 2: dirección IP de origen</span><span class="sxs-lookup"><span data-stu-id="09389-520">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="09389-521">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-521">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-522">Campo de información 4: longitud del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-522">Info Field 4: Packet length</span></span>

### <a name="internal-ip-send"></a><span data-ttu-id="09389-523">Envío de IP interno</span><span class="sxs-lookup"><span data-stu-id="09389-523">Internal IP Send</span></span>

#### <a name="internal-ip-send"></a><span data-ttu-id="09389-524">Envío de IP interno</span><span class="sxs-lookup"><span data-stu-id="09389-524">Internal IP send</span></span>

<span data-ttu-id="09389-525">**Icono** ![Icono de envío de I P interno](./media/user-guide/netx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="09389-525">**Icon** ![Internal I P send icon](./media/user-guide/netx-events/image9.png)</span></span>

<span data-ttu-id="09389-526">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-526">**Description**</span></span>

<span data-ttu-id="09389-527">Este evento representa un evento interno de envío de IP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-527">This event represents an internal NetX IP send event.</span></span>

<span data-ttu-id="09389-528">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-528">**Information Fields**</span></span>

- <span data-ttu-id="09389-529">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-529">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-530">Campo de información 2: dirección IP de destino</span><span class="sxs-lookup"><span data-stu-id="09389-530">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="09389-531">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-531">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-532">Campo de información 4: longitud del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-532">Info Field 4: Packet length</span></span>

### <a name="internal-tcp-data-receive"></a><span data-ttu-id="09389-533">Recepción de datos de TCP interna</span><span class="sxs-lookup"><span data-stu-id="09389-533">Internal TCP Data Receive</span></span> 

#### <a name="internal-tcp-data-receive"></a><span data-ttu-id="09389-534">Recepción de datos de TCP interna</span><span class="sxs-lookup"><span data-stu-id="09389-534">Internal TCP Data Receive</span></span>

<span data-ttu-id="09389-535">**Icono** ![Icono de recepción de datos de T C P interna](./media/user-guide/netx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="09389-535">**Icon** ![Internal T C P data receive icon](./media/user-guide/netx-events/image10.png)</span></span>

<span data-ttu-id="09389-536">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-536">**Description**</span></span>

<span data-ttu-id="09389-537">Este evento representa un evento interno de recepción de datos TCP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-537">This event represents an internal NetX TCP data receive event.</span></span>

<span data-ttu-id="09389-538">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-538">**Information Fields**</span></span>

- <span data-ttu-id="09389-539">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-539">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-540">Campo de información 2: dirección IP de origen</span><span class="sxs-lookup"><span data-stu-id="09389-540">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="09389-541">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-541">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-542">Campo de información 4: número de secuencia de recepción</span><span class="sxs-lookup"><span data-stu-id="09389-542">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-data-send"></a><span data-ttu-id="09389-543">Envío de datos de TCP interno</span><span class="sxs-lookup"><span data-stu-id="09389-543">Internal TCP data send</span></span> 

#### <a name="internal-tcp-data-send"></a><span data-ttu-id="09389-544">Envío de datos de TCP interno</span><span class="sxs-lookup"><span data-stu-id="09389-544">Internal TCP Data Send</span></span>

<span data-ttu-id="09389-545">**Icono** ![Icono de envío de datos de T C P interno](./media/user-guide/netx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="09389-545">**Icon** ![Internal T C P data send icon](./media/user-guide/netx-events/image11.png)</span></span>

<span data-ttu-id="09389-546">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-546">**Description**</span></span>

<span data-ttu-id="09389-547">Este evento representa un evento interno de envío de datos TCP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-547">This event represents an internal NetX TCP data send event.</span></span>

<span data-ttu-id="09389-548">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-548">**Information Fields**</span></span>

- <span data-ttu-id="09389-549">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-549">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-550">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-550">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-551">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-551">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-552">Campo de información 4: número de secuencia de transmisión</span><span class="sxs-lookup"><span data-stu-id="09389-552">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="09389-553">Recepción de TCP FIN interna</span><span class="sxs-lookup"><span data-stu-id="09389-553">Internal TCP FIN Receive</span></span> 

#### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="09389-554">Recepción de TCP FIN interna</span><span class="sxs-lookup"><span data-stu-id="09389-554">Internal TCP fin receive</span></span>

<span data-ttu-id="09389-555">**Icono** ![Icono de recepción de T C P F I N interna](./media/user-guide/netx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="09389-555">**Icon** ![Internal T C P F I N receive icon](./media/user-guide/netx-events/image12.png)</span></span>

<span data-ttu-id="09389-556">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-556">**Description**</span></span>

<span data-ttu-id="09389-557">Este evento representa un evento interno de recepción de TCP FIN de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-557">This event represents an internal NetX TCP FIN receive event.</span></span>

<span data-ttu-id="09389-558">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-558">**Information Fields**</span></span> 

- <span data-ttu-id="09389-559">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-559">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-560">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-560">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-561">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-561">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-562">Campo de información 4: número de secuencia de recepción</span><span class="sxs-lookup"><span data-stu-id="09389-562">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-fin-send"></a><span data-ttu-id="09389-563">Envío de TCP FIN interno</span><span class="sxs-lookup"><span data-stu-id="09389-563">Internal TCP FIN Send</span></span> 

#### <a name="internal-tcp-fin-send"></a><span data-ttu-id="09389-564">Envío de TCP FIN interno</span><span class="sxs-lookup"><span data-stu-id="09389-564">Internal TCP fin send</span></span>

<span data-ttu-id="09389-565">**Icono** ![Icono de envío de T C P F I N interno](./media/user-guide/netx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="09389-565">**Icon** ![Internal T C P F I N send icon](./media/user-guide/netx-events/image13.png)</span></span>

<span data-ttu-id="09389-566">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-566">**Description**</span></span>

<span data-ttu-id="09389-567">Este evento representa un evento interno de envío de TCP FIN de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-567">This event represents an internal NetX TCP FIN send event.</span></span>

<span data-ttu-id="09389-568">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-568">**Information Fields**</span></span>

- <span data-ttu-id="09389-569">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-569">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-570">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-570">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-571">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-571">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-572">Campo de información 4: número de secuencia de transmisión</span><span class="sxs-lookup"><span data-stu-id="09389-572">Info Field 4:Transmit sequence number</span></span>

### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="09389-573">Recepción de TCP RST interna</span><span class="sxs-lookup"><span data-stu-id="09389-573">Internal TCP RST Receive</span></span> 

#### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="09389-574">Recepción de TCP RST interna</span><span class="sxs-lookup"><span data-stu-id="09389-574">Internal TCP RST receive</span></span>

<span data-ttu-id="09389-575">**Icono** ![Icono de recepción de T C P R S T interna](./media/user-guide/netx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="09389-575">**Icon** ![Internal T C P R S T receive icon](./media/user-guide/netx-events/image14.png)</span></span>

<span data-ttu-id="09389-576">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-576">**Description**</span></span>

<span data-ttu-id="09389-577">Este evento representa un evento interno de recepción de TCP RST de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-577">This event represents an internal NetX TCP reset receive event.</span></span>

<span data-ttu-id="09389-578">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-578">**Information Fields**</span></span>

- <span data-ttu-id="09389-579">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-579">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="09389-580">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-580">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="09389-581">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-581">Info Field 3: Pointer to packet.</span></span>
- <span data-ttu-id="09389-582">Campo de información 4: número de secuencia de recepción</span><span class="sxs-lookup"><span data-stu-id="09389-582">Info Field 4: Receive sequence number.</span></span>

### <a name="internal-tcp-rst-send"></a><span data-ttu-id="09389-583">Envío de TCP RST interno</span><span class="sxs-lookup"><span data-stu-id="09389-583">Internal TCP RST Send</span></span> 

#### <a name="internal-tcp-rst-send"></a><span data-ttu-id="09389-584">Envío de TCP RST interno</span><span class="sxs-lookup"><span data-stu-id="09389-584">Internal TCP RST send</span></span>

<span data-ttu-id="09389-585">**Icono** ![Icono de envío de T C P R S T interno](./media/user-guide/netx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="09389-585">**Icon** ![Internal T C P R S T send icon](./media/user-guide/netx-events/image15.png)</span></span>

<span data-ttu-id="09389-586">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-586">**Description**</span></span>

<span data-ttu-id="09389-587">Este evento representa un evento interno de envío de TCP RST de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-587">This event represents an internal NetX TCP reset send event.</span></span>

<span data-ttu-id="09389-588">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-588">**Information Fields**</span></span>

- <span data-ttu-id="09389-589">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-589">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-590">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-590">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-591">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-591">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-592">Campo de información 4: número de secuencia de transmisión</span><span class="sxs-lookup"><span data-stu-id="09389-592">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="09389-593">Recepción de TCP SYN interna</span><span class="sxs-lookup"><span data-stu-id="09389-593">Internal TCP SYN Receive</span></span> 

#### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="09389-594">Recepción de TCP SYN interna</span><span class="sxs-lookup"><span data-stu-id="09389-594">Internal TCP SYN receive</span></span>

<span data-ttu-id="09389-595">**Icono** ![Icono de recepción de T C P S Y N interna](./media/user-guide/netx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="09389-595">**Icon** ![Internal T C P S Y N receive icon](./media/user-guide/netx-events/image16.png)</span></span>

<span data-ttu-id="09389-596">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-596">**Description**</span></span>

<span data-ttu-id="09389-597">Este evento representa un evento interno de recepción de TCP SYN de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-597">This event represents an internal NetX TCP SYN receive event.</span></span>

<span data-ttu-id="09389-598">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-598">**Information Fields**</span></span>

- <span data-ttu-id="09389-599">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-599">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-600">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-600">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-601">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-601">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-602">Campo de información 4: número de secuencia de recepción</span><span class="sxs-lookup"><span data-stu-id="09389-602">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-syn-send"></a><span data-ttu-id="09389-603">Envío de TCP SYN interno</span><span class="sxs-lookup"><span data-stu-id="09389-603">Internal TCP SYN Send</span></span> 

#### <a name="internal-tcp-syn-send"></a><span data-ttu-id="09389-604">Envío de TCP SYN interno</span><span class="sxs-lookup"><span data-stu-id="09389-604">Internal TCP SYN send</span></span>

<span data-ttu-id="09389-605">**Icono** ![Icono de envío de T C P S Y N interno](./media/user-guide/netx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="09389-605">**Icon** ![Internal T C P S Y N send icon](./media/user-guide/netx-events/image17.png)</span></span>

<span data-ttu-id="09389-606">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-606">**Description**</span></span>

<span data-ttu-id="09389-607">Este evento representa un evento interno de envío de TCP SYN de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-607">This event represents an internal NetX TCP SYN send event.</span></span>

<span data-ttu-id="09389-608">Campos de información</span><span class="sxs-lookup"><span data-stu-id="09389-608">Information Fields</span></span> 

- <span data-ttu-id="09389-609">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-609">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-610">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-610">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-611">Campo de información 3: puntero al paquete Campo de información 4: número de secuencia de transmisión</span><span class="sxs-lookup"><span data-stu-id="09389-611">Info Field 3: Pointer to packet -Info Field 4: Transmit sequence number</span></span>

### <a name="internal-udp-receive"></a><span data-ttu-id="09389-612">Recepción de UDP interna</span><span class="sxs-lookup"><span data-stu-id="09389-612">Internal UDP Receive</span></span> 

#### <a name="internal-udp-receive"></a><span data-ttu-id="09389-613">Recepción de UDP interna</span><span class="sxs-lookup"><span data-stu-id="09389-613">Internal UDP receive</span></span>

<span data-ttu-id="09389-614">**Icono** ![Icono de recepción de U D P interna](./media/user-guide/netx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="09389-614">**Icon** ![Internal U D P receive icon](./media/user-guide/netx-events/image18.png)</span></span>

<span data-ttu-id="09389-615">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-615">**Description**</span></span>

<span data-ttu-id="09389-616">Este evento representa un evento interno de recepción de UDP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-616">This event represents an internal NetX UDP receive event.</span></span>

<span data-ttu-id="09389-617">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-617">**Information Fields**</span></span> 

- <span data-ttu-id="09389-618">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-618">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-619">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-619">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-620">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-620">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-621">Campo de información 4: palabra 0 del encabezado UDP</span><span class="sxs-lookup"><span data-stu-id="09389-621">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-udp-send"></a><span data-ttu-id="09389-622">Envío de UDP interno</span><span class="sxs-lookup"><span data-stu-id="09389-622">Internal UDP Send</span></span> 

#### <a name="internal-udp-send"></a><span data-ttu-id="09389-623">Envío de UDP interno</span><span class="sxs-lookup"><span data-stu-id="09389-623">Internal UDP send</span></span>

<span data-ttu-id="09389-624">**Icono** ![Icono de envío de U D P interno](./media/user-guide/netx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="09389-624">**Icon** ![Internal U D P send icon](./media/user-guide/netx-events/image19.png)</span></span>

<span data-ttu-id="09389-625">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-625">**Description**</span></span>

<span data-ttu-id="09389-626">Este evento representa un evento interno de envío de UDP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-626">This event represents an internal NetX UDP send event.</span></span>

<span data-ttu-id="09389-627">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-627">**Information Fields**</span></span>

- <span data-ttu-id="09389-628">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-628">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-629">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-629">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-630">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-630">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-631">Campo de información 4: palabra 0 del encabezado UDP</span><span class="sxs-lookup"><span data-stu-id="09389-631">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-rarp-receive"></a><span data-ttu-id="09389-632">Recepción de RARP interna</span><span class="sxs-lookup"><span data-stu-id="09389-632">Internal RARP Receive</span></span> 

#### <a name="internal-rarp-receive"></a><span data-ttu-id="09389-633">Recepción de RARP interna</span><span class="sxs-lookup"><span data-stu-id="09389-633">Internal RARP receive</span></span> 

<span data-ttu-id="09389-634">**Icono** ![Icono de recepción de R A R P interna](./media/user-guide/netx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="09389-634">**Icon** ![Internal R A R P receive icon](./media/user-guide/netx-events/image20.png)</span></span>

<span data-ttu-id="09389-635">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-635">**Description**</span></span>

<span data-ttu-id="09389-636">Este evento representa un evento interno de recepción de RARP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-636">This event represents an internal NetX RARP receive event.</span></span>

<span data-ttu-id="09389-637">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-637">**Information Fields**</span></span> 

- <span data-ttu-id="09389-638">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-638">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-639">Campo de información 2: dirección IP de destino</span><span class="sxs-lookup"><span data-stu-id="09389-639">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="09389-640">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-640">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-641">Campo de información 4: palabra 1 del encabezado RARP</span><span class="sxs-lookup"><span data-stu-id="09389-641">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-rarp-send"></a><span data-ttu-id="09389-642">Envío de RARP interno</span><span class="sxs-lookup"><span data-stu-id="09389-642">Internal RARP Send</span></span> 

#### <a name="internal-rarp-send"></a><span data-ttu-id="09389-643">Envío de RARP interno</span><span class="sxs-lookup"><span data-stu-id="09389-643">Internal RARP send</span></span> 

<span data-ttu-id="09389-644">**Icono** ![Icono de envío de R A R P interno](./media/user-guide/netx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="09389-644">**Icon** ![Internal R A R P send icon](./media/user-guide/netx-events/image21.png)</span></span>

<span data-ttu-id="09389-645">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-645">**Description**</span></span>

<span data-ttu-id="09389-646">Este evento representa un evento interno de envío de RARP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-646">This event represents an internal NetX RARP send event.</span></span>

<span data-ttu-id="09389-647">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-647">**Information Fields**</span></span>

- <span data-ttu-id="09389-648">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-648">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-649">Campo de información 2: dirección IP de destino</span><span class="sxs-lookup"><span data-stu-id="09389-649">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="09389-650">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-650">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-651">Campo de información 4: palabra 1 del encabezado RARP</span><span class="sxs-lookup"><span data-stu-id="09389-651">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-tcp-retry"></a><span data-ttu-id="09389-652">Reintento de TCP interno</span><span class="sxs-lookup"><span data-stu-id="09389-652">Internal TCP Retry</span></span> 

#### <a name="internal-tcp-retry"></a><span data-ttu-id="09389-653">Reintento de TCP interno</span><span class="sxs-lookup"><span data-stu-id="09389-653">Internal TCP retry</span></span> 

<span data-ttu-id="09389-654">**Icono** ![Icono de reintento de T C P interno](./media/user-guide/netx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="09389-654">**Icon** ![Internal T C P retry icon](./media/user-guide/netx-events/image22.png)</span></span>

<span data-ttu-id="09389-655">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-655">**Description**</span></span>

<span data-ttu-id="09389-656">Este evento representa un evento interno de reintento de TCP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-656">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="09389-657">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-657">**Information Fields**</span></span>
- <span data-ttu-id="09389-658">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-658">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-659">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-659">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-660">Campo de información 3: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-660">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="09389-661">Campo de información 4: número de reintentos</span><span class="sxs-lookup"><span data-stu-id="09389-661">Info Field 4: Number of retries</span></span>

### <a name="internal-tcp-state-change"></a><span data-ttu-id="09389-662">Cambio de estado de TCP interno</span><span class="sxs-lookup"><span data-stu-id="09389-662">Internal TCP State Change</span></span> 

#### <a name="internal-tcp-state-change"></a><span data-ttu-id="09389-663">Cambio de estado de TCP interno</span><span class="sxs-lookup"><span data-stu-id="09389-663">Internal TCP state change</span></span> 

<span data-ttu-id="09389-664">**Icono** ![Icono de cambio de estado de T C P interno](./media/user-guide/netx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="09389-664">**Icon** ![Internal T C P state change icon](./media/user-guide/netx-events/image23.png)</span></span>

<span data-ttu-id="09389-665">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-665">**Description**</span></span>

<span data-ttu-id="09389-666">Este evento representa un evento interno de cambio de estado de socket TCP de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-666">This event represents an internal NetX TCP socket state change event.</span></span>

<span data-ttu-id="09389-667">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-667">**Information Fields**</span></span>

- <span data-ttu-id="09389-668">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-668">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-669">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-669">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-670">Campo de información 3: estado anterior</span><span class="sxs-lookup"><span data-stu-id="09389-670">Info Field 3: Previous state</span></span>
- <span data-ttu-id="09389-671">Campo de información 4: nuevo estado</span><span class="sxs-lookup"><span data-stu-id="09389-671">Info Field 4: New state</span></span>

### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="09389-672">Envío de paquete de controladores de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-672">Internal I/O Driver Packet Send</span></span> 

#### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="09389-673">Envío de paquete de controladores de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-673">Internal I/O driver packet send</span></span>

<span data-ttu-id="09389-674">**Icono** ![Icono de envío de paquete de controladores de E/S interno](./media/user-guide/netx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="09389-674">**Icon** ![Internal I / O driver packet send icon](./media/user-guide/netx-events/image24.png)</span></span>

<span data-ttu-id="09389-675">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-675">**Description**</span></span>

<span data-ttu-id="09389-676">Este evento representa un evento interno de envío de paquete de controladores de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-676">This event represents an internal NetX I/O driver packet send event.</span></span>

<span data-ttu-id="09389-677">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-677">**Information Fields**</span></span>

- <span data-ttu-id="09389-678">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-678">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-679">Campo de información 2: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-679">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="09389-680">Campo de información 3: tamaño del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-680">Info Field 3: Packet size</span></span>
- <span data-ttu-id="09389-681">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-681">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="09389-682">Inicialización de controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-682">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="09389-683">Inicialización de controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-683">Internal I/O driver initialize</span></span>

<span data-ttu-id="09389-684">**Icono** ![Icono de inicialización de controlador de E/S interna](./media/user-guide/netx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="09389-684">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/netx-events/image25.png)</span></span>

<span data-ttu-id="09389-685">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-685">**Description**</span></span>

<span data-ttu-id="09389-686">Este evento representa un evento interno de inicialización del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-686">This event represents an internal NetX I/O driver initialize event.</span></span>

<span data-ttu-id="09389-687">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-687">**Information Fields**</span></span>

- <span data-ttu-id="09389-688">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-688">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="09389-689">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-689">Info Field 2: Not used.</span></span>
- <span data-ttu-id="09389-690">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-690">Info Field 3: Not used.</span></span>
- <span data-ttu-id="09389-691">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-691">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="09389-692">Habilitación del vínculo de controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-692">Internal I/O Driver Link Enable</span></span> 

#### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="09389-693">Habilitación del vínculo de controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-693">Internal I/O driver link enable</span></span>

<span data-ttu-id="09389-694">**Icono** ![Icono de habilitación del vínculo de controlador de E/S interna](./media/user-guide/netx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="09389-694">**Icon** ![Internal I / O driver link enable icon](./media/user-guide/netx-events/image26.png)</span></span>

<span data-ttu-id="09389-695">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-695">**Description**</span></span>

<span data-ttu-id="09389-696">Este evento representa un evento interno de habilitación del vínculo de controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-696">This event represents an internal NetX I/O driver link enable event.</span></span>

<span data-ttu-id="09389-697">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-697">**Information Fields**</span></span>

- <span data-ttu-id="09389-698">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-698">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="09389-699">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-699">Info Field 2: Not used.</span></span>
- <span data-ttu-id="09389-700">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-700">Info Field 3: Not used.</span></span>
- <span data-ttu-id="09389-701">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-701">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="09389-702">Deshabilitación del vínculo de controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-702">Internal I/O Driver Link Disable</span></span> 

#### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="09389-703">Deshabilitación del vínculo de controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-703">Internal I/O driver link disable</span></span>

<span data-ttu-id="09389-704">**Icono** ![Icono de deshabilitación del vínculo de controlador de E/S interna](./media/user-guide/netx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="09389-704">**Icon** ![Internal I / O driver link disable icon](./media/user-guide/netx-events/image27.png)</span></span>

<span data-ttu-id="09389-705">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-705">**Description**</span></span>

<span data-ttu-id="09389-706">Este evento representa un evento interno de deshabilitación del vínculo de controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-706">This event represents an internal NetX I/O driver link disable event.</span></span>

<span data-ttu-id="09389-707">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-707">**Information Fields**</span></span>

- <span data-ttu-id="09389-708">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-708">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-709">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-709">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-710">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-710">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-711">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-711">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="09389-712">Difusión del paquete de controladores de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-712">Internal I/O Driver Packet Broadcast</span></span> 

#### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="09389-713">Difusión del paquete de controladores de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-713">Internal I/O driver packet broadcast</span></span>

<span data-ttu-id="09389-714">**Icono** ![Icono de difusión de paquete de controladores de E/S interna](./media/user-guide/netx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="09389-714">**Icon** ![Internal I / O driver packet broadcast icon](./media/user-guide/netx-events/image28.png)</span></span>

<span data-ttu-id="09389-715">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-715">**Description**</span></span>

<span data-ttu-id="09389-716">Este evento representa un evento interno de difusión del paquete de controladores de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-716">This event represents an internal NetX I/O driver packet broadcast event.</span></span>

<span data-ttu-id="09389-717">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-717">**Information Fields**</span></span>

- <span data-ttu-id="09389-718">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-718">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-719">Campo de información 2: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-719">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="09389-720">Campo de información 3: tamaño del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-720">Info Field 3: Packet size</span></span>
- <span data-ttu-id="09389-721">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-721">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="09389-722">Envío de ARP del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-722">Internal I/O Driver ARP Send</span></span> 

#### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="09389-723">Envío de ARP del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-723">Internal I/O driver ARP send</span></span>

<span data-ttu-id="09389-724">**Icono** ![Icono de envío de A R P del controlador de E/S interno](./media/user-guide/netx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="09389-724">**Icon** ![Internal I / O driver ARP send icon](./media/user-guide/netx-events/image29.png)</span></span>

<span data-ttu-id="09389-725">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-725">**Description**</span></span>

<span data-ttu-id="09389-726">Este evento representa un evento interno de envío de ARP del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-726">This event represents an internal NetX I/O driver ARP send event.</span></span>

<span data-ttu-id="09389-727">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-727">**Information Fields**</span></span>

- <span data-ttu-id="09389-728">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-728">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-729">Campo de información 2: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-729">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="09389-730">Campo de información 3: tamaño del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-730">Info Field 3: Packet size</span></span>
- <span data-ttu-id="09389-731">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-731">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="09389-732">Envío de respuesta ARP del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-732">Internal I/O Driver ARP Response Send</span></span> 

#### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="09389-733">Envío de respuesta ARP del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-733">Internal I/O driver ARP response send</span></span>

<span data-ttu-id="09389-734">**Icono** ![Icono de envío de respuesta A R P del controlador de E/S interno](./media/user-guide/netx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="09389-734">**Icon** ![Internal I / O driver ARP response send icon](./media/user-guide/netx-events/image30.png)</span></span>

<span data-ttu-id="09389-735">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-735">**Description**</span></span>

<span data-ttu-id="09389-736">Este evento representa un evento interno de envío de respuesta ARP del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-736">This event represents an internal NetX I/O driver ARP response send event.</span></span>

<span data-ttu-id="09389-737">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-737">**Information Fields**</span></span>

- <span data-ttu-id="09389-738">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-738">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-739">Campo de información 2: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-739">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="09389-740">Campo de información 3: tamaño del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-740">Info Field 3: Packet size</span></span>
- <span data-ttu-id="09389-741">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-741">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="09389-742">Envío de RARP del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-742">Internal I/O Driver RARP Send</span></span> 

#### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="09389-743">Envío de RARP del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-743">Internal I/O driver RARP send</span></span>

<span data-ttu-id="09389-744">**Icono** ![Icono de envío de R A R P del controlador de E/S interno](./media/user-guide/netx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="09389-744">**Icon** ![Internal I / O driver RARP send icon](./media/user-guide/netx-events/image31.png)</span></span>

<span data-ttu-id="09389-745">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-745">**Description**</span></span>

<span data-ttu-id="09389-746">Este evento representa un evento interno de envío de RARP del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-746">This event represents an internal NetX I/O driver RARP send event.</span></span>

<span data-ttu-id="09389-747">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-747">**Information Fields**</span></span>

- <span data-ttu-id="09389-748">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-748">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-749">Campo de información 2: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-749">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="09389-750">Campo de información 3: tamaño del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-750">Info Field 3: Packet size</span></span>
- <span data-ttu-id="09389-751">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-751">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="09389-752">Combinación de multidifusión del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-752">Internal I/O Driver Multicast Join</span></span> 

#### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="09389-753">Combinación de multidifusión del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-753">Internal I/O driver multicast join</span></span>

<span data-ttu-id="09389-754">**Icono** ![Icono de combinación de multidifusión del controlador de E/S interna](./media/user-guide/netx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="09389-754">**Icon** ![Internal I / O driver multicast join icon](./media/user-guide/netx-events/image32.png)</span></span>

<span data-ttu-id="09389-755">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-755">**Description**</span></span>

<span data-ttu-id="09389-756">Este evento representa un evento interno de combinación de multidifusión del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-756">This event represents an internal NetX I/O driver multicast join event.</span></span>

<span data-ttu-id="09389-757">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-757">**Information Fields**</span></span> 

- <span data-ttu-id="09389-758">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-758">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-759">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-759">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-760">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-760">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-761">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-761">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="09389-762">Salida de multidifusión del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-762">Internal I/O Driver Multicast Leave</span></span> 

#### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="09389-763">Salida de multidifusión del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-763">Internal I/O driver multicast leave</span></span>

<span data-ttu-id="09389-764">**Icono** ![Icono de salida de multidifusión del controlador de E/S interna](./media/user-guide/netx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="09389-764">**Icon** ![Internal I / O driver multicast leave icon](./media/user-guide/netx-events/image33.png)</span></span>

<span data-ttu-id="09389-765">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-765">**Description**</span></span>

<span data-ttu-id="09389-766">Este evento representa un evento interno de salida de multidifusión del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-766">This event represents an internal NetX I/O driver multicast leave event.</span></span>

<span data-ttu-id="09389-767">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-767">**Information Fields**</span></span>

- <span data-ttu-id="09389-768">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-768">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-769">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-769">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-770">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-770">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-771">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-771">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-status"></a><span data-ttu-id="09389-772">Obtención de estado del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-772">Internal I/O Driver Get Status</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="09389-773">Obtención de estado del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-773">Internal I/O driver get status</span></span>

<span data-ttu-id="09389-774">**Icono** ![Icono de obtención de estado del controlador de E/S interna](./media/user-guide/netx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="09389-774">**Icon** ![Internal I / O driver get status icon](./media/user-guide/netx-events/image34.png)</span></span>

<span data-ttu-id="09389-775">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-775">**Description**</span></span>

<span data-ttu-id="09389-776">Este evento representa un evento interno de obtención de estado del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-776">This event represents an internal NetX I/O driver get status event.</span></span>

<span data-ttu-id="09389-777">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-777">**Information Fields**</span></span>

- <span data-ttu-id="09389-778">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-778">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-779">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-779">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-780">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-780">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-781">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-781">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="09389-782">Obtención de velocidad del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-782">Internal I/O Driver Get Speed</span></span> 

#### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="09389-783">Obtención de velocidad del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-783">Internal I/O driver get speed</span></span>

<span data-ttu-id="09389-784">**Icono** ![Icono de obtención de velocidad del controlador de E/S interna](./media/user-guide/netx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="09389-784">**Icon** ![Internal I / O driver get speed icon](./media/user-guide/netx-events/image35.png)</span></span>

<span data-ttu-id="09389-785">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-785">**Description**</span></span>

<span data-ttu-id="09389-786">Este evento representa un evento interno de obtención de velocidad del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-786">This event represents an internal NetX I/O driver get speed event.</span></span>

<span data-ttu-id="09389-787">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-787">**Information Fields**</span></span>

- <span data-ttu-id="09389-788">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-788">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-789">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-789">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-790">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-790">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-791">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-791">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="09389-792">Obtención de tipo dúplex del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-792">Internal I/O Driver Get Duplex Type</span></span> 

#### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="09389-793">Obtención de tipo dúplex del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-793">Internal I/O driver get duplex type</span></span>

<span data-ttu-id="09389-794">**Icono** ![Icono de obtención de tipo dúplex del controlador de E/S interna](./media/user-guide/netx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="09389-794">**Icon** ![Internal I / O driver get duplex type icon](./media/user-guide/netx-events/image36.png)</span></span>

<span data-ttu-id="09389-795">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-795">**Description**</span></span>

<span data-ttu-id="09389-796">Este evento representa un evento interno de obtención de tipo dúplex del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-796">This event represents an internal NetX I/O driver get duplex type event.</span></span>

<span data-ttu-id="09389-797">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-797">**Information Fields**</span></span> 

- <span data-ttu-id="09389-798">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-798">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-799">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-799">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-800">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-800">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-801">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-801">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="09389-802">Obtención de número de errores del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-802">Internal I/O Driver Get Error Count</span></span>

#### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="09389-803">Obtención de número de errores del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-803">Internal I/O driver get error count</span></span>

<span data-ttu-id="09389-804">**Icono** ![Icono de obtención de número de errores del controlador de E/S interna](./media/user-guide/netx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="09389-804">**Icon** ![Internal I / O driver get error count icon](./media/user-guide/netx-events/image37.png)</span></span>

<span data-ttu-id="09389-805">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-805">**Description**</span></span>

<span data-ttu-id="09389-806">Este evento representa un evento interno de obtención de número de errores del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-806">This event represents an internal NetX I/O driver get error count event.</span></span>

<span data-ttu-id="09389-807">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-807">**Information Fields**</span></span>

- <span data-ttu-id="09389-808">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-808">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-809">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-809">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-810">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-810">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-811">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-811">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="09389-812">Obtención de número de RX del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-812">Internal I/O Driver Get RX Count</span></span> 

#### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="09389-813">Obtención de número de RX del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-813">Internal I/O driver get RX count</span></span>

<span data-ttu-id="09389-814">**Icono** ![Icono de obtención de número de R X del controlador de E/S interna](./media/user-guide/netx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="09389-814">**Icon** ![Internal I / O driver get RX count icon](./media/user-guide/netx-events/image38.png)</span></span>

<span data-ttu-id="09389-815">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-815">**Description**</span></span>

<span data-ttu-id="09389-816">Este evento representa un evento interno de obtención de número de RX del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-816">This event represents an internal NetX I/O driver get RX count event.</span></span>

<span data-ttu-id="09389-817">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-817">**Information Fields**</span></span> 

- <span data-ttu-id="09389-818">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-818">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-819">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-819">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-820">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-820">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-821">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-821">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="09389-822">Obtención de número de TX del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-822">Internal I/O Driver Get TX Count</span></span> 

#### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="09389-823">Obtención de número de TX del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-823">Internal I/O driver get TX count</span></span>

<span data-ttu-id="09389-824">**Icono** ![Icono de obtención de número de T X del controlador de E/S interna](./media/user-guide/netx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="09389-824">**Icon** ![Internal I / O driver get T X count icon](./media/user-guide/netx-events/image39.png)</span></span>

<span data-ttu-id="09389-825">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-825">**Description**</span></span>

<span data-ttu-id="09389-826">Este evento representa un evento interno de obtención de número de TX del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-826">This event represents an internal NetX I/O driver get TX count event.</span></span>

<span data-ttu-id="09389-827">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-827">**Information Fields**</span></span>

- <span data-ttu-id="09389-828">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-828">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-829">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-829">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-830">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-830">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-831">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-831">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="09389-832">Obtención de errores de asignación del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-832">Internal I/O Driver Get Allocation Errors</span></span> 

#### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="09389-833">Obtención de errores de asignación del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-833">Internal I/O driver get allocation errors</span></span>

<span data-ttu-id="09389-834">**Icono** ![Icono de obtención de errores de asignación del controlador de E/S interna](./media/user-guide/netx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="09389-834">**Icon** ![Internal I / O driver get allocation errors icon](./media/user-guide/netx-events/image40.png)</span></span>

<span data-ttu-id="09389-835">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-835">**Description**</span></span>

<span data-ttu-id="09389-836">Este evento representa un evento interno de obtención de errores de asignación del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-836">This event represents an internal NetX I/O driver get allocation errors event.</span></span>

<span data-ttu-id="09389-837">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-837">**Information Fields**</span></span> 

- <span data-ttu-id="09389-838">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-838">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-839">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-839">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-840">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-840">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-841">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-841">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="09389-842">Anulación de inicialización del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-842">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="09389-843">Anulación de inicialización del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="09389-843">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="09389-844">**Icono** ![Icono de anulación de inicialización del controlador de E/S interna](./media/user-guide/netx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="09389-844">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/netx-events/image41.png)</span></span>

<span data-ttu-id="09389-845">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-845">**Description**</span></span>

<span data-ttu-id="09389-846">Este evento representa un evento interno de anulación de inicialización del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-846">This event represents an internal NetX I/O driver un-initialize event.</span></span>

<span data-ttu-id="09389-847">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-847">**Information Fields**</span></span> 

- <span data-ttu-id="09389-848">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-848">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-849">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-849">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-850">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-850">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-851">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-851">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="09389-852">Procesamiento diferido del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-852">Internal I/O Driver Deferred Processing</span></span> 

#### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="09389-853">Procesamiento diferido del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="09389-853">Internal I/O driver deferred processing</span></span> 

<span data-ttu-id="09389-854">**Icono** ![Icono de procesamiento diferido del controlador de E/S interno](./media/user-guide/netx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="09389-854">**Icon** ![Internal I / O driver deferred processing icon](./media/user-guide/netx-events/image42.png)</span></span>

<span data-ttu-id="09389-855">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-855">**Description**</span></span>

<span data-ttu-id="09389-856">Este evento representa un evento interno de procesamiento diferido del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="09389-856">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="09389-857">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-857">**Information Fields**</span></span>

- <span data-ttu-id="09389-858">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-858">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-859">Campo de información 2: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-859">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="09389-860">Campo de información 3: longitud del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-860">Info Field 3: Packet length</span></span>
- <span data-ttu-id="09389-861">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-861">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entries-invalidate"></a><span data-ttu-id="09389-862">Invalidación de entradas dinámicas de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-862">ARP Dynamic Entries Invalidate</span></span> 

#### <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="09389-863">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="09389-863">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="09389-864">**Icono** ![Icono de invalidación de entradas dinámicas de A R P](./media/user-guide/netx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="09389-864">**Icon** ![A R P Dynamic Entries Invalidate icon](./media/user-guide/netx-events/image43.png)</span></span>

<span data-ttu-id="09389-865">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-865">**Description**</span></span>

<span data-ttu-id="09389-866">Este evento representa la invalidación de todas las entradas dinámicas de ARP por medio de nx_arp_dynamic_entries_invalidate.</span><span class="sxs-lookup"><span data-stu-id="09389-866">This event represents invalidating all dynamic ARP entires via nx_arp_dynamic_entries_invalidate.</span></span>

<span data-ttu-id="09389-867">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-867">**Information Fields**</span></span> 

- <span data-ttu-id="09389-868">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-868">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-869">Campo de información 2: entradas invalidadas</span><span class="sxs-lookup"><span data-stu-id="09389-869">Info Field 2: Entries invalidated</span></span>
- <span data-ttu-id="09389-870">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-870">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-871">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-871">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entry-set"></a><span data-ttu-id="09389-872">Establecimiento de entrada dinámica de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-872">ARP Dynamic Entry Set</span></span> 

#### <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="09389-873">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="09389-873">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="09389-874">**Icono** ![Icono de establecimiento de entrada dinámica de A R P](./media/user-guide/netx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="09389-874">**Icon** ![A R P Dynamic Entry Set icon](./media/user-guide/netx-events/image44.png)</span></span>

<span data-ttu-id="09389-875">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-875">**Description**</span></span>

<span data-ttu-id="09389-876">Este evento representa la configuración de una entrada dinámica de ARP por medio de nx_arp_dynamic_entry_set.</span><span class="sxs-lookup"><span data-stu-id="09389-876">This event represents setting a dynamic ARP entry via nx_arp_dynamic_entry_set.</span></span>

<span data-ttu-id="09389-877">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-877">**Information Fields**</span></span> 

- <span data-ttu-id="09389-878">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-878">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-879">Campo de información 2: dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-879">Info Field 2: IP address</span></span>
- <span data-ttu-id="09389-880">Campo de información 3: dirección física (MSW)</span><span class="sxs-lookup"><span data-stu-id="09389-880">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="09389-881">Campo de información 4: dirección física (LSW)</span><span class="sxs-lookup"><span data-stu-id="09389-881">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-enable"></a><span data-ttu-id="09389-882">Habilitación de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-882">ARP Enable</span></span> 

#### <a name="nx_arp_enable"></a><span data-ttu-id="09389-883">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="09389-883">nx_arp_enable</span></span>

<span data-ttu-id="09389-884">**Icono** ![Icono de habilitación de A R P](./media/user-guide/netx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="09389-884">**Icon** ![A R P enable icon](./media/user-guide/netx-events/image45.png)</span></span>

<span data-ttu-id="09389-885">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-885">**Description**</span></span>

<span data-ttu-id="09389-886">Este evento representa la habilitación de ARP por medio de nx_arp_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-886">This event represents enabling ARP via nx_arp_enable.</span></span>

<span data-ttu-id="09389-887">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-887">**Information Fields**</span></span> 

- <span data-ttu-id="09389-888">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-888">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-889">Campo de información 2: puntero a la memoria caché de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-889">Info Field 2: ARP cache memory pointer</span></span>
- <span data-ttu-id="09389-890">Campo de información 3: tamaño de la memoria caché de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-890">Info Field 3: ARP cache memory size</span></span>
- <span data-ttu-id="09389-891">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-891">Info Field 4: Not used</span></span>

### <a name="arp-gratuitous-send"></a><span data-ttu-id="09389-892">Envío gratuito de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-892">ARP Gratuitous Send</span></span> 

#### <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="09389-893">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="09389-893">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="09389-894">**Icono** ![Icono de envío gratuito de A R P](./media/user-guide/netx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="09389-894">**Icon** ![A R P gratuitous send icon](./media/user-guide/netx-events/image46.png)</span></span>

<span data-ttu-id="09389-895">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-895">**Description**</span></span>

<span data-ttu-id="09389-896">Este evento representa un envío gratuito de ARP por medio de nx_arp_gratuitous_send.</span><span class="sxs-lookup"><span data-stu-id="09389-896">This event represents a gratuitous ARP send via nx_arp_gratuitous_send.</span></span>

<span data-ttu-id="09389-897">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-897">**Information Fields**</span></span>

- <span data-ttu-id="09389-898">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-898">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-899">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-899">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-900">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-900">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-901">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-901">Info Field 4: Not used</span></span>

### <a name="arp-hardware-address-find"></a><span data-ttu-id="09389-902">Búsqueda de la dirección de hardware de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-902">ARP Hardware Address Find</span></span> 

#### <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="09389-903">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="09389-903">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="09389-904">**Icono** ![Icono de búsqueda de dirección de hardware de A R P](./media/user-guide/netx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="09389-904">**Icon** ![A R P Hardware Address Find icon](./media/user-guide/netx-events/image47.png)</span></span>

<span data-ttu-id="09389-905">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-905">**Description**</span></span>

<span data-ttu-id="09389-906">Este evento representa la búsqueda de una dirección física por medio de nx_arp_hardware_address_find.</span><span class="sxs-lookup"><span data-stu-id="09389-906">This event represents finding a physical address via nx_arp_hardware_address_find.</span></span>

<span data-ttu-id="09389-907">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-907">**Information Fields**</span></span> 

- <span data-ttu-id="09389-908">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-908">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-909">Campo de información 2: dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-909">Info Field 2: IP address</span></span>
- <span data-ttu-id="09389-910">Campo de información 3: dirección física (MSW)</span><span class="sxs-lookup"><span data-stu-id="09389-910">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="09389-911">Campo de información 4: dirección física (LSW)</span><span class="sxs-lookup"><span data-stu-id="09389-911">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-information-get"></a><span data-ttu-id="09389-912">Obtención de información de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-912">ARP Information Get</span></span> 

#### <a name="nx_arp_info_get"></a><span data-ttu-id="09389-913">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-913">nx_arp_info_get</span></span>

<span data-ttu-id="09389-914">**Icono** ![Icono de obtención de información de A R P](./media/user-guide/netx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="09389-914">**Icon** ![A R P informition get icon](./media/user-guide/netx-events/image48.png)</span></span>

<span data-ttu-id="09389-915">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-915">**Description**</span></span>

<span data-ttu-id="09389-916">Este evento representa la obtención de información por medio de nx_arp_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-916">This event represents getting information via nx_arp_info_get.</span></span>

<span data-ttu-id="09389-917">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-917">**Information Fields**</span></span> 

- <span data-ttu-id="09389-918">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-918">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-919">Campo de información 2: ARP enviados</span><span class="sxs-lookup"><span data-stu-id="09389-919">Info Field 2: ARPs sent</span></span>
- <span data-ttu-id="09389-920">Campo de información 3: respuestas ARP</span><span class="sxs-lookup"><span data-stu-id="09389-920">Info Field 3: ARP responses</span></span>
- <span data-ttu-id="09389-921">Campo de información 4: ARP recibidos</span><span class="sxs-lookup"><span data-stu-id="09389-921">Info Field 4: ARPs received</span></span>

### <a name="arp-ip-address-find"></a><span data-ttu-id="09389-922">Búsqueda de dirección IP de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-922">ARP IP Address Find</span></span> 

#### <a name="nx_arp_ip_address_find"></a><span data-ttu-id="09389-923">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="09389-923">nx_arp_ip_address_find</span></span>

<span data-ttu-id="09389-924">**Icono** ![Icono de búsqueda de dirección I P de A R P](./media/user-guide/netx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="09389-924">**Icon** ![A R P I P address find icon](./media/user-guide/netx-events/image49.png)</span></span>

<span data-ttu-id="09389-925">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-925">**Description**</span></span>

<span data-ttu-id="09389-926">Este evento representa la búsqueda de una dirección IP asociada a la dirección física proporcionada por medio de nx_arp_ip_address_find.</span><span class="sxs-lookup"><span data-stu-id="09389-926">This event represents finding an IP address associated with the supplied physical address via nx_arp_ip_address_find.</span></span>

<span data-ttu-id="09389-927">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-927">**Information Fields**</span></span> 

- <span data-ttu-id="09389-928">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-928">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-929">Campo de información 2: dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-929">Info Field 2: IP address</span></span>
- <span data-ttu-id="09389-930">Campo de información 3: dirección física (MSW)</span><span class="sxs-lookup"><span data-stu-id="09389-930">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="09389-931">Campo de información 4: dirección física (LSW)</span><span class="sxs-lookup"><span data-stu-id="09389-931">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entry-create"></a><span data-ttu-id="09389-932">Creación de entrada estática de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-932">ARP Static Entry Create</span></span> 

#### <a name="nx_arp_static_entry_create"></a><span data-ttu-id="09389-933">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="09389-933">nx_arp_static_entry_create</span></span>

<span data-ttu-id="09389-934">**Icono** ![Icono de creación de entrada estática de A R P](./media/user-guide/netx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="09389-934">**Icon** ![A R P static entry create icon](./media/user-guide/netx-events/image50.png)</span></span>

<span data-ttu-id="09389-935">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-935">**Description**</span></span>

<span data-ttu-id="09389-936">Este evento representa la creación de una entrada estática de ARP por medio de nx_arp_static_entry_create.</span><span class="sxs-lookup"><span data-stu-id="09389-936">This event represents creating a static ARP entry via nx_arp_static_entry_create.</span></span>

<span data-ttu-id="09389-937">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-937">**Information Fields**</span></span>

- <span data-ttu-id="09389-938">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-938">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-939">Campo de información 2: dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-939">Info Field 2: IP address</span></span>
- <span data-ttu-id="09389-940">Campo de información 3: dirección física (MSW)</span><span class="sxs-lookup"><span data-stu-id="09389-940">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="09389-941">Campo de información 4: dirección física (LSW)</span><span class="sxs-lookup"><span data-stu-id="09389-941">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entries-delete"></a><span data-ttu-id="09389-942">Eliminación de entradas estáticas de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-942">ARP Static Entries Delete</span></span> 

#### <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="09389-943">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="09389-943">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="09389-944">**Icono** ![Icono de eliminación de entradas estáticas de A R P](./media/user-guide/netx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="09389-944">**Icon** ![A R P static entries delete icon](./media/user-guide/netx-events/image51.png)</span></span>

<span data-ttu-id="09389-945">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-945">**Description**</span></span>

<span data-ttu-id="09389-946">Este evento representa la eliminación de todas las entradas estáticas de ARP por medio de nx_arp_static_entries_delete.</span><span class="sxs-lookup"><span data-stu-id="09389-946">This event represents deleting all ARP static entries via nx_arp_static_entries_delete.</span></span>

<span data-ttu-id="09389-947">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-947">**Information Fields**</span></span> 

- <span data-ttu-id="09389-948">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-948">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-949">Campo de información 2: entradas eliminadas</span><span class="sxs-lookup"><span data-stu-id="09389-949">Info Field 2: Entries deleted</span></span>
- <span data-ttu-id="09389-950">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-950">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-951">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-951">Info Field 4: Not used</span></span>

### <a name="arp-static-entry-delete"></a><span data-ttu-id="09389-952">Eliminación de entrada estática de ARP</span><span class="sxs-lookup"><span data-stu-id="09389-952">ARP Static Entry Delete</span></span> 

### <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="09389-953">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="09389-953">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="09389-954">**Icono** ![Icono de eliminación de entrada estática de A R P](./media/user-guide/netx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="09389-954">**Icon** ![A R P static entry delete icon](./media/user-guide/netx-events/image52.png)</span></span>

<span data-ttu-id="09389-955">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-955">**Description**</span></span>

<span data-ttu-id="09389-956">Este evento representa la eliminación de una entrada estática de ARP por medio de nx_arp_static_entry_delete.</span><span class="sxs-lookup"><span data-stu-id="09389-956">This event represents deleting a static ARP entry via nx_arp_static_entry_delete.</span></span>

<span data-ttu-id="09389-957">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-957">**Information Fields**</span></span> 

- <span data-ttu-id="09389-958">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-958">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-959">Campo de información 2: dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-959">Info Field 2: IP address</span></span>
- <span data-ttu-id="09389-960">Campo de información 3: dirección física (MSW)</span><span class="sxs-lookup"><span data-stu-id="09389-960">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="09389-961">Campo de información 4: dirección física (LSW)</span><span class="sxs-lookup"><span data-stu-id="09389-961">Info Field 4: Physical address (LSW)</span></span>

### <a name="duo-cache-entry-delete"></a><span data-ttu-id="09389-962">Eliminación de entrada de caché doble</span><span class="sxs-lookup"><span data-stu-id="09389-962">Duo Cache Entry Delete</span></span> 

#### <a name="nxd_und_cache_entry_delete"></a><span data-ttu-id="09389-963">nxd_und_cache_entry_delete</span><span class="sxs-lookup"><span data-stu-id="09389-963">nxd_und_cache_entry_delete</span></span>

<span data-ttu-id="09389-964">**Icono** ![Icono de eliminación de entrada de caché doble](./media/user-guide/netx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="09389-964">**Icon** ![Duo cache entry delete icon](./media/user-guide/netx-events/image53.png)</span></span>

<span data-ttu-id="09389-965">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-965">**Description**</span></span>

<span data-ttu-id="09389-966">Este evento representa la eliminación de una entrada en la tabla de caché vecina por medio de nx_udp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="09389-966">This event represents deleting an entry in the neighbor cache table via nx_udp_socket_create.</span></span>

<span data-ttu-id="09389-967">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-967">**Information Fields**</span></span> 

- <span data-ttu-id="09389-968">Campo de información 1: cuarta palabra (menos significativa) de la dirección local del vínculo IPv6 que se va a eliminar</span><span class="sxs-lookup"><span data-stu-id="09389-968">Info Field 1: Fourth (least significant) word of the IPv6 link local address to delete</span></span>
- <span data-ttu-id="09389-969">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-969">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-970">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-970">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-971">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-971">Info Field 4: Not used</span></span>

### <a name="duo-cache-entry-set"></a><span data-ttu-id="09389-972">Establecimiento de entrada de caché doble</span><span class="sxs-lookup"><span data-stu-id="09389-972">Duo Cache Entry Set</span></span> 

#### <a name="nxd_nd_cache_entry_set"></a><span data-ttu-id="09389-973">nxd_nd_cache_entry_set</span><span class="sxs-lookup"><span data-stu-id="09389-973">nxd_nd_cache_entry_set</span></span>

<span data-ttu-id="09389-974">**Icono** ![Icono de establecimiento de entrada de caché doble](./media/user-guide/netx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="09389-974">**Icon** ![Duo cache entry set icon](./media/user-guide/netx-events/image54.png)</span></span>

<span data-ttu-id="09389-975">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-975">**Description**</span></span>

<span data-ttu-id="09389-976">Este evento representa la creación de una entrada de caché y su adición a la tabla de caché vecina por medio de nxd_nd_cache_entry_set.</span><span class="sxs-lookup"><span data-stu-id="09389-976">This event represents creating a cache entry and adding to the neighbor cache table via nxd_nd_cache_entry_set.</span></span>

<span data-ttu-id="09389-977">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-977">**Information Fields**</span></span> 

- <span data-ttu-id="09389-978">Campo de información 1: cuarta palabra (menos significativa) de la dirección IPv6 que se va a agregar</span><span class="sxs-lookup"><span data-stu-id="09389-978">Info Field 1: Fourth (least significant) word of the IPv6 address to add</span></span>
- <span data-ttu-id="09389-979">Campo de información 2: MSB de la dirección física</span><span class="sxs-lookup"><span data-stu-id="09389-979">Info Field 2: Physical address msb</span></span>
- <span data-ttu-id="09389-980">Campo de información 3: LSB de la dirección física</span><span class="sxs-lookup"><span data-stu-id="09389-980">Info Field 3: Physical address lsb</span></span>
- <span data-ttu-id="09389-981">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-981">Info Field 4: Not used</span></span>

### <a name="duo-cache-invalidate"></a><span data-ttu-id="09389-982">Invalidación de caché doble</span><span class="sxs-lookup"><span data-stu-id="09389-982">Duo Cache Invalidate</span></span> 

#### <a name="nxd_nd_cache_invalidate"></a><span data-ttu-id="09389-983">nxd_nd_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="09389-983">nxd_nd_cache_invalidate</span></span>

<span data-ttu-id="09389-984">**Icono** ![Icono de invalidación de caché doble](./media/user-guide/netx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="09389-984">**Icon** ![Duo cache invalidate icon](./media/user-guide/netx-events/image55.png)</span></span>

<span data-ttu-id="09389-985">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-985">**Description**</span></span>

<span data-ttu-id="09389-986">Este evento representa la invalidación de toda la tabla de caché vecina por medio de nxd_nd_cache_invalidate.</span><span class="sxs-lookup"><span data-stu-id="09389-986">This event represents invalidating the entire neighbor cache table via nxd_nd_cache_invalidate.</span></span>

<span data-ttu-id="09389-987">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-987">**Information Fields**</span></span>

- <span data-ttu-id="09389-988">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-988">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-989">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-989">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-990">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-990">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-991">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-991">Info Field 4: Not used</span></span>

### <a name="duo-cache-ip-address-find"></a><span data-ttu-id="09389-992">Búsqueda de dirección IP de caché doble</span><span class="sxs-lookup"><span data-stu-id="09389-992">Duo Cache IP Address Find</span></span> 

#### <a name="nxd_nd_cache_ip_address_find"></a><span data-ttu-id="09389-993">nxd_nd_cache_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="09389-993">nxd_nd_cache_ip_address_find</span></span>

<span data-ttu-id="09389-994">**Icono** ![Icono de búsqueda de dirección I P de caché doble](./media/user-guide/netx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="09389-994">**Icon** ![Duo cache I P address find icon](./media/user-guide/netx-events/image56.png)</span></span>

<span data-ttu-id="09389-995">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-995">**Description**</span></span>

<span data-ttu-id="09389-996">Este evento representa la recuperación de una dirección IP que coincide con la dirección física proporcionada de la tabla de caché por medio de nxd_nd_cache_ip_address_find.</span><span class="sxs-lookup"><span data-stu-id="09389-996">This event represents retrieving an IP address matching the supplied physical address from the cache table via nxd_nd_cache_ip_address_find.</span></span>

<span data-ttu-id="09389-997">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-997">**Information Fields**</span></span>

- <span data-ttu-id="09389-998">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-998">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-999">Campo de información 2: cuarta palabra (menos significativa) de la dirección IPv6</span><span class="sxs-lookup"><span data-stu-id="09389-999">Info Field 2: Fourth (least significant) word of the IPv6 address</span></span>
- <span data-ttu-id="09389-1000">Campo de información 3: MSB de la dirección física</span><span class="sxs-lookup"><span data-stu-id="09389-1000">Info Field 3: Physical address msb</span></span>
- <span data-ttu-id="09389-1001">Campo de información 4: LSB de la dirección física</span><span class="sxs-lookup"><span data-stu-id="09389-1001">Info Field 4: Physical address lsb</span></span>

### <a name="duo-icmp-enable"></a><span data-ttu-id="09389-1002">Habilitación de ICMP doble</span><span class="sxs-lookup"><span data-stu-id="09389-1002">Duo ICMP Enable</span></span> 

#### <a name="nxd_icmp_enable"></a><span data-ttu-id="09389-1003">nxd_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1003">nxd_icmp_enable</span></span>

<span data-ttu-id="09389-1004">**Icono** ![Icono de habilitación de I C M P doble](./media/user-guide/netx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1004">**Icon** ![Duo I C M P enable icon](./media/user-guide/netx-events/image57.png)</span></span>

<span data-ttu-id="09389-1005">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1005">**Description**</span></span>

<span data-ttu-id="09389-1006">Este evento representa la habilitación de los servicios ICMPv4 y ICMPv6 en la instancia de IP especificada por medio de nxd_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1006">This event represents ICMPv4 and ICMPv6 services being enabled on the specified IP instance via nxd_icmp_enable.</span></span>

<span data-ttu-id="09389-1007">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1007">**Information Fields**</span></span>
- <span data-ttu-id="09389-1008">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1008">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1009">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1009">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1010">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1010">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1011">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1011">Info Field 4: Not used</span></span>

### <a name="duo-icmp-ping"></a><span data-ttu-id="09389-1012">Ping de ICMP doble</span><span class="sxs-lookup"><span data-stu-id="09389-1012">Duo ICMP Ping</span></span> 

#### <a name="nxd_icmp_ping"></a><span data-ttu-id="09389-1013">nxd_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="09389-1013">nxd_icmp_ping</span></span>

<span data-ttu-id="09389-1014">**Icono** ![Icono de ping de I C M P doble](./media/user-guide/netx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1014">**Icon** ![Duo I C M P ping icon](./media/user-guide/netx-events/image58.png)</span></span>

<span data-ttu-id="09389-1015">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1015">**Description**</span></span>

<span data-ttu-id="09389-1016">Este evento representa el envío de un ping (solicitud de eco) a un host IPv6 por medio de nxd_icmp_ping.</span><span class="sxs-lookup"><span data-stu-id="09389-1016">This event represents sending a ping (echo request) to an IPv6 host via nxd_icmp_ping.</span></span>

<span data-ttu-id="09389-1017">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1017">**Information Fields**</span></span>

- <span data-ttu-id="09389-1018">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1018">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1019">Campo de información 2: dirección IPv6</span><span class="sxs-lookup"><span data-stu-id="09389-1019">Info Field 2: IPv6 address</span></span>
- <span data-ttu-id="09389-1020">Campo de información 3: puntero a los datos de eco</span><span class="sxs-lookup"><span data-stu-id="09389-1020">Info Field 3: Pointer to echo data</span></span>
- <span data-ttu-id="09389-1021">Campo de información 4: tamaño de los datos de eco</span><span class="sxs-lookup"><span data-stu-id="09389-1021">Info Field 4: Size of echo data</span></span>

### <a name="duo-ip-max-payload-size-find"></a><span data-ttu-id="09389-1022">Búsqueda de tamaño máximo de carga de IP doble</span><span class="sxs-lookup"><span data-stu-id="09389-1022">Duo IP Max Payload Size Find</span></span> 

#### <a name="nxd_ip_max_payload_size"></a><span data-ttu-id="09389-1023">nxd_ip_max_payload_size</span><span class="sxs-lookup"><span data-stu-id="09389-1023">nxd_ip_max_payload_size</span></span>

<span data-ttu-id="09389-1024">**Icono** ![Icono de búsqueda de tamaño máximo de carga de I P doble](./media/user-guide/netx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1024">**Icon** ![Duo I P max payload size find icon](./media/user-guide/netx-events/image59.png)</span></span>

<span data-ttu-id="09389-1025">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1025">**Description**</span></span>

<span data-ttu-id="09389-1026">Este evento calcula la carga máxima que el paquete especificado puede llevar a cabo sin necesidad de fragmentación.</span><span class="sxs-lookup"><span data-stu-id="09389-1026">This event computes the max payload the specified packet can carry without requiring fragmentation.</span></span>

<span data-ttu-id="09389-1027">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1027">**Information Fields**</span></span>

- <span data-ttu-id="09389-1028">Campo de información 1: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1028">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="09389-1029">Campo de información 2: dirección IP del nodo del mismo nivel</span><span class="sxs-lookup"><span data-stu-id="09389-1029">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="09389-1030">Campo de información 3: puerto del nodo del mismo nivel Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1030">Info Field 3: Peer port Info Field 4: Not used</span></span>

### <a name="duo-ip-raw-packet-send"></a><span data-ttu-id="09389-1031">Envío de paquete sin formato de IP doble</span><span class="sxs-lookup"><span data-stu-id="09389-1031">Duo IP Raw Packet Send</span></span> 

#### <a name="nxd_ip_max_packet_send"></a><span data-ttu-id="09389-1032">nxd_ip_max_packet_send</span><span class="sxs-lookup"><span data-stu-id="09389-1032">nxd_ip_max_packet_send</span></span>

<span data-ttu-id="09389-1033">**Icono** ![Icono de envío de paquete sin formato de I P doble](./media/user-guide/netx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1033">**Icon** ![Duo I P raw packet send icon](./media/user-guide/netx-events/image60.png)</span></span>

<span data-ttu-id="09389-1034">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1034">**Description**</span></span>

<span data-ttu-id="09389-1035">Este evento representa el envío de un paquete de IP sin formato desde la interfaz de red especificada a la dirección de destino IP indicada por medio de nxd_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="09389-1035">This event represents sending a raw IP packet out the specified network interface to the supplied IP destination addressvia nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="09389-1036">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1036">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1037">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1037">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1038">Campo de información 2: puntero al paquete que se va a enviar</span><span class="sxs-lookup"><span data-stu-id="09389-1038">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="09389-1039">Campo de información 3: puntero a la dirección de destino</span><span class="sxs-lookup"><span data-stu-id="09389-1039">Info Field 3: Pointer to destination address</span></span>
- <span data-ttu-id="09389-1040">Campo de información 4: protocolo del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1040">Info Field 4: Packet protocol</span></span>

### <a name="duo-ipv6-default-router-add"></a><span data-ttu-id="09389-1041">Adición de enrutador predeterminado de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1041">Duo IPv6 Default Router Add</span></span> 

#### <a name="nxd_ipv6_default_router_add"></a><span data-ttu-id="09389-1042">nxd_ipv6_default_router_add</span><span class="sxs-lookup"><span data-stu-id="09389-1042">nxd_ipv6_default_router_add</span></span>

<span data-ttu-id="09389-1043">**Icono** ![Icono de adición de enrutador predeterminado de I P v 6 doble](./media/user-guide/netx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1043">**Icon** ![Duo I P v 6 default router add icon](./media/user-guide/netx-events/image61.png)</span></span>

<span data-ttu-id="09389-1044">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1044">**Description**</span></span>

<span data-ttu-id="09389-1045">Este evento representa la adición de un enrutador predeterminado a la tabla de enrutamiento IPv6 de la instancia de IP por medio de nxd_ipv6_default_router_add.</span><span class="sxs-lookup"><span data-stu-id="09389-1045">This event represents adding a default router to the IP instance's IPv6 routing table via nxd_ipv6_default_router_add.</span></span>

<span data-ttu-id="09389-1046">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1046">**Information Fields**</span></span>

- <span data-ttu-id="09389-1047">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1047">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="09389-1048">Campo de información 2: dirección de red de destino</span><span class="sxs-lookup"><span data-stu-id="09389-1048">Info Field 2: Destination Network address.</span></span>
- <span data-ttu-id="09389-1049">Campo de información 3: información de tiempo de vida</span><span class="sxs-lookup"><span data-stu-id="09389-1049">Info Field 3: Life time information.</span></span>
- <span data-ttu-id="09389-1050">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1050">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-default-router-delete"></a><span data-ttu-id="09389-1051">Eliminación de enrutador predeterminado de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1051">Duo IPv6 Default Router Delete</span></span> 

#### <a name="nxd_ipv6_default_router_delete"></a><span data-ttu-id="09389-1052">nxd_ipv6_default_router_delete</span><span class="sxs-lookup"><span data-stu-id="09389-1052">nxd_ipv6_default_router_delete</span></span>

<span data-ttu-id="09389-1053">**Icono** ![Icono de eliminación de enrutador predeterminado de I P v 6 doble](./media/user-guide/netx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1053">**Icon** ![Duo I P v 6 default router delete icon](./media/user-guide/netx-events/image62.png)</span></span>

<span data-ttu-id="09389-1054">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1054">**Description**</span></span>

<span data-ttu-id="09389-1055">Este evento representa la eliminación de un enrutador predeterminado de la tabla de enrutamiento IPv6 de la instancia de IP por medio de nxd_ipv6_default_router_delete.</span><span class="sxs-lookup"><span data-stu-id="09389-1055">This event represents removing a default router from the IP instance's IPv6 routing table via nxd_ipv6_default_router_delete.</span></span>

<span data-ttu-id="09389-1056">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1056">**Information Fields**</span></span>

- <span data-ttu-id="09389-1057">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1057">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="09389-1058">Campo de información 2: cuarta palabra (menos significativa) de la dirección IPv6 del enrutador predeterminado</span><span class="sxs-lookup"><span data-stu-id="09389-1058">Info Field 2: Fourth word (least significant) of the default router IPv6 address.</span></span>
- <span data-ttu-id="09389-1059">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="09389-1060">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1060">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-enable"></a><span data-ttu-id="09389-1061">Habilitación de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1061">Duo IPv6 Enable</span></span> 

#### <a name="nxd_ipv6_enable"></a><span data-ttu-id="09389-1062">nxd_ipv6_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1062">nxd_ipv6_enable</span></span>

<span data-ttu-id="09389-1063">**Icono** ![Icono de habilitación de I P v 6 doble](./media/user-guide/netx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1063">**Icon** ![Duo I P v 6 enable icon](./media/user-guide/netx-events/image63.png)</span></span>

<span data-ttu-id="09389-1064">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1064">**Description**</span></span>

<span data-ttu-id="09389-1065">Este evento representa la habilitación de servicios IPv6 en la instancia de IP proporcionada por medio de nxd_ipv6_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1065">This event represents enabling IPv6 services on the supplied IP instance via nxd_ipv6_enable.</span></span>

<span data-ttu-id="09389-1066">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1066">**Information Fields**</span></span>

- <span data-ttu-id="09389-1067">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1067">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1068">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1068">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1069">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1069">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1070">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1070">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-global-address-get"></a><span data-ttu-id="09389-1071">Obtención de dirección global de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1071">Duo IPv6 Global Address Get</span></span> 

#### <a name="nxd_ipv6_global_address_get"></a><span data-ttu-id="09389-1072">nxd_ipv6_global_address_get</span><span class="sxs-lookup"><span data-stu-id="09389-1072">nxd_ipv6_global_address_get</span></span>

<span data-ttu-id="09389-1073">**Icono** ![Icono de obtención de dirección global de I P v 6 doble](./media/user-guide/netx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1073">**Icon** ![Duo I P v 6 global address get icon](./media/user-guide/netx-events/image64.png)</span></span>

<span data-ttu-id="09389-1074">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1074">**Description**</span></span>

<span data-ttu-id="09389-1075">Este evento representa la recuperación de la dirección IP global (principal) de la instancia de IP que se encuentra en el índice 1 de la tabla de interfaces de instancia de IP por medio de nxd_ipv6_global_address_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1075">This event represents retrieving the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_get.</span></span>

<span data-ttu-id="09389-1076">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1076">**Information Fields**</span></span>

- <span data-ttu-id="09389-1077">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1077">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="09389-1078">Campo de información 2: cuarta palabra (menos significativa) de la dirección global</span><span class="sxs-lookup"><span data-stu-id="09389-1078">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="09389-1079">Campo de información 3: longitud del prefijo de la dirección IPv6</span><span class="sxs-lookup"><span data-stu-id="09389-1079">Info Field 3: IPv6 address prefix length.</span></span>
- <span data-ttu-id="09389-1080">Campo de información 4: índice en la tabla de interfaces de IP (1).</span><span class="sxs-lookup"><span data-stu-id="09389-1080">Info Field 4: Index into IP interface table (1).</span></span>

### <a name="duo-ipv6-global-address-set"></a><span data-ttu-id="09389-1081">Establecimiento de dirección global de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1081">Duo IPv6 Global Address Set</span></span> 

#### <a name="nxd_ipv6_global_address_set"></a><span data-ttu-id="09389-1082">nxd_ipv6_global_address_set</span><span class="sxs-lookup"><span data-stu-id="09389-1082">nxd_ipv6_global_address_set</span></span>

<span data-ttu-id="09389-1083">**Icono** ![Icono de establecimiento de dirección global de I P v 6 doble](./media/user-guide/netx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1083">**Icon** ![Duo I P v 6 global address set icon](./media/user-guide/netx-events/image65.png)</span></span>

<span data-ttu-id="09389-1084">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1084">**Description**</span></span>

<span data-ttu-id="09389-1085">Este evento representa el establecimiento de la dirección IP global (principal) en la instancia de IP que se encuentra en el índice 1 de la tabla de interfaces de instancia de IP por medio de nxd_ipv6_global_address_set.</span><span class="sxs-lookup"><span data-stu-id="09389-1085">This event represents setting the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_set.</span></span>

<span data-ttu-id="09389-1086">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1086">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1087">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1087">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1088">Campo de información 2: cuarta palabra (menos significativa) de la dirección global</span><span class="sxs-lookup"><span data-stu-id="09389-1088">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="09389-1089">Campo de información 3: longitud del prefijo de la dirección IPv6</span><span class="sxs-lookup"><span data-stu-id="09389-1089">Info Field 3: IPv6 address prefix length</span></span>
- <span data-ttu-id="09389-1090">Campo de información 4: índice en la tabla de interfaces de IP (1)</span><span class="sxs-lookup"><span data-stu-id="09389-1090">Info Field 4: Index into IP interface table (1)</span></span>

### <a name="duo-ipv6-initiate-dad-process"></a><span data-ttu-id="09389-1091">Inicio de proceso DAD de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1091">Duo IPv6 Initiate Dad Process</span></span> 

#### <a name="nxd_ipv6_initiate_dad_process"></a><span data-ttu-id="09389-1092">nxd_ipv6_initiate_dad_process</span><span class="sxs-lookup"><span data-stu-id="09389-1092">nxd_ipv6_initiate_dad_process</span></span>

<span data-ttu-id="09389-1093">**Icono** ![Icono de inicio de proceso D A D de I P v 6 doble](./media/user-guide/netx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1093">**Icon** ![Duo I P v 6 initiate dad process icon](./media/user-guide/netx-events/image66.png)</span></span>

<span data-ttu-id="09389-1094">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1094">**Description**</span></span>

<span data-ttu-id="09389-1095">Este evento representa el inicio del proceso de detección de direcciones duplicadas (DAD) cuando se asigna un vínculo local o una dirección de interfaz de IP a la instancia de IP por medio de nxd_ipv6_initiate_dad_process.</span><span class="sxs-lookup"><span data-stu-id="09389-1095">This event represents the start of the Duplicate Address Detection (DAD) process when the IP instance is assigned a link local or an IP interface address via nxd_ipv6_initiate_dad_process.</span></span>

<span data-ttu-id="09389-1096">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1096">**Information Fields**</span></span>

- <span data-ttu-id="09389-1097">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1097">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1098">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1098">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1099">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1099">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1100">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1100">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-interface-address-get"></a><span data-ttu-id="09389-1101">Obtención de dirección de interfaz de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1101">Duo IPv6 Interface Address Get</span></span> 

#### <a name="nxd_ipv6_interface_address_get"></a><span data-ttu-id="09389-1102">nxd_ipv6_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="09389-1102">nxd_ipv6_interface_address_get</span></span>

<span data-ttu-id="09389-1103">**Icono** ![Icono de obtención de dirección de interfaz de I P v 6 doble](./media/user-guide/netx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1103">**Icon** ![Duo I P v 6 interface address get icon](./media/user-guide/netx-events/image67.png)</span></span>

<span data-ttu-id="09389-1104">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1104">**Description**</span></span>

<span data-ttu-id="09389-1105">Este evento representa la recuperación de la dirección IP y el prefijo en el índice especificado de la tabla de direcciones de interfaz de instancia IP por medio de nxd_ipv6_interface_address_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1105">This event represents retrieving the IP address and prefix at the specified index into the IP instance interface address table via nxd_ipv6_interface_address_get.</span></span>

<span data-ttu-id="09389-1106">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1106">**Information Fields**</span></span>

- <span data-ttu-id="09389-1107">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1107">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1108">Campo de información 2: cuarta palabra (menos significativa) de la dirección IPv6 que se va a devolver</span><span class="sxs-lookup"><span data-stu-id="09389-1108">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="09389-1109">Campo de información 4: índice de la interfaz en la tabla de interfaces de instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1109">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-interface-address-set"></a><span data-ttu-id="09389-1110">Establecimiento de dirección de interfaz de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1110">Duo IPv6 Interface Address Set</span></span> 

### <a name="nxd_ipv6_interface_address_set"></a><span data-ttu-id="09389-1111">nxd_ipv6_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="09389-1111">nxd_ipv6_interface_address_set</span></span>

<span data-ttu-id="09389-1112">**Icono** ![Icono de establecimiento de dirección de interfaz de I P v 6 doble](./media/user-guide/netx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1112">**Icon** ![Duo I P v 6 interface addresss et icon](./media/user-guide/netx-events/image68.png)</span></span>

<span data-ttu-id="09389-1113">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1113">**Description**</span></span>

<span data-ttu-id="09389-1114">Este evento representa el establecimiento de la dirección IP y el prefijo en el índice especificado de la tabla de direcciones de interfaz de instancia IP</span><span class="sxs-lookup"><span data-stu-id="09389-1114">This event represents setting the IP address and prefix at the specified index into the IP instance interface address table.</span></span> <span data-ttu-id="09389-1115">por medio de nxd_ipv6_interface_address_set. No se permite en el índice cero (dirección local del vínculo).</span><span class="sxs-lookup"><span data-stu-id="09389-1115">Not permitted on index zero (link local address) via nxd_ipv6_interface_address_set.</span></span>

<span data-ttu-id="09389-1116">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1116">**Information Fields**</span></span>

- <span data-ttu-id="09389-1117">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1117">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1118">Campo de información 2: cuarta palabra (menos significativa) de la dirección IPv6 que se va a devolver</span><span class="sxs-lookup"><span data-stu-id="09389-1118">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="09389-1119">Campo de información 3: longitud del prefijo</span><span class="sxs-lookup"><span data-stu-id="09389-1119">Info Field 3: Prefix length</span></span>
- <span data-ttu-id="09389-1120">Campo de información 4: índice de la interfaz en la tabla de interfaces de instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1120">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-link-local-address-get"></a><span data-ttu-id="09389-1121">Obtención de dirección local de vínculo de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1121">Duo IPv6 Link Local Address Get</span></span> 

#### <a name="nxd_ipv6_linklocal_address_get"></a><span data-ttu-id="09389-1122">nxd_ipv6_linklocal_address_get</span><span class="sxs-lookup"><span data-stu-id="09389-1122">nxd_ipv6_linklocal_address_get</span></span>

<span data-ttu-id="09389-1123">**Icono** ![Icono de obtención de dirección local de vínculo de I P v 6 doble](./media/user-guide/netx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1123">**Icon** ![Duo I P v 6 link local address get icon](./media/user-guide/netx-events/image69.png)</span></span>

<span data-ttu-id="09389-1124">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1124">**Description**</span></span>

<span data-ttu-id="09389-1125">Este evento representa la recuperación de la dirección local del vínculo de la instancia de IP especificada por medio de nxd_ipv6_linklocal_address_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1125">This event represents retrieving the link local address of the specified IP instance via nxd_ipv6_linklocal_address_get.</span></span>

<span data-ttu-id="09389-1126">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1126">**Information Fields**</span></span>

- <span data-ttu-id="09389-1127">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1127">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1128">Campo de información 2: cuarta palabra (menos significativa) de la dirección local del vínculo de IPv6</span><span class="sxs-lookup"><span data-stu-id="09389-1128">Info Field 2: Fourth word (least significant) of the IP v6 link local address</span></span>
- <span data-ttu-id="09389-1129">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1129">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1130">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1130">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-link-local-address-set"></a><span data-ttu-id="09389-1131">Establecimiento de dirección local de vínculo de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1131">Duo IPv6 Link Local Address Set</span></span> 

#### <a name="nxd_ipv6_linklocal_address_set"></a><span data-ttu-id="09389-1132">nxd_ipv6_linklocal_address_set</span><span class="sxs-lookup"><span data-stu-id="09389-1132">nxd_ipv6_linklocal_address_set</span></span>

<span data-ttu-id="09389-1133">**Icono** ![Icono de establecimiento de dirección local de vínculo de I P v 6 doble](./media/user-guide/netx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1133">**Icon** ![Duo I P v 6 link local address set icon](./media/user-guide/netx-events/image70.png)</span></span>

<span data-ttu-id="09389-1134">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1134">**Description**</span></span>

<span data-ttu-id="09389-1135">Este evento representa el establecimiento de la dirección local del vínculo de la instancia de IP por medio de nxd_ipv6_linklocal_address_set.</span><span class="sxs-lookup"><span data-stu-id="09389-1135">This event represents setting the link local address of the IP instance via nxd_ipv6_linklocal_address_set.</span></span>

<span data-ttu-id="09389-1136">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1136">**Information Fields**</span></span>

- <span data-ttu-id="09389-1137">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1137">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1138">Campo de información 2: cuarta palabra (menos significativa) de la dirección local del vínculo IPv6</span><span class="sxs-lookup"><span data-stu-id="09389-1138">Info Field 2: Fourth (least significant) word of the IPv6 link local address</span></span>
- <span data-ttu-id="09389-1139">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1139">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1140">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1140">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-raw-packet-send"></a><span data-ttu-id="09389-1141">Envío de paquete sin formato de IPv6 doble</span><span class="sxs-lookup"><span data-stu-id="09389-1141">Duo IPv6 Raw Packet Send</span></span> 

#### <a name="nxd_ipv6_raw_packet_send"></a><span data-ttu-id="09389-1142">nxd_ipv6_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="09389-1142">nxd_ipv6_raw_packet_send</span></span>

<span data-ttu-id="09389-1143">**Icono** ![Icono de envío de paquete sin formato de I P v 6 doble](./media/user-guide/netx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1143">**Icon** ![Duo I P v 6 raw packet send icon](./media/user-guide/netx-events/image71.png)</span></span>

<span data-ttu-id="09389-1144">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1144">**Description**</span></span>

<span data-ttu-id="09389-1145">Este evento representa el envío de un paquete IP sin formato a través de la interfaz IP principal al destino especificado por medio de nxd_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="09389-1145">This event represents sending a raw IP packet through the primary IP interface to the speficied destination via nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="09389-1146">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1146">**Information Fields**</span></span>

- <span data-ttu-id="09389-1147">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1147">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1148">Campo de información 2: puntero al paquete que se va a enviar</span><span class="sxs-lookup"><span data-stu-id="09389-1148">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="09389-1149">Campo de información 3: dirección IP de destino</span><span class="sxs-lookup"><span data-stu-id="09389-1149">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="09389-1150">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1150">Info Field 4: Not used</span></span>

### <a name="duo-tcp-socket-peer-info-get"></a><span data-ttu-id="09389-1151">Obtención de información de nodo del mismo nivel de socket de TCP doble</span><span class="sxs-lookup"><span data-stu-id="09389-1151">Duo TCP Socket Peer Info Get</span></span> 

#### <a name="nxd_tcp_socket_peer_info_get"></a><span data-ttu-id="09389-1152">nxd_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1152">nxd_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="09389-1153">**Icono** ![Icono de obtención de información de nodo del mismo nivel de socket de T C P doble](./media/user-guide/netx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1153">**Icon** ![Duo T C P socket peer info get icon](./media/user-guide/netx-events/image72.png)</span></span>

<span data-ttu-id="09389-1154">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1154">**Description**</span></span>

<span data-ttu-id="09389-1155">Este evento extrae los datos del remitente de un paquete TCP recibido en el socket especificado.</span><span class="sxs-lookup"><span data-stu-id="09389-1155">This event extracts the sender data from a received TCP packet on the specified socket.</span></span> <span data-ttu-id="09389-1156">Devuelve la dirección IP y el puerto del remitente.</span><span class="sxs-lookup"><span data-stu-id="09389-1156">It returns the IP address and port of the sender.</span></span>

<span data-ttu-id="09389-1157">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1157">**Information Fields**</span></span>

- <span data-ttu-id="09389-1158">Campo de información 1: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1158">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="09389-1159">Campo de información 2: dirección IP del nodo del mismo nivel</span><span class="sxs-lookup"><span data-stu-id="09389-1159">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="09389-1160">Campo de información 3: puerto del nodo del mismo nivel</span><span class="sxs-lookup"><span data-stu-id="09389-1160">Info Field 3: Peer port</span></span>
- <span data-ttu-id="09389-1161">Campo de información 4: el bit menos significativo de la dirección IP de 32 bits</span><span class="sxs-lookup"><span data-stu-id="09389-1161">Info Field 4: The lease significant 32-bit of the IP address</span></span>

### <a name="duo-tcp-socket-set-interface"></a><span data-ttu-id="09389-1162">Establecimiento de interfaz de socket de TCP doble</span><span class="sxs-lookup"><span data-stu-id="09389-1162">Duo TCP Socket Set Interface</span></span> 

#### <a name="nxd_tcp_socket_set_interface"></a><span data-ttu-id="09389-1163">nxd_tcp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="09389-1163">nxd_tcp_socket_set_interface</span></span>

<span data-ttu-id="09389-1164">**Icono** ![Icono de establecimiento de interfaz de socket de T C P doble](./media/user-guide/netx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1164">**Icon** ![Duo T C P socket set interface icon](./media/user-guide/netx-events/image73.png)</span></span>

<span data-ttu-id="09389-1165">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1165">**Description**</span></span>

<span data-ttu-id="09389-1166">Este evento representa el establecimiento de la interfaz de socket saliente después de que un cliente se conecta con un servidor TCP en la dirección IP del servidor especificada por medio de nxd_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="09389-1166">This event represents setting the outgoing socket interface after a client connects with a TCP server on the specified server IP address via nxd_tcp_client_socket_connect.</span></span>

<span data-ttu-id="09389-1167">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1167">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1168">Campo de información 1: puntero al socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1168">Info Field 1: Pointer to TCP Socket</span></span>
- <span data-ttu-id="09389-1169">Campo de información 2: identificador de la interfaz</span><span class="sxs-lookup"><span data-stu-id="09389-1169">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="09389-1170">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1170">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1171">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1171">Info Field 4: Not used</span></span>

### <a name="duo-udp-socket-send"></a><span data-ttu-id="09389-1172">Envío de socket de UDP doble</span><span class="sxs-lookup"><span data-stu-id="09389-1172">Duo UDP Socket Send</span></span> 

#### <a name="nxd_udp_socket_send"></a><span data-ttu-id="09389-1173">nxd_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="09389-1173">nxd_udp_socket_send</span></span>

<span data-ttu-id="09389-1174">**Icono** ![Icono de envío de socket de U D P doble](./media/user-guide/netx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1174">**Icon** ![Duo U D P socket send icon](./media/user-guide/netx-events/image74.png)</span></span>

<span data-ttu-id="09389-1175">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1175">**Description**</span></span>

<span data-ttu-id="09389-1176">Este evento representa el envío de un paquete UDP a través del socket especificado con la dirección IP y el puerto de entrada por medio de nxd_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="09389-1176">This event represents sending a UDP packet through the specified socket with the input IP address and port via nxd_udp_socket_send.</span></span>

<span data-ttu-id="09389-1177">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1177">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1178">Campo de información 1: puntero al socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-1178">Info Field 1: Pointer UDP Socket</span></span>
- <span data-ttu-id="09389-1179">Campo de información 2: puntero al paquete UDP</span><span class="sxs-lookup"><span data-stu-id="09389-1179">Info Field 2: Pointer to UDP packet</span></span>
- <span data-ttu-id="09389-1180">Campo de información 3: longitud del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1180">Info Field 3: Packet length</span></span>
- <span data-ttu-id="09389-1181">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1181">Info Field 4: Not used</span></span>


### <a name="duo-udp-socket-set-interface"></a><span data-ttu-id="09389-1182">Establecimiento de interfaz de socket de UDP doble</span><span class="sxs-lookup"><span data-stu-id="09389-1182">Duo UDP Socket Set Interface</span></span> 

#### <a name="nxd_udp_socket_set_interface"></a><span data-ttu-id="09389-1183">nxd_udp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="09389-1183">nxd_udp_socket_set_interface</span></span>

<span data-ttu-id="09389-1184">**Icono** ![Icono de establecimiento de interfaz de socket de U D P doble](./media/user-guide/netx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1184">**Icon** ![Duo U D P socket set interface icon](./media/user-guide/netx-events/image75.png)</span></span>

<span data-ttu-id="09389-1185">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1185">**Description**</span></span>

<span data-ttu-id="09389-1186">Este evento representa el establecimiento de la interfaz de salida del socket UDP especificado en la interfaz correspondiente al identificador de interfaz de entrada por medio de nxd_udp_socket_set_interface.</span><span class="sxs-lookup"><span data-stu-id="09389-1186">This event represents setting the specified UDP socket outgoing interface to the interface corresponding to the input interface ID via nxd_udp_socket_set_interface.</span></span>

<span data-ttu-id="09389-1187">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1187">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1188">Campo de información 1: puntero al socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-1188">Info Field 1: Pointer to UDP Socket</span></span>
- <span data-ttu-id="09389-1189">Campo de información 2: identificador de la interfaz</span><span class="sxs-lookup"><span data-stu-id="09389-1189">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="09389-1190">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1190">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1191">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1191">Info Field 4: Not used</span></span>

### <a name="duo-udp-source-extract"></a><span data-ttu-id="09389-1192">Extracción de origen de UDP doble</span><span class="sxs-lookup"><span data-stu-id="09389-1192">Duo UDP Source Extract</span></span> 

#### <a name="nxd_udp_socket_extract"></a><span data-ttu-id="09389-1193">nxd_udp_socket_extract</span><span class="sxs-lookup"><span data-stu-id="09389-1193">nxd_udp_socket_extract</span></span>

<span data-ttu-id="09389-1194">**Icono** ![Icono de extracción de origen de U D P doble](./media/user-guide/netx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1194">**Icon** ![Duo U D P source extract icon](./media/user-guide/netx-events/image76.png)</span></span>

<span data-ttu-id="09389-1195">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1195">**Description**</span></span>

<span data-ttu-id="09389-1196">Este evento representa la extracción de la dirección IP y el puerto de origen de un paquete recibido (ya sea IPv4 o IPv6).</span><span class="sxs-lookup"><span data-stu-id="09389-1196">This event represents extracting the IP address and source port of a received packet (either IPv4 or IPv6).</span></span> <span data-ttu-id="09389-1197">Si es IPv6, la cuarta palabra (menos significativa) de la dirección IP se devuelve por medio de nxd_udp_source_extract.</span><span class="sxs-lookup"><span data-stu-id="09389-1197">If IPv6, the fourth word (least significant) of the IP address is returned via nxd_udp_source_extract.</span></span>

<span data-ttu-id="09389-1198">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1198">**Information Fields**</span></span>

- <span data-ttu-id="09389-1199">Campo de información 1: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1199">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="09389-1200">Campo de información 2: versión de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1200">Info Field 2: IP version</span></span>
- <span data-ttu-id="09389-1201">Campo de información 3: dirección IP de origen (IPv4 o IPv6)</span><span class="sxs-lookup"><span data-stu-id="09389-1201">Info Field 3: Source IP address (IPv4 or IPv6)</span></span>
- <span data-ttu-id="09389-1202">Campo de información 4: puerto de origen</span><span class="sxs-lookup"><span data-stu-id="09389-1202">Info Field 4: Source port</span></span>

### <a name="icmp-enable"></a><span data-ttu-id="09389-1203">Habilitación de ICMP</span><span class="sxs-lookup"><span data-stu-id="09389-1203">ICMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="09389-1204">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1204">nx_icmp_enable</span></span>

<span data-ttu-id="09389-1205">**Icono** ![Icono de habilitación de I C M P](./media/user-guide/netx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1205">**Icon** ![I C M P enable icon](./media/user-guide/netx-events/image77.png)</span></span>

<span data-ttu-id="09389-1206">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1206">**Description**</span></span>

<span data-ttu-id="09389-1207">Este evento representa la habilitación de ICMP por medio de nx_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1207">This event represents enabling ICMP via nx_icmp_enable.</span></span>

<span data-ttu-id="09389-1208">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1208">**Information Fields**</span></span>

- <span data-ttu-id="09389-1209">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1209">Info Field 1: Pointer to the IP instance l;</span></span>
- <span data-ttu-id="09389-1210">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1210">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1211">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1211">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1212">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1212">Info Field 4: Not used</span></span>

### <a name="icmp-information-get"></a><span data-ttu-id="09389-1213">Obtención de información de ICMP</span><span class="sxs-lookup"><span data-stu-id="09389-1213">ICMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="09389-1214">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1214">nx_icmp_info_get</span></span>

<span data-ttu-id="09389-1215">**Icono** ![Icono de obtención de información de I C M P](./media/user-guide/netx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1215">**Icon** ![I C M P information get icon](./media/user-guide/netx-events/image78.png)</span></span>

<span data-ttu-id="09389-1216">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1216">**Description**</span></span>

<span data-ttu-id="09389-1217">Este evento representa la obtención de información por medio de nx_icmp_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1217">This event represents getting information via nx_icmp_info_get.</span></span>

<span data-ttu-id="09389-1218">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1218">**Information Fields**</span></span>
- <span data-ttu-id="09389-1219">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1219">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1220">Campo de información 2: pings enviados</span><span class="sxs-lookup"><span data-stu-id="09389-1220">Info Field 2: Pings sent</span></span>
- <span data-ttu-id="09389-1221">Campo de información 3: respuestas de ping</span><span class="sxs-lookup"><span data-stu-id="09389-1221">Info Field 3: Ping responses</span></span>
- <span data-ttu-id="09389-1222">Campo de información 4: pings recibidos</span><span class="sxs-lookup"><span data-stu-id="09389-1222">Info Field 4: Pings received</span></span>

### <a name="icmp-ping"></a><span data-ttu-id="09389-1223">Ping de ICMP</span><span class="sxs-lookup"><span data-stu-id="09389-1223">ICMP Ping</span></span> 

#### <a name="nx_icmp_ping"></a><span data-ttu-id="09389-1224">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="09389-1224">nx_icmp_ping</span></span>

<span data-ttu-id="09389-1225">**Icono** ![Icono de ping de I C M P](./media/user-guide/netx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1225">**Icon** ![I C M P ping icon](./media/user-guide/netx-events/image79.png)</span></span>

<span data-ttu-id="09389-1226">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1226">**Description**</span></span>

<span data-ttu-id="09389-1227">Este evento representa el envío de ping a una dirección IP de destino por medio de nx_icmp_ping.</span><span class="sxs-lookup"><span data-stu-id="09389-1227">This event represents pinging a target IP address via nx_icmp_ping.</span></span>

<span data-ttu-id="09389-1228">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1228">**Information Fields**</span></span>

- <span data-ttu-id="09389-1229">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1229">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1230">Campo de información 2: dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-1230">Info Field 2: IP address</span></span>
- <span data-ttu-id="09389-1231">Campo de información 3: puntero a los datos</span><span class="sxs-lookup"><span data-stu-id="09389-1231">Info Field 3: Pointer to data</span></span>
- <span data-ttu-id="09389-1232">Campo de información 4: tamaño de los datos</span><span class="sxs-lookup"><span data-stu-id="09389-1232">Info Field 4: Size of data</span></span>

### <a name="igmp-enable"></a><span data-ttu-id="09389-1233">Habilitación de IGMP</span><span class="sxs-lookup"><span data-stu-id="09389-1233">IGMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="09389-1234">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1234">nx_icmp_enable</span></span>

<span data-ttu-id="09389-1235">**Icono** ![Icono de habilitación de I G M P](./media/user-guide/netx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1235">**Icon** ![I G M P enable icon](./media/user-guide/netx-events/image80.png)</span></span>

<span data-ttu-id="09389-1236">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1236">**Description**</span></span>

<span data-ttu-id="09389-1237">Este evento representa la habilitación de IGMP por medio de nx_igmp_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1237">This event represents enabling IGMP via nx_igmp_enable.</span></span>

<span data-ttu-id="09389-1238">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1238">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1239">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1239">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1240">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1240">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1241">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1241">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1242">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1242">Info Field 4: Not used</span></span>

### <a name="igmp-information-get"></a><span data-ttu-id="09389-1243">Obtención de información de IGMP</span><span class="sxs-lookup"><span data-stu-id="09389-1243">IGMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="09389-1244">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1244">nx_icmp_info_get</span></span>

<span data-ttu-id="09389-1245">**Icono** ![Icono de obtención de información de I G M P](./media/user-guide/netx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1245">**Icon** ![I G M P information get icon](./media/user-guide/netx-events/image81.png)</span></span>

<span data-ttu-id="09389-1246">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1246">**Description**</span></span>

<span data-ttu-id="09389-1247">Este evento representa la obtención de información por medio de nx_igmp_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1247">This event represents getting information via nx_igmp_info_get.</span></span>

<span data-ttu-id="09389-1248">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1248">**Information Fields**</span></span>

- <span data-ttu-id="09389-1249">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1249">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1250">Campo de información 2: informes enviados</span><span class="sxs-lookup"><span data-stu-id="09389-1250">Info Field 2: Reports sent</span></span>
- <span data-ttu-id="09389-1251">Campo de información 3: consultas recibidas</span><span class="sxs-lookup"><span data-stu-id="09389-1251">Info Field 3: Queries received</span></span>
- <span data-ttu-id="09389-1252">Campo de información 4: grupos combinados</span><span class="sxs-lookup"><span data-stu-id="09389-1252">Info Field 4: Groups joined</span></span>

### <a name="igmp-loopback-disable"></a><span data-ttu-id="09389-1253">Deshabilitación de bucle invertido de IGMP</span><span class="sxs-lookup"><span data-stu-id="09389-1253">IGMP Loopback Disable</span></span> 

#### <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="09389-1254">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="09389-1254">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="09389-1255">**Icono** ![Icono de deshabilitación de bucle invertido de I G M P](./media/user-guide/netx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1255">**Icon** ![I G M P loopback disable icon](./media/user-guide/netx-events/image82.png)</span></span>

<span data-ttu-id="09389-1256">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1256">**Description**</span></span>

<span data-ttu-id="09389-1257">Este evento representa la deshabilitación del bucle invertido de IGMP por medio de nx_igmp_loopback_disable.</span><span class="sxs-lookup"><span data-stu-id="09389-1257">This event represents disabling IGMP loopback via nx_igmp_loopback_disable.</span></span>

<span data-ttu-id="09389-1258">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1258">**Information Fields**</span></span>

- <span data-ttu-id="09389-1259">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1259">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1260">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1260">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1261">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1261">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1262">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1262">Info Field 4: Not used</span></span>

### <a name="igmp-loopback-enable"></a><span data-ttu-id="09389-1263">Habilitación de bucle invertido de IGMP</span><span class="sxs-lookup"><span data-stu-id="09389-1263">IGMP Loopback Enable</span></span> 

#### <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="09389-1264">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1264">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="09389-1265">**Icono** ![Icono de habilitación de bucle invertido de I G M P](./media/user-guide/netx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1265">**Icon** ![I G M P loopback enable icon](./media/user-guide/netx-events/image83.png)</span></span>

<span data-ttu-id="09389-1266">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1266">**Description**</span></span>

<span data-ttu-id="09389-1267">Este evento representa la habilitación del bucle invertido de IGMP por medio de nx_igmp_loopback_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1267">This event represents enabling IGMP loopback via nx_igmp_loopback_enable.</span></span>

<span data-ttu-id="09389-1268">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1268">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1269">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1269">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1270">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1270">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1271">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1271">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1272">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1272">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-join"></a><span data-ttu-id="09389-1273">Combinación de multidifusión de IGMP</span><span class="sxs-lookup"><span data-stu-id="09389-1273">IGMP Multicast Join</span></span> 

#### <a name="nx_igmp_multicast_join"></a><span data-ttu-id="09389-1274">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="09389-1274">nx_igmp_multicast_join</span></span>

<span data-ttu-id="09389-1275">**Icono** ![Icono de combinación de multidifusión de I G M P](./media/user-guide/netx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1275">**Icon** ![I G M P multicast join icon](./media/user-guide/netx-events/image84.png)</span></span>

<span data-ttu-id="09389-1276">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1276">**Description**</span></span>

<span data-ttu-id="09389-1277">Este evento representa la combinación de un grupo de multidifusión por medio de nx_igmp_multicast_join.</span><span class="sxs-lookup"><span data-stu-id="09389-1277">This event represents joining a multicast group via nx_igmp_multicast_join.</span></span>

<span data-ttu-id="09389-1278">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1278">**Information Fields**</span></span>

- <span data-ttu-id="09389-1279">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1279">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1280">Campo de información 2: dirección IP del grupo</span><span class="sxs-lookup"><span data-stu-id="09389-1280">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="09389-1281">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1281">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1282">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1282">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-leave"></a><span data-ttu-id="09389-1283">Salida de multidifusión de IGMP</span><span class="sxs-lookup"><span data-stu-id="09389-1283">IGMP Multicast Leave</span></span> 

#### <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="09389-1284">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="09389-1284">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="09389-1285">**Icono** ![Icono de salida de multidifusión de I G M P](./media/user-guide/netx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1285">**Icon** ![I G M P multicast leave icon](./media/user-guide/netx-events/image85.png)</span></span>

<span data-ttu-id="09389-1286">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1286">**Description**</span></span>

<span data-ttu-id="09389-1287">Este evento representa la salida de un grupo de multidifusión por medio de nx_igmp_multicast_leave.</span><span class="sxs-lookup"><span data-stu-id="09389-1287">This event represents leaving a multicast group via nx_igmp_multicast_leave.</span></span>

<span data-ttu-id="09389-1288">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1288">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1289">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1289">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1290">Campo de información 2: dirección IP del grupo</span><span class="sxs-lookup"><span data-stu-id="09389-1290">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="09389-1291">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1291">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1292">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1292">Info Field 4: Not used</span></span>

### <a name="ip-address-change-notify"></a><span data-ttu-id="09389-1293">Notificación de cambio de dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-1293">IP Address Change Notify</span></span> 

#### <a name="nx_ip_address_change_notify"></a><span data-ttu-id="09389-1294">nx_ip_address_change_notify</span><span class="sxs-lookup"><span data-stu-id="09389-1294">nx_ip_address_change_notify</span></span>

<span data-ttu-id="09389-1295">**Icono** ![Icono de notificación de cambio de dirección I P](./media/user-guide/netx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1295">**Icon** ![I P address change notify icon](./media/user-guide/netx-events/image86.png)</span></span>

<span data-ttu-id="09389-1296">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1296">**Description**</span></span>

<span data-ttu-id="09389-1297">Este evento representa el registro de la notificación de cambio de IP por medio de nx_ip_address_change_notify.</span><span class="sxs-lookup"><span data-stu-id="09389-1297">This event represents registering for IP change notification via nx_ip_address_change_notify.</span></span>

<span data-ttu-id="09389-1298">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1298">**Information Fields**</span></span>

- <span data-ttu-id="09389-1299">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1299">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1300">Campo de información 2: puntero a la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="09389-1300">Info Field 2: Callback function pointer</span></span>
- <span data-ttu-id="09389-1301">Campo de información 3: puntero a información adicional</span><span class="sxs-lookup"><span data-stu-id="09389-1301">Info Field 3: Additional information pointer</span></span>
- <span data-ttu-id="09389-1302">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1302">Info Field 4: Not used</span></span>

### <a name="ip-address-get"></a><span data-ttu-id="09389-1303">Obtención de dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-1303">IP Address Get</span></span> 

#### <a name="nx_ip_address_get"></a><span data-ttu-id="09389-1304">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="09389-1304">nx_ip_address_get</span></span>

<span data-ttu-id="09389-1305">**Icono** ![Icono de obtención de dirección I P](./media/user-guide/netx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1305">**Icon** ![I P address get icon](./media/user-guide/netx-events/image87.png)</span></span>

<span data-ttu-id="09389-1306">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1306">**Description**</span></span>

<span data-ttu-id="09389-1307">Este evento representa la obtención de la dirección IP por medio de nx_ip_address_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1307">This event represents getting the IP address via nx_ip_address_get.</span></span>

<span data-ttu-id="09389-1308">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1308">**Information Fields**</span></span>

- <span data-ttu-id="09389-1309">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1309">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1310">Campo de información 2: dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-1310">Info Field 2: IP address</span></span>
- <span data-ttu-id="09389-1311">Campo de información 3: máscara de red</span><span class="sxs-lookup"><span data-stu-id="09389-1311">Info Field 3: Network mask</span></span>
- <span data-ttu-id="09389-1312">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1312">Info Field 4: Not used</span></span>

### <a name="ip-address-set"></a><span data-ttu-id="09389-1313">Establecimiento de dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-1313">IP Address Set</span></span> 

#### <a name="nx_ip_address_set"></a><span data-ttu-id="09389-1314">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="09389-1314">nx_ip_address_set</span></span>

<span data-ttu-id="09389-1315">**Icono** ![Icono de establecimiento de dirección I P](./media/user-guide/netx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1315">**Icon** ![I P address set icon](./media/user-guide/netx-events/image88.png)</span></span>

<span data-ttu-id="09389-1316">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1316">**Description**</span></span>

<span data-ttu-id="09389-1317">Este evento representa el establecimiento de la dirección IP por medio de nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="09389-1317">This event represents setting the IP address via nx_ip_address_set.</span></span>

<span data-ttu-id="09389-1318">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1318">**Information Fields**</span></span>

- <span data-ttu-id="09389-1319">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1319">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1320">Campo de información 2: dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-1320">Info Field 2: IP address</span></span>
- <span data-ttu-id="09389-1321">Campo de información 3: máscara de red</span><span class="sxs-lookup"><span data-stu-id="09389-1321">Info Field 3: Network mask</span></span>
- <span data-ttu-id="09389-1322">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1322">Info Field 4: Not used</span></span>

### <a name="ip-create"></a><span data-ttu-id="09389-1323">Creación de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1323">IP Create</span></span> 

#### <a name="nx_ip_create"></a><span data-ttu-id="09389-1324">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="09389-1324">nx_ip_create</span></span>

<span data-ttu-id="09389-1325">**Icono** ![Icono de creación de I P](./media/user-guide/netx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1325">**Icon** ![I P create icon](./media/user-guide/netx-events/image89.png)</span></span>

<span data-ttu-id="09389-1326">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1326">**Description**</span></span>

<span data-ttu-id="09389-1327">Este evento representa la creación de una instancia de IP por medio de nx_ip_create.</span><span class="sxs-lookup"><span data-stu-id="09389-1327">This event represents creating an IP instance via nx_ip_create.</span></span>

<span data-ttu-id="09389-1328">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1328">**Information Fields**</span></span> 
- <span data-ttu-id="09389-1329">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1329">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1330">Campo de información 2: dirección IP</span><span class="sxs-lookup"><span data-stu-id="09389-1330">Info Field 2: IP address</span></span>
- <span data-ttu-id="09389-1331">Campo de información 3: máscara de red</span><span class="sxs-lookup"><span data-stu-id="09389-1331">Info Field 3: Network mask</span></span>
- <span data-ttu-id="09389-1332">Campo de información 4: puntero al grupo de paquetes predeterminado</span><span class="sxs-lookup"><span data-stu-id="09389-1332">Info Field 4: Default packet pool pointer</span></span>

### <a name="ip-delete"></a><span data-ttu-id="09389-1333">Eliminación de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1333">IP Delete</span></span> 

#### <a name="nx_ip_delete"></a><span data-ttu-id="09389-1334">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="09389-1334">nx_ip_delete</span></span>

<span data-ttu-id="09389-1335">**Icono** ![Icono de eliminación de I P](./media/user-guide/netx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1335">**Icon** ![I P delete icon](./media/user-guide/netx-events/image90.png)</span></span>

<span data-ttu-id="09389-1336">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1336">**Description**</span></span>

<span data-ttu-id="09389-1337">Este evento representa la eliminación de una instancia de IP por medio de nx_ip_delete.</span><span class="sxs-lookup"><span data-stu-id="09389-1337">This event represents deleting an IP instance via nx_ip_delete.</span></span>

<span data-ttu-id="09389-1338">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1338">**Information Fields**</span></span>

- <span data-ttu-id="09389-1339">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1339">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1340">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1340">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1341">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1341">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1342">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1342">Info Field 4: Not used</span></span>

### <a name="ip-driver-direct-command"></a><span data-ttu-id="09389-1343">Comando directo de controlador de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1343">IP Driver Direct Command</span></span> 

#### <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="09389-1344">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="09389-1344">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="09389-1345">**Icono** ![Icono de comando directo de controlador de I P](./media/user-guide/netx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1345">**Icon** ![I P driver direct command icon](./media/user-guide/netx-events/image91.png)</span></span>

<span data-ttu-id="09389-1346">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1346">**Description**</span></span>

<span data-ttu-id="09389-1347">Este evento representa un comando de controlador de E/S directo por medio de nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="09389-1347">This event represents a direct I/O driver command via nx_ip_driver_direct_command.</span></span>

<span data-ttu-id="09389-1348">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1348">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1349">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1349">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1350">Campo de información 2: comando del controlador</span><span class="sxs-lookup"><span data-stu-id="09389-1350">Info Field 2: Driver command</span></span>
- <span data-ttu-id="09389-1351">Campo de información 3: valor devuelto</span><span class="sxs-lookup"><span data-stu-id="09389-1351">Info Field 3: Return value</span></span>
- <span data-ttu-id="09389-1352">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1352">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-disable"></a><span data-ttu-id="09389-1353">Deshabilitación del reenvío de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1353">IP Forwarding Disable</span></span> 

#### <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="09389-1354">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="09389-1354">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="09389-1355">**Icono** ![Icono de deshabilitación de reenvío de I P](./media/user-guide/netx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1355">**Icon** ![I P forwarding disable icon](./media/user-guide/netx-events/image92.png)</span></span>

<span data-ttu-id="09389-1356">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1356">**Description**</span></span>

<span data-ttu-id="09389-1357">Este evento representa la deshabilitación del reenvío IP por medio de nx_ip_forwarding_disable.</span><span class="sxs-lookup"><span data-stu-id="09389-1357">This event represents disabling IP forwarding via nx_ip_forwarding_disable.</span></span>

<span data-ttu-id="09389-1358">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1358">**Information Fields**</span></span>

- <span data-ttu-id="09389-1359">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1359">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1360">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1360">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1361">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1361">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1362">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1362">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-enable"></a><span data-ttu-id="09389-1363">Habilitación del reenvío de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1363">IP Forwarding Enable</span></span> 

#### <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="09389-1364">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1364">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="09389-1365">**Icono** ![Icono de habilitación de reenvío de I P](./media/user-guide/netx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1365">**Icon** ![I P forwarding enable icon](./media/user-guide/netx-events/image93.png)</span></span>

<span data-ttu-id="09389-1366">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1366">**Description**</span></span>

<span data-ttu-id="09389-1367">Este evento representa la habilitación del reenvío de IP por medio de nx_ip_forwarding_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1367">This event represents enabling IP forwarding via nx_ip_forwarding_enable.</span></span>

<span data-ttu-id="09389-1368">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1368">**Information Fields**</span></span>

- <span data-ttu-id="09389-1369">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1369">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1370">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1370">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1371">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1371">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1372">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1372">Info Field 4: Not used</span></span>

### <a name="ip-fragment-disable"></a><span data-ttu-id="09389-1373">Deshabilitación de fragmento de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1373">IP Fragment Disable</span></span> 

#### <a name="nx_ip_fragment_disable"></a><span data-ttu-id="09389-1374">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="09389-1374">nx_ip_fragment_disable</span></span>

<span data-ttu-id="09389-1375">**Icono** ![Icono de deshabilitación de fragmento de I P](./media/user-guide/netx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1375">**Icon** ![I P fragment disable icon](./media/user-guide/netx-events/image94.png)</span></span>

<span data-ttu-id="09389-1376">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1376">**Description**</span></span>

<span data-ttu-id="09389-1377">Este evento representa la deshabilitación de la fragmentación de IP por medio de nx_ip_fragment_disable.</span><span class="sxs-lookup"><span data-stu-id="09389-1377">This event represents disabling IP fragmenting via nx_ip_fragment_disable.</span></span>

<span data-ttu-id="09389-1378">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1378">**Information Fields**</span></span>

- <span data-ttu-id="09389-1379">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1379">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1380">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1380">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1381">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1381">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1382">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1382">Info Field 4: Not used</span></span>

### <a name="ip-fragment-enable"></a><span data-ttu-id="09389-1383">Habilitación de fragmento de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1383">IP Fragment Enable</span></span> 

#### <a name="nx_ip_fragment_enable"></a><span data-ttu-id="09389-1384">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1384">nx_ip_fragment_enable</span></span>

<span data-ttu-id="09389-1385">**Icono** ![Icono de habilitación de fragmento de I P](./media/user-guide/netx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1385">**Icon** ![I P fragment enable icon](./media/user-guide/netx-events/image95.png)</span></span>

<span data-ttu-id="09389-1386">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1386">**Description**</span></span>

<span data-ttu-id="09389-1387">Este evento representa la habilitación de la fragmentación de IP por medio de nx_ip_fragment_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1387">This event represents enabling IP fragmenting via nx_ip_fragment_enable.</span></span>

<span data-ttu-id="09389-1388">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1388">**Information Fields**</span></span>

- <span data-ttu-id="09389-1389">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1389">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1390">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1390">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1391">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1391">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1392">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1392">Info Field 4: Not used</span></span>

### <a name="ip-gateway-address-set"></a><span data-ttu-id="09389-1393">Establecimiento de dirección de puerta de enlace de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1393">IP Gateway Address Set</span></span> 

#### <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="09389-1394">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="09389-1394">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="09389-1395">**Icono** ![Icono de establecimiento de dirección de puerta de enlace de I P](./media/user-guide/netx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1395">**Icon** ![I P gateway address set icon](./media/user-guide/netx-events/image96.png)</span></span>

<span data-ttu-id="09389-1396">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1396">**Description**</span></span>

<span data-ttu-id="09389-1397">Este evento representa el establecimiento de la dirección IP de puerta de enlace por medio de nx_ip_gateway_address_set.</span><span class="sxs-lookup"><span data-stu-id="09389-1397">This event represents setting the gateway IP address via nx_ip_gateway_address_set.</span></span>

<span data-ttu-id="09389-1398">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1398">**Information Fields**</span></span>

- <span data-ttu-id="09389-1399">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1399">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1400">Campo de información 2: dirección IP de puerta de enlace</span><span class="sxs-lookup"><span data-stu-id="09389-1400">Info Field 2: Gateway IP address</span></span>
- <span data-ttu-id="09389-1401">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1401">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1402">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1402">Info Field 4: Not used</span></span>

### <a name="ip-information-get"></a><span data-ttu-id="09389-1403">Obtención de información de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1403">IP Information Get</span></span> 

#### <a name="nx_ip_info_get"></a><span data-ttu-id="09389-1404">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1404">nx_ip_info_get</span></span>

<span data-ttu-id="09389-1405">**Icono** ![Icono de obtención de información de I P](./media/user-guide/netx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1405">**Icon** ![I P information get icon](./media/user-guide/netx-events/image97.png)</span></span>

<span data-ttu-id="09389-1406">**Descripción** Este evento representa la obtención de información de IP por medio de nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1406">**Description** This event represents getting IP information via nx_ip_info_get.</span></span>

<span data-ttu-id="09389-1407">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1407">**Information Fields**</span></span>

- <span data-ttu-id="09389-1408">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1408">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1409">Campo de información 2: bytes de IP enviados</span><span class="sxs-lookup"><span data-stu-id="09389-1409">Info Field 2: IP bytes sent</span></span>
- <span data-ttu-id="09389-1410">Campo de información 3: bytes de IP recibidos</span><span class="sxs-lookup"><span data-stu-id="09389-1410">Info Field 3: IP bytes received</span></span>
- <span data-ttu-id="09389-1411">Campo de información 4: paquetes de IP descartados</span><span class="sxs-lookup"><span data-stu-id="09389-1411">Info Field 4: IP packets dropped</span></span>

### <a name="ip-interface-attach"></a><span data-ttu-id="09389-1412">Asociación de interfaz de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1412">IP Interface Attach</span></span> 

#### <a name="nx_interface_attach"></a><span data-ttu-id="09389-1413">nx_interface_attach</span><span class="sxs-lookup"><span data-stu-id="09389-1413">nx_interface_attach</span></span>

<span data-ttu-id="09389-1414">**Icono** ![Icono de asociación de interfaz de I P](./media/user-guide/netx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1414">**Icon** ![I P iterface attach icon](./media/user-guide/netx-events/image98.png)</span></span>

<span data-ttu-id="09389-1415">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1415">**Description**</span></span>

<span data-ttu-id="09389-1416">Este evento representa la asociación de una interfaz de red secundaria a la instancia de IP por medio de nx_ip_interface_attach.</span><span class="sxs-lookup"><span data-stu-id="09389-1416">This event represents a secondary network interface being attached to the IP instance via nx_ip_interface_attach.</span></span>

<span data-ttu-id="09389-1417">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1417">**Information Fields**</span></span>

- <span data-ttu-id="09389-1418">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1418">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1419">Campo de información 2: dirección IP de la interfaz</span><span class="sxs-lookup"><span data-stu-id="09389-1419">Info Field 2: Interface IP Address</span></span>
- <span data-ttu-id="09389-1420">Campo de información 3: índice en la tabla de interfaces de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1420">Info Field 3: Index into IP interface table</span></span>
- <span data-ttu-id="09389-1421">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1421">Info Field 4: Not used</span></span>

### <a name="ip-interface-info-get"></a><span data-ttu-id="09389-1422">Obtención de información de interfaz de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1422">IP Interface Info Get</span></span> 

#### <a name="nx_ip_interface_info_get"></a><span data-ttu-id="09389-1423">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1423">nx_ip_interface_info_get</span></span>

<span data-ttu-id="09389-1424">**Icono** ![Icono de obtención de información de interfaz de I P](./media/user-guide/netx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1424">**Icon** ![ IP interface info get icon](./media/user-guide/netx-events/image99.png)</span></span>

<span data-ttu-id="09389-1425">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1425">**Description**</span></span>

<span data-ttu-id="09389-1426">Este evento representa la recuperación de información de la interfaz de red especificada por medio de nx_ip_interface_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1426">This event represents information retrieved from the specified network interface via nx_ip_interface_info_get.</span></span>

<span data-ttu-id="09389-1427">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1427">**Information Fields**</span></span>

- <span data-ttu-id="09389-1428">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1428">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1429">Campo de información 2: dirección IP de la interfaz</span><span class="sxs-lookup"><span data-stu-id="09389-1429">Info Field 2: Interface IP address</span></span>
- <span data-ttu-id="09389-1430">Campo de información 3: MSB de la dirección MAC de la interfaz</span><span class="sxs-lookup"><span data-stu-id="09389-1430">Info Field 3: Interface MAC address msb</span></span>
- <span data-ttu-id="09389-1431">Campo de información 4: LSB de la dirección MAC de la interfaz</span><span class="sxs-lookup"><span data-stu-id="09389-1431">Info Field 4: Interface MAC address lsb</span></span>

### <a name="ip-raw-packet-disable"></a><span data-ttu-id="09389-1432">Deshabilitación de paquete sin formato de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1432">IP Raw Packet Disable</span></span> 

#### <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="09389-1433">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="09389-1433">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="09389-1434">**Icono** ![Icono de deshabilitación de paquete sin formato de I P](./media/user-guide/netx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1434">**Icon** ![I P raw packet disable icon](./media/user-guide/netx-events/image100.png)</span></span>

<span data-ttu-id="09389-1435">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1435">**Description**</span></span>

<span data-ttu-id="09389-1436">Este evento representa la deshabilitación de la comunicación de paquetes de IP sin formato por medio de nx_ip_raw_packet_disable.</span><span class="sxs-lookup"><span data-stu-id="09389-1436">This event represents disabling raw IP packet communication via nx_ip_raw_packet_disable.</span></span>

<span data-ttu-id="09389-1437">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1437">**Information Fields**</span></span>

- <span data-ttu-id="09389-1438">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1438">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1439">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1439">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1440">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1440">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1441">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1441">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-enable"></a><span data-ttu-id="09389-1442">Habilitación de paquete sin formato de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1442">IP Raw Packet Enable</span></span> 

#### <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="09389-1443">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1443">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="09389-1444">**Icono** ![Icono de habilitación de paquete sin formato de I P](./media/user-guide/netx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1444">**Icon** ![I P raw packet enable icon](./media/user-guide/netx-events/image101.png)</span></span>

<span data-ttu-id="09389-1445">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1445">**Description**</span></span>

<span data-ttu-id="09389-1446">Este evento representa la habilitación de la comunicación de paquetes de IP sin formato por medio de nx_ip_raw_packet_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1446">This event represents enabling raw IP packet communication via nx_ip_raw_packet_enable.</span></span>

<span data-ttu-id="09389-1447">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1447">**Information Fields**</span></span>

- <span data-ttu-id="09389-1448">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1448">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1449">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1449">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1450">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1450">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1451">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1451">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-receive"></a><span data-ttu-id="09389-1452">Recepción de paquete sin formato de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1452">IP Raw Packet Receive</span></span> 

#### <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="09389-1453">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="09389-1453">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="09389-1454">**Icono** ![Icono de recepción de paquete sin formato de I P](./media/user-guide/netx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1454">**Icon** ![I P raw packet receive icon](./media/user-guide/netx-events/image102.png)</span></span>

<span data-ttu-id="09389-1455">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1455">**Description**</span></span>

<span data-ttu-id="09389-1456">Este evento representa la recepción de un paquete de IP sin formato por medio de nx_ip_raw_packet_receive.</span><span class="sxs-lookup"><span data-stu-id="09389-1456">This event represents receiving a raw IP packet via nx_ip_raw_packet_receive.</span></span>

<span data-ttu-id="09389-1457">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1457">**Information Fields**</span></span>

- <span data-ttu-id="09389-1458">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1458">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1459">Campo de información 2: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1459">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="09389-1460">Campo de información 3: opción de espera</span><span class="sxs-lookup"><span data-stu-id="09389-1460">Info Field 3: Wait option</span></span>
- <span data-ttu-id="09389-1461">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1461">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-send"></a><span data-ttu-id="09389-1462">Envío de paquete sin formato de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1462">IP Raw Packet Send</span></span> 

#### <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="09389-1463">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="09389-1463">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="09389-1464">**Icono** ![Icono de envío de paquete sin formato de I P](./media/user-guide/netx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1464">**Icon** ![I P raw packet send icon](./media/user-guide/netx-events/image103.png)</span></span>

<span data-ttu-id="09389-1465">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1465">**Description**</span></span>

<span data-ttu-id="09389-1466">Este evento representa el envío de un paquete de IP sin formato por medio de nx_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="09389-1466">This event represents sending a raw IP packet via nx_ip_raw_packet_send.</span></span>

<span data-ttu-id="09389-1467">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1467">**Information Fields**</span></span>

- <span data-ttu-id="09389-1468">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1468">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1469">Campo de información 2: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1469">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="09389-1470">Campo de información 3: dirección IP de destino</span><span class="sxs-lookup"><span data-stu-id="09389-1470">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="09389-1471">Campo de información 4: tipo de servicio</span><span class="sxs-lookup"><span data-stu-id="09389-1471">Info Field 4: Type of service</span></span>

### <a name="ip-static-route-add"></a><span data-ttu-id="09389-1472">Adición de ruta estática de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1472">IP Static Route Add</span></span> 

#### <a name="nx_ip_static_route_add"></a><span data-ttu-id="09389-1473">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="09389-1473">nx_ip_static_route_add</span></span>

<span data-ttu-id="09389-1474">**Icono** ![Icono de adición de ruta estática de I P](./media/user-guide/netx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1474">**Icon** ![I P static route add icon](./media/user-guide/netx-events/image104.png)</span></span>

<span data-ttu-id="09389-1475">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1475">**Description**</span></span>

<span data-ttu-id="09389-1476">Este evento representa la adición de una ruta estática a la tabla de enrutamiento de la instancia de IP por medio de nx_ip_static_route_add.</span><span class="sxs-lookup"><span data-stu-id="09389-1476">This event represents a static route being added to the IP instance routing table via nx_ip_static_route_add.</span></span>

<span data-ttu-id="09389-1477">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1477">**Information Fields**</span></span>

- <span data-ttu-id="09389-1478">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1478">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1479">Campo de información 2: dirección de red</span><span class="sxs-lookup"><span data-stu-id="09389-1479">Info Field 2: Network address</span></span>
- <span data-ttu-id="09389-1480">Campo de información 3: máscara de red</span><span class="sxs-lookup"><span data-stu-id="09389-1480">Info Field 3: Network mask</span></span>
- <span data-ttu-id="09389-1481">Campo de información 4: próximo salto</span><span class="sxs-lookup"><span data-stu-id="09389-1481">Info Field 4: Next hop</span></span>

### <a name="ip-static-route-delete"></a><span data-ttu-id="09389-1482">Eliminación de ruta estática de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1482">IP Static Route Delete</span></span> 

#### <a name="nx_ip_static_route_delete"></a><span data-ttu-id="09389-1483">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="09389-1483">nx_ip_static_route_delete</span></span>

<span data-ttu-id="09389-1484">**Icono** ![Icono de eliminación de ruta estática de I P](./media/user-guide/netx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1484">**Icon** ![I P static rute delete icon](./media/user-guide/netx-events/image105.png)</span></span>

<span data-ttu-id="09389-1485">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1485">**Description**</span></span>

<span data-ttu-id="09389-1486">Este evento representa la eliminación de una ruta estática de la tabla de enrutamiento de la instancia de IP por medio de nx_ip_static_route_delete.</span><span class="sxs-lookup"><span data-stu-id="09389-1486">This event represents a static route being removed from the IP instance routing table via nx_ip_static_route_delete.</span></span>

<span data-ttu-id="09389-1487">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1487">**Information Fields**</span></span>

- <span data-ttu-id="09389-1488">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1488">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1489">Campo de información 2: dirección de red</span><span class="sxs-lookup"><span data-stu-id="09389-1489">Info Field 2: Network address</span></span>
- <span data-ttu-id="09389-1490">Campo de información 3: máscara de red</span><span class="sxs-lookup"><span data-stu-id="09389-1490">Info Field 3: Network mask</span></span>
- <span data-ttu-id="09389-1491">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1491">Info Field 4: Not used</span></span>

### <a name="ip-status-check"></a><span data-ttu-id="09389-1492">Comprobación de estado de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1492">IP Status Check</span></span> 

#### <a name="nx_ip_status_check"></a><span data-ttu-id="09389-1493">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="09389-1493">nx_ip_status_check</span></span>

<span data-ttu-id="09389-1494">**Icono** ![Icono de comprobación de estado de I P](./media/user-guide/netx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1494">**Icon** ![I P status check icon](./media/user-guide/netx-events/image106.png)</span></span>

<span data-ttu-id="09389-1495">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1495">**Description**</span></span>

<span data-ttu-id="09389-1496">Este evento representa la comprobación de un estado de IP por medio de nx_ip_status_check.</span><span class="sxs-lookup"><span data-stu-id="09389-1496">This event represents checking for an IP status via nx_ip_status_check.</span></span>

<span data-ttu-id="09389-1497">Campos de información</span><span class="sxs-lookup"><span data-stu-id="09389-1497">Information Fields</span></span> 

- <span data-ttu-id="09389-1498">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1498">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="09389-1499">Campo de información 2: estado solicitado</span><span class="sxs-lookup"><span data-stu-id="09389-1499">Info Field 2: Requested status</span></span>
- <span data-ttu-id="09389-1500">Campo de información 3: estado real</span><span class="sxs-lookup"><span data-stu-id="09389-1500">Info Field 3: Actual status</span></span>
- <span data-ttu-id="09389-1501">Campo de información 4: opción de espera</span><span class="sxs-lookup"><span data-stu-id="09389-1501">Info Field 4: Wait option</span></span>

### <a name="ipsec-enable"></a><span data-ttu-id="09389-1502">Habilitación de IPsec</span><span class="sxs-lookup"><span data-stu-id="09389-1502">IPSEC Enable</span></span> 

#### <a name="nx_ipsec_enable"></a><span data-ttu-id="09389-1503">nx_ipsec_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1503">nx_ipsec_enable</span></span>

<span data-ttu-id="09389-1504">**Icono** ![Icono de habilitación de I P SEC](./media/user-guide/netx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1504">**Icon** ![I P S E C enable icon](./media/user-guide/netx-events/image107.png)</span></span>

<span data-ttu-id="09389-1505">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1505">**Description**</span></span>

<span data-ttu-id="09389-1506">Este evento representa la habilitación de servicios IPsec en la instancia de IP proporcionada por medio de nx_ipsec_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1506">This event represents enabling IPSec services on the supplied IP instance via nx_ipsec_enable.</span></span>

<span data-ttu-id="09389-1507">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1507">**Information Fields**</span></span>

- <span data-ttu-id="09389-1508">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1508">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1509">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1509">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1510">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1510">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1511">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1511">Info Field 4: Not used</span></span>

### <a name="packet-allocate"></a><span data-ttu-id="09389-1512">Asignación de paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1512">Packet Allocate</span></span> 

#### <a name="nx_packet_allocate"></a><span data-ttu-id="09389-1513">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="09389-1513">nx_packet_allocate</span></span>

<span data-ttu-id="09389-1514">**Icono** ![Icono de asignación de paquete](./media/user-guide/netx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1514">**Icon** ![Packet allocate icon](./media/user-guide/netx-events/image108.png)</span></span>

<span data-ttu-id="09389-1515">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1515">**Description**</span></span>

<span data-ttu-id="09389-1516">Este evento representa la asignación de un paquete por medio de nx_packet_allocate.</span><span class="sxs-lookup"><span data-stu-id="09389-1516">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="09389-1517">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1517">**Information Fields**</span></span>

- <span data-ttu-id="09389-1518">Campo de información 1: puntero al grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="09389-1518">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="09389-1519">Campo de información 2: puntero al paquete asignado</span><span class="sxs-lookup"><span data-stu-id="09389-1519">Info Field 2: Pointer to packet allocated</span></span>
- <span data-ttu-id="09389-1520">Campo de información 3: tipo de paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1520">Info Field 3: Packet type</span></span>
- <span data-ttu-id="09389-1521">Campo de información 4: paquetes disponibles</span><span class="sxs-lookup"><span data-stu-id="09389-1521">Info Field 4: Available packets</span></span>

### <a name="packet-copy"></a><span data-ttu-id="09389-1522">Copia de paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1522">Packet Copy</span></span> 

#### <a name="nx_packet_copy"></a><span data-ttu-id="09389-1523">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="09389-1523">nx_packet_copy</span></span>

<span data-ttu-id="09389-1524">**Icono** ![Icono de copia de paquete](./media/user-guide/netx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1524">**Icon** ![Packet cpy icon](./media/user-guide/netx-events/image109.png)</span></span>

<span data-ttu-id="09389-1525">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1525">**Description**</span></span>

<span data-ttu-id="09389-1526">Este evento representa la copia de un paquete por medio de nx_packet_copy.</span><span class="sxs-lookup"><span data-stu-id="09389-1526">This event represents copying a packet via nx_packet_copy.</span></span>

<span data-ttu-id="09389-1527">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1527">**Information Fields**</span></span>

- <span data-ttu-id="09389-1528">Campo de información 2: puntero al nuevo paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1528">Info Field 2: New packet pointer</span></span>
- <span data-ttu-id="09389-1529">Campo de información 3: puntero al grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="09389-1529">Info Field 3: Pointer to packet pool</span></span>
- <span data-ttu-id="09389-1530">Campo de información 4: opción de espera</span><span class="sxs-lookup"><span data-stu-id="09389-1530">Info Field 4: Wait option</span></span>

### <a name="packet-data-append"></a><span data-ttu-id="09389-1531">Anexión de datos de paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1531">Packet Data Append</span></span> 

#### <a name="nx_packet_data_append"></a><span data-ttu-id="09389-1532">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="09389-1532">nx_packet_data_append</span></span>

<span data-ttu-id="09389-1533">**Icono** ![Icono de anexión de datos de paquete](./media/user-guide/netx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1533">**Icon** ![Packet data append icon](./media/user-guide/netx-events/image110.png)</span></span>

<span data-ttu-id="09389-1534">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1534">**Description**</span></span>

<span data-ttu-id="09389-1535">Este evento representa la anexión de datos a un paquete por medio de nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="09389-1535">This event represents appending data to a packet via nx_packet_data_append.</span></span>

<span data-ttu-id="09389-1536">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1536">**Information Fields**</span></span>

- <span data-ttu-id="09389-1537">Campo de información 1: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1537">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="09389-1538">Campo de información 2: puntero a los datos</span><span class="sxs-lookup"><span data-stu-id="09389-1538">Info Field 2: Pointer to data</span></span>
- <span data-ttu-id="09389-1539">Campo de información 3: tamaño de los datos</span><span class="sxs-lookup"><span data-stu-id="09389-1539">Info Field 3: Size of data</span></span>
- <span data-ttu-id="09389-1540">Campo de información 4: puntero al grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="09389-1540">Info Field 4: Pointer to packet pool</span></span>

### <a name="packet-data-extract-offset"></a><span data-ttu-id="09389-1541">Desplazamiento de extracción de datos de paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1541">Packet Data Extract Offset</span></span> 

#### <a name="nx_udp_source_extract_offset"></a><span data-ttu-id="09389-1542">nx_udp_source_extract_offset</span><span class="sxs-lookup"><span data-stu-id="09389-1542">nx_udp_source_extract_offset</span></span>

<span data-ttu-id="09389-1543">**Icono** ![Icono de desplazamiento de extracción de datos de paquete](./media/user-guide/netx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1543">**Icon** ![Packet data extract offset icon](./media/user-guide/netx-events/image111.png)</span></span>

<span data-ttu-id="09389-1544">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1544">**Description**</span></span>

<span data-ttu-id="09389-1545">Este evento representa la extracción de datos de un paquete a un búfer proporcionado por medio de nx_udp_source_extract_offset.</span><span class="sxs-lookup"><span data-stu-id="09389-1545">This event represents packet data that is extracted into a supplied buffer from a packet via nx_udp_source_extract_offset.</span></span>

<span data-ttu-id="09389-1546">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1546">**Information Fields**</span></span>

- <span data-ttu-id="09389-1547">Campo de información 1: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1547">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="09389-1548">Campo de información 2: tamaño del búfer especificado</span><span class="sxs-lookup"><span data-stu-id="09389-1548">Info Field 2: Size of specified buffer</span></span>
- <span data-ttu-id="09389-1549">Campo de información 3: número de bytes copiados</span><span class="sxs-lookup"><span data-stu-id="09389-1549">Info Field 3: Number of bytes copied</span></span>
- <span data-ttu-id="09389-1550">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1550">Info Field 4: Not used</span></span>

### <a name="packet-data-retrieve"></a><span data-ttu-id="09389-1551">Recuperación de datos de paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1551">Packet Data Retrieve</span></span> 

#### <a name="nx_packet_data_retrieve"></a><span data-ttu-id="09389-1552">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="09389-1552">nx_packet_data_retrieve</span></span>

<span data-ttu-id="09389-1553">**Icono** ![Icono de recuperación de datos de paquete](./media/user-guide/netx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1553">**Icon** ![Packet data retrieve icon](./media/user-guide/netx-events/image112.png)</span></span>

<span data-ttu-id="09389-1554">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1554">**Description**</span></span>

<span data-ttu-id="09389-1555">Este evento representa la recuperación de datos de un paquete por medio de nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="09389-1555">This event represents retrieving data from a packet via nx_packet_data_retrieve.</span></span>

<span data-ttu-id="09389-1556">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1556">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1557">Campo de información 1: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1557">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="09389-1558">Campo de información 2: puntero al inicio del búfer</span><span class="sxs-lookup"><span data-stu-id="09389-1558">Info Field 2: Pointer to start of buffer</span></span>
- <span data-ttu-id="09389-1559">Campo de información 3: bytes copiados</span><span class="sxs-lookup"><span data-stu-id="09389-1559">Info Field 3: Bytes copied</span></span>
- <span data-ttu-id="09389-1560">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1560">Info Field 4: Not used</span></span>

### <a name="packet-length-get"></a><span data-ttu-id="09389-1561">Obtención de longitud de paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1561">Packet Length Get</span></span> 

#### <a name="nx_packet_length_get"></a><span data-ttu-id="09389-1562">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="09389-1562">nx_packet_length_get</span></span>

<span data-ttu-id="09389-1563">**Icono** ![Icono de obtención de longitud de paquete](./media/user-guide/netx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1563">**Icon** ![Packet length get icon](./media/user-guide/netx-events/image113.png)</span></span>

<span data-ttu-id="09389-1564">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1564">**Description**</span></span>

<span data-ttu-id="09389-1565">Este evento representa la obtención de la longitud de un paquete por medio de nx_packet_length_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1565">This event represents getting the length of a packet via nx_packet_length_get.</span></span>

<span data-ttu-id="09389-1566">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1566">**Information Fields**</span></span>

- <span data-ttu-id="09389-1567">Campo de información 1: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1567">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="09389-1568">Campo de información 2: longitud del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1568">Info Field 2: Packet length</span></span>
- <span data-ttu-id="09389-1569">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1569">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1570">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1570">Info Field 4: Not used</span></span>

### <a name="packet-pool-create"></a><span data-ttu-id="09389-1571">Creación de grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="09389-1571">Packet Pool Create</span></span> 

#### <a name="nx_packet_pool_create"></a><span data-ttu-id="09389-1572">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="09389-1572">nx_packet_pool_create</span></span>

<span data-ttu-id="09389-1573">**Icono** ![Icono de creación de grupo de paquetes](./media/user-guide/netx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1573">**Icon** ![Packet pool create icon](./media/user-guide/netx-events/image114.png)</span></span>

<span data-ttu-id="09389-1574">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1574">**Description**</span></span>

<span data-ttu-id="09389-1575">Este evento representa la creación de un grupo de paquetes por medio de nx_packet_pool_create.</span><span class="sxs-lookup"><span data-stu-id="09389-1575">This event represents creating a packet pool via nx_packet_pool_create.</span></span>

<span data-ttu-id="09389-1576">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1576">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1577">Campo de información 1: puntero al grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="09389-1577">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="09389-1578">Campo de información 2: tamaño de carga del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1578">Info Field 2: Packet payload size</span></span>
- <span data-ttu-id="09389-1579">Campo de información 3: puntero al área de memoria del grupo</span><span class="sxs-lookup"><span data-stu-id="09389-1579">Info Field 3: Pointer to pool memory area</span></span>
- <span data-ttu-id="09389-1580">Campo de información 4: tamaño del área de memoria del grupo</span><span class="sxs-lookup"><span data-stu-id="09389-1580">Info Field 4: Size of pool memory area</span></span>

### <a name="packet-pool-delete"></a><span data-ttu-id="09389-1581">Eliminación de grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="09389-1581">Packet Pool Delete</span></span> 

#### <a name="nx_packet_pool_delete"></a><span data-ttu-id="09389-1582">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="09389-1582">nx_packet_pool_delete</span></span>

<span data-ttu-id="09389-1583">**Icono** ![Icono de eliminación de grupo de paquetes](./media/user-guide/netx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1583">**Icon** ![Packet pool delete icon](./media/user-guide/netx-events/image115.png)</span></span>

<span data-ttu-id="09389-1584">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1584">**Description**</span></span>

<span data-ttu-id="09389-1585">Este evento representa la eliminación de un grupo de paquetes por medio de nx_packet_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="09389-1585">This event represents deleting a packet pool via nx_packet_pool_delete.</span></span>

<span data-ttu-id="09389-1586">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1586">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1587">Campo de información 1: puntero al grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="09389-1587">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="09389-1588">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1588">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1589">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1589">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1590">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1590">Info Field 4: Not used</span></span>

#### <a name="packet-pool-information-get"></a><span data-ttu-id="09389-1591">Obtención de información de grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="09389-1591">Packet Pool Information Get</span></span> 

#### <a name="nx_packet_pool_info_get"></a><span data-ttu-id="09389-1592">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1592">nx_packet_pool_info_get</span></span>

<span data-ttu-id="09389-1593">**Icono** ![Icono de obtención de información de grupo de paquetes](./media/user-guide/netx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1593">**Icon** ![Packet pool information get icon](./media/user-guide/netx-events/image116.png)</span></span>

<span data-ttu-id="09389-1594">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1594">**Description**</span></span>

<span data-ttu-id="09389-1595">Este evento representa la obtención de información del grupo de paquetes por medio de nx_packet_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1595">This event represents getting packet pool information via nx_packet_pool_info_get.</span></span>

<span data-ttu-id="09389-1596">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1596">**Information Fields**</span></span>

- <span data-ttu-id="09389-1597">Campo de información 1: puntero al grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="09389-1597">Info Field 1: Pointer to packet pool</span></span>
- <span data-ttu-id="09389-1598">Campo de información 2: total de paquetes</span><span class="sxs-lookup"><span data-stu-id="09389-1598">Info Field 2: Total packets</span></span>
- <span data-ttu-id="09389-1599">Campo de información 3: paquetes disponibles</span><span class="sxs-lookup"><span data-stu-id="09389-1599">Info Field 3: Available packets</span></span>
- <span data-ttu-id="09389-1600">Campo de información 4: solicitudes vacías</span><span class="sxs-lookup"><span data-stu-id="09389-1600">Info Field 4: Empty requests</span></span>

### <a name="packet-release"></a><span data-ttu-id="09389-1601">Liberación de paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1601">Packet Release</span></span> 

#### <a name="nx_packet_data_release"></a><span data-ttu-id="09389-1602">nx_packet_data_release</span><span class="sxs-lookup"><span data-stu-id="09389-1602">nx_packet_data_release</span></span>

<span data-ttu-id="09389-1603">**Icono** ![Icono de liberación de paquete](./media/user-guide/netx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1603">**Icon** ![Packet release icon](./media/user-guide/netx-events/image117.png)</span></span>

<span data-ttu-id="09389-1604">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1604">**Description**</span></span>

<span data-ttu-id="09389-1605">Este evento representa la liberación de un paquete por medio de nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="09389-1605">This event represents releasing a packet via nx_packet_release.</span></span>

<span data-ttu-id="09389-1606">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1606">**Information Fields**</span></span>

- <span data-ttu-id="09389-1607">Campo de información 1: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1607">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="09389-1608">Campo de información 2: estado del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1608">Info Field 2: Packet status</span></span>
- <span data-ttu-id="09389-1609">Campo de información 3: paquetes disponibles</span><span class="sxs-lookup"><span data-stu-id="09389-1609">Info Field 3: Available packets</span></span>
- <span data-ttu-id="09389-1610">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1610">Info Field 4: Not used</span></span>

### <a name="packet-transmit-release"></a><span data-ttu-id="09389-1611">Liberación de transmisión de paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1611">Packet Transmit Release</span></span> 

#### <a name="nx_packet_transmit_release"></a><span data-ttu-id="09389-1612">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="09389-1612">nx_packet_transmit_release</span></span>

<span data-ttu-id="09389-1613">**Icono** ![Icono de liberación de transmisión de paquete](./media/user-guide/netx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1613">**Icon** ![Packet transmit release icon](./media/user-guide/netx-events/image118.png)</span></span>

<span data-ttu-id="09389-1614">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1614">**Description**</span></span>

<span data-ttu-id="09389-1615">Este evento representa la liberación de un paquete de transmisión por medio de nx_packet_transmit_release.</span><span class="sxs-lookup"><span data-stu-id="09389-1615">This event represents releasing a transmit packet via nx_packet_transmit_release.</span></span>

<span data-ttu-id="09389-1616">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1616">**Information Fields**</span></span>

- <span data-ttu-id="09389-1617">Campo de información 1: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1617">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="09389-1618">Campo de información 2: estado del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1618">Info Field 2: Packet status</span></span>
- <span data-ttu-id="09389-1619">Campo de información 3: paquetes disponibles</span><span class="sxs-lookup"><span data-stu-id="09389-1619">Info Field 3: Available packets</span></span>
- <span data-ttu-id="09389-1620">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1620">Info Field 4: Not used</span></span>

### <a name="rarp-disable"></a><span data-ttu-id="09389-1621">Deshabilitación de RARP</span><span class="sxs-lookup"><span data-stu-id="09389-1621">RARP Disable</span></span> 

#### <a name="nx_rarp_disable"></a><span data-ttu-id="09389-1622">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="09389-1622">nx_rarp_disable</span></span>

<span data-ttu-id="09389-1623">**Icono** ![Icono de deshabilitación de R A R P](./media/user-guide/netx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1623">**Icon** ![R A R P disable icon](./media/user-guide/netx-events/image119.png)</span></span>

<span data-ttu-id="09389-1624">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1624">**Description**</span></span>

<span data-ttu-id="09389-1625">Este evento representa la deshabilitación de RARP por medio de nx_rarp_disable.</span><span class="sxs-lookup"><span data-stu-id="09389-1625">This event represents disabling RARP via nx_rarp_disable.</span></span>

<span data-ttu-id="09389-1626">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1626">**Information Fields**</span></span>

- <span data-ttu-id="09389-1627">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1627">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1628">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1628">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1629">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1629">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1630">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1630">Info Field 4: Not used</span></span>

### <a name="rarp-enable"></a><span data-ttu-id="09389-1631">Habilitación de RARP</span><span class="sxs-lookup"><span data-stu-id="09389-1631">RARP Enable</span></span> 

#### <a name="nx_rarp_enable"></a><span data-ttu-id="09389-1632">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1632">nx_rarp_enable</span></span>

<span data-ttu-id="09389-1633">**Icono** ![Icono de habilitación de R A R P](./media/user-guide/netx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1633">**Icon** ![R A R P enable icon](./media/user-guide/netx-events/image120.png)</span></span>

<span data-ttu-id="09389-1634">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1634">**Description**</span></span>

<span data-ttu-id="09389-1635">Este evento representa la habilitación de RARP por medio de nx_rarp_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1635">This event represents enabling RARP via nx_rarp_enable.</span></span>

<span data-ttu-id="09389-1636">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1636">**Information Fields**</span></span>

- <span data-ttu-id="09389-1637">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1637">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1638">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1638">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1639">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1639">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1640">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1640">Info Field 4: Not used</span></span>

### <a name="rarp-information-get"></a><span data-ttu-id="09389-1641">Obtención de información de RARP</span><span class="sxs-lookup"><span data-stu-id="09389-1641">RARP Information Get</span></span> 

#### <a name="nx_rarp_info_get"></a><span data-ttu-id="09389-1642">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1642">nx_rarp_info_get</span></span>

<span data-ttu-id="09389-1643">**Icono** ![Icono de obtención de información de R A R P](./media/user-guide/netx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1643">**Icon** ![R A R P information get icon](./media/user-guide/netx-events/image121.png)</span></span>

<span data-ttu-id="09389-1644">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1644">**Description**</span></span>

<span data-ttu-id="09389-1645">Este evento representa la obtención de información de RARP por medio de nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1645">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="09389-1646">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1646">**Information Fields**</span></span>

- <span data-ttu-id="09389-1647">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1647">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1648">Campo de información 2: solicitudes enviadas</span><span class="sxs-lookup"><span data-stu-id="09389-1648">Info Field 2: Requests sent</span></span>
- <span data-ttu-id="09389-1649">Campo de información 3: respuestas recibidas</span><span class="sxs-lookup"><span data-stu-id="09389-1649">Info Field 3: Responses received</span></span>
- <span data-ttu-id="09389-1650">Campo de información 4: respuestas no válidas</span><span class="sxs-lookup"><span data-stu-id="09389-1650">Info Field 4: Invalid responses</span></span>

### <a name="system-initialize"></a><span data-ttu-id="09389-1651">Inicialización del sistema</span><span class="sxs-lookup"><span data-stu-id="09389-1651">System Initialize</span></span> 

#### <a name="nx_system_initialize"></a><span data-ttu-id="09389-1652">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="09389-1652">nx_system_initialize</span></span>

<span data-ttu-id="09389-1653">**Icono** ![Icono de inicialización del sistema](./media/user-guide/netx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1653">**Icon** ![System initialize icon](./media/user-guide/netx-events/image122.png)</span></span>

<span data-ttu-id="09389-1654">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1654">**Description**</span></span>

<span data-ttu-id="09389-1655">Este evento representa la inicialización de NetX por medio de nx_system_initialize.</span><span class="sxs-lookup"><span data-stu-id="09389-1655">This event represents initializing NetX via nx_system_initialize.</span></span>

<span data-ttu-id="09389-1656">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1656">**Information Fields**</span></span>

- <span data-ttu-id="09389-1657">Campo de información 1: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1657">Info Field 1: Not used</span></span>
- <span data-ttu-id="09389-1658">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1658">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1659">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1659">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1660">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1660">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-bind"></a><span data-ttu-id="09389-1661">Enlace de socket de cliente TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1661">TCP Client Socket Bind</span></span> 

#### <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="09389-1662">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="09389-1662">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="09389-1663">**Icono** ![Icono de enlace de socket de cliente T C P](./media/user-guide/netx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1663">**Icon** ![T  P client socket bind icon](./media/user-guide/netx-events/image123.png)</span></span>

<span data-ttu-id="09389-1664">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1664">**Description**</span></span>

<span data-ttu-id="09389-1665">Este evento representa el enlace de un socket de cliente a un puerto por medio de nx_tcp_client_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="09389-1665">This event represents binding a client socket to a port via nx_tcp_client_socket_bind.</span></span>

<span data-ttu-id="09389-1666">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1666">**Information Fields**</span></span>

- <span data-ttu-id="09389-1667">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1667">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1668">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1668">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1669">Campo de información 3: puerto solicitado</span><span class="sxs-lookup"><span data-stu-id="09389-1669">Info Field 3: Port requested</span></span>
- <span data-ttu-id="09389-1670">Campo de información 4: opción de espera</span><span class="sxs-lookup"><span data-stu-id="09389-1670">Info Field 4: Wait option</span></span>

### <a name="tcp-client-socket-connect"></a><span data-ttu-id="09389-1671">Conexión de socket de cliente TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1671">TCP Client Socket Connect</span></span> 

#### <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="09389-1672">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="09389-1672">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="09389-1673">**Icono** ![Icono de conexión de socket de cliente T C P](./media/user-guide/netx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1673">**Icon** ![T C P client socket connect icon](./media/user-guide/netx-events/image124.png)</span></span>

<span data-ttu-id="09389-1674">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1674">**Description**</span></span>

<span data-ttu-id="09389-1675">Este evento representa la creación de una conexión de socket de cliente por medio de nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="09389-1675">This event represents making a client socket connection via nx_tcp_client_socket_connect.</span></span>

<span data-ttu-id="09389-1676">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1676">**Information Fields**</span></span>

- <span data-ttu-id="09389-1677">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1677">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1678">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1678">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1679">Campo de información 3: dirección IP del servidor</span><span class="sxs-lookup"><span data-stu-id="09389-1679">Info Field 3: Server IP address</span></span>
- <span data-ttu-id="09389-1680">Campo de información 4: puerto de servidor solicitado</span><span class="sxs-lookup"><span data-stu-id="09389-1680">Info Field 4: Server port requested</span></span>

### <a name="tcp-client-socket-port-get"></a><span data-ttu-id="09389-1681">Obtención de puerto de socket de cliente TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1681">TCP Client Socket Port Get</span></span> 

#### <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="09389-1682">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="09389-1682">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="09389-1683">**Icono** ![Icono de obtención de puerto de socket de cliente T C P](./media/user-guide/netx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1683">**Icon** ![T C P client socket port get icon](./media/user-guide/netx-events/image125.png)</span></span>

<span data-ttu-id="09389-1684">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1684">**Description**</span></span>

<span data-ttu-id="09389-1685">Este evento representa la obtención del número de puerto del socket de cliente por medio de nx_tcp_client_socket_port_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1685">This event represents getting the client socket port number via nx_tcp_client_socket_port_get.</span></span>

<span data-ttu-id="09389-1686">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1686">**Information Fields**</span></span>

- <span data-ttu-id="09389-1687">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1687">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1688">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1688">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1689">Campo de información 3: número del puerto</span><span class="sxs-lookup"><span data-stu-id="09389-1689">Info Field 3: Port number</span></span>
- <span data-ttu-id="09389-1690">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1690">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-unbind"></a><span data-ttu-id="09389-1691">Desenlace de socket de cliente TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1691">TCP Client Socket Unbind</span></span> 

#### <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="09389-1692">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="09389-1692">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="09389-1693">**Icono** ![Icono de desenlace de socket de cliente T C P](./media/user-guide/netx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1693">**Icon** ![T C P client socket unbind icon](./media/user-guide/netx-events/image126.png)</span></span>

<span data-ttu-id="09389-1694">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1694">**Description**</span></span>

<span data-ttu-id="09389-1695">Este evento representa el desenlace del puerto asociado al socket por medio de nx_tcp_client_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="09389-1695">This event represents unbinding the port associated with the socket via nx_tcp_client_socket_unbind.</span></span>

<span data-ttu-id="09389-1696">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1696">**Information Fields**</span></span>

- <span data-ttu-id="09389-1697">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1697">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1698">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1698">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1699">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1699">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1700">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1700">Info Field 4: Not used</span></span>

### <a name="tcp-enable"></a><span data-ttu-id="09389-1701">Habilitación de TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1701">TCP Enable</span></span> 

#### <a name="nx_tcp_enable"></a><span data-ttu-id="09389-1702">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1702">nx_tcp_enable</span></span>

<span data-ttu-id="09389-1703">**Icono** ![Icono de habilitación de T C P](./media/user-guide/netx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1703">**Icon** ![T C P enable icon](./media/user-guide/netx-events/image127.png)</span></span>

<span data-ttu-id="09389-1704">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1704">**Description**</span></span>

<span data-ttu-id="09389-1705">Este evento representa la habilitación de TCP por medio de nx_tcp_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1705">This event represents enabling TCP via nx_tcp_enable.</span></span>

<span data-ttu-id="09389-1706">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1706">**Information Fields**</span></span>

- <span data-ttu-id="09389-1707">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1707">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1708">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1708">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1709">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1709">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1710">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1710">Info Field 4: Not used</span></span>

###  <a name="tcp-free-port-find-tcp-free-port-find"></a><span data-ttu-id="09389-1711">Búsqueda de puerto libre de TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1711">TCP Free Port Find TCP Free Port Find</span></span> 

#### <a name="nx_tcp_free_port_find"></a><span data-ttu-id="09389-1712">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="09389-1712">nx_tcp_free_port_find</span></span>

<span data-ttu-id="09389-1713">**Icono** ![Icono de búsqueda de puerto libre de T C P](./media/user-guide/netx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1713">**Icon** ![T  CP free port find icon](./media/user-guide/netx-events/image128.png)</span></span>

<span data-ttu-id="09389-1714">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1714">**Description**</span></span>

<span data-ttu-id="09389-1715">Este evento representa la búsqueda de un puerto TCP libre por medio de nx_tcp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="09389-1715">This event represents finding a free TCP port via nx_tcp_free_port_find.</span></span>

<span data-ttu-id="09389-1716">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1716">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1717">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1717">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1718">Campo de información 2: número de puerto de inicio de búsqueda</span><span class="sxs-lookup"><span data-stu-id="09389-1718">Info Field 2: Starting search port number</span></span>
- <span data-ttu-id="09389-1719">Campo de información 3: número de puerto libre</span><span class="sxs-lookup"><span data-stu-id="09389-1719">Info Field 3: Free port number</span></span>
- <span data-ttu-id="09389-1720">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1720">Info Field 4: Not used</span></span>

###  <a name="tcp-infomation-get"></a><span data-ttu-id="09389-1721">Obtención de información de TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1721">TCP Infomation Get</span></span> 

#### <a name="nx_tcp_info_get"></a><span data-ttu-id="09389-1722">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1722">nx_tcp_info_get</span></span>

<span data-ttu-id="09389-1723">**Icono** ![Icono de obtención de información de T C P](./media/user-guide/netx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1723">**Icon** ![T C P infomation get icon](./media/user-guide/netx-events/image129.png)</span></span>

<span data-ttu-id="09389-1724">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1724">**Description**</span></span>

<span data-ttu-id="09389-1725">Este evento representa la recuperación de información de TCP para la instancia de IP especificada por medio de nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1725">This event represents retrieving TCP information for the specified IP instance via nx_tcp_info_get.</span></span>

<span data-ttu-id="09389-1726">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1726">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1727">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1727">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1728">Campo de información 2: número de bytes enviados</span><span class="sxs-lookup"><span data-stu-id="09389-1728">Info Field 2: Number of bytes sent</span></span>
- <span data-ttu-id="09389-1729">Campo de información 3: número de bytes recibidos</span><span class="sxs-lookup"><span data-stu-id="09389-1729">Info Field 3: Number of bytes received</span></span>
- <span data-ttu-id="09389-1730">Campo de información 4: número de paquetes no válidos</span><span class="sxs-lookup"><span data-stu-id="09389-1730">Info Field 4: Number of invalid packets</span></span>

###  <a name="tcp-server-socket-accept"></a><span data-ttu-id="09389-1731">Aceptación de socket de servidor TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1731">TCP Server Socket Accept</span></span> 

#### <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="09389-1732">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="09389-1732">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="09389-1733">**Icono** ![Icono de aceptación de socket de servidor T C P](./media/user-guide/netx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1733">**Icon** ![T C P server socket accept icon](./media/user-guide/netx-events/image130.png)</span></span>

<span data-ttu-id="09389-1734">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1734">**Description**</span></span>

<span data-ttu-id="09389-1735">Este evento representa la configuración del socket de servidor después de que se haya recibido una solicitud de conexión activa por medio de nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="09389-1735">This event represents setting up the server socket after an active connection request was received via nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="09389-1736">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1736">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1737">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1737">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1738">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1738">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1739">Campo de información 3: opción de espera</span><span class="sxs-lookup"><span data-stu-id="09389-1739">Info Field 3: Wait option</span></span>
- <span data-ttu-id="09389-1740">Campo de información 4: estado del socket</span><span class="sxs-lookup"><span data-stu-id="09389-1740">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-listen"></a><span data-ttu-id="09389-1741">Escucha de socket de servidor TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1741">TCP Server Socket Listen</span></span> 

#### <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="09389-1742">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="09389-1742">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="09389-1743">**Icono** ![Icono de escucha de socket de servidor T C P](./media/user-guide/netx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1743">**Icon** ![T C P server socket lsten icon](./media/user-guide/netx-events/image131.png)</span></span>

<span data-ttu-id="09389-1744">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1744">**Description**</span></span>

<span data-ttu-id="09389-1745">Este evento representa el registro de una solicitud de escucha y un socket de servidor para el puerto TCP especificado por medio de nx_tcp_server_socket_listen.</span><span class="sxs-lookup"><span data-stu-id="09389-1745">This event represents register a listen request and a server socket for the specified TCP port via nx_tcp_server_socket_listen.</span></span>

<span data-ttu-id="09389-1746">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1746">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1747">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1747">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1748">Campo de información 2: número de puerto TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1748">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="09389-1749">Campo de información 3: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1749">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="09389-1750">Campo de información 4: número máximo de conexiones que se pueden poner en cola</span><span class="sxs-lookup"><span data-stu-id="09389-1750">Info Field 4: Maximum number of connections that can be queued</span></span>

###  <a name="tcp-server-socket-relisten"></a><span data-ttu-id="09389-1751">Nueva escucha de socket de servidor TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1751">TCP Server Socket Relisten</span></span> 

#### <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="09389-1752">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="09389-1752">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="09389-1753">**Icono** ![Icono de nueva escucha de socket de servidor T C P](./media/user-guide/netx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1753">**Icon** ![T C P server socket relisten icon](./media/user-guide/netx-events/image132.png)</span></span>

<span data-ttu-id="09389-1754">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1754">**Description**</span></span>

<span data-ttu-id="09389-1755">Este evento representa el registro de otro socket de servidor para una solicitud de escucha existente en el puerto TCP especificado por medio de nx_tcp_server_socket_relisten.</span><span class="sxs-lookup"><span data-stu-id="09389-1755">This event represents register another server socket for an existing listen request on the specified TCP port via nx_tcp_server_socket_relisten.</span></span>

<span data-ttu-id="09389-1756">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1756">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1757">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1757">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1758">Campo de información 2: número de puerto TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1758">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="09389-1759">Campo de información 3: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1759">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="09389-1760">Campo de información 4: estado del socket</span><span class="sxs-lookup"><span data-stu-id="09389-1760">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-unaccept"></a><span data-ttu-id="09389-1761">Desaceptación de socket de servidor TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1761">TCP Server Socket Unaccept</span></span> 

#### <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="09389-1762">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="09389-1762">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="09389-1763">**Icono** ![Icono de desaceptación de socket de servidor T C P](./media/user-guide/netx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1763">**Icon** ![T C P server socket unaccept icon](./media/user-guide/netx-events/image133.png)</span></span>

<span data-ttu-id="09389-1764">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1764">**Description**</span></span>

<span data-ttu-id="09389-1765">Este evento representa la eliminación del socket de servidor de la asociación con el puerto que recibe una conexión pasiva anterior por medio de nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="09389-1765">This event represents removing the server socket from association with the port receiving an earlier passive connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="09389-1766">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1766">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1767">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1767">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1768">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1768">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1769">Campo de información 3: estado del socket</span><span class="sxs-lookup"><span data-stu-id="09389-1769">Info Field 3: Socket state</span></span>
- <span data-ttu-id="09389-1770">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1770">Info Field 4: Not used</span></span>

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a><span data-ttu-id="09389-1771">Abandono de escucha de socket de servidor TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1771">TCP Server Socket Unlisten TCP Server Socket Unlisten</span></span> 

#### <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="09389-1772">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="09389-1772">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="09389-1773">**Icono** ![Icono de abandono de escucha de socket de servidor T C P](./media/user-guide/netx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1773">**Icon** ![T C P server socket unlisten icon](./media/user-guide/netx-events/image134.png)</span></span>

<span data-ttu-id="09389-1774">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1774">**Description**</span></span>

<span data-ttu-id="09389-1775">Este evento representa la eliminación de una solicitud de escucha anterior para el puerto TCP especificado por medio de nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="09389-1775">This event represents removing a previous listen request for the specified TCP port via nx_tcp_server_socket_unlisten.</span></span>

<span data-ttu-id="09389-1776">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1776">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1777">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1777">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1778">Campo de información 2: número de puerto TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1778">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="09389-1779">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1779">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1780">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1780">Info Field 4: Not used</span></span>

### <a name="tcp-socket-bytes-available"></a><span data-ttu-id="09389-1781">Bytes disponibles de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1781">TCP Socket Bytes Available</span></span> 

#### <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="09389-1782">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="09389-1782">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="09389-1783">**Icono** ![Icono de bytes disponibles de socket T C P](./media/user-guide/netx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1783">**Icon** ![T C P socket bytes available icon](./media/user-guide/netx-events/image135.png)</span></span>

<span data-ttu-id="09389-1784">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1784">**Description**</span></span>

<span data-ttu-id="09389-1785">Este evento representa el número de bytes disponibles actualmente en el socket de recepción TCP especificado por medio de nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="09389-1785">This event represents the number of bytes currently available on the specified TCP receiving socket via nx_tcp_socket_bytes_available.</span></span>

<span data-ttu-id="09389-1786">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1786">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1787">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1787">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1788">Campo de información 2: puntero al socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1788">Info Field 2: Pointer to TCP socket</span></span>
- <span data-ttu-id="09389-1789">Campo de información 3: bytes recibidos en el socket</span><span class="sxs-lookup"><span data-stu-id="09389-1789">Info Field 3: Bytes received on the socket</span></span>
- <span data-ttu-id="09389-1790">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1790">Info Field 4: Not used</span></span>

### <a name="tcp-socket-create"></a><span data-ttu-id="09389-1791">Creación de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1791">TCP Socket Create</span></span> 

#### <a name="nx_tcp_socket_create"></a><span data-ttu-id="09389-1792">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="09389-1792">nx_tcp_socket_create</span></span>

<span data-ttu-id="09389-1793">**Icono** ![Icono de creación de socket T C P](./media/user-guide/netx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1793">**Icon** ![T C P socket create icon](./media/user-guide/netx-events/image136.png)</span></span>

<span data-ttu-id="09389-1794">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1794">**Description**</span></span>

<span data-ttu-id="09389-1795">Este evento representa la creación de un socket TCP por medio de nx_tcp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="09389-1795">This event represents creating a TCP socket via nx_tcp_socket_create.</span></span>

<span data-ttu-id="09389-1796">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1796">**Information Fields**</span></span>

- <span data-ttu-id="09389-1797">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1797">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1798">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1798">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1799">Campo de información 3: tipo de servicio</span><span class="sxs-lookup"><span data-stu-id="09389-1799">Info Field 3: Type of service</span></span>
- <span data-ttu-id="09389-1800">Campo de información 4: tamaño de la ventana de recepción</span><span class="sxs-lookup"><span data-stu-id="09389-1800">Info Field 4: Receive window size</span></span>

### <a name="tcp-socket-delete"></a><span data-ttu-id="09389-1801">Eliminación de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1801">TCP Socket Delete</span></span> 

#### <a name="nx_tcp_socket_delete"></a><span data-ttu-id="09389-1802">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="09389-1802">nx_tcp_socket_delete</span></span>

<span data-ttu-id="09389-1803">**Icono** ![Icono de eliminación de socket T C P](./media/user-guide/netx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1803">**Icon** ![T C P socket delete icon](./media/user-guide/netx-events/image137.png)</span></span>

<span data-ttu-id="09389-1804">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1804">**Description**</span></span>

<span data-ttu-id="09389-1805">Este evento representa la eliminación de un socket por medio de nx_tcp_socket_delete.</span><span class="sxs-lookup"><span data-stu-id="09389-1805">This event represents deleting a socket via nx_tcp_socket_delete.</span></span>

<span data-ttu-id="09389-1806">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1806">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1807">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1807">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1808">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1808">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1809">Campo de información 3: estado del socket</span><span class="sxs-lookup"><span data-stu-id="09389-1809">Info Field 3: Socket state</span></span>
- <span data-ttu-id="09389-1810">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1810">Info Field 4: Not used</span></span>

### <a name="tcp-socket-disconnect"></a><span data-ttu-id="09389-1811">Desconexión de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1811">TCP Socket Disconnect</span></span> 

#### <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="09389-1812">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="09389-1812">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="09389-1813">**Icono** ![Icono de desconexión de socket T C P](./media/user-guide/netx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1813">**Icon** ![T C P socket disconnect icon](./media/user-guide/netx-events/image138.png)</span></span>

<span data-ttu-id="09389-1814">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1814">**Description**</span></span>

<span data-ttu-id="09389-1815">Este evento representa la desconexión de un socket por medio de nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="09389-1815">This event represents disconnecting a socket via nx_tcp_socket_disconnect.</span></span>

<span data-ttu-id="09389-1816">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1816">**Information Fields**</span></span>

- <span data-ttu-id="09389-1817">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1817">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1818">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1818">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1819">Campo de información 3: opción de espera</span><span class="sxs-lookup"><span data-stu-id="09389-1819">Info Field 3: Wait option</span></span>
- <span data-ttu-id="09389-1820">Campo de información 4: estado del socket</span><span class="sxs-lookup"><span data-stu-id="09389-1820">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-information-get"></a><span data-ttu-id="09389-1821">Obtención de información de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1821">TCP Socket Information Get</span></span> 

#### <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="09389-1822">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1822">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="09389-1823">**Icono** ![Icono de obtención de información de socket T C P](./media/user-guide/netx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1823">**Icon** ![T C P socket information get icon](./media/user-guide/netx-events/image139.png)</span></span>

<span data-ttu-id="09389-1824">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1824">**Description**</span></span>

<span data-ttu-id="09389-1825">Este evento representa la obtención de información sobre un socket por medio de nx_tcp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1825">This event represents getting information about a socket via nx_tcp_socket_info_get.</span></span>

<span data-ttu-id="09389-1826">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1826">**Information Fields**</span></span>

- <span data-ttu-id="09389-1827">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1827">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1828">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1828">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1829">Campo de información 3: bytes enviados a través de este socket</span><span class="sxs-lookup"><span data-stu-id="09389-1829">Info Field 3: Bytes sent through this socket</span></span>
- <span data-ttu-id="09389-1830">Campo de información 4: bytes recibidos a través de este socket</span><span class="sxs-lookup"><span data-stu-id="09389-1830">Info Field 4: Bytes received through this socket</span></span>

### <a name="tcp-socket-mss-get"></a><span data-ttu-id="09389-1831">Obtención de MSS de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1831">TCP Socket MSS Get</span></span> 

#### <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="09389-1832">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="09389-1832">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="09389-1833">**Icono** ![Icono de obtención de M S S de socket T C P](./media/user-guide/netx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1833">**Icon** ![T C P socket M S S get icon](./media/user-guide/netx-events/image140.png)</span></span>

<span data-ttu-id="09389-1834">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1834">**Description**</span></span>

<span data-ttu-id="09389-1835">Este evento representa la obtención del MSS del socket por medio de nx_tcp_socket_mss_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1835">This event represents getting the socket's MSS via nx_tcp_socket_mss_get.</span></span>

<span data-ttu-id="09389-1836">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1836">**Information Fields**</span></span>

- <span data-ttu-id="09389-1837">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1837">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1838">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1838">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1839">Campo de información 3: tamaño máximo de segmento (MSS)</span><span class="sxs-lookup"><span data-stu-id="09389-1839">Info Field 3: Maximum Segment Size (MSS)</span></span>
- <span data-ttu-id="09389-1840">Campo de información 4: estado del socket</span><span class="sxs-lookup"><span data-stu-id="09389-1840">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-peer-get"></a><span data-ttu-id="09389-1841">Obtención de MSS de nodo del mismo nivel de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1841">TCP Socket MSS Peer Get</span></span> 

#### <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="09389-1842">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="09389-1842">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="09389-1843">**Icono** ![Icono de obtención de M S S de nodo del mismo nivel de socket T C P](./media/user-guide/netx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1843">**Icon** ![T C P socket M S S peer get icon](./media/user-guide/netx-events/image141.png)</span></span>

<span data-ttu-id="09389-1844">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1844">**Description**</span></span>

<span data-ttu-id="09389-1845">Este evento representa la obtención del valor de MSS del nodo del mismo nivel del socket por medio de nx_tcp_socket_mss_peer_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1845">This event represents getting the MSS value of the socket's peer via nx_tcp_socket_mss_peer_get.</span></span>

<span data-ttu-id="09389-1846">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1846">**Information Fields**</span></span>

- <span data-ttu-id="09389-1847">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1847">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1848">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1848">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1849">Campo de información 3: MSS del nodo del mismo nivel</span><span class="sxs-lookup"><span data-stu-id="09389-1849">Info Field 3: Peer's MSS</span></span>
- <span data-ttu-id="09389-1850">Campo de información 4: estado del socket</span><span class="sxs-lookup"><span data-stu-id="09389-1850">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-set"></a><span data-ttu-id="09389-1851">Establecimiento de MSS de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1851">TCP Socket MSS Set</span></span> 

#### <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="09389-1852">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="09389-1852">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="09389-1853">**Icono** ![Icono de establecimiento de M S S de socket T C P](./media/user-guide/netx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1853">**Icon** ![T C P socket M S S set icon](./media/user-guide/netx-events/image142.png)</span></span>

<span data-ttu-id="09389-1854">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1854">**Description**</span></span>

<span data-ttu-id="09389-1855">Este evento representa el establecimiento del MSS de un socket por medio de nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="09389-1855">This event represents setting a socket's MSS via nx_tcp_socket_mss_set.</span></span>

<span data-ttu-id="09389-1856">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1856">**Information Fields**</span></span>

- <span data-ttu-id="09389-1857">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1857">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1858">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1858">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1859">Campo de información 3: MSS</span><span class="sxs-lookup"><span data-stu-id="09389-1859">Info Field 3: MSS</span></span>
- <span data-ttu-id="09389-1860">Campo de información 4: estado del socket</span><span class="sxs-lookup"><span data-stu-id="09389-1860">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-peer-info-get"></a><span data-ttu-id="09389-1861">Obtención de información de nodo del mismo nivel de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1861">TCP Socket Peer Info Get</span></span> 

#### <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="09389-1862">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1862">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="09389-1863">**Icono** ![Icono de obtención de información de nodo del mismo nivel de socket T C P](./media/user-guide/netx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1863">**Icon** ![T C P socket peer info get icon](./media/user-guide/netx-events/image143.png)</span></span>

<span data-ttu-id="09389-1864">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1864">**Description**</span></span>

<span data-ttu-id="09389-1865">Este evento representa la información recuperada del socket TCP en relación con la dirección IP (por ejemplo, >host de conexión) y el puerto del nodo del mismo nivel por medio de nx_tcp_socket_peer_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1865">This event represents information retrieved from the TCP socket regarding the peer (e.g. >connecting host) IP address and port via nx_tcp_socket_peer_info_get.</span></span>

<span data-ttu-id="09389-1866">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1866">**Information Fields**</span></span>

- <span data-ttu-id="09389-1867">Campo de información 1: puntero al socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1867">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="09389-1868">Campo de información 2: dirección IP del nodo del mismo nivel</span><span class="sxs-lookup"><span data-stu-id="09389-1868">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="09389-1869">Campo de información 3: número de puerto del nodo del mismo nivel</span><span class="sxs-lookup"><span data-stu-id="09389-1869">Info Field 3: Peer port number</span></span>
- <span data-ttu-id="09389-1870">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1870">Info Field 4: Not used</span></span>

### <a name="tcp-socket-receive"></a><span data-ttu-id="09389-1871">Recepción de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1871">TCP Socket Receive</span></span> 

#### <a name="nx_tcp_socket_receive"></a><span data-ttu-id="09389-1872">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="09389-1872">nx_tcp_socket_receive</span></span>

<span data-ttu-id="09389-1873">**Icono** ![Icono de recepción de socket T C P](./media/user-guide/netx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1873">**Icon** ![T C P socket receive icon](./media/user-guide/netx-events/image144.png)</span></span>

<span data-ttu-id="09389-1874">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1874">**Description**</span></span>

<span data-ttu-id="09389-1875">Este evento representa la recepción de datos de un socket por medio de nx_tcp_socket_receive.</span><span class="sxs-lookup"><span data-stu-id="09389-1875">This event represents receiving data from a socket via nx_tcp_socket_receive.</span></span>

<span data-ttu-id="09389-1876">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1876">**Information Fields**</span></span>

- <span data-ttu-id="09389-1877">Campo de información 1: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1877">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="09389-1878">Campo de información 2: puntero al paquete recibido</span><span class="sxs-lookup"><span data-stu-id="09389-1878">Info Field 2: Pointer to received packet</span></span>
- <span data-ttu-id="09389-1879">Campo de información 3: longitud del paquete recibido</span><span class="sxs-lookup"><span data-stu-id="09389-1879">Info Field 3: Received packet length</span></span>
- <span data-ttu-id="09389-1880">Campo de información 4: número de secuencia de recepción</span><span class="sxs-lookup"><span data-stu-id="09389-1880">Info Field 4: Receive sequence number</span></span>

### <a name="tcp-socket-receive-notify"></a><span data-ttu-id="09389-1881">Notificación de recepción de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1881">TCP Socket Receive Notify</span></span> 

#### <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="09389-1882">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="09389-1882">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="09389-1883">**Icono** ![Icono de notificación de recepción de socket T C P](./media/user-guide/netx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1883">**Icon** ![T C P socket receive notify icon](./media/user-guide/netx-events/image145.png)</span></span>

<span data-ttu-id="09389-1884">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1884">**Description**</span></span>

<span data-ttu-id="09389-1885">Este evento representa el registro de una devolución de llamada de notificación de recepción para un socket por medio de nx_tcp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="09389-1885">This event represents registering a receive notify callback for a socket via nx_tcp_socket_receive_notify.</span></span>

<span data-ttu-id="09389-1886">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1886">**Information Fields**</span></span>

- <span data-ttu-id="09389-1887">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1887">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1888">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1888">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1889">Campo de información 3: puntero para recibir la devolución de llamada de notificación Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1889">Info Field 3: Pointer to receive notify callback Info Field 4: Not used</span></span>

### <a name="tcp-socket-send"></a><span data-ttu-id="09389-1890">Envío de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1890">TCP Socket Send</span></span> 

#### <a name="nx_tcp_socket_send"></a><span data-ttu-id="09389-1891">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="09389-1891">nx_tcp_socket_send</span></span>

<span data-ttu-id="09389-1892">**Icono** ![Icono de envío de socket T C P](./media/user-guide/netx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1892">**Icon** ![T C P socket send icon](./media/user-guide/netx-events/image146.png)</span></span>

<span data-ttu-id="09389-1893">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1893">**Description**</span></span>

<span data-ttu-id="09389-1894">Este evento representa el envío de datos en un socket por medio de nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="09389-1894">This event represents sending data on a socket via nx_tcp_socket_send.</span></span>

<span data-ttu-id="09389-1895">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1895">**Information Fields**</span></span>

- <span data-ttu-id="09389-1896">Campo de información 1: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1896">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="09389-1897">Campo de información 2: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1897">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="09389-1898">Campo de información 3: longitud del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-1898">Info Field 3: Length of packet</span></span>
- <span data-ttu-id="09389-1899">Campo de información 4: número de secuencia de transmisión</span><span class="sxs-lookup"><span data-stu-id="09389-1899">Info Field 4: Transmit sequence number</span></span>

### <a name="tcp-socket-state-wait"></a><span data-ttu-id="09389-1900">Espera de estado de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1900">TCP Socket State Wait</span></span> 

#### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="09389-1901">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="09389-1901">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="09389-1902">**Icono** ![Icono de espera de estado de socket T C P](./media/user-guide/netx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1902">**Icon** ![T C P socket state wait icon](./media/user-guide/netx-events/image147.png)</span></span>

<span data-ttu-id="09389-1903">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1903">**Description**</span></span>

<span data-ttu-id="09389-1904">Este evento representa la espera hasta que un socket entre en un estado determinado por medio de nx_tcp_socket_state_wait.</span><span class="sxs-lookup"><span data-stu-id="09389-1904">This event represents waiting for a socket to enter a particular state via nx_tcp_socket_state_wait.</span></span>

<span data-ttu-id="09389-1905">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1905">**Information Fields**</span></span>

- <span data-ttu-id="09389-1906">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1906">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1907">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1907">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1908">Campo de información 3: estado de socket deseado</span><span class="sxs-lookup"><span data-stu-id="09389-1908">Info Field 3: Desired socket state</span></span>
- <span data-ttu-id="09389-1909">Campo de información 4: estado de socket anterior</span><span class="sxs-lookup"><span data-stu-id="09389-1909">Info Field 4: Previous socket state</span></span>

### <a name="tcp-socket-transmit-configure"></a><span data-ttu-id="09389-1910">Configuración de transmisión de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1910">TCP Socket Transmit Configure</span></span> 

#### <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="09389-1911">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="09389-1911">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="09389-1912">**Icono** ![Icono de configuración de transmisión de socket T C P](./media/user-guide/netx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1912">**Icon** ![T C P socket transmit configure icon](./media/user-guide/netx-events/image148.png)</span></span>

<span data-ttu-id="09389-1913">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1913">**Description**</span></span>

<span data-ttu-id="09389-1914">Este evento representa la configuración de las opciones de transmisión para un socket por medio de nx_tcp_socket_transmit_configure.</span><span class="sxs-lookup"><span data-stu-id="09389-1914">This event represents configuring the transmit options for a socket via nx_tcp_socket_transmit_configure.</span></span>

<span data-ttu-id="09389-1915">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1915">**Information Fields**</span></span>

- <span data-ttu-id="09389-1916">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1916">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1917">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1917">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1918">Campo de información 3: profundidad de la cola de transmisión</span><span class="sxs-lookup"><span data-stu-id="09389-1918">Info Field 3: Transmit queue depth</span></span>
- <span data-ttu-id="09389-1919">Campo de información 4: valor de tiempo de espera</span><span class="sxs-lookup"><span data-stu-id="09389-1919">Info Field 4: Timeout value</span></span>

### <a name="tcp-socket-window-update-notify-set"></a><span data-ttu-id="09389-1920">Establecimiento de notificación de actualización de ventana de socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1920">TCP Socket Window Update Notify Set</span></span> 

#### <a name="nx_tcp_window_update_notify_set"></a><span data-ttu-id="09389-1921">nx_tcp_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="09389-1921">nx_tcp_window_update_notify_set</span></span>

<span data-ttu-id="09389-1922">**Icono** ![Icono de establecimiento de notificación de actualización de ventana de socket T C P](./media/user-guide/netx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1922">**Icon** ![T C P socket window update notify set icon](./media/user-guide/netx-events/image149.png)</span></span>

<span data-ttu-id="09389-1923">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1923">**Description**</span></span>

<span data-ttu-id="09389-1924">Este evento representa la recepción de una notificación en un socket TCP sobre un aumento en la ventana de recepción del host remoto por medio de nx_tcp_window_update_notify_set.</span><span class="sxs-lookup"><span data-stu-id="09389-1924">This event represents a TCP socket receiving notification of an increase in the remote host receive window via nx_tcp_window_update_notify_set.</span></span>

<span data-ttu-id="09389-1925">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1925">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1926">Campo de información 1: puntero al socket TCP</span><span class="sxs-lookup"><span data-stu-id="09389-1926">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="09389-1927">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1927">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1928">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1928">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1929">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1929">Info Field 4: Not used</span></span>

### <a name="udp-enable"></a><span data-ttu-id="09389-1930">Habilitación de UDP</span><span class="sxs-lookup"><span data-stu-id="09389-1930">UDP Enable</span></span> 

#### <a name="nx_udp_enable"></a><span data-ttu-id="09389-1931">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1931">nx_udp_enable</span></span>

<span data-ttu-id="09389-1932">**Icono** ![Icono de habilitación de U D P](./media/user-guide/netx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1932">**Icon** ![U D P enable icon](./media/user-guide/netx-events/image150.png)</span></span>

<span data-ttu-id="09389-1933">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1933">**Description**</span></span>

<span data-ttu-id="09389-1934">Este evento representa la habilitación de UDP por medio de nx_udp_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1934">This event represents enabling UDP via nx_udp_enable.</span></span>

<span data-ttu-id="09389-1935">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1935">**Information Fields**</span></span>

- <span data-ttu-id="09389-1936">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1936">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1937">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1937">Info Field 2: Not used</span></span>
- <span data-ttu-id="09389-1938">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1938">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1939">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1939">Info Field 4: Not used</span></span>

### <a name="udp-free-port-find"></a><span data-ttu-id="09389-1940">Búsqueda de puerto libre de UDP</span><span class="sxs-lookup"><span data-stu-id="09389-1940">UDP Free Port Find</span></span> 

#### <a name="nx_udp_free_port_find"></a><span data-ttu-id="09389-1941">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="09389-1941">nx_udp_free_port_find</span></span>

<span data-ttu-id="09389-1942">**Icono** ![Icono de búsqueda de puerto libre de U D P](./media/user-guide/netx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1942">**Icon** ![U D P free port find icon](./media/user-guide/netx-events/image151.png)</span></span>

<span data-ttu-id="09389-1943">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1943">**Description**</span></span>

<span data-ttu-id="09389-1944">Este evento representa la búsqueda de un puerto UDP libre por medio de nx_udp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="09389-1944">This event represents finding a free UDP port via nx_udp_free_port_find.</span></span>

<span data-ttu-id="09389-1945">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1945">**Information Fields**</span></span>

- <span data-ttu-id="09389-1946">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1946">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1947">Campo de información 2: puerto inicial a partir del cual se hace la búsqueda</span><span class="sxs-lookup"><span data-stu-id="09389-1947">Info Field 2: Starting port to search from</span></span>
- <span data-ttu-id="09389-1948">Campo de información 3: puerto libre</span><span class="sxs-lookup"><span data-stu-id="09389-1948">Info Field 3: Free port</span></span>
- <span data-ttu-id="09389-1949">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1949">Info Field 4: Not used</span></span>

### <a name="udp-information-get"></a><span data-ttu-id="09389-1950">Obtención de información de UDP</span><span class="sxs-lookup"><span data-stu-id="09389-1950">UDP Information Get</span></span> 

#### <a name="nx_udp_info_get"></a><span data-ttu-id="09389-1951">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-1951">nx_udp_info_get</span></span>

<span data-ttu-id="09389-1952">**Icono** ![Icono de obtención de información de U D P](./media/user-guide/netx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1952">**Icon** ![U D P information get icon](./media/user-guide/netx-events/image152.png)</span></span>

<span data-ttu-id="09389-1953">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1953">**Description**</span></span>

<span data-ttu-id="09389-1954">Este evento representa la obtención de información por medio de nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-1954">This event represents getting information via nx_udp_info_get.</span></span>

<span data-ttu-id="09389-1955">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1955">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1956">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1956">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1957">Campo de información 2: bytes UDP enviados</span><span class="sxs-lookup"><span data-stu-id="09389-1957">Info Field 2: UDP bytes sent</span></span>
- <span data-ttu-id="09389-1958">Campo de información 3: bytes UDP recibidos</span><span class="sxs-lookup"><span data-stu-id="09389-1958">Info Field 3: UDP bytes received</span></span>
- <span data-ttu-id="09389-1959">Campo de información 4: paquetes no válidos</span><span class="sxs-lookup"><span data-stu-id="09389-1959">Info Field 4: Invalid packets</span></span>

### <a name="udp-socket-bind"></a><span data-ttu-id="09389-1960">Enlace de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-1960">UDP Socket Bind</span></span> 

#### <a name="nx_udp_socket_bind"></a><span data-ttu-id="09389-1961">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="09389-1961">nx_udp_socket_bind</span></span>

<span data-ttu-id="09389-1962">**Icono** ![Icono de enlace de socket U D P](./media/user-guide/netx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1962">**Icon** ![U D P socket bind icon](./media/user-guide/netx-events/image153.png)</span></span>

<span data-ttu-id="09389-1963">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1963">**Description**</span></span>

<span data-ttu-id="09389-1964">Este evento representa el enlace de un socket UDP a un puerto por medio de nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="09389-1964">This event represents binding a UDP socket to a port via nx_udp_socket_bind.</span></span>

<span data-ttu-id="09389-1965">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1965">**Information Fields**</span></span>

- <span data-ttu-id="09389-1966">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1966">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1967">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1967">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1968">Campo de información 3: número del puerto</span><span class="sxs-lookup"><span data-stu-id="09389-1968">Info Field 3: Port number</span></span>
- <span data-ttu-id="09389-1969">Campo de información 4: opción de espera</span><span class="sxs-lookup"><span data-stu-id="09389-1969">Info Field 4: Wait option</span></span>

### <a name="udp-socket-bytes-available"></a><span data-ttu-id="09389-1970">Bytes disponibles de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-1970">UDP Socket Bytes Available</span></span> 

#### <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="09389-1971">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="09389-1971">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="09389-1972">**Icono** ![Icono de bytes disponibles de socket U D P](./media/user-guide/netx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1972">**Icon** ![U D P socket bytes available icon](./media/user-guide/netx-events/image154.png)</span></span>

<span data-ttu-id="09389-1973">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1973">**Description**</span></span>

<span data-ttu-id="09389-1974">Este evento representa el número actual de bytes recibidos en el socket UDP por medio de nx_udp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="09389-1974">This event represents the current number of bytes received on the UDP socket via nx_udp_socket_bytes_available.</span></span>

<span data-ttu-id="09389-1975">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1975">**Information Fields**</span></span>

- <span data-ttu-id="09389-1976">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1976">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1977">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1977">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1978">Campo de información 3: bytes recibidos en el socket</span><span class="sxs-lookup"><span data-stu-id="09389-1978">Info Field 3: Bytes received on socket</span></span>
- <span data-ttu-id="09389-1979">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1979">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-disable"></a><span data-ttu-id="09389-1980">Deshabilitación de suma de comprobación de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-1980">UDP Socket Checksum Disable</span></span> 

#### <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="09389-1981">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="09389-1981">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="09389-1982">**Icono** ![Icono de deshabilitación de suma de comprobación de socket U D P](./media/user-guide/netx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1982">**Icon** ![U D P socket checksum disable icon](./media/user-guide/netx-events/image155.png)</span></span>

<span data-ttu-id="09389-1983">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1983">**Description**</span></span>

<span data-ttu-id="09389-1984">Este evento representa la deshabilitación de la suma de comprobación para los datos de un socket UDP por medio de nx_udp_socket_checksum_disable.</span><span class="sxs-lookup"><span data-stu-id="09389-1984">This event represents disabling the checksum for data on a UDP socket via nx_udp_socket_checksum_disable.</span></span>

<span data-ttu-id="09389-1985">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1985">**Information Fields**</span></span> 

- <span data-ttu-id="09389-1986">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1986">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1987">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1987">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1988">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1988">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1989">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1989">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-enable"></a><span data-ttu-id="09389-1990">Habilitación de suma de comprobación de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-1990">UDP Socket Checksum Enable</span></span> 

#### <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="09389-1991">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="09389-1991">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="09389-1992">**Icono** ![Icono de habilitación de suma de comprobación de socket U D P](./media/user-guide/netx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="09389-1992">**Icon** ![U D P socket checksum enable icon](./media/user-guide/netx-events/image156.png)</span></span>

<span data-ttu-id="09389-1993">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-1993">**Description**</span></span>

<span data-ttu-id="09389-1994">Este evento representa la habilitación del procesamiento de suma de comprobación en un socket por medio de nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="09389-1994">This event represents enabling checksum processing on a socket via nx_udp_socket_checksum_enable.</span></span>

<span data-ttu-id="09389-1995">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-1995">**Information Fields**</span></span>

- <span data-ttu-id="09389-1996">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-1996">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-1997">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-1997">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-1998">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1998">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-1999">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-1999">Info Field 4: Not used</span></span>

### <a name="udp-socket-create"></a><span data-ttu-id="09389-2000">Creación de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2000">UDP Socket Create</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="09389-2001">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="09389-2001">nx_udp_socket_create</span></span>

<span data-ttu-id="09389-2002">**Icono** ![Icono de creación de socket U D P](./media/user-guide/netx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="09389-2002">**Icon** ![U D P socket create icon](./media/user-guide/netx-events/image157.png)</span></span>

<span data-ttu-id="09389-2003">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-2003">**Description**</span></span>

<span data-ttu-id="09389-2004">Este evento representa la creación de un socket UDP por medio de nx_udp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="09389-2004">This event represents creating a UDP socket via nx_udp_socket_create.</span></span>

<span data-ttu-id="09389-2005">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-2005">**Information Fields**</span></span>

- <span data-ttu-id="09389-2006">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-2006">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-2007">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-2007">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-2008">Campo de información 3: tipo de servicio</span><span class="sxs-lookup"><span data-stu-id="09389-2008">Info Field 3: Type of service</span></span>
- <span data-ttu-id="09389-2009">Campo de información 4: cola de recepción máxima</span><span class="sxs-lookup"><span data-stu-id="09389-2009">Info Field 4: Maximum receive queue</span></span>

### <a name="udp-socket-delete-event"></a><span data-ttu-id="09389-2010">Evento de eliminación de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2010">UDP Socket Delete Event</span></span> 

#### <a name="nx_udp_socket_delete-event"></a><span data-ttu-id="09389-2011">nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="09389-2011">nx_udp_socket_delete event</span></span>

<span data-ttu-id="09389-2012">**Icono** ![Icono de evento de eliminación de socket U D P](./media/user-guide/netx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="09389-2012">**Icon** ![U D P socket delete event icon](./media/user-guide/netx-events/image158.png)</span></span>

<span data-ttu-id="09389-2013">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-2013">**Description**</span></span>

<span data-ttu-id="09389-2014">Este evento representa la eliminación de un socket UDP por medio de nx_udp_socket_delete.</span><span class="sxs-lookup"><span data-stu-id="09389-2014">This event represents deleting a UDP socket via nx_udp_socket_delete.</span></span>

<span data-ttu-id="09389-2015">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-2015">**Information Fields**</span></span>

- <span data-ttu-id="09389-2016">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-2016">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-2017">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-2017">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-2018">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-2018">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-2019">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-2019">Info Field 4: Not used</span></span>

### <a name="udp-socket-information-get-event"></a><span data-ttu-id="09389-2020">Evento de obtención de información de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2020">UDP Socket Information Get Event</span></span> 

#### <a name="nx_udp_socket_info_get-event"></a><span data-ttu-id="09389-2021">nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="09389-2021">nx_udp_socket_info_get event</span></span>

<span data-ttu-id="09389-2022">**Icono** ![Icono de evento de obtención de información de socket U D P](./media/user-guide/netx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="09389-2022">**Icon** ![U D P socket information get event icon](./media/user-guide/netx-events/image159.png)</span></span>

<span data-ttu-id="09389-2023">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-2023">**Description**</span></span>

<span data-ttu-id="09389-2024">Este evento representa la obtención de información acerca de un socket UDP por medio de nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="09389-2024">This event represents getting information about a UDP socket via nx_udp_socket_info_get.</span></span>

<span data-ttu-id="09389-2025">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-2025">**Information Fields**</span></span>

- <span data-ttu-id="09389-2026">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-2026">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-2027">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-2027">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-2028">Campo de información 3: bytes enviados a través del socket</span><span class="sxs-lookup"><span data-stu-id="09389-2028">Info Field 3: Bytes sent through socket</span></span>
- <span data-ttu-id="09389-2029">Campo de información 4: bytes recibidos a través del socket</span><span class="sxs-lookup"><span data-stu-id="09389-2029">Info Field 4: Bytes received through socket</span></span>

### <a name="udp-socket-interface-set"></a><span data-ttu-id="09389-2030">Establecimiento de interfaz de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2030">UDP Socket Interface Set</span></span> 

#### <a name="nx_udp_socket_interface_set-event"></a><span data-ttu-id="09389-2031">nx_udp_socket_interface_set</span><span class="sxs-lookup"><span data-stu-id="09389-2031">nx_udp_socket_interface_set event</span></span>

<span data-ttu-id="09389-2032">**Icono** ![Icono de establecimiento de interfaz de socket U D P](./media/user-guide/netx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="09389-2032">**Icon** ![U D P socket interface set icon](./media/user-guide/netx-events/image160.png)</span></span>

<span data-ttu-id="09389-2033">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-2033">**Description**</span></span>

<span data-ttu-id="09389-2034">Este evento representa el establecimiento de la interfaz de salida del socket UDP especificado con la interfaz especificada por medio de nx_udp_socket_interface_set.</span><span class="sxs-lookup"><span data-stu-id="09389-2034">This event represents setting the outgoing interface of the specified UDP socket with the specified interface via nx_udp_socket_interface_set.</span></span>

<span data-ttu-id="09389-2035">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-2035">**Information Fields**</span></span>

- <span data-ttu-id="09389-2036">Campo de información 1: puntero al socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2036">Info Field 1: Pointer to UDP socket</span></span>
- <span data-ttu-id="09389-2037">Campo de información 2: índice correspondiente a la interfaz para el socket</span><span class="sxs-lookup"><span data-stu-id="09389-2037">Info Field 2: Index corresponding to the interface for the socket</span></span>
- <span data-ttu-id="09389-2038">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-2038">Info Field 3: Not used</span></span>
- <span data-ttu-id="09389-2039">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-2039">Info Field 4: Not used</span></span>

### <a name="udp-socket-port-get"></a><span data-ttu-id="09389-2040">Obtención de puerto de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2040">UDP Socket Port Get</span></span> 

#### <a name="nx_udp_socket_port_get"></a><span data-ttu-id="09389-2041">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="09389-2041">nx_udp_socket_port_get</span></span>

<span data-ttu-id="09389-2042">**Icono** ![Icono de obtención de puerto de socket U D P](./media/user-guide/netx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="09389-2042">**Icon** ![U D P socket port get icon](./media/user-guide/netx-events/image161.png)</span></span>

<span data-ttu-id="09389-2043">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-2043">**Description**</span></span>

<span data-ttu-id="09389-2044">Este evento representa la recuperación del puerto UDP al que está enlazado el socket UDP especificado por medio de nx_udp_socket_port_get.</span><span class="sxs-lookup"><span data-stu-id="09389-2044">This event represents retrieving the UDP port the specified UDP socket is bound to via nx_udp_socket_port_get.</span></span>

<span data-ttu-id="09389-2045">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-2045">**Information Fields**</span></span>

- <span data-ttu-id="09389-2046">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-2046">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-2047">Campo de información 2: puntero al socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2047">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="09389-2048">Campo de información 3: número del puerto</span><span class="sxs-lookup"><span data-stu-id="09389-2048">Info Field 3: Port number</span></span>
- <span data-ttu-id="09389-2049">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-2049">Info Field 4: Not used</span></span>

### <a name="udp-socket-receive"></a><span data-ttu-id="09389-2050">Recepción de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2050">UDP Socket Receive</span></span> 

#### <a name="nx_udp_socket_receive"></a><span data-ttu-id="09389-2051">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="09389-2051">nx_udp_socket_receive</span></span>

<span data-ttu-id="09389-2052">**Icono** ![Icono de recepción de socket U D P](./media/user-guide/netx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="09389-2052">**Icon** ![U D P socket receive icon](./media/user-guide/netx-events/image162.png)</span></span>

<span data-ttu-id="09389-2053">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-2053">**Description**</span></span>

<span data-ttu-id="09389-2054">Este evento representa la recepción de datos en el socket UDP especificado por medio de nx_udp_socket_receive.</span><span class="sxs-lookup"><span data-stu-id="09389-2054">This event represents receiving data on the specified UDP socket via nx_udp_socket_receive.</span></span>

<span data-ttu-id="09389-2055">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-2055">**Information Fields**</span></span>

- <span data-ttu-id="09389-2056">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-2056">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-2057">Campo de información 2: puntero al socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2057">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="09389-2058">Campo de información 3: puntero al paquete recibido</span><span class="sxs-lookup"><span data-stu-id="09389-2058">Info Field 3: Pointer to received packet</span></span>
- <span data-ttu-id="09389-2059">Campo de información 4: tamaño de paquete recibido</span><span class="sxs-lookup"><span data-stu-id="09389-2059">Info Field 4: Received packet size</span></span>

### <a name="udp-socket-receive-notify"></a><span data-ttu-id="09389-2060">Notificación de recepción de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2060">UDP Socket Receive Notify</span></span> 

#### <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="09389-2061">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="09389-2061">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="09389-2062">**Icono** ![Icono de notificación de recepción de socket U D P](./media/user-guide/netx-events/image163.png) **Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-2062">**Icon** ![U D P socket receive notify icon](./media/user-guide/netx-events/image163.png)s **Description**</span></span>

<span data-ttu-id="09389-2063">Este evento representa el registro de una devolución de llamada de notificación de recepción por medio de nx_udp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="09389-2063">This event represents registering a receive notify callback via nx_udp_socket_receive_notify.</span></span>

<span data-ttu-id="09389-2064">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-2064">**Information Fields**</span></span>

- <span data-ttu-id="09389-2065">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-2065">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-2066">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-2066">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-2067">Campo de información 3: puntero a la función de notificación de recepción Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-2067">Info Field 3: Pointer to receive notify function Info Field 4: Not used</span></span>

### <a name="udp-socket-send"></a><span data-ttu-id="09389-2068">Envío de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2068">UDP Socket Send</span></span> 

#### <a name="nx_udp_socket_send"></a><span data-ttu-id="09389-2069">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="09389-2069">nx_udp_socket_send</span></span>

<span data-ttu-id="09389-2070">**Icono** ![Icono de envío de socket U D P](./media/user-guide/netx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="09389-2070">**Icon** ![U D P socket send icon](./media/user-guide/netx-events/image164.png)</span></span>

<span data-ttu-id="09389-2071">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-2071">**Description**</span></span>

<span data-ttu-id="09389-2072">Este evento representa el envío de datos a través de un socket UDP por medio de nx_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="09389-2072">This event represents sending data through a UDP socket via nx_udp_socket_send.</span></span>

<span data-ttu-id="09389-2073">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-2073">**Information Fields**</span></span>

- <span data-ttu-id="09389-2074">Campo de información 1: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-2074">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="09389-2075">Campo de información 2: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-2075">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="09389-2076">Campo de información 3: longitud del paquete</span><span class="sxs-lookup"><span data-stu-id="09389-2076">Info Field 3: Packet length</span></span>
- <span data-ttu-id="09389-2077">Campo de información 4: dirección IP de destino</span><span class="sxs-lookup"><span data-stu-id="09389-2077">Info Field 4: Destination IP address</span></span>

### <a name="udp-socket-unbind"></a><span data-ttu-id="09389-2078">Desenlace de socket UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2078">UDP Socket Unbind</span></span> 

#### <a name="nx_udp_socket_unbind"></a><span data-ttu-id="09389-2079">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="09389-2079">nx_udp_socket_unbind</span></span>

<span data-ttu-id="09389-2080">**Icono** ![Icono de desenlace de socket U D P](./media/user-guide/netx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="09389-2080">**Icon** ![U D P socket unbind icon](./media/user-guide/netx-events/image165.png)</span></span>

<span data-ttu-id="09389-2081">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-2081">**Description**</span></span>

<span data-ttu-id="09389-2082">Este evento representa el desenlace de un puerto UDP con un socket por medio de nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="09389-2082">This event represents unbinding a UDP port with a socket via nx_udp_socket_unbind.</span></span>

<span data-ttu-id="09389-2083">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-2083">**Information Fields**</span></span>

- <span data-ttu-id="09389-2084">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="09389-2084">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="09389-2085">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="09389-2085">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="09389-2086">Campo de información 3: número del puerto</span><span class="sxs-lookup"><span data-stu-id="09389-2086">Info Field 3: Port number</span></span>
- <span data-ttu-id="09389-2087">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-2087">Info Field 4: Not used</span></span>

### <a name="udp-source-extract"></a><span data-ttu-id="09389-2088">Extracción de origen de UDP</span><span class="sxs-lookup"><span data-stu-id="09389-2088">UDP Source Extract</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="09389-2089">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="09389-2089">nx_udp_socket_create</span></span>

<span data-ttu-id="09389-2090">**Icono** ![Icono de extracción de origen de U D P](./media/user-guide/netx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="09389-2090">**Icon** ![U D P source extract icon](./media/user-guide/netx-events/image166.png)</span></span>

<span data-ttu-id="09389-2091">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="09389-2091">**Description**</span></span>

<span data-ttu-id="09389-2092">Este evento representa la obtención de la dirección IP y el número de puerto de un paquete UDP recibido por medio de nx_udp_source_extract.</span><span class="sxs-lookup"><span data-stu-id="09389-2092">This event represents getting the IP address and port number of a received UDP packet via nx_udp_source_extract.</span></span>

<span data-ttu-id="09389-2093">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="09389-2093">**Information Fields**</span></span>

- <span data-ttu-id="09389-2094">Campo de información 1: puntero al paquete</span><span class="sxs-lookup"><span data-stu-id="09389-2094">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="09389-2095">Campo de información 2: dirección IP del remitente</span><span class="sxs-lookup"><span data-stu-id="09389-2095">Info Field 2: Sender's IP address</span></span>
- <span data-ttu-id="09389-2096">Campo de información 3: número de puerto del remitente</span><span class="sxs-lookup"><span data-stu-id="09389-2096">Info Field 3: Sender's port number</span></span>
- <span data-ttu-id="09389-2097">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="09389-2097">Info Field 4: Not used</span></span>